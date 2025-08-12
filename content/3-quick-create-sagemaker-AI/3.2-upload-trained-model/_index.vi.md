---
title : "Upload mô hình đã huấn luyện"
date: "2025-08-11"
weight : 2
chapter : false
pre : " <b> 3.2 </b> "
---

> **Mục tiêu**: Hướng dẫn cách upload mô hình Machine Learning đã được huấn luyện sẵn lên SageMaker để deploy làm Endpoint.

---

## 1. Chuẩn bị mô hình 

- Tại thư mục dự án đường dẫn `assets/models`, bạn đã được cung cấp sẵn hai file:  
  - `inference.py` (script inference)  
  - `mobilenetv3_small.pt` (file model đã huấn luyện)  

    ![Model file](/images/3.quick-create-sagemaker-AI/3.2.upload-trained-model/upload-trained-model-1.png)  

    *Hình 1: Hai file đã được cung cấp sẵn.*

- Đóng gói hai file này thành một file nén `model.tar.gz` để SageMaker có thể sử dụng, sau đó quay trở về thư mục gốc để dễ thao tác hơn:
  ```bash
  cd assets/models 
  tar -czvf model.tar.gz mobilenetv3_small.pt inference.py
  cd ../..
  ```

  ![After packing](/images/3.quick-create-sagemaker-AI/3.2.upload-trained-model/upload-trained-model-2.png)  

    *Hình 2: Kết quả sau khi đóng gói xong và quay về thư mục gốc.*

---

## 2. Lấy ARN của IAM Role do SageMaker tự động tạo

- Vào AWS Console → IAM → Roles.  

  ![AWS Search SageMaker](/images/3.quick-create-sagemaker-AI/3.2.upload-trained-model/upload-trained-model-3.png)  

  *Hình 3: Tìm kiếm và truy cập dịch vụ SageMaker trong AWS Console.*

- Tìm role tự động sinh cho SageMaker có dạng: `AmazonSageMaker-ExecutionPolicy-xxxxxxx`.  

  ![AWS Search SageMaker](/images/3.quick-create-sagemaker-AI/3.2.upload-trained-model/upload-trained-model-4.png)  

  *Hình 4: Tìm kiếm và truy cập dịch vụ SageMaker trong AWS Console.*

- Copy ARN của role này.

  ![AWS Search SageMaker](/images/3.quick-create-sagemaker-AI/3.2.upload-trained-model/upload-trained-model-5.png)  

  *Hình 5: Tìm kiếm và truy cập dịch vụ SageMaker trong AWS Console.*

---

## 3. Cập nhật IAM Role trong script deploy

- Mở file tại đường dẫn `src/sagemaker/deploy_model.py` trong dự án.  
- Nhấn `Ctrl + F`, tìm `role =`.  

  ![Find role location](/images/3.quick-create-sagemaker-AI/3.2.upload-trained-model/upload-trained-model-6.png)  

  *Hình 6: Tìm kiếm vị trí cần thay ARN.*

- Thay giá trị role bên trong nháy đôi `""` bằng ARN đã copy.

  ![Change ARN](/images/3.quick-create-sagemaker-AI/3.2.upload-trained-model/upload-trained-model-7.png)  

  *Hình 7: Thay ARN đã được sao chép tại bước của hình thứ 5.*

- Cuối cùng nhấn **Ctrl + S** để lưu.

---

## 4. Chạy script deploy model

- Mở terminal và chạy lệnh:

  ```python
  python src/sagemaker/deploy_model.py
  ```

- Script sẽ upload `model.tar.gz` lên S3 và triển khai Endpoint SageMaker. Sau khi hoàn tất sẽ được trả về thông tin Endpoint có dạng `dogcat-endpoint-xxxxx`, sao chép lại.

  ![Finish upload](/images/3.quick-create-sagemaker-AI/3.2.upload-trained-model/upload-trained-model-8.png)  

    *Hình 8: Đã upload thành công.*

---

## 5. Cập nhật endpoint trong script deploy

- Mở file tại đường dẫn `src/lambda/lambda_function.py` trong dự án.  
- Nhấn `Ctrl + F`, tìm `EndpointName=`.  

  ![Find role location](/images/3.quick-create-sagemaker-AI/3.2.upload-trained-model/upload-trained-model-9.png)  

  *Hình 9: Tìm kiếm vị trí cần thay Endpoint.*

- Thay giá trị role bên trong nháy đơn `' '` bằng Endpoint đã copy.

  ![Change ARN](/images/3.quick-create-sagemaker-AI/3.2.upload-trained-model/upload-trained-model-10.png)  

  *Hình 10: Thay Endpoint đã được sao chép tại bước của hình thứ 8.*

- Cuối cùng nhấn **Ctrl + S** để lưu.

---

> **Xong chưa nè?**  
> Tiếp theo bạn có thể chuyển sang phần [Tạo bảng DynamoDB](/4-create-dynamoDB/) nha!