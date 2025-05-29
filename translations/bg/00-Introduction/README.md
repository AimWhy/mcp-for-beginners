<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "1446979020432f512c883848d7eca144",
  "translation_date": "2025-05-29T21:54:29+00:00",
  "source_file": "00-Introduction/README.md",
  "language_code": "bg"
}
-->
# Въведение в Model Context Protocol (MCP): Защо е важен за мащабируеми AI приложения

Генеративните AI приложения са голяма крачка напред, тъй като често позволяват на потребителя да взаимодейства с приложението чрез естествени езикови команди. Въпреки това, с нарастването на времето и ресурсите, инвестирани в такива приложения, искате да сте сигурни, че можете лесно да интегрирате функционалности и ресурси по начин, който позволява лесно разширяване, поддържа използването на повече от един модел и управлява различни специфики на моделите. Накратко, създаването на Gen AI приложения е лесно в началото, но с тяхното разрастване и усложняване, трябва да започнете да дефинирате архитектура и вероятно ще се нуждаете от стандарт, който да гарантира, че приложенията ви са изградени по последователен начин. Тук влиза MCP, който организира нещата и предоставя стандарт.

---

## **🔍 Какво е Model Context Protocol (MCP)?**

**Model Context Protocol (MCP)** е **отворен, стандартизиран интерфейс**, който позволява на големи езикови модели (LLMs) да взаимодействат безпроблемно с външни инструменти, API-та и източници на данни. Той осигурява последователна архитектура за подобряване на функционалността на AI моделите извън техните тренировъчни данни, позволявайки по-умни, мащабируеми и по-отзивчиви AI системи.

---

## **🎯 Защо стандартите в AI са важни**

С нарастването на сложността на генеративните AI приложения е важно да се приемат стандарти, които осигуряват **мащабируемост, разширяемост** и **поддържане**. MCP отговаря на тези нужди чрез:

- Унифициране на интеграциите между модел и инструменти
- Намаляване на крехки, еднократни персонализирани решения
- Позволяване на множество модели да съжителстват в една екосистема

---

## **📚 Учебни цели**

В края на тази статия ще можете да:

- Определите **Model Context Protocol (MCP)** и неговите случаи на употреба
- Разберете как MCP стандартизира комуникацията между модел и инструмент
- Идентифицирате основните компоненти на архитектурата на MCP
- Изследвате реални приложения на MCP в корпоративен и развоен контекст

---

## **💡 Защо Model Context Protocol (MCP) е революционен**

### **🔗 MCP решава проблема с фрагментацията в AI взаимодействията**

Преди MCP, интегрирането на модели с инструменти изискваше:

- Персонализиран код за всяка двойка инструмент-модел
- Нестандартизирани API-та за всеки доставчик
- Чести прекъсвания заради ъпдейти
- Лоша мащабируемост с увеличаване на броя инструменти

### **✅ Предимства на стандартизацията с MCP**

| **Предимство**            | **Описание**                                                                  |
|--------------------------|-------------------------------------------------------------------------------|
| Съвместимост             | LLM работят безпроблемно с инструменти от различни доставчици                |
| Последователност         | Еднообразно поведение на различни платформи и инструменти                     |
| Преизползваемост         | Инструментите, изградени веднъж, могат да се използват в различни проекти     |
| Ускорено разработване    | Намаляване на времето за разработка чрез стандартизирани, plug-and-play интерфейси |

---

## **🧱 Преглед на високо ниво на архитектурата на MCP**

MCP следва **клиент-сървър модел**, при който:

- **MCP Hosts** изпълняват AI моделите
- **MCP Clients** инициират заявки
- **MCP Servers** предоставят контекст, инструменти и възможности

### **Основни компоненти:**

- **Resources** – Статични или динамични данни за моделите  
- **Prompts** – Предварително дефинирани работни потоци за насочено генериране  
- **Tools** – Изпълними функции като търсене, изчисления  
- **Sampling** – Агентско поведение чрез рекурсивни взаимодействия

---

## Как работят MCP сървърите

MCP сървърите функционират по следния начин:

- **Поток на заявките**:  
    1. MCP Client изпраща заявка към AI модела, който работи в MCP Host.  
    2. AI моделът разпознава кога има нужда от външни инструменти или данни.  
    3. Моделът комуникира с MCP Server, използвайки стандартизирания протокол.

- **Функционалности на MCP Server**:  
    - Регистър на инструментите: Поддържа каталог на наличните инструменти и техните възможности.  
    - Аутентикация: Проверява разрешенията за достъп до инструментите.  
    - Обработчик на заявки: Обработва входящите заявки за инструменти от модела.  
    - Форматиране на отговори: Структурира изхода от инструментите във формат, който моделът разбира.

- **Изпълнение на инструментите**:  
    - Сървърът насочва заявките към подходящите външни инструменти  
    - Инструментите изпълняват специализираните си функции (търсене, изчисления, заявки към бази данни и др.)  
    - Резултатите се връщат на модела в последователен формат.

- **Завършване на отговора**:  
    - AI моделът включва изхода от инструментите в своя отговор.  
    - Крайният отговор се изпраща обратно към клиентското приложение.

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

## 👨‍💻 Как да изградите MCP сървър (с примери)

MCP сървърите ви позволяват да разширите възможностите на LLM, като предоставят данни и функционалности.

