---
layout: single
title: Projects
permalink: /projects/
header:
    overlay_color: "#000"
    overlay_image: "/assets/images/beach.jpg"
    caption: "Photo by [Pasindu Dhananjaya](https://unsplash.com/@pasiiijay) on [Unsplash](https://unsplash.com)"
---

Here's a summary of some projects I've been working on. Some of them are with research collaboratos from around the world. They range from Density Functional Theory (DFT) pre and post processing tools to handy scripts that make everyday life smoother. 
Please feel free to contact me about any of them. 

## PyProcar: A Python library for electronic structure pre/post-processing

<img src="/assets/images/pyprocar.jpg">

**Description:** PyProcar is a robust, open-source Python library used for pre- and post-processing of the electronic structure data coming from DFT calculations. PyProcar provides a set of functions that manage the PROCAR file obtained from Vasp and Abinit. Basically, the PROCAR file is a projection of the Kohn-Sham states over atomic orbitals. That projection is performed to every k-point in the considered mesh, every energy band and every atom. PyProcar is capable of performing a multitude of tasks including plotting plain and spin/atom/orbital projected band structures and Fermi surfaces- both in 2D and 3D, Fermi velocity plots, unfolding bands of a super cell, comparing band structures from multiple DFT calculations and generating a k-path for a given crystal structure.

**tags:** dft, python, materialsphysics

**Code:** [Github](https://github.com/romerogroup/pyprocar/)

**Read more:** [Article](https://www.sciencedirect.com/science/article/pii/S0010465519303935)

## DMFTwDFT: An open-source code combining Dynamical Mean Field Theory with various Density Functional Theory packages

<img src="/assets/images/dmftwdft.png">

**Description:** Dynamical Mean Field Theory (DMFT) is a successful method to compute the electronic structure of strongly correlated materials, especially when it is combined with density functional theory (DFT). Here, we present an open-source computational package (and a library) combining DMFT with various DFT codes interfaced through the Wannier90 package. The correlated subspace is expanded as a linear combination of Wannier functions introduced in the DMFT approach as local orbitals. In particular, we provide a library mode for computing the DMFT density matrix. This library can be linked and then internally called from any DFT package, assuming that a set of localized orbitals can be generated in the correlated subspace. The existence of this library allows developers of other DFT codes to interface with our package and achieve the charge-self-consistency within DFT+DMFT loops. To test and check our implementation, we computed the density of states and the band structure of well-known correlated materials, namely LaNiO3, SrVO3, and NiO. The obtained results are compared to those obtained from other DFT+DMFT implementations.

**tags:** manybodyphysics, materialsphysics, dmft, dft 

**Code:** [Github](https://github.com/DMFTwDFT-project/DMFTwDFT)

**Read more:** [Article](https://arxiv.org/abs/2002.00068)




