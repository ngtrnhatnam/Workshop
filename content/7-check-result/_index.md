---
title : "Check the Result"
date: "2025-08-12"
weight : 7
chapter : false
pre : " <b> 7 </b> "
---

> **Goal**: Verify that the entire system (Web UI → API Gateway → Lambda → SageMaker → DynamoDB) works smoothly.

---

## 1. Open the Web Interface

- Go back to your project in VS Code.
- Locate the **main.html** file.
- Right-click on it and choose **Open with Live Server** (in VS Code).

  ![Open with live server](/images/7.check/check-1.png)

  *Figure 1: Opening the web interface via Live Server.*

---

## 2. Upload an Image for Prediction

- On the web interface, click **Choose File** to select an image from your computer (dog or cat).
- The image will appear in the preview box below.
- Click the **Classify** button to send the image to the system.

  ![Upload image](/images/7.check/check-2.png)

  *Figure 2: Uploading an image for testing.*

---

## 3. Check the Prediction Result

- Once the API processes the image, the result will appear in the **Prediction Result** area.
- If the system is connected correctly, you will see information such as:  
  - Predicted label (`Cat` or `Dog`)  

  ![Prediction result](/images/7.check/check-3.png)

  *Figure 3: Displaying the prediction result.*

---

## 4. Check the Prediction History

- Scroll down to the **Recent Prediction History** section.
- The list shows the most recent predictions stored in **DynamoDB**.

  ![Prediction history](/images/7.check/check-4.png)

  *Figure 4: Prediction history from DynamoDB.*

---

## 5. Debugging if You Encounter Errors

- If **no result appears**: Check the browser **Console** (F12 → Console tab) for API fetch errors.
- If a CORS error occurs: Make sure **API Gateway → CORS** is enabled for both **OPTIONS** and **POST** methods.
- If you get a permission error: Verify that the Lambda's **IAM Role** has `sagemaker:InvokeEndpoint` and `dynamodb:PutItem` permissions.

> All done!
> Now you can test with different images and see the results in real time. Next, head over to the [Clean up resources section](/8-cleanup/) to remove unused resources and avoid incurring charges.