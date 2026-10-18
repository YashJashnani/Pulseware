# Pulseware — Heart Rhythm & Health Prediction

Pulseware is a decision-support prototype that helps you understand your heart rhythm from everyday wearable data. It learns what is normal for *you* from your history and flags new readings that look different from your usual pattern. It is not a medical device.

### Features

**Tier 1: Continuous Monitoring**
- Builds a personalized baseline from your PPG-derived history (BPM, SDNN, RMSSD)
- Scores new readings as Normal, Monitor, or Flag for review with an explanation
- Handles post-exercise recovery (2-hour window → Expected recovery) and supports symptom-based escalation
- Upload a reading via CSV, Excel, image or PDF — screenshots are read with Google Gemini Vision AI

**History**
- View your recent heart rate & HRV chart and all recent checks in one place

**Tier 2: ECG Snapshot**
- On-demand classification of single-lead ECG snapshots (Normal, PVC-like, AFib-like, Bradycardia-like, Abnormal)
- Upload an ECG as image, PDF or CSV, or enter values manually
- Safety guardrails check heart rate, QTc, QRS width and P-wave
- Trained on MIT-BIH Arrhythmia Database when available, otherwise synthetic data

### Tech Stack

- **Streamlit** (Python) — `app.py`, `anomaly_model.py`, `ecg_classifier.py`
- **React + Vite** — `web-app/src/App.jsx`
- **Models:** Isolation Forest (personal baseline), Random Forest (ECG)
- **Vision:** Google Gemini for screenshot/PDF reading

### Project Structure

```
Pulseware/
├── app.py                    # Streamlit app
├── .streamlit/config.toml    # Theme
├── anomaly_model.py          # Tier 1 baseline model
├── ecg_classifier.py         # Tier 2 ECG classifier
├── field_aliases.py          # Field definitions
├── file_reading.py           # File + Gemini reading
├── baseline_threshold.py
├── generate_dummy_data.py    # Sample data
├── ppg_preprocessing.py      # PPG filtering & features
├── requirements.txt
├── screenshots/
└── web-app/                  # React app
    ├── src/App.jsx
    ├── src/styles.css
    ├── src/main.jsx
    ├── index.html
    ├── vite.config.js
    └── package.json
```
