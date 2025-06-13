<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "26ab12045ee411ab7ad0eb0b1b7b1cbb",
  "translation_date": "2025-06-13T00:25:55+00:00",
  "source_file": "README.md",
  "language_code": "vi"
}
-->
![MCP-for-beginners](../../translated_images/mcp-beginners.2ce2b317996369ff66c5b72e25eff9d4288ab2741fc70c0b4e523d1ae1e249fd.vi.png) 

[![GitHub contributors](https://img.shields.io/github/contributors/microsoft/mcp-for-beginners.svg)](https://GitHub.com/microsoft/mcp-for-beginners/graphs/contributors)
[![GitHub issues](https://img.shields.io/github/issues/microsoft/mcp-for-beginners.svg)](https://GitHub.com/microsoft/mcp-for-beginners/issues)
[![GitHub pull-requests](https://img.shields.io/github/issues-pr/microsoft/mcp-for-beginners.svg)](https://GitHub.com/microsoft/mcp-for-beginners/pulls)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)

[![GitHub watchers](https://img.shields.io/github/watchers/microsoft/mcp-for-beginners.svg?style=social&label=Watch)](https://GitHub.com/microsoft/mcp-for-beginners/watchers)
[![GitHub forks](https://img.shields.io/github/forks/microsoft/mcp-for-beginners.svg?style=social&label=Fork)](https://GitHub.com/microsoft/mcp-for-beginners/fork)
[![GitHub stars](https://img.shields.io/github/stars/microsoft/mcp-for-beginners?style=social&label=Star)](https://GitHub.com/microsoft/mcp-for-beginners/stargazers)


[![Microsoft Azure AI Foundry Discord](https://dcbadge.vercel.app/api/server/ByRwuEEgH4)](https://discord.com/invite/ByRwuEEgH4)


Làm theo các bước sau để bắt đầu sử dụng các tài nguyên này:
1. **Fork Repository**: Nhấn vào [![GitHub forks](https://img.shields.io/github/forks/microsoft/mcp-for-beginners.svg?style=social&label=Fork)](https://GitHub.com/microsoft/mcp-for-beginners/fork)
2. **Clone Repository**:   `git clone https://github.com/microsoft/mcp-for-beginners.git`
3. [**Tham gia Azure AI Foundry Discord để gặp gỡ các chuyên gia và đồng nghiệp phát triển**](https://discord.com/invite/ByRwuEEgH4)


### 🌐 Hỗ trợ đa ngôn ngữ

#### Hỗ trợ qua GitHub Action (Tự động & Luôn cập nhật)

# 🚀 Giáo trình Model Context Protocol (MCP) cho người mới bắt đầu

## **Học MCP với các ví dụ mã thực hành bằng C#, Java, JavaScript, Python và TypeScript**

## 🧠 Tổng quan về giáo trình Model Context Protocol

**Model Context Protocol (MCP)** là một khuôn khổ tiên tiến được thiết kế để chuẩn hóa tương tác giữa các mô hình AI và ứng dụng khách. Giáo trình mã nguồn mở này cung cấp một lộ trình học có cấu trúc, kèm theo các ví dụ mã thực tế và các trường hợp sử dụng trong thế giới thực, trải dài trên các ngôn ngữ lập trình phổ biến như C#, Java, JavaScript, TypeScript và Python.

Dù bạn là nhà phát triển AI, kiến trúc sư hệ thống hay kỹ sư phần mềm, hướng dẫn này sẽ là nguồn tài nguyên toàn diện giúp bạn nắm vững các kiến thức cơ bản và chiến lược triển khai MCP.

## 🔗 Tài nguyên chính thức của MCP

- 📘 [MCP Documentation](https://modelcontextprotocol.io/) – Hướng dẫn chi tiết và tài liệu người dùng  
- 📜 [MCP Specification](https://spec.modelcontextprotocol.io/) – Kiến trúc giao thức và tài liệu kỹ thuật  
- 🧑‍💻 [MCP GitHub Repository](https://github.com/modelcontextprotocol) – SDK mã nguồn mở, công cụ và ví dụ mã  

## 🧭 Cấu trúc đầy đủ của giáo trình MCP

| Ch | Tiêu đề | Mô tả | Liên kết |
|--|--|--|--|
| 00 | **Giới thiệu về MCP** | Tổng quan về Model Context Protocol và tầm quan trọng của nó trong các pipeline AI, bao gồm MCP là gì, tại sao chuẩn hóa lại quan trọng và các trường hợp sử dụng cùng lợi ích thực tiễn | [Introduction](./00-Introduction/README.md) |
| 01 | **Giải thích các khái niệm cốt lõi** | Khám phá sâu về các khái niệm cốt lõi của MCP, bao gồm kiến trúc client-server, các thành phần chính của giao thức và các mẫu thông điệp | [Core Concepts](./01-CoreConcepts/README.md) |
| 02 | **Bảo mật trong MCP** | Nhận diện các mối đe dọa bảo mật trong hệ thống dựa trên MCP, kỹ thuật và thực hành tốt nhất để bảo vệ triển khai | [Security](/02-Security/README.md) |
| 03 | **Bắt đầu với MCP** | Thiết lập môi trường và cấu hình, tạo các server và client MCP cơ bản, tích hợp MCP với các ứng dụng hiện có | [Getting Started](./03-GettingStarted/README.md) |
| 3.1 | **Server đầu tiên** | Thiết lập một server cơ bản sử dụng giao thức MCP, hiểu cách tương tác giữa server và client, và kiểm thử server | [First Server](./03-GettingStarted/01-first-server/README.md) |
| 3.2 | **Client đầu tiên**  | Thiết lập một client cơ bản sử dụng giao thức MCP, hiểu cách tương tác giữa client và server, và kiểm thử client | [First Client](./03-GettingStarted/02-client/README.md) |
| 3.3 | **Client với LLM**  | Thiết lập một client sử dụng MCP cùng với Mô hình Ngôn ngữ Lớn (LLM) | [Client with LLM](./03-GettingStarted/03-llm-client/README.md) |
| 3.4 | **Sử dụng Visual Studio Code để kết nối server** | Thiết lập Visual Studio Code để sử dụng các server theo giao thức MCP | [Consuming a server with Visual Studio Code](./03-GettingStarted/04-vscode/README.md) |
| 3.5 | **Tạo server sử dụng SSE** | SSE giúp chúng ta mở server ra internet. Phần này sẽ hướng dẫn bạn tạo server dùng SSE | [Creating a server using SSE](./03-GettingStarted/05-sse-server/README.md) |
| 3.6 | **Sử dụng AI Toolkit** | AI Toolkit là công cụ tuyệt vời giúp bạn quản lý quy trình AI và MCP của mình. | [Use AI Toolkit](./03-GettingStarted/06-aitk/README.md) |
| 3.7 | **Kiểm thử server của bạn** | Kiểm thử là phần quan trọng trong quá trình phát triển. Phần này sẽ giúp bạn kiểm thử với nhiều công cụ khác nhau. | [Testing your server](./03-GettingStarted/07-testing/README.md) |
| 3.8 | **Triển khai server của bạn** | Làm thế nào để chuyển từ phát triển cục bộ sang sản xuất? Phần này sẽ hướng dẫn bạn phát triển và triển khai server. | [Deploy your server](./03-GettingStarted/08-deployment/README.md) |
| 04 | **Triển khai thực tế** | Sử dụng SDK trên nhiều ngôn ngữ, gỡ lỗi, kiểm thử và xác nhận, xây dựng các mẫu prompt và workflow có thể tái sử dụng | [Practical Implementation](./04-PracticalImplementation/README.md) |
| 05 | **Các chủ đề nâng cao trong MCP** | Workflow AI đa phương thức và khả năng mở rộng, chiến lược mở rộng bảo mật, MCP trong hệ sinh thái doanh nghiệp | [Advanced Topics](./05-AdvancedTopics/README.md) |
| 5.1 | **Tích hợp MCP với Azure** | Trình bày tích hợp với Azure | [MCP Azure integration](./05-AdvancedTopics/mcp-integration/README.md) |
| 5.2 | **Đa phương thức** | Hướng dẫn làm việc với các phương thức khác nhau như hình ảnh và nhiều hơn nữa | [Multi modality](./05-AdvancedTopics/mcp-multi-modality/README.md) |
| 5.3 | **Demo MCP OAuth2** | Ứng dụng Spring Boot tối giản trình diễn OAuth2 với MCP, cả vai trò Authorization và Resource Server. Minh họa cấp phát token an toàn, endpoint bảo vệ, triển khai Azure Container Apps, và tích hợp API Management. | [MCP OAuth2 Demo](./05-AdvancedTopics/mcp-oauth2-demo/README.md) |
| 5.4 | **Root Contexts** | Tìm hiểu thêm về root context và cách triển khai chúng | [Root Contexts](./05-AdvancedTopics/mcp-root-contexts/README.md) |
| 5.5 | **Routing** | Tìm hiểu các loại routing khác nhau | [Routing](./05-AdvancedTopics/mcp-routing/README.md) |
| 5.6 | **Sampling** | Học cách làm việc với sampling | [Sampling](./05-AdvancedTopics/mcp-sampling/README.md) |
| 5.7 | **Scaling** | Tìm hiểu về cách mở rộng server MCP, bao gồm chiến lược mở rộng ngang và dọc, tối ưu tài nguyên và điều chỉnh hiệu năng | [Scaling](./05-AdvancedTopics/mcp-scaling/README.md) |
| 5.8 | **Security** | Bảo mật server MCP của bạn, bao gồm xác thực, phân quyền và chiến lược bảo vệ dữ liệu | [Security](./05-AdvancedTopics/mcp-security/README.md) |
| 5.9 | **Web Search MCP** | Server và client MCP bằng Python tích hợp với SerpAPI cho tìm kiếm web, tin tức, sản phẩm và hỏi đáp theo thời gian thực. Minh họa phối hợp đa công cụ, tích hợp API bên ngoài và xử lý lỗi mạnh mẽ | [Web Search MCP](./05-AdvancedTopics/web-search-mcp/README.md) |
| 5.10 | **Streaming thời gian thực** | Streaming dữ liệu thời gian thực đã trở nên thiết yếu trong thế giới dữ liệu ngày nay, nơi doanh nghiệp và ứng dụng cần truy cập thông tin ngay lập tức để đưa ra quyết định kịp thời. | [Realtime Streaming](./05-AdvancedTopics/mcp-realtimestreaming/README.md) |
| 5.11 | **Tìm kiếm web thời gian thực** | Tìm kiếm web thời gian thực: MCP thay đổi cách quản lý ngữ cảnh trong tìm kiếm web, các mô hình AI, công cụ tìm kiếm và ứng dụng bằng cách cung cấp phương pháp chuẩn hóa. | [Realtime Web Search](./05-AdvancedTopics/mcp-realtimesearch/README.md) |
| 06 | **Đóng góp từ cộng đồng** | Cách đóng góp mã và tài liệu, hợp tác qua GitHub, các cải tiến và phản hồi do cộng đồng thúc đẩy | [Community Contributions](./06-CommunityContributions/README.md) |
| 07 | **Bài học từ những người dùng đầu tiên** | Triển khai thực tế và những gì đã thành công, xây dựng và triển khai giải pháp dựa trên MCP, xu hướng và lộ trình tương lai | [Insights](./07-LessonsFromEarlyAdoption/README.md) |
| 08 | **Thực hành tốt nhất cho MCP** | Tối ưu hiệu suất và điều chỉnh, thiết kế hệ thống MCP chịu lỗi, chiến lược kiểm thử và khả năng phục hồi | [Best Practices](./08-BestPractices/README.md) |
| 09 | **Nghiên cứu trường hợp MCP** | Phân tích sâu kiến trúc giải pháp MCP, bản thiết kế triển khai và mẹo tích hợp, sơ đồ chú thích và hướng dẫn dự án | [Case Studies](./09-CaseStudy/README.md) |
| 10 | **Tinh giản quy trình AI: Xây dựng máy chủ MCP với AI Toolkit** | Workshop thực hành toàn diện kết hợp MCP với AI Toolkit của Microsoft cho VS Code. Học cách xây dựng ứng dụng thông minh liên kết mô hình AI với công cụ thực tế qua các mô-đun thực tế bao gồm kiến thức cơ bản, phát triển máy chủ tùy chỉnh và chiến lược triển khai sản xuất. | [Hands On Lab](./10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/README.md) |

## Dự án mẫu

### 🧮 Dự án mẫu MCP Calculator:
<details>
  <summary><strong>Khám phá các triển khai mã theo ngôn ngữ</strong></summary>

  - [Ví dụ máy chủ MCP C#](./03-GettingStarted/samples/csharp/README.md)
  - [Máy tính MCP Java](./03-GettingStarted/samples/java/calculator/README.md)
  - [Demo MCP JavaScript](./03-GettingStarted/samples/javascript/README.md)
  - [Máy chủ MCP Python](../../03-GettingStarted/samples/python/mcp_calculator_server.py)
  - [Ví dụ MCP TypeScript](./03-GettingStarted/samples/typescript/README.md)

</details>

### 💡 Dự án MCP Calculator nâng cao:
<details>
  <summary><strong>Khám phá các mẫu nâng cao</strong></summary>

  - [Mẫu nâng cao C#](./04-PracticalImplementation/samples/csharp/README.md)
  - [Ví dụ ứng dụng Container Java](./04-PracticalImplementation/samples/java/containerapp/README.md)
  - [Mẫu nâng cao JavaScript](./04-PracticalImplementation/samples/javascript/README.md)
  - [Triển khai phức tạp Python](../../04-PracticalImplementation/samples/python/mcp_sample.py)
  - [Mẫu Container TypeScript](./04-PracticalImplementation/samples/typescript/README.md)

</details>

## 🎯 Yêu cầu cần thiết để học MCP

Để tận dụng tối đa chương trình học này, bạn nên có:

- Kiến thức cơ bản về C#, Java hoặc Python
- Hiểu biết về mô hình client-server và API
- (Tùy chọn) Quen thuộc với các khái niệm về máy học

## 📚 Hướng dẫn học tập

Một [Hướng dẫn học tập](./study_guide.md) toàn diện giúp bạn dễ dàng điều hướng kho lưu trữ này. Hướng dẫn bao gồm:

- Bản đồ chương trình trực quan thể hiện tất cả các chủ đề
- Phân tích chi tiết từng phần trong kho lưu trữ
- Hướng dẫn sử dụng các dự án mẫu
- Lộ trình học đề xuất theo từng trình độ kỹ năng
- Tài nguyên bổ sung hỗ trợ hành trình học của bạn

## 🛠️ Cách sử dụng chương trình học hiệu quả

Mỗi bài học trong hướng dẫn này bao gồm:

1. Giải thích rõ ràng các khái niệm MCP  
2. Ví dụ mã trực tiếp với nhiều ngôn ngữ  
3. Bài tập xây dựng ứng dụng MCP thực tế  
4. Tài nguyên bổ sung cho người học nâng cao  

## 📜 Thông tin bản quyền

Nội dung này được cấp phép theo **MIT License**. Điều khoản chi tiết xem tại [LICENSE](../../LICENSE).

## 🤝 Hướng dẫn đóng góp

Dự án này hoan nghênh các đóng góp và đề xuất. Hầu hết các đóng góp yêu cầu bạn đồng ý với Thỏa thuận Cấp phép Đóng góp (CLA) xác nhận bạn có quyền và thực sự cấp quyền sử dụng đóng góp của mình cho chúng tôi. Chi tiết xem tại <https://cla.opensource.microsoft.com>.

Khi bạn gửi pull request, bot CLA sẽ tự động xác định xem bạn có cần cung cấp CLA và gắn nhãn PR phù hợp (ví dụ: kiểm tra trạng thái, bình luận). Chỉ cần làm theo hướng dẫn của bot. Bạn chỉ cần làm điều này một lần cho tất cả các kho sử dụng CLA của chúng tôi.

Dự án này đã áp dụng [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/). Thông tin thêm xem tại [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) hoặc liên hệ [opencode@microsoft.com](mailto:opencode@microsoft.com) nếu có thắc mắc hoặc góp ý.

## 🎒 Các khóa học khác
Nhóm của chúng tôi còn có các khóa học khác! Hãy khám phá:

- [AI Agents For Beginners](https://github.com/microsoft/ai-agents-for-beginners?WT.mc_id=academic-105485-koreyst)
- [Generative AI for Beginners using .NET](https://github.com/microsoft/Generative-AI-for-beginners-dotnet?WT.mc_id=academic-105485-koreyst)
- [Generative AI for Beginners using JavaScript](https://github.com/microsoft/generative-ai-with-javascript?WT.mc_id=academic-105485-koreyst)
- [Generative AI for Beginners](https://github.com/microsoft/generative-ai-for-beginners?WT.mc_id=academic-105485-koreyst)
- [ML for Beginners](https://aka.ms/ml-beginners?WT.mc_id=academic-105485-koreyst)
- [Data Science for Beginners](https://aka.ms/datascience-beginners?WT.mc_id=academic-105485-koreyst)
- [AI for Beginners](https://aka.ms/ai-beginners?WT.mc_id=academic-105485-koreyst)
- [Cybersecurity for Beginners](https://github.com/microsoft/Security-101??WT.mc_id=academic-96948-sayoung)
- [Web Dev for Beginners](https://aka.ms/webdev-beginners?WT.mc_id=academic-105485-koreyst)
- [IoT for Beginners](https://aka.ms/iot-beginners?WT.mc_id=academic-105485-koreyst)
- [XR Development for Beginners](https://github.com/microsoft/xr-development-for-beginners?WT.mc_id=academic-105485-koreyst)
- [Mastering GitHub Copilot for AI Paired Programming](https://aka.ms/GitHubCopilotAI?WT.mc_id=academic-105485-koreyst)
- [Mastering GitHub Copilot for C#/.NET Developers](https://github.com/microsoft/mastering-github-copilot-for-dotnet-csharp-developers?WT.mc_id=academic-105485-koreyst)
- [Choose Your Own Copilot Adventure](https://github.com/microsoft/CopilotAdventures?WT.mc_id=academic-105485-koreyst)


## ™️ Thông Báo Thương Hiệu

Dự án này có thể chứa các thương hiệu hoặc logo của các dự án, sản phẩm hoặc dịch vụ. Việc sử dụng thương hiệu hoặc logo của Microsoft được ủy quyền phải tuân theo
[Hướng Dẫn Thương Hiệu & Nhãn Hiệu của Microsoft](https://www.microsoft.com/legal/intellectualproperty/trademarks/usage/general).
Việc sử dụng thương hiệu hoặc logo của Microsoft trong các phiên bản sửa đổi của dự án này không được gây nhầm lẫn hoặc ngụ ý Microsoft tài trợ.
Mọi việc sử dụng thương hiệu hoặc logo của bên thứ ba phải tuân theo chính sách của các bên đó.

**Tuyên bố miễn trừ trách nhiệm**:  
Tài liệu này đã được dịch bằng dịch vụ dịch thuật AI [Co-op Translator](https://github.com/Azure/co-op-translator). Mặc dù chúng tôi cố gắng đảm bảo độ chính xác, xin lưu ý rằng các bản dịch tự động có thể chứa lỗi hoặc sai sót. Tài liệu gốc bằng ngôn ngữ bản địa nên được xem là nguồn tham khảo chính xác nhất. Đối với các thông tin quan trọng, nên sử dụng dịch vụ dịch thuật chuyên nghiệp do con người thực hiện. Chúng tôi không chịu trách nhiệm về bất kỳ hiểu lầm hay giải thích sai nào phát sinh từ việc sử dụng bản dịch này.