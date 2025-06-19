

# GPIL Project 01 – MongoDB + Grafana Data Visualization

This project is part of my internship at **Godavari Power and Ispat Limited (GPIL)**. The goal is to visualize industrial machine data using **Grafana**, with data stored and queried from **MongoDB**.

---

## 📌 Project Summary

- **Data Source**: MongoDB dump (~50GB+), includes sensor data, health logs, and machine metrics.
- **Visualization Tool**: Grafana
- **Monitoring Layer**: Prometheus + MongoDB Exporter
- **Tech Stack**: MongoDB, Grafana, Prometheus, Linux/MacOS Terminal

---

## 📁 Key MongoDB Collections

Database: `OPCUA`

- `LiveData` – Real-time machine readings
- `HistoricalData`, `NewHistoricalData_*` – Time-series logs
- `KN_HealthData`, `OPE_HealthData`, `PN_HealthData` – Health metrics by area
- `*_FFT_Analysis`, `*_RUL` – Analysis & predictions

---

## 🚀 Current Progress

- ✅ MongoDB dump restored locally
- ✅ Verified major collections and record counts
- ✅ Connected Prometheus to MongoDB
- ✅ Grafana setup in progress

---

## 🔧 Next Steps

- Set up Grafana dashboards with live query panels
- Design visualization layout for LiveData, FFT, and Health Summary
- Document queries, graphs, and insights

---

## 🧠 Learning Outcome

This project deepens my understanding of:

- Real-time data pipelines
- Industrial machine monitoring
- Full-stack observability (data → monitoring → visualization)

---

## 👨‍💻 Maintainer

**Akshat Palia**  
[GitHub](https://github.com/Akshat-palia)

---

