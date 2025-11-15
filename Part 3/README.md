# COMPAS Recidivism Bias Audit

## A Fairness Analysis Using Python & AIF360


---

📌 Overview

This project performs a fairness and bias audit on the COMPAS Recidivism Risk Score Dataset, investigating whether risk predictions disproportionately disadvantage Black defendants. The analysis uses Python, Pandas, Matplotlib, and IBM’s AI Fairness 360 (AIF360) toolkit.

The aim is to evaluate racial disparities in risk classification and demonstrate responsible, ethical AI development.


---

⚙️ Methodology

1. Dataset Preparation

Loaded the COMPAS two-year recidivism dataset.

Selected key fields: age, sex, race, priors_count, and two_year_recid.

Cleaned data by removing missing entries.

Encoded:

sex → Male = 1, Female = 0

race → African-American = 1 (protected group), others = 0

label → No recidivism = 0 (favorable), Recidivism = 1 (unfavorable)



2. Fairness Wrapping

The cleaned dataset was converted into an AIF360 BinaryLabelDataset, enabling the calculation of fairness metrics such as:

Mean Difference

Disparate Impact


3. Model Training

A Logistic Regression model was trained using:
age, sex, and priors_count
The model’s predictions were wrapped into AIF360 for post-model fairness evaluation.

4. Bias Metrics Computed

False Positive Rate Difference

False Negative Rate Difference

Overall disparate treatment and impact

Visualization of FPR differences between Black and non-Black groups



---

📊 Findings

1. Pre-Model Bias

The dataset showed measurable racial disparities, with mean difference and disparate impact indicating baked-in structural bias.

2. Model Bias

Even after training, the model produced a higher false positive rate for Black defendants, meaning they were more likely to be incorrectly labeled as high-risk.
This mirrors similar findings reported by ProPublica.

3. Visualization

A bar chart comparing FPR values confirmed systematic differences in misclassification rates across racial groups.


---

🛠️ Recommendations

To improve fairness in risk assessment systems:

Reweighing to balance group representation

Preprocessing techniques (e.g., disparate impact remover)

Fairness-aware model training (in-processing)

Regular transparency reports documenting fairness metrics

Human-in-the-loop oversight for high-stakes decisions


Implementing these steps reduces algorithmic bias and supports ethical, trustworthy AI systems.


---

📁 Tools Used

Python

Pandas

Matplotlib

AIF360 (IBM)

Logistic Regression (Sklearn)