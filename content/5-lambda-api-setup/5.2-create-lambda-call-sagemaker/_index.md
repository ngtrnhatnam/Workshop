---
title : "Create Lambda Function call SageMaker Endpoint"
date: "2025-08-12"
weight : 2
chapter : false
pre : " <b> 5.2 </b> "
---

> **Goal**: Create a Lambda function using Python to save prediction history into DynamoDB.

---

## 1. Create a New Lambda Function

- Go to AWS Console → Lambda

    ![AWS Search Lambda](/Workshop/images/5.lambda-api-setup/5.1.create-lambda-save-history/create-lambda-save-history-1.png)  

    *Figure 1: Searching and accessing Lambda service in AWS Console.*

- Click on the **Functions** tab → hit **Create function**.  

    ![Create new Function](/Workshop/images/5.lambda-api-setup/5.1.create-lambda-save-history/create-lambda-save-history-2.png)    

    *Figure 2: Starting to create the SavePredictionHistory function.*

- Choose **Author from scratch**.  
- **Function name**: `SavePredictionHistory`.
- **Runtime**: **Python 3.13**  or the latest available version.
- Click **Create function**.

    ![Set up attribute](/Workshop/images/5.lambda-api-setup/5.1.create-lambda-save-history/create-lambda-save-history-3.png)  

    *Figure 3: Setting up Lambda function details.*

---

## 2. Configure the Lambda Function Code

- After creation, the console will navigate you to the function configuration screen

    ![Lambda screen](/Workshop/images/5.lambda-api-setup/5.1.create-lambda-save-history/create-lambda-save-history-4.png)  

    *Figure 4: Lambda function configuration screen.*

-Open your project folder and locate the code at `src/lambda/lambda_history.py`. Copy all the code inside.

    ![Copy function](/Workshop/images/5.lambda-api-setup/5.1.create-lambda-save-history/create-lambda-save-history-5.png)  

    *Figure 5: Copying the Lambda function code.*

- Return to the AWS Console under the Code tab (which looks like VS Code)

- Paste the copied code, then click Deploy

    ![Copy function](/Workshop/images/5.lambda-api-setup/5.1.create-lambda-save-history/create-lambda-save-history-6.png)  

    *Figure 6: Deploying the Lambda function.*

---

## 3. Set Up IAM Role for Lambda

- Go to AWS Console → IAM

    ![AWS Search IAM](/Workshop/images/5.lambda-api-setup/5.1.create-lambda-save-history/create-lambda-save-history-7.png)  

    *Figure 7: Searching and accessing IAM service.*

- Click on **Access managemen** → **Roles**, then search for `SavePredictionHistory` role. It will look like **SavePredictionHistory-role-xxxxx**. Click it.

    ![Search IAM Role](/Workshop/images/5.lambda-api-setup/5.1.create-lambda-save-history/create-lambda-save-history-8.png)  

    *Figure 8: Searching for the IAM Role.*

- In the **Permissions policies**, click **Add permissions** on the right side, then choose **Attach Policies**.

    ![Attach Policies](/Workshop/images/5.lambda-api-setup/5.1.create-lambda-save-history/create-lambda-save-history-9.png)  

    *Figure 9: Adding permissions for Lambda.*
 
- Search for `AmazonDynamoDBFullAccess`, check the box, and click **Add permissions**

    ![Attach Policies](/Workshop/images/5.lambda-api-setup/5.1.create-lambda-save-history/create-lambda-save-history-9.png)  

    *Figure 10: Adding DynamoDB access permission to Lambda.*

- Continue by selecting **Add permissions**  on the right-hand side, then choose **Create Inline Policy**.
- Next, in the **Policy Editor**, switch to the **JSON**.

    ![Attach Policies](/Workshop/images/5.lambda-api-setup/5.2.create-lambda-call-sagemaker/create-lambda-call-sagemaker-11.png)  

    *Figure 11: Adding additional permissions to Lambda.*

- Paste the following code into the editor, then click **Next**:

    ```json
    {
        "Version": "2012-10-17",
        "Statement": [
            {
                "Sid": "VisualEditor0",
                "Effect": "Allow",
                "Action": "sagemaker:InvokeEndpoint",
                "Resource": "*"
            }
        ]
    }
    ```

    ![Attach Policies](/Workshop/images/5.lambda-api-setup/5.2.create-lambda-call-sagemaker/create-lambda-call-sagemaker-12.png)  

    *Figure 12: Adding InvokeEndpoint permission for Lambda.*

    - In the **Policy name** field, enter `Invoke-endpoint`, and finally click **Create Policy**

    ![Finish Attach Policies](/Workshop/images/5.lambda-api-setup/5.2.create-lambda-call-sagemaker/create-lambda-call-sagemaker-12.png)  

    *Figure 13: Completing permission setup for Lambda.*

---

> **Pretty easy, right?**  
> If you’ve completed this step and feel ready, let’s move on to [Create API Gateway](/5-lambda-api-setup/5.3-create-api-gateway)!