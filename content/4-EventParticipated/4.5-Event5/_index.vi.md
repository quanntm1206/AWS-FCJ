---
title: "Event 5"
date: "2025-11-29"
weight: 5
chapter: false
pre: " <b> 4.5.</b> "
---

# Báo cáo Tóm tắt: “BUILDING AGENTIC AI - Context Optimization with Amazon Bedrock”

## Mục tiêu Sự kiện

- Thực hiện tìm hiểu sâu về kỹ thuật (technical deep-dive) đối với AWS Bedrock Agent Core.
- Minh họa việc xây dựng các Quy trình làm việc Agentic (Agentic Workflows) trong hệ sinh thái AWS.
- Giới thiệu **Diaflow** như một nền tảng tự động hóa AI.
- Giới thiệu **CloudThinker** và các khả năng của nó trong Vận hành Đám mây (Cloud Operations).
- Khám phá các chiến lược Điều phối Agentic (Agentic Orchestration) và Tối ưu hóa Ngữ cảnh (Context Optimization) sử dụng Amazon Bedrock.
- Tạo điều kiện học tập thực tế thông qua CloudThinker Hack: Hands-on Workshop.

## Diễn giả

- **Nguyen Gia Hung** - Head of Solutions Architect, AWS
- **Kien Nguyen** - AWS Startup Solutions Architect
- **Viet Pham** - CEO & Founder, Diaflow
- **Thang Ton** - Co-Founder & COO, CloudThinker
- **Henry Bui** - Head of Engineering, CloudThinker
- **Van Hoang Kha** - AWS Community Leader
- **Nhat Tran** - CTO, CloudThinker

## Điểm nổi bật Chính

### Amazon Bedrock AgentCore

**Sự tiến hóa lên Agentic AI:** Việc các doanh nghiệp áp dụng các hệ thống Agentic AI đang tăng tốc nhanh chóng. AWS định vị mình là môi trường tối ưu để xây dựng và mở rộng quy mô các AI Agents này.

**Cung cấp từ Hệ sinh thái AWS:**
- **Frameworks:** Hỗ trợ tích hợp với Strands, LangGraph, OpenAI, v.v.
- **Applications (Ứng dụng):** Các dịch vụ bao gồm Kiro và AWS QuickSuite.
- **Foundation (Nền tảng):** Được xây dựng dựa trên Amazon SageMaker và Amazon Bedrock Models.

**Các thành phần cốt lõi của Amazon Bedrock AgentCore:**
- **Runtime:** Một môi trường triển khai agent không máy chủ (serverless), an toàn giúp mở rộng khối lượng công việc và tăng tốc thời gian đưa ra thị trường.
- **Identity:** Quản lý định danh và truy cập (IAM) cấp doanh nghiệp giúp tăng tốc phát triển trong khi bảo mật quyền truy cập cho AI Agents.
- **Gateway:** Cung cấp quyền truy cập thống nhất, an toàn vào các công cụ, với khả năng khám phá công cụ thông minh.
- **Memory:** Tạo điều kiện lưu giữ bộ nhớ nhận thức ngữ cảnh thông minh, đơn giản hóa việc quản lý dữ liệu cấp doanh nghiệp với các tùy chọn tùy chỉnh sâu.
- **Browser:** Một runtime trình duyệt đám mây serverless, có thể mở rộng, cung cấp bảo mật và khả năng quan sát cấp doanh nghiệp.
- **Code Interpreter:** Một môi trường sandboxed an toàn để thực thi mã, cho phép xử lý dữ liệu quy mô lớn một cách dễ dàng.
- **Observability:** Cung cấp khả năng hiển thị hoàn chỉnh về hiệu suất của agent để duy trì chất lượng và sự tin cậy trong khi tích hợp liền mạch với các công cụ quan sát khác.

### Diaflow: Nền tảng Tự động hóa AI

Diaflow là một Nền tảng Tự động hóa AI cho Doanh nghiệp được thiết kế để khai mở tiềm năng của đội ngũ bằng cách cung cấp các công cụ linh hoạt, không cần mã (no-code) để tự động hóa các quy trình công việc quan trọng một cách nhanh chóng.

- **Sứ mệnh:** Biến các quy trình thủ công thành các quy trình làm việc thông minh trong vài phút, giải quyết thực trạng 90% doanh nghiệp lãng phí hơn 20 giờ mỗi người mỗi tuần cho các tác vụ lặp lại, đồng thời giải quyết các lo ngại về quyền riêng tư dữ liệu.
- **Sự chấp nhận:** Hơn 6.000 người dùng trên toàn cầu trong các lĩnh vực Bán lẻ, Dịch vụ CNTT, Tài chính, Tiếp thị và Chăm sóc sức khỏe.
- **Được hậu thuẫn bởi:** Được phát triển bởi các chuyên gia từ các tổ chức công nghệ lớn và được hỗ trợ bởi các đối tác như NVIDIA, Microsoft, AWS và Google.
- **Sự hiện diện:** Hoạt động tại Mỹ, Thụy Sĩ, Pháp, Hàn Quốc, Singapore và Việt Nam.

