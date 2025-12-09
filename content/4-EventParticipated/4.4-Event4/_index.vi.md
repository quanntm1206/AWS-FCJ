---
title: "Event 4"
date: "2025-11-29"
weight: 4
chapter: false
pre: " <b> 4.4.</b> "
---

# Báo cáo Tóm tắt: “AWS Cloud Mastery Series #3: AWS Well-Architected – Security Pillar Workshop”

## Mục tiêu Sự kiện

- **Giới thiệu về AWS Cloud Club:** Thiết lập sứ mệnh và phạm vi của cộng đồng.
- **Pillar 1: Identity and Access Management (IAM):** Làm chủ kiểm soát truy cập và ủy quyền.
- **Pillar 2: Detection and Continuous Monitoring:** Triển khai khả năng quan sát và cảnh báo tự động.
- **Pillar 3: Infrastructure Protection:** Bảo vệ biên giới mạng và tài nguyên tính toán.
- **Pillar 4: Data Protection:** Đảm bảo tính bảo mật và toàn vẹn dữ liệu thông qua mã hóa và quản trị.
- **Pillar 5: Incident Response:** Thiết lập các giao thức để chuẩn bị, ứng phó và phục hồi sau các sự cố bảo mật.

## Diễn giả

- **Le Vu Xuan An** - AWS Cloud Club Captain HCMUTE
- **Tran Duc Anh** - AWS Cloud Club Captain SGU
- **Tran Doan Cong Ly** - AWS Cloud Club Captain PTIT
- **Danh Hoang Hieu Nghi** - AWS Cloud Club Captain HUFLIT
- **Huynh Hoang Long** - AWS Community Builder
- **Dinh Le Hoang Anh** - AWS Community Builder
- **Nguyen Tuan Thinh** - Cloud Engineer Trainee
- **Nguyen Do Thanh Dat** - Cloud Engineer Trainee
- **Van Hoang Kha** - Cloud Security Engineer, AWS Community Builder
- **Thinh Lam** - FCJ Member
- **Viet Nguyen** - FCJ Member
- **Mendel Grabski (Long)** - Ex-Head of Security & DevOps, Cloud Security Solution Architect
- **Tinh Truong** - Platform Engineer at TymeX, AWS Community Builder

## Điểm nổi bật Chính

### AWS Cloud Club

Phiên làm việc bắt đầu với phần giới thiệu về AWS Cloud Club, một sáng kiến được thiết kế để:
- Tạo điều kiện khám phá và trau dồi kỹ năng điện toán đám mây.
- Thúc đẩy khả năng lãnh đạo kỹ thuật trong cộng đồng sinh viên.
- Xây dựng các kết nối chuyên nghiệp ý nghĩa, mang tính toàn cầu.

Câu lạc bộ cung cấp cho các thành viên trải nghiệm AWS thực tế, sự cố vấn từ các chuyên gia AWS dày dạn kinh nghiệm và hỗ trợ nghề nghiệp lâu dài. Các AWS Cloud Clubs liên kết với FCJA bao gồm các chapter tại HCMUTE, SGU, PTIT và HUFLIT.

**Lợi ích:** Các thành viên có cơ hội đáng kể để xây dựng các kỹ năng thực tế, tham gia sâu vào cộng đồng và tiếp cận các con đường thăng tiến nghề nghiệp.

### Identity & Access Management (IAM)

IAM đóng vai trò là dịch vụ AWS cơ bản chịu trách nhiệm kiểm soát truy cập an toàn. Nó quản lý Users, Groups, Roles và Permissions, đảm bảo các cơ chế xác thực và ủy quyền mạnh mẽ trên toàn môi trường.

- **Các phương pháp hay nhất (Best Practices):**
    + **Nguyên tắc đặc quyền tối thiểu (Least Privilege Principle):** Chỉ cấp các quyền cụ thể cần thiết để thực hiện một tác vụ.
    + **Truy cập Root:** Xóa access key của tài khoản root ngay sau khi tạo tài khoản để ngăn chặn xâm phạm.
    + **Độ chính xác của Policy:** Tránh sử dụng ký tự đại diện ("*") trong Actions hoặc Resources để giảm thiểu bề mặt tấn công.
    + **Single Sign-On (SSO):** Sử dụng SSO để tích hợp đa tài khoản liền mạch và quản lý truy cập tập trung.

- **Service Control Policies (SCPs):** Đây là các chính sách cấp tổ chức xác định các quyền tối đa có sẵn cho tất cả các tài khoản trong một tổ chức. Điều quan trọng cần lưu ý là SCP hoạt động nghiêm ngặt như các bộ lọc; bản thân chúng không cấp quyền.

