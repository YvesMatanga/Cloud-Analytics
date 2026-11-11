# Multimodal Image Retrieval System

**Natural Language Processing | Computer Vision | Semantic Search | Machine Learning | Flask | React**

## 1. Project Overview

The **Multimodal Image Retrieval System** is an AI-powered application that enables users to search for and retrieve relevant images using natural-language descriptions.

The system integrates **computer vision and natural language processing (NLP)** to bridge the gap between visual information and textual queries. It uses automated image captioning, TF-IDF, Word2Vec semantic embeddings and cosine similarity to identify and rank images according to their relevance to a user's search query.

The solution comprises three main components:

- **Analytics:** Image sampling, automated caption generation, text preprocessing and semantic matching.
- **Back-end:** A Python Flask API that loads a serialised image retrieval model and processes search requests.
- **Front-end:** A React-based web interface that allows users to submit textual queries and explore matching images.

The project demonstrates the development of an end-to-end machine-learning application, from data preparation and feature engineering to model integration and interactive web-based retrieval.

## 2. Business Problem

Traditional image retrieval systems often rely on manually assigned keywords, filenames or metadata to identify relevant images. These approaches can be limited when images lack descriptive labels or when users express their search intentions through natural language.

For example, a user may search for:

> "A person walking along a beach during sunset."

A conventional keyword-based system may struggle to identify images that convey this meaning without containing the exact search terms.

The objective of this project is to develop a **semantic image retrieval system** capable of interpreting textual descriptions and identifying images with similar semantic content.

Potential applications include digital asset management, e-commerce product discovery, media libraries, content recommendation and intelligent image search.

## 3. Project Objectives

The project aims to:

1. Develop an automated pipeline for generating textual descriptions of images using pretrained vision-language models.
2. Transform image captions into numerical representations using NLP feature extraction techniques.
3. Implement semantic matching algorithms to measure similarity between user queries and image descriptions.
4. Rank and retrieve images according to their semantic relevance.
5. Integrate the retrieval model into a Flask back-end and React front-end.
6. Demonstrate an extensible architecture for intelligent, text-based image search.

## 4. System Architecture

The system follows a two-stage architecture consisting of an offline analytics pipeline and an online retrieval application.

### Offline Analytics Pipeline

```text
Image Dataset
     |
     v
Image Sampling (500 Images)
     |
     v
Automated Image Captioning
(Florence-2 / Alternative Captioning Model)
     |
     v
Text Cleaning and Normalisation
     |
     v
TF-IDF + Word2Vec Semantic Representations
     |
     v
Image-Caption Feature Index
     |
     v
Pickle Model Serialization
```

### Online Image Retrieval

```text
User
 |
 v
React Front-End
 |
 | Natural-Language Query
 v
Flask REST API
 |
 v
Text Preprocessing
 |
 v
Query Vectorisation
 |
 v
Cosine Similarity
 |
 v
Image Ranking
 |
 v
Top Matching Images
 |
 v
React Front-End
```

**Technical note:** This is a caption-mediated image retrieval approach. Images are first converted into textual descriptions, after which query matching operates in the text representation space rather than directly comparing image and text embeddings.

## 5. Dataset

The project uses a sample of **500 real images** extracted from the publicly available AI vs Human-Generated Images dataset on Kaggle.

