---
title: "Getting started with spatial transcriptomics analysis"
date: 2025-01-15
draft: true
tags:
  - Spatial Omics
  - Tutorial
  - Xenium
summary: "A practical introduction to analysing spatial transcriptomics data with Python, covering data loading, quality control, cell typing, and spatial statistics."
authors:
  - me
---

*This is a draft post — replace with your own content.*

## Introduction

Spatial transcriptomics is transforming how we study tissue biology...

## Loading Xenium data

```python
import spatialdata as sd

sdata = sd.read_zarr("path/to/xenium.zarr")
```

## Next steps

- Cell typing with CellTypist
- Batch correction with Harmony/scVI
- Spatial neighbourhood analysis
