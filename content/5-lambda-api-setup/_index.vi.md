---
title : "Giới thiệu Lambda và API Gateway"
date: "2025-08-12"
weight : 5
chapter : false
pre : " <b> 5 </b> "
---

> **Mục tiêu**: Hiểu tổng quan về vai trò của AWS Lambda và API Gateway trong ứng dụng serverless nhận diện hình ảnh.

---

## AWS Lambda là gì?

AWS Lambda là dịch vụ compute serverless của AWS, cho phép bạn chạy mã (code) mà không cần quản lý server. Lambda tự động mở rộng, chỉ tính phí theo thời gian thực thi.

Ứng dụng Lambda trong workshop:
- Xử lý các yêu cầu người dùng (upload hình ảnh, gọi dự đoán).
- Lưu trữ lịch sử dự đoán vào DynamoDB.
- Gọi mô hình Machine Learning trên SageMaker để trả kết quả dự đoán.

---

## API Gateway là gì?

API Gateway là dịch vụ quản lý API của AWS, giúp bạn tạo, bảo mật, theo dõi và vận hành các API RESTful hoặc WebSocket.

Vai trò trong workshop:
- Cung cấp endpoint RESTful để frontend gửi ảnh và nhận kết quả dự đoán.
- Kết nối với các Lambda function xử lý logic backend.
- Quản lý bảo mật và phân quyền truy cập API.

---

## Kiến trúc tổng thể

Frontend → API Gateway → Lambda (gọi SageMaker) → SageMaker Endpoint → Lambda (lưu lịch sử) → DynamoDB

---

## Các bước chính

| **Bước** | **Nội dung** |
|----------|--------------|
| 5.1 | [Thiết lập Lambda Function lưu lịch sử](/5-lambda-api-setup/5.1-create-lambda-save-history/) |
| 5.2 | [Thiết lập Lambda Function gọi endpoint Sagemaker](/5-lambda-api-setup/5.2-create-lambda-call-sagemaker/) |
| 5.3 | [Thiết lập API Gateways](/5-lambda-api-setup/5.3-create-api-gateway/) |

---

> **Sẵn sàng chưa?**  
> Tiếp theo, ta sẽ tạo Lambda function lưu lịch sử trong phần [Thiết lập Lambda Function lưu lịch sử](/5-lambda-api-setup/5.1-create-lambda-save-history/) nha!