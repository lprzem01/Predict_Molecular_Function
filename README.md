# Coursework 2: Predict Molecular Function from Protein Sequence
## Overview
This project aims to predict the molecular function of proteins based on their amino acid sequences. Using data from UniProt and Gene Ontology (GO) identifiers, the workflow processes protein sequence and annotation data, extracts features, and applies machine learning models to classify proteins into molecular function categories.

## Setup Instructions
### Install Required R Packages
The analysis uses several R packages for data manipulation, sequence analysis, and modeling, including:
  <p> tidyr, readr, dplyr, tidyverse
  phylotools, Biostrings, protr, seqinr
  ggplot2, ggrepel, ggExtra
  randomForest, tree, e1071, caret, neuralnet
  shiny, bslib </p>
The script checks for and installs any missing packages automatically.

### Data Download
The script creates Data and Output folders if they do not exist. It then downloads protein annotation (TSV) and sequence (FASTA) files for six GO molecular function categories from UniProt using provided URLs.

### Data Sources
TSV Files: Contain protein accession, organism, sequence length, and GO annotations.
FASTA Files: Contain protein sequences for each GO category.
GO Categories:
  Catalytic activity (GO:0003824)
  Binding (GO:0005488)
  Electron transfer (GO:0009055)
  Molecular function regulator (GO:0098772)
  Transporter activity (GO:0005215)
  Structural molecule (GO:0005198)
### Data Processing Steps
#### Read and Inspect Data
Load TSV and FASTA files for each GO category.
Add a column to each TSV for the molecular function label
#### Remove Overlapping Entries
Filter out proteins that appear in more than one GO category to ensure unique classification.
#### Combine and Clean Data
Merge filtered dataframes.
#### Check for and handle missing values.
Save intermediate cleaned data to Output/output_file1.tsv.
#### Process FASTA Sequences
  Extract protein accession (Entry) from FASTA headers.
  Create dataframes mapping Entry to sequence.
  Merge all FASTA dataframes and join with filtered TSV data to retain only unique entries.
  Save filtered sequences to Output/filtered.fasta.

#### Feature Extraction
Remove sequences with non-standard amino acids.
Calculate amino acid composition descriptors (APAAC) using the protr package.
Save composition data to Output/Composition.tsv.



#### Final Data Preparation
Merge composition features with annotation data.
Remove unused columns and handle missing values.
Save the final dataset to Output/final_df.tsv.

### Exploratory Data Analysis
Visualize variable importance using tree plots and feature importance from Random Forests.
Use Shiny apps for interactive exploration of feature relationships and distributions.

### Modeling
Three classification models are explored:
  Random Forest
  Support Vector Machine (SVM)
  Neural Networks

Model selection and parameter tuning are performed using a sample of the data. The best-performing model (Random Forest) is trained on the full dataset.#

### Evaluation
The dataset is split into training and test sets (70/30).
Three Random Forest models with different feature sets are evaluated.
Confusion matrices and error rates are computed and visualized.
The best model achieves an accuracy of ~0.86, with results visualized in the Output folder.

### Visualization
Confusion matrices and error rate plots are generated using ggplot2 and saved as PNG files in the Output folder.
Interactive Shiny apps allow further exploration of feature relationships.

### Contents of Data and Output Folders
Data/

Raw TSV and FASTA files for each GO category.

Output/

output_file1.tsv: Cleaned and merged annotation data.
filtered.fasta: Filtered protein sequences.
Composition.tsv: Extracted amino acid composition features.
final_df.tsv: Final dataset for modeling.
SimpleTree.png: Tree plot of feature importance.
ConfusionMatrix.png: Confusion matrix of model predictions.
rfError.png: Random Forest error rate plot.



Reproducibility
All steps are scripted in R Markdown, allowing for reproducible analysis from data download to model evaluation and visualization.
