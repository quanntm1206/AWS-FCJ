---
title: "Event 3"
date: "2025-11-17"
weight: 3
chapter: false
pre: " <b> 4.3. </b> "
---

# Báo cáo Tóm tắt: “AWS Cloud Mastery Series #2 - DevOps on AWS”

## Mục tiêu Sự kiện

- Giới thiệu các dịch vụ AWS DevOps, tập trung cụ thể vào CI/CD Pipelines.
- Cung cấp cái nhìn tổng quan toàn diện về Infrastructure as Code (IaC) và các công cụ liên quan.
- Khám phá các Dịch vụ Container khác nhau có sẵn trong hệ sinh thái AWS.
- Đảm bảo khả năng Giám sát (Monitoring) và Quan sát (Observability) mạnh mẽ sử dụng các dịch vụ AWS.

## Diễn giả

- **Truong Quang Tinh** – AWS Community Builder, Platform Engineer - TymeX
- **Bao Huynh** – AWS Community Builder
- **Nguyen Khanh Phuc Thinh** – AWS Community Builder
- **Tran Dai Vi** – AWS Community Builder
- **Huynh Hoang Long** – AWS Community Builder
- **Pham Hoang Quy** – AWS Community Builder
- **Nghiem Le** – AWS Community Builder
- **Dinh Le Hoang Anh** - Cloud Engineer Trainee, First Cloud AI Journey

## Điểm nổi bật Chính

### Tư duy DevOps

**- Văn hóa (Culture):** Khái niệm này bao gồm sự hợp tác, tự động hóa, học tập liên tục và đo lường nhất quán.
**- Các vai trò DevOps:** Các vị trí chính bao gồm DevOps Engineer, Cloud Engineer, Platform Engineer và Site Reliability Engineer (SRE).
**- Các chỉ số Thành công:**
    + Đảm bảo sức khỏe triển khai (deployment health).
    + Nâng cao sự linh hoạt (agility).
    + Duy trì sự ổn định hệ thống.
    + Tối ưu hóa trải nghiệm khách hàng.
    + Biện minh cho các khoản đầu tư công nghệ.

