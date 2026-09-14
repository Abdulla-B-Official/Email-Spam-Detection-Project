# Email Spam Detection System

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge)
![Scikit-Learn](https://img.shields.io/badge/Scikit_Learn-TF--IDF_%26_Na%C3%AFve_Bayes-F7931E?style=for-the-badge)
![Pandas](https://img.shields.io/badge/Pandas-Data_Processing-150458?style=for-the-badge)
![GitHub](https://img.shields.io/badge/GitHub-Repository-181717?style=for-the-badge)

<p align="center">
  <b>An end-to-end Natural Language Processing (NLP) binary text classification pipeline designed to ingest raw email content, execute TF-IDF vectorization, mitigate class imbalance, evaluate classification metrics, and deliver real-time spam predictions.</b>
</p>

---

<p align="center">
  <img src="https://img.shields.io/badge/Algorithm-TF--IDF_Vectorization-blue?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Model-Multinomial_NB_%2F_Logistic_Regression-green?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Handling-Class_Weight_Balanced-orange?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Metrics-Precision_%26_Recall-red?style=for-the-badge" />
</p>

---

## Overview

**Email Spam Detection System** is an NLP-driven binary classification pipeline built to analyze unstructured email text and automatically categorize messages into **Spam** or **Ham (Legitimate)**.

Instead of relying on simple keyword blacklists, the system establishes a robust machine learning workflow incorporating:

* **Text Preprocessing & Normalization:** Lowercasing, noise removal, tokenization, stop-word filtering, and stem/lemma normalization.
* **Feature Extraction:** Sublinear TF-IDF N-gram Vectorization to transform raw text into sparse numerical matrices.
* **Class Imbalance Mitigation:** Optimized probability thresholds and class-weight balancing to reduce false positives.
* **Evaluation & Diagnostics:** Performance evaluation prioritizing **Precision** to ensure legitimate emails are never misclassified as spam.

The pipeline transforms raw textual bodies into high-dimensional numerical feature vectors using TF-IDF and outputs instant spam likelihood predictions via modular execution scripts.

---

### Application Features

* **Modular End-to-End Architecture:** Clean separation across data loading, preprocessing, feature extraction, model training, evaluation, and inference modules.
* **High-Precision Filtering:** Fine-tuned to maximize Precision, minimizing the risk of legitimate emails (Ham) being marked as Spam.
* **Preserved Context Signals:** Text cleaning routines optimized to preserve structural flags (e.g., currency symbols, urgent phrasing, specific punctuation).
* **Transparent Evaluation Matrix:** Reports precision, recall, F1-score, ROC-AUC curves, and structured confusion matrices.
* **Production-Ready Artifacts:** Automatically serializes trained models and vectorizer instances (`.pkl`) for instant real-time inference workflows.

---

## Project Objective

The primary objective is to build a scalable, high-precision spam filtering pipeline that can:

* Clean and structure high-dimensional unstructured email text from raw CSV datasets.
* Resolve data quality issues such as empty strings, duplicate messages, and uninformative noise words.
* Transform message text into sparse numerical representations using `TfidfVectorizer`.
* Handle real-world class imbalance where legitimate emails outnumber spam messages.
* Benchmark model performance using standard metrics (Precision, Recall, F1-Score, Confusion Matrix).
* Package model artifacts cleanly for version control and modular deployment.

---

## Problem Statement

Spam emails flood user inboxes daily, presenting security risks such as phishing attacks and malware distribution. Simple rule-based filters fail to adapt to modern adversarial spam phrasing.

Standard machine learning baselines often suffer from:

* **High False Positive Rates:** Marking crucial legitimate emails as spam due to aggressive keyword matching.
* **Overfitting:** Failing to generalize when spam senders intentionally misspell words or vary phrasing.
* **Lack of Modularity:** Monolithic script structures that lack entry points for automated training or API integration.

### Proposed Solution

This project introduces a robust NLP classification pipeline executing:

$$\text{Raw Email Text} \longrightarrow \text{Text Preprocessing} \longrightarrow \text{TF-IDF Matrix} \longrightarrow \text{ML Classification} \longrightarrow \text{Spam Prediction}$$

For every message processed, the system produces:

```text
Cleaned Email Text
Predicted Label (Spam / Ham)
Prediction Confidence / Decision Probability
Evaluation Metrics & Confusion Matrix Output
