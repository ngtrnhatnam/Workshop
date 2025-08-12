---
title : "Dọn Dẹp Tài Nguyên"
date: "2025-08-12"
weight : 8
chapter : false
pre : " <b> 8 </b> "
---

> **Mục tiêu**: Xóa toàn bộ tài nguyên AWS đã tạo để tránh phát sinh chi phí ngoài ý muốn.

---

## 1. Xóa endpoint trên SageMaker

### Xóa Endpoint

- Mở **AWS Console** → tìm **Amazon SageMaker**.
- Ở menu bên trái, chọn **Inference → Endpoints**.

    ![Delete Endpoint](/images/8.clean/clean-1.png)

    *Ảnh 1: Truy cập trang Endpoint.*

- Chọn endpoint của bạn (có dạng: `dogcat-endpoint-xxxxxxxx`) và nhấn vào **Delete**.
- Nhấn xác nhận

    ![Delete Endpoint](/images/8.clean/clean-2.png)

    *Ảnh 2: Xóa Endpoint.*

### Xóa Endpoint Configurations

- Tiếp tục ở menu bên trái, chọn **Inference → Endpoints configurations**.

    ![Delete Endpoint Conf](/images/8.clean/clean-3.png)

    *Ảnh 3: Truy cập trang Endpoint Configurations.*

- Chọn endpoint configurations của bạn (có dạng: `dogcat-endpoint-xxxxxxxx`) và nhấn vào **Delete**.
- Nhấn xác nhận

    ![Delete Endpoint Conf](/images/8.clean/clean-4.png)

    *Ảnh 4: Xóa Endpoint Configurations.*

### Xóa Model

- Vẫn trong **SageMaker**, chọn **Inference → Models**.
- Chọn model cần xóa, chọn **Action** → **Delete** 

    ![Delete Model](/images/8.clean/clean-4.1.png)

    *Ảnh 4.1: Truy cập trang Model.*

- Nhấn **Delete** để xác nhận xóa

    ![Delete Model](/images/8.clean/clean-4.2.png)

    *Ảnh 4.2: Xóa Model.*

---

## 2. Xóa dịch vụ Lambda

- Mở **AWS Console** → tìm **Lambda**.
- Chọn 2 function đã tạo, bao gồm `InvokeModelLambda`, `SaveHistoryLambda`, chọn **Action** →  **Delete**.

    ![Delete Lambda](/images/8.clean/clean-5.png)

    *Ảnh 5: Truy cập trang Lambda.*

- Gõ `confirm` vào ô, sau đó chọn Delete.

    ![Delete Lambda](/images/8.clean/clean-6.png)

    *Ảnh 6: Xóa Lambda.*

---

## 3. Xóa bảng DynamoDB

- Đi đến dịch vụ **DynamoDB**.
- Chọn **Tables** bên tay trái, tick vào bảng đã tạo cần xóa `PredictionHistory`, chọn **Delete**

    ![Delete Lambda](/images/8.clean/clean-7.png)

    *Ảnh 7: Truy cập trang DynamoDB Tables.*

-  Gõ xác nhận `confirm` và chọn **delete**. 

    ![Delete Lambda](/images/8.clean/clean-8.png)

    *Ảnh 8: Xóa bảng PredictionHistory.*

---

## 4. Xóa API Gateway

- Đi đến dịch vụ **API Gateway**, chọn **APIs** bên tay trái.
- Chọn API Gateway đã tạo `MLInferenceAPI` và chọn **Delete**.

    ![Delete API Gateway](/images/8.clean/clean-9.png)

    *Ảnh 9: Truy cập trang API Gateway.*

-  Gõ xác nhận `confirm` và chọn **delete**. 

    ![Delete API Gateway](/images/8.clean/clean-10.png)

    *Ảnh 10: Xóa API MLInferenceAPI.*

---

## 5. Xóa IAM Roles (Không ưu tiên nhưng vẫn nên xóa)

- Đi đến dịch vụ **IAM**, tại **Access Management**, chọn **Roles**
- Tìm và click các IAM roles như `InvokeModelLambda-role-xxx`, `SavePredictionHistory-role-xxx`, `AmazonSageMaker-ExecutionRole-xxx`.

    ![Delete IAM Roles](/images/8.clean/clean-11.png)

    *Ảnh 11: Truy cập trang IAM.*

> Tips: Click 2 lần vào **Last activity** sẽ cực kỳ dễ tìm.

-  Gõ xác nhận `delete` và chọn **delete**. 

    ![Delete API Gateway](/images/8.clean/clean-12.png)

    *Ảnh 12: Xóa API MLInferenceAPI.*

- **Chú ý:** Hãy chắc chắn rằng không còn dịch vụ nào còn được sử dụng gắn với các IAM role này.

---

## 6. Xóa S3 Bucket

- **S3 Bucket** được Sagemaker tự động tạo để lưu model.
- Truy cập trang **S3**, chọn bucket cần xóa → **Delete**

    ![Delete S3 Bucket](/images/8.clean/clean-13.png)

    *Ảnh 13: Truy cập trang S3.*

- Lúc này sẽ có 1 dòng cảnh báo **This bucket is not empty**, các bạn chọn **Empty bucket** để tự động dọn bucket.

    ![Delete S3 Bucket](/images/8.clean/clean-14.png)

    *Ảnh 14: Dọn sạch bucket.*

- Sau đó các bạn gõ xác nhận `permanently delete`, sau đó nhấn **Empty** để hoàn tất xóa S3 bucket.

--

> ✅ **Xong nè!** Giờ bạn đã dọn sạch tài nguyên để tránh phát sinh chi phí không cần thiết rồi đó.