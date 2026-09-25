# IBM Telco Customer Churn — Customer Retention Analytics

An end-to-end machine-learning project for predicting customer churn, analysing customer retention drivers, and supporting data-driven retention decisions using the IBM Telco Customer Churn dataset.

## Project Overview

IBM (International Business Machines Corporation) is a global technology company specialising in enterprise computing, software, cloud technologies, artificial intelligence, data and analytics, and consulting services.

As part of its analytics resources, IBM provides the **Telco Customer Churn** sample dataset for demonstrating customer analytics and churn modelling.

The dataset represents a **fictional telecommunications company** providing home phone and Internet services to **7,043 customers in California**. It contains customer demographic, account, service, billing, satisfaction and behavioural information, together with indicators showing whether customers remained with or left the company.

This project uses the dataset to develop an end-to-end customer retention analytics solution that moves beyond simply predicting churn toward understanding **which customers are at risk, why they are at risk, and how predictive insights can support retention decisions**.

---

## Business Problem

Customer churn occurs when an existing customer stops using a company's products or services. High churn can negatively affect recurring revenue, customer lifetime value, acquisition efficiency, and long-term profitability.

The central business question is:

> **Which customers are most likely to churn, what factors are driving their churn risk, and how can these predictions support targeted customer retention strategies?**

From a machine-learning perspective, the primary task is a binary classification problem:

\[
Y =
\begin{cases}
1, & \text{Customer churns} \\
0, & \text{Customer remains}
\end{cases}
\]

Given customer characteristics \(X\), the model estimates:

\[
P(Y=1\mid X)
=
P(\text{Churn}\mid X)
\]

Rather than using this probability only for classification, the resulting churn propensity score can be incorporated into a broader customer decision-support process.

---

## Project Objectives

The project aims to:

- Explore customer demographic, service, account and behavioural characteristics associated with churn.
- Develop reproducible data-cleaning and feature-engineering pipelines.
- Train and compare multiple machine-learning classification models.
- Estimate customer-level churn probabilities.
- Evaluate models using appropriate classification and ranking metrics.
- Identify the most important drivers of customer churn.
- Segment customers according to churn risk and customer characteristics.
- Translate model predictions into actionable retention insights.
- Extend churn prediction toward **next-best-action and retention decision support**.
- Deploy the resulting ML solution using a cost-efficient AWS architecture.
- Implement appropriate model monitoring and MLOps practices.

---

## Dataset

The IBM Telco Customer Churn dataset contains information on **7,043 fictional telecommunications customers**.

The available information includes:

### Customer Demographics

Examples include:

- Gender
- Age-related information
- Dependents
- Partner status

### Account Information

Examples include:

- Customer tenure
- Contract type
- Payment method
- Paperless billing
- Monthly charges
- Total charges

### Services

Customer subscriptions include services such as:

- Phone service
- Internet service
- Multiple lines
- Online security
- Online backup
- Device protection
- Technical support
- Streaming TV
- Streaming movies

### Customer Retention Information

Depending on the version of the IBM dataset, retention-related information may include:

- Churn status
- Churn score
- Satisfaction score
- Customer Lifetime Value (CLTV)
- Churn reason/category

The primary target variable for the predictive modelling component is:

**Churn**

---

## Analytical Workflow

The project follows an end-to-end data-science lifecycle:

```text
Customer Data
      |
      v
Data Understanding
      |
      v
Data Cleaning
      |
      v
Exploratory Data Analysis
      |
      v
Feature Engineering
      |
      v
Train / Validation / Test
      |
      v
Model Development
      |
      v
Model Evaluation
      |
      v
Churn Propensity Scores
      |
      v
Model Explainability
      |
      v
Customer Risk Segmentation
      |
      v
Retention Decision Support
```

---

## Exploratory Data Analysis

The exploratory analysis investigates relationships between churn and customer characteristics such as:

- Contract type
- Customer tenure
- Monthly charges
- Total charges
- Internet service
- Technical support
- Payment method
- Number of subscribed services
- Customer demographics

