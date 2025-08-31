# maSigPro Time-Series Clustering Tutorial

A comprehensive R workflow for time-course RNA-seq analysis using the **maSigPro** package to identify condition-specific temporal gene expression patterns.

**[View the Tutorial](https://zohebkhan1.github.io/maSigPro-clustering/)**

---

## Overview

This tutorial demonstrates how to:

- Perform time-series clustering on RNA-seq data using maSigPro
- Identify genes with significant temporal expression changes
- Cluster genes by expression pattern
- Conduct Gene Ontology (GO) enrichment analysis on gene clusters

---

## Repository Structure

```
maSigPro-clustering/
│
├── tutorial_masigpro_workflow.Rmd    # Source R Markdown
├── index.html                        # Rendered tutorial (GitHub Pages)
│
├── data/
│   ├── counts/
│   │   ├── cpm/                      # CPM normalized counts
│   │   ├── normalized/               # DESeq2 normalized counts
│   │   ├── raw/                      # Filtered raw counts
│   │   └── vst/                      # Variance-stabilized counts
│   ├── deg/
│   │   ├── apeglm/                   # Shrunken LFC results
│   │   └── unshrunken/               # Unshrunken DESeq2 results
│   └── metadata/                     # Sample metadata
│
└── results/
    ├── figures/
    │   └── masigpro/
    │       ├── all_clusters_combined.svg
    │       └── go_enrichment/        # GO dotplots per cluster
    └── masigpro/
        ├── cluster_assignments.csv   # Gene-to-cluster mapping
        ├── summary_statistics.csv    # Cluster summary stats
        └── go_enrichment/            # GO results per cluster
```

---

## Dependencies

### R Version
- R >= 4.0

### CRAN Packages
```r
install.packages(c(
  "ggplot2",
  "dplyr",
  "tidyr",
  "reshape2",
  "patchwork",
  "pheatmap",
  "readr",
  "stringr",
  "knitr"
))
```

### Bioconductor Packages
```r
if (!require("BiocManager", quietly = TRUE))
    install.packages("BiocManager")

BiocManager::install(c(
  "maSigPro",
  "clusterProfiler",
  "org.Hs.eg.db"
))
```

---

## Usage

1. Clone the repository:
   ```bash
   git clone https://github.com/ZohebKhan1/maSigPro-clustering.git
   ```

2. Open `tutorial_masigpro_workflow.Rmd` in RStudio

3. Install dependencies (see above)

4. Knit the R Markdown to reproduce the analysis

---

## Contact

For questions or feedback, please contact:

**Zoheb Khan**
[zohebk@uchicago.edu](mailto:zohebk@uchicago.edu)
