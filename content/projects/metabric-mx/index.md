---
title: "METABRIC-MX"
summary: "Multimodal eXplorer for breast cancer spatial transcriptomics — integrating Xenium, metallomics, IF imaging, and H&E into unified SpatialData objects."
tags:
  - Spatial Omics
  - Breast Cancer
  - Pipeline
date: 2024-06-01
lastmod: 2026-04-17
external_link: ""
---

METABRIC-MX (Multimodal eXplorer) is a platform for processing and analysing Xenium breast cancer spatial transcriptomics data from the METABRIC cohort. The pipeline handles:

- **Multi-modal registration**: Aligning metallomics, immunofluorescence, H&E, and Xenium data into unified SpatialData/Zarr objects
- **Cell typing**: Automated annotation using CellTypist with the Chen.pkl model trained on 600k+ cells
- **Batch correction**: Harmony and scVI integration across tissue microarray cores
- **Spatial analysis**: KNN smoothing, neighbourhood composition, and immune niche profiling
