# ML-Driven Wearable Prototype for Tribocorrosion Monitoring in Hip Implants

This repository documents the development of a diagnostic system that uses Machine Learning to monitor the structural and chemical integrity of Total Hip Replacements (THR) in real-time.



## Scientific Foundation: Tribocorrosion
Unlike traditional monitoring, this project focuses on **Tribocorrosion**—the synergistic effect of mechanical wear and electrochemical degradation. 
- **AE (Acoustic Emission):** Captures high-frequency vibrations from mechanical friction.
- **EC (Electrochemical Potential):** Detects voltage spikes indicating a breach in the implant's protective passive layer.
- **M (Material):** Categorical data representing specific implant alloy compositions.

> **Note:** This repository focuses on the ML Pipeline. The complete scope, including the **Raspberry Pi Zero 2 W** integration and **LM358 Signal Conditioning**, is available in the report.

## Model Performance & Verification
We conducted a series of experiments to find the most accurate "sensor fusion" signature.

| Configuration | Features | Algorithm | Accuracy |
| :--- | :--- | :--- | :--- |
| **Fusion Model** | AE + EC | Random Forest | **100%** |
| **Acoustic Focus** | AE Only | Gradient Boosting | **95.9%** |
| **Material Study** | AE + M | Random Forest | **95.7%** |
| **Baseline** | M Only | Naive Bayes | **34.6%** |

### Analysis of High Accuracy (99-100%)
The 100% and 99.9% results achieved in the fusion models have been verified through a rigorous **Split-then-Scale** pipeline to ensure zero data leakage. 
- **Physical Separation:** The high accuracy is due to the distinct, non-overlapping signatures of "Healthy" vs "Failure" states in a controlled lab environment.
- **Generalization:** While perfect in lab conditions, real-world clinical use would introduce biological noise (movement artifacts), which would likely normalize these figures.



## Tech Stack
- **AI/ML:** Scikit-Learn, XGBoost, Pandas, NumPy.
- **Hardware:** Raspberry Pi Zero 2 W, Arduino Nano, Piezoelectric Sensors.
- **Electronics:** LM358 Operational Amplifier (Signal Gain: 6.5).

## Getting Started
1. Clone the repo.
2. Install dependencies: `pip install -r requirements.txt`
3. Explore the main results in `notebooks/01_Fusion_Model_AE_EC.ipynb`.
