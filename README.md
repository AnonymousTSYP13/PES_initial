# 🧠 AI Energy Health Monitoring System for Smart Factories  
### Integrating NILM-based Energy Disaggregation & PV Anomaly Detection  
*(IEEE PES & YP Tunisia Challenge 2025 — Energy Utopia)*

---

## 📝 Overview

This repository hosts the implementation of the **AI Energy Health Monitoring System**, an intelligent platform designed to monitor, diagnose, and optimize both **renewable energy generation (PV)** and **industrial electricity consumption** within **smart factories**.

The project unifies two complementary AI modules:

1. **Consumption-side Intelligence (NILM + Classification)**  
   - Non-Intrusive Load Monitoring (NILM) using **LSTM** models for energy disaggregation.  
   - Classification module for detecting **overconsumption and anomalous machine behavior**.

2. **Production-side Intelligence (PV Fault Detection)**  
   - **Random Forest** (and optionally LSTM) models for detecting photovoltaic anomalies such as **short-circuit**, **open-circuit**, and **partial shading**.

Together, these modules create a **unified energy intelligence layer** enabling predictive maintenance, efficiency optimization, and holistic factory energy management.

---

## 🧩 Repository Structure

```
AI_Energy_Health_Monitoring/
│
├── README.md                # Project documentation (this file)
│
├── Classification/           # Consumption-side intelligence
│   ├── main.py               # Pipeline orchestration
│   ├── train.py              # Training script for MLP model
│   ├── model.py              # Neural network definition (classification)
│   ├── loader.py             # Data loader for machine consumption data
│   ├── labelling.py          # Label generation (overconsumption detection)
│   ├── preprocessing.py      # Cleaning and feature scaling
│   ├── evaluate.py, plot.py  # Evaluation & visualization utilities
│   ├── data/                 # Industrial dataset (HIPE-based CSVs)
│   ├── model/                # Saved trained models
│   └── plots/                # Generated analysis plots
│
├── NILM/                     # Non-Intrusive Load Monitoring (LSTM)
│   ├── main.py               # Entry point for NILM pipeline
│   ├── src/
│   │   ├── data_loader.py
│   │   ├── preprocessing.py
│   │   ├── model.py          # LSTM architecture for disaggregation
│   │   ├── train.py
│   │   ├── evaluate.py
│   │   └── config.py         # Model & data configuration
│   ├── data/                 # Aggregated and sub-metered power data
│   ├── notebooks/            # EDA & experiments (Jupyter)
│   └── outputs/
│       ├── models/           # Trained LSTM models
│       └── plots/            # NILM result visualizations
│
└── requirements.txt          # Python dependencies
```

---

## ⚙️ Installation

1. **Create a virtual environment**
   ```bash
   python -m venv .venv
   .venv\Scripts\activate
   ```
2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

---

## 🚀 Quick Start

### 🔹 Consumption Anomaly Detection (Classification)

```bash
# Launch the full classification pipeline
python Classification/main.py
```

Adjust parameters in:
- `Classification/train.py` → model hyperparameters  
- `Classification/labelling.py` → thresholds for overconsumption  
- `Classification/loader.py` → input CSV paths  

Outputs:
- Trained models → `Classification/model/`  
- Graphs & metrics → `Classification/plots/`

---

### 🔹 NILM (Non-Intrusive Load Monitoring)

```bash
# Run NILM model training
python NILM/main.py
```

Configuration:
- Sequence length, batch size, epochs → `NILM/src/config.py`  
- Input data → `NILM/data/`  

Outputs:
- LSTM models → `NILM/outputs/models/`  
- Disaggregation visualizations → `NILM/outputs/plots/`

---

## 🧠 AI Models Summary

| Module | Model Type | Objective | Dataset |
|:--|:--|:--|:--|
| NILM | LSTM | Disaggregate total power into per-machine loads | HIPE Industrial Dataset |
| Classification | MLP | Detect abnormal or overconsuming machines | HIPE Dataset |
| PV Fault Detection | Random Forest / LSTM | Detect faults (SC, OC, PS) in solar panels | Digital Twin PV Dataset |

---

## 📊 Datasets

1. **HIPE Industrial Dataset**  
   - Real factory data with Active (P), Reactive (Q), Apparent (S) power, Voltage (V), and Current (I).  
   - Sampling: 0.2 Hz, duration: 3 months.  
   - Used for NILM and overconsumption classification.

2. **Digital Twin PV Dataset**  
   - Generated via MATLAB Simulink PV microgrid model.  
   - Simulates healthy and faulty solar conditions (SC, OC, PS).  
   - ~5.8 million samples over 11 simulated years.

---

## 🌐 Integrated Energy Intelligence Layer

Both models feed a unified analytical dashboard that:
- Correlates **PV production** with **machine-level consumption**.  
- Identifies **root causes** of anomalies (supply or demand side).  
- Recommends **load balancing and maintenance actions**.

---

## 📈 Key Metrics

| Task | Metric | Description |
|:--|:--|:--|
| NILM | MAE, F1-score | Disaggregation accuracy & device state detection |
| Classification | Precision, Recall, F1 | Overconsumption detection quality |
| PV Fault Detection | Confusion Matrix, Accuracy | Fault identification reliability |
| System | Latency | Real-time deployment feasibility |

---

## ♻️ Impact & Sustainability

- **Economic:** Reduced downtime, optimized energy use, predictive maintenance  
- **Environmental:** Lower CO₂ footprint, renewable integration  
- **Technological:** AI-driven control, scalability toward Industry 5.0  
- **Social:** Promotes digital transition and technical upskilling  

Aligned with:
- **SDG 7:** Clean Energy  
- **SDG 9:** Industry, Innovation, Infrastructure  
- **SDG 12:** Responsible Consumption & Production

---

## 🤝 Contribution

- Extend the NILM module to Transformer-based architectures  
- Add visualization dashboards (Streamlit / Dash)  
- Integrate real-time PV anomaly detection  

Contributions, feedback, and dataset improvements are welcome.

---

## 📚 References

- HIPE Dataset: *High-resolution Industrial Production Energy* (public benchmark).  
- MATLAB Digital Twin simulations for PV microgrids.  
- TensorFlow / Keras, Scikit-learn, Pandas, Matplotlib.  
- IEEE PES & YP Tunisia Challenge 2025 — *Energy Utopia: AI for a Smarter, Greener Future*.
