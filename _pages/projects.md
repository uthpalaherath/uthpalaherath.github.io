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
    title: "PyProcar"
    excerpt: "
    *A Python library for electronic structure pre/post-processing* <br><br>
    PyProcar is a robust, open-source Python library used for pre- and post-processing of the electronic structure data coming from DFT calculations. It provides a set of functions that manage data obtained from the PROCAR format. Basically, the PROCAR format is a projection of the Kohn-Sham states over atomic orbitals. That projection is performed to every k-point in the considered mesh, every energy band and every atom. PyProcar is capable of performing a multitude of tasks including plotting plain and spin/atom/orbital projected band structures and Fermi surfaces- both in 2D and 3D, Fermi velocity plots, unfolding bands of a super cell, comparing band structures from multiple DFT calculations, plotting partial density of states, filtering bands and generating a k-path for a given crystal structure. Currently supports VASP, Elk, Quantum Espresso, Abinit, Lobster, Siesta and DFTB+.<br><br>

    **Reference:**<br>
    1. Lang, L., Tavadze, P., Tellez, A., Bousquet, E., Xu, H., Muñoz, F., Vasquez, N., Herath, U., & Romero, A. H. Expanding PyProcar for new features,
maintainability, and reliability. Computer Physics Communications 297, 109063 (2024). DOI: [https://doi.org/10.1016/j.cpc.2023.109063](https://doi.org/10.1016/j.cpc.2023.109063)<br>
    2. Herath, U., Tavadze, P., He, X., Bousquet, E., Singh, S., Muñoz, F., & Romero, A. H. PyProcar: A Python library for electronic structure pre/post‑processing. Computer Physics Communications 251, 107080 (2020). DOI: [https://doi.org/10.1016/j.cpc.2019.107080](https://doi.org/10.1016/j.cpc.2019.107080)"
    url: "https://github.com/romerogroup/pyprocar/"
    btn_label: "Code"
    btn_class: "btn--primary"

feature_row2:
  - image_path: "/assets/images/projects/dmftwdft.svg"
    alt: "DMFTwDFT"
    title: "DMFTwDFT"
    excerpt: "
    *An open-source code combining Dynamical Mean Field Theory with various Density Functional Theory packages to study strongly correlated materials*<br><br>
    DMFTwDFT is an open-source, user-friendly framework developed in Python, Fortran and C/C++, combining DMFT with various DFT codes interfaced through the Wannier90 package. It allows users to perform full charge self-consistent DFT+DMFT calculations using minimal commands followed by post-processing functions including DMFT self-energy, total energy, band structures, projected DOS, and effective mass enhancements. DMFTwDFT uses Wannier orbitals for constructing the hybridization and correlation subspaces to perform DMFT loops by taking advantage of the Wannier90 interface between various DFT codes. It also equips a library mode to link the module for computing a DMFT density matrix and updating a charge density within the DFT loops allowing implementing full charge self-consistency within various DFT codes without modifying their source codes significantly. Currently supports VASP, Quantum Espresso (one-shot DMFT), and Siesta (one-shot DMFT). <br><br>

    **Reference:**<br>
    Singh, V., Herath, U., Wah, B., Liao, X., Romero, A. H., & Park, H. DMFTwDFT: An open‑source code combining Dynamical Mean Field Theory with various density functional theory packages. Computer Physics Communications 261, 107778 (2021). DOI: [https://doi.org/10.1016/j.cpc.2020.107778](https://doi.org/10.1016/j.cpc.2020.107778)"
    url: "https://github.com/DMFTwDFT-project/DMFTwDFT"
    btn_label: "Code"
    btn_class: "btn--primary"

feature_row3:
  - image_path: "/assets/images/projects/mechelastic.svg"
    alt: "MechElastic"
    title: "MechElastic"
    excerpt: "
    *A Python Library for Analysis of Mechanical and Elastic Properties of Bulk and 2D Materials*<br><br>
    MechElastic allows users to calculate several important physical properties such as elastic moduli, melting temperature, Debye temperature, elastic wave velocities, elastic anisotropy, etc. for all crystalline 2D and 3D systems using output data from an elastic tensor calculation. It can also be used to test the mechanical stability of any bulk system. Additionally, MechElastic allows performing Equation of State (EOS) analysis provided inputs of Volume and Energy or Volume and Pressure and automatically provides information on phase transitions. Currently supports VASP, Abinit and Quantum Espresso.

    <br><br>

    **Reference:**<br>
    Singh, S., Lang, L., Dovale‑Farelo, V., Herath, U., Tavadze, P., Coudert, F.‑X., & Romero, A. H. MechElastic: A Python library for analysis of mechanical and elastic properties of bulk and 2D materials. Computer Physics Communications 267, 108068 (2021). DOI: [https://doi.org/10.1016/j.cpc.2021.108068](https://doi.org/10.1016/j.cpc.2021.108068)"
    url: "https://github.com/romerogroup/MechElastic"
    btn_label: "Code"
    btn_class: "btn--primary"

feature_row4:
  - image_path: "/assets/images/projects/aims.svg"
    alt: "FHI-aims"
    title: "FHI-aims"
    excerpt: "
    *An all-electron electronic structure theory with numeric atom-centered orbitals*<br><br>
    FHI-aims is an all-electron electronic structure code based on numeric atom-centered orbitals. It enables first-principles simulations with very high numerical accuracy for production calculations, with excellent scalability up to very large system sizes (thousands of atoms) and up to very large, massively parallel supercomputers (ten thousand CPU cores).<br><br>

    **Reference:**<br>
    V. Blum, R. Gehrke, F. Hanke, P. Havu, V. Havu, X. Ren, K. Reuter, and M. Scheffler, Ab initio molecular simulations with numeric atom-centered orbitals, Computer Physics Communications 180, 2175 (2009). DOI: [https://doi.org/10.1016/j.cpc.2009.06.022](https://doi.org/10.1016/j.cpc.2009.06.022)"
    url: "https://fhi-aims.org"
    btn_label: "Code"
    btn_class: "btn--primary"

feature_row5:
  - image_path: "/assets/images/projects/elsi.png"
    alt: "ELSI"
    title: "ELSI (ELectronic Structure Infrastructure)"
    excerpt: "
    *A unified software interface designed for electronic structure codes to connect with various high-performance eigensolvers and density matrix solvers*<br><br>
    ELSI provides and enhances scalable, open-source software library solutions for electronic structure calculations in materials science, condensed matter physics, chemistry, and many other fields. ELSI focuses on methods that solve or circumvent eigenvalue problems in electronic structure theory. The ELSI infrastructure should also be useful for other challenging eigenvalue problems.<br><br>

    **Reference:**<br>
    1. V. W. Yu et al., ELSI — An open infrastructure for electronic structure solvers, Computer Physics Communications 256, 107459 (2020). DOI: [https://doi.org/10.1016/j.cpc.2020.107459](https://doi.org/10.1016/j.cpc.2020.107459)<br>
    2. V. W. Yu et al., ELSI: A unified software interface for Kohn–Sham electronic structure solvers, Computer Physics Communications 222, 267 (2018). DOI: [https://doi.org/10.1016/j.cpc.2017.09.007](https://doi.org/10.1016/j.cpc.2017.09.007)"
    url: "https://wordpress.elsi-interchange.org"
    btn_label: "Code"
    btn_class: "btn--primary"

feature_row6:
  - image_path: "/assets/images/projects/hybrid3.png"
    alt: "HybriD3"
    title: "HybriD3"
    excerpt: "
    *A curatable database for experimental and theoretical data on hybrid organic-inorganic materials*<br><br>
    Hybrid organic-inorganic materials offer a unique opportunity for the discovery and refinement of new functional semiconductor materials with fine-tuned properties, controlled at the atomic scale by organic chemistry and organic-inorganic synthesis and processing. The HybriD$^3$ project accelerates the Design, Discovery and Dissemination (D3) of new crystalline organic-inorganic hybrid semiconductors in a collaborative effort between a consortium of researchers in the NC Triangle area and beyond. It is based on the MatD$^3$ framework written in Python-Django and uses SQL for database functions.<br><br>

    **Reference:**<br>
    R. Laasner, X. Du, A. Tanikanti, C. Clayton, M. Govoni, G. Galli, M. Ropo, and V. Blum, MatD$^3$: A Database and Online Presentation Package for Research Data Supporting Materials Discovery, Design, and Dissemination, JOSS 5, 1945 (2020). DOI: [https://doi.org/10.21105/joss.01945](https://doi.org/10.21105/joss.01945)"
    url: "https://materials.hybrid3.duke.edu"
    btn_label: "Database"
    btn_class: "btn--primary"

feature_row7:
  - image_path: "/assets/images/projects/springer-materials.png"
    alt: "Springer Materials"
    title: "Springer Materials"
    excerpt: "
    *The research solution for identifying material properties*<br><br>
    Springer Materials provides curated data and advanced functionalities to support research in materials science, physics, chemistry, engineering, and other related fields."
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

feature_row10:
  - image_path: "/assets/images/projects/pychemia.png"
    alt: "PyChemia"
    title: "PyChemia"
    excerpt: "PyChemia is an open-source Python library for materials structural search providing an agnostic framework for materials discovery and design using a variety of methods from Minima Hoping to Soft-computing based methods. PyChemia is also a library for data-mining, using several methods to discover interesting candidates among the materials already processed. Currently supports VASP, ABINIT, Octopus, DFTB+, and Fireball."
    url: "https://github.com/MaterialsDiscovery/PyChemia"
    btn_label: "Code"
    btn_class: "btn--primary"

feature_row11:
  - image_path: "/assets/images/projects/mdwc3.gif"
    alt: "mdwc3"
    title: "mdwc3"
    excerpt: "The molecular dynamics with constraints (mdwc3) package is a command line open source Python program for molecular dynamics simulations. It performs constraint MD simulations with either NPT (keeping pressure constant with the Parrinello Rahman lagrangian, and keeping the temperature constant with the Nose thermostat) or NVT (keeping the temperature constant with the Nose thermostat). mdwc3 performs constraint MD simulations following the SHAKE algorithm and allows constraints for bond distances, angles, atomic positions, lattice parameters (a, b, c), angles between lattice vectors, and volume of the unit cell."
    url: "https://github.com/romerogroup/mdwc3"
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
{% include feature_row id="feature_row10" type="left" %}
{% include feature_row id="feature_row11" type="left" %}
