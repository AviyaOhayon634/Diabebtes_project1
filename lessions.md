Lecture 1 – Introduction to Machine Learning in Medical Applications

This lecture introduced the foundations of Machine Learning (ML), defined as computational methods that learn patterns from data without being explicitly programmed.

Two main paradigms were presented:

1. Supervised Learning

(Situations where each sample has a known label/target)

Regression – Predicting a continuous value (e.g., blood glucose level).

Classification – Predicting categorical outcomes (e.g., healthy vs. diseased).

Key terminology:

Feature – An input variable used for prediction.

Target (Label) – The variable being predicted.

Sample (Observation) – A single data instance.

2. Unsupervised Learning

(No labeled outcome variable)

Clustering – Grouping similar samples.

Dimensionality Reduction (e.g., PCA) – Reducing the number of features while preserving variability.

The lecture also reviewed statistical foundations:

Descriptive Statistics – Mean, median, variance, visualization.

Inferential Statistics – Hypothesis testing, estimation, p-values.

Challenges in Medical Data

Medical datasets are often:

Heterogeneous (clinical, genomic, imaging).

Skewed (non-normal distributions).

Imbalanced (rare diseases).

Sparse.

High-dimensional.

Affected by batch effects.

The importance of normalization (e.g., Min-Max scaling, Z-score, log transformation) was emphasized.

Core idea: Medical data require careful preprocessing and model selection.

📘 Lecture 2 – Microbiome Data and MIPMLP

This lecture focused on microbiome datasets.

The microbiome refers to the collection of microorganisms inhabiting the human body. Data are typically generated from sequencing (e.g., 16S rRNA) and represented as:

Rows → samples

Columns → ASVs (Amplicon Sequence Variants), representing microbial sequences

Values → abundance counts

Characteristics of Microbiome Data

Sparse (many zeros)

High-dimensional (p ≫ n)

Compositional (relative abundances sum to a constant)

Hierarchical (taxonomy: Kingdom → Species)

MIPMLP (Microbiome Preprocessing Machine Learning Pipeline)

A structured preprocessing pipeline including:

Taxonomic Aggregation – Combining ASVs at a chosen taxonomic level.

Sum

Mean

Sub-PCA (PCA applied within each taxonomic group)

Normalization

Log transformation

Z-score normalization

Feature filtering

Removing rare taxa

Machine Learning model training

Core idea: Incorporating biological hierarchy reduces noise and improves model stability.

📘 Lecture 3 – Models for Tabular Data

This lecture reviewed supervised models commonly used for tabular medical data.

Linear Regression

Assumes linear relationship.

Optimizes Mean Squared Error (MSE).

Logistic Regression

Used for binary classification.

Applies Sigmoid function to output probabilities.

Decision Trees

Split data using thresholds.

Use impurity measures:

Gini impurity

Entropy

Easily interpretable but prone to overfitting.

Random Forest

Ensemble of decision trees.

Uses Bootstrap sampling.

More stable and reduces variance.

XGBoost

Gradient boosting method.

Sequentially corrects previous errors.

Often high-performing.

Core idea: Model choice depends on data structure and clinical goals.

📘 Lectures 4–5 – Model Evaluation and Statistical Comparison

Focused on correct evaluation procedures.

Data Splitting

Training set

Validation set

Test set

Stratified split (preserves class proportions)

Cross-validation (K-fold)

Overfitting

When a model memorizes training data and fails to generalize.

Solutions:

Regularization (L1, L2)

Dropout

Early stopping

More data

Regression Metrics

MAE

MSE

RMSE

R²

Pearson and Spearman correlation

Classification Metrics

Confusion Matrix

Accuracy

Precision

Recall (Sensitivity)

F1 Score

ROC Curve

AUC

Statistical Comparison

Paired t-test

ANOVA

Post-hoc testing

Core idea: Model evaluation must be rigorous and statistically valid.

📘 Lecture 6 – CNNs and GNNs

Traditional fully connected networks ignore spatial structure.

CNN (Convolutional Neural Network)

Used for images.

Key components:

Convolution (kernel/filter sliding across image)

Stride

Padding

Pooling

Feature maps

Vanishing Gradient Problem

Gradients diminish in deep networks.

Solution:

ResNet (Residual connections)

Transfer Learning

Using pretrained networks and fine-tuning for new tasks.

GNN / GCN

Graph Neural Networks operate on:

Nodes

Edges

Useful for biological networks, molecular graphs, microbiome graphs.

Core idea: Architecture must match data structure.

📘 Lecture 7 – Taxonomy, Trees, and Hierarchical Clustering

Microbiome data follow taxonomic hierarchy.

Tree of Means

Each internal node represents aggregation (e.g., mean) of children taxa.

Embedding

Mapping tree nodes into continuous space (e.g., R²).

Hierarchical Clustering

Builds a dendrogram by iteratively merging clusters.

Linkage methods:

Single

Complete

Average

Core idea: Structure-aware representations improve learning.

📘 Lecture 8 – iMic and Explainability

iMic converts microbiome data into an image-like representation and applies CNN.

The study evaluated:

Accuracy

AUC

Robustness to sparsity

Robustness to small training sets

Grad-CAM

Visual explanation method that highlights important regions influencing predictions.

Core idea: Medical ML models must be robust and interpretable.

📘 Lecture 9 – Differential Abundance Analysis

Goal: Identify taxa whose abundance differs between groups.

Challenge:

No ground truth.

Permutation Test

Randomly shuffle labels to estimate null distribution.

RSP Score

Compares real positives vs shuffled positives.

Existing Methods

DeSeq2 – Negative binomial model for count data.

ALDEx2 – Uses centered log-ratio transformation.

ANCOM – Compares log ratios between taxa.

Core idea: Statistical rigor is essential when ground truth is unavailable.

🧠 Overall Course Framework

The course integrates:

Statistical thinking

Machine learning modeling

Medical domain knowledge

Structured preprocessing

Robust evaluation

Interpretability

It emphasizes adapting methods to the unique challenges of biomedical data.