- **Permission Boundaries:** Cho phép quản trị viên thiết lập các quyền tối đa mà một chính sách dựa trên danh tính (identity-based policy) có thể cấp cho một User hoặc Role cụ thể, cung cấp một mạng lưới an toàn chống lại việc leo thang đặc quyền.

- **Multi-Factor Authentication (MFA):**

| Tính năng | TOTP (Time-based One-Time Password) | FIDO2 (Fast Identity Online 2) |
| :--- | :--- | :--- |
| **Cơ chế** | **Bí mật được chia sẻ (Shared secret)** | **Mật mã khóa công khai (Public-key cryptography)** |
| **Tương tác người dùng** | Yêu cầu nhập mã 6 chữ số thủ công | Yêu cầu chạm đơn giản hoặc quét sinh trắc học |
| **Chi phí** | Miễn phí (Dựa trên phần mềm) | Chi phí thay đổi (Khóa phần cứng) |
| **Khôi phục** | Sao lưu linh hoạt và các tùy chọn khôi phục | Sao lưu nghiêm ngặt và thường không thể khôi phục nếu bị mất |

- **Xoay vòng thông tin xác thực với AWS Secrets Manager:**
    + Credential Updater sử dụng các hàm của Secrets Manager theo chu kỳ: *Create Secret* -> *Set Secret* (ví dụ: mỗi 7 ngày) -> *Test Secret* -> *Finish Secret*.
    + Các sự kiện xoay vòng có thể được kích hoạt chính xác thông qua EventBridge Schedule.
    + Quá trình kết thúc bằng việc loại bỏ bí mật cũ, đảm bảo vô hiệu hóa các thông tin xác thực cũ.

### Detection and Continuous Monitoring (Phát hiện và Giám sát Liên tục)

- **Khả năng hiển thị bảo mật đa lớp:**
    + **Management Events:** Giám sát các lệnh gọi API và hành động console trên tất cả các tài khoản tổ chức.
    + **Data Events:** Theo dõi truy cập đối tượng S3 và thực thi Lambda ở quy mô lớn.
    + **Network Activity Events:** Tích hợp VPC Flow Logs để giám sát cấp độ mạng chi tiết.
    + **Phạm vi tổ chức:** Đảm bảo nhập log thống nhất trên tất cả các tài khoản thành viên và các region.

- **Cảnh báo & Tự động hóa với EventBridge:**
    + **Sự kiện thời gian thực:** Các sự kiện CloudTrail chuyển trực tiếp vào EventBridge để xử lý ngay lập tức. Điều này tạo thành nền tảng của Kiến trúc hướng sự kiện (EDA), cho phép hệ thống phản ứng tức thời với các thay đổi trạng thái.
    + **Cảnh báo tự động:** Phát hiện và thông báo về các hoạt động đáng ngờ trên toàn bộ tổ chức.
    + **Định tuyến sự kiện liên tài khoản:** Tạo điều kiện xử lý sự kiện tập trung và phản hồi tự động bằng cách định tuyến các sự kiện dựa trên quy tắc đến các mục tiêu ở các tài khoản hoặc region khác nhau.
    + **Tích hợp & Quy trình làm việc:** Hỗ trợ tích hợp liền mạch với Lambda, SNS và SQS để kích hoạt các quy trình bảo mật tự động.

- **Detection-as-Code:**
    + **CloudTrail Lake Queries:** Liên quan đến việc tạo và thực thi các quy tắc phát hiện dựa trên SQL để săn tìm mối đe dọa nâng cao.
    + **Logic được kiểm soát phiên bản:** Các quy tắc và logic phát hiện được theo dõi, lập phiên bản và quản lý thông qua các kho lưu trữ mã (code repositories).
    + **Triển khai tự động:** Trails và các quy tắc phát hiện được triển khai tự động trên tất cả các tài khoản tổ chức liên quan thông qua CI/CD pipelines.
    + **Infrastructure-as-Code (IaC):** Sử dụng các công cụ như CloudFormation hoặc Terraform để tự động hóa việc thiết lập logging và event trails của tổ chức.

### GuardDuty

GuardDuty là một giải pháp phát hiện mối đe dọa thông minh, luôn bật, liên tục giám sát hoạt động độc hại và hành vi trái phép.

- **Cách GuardDuty hoạt động:** Nó dựa vào việc phân tích liên tục **Ba Trụ cột Phát hiện (Three Pillars of Detection):**

