---
title : "Set Up Environment"
date: "2025-08-10" 
weight : 2 
chapter : false
pre : " <b> 2.2 </b> "
---

> **Goal**: Fork & clone the project, create a virtual environment, and install required Python libraries to run the application.

---

## 1. Fork and Clone the Project

- Go to the GitHub repo:  
  [https://github.com/yourusername/your-repo](https://github.com/yourusername/your-repo)
- Click **Fork** to create a copy under your own GitHub account.
- Clone it to your machine:
```bash
git clone https://github.com/<your-username>/Serverless-ML-Inference-with-Lambda-and-SageMaker.git
cd <your-repo>
code .
```

---

## 2. Create and Activate Virtual Environment

- Create Virtual Environment:
```bash
python -m venv .venv
```

- And then activate it:
  - Windows:
  ```bash
  .venv\Scripts\activate
  ```

  - macOS / Linux:
  ```bash
  source .venv/bin/activate
  ```
> If successful, you’ll see the environment name (e.g., *.venv*) at the beginning of the terminal line.

![Activate venv](/images/2.prerequisite/2.2.set-up-environment/set-up-environment-1.png)

*Hình 1: Check the virtual environment if it activated.*

---

## 3. Install Required Libraries

- Quick install these required libraries:  
```bash
pip install boto3 sagemaker torch torchvision pillow
```
> Note:
> - If you plan to train models locally, ensure gcc or the corresponding build tools are installed for your OS.
> - torch installation might take a few minutes depending on your internet speed.
---

> **Seem easy right!?**  
> Let’s move to [Quick set up Sagemaker AI](/3-quick-create-sagemaker-AI/) to start interacting with AWS! 🚀