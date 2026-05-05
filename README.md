# AWS Serverless Web Application

## Overview
This project demonstrates how to build a fully serverless web application using AWS services.

Users can submit data through a web interface, which is processed by a backend API and stored in a database.

---

## Architecture
User → CloudFront → S3 → API Gateway → Lambda → DynamoDB

![Architecture](./architecture/architecture-diagram.png)

---

## Services Used
- Amazon S3
- Amazon CloudFront
- Amazon API Gateway
- AWS Lambda
- Amazon DynamoDB
- AWS IAM

---

## Project Structure
aws-serverless-app/
│
├── frontend/
│   ├── index.html
│   ├── style.css
│   └── script.js
│
├── lambda/
│   └── function.py (or index.js)
│
├── screenshots/
│   ├── frontend/
│   ├── api/
│   ├── lambda/
│   ├── dynamodb/
│   └── solutions/
│
├── architecture/
│
├── terraform/   (optional but recommended)
│
└── README.md

---

## Setup Steps (Manual)

### 1. Create DynamoDB Table
Create a table to store user data.

![DynamoDB](./screenshots/dynamodb/table.png)

---

### 2. Create Lambda Function
Create a Lambda function to process incoming requests.

- Runtime: Python / Node.js
- Add logic to store data in DynamoDB

![Lambda](./screenshots/lambda/function.png)

---

### 3. Create API Gateway
Create a REST API and connect it to the Lambda function.

![API Gateway](./screenshots/api/api.png)

---

### 4. Enable CORS
Enable CORS so the frontend can call the API.

![CORS](./screenshots/api/cors.png)

---

### 5. Build Frontend (S3)
Create a simple HTML form and host it on S3.

![Frontend](./screenshots/frontend/form.png)

---

### 6. Connect Frontend to API
Use JavaScript (fetch/axios) to send requests to API Gateway.

---

### 7. (Optional) Add CloudFront
Distribute the frontend securely via CloudFront.

---

## Problems and Solutions

### Problem 1 – CORS Error
Frontend could not call the API.

**Solution:**
Enabled CORS in API Gateway.

---

### Problem 2 – Lambda Permission Error
Lambda could not write to DynamoDB.

**Solution:**
Attached correct IAM role with DynamoDB permissions.

---

## Terraform Implementation (Optional)

This project can also be automated using Terraform.

### Resources Created
- S3 bucket
- CloudFront distribution
- API Gateway
- Lambda function
- DynamoDB table

### How to Deploy
```bash
cd terraform
terraform init
terraform plan
terraform apply
```

---

## What I Learned
- How serverless architectures work
- How APIs connect frontend and backend
- How to use Lambda functions
- How to manage IAM permissions
- Debugging real-world cloud issues

---

## Future Improvements
- Add authentication (Cognito)
- Add validation
- Add logging (CloudWatch)
- Add CI/CD pipeline

---

## Author
Nahuel Egidi
