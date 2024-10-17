# SOCIAL: Single-cell transcriptOmics Cell-cell Interaction ALgorithm
**Last Updated: 09/24/2024**
<img src="https://github.com/kwangcb/IRIS/blob/main/4-Figure/figures/biorender/png/SOCIAL%20%5Bnc%20acc%5D.png" alt="grouping">

## Overview

We developed an **```R```** method, **SOCIAL** (**S**ingle-cell transcript**O**mics **C**ell-cell **I**nteraction **AL**gorithm), to identify significant ligand-receptor interactions between two specific cell types, drawing upon insights from [Kumar et al.'s](https://pubmed.ncbi.nlm.nih.gov/30404002/), [**CellPhoneDB** (v1)](https://pubmed.ncbi.nlm.nih.gov/30429548/), and our own [**LIRICS**](https://pubmed.ncbi.nlm.nih.gov/34983745/) framework. Our decision to create our own code stemmed from four primary motivations: 1. Leveraging the strengths of previous methods: By combining aspects of the three approaches, we aimed to maximize the accuracy and robustness of our ligand-receptor interaction predictions. 2. Implementing an R-based solution: While the first method lacked publicly accessible code and the second was in Python, we sought to create an R-based solution for accessibility and ease of use. 3. Incorporating our comprehensive database: Our ligand-receptor interaction database (LIRICS) provided rich and informative annotations, enhancing the depth of our analysis. 4. Accommodating variations in ligand-receptor interaction activity observed across patients.

SOCIAL comprises three main steps: 1. Querying the LIRICS database: Initially, we queried the LIRICS database to identify plausible ligand-receptor interactions; 2. Computing interaction scores: Next, we computed the ligand-receptor interaction score by multiplying the average expression levels of the ligand and receptor complexes for each interaction pair and cell type. 3. Permutation testing: Following that, we performed permutation tests (utilizing 100 iterations in our study) by randomly shuffling cell type labels. This allowed us to derive empirical p-values by calculating the fraction of permutation tests resulting in a higher interaction score than the foreground score determined in step 2. A lower p-value suggests a higher likelihood of the interaction occurring. 4. Optionally, ligand-receptor interactions can be further denoted as significantly activated if the average expression level of both the ligand and receptor genes is greater than the median across all samples.
## Installation
```r
install.packages('devtools')
library(devtools)
devtools::install_github("KWangLab/SOCIAL")
```
## Tutorials
* To reproduce the Nat. Comms. results from Sahni et al. (for Jerby-Arnon et al. single-cell cohort), see: https://github.com/KWangLab/SOCIAL/blob/main/vignettes/SOCIAL_Jerby-Arnon.Rmd
* To implement SOCIAL in your own work, see: https://github.com/KWangLab/SOCIAL/blob/main/vignettes/SOCIAL.Rmd

## Sample data availability
Sample SOCIAL relevant data can be found at https://zenodo.org/records/13172848.

## System requirements
SOCIAL was developed on R (v4.4.1) using R packages: dplyr (v1.1.4), magrittr (v2.0.3), parallel (v4.4.1), pROC (v1.18.5), rBayesianOptimization (v1.2.1), tidyr (v1.3.1), abind (v1.4-5), Matrix (v1.7-0),  urr (v1.0.2), reshape2 (1.4.4), rslurm (v0.6.2), and stats (v4.4.1). All analyses were done on R (v4.4.1).

## Citation
If using SOCIAL, please cite:

Sahni, S., Wang, B., Wu, D. et al. A machine learning model reveals expansive downregulation of ligand-receptor interactions that enhance lymphocyte infiltration in melanoma with developed resistance to immune checkpoint blockade. Nat Commun 15, 8867 (2024). https://doi.org/10.1038/s41467-024-52555-4

[**Download Citation**](https://citation-needed.springer.com/v2/references/10.1038/s41467-024-52555-4?format=refman&flavour=citation)

## Acknowledgement(s)
### Lead Developers(s)
1. **Sahil Sahni**
2. **Sushanth Patkar**
3. **Kun Wang** (kwang222@illinois.edu)^
4. **Eytan Ruppin** (eytan.ruppin@nih.gov)^

^*equally-contributing corresponding author(s)*

### Acknowledgement(s)
SOCIAL figures was created with BioRender.com.

