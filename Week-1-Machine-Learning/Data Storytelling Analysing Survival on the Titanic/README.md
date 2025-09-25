# Titanic Survival Classifier — the step-by-step (no-pipeline) version

## Why this exists 
I wanted a model that predicts **whether a passenger survived the Titanic** using a Kaggle dataset.

- **Data:** Kaggle — Titanic Dataset
- **Goal:** Binary classification: `0 = did not survive`, `1 = survived`  
- **Rows after cleaning:** **712**  (dropping rows with missing `Age` or `Embarked`)

## A tiny bit more detail

### Exploratory Data Analysis (EDA)
- Checked `.info()` and `.describe()` to understand column types and ranges.  
- Plotted distributions for numeric features (e.g., `Age`, `Fare`) and counts for categoricals (`Sex`, `Pclass`, `Embarked`).  
- Reviewed a correlation heatmap and simple group comparisons (e.g., survival rate by `Sex` and `Pclass`).

### Data cleaning choices (and why)
- **Missing `Age`:** either dropped for the minimal version or imputed in a variant run; a manual approach keeps the logic obvious.  
- **`Embarked` blanks:** imputed with the mode or dropped in the minimal path to keep the pipeline-free story clean.  
- **`Cabin`:** mostly missing; excluded from the minimal model.  
- **Sanity checks:** trimmed odd characters, verified ranges, and ensured target integrity.

### Feature preparation
- **Categorical to numeric:**  
  `Sex`, `Embarked`, `Pclass` → encoded by hand (label maps and one‑hot where needed).  
- **Continuous kept continuous:**  
  `Age`, `Fare` stayed numeric.  
- **Optional engineered features:**  
  **FamilySize** (`SibSp + Parch + 1`) and **Title** extracted from `Name` (shown plainly, step by step).


## How to run it locally
Download the repository and open the notebook in Google Colab, JupyterLab, or your preferred environment.  
Run the cells in order.