---
permalink: /projects/
layout: single
classes: wide
title: Projects
header:
    overlay_image: "/assets/images/beach.jpg"
    caption: "Photo by [Pasindu Dhananjaya](https://unsplash.com/@pasiiijay) on [Unsplash](https://unsplash.com)"

feature_row1:
  - image_path: "/assets/images/projects/pyprocar.png"
    alt: "PyProcar"
    title: "PyProcar: A Python library for electronic structure pre/post-processing"
    excerpt: "PyProcar is a robust, open-source Python library used for pre- and post-processing of the electronic structure data coming from DFT calculations."
    url: "https://github.com/romerogroup/pyprocar/"
    btn_label: "Code"
    btn_class: "btn--primary"

feature_row2:
  - image_path: "/assets/images/projects/dmftwdft_logo.png"
    alt: "DMFTwDFT"
    title: "DMFTwDFT: An open-source code combining Dynamical Mean Field Theory with various Density Functional Theory packages"
    excerpt: "An open-source computational package (and a library) combining DMFT with various DFT codes interfaced through the Wannier90 package."
    url: "https://github.com/DMFTwDFT-project/DMFTwDFT"
    btn_label: "Code"
    btn_class: "btn--primary"

feature_row3:
  - image_path: "/assets/images/projects/mechelastic.png"
    alt: "MechElastic"
    title: "MechElastic: A Python Library for Analysis of Mechanical and Elastic Properties of Bulk and 2D Materials"
    excerpt: "A Python library to calculate elastic properties of materials."
    url: "https://github.com/romerogroup/MechElastic"
    btn_label: "Code"
    btn_class: "btn--primary"

feature_row4:
  - image_path: "/assets/images/projects/aims.svg"
    alt: "FHI-aims"
    title: "FHI-aims: An all-electron electronic structure theory with numeric atom-centered orbitals."
    excerpt: "FHI-aims is an all-electron electronic structure code based on numeric atom-centered orbitals. It enables first-principles simulations with very high numerical accuracy for production calculations, with excellent scalability up to very large system sizes (thousands of atoms) and up to very large, massively parallel supercomputers (ten thousand CPU cores)."
    url: "https://fhi-aims.org"
    btn_label: "Code"
    btn_class: "btn--primary"

feature_row5:
  - image_path: "/assets/images/projects/elsi.png"
    alt: "ELSI"
    title: "ELSI (ELectronic Structure Infrastructure): A unified software interface designed for electronic structure codes to connect with various high-performance eigensolvers and density matrix solvers."
    excerpt: "ELSI provides and enhances scalable, open-source software library solutions for electronic structure calculations in materials science, condensed matter physics, chemistry, and many other fields. ELSI focuses on methods that solve or circumvent eigenvalue problems in electronic structure theory. The ELSI infrastructure should also be useful for other challenging eigenvalue problems."
    url: "https://wordpress.elsi-interchange.org"
    btn_label: "Code"
    btn_class: "btn--primary"

feature_row6:
  - image_path: "/assets/images/projects/hybrid3.png"
    alt: "HybriD3"
    title: "HybriD3: A curatable database for experimental and theoretical data on hybrid organic-inorganic materials."
    excerpt: "Hybrid organic-inorganic materials offer a unique opportunity for the discovery and refinement of new functional semiconductor materials with fine-tuned properties, controlled at the atomic scale by organic chemistry and organic-inorganic synthesis and processing. The HybriD3 project accelerates the Design, Discovery and Dissemination (D3) of new crystalline organic-inorganic hybrid semiconductors in a collaborative effort between a consortium of researchers in the NC Triangle area and beyond."
    url: "https://materials.hybrid3.duke.edu"
    btn_label: "Database"
    btn_class: "btn--primary"

feature_row7:
  - image_path: "/assets/images/projects/springer-materials.png"
    alt: "Springer Materials"
    title: "Springer Materials: The research solution for identifying material properties. "
    excerpt: "Springer Materials provides curated data and advanced functionalities to support research in materials science, physics, chemistry, engineering, and other related fields."
    url: "https://materials.springer.com"
    btn_label: "Database"
    btn_class: "btn--primary"

feature_row8:
  - image_path: "/assets/images/projects/spei.jpg"
    alt: "convertSPEI"
    title: "convertSPEI"
    excerpt: "This program converts time series Standardised Precipitation-Evapotranspiration Index (SPEI) data from the netcdf format to a csv format which could be read by a program such as Excel. It is parallelized through Python's multiprocessing library. The SPEI data is available at [https://spei.csic.es/index.html](https://spei.csic.es/index.html)."
    url: "https://github.com/uthpalaherath/convertSPEI"
    btn_label: "Code"
    btn_class: "btn--primary"

feature_row9:
  - image_path: "/assets/images/projects/NEBgen.png"
    alt: "NEBgen"
    title: "NEBgen"
    excerpt: "NEBgen prepares POSCAR's for Nudged Elastic Band (NEB) calculations through Distortion Symmetry Method with [VTST](http://theory.cm.utexas.edu/vtsttools/) and [DiSPy](https://github.com/munrojm/DiSPy). The nudged elastic band (NEB) method is a popular method for calculating the minimum energy pathways of kinetic processes. Although, linear interpolation between an initial and final structure (image) provides a decent estimate for the minimum energy pathway, the Distortion Symmetry Method takes into account symmetry-adapted perturbations to systematically lower the initial path symmetry, enabling the exploration of other low-energy pathways that may exist."
    url: "https://github.com/uthpalaherath/NEBgen"
    btn_label: "Code"
    btn_class: "btn--primary"

---
The following is a list of research projects I have contributed to.

{% include feature_row id="feature_row1" type="left" %}
{% include feature_row id="feature_row2" type="left" %}
{% include feature_row id="feature_row3" type="left" %}
{% include feature_row id="feature_row4" type="left" %}
{% include feature_row id="feature_row5" type="left" %}
{% include feature_row id="feature_row6" type="left" %}
{% include feature_row id="feature_row7" type="left" %}
{% include feature_row id="feature_row8" type="left" %}
{% include feature_row id="feature_row9" type="left" %}
