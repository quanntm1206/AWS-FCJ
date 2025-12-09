---
title: "Nhật ký công việc Tuần 9"
date: "2025-11-03"
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---
### Mục tiêu Tuần 9:

* **Kiến trúc Dự án:** Thiết kế pipeline Serverless Log Analytics sử dụng các dịch vụ được quản lý bởi AWS.
* **Thu thập Dữ liệu (Data Ingestion):** Tự động hóa việc trích xuất log từ Amazon CloudWatch sang Amazon S3 sử dụng AWS Lambda.
* **Tự động hóa ETL:** Triển khai logic Extract-Transform-Load (ETL) để chuẩn hóa các raw JSON log.
* **Phân tích Dữ liệu:** Cho phép thực hiện các truy vấn SQL tương tác trên dữ liệu S3 sử dụng Amazon Athena.

### Các nhiệm vụ thực hiện trong tuần:

| Ngày | Nhiệm vụ | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| :--- | :--- | :--- | :--- | :--- |
| **Thứ 2 (3/11)** | **Nghiên cứu & Phát triển Dự án: Kiến trúc Log Analytics**<br>- **Phân tích Yêu cầu:** Xác định luồng thu thập và phân tích log ứng dụng.<br>- **Thiết kế Kiến trúc:** Thiết kế pipeline: **CloudWatch Logs** (Source) to **AWS Lambda** (Collector) $\to$ **Amazon S3** (Data Lake) to **Amazon Athena** (Query Engine).<br>- **Chiến lược Định dạng:** Quyết định sử dụng định dạng JSON cho raw logs để đảm bảo tính linh hoạt của schema. | 03/11/2025 | 03/11/2025 | [S3 User Guide](https://docs.aws.amazon.com/pdfs/AmazonS3/latest/userguide/s3-userguide.pdf)<br>[Module 04-02 - S3 Concepts](https://youtu.be/_yunukwcAwc?si=eFjVimOndHJO2_x1)<br>[CloudWatch Metrics](https://docs.aws.amazon.com/pdfs/AWSEC2/latest/UserGuide/ec2-ug.pdf) |
| **Thứ 3 (4/11)** | **Triển khai Thu thập Dữ liệu (Phần 1)**<br>- **Phát triển Lambda:** Phát triển một Lambda function (Python/Node.js) để giao tiếp với CloudWatch Logs API.<br>- **Logic:** Triển khai logic để "crawl" (lấy) các log stream và tổng hợp chúng.<br>- **Lưu trữ:** Cấu hình S3 Bucket policy để cho phép Lambda quyền ghi (write access). | 04/11/2025 | 04/11/2025 | [S3 API Reference](https://docs.aws.amazon.com/pdfs/AmazonS3/latest/API/s3-api.pdf)<br>[CloudWatch for VPC](https://docs.aws.amazon.com/pdfs/vpc/latest/userguide/vpc-ug.pdf) |
| **Thứ 4 (5/11)** | **Triển khai Thu thập Dữ liệu (Phần 2)**<br>- **Định dạng:** Cấu trúc lại các log đã lấy thành các đối tượng JSON hợp lệ.<br>- **Lưu trữ:** Lưu trữ thành công các file raw log vào S3 bucket (Raw Zone).<br>- **Kiểm thử:** Xác minh tính toàn vẹn của log bằng cách kiểm tra thủ công các đối tượng S3. | 05/11/2025 | 05/11/2025 | [S3 User Guide](https://docs.aws.amazon.com/pdfs/AmazonS3/latest/userguide/s3-userguide.pdf) |
| **Thứ 5 (6/11)** | **Phát triển Xử lý ETL (Phần 1)**<br>- **Lambda ETL:** Bắt đầu phát triển Lambda function thứ hai được kích hoạt bởi S3 Event Notifications (ObjectCreate).<br>- **Chuyển đổi (Transformation):** Triển khai logic để phân tích cú pháp (parse) file raw JSON, làm sạch dữ liệu và làm phẳng (flatten) các cấu trúc lồng nhau. | 06/11/2025 | 06/11/2025 | [Athena User Guide](https://docs.aws.amazon.com/pdfs/AmazonS3/latest/userguide/s3-userguide.pdf)|
| **Thứ 6 (7/11)** | **Xử lý ETL & Tích hợp Athena (Phần 2)**<br>- **Nạp (Loading):** Cấu hình Lambda để xuất dữ liệu đã xử lý sang S3 bucket đích (Clean Zone).<br>- **Tích hợp Athena:** Định nghĩa Table Schema (DDL) trong Athena để ánh xạ với dữ liệu JSON đã xử lý.<br>- **Xác thực:** Thực thi các truy vấn SQL trong Athena để xác minh độ chính xác và cấu trúc dữ liệu. | 07/11/2025 | 07/11/2025 | [VPC Flow Logs & Athena](https://docs.aws.amazon.com/pdfs/vpc/latest/userguide/vpc-ug.pdf)<br>[Athena Solutions](https://docs.aws.amazon.com/pdfs/solutions/latest/amazon-marketing-cloud-insights-on-aws/amazon-marketing-cloud-insights-on-aws.pdf) |

### Thành tựu Tuần 9:

* **Xây dựng một Serverless ETL Pipeline:**
    * Đã tự động hóa thành công luồng dữ liệu từ operational logs (CloudWatch) sang analytical data lake (S3) mà không cần cấp phát bất kỳ máy chủ nào (sử dụng **AWS Lambda**).
    * Triển khai các quy trình **ETL (Extract, Transform, Load)** để chuyển đổi raw logs phi cấu trúc thành các tập dữ liệu JSON có cấu trúc, có thể truy vấn được.

* **Làm chủ Phân tích Dữ liệu trên AWS:**
    * Cấu hình **Amazon Athena** để xử lý các file trong S3 như một cơ sở dữ liệu quan hệ, cho phép phân tích log dựa trên SQL.
    * Áp dụng **S3 Best Practices** bằng cách tổ chức dữ liệu thành các vùng "Raw" và "Processed" để duy trì vệ sinh cho data lake.

* **Tích hợp CloudWatch:**
    * Hiểu sâu hơn về quyền truy cập lập trình (programmatic access) vào CloudWatch Logs ngoài giao diện Console UI.