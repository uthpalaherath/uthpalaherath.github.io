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

### Publications

- Uthpala Herath, Pedram Tavadze, Xu He, Eric Bousquet, Sobhit Singh, Francisco Muñoz, and Aldo H. Romero. **PyProcar: A Python library for electronic structure pre/post-processing**. *Computer Physics Communications 251 (2020): 107080*.
[doi:10.1016/j.cpc.2019.107080](https://www.sciencedirect.com/science/article/pii/S0010465519303935)
- Singh, V., Herath, U., Wah, B., Liao, X., Romero, A., Park, H., **DMFTwDFT: An open-source code combining Dynamical Mean Field Theory with various Density Functional Theory packages.** *Submitted to Computer Physics Communications (2020).*
[arXiv:2002.00068](https://arxiv.org/abs/2002.00068)
- Herath, A., Herath, U.K., **Developing an Expert System for Plant Pest Diagnosis**, *Annals of the Sri Lanka Department of Agriculture Vol.15:381 (Aug, 2012).*

### Presentations

- **TALK:** Herath, U.,  Park, H., Romero, A.,  **An ab-initio DFT+DMFT study of the effect of oxygen vacancies on structural, electronic and magnetic properties of rare-earth nickelate perovskites (RNiO3)**, *APS March Meeting, Boston, MA (March, 2019)*
- **POSTER:**  Herath, U., Park, H., Romero, A., **Development of computational methods for the characterization of novel strongly correlated materials**, *International Summer School on Computational Quantum Materials - Sherbrooke, Québec, Canada (June, 2018)*
- **POSTER:** Herath, U., Tu, W., **The Effect of Magnetic Field Line Curvature Scattering on the Rapid Loss of Ring Current Ions**, *Geospace Environment Modeling (GEM) conference - Portsmouth, VA (July, 2017)*
