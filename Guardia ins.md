# Delaroche Guardia — AI Scam & Phishing Shield (SMS MVP)

**Guardia** is a small security app that flags scammy **SMS** messages with
a learned AI model. Upload a CSV of messages, pick how strict you want to be,
see per-message risk and reasons, and export only the risky ones.

https://github.com/<YOUR-USERNAME>/delaroche-guardia

## ✨ Features
- Upload CSV (`label,text` or just `text`)
- AI scoring with probability (`spam_prob`)
- Threshold slider (precision/recall trade-off)
- “Show only spam” + sort by risk
- Quick keyword hints (“why”)
- Highlight very high-risk rows
- Download **all predictions** or **spam-only**

## 🧠 What’s inside (plain words → pro terms)
- Learns from examples → *supervised learning on the UCI SMS Spam dataset*
- Turns words into numbers → *TF-IDF (unigrams+bigrams)*
- Predicts with confidence → *Logistic Regression, `predict_proba`*
- Saved model → *joblib artifact at `data/processed/sms_model.joblib`*
- UI → *Streamlit app (`streamlit_app.py`)*

## 📦 Install & Run (Windows / PowerShell)
```powershell
# 1) create venv and install deps
python -m venv .venv
.\.venv\Scripts\activate
pip install -r requirements.txt

# 2) train the model (optional; a model may already be checked in)
$env:PYTHONPATH = "$PWD\src"
.\.venv\Scripts\python.exe scripts\train_sms_baseline.py

# 3) launch app
.\.venv\Scripts\python.exe -m streamlit run streamlit_app.py --server.address=127.0.0.1 --server.port=8501
