<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "25a94c681cf43612ff394d8cf78a74de",
  "translation_date": "2025-05-27T16:08:38+00:00",
  "source_file": "00-Introduction/README.md",
  "language_code": "vi"
}
-->
# Giới thiệu về Model Context Protocol (MCP): Tại sao nó quan trọng đối với các ứng dụng AI có thể mở rộng

Các ứng dụng AI sinh tạo là một bước tiến lớn vì chúng thường cho phép người dùng tương tác với ứng dụng bằng các câu lệnh ngôn ngữ tự nhiên. Tuy nhiên, khi ngày càng đầu tư nhiều thời gian và tài nguyên vào các ứng dụng này, bạn cần đảm bảo rằng có thể dễ dàng tích hợp các chức năng và nguồn lực sao cho dễ dàng mở rộng, ứng dụng có thể hỗ trợ nhiều mô hình cùng lúc và xử lý các đặc điểm phức tạp của từng mô hình. Nói tóm lại, xây dựng ứng dụng Gen AI ban đầu rất đơn giản, nhưng khi chúng phát triển và trở nên phức tạp hơn, bạn cần bắt đầu xác định kiến trúc và có thể cần dựa vào một chuẩn để đảm bảo các ứng dụng được xây dựng một cách nhất quán. Đây chính là vai trò của MCP trong việc tổ chức và cung cấp một chuẩn mực.

---

## **🔍 Model Context Protocol (MCP) là gì?**

**Model Context Protocol (MCP)** là một **giao diện mở, chuẩn hóa** cho phép các Mô hình Ngôn ngữ Lớn (LLMs) tương tác mượt mà với các công cụ bên ngoài, API và nguồn dữ liệu. Nó cung cấp một kiến trúc nhất quán để nâng cao chức năng của mô hình AI vượt ra ngoài dữ liệu huấn luyện, giúp hệ thống AI thông minh hơn, có khả năng mở rộng và phản hồi nhanh hơn.

---

## **🎯 Tại sao chuẩn hóa trong AI lại quan trọng**

Khi các ứng dụng AI sinh tạo ngày càng phức tạp, việc áp dụng các chuẩn để đảm bảo **khả năng mở rộng, dễ dàng mở rộng** và **dễ bảo trì** là điều cần thiết. MCP giải quyết những nhu cầu này bằng cách:

- Thống nhất việc tích hợp mô hình với công cụ
- Giảm thiểu các giải pháp tùy chỉnh dễ hỏng hóc, một lần
- Cho phép nhiều mô hình cùng tồn tại trong một hệ sinh thái

---

## **📚 Mục tiêu học tập**

Sau khi đọc xong bài viết này, bạn sẽ có thể:

- Định nghĩa **Model Context Protocol (MCP)** và các trường hợp sử dụng của nó
- Hiểu cách MCP chuẩn hóa giao tiếp giữa mô hình và công cụ
- Xác định các thành phần cốt lõi trong kiến trúc MCP
- Khám phá các ứng dụng thực tế của MCP trong doanh nghiệp và phát triển

---

## **💡 Tại sao Model Context Protocol (MCP) là bước đột phá**

### **🔗 MCP giải quyết sự phân mảnh trong tương tác AI**

Trước MCP, việc tích hợp mô hình với công cụ đòi hỏi:

- Mã tùy chỉnh cho từng cặp công cụ - mô hình
- API không chuẩn cho từng nhà cung cấp
- Thường xuyên bị gián đoạn do cập nhật
- Khả năng mở rộng kém khi có nhiều công cụ hơn

### **✅ Lợi ích của việc chuẩn hóa MCP**

| **Lợi ích**              | **Mô tả**                                                                    |
|--------------------------|------------------------------------------------------------------------------|
| Tương tác đa chiều       | LLM hoạt động trơn tru với các công cụ từ nhiều nhà cung cấp khác nhau       |
| Tính nhất quán           | Hành vi đồng nhất trên các nền tảng và công cụ                               |
| Tái sử dụng              | Công cụ xây dựng một lần có thể dùng lại trên nhiều dự án và hệ thống        |
| Tăng tốc phát triển      | Giảm thời gian phát triển bằng cách sử dụng giao diện chuẩn, cắm là chạy     |

---

## **🧱 Tổng quan kiến trúc MCP cấp cao**

MCP theo mô hình **client-server**, trong đó:

