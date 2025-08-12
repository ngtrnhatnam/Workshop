---
title : "Kiểm Tra Kết Quả"
date: "2025-08-12"
weight : 7
chapter : false
pre : " <b> 7. </b> "
---

> **Mục tiêu**: Xác minh toàn bộ hệ thống (Web UI → API Gateway → Lambda → SageMaker → DynamoDB) hoạt động trơn tru.

---

## 1. Mở giao diện web

- Quay lại project trên VS Code.
- Tìm file **main.html**.
- Nhấn chuột phải chọn **Open with Live Server** (trong VS Code).

  ![Open with live server](/images/7.check/check-1.png)

  *Hình 1: Mở giao diện web qua Live Server.*

---

## 2. Upload ảnh để dự đoán

- Tại giao diện web, nhấn **Choose File** để chọn ảnh từ máy (ảnh chó hoặc mèo).
- Ảnh sẽ hiển thị ở khung preview ngay bên dưới.
- Nhấn nút **Phân loại** để gửi ảnh lên hệ thống.

  ![Upload image](/images/7.check/check-2.png)

  *Hình 2: Upload ảnh kiểm tra.*

---

## 3. Kiểm tra kết quả dự đoán

- Sau khi API xử lý, kết quả sẽ hiện ở vùng **Kết quả dự đoán**.
- Nếu hệ thống kết nối đúng, bạn sẽ thấy thông tin như:  
  - Nhãn dự đoán (`Cat` hoặc `Dog`)  

  ![Prediction result](/images/7.check/check-3.png)

  *Hình 3: Kết quả dự đoán hiển thị.*

---

## 4. Kiểm tra lịch sử dự đoán

- Kéo xuống phần **Lịch sử đoán gần đây**.
- Danh sách hiển thị các dự đoán gần nhất được lưu trong **DynamoDB**.

  ![Prediction history](/images/7.check/check-4.png)

  *Hình 4: Lịch sử dự đoán từ DynamoDB.*

---

## 5. Debug nếu gặp lỗi

- Nếu **không thấy kết quả**: Kiểm tra **Console** của trình duyệt (F12 → tab Console) để xem lỗi fetch API.
- Nếu lỗi CORS: Kiểm tra lại **API Gateway → CORS** đã bật cho cả phương thức **OPTIONS** và **POST** chưa.
- Nếu lỗi quyền: Xem lại **IAM Role** của Lambda đã có quyền `sagemaker:InvokeEndpoint` và `dynamodb:PutItem` chưa.

---

> **Hoàn thành rồi đó!**  
> Giờ bạn đã có thể test nhiều ảnh khác nhau và xem kết quả real-time. Tiếp theo, hãy sang phần [Dọn dẹp tài nguyên](/8-cleanup/) để dọn dẹp tài nguyên tránh phát sinh chi phí nhé!