# crispr-offtarget-model

Machine learning model to predict CRISPR-Cas9 off-target cleavage using the CIRCLE-seq 10 gRNA dataset (~585k sequence pairs, 1.25% positives).

---

## Features

- Mismatch count  
- GC content  
- Full positional one-hot encoding (195 total features)

---

## Models Compared

- Logistic Regression (mismatch only): ~0.75 ROC-AUC  
- Logistic Regression (+ GC): ~0.78  
- Random Forest (3 features): ~0.85  
- Random Forest (195 features): ~0.96  

---

## Final Model Performance

- ROC-AUC:0.959
- PR-AUC: 0.611  
- 3-fold CV ROC-AUC: 0.956 ± 0.0003  
- Optimal threshold: 0.31  

---

## How to Run

Open crispr_offtarget_model.ipynb in Jupyter,
```bash
git clone https://github.com/likithag2405/crispr-offtarget-model
cd crispr-offtarget-model
pip install -r requirements.txt


