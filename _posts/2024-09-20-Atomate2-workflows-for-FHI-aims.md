---
title: Atomate2 workflows for FHI-aims
excerpt: 
date: 2024-09-20
toc: true
tags:
  - fhiaims
  - density-functional-theory
  - python
  - condensed-matter-physics
  - materials-science
header:
  teaser: /images/2024-09-20-Atomate2-workflows-for-FHI-aims/2024-09-20-Atomate2-workflows-for-FHI-aims-20240920121324117.png
---
{: .notice--primary}
*This brief tutorial provides an introduction to using Atomate2 to set up DFT workflows with the FHI-aims code.*

![2024-09-20-Atomate2-workflows-for-FHI-aims-20240920121324117](/images/2024-09-20-Atomate2-workflows-for-FHI-aims/2024-09-20-Atomate2-workflows-for-FHI-aims-20240920121324117.png)
{: width="50%"}

With the increasing availability of High Performance Computing (HPC) and High Throughput Computing (HTC), the use of efficient tools to perform complex Density Functional Theory (DFT) calculations is critical for advancing materials design. Atomate2 [^1] is such a tool that can create workflows for various DFT codes. This is a brief tutorial on running FHI-aims [^2] workflows with Atomate2. It guides a user to setup a conda environment, MongoDB [^3], Pymatgen [^4], jobflow_remote [^5] and Atomate2 to run a relaxation calculation for a Si structure using a `light`  basis set on a 7x7x7 k-grid. The first section discusses running a calculation on a local computer followed by instructions on launching a calculation on a remote server and storing the output data in a MongoDB database which can be  post-processed with Python. 

# Creating a conda environment

Create conda environment  `atomate2` (or any arbitrary name) and activate it.

```shell
conda create -n atomate2 python=3.10
conda activate atomate2
```

Install the following packages.

```
pip install atomate2 ase pymatgen jobflow_remote
```

# Installing MongoDB

Atomate2 uses MongoDB to store the data output from the calculations. This is stored in a `.json`-like format which makes it easier to access through Python for further post-processing. To install MongoDB through Homebrew, run the following commands on a terminal.

```shell
brew tap mongodb/brew
brew update
brew install mongodb-community
```

Start the MongoDB server with, 

```
brew services start mongodb-community
```

