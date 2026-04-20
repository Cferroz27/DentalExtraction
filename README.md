# DentalExtraction
ML and DL models for dental extraction decision-making in a mestizo population (Cali, Colombia)

# Dental Extraction Decision-Making with ML and DL

**Paper:** *Evaluation of Machine Learning and Deep Learning Models for Dental 
Extraction Decision-Making with Interpretability Methods in a Mestizo Population*

**Authors:** Carlos Andres Ferro Sanchez, Sergio Alejandro Holguín-García, 
Cristian Orlando Diaz Laverde, Ricardo Medellin Fuentes, Juan Fernando Aristizábal, 
Sandra Esperanza Nope Rodríguez, Oscar Iván Campo Salazar, Reinel Tabares-Soto, 
Mario Alejandro Bravo-Ortiz, Lucia Cevidanes

---

## Overview

This repository contains the code and data used in the study of machine learning (ML) 
and deep learning (DL) models for predicting dental extraction decisions in a mestizo 
population from Cali, Valle del Cauca, Colombia. The study evaluates upper, lower, 
and general extraction predictions using a dataset of 500 patients and employs 
interpretability methods including SHAP values and modified partial dependence plots.

---

## Repository Structure

DentalExtraction/
│
├── data/
│   ├── balanced/          # Datasets balanced with SMOTE
│   └── unbalanced/        # Original unbalanced datasets
│
├── scripts/
│   ├── node_gam_kan/      # Node-GAM and KAN model scripts
│   └── partial_dependence_plots/  # Code for partial dependence and SHAP plots
│
├── docs/                  # Additional documentation
├── .gitignore
├── requirements.txt
└── README.md

---

## Models Evaluated

- Gradient Boosting (GB)
- Node-GAM (Neural Generalized Additive Model)
- Kolmogorov-Arnold Networks (KAN)
- Random Forest (RF)
- Extra Trees Classifier (ETC)
- Decision Tree Classifier (DTC)
- K-Nearest Neighbors (KNN)
- Multilayer Perceptron (MLP)
- Stochastic Gradient Descent (SGD)
- Convolutional Neural Network + Fully Connected (CNN + Fully)
- CNN + Capsule-Net
- CNN + Transformer Encoder

---

## Key Results

| Extraction Type | Best Model | Test F1-Score |
|---|---|---|
| Upper extraction | Gradient Boosting | 92.52% ± 2.51% |
| Lower extraction | Gradient Boosting | 93.45% ± 2.48% |
| General extraction | Node-GAM (SMOTE) | 91.56% ± 2.34% |

---

## Dataset

- **N = 500 patients** from Cali, Valle del Cauca, Colombia
- Ethnicities: Mestizo and Afro-Colombian
- **36 variables:** 26 cephalometric, 7 clinical (from CBCT), 3 demographic
- Cephalometric data extracted from CBCT volumes corrected to Natural Head 
  Position (NHP) using BlueSkyPlan4 (v4.13.31)
- Ethics approval: Universidad Autónoma de Occidente, 
  Ethics Committee Act No. 01-2024 (February 12, 2024)

> ⚠️ **Note:** Raw CBCT images and patient photographs are **not included** 
> in this repository due to patient privacy and data protection regulations.

---

## Preprocessing Pipelines

The following preprocessing strategies were evaluated for each model:

- No transformation (`Any`)
- `StandardScaler`
- `RobustScaler`
- `MinMaxScaler`
- `PCA`
- `PCA + StandardScaler`
- `PCA + RobustScaler`
- `PCA + MinMaxScaler`

Class imbalance was handled using **SMOTE** (Synthetic Minority Over-sampling 
Technique). Hyperparameter optimization was performed via **Grid Search** 
with 5-fold cross-validation.

---

## Interpretability Methods

- **Feature Importance** — ranking of variables by contribution to model decisions
- **SHAP Values** — individual feature contribution per prediction
- **Modified Partial Dependence Plots** — decision threshold identification 
  via first-derivative analysis, with critical thresholds marked for:
  - L1-APog
  - Lower crowding
  - Upper crowding
  - Overjet

---

## Requirements

Install dependencies with:

```bash
pip install -r requirements.txt
```

Key libraries:
- `scikit-learn`
- `xgboost`
- `node-gam`
- `shap`
- `torch`
- `numpy`
- `pandas`
- `matplotlib`
- `imbalanced-learn`

---

## Citation

If you use this code or data in your research, please cite:

```bibtex
@article{ferro2026dental,
  title={Evaluation of Machine Learning and Deep Learning Models for Dental 
         Extraction Decision-Making with Interpretability Methods in a 
         Mestizo Population},
  author={Ferro Sanchez, Carlos Andres and Holguín-García, Sergio Alejandro 
          and Diaz Laverde, Cristian Orlando and Medellin Fuentes, Ricardo 
          and Aristizábal, Juan Fernando and Nope Rodríguez, Sandra Esperanza 
          and Campo Salazar, Oscar Iván and Tabares-Soto, Reinel 
          and Bravo-Ortiz, Mario Alejandro and Cevidanes, Lucia},
  year={2026}
}
```

> Update the citation with the journal name, volume, pages, and DOI once published.

---

## License

This project is licensed under the MIT License. See `LICENSE` for details.

---

## Acknowledgments

- Universidad Autónoma de Occidente (doctoral assistantship scholarship)
- Universidad Autónoma de Manizales — projects 873-139 and 847-2023 TD
- Universidad de Caldas — project PRY-89
- ANID PIA/BASAL FB0002 and ANID/PIA/ANILLO ACT210096
- ANID IDeA I+D 2023, code ID23I10357
