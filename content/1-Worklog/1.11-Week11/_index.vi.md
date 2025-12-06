---
title: "Nhật ký công việc Tuần 11"
date: "2025-11-17"
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---
### Mục tiêu Tuần 11:

* **Tự động hóa ETL:** Nâng cao "CloudWatch ETL Lambda" để hỗ trợ tự động thay đổi schema (Auto-Create Table) và thực thi hướng sự kiện (Event-driven).
* **Nghiên cứu Pipeline (R&D):** Điều tra các phương pháp để tự động hóa CloudWatch Log Exports (Batch Ingestion) so với Streaming.
* **Đánh đổi Kiến trúc:** Đánh giá EventBridge Scheduler so với Subscription Filters cho việc thu thập dữ liệu.
* **Phân tích Sự cố:** Xử lý các vấn đề tương thích giữa Real-time Streaming (Subscription Filters) và định dạng Batch Processing.

### Các nhiệm vụ thực hiện trong tuần:

| Ngày | Nhiệm vụ | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| :--- | :--- | :--- | :--- | :--- |
| **Thứ 2 (17/11)** | **Sự kiện: “AWS Cloud Mastery Series #2 - DevOps on AWS”**<br>- Giới thiệu AWS DevOps Services – CI/CD Pipeline.<br>- Giới thiệu Infrastructure as Code (IaC) và các công cụ liên quan.<br>- Giới thiệu Container Services trên AWS. <br> - Đảm bảo khả năng Giám sát (Monitoring) và Quan sát (Observability) sử dụng AWS Services. | 17/11/2025 | 17/11/2025 | |
| **Thứ 3 (18/11)** | **Nâng cấp Pipeline ETL (Kiến trúc Hướng sự kiện)**<br>- **Tính năng:** Nâng cấp code **CloudWatch ETL Lambda** để tự động phát hiện schema và thực thi DDL (Create Table) nếu bảng Athena bị thiếu.<br>- **Tự động hóa:** Cấu hình **S3 Event Notifications** để trigger Lambda này ngay khi đối tượng được tạo (`s3:ObjectCreated:*`), loại bỏ nhu cầu kích hoạt thủ công. | 18/11/2025 | 18/11/2025 |  |
| **Thứ 4 (19/11)** | **Phân tích Lỗ hổng Thu thập (Nghiên cứu Auto-Export)**<br>- **Lỗ hổng:** Nhận thấy CloudWatch Logs yêu cầu kích hoạt thủ công để export ra S3.<br>- **Nghiên cứu:** Điều tra **Amazon EventBridge Scheduler** để trigger API `create_export_task` định kỳ.<br>- **Trạng thái:** Giai đoạn Proof of Concept (PoC). | 19/11/2025 | 19/11/2025 |  |
| **Thứ 5 (20/11)** | **Chuyển hướng Kiến trúc & Phân tích Thất bại**<br>- **Chuyển hướng:** Thử nghiệm sử dụng **CloudWatch Subscription Filters** như một giải pháp thay thế đơn giản hơn cho EventBridge.<br>- **Thất bại:** Pipeline bị vỡ vì Subscription Filters stream dữ liệu (base64 encoded real-time stream), trong khi ETL Lambda hiện tại mong đợi các file log dạng batch (.gz).<br>- **Quyết định:** Quay lại chiến lược Batch Export. | 20/11/2025 | 20/11/2025 | [Subscription Filters](https://youtu.be/KRwDInHmgQY?si=4VrwITz_bgjgk_uN) |
| **Thứ 6 (21/11)** | **Khắc phục Thu thập (Thử lại EventBridge)**<br>- **Hành động:** Tiếp tục kiểm thử với EventBridge Scheduler để trigger Log Exports.<br>- **Thách thức:** Gặp phải các vấn đề về quyền IAM và Lambda timeout trong quá trình thực thi trigger export.<br>- **Kết quả:** Giải pháp hiện tại **không ổn định/đang chờ giải quyết**. Tiếp tục debug qua cuối tuần. | 21/11/2025 | 22/11/2025 |  |

### Thành tựu Tuần 11:

* **Lambda & Tự động hóa Nâng cao:**
    * Đã chuyển đổi thành công quy trình ETL thành một workflow hoàn toàn **Event-Driven**. Giờ đây, dữ liệu được xử lý ngay lập tức khi đến Data Lake (S3), giảm độ trễ dữ liệu.
    * Triển khai **Quản lý Schema Tự động** bên trong Lambda (Auto-Create Athena Table), giảm gánh nặng vận hành khi triển khai sang môi trường mới.

* **Đào sâu Kiến trúc (Streaming vs Batch):**
    * Có được sự hiểu biết sâu sắc về sự khác biệt giữa **Log Streaming** (Subscription Filters - Kinesis/Lambda) và **Log Export** (S3 Batch).
    * Xác thực rằng "Streaming" yêu cầu logic xử lý hoàn toàn khác (Stream decoding) so với "Batching" (File parsing), dẫn đến các quyết định kiến trúc sáng suốt.