| Nguồn dữ liệu | Những gì nó giám sát | Ví dụ thực tế |
| :--- | :--- | :--- |
| **CloudTrail Events** | Các hành động IAM, thay đổi quyền, gọi API | Kẻ tấn công vô hiệu hóa logging để che giấu dấu vết. |
| **VPC Flow Logs** | Lưu lượng mạng đến/đi từ tài nguyên của bạn | Một EC2 instance gửi dữ liệu đến máy chủ C2 botnet đã biết. |
| **DNS Logs** | Các truy vấn DNS từ cơ sở hạ tầng của bạn | Các truy vấn bị nhiễm phần mềm độc hại cố gắng phân giải các trang web khai thác tiền điện tử. |

- **Các gói bảo vệ nâng cao:** GuardDuty cung cấp các tiện ích bổ sung chuyên biệt để bảo vệ toàn diện:
    + **S3 Protection:** Phát hiện các mẫu truy cập S3 bất thường và quét phần mềm độc hại trong các đối tượng S3 khi tải lên.
    + **EKS Protection:** Giám sát audit logs Kubernetes để phát hiện truy cập trái phép và tương quan các finding với S3 để lập bản đồ đường dẫn tấn công đầy đủ.
    + **Malware Protection:** Tự động quét các volume EBS của EC2 instance khi nghi ngờ bị xâm phạm.
    + **RDS Protection:** Phân tích nhật ký hoạt động đăng nhập cho cơ sở dữ liệu (Aurora/RDS) để phát hiện các cuộc tấn công brute-force.
    + **Lambda Protection:** Giám sát nhật ký mạng từ các lệnh gọi hàm Lambda để phát hiện xem một hàm bị xâm phạm có đang giao tiếp với các IP độc hại hay không.
    + **Runtime Monitoring:** Đạt được bằng cách sử dụng GuardDuty Agent được cài đặt trên EC2/EKS/ECS Fargate để giám sát các tiến trình đang chạy, các mẫu truy cập tệp và system calls.

- **Tiêu chuẩn tuân thủ:**
    + **AWS Foundational Security Best Practices:** Một tiêu chuẩn được phát triển bởi AWS, bao gồm một loạt các dịch vụ.
    + **CIS AWS Foundations Benchmark:** Một hướng dẫn dựa trên sự đồng thuận được phát triển bởi AWS và các chuyên gia trong ngành, tập trung vào Identity (IAM), Logging & Monitoring và Networking.

- **Thực thi tuân thủ với Detection-as-Code:**
    + **Công cụ IaC:** AWS CloudFormation được sử dụng để triển khai cấu hình.
    + **Compliance Engine:** AWS CloudFormation đẩy các kiểm tra cấu hình đến AWS Security Hub CSPM.
    + **Tiêu chuẩn tuân thủ được áp dụng:** Security Hub thực hiện kiểm tra so với các tiêu chuẩn được liệt kê (AWS Foundational, CIS, PCI DSS, NIST).
    + **Tài nguyên được bao gồm:** Chủ yếu là Amazon S3, Amazon EC2 và Amazon RDS.

### Network Security Controls

- **Các vector tấn công:** Các mối đe dọa được phân loại thành **Ingress Attacks** (ví dụ: DDoS, SQL injection), **Egress Attacks** (ví dụ: trích xuất dữ liệu, DNS tunneling) và **Inside Attacks** (ví dụ: di chuyển ngang - lateral movement).

- **Security Groups (SG):** Hoạt động như tường lửa stateful ở cấp độ instance/giao diện. Chúng chỉ hỗ trợ các quy tắc "allow" và bao gồm mặc định ngầm định "deny all".

- **Network ACLs (NACLs):** Hoạt động ở cấp độ subnet như một lớp bảo vệ bổ sung. Chúng là stateless và sử dụng các quy tắc được đánh số để cho phép (ALLOW) hoặc từ chối (DENY) lưu lượng truy cập một cách rõ ràng.

- **AWS TGW Security Group Referencing:** Cho phép Transit Gateway (TGW) VPC xác định các quy tắc inbound chỉ sử dụng tham chiếu SG, đơn giản hóa việc quản lý trong các cấu trúc liên kết phức tạp.

- **Route 53 Resolver:** Định tuyến các truy vấn DNS đến Private DNS (private hosted zones), VPC DNS hoặc Public DNS dựa trên các quy tắc.

- **AWS Network Firewall:**
    + **Trường hợp sử dụng:** Lọc Egress (chặn các tên miền/giao thức độc hại), phân đoạn môi trường (VPC tới VPC) và ngăn chặn xâm nhập (quy tắc IDS/IPS).
    + **Phòng thủ chủ động:** Có thể tự động chặn lưu lượng truy cập độc hại bằng cách sử dụng Amazon Threat Intelligence, nơi các GuardDuty findings được đánh dấu cho các hành động chặn tự động.

### Bảo vệ Dữ liệu & Quản trị

