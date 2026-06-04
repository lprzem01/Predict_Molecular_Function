# Predicting Protein Molecular Function from Amino Acid Sequences

## Overview

This project develops a machine learning pipeline to predict protein molecular function directly from amino acid sequence data. Protein sequences and annotations were obtained from UniProt and classified into six Gene Ontology (GO) molecular function categories.

The workflow integrates biological sequence processing, feature extraction, exploratory data analysis, and machine learning to classify proteins based on sequence-derived features.

### Key Features

- Automated download of protein sequence and annotation data from UniProt
- Protein sequence preprocessing and quality filtering
- Amino acid composition feature extraction using APAAC descriptors
- Exploratory data analysis and feature importance assessment
- Machine learning classification using Random Forest, Support Vector Machine (SVM), and Neural Networks
- Interactive data exploration with Shiny
- Reproducible end-to-end workflow implemented in R

---

## Research Objective

The aim of this project is to investigate whether molecular function can be predicted directly from protein sequence information using machine learning techniques.

The project focuses on six Gene Ontology molecular function categories:

| GO ID | Molecular Function |
|---------|-------------------|
| GO:0003824 | Catalytic Activity |
| GO:0005488 | Binding |
| GO:0009055 | Electron Transfer Activity |
| GO:0098772 | Molecular Function Regulator |
| GO:0005215 | Transporter Activity |
| GO:0005198 | Structural Molecule Activity |

---

## Workflow

### 1. Data Acquisition

Protein annotation and sequence data were downloaded directly from UniProt.

Data sources included:

- TSV annotation files
- FASTA protein sequence files

---

### 2. Data Cleaning and Preparation

The preprocessing workflow included:

- Loading protein annotations and sequences
- Assigning molecular function labels
- Identifying proteins present in multiple GO categories
- Removing overlapping entries to ensure unique class assignment
- Handling missing values
- Creating a unified annotation dataset

Output:

```text
Output/output_file1.tsv
```

---

### 3. Sequence Processing

Protein FASTA sequences were processed to:

- Extract UniProt accession identifiers
- Merge sequence and annotation information
- Remove proteins containing non-standard amino acids
- Generate a filtered sequence dataset

Output:

```text
Output/filtered.fasta
```

---

### 4. Feature Extraction

Sequence-derived features were generated using the APAAC (Amphiphilic Pseudo Amino Acid Composition) method from the `protr` package.

These descriptors capture:

- Amino acid composition
- Physicochemical properties
- Sequence-order information

Output:

```text
Output/Composition.tsv
```

---

### 5. Exploratory Data Analysis

Exploratory analyses included:

- Feature importance visualisation
- Decision tree analysis
- Sequence descriptor exploration
- Interactive Shiny applications

Visualisation tools:

- ggplot2
- ggrepel
- ggExtra
- Shiny

---

### 6. Machine Learning Models

Three classification algorithms were evaluated:

#### Random Forest

- Feature importance assessment
- Hyperparameter optimisation
- Final production model

#### Support Vector Machine (SVM)

- Multi-class protein classification

#### Neural Network

- Comparative model evaluation

Model tuning was performed using sampled datasets before training on the complete feature set.

---

## Model Evaluation

The final dataset was divided into:

- 70% Training Data
- 30% Test Data

Three Random Forest configurations were compared using different feature subsets.

Evaluation metrics included:

- Accuracy
- Error Rate
- Confusion Matrix
- Feature Importance

### Results

The best-performing Random Forest model achieved:

**Accuracy ≈ 86%**

Performance was assessed using held-out test data and visualised through confusion matrices and error-rate plots.

---

## Technologies Used

### Programming Language

- R

### Bioinformatics Packages

- Biostrings
- protr
- seqinr
- phylotools

### Data Analysis

- dplyr
- tidyr
- tidyverse
- readr

### Machine Learning

- randomForest
- caret
- e1071
- neuralnet
- tree

### Visualisation

- ggplot2
- ggrepel
- ggExtra
- Shiny
- bslib

---

## Repository Structure

```text
Data/
├── Raw FASTA files
├── Raw TSV annotation files

Output/
├── output_file1.tsv
├── filtered.fasta
├── Composition.tsv
├── final_df.tsv
├── SimpleTree.png
├── ConfusionMatrix.png
└── rfError.png
```

---

## Key Outputs

### Processed Datasets

- Cleaned annotation dataset
- Filtered protein sequences
- Amino acid composition descriptors
- Final machine learning dataset

### Visualisations

- Decision tree feature analysis
- Confusion matrices
- Random Forest error curves
- Interactive Shiny dashboards

---

## Reproducibility

The entire workflow is implemented in R Markdown and can be reproduced from raw data acquisition through model training, evaluation, and visualisation.

