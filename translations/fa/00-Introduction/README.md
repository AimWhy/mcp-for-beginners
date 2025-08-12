<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "85eb103a78a43a542f2890a3d7d62318",
  "translation_date": "2025-08-11T11:27:39+00:00",
  "source_file": "00-Introduction/README.md",
  "language_code": "fa"
}
-->
# معرفی پروتکل زمینه مدل (MCP): چرا برای برنامه‌های مقیاس‌پذیر هوش مصنوعی اهمیت دارد

[![معرفی پروتکل زمینه مدل](../../../translated_images/01.a467036d886b5fb5b9cf7b39bac0e743b6ca0a4a18a492de90061daaf0cc55f0.fa.png)](https://youtu.be/agBbdiOPLQA)

_(برای مشاهده ویدئوی این درس روی تصویر بالا کلیک کنید)_

برنامه‌های هوش مصنوعی مولد گامی بزرگ به جلو هستند، زیرا اغلب به کاربران اجازه می‌دهند با استفاده از دستورات زبان طبیعی با برنامه تعامل کنند. با این حال، با سرمایه‌گذاری بیشتر زمان و منابع در چنین برنامه‌هایی، باید مطمئن شوید که می‌توانید به راحتی قابلیت‌ها و منابع را به گونه‌ای ادغام کنید که توسعه آن آسان باشد، برنامه شما بتواند از بیش از یک مدل استفاده کند و پیچیدگی‌های مختلف مدل‌ها را مدیریت کند. به طور خلاصه، ساخت برنامه‌های هوش مصنوعی مولد در ابتدا آسان است، اما با رشد و پیچیده‌تر شدن آن‌ها، نیاز به تعریف معماری پیدا می‌کنید و احتمالاً باید به یک استاندارد تکیه کنید تا مطمئن شوید برنامه‌هایتان به صورت یکپارچه ساخته شده‌اند. اینجاست که MCP وارد عمل می‌شود تا همه چیز را سازماندهی کند و یک استاندارد ارائه دهد.

---

## **🔍 پروتکل زمینه مدل (MCP) چیست؟**

**پروتکل زمینه مدل (MCP)** یک **رابط استاندارد و باز** است که به مدل‌های زبان بزرگ (LLM) اجازه می‌دهد به طور یکپارچه با ابزارها، APIها و منابع داده خارجی تعامل کنند. این پروتکل معماری ثابتی ارائه می‌دهد که عملکرد مدل‌های هوش مصنوعی را فراتر از داده‌های آموزشی آن‌ها افزایش می‌دهد و سیستم‌های هوش مصنوعی هوشمندتر، مقیاس‌پذیرتر و پاسخگوتر ایجاد می‌کند.

---

## **🎯 چرا استانداردسازی در هوش مصنوعی اهمیت دارد**

با پیچیده‌تر شدن برنامه‌های هوش مصنوعی مولد، ضروری است که استانداردهایی اتخاذ شوند که **مقیاس‌پذیری، توسعه‌پذیری، نگهداری‌پذیری** و **اجتناب از وابستگی به یک فروشنده خاص** را تضمین کنند. MCP این نیازها را با:

- یکپارچه‌سازی مدل‌ها و ابزارها  
- کاهش راه‌حل‌های سفارشی شکننده  
- امکان همزیستی چندین مدل از فروشندگان مختلف در یک اکوسیستم  

**توجه:** اگرچه MCP خود را به عنوان یک استاندارد باز معرفی می‌کند، هیچ برنامه‌ای برای استانداردسازی MCP از طریق نهادهای استاندارد موجود مانند IEEE، IETF، W3C، ISO یا سایر نهادهای استاندارد وجود ندارد.

---

## **📚 اهداف آموزشی**

تا پایان این مقاله، شما قادر خواهید بود:

- **پروتکل زمینه مدل (MCP)** و موارد استفاده آن را تعریف کنید  
- درک کنید که چگونه MCP ارتباط بین مدل‌ها و ابزارها را استاندارد می‌کند  
- اجزای اصلی معماری MCP را شناسایی کنید  
- کاربردهای واقعی MCP در زمینه‌های سازمانی و توسعه را بررسی کنید  

---

## **💡 چرا پروتکل زمینه مدل (MCP) یک تغییر بزرگ است**

### **🔗 MCP مشکل پراکندگی در تعاملات هوش مصنوعی را حل می‌کند**

پیش از MCP، ادغام مدل‌ها با ابزارها نیازمند:

- کدنویسی سفارشی برای هر جفت ابزار-مدل  
- APIهای غیر استاندارد برای هر فروشنده  
- شکست‌های مکرر به دلیل به‌روزرسانی‌ها  
- مقیاس‌پذیری ضعیف با افزایش تعداد ابزارها  

### **✅ مزایای استانداردسازی MCP**

| **مزیت**                  | **توضیحات**                                                                  |
|--------------------------|------------------------------------------------------------------------------|
| قابلیت همکاری            | مدل‌های زبان بزرگ به طور یکپارچه با ابزارهای فروشندگان مختلف کار می‌کنند     |
| ثبات                     | رفتار یکنواخت در پلتفرم‌ها و ابزارها                                         |
| قابلیت استفاده مجدد      | ابزارهایی که یک بار ساخته شده‌اند می‌توانند در پروژه‌ها و سیستم‌های مختلف استفاده شوند |
| توسعه سریع‌تر            | کاهش زمان توسعه با استفاده از رابط‌های استاندارد و آماده استفاده            |

---

## **🧱 نمای کلی معماری MCP در سطح بالا**

MCP از یک **مدل کلاینت-سرور** پیروی می‌کند، که در آن:

- **میزبان‌های MCP** مدل‌های هوش مصنوعی را اجرا می‌کنند  
- **کلاینت‌های MCP** درخواست‌ها را آغاز می‌کنند  
- **سرورهای MCP** زمینه، ابزارها و قابلیت‌ها را ارائه می‌دهند  

### **اجزای کلیدی:**

- **منابع** – داده‌های ثابت یا پویا برای مدل‌ها  
- **دستورات** – جریان‌های کاری از پیش تعریف‌شده برای تولید هدایت‌شده  
- **ابزارها** – توابع اجرایی مانند جستجو، محاسبات  
- **نمونه‌گیری** – رفتار عاملانه از طریق تعاملات بازگشتی  

---

## نحوه عملکرد سرورهای MCP

سرورهای MCP به این صورت عمل می‌کنند:

- **جریان درخواست**:
    1. یک درخواست توسط کاربر نهایی یا نرم‌افزاری که به نمایندگی از او عمل می‌کند آغاز می‌شود.  
    2. **کلاینت MCP** درخواست را به **میزبان MCP** ارسال می‌کند، که زمان اجرای مدل هوش مصنوعی را مدیریت می‌کند.  
    3. **مدل هوش مصنوعی** درخواست کاربر را دریافت می‌کند و ممکن است برای دسترسی به ابزارها یا داده‌های خارجی از طریق یک یا چند فراخوان ابزار درخواست کند.  
    4. **میزبان MCP**، نه خود مدل، با **سرورهای MCP** مناسب از طریق پروتکل استاندارد ارتباط برقرار می‌کند.  
- **عملکرد میزبان MCP**:
    - **ثبت ابزار**: یک کاتالوگ از ابزارهای موجود و قابلیت‌های آن‌ها را نگهداری می‌کند.  
    - **احراز هویت**: مجوزهای دسترسی به ابزارها را تأیید می‌کند.  
    - **مدیریت درخواست**: درخواست‌های ابزار ورودی از مدل را پردازش می‌کند.  
    - **فرمت‌دهی پاسخ**: خروجی ابزارها را در قالبی که مدل بتواند درک کند ساختاردهی می‌کند.  
- **اجرای سرور MCP**:
    - **میزبان MCP** فراخوان‌های ابزار را به یک یا چند **سرور MCP** هدایت می‌کند، که هر کدام توابع تخصصی (مانند جستجو، محاسبات، پرس‌وجوهای پایگاه داده) را ارائه می‌دهند.  
    - **سرورهای MCP** عملیات مربوطه را انجام داده و نتایج را به **میزبان MCP** در قالبی ثابت بازمی‌گردانند.  
    - **میزبان MCP** این نتایج را فرمت‌دهی کرده و به **مدل هوش مصنوعی** منتقل می‌کند.  
- **تکمیل پاسخ**:
    - **مدل هوش مصنوعی** خروجی ابزارها را در یک پاسخ نهایی ادغام می‌کند.  
    - **میزبان MCP** این پاسخ را به **کلاینت MCP** ارسال می‌کند، که آن را به کاربر نهایی یا نرم‌افزار فراخواننده تحویل می‌دهد.  

```mermaid
---
title: MCP Architecture and Component Interactions
description: A diagram showing the flows of the components in MCP.
---
graph TD
    Client[MCP Client/Application] -->|Sends Request| H[MCP Host]
    H -->|Invokes| A[AI Model]
    A -->|Tool Call Request| H
    H -->|MCP Protocol| T1[MCP Server Tool 01: Web Search]
    H -->|MCP Protocol| T2[MCP Server Tool 02: Calculator tool]
    H -->|MCP Protocol| T3[MCP Server Tool 03: Database Access tool]
    H -->|MCP Protocol| T4[MCP Server Tool 04: File System tool]
    H -->|Sends Response| Client

    subgraph "MCP Host Components"
        H
        G[Tool Registry]
        I[Authentication]
        J[Request Handler]
        K[Response Formatter]
    end

    H <--> G
    H <--> I
    H <--> J
    H <--> K

    style A fill:#f9d5e5,stroke:#333,stroke-width:2px
    style H fill:#eeeeee,stroke:#333,stroke-width:2px
    style Client fill:#d5e8f9,stroke:#333,stroke-width:2px
    style G fill:#fffbe6,stroke:#333,stroke-width:1px
    style I fill:#fffbe6,stroke:#333,stroke-width:1px
    style J fill:#fffbe6,stroke:#333,stroke-width:1px
    style K fill:#fffbe6,stroke:#333,stroke-width:1px
    style T1 fill:#c2f0c2,stroke:#333,stroke-width:1px
    style T2 fill:#c2f0c2,stroke:#333,stroke-width:1px
    style T3 fill:#c2f0c2,stroke:#333,stroke-width:1px
    style T4 fill:#c2f0c2,stroke:#333,stroke-width:1px
```

## 👨‍💻 چگونه یک سرور MCP بسازیم (با مثال‌ها)

سرورهای MCP به شما امکان می‌دهند قابلیت‌های مدل‌های زبان بزرگ را با ارائه داده و عملکرد گسترش دهید.

آماده امتحان کردن هستید؟ در اینجا SDKهای زبان و/یا پشته خاص با مثال‌هایی از ایجاد سرورهای MCP ساده در زبان‌ها/پشته‌های مختلف آورده شده است:

- **Python SDK**: https://github.com/modelcontextprotocol/python-sdk  

- **TypeScript SDK**: https://github.com/modelcontextprotocol/typescript-sdk  

- **Java SDK**: https://github.com/modelcontextprotocol/java-sdk  

- **C#/.NET SDK**: https://github.com/modelcontextprotocol/csharp-sdk  

---

## 🌍 موارد استفاده واقعی از MCP

MCP طیف گسترده‌ای از برنامه‌ها را با گسترش قابلیت‌های هوش مصنوعی امکان‌پذیر می‌کند:

| **برنامه**                 | **توضیحات**                                                                  |
|----------------------------|------------------------------------------------------------------------------|
| یکپارچه‌سازی داده‌های سازمانی | اتصال مدل‌های زبان بزرگ به پایگاه‌های داده، CRMها یا ابزارهای داخلی           |
| سیستم‌های هوش مصنوعی عاملانه | فعال‌سازی عوامل خودمختار با دسترسی به ابزارها و جریان‌های کاری تصمیم‌گیری     |
| برنامه‌های چندوجهی          | ترکیب ابزارهای متن، تصویر و صوت در یک برنامه هوش مصنوعی یکپارچه              |
| یکپارچه‌سازی داده‌های بلادرنگ | آوردن داده‌های زنده به تعاملات هوش مصنوعی برای خروجی‌های دقیق‌تر و به‌روزتر   |

---

### 🧠 MCP = استاندارد جهانی برای تعاملات هوش مصنوعی

پروتکل زمینه مدل (MCP) به عنوان یک استاندارد جهانی برای تعاملات هوش مصنوعی عمل می‌کند، مشابه نحوه استانداردسازی USB-C برای اتصال فیزیکی دستگاه‌ها. در دنیای هوش مصنوعی، MCP یک رابط ثابت ارائه می‌دهد که به مدل‌ها (کلاینت‌ها) اجازه می‌دهد به طور یکپارچه با ابزارها و ارائه‌دهندگان داده خارجی (سرورها) ادغام شوند. این امر نیاز به پروتکل‌های متنوع و سفارشی برای هر API یا منبع داده را از بین می‌برد.

در MCP، یک ابزار سازگار با MCP (که به عنوان سرور MCP شناخته می‌شود) از یک استاندارد یکپارچه پیروی می‌کند. این سرورها می‌توانند ابزارها یا اقداماتی که ارائه می‌دهند را فهرست کنند و این اقدامات را هنگام درخواست یک عامل هوش مصنوعی اجرا کنند. پلتفرم‌های عامل هوش مصنوعی که از MCP پشتیبانی می‌کنند قادر به کشف ابزارهای موجود از سرورها و فراخوانی آن‌ها از طریق این پروتکل استاندارد هستند.

---

### 💡 تسهیل دسترسی به دانش

فراتر از ارائه ابزارها، MCP دسترسی به دانش را نیز تسهیل می‌کند. این پروتکل به برنامه‌ها امکان می‌دهد زمینه را به مدل‌های زبان بزرگ (LLM) ارائه دهند، با اتصال آن‌ها به منابع داده مختلف. به عنوان مثال، یک سرور MCP ممکن است نماینده مخزن اسناد یک شرکت باشد و به عوامل اجازه دهد اطلاعات مرتبط را در صورت نیاز بازیابی کنند. سرور دیگری می‌تواند اقدامات خاصی مانند ارسال ایمیل یا به‌روزرسانی سوابق را مدیریت کند. از دیدگاه عامل، این‌ها صرفاً ابزارهایی هستند که می‌تواند استفاده کند—برخی ابزارها داده‌ها (زمینه دانش) را بازمی‌گردانند، در حالی که برخی دیگر اقدامات را انجام می‌دهند. MCP هر دو را به طور مؤثر مدیریت می‌کند.

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

### 🔄 سناریوهای پیشرفته MCP با ادغام LLM در سمت کلاینت

فراتر از معماری پایه MCP، سناریوهای پیشرفته‌ای وجود دارند که در آن‌ها هم کلاینت و هم سرور شامل مدل‌های زبان بزرگ هستند و تعاملات پیچیده‌تری را امکان‌پذیر می‌کنند. در نمودار زیر، **برنامه کلاینت** می‌تواند یک IDE باشد که تعدادی ابزار MCP برای استفاده توسط مدل زبان بزرگ در دسترس دارد:

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

- **تازگی**: مدل‌ها می‌توانند به اطلاعات به‌روز فراتر از داده‌های آموزشی خود دسترسی پیدا کنند  
- **گسترش قابلیت‌ها**: مدل‌ها می‌توانند از ابزارهای تخصصی برای وظایفی که برای آن‌ها آموزش ندیده‌اند استفاده کنند  
- **کاهش توهمات**: منابع داده خارجی زمینه واقعی ارائه می‌دهند  
- **حریم خصوصی**: داده‌های حساس می‌توانند در محیط‌های امن باقی بمانند و به جای جاسازی در دستورات استفاده شوند  

---

## 📌 نکات کلیدی

نکات کلیدی استفاده از MCP عبارتند از:

- **MCP** نحوه تعامل مدل‌های هوش مصنوعی با ابزارها و داده‌ها را استاندارد می‌کند  
- **توسعه‌پذیری، ثبات و قابلیت همکاری** را ترویج می‌دهد  
- MCP به **کاهش زمان توسعه، بهبود قابلیت اطمینان و گسترش قابلیت‌های مدل** کمک می‌کند  
- معماری کلاینت-سرور **برنامه‌های هوش مصنوعی انعطاف‌پذیر و توسعه‌پذیر** را امکان‌پذیر می‌کند  

---

## 🧠 تمرین

به یک برنامه هوش مصنوعی که به ساخت آن علاقه دارید فکر کنید.

- کدام **ابزارها یا داده‌های خارجی** می‌توانند قابلیت‌های آن را افزایش دهند؟  
- MCP چگونه می‌تواند ادغام را **ساده‌تر و قابل اعتمادتر** کند؟  

---

## منابع اضافی

- [مخزن GitHub MCP](https://github.com/modelcontextprotocol)

---

## مرحله بعدی

بعدی: [فصل ۱: مفاهیم اصلی](../01-CoreConcepts/README.md)

**سلب مسئولیت**:  
این سند با استفاده از سرویس ترجمه هوش مصنوعی [Co-op Translator](https://github.com/Azure/co-op-translator) ترجمه شده است. در حالی که ما تلاش می‌کنیم دقت را حفظ کنیم، لطفاً توجه داشته باشید که ترجمه‌های خودکار ممکن است شامل خطاها یا نادرستی‌ها باشند. سند اصلی به زبان اصلی آن باید به عنوان منبع معتبر در نظر گرفته شود. برای اطلاعات حساس، توصیه می‌شود از ترجمه حرفه‌ای انسانی استفاده کنید. ما مسئولیتی در قبال سوء تفاهم‌ها یا تفسیرهای نادرست ناشی از استفاده از این ترجمه نداریم.