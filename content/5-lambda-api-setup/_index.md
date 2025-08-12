---
title : "Introduction to Lambda and API Gateway"
date: "2025-08-12"
weight : 5
chapter : false
pre : " <b> 5. </b> "
---

> **Objective**: Understand the role of AWS Lambda and API Gateway in the serverless image recognition application.

---

## What is AWS Lambda?

AWS Lambda is AWS’s serverless compute service that lets you run code without managing servers. Lambda automatically scales and charges you only for the compute time you consume.

Lambda’s role in this workshop:
- Handle user requests (image upload, prediction calls).
- Store prediction history into DynamoDB.
- Call the Machine Learning model on SageMaker to return prediction results.

---

## What is API Gateway?

API Gateway is AWS’s API management service that helps you create, secure, monitor, and operate RESTful or WebSocket APIs.

Its role in the workshop:
- Provide a RESTful endpoint for the frontend to send images and receive prediction results.
- Connect to Lambda functions that handle backend logic.
- Manage security and access permissions for the API.

---

## Overall Architecture

Frontend → API Gateway → Lambda (gọi SageMaker) → SageMaker Endpoint → Lambda (lưu lịch sử) → DynamoDB

---

## Main Steps  

| **Step** | **Description** |
|----------|--------------|
| 5.1 | [Create Lambda Function to save history](/5-lambda-api-setup/5.1-create-lambda-save-history/) |
| 5.2 | [Create Lambda Function to call SageMaker endpoint](/5-lambda-api-setup/5.2-create-lambda-call-sagemaker/) |
| 5.3 | [Create API Gateways](/5-lambda-api-setup/5.3-create-api-gateway/) |

---

> **Ready?**  
> Next, we’ll create the Lambda function to save history in [Create Lambda Function to save history](/5-lambda-api-setup/5.1-create-lambda-save-history/)!