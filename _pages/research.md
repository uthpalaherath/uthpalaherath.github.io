---
title: Research
permalink: /research/
classes: wide
header:
    overlay_image: "/assets/images/beach.jpg"
    caption: "Photo by [Pasindu Dhananjaya](https://unsplash.com/@pasiiijay) on [Unsplash](https://unsplash.com)"
---

Here's a brief description about the research I'm involved with. 

### Strongly Correlated Materials 

The electronic correlations in materials drive a variety of fascinating phenomena from magnetism to superconductivity, which are due to the coupling between electron’s spin, charge, ionic displacements and orbital ordering. Although DFT is a very successful theory in describing the electronic structure of weakly interacting material systems, it fails to predict the properties of SCM’s that include transition and rare earth metals where there  is  a  natural  strong  electron  localization  as  in  the  case  of  *d*  and  *f* orbitals due to the nature of their spatial confinement. They lead to a wide variety of astonishing phenomena in materials including magnetism, high-temperature superconductivity, colossal magnetoresistance, heavy fermion systems, metal to insulator transitions (Mott insulator) and thermomagnetism, all which have a profound impact on novel applications. These  correlated  electrons  cannot  be  studied  under  mean  field  approaches  since  their  interactions  on  each other are too prominent to be treated independently. 

### Dynamical Mean Field Theory

<figure style="width: 50%" class="align-right">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/dmftwdft.png" alt="">
  <figcaption>The spectral function of SrVO3 calculated from DMFT</figcaption>
</figure> 


Dynamical Mean Field Theory (DMFT) is a technique used to study these materials in which the Hubbard model is mapped to a local Anderson Impurity model and solved numerically using quantum Monte Carlo methods to capture both itinerant and localized nature of electrons. The initial self-energy is estimated from the self-consistent density obtained from DFT which is then projected into maximally localized Wannier functions (MLWF's) as the basis set which is then used to solve for the interacting DMFT density matrix. Full charge self-consistency is achieved by repeatedly updating the DFT and DMFT charge densities until they are both converged. This methodology accurately describes properties of strongly correlated materials where most DFT calculations fail. 

Here's a list of research projects I'm currently working on. A detailed description of these can be found in [Projects](/projects/).

- The development of the DMFTwDFT framework to characterize strongly correlated materials
- An ab-initio DFT+DMFT study of the effect of oxygen vacancies on structural, electronic and magnetic properties of rare-earth nickelate perovskites
- PyProcar: A Python library for electronic structure pre/post-processing
- MDWC -A Molecular Dynamics simulation library
- Employing Virtual Crystal Approximation (VCA) with DMFT to study strongly correlated alloys/defects


