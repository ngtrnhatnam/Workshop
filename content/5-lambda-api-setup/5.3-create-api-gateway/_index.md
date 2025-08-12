---
title : "Tạo Lambda Function lưu lịch sử"
date: "2025-08-12"
weight : 5
chapter : false
pre : " <b> 5.3 </b> "
---

> **Mục tiêu**: Create an API Gateway to interact with Lambda.

---

## 1. Tạo API Gateway mới

- Go to AWS Console → API Gateway.

    ![AWS Search Lambda](/images/5.lambda-api-setup/5.3.create-api-gateway/create-api-gateway-1.png)  

    *Figure 1: Searching and accessing API Gateway service in AWS Console.*

- Select the **APIs** tab → click **Create API**. 

    ![Create new API](/images/5.lambda-api-setup/5.3.create-api-gateway/create-api-gateway-2.png)  
    *Figure 2: Starting to create a new API.*

- In **HTTP API**, choose  **Build**.

    ![HTTP API](/images/5.lambda-api-setup/5.3.create-api-gateway/create-api-gateway-3.png)  
    *Figure 3: Selecting HTTP API type.*

- In Step 1, set the API name as `MLInferenceAPI`, then click **Next**.

    ![Set API name](/images/5.lambda-api-setup/5.3.create-api-gateway/create-api-gateway-4.png)  
    *Figure 4: Naming the API.*

- In Step 2, click **Next**; in Step 3, set the Stage name as `prod`, then continue with **Next**.

    ![HTTP API](/images/5.lambda-api-setup/5.3.create-api-gateway/create-api-gateway-5.png)  
    *Figure 5: Setting Stage name.*

- In Step 4, click **Create**.

    ![Set up attribute](/images/5.lambda-api-setup/5.3.create-api-gateway/create-api-gateway-6.png)  

    *Figure 6: Finishing API setup.*

---

## 2. Set up API routes

- The screen will switch to the Develop → Routes tab. Here, set up routes to attach Lambda functions later. Click **Create**.

    ![Set up routers](/images/5.lambda-api-setup/5.3.create-api-gateway/create-api-gateway-7.png)  

    *Figure 7: Creating routes.*

- Create two routes:
    - `/history`

    ![Router history](/images/5.lambda-api-setup/5.3.create-api-gateway/create-api-gateway-8.png)  

    *Figure 8: Creating /history route.*

    -  `/predict`

    ![Router predict](/images/5.lambda-api-setup/5.3.create-api-gateway/create-api-gateway-9.png)  

    *Figure 9: Creating /predict route.*

---

## Conclusion 

Now your API is ready to receive requests from the frontend!

> **Seem easy, right?**  
> If you’re done, move on to [Create Lambda function to save history](/5-lambda-api-setup/5.2-create-lambda-save-history) and continue your serverless journey! 🚀✨