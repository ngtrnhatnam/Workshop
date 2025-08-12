---
title : "Cài đặt công cụ cần thiết"
date: "2025-08-10" 
weight : 2.1
chapter : false
pre : " <b> 2.1 </b> "
---

> **Mục tiêu**: Cài đặt Python, VS Code, AWS CLI và các thư viện Python cần thiết để phát triển ứng dụng serverless nhận diện hình ảnh.

---

## Yêu Cầu Ban Đầu

*Trước khi bắt đầu, hãy đảm bảo máy tính bạn đã sẵn sàng với các công cụ cần thiết nhé!*

## 1. Python

- Tải và cài đặt [Python](https://www.python.org/downloads/).  
- Kiểm tra cài đặt bằng lệnh:
```bash
python --version 
```
- Nếu bạn được trả kết quả có dạng bên dưới thì chúng ta đến bước tiếp theo nhé: 
```bash
Python 3.xx.x
```
> *x* là số phiên bản nha, ví dụ như Python 3.13.1 như mình là ổn rồi nè 💖

![CMD check Python version](/images/2.prerequisite/2.1.install-necessary-tool/install-necessary-tool-1.png)

*Hình 1: Giao diện Console kiểm tra phiên bản Python sau khi cài.*

---

## 2. Visual Studio Code (VS Code)

- Tải và cài đặt [VS Code](https://code.visualstudio.com/download).
- Cài đặt các extension hữu ích:
    - Python (Microsoft):

        ![Extension Python](/images/2.prerequisite/2.1.install-necessary-tool/install-necessary-tool-2.png)

        *Hình 2: Giao diện VS Code cài đặt extension Python.*

    - Live Server để chạy giao diện web local:

        ![Extension Live Server](/images/2.prerequisite/2.1.install-necessary-tool/install-necessary-tool-3.png)

        *Hình 3: Giao diện VS Code cài đặt extension Live Server.*

---

## 3. AWS CLI

- Tải và cài đặt [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html).
- Kiểm tra cài đặt bằng lệnh:
```bash
aws --version 
```
- Nếu bạn được trả kết quả có dạng bên dưới thì chúng ta đến bước tiếp theo nhé: 
```bash
aws-cli/2.27.52 Python/3.13.4 Windows/11 exe/AMD64
``` 
> *Thông số có thể khác nhau tùy phiên bản/chipset của máy, đừng lo lắng nhé 💪*

![CMD check AWS CLI](/images/2.prerequisite/2.1.install-necessary-tool/install-necessary-tool-4.png)

*Hình 4: Giao diện Console kiểm tra AWS CLI sau khi cài.*

---

> **Xong hết chưa nè?**  
> Mình chuyển đến [Chuẩn bị môi trường](/2-preparation-steps/2.2-set-up-environment/) để tiếp tục nha! ✨