# Fake-drug-checker

Fake Drug Checker and NAFDAC Registration Checker — a capstone project to help users verify whether a medication is genuine by checking features, packaging, or registration details and validating NAFDAC registration status.

---

## Table of Contents

- [Project Overview](#project-overview)
- [Features](#features)
- [Motivation](#motivation)
- [Architecture & Tech Stack](#architecture--tech-stack)
- [Data Sources](#data-sources)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Environment / Configuration](#environment--configuration)
  - [Running Locally](#running-locally)
- [Usage](#usage)
- [Model / Detection Approach](#model--detection-approach)
- [Evaluation](#evaluation)
- [Testing](#testing)
- [Deployment](#deployment)
- [Roadmap / Future Work](#roadmap--future-work)
- [Contributing](#contributing)
- [License](#license)
- [Acknowledgements](#acknowledgements)
- [Contact](#contact)

---

## Project Overview

Fake-drug-checker is a tool designed to reduce the risk of counterfeit medication by offering two complementary checks:

1. Visual / metadata-based fake-drug detection (e.g., packaging, label text, batch/expiry anomalies).
2. NAFDAC registration lookup to verify if the medicine (by brand or product code) is registered with NAFDAC.

The tool can be extended into a mobile/web app, or run as a CLI/API for pharmacists, healthcare workers, and consumers.

---

## Features

- Submit product name, batch number, or upload photos of the packaging for a quick authenticity check.
- Check NAFDAC registration status using the official NAFDAC registry (or cached dataset).
- Provide user-friendly results with confidence levels and recommended next steps (e.g., report to authorities).
- Audit trail and local logs for traceability (optional).
- Administrative interface to update product database, blacklist, or whitelists.

---

## Motivation

Counterfeit drugs are a serious public health risk. This capstone addresses a real-world need: giving community members and health professionals a fast, accessible way to check drug authenticity and registration status in Nigeria.

---

## Architecture & Tech Stack

Suggested / example stack (adjust to your implementation):

- Backend: Python (Flask / FastAPI) or Node.js (Express)
- Model & ML: TensorFlow / PyTorch / scikit-learn (or simple heuristics if not using ML)
- Database: PostgreSQL / SQLite (for small demos)
- Frontend: React / Vue / plain HTML+CSS (optional)
- Deployment: Docker, Heroku, or any cloud provider (AWS, GCP)
- Optional: NAFDAC data fetcher / scraper or API connector

(If you tell me which stack you used, I can tailor these sections and commands precisely.)

---

## Data Sources

- NAFDAC public registry (link or method used to obtain/verify registration)
- Image dataset or packaging examples used for training/validation (if applicable)
- Any third-party APIs (list them here)

Make sure to document data licensing and permissions for scraping or using registry data.

---

## Getting Started

### Prerequisites

- Git
- Python 3.8+ (or Node 14+) depending on your stack
- pip / npm
- Docker (optional, recommended for reproducible runs)

### Installation (example for a Python backend)

1. Clone the repo:
   git clone https://github.com/YodahJ/Fake-drug-checker.git
   cd Fake-drug-checker

2. Create a virtual environment and install:
   python -m venv venv
   source venv/bin/activate  # Windows: venv\Scripts\activate
   pip install -r requirements.txt

3. Prepare database and environment variables (see `.env.example`).

### Environment / Configuration

Create a `.env` file with values like:
- DATABASE_URL=sqlite:///data/db.sqlite (or your DB connection)
- NAFDAC_DATA_PATH=./data/nafdac.csv
- SECRET_KEY=your_secret_here
- PORT=8000

### Running Locally

Start the backend:
- For Python / FastAPI:
  uvicorn app.main:app --reload --host 0.0.0.0 --port 8000

- For Node / Express:
  npm install
  npm run dev

Start the frontend (if present):
  cd frontend
  npm install
  npm start

---

## Usage

- Web: Visit http://localhost:8000 (adjust port as configured)
- API endpoints (example):
  - POST /api/check-image — upload packaging image for analysis
  - GET /api/nafdac?product=ProductName — check registration status
  - POST /api/report — report suspected fake product

Example curl (NAFDAC check):
  curl "http://localhost:8000/api/nafdac?product=Paracetamol"

Return format:
- { "registered": true, "nafdac_number": "NN-12345", "confidence": 0.92 }

---

## Model / Detection Approach

Describe the approach used in your project (update as appropriate):

- Preprocessing: Resize images, normalize, OCR for text extraction.
- Model: CNN classifier trained on packaging images (or rule-based comparisons).
- OCR: Tesseract or cloud OCR to extract printed batch/expiry/NAFDAC text.
- Decision logic: Combine OCR matches, visual similarities, and registration lookup to produce a final verdict.

Include training commands, important hyperparameters, and how to reproduce model training.

---

## Evaluation

Report metrics you used to evaluate the system:
- Accuracy, Precision, Recall, F1-score on the validation/test set
- Confusion matrix
- ROC/AUC (if applicable)

Add a short summary of results and any limitations discovered during testing.

---

## Testing

- Unit tests: Add tests under `tests/` and run with pytest / jest
- Sample test command:
  pytest --maxfail=1 --disable-warnings -q

- Include sample test data in `tests/fixtures/` or provide instructions to generate them.

---

## Deployment

Example Docker workflow:
1. Build image:
   docker build -t fake-drug-checker:latest .

2. Run:
   docker run -p 8000:8000 --env-file .env fake-drug-checker:latest

Provide additional deployment instructions for your chosen platform (Heroku/GCP/AWS).

---

## Roadmap / Future Work

- Mobile app for camera-based scanning
- Integration with official NAFDAC live API if available
- Improved model with larger dataset and stricter evaluation
- Admin dashboard for product database curation
- Real-time reporting to authorities

---

## Contributing

Contributions are welcome! Please follow these guidelines:
1. Fork the repository
2. Create a branch: git checkout -b feature/YourFeature
3. Commit your changes: git commit -m "Add feature"
4. Push to branch and open a Pull Request

Add an issue first for larger features to discuss design.

---

## License

Specify your license here (e.g., MIT). Example:
MIT License — see LICENSE file for details.

---

## Acknowledgements

- NAFDAC (for the registration data and resources)
- Any dataset or libraries you used (Tesseract, TensorFlow, PyTorch, scikit-learn)

---

## Contact

Project maintained by YodahJ.  
Email: (add your email)  
GitHub: https://github.com/YodahJ

---

Screenshots / Demo
- Add screenshots or a GIF here showing the app in action.
- Demo link: https://your-deployment.example.com (if deployed)