The objective is not only to visualise the data but also to identify potential behavioural and commercial patterns that can inform feature engineering and model development.

---

## Data Preprocessing

The preprocessing pipeline may include:

- Missing-value analysis and treatment
- Duplicate detection
- Data-type correction
- Categorical-variable encoding
- Numerical feature scaling where required
- Outlier investigation
- Feature transformation
- Feature selection
- Prevention of target leakage
- Train/validation/test separation

Preprocessing transformations used during training will be incorporated into reproducible pipelines to ensure that identical transformations are applied during inference.

---

## Machine-Learning Models

The project will compare multiple classification approaches, potentially including:

- Logistic Regression
- Decision Tree
- Random Forest
- Gradient Boosting
- XGBoost
- Neural Networks

A simple interpretable model such as Logistic Regression will provide a baseline before more complex models are evaluated.

---

## Model Evaluation

Because business decisions depend on correctly identifying customers at risk, model evaluation will extend beyond classification accuracy.

Metrics may include:

\[
\text{Precision}
\]

\[
\text{Recall}
\]

\[
F_1
\]

\[
ROC\text{-}AUC
\]

\[
PR\text{-}AUC
\]

and the confusion matrix.

Where customer-level probabilities are used for downstream decisions, probability calibration will also be considered.

The final model will be selected based not only on predictive performance but also on interpretability, robustness and suitability for the intended business application.

---

## Churn Propensity

Instead of producing only a binary prediction, the model will generate a customer-level churn probability:

\[
P(\text{Churn}\mid X_i)
\]

For example:

```text
Customer ID:       7590-VHVEG
Churn Probability: 0.81
Risk Level:        High
```

Customers can subsequently be grouped into operational risk categories such as:

```text
Low Risk
Medium Risk
High Risk
```

This allows retention resources to be prioritised toward customers with elevated churn propensity.

---

## Model Explainability

Prediction alone does not answer the business question:

> **Why is this customer considered at risk?**

Model explainability will therefore be incorporated using global feature importance and, where appropriate, local explanation techniques such as SHAP.

A customer-level explanation might conceptually resemble:

```text
Customer Churn Risk: 81%

Major contributing factors
--------------------------------
Month-to-month contract
Short customer tenure
High monthly charges
No technical support
Electronic payment method
```

This allows predictions to be interpreted within a customer-retention context.

---

## Customer Retention Decision Support

The longer-term objective is to extend the predictive model from:

\[
\text{Prediction}
\]

toward:

\[
\boxed{
\text{Prediction}
\rightarrow
\text{Insight}
\rightarrow
\text{Decision}
\rightarrow
\text{Business Value}
}
\]

The churn model can therefore serve as the predictive layer of a retention decision-support system.

Future extensions may incorporate:

- Customer segmentation
- Offer eligibility rules
- Retention incentives
- Customer lifetime value
- Offer-response propensity
- Next-best-offer recommendations
- Campaign budget constraints
- Incremental value estimation
- ROI optimisation

For customer \(i\) and retention action \(j\), an expected-value framework can be represented conceptually as:

\[
EV_{ij}
=
P(\text{response}_{ij})V_i-C_{ij}
\]

where:

- \(P(\text{response}_{ij})\) is the estimated probability of customer \(i\) responding to intervention \(j\),
- \(V_i\) represents the estimated customer value,
- \(C_{ij}\) represents the cost of the intervention.

The resulting decision problem can then identify retention actions that maximise expected customer value while respecting operational or campaign constraints.

---

## AWS Deployment Architecture

The project is intended to demonstrate not only model development but also **cloud-based ML deployment and MLOps**.

A cost-efficient AWS architecture is planned:

```text
                         User
                           |
                           v
                    Web Dashboard
                           |
                           v
                     API Gateway
                           |
                           v
                       Lambda
                           |
                +----------+----------+
                |                     |
                v                     v
          Churn Model          Decision Engine
                |                     |
                +----------+----------+
                           |
                           v
                    Prediction/API


                 ML DEVELOPMENT

                    Amazon S3
                        |
                        v
                Data Processing
                        |
                        v
               SageMaker Training
                        |
                        v
                Model Evaluation
                        |
                        v
                 Model Registry
                        |
                        v
                Model Artifact


                 MLOps / DevOps

GitHub --> CI/CD --> Docker --> Amazon ECR --> Deployment

                         |
                         v
                    CloudWatch
```

