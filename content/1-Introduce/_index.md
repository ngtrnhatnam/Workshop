---
title : "Introduction"
date: "2025-08-10" 
weight : 1 
chapter : false
pre : " <b> 1. </b> "
---

> **Explore the power of real-time AI in the cloud!**  
> This workshop will guide you step-by-step to build a **serverless image recognition web application**, using AWS services to process, predict, and store image-based data in a **fast**, **secure**, and **cost-effective** way.

In the era of AI, building real-time applications that are scalable, secure, and easy to maintain is a top priority. The workshop **"Deploying a Serverless Real-Time Image Recognition Application with Lambda and Sagemaker"** will help you integrate a pre-trained Machine Learning model into a web interface, enabling real-time predictions without managing servers.

The application supports:
- **Uploading an image** directly from your browser.
- **Instant predictions** from a deployed ML model.
- **Saving prediction history** to DynamoDB for tracking.
- **Simple and responsive UI** for smooth interaction.
- **Serverless architecture** — no need for server maintenance.

---

## Benefits of Serverless Applications

The AWS serverless stack brings multiple benefits for AI-powered applications:

### 1. Real-Time Processing
AWS Lambda executes predictions immediately upon receiving an image, ensuring low-latency responses.

> **Example**: A user uploads an image of a handwritten digit, and the system instantly returns the predicted digit.

### 2. Automatic Scaling
Lambda scales automatically based on demand — whether 1 or 1,000 users upload images simultaneously.

### 3. Secure Data Handling
API Gateway works with **IAM roles** and resource policies to ensure:
- Only authorized calls reach the Lambda functions.
- DynamoDB write/read access is strictly role-based.

> **Example**: The prediction Lambda can only write to the `PredictionHistory` table, not delete data.

### 4. Cost Efficiency
You only pay for what you use:
- **Lambda**: Charged per execution time.
- **DynamoDB**: Pay-per-request pricing.
- **S3**: Pay for stored static assets.

### 5. Fast Access & Smooth Experience
The web interface (HTML, CSS, JS) will run locally using VS Code’s Live Server.
This approach allows you to develop, test, and modify the UI quickly without deploying static files to S3.

---

## Workshop Goals

By completing this workshop, you will learn how to:

| **Goal** | **Technology** | **Outcome** |
|----------|----------------|-------------|
| Design a simple, responsive UI | HTML, CSS | Easy-to-use image upload interface |
| Build and secure APIs | API Gateway | Endpoints for image submission & prediction |
| Deploy ML inference | AWS Lambda, SageMaker Endpoint | Real-time predictions from a pre-trained model |
| Store results | DynamoDB | Persistent prediction history |
| Distribute globally | S3, CloudFront | Fast, worldwide content delivery |
| Monitor and debug | CloudWatch | Insight into system performance |

---

## Start Your Journey!

By the end of this workshop, you will have:
1. A **working real-time image recognition app**.
2. Hands-on experience connecting AWS services into a serverless workflow.
3. Skills to deploy AI-powered apps without managing servers.

> **Ready to start?**  
> Move on to [Preparation Steps](2-preparation-steps/) to set up your AWS environment!