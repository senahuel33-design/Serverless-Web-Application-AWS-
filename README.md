# AWS Serverless Web Application

## Overview
This project demonstrates how to build a fully serverless web application using AWS services.

Users can submit data through a web interface, which is processed by a backend API and stored in a database.

---

## Architecture
User → CloudFront → S3 → API Gateway → Lambda → DynamoDB

![Architecture](<Architecture/Serverless Web Application.png>)

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

![DynamoDB](<Screenshots/DynamoBD/Dynamo DB table.PNG>)
![Table active](<Screenshots/DynamoBD/Dynamo DB table created.PNG>)
---

### 2. Create Lambda Function

Create a Lambda function to process incoming requests and store data in DynamoDB.

- Runtime: Python 3.12
- Generates unique message IDs
- Stores user messages in DynamoDB

#### Lambda Function Created
![Lambda Function](<Lamba/Lambda function created.PNG>)

#### Lambda Function Code
![Lambda Code](<Lamba/Lambda code.PNG>)

#### IAM Permissions for DynamoDB Access
![Lambda IAM Role](<Lamba/IAM role with DynamoDB permissions.PNG>)

---

### 3. Create API Gateway
Create a REST API and connect it to the Lambda function.

![API Gateway](<Screenshots/Api/Create API Gateway.PNG>)

#### POST Route Configuration
![POST Route](<Screenshots/Api/POST Route Configuration.PNG>)

#### API Test Success
![API Test](<Screenshots/Api/API Test Success.PNG>)
---

### 4. Enable CORS
Enable CORS so the frontend can call the API.

![CORS](<Screenshots/Api/Enable CORS.PNG>)

---

### 5. Build Frontend

Create a frontend using HTML, CSS, and JavaScript to interact with the serverless backend.
The frontend uses JavaScript Fetch API to send POST requests to API Gateway.

#### Frontend Files
![Frontend Files](<Screenshots/Frontend/frontend-files-uploaded.PNG>)

#### Contact Form
![Frontend Form](<Screenshots/Frontend/Contact form.PNG>)

#### Frontend Local Test
![Frontend Local Test](<Screenshots/Frontend/Frontend Local Test.PNG>)

---

### 6. Connect Frontend to API Gateway

Connect the frontend application to API Gateway and store messages in DynamoDB.

#### API Endpoint Configuration
![API Endpoint](<Screenshots/Api/API Endpoint Configuration.PNG>)

#### Successful Message Submission
![Frontend Success](<Screenshots/Frontend/frontend-working.PNG>)

#### DynamoDB Record Created
![DynamoDB Success](<Screenshots/DynamoBD/DynamoDB Record Created.PNG>)

### 7.Frontend via CloudFront
Distribute the frontend securely via CloudFront.
![Cloudfront Distribution](<Screenshots/CloudFront/CloudFront Distribution.PNG>)
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
