---
title: "Nhật ký công việc Tuần 2"
date: "2025-09-15"
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Mục tiêu Tuần 2:

* **Làm chủ Tính toán & Lưu trữ:** Tìm hiểu sâu về các họ EC2, Mô hình giá (Pricing models), và các giải pháp Lưu trữ (EBS, EFS, FSx).
* **Cơ sở dữ liệu & Di chuyển:** Hiểu về tích hợp RDS và các công cụ di chuyển Lift-and-Shift (MGN).
* **Lab 5 Nâng cao:** Triển khai ứng dụng 2-Tier (Node.js + RDS) trên Amazon Linux 2023 với quy trình xử lý sự cố nghiêm ngặt.
* **Chi phí & Bảo mật:** Triển khai các chính sách IAM để kiểm soát chi phí và giới hạn tài nguyên.

### Các nhiệm vụ thực hiện trong tuần:
| Ngày | Nhiệm vụ | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| **Thứ 2 (15/9)** | **Module 3: Đi sâu vào EC2, Lưu trữ & Di chuyển** <br> - Phân tích các họ Instance (Intel/AMD vs Graviton/ARM) và lợi ích của Nitro Hypervisor. <br> - So sánh các Mô hình giá: On-Demand, Reserved, Savings Plans, và Spot Instances (tích hợp Auto Scaling). <br> - **Lưu trữ:** Phân biệt EBS (Persistent) vs Instance Store (Ephemeral/NVMe). Tìm hiểu các trường hợp sử dụng cho EFS (Linux shared) vs FSx (Windows/HPC). <br> - **Di chuyển:** Nghiên cứu AWS MGN (Application Migration Service) để sao chép liên tục và chuyển đổi (cutover). | 15/09/2025 | 16/09/2025 | [Module 03-01](https://youtu.be/-t5h4N6vfBs?si=3XX1N0oZI8bndOxK) <br> [Module 03-01-01](https://youtu.be/e7XeKdOVq40?si=6mI_xS_XKjEhwLax) <br> [Module 03-01-02](https://youtu.be/yAR6QRT3N1k?si=ZDgGBWoLCkIoJEvi) <br> [Module 03-01-03](https://youtu.be/hKr_TfGP7NY?si=tuFUwHJ5wdKJGs0X) <br> [Module 03-01-04](https://youtu.be/6IHNDJ85aoQ?si=BlBvt0hONt5SKsTD) <br> [Module 03-01-05](https://youtu.be/_v_43Wi7zjo?si=6skGCPHSBU2xeJRV) <br> [Module 03-01-06](https://youtu.be/Ew3QRaKJQSA?si=yjHJyTCDH9cK_iXq) <br> [Module 03-01-07](https://youtu.be/bbLcPitXJSY?si=ATvs418bGA-SFuAl) <br> [Module 03-02](https://youtu.be/hFVYG8WqfU0?si=bP8gy4OhylbDx6u1) |
| **Thứ 4 (17/9)** | **Quản lý & Bảo mật EC2:** <br> - **Thực hành:** Tạo Custom AMI, EBS Snapshots, và kiểm thử Instance Recovery. <br> - **Kiểm soát chi phí:** Cấu hình IAM Policies để giới hạn Region, Instance Type, và thực thi các quy tắc dựa trên IP/Thời gian. | 17/09/2025 | 17/09/2025 | |
| **Thứ 5 (18/9)** | **Lab 5: Amazon Relational Database Service (Amazon RDS)** <br> - Thiết kế mạng VPC và Security Groups (giao tiếp giữa EC2 & RDS). <br> - Cấp phát RDS (MySQL) và Amazon Linux 2023 instance (chuyển sang `t3.micro` do `t2.micro` không khả dụng). <br> - Xử lý lỗi timeout của Customer Gateway trong quá trình thiết lập SSH. <br> - **Triển khai Ứng dụng:** Thiết lập ứng dụng Quản lý người dùng Node.js. <br> - **Xử lý sự cố (Troubleshooting):** <br>&emsp; + Sửa lỗi `npm start` (cập nhật `package.json`). <br>&emsp; + Giải quyết lỗi cài đặt MySQL trên AL2023 bằng cách kết nối trực tiếp đến RDS endpoint. <br>&emsp; + Tạo DB Users và cấp quyền thông qua các lệnh SQL. <br> - Khám phá Amazon Lightsail cho các nhu cầu máy chủ ảo đơn giản. <br> - Ôn tập quy trình triển khai cho cả Windows Server 2022 và Linux. <br> - Dọn dẹp tài nguyên để tránh phát sinh chi phí. | 18/09/2025 | 20/09/2025 | https://000005.awsstudygroup.com/ |


### Thành tựu Tuần 2:

* **Hoàn thành xuất sắc Lab 5 (Kiến trúc 2-Tier):**
    * Triển khai thành công ứng dụng Node.js hoạt động hoàn chỉnh kết nối với cơ sở dữ liệu RDS MySQL.
    * Xác minh toàn bộ chức năng của ứng dụng (Đăng ký/Đăng nhập/Truy xuất dữ liệu) sau khi giải quyết các vấn đề kết nối.

* **Giải quyết các vấn đề tương thích trên Amazon Linux 2023:**
    * Thích nghi với các ràng buộc hạ tầng bằng cách nâng cấp từ `t2.micro` lên `t3.micro`.
    * Xác định rằng `mysql-community-server` và `mariadb105` không ổn định/thiếu trên AL2023.
    * Tái cấu trúc kết nối cơ sở dữ liệu để trỏ trực tiếp đến **RDS Endpoint**, bỏ qua các vấn đề proxy cục bộ.

* **Quản lý EC2 & Cơ sở dữ liệu nâng cao:**
    * Thành thạo việc tạo **Custom AMIs** và **EBS Snapshots** để sao lưu/phục hồi.
    * Quản lý thành công người dùng RDS Database: Tạo người dùng ứng dụng cụ thể (`appuser`) và cấp các quyền chi tiết (`GRANT ALL`) để bảo mật.
    * Áp dụng **IAM Policies** nghiêm ngặt để giới hạn việc tạo tài nguyên (giới hạn Region/Type), đảm bảo không phát sinh chi phí ngoài ý muốn.