---  
title : "Tạo DynamoDB Table: PredictionHistory"  
date: "2025-08-11"  
weight : 4  
chapter : false  
pre : " <b> 4 </b> "  
---  

> **Mục tiêu**: Hiểu về DynamoDB và tạo bảng `PredictionHistory` để lưu lịch sử dự đoán hình ảnh.  

---  

## Giới thiệu DynamoDB  

DynamoDB là dịch vụ cơ sở dữ liệu NoSQL serverless của AWS, rất nhanh, có khả năng mở rộng tự động và không cần quản lý server. Rất phù hợp để lưu trữ dữ liệu như lịch sử dự đoán của ứng dụng serverless.  

---  

## Tạo bảng PredictionHistory  

- Vào AWS Console → DynamoDB

  ![Find DynamoDB](/images/4.create-dynamoDB/create-dynamoDB-1.png)  

  *Hình 1: Tìm DynamoDB tại console.*

- Tiếp tục chọn Table → Create Table để tạo bảng mới

  ![Create Table](/images/4.create-dynamoDB/create-dynamoDB-2.png)  

  *Hình 2: Nhấn vào Create Table để bắt đầu tạo bảng mới.*

- Đặt tên bảng: `PredictionHistory`.  
- Thiết lập Partition key: `id` (Kiểu String).  
- Bỏ qua phần Sort key (không cần).  

  ![Set up info](/images/4.create-dynamoDB/create-dynamoDB-3.png)  

  *Hình 3: Thiết lập các thuộc tính cho bảng mới.*

- Để các thiết lập còn lại mặc định, nhấn Create table.  

  ![Create Table](/images/4.create-dynamoDB/create-dynamoDB-4.png)  

  *Hình 4: Nhấn Create Table để tạo bảng mới.*

---  

## Lời kết  

Bây giờ bạn đã có bảng `PredictionHistory` sẵn sàng để lưu dữ liệu từ Lambda functions. Tiếp theo, chúng ta sẽ tạo Lambda function để sử dụng bảng này nha!  

> **Sẵn sàng chưa nè?**  
> Chuyển sang [Tạo Lambda function và API](/5-lambda-api-setup/) nha!  