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

## 🖥️ EC2 Setup & MLflow Installation (All Commands)

```bash
# Update system
sudo apt update

# Install dependencies
sudo apt install -y python3-pip
sudo apt install -y pipenv
sudo apt install -y virtualenv

# Create project directory
mkdir mlflow
cd mlflow

# Install required packages
pipenv install mlflow
pipenv install awscli
pipenv install boto3

# Activate environment
pipenv shell

# Start MLflow server
mlflow server \
--backend-store-uri sqlite:///mlflow.db \
--default-artifact-root s3://ml-flows-bucket-011 \
--host 0.0.0.0 \
--port 5000 \
--allowed-hosts '*'
