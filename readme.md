# Hybrid Ensemble Learning for Precision Reproductive and Decision Support in Dairy Cattle

## Overview

Accurate estimation of the **non-return rate (NRR)** — the proportion of dairy cows not returning to estrus after artificial insemination (AI) — is critical for improving reproductive efficiency in dairy farming.

This repository contains the code and pipeline used to analyze **118,996 insemination records** from Iranian Holstein herds using a rigorously designed machine-learning workflow. The study demonstrates how **advanced preprocessing and hybrid ensemble models** can robustly predict estrus and support precision dairy management.

---

## Features

**Dataset:** `clean_sql_export_for_datamining_day_to_quartile.xlsx` (main dataset)

| Feature Name | Definition |
|--------------|------------|
| Animal | Animal ID |
| PAS | Parturition Status [Stillbirth-Natural=12, Stillbirth=1, Natural=2] |
| BT | Birth Type [Singlet=1, Twins=2, Triplets=3] |
| Sex | Calf Sex [Singlet-Male=M, Singlet-Female=F, Mixed=, Twins-Female=2F, Twins-Male=2M] |
| WB | Birth weight of calf at calving before insemination |
| DS | Dystocia score at calving |
| RP | Retained Placenta [Yes=1, No=0] |
| TNR | Total number of retained placenta in total parties |
| DR | Dry Period |
| GL | Gestation Length |
| DMP | Days in milk at first insemination of current lactation period |
| DFS | Age at first insemination |
| IFI | Interval from insemination to previous abortion |
| NPA | Number of previous abortion |
| DIM | DIM ID |
| SIR | SIR ID |
| AI | Age at insemination |
| DI | Day of insemination based upon lunar calendar |
| MI | Month of insemination based upon lunar calendar |
| YI | Year of insemination based upon lunar calendar |
| LP | Lactation Period |
| TP | Type of Gestation [Natural=1, Artificial-Insemination=2, Embryo-Transfer=3] |
| S | Sperm ID |
| AIT | Artificial Insemination Technician |
| DM | Days in milk at insemination |
| AM | Average milk yield on the day of insemination |
| CL | Classification of lunar date day into four categories |
| C1 | Classification of insemination time into four categories |
| PS | Pregnancy Status [Return to estrus=0, Not return to estrus=1] **(Target column)** |

---

## Data Preprocessing

### Initial Preprocessing
1. Data conversion  
2. Elimination of missing/invalid values  
3. Addressing skewness issues  
4. Outlier elimination  

### Final Preprocessing
1. Feature selection  
2. Examination of categorical columns containing many categories  
3. Scaling of continuous columns  
4. Data balancing (SMOTENC)

---

## Model Implementation and Comparison

- **Benchmarking:** 15 machine-learning algorithms using PyCaret  
- **Hybrid Ensemble:** Two-tier STACKING_VOTING_HYBRID (SVH)
  - **Tier 1:** LGBM, Random Forest, XGBoost, Extra Trees (voting mechanism)  
  - **Tier 2:** Outputs of Tier 1 integrated with Gradient Boosting Machine, Decision Tree, KNN, and AdaBoost (stacking meta-classifier)

### Evaluation Metrics
- **Accuracy:** Overall correctness of predictions  
- **Precision:** Correctly predicted positives / Total predicted positives  
- **Recall:** Correctly predicted positives / Total actual positives  
- **F1 Score:** Harmonic mean of precision and recall  
- **MCC (Matthews Correlation Coefficient):** Balanced evaluation for imbalanced datasets  
- **Cohen's Kappa:** Measures agreement between predicted and actual classes accounting for chance

---

## References / Libraries Used

- **Python (>=3.8)** — [https://www.python.org/](https://www.python.org/)  
- **pandas** — [https://pandas.pydata.org/](https://pandas.pydata.org/)  
- **numpy** — [https://numpy.org/](https://numpy.org/)  
- **scikit-learn** — [https://scikit-learn.org/](https://scikit-learn.org/)  
- **scipy** — [https://scipy.org/](https://scipy.org/)  
- **imbalanced-learn (imblearn)** — [https://imbalanced-learn.org/stable/](https://imbalanced-learn.org/stable/)  
- **PyCaret** — [https://pypi.org/project/pycaret/](https://pypi.org/project/pycaret/)  
- **XGBoost** — [https://xgboost.readthedocs.io/en/stable/](https://xgboost.readthedocs.io/en/stable/)  
- **LightGBM** — [https://lightgbm.readthedocs.io/en/stable/](https://lightgbm.readthedocs.io/en/stable/)  
- **matplotlib** — [https://matplotlib.org/](https://matplotlib.org/)  
- **seaborn** — [https://seaborn.pydata.org/](https://seaborn.pydata.org/)  
- **psutil** — [https://psutil.readthedocs.io/en/latest/](https://psutil.readthedocs.io/en/latest/)  
- **cpuinfo** — [https://github.com/workhorsy/py-cpuinfo](https://github.com/workhorsy/py-cpuinfo)

---

## Related Research

This repository accompanies ongoing research work titled:  
**"Hybrid Ensemble Methods for Reproduction Management in Dairy Cattle: Toward Precision and Breeding Decision Support"**  
*(in preparation)* by Parham Khalifehzadeh, Mostafa Ghaderi-Zefrehei, Farjad Rafeie, Mohammadreza Hashemi, Somayeh Sharifi, Mahsa Rahmani, Saeid Ansari Mahyari, Mustafa Muhaghegh-Dolatabady

---
