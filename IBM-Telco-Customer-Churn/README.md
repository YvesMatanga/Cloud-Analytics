
# IBM Telco Customer Churn — Customer Retention Analytics

An end-to-end data science project focused on predicting customer churn, understanding customer behaviour, and supporting data-driven retention strategies using the IBM Telco Customer Churn dataset.

## 1. Project Overview

The IBM Telco Customer Churn dataset represents a fictional telecommunications company serving 7,043 customers in California.

The dataset contains information about customer demographics, subscriptions, billing, account history and churn behaviour.

The project explores how machine learning can help telecommunications companies identify customers at risk of leaving and support targeted retention decisions.

**Business question:**

> Which customers are likely to leave, what factors contribute to their churn risk, and how can the company improve customer retention?

## 2. Project Objectives

- Explore customer behaviour and identify patterns associated with churn.
- Clean and preprocess customer data.
- Develop and compare machine-learning classification models.
- Predict customer-level churn probabilities.
- Identify important factors influencing churn.
- Segment customers into different churn-risk categories.
- Support customer retention decisions using predictive insights.
- Explore cloud deployment and MLOps using AWS.

## 3. Dataset

**Source:** IBM Telco Customer Churn

**Customers:** 7,043

**Target variable:** Churn (Yes/No)

The dataset includes:

- **Demographics:** Gender, dependents and age-related information.
- **Account information:** Tenure, contract type, payment method and billing.
- **Services:** Internet, phone, technical support, online security and streaming services.
- **Retention information:** Churn status and, depending on the dataset version, satisfaction scores, churn reasons and customer lifetime value.

The dataset is fictional and intended for educational and analytical purposes.

## 4. Data Science Workflow

The analytical workflow consists of the following stages:

1. Data understanding and exploration
2. Data cleaning and preprocessing
3. Exploratory data analysis (EDA)
4. Feature engineering and selection
5. Training, validation and testing
6. Machine-learning model development
7. Model evaluation and comparison
8. Churn probability prediction
9. Model explainability
10. Customer retention decision support

## 5. Machine-Learning Models

The project considers several classification algorithms:

- Logistic Regression
- Decision Tree
- Random Forest
- XGBoost
- Neural Networks

Logistic Regression provides an interpretable baseline for comparison with more complex models.

### Model Evaluation

Model performance is assessed using appropriate classification metrics, including:

- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC
- Confusion matrix

The final model should balance predictive performance, interpretability and practical business usefulness.

## 6. Customer Churn Prediction

The objective is to estimate the probability that an individual customer will leave the company.

For example:

| Customer | Predicted Churn Risk | Risk Category |
|---|---|---|
| Customer A | 81% | High |
| Customer B | 46% | Medium |
| Customer C | 12% | Low |

*Illustrative predictions only.*

These predictions can help businesses prioritise customers for retention initiatives.

### Model Explainability

Feature importance and explainability techniques such as SHAP can help identify factors associated with customer churn.

Examples of potential churn drivers include:

- Month-to-month contracts
- Short customer tenure
- High monthly charges
- Limited technical support
- Payment methods

The importance of these factors must be established through the actual model results.

## 7. Customer Retention Decision Support

Beyond predicting churn, the project aims to support practical customer retention decisions.

Potential applications include:

- Identifying high-risk customers.
- Segmenting customers by churn probability.
- Prioritising retention campaigns.
- Recommending appropriate retention offers.
- Incorporating customer lifetime value.
- Evaluating the potential value of retention interventions.

The longer-term objective is to extend predictive analytics into a retention decision-support system.

## 8. AWS Deployment and MLOps

A cloud-based deployment is planned to demonstrate how the predictive model could be integrated into a practical application.

### Proposed AWS Services

| Service | Purpose |
|---|---|
| Amazon S3 | Dataset and model storage |
| Amazon SageMaker | Model training and management |
| AWS Lambda | Serverless application logic |
| Amazon API Gateway | REST API access |
| Amazon ECR | Container image storage |
| Amazon CloudWatch | Logging and monitoring |
| AWS IAM | Access and permissions |

### Planned MLOps Features

- Reproducible data preprocessing
- Model versioning
- Docker containerisation
- Automated testing
- CI/CD pipelines
- Model deployment
- Logging and monitoring
- Model performance and drift monitoring

These components form part of the proposed production-oriented extension.

## 9. Technology Stack

| Category | Technologies |
|---|---|
| Programming | Python |
| Data Processing | Pandas, NumPy |
| Machine Learning | scikit-learn, XGBoost |
| Visualisation | Matplotlib, Power BI |
| Explainability | SHAP |
| Backend | Flask, REST APIs |
| Cloud | AWS, SageMaker, S3, Lambda |
| MLOps | Docker, GitHub Actions, CI/CD |

Some technologies are intended for later development stages.

## 10. Project Roadmap

- [ ] Data exploration and preprocessing
- [ ] Feature engineering
- [ ] Machine-learning model development
- [ ] Model evaluation and comparison
- [ ] Churn probability prediction
- [ ] Model explainability
- [ ] Customer risk segmentation
- [ ] Retention decision-support system
- [ ] REST API development
- [ ] Docker containerisation
- [ ] AWS deployment
- [ ] CI/CD and model monitoring
- [ ] Interactive analytics dashboard

## 11. Business Applications

Although the project focuses on telecommunications, the analytical approach can be adapted to customer-retention problems in:

- Banking and financial services
- Insurance
- Retail and e-commerce
- Telecommunications
- Subscription-based businesses

The central objective is to understand customer churn risk and use predictive insights to support better retention decisions.

## Disclaimer

The IBM Telco Customer Churn dataset describes a fictional telecommunications company. This is an independent data science portfolio project and is not affiliated with or endorsed by IBM.
