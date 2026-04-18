# Final Project: Type 2 Diabetes Detection from Microbiome Data

## Project Context
This repository contains the final project for the course **Machine Learning and Statistics in Medical Applications**.
The project studies whether gut microbiome composition can distinguish **Type 2 Diabetes (T2D)** from **healthy controls** using statistical testing, classical machine learning, and a taxonomy-aware CNN baseline.

The main analysis is documented in `research2.ipynb`.

## Research Question
Can microbiome composition be used to distinguish **T2D** from **healthy** patients, and is the signal better explained by:
- specific taxa with differential abundance,
- broader taxonomy-wide structure, or
- multivariate predictive patterns captured by machine learning?

## Dataset
- Source file used in the main notebook: `T2D_microbiome_dataset_2.csv`
- Cohort size: `116` patients
- Class distribution:
  - `T2D`: `63`
  - `healthy`: `53`
- Raw feature space: species- and genus-level microbiome abundance columns plus the label column

## Main Workflow
The current project process in `research2.ipynb` is:

1. Load the binary T2D/healthy cohort and isolate microbiome features.
2. Preprocess the taxonomic table with `MIPMLP`:
   - taxonomy level `7`
   - taxonomic aggregation by `sum`
   - relative normalization
   - rare-bacteria filtering threshold `0.05`
3. Reduce the feature matrix from the raw input to a processed table of `258` taxa.
4. Apply a global `log10(X + 1e-6)` transform for visualization and downstream analysis.
5. Run exploratory plots for:
   - dominant taxa by class
   - sparsity / non-zero taxa per patient
   - raw vs. log-transformed abundance distributions
6. Perform differential abundance testing:
   - Mann-Whitney U test per taxon
   - Benjamini-Hochberg FDR correction
   - log2 fold-change summary
7. Run taxonomy-aware validation with `mi-Mic`.
8. Train full-feature tabular models:
   - Random Forest
   - XGBoost
9. Extract XGBoost feature importance for biological interpretation.
10. Convert the processed table to taxonomy-aware image-like matrices with `micro2matrix` and train a CNN with Optuna-based tuning.
11. Compare models and run a post-hoc reduced-feature experiment based on statistically selected taxa.

## Current Results Summary
The README summary below follows the latest stored notebook outputs and saved artifacts.

- Differential abundance testing identifies `16` taxa with `FDR q < 0.05`.
- `mi-Mic` does not find a broad taxonomy-wide separation:
  - global nested ANOVA `p = 0.99998`
- Full-feature tabular models:
  - Random Forest: `ROC-AUC 0.780`
  - XGBoost: `ROC-AUC 0.720`
- CNN image pipeline:
  - ROC-AUC: `0.608`
  - best threshold from Youden's J: `0.390`
  - at that threshold: accuracy `0.708`, precision `0.750`, recall `0.545`, F1 `0.632`
- Reduced-feature follow-up using `19` statistically guided taxa:
  - XGBoost: `ROC-AUC 0.741`
  - Random Forest: `ROC-AUC 0.713`

Interpretation:
- The microbiome signal is **real but moderate**.
- The signal appears **feature-specific**, not driven by a broad taxonomy-wide shift.
- In the current notebook, the strongest overall baseline is the **full-feature Random Forest** model.

## Repository Structure
- `research2.ipynb` - main final notebook with the current end-to-end workflow
- `research.ipynb` - earlier notebook version
- `T2D_microbiome_dataset_2.csv` - main binary dataset used in `research2.ipynb`
- `T2D_microbiome_dataset.csv` - earlier dataset version
- `plots/` - figures generated during analysis
- `xgboost_feature_importance.png` - exported XGBoost feature-importance figure
- `roc.png` - CNN ROC curve figure
- `confusion_matrix.png` - CNN confusion matrix at the tuned threshold
- `preds.npy`, `acts.npy`, `metrics_saved.csv` - saved CNN evaluation artifacts reused later in the notebook
- `projectInstruction.md` - course project instructions
- `lessions.md` - course notes
- `assay_draft.md` - writing draft / notes

## How to Run
1. Open `research2.ipynb`.
2. Run the notebook from top to bottom.
3. Review the generated figures and comparison tables.

The notebook depends on these main libraries:
- `numpy`
- `pandas`
- `matplotlib`
- `seaborn`
- `scikit-learn`
- `xgboost`
- `torch`
- `pytorch-lightning`
- `optuna`
- `MIPMLP`
- `mimic_da`

## Reproducibility Notes
- Later comparison cells depend on variables and saved artifacts produced by earlier CNN cells.
- The `preds.npy`, `acts.npy`, and `metrics_saved.csv` files are generated during the CNN section and reused in later evaluation cells.
- Some third-party microbiome packages in this project are version-sensitive, so reproducing the exact notebook outputs is easiest in the same environment used for the original run.

## Alignment with Course Requirements
This repository is organized to match the required project structure:

- **Abstract / Introduction**: background, research question, and motivation are written in the notebook.
- **Methods**: preprocessing, filtering, statistical testing, feature handling, model selection, and evaluation are explicitly documented.
- **Results**: quantitative outputs, tables, plots, ROC analysis, confusion matrices, and model comparisons are included.
- **Discussion**: the notebook and report drafts focus on interpretation, limitations, and future directions.

Technical requirements addressed:
- GitHub repository structure
- clear README
- executable notebook-based analysis
- quantitative statistical and machine-learning evaluation
