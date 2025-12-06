---
title: "Nhật ký công việc Tuần 8"
date: "2025-10-27"
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---
### Các nhiệm vụ thực hiện trong tuần:
| Ngày | Nhiệm vụ | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| **Thứ 2 (27/10)** | **Các Dịch vụ Bảo mật Nâng cao** <br> - **Ôn tập:** Củng cố toàn diện các dịch vụ cốt lõi của AWS (EC2, VPC, IAM, S3, RDS). <br> - **Mã hóa Dữ liệu:** Cấu hình **AWS KMS** (Key Management Service) để mã hóa dữ liệu khi nghỉ (at rest) và **AWS ACM** cho chứng chỉ SSL/TLS. | 20/10/2025 | 20/10/2025 | [EC2 User Guide](https://docs.aws.amazon.com/pdfs/AWSEC2/latest/UserGuide/ec2-ug.pdf) <br> [VPC User Guide](https://docs.aws.amazon.com/pdfs/vpc/latest/userguide/vpc-ug.pdf) <br> [IAM User Guide](https://docs.aws.amazon.com/pdfs/IAM/latest/UserGuide/iam-ug.pdf) <br> [S3 User Guide](https://docs.aws.amazon.com/pdfs/AmazonS3/latest/userguide/s3-userguide.pdf) <br> [RDS User Guide](https://docs.aws.amazon.com/pdfs/AmazonRDS/latest/UserGuide/rds-ug.pdf)<br> [KMS Developer Guide](https://docs.aws.amazon.com/pdfs/kms/latest/developerguide/kms-dg.pdf) <br> [ACM User Guide](https://docs.aws.amazon.com/pdfs/acm/latest/userguide/acm-ug.pdf) |
| **Thứ 3 (28/10)** | **Bảo vệ Biên (Edge Protection):** Triển khai **AWS WAF** và **AWS Shield** để giảm thiểu các cuộc tấn công DDoS/Web. <br> - **Phát hiện Mối đe dọa:** Phân tích các phát hiện từ **Amazon GuardDuty** và tích hợp **AWS Secrets Manager** để xoay vòng thông tin xác thực. **Nghiên cứu & Phát triển Dự án: Phân tích Dữ liệu Serverless** <br> - **Lớp Lưu trữ:** Cấu trúc các bucket **Amazon S3** thành Data Lake để tổng hợp log. <br> - **Công cụ Truy vấn:** Sử dụng **Amazon Athena** để chạy các truy vấn SQL tiêu chuẩn trực tiếp trên dữ liệu S3 mà không cần cấp phát máy chủ. <br> - **Khả năng quan sát:** Cấu hình **CloudWatch** để giám sát metrics và logs. | 21/10/2025 | 21/10/2025 |[WAF Developer Guide](https://docs.aws.amazon.com/pdfs/waf/latest/developerguide/waf-dg.pdf) <br> [AMS User Guide (GuardDuty)](https://docs.aws.amazon.com/pdfs/managedservices/latest/userguide/ams-ug.pdf) <br> [RDS Guide (Secrets Manager)](https://docs.aws.amazon.com/pdfs/AmazonRDS/latest/UserGuide/rds-ug.pdf)<br> [S3 User Guide](https://docs.aws.amazon.com/pdfs/AmazonS3/latest/userguide/s3-userguide.pdf) <br> [S3 API Reference](https://docs.aws.amazon.com/pdfs/AmazonS3/latest/API/s3-api.pdf) |
| **Thứ 4 (29/10)** | **Mạng & Mở rộng Tính toán** <br> - **Lưu lượng Toàn cầu:** Cấu hình **Amazon Route 53** (DNS Failover) và **AWS Global Accelerator** để truy cập người dùng với độ trễ thấp. <br> - **CDN:** Tối ưu hóa phân phối nội dung với **Amazon CloudFront**. <br> - **Tính toán Serverless:** Triển khai các function trên **AWS Lambda** và container trên **AWS Fargate**. <br> - **Hiệu năng Lưu trữ:** So sánh các chế độ thông lượng giữa **EBS Provisioned IOPS** so với **Amazon EFS**. | 22/10/2025 | 22/10/2025 |[Route 53 Guide](https://docs.aws.amazon.com/pdfs/Route53/latest/DeveloperGuide/route53-dg.pdf) <br> [Global Accelerator Guide](https://docs.aws.amazon.com/pdfs/global-accelerator/latest/dg/global-accelerator-guide.pdf) <br> [CloudFront Guide](https://docs.aws.amazon.com/pdfs/AmazonCloudFront/latest/DeveloperGuide/AmazonCloudFront_DevGuide.pdf) <br> [Lambda Developer Guide](https://docs.aws.amazon.com/pdfs/lambda/latest/dg/lambda-dg.pdf) <br> [ECS Guide (Fargate)](https://docs.aws.amazon.com/pdfs/AmazonECS/latest/developerguide/ecs-dg.pdf) |
| **Thứ 5 (30/10)** | **Tối ưu hóa Chi phí & Quản trị** <br> - **Phân tích:** Trực quan hóa xu hướng chi tiêu sử dụng **AWS Cost Explorer** và thiết lập cảnh báo qua **AWS Budgets**. <br> - **Chiến lược Giá:** Đánh giá **Savings Plans** so với **Reserved Instances** so với **Spot Instances**. <br> - **Đa Tài khoản:** Quản lý các chính sách sử dụng **AWS Organizations**. <br> **Ôn tập Tương tác: AWS Card Clash** <br> - **Hoạt động:** Sử dụng trò chơi "AWS Card Clash 3D" để mô phỏng việc ra quyết định kiến trúc. <br> - **Lợi ích:** Củng cố logic lựa chọn dịch vụ và hiểu biết về sự tương tác giữa các dịch vụ trong môi trường trò chơi hóa. | 23/10/2025 | 23/10/2025 | [Cost Management Guide](https://docs.aws.amazon.com/pdfs/cost-management/latest/userguide/cost-management-guide.pdf) <br> [Savings Plans Guide](https://docs.aws.amazon.com/pdfs/savingsplans/latest/userguide/savingsplans.pdf) <br> [EC2 Purchasing Options](https://docs.aws.amazon.com/pdfs/AWSEC2/latest/UserGuide/ec2-ug.pdf) <br> [Organizations Guide](https://docs.aws.amazon.com/pdfs/organizations/latest/userguide/organizations-userguide.pdf) <br> [AWS Card Clash](https://arcade.cardclash.training.aws.dev/) |
| **Thứ 6 (31/10)** | **Ngày Đánh giá Cuối cùng** <br> - **Mốc quan trọng:** Tham gia thành công Kỳ thi Cuối cùng. <br> - **Kết quả:** Thể hiện năng lực về Kiến trúc Đám mây AWS và triển khai Dịch vụ. | 31/10/2025 | 31/10/2025 |  |


### Thành tựu Tuần 8:

* **Năng lực Bảo mật Nâng cao:**
    * Chuyển từ tường lửa cơ bản sang triển khai bảo mật nhiều lớp với **AWS WAF** (Lớp Ứng dụng 7) và **AWS Shield** (bảo vệ DDoS).
    * Bảo mật dữ liệu nhạy cảm khi nghỉ (at rest) sử dụng **KMS Customer Master Keys (CMKs)**.

* **Làm chủ Kiến trúc Serverless:**
    * Thiết kế một ngăn xếp (stack) phân tích có khả năng mở rộng cao, không cần bảo trì sử dụng **S3 + Athena**, loại bỏ nhu cầu về các máy chủ ETL truyền thống.
    * Hiểu rõ sự đánh đổi giữa **Lambda** (hướng sự kiện - Event-driven) và **Fargate** (container chạy dài hạn).

* **Quản lý Chi phí Chiến lược:**
    * Phân biệt giữa tính linh hoạt của **Savings Plans** so với tính cứng nhắc của **Reserved Instances** để tối ưu hóa chi phí tính toán dài hạn.
    * Sử dụng **Cost Explorer** để xác định và loại bỏ lãng phí tài nguyên.