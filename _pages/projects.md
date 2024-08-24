---
permalink: /projects/
layout: single
classes: wide
title: Projects
header:
    overlay_image: "/assets/images/beach.jpg"
    caption: "Photo by [Pasindu Dhananjaya](https://unsplash.com/@pasiiijay) on [Unsplash](https://unsplash.com)"

feature_row1:
  - image_path: "/assets/images/pyprocar.png"
    alt: "PyProcar"
    title: "PyProcar: A Python library for electronic structure pre/post-processing"
    excerpt: "PyProcar is a robust, open-source Python library used for pre- and post-processing of the electronic structure data coming from DFT calculations."
    url: "https://github.com/romerogroup/pyprocar/"
    btn_label: "Read More"
    btn_class: "btn--primary"

feature_row2:
  - image_path: "/assets/images/dmftwdft.png"
    alt: "DMFTwDFT"
    title: "DMFTwDFT: An open-source code combining Dynamical Mean Field Theory with various Density Functional Theory packages"
    excerpt: "An open-source computational package (and a library) combining DMFT with various DFT codes interfaced through the Wannier90 package."
    url: "https://github.com/DMFTwDFT-project/DMFTwDFT"
    btn_label: "Read More"
    btn_class: "btn--primary"

feature_row3:
  - image_path: "/assets/images/mechelastic.png"
    alt: "MechElastic"
    title: "MechElastic: A Python Library for Analysis of Mechanical and Elastic Properties of Bulk and 2D Materials"
    excerpt: "A Python library to calculate elastic properties of materials."
    url: "https://github.com/romerogroup/MechElastic"
    btn_label: "Read More"
    btn_class: "btn--primary"

feature_row4:
  - image_path: "/assets/images/aims.svg"
    alt: "FHI-aims"
    title: "FHI-aims: An all-electron electronic structure theory with numeric atom-centered orbitals."
    excerpt: "FHI-aims is an all-electron electronic structure code based on numeric atom-centered orbitals. It enables first-principles simulations with very high numerical accuracy for production calculations, with excellent scalability up to very large system sizes (thousands of atoms) and up to very large, massively parallel supercomputers (ten thousand CPU cores)."
    url: "https://fhi-aims.org"
    btn_label: "Read More"
    btn_class: "btn--primary"

feature_row5:
  - image_path: "/assets/images/elsi.png"
    alt: "ELSI"
    title: "ELSI (ELectronic Structure Infrastructure): A unified software interface designed for electronic structure codes to connect with various high-performance eigensolvers and density matrix solvers."
    excerpt: "ELSI provides and enhances scalable, open-source software library solutions for electronic structure calculations in materials science, condensed matter physics, chemistry, and many other fields. ELSI focuses on methods that solve or circumvent eigenvalue problems in electronic structure theory. The ELSI infrastructure should also be useful for other challenging eigenvalue problems."
    url: "https://wordpress.elsi-interchange.org"
    btn_label: "Read More"
    btn_class: "btn--primary"
---
The following is a list of individual and collaborative research projects.
More projects can be found on my [Github](https://github.com/uthpalaherath) along with Github organizations I have contributed to.

{% include feature_row id="feature_row1" type="left" %}
{% include feature_row id="feature_row2" type="left" %}
{% include feature_row id="feature_row3" type="left" %}
{% include feature_row id="feature_row4" type="left" %}
{% include feature_row id="feature_row5" type="left" %}
