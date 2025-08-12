---
title : "Chuẩn bị môi trường"
date: "2025-08-10" 
weight : 2
chapter : false
pre : " <b> 2.2 </b> "
---

> **Mục tiêu**: Fork & clone project, tạo môi trường ảo và cài các thư viện Python cần thiết để chạy ứng dụng.

---

## 1. Fork và Clone Project

- Truy cập GitHub repo dự án của tui nè: [Serverless-ML-Inference-with-Lambda-and-SageMaker](https://github.com/ngtrnhatnam/Serverless-ML-Inference-with-Lambda-and-SageMaker)
- Nhấn **Fork** để tạo bản sao về tài khoản GitHub của bạn.
- Clone về máy:
```bash
git clone https://github.com/<your-username>/Serverless-ML-Inference-with-Lambda-and-SageMaker.git
cd <your-repo>
code .
```

---

## 2. Tạo và kích hoạt môi trường ảo (Virtual Environment)

- Tạo môi trường ảo:
```bash
python -m venv .venv
```

- Sau đó kích hoạt môi trường ảo:
  - Windows:
  ```bash
  .venv\Scripts\activate
  ```

  - macOS / Linux:
  ```bash
  source .venv/bin/activate
  ```
> Nếu thành công, bạn sẽ thấy tên môi trường (ví dụ *.venv*) xuất hiện ở đầu dòng lệnh.

![Activate venv](/images/2.prerequisite/2.2.set-up-environment/set-up-environment-1.png)

*Hình 1: Giao diện Console kiểm tra môi trường ảo đã được kích hoạt chưa.*

---

## 3. Cài đặt các thư viện cần thiết

- Cài đặt nhanh các thư viện cần thiết:  
```bash
pip install boto3 sagemaker torch torchvision pillow
```
> Lưu ý:
> - Nếu bạn cần train model local, hãy đảm bảo đã cài gcc hoặc build tools tương ứng với hệ điều hành của bạn.
> - Thư viện torch có thể mất vài phút để cài, tuỳ tốc độ mạng, đừng nóng vội nha

---

> **Cũng dễ mà phải hong?**  
> Vậy mình chuyển đến [Thiết lập Sagemake AI](/3-3-quick-create-sagemaker-AI/) để tiếp tục nha! ✨