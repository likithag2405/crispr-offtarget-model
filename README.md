# CRISPR Off-Target Prediction  Model

Machine learning model for predicting CRISPR-Cas9 off-target cleavage using the CIRCLE-seq 10 gRNA dataset (~585,000 sgRNA–off-target pairs, ~1.25% positives).

---

## Dataset

CIRCLE-seq 10 gRNA Whole Dataset  

Each row represents:
- One sgRNA sequence  
- One potential off-target genomic site  
- Binary label:
  - 1 → cleavage experimentally detected  
  - 0 → no cleavage detected  

The dataset is highly imbalanced (~1.25% positive class).

---

## Features

- Mismatch count between sgRNA and off-target sequence  
- GC content of both sequences  
- One-hot encoding of 24 base positions  
  (24 positions × 4 bases × 2 sequences = 192 binary features)

Total features: 195

---

## Models Compared

All models were trained and evaluated on the same stratified 80/20 train–test split.

| Model | ROC-AUC |
|-------|---------|
| Logistic Regression (mismatch only) | ~0.75 |
| Logistic Regression (+ GC content) | ~0.78 |
| Random Forest (3 features) | ~0.85 |
| Random Forest (195 features) | **~0.96** |

---

## Final Model Performance

- ROC-AUC: 0.959  
- PR-AUC: 0.611  
- 3-fold CV ROC-AUC: 0.956 ± 0.0003  
- Optimal classification threshold: 0.31  

The improvement from 0.85 to 0.96 after full positional encoding highlights the importance of base-position information in sequence-based prediction.

---

## How to Run

```bash
git clone https://github.com/likithag2405/crispr-offtarget-model
cd crispr-offtarget-model
pip install -r requirements.txt
```

Place `CIRCLE_seq_10gRNA_wholeDataset.csv` in the project folder and open `crispr_offtarget_model.ipynb` in Jupyter.

---

## Requirements

See `requirements.txt` for required Python packages.

---

## Notes

This project is intended for computational research and educational purposes.  
It is not validated for clinical or therapeutic applications.
