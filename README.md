# EyeGuard AI – Glaucoma Detection Using Machine Learning

## Project Overview

EyeGuard AI is a web-based machine learning application designed to classify eye conditions using structured clinical measurements. The system uses a trained Random Forest classification model to predict whether a patient's input measurements belong to one of three categories:

- Healthy
- Glaucoma
- Glaucoma Suspect

The application provides an interactive interface where users can enter clinical measurements, receive predictions, view confidence scores, and identify low-confidence predictions through a warning mechanism.

The project integrates Machine Learning with Full Stack Development to demonstrate how clinical data can be processed and used for automated classification.

## Objectives

- Develop a machine learning model for glaucoma-related classification.
- Use structured clinical measurements instead of relying only on eye images.
- Integrate the trained model with a Django backend.
- Develop an interactive frontend using React.js.
- Provide prediction confidence and class probabilities.
- Implement a Low-Confidence Prediction Warning feature.
- Support batch prediction for multiple patient records.

## Technologies Used

### Frontend
- React.js
- JavaScript
- HTML5
- CSS3
- Vite
- Fetch API

### Backend
- Python
- Django
- Django REST Framework
- REST API
- JSON

### Machine Learning
- Scikit-learn
- Random Forest Classifier
- Pandas
- NumPy
- Joblib

### Development Tools
- Visual Studio Code
- Git
- GitHub
- Python Virtual Environment

## Dataset

The project uses structured clinical measurements from the PAPILA dataset.

The dataset contains patient-related clinical information used to train and evaluate the machine learning model.

### Input Features

The model uses 11 clinical features:

| No. | Feature | Description |
|---|---|---|
| 1 | Age | Patient age |
| 2 | Gender | Gender code |
| 3 | Dioptre 1 | First refractive measurement |
| 4 | Dioptre 2 | Second refractive measurement |
| 5 | Astigmatism | Astigmatism measurement |
| 6 | Phakic/Pseudophakic | Lens status code |
| 7 | Pneumatic IOP | Intraocular pressure measured using pneumatic tonometry |
| 8 | Perkins IOP | Intraocular pressure measured using Perkins tonometry |
| 9 | Pachymetry | Corneal thickness |
| 10 | Axial Length | Length of the eye |
| 11 | VF_MD | Visual field mean deviation |

### Target Classes

The model classifies the input into three categories:

- Class 0 – Healthy
- Class 1 – Glaucoma
- Class 2 – Glaucoma Suspect

## Machine Learning Algorithm

### Random Forest Classifier

EyeGuard AI uses the Random Forest algorithm for classification.

Random Forest is an ensemble machine learning algorithm that combines multiple decision trees to generate a final prediction.

The model processes the clinical measurements and generates:
- Predicted disease class.
- Prediction confidence.
- Probability for each of the three classes.

The trained model is saved as a Joblib file and loaded by the Django backend during prediction.

## Main Features

### 1. Clinical Measurement Input

Users can enter 11 clinical measurements through the React frontend.

### 2. Glaucoma Classification

The trained Random Forest model classifies the input into Healthy, Glaucoma, or Glaucoma Suspect.

### 3. Prediction Confidence

The application displays the model's confidence percentage and class probabilities.

### 4. Low-Confidence Prediction Warning

This additional feature allows users to select a minimum confidence threshold.

If the model's prediction confidence is below the selected threshold, the application displays a low-confidence warning recommending further review.

The threshold controls the warning only. It does not change the predicted disease class.

### 5. Batch Prediction

Users can submit multiple patient measurement records and receive predictions for multiple records.

### 6. CSV Input

The application supports uploading clinical measurement records in CSV format for batch processing.

### 7. Prediction Result Display

The frontend displays the predicted class, confidence percentage, class probabilities, and warning status.

## System Architecture

EyeGuard AI follows a full-stack architecture.

1. **Presentation Layer:** React.js provides the user interface.
2. **Communication Layer:** Fetch API sends HTTP requests in JSON format.
3. **Backend Layer:** Django REST Framework receives and processes API requests.
4. **Machine Learning Layer:** The trained Random Forest model generates predictions.
5. **Response Layer:** Django returns prediction results to React in JSON format.

### Application Workflow

User Input → React Frontend → Fetch API → Django REST API → Random Forest Model → JSON Response → Prediction Display

## API Endpoints

The application provides two prediction endpoints:

| Endpoint | Method | Description |
|---|---|---|
| `/api/predict/` | POST | Performs single-record prediction |
| `/api/predict/batch/` | POST | Performs batch prediction |

The frontend communicates with the backend through HTTP requests, and JSON is used for data exchange.

## Project Structure

```text
EyeGuardAI/
│
├── frontend/
│   ├── src/
│   │   ├── App.jsx
│   │   ├── App.css
│   │   └── main.jsx
│   ├── package.json
│   └── index.html
│
├── backend/
│   ├── manage.py
│   ├── config/
│   ├── predictor/
│   └── ml_models/
│       └── eyeguard_model.joblib
│
├── ml/
│   └── Machine Learning scripts
│
├── dataset/
│   └── Clinical datasets
│
└── README.md
```

## Installation and Execution

### Prerequisites

- Python
- Node.js and npm
- Git
- Visual Studio Code

### Step 1: Clone the Repository

```bash
git clone https://github.com/sahasra1812/EyeGuardAI.git
```

```bash
cd EyeGuardAI
```

### Step 2: Set Up the Python Environment

```bash
python -m venv .venv
```

Activate the environment on Windows:

```bash
.venv\Scripts\activate
```

Install backend dependencies:

```bash
pip install -r backend/requirements.txt
```

### Step 3: Run Django Backend

```bash
python backend/manage.py migrate
```

```bash
python backend/manage.py runserver
```

Backend address:

```text
http://127.0.0.1:8000/
```

### Step 4: Run React Frontend

Open another terminal:

```bash
cd frontend
```

Install dependencies:

```bash
npm install
```

Start the frontend:

```bash
npm run dev
```

Frontend address:

```text
http://localhost:5173/
```

## Expected Output

The application provides:
- Patient clinical measurement input.
- Healthy, Glaucoma, and Glaucoma Suspect classification.
- Prediction confidence percentage.
- Class probability distribution.
- Customizable minimum confidence threshold.
- Low-confidence warning.
- Batch prediction results.

## Future Enhancements

- Improve model performance using larger and more diverse clinical datasets.
- Explore additional machine learning algorithms.
- Improve classification of the Glaucoma Suspect category.
- Add more detailed prediction reports.
- Improve model validation and probability calibration.
- Deploy the application for wider research and educational use.

## Disclaimer

EyeGuard AI is an academic and research prototype developed for educational purposes. Its predictions are based on a machine learning model trained using clinical measurements. Model confidence does not guarantee prediction correctness.

This application is not a medical diagnostic tool and must not replace professional examination or advice from a qualified ophthalmologist.

## Project Information

**Project Name:** EyeGuard AI  
**Domain:** Machine Learning and Full Stack Development  
**Application Type:** Web-Based Clinical Data Classification System  
**Algorithm:** Random Forest Classifier  
**Frontend:** React.js  
**Backend:** Django REST Framework  
**Data Exchange:** REST API and JSON

---

Developed as an academic project to explore the integration of Machine Learning and Full Stack Development in healthcare-related applications.