Готови ли сте да опитате? Ето примери за създаване на прост MCP сървър на различни езици:

- **Python пример**: https://github.com/modelcontextprotocol/python-sdk

- **TypeScript пример**: https://github.com/modelcontextprotocol/typescript-sdk

- **Java пример**: https://github.com/modelcontextprotocol/java-sdk

- **C#/.NET пример**: https://github.com/modelcontextprotocol/csharp-sdk


## 🌍 Реални случаи на употреба на MCP

MCP позволява широк спектър от приложения чрез разширяване на възможностите на AI:

| **Приложение**             | **Описание**                                                                   |
|----------------------------|--------------------------------------------------------------------------------|
| Интеграция на корпоративни данни | Свързване на LLM с бази данни, CRM системи или вътрешни инструменти          |
| Агентни AI системи          | Позволява автономни агенти с достъп до инструменти и работни потоци за вземане на решения |
| Мултимодални приложения     | Комбиниране на текстови, визуални и аудио инструменти в едно унифицирано AI приложение |
| Интеграция на данни в реално време | Внасяне на актуални данни в AI взаимодействия за по-точни и актуални резултати |

### 🧠 MCP = Универсален стандарт за AI взаимодействия

Model Context Protocol (MCP) действа като универсален стандарт за AI взаимодействия, подобно на това как USB-C стандартизира физическите връзки за устройства. В света на AI MCP осигурява последователен интерфейс, позволяващ на моделите (клиентите) да се интегрират безпроблемно с външни инструменти и доставчици на данни (сървъри). Това елиминира нуждата от разнообразни, персонализирани протоколи за всяко API или източник на данни.

Под MCP, инструмент, съвместим с MCP (наричан MCP сървър), следва единен стандарт. Тези сървъри могат да изброяват предлаганите от тях инструменти или действия и да ги изпълняват при поискване от AI агент. Платформите за AI агенти, които поддържат MCP, могат да откриват наличните инструменти от сървърите и да ги извикват чрез този стандартен протокол.

### 💡 Улеснява достъпа до знание

Освен че предлага инструменти, MCP улеснява и достъпа до знания. Той позволява на приложенията да предоставят контекст на големи езикови модели (LLMs), като ги свързва с различни източници на данни. Например, MCP сървър може да представлява фирмен архив с документи, позволявайки на агентите да извличат релевантна информация при поискване. Друг сървър може да обработва специфични действия като изпращане на имейли или обновяване на записи. От гледна точка на агента, това са просто инструменти, които може да използва — някои инструменти връщат данни (контекст на знание), а други изпълняват действия. MCP управлява ефективно и двата типа.

Агент, който се свързва с MCP сървър, автоматично научава наличните възможности и достъпните данни на сървъра чрез стандартизиран формат. Тази стандартизация позволява динамично добавяне на инструменти. Например, добавянето на нов MCP сървър в системата на агента прави неговите функции веднага достъпни без нужда от допълнителна персонализация на инструкциите за агента.

Тази опростена интеграция съответства на потока, изобразен в мермейд диаграмата, където сървърите предоставят както инструменти, така и знания, осигурявайки безпроблемно сътрудничество между системите.

### 👉 Пример: Мащабируемо агентно решение

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

### 🔄 Разширени MCP сценарии с интеграция на LLM на клиентската страна

Освен базовата архитектура на MCP, съществуват и по-сложни сценарии, при които както клиентът, така и сървърът съдържат LLM, позволявайки по-усъвършенствани взаимодействия:

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

## 🔐 Практически ползи от MCP

Ето практическите ползи от използването на MCP:

- **Актуалност**: Моделите могат да достъпват най-новата информация извън тренировъчните си данни  
- **Разширяване на възможностите**: Моделите могат да използват специализирани инструменти за задачи, за които не са били обучени  
- **Намаляване на халюцинациите**: Външните източници на данни осигуряват фактологична основа  
- **Поверителност**: Чувствителните данни могат да останат в защитени среди, вместо да се вграждат в подсказките

## 📌 Основни изводи

Ето основните изводи при използването на MCP:

- **MCP** стандартизира начина, по който AI моделите взаимодействат с инструменти и данни  
- Насърчава **разширяемост, последователност и съвместимост**  
- MCP помага да се **намали времето за разработка, подобри надеждността и разшири възможностите на моделите**  
- Клиент-сървър архитектурата **позволява гъвкави, разширяеми AI приложения**

## 🧠 Упражнение

Помислете за AI приложение, което искате да създадете.

- Кои **външни инструменти или данни** биха подобрили възможностите му?  
- Как MCP би направил интеграцията **по-проста и по-надеждна?**

## Допълнителни ресурси

- [MCP GitHub Repository](https://github.com/modelcontextprotocol)


## Какво следва

Следва: [Глава 1: Основни концепции](/01-CoreConcepts/README.md)

**Отказ от отговорност**:  
Този документ е преведен с помощта на AI преводаческа услуга [Co-op Translator](https://github.com/Azure/co-op-translator). Въпреки че се стремим към точност, моля, имайте предвид, че автоматизираните преводи могат да съдържат грешки или неточности. Оригиналният документ на неговия език трябва да се счита за авторитетен източник. За критична информация се препоръчва професионален човешки превод. Ние не носим отговорност за каквито и да е недоразумения или неправилни тълкувания, произтичащи от използването на този превод.