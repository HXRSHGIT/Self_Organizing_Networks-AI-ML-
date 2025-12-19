# ML-Driven Self-Organizing Network (SON)

## Overview
This project demonstrates a **Machine Learning–driven Self-Organizing Network (SON)** using telecom Key Performance Indicator (KPI) data.  
The goal is to show how **simple, interpretable ML models** can support SON functions such as:

- Self-Configuration  
- Self-Optimization  
- Self-Healing  

The project focuses on **decision support**, not real-time network automation.

---

## Problem Statement
Modern cellular networks consist of thousands of cells generating continuous KPI data.  
Manual monitoring and troubleshooting of these KPIs does not scale and leads to delayed fault detection and degraded Quality of Service (QoS).

**Objective:**
> Automatically analyze KPI data using ML to detect network degradation and assist SON self-healing decisions.

---

## Dataset
Since real operator data is proprietary, a **synthetic telecom KPI dataset** is used.

Each row represents a network cell with the following KPIs:
- `throughput_mbps`
- `latency_ms`
- `drop_rate`
- `packet_loss`
- `rsrp_dbm`

The dataset simulates:
- Healthy cells
- Degraded cells
- Faulty cells

---

## SON Functions Implemented

### 1. Self-Configuration
- Demonstrated using regression-based parameter expectation
- Represents initial KPI estimation for new or reconfigured cells

### 2. Self-Optimization
- Uses clustering to group cells into performance tiers
- Helps identify underperforming cells requiring optimization

### 3. Self-Healing (Primary Focus)
- Detects abnormal KPI behavior
- Classifies cells into:
  - Normal
  - Degraded
  - Critical
- Assigns corrective actions such as:
  - Traffic offloading
  - Technician dispatch
- Triggers automated alerts for critical cells

---

## Machine Learning Models Used

| SON Function | ML Task | Model |
|-------------|-------|-------|
| Self-Configuration | Parameter estimation | Linear Regression |
| Self-Optimization | Performance grouping | K-Means Clustering |
| Self-Healing | Fault detection | Isolation Forest |

These models were chosen for:
- Interpretability
- Low complexity
- Operational relevance

---

## Self-Healing Workflow
1. Load KPI data
2. Normalize features
3. Apply anomaly detection
4. Classify degradation severity
5. Assign healing actions
6. Trigger operator alerts via email

---

## Visualization
The project includes KPI visualizations such as:
- Packet loss vs cell health
- Latency vs drop rate
- Healthy vs faulty cell distributions

These plots validate that ML-detected faulty cells exhibit degraded KPI behavior.

---

## Automated Alerting
When **critical cells** are detected:
- Relevant KPI information is collected
- A structured email alert is generated
- Notification is sent to the operator

Email credentials are securely handled using **environment variables**.

---

## Scope & Limitations

### Included
- KPI analysis
- ML-based SON logic
- Decision support
- Automated alerts

### Not Included
- Real network automation
- Closed-loop optimization
- Hardware integration
- Advanced AI models

---

## Technologies Used
- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib / Seaborn
- Google Colab
- SMTP (Email alerts)

---

## How to Run
1. Open the notebook in Google Colab
2. Run all cells sequentially
3. Set environment variables for email alerts
4. Observe ML outputs and visualizations

---

## Conclusion
This project demonstrates how machine learning can enhance **SON self-healing** by:
- Proactively detecting faults
- Reducing manual monitoring
- Supporting faster operator response

The approach is scalable, explainable, and aligned with real telecom network operations.

---

## Author
**Harsh Thakur**

---

## License
This project is intended for educational and academic demonstration purposes.
