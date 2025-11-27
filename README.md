# Graph-Based Network Analysis & Statistical Hypothesis Testing for Expression Pattern Recognition Analysis

### Project Overview

**Objective:** To identify latent statistical patterns in high-dimensional datasets that correlate with quantitative clinical outcomes.

**Hypothesis:** Traditional analysis fails to capture non-linear relationships in datasets with high feature-to-sample ratios.

**Approach**

* Data Engineering: Pre-processing and normalization of raw count data to remove technical bias.

* Statistical Methods:

  - Statistical Validation: Applied Linear Correlation and ANOVA to screen for significant features and handle noise.
  - Network Construction: Deployed **WGCNA** (Weighted Correlation Network Analysis) to build a scale-free topology graph, clustering variables into co-regulated modules.

* Stack: R (tidyverse, ggplot2, WGCNA).

**Key Findings, Pivot & Pipeline Validation**

* Initial Screening & The Linear Limit

  * Observation: Contrary to general literature, my initial univariate analysis revealed no statistically significant correlation (p>0.05) between the target biomarkers (Vitamin D/Calcium) and Insulin Sensitivity (eIS).
  * Pivot: This finding ruled out simple linear biomarkers as predictors. I determined that standard regression was insufficient to capture the system's complexity, necessitating a shift to unsupervised network analysis (WGCNA) to identify latent, non-linear gene clusters.

* Pipeline Validation (Proof of Concept)

  * To verify that my WGCNA architecture was functional before accepting the null result, I tested it against known clinical drivers (Age and BMI).
  * Result: The pipeline successfully clustered Age and BMI into statistically significant gene modules (p<0.05).
  * Impact: This was a critical "sanity check." It proved that the algorithms and code were correctly identifying real biological signals in the data, validating the pipeline's integrity.

* Hypothesis Elimination

  * With the pipeline validated by the confounding factors, I re-tested the primary hypothesis.
  * Result: The network analysis confirmed no significant functional enrichment or distinct module membership for Vitamin D or Calcium.
  * Conclusion: The study demonstrated that the signal associated with Insulin Sensitivity was entirely driven by confounding factors (Age/BMI). This rigorously eliminated the nutritional biomarkers as potential targets, contradicting lower-resolution literature and effectively pruning the search space for future research.



# About the scripts :

* Correlation_and_ANOVA.R: This script holds the necessary functions for correlation testing, tercile division of data and ANOVA. This script should be run first to check the integrity of the data and reproducing the results from the study.

* WGCNA.R: The outlier datasets were removed and gene custers were made. The modules were related with traits and genes correlated to vitamin D, calcium and estimated insulin sensitivity were extracted. This script needs to be run second and reproduce the reults from the study.