**Dataset:** [AI vs Human-Generated Images](https://www.kaggle.com/datasets/alessandrasala79/ai-vs-human-generated-dataset/data?select=test_data_v2)

### Data Preparation

The preparation workflow includes:

- Random sampling of 500 real images from the source dataset.
- Automated generation of image captions.
- Cleaning and normalisation of textual descriptions.
- Association of image identifiers with their generated captions.
- Preparation of caption representations for semantic retrieval.

The resulting dataset provides the foundation for developing and testing text-to-image retrieval algorithms.

## 6. Machine Learning Methodology

### 6.1 Automated Image Captioning

The first stage converts visual information into natural-language descriptions using pretrained image captioning models.

The primary captioning model is **Florence-2**, a vision-language model capable of generating detailed textual descriptions of image content.

An alternative pretrained GPT-2-based captioning approach is also considered.

The generated captions serve as textual representations of the images and are subsequently processed using NLP techniques.

### 6.2 Text Preprocessing and Feature Engineering

The image captions are cleaned and transformed into numerical representations suitable for semantic similarity analysis.

The project combines two complementary techniques:

**TF-IDF (Term Frequency–Inverse Document Frequency)**

TF-IDF captures the relative importance of words within image descriptions by assigning greater weight to informative terms.

**Word2Vec Semantic Embeddings**

Word2Vec represents words in a continuous vector space where semantically related terms tend to have similar representations.

Combining TF-IDF weighting with semantic word embeddings provides a mechanism for constructing caption representations that account for both word importance and semantic relationships.

### 6.3 Semantic Similarity and Image Ranking

The system uses **cosine similarity** to measure the relevance of image captions to a user's textual query.

For a query vector \(\mathbf{q}\) and an image-caption vector \(\mathbf{d}_i\), cosine similarity is defined as:

\[
\operatorname{sim}(\mathbf{q},\mathbf{d}_i)
=
\frac{\mathbf{q}^{T}\mathbf{d}_i}
{\|\mathbf{q}\|\|\mathbf{d}_i\|}
\]

where:

- \(\mathbf{q}\) represents the vectorised user query.
- \(\mathbf{d}_i\) represents the vectorised caption associated with image \(i\).
- \(\operatorname{sim}(\mathbf{q},\mathbf{d}_i)\) measures semantic similarity.

Images are ranked in descending order of similarity, allowing the system to return the most relevant matches.

### 6.4 Model Serialization

The retrieval model and associated artefacts are serialised using Python's `pickle` library.

The model artefact is named:

`image_recommender_model_florence_long_word2vectfidf_files.pkl`

Serialisation enables the back-end application to load the prepared retrieval model without repeating the entire image-captioning and feature-engineering pipeline for every user query.

## 7. Repository Structure

```text
Multimodal Image Retrieval System/
|
|-- analytics/
|   |-- Image sampling and dataset preparation
|   |-- Image captioning notebooks
|   |-- Semantic matching and model development
|   |-- Retrieval model testing
|
|-- web-back-end/
|   |-- Python Flask application
|   |-- Model loading and inference
|   |-- Image retrieval API
|
|-- web-front-end/
|   |-- React application
|   |-- Search interface
|   |-- Image retrieval results
|
|-- README.md
```

### Main Components

| Component | Description |
|---|---|
| [Analytics](https://github.com/YvesMatanga/Cloud-Analytics/tree/main/Multimodal%20Image%20Retrieval%20System/analytics) | Data preparation, image captioning, semantic feature engineering and retrieval modelling |
| [Web Back-End](https://github.com/YvesMatanga/Cloud-Analytics/tree/main/Multimodal%20Image%20Retrieval%20System/web-back-end) | Flask-based API and model integration |
| [Web Front-End](https://github.com/YvesMatanga/Cloud-Analytics/tree/main/Multimodal%20Image%20Retrieval%20System/web-front-end) | React-based interface for natural-language image search |

## 8. Application Development

### Back-End: Flask

The Python Flask back-end serves as the interface between the trained retrieval model and the web application.

Its responsibilities include:

- Loading the serialised retrieval model.
- Receiving natural-language search queries.
- Processing and vectorising user queries.
- Computing semantic similarity scores.
- Ranking relevant images.
- Returning retrieval results to the front-end.

### Front-End: React

The React front-end provides an interactive interface for searching and exploring images.

It enables users to enter natural-language descriptions, submit retrieval requests and view images returned by the Flask API.

This separation between the analytics, back-end and front-end supports modular development and future application extensions.

## 9. Technology Stack

| Category | Technologies |
|---|---|
| Programming | Python, JavaScript |
| Machine Learning | Scikit-learn, Word2Vec, TF-IDF |
| Computer Vision | Florence-2 |
| Natural Language Processing | Text preprocessing, semantic embeddings |
| Similarity Matching | Cosine Similarity |
| Model Serialization | Pickle |
| Back-End | Flask |
| Front-End | React |
| Development | Jupyter Notebook, Google Colab |
| Data Source | Kaggle |

## 10. Model Evaluation

The retrieval model can be assessed by examining how effectively it identifies images corresponding to natural-language queries.

Relevant evaluation approaches include:

- **Qualitative retrieval assessment:** Inspecting the semantic relevance of returned images.
- **Precision@K:** Measuring the proportion of relevant images among the top-K retrieval results.
- **Recall@K:** Measuring the proportion of relevant images retrieved within the top-K results.
- **Mean Reciprocal Rank (MRR):** Evaluating the ranking position of the first relevant result.

Quantitative evaluation using these metrics requires a labelled set of queries and relevant images.

## 11. Potential Improvements

The current architecture provides a foundation for further development.

Potential extensions include:

- **CLIP-based retrieval:** Directly comparing image and text embeddings in a shared multimodal representation space.
- **Vector databases:** Integrating FAISS or another vector search solution to support larger image collections.
- **Improved ranking:** Evaluating alternative semantic embedding models and retrieval strategies.
- **Cloud deployment:** Deploying the application using AWS services.
- **Scalability:** Supporting larger image datasets and optimised similarity search.
- **Hybrid retrieval:** Combining keyword-based matching with semantic search.

These extensions could improve retrieval accuracy, scalability and production readiness.

## 12. Key Data Science Competencies Demonstrated

This project demonstrates practical competencies in:

- Natural language processing and semantic feature engineering.
- Computer vision and pretrained vision-language models.
- Text vectorisation using TF-IDF and Word2Vec.
- Similarity-based information retrieval and ranking.
- Model serialization and inference integration.
- REST API development using Flask.
- Front-end integration using React.
- End-to-end machine-learning application development.

## 13. Scientific References

[1] Mikolov, T., Chen, K., Corrado, G. and Dean, J. (2013). *Efficient Estimation of Word Representations in Vector Space.* [arXiv:1301.3781](https://arxiv.org/abs/1301.3781).

[2] Xiao, B. et al. (2024). *Florence-2: Advancing a Unified Representation for a Variety of Vision Tasks.* [arXiv:2311.06242](https://arxiv.org/abs/2311.06242).

## 14. Author

**Dr Yves Matanga**

Data Scientist | Machine Learning | Decision Analytics & Optimisation

GitHub: [YvesMatanga](https://github.com/YvesMatanga)

Repository: [Cloud Analytics](https://github.com/YvesMatanga/Cloud-Analytics)

---

*This project forms part of the Cloud Analytics portfolio, demonstrating the application of machine learning, natural language processing and software engineering to intelligent information retrieval.*
