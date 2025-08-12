---
title : "Giới thiệu"
date: "2025-06-07" 
weight : 1 
chapter : false
pre : " <b> 1. </b> "
---
> **Khám phá sức mạnh của AI thời gian thực trên nền tảng đám mây!**  
> Workshop này sẽ hướng dẫn bạn từng bước xây dựng **ứng dụng web nhận diện hình ảnh serverless**, sử dụng dịch vụ AWS để xử lý, dự đoán và lưu trữ dữ liệu hình ảnh một cách **nhanh chóng**, **an toàn** và **tiết kiệm chi phí**.

Trong thời đại AI, việc xây dựng các ứng dụng thời gian thực có khả năng mở rộng, bảo mật và dễ bảo trì là ưu tiên hàng đầu. Workshop **"Triển khai ứng dụng nhận diện hình anh thời gian thực Serverless với Lambda và SageMaker"** sẽ giúp bạn tích hợp mô hình Machine Learning đã huấn luyện sẵn vào giao diện web, cho phép dự đoán theo thời gian thực mà không cần quản lý máy chủ.

Ứng dụng hỗ trợ:
- Tải ảnh trực tiếp từ trình duyệt.
- Dự đoán tức thì từ mô hình ML đã deploy.
- Lưu lịch sử dự đoán vào DynamoDB để theo dõi.
- Giao diện đơn giản, responsive cho trải nghiệm mượt mà.
- Kiến trúc serverless — không cần bảo trì máy chủ.

---

## Lợi ích của ứng dụng Serverless

Hệ sinh thái serverless của AWS mang lại nhiều lợi ích cho ứng dụng AI:

### 1. Xử lý thời gian thực
AWS Lambda thực hiện dự đoán ngay khi nhận ảnh, đảm bảo độ trễ thấp.

> **Ví dụ**: Người dùng tải ảnh chữ số viết tay và hệ thống lập tức trả về con số dự đoán.

### 2. Tự Động Mở Rộng
Lambda tự động scale theo nhu cầu — dù chỉ 1 hay 1.000 người dùng tải ảnh cùng lúc.

### 3. Xử Lý Dữ Liệu An Toàn
API Gateway kết hợp với **IAM roles** và resource policies để đảm bảo:
- Chỉ các lời gọi được ủy quyền mới đến được Lambda.
- Quyền đọc/ghi DynamoDB được giới hạn rõ ràng.

> **Ví dụ**: Lambda dự đoán chỉ có quyền ghi vào bảng `PredictionHistory` chứ không thể xóa dữ liệu.

### 4. Tiết Kiệm Chi Phí
Bạn chỉ trả tiền cho những gì bạn dùng:
- Lambda: Tính phí dựa trên thời gian thực thi.
- DynamoDB: Tính phí theo số request.
- S3: Tính phí lưu trữ file tĩnh.

### 5. Truy Cập Nhanh & Trải Nghiệm Mượt Mà
Giao diện web (HTML, CSS, JS) sẽ chạy trực tiếp trên máy local thông qua Live Server của VS Code.
Cách này giúp phát triển, test và sửa UI nhanh chóng mà không cần deploy file tĩnh lên S3.

---

## Mục Tiêu Workshop

Hoàn thành workshop này, bạn sẽ học được cách:

| **Mục tiêu** | **Công nghệ** | **Kết quả** |
|----------|----------------|-------------|
| Thiết kế giao diện đơn giản, responsive | HTML, CSS | Giao diện upload ảnh dễ dùng |
| Xây dựng và bảo mật API | API Gateway | Endpoint để gửi ảnh và nhận dự đoán |
| Triển khai suy luận ML | AWS Lambda, SageMaker Endpoint | Dự đoán thời gian thực từ model đã huấn luyện |
| Lưu trữ kết quả | DynamoDB | Lưu lịch sử dự đoán để tra cứu sau |
| Giám sát & gỡ lỗi | S3, CloudFront | Fast, worldwide content delivery |
| Monitor and debug | CloudWatch | Theo dõi và phân tích hiệu suất hệ thống |

## Bắt đầu hành trình nào!

Khi kết thúc workshop này, bạn sẽ có được:
1. Một **ứng dụng nhận diện ảnh thời gian thực hoạt động hoàn chỉnh**.
2. Kinh nghiệm thực tế kết nối các dịch vụ AWS thành một quy trình serverless.
3. Kỹ năng triển khai ứng dụng AI mà không cần quản lý server.

> **Sẵn sàng chưa nè?**  
> Chúng ta đi tiếp đến [các bước chuẩn bị](2-preparation-steps/) để thiết lập môi trường AWS nha!