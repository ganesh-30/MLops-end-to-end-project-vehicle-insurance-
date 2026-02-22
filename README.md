<div align="center">

# 🚗 Vehicle Data MLOps Pipeline
### End-to-End Production ML System with CI/CD on AWS

![Python](https://img.shields.io/badge/Python-3.10-3776AB.svg?style=flat&logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-005571?style=flat&logo=fastapi)
![AWS](https://img.shields.io/badge/AWS-%23FF9900.svg?style=flat&logo=amazon-aws&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED.svg?style=flat&logo=docker&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-%234ea94b.svg?style=flat&logo=mongodb&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF.svg?style=flat&logo=github-actions&logoColor=white)

</div>

---

## 📌 Project Overview

This project demonstrates a **production-grade Machine Learning pipeline** built using modern MLOps principles. It covers the complete ML lifecycle — from data ingestion to automated cloud deployment. The system is designed with scalability, maintainability, and automation in mind.

### ✅ Key Features
- Modular ML pipeline architecture
- MongoDB-based data ingestion (development only)
- Data validation & transformation
- Model training & evaluation
- AWS S3 model registry
- Dockerized deployment
- Automated CI/CD using GitHub Actions
- Deployment on AWS EC2

---

## 🏗️ Architecture Overview

**Data Flow Pipeline:**
```text
MongoDB Atlas (Dev) ➔ Data Ingestion ➔ Data Validation ➔ Data Transformation ➔ Model Trainer ➔ Model Evaluation ➔ Model Pusher (AWS S3) ➔ Prediction Pipeline (FastAPI) ➔ Docker ➔ ECR ➔ EC2 (CI/CD)
```
# ⚙️ Tech Stack

🔹 Backend & ML
Language: Python 3.10

Framework: FastAPI

Libraries: Scikit-learn, Pandas, NumPy, PyYAML

🔹 Database
Database: MongoDB Atlas

🔹 Cloud Services
AWS S3: Model Registry

AWS ECR: Docker Image Storage

AWS EC2: Deployment environment

AWS IAM: Access Control

🔹 DevOps & Automation
Containerization: Docker

CI/CD: GitHub Actions

Runner: Self-hosted Runner on EC2

# 📂 Project Structure

```text
src/
├── components/
│   ├── data_ingestion.py
│   ├── data_validation.py
│   ├── data_transformation.py
│   ├── model_trainer.py
│   ├── model_evaluation.py
├── entity/
├── configuration/
├── aws_storage/
├── constants/
├── pipeline/
│   ├── training_pipeline.py
│   ├── prediction_pipeline.py
app.py
Dockerfile
requirements.txt
.github/workflows/aws.yaml
```

# 🗄️ MongoDB Setup (Development Only)

MongoDB is used only for local training and experimentation.

Steps:
Create a MongoDB Atlas project

Create an M0 cluster

Add a database user

Allow IP access: 0.0.0.0/0

Copy the connection string

Set Environment Variable:
Bash:

```Bash
export MONGODB_URL="your_connection_string"
PowerShell:

PowerShell
$env:MONGODB_URL="your_connection_string"
```
⚠️ Note: MongoDB is NOT required for deployment. Deployment uses only the prediction pipeline and pre-trained models.

# ☁️ AWS Setup

1️⃣ IAM User
Programmatic access enabled

AdministratorAccess policy attached

2️⃣ S3 Bucket
Bucket Name: your_bucket_name

Region: us-east-1

3️⃣ Environment Variables
```Bash
export AWS_ACCESS_KEY_ID="your_key"
export AWS_SECRET_ACCESS_KEY="your_secret"
export AWS_DEFAULT_REGION="us-east-1"
```
# 🐳 Docker Setup

Build Image:

```Bash
docker build -t vehicleproj .
```
Run Locally:

```Bash
docker run -p 5000:5000 vehicleproj
```
Application runs at: http://localhost:5000

# 🚀 CI/CD Pipeline

Triggered on every push to the main branch. Ensures fully automated, zero-downtime deployments.

Continuous Integration:

Build Docker image

Push image to AWS ECR

Continuous Deployment:

Pull latest image on EC2

Stop previous container

Deploy updated container

# 🌐 Production Deployment

Docker image stored in AWS ECR

EC2 Ubuntu server hosts the application

Port 5000 exposed via Security Group

Access the application: http://<EC2_PUBLIC_IP>:5000

# 🔐 Security Best Practices

✔️ AWS credentials stored securely as GitHub Secrets

✔️ Environment variables for sensitive configs

✔️ No secrets hardcoded in the codebase

✔️ .env, artifact/, and local files ignored via .gitignore

# 🧠 MLOps Concepts Demonstrated

Modular ML pipeline architecture

Configuration-driven design

Artifact management

Model registry using S3

Docker containerization

CI/CD automation

Cloud-native deployment

# ▶️ Running Locally

To set up the project on your local machine:

``` Bash
conda create -n vehicle python=3.10 -y
conda activate vehicle
pip install -r requirements.txt
python app.py
```

# 📈 Future Improvements

[ ] Implement real-time Model monitoring

[ ] Add AWS CloudWatch logging

[ ] Create multi-environment deployment (Staging/Production)

[ ] Adopt Infrastructure as Code (Terraform)

[ ] Integrate a model versioning strategy (e.g., MLflow)

# 👨‍💻 Author
**Ganesh Deshpande** 

Machine Learning Engineer | MLOps Enthusiast Skills: AWS | Docker | FastAPI | CI/CD
