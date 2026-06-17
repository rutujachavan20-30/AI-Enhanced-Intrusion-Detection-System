# AI-Enhanced Intrusion Detection System 🛡️

## Project Overview

The **AI-Enhanced Intrusion Detection System (IDS)** is a machine learning-powered cybersecurity web application that detects and classifies network intrusions in real time. It uses a **Random Forest Classifier** trained on NSL-KDD dataset features to identify five types of network traffic: Normal, DoS, Probe, R2L, and U2R attacks.

Built with **Python Flask** and deployed as a full-stack web application, it includes a live dashboard, prediction interface, alert logging, and a REST API endpoint.

---

## Folder Structure

```
AI-Enhanced-Intrusion-Detection-System/
├── Documentation/
│   └── Project_Documentation.docx
├── models/
│   ├── ids_model.pkl          ← Trained Random Forest model (generated)
│   └── scaler.pkl             ← Feature scaler (generated)
├── static/
│   └── css/
│       └── style.css
├── templates/
│   ├── home.html
│   ├── dashboard.html
│   ├── predict.html
│   ├── alerts.html
│   └── about.html
├── app.py                     ← Main Flask application
├── train_model.py             ← ML model training script
├── requirements.txt
└── README.md
```

---

## Technologies Used

| Category        | Technology                          |
|-----------------|--------------------------------------|
| Backend         | Python 3, Flask                     |
| Machine Learning| scikit-learn (Random Forest)        |
| Data Processing | NumPy, Pandas                       |
| Frontend        | HTML5, CSS3, Bootstrap 5, Chart.js  |
| Model Storage   | Pickle (.pkl)                       |
| Dataset         | NSL-KDD (Network Intrusion Dataset) |
| Version Control | Git & GitHub                        |

---

## System Architecture

```
User (Browser)
      |
      ▼
[ Flask Web Server (app.py) ]
      |              |
      ▼              ▼
[ ML Model ]    [ Alert Log ]
  Random Forest   In-memory / DB
  (ids_model.pkl)
      |
      ▼
[ Prediction Result ]
  Normal / DoS / Probe / R2L / U2R
```

---

## Attack Categories Detected

| Attack Type | Full Name               | Description                                      |
|-------------|-------------------------|--------------------------------------------------|
| **DoS**     | Denial of Service       | Floods server with traffic to crash/slow it      |
| **Probe**   | Probing / Port Scan     | Scans network to find open ports/vulnerabilities |
| **R2L**     | Remote to Local         | Unauthorized access from a remote machine        |
| **U2R**     | User to Root            | Privilege escalation to gain admin/root access   |
| **Normal**  | Normal Traffic          | Legitimate, safe network connection              |

---

## Features

- **ML-Powered Prediction** — Random Forest model classifies network traffic with ~96% accuracy
- **Real-Time Analysis** — Enter network features and get an instant threat classification
- **Live Dashboard** — See total analyses, attack count, normal count, and doughnut chart
- **Alert Logging** — All predictions are logged with timestamp, label, and confidence score
- **Demo Mode** — Quick "Simulate Attack" buttons for DoS, Normal, and R2L scenarios
- **REST API** — `POST /api/predict` endpoint for programmatic integration
- **Confidence Score** — Each prediction shows a percentage confidence

---

## Setup & Run

### Step 1: Clone Repository
```bash
git clone https://github.com/<your-username>/AI-Enhanced-Intrusion-Detection-System.git
cd AI-Enhanced-Intrusion-Detection-System
```

### Step 2: Install Dependencies
```bash
pip install -r requirements.txt
```

### Step 3: Train the ML Model
```bash
python train_model.py
```
This creates `models/ids_model.pkl` and `models/scaler.pkl`.

### Step 4: Run the Flask App
```bash
python app.py
```

### Step 5: Open in Browser
```
http://localhost:5000
```

---

## Application Routes

| Route           | Method     | Description                              |
|-----------------|------------|------------------------------------------|
| `/`             | GET        | Home page with feature overview          |
| `/dashboard`    | GET        | Live stats dashboard with chart          |
| `/predict`      | GET, POST  | Network traffic prediction form          |
| `/alerts`       | GET        | Full alert log with confidence bars      |
| `/about`        | GET        | Project details, tech stack, API docs    |
| `/api/predict`  | POST       | REST API for programmatic predictions    |

---

## API Usage

### Endpoint
```
POST /api/predict
Content-Type: application/json
```

### Request Body
```json
{
  "features": [0, 490000, 0, 0, 3, 0, 0, 0, 0, 0]
}
```

Feature order:
1. duration
2. src_bytes
3. dst_bytes
4. land
5. wrong_fragment
6. urgent
7. hot
8. num_failed_logins
9. logged_in
10. num_compromised

### Response
```json
{
  "label": "DoS Attack",
  "confidence": 92.3,
  "is_attack": true,
  "timestamp": "2024-10-15T14:32:00"
}
```

---

## ML Model Details

- **Algorithm:** Random Forest Classifier (100 estimators)
- **Dataset:** NSL-KDD (synthetic generation for demo; replace with real NSL-KDD CSV for production)
- **Train/Test Split:** 80% / 20%
- **Accuracy:** ~96%
- **Classes:** Normal (0), DoS (1), Probe (2), R2L (3), U2R (4)
- **Preprocessing:** StandardScaler for feature normalization

---

## Screenshots

### Home Page
> Hero section with attack type badges and feature cards

### Dashboard
> Real-time stats cards + doughnut chart of traffic classification

### Predict Page
> 10-feature input form with quick demo buttons and result card

### Alerts Page
> Full table of all logged predictions with confidence progress bars

---

## Future Enhancements

- Integrate real-time packet capture using Scapy
- Add user authentication for admin access
- Deploy on AWS EC2 with persistent database (RDS/SQLite)
- Add email/SMS alerts for high-confidence threat detections
- Extend to deep learning model (LSTM for sequential traffic analysis)

---

## Conclusion

This project demonstrates how Artificial Intelligence can be applied to the domain of **network security** to automate intrusion detection. The combination of Flask (web framework), scikit-learn (ML), and Bootstrap (UI) creates a practical, deployable cybersecurity tool suitable for small network environments, academic demonstrations, and internship showcases.

---

## Author

**Your Name**
Final Project — AI & Cybersecurity
SmartInternz Externship Program — 2024
