---
title : "Thiết kế Giao Diện Web"
date: "2025-08-12"
weight : 6
chapter : false
pre : " <b> 6. </b> "
---

> **Mục tiêu**: Xây dựng giao diện web đơn giản, thân thiện, hỗ trợ người dùng upload hình ảnh để dự đoán.

---

## 1. Tổng quan về giao diện

Giao diện web được thiết kế đơn giản, dễ dùng, tập trung vào chức năng upload ảnh và hiển thị kết quả dự đoán một cách rõ ràng, trực quan.

- Hỗ trợ upload ảnh trực tiếp từ máy tính người dùng.
- Hiển thị ảnh vừa upload cùng kết quả dự đoán bên dưới.
- Có nút gửi dữ liệu để gọi API backend.
- Giao diện responsive, chạy ngon trên cả desktop và mobile.

---

## 2. Công nghệ sử dụng

- HTML5 cho cấu trúc trang.
- CSS3 cho tạo style đẹp, dễ nhìn.
- JavaScript (vanilla) để xử lý tương tác như upload ảnh, gọi API, hiển thị kết quả.

---

## 3. Cấu trúc trang chính

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Cat vs Dog Classifier</title>
    <link rel="stylesheet" href="style.css">
  </head>
  <body>
    <h1>Cat or Dog?</h1>
    <h2>Upload ảnh để phân loại</h2>
    <input type="file" id="imageInput" accept="image/*" />
    
    <div id="previewBox" style="display:none;">
      <h3>Ảnh bạn vừa chọn:</h3>
      <img id="previewImage" src="" alt="Preview">
    </div>

    <button onclick="sendImage()">Phân loại</button>
    <p id="result"></p>

    <div id="history">
      <h2>Lịch sử đoán gần đây</h2>
      <ul id="historyList"></ul>
    </div>

    <script src="script.js"></script>
  </body>
</html>
```

## 4. Một số điểm lưu ý
- Nút “Dự đoán” sẽ gọi API backend qua JavaScript fetch.
- Ảnh được preview ngay khi chọn để người dùng kiểm tra.
- Kết quả dự đoán sẽ hiện ra trong `<p id="result">`.
- Thiết kế đơn giản, dễ bảo trì và mở rộng.

## 5. Hướng dẫn chỉnh sửa JS - API Gateway

- Vào AWS Console → API Gateway

  ![Find API Gateway](/images/6.web/web-1.png)  

  *Hình 1: Tìm API Gateway tại console.*

- Truy cập vào tab **Function** - chọn `InvokeModelLambda` Function

  ![Access InvokeModelLambda](/images/6.web/web-2.png)  

  *Hình 2: Truy cập InvokeModelLambda.*

- Tiếp tục vào tab **Configuration** - **Trigger**. Tại dòng **API Endpoint** sao chép toàn bộ đường dẫn. Đường dẫn có dạng `https://xxxx.execute-api.<vùng-của-bạn>.amazonaws.com/prod/predict`.

  ![Copy API](/images/6.web/web-3.png)  

  *Hình 3: Sao chép API Endpoint.*

- Quay lại project, tại file `script.js`, các bạn nhấn **Ctrl + F**, điền `Change predict`. Các bạn thay đường dẫn bên trong cặp ngoặc kép **" "**.

  ![Copy API](/images/6.web/web-4.png)  

  *Hình 4: Sao chép API Endpoint.*

- Tiếp tục tương tự với `SavePredictionHistory`, tuy nhiên ở project, các bạn nhấn **Ctrl + F**, điền `Change history`. Các bạn thay đường dẫn bên trong cặp ngoặc kép **" "**.

- Cuối cùng nhấn **Ctrl + S**.

> **Sẵn sàng chưa?**  
> Tiếp theo, bạn có thể chuyển sang phần [Kiểm tra kết quả](/7-check-result/) để xác minh hoạt động của toàn hệ thống nha!!