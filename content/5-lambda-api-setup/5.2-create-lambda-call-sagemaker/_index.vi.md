---
title : "Tạo Lambda Function gọi Sagemaker Endpoint"
date: "2025-08-12"
weight : 2
chapter : false
pre : " <b> 5.2 </b> "
---

> **Mục tiêu**: Tạo Lambda function sử dụng Python để lưu lịch sử dự đoán vào DynamoDB.

---

## 1. Tạo Lambda Function mới

- Vào AWS Console → Lambda

    ![AWS Search Lambda](/Workshop/images/5.lambda-api-setup/5.2.create-lambda-call-sagemaker/create-lambda-call-sagemaker-1.png)  

    *Hình 1: Tìm kiếm và truy cập dịch vụ Lambda trong AWS Console.*

- Chọn tab **Functions** → nhấn nút **Create function**.  

    ![Create new Function](/Workshop/images/5.lambda-api-setup/5.2.create-lambda-call-sagemaker/create-lambda-call-sagemaker-2.png)    

    *Hình 2: Bắt đầu tạo function gọi endpoint.*

- Chọn **Author from scratch**.  
- **Function name**: `InvokeModelLambda`  
- **Runtime**: Chọn **Python 3.13** hoặc phiên bản gần nhất.  
- Nhấn **Create function** để tạo Lambda mới.

    ![Set up attribute](/Workshop/images/5.lambda-api-setup/5.2.create-lambda-call-sagemaker/create-lambda-call-sagemaker-3.png)  

    *Hình 3: Thiết lập thông tin cho Lambda gọi endpoint.*

---

## 2. Thiết lập function cho Lambda

- Sau đó màn hình sẽ chuyển qua để chúng ta thiết lập function.

    ![Lambda screen](/Workshop/images/5.lambda-api-setup/5.2.create-lambda-call-sagemaker/create-lambda-call-sagemaker-4.png)  

    *Hình 4: Màn hình để thiết lập function.*

- Các bạn quay lại project tại đường dẫn `src/lambda/lambda_function.py`, các bạn tiến hành sao chép toàn bộ.

    ![Copy function](/Workshop/images/5.lambda-api-setup/5.2.create-lambda-call-sagemaker/create-lambda-call-sagemaker-5.png)  

    *Hình 5: Thiết lập thông tin cho Lambda lưu lịch sử.*

- Quay lại console, tại tab Code sẽ có 1 màn hình giống của VS Code.
- Các bạn dán toàn bộ code vào trong, sau đó nhấn deploy

    ![Copy function](/Workshop/images/5.lambda-api-setup/5.2.create-lambda-call-sagemaker/create-lambda-call-sagemaker-6.png)  

    *Hình 6: Thiết lập funtion để deploy.*

---

## 3. Thiết lập IAM Role cho Lambda

- Vào AWS Console → IAM

    ![AWS Search IAM](/Workshop/images/5.lambda-api-setup/5.2.create-lambda-call-sagemaker/create-lambda-call-sagemaker-7.png)  

    *Hình 7: Tìm kiếm và truy cập dịch vụ IAM trong AWS Console.*

- Chọn tab **Access managemen** → **Roles**. Tại ô **Search**, tiến hành tìm `InvokeModelLambda`, role sẽ có tên dạng **InvokeModelLambda-role-xxxxx**, nhấn vào chọn role đó.

    ![Search IAM Role](/Workshop/images/5.lambda-api-setup/5.2.create-lambda-call-sagemaker/create-lambda-call-sagemaker-8.png)  

    *Hình 8: Tìm kiếm IAM Role.*

- Tại tab **Permissions policies**, chúng ta chọn **Add permissions** bên phía bên tay phải, rồi chọn tiếp **Attach Policies**

    ![Attach Policies](/Workshop/images/5.lambda-api-setup/5.2.create-lambda-call-sagemaker/create-lambda-call-sagemaker-9.png)  

    *Hình 9: Chuẩn bị thêm quyền hạn cho Lambda.*
 
- Tại tab **Other permissions policies**, tìm kiếm `AmazonDynamoDBFullAccess` và tick vào, sau đó chọn **Add permission**

    ![Attach Policies](/Workshop/images/5.lambda-api-setup/5.2.create-lambda-call-sagemaker/create-lambda-call-sagemaker-10.png)  

    *Hình 10: Thêm quyền hạn cho Lambda đối với DynamoDB.*

- Tiếp tục chọn **Add permissions** bên phía bên tay phải, rồi chọn tiếp **Create Inline Policy**.
- Sau đó chọn **JSON** tại **Policy Editor**

    ![Attach Policies](/Workshop/images/5.lambda-api-setup/5.2.create-lambda-call-sagemaker/create-lambda-call-sagemaker-11.png)  

    *Hình 11: Tiếp tục thêm quyền hạn cho Lambda.*

- Rồi dán đoạn này vào, sau đó chọn **Next**:

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

    *Hình 12: Tiếp tục thêm quyền hạn cho Lambda.*

    - Tại **Policy name**, đặt tên là `Invoke-endpoint`, cuối cùng chọn **Create Policy**

    ![Finish Attach Policies](/Workshop/images/5.lambda-api-setup/5.2.create-lambda-call-sagemaker/create-lambda-call-sagemaker-12.png)  

    *Hình 13: Hoàn tất thêm quyền hạn cho Lambda.*
    
---

> **Cũng khá là dễ mà đúng không?**  
> Nếu bạn đã hoàn thành và sẵn sàng, tiếp tục sang [Thiết lập API Gateway](/5-lambda-api-setup/5.3-create-api-gateway) nào!