- **Mã hóa (KMS):** Dữ liệu được mã hóa bằng Data Key, khóa này lại được bảo vệ bởi Customer Master Key (CMK) (Envelope Encryption). Các chính sách KMS thực thi lớp bảo mật thứ hai với các khóa Condition để xác định chính xác *khi nào* được phép mã hóa/giải mã.

- **Certificate Management (ACM):** Cung cấp chứng chỉ công khai miễn phí và tự động gia hạn chúng 60 ngày trước khi hết hạn. DNS Validation là phương pháp được khuyến nghị để xác minh quyền sở hữu.

- **Secrets Manager:** Giải quyết rủi ro bảo mật của thông tin xác thực được hardcode. Nó sử dụng logic Lambda 4 bước để thực hiện xoay vòng thông tin xác thực tự động mà không gây ra thời gian chết (downtime).

- **Bảo mật dịch vụ API (S3 & DynamoDB):** S3 yêu cầu TLS 1.2+ và bucket policies với `aws:SecureTransport` để thực thi. DynamoDB được bảo mật theo mặc định, bắt buộc sử dụng HTTPS.

- **Bảo mật dịch vụ cơ sở dữ liệu (RDS):** Yêu cầu sự tin cậy phía máy khách vào AWS Root CA Bundle để xác minh danh tính máy chủ và thực thi phía máy chủ (ví dụ: đặt `rds.force_ssl=1` cho PostgreSQL).

### Ứng phó Sự cố & Phòng ngừa

- **Các phương pháp phòng ngừa hay nhất:** Các biện pháp phòng ngừa chính bao gồm sử dụng thông tin xác thực tạm thời, đảm bảo S3 buckets không bao giờ tiếp xúc trực tiếp với internet, đặt các dịch vụ nhạy cảm trong private subnets, quản lý tất cả tài nguyên thông qua Infrastructure as Code và sử dụng xác minh hai cổng (double-gate verification) cho các thay đổi rủi ro cao (phê duyệt PR, triển khai pipeline).

- **Quy trình Ứng phó Sự cố:** Một cách tiếp cận có cấu trúc gồm 5 bước:
    1.  Chuẩn bị (Preparation)
    2.  Phát hiện & Phân tích (Detection & Analysis)
    3.  Ngăn chặn (Containment) (cô lập tài nguyên, thu hồi thông tin xác thực)
    4.  Diệt trừ & Phục hồi (Eradication & Recovery)
    5.  Hoạt động sau sự cố (Post-Incident Activity) (bài học kinh nghiệm và tài liệu hóa).

## Trải nghiệm Sự kiện

Hội thảo này rất phù hợp với nhóm của chúng tôi, vì nội dung phù hợp trực tiếp với dự án đang diễn ra tập trung vào Ứng phó sự cố tự động (Automated Incident Response) và Pháp y số (Forensics).

Các diễn giả đã giải quyết một số câu hỏi quan trọng từ nhóm của chúng tôi:

- **Hỏi:** Dự án của nhóm chúng tôi là một công cụ Ứng phó sự cố tự động và Forensics sử dụng GuardDuty làm trình kích hoạt chính. Tuy nhiên, thử nghiệm của chúng tôi chỉ ra rằng GuardDuty có thể mất tới 5 phút để tạo ra một finding sau khi sự cố xảy ra. Có giải pháp nào để giảm thiểu độ trễ này không?
- **Đáp:** Độ trễ 5 phút để GuardDuty tạo ra finding phần lớn là do cấu hình vốn có của nó, vì nó phải nhập và xử lý một lượng lớn dữ liệu bảo mật để xác định chính xác các mối đe dọa. Để giảm độ trễ, bạn có thể xem xét tích hợp các dịch vụ bảo mật của bên thứ ba, chẳng hạn như Open Clarity Free, để có các finding gần như thời gian thực. Ngoài ra, việc tận dụng trực tiếp CloudTrail có thể giúp phát hiện các bất thường cụ thể và hành vi người dùng bất thường nhanh hơn so với việc chờ finding tổng hợp từ GuardDuty.

Hơn nữa, ông Mendel Grabski đã ân cần đề nghị hỗ trợ và cố vấn khi chúng tôi thảo luận về các chi tiết cụ thể của dự án sau sự kiện.

#### Một số hình ảnh sự kiện

![Hình ảnh tất cả người tham dự](/images/4-Event/Event6AttendeePic.jpg)
_Hình ảnh tất cả người tham dự_

![Ảnh nhóm với diễn giả Mendel Grabski và diễn giả Van Hoang Kha](/images/4-Event/Event6PicturewithSpeakers.jpg)
_Ảnh nhóm với diễn giả Mendel Grabski và diễn giả Van Hoang Kha_