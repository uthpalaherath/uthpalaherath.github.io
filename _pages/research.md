---
title: Research
permalink: /research/
classes: wide
header:
    overlay_image: "/assets/images/beach.jpg"
    caption: "Photo by [Pasindu Dhananjaya](https://unsplash.com/@pasiiijay) on [Unsplash](https://unsplash.com)"
---

My primary area of research is employing High Performance Computing with Density Functional Theory (DFT) and beyond DFT methods to study a class of materials known as Strongly Correlated Materials (SCM). The following is a brief description of SCM and the methodologies I use to study them.

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



### Honors & Awards

- **Robert T. Bruhn Physics Research Award** (2020)
  Funding to support the research effort of a graduate or undergraduate student in the Department of Physics and Astronomy in nanotechnology and material science.

- **Office of the Provost Graduate Student Travel Award** (2018)
  Awarded by the Office of the Provost, West Virginia University to fund travel to research conferences.

- **Eberly College of Arts and Sciences Graduate Student Travel Award** (2018)
  Awarded by the Eberly College of Arts and Sciences, West Virginia University to fund travel to research conferences.



### Publications

Please visit my [Google Scholar](https://scholar.google.com/citations?user=m6VPFYoAAAAJ&hl=en&authuser=1) profile for an updated list of publications. 

1. **Herath, U.**, Tavadze, P., He, X., Bousquet, E., Singh, S., Muñoz, F. & Romero, A. H. PyProcar: A Python library for electronic structure pre/post-processing. *Computer Physics Communications* 251, 107080. doi:https://doi.org/10.1016/j.cpc.2019.107080 (2020).
2. Singh, V., **Herath, U**., Wah, B., Liao, X., Romero, A. H. & Park, H. DMFTwDFT: An Open-Source Code Combining Dynamical Mean Field Theory with Various Density Functional Theory Packages. *Computer Physics Communications*, 107778. doi:10.1016/j.cpc.2020.107778 (Dec. 2020).
3. Singh, S., Lang, L., Dovale-Farelo, V., **Herath, U.**, Tavadze, P., Coudert, F.-X. & Romero, A. H. MechElastic: A Python Library for Analysis of Mechanical and Elastic Properties of Bulk and 2D Materials 2020. *arXiv: 2012.04758 [cond-mat.mtrl-sci]*.
4. Herath, A. & **Herath, U.** Developing an Expert System for Plant Pest Diagnosis. *Annals of the Sri Lanka Department of Agriculture* 15, 381 (2012).

#### In progress

5. **Herath, U.**, Singh, V., Wah, B., Park, H. & Romero, A. H. A site occupation disorder study of oxygen vacancies in LaNiO3.

### Presentations

- Uthpala Herath, Vijay Singh, Benny Wah, Xingyu Liao, Hyowon Park and Aldo H. Romero 

  *“DMFTwDFT: An open-source code combining Dynamical Mean Field Theory with various Density Functional Theory packages”*
  APS Mid Atlantic Section Meeting, December 4-6, 2020 (VIRTUAL TALK)

- Uthpala Herath, Pedram Tavadze, Xu He, Eric Bousquet, Sobhit Singh, Francisco Muñoz, and Aldo H. Romero 

  *“Recent developments in PyProcar: A Python library for electronic structure pre/post-processing”*
  Carolina Science Symposium, Nov 12-13, 2020 (VIRTUAL TALK)

- Uthpala Herath, Pedram Tavadze, Xu He, Eric Bousquet, Sobhit Singh, Francisco Muñoz, and Aldo H. Romero 

  *“PyProcar: A Python library for electronic structure pre/post-processing”*
   Electronic Structure Workshop, June, 2020, University of California, Merced (VIRTUAL TALK)

- Uthpala Herath, Pedram Tavadze, Xu He, Eric Bousquet, Sobhit Singh, Francisco Muñoz, and Aldo H. Romero

  *“PyProcar: A Python library for electronic structure pre/post-processing”*
  APS March Meeting, March 4-8, 2019, Boston, MA (TALK)

- Uthpala Herath, Hyowon Park and Aldo H. Romero
  *“Development of computational methods for the characterization of novel strongly correlated materials”*

  International Summer School on Computational Quantum Materials, June 2018, Sherbrooke, Québec, Canada (POSTER)

- Uthpala Herath and Weichao Tu
   *“The Effect of Magnetic Field Line Curvature Scattering on the Rapid Loss of Ring Current Ions”*

  Geospace Environment Modeling (GEM) conference, July 2017, Portsmouth, VA (POSTER)

