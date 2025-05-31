---
title: Research
permalink: /research/
classes: wide
header:
    overlay_image: "/assets/images/beach.jpg"
    caption: "Photo by [Pasindu Dhananjaya](https://unsplash.com/@pasiiijay) on [Unsplash](https://unsplash.com)"
---

<div class="my-custom-notice">
I am a computational physicist specializing in the development and application of beyond-DFT (Density Functional Theory) methods for the design, discovery and characterization of novel materials. Over the past decade, I have leveraged high-performance computing (HPC) to push the boundaries of electronic structure simulations from GW approximation and DMFT (Dynamical
Mean Field Theory) to emerging high-accuracy machine learning interatomic potentials for molecular dynamics, alongside the development of open-source frameworks that accelerate materials research for a worldwide user community. My ultimate goal is to combine advanced computational methods, AI and data-driven insights, and collaborative code development to enable next-generation technologies for semiconductors, electronics, and energy applications.
</div>

# Beyond-DFT many-body excited states and quasiparticle methods

<figure style="width: 50%" class="align-right">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/research/GW-CSC.pdf" alt="">
  <figcaption class="figure-caption text-center">A benchmark of GW band gaps of compound semiconductors with varying accuracies computed with the FHI-aims code</figcaption>
</figure>

Although DFT in its standard Kohn-Sham formalism is a successful theory in describing the ground state electronic structure of materials, it lacks the physics required to accurately explain excited state and quasiparticle properties stemming from dynamic many-body interactions.
The GW approximation is a Green’s function based many-body perturbation method that captures such particle interactions leading to a higher accurate representation of quasiparticles and excited states. Utilizing the GW approximation implemented within the electronic structure code [FHI-aims](https://fhi-aims.org), I perform simulations to study excited states of compound semiconductors and hybrid organic-inorganic perovskites (HOIP) which have broad implications for semiconductors, photovoltaics, and optoelectronics, where correct band gap and carrier dynamics predictions are essential for guiding experimental fabrication.

**Relativistic effects in complex materials**<br>

Spin-orbit coupling (SOC) is a relativistic effect that can radically alter electronic structures in materials with heavy elements. My work on the implementation of SOC into periodic GW in [FHI-aims](https://fhi-aims.org) will ensure such effects are taken into account for excited state simulations of compound semiconductors and HOIP.

**Discovering high-temperature superfluorescence**<br>

Through a novel $\Delta$-SCF implementation to simulate excited electrons within [FHI-aims](https://fhi-aims.org) and [ELSI](https://wordpress.elsi-interchange.org), I collaborate with experimental teams to investigate spontaneous polaron synchronization driven high-temperature superfluorescence phenomena in perovskites. These insights show promising potential in quantum computing, communications, and photonics applications [[Biliroglu, M., *et al.* Nature (May 2025)](https://www.nature.com/articles/s41586-025-09030-x)].

# Strongly Correlated Materials and DMFT

<figure style="width: 50%" class="align-right">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/research/impurity.pdf" alt="">
  <figcaption class="figure-caption text-center">Mapping of the lattice to an impurity embedded in a bath which is determined self-consistency with DMFT. The impurity is an interacting single site coupled to an effective non-interacting bath representing the residual lattice through a hybridization function. </figcaption>
</figure>

The electronic correlations in materials drive a variety of fascinating phenomena due to the coupling between electron spin, charge, ionic displacements and orbital ordering. In materials with localized *d* and *f* electrons such as transition metals and rare-earths, conventional mean-field approaches like DFT often fails to capture the strong electron-electron interactions which lead to magnetism, high-temperature superconductivity, colossal magnetoresistance, metal-insulator transitions.

**The DMFTwDFT framework**<br>

<figure style="width: 50%" class="align-right">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/research/dmftwdft.png" alt="">
  <figcaption class="figure-caption text-center">The spectral function of SrVO3 calculated with DMFTwDFT. The band broadening is a measure of quasiparticle lifetimes which is not present in DFT band structures. </figcaption>
</figure>

Dynamical Mean Field Theory (DMFT) is a many-body Green's function technique used to study Strongly Correlated Materials (SCM) in which a lattice is mapped onto a local interacting impurity problem and solved numerically using Quantum Monte Carlo methods to capture both itinerant and localized nature of electrons. The initial self-energy ($\Sigma$) is estimated from the self-consistent density obtained from DFT which is then projected into maximally localized Wannier functions (MLWF's) as the basis set which is then used to solve for the interacting DMFT density matrix. Full charge self-consistency is achieved by repeatedly updating the DFT and DMFT charge densities until they are both converged.<br>
I am a developer of the open-source [DMFTwDFT](https://github.com/DMFTwDFT-project/DMFTwDFT) framework that interfaces various DFT codes with DMFT, enabling accurated simulations of SCM such as rare-earth perovskites.

**Investigating defects in SCM**<br>

My research has highlighted the effects of oxygen vacancies [[U. Herath et al., arXiv:2212.07348v1 [cond-mat.str-el] (2022)](https://arxiv.org/abs/2212.07348)] and hydrogen doping [[S. S. Bhat et al., Phys. Rev. B 109, 205124 (2024)](https://journals.aps.org/prb/abstract/10.1103/PhysRevB.109.205124)] on metal-insulator transitions and diffusion in transition metal and rare-earth nickelate perovskites, with implications for neuromorphic computing and microelectronics.<br>
I also implemented a symmetry based method to investigate alloying/defects in SCM with higher computational efficiency.

**High-accuracy machine learning interatomic potentials for SCM**<br>

In collaboration with AI/ML experts, I developed neural network-based interatomic potentials capturing DMFT-level accuracy for SCM, enabling large scale MD simulations across diverse time and length scales.

<figure style="width: 80%" class="align-center">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/research/nc.png" alt="">
  <figcaption class="figure-caption text-center">The workflow for generating high-accuracy machine learning interatomic potentials for SCM using DMFTwDFT</figcaption>
</figure>

# High-performance and high-throughput electronic structure framework development

Over the years, I have led and contributed to multiple open-source tools, each designed to streamline the electronic structure workflow, from data generation to analysis and materials discovery.

- [PyProcar](https://github.com/romerogroup/pyprocar/): A widely adopted electronic structure pre and post-processing library to perform band structure, Fermi surface, density of states, and band unfolding calculations

- [MechElastic](https://github.com/romerogroup/MechElastic): A Python library for calculating mechanical and elastic properties of materials

- [mdwc3](https://github.com/romerogroup/mdwc3): A constrained molecular dynamics simulations code

- [PyChemia](https://github.com/MaterialsDiscovery/PyChemia): A Python library for materials search facilitating materials design and discovery

- [HybriD$^3$](https://materials.hybrid3.duke.edu): A materials database for hybrid organic-inorganic perovskites (HOIP) based on the [MatD$^3$](https://github.com/HybriD3-database/MatD3) Django framework. This database enables the curation and analysis of data to expedite the search for stable, high-efficiency photovoltaic materials.

- [FHI-aims](https://fhi-aims.org): An all-electron electronic structure theory with numeric atom-centered orbitals

- [ELSI](https://wordpress.elsi-interchange.org): A unified software interface designed for electronic structure codes to connect with various high-performance eigensolvers and density matrix solvers

My work also involves developing and establishing continuous integration (CI) pipelines, Docker, build systems, and unit testing to maintain streamlined collaborative code development environments.

# Modeling Earth's magnetosphere

In the early stages of my PhD, I explored the development and application of a HPC C/C++ particle tracer code to perform test particle simulations to quantify the effect of magnetic Field Line Curvature (FLC) scattering on the rapid loss of ring current ions in Earth’s magnetosphere.

# Mapping stellar populations with photometry methods

During my internship at the Arthur C. Clark Institute for Modern Technologies, I utilized telescopic data to construct a novel Color‐Magnitude Diagram (CMD) of the globular cluster M53, mapping Blue Straggler stars using CCD Aperture Photometry and PSF (Point Spread Function) Fitting Photometry methods with the IRAF (Image Reduction and Analysis Facility) system.
