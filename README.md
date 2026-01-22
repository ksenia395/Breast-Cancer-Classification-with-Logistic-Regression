# Breast-Cancer-Classification-with-Logistic-Regression
This project is a binary classification case study based on the Breast Cancer Wisconsin (Diagnostic) dataset.  The goal is to predict whether a tumor is malignant or benign using numerical features extracted from medical images. 
The main focus of the project is building a correct and clean Logistic Regression pipeline, with proper validation and evaluation.

🎯 Problem Statement

Breast cancer diagnosis is a high-risk classification problem where different types of errors have different costs.

Malignant tumors (1) should be detected with high recall

Benign tumors (0) should not be misclassified excessively

Because of this, the project emphasizes:

probability-based predictions

ROC-AUC evaluation

threshold analysis instead of accuracy only

📊 Dataset

The dataset is based on the Breast Cancer Wisconsin (Diagnostic) data.

Key characteristics:

569 samples

30 numerical features per sample

Target variable:

1 → malignant

0 → benign

Typical malignant tumors show:

larger radius, area, and perimeter

higher concavity and irregular texture

Malignant class is treated as the positive class.

🛠 Data Preparation

Steps applied:

Removed identifier column (id)

Separated target variable (diagnosis)

Converted target to binary format

Used stratified train/validation split to preserve class balance

All features are numerical, so no categorical encoding was required.

🤖 Model

The model is built using scikit-learn Pipeline:

StandardScaler — feature normalization

LogisticRegression — linear classifier with L2 regularization

Using a pipeline ensures that:

scaling is fitted only on training data

data leakage is avoided

📐 Validation Strategy

Two validation approaches were used:

Cross-Validation

5-fold StratifiedKFold

Evaluation metric: ROC-AUC

Holdout Validation

80% training / 20% validation split

ROC-AUC calculated on validation set

ROC-AUC was chosen because it evaluates ranking quality independent of threshold choice.

📈 Results

Cross-validation ROC-AUC: ~0.99

Holdout ROC-AUC: close to CV score

## 🔍 Why ROC-AUC instead of Accuracy

Accuracy can be misleading in medical classification problems.

ROC-AUC evaluates how well the model ranks malignant cases above benign ones,

independently of a fixed decision threshold.

This makes ROC-AUC more suitable for problems where the cost of errors is asymmetric.

This indicates:

strong class separability

no significant overfitting
## 📈 ROC Curve
The ROC curve below shows strong class separability on the validation set.

![ROC Curve](images/roc_curve.png)

⚖️ Decision Threshold

Logistic Regression outputs probabilities:

P(malignant | features)


While the default threshold is 0.5, in medical tasks:

false negatives (missed cancer cases) are more critical than false positives

Threshold adjustment allows:

higher recall for malignant cases

better control over error trade-offs

✅ Conclusions

Logistic Regression performs very well on this dataset

Proper preprocessing and validation are essential

ROC-AUC is more informative than accuracy for medical classification

Threshold tuning is an important part of model evaluation

🔧 Possible Improvements

Hyperparameter tuning (C)

Using class_weight="balanced"

Feature importance analysis using model coefficients

Comparison with non-linear models (e.g. Gradient Boosting)

📁 Repository Structure (suggested)
├── notebook.ipynb
├── README.md
├── requirements.txt

🧠 Key Takeaway

This project demonstrates a clean end-to-end classification workflow, focusing on correctness, interpretability, and evaluation — rather than leaderboard optimization.
## 📎 Kaggle Notebook
The full implementation and experiments are available on Kaggle:

 👉 [View the Kaggle Notebook](https://www.kaggle.com/code/ksenia395/notebookaf618d359a)
