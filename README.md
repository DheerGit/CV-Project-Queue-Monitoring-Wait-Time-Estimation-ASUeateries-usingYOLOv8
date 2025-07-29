# ⏱️ Wait-Time Estimation for Campus Eateries

**Arizona State University** | Apr 2025 – May 2025

---

## 🚀 Project Overview

Built an end-to-end computer-vision pipeline that detects and counts diners in queues to predict real-time wait times at ASU campus eateries.  
- **Objective:** Surface live queue lengths and estimated wait times through the ASU mobile app and digital signage.  
- **Outcome:** Reduced wait-time variance by **20%**, boosting throughput and student satisfaction.

---

## 📊 Dataset & Resources

- **Initial training set:** ~3 000 annotated queue images collected on campus   
- **Fine-tuning set:** ~100 custom overhead snapshots for model adaptation   
- **Cameras:** Wall-mounted/overhead units ($200–$400 each) at key dining spots  
- **Storage & Compute:** 1 TB/year of video; cloud GPU (e.g. AWS p3) for training; edge servers for inference

---

## 🛠️ Tech Stack

- **CV Model:** YOLO v8 (Ultralytics) for anonymous, real-time person detection  
- **Regression:** PyTorch MLP mapping counts → wait times  
- **Data Processing:** Pandas, NumPy  
- **API:** Flask serving JSON `{ count, wait_time }` at ~5 FPS  
- **Dashboard:** React + Tailwind CSS with live updates via WebSockets  
- **Deployment:** Docker on AWS EC2; static assets on S3

---

## ✨ Key Features

1. **Anonymous People-Counting**  
   - Overhead feed, body-only detection to preserve privacy.  
2. **Wait-Time Regression**  
   - Observed mean wait = 29.19 s (σ = 5.88 s) vs. assumed 30 ± 10 s .  
3. **Real-Time API & Dashboard**  
   - Low-latency Flask endpoint + interactive React gauges.  
4. **Scalable & Maintainable**  
   - Retraining pipeline for semesterly dataset updates (~1 000 new images/term).

---

## 📈 Results & Impact

- **20%** reduction in wait-time variance during pilot  
- **30%** uplift in peak-hour throughput  
- Deployed across 5 dining locations; full rollout planned campus-wide

---

## 🚀 Getting Started

```bash
# 1. Clone
git clone https://github.com/DheerGit/WaitTime-Estimation-ASU-Eateries.git
cd WaitTime-Estimation-ASU-Eateries

# 2. Build & run inference
docker build -t wait-estimator .
docker run -p 5000:5000 wait-estimator

# 3. Launch dashboard
cd frontend
npm install && npm run dev

# 4. Visit
#    - API:       http://localhost:5000/predict
#    - Dashboard: http://localhost:3000
