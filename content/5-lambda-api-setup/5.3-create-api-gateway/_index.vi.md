---
title : "Tạo Lambda Function lưu lịch sử"
date: "2025-08-12"
weight : 5
chapter : false
pre : " <b> 5.3 </b> "
---

> **Mục tiêu**: Tạo API Gateway để giao tiếp với Lambda.

---

## 1. Tạo API Gateway mới

- Vào AWS Console → API Gateway.

    ![AWS Search Lambda](/images/5.lambda-api-setup/5.3.create-api-gateway/create-api-gateway-1.png)  

    *Hình 1: Tìm kiếm và truy cập dịch vụ API Gateway trong AWS Console.*

- Chọn tab **APIs** → nhấn nút **Create API**.  

    ![Create new API](/images/5.lambda-api-setup/5.3.create-api-gateway/create-api-gateway-2.png)  
    *Hình 2: Bắt đầu tạo API mới.*

- Tại **HTTP API**, chọn **Build**.

    ![HTTP API](/images/5.lambda-api-setup/5.3.create-api-gateway/create-api-gateway-3.png)  
    *Hình 3: Chọn phương thức HTTP.*

- Tiếp tục tại Step 1, ta đặt API name là `MLInferenceAPI`, sau đó chọn **Next**

    ![Set API name](/images/5.lambda-api-setup/5.3.create-api-gateway/create-api-gateway-4.png)  
    *Hình 4: Tiến hành đặt tên cho API.*

- Tại Step 2 chọn **Next**, đến Step 3 chúng ta đặt Stage name là `prod`, rồi tiếp tục chọn **Next**.

    ![HTTP API](/images/5.lambda-api-setup/5.3.create-api-gateway/create-api-gateway-5.png)  
    *Hình 5: Tiến hành đặt Stage name.*

- Tại Step 4, chọn **Create**.

    ![Set up attribute API](/images/5.lambda-api-setup/5.3.create-api-gateway/create-api-gateway-6.png)  

    *Hình 6: Hoàn tất sơ bộ tạo API.*

---

## 2. Thiết lập routers cho API

- Sau đó màn hình sẽ chuyển qua tab Develop → Routers, tại đây chúng ta set up router trước để gắn cho Lambda ở các bước sau, chọn **Create**.

    ![Set up routers](/images/5.lambda-api-setup/5.3.create-api-gateway/create-api-gateway-7.png)  

    *Hình 7: Bắt đầu tạo router.*

- Các bạn quay lại tiến hành tạo liên tiếp 2 router là:
    - `/history` và

    ![Router history](/images/5.lambda-api-setup/5.3.create-api-gateway/create-api-gateway-8.png)  

    *Hình 8: Tiến hành tạo router history.*

    -  `/predict`

    ![Router predict](/images/5.lambda-api-setup/5.3.create-api-gateway/create-api-gateway-9.png)  

    *Hình 9: Tiến hành tạo router predict.*

---

## 3. Thiết lập CORS cho API

- Tại tab **Develop** → **CORS** chúng ta chọn **Configure** để tiến hành set up:

    ![Start set up CORS](/images/5.lambda-api-setup/5.3.create-api-gateway/create-api-gateway-10.png)  

    *Hình 10: Tiến hành set up CORS.*

    - **Access-Control-Allow-Origin**: nhập `*`, sau đó chọn **Add** bên cạnh.
    - **Access-Control-Allow-Headers**: nhập `content-type`, sau đó cũng chọn **Add** bên cạnh.
    - **Access-Control-Allow-Methods**: chúng ta sẽ tick vào 3 options là `GET`, `POST` và `OPTION`.
    - **Access-Control-Expose-Headers**: để trống.
    - Cuối cùng chọn **Save**.

    ![Set up attribute CORS](/images/5.lambda-api-setup/5.3.create-api-gateway/create-api-gateway-11.png)  

    *Hình 11: Thiết lập thông số cho CORS.*

---

## 4. Gắn API vào Lambda

- Tại tab **Develop** → **Integrations** chúng ta chọn **/history** - **ANY** → **Create and attach an integration** để tiến hành set up:

    ![Set up API](/images/5.lambda-api-setup/5.3.create-api-gateway/create-api-gateway-12.png)  

    *Hình 12: Tiến hành gắn API.*

    - Tại tab **Integration target** - **Integration type**: chọn **Lambda Function**.
    - **AWS Region**: chọn region có chứa **Lambda Function**, ở đây mình chọn `ap-southeast-1`
    - **Lambda function**: chọn fuction để lưu tương tác với Sagemaker Endpoint trước đó chúng ta tạo với tên là `SavePredictionHistory`.
    - Cuối cùng chọn **Create**.

    ![Finish](/images/5.lambda-api-setup/5.3.create-api-gateway/create-api-gateway-13.png)  

    *Hình 13: Thiết lập thông số.*

- Tương tự với **/predict** - **POST**. Chỉ khác tại **Lambda function**: chọn fuction để gọi endpoint trước đó chúng ta tạo với tên là `InvokeModelLambda`

---

## Lời kết  

Giờ thì API đã sẵn sàng đón nhận request từ frontend rồi đó bạn iu ơi!