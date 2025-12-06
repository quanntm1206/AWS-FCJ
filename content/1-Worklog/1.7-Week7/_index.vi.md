---
title: "Nhật ký công việc Tuần 7"
date: "2025-10-20"
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---
### Mục tiêu Tuần 7:

* **Mạng Nâng cao (Advanced Networking):** Làm chủ kết nối VPC (Peering so với Transit Gateway) và phân giải Hybrid DNS.
* **Các thực hành tốt nhất về Bảo mật:** Triển khai IAM Roles cho EC2 để thực thi truy cập "Least Privilege" (Đặc quyền tối thiểu).
* **Lưu trữ Lai (Hybrid Storage):** Triển khai các giải pháp lưu trữ cho Windows workloads (FSx) và mở rộng lưu trữ on-premise lên cloud (Storage Gateway).
* **Bảo vệ Dữ liệu & Di chuyển:** Tự động hóa sao lưu tập trung và thực hiện di chuyển VM theo kiểu "Lift-and-Shift".

### Các nhiệm vụ thực hiện trong tuần:
| Ngày | Nhiệm vụ | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| **Thứ 2 (20/10)** | **Cơ bản về Mạng & Bảo mật** <br> - **Lab 19 (VPC Peering):** Thiết lập kết nối mạng trực tiếp giữa hai VPC, cấu hình Route Tables, và kích hoạt Cross-Peer DNS Resolution. <br> - **Lab 48 (IAM Roles):** Thay thế Access Keys cứng bằng IAM Roles gắn vào EC2 instances để bảo mật quyền truy cập ứng dụng vào S3. | 22/09/2025 | 22/09/2025 | https://000019.awsstudygroup.com/ <br> https://000048.awsstudygroup.com/ |
| **Thứ 3 (21/10)** | **Lab 20: Mạng Nâng cao với Transit Gateway** <br> - **Kiến trúc:** Triển khai topo mạng Hub-and-Spoke kết nối 4 VPC sử dụng một Transit Gateway (TGW) duy nhất. <br> - **Định tuyến:** Cấu hình TGW Route Tables để tập trung hóa quản lý lưu lượng, thay thế các kết nối peering lưới phức tạp. | 23/09/2025 | 23/09/2025 | https://000020.awsstudygroup.com/ |
| **Thứ 4 (22/10)** | **Lab 10: Kết nối Lai với Route 53 Resolver** <br> - **Hybrid DNS:** Cấu hình Inbound và Outbound Endpoints để phân giải tên miền giữa AWS VPC và mạng On-premise. <br> - **Tích hợp:** Triển khai Microsoft Active Directory để mô phỏng phân giải DNS on-premise. | 24/09/2025 | 24/09/2025 | https://000010.awsstudygroup.com/ |
| **Thứ 5 (23/10)** | **Lab 25: Amazon FSx for Windows File Server** <br> - **Triển khai:** Tạo một Native Windows File System được quản lý hoàn toàn, tích hợp với Microsoft Active Directory. <br> - **Tính năng:** Ánh xạ SMB file shares tới Windows instances và kích hoạt Data Deduplication/Shadow Copies để tối ưu lưu trữ. | 25/09/2025 | 25/09/2025 | https://000025.awsstudygroup.com/ |
| **Thứ 6 (24/10)** | **Tự động hóa Lưu trữ Lai & Sao lưu** <br> - **Lab 24 (Storage Gateway):** Triển khai File Gateway để ánh xạ NFS/SMB shares cục bộ trực tiếp tới S3 buckets để mở rộng lưu trữ cloud không giới hạn. <br> - **Lab 13 (AWS Backup):** Tạo một Backup Plan tập trung để tự động hóa bảo vệ cho tài nguyên EBS, RDS, và EFS với thông báo SNS. | 26/09/2025 | 26/09/2025 | https://000024.awsstudygroup.com/ <br> https://000013.awsstudygroup.com/ |
| **Thứ 7 (25/10)** | **Lab 14: Chiến lược Di chuyển (Lift & Shift)** <br> - **VM Import/Export:** Export một Virtual Machine cục bộ (VMware), upload image lên S3, và chuyển đổi thành Amazon Machine Image (AMI). <br> - **Xác thực:** Khởi chạy một EC2 instance mới từ AMI đã import, xác minh khả năng di chuyển workload. | 27/09/2025 | 27/09/2025 | https://000014.awsstudygroup.com/ |


### Thành tựu Tuần 3:

* **Thiết kế Kiến trúc Mạng Có khả năng mở rộng:**
    * Chuyển đổi từ **VPC Peering** đơn giản (Lab 19) sang kiến trúc **Transit Gateway** có khả năng mở rộng (Lab 20), giảm đáng kể độ phức tạp định tuyến cho môi trường đa VPC.
    * Giải quyết thách thức **Hybrid DNS** sử dụng **Route 53 Resolver**, cho phép khám phá dịch vụ liền mạch giữa Cloud và On-premise.

* **Làm chủ Lưu trữ & Bảo vệ Dữ liệu:**
    * Triển khai lưu trữ chuyên dụng cho Windows workloads sử dụng **Amazon FSx** và mở rộng dung lượng on-prem bằng **Storage Gateway**.
    * Thiết lập nền tảng Disaster Recovery vững chắc bằng cách tự động hóa sao lưu thông qua **AWS Backup**.

* **Thực hiện Di chuyển lên Cloud:**
    * Thực hiện thành công việc di chuyển **"Lift and Shift"** (Lab 14), xác thực lộ trình kỹ thuật để di chuyển các máy ảo cũ (legacy) sang AWS EC2 mà không cần tái cấu trúc.