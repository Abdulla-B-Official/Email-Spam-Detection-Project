# Email Spam Detection System

![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-Web_API-000000?style=for-the-badge&logo=flask&logoColor=white)
![NLP](https://img.shields.io/badge/NLP-CountVectorizer_%7C_Machine_Learning-yellow?style=for-the-badge)
![Scikit-Learn](https://img.shields.io/badge/Scikit_Learn-Classification-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)

<p align="center">
  <b>An end-to-end Natural Language Processing (NLP) machine learning pipeline and web application designed to clean, vectorize, train, evaluate, and classify incoming emails as spam or legitimate (ham) messages.</b>
</p>

---

## Overview

The **Email Spam Detection System** is an automated text classification engine built to ingest raw email datasets, perform data cleaning and tokenization, extract count-based features, and train predictive machine learning models to filter out unwanted spam messages.

The project features a modular backend structure located inside `src/`, containing dedicated subpackages for data processing, feature engineering, model training, evaluation, inference, quarantine management, and API routing:

* **Data Management (`src/data/`, `data/`):** Handles raw dataset ingestion (`email_spam_dataset.csv`), text preprocessing, and processed data persistence (`cleaned_emails.csv`).
* **Feature Extraction (`src/features/`):** Transforms clean text messages into numeric feature vectors using Count Vectorization (`vectorizer.py`).
* **Model Training & Evaluation (`src/models/`):** Orchestrates model building (`build_model.py`), training (`train.py`), performance evaluation (`evaluate.py`), and real-time prediction (`predict.py`).
* **Quarantine & API Routing (`src/quarantine/`, `src/api/`):** Manages flagged messages (`store.py`) and serves predictions via Flask web endpoints (`app.py`).

---

## Repository Structure

```text
Project-2 Email Spam Detection/
├── data/
│   ├── processed/
│   │   └── cleaned_emails.csv     # Preprocessed email text dataset
│   ├── raw/
│   │   └── email_spam_dataset.csv # Original raw email dataset
│   └── sample/                    # Sample test files
├── models/
│   ├── count_vectorizer.pkl       # Fitted Count Vectorizer binary
│   └── spam_model.pkl             # Trained spam classification model binary
├── notebooks/                     # Jupyter notebooks for EDA and prototyping
├── src/
│   ├── api/
│   │   └── app.py                 # Flask API server implementation
│   ├── data/                      # Data loading & cleaning pipeline
│   ├── features/
│   │   └── vectorizer.py          # Count Vectorizer feature extraction module
│   ├── models/
│   │   ├── build_model.py         # Classifier model architecture
│   │   ├── evaluate.py            # Evaluation metrics calculation
│   │   ├── predict.py             # Single & batch prediction logic
│   │   └── train.py               # Model training script
│   ├── quarantine/
│   │   └── store.py               # Flagged/quarantined email management
│   └── utils/                     # Utility helper functions
├── .gitignore                     # Git exclusion rules
├── Email_Spam_Detection_Guide.docx # Detailed project documentation guide
├── main.py                        # Core application execution entry point
├── README.md                      # Project documentation
└── requirements.txt               # Python dependencies

```

---

## System Architecture

$$\text{Raw Email} \longrightarrow \text{Data Processing (`src/data/`)} \longrightarrow \text{Count Vectorization (`src/features/`)} \longrightarrow \text{Classification Model (`src/models/`)} \longrightarrow \text{Flask API (`src/api/app.py`)}$$

1. **Ingestion & Cleaning:** Raw email messages are loaded and normalized.
2. **Feature Vectorization:** Processed text is transformed into numerical token counts using `count_vectorizer.pkl`.
3. **Classification:** The trained model (`spam_model.pkl`) evaluates the vector to classify the email as Spam or Ham.
4. **API Serving:** Results are delivered via the Flask backend interface and managed through quarantine storage rules.

---

## Installation & Setup

### 1. Clone the Repository

```bash
git clone [https://github.com/Abdulla-B-Official/Email-Spam-Detection-System.git](https://github.com/Abdulla-B-Official/Email-Spam-Detection-System.git)
cd "Project-2 Email Spam Detection"

```

### 2. Set Up Virtual Environment

```bash
python -m venv .venv
# Activate on Windows PowerShell:
.venv\Scripts\Activate.ps1
# Activate on Linux/macOS:
source .venv/bin/activate

```

### 3. Install Dependencies

```bash
pip install -r requirements.txt

```

### 4. Run the Application

```bash
python main.py

```

*(Or launch the API service directly via `python src/api/app.py`)*

```

```
