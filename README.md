# ⌚ Grip Lab AI: The "Recovery 2.0" Algorithm

## 📌 Business Overview
The elite wearable market (Oura, Whoop, Garmin) faces a critical blind spot: current algorithms rely heavily on **Physiological** factors (HRV, Resting Heart Rate) to measure stress but completely ignore **Neuromuscular** factors.
* **The Problem:** A user can have a great heart rate (Green Score) but a fatigued Central Nervous System (CNS), leading to injury risk if they train heavy.
* **The Solution:** We validated **Isometric Grip Strength** as a scalable biometric to measure CNS readiness and created an algorithm to "correct" standard wearable scores.

## 🧠 Technical Approach
We proposed a **"Hybrid Scoring Model"** that adds an active calibration step to passive tracking.

### 1. Data Pipeline
* **Inputs:** Oura Ring Data (Sleep, HRV) + Squegg Smart Dynamometer (Grip Force, Duration).
* **Proprietary Metric:** **"Neural Asymmetry"** – The difference in performance between the left and right hand. A divergence >10% often signals neural fatigue before physical symptoms appear.

<img width="586" height="475" alt="image" src="https://github.com/user-attachments/assets/100b3df4-2ec8-4511-9fd5-e0fa611ac6c6" />

### 2. The Model (XGBoost + Logic Layer)
We built a stacked model to refine the "Readiness Score":
1.  **Base Score:** Derived from Oura (Sleep + HRV).
2.  **The Adjustment:**
    * *If Grip Strength < 30-Day Moving Average:* Apply **Linear Penalty**.
    * *If Asymmetry > Threshold:* Apply **Neural Penalty**.
3.  **Final Output:** A "Load Recommendation" (e.g., "High Intensity" vs. "Active Recovery").

<img width="1117" height="561" alt="image" src="https://github.com/user-attachments/assets/6d6429c4-eb5f-4685-b813-e822310c22ec" />

## 📈 Key Findings
* **The "Hidden Fatigue" Factor:** In **86% of Weightlifting cases**, our algorithm correctly downgraded a "High Readiness" score to "Caution," aligning with the athlete's actual RPE (Rate of Perceived Exertion).
* **Feature Importance:** "Grip Force Decay" (how fast you get tired squeezing) was a stronger predictor of daily readiness than Sleep Duration.

<img width="474" height="424" alt="image" src="https://github.com/user-attachments/assets/dc2e0a5c-23fc-4053-a8b9-7cbd71150a0c" />

## 🛠 Tools Used
* **Python:** XGBoost, Pandas, Scikit-Learn
* **Hardware:** Oura Ring API, Squegg Bluetooth Dynamometer
* **Visualization:** Plotly (Interactive Time-Series), Matplotlib

## 📂 Project Structure
* `Final Poster.pdf` - A one-page visual summary of the research.
* `S04- Grip Lab AI Final Report.pdf` - Full whitepaper on the algorithm logic.
* `final99.ipynb` - The Python code for the Adjustment Algorithm.