The public demonstration is designed around serverless or usage-based services where practical to minimise idle infrastructure costs.

---

## AWS Services

The deployment may use:

- **Amazon S3** — dataset and model-artifact storage
- **Amazon SageMaker AI** — model training and ML lifecycle management
- **AWS Lambda** — cost-efficient serverless inference/application logic
- **Amazon API Gateway** — REST API exposure
- **Amazon ECR** — Docker container storage
- **Amazon CloudWatch** — logging and operational monitoring
- **AWS IAM** — service permissions and access control

---

## MLOps

The production-oriented extension of the project will demonstrate:

- Reproducible preprocessing
- Model versioning
- Model registration
- Containerisation
- Automated testing
- CI/CD
- Deployment
- Logging
- Model monitoring
- Data/model drift analysis
- Controlled model updates

The objective is to demonstrate the complete ML lifecycle rather than only model training inside a notebook.

---

## Technology Stack

**Data Science**

`Python` · `Pandas` · `NumPy` · `scikit-learn` · `XGBoost`

**Visualisation**

`Matplotlib` · `Power BI / React Dashboard`

**Explainability**

`SHAP`

**Backend**

`Python` · `Flask/REST API`

**Cloud & MLOps**

`AWS` · `SageMaker` · `S3` · `Lambda` · `API Gateway` · `ECR` · `CloudWatch`

**DevOps**

`Docker` · `GitHub Actions` · `CI/CD`

---

## Repository Structure

```text
ibm-telco-retention/
|
|-- data/
|   |-- raw/
|   `-- processed/
|
|-- notebooks/
|   |-- 01_data_understanding.ipynb
|   |-- 02_eda.ipynb
|   |-- 03_feature_engineering.ipynb
|   `-- 04_model_development.ipynb
|
|-- src/
|   |-- preprocessing.py
|   |-- features.py
|   |-- train.py
|   |-- evaluate.py
|   `-- inference.py
|
|-- decision_engine/
|   |-- segmentation.py
|   |-- offers.py
|   `-- optimisation.py
|
|-- api/
|   `-- app.py
|
|-- tests/
|
|-- docker/
|   `-- Dockerfile
|
|-- .github/
|   `-- workflows/
|
|-- requirements.txt
|-- README.md
`-- LICENSE
```

---

## Project Roadmap

- [ ] Data acquisition and understanding
- [ ] Exploratory data analysis
- [ ] Data preprocessing
- [ ] Feature engineering
- [ ] Baseline modelling
- [ ] Model comparison and tuning
- [ ] Churn propensity scoring
- [ ] Model explainability
- [ ] Customer risk segmentation
- [ ] Retention decision engine
- [ ] Next-best-offer extension
- [ ] ROI/value optimisation
- [ ] REST API
- [ ] Docker containerisation
- [ ] AWS deployment
- [ ] CI/CD pipeline
- [ ] Model monitoring
- [ ] Interactive analytics dashboard

---

## Business Applications

Although demonstrated using telecommunications customer data, the underlying analytical framework is transferable to customer-retention problems in:

- Banking and financial services
- Retail
- Insurance
- Telecommunications
- Subscription businesses
- E-commerce
- Transportation and mobility services
- Loyalty and rewards programmes

The general decision problem remains:

\[
\boxed{
\text{Who is at risk?}
\rightarrow
\text{Why?}
\rightarrow
\text{What action should be taken?}
\rightarrow
\text{What value can the action generate?}
}
\]

---

## Disclaimer

The IBM Telco Customer Churn dataset represents a **fictional telecommunications company** and is intended for analytical and educational purposes. The results of this project should therefore not be interpreted as findings about IBM's own customers or telecommunications operations.

This repository is an independent data-science portfolio project and is not affiliated with or endorsed by IBM.
