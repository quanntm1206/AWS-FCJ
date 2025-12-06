---
title: "Nhật ký công việc Tuần 10"
date: "2025-11-10"
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---
### Mục tiêu Tuần 10:

* **Tối ưu hóa Chi phí:** Tái cấu trúc Data Pipeline từ Athena ETL sang AWS Lambda để giảm chi phí vận hành.
* **Triển khai ChatOps:** Tích hợp AWS GuardDuty với Slack để giám sát mối đe dọa theo thời gian thực (real-time threat monitoring).
* **Vận hành Xuất sắc (Operational Excellence):** Tùy chỉnh payload thông báo để hiển thị tốt hơn và xử lý các sự cố "Alert Fatigue" (Mệt mỏi vì cảnh báo).
* **Kỹ thuật Dữ liệu (Data Engineering):** Giải quyết các vấn đề schema mismatch bằng cách chuẩn hóa định dạng dữ liệu sang JSONL.

### Các nhiệm vụ thực hiện trong tuần:

| Ngày | Nhiệm vụ | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| :--- | :--- | :--- | :--- | :--- |
| **Thứ 2 (10/11)** | **Tái cấu trúc Pipeline (Tối ưu Chi phí)**<br>- **Quyết định:** Di chuyển từ Athena ETL sang **AWS Lambda** để xử lý log nhằm giảm thiểu chi phí.<br>- **Vấn đề:** Gặp lỗi **Schema Mismatch** (field mix-up) khi raw logs không thể parse chính xác vào cấu trúc đích.<br>- **Trạng thái:** Đang tiến hành điều tra. | 10/11/2025 | 10/11/2025 | [Lambda Pricing](https://aws.amazon.com/lambda/pricing/)<br>[Athena Pricing](https://aws.amazon.com/athena/pricing/) |
| **Thứ 3 (11/11)** | **Tích hợp ChatOps & Xử lý Sự cố**<br>- **Thiết lập:** Cấu hình **AWS Chatbot** để tích hợp SNS với Slack Channel.<br>- **Sự cố:** Kích hoạt "Alert Storm" (1000+ emails) do đồng đội kích hoạt tất cả **GuardDuty Sample Findings** cùng lúc.<br>- **Phản hồi:** Tinh chỉnh SNS subscription filters để quản lý nhiễu (noise). | 11/11/2025 | 11/11/2025 | [GuardDuty Findings](https://docs.aws.amazon.com/guardduty/latest/ug/guardduty_findings.html) |
| **Thứ 4 (12/11)** | **Tối ưu hóa Payload Thông báo (Lambda)**<br>- **Kiểm tra UX:** Nhận thấy thông báo Slack mặc định thiếu ngữ cảnh quan trọng (Severity Level) trong chế độ xem trước/thu gọn.<br>- **Coding:** Cập nhật **logic Lambda** để parse raw findings và xây dựng một **Custom Message Payload**.<br>- **Kết quả:** Các trường quan trọng (Severity, Region, Type) hiện đã hiển thị ngay lập tức mà không cần mở ứng dụng. | 12/11/2025 | 12/11/2025 | |
| **Thứ 5 (13/11)** | **Khắc phục Data Pipeline (Phần 1)**<br>- **Gỡ lỗi:** Phân tích lỗi "field mix-up" từ Thứ 2.<br>- **Nguyên nhân gốc:** Các mảng JSON tiêu chuẩn gây ra sự cố ingest với SerDe của Athena.<br>- **Chiến lược Giải pháp:** Quyết định chuyển đổi định dạng luồng dữ liệu sang **JSONL (Newline Delimited JSON)**. | 13/11/2025 | 13/11/2025 | |
| **Thứ 6 (14/11)** | **Khắc phục Data Pipeline (Phần 2)**<br>- **Triển khai:** Cập nhật logic Lambda để serialize các log đã xử lý thành file `.jsonl`.<br>- **Xác thực:** Đẩy thành công dữ liệu đã làm sạch lên S3 và truy vấn thủ công qua Athena mà không gặp lỗi schema.<br>- **Kết quả:** Pipeline hiện đã hoạt động và tối ưu chi phí. | 14/11/2025 | 14/11/2025 |  |
| **Thứ 7 (15/11)** | **Sự kiện: “AWS Cloud Mastery Series #1 - AI/ML/GenAI on AWS”**<br>- Giới thiệu về AI/ML/GenAI trên AWS. | 15/11/2025 | 15/11/2025 | |

### Thành tựu Tuần 10:

* **Xây dựng Data Pipeline Tối ưu Chi phí:**
    * Đã thay thế thành công phương pháp Athena ETL đắt đỏ bằng giải pháp **Lambda-based** nhẹ nhàng hơn.
    * Giải quyết vấn đề phức tạp về **JSON Parsing/Schema Mismatch** bằng cách triển khai **JSONL serialization**, đảm bảo ingest dữ liệu liền mạch vào Data Lake.

* **Thiết lập ChatOps Mạnh mẽ:**
    * Xây dựng hệ thống thông báo mối đe dọa thời gian thực: **GuardDuty $\to$ EventBridge $\to$ SNS $\to$ AWS Chatbot $\to$ Slack**.
    * **Tối ưu hóa UX:** Tùy chỉnh định dạng thông báo để hiển thị **Severity** ngay lập tức, giảm đáng kể "Mean Time To Know" (MTTK) cho các cảnh báo bảo mật.

* **Kinh nghiệm Quản lý Sự cố:**
    * Học được bài học giá trị về **Alert Fatigue** khi xử lý 1000+ sample findings, củng cố tầm quan trọng của việc lọc SNS và quy trình kiểm thử phù hợp.