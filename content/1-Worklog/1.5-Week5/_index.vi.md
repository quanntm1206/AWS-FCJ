---
title: "Nhật ký công việc Tuần 5"
date: "2025-10-06"
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Mục tiêu Tuần 5:

* **Tuân thủ Đám mây (Cloud Compliance):** Hiểu về các tiêu chuẩn bảo mật tài chính (OSPAR) và phạm vi tuân thủ của AWS.
* **Quản lý Danh tính & Truy cập (IAM):** Xử lý sự cố Trust Relationships và làm chủ Permission Boundaries.
* **Kiểm soát Truy cập Nâng cao:** Triển khai Kiểm soát truy cập dựa trên thuộc tính (ABAC) và Bảo mật theo ngữ cảnh (Context-Aware Security - điều kiện IP/Thời gian).
* **Bảo mật Dữ liệu:** Mã hóa dữ liệu khi nghỉ (at rest) với AWS KMS và kiểm toán truy cập thông qua CloudTrail & Athena.

### Các nhiệm vụ thực hiện trong tuần:
| Ngày | Nhiệm vụ | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| **Thứ 2 (6/10)** | **Nghiên cứu Tuân thủ (Blog 3):** <br> - **Chủ đề:** Báo cáo OSPAR 2025 & Phạm vi Dịch vụ AWS. <br> - **Nhiệm vụ:** Đã dịch Blog "OSPAR 2025 report now available with 170 services...". <br> - **Bài học chính:** Hiểu các hướng dẫn bảo mật cho các tổ chức tài chính sử dụng dịch vụ đám mây. | 06/10/2025 | 06/10/2025 | [Original Blog](https://aws.amazon.com/vi/blogs/security/ospar-2025-report-now-available-with-170-services-in-scope-based-on-the-newly-enhanced-ospar-v2-0-guidelines/) <br> [My Translation](https://docs.google.com/document/d/13-kZadS-z_8CVrHl8gdwBpnqOZeLTsWN71rHNkkYto4/edit?tab=t.0#heading=h.klgwyn9uayj) |
| **Thứ 3 (7/10)** | **Lý thuyết Module 5:** <br> - Nghiên cứu các khái niệm cốt lõi IAM: Users, Groups, Roles, Policies. <br> - Phân tích Mô hình Trách nhiệm Chia sẻ (Shared Responsibility Model) & Cấu trúc Policy (Effect, Action, Resource, Condition). <br> - Nghiên cứu các thực hành tốt nhất về Nguyên tắc Đặc quyền Tối thiểu (Principle of Least Privilege). | 07/10/2025 | 07/10/2025 | [Module 05-01](https://youtu.be/tsobAlSg19g) <br> [Module 05-02](https://youtu.be/N_vlJGAqZxo) <br> [Module 05-03](https://youtu.be/pZ2fgEFK3Vs) <br> [Module 05-04](https://youtu.be/5oQY8Rogz9Y) <br> [Module 05-05](https://youtu.be/NW1xrMkNMjU?si=W15z-7egjukm0Wih) <br> [Module 05-06](https://www.youtube.com/watch?v=GMihNQojhZc&t=1s) <br> [Module 05-07](https://youtu.be/clj2E0rNBEs?si=sOugbG2fLHk1XI7R) <br> [Module 05-08](https://youtu.be/0SdpD2GPYz4?si=UB09iE84xU7BSVky) |
| **Thứ 4 (8/10)** | **Lab 18 & Lab 22: Security Hub & IAM Troubleshooting** <br> - **Lab 18:** Kích hoạt AWS Security Hub để tự động hóa các kiểm tra bảo mật. <br> - **Lab 22:** Sửa lỗi giả mạo Role (Role assumption failure) bằng cách điều chỉnh **Trust Policy** để cho phép đúng Principal. | 08/10/2025 | 09/10/2025 | https://000018.awsstudygroup.com/ <br> https://000022.awsstudygroup.com/ |
| **Thứ 6 (10/10)** | **Lab 27 & 28: Gán thẻ Tài nguyên & Kiểm soát Truy cập** <br> - **Lab 27:** Tổ chức EC2 instances sử dụng Tags và tạo Resource Groups để lọc hiệu quả. <br> - **Lab 28 (ABAC):** Cấu hình IAM Policies để hạn chế các hành động EC2 dựa trên Tags. <br>&emsp; + *Kiểm thử:* Xác minh quyền truy cập người dùng qua các Regions (Tokyo vs N. Virginia) dựa trên sự khớp Tag. | 10/10/2025 | 10/10/2025 | https://000027.awsstudygroup.com/ <br> https://000028.awsstudygroup.com/ |
| **Thứ 7 (11/10)** | **Lab 30, 33 & 44: Quản trị Nâng cao & Bảo mật Ngữ cảnh** <br> - **Lab 30:** Triển khai **IAM Permission Boundaries** để giới hạn nghiêm ngặt quyền tối đa của người dùng. <br> - **Lab 33:** Mã hóa dữ liệu S3 bằng AWS KMS và kiểm toán các sự kiện giải mã thông qua Athena. <br> - **Lab 44:** Cấu hình **IAM Roles với Conditions** để hạn chế truy cập dựa trên Source IPs cụ thể và khung thời gian (ví dụ: chỉ giờ hành chính). | 11/10/2025 | 12/10/2025 | https://000030.awsstudygroup.com/ <br> https://000033.awsstudygroup.com/ <br> https://000044.awsstudygroup.com/ |


### Thành tựu Tuần 5:

* **Triển khai Bảo mật theo Ngữ cảnh (Context-Aware Security):**
    * Đã vượt qua các quyền tiêu chuẩn bằng cách áp dụng **IAM Conditions** (Lab 44), hạn chế thành công các Admin Roles chỉ được giả mạo (assume) từ các địa chỉ IP tin cậy cụ thể và trong khung thời gian quy định.

* **Tăng cường Quản trị Bảo mật:**
    * Đã áp dụng **IAM Permission Boundaries** (Lab 30) để tạo một "mức trần" cho các quyền, ngăn chặn các quản trị viên được ủy quyền tự leo thang đặc quyền của chính họ.
    * Triển khai **Attribute-Based Access Control (ABAC)** (Lab 28) sử dụng Resource Tags để quản lý quyền động.

* **Mã hóa Dữ liệu & Kiểm toán:**
    * Đã bảo mật dữ liệu nhạy cảm trong S3 sử dụng **AWS KMS** (Lab 33) để mã hóa khi nghỉ (at rest).
    * Tích hợp **CloudTrail** và **Athena** để thực hiện phân tích điều tra số (forensic analysis), theo dõi chính xác ai đã truy cập dữ liệu được mã hóa và vào thời điểm nào.