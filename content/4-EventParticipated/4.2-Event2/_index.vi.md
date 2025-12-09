---
title: "Event 2"
date: "2025-11-15"
weight: 2
chapter: false
pre: " <b> 4.2. </b> "
---

# Báo cáo Tóm tắt: “AWS Cloud Mastery Series #1 - AI/ML/GenAI on AWS”

### Mục tiêu Sự kiện

- Cung cấp phần giới thiệu về AI, Machine Learning và Generative AI trong hệ sinh thái AWS.

### Diễn giả

- **Lam Tuan Kiet** – Sr DevOps Engineer, FPT Software
- **Danh Hoang Hieu Nghi** - AI Engineer, Renova Cloud
- **Dinh Le Hoang Anh** - Cloud Engineer Trainee, First Cloud AI Journey
- **Van Hoang Kha** - Cloud Security Engineer, AWS Community Builder

### Điểm nổi bật Chính

# Khám phá Generative AI với Amazon Bedrock:

**- Các mô hình nền tảng (Foundation Models):** Không giống như các mô hình truyền thống, chúng đóng vai trò là công cụ đa năng thích ứng với nhiều tác vụ. Bedrock cung cấp quyền truy cập vào các mô hình được quản lý hoàn toàn từ các công ty AI hàng đầu như OpenAI, Claude và Anthropic.
**- Prompt Engineering:** Nghệ thuật tạo và tinh chỉnh các hướng dẫn để tối ưu hóa đầu ra của mô hình.
    + Zero-Shot Prompting: Cung cấp prompt mà không cần ngữ cảnh hoặc ví dụ trước đó.
    + Few-shot Prompting: Bao gồm một lượng nhỏ ngữ cảnh và ví dụ trong prompt để hướng dẫn mô hình.
    + Chain of Thought: Khuyến khích mô hình phác thảo quy trình suy luận và các bước để đưa ra câu trả lời cuối cùng.
**- Retrieval Augmented Generation (RAG):** Một phương pháp để truy xuất thông tin liên quan từ các nguồn dữ liệu cụ thể. 

[Image of retrieval augmented generation flow diagram]

    + R: Retrieval - Thu thập thông tin liên quan từ knowledge base hoặc các nguồn dữ liệu bên ngoài.
    + A: Augmented - Kết hợp thông tin được truy xuất làm ngữ cảnh bổ sung trong prompt của người dùng trước khi nhập liệu.
    + G: Generation - Tạo phản hồi từ mô hình dựa trên prompt đã được tăng cường, nâng cao.
    + Các trường hợp sử dụng (Use cases): Các ứng dụng bao gồm nâng cao chất lượng nội dung, tạo chatbot theo ngữ cảnh, cho phép tìm kiếm cá nhân hóa và hỗ trợ tóm tắt dữ liệu thời gian thực.

**- Amazon Titan Embedding:** Một mô hình nhẹ được thiết kế để dịch văn bản thành các biểu diễn số (embeddings) một cách hiệu quả. Nó vượt trội trong các tác vụ truy xuất độ chính xác cao và hỗ trợ hơn 100 ngôn ngữ.

**- Các Dịch vụ AI được huấn luyện trước (Pretrained AI Services):** + Amazon Rekognition: Hỗ trợ phân tích hình ảnh và video.
  + Amazon Translate: Phát hiện và dịch văn bản giữa các ngôn ngữ.
  + Amazon Textract: Trích xuất văn bản và dữ liệu bố cục từ tài liệu.
  + Amazon Transcribe: Chuyển đổi giọng nói thành văn bản.
  + Amazon Polly: Chuyển đổi văn bản thành giọng nói sống động như thật.
  + Amazon Comprehend: Rút ra thông tin chi tiết và xác định mối quan hệ trong văn bản.
  + Amazon Kendra: Một dịch vụ tìm kiếm doanh nghiệp thông minh.
  + Amazon Lookout: Phát hiện bất thường trong các chỉ số kinh doanh, thiết bị và hình ảnh.
  + Amazon Personalize: Tùy chỉnh các đề xuất cho từng người dùng cá nhân.

**- Demo:** AMZPhoto: Một bản demo về khả năng nhận diện khuôn mặt sử dụng AI trên hình ảnh.

