---
title : "Designing the Web Interface"
date: "2025-08-12"
weight : 6
chapter : false
pre : " <b> 6. </b> "
---

> **Objective**: Build a simple, user-friendly web interface that allows users to upload images for prediction.

---

## 1. Overview

The web interface is designed to be simple and easy to use, focusing on the main features: uploading an image and displaying prediction results clearly.

- Supports uploading images directly from the user’s device.
- Displays the uploaded image along with the prediction result below it.
- Includes a “Predict” button to call the backend API.
- Responsive design for both desktop and mobile devices.

---

## 2. Technologies Used

- **HTML5** for page structure.
- **CSS3** for clean and user-friendly styling.
- **Vanilla JavaScript** to handle interactions such as image upload, API calls, and result display.

---

## 3. Main Page Structure

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <title>Cat vs Dog Classifier</title>
    <link rel="stylesheet" href="style.css">
  </head>
  <body>
    <h1>Cat or Dog?</h1>
    <h2>Upload an image to classify</h2>
    <input type="file" id="imageInput" accept="image/*" />
    
    <div id="previewBox" style="display:none;">
      <h3>Your selected image:</h3>
      <img id="previewImage" src="" alt="Preview">
    </div>

    <button onclick="sendImage()">Predict</button>
    <p id="result"></p>

    <div id="history">
      <h2>Recent Prediction History</h2>
      <ul id="historyList"></ul>
    </div>

    <script src="script.js"></script>
  </body>
</html>
```

## 4. Notes
- The “Predict” button will call the backend API via JavaScript fetch.
- The selected image is previewed immediately so the user can confirm it’s correct.
- Prediction results are displayed inside the #result element.
- Simple and clean design for easy maintenance and future upgrades.

## 5. Updating API Endpoints in JavaScript

- Go to AWS Console → API Gateway

  ![Find API Gateway](/Workshop/images/6.web/web-1.png)  

  *Figure 1: Search for API Gateway in the console.*

- Navigate to the **Function** tab → select the `InvokeModelLambda` function

  ![Access InvokeModelLambda](/Workshop/images/6.web/web-2.png)  

  *Figure 2: Accessing InvokeModelLambda.*

- Open the Configuration tab → Trigger. Under API Endpoint, copy the full URL. The format is: `https://xxxx.execute-api.<your-region>.amazonaws.com/prod/predict`.

  ![Copy API](/Workshop/images/6.web/web-3.png)  

  *Figure 3: Copying the API endpoint.*

- Go back to your project, open the `script.js` file. Press **Ctrl + F**, search for `Change predict`. and replace the URL inside the quotes **" "** with the copied API endpoint.

  ![Copy API](/Workshop/images/6.web/web-4.png)  

  *Figure 4: Replacing the API endpoint.*

- Repeat the same process for `SavePredictionHistory`: But in project, search for `Change history` in `script.js` and replace the URL inside the quotes " ".

-Save the file **Ctrl + S**.

> **Ready?**  
> Next, let’s move on to [Check the Results](/7-check-result/) to verify the entire system is working properly!