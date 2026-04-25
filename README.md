# 🧪 From Raw Ct to Insights: A qPCR Analysis Tutorial in R

[![R](https://img.shields.io/badge/R-%3E%3D4.3-276DC3?logo=r)](https://www.r-project.org/)
[![RMarkdown](https://img.shields.io/badge/RMarkdown-2.0-75AADB)](https://rmarkdown.rstudio.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

A self-contained, beginner-friendly tutorial covering the complete
qPCR analysis workflow — from raw Ct values to statistical testing and
publication-ready figures. **All data are simulated**, so you can run it
immediately without any experimental data, then swap in your own.

---

## What This Tutorial Covers

| Section | Topic |
|---|---|
| 1 | Package setup |
| 2 | Simulating a realistic qPCR dataset |
| 3 | ΔCt normalization (housekeeping gene subtraction) |
| 4 | ΔΔCt and 2^-ΔΔCt fold change |
| 5 | Descriptive statistics (mean, SD, SE by group) |
| 6 | One-way ANOVA, Two-way ANOVA, Tukey HSD post-hoc |
| 7 | Visualization: interaction plot, violin, volcano, ridgeline, heatmap |
| 8 | PCA: scree plot, sample map, variable map, contributions |
| 9 | Export results to CSV |

---

## Simulated Experimental Design

```
40 samples
├── Group:  Control (n=20) | Treatment (n=20)
├── Tissue: TypeA    (n=20) | TypeB     (n=20)
├── Genes:  20 target genes + GAPDH (housekeeping)
└── 8 genes are "responsive" to Treatment (simulated downregulation)
```

Adapt the simulation in **Section 2** to match your own design — change
`n_samples`, `n_targets`, `groups`, `tissues`, or the effect sizes.


## Key Formulas

$$\Delta Ct = Ct_{target} - Ct_{housekeeping}$$
$$\Delta\Delta Ct = \Delta Ct_{sample} - \Delta Ct_{calibrator}$$
$$\text{Fold Change} = 2^{-\Delta\Delta Ct}$$

---

## Dependencies

All packages are installed automatically by the notebook. Manual install:

```r
install.packages(c(
  "tidyverse", "ggpubr", "RColorBrewer",
  "factoextra", "FactoMineR", "corrplot",
  "patchwork", "ggridges", "viridis",
  "ggrepel", "gt"
))
```

---

## Adapting to Your Own Data

Replace the simulation block (Section 2) with a `read.csv()` call pointing
to your own Ct value table. The expected format is:

```
Sample_ID | Group | Tissue | Gene_01 | Gene_02 | ... | GAPDH
S01       | Ctrl  | TypeA  | 27.3    | 29.1    | ... | 18.2
S02       | Treat | TypeA  | 25.1    | 28.8    | ... | 18.0
```

Then update `target_genes`, `hk_gene`, `groups`, and `tissues` in the
setup chunk to match your column names.

---

## Author

**Hamed Abdollahi**  
University of South Carolina| [HPROVAX@gmail.com, HA25@mailbox.sc.edu] | [0000-0002-2202-2193]

