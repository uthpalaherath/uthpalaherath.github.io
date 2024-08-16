---
title: Research
permalink: /research/
classes: wide
header:
    overlay_image: "/assets/images/beach.jpg"
    caption: "Photo by [Pasindu Dhananjaya](https://unsplash.com/@pasiiijay) on [Unsplash](https://unsplash.com)"
---

# Current Research (Postdoctoral Associate, Duke University)

My current research focuses on developing computational methods to study materials useful in novel semiconductor and renewable energy applications. Similar to my Ph.D. research this work also requires utilizing High-Performance Computing (HPC) and beyond-DFT methods including the GW approximation.

DFT is a successful theory in describing the ground state electronic structure properties of materials but lacks the physics required to explain the quasi-particle nature stemming from many-body interactions. The GW approximation, on the other hand, is a Green’s function based method that captures the dynamical nature of electrons which enables a pathway to explain the quasi-particle nature of particles. The term “GW” represents a one-body Green’s function G and a dynamically screened Coulomb interaction W. Since the GW approximation method provides quasi-particle excitation information, it has great use in the study of organic-inorganic hybrid perovskites used for novel semiconductor and photovoltaic applications. However, when dealing with heavy elements in such materials, relativistic effects are needed to be taken into account. Therefore, it is critical to incorporate spin-orbit coupling (SOC) effects into the periodic GW approximation. My current work involves implementing this within the DFT code FHI-aims and also ensuring its scalability to systems with a large number of atoms. Subsequently, this implementation would be employed in calculating electronic structure properties of organic-inorganic hybrid perovskites.


# Doctoral Research (Ph.D. Candidate, West Virginia University )

My Ph.D. research focused on employing High-Performance Computing (HPC) and High-Throughput Computing (HTC) to perform first principles *ab-initio* electronic structure calculations for bulk material and heterostructures, primarily focusing on strongly correlated materials (SCMs) using beyond-DFT quantum many body Green’s functions methods and Dynamical Mean Field Theory (DMFT).

## Summary of research interests

- Electronic structure methods :

  - Calculating electronic, magnetic, optical, elastic, mechanical, thermal and vibrational properties of strongly/weakly correlated material.
  - Performing molecular dynamics simulations of strongly/weakly correlated material.
  - Design and characterization of state-of-the-art novel material with remarkable emergent properties.
  - Study of defects, vacancies and alloying in SCMs.

- Interest in materials useful for high-temperature superconductivity, magnetism, colossal magnetoresistance, metalto insulator transitions, ferromagnetism, thermo-magnetic, spintronics, neuromorphic computing and energy applications.

- Collaborative development of frameworks to facilitate electronic structure calculations along with their pre and post-processing. E.g.-
    - [PyProcar](https://github.com/romerogroup/pyprocar/)
    - [DMFTwDFT](https://github.com/DMFTwDFT-project/DMFTwDFT)
    - [MechElastic](https://github.com/romerogroup/MechElastic)
    - [mdwc3](https://github.com/romerogroup/mdwc3)

The following is a brief description of SCMs and the methodologies I use to study them.

## Strongly Correlated Materials (SCMs)

The electronic correlations in materials drive a variety of fascinating phenomena from magnetism to superconductivity, which are due to the coupling between electron’s spin, charge, ionic displacements and orbital ordering. Although DFT is a very successful theory in describing the electronic structure of weakly interacting material systems, it fails to predict the properties of SCMs that include transition and rare earth metals where there  is  a  natural  strong  electron  localization  as  in  the  case  of  *d*  and  *f* orbitals due to the nature of their spatial confinement. They lead to a wide variety of astonishing phenomena in materials including magnetism, high-temperature superconductivity, colossal magnetoresistance, heavy fermion systems, metal to insulator transitions (Mott insulator) and thermomagnetism, all which have a profound impact on novel applications. These  correlated  electrons  cannot  be  studied  under  mean  field  approaches  since  their  interactions  on  each other are too prominent to be treated independently.

## Dynamical Mean Field Theory (DMFT)

<figure style="width: 50%" class="align-right">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/dmftwdft.png" alt="">
  <figcaption>The spectral function of the strongly correlated material SrVO3 calculated from DMFT</figcaption>
</figure>


Dynamical Mean Field Theory (DMFT) is a technique used to study these materials in which the Hubbard model is mapped to a local Anderson Impurity model and solved numerically using quantum Monte Carlo methods to capture both itinerant and localized nature of electrons. The initial self-energy is estimated from the self-consistent density obtained from DFT which is then projected into maximally localized Wannier functions (MLWF's) as the basis set which is then used to solve for the interacting DMFT density matrix. Full charge self-consistency is achieved by repeatedly updating the DFT and DMFT charge densities until they are both converged. This methodology accurately describes properties of strongly correlated materials where most DFT calculations fail.

Please see [projects](https://uthpalaherath.github.io/projects/) for several selected research performed on SCMs.

# Previous research

In the first year of grad school I did research on the computational modeling of Earth's radiation belts in which I studied different loss mechanisms of Ring Current ions. Test particle simulations were carried out to quantify cumulative Field Line Curvature (FLC) scattering of Ring Current ions. It was here where I was first introduced to employing high performance computing (HPC) to solve physics problems.

My bachelor's research project was done in collaboration with the Arthur C. Clark Institute for Modern Technologies- a leading research institute in Sri Lanka, where I was an intern. I did an extensive study of the stellar population in the globular cluster M53 using CCD Photometry techniques including Aperture Photometry and Point Spread Function (PSF) Fitting Photometry to construct a novel Color-Magnitude Diagram (CMD) of the cluster, which was in turn utilized to study its stellar population, mainly focusing on Blue Straggler Stars.

After finishing high school, I volunteered in a research project conducted by the Sri Lanka Department of Agriculture to develop a system for plant disease diagnosis. This would allow farmers around the island to use a software framework to self-diagnose and treat plant diseases. I assisted in computational aspects of this system.
