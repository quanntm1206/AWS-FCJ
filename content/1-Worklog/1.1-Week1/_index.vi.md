---
title: "Nhật ký công việc Tuần 1"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### Mục tiêu Tuần 1:

* **Kiến thức nền tảng Cloud:** Hiểu về Hạ tầng toàn cầu AWS (Global Infrastructure), Tính giá (Pricing), các gói Support Plans, và bảo mật cơ bản (IAM).
* **Cốt lõi về Networking:** Nắm vững kiến trúc VPC (Subnets, Routing, Security Groups/NACLs) và Cân bằng tải (Load Balancing).
* **Bài thực hành (Hands-on Labs):** Thiết lập tài khoản, Quản lý chi phí, xây dựng VPC, và xử lý sự cố kết nối VPN.

### Các nhiệm vụ thực hiện trong tuần:
| Ngày | Nhiệm vụ | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| **Thứ 3 (9/9)** | **Module 1 & Labs 1, 7, 9:** <br> - **Lý thuyết:** Các khái niệm Điện toán đám mây, Regions/AZs, Tối ưu hóa chi phí (Budgets), Support Plans. <br> - **Thực hành:** <br>&emsp; + Tạo & Bảo mật tài khoản AWS (MFA, IAM User). <br>&emsp; + Cấu hình AWS Budgets (Cost, Usage, RI). <br>&emsp; + Mở các yêu cầu hỗ trợ (Support Cases). | 09/09/2025 | 09/09/2025 | [Module 01-01 - Điện Toán Đám Mây Là Gì?](https://youtu.be/HxYZAK1coOI?si=4xf1yZmepR82emMd) <br> [Module 01-02 - Điều Gì Tạo Nên Sự Khác Biệt Của AWS?](https://youtu.be/IK59Zdd1poE?si=X5Qao9OxMLUvpBYg) <br> [Module 01-03 - Bắt Đầu Hành Trình Lên Mây Như Thế Nào](https://youtu.be/HSzrWGqo3ME?si=r478_UihmyCTKcQ3) <br> [Module 01-04 - Hạ Tầng Toàn Cầu Của AWS](https://youtu.be/pjr5a-HYAjI?si=_QqGDOBJy_1c6WUe) <br> [Module 01-05 - Công Cụ Quản Lý AWS Services](https://youtu.be/2PQYqH_HkXw?si=DKIEZLPrSbzEtRvh) <br> [Module 01-06 - Tối Ưu Hóa Chi Phí Trên AWS...](https://youtu.be/IY61YlmXQe8?si=taziN3scWc-corP6) <br> [Module 01-07 - Thực Hành và Nghiên Cứu Bổ Sung](https://youtu.be/Hku7exDBURo?si=715J5Yl4OjkLVEfj) <br> [Lab 1](https://000001.awsstudygroup.com/) <br> [Lab 7](https://000007.awsstudygroup.com/) <br> [Lab 9](https://000009.awsstudygroup.com/) |
| **Thứ 5 (11/9)** | **Module 2 & Lab 3:** <br> - **Lý thuyết:** VPC, Subnets, Route Tables, IGW/NGW, Bảo mật (SG vs NACL), ELB (ALB/NLB/GLB). <br> - **Thực hành:** <br>&emsp; + Xây dựng mạng VPC từ đầu (from scratch). <br>&emsp; + Khởi chạy EC2 (Amazon Linux 2023). <br>&emsp; + Giải quyết thành công các vấn đề về kết nối. | 11/09/2025 | 11/09/2025 | [Module 02-01 - AWS Virtual Private Cloud](https://youtu.be/O9Ac_vGHquM?si=1bFj633qq7EvfLhi) <br> [Module 02-02 - VPC Security and Multi-VPC features](https://youtu.be/BPuD1l2hEQ4?si=LrrKAww4vVeK74eE) <br> [Module 02-03 - VPN - DirectConnect - LoadBalancer...](https://youtu.be/CXU8D3kyxIc?si=ju2OidhffNpSfWZ6) <br> [Lab 3](https://000003.awsstudygroup.com/) |
| **Thứ 7 (13/9)** | **Lab 4: Thiết lập VPN Site-to-Site** <br> - Cấu hình Customer Gateway & VPN Tunnel. <br> - **Xử lý sự cố (Troubleshooting):** <br>&emsp; + Cài đặt `libreswan` cho Amazon Linux 2023. <br>&emsp; + Điều chỉnh lệnh: sử dụng `systemctl` thay vì `service`. <br>&emsp; + Ghi chú: Đã phát hiện sự không khớp giữa hướng dẫn và Console thực tế. | 13/09/2025 | 13/09/2025 | [Lab 4](https://000004.awsstudygroup.com/) |


### Thành tựu Tuần 1:

* **Nắm vững Kiến thức nền tảng Cloud & Bảo mật:**
    * Hiểu rõ mô hình "Pay-as-you-go" và Hạ tầng toàn cầu AWS (Region, AZ, Edge Locations).
    * Đã bảo mật tài khoản Root với MFA và thiết lập các IAM users cho công việc hàng ngày.
    * Phân loại được các gói Support Plans (Basic đến Enterprise) và sử dụng AWS Budgets để kiểm soát chi phí.

* **Đào sâu vào Networking (VPC):**
    * Thiết kế các mạng cô lập về mặt logic sử dụng VPC, Subnets (Public/Private), và Route Tables.
    * Phân biệt rõ giữa Security Groups (Stateful) và NACLs (Stateless).
    * Hiểu các tùy chọn kết nối: IGW (Internet), NGW (Outbound only), và VPC Peering/Transit Gateway.

* **Kinh nghiệm Xử lý sự cố Thực tế:**
    * Thích nghi thành công với môi trường **Amazon Linux 2023** (chuyển đổi từ Amazon Linux 2).
    * Giải quyết các khác biệt về quản lý dịch vụ (sử dụng `systemd-networkd` / `systemctl`).
    * Tích lũy kinh nghiệm cấu hình các thành phần Site-to-Site VPN (Customer Gateway).