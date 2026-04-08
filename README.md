# MLOps-Pipeline-with-Python-AWS-Docker-YouTube-Viewer-Sentiment
This Project teaches how build an end-to-end MLOps pipeline that analyzes YouTube sentiment in real-time through a Chrome extension. Using modern ML tools like MLflow, DVC, Docker, and AWS while developing a complete solution from data collection to deployment.

📌 Project Setup Steps
1. AWS Setup
Created an S3 bucket
Launched an EC2 instance
2. IAM Role Configuration
Created a new IAM role
Attached S3FullAccess policy
Attached the role to the EC2 instance
🖥️ EC2 Setup
Install Dependencies
sudo apt update

sudo apt install python3-pip

sudo apt install pipenv

sudo apt install virtualenv
Create Project Directory
mkdir mlflow

cd mlflow
Install Required Packages
pipenv install mlflow

pipenv install awscli

pipenv install boto3
Activate Environment
pipenv shell
▶️ Start MLflow Server
mlflow server \
--backend-store-uri sqlite:///mlflow.db \
--default-artifact-root s3://ml-flows-bucket-011 \
--host 0.0.0.0 \
--port 5000 \
--allowed-hosts '*'
🌐 Access MLflow UI
Open EC2 Public IPv4 DNS
Use port: 5000

Example:

http://<EC2-PUBLIC-DNS>:5000