**- Amazon Bedrock AgentCore:** Một nền tảng toàn diện được thiết kế để giải quyết những thách thức khi triển khai các agent vào production:
  + Thực thi và mở rộng quy mô mã agent một cách an toàn.
  + Kết hợp bộ nhớ (memory) để lưu giữ các tương tác trong quá khứ và hỗ trợ việc học hỏi.
  + Triển khai các biện pháp kiểm soát định danh và truy cập cho cả agent và công cụ.
  + Cho phép sử dụng công cụ agentic cho các quy trình công việc phức tạp.
  + Khám phá và kết nối với các công cụ và tài nguyên tùy chỉnh.
  + Hiểu và kiểm toán mọi tương tác (observability).
  **+ Các Dịch vụ Nền tảng (Foundational Services):** Các dịch vụ được phân loại đảm bảo agent chạy an toàn ở quy mô lớn.

  **+ Nâng cao với công cụ & bộ nhớ:** Bao gồm các thành phần như Memory, Gateway, Browser tools và Code Interpreter.

  **+ Triển khai an toàn ở quy mô lớn:** Bao gồm quản lý Runtime và Identity.

  **+ Đạt được thông tin chi tiết vận hành:** Tập trung vào Observability.

  **+ Kích hoạt Agents ở Quy mô lớn (Kiến trúc):** Kết nối AgentCore Gateway (thông qua MCP) với các thành phần Memory, Identity, Observability, Browser và Code Interpreter.

  **+ Các Framework để Xây dựng Agents:** Hỗ trợ các framework như CrewAI, Google ADK, LangGraph/LangChain, LlamaIndex, OpenAI Agents SDK và Strands Agents SDK.

### Bài học Chính
- Bedrock là GenAI Hub: Amazon Bedrock đóng vai trò là trung tâm, cung cấp các Foundation Models được quản lý hoàn toàn từ những tên tuổi hàng đầu trong ngành cho nhiều tác vụ.

- Tùy chỉnh thông qua Prompts và Dữ liệu: Người dùng có thể tùy chỉnh các tương tác thông qua các kỹ thuật prompting khác nhau (Zero-Shot, Few-Shot, CoT) và sử dụng RAG để đưa ngữ cảnh vào nhằm có phản hồi mô hình tốt hơn.

- Embeddings Hỗ trợ Tìm kiếm: Amazon Titan Embeddings đóng vai trò quan trọng trong việc dịch văn bản thành dữ liệu số, từ đó tạo điều kiện cho các tác vụ truy xuất độ chính xác cao (như RAG).

- Các Mô hình Pretrained: AWS cung cấp một bộ các dịch vụ AI sẵn sàng triển khai cho các yêu cầu phổ biến, như Amazon Rekognition cho hình ảnh và Textract cho tài liệu.

- AgentCore Giải quyết các Vấn đề Production: Amazon Bedrock AgentCore là một nền tảng toàn diện giải quyết sự phức tạp của việc vận hành AI Agents ở quy mô lớn, quản lý các thành phần quan trọng như Memory, Identity và Observability.

### Áp dụng vào Công việc

- Những kiến thức thu được sẽ rất hữu ích cho các dự án sắp tới của team, có khả năng sẽ kết hợp các AI Foundation Models vào kiến trúc của chúng tôi.

### Trải nghiệm Sự kiện
- Các diễn giả diễn đạt rõ ràng và cung cấp nội dung rất giàu thông tin.
- Hỏi đáp (Q&A): Một thành viên trong nhóm đã đặt câu hỏi quan trọng cho dự án, mặc dù nó hơi lạc đề so với chủ đề chính.
  + Hỏi: Kiến trúc của chúng tôi sử dụng SNS để xử lý các phát hiện của GuardDuty (findings), nhưng chúng tôi gặp tắc nghẽn khi có hơn 1000 cảnh báo xảy ra đồng thời. Làm thế nào để giải quyết vấn đề này?
  + Đáp: Triển khai SQS để đưa các sự kiện vào hàng đợi (queue) đảm bảo rằng không có cảnh báo nào bị bỏ lỡ trong các giai đoạn có lưu lượng lớn.
- Tôi đã giành được vị trí trong top 10 trong bài kiểm tra Kahoot kết thúc và có cơ hội chụp ảnh với các diễn giả.
- Chúng tôi đã thành lập một nhóm không chính thức tên là "Mèo Cam Đeo Khăn", đại diện cho sự hợp tác giữa nhóm của tôi, "The Ballers", và "Vinhomies".

#### Một số hình ảnh sự kiện
![Nhóm Mèo Cam Đeo Khăn](/images/4-Event/Meocamdeokhan.jpg)