# FitPulse: Health Anomaly Detection System

## Overview

FitPulse is a full-stack health analytics and anomaly detection platform built to analyze wearable fitness data such as heart rate, step count, sleep duration, and weight. The system detects abnormal health patterns using machine learning techniques, forecasts future trends using time-series models, and generates AI-based wellness insights through an interactive dashboard.

The application follows a modular client–server architecture:
- Streamlit is used for the frontend visualization and interaction
- FastAPI powers the backend for data processing, ML pipelines, forecasting, and report generation

---

## Key Features

- Upload and preprocess wearable health datasets  
- Feature engineering using rolling statistics  
- Anomaly detection using:  
  - Rule-based medical thresholds  
  - DBSCAN clustering  
- Time-series forecasting using Facebook Prophet  
- Interactive health trend visualization  
- AI-based personalized wellness recommendations  
- CSV and PDF report generation  
- Modular and scalable architecture  

---

## Dataset Information

**Dataset Source (Kaggle)**  
[Fitbit Dataset](https://www.kaggle.com/datasets/arashnic/fitbit)

### Files Used

- `minuteSleep_merged.csv` – Sleep duration and quality  
- `heartrate_seconds_merged.csv` – Continuous heart rate readings  
- `weightLogInfo_merged.csv` – Weight and BMI information  
- `dailyActivity_merged.csv` – Daily steps and activity data  

---

## Data Preparation Process

1. Individual preprocessing on all datasets:  
   - Timestamp normalization  
   - Data type conversions  
   - Missing value handling  

2. Dataset merging:  
   - Inner join between heart rate and steps → `clean_Dataset.csv`  
   - Left join with sleep and weight datasets → `final_Dataset.csv`  

3. `final_Dataset.csv` is used as the primary input for the system.

---

## System Workflow

1. Data upload and validation  
2. Data preprocessing and normalization  
3. Feature engineering using rolling mean and rolling standard deviation  
4. Anomaly detection:  
   - Rule-based threshold detection  
   - DBSCAN clustering  
5. Time-series forecasting using Prophet  
6. Visualization of trends and anomalies  
7. AI-based wellness advice generation  
8. CSV and PDF report generation  

---

## System Architecture

User
  ↓
Streamlit Dashboard
  ↓
FastAPI REST Backend
  ↓
Data Processing & Feature Engineering
  ↓
ML Forecasting & Anomaly Detection Engine
  ↓
Visualization & Report Generation

---

## Tech Stack

### Frontend
- Streamlit  
- Plotly  

### Backend
- FastAPI  
- Uvicorn  

### Data Science & Machine Learning
- Pandas  
- NumPy  
- Scikit-learn  
- Prophet  
- Matplotlib  

### AI / LLM
- OpenAI API  

### Utilities
- ReportLab  
- PyNgrok  

---

## Backend API Endpoints

| Endpoint | Description |
|----------|-------------|
| POST `/preprocess` | Data upload and preprocessing |
| POST `/module2` | Feature engineering |
| GET `/module3/prophet/{metric}` | Time-series forecasting |
| GET `/module3/summary` | Anomaly summary |
| GET `/module3/anomaly-with-recommendations` | AI-based health insights |
| GET `/module3/dbscan` | DBSCAN clustering |
| GET `/download-report` | Generate full PDF report |

---

## Dashboard Pages

1. **Data Upload & Preprocessing**  
   - Upload Fitbit dataset  
   - Data validation and cleaning  
   - Dataset overview and preview  

2. **Feature Engineering**  
   - Rolling averages and statistical features  
   - TSFRESH feature importance visualization  

3. **Health Trends**  
   - Prophet-based forecasting  
   - User-wise trend visualization  

4. **Anomaly Detection**  
   - Rule-based anomaly detection  
   - AI-generated recommendations  


5. **Distributions & Clustering**  
   - Metric distributions  
   - DBSCAN clustering visualization  


6. **User Health Dashboard**  
   - Raw vs rolling metric trends  
   - Health score computation  
   - Donut chart and anomaly table  


7. **Downloads**  
   - Full system PDF report  
   - Personalized user PDF report  

---

## How to Run the Project

### 1. Install Dependencies

```bash
pip install fastapi uvicorn pyngrok pandas numpy prophet scikit-learn matplotlib plotly streamlit requests openai reportlab
```

### 2. Start Backend Server

```bash
uvicorn backend:app --port 8003
```

Backend runs at:

```bash
http://localhost:8003
```

### 3. Start Frontend Application
```bash
streamlit run app.py
```

The Streamlit dashboard opens in the browser and communicates with the backend using REST APIs.


## Screenshots

The Screenshots/ directory contains screenshots captured during live execution of the application, illustrating the full workflow and user interface.

The screenshots demonstrate:

  - Data upload and preprocessing summary

  - Feature extraction and TSFRESH insights

  - Health trend visualization using Prophet

  - Anomaly detection summaries and severity classification

  - User-specific health dashboards

  - Health score donut charts and rolling averages

  - Metric distributions and DBSCAN clustering outputs

These images provide a visual walkthrough of the system’s functionality and analytics pipeline.

## Output Reports

The Output_Report/ directory contains system-generated PDF reports created by the application.

### Available Reports

Full Dashboard Report

  - Dataset overview

  - Sample records

  - Anomaly summary

  - Visual analytics

  - Health recommendations

Personalized User Dashboard Report

  - User-specific health metrics

  - Health score breakdown

  - Detected anomalies and recommendations

  - Recent activity summary

  - Trend and clustering visualizations

