---
title : "Tạo Lambda Function lưu lịch sử"
date: "2025-08-12"
weight : 6
chapter : false
pre : " <b> 5.1 </b> "
---

> **Mục tiêu**: Tạo Lambda function sử dụng Python để lưu lịch sử dự đoán vào DynamoDB.

---

## 1. Tạo Lambda Function mới

- Vào AWS Console → Lambda

    ![AWS Search Lambda](/images/5.lambda-api-setup/5.1.create-lambda-save-history/create-lambda-save-history-1.png)  

    *Hình 1: Tìm kiếm và truy cập dịch vụ Lambda trong AWS Console.*

- Chọn tab **Functions** → nhấn nút **Create function**.  

    ![Create new Function](/images/5.lambda-api-setup/5.1.create-lambda-save-history/create-lambda-save-history-2.png)    

    *Hình 2: Bắt đầu tạo function lưu lịch sử.*

- Chọn **Author from scratch**.  
- **Function name**: `SavePredictionHistory`  
- **Runtime**: Chọn **Python 3.13** hoặc phiên bản gần nhất.  
- Nhấn **Create function** để tạo Lambda mới.

    ![Set up attribute](/images/5.lambda-api-setup/5.1.create-lambda-save-history/create-lambda-save-history-3.png)  

    *Hình 3: Thiết lập thông tin cho Lambda lưu lịch sử.*

---

## 2. Thiết lập function cho Lambda

- Sau đó màn hình sẽ chuyển qua để chúng ta thiết lập function.

    ![Lambda screen](/images/5.lambda-api-setup/5.1.create-lambda-save-history/create-lambda-save-history-4.png)  

    *Hình 4: Màn hình để thiết lập function.*

- Các bạn quay lại project tại đường dẫn `src/lambda/lambda_history.py`, các bạn tiến hành sao chép toàn bộ.

    ![Copy function](/images/5.lambda-api-setup/5.1.create-lambda-save-history/create-lambda-save-history-5.png)  

    *Hình 5: Thiết lập thông tin cho Lambda lưu lịch sử.*

- Quay lại console, tại tab Code sẽ có 1 màn hình giống của VS Code.
- Các bạn dán toàn bộ code vào trong, sau đó nhấn deploy

    ![Copy function](/images/5.lambda-api-setup/5.1.create-lambda-save-history/create-lambda-save-history-6.png)  

    *Hình 6: Thiết lập funtion để deploy.*

---

## 3. Thiết lập IAM Role cho Lambda

- Vào AWS Console → IAM

    ![AWS Search IAM](/images/5.lambda-api-setup/5.1.create-lambda-save-history/create-lambda-save-history-7.png)  

    *Hình 7: Tìm kiếm và truy cập dịch vụ IAM trong AWS Console.*

- Chọn tab **Access managemen** → **Roles**. Tại ô **Search**, tiến hành tìm `SavePredictionHistory`, role sẽ có tên dạng **SavePredictionHistory-role-xxxxx**, nhấn vào chọn role đó.

    ![Search IAM Role](/images/5.lambda-api-setup/5.1.create-lambda-save-history/create-lambda-save-history-8.png)  

    *Hình 8: Tìm kiếm IAM Role.*

- Tại tab **Permissions policies**, chúng ta chọn **Add permissions** bên phía bên tay phải, rồi chọn tiếp **Attach Policies**

    ![Attach Policies](/images/5.lambda-api-setup/5.1.create-lambda-save-history/create-lambda-save-history-9.png)  

    *Hình 9: Chuẩn bị thêm quyền hạn cho Lambda.*
 
- Tại tab **Other permissions policies**, tìm kiếm `AmazonDynamoDBFullAccess` và tick vào, sau đó chọn **Add permission**

    ![Attach Policies](/images/5.lambda-api-setup/5.1.create-lambda-save-history/create-lambda-save-history-9.png)  

    *Hình 10: Thêm quyền hạn cho Lambda đối với DynamoDB.*

---

> **Cũng khá là dễ mà đúng không?**  
> Nếu bạn đã hoàn thành và sẵn sàng, tiếp tục sang [Thiết lập Lambda function gọi Sagemaker Endpoint](/5-lambda-api-setup/5.2-create-lambda-call-sagemaker) nào!