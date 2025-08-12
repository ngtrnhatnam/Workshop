---
title : "Upload a Trained Model"
date: "2025-08-11"
weight : 2
chapter : false
pre : " <b> 3.2 </b> "
---

> **Objective**: Guide on updating IAM Role and uploading a pre-trained model to SageMaker using Python script.


---

## 1. Prepare the model

- In the project folder under `assets/models`, you are provided with two files:  
  - `inference.py` (inference script)  
  - `mobilenetv3_small.pt` (pre-trained model file)  

   ![Model file](/Workshop/images/3.quick-create-sagemaker-AI/3.2.upload-trained-model/upload-trained-model-1.png)  

   *Figure 1: The two provided files.*

- Package these two files into a `model.tar.gz` archive so SageMaker can use them, then go back to the root directory for convenience:

  ```bash
  cd assets/models
  tar -czvf model.tar.gz mobilenetv3_small.pt inference.py
  cd ../..
  ```

  ![After packing](/Workshop/images/3.quick-create-sagemaker-AI/3.2.upload-trained-model/upload-trained-model-2.png)  

   *Figure 2: After packing the files and returning to the root folder.*

---

## 2. Get the ARN of the auto-created IAM Role

- Go to AWS Console → IAM → Roles.

  ![AWS Search SageMaker](/Workshop/images/3.quick-create-sagemaker-AI/3.2.upload-trained-model/upload-trained-model-3.png)  

  *Figure 3: Search and access SageMaker service in AWS Console.*

- Find the auto-created SageMaker Role with name like: `AmazonSageMaker-ExecutionPolicy-xxxxxxx`.  

  ![AWS Search SageMaker](/Workshop/images/3.quick-create-sagemaker-AI/3.2.upload-trained-model/upload-trained-model-4.png)  

  *Figure 4: Search and find the SageMaker Role.*

- Copy the ARN of this Role..

  ![AWS Search SageMaker](/Workshop/images/3.quick-create-sagemaker-AI/3.2.upload-trained-model/upload-trained-model-5.png)  

  *Figure 5: Copy the ARN of the SageMaker Role.*

---

## 3. Update IAM Role trong script deploy

- Update IAM Role in deploy script `src/sagemaker/deploy_model.py` in project. 
- Press `Ctrl + F`, and search for `role = ""`.  

  ![Find role location](/Workshop/images/3.quick-create-sagemaker-AI/3.2.upload-trained-model/upload-trained-model-6.png)  

  *Figure 6: Find where to update the ARN.*

- Replace the role value inside the quotes with the ARN you copied..

  ![Change ARN](/Workshop/images/3.quick-create-sagemaker-AI/3.2.upload-trained-model/upload-trained-model-7.png)  

  *Figure 7: Replace with the ARN copied earlier.*

---

## 4. Run the deploy script

- Open your terminal and run:

  ```python
  python src/sagemaker/deploy_model.py
  ```

- The script will upload `model.tar.gz` to S3 and deploy the SageMaker Endpoint.

---

## 5. Update the endpoint in the deploy script

- Open the file located at `src/lambda/lambda_function.py` in project. 
- Press `Ctrl + F`, and search for `EndpointName=`.  

  ![Find role location](/Workshop/images/3.quick-create-sagemaker-AI/3.2.upload-trained-model/upload-trained-model-9.png)  

  *Figure 9: Search for the location where the Endpoint needs to be updated.*

- Replace the value inside the single quotes `' '` with the Endpoint you copied earlier.

  ![Change ARN](/Workshop/images/3.quick-create-sagemaker-AI/3.2.upload-trained-model/upload-trained-model-10.png)  

  *Figure 10: Replace the Endpoint copied in the step shown in Figure 8.*

- Finally, press **Ctrl + S** to save the file.

---


> **All done?**  
> Now you can move on to [Create DynamoDB Table](/4-create-dynamoDB/)!