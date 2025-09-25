# Heart Disease Classifier — the step-by-step (no-pipeline) version

## Why this exists 
I wanted a simple, transparent model that predicts **whether a patient has heart disease** using the classic Kaggle dataset — and I wanted to show **every step manually**, without scikit-learn Pipelines. That way, you can see exactly how the data is explored, cleaned, encoded, and fed into a classifier.

- **Data:** [Kaggle — Heart Disease Dataset](https://www.kaggle.com/datasets/johnsmith88/heart-disease-dataset)  
- **Goal:** Binary classification: `0 = no disease`, `1 = disease` (I binarised the original 0–4 target)  
- **Rows after cleaning:** **906**  

---

## What I did 
1. **EDA:** Looked at structure, summary stats, distributions, and correlations.  
2. **Cleaning:** Fixed obviously invalid values (e.g., `chol == 0`) and kept a flag so the model could learn from the fact that they were odd.  
3. **Encoding:** Turned categoricals into numbers (and one-hot where needed).  
4. **Split:** Train/test = **80/20** with stratification.  
5. **Train:** **Logistic Regression** (no Pipelines — everything applied by hand).  
6. **Evaluate:** Accuracy, precision/recall, ROC-AUC, and a confusion matrix.

---

## A tiny bit more detail

### Exploratory Data Analysis (EDA)
- Checked `.info()` and `.describe()` to understand column types and ranges.  
- Plotted distributions for numeric features (e.g., `age`, `trestbps`, `chol`, `oldpeak`) and counts for categoricals (`cp`, `restecg`, `slope`, `ca`, `thal`).  
- Looked at a correlation heatmap to get a feel for feature–target relationships.

### Data cleaning choices (and why)
- **Cholesterol zeros:** `chol == 0` isn’t physiologically plausible, so I treated those as missing, **imputed**, and kept a binary flag **`chol_0_values`** so the model can learn from the fact the value was originally invalid.  
- **Negative `oldpeak`:** not physiologically meaningful → corrected/removed.  
- Dropped **`id`** (identifier) and **`dataset`** (site/source) to avoid leakage and spurious shortcuts.

### Feature preparation
- **Categorical to numeric:**  
  `sex, cp, fbs, exang, restecg` → mapped to integers.  
  `slope, ca, thal` → encoded as categories and then **one-hot encoded** for Logistic Regression.  
- **Continuous kept continuous:**  
  `age, trestbps, chol, thalch, oldpeak` stayed numeric (floats/ints as appropriate).  
- **Target:** `num` collapsed to binary: `0` vs `>0`.

### Modelling (manually, no Pipelines)
- Train/test split: **80/20**, `random_state=42`, `stratify=y`.  
- **Logistic Regression** with `solver='liblinear'`, `max_iter=2000` (the higher `max_iter` just prevents convergence warnings on some splits).

---

## Results (test set)
- **Accuracy:** **0.857**  
- **Precision (disease = 1):** **0.88** — when the model predicts disease, it’s right 88% of the time.  
- **Recall / Sensitivity (disease = 1):** **0.86** — it catches 86% of true disease cases.  
- **ROC-AUC:** **0.91** — excellent class separation.

**Confusion matrix** (182 test patients):  
- **TN = 67** (healthy correctly identified)  
- **FP = 15** (healthy flagged as disease)  
- **FN = 11** (disease missed)  
- **TP = 89** (disease correctly identified)

**Takeaway:** Performance is balanced and clinically sensible: strong recall for disease (fewer missed cases), and overall accuracy that matches the ROC-AUC story.

> Warning Note: This is a learning project. It’s **not** a clinical tool and shouldn’t be used for real-world diagnosis.

---

## How to run it locally
   Download it and open it on Google Colab or another software of your choice.
   Run it & thats it!
