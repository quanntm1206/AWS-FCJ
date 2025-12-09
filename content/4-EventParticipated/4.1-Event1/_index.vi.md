---
title: "Event 1"
date: "2025-10-03"
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

# Báo cáo Tóm tắt: “AI-Driven Development Life Cycle: Reimagining Software Engineering”

### Mục tiêu Sự kiện

- Khám phá sự chuyển đổi quan trọng trong phát triển phần mềm được thúc đẩy bởi generative AI.
- Giới thiệu về AI-Driven Development Life Cycle (AI-DLC) cùng với các khái niệm cơ bản của nó.
- Demo các khả năng của Kiro và Amazon Q Developer.

### Diễn giả

- **Toan Huynh** – Specialist SA, PACE
- **My Nguyen** - Sr. Prototyping Architect, Amazon Web Services - ASEAN

### Điểm nổi bật Chính

- Phiên làm việc tập trung vào khung AI-DLC, một hệ thống nơi AI điều phối quy trình phát triển—bao gồm lập kế hoạch, phân rã tác vụ và đề xuất kiến trúc—trong khi các lập trình viên giữ trách nhiệm cuối cùng về việc xác thực, ra quyết định và giám sát.

**- Khái niệm Cốt lõi AI-DLC:** Cách tiếp cận này hoàn toàn lấy con người làm trung tâm, với AI đóng vai trò là cộng sự để tăng cường khả năng của lập trình viên. Mối quan hệ hợp tác này dẫn đến việc tăng tốc độ phân phối, giảm chu kỳ từ vài tuần hoặc vài tháng xuống chỉ còn vài giờ hoặc vài ngày.

**- Quy trình làm việc AI-DLC:** Quy trình tuân theo một vòng lặp lặp lại bao gồm Các Tác vụ AI (như tạo và triển khai kế hoạch hoặc tìm kiếm sự làm rõ) và Các Tác vụ Con người (cung cấp sự làm rõ và triển khai kế hoạch). Trong quy trình này, AI liên tục đặt các câu hỏi làm rõ và chỉ tiến hành các giải pháp sau khi có sự xác thực của con người.

**- Các Giai đoạn AI-DLC:** Vòng đời được chia thành Khởi tạo (Inception), Xây dựng (Construction) và Vận hành (Operation), với mỗi giai đoạn thiết lập ngữ cảnh phong phú hơn cho giai đoạn tiếp theo:

+ Khởi tạo (Inception): Liên quan đến việc xây dựng ngữ cảnh, làm rõ ý định thông qua User Stories và lập kế hoạch thông qua Units of Work.

+ Xây dựng (Construction): Bao gồm mô hình hóa domain, tạo và kiểm thử mã (code generation and testing), bổ sung các thành phần kiến trúc và triển khai sử dụng Infrastructure as Code (IaC) và các bài test.

+ Vận hành (Operation): Tập trung vào triển khai production và quản lý sự cố.

**- Những Thách thức mà AI-DLC Hướng tới Giải quyết:**

+ Mở rộng quy mô phát triển AI: Các công cụ lập trình AI thường gặp khó khăn khi áp dụng cho các dự án phức tạp.

+ Quyền kiểm soát hạn chế: Các công cụ hiện tại khiến việc cộng tác và quản lý các AI agents trở nên khó khăn.

+ Chất lượng mã nguồn (Code quality): Duy trì kiểm soát chất lượng nghiêm ngặt khi chuyển từ proof-of-concept (PoC) sang production vẫn là một rào cản lớn.

## Tìm hiểu sâu: Kiro - AI IDE từ Prototype đến Production

- Kiro là một Môi trường phát triển tích hợp (IDE) ưu tiên AI (AI-first) được thiết kế để hỗ trợ AI-DLC, với trọng tâm cụ thể vào phát triển dựa trên đặc tả (Spec-driven development).

**- Spec-driven Development:** Kiro chuyển đổi các câu lệnh (prompts) cấp cao (ví dụ: "Tôi muốn tạo một ứng dụng chat giống như Slack") thành các yêu cầu chính xác (requirements.md), thiết kế hệ thống (design.md) và các tác vụ riêng biệt (tasks.md). Điều này thay đổi cơ bản việc phát triển từ "vibe coding" sang một quy trình có cấu trúc, có thể truy xuất nguồn gốc, nơi các lập trình viên cộng tác với Kiro trên các đặc tả này, đóng vai trò là nguồn sự thật duy nhất (single source of truth).

