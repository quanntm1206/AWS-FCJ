---
title: "Nhật ký công việc Tuần 8"
date: "2000-01-01"
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---
### Mục tiêu Tuần 8:

* **Bảo mật Nâng cao:** Triển khai bảo mật nhiều lớp với mã hóa (KMS, ACM) và bảo vệ tại biên (WAF, Shield).
* **Hồ dữ liệu Serverless:** Xây dựng cấu trúc phân tích không máy chủ (serverless) sử dụng Amazon S3 để lưu trữ và Amazon Athena để truy vấn.
* **Mạng Toàn cầu:** Tối ưu hóa việc phân phối nội dung và độ trễ sử dụng Route 53, Global Accelerator và CloudFront.
* **Quản trị Chi phí:** Làm chủ các công cụ phân tích chi phí (Cost Explorer, Budgets) và các chiến lược quản lý đa tài khoản.

### Các công việc thực hiện trong tuần:
| Ngày | Công việc | Ngày Bắt đầu | Ngày Hoàn thành | Tài liệu Tham khảo |
| --- | --- | --- | --- | --- |
| Thứ Hai (27/10) | **Các Dịch vụ Bảo mật Nâng cao** <br> - **Ôn tập:** Tổng hợp toàn diện các dịch vụ AWS cốt lõi (EC2, VPC, IAM, S3, RDS). <br> - **Mã hóa Dữ liệu:** Cấu hình **AWS KMS** (Key Management Service) để mã hóa dữ liệu khi nghỉ (at rest) và **AWS ACM** cho chứng chỉ SSL/TLS. | 20/10/2025 | 20/10/2025 | [EC2 User Guide](https://docs.aws.amazon.com/pdfs/AWSEC2/latest/UserGuide/ec2-ug.pdf) <br> [VPC User Guide](https://docs.aws.amazon.com/pdfs/vpc/latest/userguide/vpc-ug.pdf) <br> [IAM User Guide](https://docs.aws.amazon.com/pdfs/IAM/latest/UserGuide/iam-ug.pdf) <br> [S3 User Guide](https://docs.aws.amazon.com/pdfs/AmazonS3/latest/userguide/s3-userguide.pdf) <br> [RDS User Guide](https://docs.aws.amazon.com/pdfs/AmazonRDS/latest/UserGuide/rds-ug.pdf)<br> [KMS Developer Guide](https://docs.aws.amazon.com/pdfs/kms/latest/developerguide/kms-dg.pdf) <br> [ACM User Guide](https://docs.aws.amazon.com/pdfs/acm/latest/userguide/acm-ug.pdf) |
| Thứ Ba (28/10) | **Bảo vệ tại Biên (Edge):** Triển khai **AWS WAF** và **AWS Shield** để giảm thiểu các cuộc tấn công DDoS/Web exploits. <br> - **Phát hiện Mối đe dọa:** Phân tích các phát hiện từ **Amazon GuardDuty** và tích hợp **AWS Secrets Manager** để xoay vòng thông tin xác thực. **R&D Dự án: Phân tích Dữ liệu Serverless** <br> - **Lớp Lưu trữ:** Cấu trúc các bucket **Amazon S3** thành Data Lake (Hồ dữ liệu) để tổng hợp log. <br> - **Công cụ Truy vấn:** Sử dụng **Amazon Athena** để chạy các truy vấn SQL tiêu chuẩn trực tiếp trên dữ liệu S3 mà không cần cấp phép máy chủ. <br> - **Khả năng quan sát:** Cấu hình **CloudWatch** để giám sát các chỉ số (metrics) và nhật ký (logs). | 21/10/2025 | 21/10/2025 |[WAF Developer Guide](https://docs.aws.amazon.com/pdfs/waf/latest/developerguide/waf-dg.pdf) <br> [AMS User Guide (GuardDuty)](https://docs.aws.amazon.com/pdfs/managedservices/latest/userguide/ams-ug.pdf) <br> [RDS Guide (Secrets Manager)](https://docs.aws.amazon.com/pdfs/AmazonRDS/latest/UserGuide/rds-ug.pdf)<br> [S3 User Guide](https://docs.aws.amazon.com/pdfs/AmazonS3/latest/userguide/s3-userguide.pdf) <br> [S3 API Reference](https://docs.aws.amazon.com/pdfs/AmazonS3/latest/API/s3-api.pdf) |
| Thứ Tư (29/10) | **Mạng & Mở rộng Tính toán** <br> - **Lưu lượng Toàn cầu:** Cấu hình **Amazon Route 53** (DNS Failover) và **AWS Global Accelerator** để truy cập độ trễ thấp cho người dùng. <br> - **CDN:** Tối ưu hóa phân phối nội dung với **Amazon CloudFront**. <br> - **Tính toán Serverless:** Triển khai các hàm trên **AWS Lambda** và container trên **AWS Fargate**. <br> - **Hiệu suất Lưu trữ:** So sánh chế độ thông lượng giữa **EBS Provisioned IOPS** và **Amazon EFS**. | 22/10/2025 | 22/10/2025 |[Route 53 Guide](https://docs.aws.amazon.com/pdfs/Route53/latest/DeveloperGuide/route53-dg.pdf) <br> [Global Accelerator Guide](https://docs.aws.amazon.com/pdfs/global-accelerator/latest/dg/global-accelerator-guide.pdf) <br> [CloudFront Guide](https://docs.aws.amazon.com/pdfs/AmazonCloudFront/latest/DeveloperGuide/AmazonCloudFront_DevGuide.pdf) <br> [Lambda Developer Guide](https://docs.aws.amazon.com/pdfs/lambda/latest/dg/lambda-dg.pdf) <br> [ECS Guide (Fargate)](https://docs.aws.amazon.com/pdfs/AmazonECS/latest/developerguide/ecs-dg.pdf) |
| Thứ Năm (30/10) | **Tối ưu hóa Chi phí & Quản trị** <br> - **Phân tích:** Trực quan hóa xu hướng chi tiêu bằng **AWS Cost Explorer** và thiết lập cảnh báo qua **AWS Budgets**. <br> - **Chiến lược Giá:** Đánh giá giữa **Savings Plans** (Gói tiết kiệm) vs **Reserved Instances** (Phiên bản đặt trước) vs **Spot Instances**. <br> - **Đa tài khoản:** Quản lý các chính sách sử dụng **AWS Organizations**. <br> **Ôn tập Tương tác: AWS Card Clash** <br> - **Hoạt động:** Sử dụng trò chơi "AWS Card Clash 3D" để mô phỏng việc ra quyết định kiến trúc. <br> - **Lợi ích:** Củng cố tư duy lựa chọn dịch vụ và hiểu rõ sự tương tác giữa các dịch vụ trong môi trường game hóa. | 23/10/2025 | 23/10/2025 | [Cost Management Guide](https://docs.aws.amazon.com/pdfs/cost-management/latest/userguide/cost-management-guide.pdf) <br> [Savings Plans Guide](https://docs.aws.amazon.com/pdfs/savingsplans/latest/userguide/savingsplans.pdf) <br> [EC2 Purchasing Options](https://docs.aws.amazon.com/pdfs/AWSEC2/latest/UserGuide/ec2-ug.pdf) <br> [Organizations Guide](https://docs.aws.amazon.com/pdfs/organizations/latest/userguide/organizations-userguide.pdf) <br> [AWS Card Clash](https://arcade.cardclash.training.aws.dev/) |
| Thứ Sáu (31/10) | **Ngày Đánh giá Cuối cùng** <br> - **Cột mốc:** Tham gia thành công Kỳ thi Cuối khóa. <br> - **Kết quả:** Thể hiện năng lực về Kiến trúc Đám mây AWS và triển khai Dịch vụ. | 31/10/2025 | 31/10/2025 | |

### Thành tựu Tuần 8:

* **Năng lực Bảo mật Nâng cao:**
    * Nâng cấp từ tường lửa cơ bản sang triển khai bảo mật nhiều lớp với **AWS WAF** (Lớp ứng dụng - Layer 7) và **AWS Shield** (Bảo vệ chống DDoS).
    * Bảo mật dữ liệu nhạy cảm khi nghỉ (at rest) sử dụng **KMS Customer Master Keys (CMKs)**.

* **Thành thạo Kiến trúc Serverless:**
    * Thiết kế một stack phân tích có khả năng mở rộng cao, không cần bảo trì sử dụng **S3 + Athena**, loại bỏ nhu cầu về các máy chủ ETL truyền thống.
    * Hiểu rõ sự đánh đổi giữa **Lambda** (Hướng sự kiện) và **Fargate** (Container chạy dài hạn).

* **Quản lý Chi phí Chiến lược:**
    * Phân biệt được sự linh hoạt của **Savings Plans** so với sự cứng nhắc của Reserved Instances để tối ưu hóa chi phí tính toán dài hạn.
    * Sử dụng **Cost Explorer** để xác định và loại bỏ sự lãng phí tài nguyên.