**Các khả năng & Tính năng Cốt lõi:**
- **AI-Powered Automation:** Giảm 80% các tác vụ thủ công bằng cách kết nối Cơ sở dữ liệu, Ứng dụng, Knowledge Bases, API và các hệ thống Legacy.
- **Autonomous Task Execution:** Người dùng mô tả mục tiêu, và Diaflow lập kế hoạch và thực hiện các bước cần thiết.
- **Multi-Model Processing:** Hỗ trợ nhiều LLM khác nhau bao gồm Claude, Gemini và Deepseek.
- **Enterprise-Grade Security:** Tuân thủ HIPAA, SOC2 và GDPR.

### CloudThinker: Agentic Cloud Operations

CloudThinker giải quyết các thách thức phổ biến của khách hàng như chi phí đám mây bùng nổ, sự phức tạp của quản lý đám mây vượt quá khả năng và phản ứng sự cố thụ động.

**Khả năng: Insights (Thông tin chi tiết) -> Reasoning (Suy luận) -> Execution (Thực thi)**
- Cộng tác Đa agent (Multi-agent Collaboration)
- Vận hành Tự chủ (Autonomous Operations)
- Tối ưu hóa & Học tập Liên tục
- Khả năng Đa đám mây (Multi-cloud Capability)

**Đội ngũ CloudThinker AI Agent:**
- **Alex:** Cloud Engineer
- **Kai:** Kubernetes Engineer
- **Anna:** General Manager
- **Oliver:** Security Engineer
- **Tony:** Database Engineer

### Agentic Orchestration và Context Optimization

#### Kiến trúc AI Agent
- **Chatbots so với Agents:** Không giống như các chatbot thụ động sử dụng các quyết định dựa trên quy tắc, Agents chủ động, có khả năng bắt đầu hành động, đưa ra các quyết định động và thích ứng thông qua kinh nghiệm để xử lý các tác vụ nhiều bước.
- **Các thành phần Cốt lõi:**
    + **Planning (Lập kế hoạch):** Phân rã các tác vụ thành các bước có thể thực thi.
    + **Memory (Bộ nhớ):** Lưu giữ ngữ cảnh và lịch sử tương tác.
    + **Tools (Công cụ):** Giao tiếp với các API bên ngoài, công cụ tìm kiếm và trình thông dịch mã.
    + **Action (Hành động):** Thực thi kế hoạch và đưa ra phản hồi cuối cùng.

#### Bắt đầu với Agents
- **Kiến trúc ReAct:** Một mô hình đan xen giữa suy nghĩ và hành động (User Input → Reasoning/Thought → Action/Tool Use → Observation → Final Answer).
- **Lựa chọn Công cụ:** Các công cụ hiệu quả phải sở hữu Ngữ cảnh Agent, hỗ trợ các quy trình làm việc đa dạng, cho phép giải quyết vấn đề trực quan và trải qua các thử nghiệm thực tế nghiêm ngặt.

#### Các mô hình Phối hợp: Giải quyết các Điểm nghẽn
Các hệ thống Single-Agent thường đối mặt với "sự cô lập ngữ cảnh" (xử lý 100k+ tokens) và các điểm nghẽn xử lý tuần tự. Điều phối phân tán giải quyết vấn đề này thông qua hai mô hình chính:

| Tính năng | Network (Peer-to-Peer) | Supervisor |
| :--- | :--- | :--- |
| **Cấu trúc** | Các agents giao tiếp trực tiếp với nhau. | Một Supervisor trung tâm ủy quyền nhiệm vụ cho các Worker agents chuyên biệt. |
| **Ưu điểm** | * Giao tiếp linh hoạt.<br>* Khả năng chịu lỗi cao.<br>* Dễ dàng chuyển đổi từ chế độ single-agent. | * Ủy quyền nhiệm vụ rõ ràng.<br>* Phối hợp tập trung.<br>* Kiến trúc mô-đun và có thể mở rộng. |
| **Nhược điểm** | * Gỡ lỗi phức tạp.<br>* Sự mơ hồ về quyền sở hữu. | * Rủi ro điểm nghẽn tiềm ẩn.<br>* Không linh hoạt khi chuyển sang chế độ single-agent. |

