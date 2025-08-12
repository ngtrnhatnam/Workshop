---
title : "Clean Up Resources"
date: "2025-08-12"
weight : 8
chapter : false
pre : " <b> 8 </b> "
---

> **Goal**: Delete all AWS resources created during the tutorial to avoid unnecessary charges.

---

## 1. Delete Endpoint on SageMaker

### Delete Endpoint

- Open **AWS Console** → search for **Amazon SageMaker**.
- In the left menu, choose **Inference → Endpoints**.

    ![Delete Endpoint](/images/8.clean/clean-1.png)

    *Image 1: Go to Endpoint page.*

- Select your endpoint (e.g., `dogcat-endpoint-xxxxxxxx`) and click **Delete**.
- Confirm the deletion.

    ![Delete Endpoint](/images/8.clean/clean-2.png)

    *Image 2: Delete Endpoint.*

### Delete Endpoint Configurations

- In the left menu, choose **Inference → Endpoints configurations**.

    ![Delete Endpoint Conf](/images/8.clean/clean-3.png)

    *Image 3: Go to Endpoint Configurations page.*

- Select your endpoint configuration (e.g., `dogcat-endpoint-xxxxxxxx`) and click **Delete**.
- Confirm the deletion.

    ![Delete Endpoint Conf](/images/8.clean/clean-4.png)

    *Image 4: Delete Endpoint Configurations.*

### Delete Model

- Still in **SageMaker**, choose **Inference → Models**.
- Select the model, click **Action** → **Delete**.

    ![Delete Model](/images/8.clean/clean-4.1.png)

    *Image 4.1: Go to Model page.*

- Click **Delete** to confirm.

    ![Delete Model](/images/8.clean/clean-4.2.png)

    *Image 4.2: Delete Model.*

---

## 2. Delete Lambda Functions

- Open **AWS Console** → search for **Lambda**.
- Select the 2 functions you created, `InvokeModelLambda` and `SaveHistoryLambda`, then choose **Action** → **Delete**.

    ![Delete Lambda](/images/8.clean/clean-5.png)

    *Image 5: Go to Lambda page.*

- Type `confirm` in the input box, then click **Delete**.

    ![Delete Lambda](/images/8.clean/clean-6.png)

    *Image 6: Delete Lambda.*

---

## 3. Delete DynamoDB Table

- Go to **DynamoDB** service.
- In the left menu, select **Tables**, tick the table you created `PredictionHistory`, and choose **Delete**.

    ![Delete DynamoDB](/images/8.clean/clean-7.png)

    *Image 7: Go to DynamoDB Tables page.*

- Type `confirm` and click **Delete**.

    ![Delete DynamoDB](/images/8.clean/clean-8.png)

    *Image 8: Delete PredictionHistory table.*

---

## 4. Delete API Gateway

- Go to **API Gateway** service, choose **APIs** in the left menu.
- Select the API Gateway you created `MLInferenceAPI` and click **Delete**.

    ![Delete API Gateway](/images/8.clean/clean-9.png)

    *Image 9: Go to API Gateway page.*

- Type `confirm` and click **Delete**.

    ![Delete API Gateway](/images/8.clean/clean-10.png)

    *Image 10: Delete MLInferenceAPI.*

---

## 5. Delete IAM Roles (Optional but recommended)

- Go to **IAM** service, under **Access Management**, choose **Roles**.
- Search and select IAM roles like `InvokeModelLambda-role-xxx`, `SavePredictionHistory-role-xxx`, `AmazonSageMaker-ExecutionRole-xxx`.

    ![Delete IAM Roles](/images/8.clean/clean-11.png)

    *Image 11: Go to IAM page.*

> Tip: Double-click **Last activity** to sort and find inactive roles quickly.

- Type `delete` and click **Delete**.

    ![Delete IAM Roles](/images/8.clean/clean-12.png)

    *Image 12: Delete IAM Roles.*

- **Note:** Make sure no other AWS services are still using these IAM roles.

---

## 6. Delete S3 Bucket

- **S3 Buckets** are automatically created by SageMaker to store models.
- Go to **S3**, select the bucket to delete → **Delete**.

    ![Delete S3 Bucket](/images/8.clean/clean-13.png)

    *Image 13: Go to S3 page.*

- You will see the warning **This bucket is not empty**. Click **Empty bucket** to remove all objects.

    ![Delete S3 Bucket](/images/8.clean/clean-14.png)

    *Image 14: Empty bucket.*

- Then type `permanently delete` and click **Empty** to completely delete the S3 bucket.

---

✅ **Done!** All AWS resources have been removed, preventing any unwanted charges.