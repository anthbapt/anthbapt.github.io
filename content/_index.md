---
title: ''
summary: ''
date: 2026-04-17
type: landing

design:
  spacing: '6rem'

sections:
  - block: resume-biography-3
    content:
      username: me
      text: ''
      button:
        text: Download CV
        url: uploads/resume.pdf
    design:
      background:
        gradient_mesh:
          enable: true
      name:
        size: md
      avatar:
        size: medium
        shape: circle

  - block: markdown
    content:
      title: '🔬 My Research'
      subtitle: ''
      text: |-
        My work focuses on tumour microenvironments through the lens of spatial transcriptomics and network biology. I develop computational methods that integrate multi-modal spatial data, graph theory, and machine learning to map how cancer cells interact with their immune neighbourhood.

        Current projects include the **METABRIC-MX** platform for multimodal breast cancer spatial analysis, the **MOSAIK** toolkit for cross-platform spatial transcriptomics integration, and a **Cell-cell communications** project establishing a mathematical equivalence between PDE-based models and random walk with restart on spatial graphs (details currently under NDA).

        I'm always open to collaboration — feel free to [reach out](mailto:anthony.baptista@kcl.ac.uk).
    design:
      columns: '1'

  - block: markdown
    id: news
    content:
      title: '📣 Latest News'
      subtitle: ''
      text: |-
        - **Jan 2026** — Awarded £10,000 DisCouRSE Flexible Fund for the **SpatiaLondon Network** project (with A. Vigilante, N. Matthews, M. Del Pilar Acedo Nunez, F. Ciccarelli, I. Sequeira).
        - **May 2025** — Poster prize at the KCL School of Cancer & Pharmaceutical Sciences Annual Symposium.
        - **2024** — Co-PI on the OpnMe Innovation Grant from Boehringer Ingelheim (£80,000) for spatial transcriptomics of TLS maturity in TNBC.
        - **2024** — First place in the Alan Turing Institute Theory and Methods Challenge Fortnights call (£30,000) for the *Geometry-Informed Data Representations* workshop.
    design:
      columns: '1'

  - block: collection
    id: papers
    content:
      title: Featured Publications
      text: 'A selection of recent work. See the [full publications list](publications/) for more.'
      filters:
        folders:
          - publications
        featured_only: true
      sort_by: 'Weight'
      sort_order: 'asc'
    design:
      view: article-grid
      columns: 3

  - block: collection
    id: projects
    content:
      title: Projects
      filters:
        folders:
          - projects
    design:
      view: article-grid
      columns: 3
---