**Các biến thể Supervisor:**
1.  **Group Chat-based:** Ngữ cảnh cộng tác, phối hợp đơn giản. *Được sử dụng bởi CloudThinker.*
2.  **Supervisor as Tool (Subagents):** Kiểm soát chi tiết, worker ít tự chủ hơn.
3.  **Hierarchical:** Giám sát đa lớp, có thể mở rộng cho các tổ chức lớn.

#### Giải quyết Bài toán Chi phí Agentic 100:1
Các kiến trúc Agentic đối mặt với "Sự bùng nổ Ngữ cảnh" (Context Explosion) nơi tỷ lệ token Input/Output có thể đạt 100:1 (so với 3:1 cho chatbot). Để giải quyết vấn đề này, bốn kỹ thuật "Quick-win" đã được trình bày, mang lại khoản tiết kiệm chi phí 80–95% và giảm độ trễ 3–5 lần:

1.  **Prompt Caching:**
    * *Mục tiêu:* Giảm 70–90% chi phí.
    * *Phương pháp:* Kiến trúc Ba tầng (Three-Tier Architecture) nơi System Prompt và Lịch sử Hội thoại được cache, trong khi lượt hiện tại vẫn động.
2.  **Context Compaction:**
    * *Mục tiêu:* Giảm 80% chi phí tóm tắt.
    * *Phương pháp:* Cache-Preserving Summarization thêm các hướng dẫn ở cấp độ payload để tóm tắt các tin nhắn cũ mà không phá vỡ cache keys.
3.  **Tool Consolidation:**
    * *Mục tiêu:* Giảm 20% số lượng token và ảo giác (hallucinations).
    * *Phương pháp:* Hợp nhất các hoạt động CRUD vào các giao diện đơn lẻ và sử dụng **Just-In-Time Schemas** để tìm nạp tài liệu chỉ khi cần thiết.
4.  **Parallel Tool Calling:**
    * *Mục tiêu:* Giảm 30–40% số vòng lặp (round trips).
    * *Phương pháp:* Cung cấp hướng dẫn rõ ràng cho LLM để song song hóa các lệnh gọi công cụ và các bước suy luận.

#### Cross-Region Inference (Suy luận Liên vùng)
Để tránh giới hạn tốc độ (rate limits) do khối lượng gọi công cụ lớn (50–100 mỗi tác vụ), khối lượng công việc được tự động định tuyến qua các khu vực toàn cầu (US, EU, APAC). Điều này loại bỏ các điểm lỗi đơn lẻ và cung cấp hồ sơ toàn cầu cho độ trễ gần như bằng không.

> **Key Insight:** Hệ thống multi-agent tốt nhất tự nhận ra khi nào *KHÔNG* nên sử dụng nhiều agents.

## CloudThinker Hack: Hands-On Workshop

Ban tổ chức đã cung cấp cho người tham dự quyền truy cập vào hướng dẫn CloudThinker và Mã gói Standard miễn phí để phân tích Tài khoản AWS cá nhân của họ.

## Trải nghiệm Sự kiện

Sự kiện này rất giàu thông tin, củng cố đáng kể sự hiểu biết của chúng tôi về Amazon Bedrock và giới thiệu cho chúng tôi các công cụ mạnh mẽ như Diaflow và CloudThinker.

**Câu chuyện Thành công:**
Trong workshop *CloudThinker Hack*, nhóm chúng tôi đã sử dụng công cụ này để phân tích cơ sở hạ tầng Tài khoản AWS của mình.
- **Phát hiện:** CloudThinker đã xác định thành công khối lượng yêu cầu GET S3 Bucket cao bất thường (hơn 3 triệu yêu cầu trong khoảng thời gian 2 tuần).
- **Giải pháp:** Agent đã khuyến nghị sử dụng **Amazon Data Firehose** để hợp nhất các log trước khi lưu chúng vào S3, thay vì ghi các tệp nhỏ riêng lẻ.
- **Kết quả:** Nhóm chúng tôi đã được trao giải thưởng vì đã sử dụng CloudThinker hiệu quả để chẩn đoán và giải quyết vấn đề này. Chúng tôi đã nhận được Áo thun và Móc khóa CloudThinker.

#### Một số hình ảnh sự kiện
![Hình ảnh tất cả người tham dự](/images/4-Event/Event7AllAttendee.jpg)
_Hình ảnh tất cả người tham dự_

![Nhận giải thưởng từ CloudThinker 1](/images/4-Event/CloudThinkerPrize1.jpg)
_Nhận giải thưởng từ CloudThinker_

![Nhận giải thưởng từ CloudThinker 2](/images/4-Event/CloudThinkerPrize2.jpg)
_Nhận giải thưởng từ CloudThinker_