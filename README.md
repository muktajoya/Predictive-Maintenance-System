# Predictive Maintenance System – Industry 4.0 Architecture
## Developed by:   Mukta Ghosh  (Data Engineer / ML Engineer)

## Industry Problem

In modern manufacturing environments, unexpected machine failures can lead to:

  - Unplanned downtime and production loss
  - High maintenance costs due to reactive repairs
  - Lack of early warning systems for equipment degradation
  - Difficulty in monitoring large-scale industrial assets in real time

Traditional maintenance strategies (reactive or scheduled maintenance) are often inefficient and costly in Industry 4.0 environments.

## This system addresses these challenges by:
The goal of this system is to support data-driven maintenance decisions in Industry 4.0 environments and reduce unexpected equipment failures through predictive analytics.

  - Continuously monitoring IoT sensor data
  - Detecting anomalies before failure occurs
  - Assigning a real-time risk score to each machine
  - Classifying machines into HEALTHY / WARNING / CRITICAL states
  - Providing a dashboard for maintenance decision supports

This enables a shift from reactive maintenance → predictive maintenance, reducing downtime and improving operational efficiency. The system enables real-time predictive maintenance, allowing teams to monitor machine health and take timely action before failures occur.

##  Why choosed kaggle dataset is suitable for industrial ML
This dataset sourced from Kaggle is highly representative of real-world industrial IoT systems because it contains:

- Time-series sensor data (timestamp-based behavior)
- Multiple machine entities (machine_id)
- Multi-sensor inputs (temperature, vibration, etc.)
- Failure / anomaly labels for supervised learning
- Realistic operational variability

This makes it suitable for building an end-to-end predictive maintenance pipeline similar to industrial SCADA systems used in Siemens / Bosch environments.

https://www.kaggle.com/datasets/ziya07/smart-manufacturing-iot-cloud-monitoring-dataset?resource=download&select=smart_manufacturing_data.csv
---

# End-to-End Machine Learning Pipeline

## STEP A — Data Understanding
- Missing value analysis
- Distribution analysis of sensor signals
- Machine-wise grouping
- Baseline behavior profiling


## STEP B — Feature Engineering (Industrial IoT Signals)

This layer transforms raw sensor data into meaningful intelligence:

### Baseline Features
- Mean temperature per machine
- Standard deviation of vibration

### Instant Anomaly Signals
- Z-score temperature deviation
- Z-score vibration spikes

### Time-Series Features
- Lag features (previous sensor states)
- Rolling mean
- Rolling standard deviation
- Delta changes over time


## STEP C — Anomaly Detection
Initial approach:
- Statistical method (Z-score thresholding)

Advanced approach:
- Machine Learning model (Random Forest Classifier)
- Target: anomaly_flag


## STEP D — Prediction Layer
Model outputs:
- anomaly prediction (0/1)
- anomaly probability score


## STEP E — Machine-Level Aggregation
Aggregates predictions at machine level:

- Average anomaly probability
- Anomaly rate per machine
- Risk score computation


## STEP F — Health Scoring & Alert System
Machines are classified into:

- 🟢 HEALTHY
- 🟠 WARNING
- 🔴 CRITICAL

Based on:
- percentile ranking
- risk score distribution


## STEP G — Business Output Layer

Final outputs for decision-making:

- Machine health monitoring dashboard
- Real-time alert system
- Ranking of most critical machines
- Maintenance prioritization insights

---

##  Final Dashboard (Power BI)

- Fleet health overview
- Risk distribution analysis
- Alert monitoring panel
- Industrial SCADA-style UI


# System Architecture

IoT Sensor Data 
↓  
Data Ingestion (Spark / Databricks)  
↓  
Data Preprocessing  
↓  
Feature Engineering (Time-series + statistical features)  
↓  
ML Model Training (Random Forest)  
↓  
Prediction Layer  
↓  
Machine-level Aggregation  
↓  
Risk Scoring Engine  
↓  
Health Classification (HEALTHY / WARNING / CRITICAL)  
↓  
Dashboard & Alert System  

# Future Upgrade of this project
The current system focuses on machine health monitoring, anomaly detection, and risk scoring.

In future iterations, this project can be extended from **real-time predictive maintenance** to **future failure forecasting (Prognostics / RUL prediction)**.

###  Planned Improvements:

• Remaining Useful Life (RUL) prediction for machines  
• Time-to-failure forecasting using time-series models (LSTM / GRU)  
• Prediction of risk score trends over time (risk forecasting)  
• Early warning system before machine reaches CRITICAL state  
• Transition from classification → regression-based predictive maintenance  

### 🧠 Expected Outcome:

Instead of only identifying:
- HEALTHY / WARNING / CRITICAL

The system will be able to predict:

- Estimated time until failure  
- Degradation trend of machine health  
- Future risk trajectory  

### 🏭 Impact:

This upgrade moves the system from:
**Reactive + Predictive Maintenance → Proactive + Forecasting-based Maintenance**

aligning with advanced Industry 4.0 and smart manufacturing systems.

