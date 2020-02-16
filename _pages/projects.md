---
layout: single
title: Projects
permalink: /projects/
header:
    overlay_color: "#000"
    overlay_image: "/assets/images/beach.jpg"
    caption: "Photo by [Pasindu Dhananjaya](https://unsplash.com/@pasiiijay) on [Unsplash](https://unsplash.com)"
excerpt: 

feature_row1:
  - image_path: /assets/images/pyprocar.jpg
    alt: "PyProcar"
    title: "PyProcar: A Python library for electronic structure pre/post-processing" 
    text: "PyProcar is a robust, open-source Python library used for pre- and post-processing of the electronic structure data coming from DFT calculations. PyProcar provides a set of functions that manage the PROCAR file obtained from Vasp and Abinit. Basically, the PROCAR file is a projection of the Kohn-Sham states over atomic orbitals. That projection is performed to every k-point in the considered mesh, every energy band and every atom. PyProcar is capable of performing a multitude of tasks including plotting plain and spin/atom/orbital projected band structures and Fermi surfaces- both in 2D and 3D, Fermi velocity plots, unfolding bands of a super cell, comparing band structures from multiple DFT calculations and generating a k-path for a given crystal structure."
    url: "https://github.com/romerogroup/pyprocar/"
    btn_label: "Code"
    btn_class: "btn--primary"
    url2: "https://www.sciencedirect.com/science/article/pii/S0010465519303935"
    btn_label2: "Read more"
    btn_class2: "btn--primary" 
    tags: 
        - dft
        - python
        - materialsphysics

feature_row2:
  - image_path: /assets/images/dmftwdft.png
    alt: "DMFTwDFT"
    title: "DMFTwDFT: An open-source code combining Dynamical Mean Field Theory with various Density Functional Theory packages"
    text: "Dynamical Mean Field Theory (DMFT) is a successful method to compute the electronic structure of strongly correlated materials, especially when it is combined with density functional theory (DFT). Here, we present an open-source computational package (and a library) combining DMFT with various DFT codes interfaced through the Wannier90 package. The correlated subspace is expanded as a linear combination of Wannier functions introduced in the DMFT approach as local orbitals. In particular, we provide a library mode for computing the DMFT density matrix. This library can be linked and then internally called from any DFT package, assuming that a set of localized orbitals can be generated in the correlated subspace. The existence of this library allows developers of other DFT codes to interface with our package and achieve the charge-self-consistency within DFT+DMFT loops. To test and check our implementation, we computed the density of states and the band structure of well-known correlated materials, namely LaNiO3, SrVO3, and NiO. The obtained results are compared to those obtained from other DFT+DMFT implementations."
    url: "https://github.com/DMFTwDFT-project/DMFTwDFT"
    btn_label: "Code"
    btn_class: "btn--primary"
    url2: "https://arxiv.org/abs/2002.00068"
    btn_label2: "Read more"
    btn_class2: "btn--primary"
    tags: 
    - manybodyphysics
    - materialsphysics 
    - dmft
    - dft 

---

Here's a summary of some projects I've been working on. Some of them are with research collaboratos from around the world. They range from Density Functional Theory (DFT) pre and post processing tools to handy scripts that make everyday life smoother. 
Please feel free to contact me about any of them. 

{% include feature_row id="feature_row1" type="left" %}
{% include feature_row id="feature_row2" type="left" %}



