<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "2bbbcded256d46a24e3f448384a2b4a2",
  "translation_date": "2025-07-29T01:13:21+00:00",
  "source_file": "00-Introduction/README.md",
  "language_code": "fa"
}
-->
# مقدمه‌ای بر پروتکل زمینه مدل (MCP): چرا برای برنامه‌های مقیاس‌پذیر هوش مصنوعی اهمیت دارد

[![مقدمه‌ای بر پروتکل زمینه مدل](../../../translated_images/01.a467036d886b5fb5b9cf7b39bac0e743b6ca0a4a18a492de90061daaf0cc55f0.fa.png)](https://youtu.be/agBbdiOPLQA)

_(برای مشاهده ویدئوی این درس روی تصویر بالا کلیک کنید)_

برنامه‌های هوش مصنوعی مولد یک گام بزرگ به جلو هستند، زیرا اغلب به کاربران اجازه می‌دهند با استفاده از دستورات زبان طبیعی با برنامه تعامل داشته باشند. با این حال، هرچه زمان و منابع بیشتری در این برنامه‌ها سرمایه‌گذاری شود، باید مطمئن شوید که می‌توانید قابلیت‌ها و منابع را به گونه‌ای ادغام کنید که گسترش آن آسان باشد، برنامه شما بتواند از بیش از یک مدل استفاده کند و پیچیدگی‌های مختلف مدل‌ها را مدیریت کند. به طور خلاصه، ساخت برنامه‌های هوش مصنوعی مولد در ابتدا آسان است، اما با رشد و پیچیده‌تر شدن آن‌ها، نیاز به تعریف یک معماری خواهید داشت و احتمالاً باید به یک استاندارد تکیه کنید تا اطمینان حاصل شود که برنامه‌هایتان به صورت یکپارچه ساخته می‌شوند. اینجاست که MCP وارد عمل می‌شود تا همه چیز را سازماندهی کرده و یک استاندارد ارائه دهد.

---

## **🔍 پروتکل زمینه مدل (MCP) چیست؟**

**پروتکل زمینه مدل (MCP)** یک **رابط باز و استاندارد شده** است که به مدل‌های زبانی بزرگ (LLM) اجازه می‌دهد به طور یکپارچه با ابزارها، APIها و منابع داده خارجی تعامل داشته باشند. این پروتکل یک معماری یکپارچه ارائه می‌دهد تا عملکرد مدل‌های هوش مصنوعی را فراتر از داده‌های آموزشی آن‌ها افزایش دهد و سیستم‌های هوش مصنوعی هوشمندتر، مقیاس‌پذیرتر و پاسخگوتر ایجاد کند.

---

## **🎯 چرا استانداردسازی در هوش مصنوعی اهمیت دارد**

با پیچیده‌تر شدن برنامه‌های هوش مصنوعی مولد، ضروری است که استانداردهایی را اتخاذ کنیم که **مقیاس‌پذیری، گسترش‌پذیری** و **نگهداری‌پذیری** را تضمین کنند. MCP این نیازها را با:

- یکپارچه‌سازی مدل‌ها و ابزارها  
- کاهش راه‌حل‌های سفارشی شکننده  
- امکان همزیستی چندین مدل در یک اکوسیستم  

برطرف می‌کند.

---

## **📚 اهداف آموزشی**

در پایان این مقاله، شما قادر خواهید بود:

- **پروتکل زمینه مدل (MCP)** و موارد استفاده آن را تعریف کنید  
- درک کنید که چگونه MCP ارتباط بین مدل و ابزار را استاندارد می‌کند  
- اجزای اصلی معماری MCP را شناسایی کنید  
- کاربردهای واقعی MCP را در زمینه‌های سازمانی و توسعه بررسی کنید  

---

## **💡 چرا پروتکل زمینه مدل (MCP) یک تحول‌ساز است**

### **🔗 MCP مشکل پراکندگی در تعاملات هوش مصنوعی را حل می‌کند**

پیش از MCP، ادغام مدل‌ها با ابزارها نیازمند:

- کدنویسی سفارشی برای هر جفت ابزار-مدل  
- APIهای غیر استاندارد برای هر فروشنده  
- خرابی‌های مکرر به دلیل به‌روزرسانی‌ها  
- مقیاس‌پذیری ضعیف با افزایش تعداد ابزارها  

بود.

### **✅ مزایای استانداردسازی MCP**

| **مزیت**                 | **توضیح**                                                                      |
|--------------------------|--------------------------------------------------------------------------------|
| قابلیت همکاری            | مدل‌های زبانی بزرگ به طور یکپارچه با ابزارهای فروشندگان مختلف کار می‌کنند      |
| یکپارچگی                 | رفتار یکنواخت در سراسر پلتفرم‌ها و ابزارها                                     |
| قابلیت استفاده مجدد      | ابزارهایی که یک بار ساخته می‌شوند، می‌توانند در پروژه‌ها و سیستم‌های مختلف استفاده شوند |
| توسعه سریع‌تر            | کاهش زمان توسعه با استفاده از رابط‌های استاندارد و آماده به کار              |

---

## **🧱 نمای کلی معماری سطح بالا MCP**

MCP از یک **مدل کلاینت-سرور** پیروی می‌کند، که در آن:

- **میزبان‌های MCP** مدل‌های هوش مصنوعی را اجرا می‌کنند  
- **کلاینت‌های MCP** درخواست‌ها را آغاز می‌کنند  
- **سرورهای MCP** زمینه، ابزارها و قابلیت‌ها را ارائه می‌دهند  

### **اجزای کلیدی:**

- **منابع** – داده‌های ایستا یا پویا برای مدل‌ها  
- **دستورات** – جریان‌های کاری از پیش تعریف‌شده برای تولید هدایت‌شده  
- **ابزارها** – توابع اجرایی مانند جستجو، محاسبات  
- **نمونه‌گیری** – رفتار عامل‌محور از طریق تعاملات بازگشتی  

---

## نحوه کار سرورهای MCP

سرورهای MCP به این صورت عمل می‌کنند:

- **جریان درخواست**:  
    1. کلاینت MCP یک درخواست به مدل هوش مصنوعی که در میزبان MCP اجرا می‌شود ارسال می‌کند.  
    2. مدل هوش مصنوعی تشخیص می‌دهد که چه زمانی به ابزارها یا داده‌های خارجی نیاز دارد.  
    3. مدل با استفاده از پروتکل استاندارد با سرور MCP ارتباط برقرار می‌کند.  

- **عملکرد سرور MCP**:  
    - **ثبت ابزارها**: فهرستی از ابزارهای موجود و قابلیت‌های آن‌ها را نگهداری می‌کند.  
    - **احراز هویت**: مجوزهای دسترسی به ابزارها را تأیید می‌کند.  
    - **مدیریت درخواست‌ها**: درخواست‌های ابزار ورودی از مدل را پردازش می‌کند.  
    - **فرمت‌بندی پاسخ‌ها**: خروجی ابزارها را در قالبی که مدل بتواند درک کند ساختاردهی می‌کند.  

- **اجرای ابزارها**:  
    - سرور درخواست‌ها را به ابزارهای خارجی مناسب هدایت می‌کند.  
    - ابزارها توابع تخصصی خود (مانند جستجو، محاسبات، پرس‌وجوهای پایگاه داده و غیره) را اجرا می‌کنند.  
    - نتایج در قالبی یکپارچه به مدل بازگردانده می‌شوند.  

- **تکمیل پاسخ**:  
    - مدل هوش مصنوعی خروجی ابزارها را در پاسخ خود ادغام می‌کند.  
    - پاسخ نهایی به برنامه کلاینت ارسال می‌شود.  

```mermaid
---
title: MCP Server Architecture and Component Interactions
description: A diagram showing how AI models interact with MCP servers and various tools, depicting the request flow and server components including Tool Registry, Authentication, Request Handler, and Response Formatter
---
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

## 👨‍💻 چگونه یک سرور MCP بسازیم (با مثال‌ها)

سرورهای MCP به شما امکان می‌دهند قابلیت‌های مدل‌های زبانی بزرگ را با ارائه داده‌ها و عملکردها گسترش دهید.

آماده امتحان کردن هستید؟ در اینجا مثال‌هایی از ایجاد یک سرور MCP ساده در زبان‌های مختلف آورده شده است:

- **مثال پایتون**: https://github.com/modelcontextprotocol/python-sdk  
- **مثال تایپ‌اسکریپت**: https://github.com/modelcontextprotocol/typescript-sdk  
- **مثال جاوا**: https://github.com/modelcontextprotocol/java-sdk  
- **مثال C#/.NET**: https://github.com/modelcontextprotocol/csharp-sdk  

---

## 🌍 موارد استفاده واقعی از MCP

MCP طیف گسترده‌ای از برنامه‌ها را با گسترش قابلیت‌های هوش مصنوعی امکان‌پذیر می‌کند:

| **برنامه**                 | **توضیح**                                                                      |
|----------------------------|--------------------------------------------------------------------------------|
| یکپارچه‌سازی داده‌های سازمانی | اتصال مدل‌های زبانی بزرگ به پایگاه‌های داده، CRMها یا ابزارهای داخلی            |
| سیستم‌های هوش مصنوعی عامل   | فعال‌سازی عوامل خودمختار با دسترسی به ابزارها و جریان‌های کاری تصمیم‌گیری       |
| برنامه‌های چندوجهی          | ترکیب ابزارهای متنی، تصویری و صوتی در یک برنامه هوش مصنوعی یکپارچه             |
| یکپارچه‌سازی داده‌های بلادرنگ | آوردن داده‌های زنده به تعاملات هوش مصنوعی برای خروجی‌های دقیق‌تر و به‌روزتر     |

---

### 🧠 MCP = استاندارد جهانی برای تعاملات هوش مصنوعی

پروتکل زمینه مدل (MCP) به عنوان یک استاندارد جهانی برای تعاملات هوش مصنوعی عمل می‌کند، درست مانند اینکه USB-C اتصالات فیزیکی دستگاه‌ها را استاندارد کرد. در دنیای هوش مصنوعی، MCP یک رابط یکپارچه ارائه می‌دهد که به مدل‌ها (کلاینت‌ها) اجازه می‌دهد به طور یکپارچه با ابزارها و ارائه‌دهندگان داده خارجی (سرورها) ادغام شوند. این امر نیاز به پروتکل‌های متنوع و سفارشی برای هر API یا منبع داده را از بین می‌برد.

در MCP، یک ابزار سازگار با MCP (که به آن سرور MCP گفته می‌شود) از یک استاندارد یکپارچه پیروی می‌کند. این سرورها می‌توانند ابزارها یا اقداماتی که ارائه می‌دهند را فهرست کنند و این اقدامات را در صورت درخواست یک عامل هوش مصنوعی اجرا کنند. پلتفرم‌های عامل هوش مصنوعی که از MCP پشتیبانی می‌کنند، قادر به کشف ابزارهای موجود از سرورها و فراخوانی آن‌ها از طریق این پروتکل استاندارد هستند.

---

### 💡 تسهیل دسترسی به دانش

علاوه بر ارائه ابزارها، MCP دسترسی به دانش را نیز تسهیل می‌کند. این پروتکل به برنامه‌ها اجازه می‌دهد زمینه را از طریق اتصال به منابع داده مختلف به مدل‌های زبانی بزرگ (LLM) ارائه دهند. برای مثال، یک سرور MCP ممکن است نماینده مخزن اسناد یک شرکت باشد و به عوامل اجازه دهد اطلاعات مرتبط را در صورت نیاز بازیابی کنند. سرور دیگری می‌تواند اقدامات خاصی مانند ارسال ایمیل یا به‌روزرسانی سوابق را مدیریت کند. از دیدگاه عامل، این‌ها صرفاً ابزارهایی هستند که می‌تواند استفاده کند—برخی ابزارها داده‌ها را بازمی‌گردانند (زمینه دانش)، در حالی که برخی دیگر اقدامات را انجام می‌دهند. MCP هر دو را به طور کارآمد مدیریت می‌کند.

---

### 👉 مثال: راه‌حل عامل مقیاس‌پذیر

```mermaid
---
title: Scalable Agent Solution with MCP
description: A diagram illustrating how a user interacts with an LLM that connects to multiple MCP servers, with each server providing both knowledge and tools, creating a scalable AI system architecture
---
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

---

### 🔄 سناریوهای پیشرفته MCP با ادغام مدل‌های زبانی در سمت کلاینت

فراتر از معماری پایه MCP، سناریوهای پیشرفته‌ای وجود دارد که در آن هم کلاینت و هم سرور شامل مدل‌های زبانی هستند و تعاملات پیچیده‌تری را امکان‌پذیر می‌کنند:

```mermaid
---
title: Advanced MCP Scenarios with Client-Server LLM Integration
description: A sequence diagram showing the detailed interaction flow between user, client application, client LLM, multiple MCP servers, and server LLM, illustrating tool discovery, user interaction, direct tool calling, and feature negotiation phases
---
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

---

## 🔐 مزایای عملی MCP

در اینجا مزایای عملی استفاده از MCP آورده شده است:

- **به‌روز بودن**: مدل‌ها می‌توانند به اطلاعات به‌روز فراتر از داده‌های آموزشی خود دسترسی داشته باشند  
- **گسترش قابلیت‌ها**: مدل‌ها می‌توانند از ابزارهای تخصصی برای وظایفی که برای آن‌ها آموزش ندیده‌اند استفاده کنند  
- **کاهش توهمات**: منابع داده خارجی زمینه واقعی ارائه می‌دهند  
- **حریم خصوصی**: داده‌های حساس می‌توانند در محیط‌های امن باقی بمانند و در دستورات جاسازی نشوند  

---

## 📌 نکات کلیدی

نکات کلیدی استفاده از MCP عبارتند از:

- **MCP** نحوه تعامل مدل‌های هوش مصنوعی با ابزارها و داده‌ها را استاندارد می‌کند  
- **گسترش‌پذیری، یکپارچگی و قابلیت همکاری** را ترویج می‌دهد  
- MCP به **کاهش زمان توسعه، بهبود قابلیت اطمینان و گسترش قابلیت‌های مدل** کمک می‌کند  
- معماری کلاینت-سرور **برنامه‌های هوش مصنوعی انعطاف‌پذیر و گسترش‌پذیر** را امکان‌پذیر می‌کند  

---

## 🧠 تمرین

به برنامه هوش مصنوعی که به ساخت آن علاقه دارید فکر کنید.

- کدام **ابزارها یا داده‌های خارجی** می‌توانند قابلیت‌های آن را افزایش دهند؟  
- MCP چگونه می‌تواند ادغام را **ساده‌تر و قابل اطمینان‌تر** کند؟  

---

## منابع اضافی

- [مخزن GitHub MCP](https://github.com/modelcontextprotocol)

---

## مرحله بعدی

بعدی: [فصل ۱: مفاهیم اصلی](../01-CoreConcepts/README.md)  

**سلب مسئولیت**:  
این سند با استفاده از سرویس ترجمه هوش مصنوعی [Co-op Translator](https://github.com/Azure/co-op-translator) ترجمه شده است. در حالی که ما تلاش می‌کنیم دقت را حفظ کنیم، لطفاً توجه داشته باشید که ترجمه‌های خودکار ممکن است حاوی خطاها یا نادرستی‌هایی باشند. سند اصلی به زبان اصلی آن باید به عنوان منبع معتبر در نظر گرفته شود. برای اطلاعات حساس، ترجمه حرفه‌ای انسانی توصیه می‌شود. ما هیچ مسئولیتی در قبال سوءتفاهم‌ها یا تفسیرهای نادرست ناشی از استفاده از این ترجمه نداریم.