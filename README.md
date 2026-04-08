# MLOps-Pipeline-with-Python-AWS-Docker-YouTube-Viewer-Sentiment
This Project teaches how build an end-to-end MLOps pipeline that analyzes YouTube sentiment in real-time through a Chrome extension. Using modern ML tools like MLflow, DVC, Docker, and AWS while developing a complete solution from data collection to deployment.

## 📌 Project Setup Steps

### 1. AWS Setup
- Created an S3 bucket  
- Launched an EC2 instance  

### 2. IAM Role Configuration
- Created a new IAM role  
- Attached **S3FullAccess** policy  
- Attached the role to the EC2 instance  

---

## 🖥️ EC2 Setup

### Install Dependencies
```bash
sudo apt update

sudo apt install python3-pip

sudo apt install pipenv

sudo apt install virtualenv
