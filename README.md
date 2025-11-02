# CRISP-DM, KDD & SEMMA Data Science Projects  
*Vineeth (Software Engineer) – GitHub: [vcsk02](https://github.com/vcsk02)*  

This repository contains **three end-to-end data science projects**, each implementing a different methodology:

| Methodology | Dataset | Description |
|-------------|---------|-------------|
| **CRISP-DM** | *Students Performance* (Classification) | Predict high-performing students using demographic & test data. |
| **KDD** | *Students Performance* (Clustering/Discovery) | Discover hidden clusters and patterns in student achievement. |
| **SEMMA** | *Students Performance* (Classification + Regression) | Build and evaluate predictive models using SEMMA workflow. |

---

## 🗂 Repository Structure  
```
├─ CRISP_DM_StudentsPerformance/
│   ├─ crisp_dm_studentsperformance.ipynb
│   ├─ artifacts/
│   │   └─ export/ (model.joblib, schema.json)
│   └─ README.md
├─ KDD_StudentsPerformance/
│   ├─ kdd_studentsperformance.ipynb
│   ├─ artifacts/
│   │   └─ ... cluster outputs, CSVs
│   └─ README.md
├─ SEMMA_StudentsPerformance/
│   ├─ semma_studentsperformance.ipynb
│   ├─ artifacts/
│   │   └─ (clf_model.joblib, reg_model.joblib, schema files)
│   └─ README.md
└─ README.md  ← (this file)
```

---

## 🚀 Getting Started  
You can run all notebooks in **Google Colab** or locally in Jupyter.  
1. Clone this repo:  
   ```bash
   git clone https://github.com/vcsk02/crisp-dm-semma-and-kdd.git
   cd crisp-dm-semma-and-kdd
   ```  
2. If using Google Colab:  
   - Upload your data file (e.g., `StudentsPerformance.csv`) to Google Drive or `/content`.  
   - Open the notebook and update `DATA_FILE = ...` to point to your file.  
   - Run the notebook cells sequentially.  
3. If running locally:  
   - Create a Python 3.10+ virtual environment.  
   - Install dependencies:  
     ```bash
     pip install pandas numpy scikit-learn seaborn matplotlib joblib
     ```  
   - Run the notebooks in Jupyter or VS Code.

---

## 📘 Methodology Summary  

### 1. CRISP-DM (students performance)  
- **Business Understanding**: Identify factors predicting student success.  
- **Data Understanding**: Explore student demographics and scores.  
- **Data Preparation**: Clean data, create `High_Performer` label (avg ≥ 70).  
- **Modeling**: Baseline logistic regression → HGB classifier.  
- **Evaluation**: ROC/AUC, PR curve, Recall@TopK.  
- **Deployment**: Save pipeline & schema to `artifacts/export`.

### 2. KDD (students performance)  
- **Selection**: Choose demographics + scores.  
- **Preprocessing**: Clean, standardize numeric, one-hot encode categorical.  
- **Transformation**: Create `avg_score`, performance bands.  
- **Data Mining**: Use K-Means clustering (k selected by silhouette) to find student groups.  
- **Interpretation**: Profile clusters, visualize with PCA, extract decision tree rules.  
- **Export**: Save CSVs with cluster assignments and profile summaries.

### 3. SEMMA (students performance)  
- **Sample**: Create classification and regression splits.  
- **Explore**: Distributions, boxplots by category.  
- **Modify**: Preprocessing pipelines for both tasks.  
- **Model**: Logistic Regression & HGB for classification. Ridge & Random Forest for regression.  
- **Assess**: ROC/AUC, Recall@TopK (classification). MAE & R², residual plots (regression).  
- **Export**: Two pipelines + schema files in `artifacts`.

---

## 📄 Medium Articles & Video Walkthroughs  
- CRISP-DM article & walkthrough video (students performance)  
- KDD article + video (clusters of student achievement)  
- SEMMA article + video (predicting student performance)  
[Links to Medium posts and YouTube videos] _(update when published)_

---

## 🎯 How to Use the Models  
1. Load the saved `.joblib` pipeline and `.json` schema.  
2. Prepare new student data matching the schema’s feature names.  
3. Run:  
   ```python
   import joblib, json
   pipe = joblib.load("model.joblib")
   with open("schema.json") as f:
       schema = json.load(f)
   proba = pipe.predict_proba(new_data)[:,1]   # classification
   pred  = pipe.predict(new_data)              # regression
   ```  
4. Interpret results and output accordingly (e.g., intervene with students flagged high-risk).

---

## 📌 Notes & Considerations  
- Dataset is publicly available; no personal data privacy concerns.  
- Score thresholds (e.g., avg ≥ 70) can be adjusted based on context.  
- These models *should not* be used in production without fairness, bias, and ethical checks.  
- The clustering and predictive results are *illustrative* of the methodology.

---

## ❓ Questions or Feedback  
For questions or feedback, open an issue or contact me via GitHub or email.

---

Thanks for checking out these projects! I hope you find them useful, insightful, and inspiring.

---

*Repo created by Vineeth (Software Engineer).*  
