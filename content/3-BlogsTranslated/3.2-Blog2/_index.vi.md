---
title: "Blog 2"
date: "2025-09-16"
weight: 02
chapter: false
pre: " <b> 3.2. </b> "
---

# Amazon MSK Replicator và MirrorMaker2: Chiến lược sao chép Apache Kafka cho DR và Di chuyển

Khách hàng cần sao chép dữ liệu từ các cụm Apache Kafka của họ vì nhiều lý do khác nhau, chẳng hạn như yêu cầu tuân thủ quy định, di chuyển cụm và triển khai phục hồi thảm họa (DR). Tuy nhiên, chiến lược sao chép phù hợp có thể thay đổi tùy theo bối cảnh ứng dụng.

Trong bài viết này, chúng tôi sẽ phân tích các yếu tố cần xem xét khi sử dụng **Amazon MSK Replicator** thay vì **MirrorMaker 2** của Apache Kafka, đồng thời giúp bạn lựa chọn giải pháp sao chép phù hợp với trường hợp sử dụng của mình.

---

## Những thách thức trong việc lựa chọn chiến lược phục hồi thảm họa (DR)

Khách hàng tạo ra kế hoạch duy trì hoạt động kinh doanh và chiến lược phục hồi thảm họa (DR) nhằm tối đa hóa khả năng chịu lỗi cho các ứng dụng của họ, bởi vì thời gian gián đoạn hoặc mất mát dữ liệu có thể dẫn đến mất doanh thu hoặc ngừng hoạt động.

Đối với những khách hàng sử dụng Kafka như một dịch vụ phát trực tuyến và nhắn tin cốt lõi, việc lên kế hoạch DR cho hạ tầng Kafka là thiết yếu để đạt được các mục tiêu về **Thời gian Khôi phục (RTO)** và **Điểm Khôi phục (RPO)**.

### Tính sẵn sàng của Amazon MSK
* **Đa vùng khả dụng (Multi-AZ):** Amazon MSK phân phối các broker trên nhiều vùng khả dụng khác nhau trong một khu vực AWS.
* **Sao chép nội cụm:** Hệ số nhân bản là 3 và giá trị `min-ISR` là 2, cùng với thiết lập producer `acks=all`, đảm bảo khả năng bảo vệ trước sự cố mất một broker hoặc mất một vùng khả dụng đơn lẻ.
* **Express brokers:** Tăng cường khả năng phục hồi với lưu trữ trả theo mức sử dụng, tự động cấu hình tin cậy và phục hồi nhanh hơn.

Tuy nhiên, nếu sự cố ảnh hưởng đến nhiều hơn một Availability Zone, bạn cần kiến trúc đa vùng (Multi-Region).

### Sao lưu vào Amazon S3 so với Sao chép đa vùng
Đối với các công ty có thể chịu được RTO dài hơn nhưng yêu cầu RPO thấp hơn, việc sao lưu dữ liệu vào **Amazon S3** (sử dụng Amazon MSK Connect) có thể là đủ. Tuy nhiên, phương pháp này có nhược điểm:
* Quá trình khôi phục có thể mất nhiều thời gian tùy thuộc vào khối lượng dữ liệu.
* Phức tạp trong việc xử lý offset nhóm tiêu dùng (consumer group offsets).

Do đó, phần lớn các trường hợp sử dụng dữ liệu luồng đều dựa vào thiết lập các cụm **MSK đa vùng (multi-Region)** và cấu hình sao chép dữ liệu giữa các cụm để đảm bảo tính liên tục kinh doanh.

---

## Lựa chọn giải pháp sao chép phù hợp: MSK Replicator so với MirrorMaker 2

AWS khuyến nghị hai giải pháp chính để sao chép Kafka giữa các vùng (cross-Region):

### 1. MSK Replicator: Ưu tiên cho sao chép cụm MSK trong cùng một tài khoản
MSK Replicator là dịch vụ được quản lý hoàn toàn, không máy chủ (serverless), giúp sao chép dữ liệu giữa các cụm MSK ở các vùng khác nhau hoặc trong cùng một vùng.

