# GPIL Project 01: Grafana + MongoDB Monitoring Setup

This project documents the full process of setting up MongoDB data monitoring with Prometheus and Grafana, as part of the GPIL internship.

---

## 📅 Date: June 19, 2025  
## 🧑‍💻 Intern: Akshat Palia

---

## 🗂️ Project Objective

Visualize power plant machine data from a large MongoDB dump (~50 GB) using Prometheus and Grafana. Collections include health data, historical values, and FFT analysis for various plant components.

---

## 📌 Steps Covered

### ✅ 1. Received MongoDB `.bson` dump (~50GB)
- Collections like `LiveData`, `HistoricalData`, `HealthData`, `AlarmLog`, `RUL`, `FFT_Analysis`, etc. under `OPCUA` database.

### ✅ 2. Restored MongoDB Dump
```bash
mongorestore --dir=/Users/akshatpalia/dump
### # 📊 GPIL Project 01: Grafana + MongoDB Monitoring Setup

This project documents the full process of setting up MongoDB data monitoring with Prometheus and Grafana, as part of my internship at **Godavari Power and Ispat Limited (GPIL)**.

---

## 📅 Date: June 19, 2025  
## 🧑‍💻 Intern: Akshat Palia

---

## 🎯 Project Objective

Visualize power plant machine sensor data from a large MongoDB dump (~50 GB) using **Prometheus** and **Grafana**.  
The database includes metrics like health data, live sensor values, FFT analysis, RUL, etc., stored under the `OPCUA` database.

---

## 🧩 Database Collections (MongoDB → OPCUA)

- `LiveData`
- `HistoricalData`
- `Hourly`
- `AlarmLog`
- `KN_HealthData`, `KN_HealthSummary`, `KN_RUL`
- `OPE_HealthData`, `OPE_HealthSummary`, `OPE_RUL`, `OPE_FFT_Analysis`
- `PN_HealthData`, `PN_RUL`, `PN_FFT_Analysis`
- `Motor_Analysis`, `Motor_Analysis_prev`
- `MaintenanceDevice`
- `UserMast`
- `NewHistoricalData`, `NewHistoricalData_06_12_06_13`, `NewHistoricalData_06_13_06_15`

---

## ✅ Step-by-Step Progress

### 1️⃣ Dump Restoration to MongoDB

```bash
mongorestore --dir=/Users/akshatpalia/Downloads/dump
### ✅ 3. Explored MongoDB Data
use OPCUA
show collections
db.LiveData.findOne()

✅ 4. Setup MongoDB Exporter
Downloaded and extracted: mongodb_exporter-0.40.0.darwin-arm64
Ran exporter:
./mongodb_exporter --mongodb.uri="mongodb://localhost:27017"
Saw only basic metrics like mongodb_up
✅ 5. Setup Prometheus
Verified target at localhost:9090/targets
Only minimal data visible
✅ 6. Fixed Exporter to Enable Full Metrics
./mongodb_exporter \
  --mongodb.uri="mongodb://localhost:27017" \
  --collect-all \
  --discovering-mode
✅ This exposed deep metrics like:

mongodb_ss_connections
mongodb_mongod_metrics_document_total
mongodb_collection_count
✅ 7. Started All Services
brew services start mongodb/brew/mongodb-community@7.0
brew services start prometheus
brew services start grafana
✅ 8. Validated Data in Prometheus
Ran PromQL in Prometheus:
mongodb_ss_connections
Saw time series graph — confirmed working
✅ 9. Tested Query in Grafana
Connected Prometheus as data source
Ran first visual PromQL query inside Explore tab
📊 Next Steps

Create dashboards showing machine health vs time
Use HistoricalData and RUL for insights
Visualize real-time sensor values via LiveData

