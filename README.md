# ⚙️ Predictive Maintenance Analytics for CNC Milling Machines

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)
![Plotly](https://img.shields.io/badge/Plotly-Interactive-lightgrey.svg)
![Data Analysis](https://img.shields.io/badge/Data-Analytics-success.svg)

## 📌 Project Overview
In the modern manufacturing landscape, unexpected equipment breakdown is a primary driver of operational cost and lost production time. This project facilitates a data-driven transition from **reactive maintenance** (fixing broken machines) to **predictive maintenance** (intervening before catastrophic failure). 

By analyzing the physical sensor logs of a CNC milling machine, this project isolates specific operational envelopes—such as thermal limits, torque-speed interactions, and tool wear thresholds—that directly trigger mechanical breakdowns.

## 📊 The Dataset
The data utilized in this project is the **AI4I 2020 Predictive Maintenance Dataset**, sourced from the UCI Machine Learning Repository. 
* **Size:** 10,000 operational records.
* **Features:** 14 distinct features including continuous sensor telemetry (RPM, Torque, Temperatures) and cumulative Tool Wear.
* **Failure Modes Isolated:**
  * `TWF`: Tool Wear Failure
  * `HDF`: Heat Dissipation Failure
  * `PWF`: Power Failure
  * `OSF`: Overstrain Failure
  * `RNF`: Random Failures

## 🛠️ Tech Stack & Libraries
* **Language:** Python
* **Environment:** Jupyter Notebook
* **Data Manipulation:** `pandas`, `numpy`
* **Data Visualization:** `plotly.express` (Interactive), `matplotlib`, `seaborn` (Static)

## 🔬 Key Feature Engineering
To capture the true physical stresses on the machine, raw sensor data was transformed into derived mechanical metrics:
1. **Temperature Differential ($\Delta T$):** Calculated the exact difference between ambient air and spindle process temperature to act as a proxy for cooling efficiency.
2. **Continuous Mechanical Power (Watts):** Derived true mechanical workload by calculating $Power = Torque \times Angular Velocity$, allowing for accurate identification of overstrain events.

## 💡 Key Analytical Insights
1. **The Power Envelope:** Machine failures are heavily concentrated at the extreme boundaries of the operational power band (High Torque/Low RPM and High RPM/Low Torque).
2. **The Tool Wear Cliff:** A massive cluster of failures occurs strictly after **200 minutes** of accumulated tool wear, driven by rising friction.
3. **Thermal Dependency:** Process temperatures are strictly linearly dependent on ambient factory temperatures ($r \approx 0.88$), causing Heat Dissipation Failures (HDF) when the room cannot absorb excess spindle heat.
4. **Compounding Stresses:** Multivariate analysis reveals failures are rarely single-variable events; they occur when multiple thresholds (e.g., High Wear + High Torque) are crossed simultaneously.

## 🎯 Strategic Business Recommendations
Based on the EDA, the following quality control and maintenance protocols are recommended:
* **Hard-Stop Tool Replacement:** Mandate a preventative cutting tool swap at exactly 180 minutes of continuous operational wear.
* **Dynamic CNC Governors:** Program software-based RPM/Torque limits into the machine controller to prevent operations outside the safe mechanical power envelope.
* **Active Cooling Upgrades:** Improve localized spindle cooling or shop-floor HVAC systems, as thermodynamic failures are directly tied to ambient room temperatures.

## 🚀 How to Run this Project
1. Clone this repository to your local machine:
   ```bash
   git clone [https://github.com/VaisakhanMN/DA-CAPSTONE-PROJECT/tree/main]

## 👨‍💻 Author

**Vaisakhan M.N.** *Data Analyst*
