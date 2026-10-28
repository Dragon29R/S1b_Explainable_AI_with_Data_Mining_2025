# AI & Data Mining Portfolio

This repository contains two distinct data mining and machine learning projects:
1. **Molecular Frequent Subgraph Mining**: Analyzing chemical structures and extracting frequent subgraphs using the gSpan algorithm.
2. **Spotify Customer Churn Prediction**: An end-to-end machine learning pipeline to predict user churn using tabular data.

---

## Project 1: Molecular Frequent Subgraph Mining

This project focuses on cheminformatics, processing molecular datasets to identify common structural patterns (subgraphs) across different groups of molecules.

### Overview & Workflow
* **Data Preparation**: Extracts SMILES strings and pIC50 values from `SMILES_Big_Data_Set.csv` and formats them into a `.smi` file for PaDEL-Descriptor.
* **SDF Processing**: Extracts compressed `.sdf.gz` molecular files and converts them into visualizable `.png` formats using RDKit.
* **Dataset Splitting & Graph Conversion**: Molecules are randomly split into two groups (Group A and Group B). The molecular graphs (vertices for atoms, edges for bonds) are then encoded into the `.gspan` format.
* **Frequent Subgraph Mining**: The `gspan-mining` library is executed on both groups with specific constraints (support `-s 35`, min vertices `-l 7`, max vertices `-u 10`).
* **Pattern Analysis**: The mining process successfully identified 23 unique frequent subgraphs in Group A and 16 in Group B. Canonical string representation is used to cross-reference results and isolate subgraphs unique to each group (e.g., 9 subgraphs exclusive to Group A, and 2 exclusive to Group B).

### 🛠️ Tech Stack (Project 1)
* `rdkit` & `py3Dmol` (Molecular parsing and visualization).
* `gspan-mining` (Frequent subgraph extraction).
* `pandas` & `numpy` (Data manipulation).

---

## Project 2: Spotify Customer Churn Prediction

This project builds a predictive classification pipeline to identify users likely to churn based on their listening habits and account details.

### Overview & Workflow
* **Data Ingestion & Cleaning**: Loads `spotify_churn_dataset.csv`, coercing text columns (e.g., gender, country, subscription_type) into categorical formats and usage metrics (listening_time, skip_rate) into numeric types.
* **Exploratory Data Analysis (EDA)**: Analyzes the target variable (`is_churned`) to check for class imbalances and visualizes numeric/categorical feature distributions against churn status using Seaborn.
* **Data Preprocessing**: Implements a `scikit-learn` `ColumnTransformer` to handle missing values (median imputation for numerical data, mode imputation for categorical data), scales numeric features via `StandardScaler`, and applies `OneHotEncoder` to categorical features.
* **Model Training & Evaluation**: Trains and evaluates four different machine learning models: Decision Tree, Random Forest, Support Vector Machine (SVM), and Artificial Neural Network (MLPClassifier).
* **Metrics**: Evaluates model performance using Accuracy, ROC-AUC, classification reports, and confusion matrices.

###  Tech Stack (Project 2)
* `scikit-learn` (Pipelines, Imputation, Classification Models, Metrics).
* `pandas` & `numpy` (Data processing).
* `matplotlib` & `seaborn` (Data visualization).

---

##  Setup & Installation

To run the notebooks in this repository, it is recommended to use Python 3.11+. Install the required dependencies using `pip`:

```bash
pip install pandas numpy scikit-learn matplotlib seaborn
pip install rdkit py3Dmol gspan-mining
