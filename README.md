# ML-Driven Tribocorrosion Monitoring for Hip Implants

This repository documents the machine learning research phase of a wearable prototype designed to monitor the integrity of Total Hip Replacements (THR). The project focuses on detecting **tribocorrosion**—the simultaneous degradation of implants through mechanical wear and electrochemical reactions.

## Scientific Context
Traditional diagnostics often fail to detect early-stage wear. This project utilizes multi-modal sensor fusion to capture:
- **Acoustic Emission (AE):** Ultrasonic stress waves from mechanical friction.
- **Electrochemical Potential (EC):** Voltage/current spikes indicating passive layer breakdown.

> **Full System Scope:** This repo covers the ML training. Detailed hardware schematics (Raspberry Pi Zero 2 W / LM358 Op-Amp) and 3D CAD designs are available in the [Project Report](./Team_Report-1.pdf).

## Experimental Results & Disclaimers
We evaluated various sensor combinations to find the most robust diagnostic signature.

| Configuration | Features | Accuracy | Note |
| :--- | :--- | :--- | :--- |
| **Fusion** | AE + EC | **100%** | Perfect separation of failure modes in lab conditions. |
| **Chemical** | EC Only | **99.9%** | Highly sensitive to electrochemical spikes. |
| **Acoustic** | AE Only | **95.9%** | Robust detection of mechanical stress. |
| **Material** | M Only | **34.6%** | Low correlation; material type is not a primary failure predictor. |

### A Note on High Accuracy (99-100%)
The 100% accuracy achieved in the Fusion and EC models reflects the **high signal-to-noise ratio** of the sensors in a controlled laboratory environment. 
1. **Mathematical Separability:** In this dataset, the "Healthy," "Wear," and "Failure" signatures occupy distinct, non-overlapping spaces.
2. **Generalization:** While perfect for this setup, accuracy may vary in clinical "in-vivo" environments due to biological noise (movement, sweat, etc.).
3. **Verified Logic:** All models utilize a "Split-then-Scale" pipeline to ensure no data leakage occurred during training.



## 🛠️ Installation & Usage
1. Clone the repo.
2. Install dependencies: `pip install -r requirements.txt`
3. Run the main analysis: `jupyter notebook notebooks/01_Hybrid_Fusion_AE_EC.ipynb`
