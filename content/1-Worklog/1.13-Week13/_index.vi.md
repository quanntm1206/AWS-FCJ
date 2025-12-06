---
title: "Nhật ký công việc Tuần 13"
date: "2025-12-01"
weight: 13
chapter: false
pre: " <b> 1.13. </b> "
---

### Mục tiêu Tuần 13:

* **Tối ưu hóa Phân tích Nâng cao:** Triển khai **Athena Partition Projection** để tự động hóa quản lý phân vùng và cải thiện hiệu suất truy vấn.
* **Tinh chỉnh Pipeline:** Chuyển đổi từ cơ chế polling SQS sang **Amazon Kinesis Data Firehose** để giải quyết các vấn đề về thực thi đồng thời cao (high-concurrency invocation).
* **Nghiên cứu Chuyên sâu AI/ML:** Nắm vững Sequence Models và Attention Mechanisms trong NLP; khám phá Agentic AI với **Amazon Bedrock**.
* **Chuẩn bị Đồ án Tốt nghiệp:** Hoàn thiện tài liệu thuyết trình cho buổi bảo vệ thực tập.

### Các nhiệm vụ thực hiện trong tuần:

| Ngày | Nhiệm vụ | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| :--- | :--- | :--- | :--- | :--- |
| **Thứ 2 (01/12)** | **Quản lý Dự án & Nghiên cứu NLP (Phần 3)**<br>- **Mốc quan trọng:** Đã nộp Đề xuất Dự án Cuối cùng (Final Project Proposal) cho nhóm để đánh giá ngang hàng.<br>- **Khóa học:** Tiến tới **NLP: Sequence Models**. Nghiên cứu RNNs (Recurrent Neural Networks) để xử lý dữ liệu log tuần tự. | 01/12/2025 | 01/12/2025 | [NLP Course 3](https://www.coursera.org/programs/fptu-fall-2025-zmahp/learn/sequence-models-in-nlp) |
| **Thứ 3 (02/12)** | **Vận hành & Tái cấu trúc Lambda**<br>- **Chia sẻ kiến thức:** Sản xuất Video hướng dẫn cách tạo Slack Webhooks cho ChatOps.<br>- **Cập nhật Code:** Cấu hình lại logic **Lambda ENI** để định dạng đầu ra khớp với các yêu cầu schema mới của **Athena**. | 02/12/2025 | 02/12/2025 | N/A |
| **Thứ 4 (03/12)** | **Tối ưu hóa Pipeline (Firehose & Athena)**<br>- **Vấn đề:** Lambda được kích hoạt bởi SQS phát sinh quá nhiều GET request/lần thực thi.<br>- **Giải pháp:** Chuyển sang **Kinesis Data Firehose** để đóng gói (batching) và đệm (buffering) dữ liệu trước khi nạp vào **S3**.<br>- **Tối ưu hóa Athena:** Triển khai **Partition Projection** cho VPC Logs để tự động hóa quản lý phân vùng mà không cần lệnh `MSCK REPAIR TABLE`. | 03/12/2025 | 03/12/2025 | [Athena Partition Projection](https://docs.aws.amazon.com/athena/latest/ug/partition-projection.html) |
| **Thứ 5 (04/12)** | **Phát triển Nội dung Workshop**<br>- **Nhiệm vụ:** Soạn thảo "Data Module" cho buổi workshop nội bộ của nhóm.<br>- **Nội dung:** Chi tiết hóa luồng dữ liệu log end-to-end từ thu thập (**Firehose**) đến phân tích (**Athena**). | 04/12/2025 | 04/12/2025 | N/A |
| **Thứ 6 (05/12)** | **Tham gia Sự kiện Ngành: GenAI & Agentic AI**<br>- **Sự kiện:** Tham dự **"BUILDING AGENTIC AI - Context Optimization with Amazon Bedrock"**.<br>- **Bài học chính:** Tìm hiểu về RAG (Retrieval-Augmented Generation) và quản lý ngữ cảnh cho AI Agents.<br>- **Hành động:** Tiếp tục phát triển tài liệu workshop. | 05/12/2025 | 05/12/2025 | [Amazon Bedrock](https://aws.amazon.com/bedrock/) |
| **Thứ 7 (06/12)** | **Nghiên cứu AI Nâng cao & Chuẩn bị Cuối cùng**<br>- **Khóa học:** Tiến tới **NLP: Attention Models** (Transformers/Self-Attention).<br>- **Thuyết trình:** Thiết kế **Slide Bảo vệ Cuối cùng** (Final Defense Slides), trực quan hóa sự phát triển kiến trúc (Batch $\to$ Streaming) và các thành tựu kỹ thuật chính. | 06/12/2025 | 06/12/2025 | [NLP Course 4](https://www.coursera.org/programs/fptu-fall-2025-zmahp/learn/attention-models-in-nlp) |

### Thành tựu Tuần 13:

* **Giải quyết vấn đề Thu thập Dữ liệu Quy mô lớn:**
    * Chẩn đoán nút thắt cổ chai với cơ chế polling SQS (High GET requests) và tái cấu trúc thành công pipeline sử dụng **Kinesis Data Firehose**, giảm chi phí API và cải thiện thông lượng.

* **Làm chủ các Tính năng Nâng cao của Athena:**
    * Triển khai thành công **Partition Projection** (thông qua DDL `TBLPROPERTIES`), loại bỏ gánh nặng vận hành khi phải thêm phân vùng thủ công. Điều này đảm bảo các truy vấn trên `vpc-logs` luôn cập nhật và đạt hiệu suất cao.

* **Sẵn sàng Hoàn thành Dự án:**
    * Nối liền khoảng cách giữa NLP truyền thống và Generative AI hiện đại, đồng thời hoàn thiện tài liệu và slide thuyết trình cho buổi bảo vệ dự án.