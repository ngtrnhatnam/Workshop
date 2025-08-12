# 🏁Workshop: Triển khai Ứng Dụng Nhận Diện Hình Ảnh Thời Gian Thực Serverless với Lambda và SageMaker 🚀

Chào mừng bạn đến với **Workshop: Triển khai Ứng Dụng Nhận Diện Hình Ảnh Thời Gian Thực Serverless với Lambda và SageMaker**! Đây là một chương trình đào tạo thực hành kéo dài **6 giờ**, giúp bạn xây dựng một **ứng dụng web serverless** nhận diện ảnh thời gian thực sử dụng **Amazon Web Services (AWS)**. Sử dụng các dịch vụ như **S3**, **API Gateway**, **Lambda**, **DynamoDB**, và **SageMaker**, bạn sẽ học cách triển khai một hệ thống hoàn chỉnh từ giao diện tĩnh đến backend, tích hợp sao lưu tự động và giám sát hiệu suất.

<p align="center">
  <a href="https://ngtrnhatnam.github.io/" rel="dofollow" target="blank"><strong>Explore »</strong></a>
    <br/>
    <br/>
    <a href="https://github.com/ngtrnhatnam/Workshop/blob/main/.github/PROPOSAL.md">💡Workshop Proposal</a>
    &nbsp;|&nbsp;
    <a href="https://github.com/ngtrnhatnam/Serverless-ML-Inference-with-Lambda-and-SageMaker">📂Source code</a>
</p>

<p>Sơ đồ kiến trúc tổng hợp: </p> 
<p align="center">
    <img loading="lazy" src="./images/Architecture_Diagram_Serverless_ML_Inference_with_AWS_Lambda_and_SageMaker.png" alt="Project">
</p>

---

### 🔰Giới Thiệu

🧠Workshop này được thiết kế để trang bị kỹ năng thực tiễn về **kiến trúc serverless** và **điện toán đám mây** cho lập trình viên, sinh viên CNTT, và chuyên gia IT. Qua **8 phần thực hành**, bạn sẽ:
- Xây dựng giao diện web cơ bản với **HTML, CSS**.
- Tích hợp backend serverless với **AWS Lambda**, **API Gateway**, và **DynamoDB**.
- Tải model lên **SageMaker Endpoint**.

Workshop phù hợp cho các tổ chức giáo dục, trung tâm đào tạo, và doanh nghiệp muốn nâng cao năng lực công nghệ đám mây. Sau khi hoàn thành, bạn sẽ có một **dự án thực tế** để bổ sung vào portfolio và kỹ năng triển khai ứng dụng serverless chuyên nghiệp.

### Thông Tin Sinh Viên Thực Tập 👨‍🎓

- **📛Họ và Tên**: Nguyễn Trần Nhật Nam  
- **🏫Trường**: Trường Đại Học Công nghệ Thành phố Hồ Chí Minh (HUTECH)  
- **🆔MSSV**: 2180608712  
- **📧Gmail**: [nhatnam.ngtr@gmail.com](mailto:nhatnam.ngtr@gmail.com)  
- **💻GitHub**: [ngtrnhatnam](https://github.com/ngtrnhatnam)  

---

### 🧩Nội Dung Chính

📦Workshop bao gồm **8 phần thực hành**, từ giới thiệu serverless đến triển khai và dọn dẹp tài nguyên:

| 📚Phần | 📌Nội Dung | 📝Mô Tả |
|------|----------|-------|
| 1 | **📖Giới Thiệu** | Tổng quan serverless, lợi ích, và kiến trúc hệ thống. |
| 2 | **⚙️Chuẩn Bị** | Thiết lập tài khoản AWS, AWS CLI, và môi trường phát triển. |
| 3 | **🧠Triển khai nhanh SageMaker AI** | Tạo SageMaker để upload model lên SageMaker Endpoint. |
| 4 | **🎥Tạo DynamoDB** | Tạo DynamoDB để lưu lịch sử ảnh đã dự đoán |
| 5 | **🔗Cấu Hình Lambda và API** | Tạo Lambda functions để xử lý logic và cấu hình API tích hợp Lambda. |
| 6 | **🎨Giao Diện Web** | Thiết kế giao diện đơn giản với HTML và CSS. |
| 7 | **🧪Kiểm Tra Kết Quả** | Xác minh hoạt động của giao diện, API, và sao lưu. |
| 8 | **🧹Dọn Dẹp Tài Nguyên** | Xóa tài nguyên để tránh chi phí dư thừa. |

**🛠️Công Cụ Sử Dụng**:
- **🖥️AWS Management Console**, **AWS CLI**: Cấu hình dịch vụ AWS.
- **💻Visual Studio Code**: Viết mã Python, HTML/CSS/JS.

---

### 🚀Hướng Dẫn Cài Đặt và Chạy Dự Án

### 🔽1. Clone Mã Nguồn từ GitHub
- Mở terminal và chạy lệnh sau để sao chép mã nguồn về máy:

```bash
git clone https://github.com/ngtrnhatnam/Serverless-ML-Inference-with-Lambda-and-SageMaker
cd Serverless-ML-Inference-with-Lambda-and-SageMaker
```

### 🧰2. Install Required Tools
- **AWS CLI**: Cài đặt theo hướng dẫn tại [https://aws.amazon.com/cli/](https://aws.amazon.com/cli/).
- **Python**: Tải và cài đặt từ [https://www.python.org/](https://www.python.org/) để upload model.
- **Visual Studio Code**: Tải tại [https://code.visualstudio.com/](https://code.visualstudio.com/) để chỉnh sửa mã.

### 🧪3. Chạy và Kiểm Tra Dự Án
- Mở `main.html` cục bộ trong trình duyệt để kiểm tra giao diện tĩnh.
- Xem chi tiết content để hiểu toàn bộ quy trình.

---

### 🧱Yêu Cầu Hệ Thống

| ⚙️Yêu Cầu | 💡Mô Tả |
|---------|-------|
| **💻Hệ Điều Hành** | Windows, macOS, hoặc Linux |
| **☁️AWS Account** | Tài khoản AWS Free Tier (khuyến nghị) |
| **🔧Công Cụ** | AWS CLI, Python (3.13+), Visual Studio Code |
| **🌐Trình Duyệt** | Chrome, Firefox, hoặc Edge (hỗ trợ JavaScript) |
| **📶Kết Nối** | Internet ổn định để truy cập AWS và GitHub |

---

### 📚Tài Liệu Tham Khảo 

- [🔗The First Cloud Journey](https://cloudjourney.awsstudygroup.com/)
- [🌟AWS Special Force Portal](https://specialforce.awsstudygroup.com/)
- [🧠AWS Serverless Workshops](https://aws.amazon.com/serverless/)
- [📖AWS Documentation](https://docs.aws.amazon.com/)

---

### 📬Liên Hệ

Có thắc mắc hoặc cần hỗ trợ? Hãy liên hệ với tôi:
- **📧Nguyễn Trần Nhật Nam**: [nhatnam.ngtr@gmail.com](mailto:nhatnam.ngtr@gmail.com)

🌟 **Cảm ơn bạn đã quan tâm đến workshop của tôi!** Tham gia để làm chủ công nghệ serverless và xây dựng ứng dụng hiện đại với AWS! 🚀

---

### 📄License

This project is licensed under the terms of the [MIT](LICENSE) license.