- **MCP Hosts** chạy các mô hình AI
- **MCP Clients** khởi tạo yêu cầu
- **MCP Servers** cung cấp ngữ cảnh, công cụ và khả năng

### **Các thành phần chính:**

- **Resources** – Dữ liệu tĩnh hoặc động cho mô hình  
- **Prompts** – Các quy trình đã định sẵn để hướng dẫn sinh tạo  
- **Tools** – Các hàm thực thi như tìm kiếm, tính toán  
- **Sampling** – Hành vi tác nhân qua các tương tác đệ quy

---

## Cách MCP Servers hoạt động

MCP server hoạt động theo cách sau:

- **Luồng yêu cầu**:  
    1. MCP Client gửi yêu cầu đến mô hình AI đang chạy trong MCP Host.  
    2. Mô hình AI xác định khi nào cần công cụ hoặc dữ liệu bên ngoài.  
    3. Mô hình giao tiếp với MCP Server qua giao thức chuẩn hóa.

- **Chức năng của MCP Server**:  
    - Đăng ký công cụ: Quản lý danh mục các công cụ và khả năng của chúng.  
    - Xác thực: Kiểm tra quyền truy cập công cụ.  
    - Xử lý yêu cầu: Xử lý các yêu cầu công cụ từ mô hình.  
    - Định dạng phản hồi: Cấu trúc đầu ra công cụ theo định dạng mô hình có thể hiểu.

- **Thực thi công cụ**:  
    - Server chuyển tiếp yêu cầu đến các công cụ bên ngoài phù hợp  
    - Công cụ thực hiện chức năng chuyên biệt (tìm kiếm, tính toán, truy vấn cơ sở dữ liệu, v.v.)  
    - Kết quả được trả về mô hình theo định dạng nhất quán.

- **Hoàn tất phản hồi**:  
    - Mô hình AI kết hợp kết quả công cụ vào phản hồi của mình.  
    - Phản hồi cuối cùng được gửi lại ứng dụng client.

```mermaid
graph TD
    A[AI Model in MCP Host] <-->|MCP Protocol| B[MCP Server]
    B <-->|Tool Interface| C[Tool 1: Web Search]
    B <-->|Tool Interface| D[Tool 2: Calculator]
    B <-->|Tool Interface| E[Tool 3: Database Access]
    B <-->|Tool Interface| F[Tool 4: File System]
    
    Client[MCP Client/Application] -->|Sends Request| A
    A -->|Returns Response| Client
    
    subgraph "MCP Server Components"
        B
        G[Tool Registry]
        H[Authentication]
        I[Request Handler]
        J[Response Formatter]
    end
    
    B <--> G
    B <--> H
    B <--> I
    B <--> J
    
    style A fill:#f9d5e5,stroke:#333,stroke-width:2px
    style B fill:#eeeeee,stroke:#333,stroke-width:2px
    style Client fill:#d5e8f9,stroke:#333,stroke-width:2px
    style C fill:#c2f0c2,stroke:#333,stroke-width:1px
    style D fill:#c2f0c2,stroke:#333,stroke-width:1px
    style E fill:#c2f0c2,stroke:#333,stroke-width:1px
    style F fill:#c2f0c2,stroke:#333,stroke-width:1px    
```

## 👨‍💻 Cách xây dựng MCP Server (có ví dụ)

MCP server cho phép bạn mở rộng khả năng của LLM bằng cách cung cấp dữ liệu và chức năng.

Sẵn sàng thử chưa? Dưới đây là ví dụ tạo MCP server đơn giản bằng các ngôn ngữ khác nhau:

- **Ví dụ Python**: https://github.com/modelcontextprotocol/python-sdk

- **Ví dụ TypeScript**: https://github.com/modelcontextprotocol/typescript-sdk

- **Ví dụ Java**: https://github.com/modelcontextprotocol/java-sdk

- **Ví dụ C#/.NET**: https://github.com/modelcontextprotocol/csharp-sdk


## 🌍 Các trường hợp sử dụng thực tế của MCP

MCP mở rộng khả năng AI cho nhiều ứng dụng khác nhau:

| **Ứng dụng**               | **Mô tả**                                                                    |
|---------------------------|------------------------------------------------------------------------------|
| Tích hợp dữ liệu doanh nghiệp | Kết nối LLM với cơ sở dữ liệu, CRM hoặc công cụ nội bộ                      |
| Hệ thống AI tác nhân       | Cho phép các tác nhân tự chủ truy cập công cụ và quy trình ra quyết định     |
| Ứng dụng đa phương tiện    | Kết hợp công cụ xử lý văn bản, hình ảnh, âm thanh trong một ứng dụng AI thống nhất |
| Tích hợp dữ liệu thời gian thực | Đưa dữ liệu trực tiếp vào tương tác AI để có kết quả chính xác và cập nhật  |

