# Proposal: Real-time Serverless ML Inference with AWS Lambda and SageMaker
# Thông Tin Sinh Viên Thực Tập
-  👨‍🎓 **Họ và Tên**: Nguyễn Trần Nhật Nam
-  👨‍🎓 **Trường Đại Học**: Đại Học công Nghệ TP.HCM (HUTECH)
-  🆔 **MSSV**: 2180608712
-  📧 **Gmail**: nhatnam.ngtr@gmail.com
-  🐱 **Github**: [https://github.com/ngtrnhatnam/](https://github.com/ngtrnhatnam/)
-  🔗 **Link Workshop**: [https://github.com/ngtrnhatnam/Serverless-ML-Inference-with-Lambda-and-SageMaker](https://github.com/ngtrnhatnam/Serverless-ML-Inference-with-Lambda-and-SageMaker)
## 1. 📄 Executive Summary

### Problem Statement
Việc triển khai mô hình Machine Learning (ML) truyền thống yêu cầu phải duy trì server hoặc endpoint hoạt động liên tục, dẫn đến chi phí cao và kém linh hoạt. Trong khi đó, nhiều bài toán inference có tần suất thấp hoặc không cần real-time 24/7, gây lãng phí tài nguyên nếu không tối ưu. Cần một giải pháp inference hiệu quả về chi phí nhưng vẫn đảm bảo độ trễ thấp.
### Solution Overview
Hệ thống sử dụng mô hình MobileNetV2 để phân loại ảnh (chó/mèo) theo hướng serverless. Mô hình được deploy trên AWS SageMaker và inference được trigger thông qua AWS Lambda kết hợp API Gateway. Toàn bộ pipeline hoạt động theo sự kiện (event-driven), không cần duy trì server 24/7, giúp tiết kiệm chi phí. Hệ thống cũng được thiết kế để dễ mở rộng, tích hợp với các kỹ thuật tối ưu như caching hoặc batch processing nếu cần.
### Business Benefits và ROI Summary
- **Tiết kiệm chi phí hạ tầng**: Không cần duy trì máy chủ inference liên tục, chỉ trả tiền khi có request → giảm chi phí so với EC2.
- **Tự động mở rộng**: Lambda và SageMaker hỗ trợ autoscaling → phù hợp cả với hệ thống nhỏ hoặc khi nhu cầu tăng đột biến.
- **Thời gian triển khai nhanh**: Nhờ serverless và dịch vụ managed của AWS, hệ thống có thể triển khai trong vài giờ thay vì vài ngày.
- **Dễ tích hợp vào sản phẩm thực tế**: API inference hoạt động qua HTTP, có thể tích hợp vào bất kỳ web/mobile app nào.
- **ROI cao**: Với chi phí thấp, thời gian triển khai nhanh và độ trễ thấp, hệ thống này phù hợp cho các doanh nghiệp nhỏ, startup thử nghiệm AI mà không cần đầu tư hạ tầng lớn.

### Investment Required và Timeline
- **AWS SageMaker endpoint** (ml.t2.medium): ~0.07 USD/giờ → ~1.68 USD/ngày nếu chạy liên tục
- **AWS Lambda**: ~0.20 USD/1 triệu request đầu tiên/tháng → gần như miễn phí
- **Tổng chi phí thử nghiệm 1–2 ngày**: ít hơn 5 USD
- **Timeline**: Dự án dự kiến hoàn thành trong 3 tháng.

### Success Metrics và Expected Outcomes
- **Inference latency**: < 500ms cho mỗi ảnh
- **Cost per 1000 inferences**: ít hơn 0.50 USD
- **Mô hình accuracy**: > 90% (trên tập test chó/mèo)
- **SLA uptime**: 99.9% (nhờ sử dụng các dịch vụ managed)
- **Tài liệu hoàn chỉn**h: bao gồm hướng dẫn triển khai, sơ đồ hệ thống và benchmark
- **Khả năng mở rộng**: Có thể dùng lại kiến trúc này để triển khai các mô hình AI khác

## 2. 🎯 Problem Statement

### Current Situation Analysis
Nhu cầu ứng dụng Machine Learning vào sản phẩm thật ngày càng tăng, đặc biệt trong các tác vụ inference (phân loại hình ảnh, dự đoán, gợi ý...). Tuy nhiên, đa phần các hệ thống inference hiện tại vẫn yêu cầu chạy mô hình trên các server liên tục hoạt động (EC2, GPU node, on-prem), gây ra chi phí cao và khó mở rộng khi traffic tăng giảm không đều.
### Pain Points Identification
- Chi phí cao: Các mô hình cần “always-on” server, kể cả khi không có request nào. 
- Khó mở rộng linh hoạt: Khi lượng inference tăng đột biến, hệ thống truyền thống dễ quá tải hoặc cần nhiều công sức scale thủ công. 
- Tối ưu thấp với mô hình nhẹ: Với các mô hình nhỏ như MobileNet, việc chạy server riêng là thừa tài nguyên. 
- Thời gian triển khai lâu: DevOps cần cấu hình nhiều bước hạ tầng, tốn thời gian triển khai.

### Stakeholders Affected và Their Concerns
- **Startup/SMEs**: Không có đủ ngân sách để duy trì hệ thống ML truyền thống, cần giải pháp rẻ, dễ vận hành. 
- **Dev teams**: Muốn tích hợp AI vào sản phẩm nhưng thiếu kinh nghiệm vận hành mô hình trên cloud. End-users: Yêu cầu inference nhanh, ổn định dù chỉ là request nhỏ lẻ.

### Business Consequences của Inaction
- Bỏ lỡ cơ hội tích hợp AI vào sản phẩm trong thời đại AI-first. 
- Chi phí duy trì mô hình cao, không khả thi cho các dự án thử nghiệm nhỏ. 
- Chậm trễ ra mắt sản phẩm do hạ tầng phức tạp dẫn đến mất lợi thế cạnh tranh.
### Market Opportunity
- Serverless ML inference đang là xu hướng hot với nhu cầu cao từ thị trường: 
  - Các công ty muốn nhanh chóng POC (Proof of Concept) AI mà không phải chi hàng trăm đô cho server. 
  - Tăng trưởng các dịch vụ FaaS (Function-as-a-Service) như AWS Lambda. 
  - AWS hỗ trợ mạnh mẽ cho SageMaker + Lambda, tạo điều kiện dễ dàng cho các team nhỏ thử nghiệm mô hình.
## 3. 🏗️ Solution Architecture

### High-level Architecture Diagram
![Architecture Diagram](/image/Architecture_Diagram_Serverless_ML_Inference_with_AWS_Lambda_and_SageMaker.png)

### AWS Services Selection và Justification
- **Amazon SageMaker**: Chạy endpoint cho mô hình MobileNetV2, không phải tự quản lý hạ tầng, có sẵn autoscaling theo traffic.
- **AWS Lambda**: Serverless compute, chỉ trả tiền khi có request, cold‑start thấp với Python.
- **Amazon DynamoDB**: Lưu metadata, bao gồm tên file S3, userId, nhãn model, thời gian inference…. Miễn phí 25GB bộ nhớ lưu trữ.
- **Amazon S3**: Lưu ảnh gốc và (tùy chọn) output kết quả. Miễn phí 5GB bộ nhớ lưu trữ ở free tier và 20,000 request/tháng.
- **API Gateway**: 	Tạo REST/HTTP API ➜ bảo mật, throttling, dễ tích hợp mobile/web.
- **AWS CloudWatch**: Log + métrics (latency, error rate) của Lambda & SageMaker, cảnh báo khi latency > 500 ms.
- **AWS IAM**: Quản lý quyền truy cập và bảo mật các dịch vụ AWS.

### Component Interactions và Data Flow
1. Người dùng (client/frontend) gửi HTTP POST kèm ảnh cần phân loại.
2. API Gateway nhận request và chuyển tới AWS Lambda.
3. Lambda xử lý ảnh (resize, encode base64, etc.), sau đó gọi tới endpoint của SageMaker.
4. SageMaker nhận input, thực hiện inference bằng mô hình MobileNetV2, trả kết quả (cat/dog).
5. Lambda nhận kết quả và trả response về lại cho người dùng.

### Security Architecture và Compliance
- **IAM Role**: giới hạn quyền Lambda chỉ được gọi SageMaker và đọc từ S3 nếu cần.
- **API Gateway** có thể cấu hình với:
  - **API Key** hoặc Cognito để bảo vệ endpoint
  - **CORS settings**: cho phép frontend truy cập
- **SageMaker endpoint**: chỉ accessible từ Lambda (không public)
- **Logging** đầy đủ qua CloudWatch để kiểm tra audit trail

### Scalability và Performance Considerations
- **AWS Lambda**: tự động scale theo số lượng request.
- **SageMaker**: endpoint có thể dùng loại ml.t2.medium để tiết kiệm chi phí ban đầu, nhưng có thể nâng cấp sau.
- Có thể áp dụng **model optimization** (convert sang TorchScript .pt) để giảm thời gian inference.
- **Cache layer (tùy chọn)**: nếu kết quả ảnh giống nhau, có thể lưu result tạm trong Redis hoặc memory cache.
- **Cold start mitigation**: có thể giữ Lambda “warm” bằng cách gọi định kỳ (CloudWatch Event mỗi 5 phút).

### Integration Points với Existing Systems
- Hệ thống có thể tích hợp với:
  - Frontend React/Vue qua REST API
  - Mobile app (Flutter, React Native) để gọi ảnh và hiển thị kết quả
  - CI/CD pipeline: deploy mô hình mới lên SageMaker, update Lambda qua GitHub Actions
## 4. 🔧 Technical Implementation

### Implementation Phases và Deliverables
1. **Giai đoạn 1**: Huấn luyện và export mô hình MobileNetV2 (.pt)
2. **Giai đoạn 2**: Tạo và deploy SageMaker endpoint
3. **Giai đoạn 3**: Benchmark latency, cost, viết báo cáo
4. **Giai đoạn 4**: Triển khai, kiểm tra hiệu suất (1 tuần)

### Technical Requirements
- **Compute**: AWS Lambda (miễn phí 1 triệu lượt gọi mỗi tháng)
- **Storage**: DynamoDB (miễn phí 25GB bộ nhớ lưu trữ), S3 (miễn phí 5GB bộ nhớ lưu trữ)
- **Network**: IoT Core (MQTT, 2,000 tin nhắn Free Tier)
- **Ngôn ngữ**: Python 3.10
- **Framework**: PyTorch, TorchVision
- **AWS SDK**: boto3, sagemaker
- **Model format**: TorchScript (.pt)
- **API tool test**: Postman, curl
- **Cloud requirements**:
  - Quyền truy cập AWS (Lambda, SageMaker, S3, IAM)
  - Tối thiểu 1 endpoint active
  - Tài khoản trong free tier hoặc đã set budget

### Development Approach và Methodologies
- Áp dụng mô hình **Agile-lite**, chia thành 4–5 sprint nhỏ.
- Code theo hướng modular, tách riêng: training, deployment, inference logic.
- Ghi chú và log từng bước để có thể tái hiện pipeline end-to-end.
- Sử dụng Git + GitHub để quản lý source code và version control.

### Testing Strategy
- **Unit Testing**: kiểm thử từng module riêng biệt như image preprocessing, response parsing.
- **Integration Testing**: test toàn bộ flow từ ảnh → Lambda → SageMaker → trả kết quả.
- **Performance Testing**: đo thời gian phản hồi của Lambda và SageMaker.
- **Cost testing**: thử gọi 1000 requests → đo chi phí thực tế từ AWS Billing.

### Deployment Plan và Rollback Procedures
- **Triển khai**:
  - Tạo mô hình & export .pt
  - Deploy lên SageMaker bằng boto3 script
  - Tạo Lambda function và cấp quyền IAM
  - Kết nối Lambda qua API Gateway
- **Rollback**:
  - Nếu SageMaker lỗi: xóa endpoint, dùng lại bản model cũ
  - Nếu Lambda fail: deploy lại từ phiên bản trước trong GitHub hoặc AWS Console
  - Nếu API lỗi: rollback stage trong API Gateway hoặc disable route tạm thời

### Configuration Management
- Sử dụng .env hoặc config.json để quản lý các biến môi trường:
  - Endpoint name
  - Region AWS
  - IAM Role ARN
- Phân chia cấu hình theo môi trường: dev, prod (nếu cần)
- Tài liệu hóa toàn bộ bước setup môi trường để người khác có thể triển khai lại.
## 5. 📅 Timeline & Milestones

### Project Phases Breakdown
1. **Giai đoạn 1**: Cấu hình IAM Role cho Lambda (3 ngày)
  - **Mục tiêu**:  Đảm bảo Lambda chỉ có quyền tối thiểu để gọi SageMaker và đọc object từ S3, tuân theo nguyên tắc least privilege.
  - **Deliverables**: Terraform/IaC script cấu hình role và policy.
2. **Giai đoạn 2**: Bảo vệ API Gateway (3 ngày)
  - **Mục tiêu**: Ngăn truy cập trái phép và đảm bảo chỉ frontend có quyền truy cập API.
  - **Deliverables**: 
    - Thiết lập API Key hoặc xác thực qua Amazon Cognito.
    - Cấu hình CORS để cho phép frontend truy cập an toàn.
3. **Giai đoạn 3**: Bảo mật endpoint SageMaker (2 ngày)
  - **Mục tiêu**: Đảm bảo endpoint SageMaker không public, chỉ Lambda mới gọi được. 
  - **Deliverables**: Cấu hình VPC endpoint hoặc endpoint policy giới hạn quyền truy cập.
4. **Giai đoạn 4**: Thiết lập logging và auditing (2 ngày)
  - **Mục tiêu**: Theo dõi hoạt động inference, ghi nhận lỗi và hành vi truy cập.
  - **Deliverables**: Thiết lập CloudWatch Log Group, cấu hình thời gian lưu trữ và kiểm thử log với một vài request mẫu.

### Key Milestones và Success Criteria
- **Milestone 1**:  Hoàn thiện hạ tầng inference.
   - **Success Criteria**: Deploy thành công mô hình và Lambda trigger, test hoạt động đúng >90% các sample.
   - **Ngày hoàn thành dự kiến**: Ngày 14 sau khi bắt đầu dự án.

- **Milestone 2**: Tối ưu hóa performance inference.
   - **Success Criteria**: Đáp ứng thời gian inference trung bình <500ms/lần.
   - **Ngày hoàn thành dự kiến**: Ngày 21 sau khi bắt đầu dự án.

- **Milestone 3**:  Tích hợp frontend và báo cáo dự án.
   - **Success Criteria**: Frontend tương tác mượt, báo cáo hoàn chỉnh.
   - **Ngày hoàn thành dự kiến**: Ngày 28 sau khi bắt đầu dự án.

### Dependencies Identification
- AWS account với quyền tạo Lambda, SageMaker, API Gateway.
- Mạng ổn định trong suốt quá trình train và deploy model.
- Pretrained model MobileNetV2 (.pt) sẵn sàng.

### Critical Path Analysis
- Chuẩn hóa + convert model → Deploy SageMaker Endpoint → Setup Lambda trigger → Kiểm thử → Ghi log & báo cáo.

### Resource Allocation Plan
- **Nhân lực**: 1 sinh viên thực tập, 1 người hướng dẫn.
- **Công cụ**:  AWS Console, GitHub, Visual Studio Code, Terraform (hoặc AWS CLI), Postman.

### Buffer Time cho Risks
- Dự phòng +2 ngày cho các tình huống: lỗi triển khai model, quota AWS, Lambda timeout, hoặc sai CORS khi kết nối frontend.

## 6. 💰 Budget Estimation

### AWS Infrastructure Costs (Monthly/Annual)
- **Monthly**: Dự kiến 31.66 USD, bao gồm:
  - **SageMaker Endpoint**(ml.t2.medium – on-demand) nếu luôn mở: khoảng 28.16 USD
  - **AWS Lambda**: Miễn phí 1 triệu lượt gọi mỗi tháng.
  - **Amazon S3**: Miễn phí 5GB bộ nhớ lưu trữ và 20,000 lượt truy xuất mỗi tháng.
  - **DynamoDB**: 25GB bộ nhớ lưu trữ.
  - **AWS CloudWatch**: Miễn phí 5GB lưu trữ logs và 5GB dữ liệu gửi đi mỗi tháng.
  - **API Gateway**(REST API): 3.50 USD

- **Annually**:  
  - Khoảng 379.92 USD nếu dùng như trên mỗi tháng. 
  - Tuy nhiên, nếu tận dụng Free Tier, chi phí có thể giảm đáng kể trong 12 tháng đầu. 

### Development Costs (One-time)
- **Nhân sự phát triển**: Dự án được triển khai bởi một sinh viên thực tập trong vòng 3 tháng. Với giả định chi phí lao động là **5 USD/giờ**, tổng chi phí ước tính là:
  - **5 USD x 160 giờ/tháng x 3 tháng = 2,400 USD**
- **Công cụ & nền tảng phát triển**: Không phát sinh chi phí phần mềm hay phần cứng ngoài phạm vi Free Tier của AWS. Các công cụ như **GitHub**, **AWS Console**, **Terraform**(hoặc AWS CLI), và **Visual Studio Code** đều là **miễn phí** hoặc có phiên bản dành cho sinh viên.


### Third-party Services và Licenses
- **Third-party Services**: Trong phạm vi của dự án này, không yêu cầu bất kỳ dịch vụ bên ngoài nào ngoài AWS.
- **Licenses**: Không có phí cấp phép phát sinh, vì tất cả các dịch vụ AWS được sử dụng đều nằm trong phạm vi AWS Free Tier hoặc được tính phí theo mức độ sử dụng.

### Operational Costs (Ongoing)
- **Chi phí AWS hàng tháng**: 
  - **Monitoring**: Miễn phí trong mức Free Tier của CloudWatch (nếu dùng cẩn thận)
  - **Quản lý hạ tầng**: Không phát sinh chi phí nếu tự vận hành
- Chi phí vận hành có thể phát sinh nếu số lượng logs vượt quá mức Free Tier hoặc khi triển khai ở production scale.

### ROI Calculation và Break-even Analysis
- **Investment**: Khoảng 35 USD/tháng
  
- **Benefit**: 
  - Rút ngắn thời gian inference còn <500ms
  - Giảm khoảng 30% effort do không cần quản lý hạ tầng
  - Khả năng mở rộng linh hoạt và tái sử dụng mô hình cho các dự án tương lai

- Nếu dự án dùng thật sự trong môi trường sản xuất:
  - Chỉ cần phục vụ 1000+ users/tháng là đã tối ưu hơn self-hosting.
  - Break-even trong vòng 1–2 tháng do chi phí thấp và hiệu quả cao.

### Cost Optimization Strategies
- **Use smaller instance types**: thử ml.t3.medium hoặc spot instances nếu không cần 24/7.
- **Turn off endpoint khi không sử dụng**: tiết kiệm đến 70% chi phí SageMaker.
- Chuyển sang **Serverless Inference**(Async) nếu mô hình lớn hơn sau này.
- Thiết lập **CloudWatch Alarms** để giám sát chi phí và tối ưu theo thời gian.
Những chiến lược này giúp giảm chi phí đến 50–70%, đặc biệt trong giai đoạn phát triển và thử nghiệm.

## 7. ⚠️ Risk Assessment

### Risk Identification (Technical, Business, Operational)
1. **Technical Risks**:
  - **Độ trễ inference vượt quá 500ms**: Do cold start và đôi khi là lỗi cấu hình Lambda.
  - **Model không đủ chính xác**: Do thiếu dữ liệu huấn luyện hoặc preprocessing không đầy đủ.
  - **Giới hạn từ AWS Free Tier*: Nhanh chóng bị vượt qua nếu số lượng request tăng đột biến.

2. **Business Risks**:
  - **Dự án không được tiếp tục triển khai sau giai đoạn thử nghiệm**: Do không chứng minh được hiệu quả rõ ràng.
  - **Người dùng không thấy giá trị thực**: chưa rõ ràng sự khác biệt so với giải pháp cũ.

3. **Operational Risks**:
  - **Thiếu tài liệu và quy trình update model**: gây khó khăn khi vận hành.
  - **Không có hệ thống giám sát lỗi**: dẫn đến downtime không được phát hiện.
  - **Lỗi IAM cấu hình sai:** gây lỗ hổng bảo mật.

### Impact Assessment và Probability Analysis
- **Technical Risks**:
  - **Impact**: High — ảnh hưởng trực tiếp đến UX nếu inference bị chậm hoặc lỗi.
  - **Probability**: Medium — có thể tối ưu bằng cấu hình đúng và test kỹ.

- **Business Risks**:
  - **Impact**: Medium to high — ảnh hưởng tới việc có được chấp thuận hay không.
  - **Probability**: Medium — phụ thuộc vào cách trình bày ROI và kết quả demo.

- **Operational Risks**:
    - **Impact**: Medium — ảnh hưởng tới khả năng duy trì hệ thống lâu dài.
    - **Probability**: High — nếu team không có kinh nghiệm vận hành AWS.

### Risk Matrix với Prioritization
| Risk Type                    | Impact | Probability | Mitigation Strategy                             |
|------------------------------|--------|-------------|-------------------------------------------------|
| **Technical Risk**           |        |             |                                                 |
| Độ trễ inference > 500ms	   | High   | Medium      | Dùng provisioned concurrency, warm-up schedule  |
| Model không chính xác	       | High   | Medium      | Thu thập thêm dữ liệu, đánh giá kỹ trước deploy |
| Vượt AWS Free Tier	       | Medium | High        | Giới hạn số request khi test, tracking billing  |
| **Business Risk**            |        |             |                                                 |
| Dự án bị dừng sớm            | High   | Medium      | Chứng minh ROI rõ qua demo, số liệu đo lường    |
| Người dùng không adopt       | Medium | Medium      | Chứng minh ROI rõ qua demo, số liệu đo lường    |
| **Operational Risk**         |        |             |                                                 |
| Thiếu tài liệu update	       | Medium | Medium      | Viết guideline, checklist update định kỳ        |
| Không có hệ thống monitoring | High   | Medium      | Dùng CloudWatch, thiết lập alert threshold      |
| Cấu hình IAM sai	           | High   | Medium      | Audit định kỳ, dùng least-privilege IAM roles   |

### Mitigation Strategies cho Each Risk
- **Độ trễ inference vượt quá 500ms**:
  - Dùng Provisioned Concurrency để giảm cold start cho Lambda.
  - Tối ưu thời gian load model: chuyển từ .pth sang .pt, preload model trong global scope.
  - Caching kết quả inference nếu dữ liệu đầu vào trùng lặp.

- **Model không đủ chính xác**:
  - Cải thiện preprocessing: normalize ảnh, resize phù hợp với input size của MobileNetV2.
  - Dùng thêm dữ liệu huấn luyện (augmentation hoặc mở rộng tập dữ liệu).
  - Theo dõi confusion matrix, precision/recall để hiểu rõ điểm yếu của model.

- **Giới hạn từ AWS Free Tier**:
  - Thiết lập cảnh báo (Billing Alert) và giới hạn dùng.
  - Chuyển sang test bằng tài khoản sandbox hoặc chỉ bật tài nguyên khi cần.
  - Giới hạn số lượng concurrent requests khi demo.

- **Người dùng không thấy được giá trị vượt trội**:
  - Xây dựng dashboard/UX đơn giản nhưng ấn tượng, hiển thị tốc độ inference và chi phí tiết kiệm được.
  - Truyền thông tốt hơn về lợi ích "real-time" và serverless (zero maintenance).

- **Khó scale lên production nếu chưa có ngân sách**:
  - Đề xuất mô hình hybrid: test trên Lambda, scale lên SageMaker Endpoint khi cần.
  - Chứng minh chi phí theo từng giai đoạn (dev - test - prod) để dễ duyệt ngân sách.
    
- **Thiếu tài liệu vận hành**:
  - Viết log lại quy trình từ training → convert model → deploy Lambda.
  - Tạo README + sơ đồ pipeline model để team dễ follow.

- **Không có hệ thống giám sát lỗi**:
  - Tích hợp CloudWatch Logs, Alarms và X-Ray tracing ngay từ đầu.
  - Cảnh báo gửi về email/Slack khi function lỗi hoặc latency tăng.

- **Sai cấu hình IAM, gây lỗi bảo mật**:
  - Sử dụng chính sách Least Privilege.
  - Tách quyền giữa dev/test/prod rõ ràng.
  - Dùng IAM Role cho Lambda thay vì access key hardcode.

### Contingency Plans
- **Technical Risks**: Nếu latency vượt quá ngưỡng, fallback sang endpoint dự phòng hoặc tạm thời cache kết quả inference.
- **Business Risks**: Nếu không nhận được tài trợ, có thể chuyển sang mô hình open-source hoặc tối giản để duy trì POC.
- **Operational Risks**: Nếu hệ thống gặp sự cố, ưu tiên khôi phục bằng snapshot, log error và rollback version model gần nhất.

### Monitoring và Escalation Procedures
- **Monitoring**: 
  - Sử dụng AWS CloudWatch Metrics để theo dõi các chỉ số quan trọng như:
    - Lambda latency, invocation errors, cold start counts.
    - Model load time (custom metric nếu cần).
  - CloudWatch Alarms cảnh báo khi vượt ngưỡng định nghĩa (ví dụ latency > 400ms).
- **Escalation Procedures**: 
  - Các sự cố được phân loại theo mức độ nghiêm trọng:
    - Minor: Xử lý trong vòng 1–2h.
    - Medium: Ưu tiên cao, xử lý trong 30–60 phút.
    - Critical (ví dụ downtime): Immediate rollback, bật fallback endpoint, gửi alert.
  - Báo cáo nhanh qua email/Slack và ghi nhận trong log sự kiện để audit.

## 8. 🎯 Expected Outcomes

### Success Metrics
- Inference latency dưới 500ms cho 95% request.
- Độ chính xác mô hình (model accuracy) >= 90% với tập dữ liệu kiểm thử.
- Tỷ lệ uptime dịch vụ inference >= 99.9%.
- Chi phí vận hành không vượt quá $15/tháng với workload thử nghiệm.
- Thời gian phản hồi người dùng cuối giảm ít nhất 30% so với kiến trúc truyền thống (EC2-based).
- Tích hợp CI/CD cho deploy mô hình ML dưới 10 phút mỗi lần.

### Short-term Benefits (0-6 months)
- Triển khai nhanh chóng hệ thống inference nhờ hạ tầng serverless (Lambda, API Gateway).
- Tiết kiệm chi phí nhờ tận dụng AWS Free Tier.
- Khả năng mở rộng dễ dàng, phù hợp cho giai đoạn POC và thử nghiệm mô hình.
- Tăng tính tự động hóa trong quy trình MLOps nhờ tích hợp với GitHub và CloudWatch.

### Medium-term Benefits (6-18 months)
- Khả năng phục vụ inference real-time ổn định trong các hệ thống quy mô nhỏ đến trung bình.
- Dễ dàng tích hợp thêm các mô hình mới hoặc cập nhật phiên bản mà không cần downtime.
- Tiềm năng mở rộng sang các loại mô hình khác, như NLP, object detection.
- Xây dựng được pipeline CI/CD hoàn chỉnh cho mô hình ML trong doanh nghiệp nhỏ hoặc team nghiên cứu.

### Long-term Value (18+ months)
- Góp phần xây dựng nền tảng MLOps chuẩn hóa, giúp team tiết kiệm thời gian quản lý hạ tầng.
- Khả năng scale đến hàng nghìn request/ngày mà không cần đầu tư server vật lý.
- Tích lũy kiến thức thực tiễn để áp dụng cho các sản phẩm AI thương mại trong tương lai.
- Tăng tính cạnh tranh cho team/doanh nghiệp trong lĩnh vực tích hợp AI vào sản phẩm.

### User Experience Improvements
- Giao diện phản hồi nhanh hơn nhờ inference gần như tức thì.
- Trải nghiệm người dùng mượt mà, không bị gián đoạn khi hệ thống scale hoặc cập nhật mô hình.
- Phản hồi đầu ra rõ ràng, trực quan nhờ tích hợp thêm thông tin confidence score và thông báo kết quả.

### Strategic Capabilities Gained
- Hiểu biết thực tiễn về serverless architecture cho Machine Learning.
- Tăng cường năng lực triển khai real-time ML application trong các môi trường production.
- Kỹ năng tối ưu hóa chi phí vận hành ML, phục vụ các dự án quy mô vừa và nhỏ.
- Nâng cao kỹ năng DevOps và MLOps, giúp định hướng nghề nghiệp rõ ràng hơn trong lĩnh vực AI Engineering.