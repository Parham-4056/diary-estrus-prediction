# Estrus Prediction in Iranian Holstein Dairy Herds Using Machine Learning Ensembles

# overvoiew

Accurate estimation of the non-return rate (NRR)- the proportion of diary cows
not returning to estrus after artificial insemination (AI)- is critical for improving
reproductive efficiency in diary farming.

This repository contains the code and pipline used to analyze 118996 insemination records
from Iranin Holstein Herds using a rigorously designed machine-learning workflow. The study
demonstrates how advanced preprocessing and hybrid ensemble models can robustly predict estrus
and support precision dairy management.

# Features

datasetname:clean_sql_export_for_datamining_day_to_quartile.xlsx is main dataset

Features_Name         Definition

Animal	              Animal ID
PAS	                  Parturition Status [Stillbirth-Natural=12, Stillbirth=1, Natural=2]
BT	                  Birth Type [Singlet=1, Twins=2, Triplets=3]
Sex	                  Calf Sex [Singlet-Male=M, Singlet-Female=F, Mixed=, Twins-Female=2F, Twins-Male=2M]
WB	                  Birth weight of calf at calving before insemination
DS	                  Dystocia score at calving
RP	                  Retained Placenta [Yes=1, No=0]
TNR	                  Total number of retained placenta in total parties
DR	                  Dry Period
GL	                  Gestation Length
DMP	                  Days in milk at first insemination of current lactation period
DFS	                  Age at first insemination
IFI	                  Interval from insemination to previous abortion
NPA	                  Number of previous abortion
DIM	                  DIM ID
SIR	                  SIR ID
AI	                  Age at insemination
DI	                  Day of insemination based upon lunar calendar
MI	                  Month of insemination based upon lunar calendar
YI	                  Year of insemination based upon lunar calendar
LP	                  Lactation Period
TP	                  Type of Gestation [Natural=1, Artificial-Insemination=2, Embryo-Transfer=3]
S	                  Sperm ID
AIT	                  Artificial Insemination Technician
DM	                  Days in milk in insemination
AM	                  Average milk yield on the day of insemination
CL	                  Classification of lunar date day into four categories
C1	                  Classification of insemination time into four categories
PS	                  Pregnancy Status [Return to estrus=0, Not return to estrus=1] (Target column)


# Data Preprocessing

a:inintial preprocessing: 1-data conversion 2-elimination 3-addressing_skewness_issues 4-outlier_elimination

b:final preprocessing: 1-Feature selection 2- examination_of_two_categorical_columns_containing_substantial_number_of_categories
                       3-scaling_of_continuous_columns 4-data_balancing
					   
c:models implementation and comparison:

-benchmarking of 15 machine-learning algorithms using PyCaret

-development of a two-tier hybrid ensemble (STACKING_VOTING_HYBRID, SVH):
    -Tier1: LGBM,Random Forest,XGBoost,Extra Trees combined via avoting mechanism
    -Tier2:Outputs of Tier1 integrated with Gradient Boosting Machine,Decision Tree,KNN,and AdaBoost
         using a stacking meta_classifier
-evaluation metrics:
    -Accuracy: Overall correctness of predictions
    -Precision:Correctly Predicted positive/ Total predicted positives
    -Recall:Correctly predicted positives/ total actual positives
    -F1_Score:Harmonic mean of precision and recall
    -MCC(Matthews Correlation Coefficient):Balanced evaluation for imbalanced datasets
    -Cohen's Kappa:Measures agreement between predicted and actu classes accounting for chance

# References

[python-version>=3.8](https://www.python.org/)

[pandas](https://pandas.pydata.org/)

[numpy](https://numpy.org/)

[scikit-learn](https://scikit-learn.org)

[scipy](https://scipy.org/)

[imblearn](https://imbalanced-learn.org/)

[Pycaret](https://pypi.org/project/pycaret/)

[XGBoost](https://xgboost.readthedocs.io/en/stable/)

[LightGBM](https://lightgbm.readthedocs.io/en/stable/)

[matplotlib](https://matplotlib.org/)

[seabron](https://seaborn.pydata.org/)

[psutil](https://psutil.readthedocs.io/en/latest/)

[cpuinfo](https://github.com/workhorsy/py-cpuinfo)

## Related Research

This repository accompanies ongoing research work titled: "Hybrid Ensemble Methods for Reproduction Management in Dairy Cattle: Toward Precision and Breeding Decision Support" (in preparation) by
Parham Khalifehzadeh,Mostafa Ghaderi-Zefrehei,Somayeh Sharifi, Mahsa Rahmani,Mustafa Muhaghegh-Dolatabady