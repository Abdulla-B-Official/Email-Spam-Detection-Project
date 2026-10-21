```markdown
![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/Scikit_Learn-Machine_Learning-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)
![NLP](https://img.shields.io/badge/NLP-Text_Classification-orange?style=for-the-badge)
![FastAPI](https://img.shields.io/badge/FastAPI-Web_API-005571?style=for-the-badge&logo=fastapi&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-Containerized-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Pytest](https://img.shields.io/badge/Pytest-Testing-0A9EDC?style=for-the-badge&logo=pytest&logoColor=white)

<p align="center">
  <b>A production-style machine learning web application designed to classify messages as spam or legitimate (ham) using natural language processing text vectorisation and supervised classification algorithms over a high-performance FastAPI backend with a responsive Bootstrap UI.</b>
</p>

---

## Overview

Email Spam Detection System is an advanced machine learning application designed to automatically filter and detect unwanted spam messages from legitimate email or SMS text inputs.

The system incorporates supervised classification models trained on text corpora with rigorous text preprocessing and feature extraction:
- **TF-IDF Vectorisation:** Converts raw text strings into numerical feature matrices based on term frequency-inverse document frequency weighting.
- **Supervised Classifiers:** Implements robust classification algorithms (such as Naive Bayes, Logistic Regression, or Support Vector Machines) optimized for binary text classification.

Instead of retraining on the fly, the application loads pre-trained model artifacts and fitted vectorisers, ensuring instantaneous response times and faithful reproduction of text cleaning, normalisation, and inference logic.

---

## Features

- **Spam Classification:** Input any email or message text to determine whether it is spam or ham with associated confidence scoring.
- **Dynamic Model Verification:** Inspect loaded model artifacts and classification performance metrics via API endpoints.
- **Interactive REST API:** Automatic OpenAPI documentation and interactive testing via `/docs` (Swagger UI).
- **Modern Bootstrap UI:** Clean, responsive single-page interface for seamless user interaction.
- **Containerised Deployment:** Fully configured with Docker, Render, and Railway deployment blueprints.
- **Robust Test Suite:** Comprehensive `pytest` coverage running with real-artifact readiness and mocked test support.

---

## How It Works

```text
                  USER INPUT
                      │
                      ▼
         ┌─────────────────────────┐
         │  Web UI / FastAPI REST  │
         └────────────┬────────────┘
                      │
                      ▼
         ┌─────────────────────────┐
         │    Text Normalisation   │
         │   & TF-IDF Vectoriser   │
         └────────────┬────────────┘
                      │
                      ▼
         ┌─────────────────────────┐
         │   Trained Classifier    │
         │   (Spam vs Ham Logic)   │
         └────────────┬────────────┘
                      │
                      ▼
         ┌─────────────────────────┐
         │   JSON API Response     │
         └─────────────────────────┘

```

---

## Project Architecture & Layout

```text
email_spam_detector/
├── app/
│   ├── main.py              # FastAPI application entrypoint
│   ├── routes/              # API route handlers (/predict, /health, /models)
│   ├── services/            # Predictor logic and text processing pipelines
│   ├── models/              # Model loaders, vectoriser loader, and Pydantic schemas
│   ├── utils/               # Text cleaning and normalisation utilities
│   └── config/              # Application settings and environment variables
├── static/                  # Frontend assets (CSS stylesheets, client-side JS)
├── templates/               # HTML single-page interface (index.html)
├── notebooks/               # Training scripts and artifact export utilities
├── saved_models/            # Directory for trained model files, vectoriser, and config.json
├── data/                    # Corpus data files (e.g., spam.csv dataset)
├── tests/                   # Pytest automated test suite
├── requirements.txt         # Pinned python dependencies
├── Dockerfile               # Container build instructions
├── Procfile                 # Railway process configuration
├── render.yaml              # Render cloud deployment blueprint
└── README.md                # Project documentation

```

---

## Installation & Setup

### 1. Clone the Repository

```bash
git clone [https://github.com/Abdulla-B-Official/Email-Spam-Detection-Project.git](https://github.com/Abdulla-B-Official/Email-Spam-Detection-Project.git)
cd Email-Spam-Detection-Project

```

### 2. Create and Activate Virtual Environment

```bash
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate

```

### 3. Install Dependencies

```bash
pip install -r requirements.txt

```

---

## Running Locally

Start the development server using Uvicorn:

```bash
uvicorn app.main:app --reload

```

* **Web Interface:** [http://localhost:8000/](http://localhost:8000/)
* **Interactive API Docs:** [http://localhost:8000/docs](http://localhost:8000/docs)
* **Health Check:** [http://localhost:8000/health](http://localhost:8000/health)

---

## API Endpoints & Usage

### `POST /predict`

Classify an input message as spam or ham.

**Request Body:**

```json
{
  "text": "Congratulations! You have won a free lottery ticket worth $1000. Click here to claim."
}

```

**Response:**

```json
{
  "input": "Congratulations! You have won a free lottery ticket worth $1000. Click here to claim.",
  "prediction": "spam",
  "confidence": 0.96
}

```

### `GET /health`

Returns system status and model readiness.

```json
{
  "status": "ok",
  "model_loaded": true
}

```

**cURL Example:**

```bash
curl -X POST http://localhost:8000/predict \
  -H "Content-Type: application/json" \
  -d '{"text":"Hey, are we still meeting for lunch today?"}'

```

---

## Model Training & Artifacts

To train the model from scratch using your own corpus:

```bash
python notebooks/train_model.py --data data/spam.csv --out saved_models

```

### Artifact Specifications

* **Model Checkpoint:** Saved as `spam_classifier.pkl` (or corresponding model format).
* **Vectoriser:** Serialised using `pickle` as `vectoriser.pkl`, preserving vocabulary features.
* **Configuration:** `config.json` stores pipeline parameters to guarantee preprocessing parity.

---

## Testing

Run the automated test suite using `pytest`:

```bash
pytest

```

The tests validate text normalisation, feature extraction, classifier prediction logic, and FastAPI endpoint validation schemas.

---

## Deployment

### Docker Containerisation

```bash
docker build -t email-spam-detector .
docker run -p 8000:8000 email-spam-detector

```

*(The container automatically detects the `$PORT` environment variable).*

### Render & Railway

* **Render:** Connect your GitHub repository and configure using `render.yaml`.
* **Railway:** Deploy directly using the provided `Procfile`:
```text
web: uvicorn app.main:app --host 0.0.0.0 --port $PORT

```



---

## Technology Stack

| Technology | Purpose |
| --- | --- |
| **Python** | Core Programming Language |
| **FastAPI** | High-Performance REST API & OpenAPI Docs |
| **Scikit-Learn** | Machine Learning Algorithms & TF-IDF Vectorisation |
| **Uvicorn** | ASGI Web Server |
| **Bootstrap 5** | Responsive Frontend UI Framework |
| **Docker** | Containerisation & Environment Isolation |
| **Pytest** | Automated Testing Framework |
| **Git / GitHub** | Version Control & Collaboration |

---

## Project Outcomes

* Successfully trained and evaluated machine learning classifiers for text spam filtering.
* Developed a robust inference pipeline with exact text preprocessing parity.
* Built an intuitive, responsive single-page web interface.
* Exposed clean, validated endpoints via FastAPI with automatic documentation.
* Successfully packaged and containerised the application for cloud deployment.

---

### Filter Smarter. Secure Communications. Automate Spam Detection.

If you found this project useful, consider giving the repository a star!

---