### 🧠 MCP = Chuẩn phổ quát cho tương tác AI

Model Context Protocol (MCP) hoạt động như một chuẩn phổ quát cho các tương tác AI, giống như USB-C đã chuẩn hóa kết nối vật lý cho các thiết bị. Trong thế giới AI, MCP cung cấp một giao diện nhất quán, cho phép các mô hình (client) tích hợp mượt mà với các công cụ và nhà cung cấp dữ liệu bên ngoài (server). Điều này loại bỏ nhu cầu sử dụng các giao thức tùy chỉnh đa dạng cho từng API hoặc nguồn dữ liệu.

Theo MCP, một công cụ tương thích MCP (được gọi là MCP server) tuân theo một chuẩn thống nhất. Các server này có thể liệt kê các công cụ hoặc hành động mà chúng cung cấp và thực thi các hành động đó khi được tác nhân AI yêu cầu. Các nền tảng tác nhân AI hỗ trợ MCP có khả năng phát hiện các công cụ có sẵn từ các server và gọi chúng qua giao thức chuẩn này.

### 💡 Hỗ trợ truy cập kiến thức

Ngoài việc cung cấp công cụ, MCP còn hỗ trợ truy cập kiến thức. Nó cho phép ứng dụng cung cấp ngữ cảnh cho các mô hình ngôn ngữ lớn (LLM) bằng cách liên kết chúng với nhiều nguồn dữ liệu khác nhau. Ví dụ, một MCP server có thể đại diện cho kho tài liệu của một công ty, cho phép các tác nhân truy xuất thông tin liên quan khi cần. Một server khác có thể xử lý các hành động cụ thể như gửi email hoặc cập nhật hồ sơ. Với tác nhân, đây chỉ đơn giản là các công cụ mà nó có thể sử dụng — một số công cụ trả về dữ liệu (ngữ cảnh kiến thức), trong khi những công cụ khác thực hiện hành động. MCP quản lý hiệu quả cả hai.

Một tác nhân kết nối với MCP server tự động nhận biết các khả năng và dữ liệu có thể truy cập của server thông qua định dạng chuẩn. Sự chuẩn hóa này cho phép công cụ có thể thay đổi linh hoạt. Ví dụ, thêm một MCP server mới vào hệ thống của tác nhân sẽ khiến các chức năng của server đó có thể sử dụng ngay mà không cần tùy chỉnh thêm hướng dẫn cho tác nhân.

Việc tích hợp này được minh họa rõ trong sơ đồ mermaid, nơi các server cung cấp cả công cụ và kiến thức, đảm bảo sự phối hợp mượt mà giữa các hệ thống.

### 👉 Ví dụ: Giải pháp tác nhân có khả năng mở rộng

```mermaid
graph TD
    User -->|Prompt| LLM
    LLM -->|Response| User
    LLM -->|MCP| ServerA
    LLM -->|MCP| ServerB
    ServerA -->|Universal connector| ServerB
    ServerA --> KnowledgeA
    ServerA --> ToolsA
    ServerB --> KnowledgeB
    ServerB --> ToolsB

    subgraph Server A
        KnowledgeA[Knowledge]
        ToolsA[Tools]
    end

    subgraph Server B
        KnowledgeB[Knowledge]
        ToolsB[Tools]
    end
```

### 🔄 Kịch bản MCP nâng cao với tích hợp LLM phía client

Ngoài kiến trúc MCP cơ bản, còn có các kịch bản nâng cao khi cả client và server đều chứa LLM, cho phép tương tác phức tạp hơn:

```mermaid
sequenceDiagram
    autonumber
    actor User as 👤 User
    participant ClientApp as 🖥️ Client App
    participant ClientLLM as 🧠 Client LLM
    participant Server1 as 🔧 MCP Server 1
    participant Server2 as 📚 MCP Server 2
    participant ServerLLM as 🤖 Server LLM
    
    %% Discovery Phase
    rect rgb(220, 240, 255)
        Note over ClientApp, Server2: TOOL DISCOVERY PHASE
        ClientApp->>+Server1: Request available tools/resources
        Server1-->>-ClientApp: Return tool list (JSON)
        ClientApp->>+Server2: Request available tools/resources
        Server2-->>-ClientApp: Return tool list (JSON)
        Note right of ClientApp: Store combined tool<br/>catalog locally
    end
    
    %% User Interaction
    rect rgb(255, 240, 220)
        Note over User, ClientLLM: USER INTERACTION PHASE
        User->>+ClientApp: Enter natural language prompt
        ClientApp->>+ClientLLM: Forward prompt + tool catalog
        ClientLLM->>-ClientLLM: Analyze prompt & select tools
    end
    
    %% Scenario A: Direct Tool Calling
    alt Direct Tool Calling
        rect rgb(220, 255, 220)
            Note over ClientApp, Server1: SCENARIO A: DIRECT TOOL CALLING
            ClientLLM->>+ClientApp: Request tool execution
            ClientApp->>+Server1: Execute specific tool
            Server1-->>-ClientApp: Return results
            ClientApp->>+ClientLLM: Process results
            ClientLLM-->>-ClientApp: Generate response
            ClientApp-->>-User: Display final answer
        end
    
    %% Scenario B: Feature Negotiation (VS Code style)
    else Feature Negotiation (VS Code style)
        rect rgb(255, 220, 220)
            Note over ClientApp, ServerLLM: SCENARIO B: FEATURE NEGOTIATION
            ClientLLM->>+ClientApp: Identify needed capabilities
            ClientApp->>+Server2: Negotiate features/capabilities
            Server2->>+ServerLLM: Request additional context
            ServerLLM-->>-Server2: Provide context
            Server2-->>-ClientApp: Return available features
            ClientApp->>+Server2: Call negotiated tools
            Server2-->>-ClientApp: Return results
            ClientApp->>+ClientLLM: Process results
            ClientLLM-->>-ClientApp: Generate response
            ClientApp-->>-User: Display final answer
        end
    end
```

## 🔐 Lợi ích thực tế của MCP

Dưới đây là các lợi ích thực tế khi sử dụng MCP:

- **Cập nhật mới nhất**: Mô hình có thể truy cập thông tin cập nhật ngoài dữ liệu huấn luyện  
- **Mở rộng khả năng**: Mô hình có thể sử dụng các công cụ chuyên biệt cho các tác vụ chưa được huấn luyện  
- **Giảm ảo tưởng**: Nguồn dữ liệu bên ngoài cung cấp cơ sở thực tế  
- **Bảo mật**: Dữ liệu nhạy cảm có thể được giữ trong môi trường an toàn thay vì nhúng vào câu lệnh

## 📌 Những điểm cần nhớ

Những điểm chính khi sử dụng MCP:

- **MCP** chuẩn hóa cách mô hình AI tương tác với công cụ và dữ liệu  
- Thúc đẩy **khả năng mở rộng, tính nhất quán và tương tác đa chiều**  
- MCP giúp **giảm thời gian phát triển, nâng cao độ tin cậy và mở rộng khả năng mô hình**  
- Kiến trúc client-server **cho phép ứng dụng AI linh hoạt và dễ mở rộng**

## 🧠 Bài tập

Hãy nghĩ về một ứng dụng AI mà bạn muốn xây dựng.

- Những **công cụ hoặc dữ liệu bên ngoài** nào có thể nâng cao khả năng của nó?  
- MCP có thể giúp việc tích hợp trở nên **đơn giản và đáng tin cậy hơn** như thế nào?

## Tài nguyên bổ sung

- [MCP GitHub Repository](https://github.com/modelcontextprotocol)

## Tiếp theo

Tiếp: [Chapter 1: Core Concepts](/01-CoreConcepts/README.md)

**Tuyên bố từ chối trách nhiệm**:  
Tài liệu này đã được dịch bằng dịch vụ dịch thuật AI [Co-op Translator](https://github.com/Azure/co-op-translator). Mặc dù chúng tôi cố gắng đảm bảo độ chính xác, xin lưu ý rằng các bản dịch tự động có thể chứa lỗi hoặc không chính xác. Tài liệu gốc bằng ngôn ngữ gốc của nó nên được coi là nguồn tham khảo chính thức. Đối với các thông tin quan trọng, nên sử dụng dịch vụ dịch thuật chuyên nghiệp do con người thực hiện. Chúng tôi không chịu trách nhiệm về bất kỳ sự hiểu nhầm hoặc giải thích sai nào phát sinh từ việc sử dụng bản dịch này.