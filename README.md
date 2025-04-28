# Youth Cancer Prediction using Support Vector Machines

## Overview
This project explores the use of Support Vector Machines (SVMs) to predict whether an individual has a history of cancer based on health and demographic indicators from the NHIS 2022 dataset.

Three SVM models were built and compared:
- Linear SVM
- Radial SVM
- Polynomial SVM

## Dataset
- Source: NHIS 2022 Public Dataset
- Variables used:
  - **AGE** (Age of respondent)
  - **SEX** (Sex: Male/Female)
  - **POVERTY** (Income to poverty ratio)
  - **BMICALC** (Body Mass Index)
  - **ALCDAYSYR** (Number of days drank alcohol in the past year)

## Data Cleaning
- Removed missing or invalid responses for key variables (coded as 7, 8, 9, 995, etc.).
- Converted categorical variables to factors (e.g., SEX and CANCEREV).
- Filtered data:
  - Only individuals **over 45 years old**
  - **Married with spouse present**
  - **More than 50 days of alcohol use**

## Data Splitting
- 70% of the cleaned dataset was used for training.
- 30% was used for testing.

## Modeling
### Linear SVM
- Kernel: `linear`
- Cost: tuned from 0.01 to 100.
- **Best Cost:** 0.01
- **Accuracy after tuning:** ~81%

### Radial SVM
- Kernel: `radial`
- Cost and gamma tuned.
- **Best Cost:** 0.1
- **Best Gamma:** 0.5
- **Accuracy after tuning:** ~81%

### Polynomial SVM
- Kernel: `polynomial`
- Degree and cost tuned.
- **Best Degree:** 2
- **Best Cost:** 0.01
- **Accuracy after tuning:** ~81%

## Key Observations
- **After tuning, all three models achieved very similar accuracy (~81%).**
- Radial SVM captured non-linear patterns slightly better but was not drastically better than linear SVM.
- Polynomial SVM performed similarly but had more computational overhead.
- Class imbalance was a challenge: the number of "No Cancer" cases greatly outnumbered "Yes" cases.

## Plots
- Boxplots of Alcohol Use, Age vs Cancer Diagnosis
- Decision Boundary Cartoon Plots:
  - Linear SVM: AGE vs BMI
  - Radial SVM: POVERTY vs AGE
  - Polynomial SVM: AGE vs BMI
- Confusion Matrices for each model.

## Methodology Summary
- Cleaned and subsetted the dataset to focus on a higher-risk group.
- Trained SVM models using different kernels.
- Used cross-validation with 10-folds for tuning.
- Evaluated based on Accuracy, Precision, Recall, and F1 Score.
- Compared model performance after tuning.

## Conclusion
- Age, BMI, Poverty ratio, and Alcohol consumption were important predictors.
- Radial SVM was best suited for handling complex patterns but not significantly better than linear.
- Tuning hyperparameters improved model stability but not overall accuracy beyond 81%.

## Technologies Used
- R
- Libraries: `e1071`, `caret`, `ggplot2`, `dplyr`

## Author
- Prateek Pagare

---

*Note: No ROC curves were included in this version.*
