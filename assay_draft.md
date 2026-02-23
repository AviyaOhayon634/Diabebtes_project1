# Abstract
We analyzed microbiome data to classify T2D vs non-T2D using modular preprocessing and taxonomy-aware representations. The selected TAXA level was species. The best test-set model was Gradient Boosting (XGBoost fallback) (AUC=0.722).

# Introduction
Our question is whether microbiome composition can separate T2D from non-T2D and which representation is most informative.

# Methods
Leakage-safe split, prevalence filtering, log transformation, genus aggregation, subPCA, RF/XGBoost(fallback)/CNN comparison, multi-metric evaluation, paired statistical tests, FDR/Bonferroni correction, SHAP.

# Results
Model and statistical tables are exported to CSV. Differential taxa were ranked after multiple-testing correction.

# Discussion
The analysis supports predictive signal in microbiome data but is limited by sample size and restricted taxonomy depth.
