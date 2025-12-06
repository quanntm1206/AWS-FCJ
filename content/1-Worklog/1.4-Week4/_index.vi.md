---
title: "Nhật ký công việc Tuần 4"
date: "2025-09-29"
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu Tuần 4:

* **Khả năng quan sát & Giám sát:** Nắm vững "Ba trụ cột của Khả năng quan sát" trên AWS: Logs (CloudTrail), Metrics (CloudWatch), và Traces/Traffic (VPC Flow Logs).
* **Tự động hóa Ứng phó sự cố:** Hiểu cách liên kết CloudWatch Alarms với SNS để kích hoạt cảnh báo tự động.
* **Phân tích Bảo mật:** Học cách truy vấn nhật ký kiểm toán (audit logs) bằng Amazon Athena và phát hiện mối đe dọa với GuardDuty.
* **Kiến thức cơ bản về Serverless:** Giới thiệu về AWS Lambda và Systems Manager.
* **Khởi động Dự án:** Bắt đầu nghiên cứu kiến trúc dự án và dịch các bài blog kỹ thuật chuyên sâu.

### Các nhiệm vụ thực hiện trong tuần:
| Ngày | Nhiệm vụ | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| **Thứ 2 (29/9)** | **Các yếu tố cốt lõi của Ứng phó sự cố:** <br> - **CloudTrail:** Cấu hình trails để kiểm toán hoạt động người dùng và các lệnh gọi API. <br> - **CloudWatch:** Thiết lập Metrics và Alarms (các ngưỡng CPU/Network). <br> - **VPC Flow Logs:** Thu thập lưu lượng IP để khắc phục sự cố mạng. <br> - **SNS:** Thiết lập các topic thông báo để kích hoạt cảnh báo. | 29/09/2025 | 29/09/2025 | [CloudWatch Metrics](https://youtu.be/Yxl7e88cTAQ) <br> [VPC Flow Logs](https://youtu.be/_qM6ilKz3C8) <br> [CloudWatch Alarms](https://youtu.be/3v_X53RmYf0) <br> [SNS Setup](https://youtu.be/j5Xp51eUyXE) <br> [CloudTrail Basics](https://youtu.be/CXbdsp9ThvM) |
| **Thứ 3 (30/9)** | **Phân tích Nâng cao & Serverless:** <br> - **Athena:** Truy vấn logs CloudTrail trong S3 bằng SQL để điều tra các sự kiện cụ thể. <br> - **GuardDuty:** Khám phá các cơ chế phát hiện mối đe dọa thông minh. <br> - **Compute:** Giới thiệu về AWS Lambda (Serverless) và Systems Manager (Tự động hóa Ops). | 30/09/2025 | 30/09/2025 | [AWS Lambda Intro](https://youtu.be/eOBq__h4OJ4) <br> [Systems Manager](https://youtu.be/pSVK-ingvfc) <br> [GuardDuty Deep Dive](https://www.youtube.com/watch?v=Wkpl66NaqEA) <br> [CloudTrail with Athena](https://youtu.be/I4vYkrHq5hs) |
| **Thứ 4 (1/10)** | **Tự học & Ôn tập:** <br> - Củng cố kiến thức về các công cụ Giám sát (Monitoring tools). <br> - Chuẩn bị môi trường cho Dự án sắp tới. | 01/10/2025 | 01/10/2025 ||
| **Thứ 5 (2/10)** | **Kiến trúc Dự án & Dịch thuật:** <br> - **Dự án:** Nghiên cứu và phân tích kiến trúc đề xuất cho dự án thực tập. <br> - **Blog 1:** Đã dịch bài "Democratizing quantum resources: University of Michigan and AWS collaborate on a remote access quantum testbed". | 02/10/2025 | 02/10/2025 | [Blog gốc](https://aws.amazon.com/vi/blogs/publicsector/democratizing-quantum-resources-university-of-michigan-and-aws-collaborate-on-a-remote-access-quantum-testbed/) <br> [Bản dịch của tôi](https://docs.google.com/document/d/1SAgaxbJU1wQMvoegtjcIjG0iNRnHMAaOlaZg5VzcaXk/edit?tab=t.0) |
| **Thứ 6 (3/10)** | **Sự kiện: AI-Driven Development Life Cycle: Reimagining Software Engineering** <br> - Generative AI đang biến các lập trình viên thành biên tập viên, chuyển trọng tâm từ viết mã sang review mã. <br> - AI-DLC là nơi AI thực hiện các giai đoạn viết mã và kiểm thử, chuyển vai trò của con người từ viết cú pháp sang định nghĩa ý định kinh doanh và xác thực đầu ra của AI. <br> Trình diễn Kiro và Amazon Q Developer. | 03/10/2025 | 03/10/2025 | |
| **Thứ 7 (4/10)** | **Streaming Dữ liệu Nâng cao (Blog 2):** <br> - **Chủ đề:** Apache Kafka Disaster Recovery & Migration. <br> - **Nhiệm vụ:** Đã dịch Blog "Amazon MSK Replicator and MirrorMaker2". <br> - **Bài học chính:** Các chiến lược sao chép (Replication strategies), cấu hình Active-Active vs Active-Passive. | 04/10/2025 | 04/10/2025 | [Blog gốc](https://aws.amazon.com/vi/blogs/big-data/amazon-msk-replicator-and-mirrormaker2-choosing-the-right-replication-strategy-for-apache-kafka-disaster-recovery-and-migrations/) <br> [Bản dịch của tôi](https://docs.google.com/document/d/11JuanGg4j-wQ8khxs8xU23GkNEaO-xmhJlYNLc4Q6H8/edit?tab=t.0) |


### Thành tựu Tuần 4:

* **Làm chủ bộ công cụ AWS Observability:**
    * Phân biệt rõ vai trò của **CloudTrail** (Kiểm toán/Ai đã làm gì?) so với **CloudWatch** (Hiệu suất/Hệ thống đang chạy thế nào?).
    * Hiểu các giới hạn về chi phí/lưu trữ của CloudTrail (mặc định 90 ngày) và sự cần thiết của việc xuất ra S3 để tuân thủ quy định dài hạn.

* **Phân tích Bảo mật & Điều tra số (Forensic Analysis):**
    * Đã học cách sử dụng **Amazon Athena** để chạy các truy vấn SQL trực tiếp trên dữ liệu log trong S3, giảm đáng kể thời gian cần thiết để điều tra các sự cố bảo mật.
    * Đã cấu hình **SNS** để tách biệt việc giám sát khỏi việc cảnh báo, cho phép nhiều người đăng ký (Email, Lambda, SMS) phản ứng với cùng một cảnh báo.

* **Dịch thuật Kỹ thuật & Nghiên cứu:**
    * Mở rộng vốn từ vựng kỹ thuật thông qua việc dịch các chủ đề phức tạp (Quantum Computing & Kafka Replication).
    * Có được cái nhìn sâu sắc về các kiến trúc lai (hybrid architectures) như MSK Replicator và các hợp tác học thuật trên nền tảng đám mây.