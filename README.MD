# Final Project: Type 2 Diabetes Detection from Microbiome Data

## Project Context
This repository is for the course **Machine Learning and Statistics in Medical Applications**.  
The project follows the official requirements in `projectInstruction.md`.

The medical task is to analyze microbiome data and build a pipeline for **Type 2 Diabetes (T2D) detection**.

## Research Question
Can microbiome composition be used to distinguish:
- `T2D` vs `non-T2D` (primary binary target), and
- `healthy`, `IGT`, `T2D` (exploratory multiclass labels)?

## Dataset
- Source: `curatedMetagenomicData` (extracted using R/RStudio workflow).
- File: `T2D_microbiome_dataset.csv`
- Shape: `145 samples x 499 columns`
- Features: `498` microbiome variables
- Label column: `label`
- Label distribution:
  - `T2D`: 53
  - `IGT`: 49
  - `healthy`: 43

## Repository Structure
- `research.ipynb` - main working notebook.
- `T2D_microbiome_dataset.csv` - project dataset.
- `projectInstruction.md` - official project requirements.
- `lessions.md` - course notes summary.
- `README.MD` - project guide and reproducibility notes.

## Current Workflow Implemented (in `research.ipynb`)
1. Data loading and target definition.
2. Raw microbiome diagnostics (distribution, sparsity/composition checks).
3. MIPMLP-inspired preprocessing utilities.
4. Leakage-safe train/test split.
5. Prevalence filtering.
6. `log1p` transformation.
7. Preprocessing stage shape tracking and visualization.

## How to Run
1. Open `research.ipynb`.
2. Run all cells from top to bottom.
3. Verify outputs for:
   - class counts,
   - raw data diagnostics,
   - preprocessing stage tables/plots.

Environment:
- Python 3.12
- Core libraries used: `numpy`, `pandas`, `matplotlib`, `seaborn`, `scikit-learn`

## Alignment with Project Instructions
This repository is organized to support the required submission structure:
- **Methods**: preprocessing steps, filtering criteria, normalization, split strategy.
- **Results**: quantitative outputs, tables, and figures from the notebook.
- **Discussion**: limitations and future extensions will be documented in the final paper.

Technical requirements addressed:
- GitHub repository structure.
- Clear README.
- Executable notebook-based analysis.

## Submission Plan (According to `projectInstruction.md`)
- **Stage 1 (Presentation, 30%)**: background, research question, methods, dataset, preliminary results, future direction.
- **Stage 2 (Final paper, 70%)**: scientific-paper format (Abstract, Introduction, Methods, Results, Discussion), max 8 pages, quantitative analysis required.
