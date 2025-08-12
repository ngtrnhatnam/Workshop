---
title : "Tạo nhanh SageMaker AI"
date: "2025-08-11" 
weight : 3
chapter : false
pre : " <b> 3. </b> "
---

> **Mục tiêu**: Tạo nhanh một mô hình AI trên AWS SageMaker, sẵn sàng để tích hợp vào ứng dụng serverless nhận diện hình ảnh của bạn.

---

## Giới thiệu

Trong phần này, chúng ta sẽ **khởi tạo nhanh SageMaker AI** để phục vụ việc nhận diện hình ảnh thời gian thực.  
Quy trình này bao gồm:

- Tạo **SageMaker Studio** để làm việc.
- Cấu hình **IAM Role** để SageMaker có quyền truy cập S3, Lambda, và các dịch vụ AWS liên quan.
- Upload mô hình đã train sẵn để sẵn sàng triển khai.

---

## Các bước chính

| **Bước** | **Nội dung** |
|----------|--------------|
| 3.1 | [Thiết lập SageMaker AI](/3-quick-create-sagemaker-AI/3.1-set-up-sagemaker-AI/) |
| 3.2 | [Thiết lập IAM Role cho SageMaker](/3-quick-create-sagemaker-AI/3.2-set-up-IAM-role-for-sagemaker/) |
| 3.3 | [Upload mô hình đã train](/3-quick-create-sagemaker-AI/3.3-upload-trained-model/) |

---

> **Lưu ý**: Bạn cần hoàn thành phần **2 – Các bước chuẩn bị** trước khi tiếp tục, để đảm bảo môi trường AWS và công cụ đã sẵn sàng.

---

## Kết luận

Khi hoàn thành phần này, bạn sẽ:
- Có môi trường SageMaker sẵn sàng hoạt động.
- Đã gán quyền truy cập đầy đủ cho SageMaker.
- Upload xong mô hình để triển khai vào ứng dụng serverless.

> **Sẵn sàng chưa nè?**  
> Chúng ta bắt đầu với [Thiết lập SageMaker AI](/3-quick-create-sagemaker-AI/3.1-set-up-sagemaker-AI/) nha!