**- Quy trình làm việc Agentic (Agentic Workflows):** Các AI agents của Kiro thực thi các đặc tả trong khi vẫn đảm bảo lập trình viên con người nắm quyền kiểm soát. Các tính năng chính bao gồm:

**+ Kế hoạch Triển khai:** Kiro tạo ra một kế hoạch triển khai toàn diện chứa các tác vụ bắt đầu và tác vụ phụ (như "Triển khai đăng ký người dùng và các endpoint đăng nhập" hoặc "Triển khai JWT middleware"), liên kết chúng trực tiếp với các yêu cầu cụ thể để xác thực.

**+ Agent Hooks:** Các hook này ủy quyền các tác vụ cho AI agents được kích hoạt bởi các sự kiện như "lưu file" (file save). Chúng thực thi tự chủ trong nền dựa trên các prompt được định nghĩa trước, giúp tăng năng suất bằng cách tạo tài liệu, viết unit tests hoặc tối ưu hóa hiệu suất mã.

### Bài học Chính
**- AI Đảm bảo Sự sẵn sàng cho Production:** Bằng cách tạo ra các tài liệu thiết kế chi tiết—như biểu đồ luồng dữ liệu và hợp đồng API—và tạo unit tests trước khi viết code, Kiro đảm bảo rằng mã do AI tạo ra có thể bảo trì và sẵn sàng cho production, thay vì chỉ là một bản prototype nhanh chóng.

**- Sự kiểm soát của Con người thông qua Artifact:** Các lập trình viên duy trì quyền kiểm soát không phải bằng cách viết phần lớn mã, mà bằng cách xác thực và tinh chỉnh các artifact—cụ thể là các yêu cầu, thiết kế và kế hoạch tác vụ—trước khi AI agents tiến hành triển khai.

### Áp dụng vào Công việc

**- Tích hợp Amazon Q Developer/Các công cụ tương tự:** Tôi dự định tích hợp các trợ lý lập trình AI vào các dự án học thuật của mình để tự động hóa mã mẫu (boilerplate code) và các tác vụ thường ngày, từ đó tăng năng suất tổng thể.

**- Tập trung vào các Tác vụ Giá trị Cao:** Bằng cách cho phép AI xử lý các công việc nặng nhọc không tạo ra sự khác biệt, tôi có thể dành thời gian để làm chủ các hoạt động sáng tạo, có giá trị cao hơn như Domain Modeling và Architectural Design, vốn vẫn là những yếu tố lấy con người làm trung tâm trong giai đoạn Xây dựng.

### Trải nghiệm Sự kiện

Tham dự sự kiện **AI-Driven Development Life Cycle: Reimagining Software Engineering** đã mang lại cái nhìn hấp dẫn về tương lai của phát triển phần mềm. Rõ ràng là Generative AI không chỉ đơn thuần là một trợ lý lập trình; nó đang sẵn sàng trở thành người điều phối cốt lõi của toàn bộ quy trình phát triển. Phiên làm việc được cấu trúc tốt, tiến triển logic từ khái niệm bao quát của AI-DLC đến các bản demo cụ thể của Amazon Q Developer và Kiro. Bản demo Kiro đặc biệt ấn tượng, minh họa cách một text prompt đơn lẻ có thể được chuyển đổi thành một kế hoạch phát triển toàn diện, khả thi và có thể truy xuất nguồn gốc ngay trong IDE.

#### Bài học rút ra
- Ba thách thức chính liên quan đến phát triển AI hiện tại—mở rộng quy mô, quyền kiểm soát hạn chế và chất lượng mã nguồn—đã làm cho cách tiếp cận có cấu trúc, được con người xác thực của AI-DLC trở nên vô cùng cần thiết và được thiết kế tốt.

#### Một số hình ảnh sự kiện
![Ảnh nhóm trong sự kiện](/images/4-Event/TheBois-AIDLC.jpg)