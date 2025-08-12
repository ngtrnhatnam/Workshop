---
title : "Thiết lập SageMaker AI"
date: "2025-08-11"
weight : 3.1
chapter : false
pre : " <b> 3.1 </b> "
---

> **Mục tiêu**: Khởi tạo SageMaker AI bằng tính năng Quick setup cho người dùng đơn, sẵn sàng triển khai mô hình AI.

---

## 1. Truy cập SageMaker

- Đăng nhập AWS Management Console.
- Tìm kiếm **SageMaker AI** và mở dịch vụ.

![AWS Search SageMaker](/images/3.quick-create-sagemaker-AI/3.1.set-up-sagemaker-AI/set-up-sagemaker-AI-1.png)  
*Hình 1: Tìm kiếm và truy cập dịch vụ SageMaker trong AWS Console.*

---

## 2. Chọn Quick setup

- Ở màn hình chính của SageMaker, tìm phần **New to SageMaker AI?**  
- Nhấn **Set up for single user**.

![SageMaker Quick Setup](/images/3.quick-create-sagemaker-AI/3.1.set-up-sagemaker-AI/set-up-sagemaker-AI-2.png)  
*Hình 2: Tùy chọn Quick setup cho người dùng đơn.*

---

## 3. Xác nhận cấu hình mặc định

- AWS sẽ tự động đề xuất cấu hình và các thiết lập mặc định, bạn chỉ việc đợi load xong.

![SageMaker Default Config](/images/3.quick-create-sagemaker-AI/3.1.set-up-sagemaker-AI/set-up-sagemaker-AI-3.png)  
*Hình 3: Giao diện xác nhận cấu hình Quick setup.*

---

## 4. Chờ khởi tạo

- Trạng thái ban đầu: **Pending** → sẽ chuyển sang **InService** khi hoàn tất.
- Quá trình này thường mất vài phút.

---

> **Lưu ý nhỏ**: Khi sử dụng **Quick setup** của SageMaker, hệ thống sẽ tự động tạo cho bạn các IAM Role và Policy cần thiết để SageMaker hoạt động trơn tru mà bạn không cần phải tạo thủ công.  
> Nếu bạn muốn tuỳ chỉnh quyền hạn hoặc triển khai trong môi trường sản xuất, có thể tạo và gán IAM Role riêng cho SageMaker.  
>  
> Với mục đích workshop này, bạn hoàn toàn có thể yên tâm sử dụng các Role mặc định do AWS tạo sẵn nhé!

> **Xong chưa nè?**  
> Tiếp theo, chúng ta sẽ [Tạo IAM Role cho SageMaker](/3-quick-create-sagemaker-AI/3.2-set-up-IAM-role-for-sagemaker/) nha!