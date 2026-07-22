# Spinal Kyphosis Detector Using Machine Learning

A full-stack web application that uses machine learning to help identify the likelihood of kyphosis based on three key clinical inputs. The project combines a FastAPI backend with a simple front-end experience to make the prediction process easy to understand and demonstrate.

> ⚠️ Medical Disclaimer: This application is for educational and demonstration purposes only. It should not be used for actual medical diagnosis or treatment decisions. Always consult a qualified healthcare professional for medical advice.

---

## Why This Project Matters

Kyphosis is a spinal condition in which the spine curves abnormally, often creating visible posture changes and, in more serious cases, pain, breathing issues, or reduced mobility. It can affect children, adolescents, and adults, and early detection is important because treatment outcomes are often better when the condition is identified early.

In the real world, one of the biggest challenges is that kyphosis may not always be obvious at first glance, and diagnosis often depends on clinical assessment, imaging, and specialist review. This makes it an important problem for health technology, education, and decision support systems.

Our project aims to show how machine learning can support awareness and preliminary screening by analyzing a small set of structured features that are often available in medical records.

![Kyphosis X-ray](frontend/assets/kyphosis-xray.png)

---

## Our Solution Approach

This project builds a simple predictive model that learns from historical medical-style data and predicts whether kyphosis is present or absent. The solution is designed to be:

- Easy to understand for students and beginners
- Lightweight and fast to run
- Suitable for a web-based demonstration
- Focused on clear explainability rather than complex clinical deployment

The system uses a decision tree classifier trained on the available dataset and exposes the prediction through a small web interface.

---

## How the Analysis Works

The analysis is based on three main components:

1. Age
   - Age is an important factor because spinal development and structural changes often vary significantly with age.
   - This helps the model understand whether the patient profile is more consistent with kyphosis or a normal spinal pattern.

2. Number of Vertebrae Involved
   - This refers to how many vertebrae are involved in the surgical or structural condition being considered.
   - A higher number may indicate a more severe or widespread pattern.

3. Starting Vertebrae Level
   - This represents the topmost vertebra level involved in the condition.
   - The location of the starting point can strongly affect how the curvature develops and is therefore useful for prediction.

These three features form the core of the analysis and are used by the model to make a prediction.

![Analysis Screenshot](frontend/assets/frontend.png)

---

## Model Accuracy

The model is trained using a decision tree classifier on a structured dataset with the three input features mentioned above. The training pipeline evaluates the model on a held-out test set, and the current implementation is designed to provide approximately 82% accuracy in this setup.

This makes the project a strong educational example of how machine learning can be used in a medical-inspired prediction problem, while also keeping the scope practical and understandable.

---

## Project Structure

```text
spinal-kyphosis-detector-using-machine-learning/
├── backend/
│   ├── main.py                 # FastAPI server
│   ├── requirements.txt        # Python dependencies
│   ├── model.pkl              # Pre-trained model (generated)
│   └── train_model.ipynb      # Jupyter notebook for model training
├── Dataset/
│   └── kyphosis.csv           # Training dataset
├── frontend/
│   ├── about.html
│   ├── index.html
│   ├── predict.html
│   ├── script.js
│   ├── style.css
│   └── assets/               # Images and static files
└── README.md
```

---

## Quick Start Guide

### Prerequisites
- Python 3.8+ installed
- pip package manager
- A modern web browser

### Step 1: Clone the Repository
```bash
git clone <repository-url>
cd spinal-kyphosis-detector-using-machine-learning
```

### Step 2: Set Up the Backend Environment
Navigate to the backend directory and create a virtual environment:
```bash
cd backend
python -m venv .venv
```

### Step 3: Activate Virtual Environment

**On Windows:**
```cmd
.\.venv\Scripts\activate
```

**On macOS/Linux:**
```bash
source .venv/bin/activate
```

You should see `(.venv)` in your command prompt when activated.

### Step 4: Install Dependencies
```bash
pip install -r requirements.txt
```

### Step 5: Start the Backend Server
The model is already trained and saved as `model.pkl`. Simply start the server:
```bash
python -m uvicorn main:app --host 127.0.0.1 --port 8000
```

You should see output like:
```
INFO:     Started server process
INFO:     Waiting for application startup.
Model loaded successfully from model.pkl
FastAPI server started successfully!
INFO:     Application startup complete.
INFO:     Uvicorn running on http://127.0.0.1:8000
```

### Step 6: Open the Frontend
**Option 1 - Simple HTTP Server (Python):**
Open a new terminal window and navigate to the frontend directory:
```bash
cd frontend
python -m http.server 3000
```

Then open your browser and go to: http://localhost:3000

**Option 2 - Direct File Opening:**
Navigate to the `frontend` folder and double-click `index.html`

---

## API Testing

You can test the API directly:

**Health Check:**
```bash
curl http://127.0.0.1:8000/health
```

**Make a Prediction:**
```bash
curl -X POST http://127.0.0.1:8000/predict \
  -H "Content-Type: application/json" \
  -d '{"age": 118, "number": 3, "start": 3}'
```

**View API Documentation:**
Visit http://127.0.0.1:8000/docs in your browser

---

## Model Training (Optional)

If you want to retrain the model or explore the training process:

1. Install Jupyter:
   ```bash
   pip install jupyter matplotlib seaborn
   ```

2. Start Jupyter:
   ```bash
   jupyter notebook train_model.ipynb
   ```

3. Run all cells in the notebook to see the training process and analysis

---

## Troubleshooting

**Virtual Environment Issues:**
- Make sure you see `(.venv)` in your command prompt
- If activation fails, try: `python -m venv .venv --clear`

**Port Already in Use:**
- Change the port: `--port 8001` instead of `--port 8000`
- Check what's using the port: `netstat -ano | findstr :8000` (Windows)

**Module Import Errors:**
- Ensure virtual environment is activated
- Reinstall dependencies: `pip install -r requirements.txt`

**Frontend Not Loading:**
- Try a different port for the frontend: `python -m http.server 3001`
- Check that the backend is running on port 8000
- Ensure your browser allows local connections

---

## Features of the App

- Educational home page explaining kyphosis
- Prediction page for entering age, number of vertebrae, and start level
- About page showing the project concept and model performance
- Simple web-based interface with a medical-themed design

---

## API Reference

| Endpoint | Method | Description |
|---|---|---|
| /health | GET | Server health check |
| /predict | POST | Returns a prediction result |
| /metrics | GET | Returns model-related metrics |

---

## Tech Stack

- Backend: Python, FastAPI, scikit-learn, pandas, joblib
- Frontend: HTML, CSS, JavaScript
- Model: Decision Tree Classifier

---

## License

This project is intended for educational and demonstration purposes only.

---

Built for learning, experimentation, and awareness about kyphosis detection through machine learning.