| NÊN (DO) | KHÔNG NÊN (DON'T) |
| :--- | :--- |
| Bắt đầu với các nguyên tắc cơ bản | Mắc kẹt trong "Tutorial Hell" (Học vẹt) |
| Học bằng cách xây dựng dự án thực tế | Copy-paste một cách mù quáng |
| Tài liệu hóa mọi thứ | So sánh tiến độ của bạn với người khác |
| Làm chủ từng thứ một | Từ bỏ sau những thất bại |
| Nâng cao kỹ năng mềm | |

**- Continuous Integration:** Một thực hành trong đó các thành viên trong nhóm thường xuyên tích hợp công việc của họ, nhằm mục đích tạo điều kiện thuận lợi cho Continuous Delivery và Deployment hiệu quả.

### Infrastructure as Code (IaC)

**- Lợi ích:** Cách tiếp cận này mang lại sự tự động hóa, khả năng mở rộng, khả năng tái tạo và cải thiện đáng kể sự cộng tác.

#### AWS CloudFormation

Đây là giải pháp IaC native của AWS. Nó sử dụng các template được viết bằng YAML hoặc JSON để tự động cung cấp (provision) mọi thành phần của cơ sở hạ tầng AWS.

**- Stack:** Một tập hợp các tài nguyên AWS được định nghĩa trong một template, cho phép CloudFormation tạo, cập nhật hoặc xóa như một đơn vị duy nhất.

**- CloudFormation Template:** Một tệp YAML hoặc JSON đóng vai trò là bản thiết kế (blueprint) để cấu hình và triển khai tài nguyên, xác định cơ sở hạ tầng AWS một cách hiệu quả.

**- Quy trình làm việc:** Tạo template -> Lưu trữ trong S3 Bucket hoặc local storage -> Sử dụng CloudFormation để tạo Stack dựa trên template -> CloudFormation cung cấp tài nguyên.

**- Drift Detection:** Tính năng này xác định sự khác biệt giữa cơ sở hạ tầng thực tế và cấu hình Stack. Nó cho phép quản trị viên cập nhật Stack hoặc hoàn nguyên các thay đổi, điều này rất cần thiết để duy trì kiểm soát phiên bản.

#### AWS Cloud Development Kit (CDK)

Một framework phát triển phần mềm mã nguồn mở hỗ trợ IaC sử dụng các ngôn ngữ lập trình tiêu chuẩn, bao gồm Python, Java, C#.Net, TypeScript/JavaScript và Go.

**- Construct:** Đây là các khối xây dựng cơ bản, bao gồm các thành phần đại diện cho tài nguyên AWS và cấu hình của chúng. Có ba cấp độ construct:
    + **L1 Construct:** Các tài nguyên cấp thấp (low-level) ánh xạ trực tiếp đến một tài nguyên AWS CloudFormation đơn lẻ.
    + **L2 Construct:** Cung cấp mức độ trừu tượng cao hơn thông qua API trực quan, dựa trên ý định (intent-based), đóng gói các phương pháp hay nhất (best practices) và các mặc định bảo mật.
    + **L3 Construct:** Đại diện cho các mẫu kiến trúc hoàn chỉnh liên quan đến nhiều tài nguyên, cung cấp các triển khai có quan điểm riêng (opinionated implementations) để triển khai nhanh chóng.

#### AWS Amplify

Một nền tảng AWS được thiết kế để tạo điều kiện thuận lợi cho việc xây dựng, triển khai và mở rộng quy mô các ứng dụng web và di động. Nó sử dụng CloudFormation bên dưới, triển khai các Stack để xây dựng cơ sở hạ tầng theo chương trình.

#### Terraform

Một công cụ IaC trong đó cơ sở hạ tầng được định nghĩa thông qua mã Terraform. Người dùng lập kế hoạch (plan) và sau đó áp dụng (apply) cơ sở hạ tầng trên nhiều nền tảng đám mây, chẳng hạn như Azure, AWS và Google Cloud.

**- Điểm mạnh:** Ưu điểm chính của nó nằm ở việc hỗ trợ đa đám mây (multi-cloud) và theo dõi trạng thái (state tracking) bằng cách sử dụng cấu hình thống nhất.

#### Cách chọn Công cụ IaC?
**- Tiêu chí:**
    + Bạn đang lên kế hoạch sử dụng một nhà cung cấp đám mây đơn lẻ hay chiến lược đa đám mây?
    + Vai trò chính của bạn là Developer hay Operations?
    + Hệ sinh thái đám mây cụ thể có hỗ trợ đầy đủ cho công cụ không?

### Dịch vụ Container trên AWS

#### Dockerfile

Một Dockerfile vạch ra quy trình xây dựng một container image. Nó mô tả môi trường, các phụ thuộc (dependencies), các bước xây dựng và cấu hình runtime cuối cùng, đảm bảo rằng ứng dụng chạy nhất quán trên bất kỳ hệ thống nào hỗ trợ Docker.

**- Images:** Bản thiết kế (blueprint) được đóng gói của một ứng dụng, được xây dựng từ Dockerfile sử dụng hệ thống tệp phân lớp. Chúng được sử dụng để khởi tạo các container một cách nhất quán trên các môi trường đa dạng.

**- Quy trình:** Một Dockerfile được sử dụng để xây dựng Docker Image, sau đó có thể chạy Container và được đẩy (push) lên ECR hoặc Docker Hub.

#### Amazon ECR

Một container registry được quản lý hoàn toàn giúp đơn giản hóa việc lưu trữ, quản lý và chia sẻ an toàn các Docker container images. Nó đóng vai trò là container registry riêng tư, bảo mật và có thể mở rộng của chính AWS.

**- Tính năng:**
    + Quét Image (Image Scanning)
    + Immutable Tags
    + Chính sách vòng đời (Lifecycle Policies)
    + Mã hóa & IAM

**- Điều phối (Orchestration):** Điều này liên quan đến việc quản lý nhiều tiến trình container, bao gồm khởi động lại container, tự động mở rộng quy mô khi tải cao, phân phối lưu lượng hiệu quả và quản lý nơi container được đặt và thực thi.

#### Kubernetes

Một hệ thống mã nguồn mở tự động hóa việc triển khai, mở rộng quy mô, phục hồi (healing) và cân bằng tải.
**- Thành phần:**
    + **Master Node:** Control Plane quản lý các worker nodes và pods.
    + **Worker Node:** Chạy khối lượng công việc ứng dụng bên trong pods.
    + **Pod:** Đơn vị triển khai nhỏ nhất, có thể chứa một hoặc nhiều containers.
    + **Service**

**So sánh: ECS vs EKS**

| Tính năng | Amazon ECS (Elastic Container Service) | Amazon EKS (Elastic Kubernetes Service) |
| :--- | :--- | :--- |
| **Công nghệ Cốt lõi** | Điều phối container native của AWS | Dựa trên Kubernetes (tiêu chuẩn nguồn mở) |
| **Độ phức tạp** | Đơn giản hơn, dễ vận hành hơn | Linh hoạt cao nhưng **phức tạp** hơn |
| **Kiến thức Yêu cầu** | **Không cần kiến thức Kubernetes** | Yêu cầu **kiến thức Kubernetes** (pods, deployments, v.v.) |
| **Tích hợp AWS** | Tích hợp sâu với AWS (ALB, IAM, CloudWatch, v.v.) | Tích hợp Kubernetes tiêu chuẩn |
| **Trường hợp sử dụng/Lợi ích** | Tuyệt vời cho **triển khai nhanh** & **chi phí vận hành thấp hơn** | **Đa cụm (Multi-cluster)**, **tính di động đa đám mây** |
| **Hệ sinh thái/Cộng đồng** | Các công cụ và cộng đồng native của AWS | **Hệ sinh thái lớn hơn** & công cụ cộng đồng |
| **Tóm tắt** | ECS = dễ hơn, chạy nhanh hơn, **chi phí vận hành thấp hơn** | EKS = linh hoạt hơn, kiểm soát nhiều hơn, **phức tạp hơn** |

#### App Runner

Dịch vụ này phù hợp để triển khai nhanh các ứng dụng web và REST API, lý tưởng cho khối lượng công việc sản xuất (production workloads) vừa và nhỏ.

### Giám sát & Khả năng quan sát (Monitoring & Observability)

#### CloudWatch
- Giám sát các tài nguyên AWS và các ứng dụng chạy trên AWS trong thời gian thực.
- Cung cấp khả năng quan sát toàn diện.
- Kích hoạt cảnh báo và phản hồi tự động.
- Cung cấp dashboard để hỗ trợ tối ưu hóa vận hành và chi phí.

**- CloudWatch metrics:** Dữ liệu hiệu suất được thu thập từ các hệ thống trên AWS hoặc tại chỗ (thông qua CloudWatch Agent), tích hợp liền mạch với EventBridge, Auto Scaling và quy trình DevOps.

#### AWS X-Ray
**- Distributed Tracing:** Theo dõi các yêu cầu từ đầu đến cuối và ánh xạ đường dẫn giữa các dịch vụ được truy cập. Nó đòi hỏi phải thêm SDK vào mã để tạo trace ID.

**- Performance Insight:** Tạo điều kiện phân tích nguyên nhân gốc rễ cho độ trễ và lỗi bằng cách suy luận thông tin chi tiết từ các trace và cung cấp Giám sát Người dùng Thực (Real User Monitoring).

## Trải nghiệm Sự kiện

Sự kiện này tỏ ra rất quan trọng đối với dự án của chúng tôi, vì nó giải quyết trực tiếp kế hoạch triển khai IaC bằng cách sử dụng CDK, thay thế phương pháp "ClickOps" hiện tại của chúng tôi để nâng cao khả năng bảo trì và khả năng tái tạo. Ngoài ra, những thông tin chi tiết về CloudWatch đã củng cố đáng kể chiến lược giám sát dữ liệu của chúng tôi.

Các diễn giả đã giải quyết một số câu hỏi chính từ nhóm của chúng tôi:

- **Hỏi:** Cho đến nay, dự án của chúng tôi được xây dựng hoàn toàn bằng ClickOps và chúng tôi dự định chuyển sang CDK. Có công cụ nào có thể quét và chuyển đổi cơ sở hạ tầng hiện có của chúng tôi thành CDK hoặc CloudFormation template để tránh phải xây dựng lại từ đầu không?
- **Đáp:** Đáng tiếc là hiện tại không có công cụ nào có khả năng tự động hóa hoàn toàn việc chuyển đổi này. Do đó, nhóm sẽ cần xây dựng lại cơ sở hạ tầng từ đầu. Tuy nhiên, nếu bạn khám phá ra công cụ hỗ trợ việc này, hãy chia sẻ với cộng đồng.

- **Hỏi:** Chúng tôi nhận thấy rằng AWS X-Ray, khi được sử dụng với CloudWatch, có vẻ giống với CloudTrail trong phương pháp theo dõi. Bạn có thể giải thích những điểm khác biệt chính không?
- **Đáp:** X-Ray được tích hợp với CloudWatch và được sử dụng cụ thể để theo dõi đường dẫn qua các tài nguyên và dịch vụ mà hệ thống tương tác. Ngược lại, CloudTrail chủ yếu được sử dụng để ghi nhật ký và kiểm toán các hành động do người dùng AWS thực hiện (API calls).

- **Hỏi:** Dự án của chúng tôi dựa trên GuardDuty Findings. Bạn có kinh nghiệm nào về việc kích hoạt Findings một cách đáng tin cậy cho các kịch bản demo không?
- **Đáp:** Theo kinh nghiệm của tôi, GuardDuty Findings có thể được kích hoạt bằng các hoạt động quét cổng (port scanning), mặc dù chắc chắn còn có các phương pháp khác.
- **Đáp:** GuardDuty cũng có thể được cấu hình với một danh sách mối đe dọa (threat list) chứa các quy tắc tùy chỉnh để kích hoạt finding khi có các hoạt động liên quan đến các tên miền hoặc IP độc hại cụ thể.

Sự kiện này cũng đánh dấu buổi thuyết trình đầu tiên của một số diễn giả:
- Các phần DevOps và IaC được trình bày với sự thành thạo cao.
- Phần Monitoring & Observability ít trau chuốt hơn một chút và có thể nhận thấy sự lo lắng của diễn giả; tuy nhiên, họ vẫn mang lại giá trị đáng kể.

#### Một số hình ảnh sự kiện
![Ảnh nhóm trong sự kiện được chụp bởi diễn giả Trần Đại Vĩ](/images/4-Event/CM2GroupPic.jpg)