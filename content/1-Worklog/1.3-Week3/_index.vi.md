---
title: "Nhật ký công việc Tuần 3"
date: "2025-09-22"
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Mục tiêu Tuần 3:

* **Các thực hành tốt nhất về Bảo mật:** Chuyển đổi từ Access Keys dài hạn sang IAM Roles (IMDSv2) để bảo mật EC2.
* **Lưu trữ lai & Di chuyển:** Triển khai các giải pháp Hybrid Cloud sử dụng Storage Gateway và VM Import/Export.
* **Chiến lược Bảo vệ Dữ liệu:** Tự động hóa sao lưu tập trung với AWS Backup và làm chủ Disaster Recovery (RTO/RPO).
* **Lưu trữ Nâng cao:** Nắm vững S3 Storage Classes, Lifecycle Management, và Snow Family.
* **Quản lý Sự cố:** Kinh nghiệm thực tế trong việc xử lý sự cố tạm ngưng tài khoản (account suspension) và làm việc với AWS Support.

### Các nhiệm vụ thực hiện trong tuần:
| Ngày | Nhiệm vụ | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| **Thứ 2 (22/9)** | **Lab 48: Cấp quyền cho ứng dụng truy cập dịch vụ AWS bằng IAM role.** <br> - **Kịch bản 1:** Cấu hình AWS CLI sử dụng Access Key/Secret Key (Mô phỏng phương pháp cũ). <br> - **Kịch bản 2 (Best Practice):** Tạo IAM Role với S3 Policy và gắn vào EC2 để tận dụng Instance Metadata (IMDSv2). <br> - **Kiểm toán:** Xem lại CloudTrail để kiểm tra việc sử dụng thông tin xác thực. | 22/09/2025 | 22/09/2025 | https://000048.awsstudygroup.com/ |
| **Thứ 3 (23/9)** | **Lab 24: Sử dụng File Storage Gateway** <br> - Triển khai File Gateway Appliance trên EC2. <br> - Cấu hình NFS/SMB file shares ánh xạ trực tiếp đến một S3 Bucket. <br> - **Xác minh:** Mount file shares trên máy trạm (client machine) và kiểm tra độ trễ đọc/ghi. | 23/09/2025 | 23/09/2025 | https://000024.awsstudygroup.com/ |
| **Thứ 4 (24/9)** | **Lab 25: Amazon FSx for Windows File Server** <br> - **Lab 25:** Xử lý sự cố và sửa CloudFormation templates để triển khai stack. <br> - **Sự cố:** Tài khoản AWS bị tạm ngưng đột ngột. <br> - **Hành động:** Đã gửi Support Ticket #1 liên quan đến trạng thái tài khoản và xác minh thanh toán. | 24/09/2025 | 24/09/2025 | https://000025.awsstudygroup.com/ |
| **Thứ 5 (25/9)** | **Module 4: Các khái niệm cốt lõi S3 & Hybrid Storage** <br> - **Kiến trúc:** S3 Buckets, Objects, và độ bền 11 số 9 (Multi-AZ). <br> - **Storage Classes:** Phân tích đánh đổi chi phí/hiệu năng: Standard, Intelligent-Tiering, Standard-IA, One Zone-IA, và Glacier/Deep Archive. <br> - **Snow Family & Gateway:** Nghiên cứu các công cụ di chuyển dữ liệu offline (Snowball Edge) và các loại Storage Gateway (File/Volume/Tape). <br> - **Disaster Recovery:** Định nghĩa RTO/RPO và so sánh các chiến lược DR (Pilot Light vs Warm Standby). | 25/09/2025 | 27/09/2025 | [Module 04-01](https://youtu.be/hsCfP0IxoaM?si=MUhp_BIJabumvMNc) <br> [Module 04-02](https://youtu.be/_yunukwcAwc?si=eFjVimOndHJO2_x1) <br> [Module 04-03](https://youtu.be/mPBjB6Ltl_Q?si=5kiObguWl9zNLOUJ) <br> [Module 04-04](https://youtu.be/YXn8Q_Hpsu4?si=ZGjYozwcw6693G8i) |
| **Thứ 6 (26/9)** | **Lab 13: Triển khai AWS Backup cho hệ thống** <br> - **Tự động hóa:** Tạo Backup Plan tập trung cho các tài nguyên EBS, RDS, và EFS. <br> - **Thông báo:** Cấu hình SNS topics để cảnh báo quản trị viên về trạng thái sao lưu. <br> - **Xác thực:** Thực hiện "Test Restore" để xác minh tính toàn vẹn dữ liệu và khả năng RTO. | 26/09/2025 | 26/09/2025 | https://000013.awsstudygroup.com/ |
| **Thứ 7 (27/9)** | **Lab 14: VM Import/Export** <br> - **Chuẩn bị:** Thiết lập VMWare Workstation và môi trường AWS CLI. <br> - **Di chuyển:** Export ảnh máy ảo (VM image) cục bộ và tải lên S3 Bucket. <br> - **Triển khai:** Import VM image thành một AMI và khởi chạy EC2 instance mới (Mô phỏng quy trình di chuyển "Lift and Shift"). | 27/09/2025 | 27/09/2025 | https://000014.awsstudygroup.com/ |


### Thành tựu Tuần 3:

* **Triển khai Mô hình Bảo mật Least Privilege:**
    * Đã chuyển đổi thành công ứng dụng từ việc sử dụng Access Keys hard-coded sang sử dụng **IAM Roles**.
    * Đã xác minh rằng việc sử dụng IAM Roles loại bỏ rủi ro rò rỉ thông tin xác thực và đơn giản hóa việc xoay vòng khóa (key rotation).

* **Năng lực về Hybrid Cloud & Di chuyển:**
    * Đã cấu hình **Storage Gateway** để mở rộng lưu trữ on-premise lên S3 một cách liền mạch.
    * Đã thực hiện thành công quy trình **Lift-and-Shift Migration** (Lab 14) bằng cách import một Virtual Machine cục bộ vào AWS EC2, xác thực lộ trình di chuyển cho các workload cũ (legacy).

* **Tự động hóa Bảo vệ Dữ liệu & Khả năng phục hồi:**
    * Đã triển khai chiến lược **AWS Backup** tập trung (Lab 13) bao phủ nhiều loại tài nguyên (EBS, RDS).
    * Đã xác thực khả năng sẵn sàng Disaster Recovery bằng cách thực hiện test khôi phục thành công và thiết lập **SNS Notifications** để giám sát chủ động.

* **Kinh nghiệm Quản lý Sự cố:**
    * Tích lũy kinh nghiệm thực tế trong việc xử lý các vấn đề nghiêm trọng về **Tạm ngưng tài khoản (Account Suspension)**.
    * Đã học được quy trình giao tiếp hiệu quả với AWS Support, cung cấp log và tài liệu xác minh cần thiết để khôi phục dịch vụ.