**Lợi ích:**
* **Sao chép giữa các cụm MSK:** Hỗ trợ mô hình active-active và active-passive.
* **Không quản lý hạ tầng:** Hoàn toàn không máy chủ, tự động mở rộng.
* **Giám sát tích hợp:** Tích hợp chặt chẽ với Amazon CloudWatch.
* **Tính khả dụng cao:** Khả năng chịu lỗi tích hợp vượt qua các Vùng Khả dụng.

### 2. MirrorMaker 2: Dành cho các kịch bản di cư, phức tạp và lai
MirrorMaker 2 (MM2) là tiện ích tích hợp trong Kafka, sử dụng khung Kafka Connect, phù hợp cho các trường hợp đòi hỏi sự linh hoạt cao hoặc môi trường không phải Amazon MSK hoàn toàn.

**Khuyến nghị sử dụng khi:**
* **Sao chép giữa các tài khoản:** Giữa các cụm MSK trong các tài khoản AWS khác nhau.
* **Di chuyển sang Amazon MSK:** Từ on-premise, đám mây khác hoặc EC2 tự quản lý.
* **Đám mây lai / Đa đám mây:** Kết nối Kafka tại cơ sở với Amazon MSK.
* **Sử dụng xác thực mTLS hoặc SASL/SCRAM:** Khi không thể kích hoạt xác thực IAM (mặc dù MSK Replicator có hỗ trợ IAM kết hợp).
* **Chính sách tùy chỉnh:** Yêu cầu nâng cao về đặt tên chủ đề hoặc biến đổi dữ liệu (SMT).

---

## Tổng quan giải pháp MSK Replicator

Sơ đồ sau minh họa kiến trúc sử dụng MSK Replicator cho mô hình phục hồi thảm họa:

![alt text](/images/3-Blog/1.png)

Chúng tôi tạo ra hai cụm MSK — một cụm chính tại vùng chính và một cụm dự phòng tại vùng phụ. MSK Replicator được triển khai ở vùng phụ nhằm sao chép các chủ đề, ACL, dữ liệu và offset nhóm tiêu dùng từ cụm chính.

* **Mô hình:** Sao chép một chiều cho DR (active-passive), nhưng có thể mở rộng cho active-active.
* **Hoạt động:** Client kết nối với cụm chính và chuyển sang cụm phụ nếu xảy ra failover.

---

## Giải pháp MirrorMaker 2

Sơ đồ sau minh họa kiến trúc sử dụng MirrorMaker 2 cho kịch bản di chuyển:

![alt text](/images/3-Blog/2.png)

Chúng tôi tạo một cụm MSK tại vùng chính cùng với cụm Kafka hiện có tại cơ sở (hoặc trên đám mây khác/EC2).
* **Mô hình:** Sao chép một chiều cho di cư cụm.
* **Hoạt động:** Client tương tác với cụm tại cơ sở và dần được di cư sang tương tác với cụm MSK trên AWS.

**Tài nguyên triển khai tự động (Amazon ECS với Fargate):**
Thay vì cấu hình thủ công, nên sử dụng các mẫu Terraform và Docker có sẵn để triển khai MM2 trên Amazon ECS/Fargate với khả năng tự động mở rộng.

---

## Kết luận

Việc lựa chọn phụ thuộc vào yêu cầu cụ thể:

| Giải pháp | Trường hợp sử dụng chính |
| :--- | :--- |
| **Amazon MSK Replicator** | Sao chép MSK-sang-MSK trong cùng tài khoản, cần giải pháp quản lý hoàn toàn cho DR. |
| **MirrorMaker 2** | Di chuyển sang MSK, môi trường lai, sao chép chéo tài khoản, hoặc cần chính sách sao chép tùy chỉnh phức tạp. |

Các phương pháp này cung cấp các tùy chọn để đảm bảo dự phòng dữ liệu, đáp ứng tuân thủ quy định và giảm thiểu công tác vận hành thông qua tự động hóa.

_Nguồn: Mazrim Mehrtens | 16/08/2025_