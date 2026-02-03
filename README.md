# Detection-of-fraudulent-jobs-
# Job Fraud Detection using Logistic Regression model
# 📌 Project Overview

This project investigates fraudulent job postings using structured job-advertisement data and machine learning. The analysis is framed around a business trust & safety problem, with a focus on:

1. Understanding patterns associated with fraudulent job listings
2. Handling severe class imbalance
3. Building an interpretable classification model
4. Explaining predictions using SHAP values

Rather than optimizing accuracy alone, the project emphasizes business interpretability, risk identification, and explainable decision-making.

# Business Report
## Executive Summary

Online job platforms face reputational and financial risks when fraudulent job postings are not detected early. This analysis explores a job-posting dataset to identify characteristics associated with fraudulent listings and to develop an interpretable predictive model.
Exploratory Data Analysis (EDA) reveals strong concentrations of fraud across specific job titles, regions, departments, salary ranges, operations, and qualification levels. A regression-based classification model, interpreted using SHAP values, highlights which features most strongly influence fraud predictions.

The project demonstrates how explainable machine learning can support early fraud flagging while remaining transparent and actionable for business stakeholders.

# Business Problem

Fraudulent job postings can:
1. Mislead job seekers
2. Cause financial losses
3. Damage platform credibility

# Business Objective

Identify characteristics associated with fraudulent job postings and develop an interpretable model that can help flag high-risk postings before publication.
A successful solution must balance:
1. Predictive performance
2. Interpretability
Practical usefulness for trust & safety teams

## Hypothesis Tested

The notebook explicitly investigates the following hypothesis:
Profile length hypothesis
1. Job postings with shorter profile lengths are more likely to be fraudulent

## Exploratory Data Analysis (EDA)

EDA is conducted with a business-first mindset, focusing on fraud exposure and risk concentration.
Key Findings:
1. Class Imbalance
Fraudulent postings form a small minority of the dataset.
This necessitates techniques beyond standard accuracy-based evaluation.

3. Job Titles
Certain job titles dominate fraud counts.
Some titles (e.g. Administrative Assistant) exhibit the highest fraud rate, indicating a higher likelihood of fraud rather than volume effects.

4. Geographic Patterns
US, Texas (Houston) has the highest fraud count.
US, CA (San Mateo) has the highest fraud rate.

5. Department & Operations
Engineering departments show the highest fraud counts.
Administrative operations exhibit elevated fraud exposure.

6. Salary & Qualification
Mid-to-high salary ranges show notable fraud concentration.

Lower qualification requirements are associated with higher fraud counts.
7. Missing Data as Signal
Features with high missing rates are not dropped blindly.

Missingness itself is treated as potentially informative for fraud detection.

##  Handling Class Imbalance: SMOTE

Given the extreme imbalance between legitimate and fraudulent postings, SMOTE (Synthetic Minority Over-sampling Technique) is applied during model training.

## Rationale

1.Prevents the model from defaulting to the majority (legitimate) class

2. Improves exposure to minority fraud patterns

3. Enables better learning of fraud-related feature interactions

SMOTE is applied only to the training data to avoid data leakage.

## 🤖 Model Development & Cross-Validation

1. A regression-based classification model is trained

2. Cross-validation is used to evaluate model stability

3. Performance is assessed with metrics suitable for imbalanced classification
   
4. Cross-validation ensures that observed patterns are not artifacts of a single train-test split.

## 🎚️ Threshold Tuning

Rather than relying on a default probability threshold:
Decision thresholds are evaluated based on fraud-detection priorities

# Model Explainability with SHAP

SHAP (SHapley Additive exPlanations) is used to interpret both global and local model behavior.
🌍 Global SHAP Value Analysis
Mean SHAP values identify the most influential features
Features related to profile completeness and structure emerge as strong predictors

This confirms that the model is learning intuitively reasonable fraud signals rather than spurious correlations.

# Force Plot Interpretation

Force plots explain individual predictions by showing how features push the model output:

Red features increase fraud likelihood

Blue features decrease fraud likelihood

The base value represents the average model prediction

A strongly negative force value (e.g. −5.93) indicates that feature contributions significantly reduce the predicted fraud risk relative to the baseline.

# Waterfall Plot Interpretation

Waterfall plots provide a step-by-step breakdown of how individual features move the prediction from the base value to the final output.

Key observations:

A small number of dominant features often drive predictions

Negative SHAP values correspond to fraud-reducing signals

Variation between runs is expected due to sampling, SMOTE, and cross-validation

This behavior reflects normal model stochasticity, not instability.

Key Business Insights

Fraud is strongly associated with incomplete or low-information job postings

Missing values carry predictive meaning

High fraud count does not always imply high fraud risk

Explainable models enable transparent and defensible moderation decisions

Skills Demonstrated

## Business-driven EDA

1. Imbalanced classification handling

2. Hypothesis-based analysis

3. Threshold tuning

4. Explainable AI (SHAP)

5. Model interpretability for non-technical stakeholders

## Future Work

1. Text embeddings for job descriptions

2. Cost-sensitive learning

3. Temporal fraud pattern analysis

4. Deployment-ready risk scoring pipeline
5. The focus is on risk identification, not pure accuracy
6. Use a treebased model to describe the 

This aligns the model’s behavior with real-world moderation and review workflows.
