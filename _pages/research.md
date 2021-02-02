---
title: Research
permalink: /research/
classes: wide
header:
    overlay_image: "/assets/images/beach.jpg"
    caption: "Photo by [Pasindu Dhananjaya](https://unsplash.com/@pasiiijay) on [Unsplash](https://unsplash.com)"
---

My research focuses on the computational modeling of state-of-the-art novel material using high performance computing. I mainly study a class of materials known as Strongly Correlated Materials (SCM's) using Density Functional Theory (DFT) and Quantum Many Body methods including Dynamical Mean Field Theory (DMFT) while actively collaborating with experimental groups which perform synthesis of these remarkable materials. I am also involved with code development projects which facilitate the pre and post processing of electronic structure calculations. The following is a brief description of SCM and the methodologies I use to study them.


### Strongly Correlated Materials

The electronic correlations in materials drive a variety of fascinating phenomena from magnetism to superconductivity, which are due to the coupling between electron’s spin, charge, ionic displacements and orbital ordering. Although DFT is a very successful theory in describing the electronic structure of weakly interacting material systems, it fails to predict the properties of SCM’s that include transition and rare earth metals where there  is  a  natural  strong  electron  localization  as  in  the  case  of  *d*  and  *f* orbitals due to the nature of their spatial confinement. They lead to a wide variety of astonishing phenomena in materials including magnetism, high-temperature superconductivity, colossal magnetoresistance, heavy fermion systems, metal to insulator transitions (Mott insulator) and thermomagnetism, all which have a profound impact on novel applications. These  correlated  electrons  cannot  be  studied  under  mean  field  approaches  since  their  interactions  on  each other are too prominent to be treated independently.

### Dynamical Mean Field Theory

<figure style="width: 50%" class="align-right">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/dmftwdft.png" alt="">
  <figcaption>The spectral function of the strongly correlated material SrVO3 calculated from DMFT</figcaption>
</figure>


Dynamical Mean Field Theory (DMFT) is a technique used to study these materials in which the Hubbard model is mapped to a local Anderson Impurity model and solved numerically using quantum Monte Carlo methods to capture both itinerant and localized nature of electrons. The initial self-energy is estimated from the self-consistent density obtained from DFT which is then projected into maximally localized Wannier functions (MLWF's) as the basis set which is then used to solve for the interacting DMFT density matrix. Full charge self-consistency is achieved by repeatedly updating the DFT and DMFT charge densities until they are both converged. This methodology accurately describes properties of strongly correlated materials where most DFT calculations fail.

Research interests:

- The development of the DMFTwDFT framework to characterize strongly correlated materials
- An ab-initio DFT+DMFT study of the effect of oxygen vacancies on structural, electronic and magnetic properties of rare-earth nickelate perovskites
- PyProcar: A Python library for electronic structure pre/post-processing
- MDWC -A Molecular Dynamics simulation library developed by our group
- Employing Virtual Crystal Approximation (VCA) with DMFT to study strongly correlated alloys/defects


### Previous research

In the first year of grad school I did research on the computational modeling of Earth's radiation belts in which I studied different loss mechanisms of Ring Current ions. Test particle simulations were carried out to quantify cumulative Field Line Curvature (FLC) scattering of Ring Current ions. It was here where I was first introduced to employing high performance computing (HPC) to solve physics problems. 

My bachelor's research project was done in collaboration with the Arthur C. Clark Institute for Modern Technologies- a leading research institute in Sri Lanka, where I was an intern. I did an extensive study of the stellar population in the globular cluster M53 using CCD Photometry techniques including Aperture Photometry and Point Spread Function (PSF) Fitting Photometry to construct a novel Color-Magnitude Diagram (CMD) of the cluster, which was in turn utilized to study its stellar population, mainly focusing on Blue Straggler Stars.  

After finishing high school, I volunteered in a research project conducted by the Sri Lanka Department of Agriculture to develop a system for plant disease diagnosis. This would allow farmers around the island to use a software framework to self-diagnose and treat plant diseases. I assisted in computational aspects of this system.