You can check if the service is running with `brew services list`. It should display something like `mongodb-community started uthpala ~/Library/LaunchAgents/homebrew.mxcl.mongodb-community`. For installing on other platforms see [this](https://www.mongodb.com/docs/manual/administration/install-community/) page.
If you would like to see your databases in a GUI, consider installing [MongoDB Atlas](https://www.mongodb.com/cloud/atlas/register).

# Configuring Atomate2

Next, we have to configure Atomate2 to use FHI-aims. This is done through two `yaml` files. I stored them in `/Users/uthpala/atomate-workflows/config`. 

1. `atomate2.yaml:`
    ```yaml
    AIMS_CMD: mpirun aims.x > aims.out
    ```

    Here, `aims.x` is the FHI-aims binary. Consider adding the location of `aims.x` to the `$PATH` environmental variable to provide global access to it.

2. `jobflow.yaml:`
    ```yaml
	JOB_STORE:
	  docs_store:
	    type: MongoStore
	    database: atomate2
	    host: localhost
	    port: 27017
	    collection_name: outputs
	  additional_stores:
	    data:
	      type: GridFSStore
	      database: atomate2
	      host: localhost
	      port: 27017
	      collection_name: outputs_blobs
```

The locations of these files are then added to the `~/.bashrc` file (`~/.zshrc` on a Mac) as,

```shell
export ATOMATE2_CONFIG_FILE="/Users/uthpala/atomate-workflows/config/atomate2.yaml"
export JOBFLOW_CONFIG_FILE="/Users/uthpala/atomate-workflows/config/jobflow.yaml"
```

The database `atomate2` along with the collections `outputs` and `outputs_blobs` need to be created. To do that, log in to the MongoDB server with the command `mongosh` and run the following.

```shell
use atomate2;
db.createCollection("outputs");
db.createCollection("outputs_blobs");
```

Additionally, as the FHI-aims species defaults are parsed through Pymatgen, the location has to be added to `~/.config/.pmgrc.yaml` as follows, 

```yaml
AIMS_SPECIES_DIR: "/Users/uthpala/apps/FHIaims/FHIaims/species_defaults/"
```

# Running locally

The following script is used to run a relaxation calculation locally. 

`si_relax.py:`
```python
#!/usr/bin/env python

from pymatgen.core import Structure, Molecule, Lattice
from pymatgen.io.aims.sets.core import RelaxSetGenerator
from atomate2.aims.jobs.core import RelaxMaker
from jobflow import run_locally

a = 2.715
lattice = Lattice([0.0, a, a](0.0,%20a,%20a))
si = Structure(
    lattice=lattice,
    species=["Si", "Si"],
    coords=[0, 0, 0](0,%200,%200),
)

# Create relax job
relax_job = RelaxMaker(
    input_set_generator=RelaxSetGenerator(
        user_params={"species_dir": "light", "k_grid": [7, 7, 7]}
    )
).make(si)

# Run relax job locally
j_id = run_locally(relax_job)
```

In your terminal, run:

```shell
python si_relax.py
```

Once the calculation is complete, the output information is parsed from `aims.out` and stored in the MongoDB database `atomate2` under the collection `outputs`.
	
# Running remotely

To run Atomate2 in a remote cluster, repeat the previous steps of creating a conda environment and installing the Python libraries on that cluster. Note that this is only possible for clusters you have password-less access to, which can be achieved by using `ssh-keys`. The calculation request is initiated in your local computer and is sent to the remote cluster through the `jobflow_remote` library which is then actually run on that cluster based on the input parameters you provided.

Add the following jobflow_remote configuration file to `~/.jfremote/timewarp.yaml` on your **local** computer. Replace `timewarp.yaml` with the name of your **remote** server. `pre_run` invokes the commands run prior to running the calculation on the **remote** server. Make sure you are activating an `automate2` conda environment. `work_dir` is the location the calculations are run on the **remote** server. Modify this according to your needs. 

`timewarp.yaml:`
```yaml
name: timewarp
log_level: debug
workers:
  timewarp_worker:
    type: remote
    interactive_login: false
    scheduler_type: slurm
    work_dir: /home/ukh/atomate2
    pre_run: |
      source ~/.bashrc
      intel
      conda activate atomate2
    timeout_execute: 60
    host: timewarp-02.egr.duke.edu
    user: ukh
queue:
  store:
    type: MongoStore
    host: localhost
    database: timewarp
    collection_name: queue
exec_config: {}
jobstore:
  docs_store:
    type: MongoStore
    database: timewarp
    host: localhost
    port: 27017
    collection_name: outputs
  additional_stores:
    data:
      type: GridFSStore
      database: timewarp
      host: localhost
      port: 27017
      collection_name: outputs_blobs
```

For the remote server calculations, we store the data in the MongoDB database `timewarp` with the collections `queue`, `outputs` and `outputs_blobs`. Create these through `mongosh` with, 

```shell
use timewarp;
db.createCollection("queue");
db.createCollection("outputs");
db.createCollection("outputs_blobs");
```

On the **remote** server, create the file `~/.config/atomate2/atomate2.yaml` with the following content.

`atomate2.yaml:`
```yaml
AIMS_CMD: srun aims.x > aims.out
```

Then add the following line to the `~/.bashrc` on the **remote** server,
```shell
export ATOMATE2_CONFIG_FILE="/home/ukh/.config/atomate2/atomate2.yaml"
```

We have to then start the jf-runner on the **local** computer with the following commands.

```shell
jf runner start
jf admin reset
```

Any time you change the contents of `~/.jfremote/timewarp.yaml`, you will have to restart the runner after first stopping it with `jf runner stop`.

## Running the calculation

The python code, `si_relax_remote.py` is used to run a FHI-aims relaxation calculation on the remote server, requested from the local computer.

`si_relax_remote.py:`
```python
#!/usr/bin/env python

from pymatgen.core import Structure, Molecule, Lattice
from pymatgen.io.aims.sets.core import RelaxSetGenerator
from atomate2.aims.jobs.core import RelaxMaker
from jobflow_remote import submit_flow

a = 2.715
lattice = Lattice([0.0, a, a](0.0,%20a,%20a))
si = Structure(
    lattice=lattice,
    species=["Si", "Si"],
    coords=[0, 0, 0](0,%200,%200),
)

# Create relax job
relax_job = RelaxMaker(
    input_set_generator=RelaxSetGenerator(
        user_params={"species_dir": "light", "k_grid": [7, 7, 7]}
    )
).make(si)

resource = {"nodes": 4, "ntasks_per_node": 4, "partition": "small"}

# Run relax job remotely
j_id = submit_flow(relax_job, project="timewarp", resources=resource)
print(j_id)
```

On your **local** computer run, 
```shell
python si_relax_remote.py 
```

You can monitor the job status with the command `jf job list` from your **local** computer. You may submit as many calculations as you want since the job scheduler on the remote cluster will take care of queuing jobs and executing them. Once the calculation is complete, the output data can be accessed in the MongoDB database `timewarp`. Each job is saved with a unique identifier, `uuid` which looks something like `
`uuid:"71411da5-078c-4f88-8362-9da3ae3263ea"`.

# Importing MongoDB data in Python

The calculation data is saved in the database `timewarp` in the collection `outputs`. Each run is a document within the collection and can be referenced by its `uuid` using Python. The following script displays the structural information and bandgap of the material. 

```python
from jobflow_remote import get_jobstore

js = get_jobstore()
js.connect()

data = js.get_output("71411da5-078c-4f88-8362-9da3ae3263ea")

# output structural information
print(data["structure"])

# output bandgap 
print(data["output"]["bandgap"])
```

# Next steps

What we just did was a simple structural relaxation calculation. However, the beauty of Atomate2 is the ability to chain calculations to do workflows. For instance, a relaxation followed by a bandstructure calculation.
Please refer to the Atomate2 [documentation](https://materialsproject.github.io/atomate2/) for guidance on how to do this and much more.

# References

[^1]: [https://github.com/materialsproject/atomate2](https://github.com/materialsproject/atomate2)
[^2]: [https://fhi-aims.org](https://fhi-aims.org)
[^3]: [https://www.mongodb.com](https://www.mongodb.com)
[^4]: [https://pymatgen.org](https://pymatgen.org)
[^5]: [https://matgenix.github.io/jobflow-remote/](https://matgenix.github.io/jobflow-remote/)

