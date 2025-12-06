---
title: "Nhật ký công việc Tuần 6"
date: "2025-10-13"
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---
### Mục tiêu Tuần 6:

* **Kiến thức nền tảng về Cơ sở dữ liệu:** Ôn tập các khái niệm cốt lõi như Chuẩn hóa (Normalization), Đánh chỉ mục (Indexing), và các mô hình ACID so với BASE.
* **Cơ sở dữ liệu Quan hệ được Quản lý:** Làm chủ kiến trúc Amazon RDS và Aurora.
* **Lưu trữ Web Tĩnh:** Triển khai các website tĩnh trên S3 và bảo mật chúng bằng các cấu hình Public Access Block.
* **Mạng Phân phối Nội dung (CDN):** Phân tích các ràng buộc kiến trúc khi tích hợp CloudFront với S3 Website Endpoints.
* **Quản lý Sự cố:** Tài liệu hóa các phụ thuộc hạ tầng và giải quyết các xung đột cấu hình.

### Các nhiệm vụ thực hiện trong tuần:
| Ngày | Nhiệm vụ | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| **Thứ 2 (13/10)** | **Lý thuyết Module 6: Các dịch vụ Cơ sở dữ liệu AWS** <br> - **Các khái niệm cốt lõi:** RDBMS vs. NoSQL, PK/FK, Indexing, Partitioning. <br> - **RDS & Aurora:** Sao lưu tự động (Automated backups), Multi-AZ cho tính sẵn sàng cao (HA), Read Replicas. <br> - **Redshift & ElastiCache:** Kho dữ liệu (Data Warehousing) và các chiến lược bộ nhớ đệm In-memory. | 13/10/2025 | 13/10/2025 | [Module 06-01](https://youtu.be/OOD2RwWuLRw?si=zjAdvLgGv-_4N0Py) <br> [Module 06-02](https://youtu.be/qbrobQZrokY?si=HGRY-XhKWkr83Fod) <br> [Module 06-03](https://youtu.be/UvdiRW34aNI?si=vc11G0NB6erHFvRQ) |
| **Thứ 3 (14/10)** | **Lab 43: Kế hoạch Thực hiện & Báo cáo Sự cố** <br> - **Hoạt động:** Lên lịch thực hiện Lab 43. <br> - **Sự cố:** Cổng thông tin tài liệu dịch vụ không khả dụng (Lỗi HTTP 5xx/Timeout). <br> - **Hành động:** Đánh dấu là "Lỗi Phụ thuộc Bên ngoài" (External Dependency Failure). Ghi nhận sự cố và chuyển hướng sang tự nghiên cứu các khái niệm AWS liên quan trong khi chờ giải quyết. | 14/10/2025 | 14/10/2025 | https://000043.awsstudygroup.com/ |
| **Thứ 4 (15/10)** | **Lab 57: Tích hợp S3 Static Website & CloudFront** <br> - **Phần 1 (Thành công):** Hoàn thành thiết lập S3, kích hoạt Static Website Hosting, cấu hình Bucket Policy cho quyền đọc công khai (Các bước 1-6). <br> - **Phần 2 (Vấn đề Nghiêm trọng):** Cố gắng tăng tốc trang web với CloudFront (Bước 7.2). <br> - **Phân tích Nguyên nhân Gốc rễ:** Xác định xung đột kiến trúc: Hướng dẫn yêu cầu sử dụng **OAI/OAC** với một **S3 Website Endpoint**, điều này không được AWS hỗ trợ. <br> - **Chiến lược Giải quyết:** Xác định rằng S3 Website Endpoints phải được xử lý như "Custom Origins" (không có OAC), hoặc chuyển sang S3 Origin tiêu chuẩn để sử dụng OAC. | 15/10/2025 | 15/10/2025 | https://000057.awsstudygroup.com/ |
| **Thứ 5 (16/10)** | **Tinh chỉnh Tài liệu** <br> - **Nhiệm vụ:** Tái cấu trúc nhật ký công việc hàng tuần để phù hợp với các tiêu chuẩn báo cáo chuyên nghiệp (Markdown/Hugo). <br> - **Mục tiêu:** Cải thiện khả năng đọc, cấu trúc và tính nhất quán trên tất cả các báo cáo trước đó. | 16/10/2025 | 16/10/2025 |  |
| **Thứ 6 (17/10)** | **Nghỉ phép (Việc gia đình)**  | 17/10/2025 | 18/10/2025 |  |


### Thành tựu Tuần 6:

* **Đào sâu vào Kiến trúc CloudFront:**
    * Đã triển khai thành công một Website Tĩnh trên Amazon S3 với quyền đọc công khai.
    * **Bài học Quan trọng:** Khám phá ra rằng **Origin Access Control (OAC)** KHÔNG tương thích với **S3 Website Endpoints**.
    * Phân tích sự khác biệt giữa **S3 REST API Endpoints** (hỗ trợ OAC/OAI để bảo mật) so với **S3 Website Endpoints** (yêu cầu cấu hình Custom Origin).

* **Quản lý Sự cố & Rủi ro:**
    * Thể hiện khả năng thích ứng bằng cách xử lý các lỗi tài liệu bên ngoài (Lab 43) mà không làm gián đoạn tiến độ.
    * Đối chiếu hướng dẫn lab với Tài liệu AWS chính thức để xác định các lỗi cấu hình nghiêm trọng trước khi triển khai.

* **Tài liệu Chuyên nghiệp:**
    * Chuẩn hóa toàn bộ nhật ký thực tập, đảm bảo định dạng trình bày sạch sẽ, dễ bảo trì và chuyên nghiệp bằng Markdown.