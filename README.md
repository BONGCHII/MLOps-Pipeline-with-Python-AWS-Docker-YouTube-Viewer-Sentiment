# MLOps-Pipeline-with-Python-AWS-Docker-YouTube-Viewer-Sentiment
This Project teaches how build an end-to-end MLOps pipeline that analyzes YouTube sentiment in real-time through a Chrome extension. Using modern ML tools like MLflow, DVC, Docker, and AWS while developing a complete solution from data collection to deployment.

## 📌 Project Setup Steps

### 1. AWS Setup

#### ✅ S3 Bucket
- Created an S3 bucket to store MLflow artifacts.

#### ✅ EC2 Instance Configuration
- **AMI**: Choose the **Ubuntu** image.
- **Instance Type**: Select at least **t2.medium**.
- **Storage**: Allocate a minimum of **30 GB** of EBS storage.

#### ✅ Network (VPC) & Security Group Settings
Update the **inbound rules** of the EC2 security group as follows:

| Type        | Protocol | Port Range | Source    | Purpose                     |
|-------------|----------|------------|-----------|-----------------------------|
| HTTP        | TCP      | 80         | 0.0.0.0/0 | Web access                  |
| HTTPS       | TCP      | 443        | 0.0.0.0/0 | Secure web access           |
| Custom TCP  | TCP      | 5000       | 0.0.0.0/0 | MLflow UI access            |

---

### 2. IAM Role Configuration
- Created a new IAM role.
- Attached the **S3FullAccess** policy.
- Attached the role to the EC2 instance.

---

## 🖥️ EC2 Setup & MLflow Installation

Run the following commands on the EC2 instance:

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
```

---

## 🌐 Access MLflow UI

- Open EC2 **Public IPv4 DNS**
- Use port: `5000`

Example:

    http://<EC2-PUBLIC-DNS>:5000

---

