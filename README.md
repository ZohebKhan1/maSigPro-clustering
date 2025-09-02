# maSigPro Time-Series Clustering Tutorial

Workflow/analysis of temporal gene expression clustering for time-course bulk RNA-seq data using the maSigPro package in R.

> Conesa, A., Nueda, M.J., Ferrer, A., & Talon, M. (2006). maSigPro: a method to identify significantly differential expression profiles in time-course microarray experiments. *Bioinformatics*, 22(9), 1096-1102.

I published the workflow here using RMarkdown with associated/relevant code chunks: **[maSigPro Tutorial](https://zohebkhan1.github.io/maSigPro-clustering/)**

---

## maSigPro Resources

- [Bioconductor Package Page](https://www.bioconductor.org/packages/release/bioc/html/maSigPro.html)
- [User Guide (PDF)](https://mirror.accum.se/mirror/bioconductor.org/packages/3.4/bioc/vignettes/maSigPro/inst/doc/maSigProUsersGuide.pdf)
- [Original Paper (2006)](https://academic.oup.com/bioinformatics/article/22/9/1096/200371)
- [Updated Paper (2014)](https://academic.oup.com/bioinformatics/article/30/18/2598/2475510)

---

## Overview

This tutorial, broadly, demonstrates how to perform time-series clustering on RNA-seq data using maSigPro, identify genes with significant temporal expression changes between conditions (genotype/treatment/etc.), cluster genes by expression pattern, and conduct Gene Ontology (GO) enrichment analysis on gene clusters.

---

## Repository Structure

Here is a general outline of this repository in case you want to download and adapt this workflow to your experimental design.

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

## Contact

If you have any questions, suggestions, or want to adapt maSigPro to your workflow and have questions, feel free to send an email here:

**Zoheb Khan** — [zohebk@uchicago.edu](mailto:zohebk@uchicago.edu)
