---
title: "Nhật ký công việc Tuần 12"
date: "2025-11-25"
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---

### Mục tiêu Tuần 12:

* **Tái cấu trúc Pipeline:** Hoàn tất quá trình chuyển đổi từ **Batch Export** sang **Real-time Log Streaming** (sử dụng Subscription Filters).
* **Bảo mật Mạng:** Cấu hình mạng **Lambda** (ENI) để đảm bảo ingestion dữ liệu an toàn bên trong **VPC**.
* **Nghiên cứu & Phát triển Nâng cao (NLP):** Đi sâu vào **Natural Language Processing** (Vector Spaces & Probabilistic Models) để phân tích ngữ nghĩa log.
* **Kết nối Ngành:** Cập nhật kiến thức về **AWS DevOps**, **IaC**, và các dịch vụ **Container** thông qua các workshop kỹ thuật.

### Các nhiệm vụ thực hiện trong tuần:

| Ngày | Nhiệm vụ | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| :--- | :--- | :--- | :--- | :--- |
| **Thứ 2 (25/11)** | **Chuyển hướng Kiến trúc (Batch to Streaming)**<br>- **Phân tích Thất bại:** Từ bỏ cách tiếp cận *CloudWatch to S3 to Lambda* (Batch) do giới hạn API và độ trễ cao.<br>- **Thành công:** Triển khai **CloudWatch Subscription Filters** để trigger **Lambda** trực tiếp (*CloudWatch to Lambda to S3*).<br>- **Lợi ích:** Đạt được độ trễ ingestion dữ liệu gần như thời gian thực (near real-time). | 25/11/2025 | 25/11/2025 | [Subscription Filters](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/SubscriptionFilters.html)<br>[Real-time Log Processing](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/SubscriptionFilters.html#LambdaFunctionExample) |
| **Thứ 3 (26/11)** | **Logic Xử lý Luồng (Lambda)**<br>- **Xử lý Dữ liệu:** Cập nhật code **Lambda** để xử lý streaming payload (được mã hóa Base64 & nén Gzip) từ CloudWatch.<br>- **Chuyển đổi:** Phân tích cú pháp (parse) các sự kiện raw log và định dạng chúng thành các dòng JSON trước khi đệm (buffering). | 26/11/2025 | 26/11/2025 | [Decompressing Log Data](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/SubscriptionFilters.html) |
| **Thứ 4 (27/11)** | **Tối ưu hóa Mạng & NLP Phần 1**<br>- **Hạ tầng:** Cấu hình **Lambda ENI** để truy cập an toàn các **S3 buckets** bên trong **VPC** (sử dụng Gateway Endpoints).<br>- **Khóa học:** Hoàn thành **NLP: Classification and Vector Spaces**. Nghiên cứu cách biểu diễn text logs thành các vector cho các mô hình học máy (machine learning). | 27/11/2025 | 27/11/2025 | [Lambda VPC Access](https://docs.aws.amazon.com/lambda/latest/dg/configuration-vpc.html)<br>[NLP Course 1](https://www.coursera.org/programs/fptu-fall-2025-zmahp/learn/classification-vector-spaces-in-nlp) |
| **Thứ 5 (28/11)** | **R&D Phân tích Nâng cao (NLP Phần 2)**<br>- **Khóa học:** Tiến tới **NLP: Probabilistic Models**. Nghiên cứu các mô hình ngôn ngữ Auto-correct và N-gram để phát hiện bất thường trong chuỗi log.<br>- **Ứng dụng:** Đánh giá tiềm năng tích hợp các mô hình xác suất để dự đoán lỗi hệ thống dựa trên các mẫu log. | 28/11/2025 | 28/11/2025 | [NLP Course 2](https://www.coursera.org/programs/fptu-fall-2025-zmahp/learn/probabilistic-models-in-nlp) |
| **Thứ 6 (29/11)** | **Workshop & Lập kế hoạch Đồ án**<br>- **Sự kiện:** Tham dự **"AWS Cloud Mastery Series #3 - Security Pillar Workshop"**.<br>- **Chủ đề chính:** CI/CD Pipeline, Infrastructure as Code (IaC), Container Services, và Observability.<br>- **Đồ án:** Nghiên cứu cấu trúc đề xuất kỹ thuật và bắt đầu soạn thảo **Final Project Proposal**. | 29/11/2025 | 29/11/2025 |  |

### Thành tựu Tuần 12:

* **Kiến trúc thành công Pipeline Real-time:**
    * Xác thực rằng **Streaming Pattern** (Subscription Filter) vượt trội hơn **Batch Pattern** (Export Task) cho trường hợp sử dụng cụ thể này.
    * Giảm độ trễ ingestion dữ liệu từ phút/giờ xuống còn **mili giây**.

* **Tiếp thu Kỹ năng Nâng cao (AI/ML):**
    * Xây dựng nền tảng học thuật vững chắc về **Natural Language Processing** (Vector Spaces, Probabilistic Models), chuẩn bị cho việc triển khai các tính năng "Smart Log Analysis".

* **Mở rộng Năng lực Cloud:**
    * Có được cái nhìn toàn diện về hệ sinh thái **DevOps** trên AWS (CI/CD, IaC, Containers) thông qua workshop Cloud Mastery, hỗ trợ chiến lược vận hành cho dự án cuối cùng.