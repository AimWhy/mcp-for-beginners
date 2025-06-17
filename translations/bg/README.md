<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "9a14017adf28f7440f20c2d5e7f1d0f8",
  "translation_date": "2025-06-17T16:12:35+00:00",
  "source_file": "README.md",
  "language_code": "bg"
}
-->
![MCP-за-начинаещи](../../translated_images/mcp-beginners.2ce2b317996369ff66c5b72e25eff9d4288ab2741fc70c0b4e523d1ae1e249fd.bg.png) 

[![GitHub contributors](https://img.shields.io/github/contributors/microsoft/mcp-for-beginners.svg)](https://GitHub.com/microsoft/mcp-for-beginners/graphs/contributors)
[![GitHub issues](https://img.shields.io/github/issues/microsoft/mcp-for-beginners.svg)](https://GitHub.com/microsoft/mcp-for-beginners/issues)
[![GitHub pull-requests](https://img.shields.io/github/issues-pr/microsoft/mcp-for-beginners.svg)](https://GitHub.com/microsoft/mcp-for-beginners/pulls)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)

[![GitHub watchers](https://img.shields.io/github/watchers/microsoft/mcp-for-beginners.svg?style=social&label=Watch)](https://GitHub.com/microsoft/mcp-for-beginners/watchers)
[![GitHub forks](https://img.shields.io/github/forks/microsoft/mcp-for-beginners.svg?style=social&label=Fork)](https://GitHub.com/microsoft/mcp-for-beginners/fork)
[![GitHub stars](https://img.shields.io/github/stars/microsoft/mcp-for-beginners?style=social&label=Star)](https://GitHub.com/microsoft/mcp-for-beginners/stargazers)


[![Microsoft Azure AI Foundry Discord](https://dcbadge.vercel.app/api/server/ByRwuEEgH4)](https://discord.com/invite/ByRwuEEgH4)


Следвайте тези стъпки, за да започнете да използвате тези ресурси:
1. **Направете Fork на хранилището**: Натиснете [![GitHub forks](https://img.shields.io/github/forks/microsoft/mcp-for-beginners.svg?style=social&label=Fork)](https://GitHub.com/microsoft/mcp-for-beginners/fork)
2. **Клонирайте хранилището**:   `git clone https://github.com/microsoft/mcp-for-beginners.git`
3. [**Присъединете се към Azure AI Foundry Discord и се запознайте с експерти и други разработчици**](https://discord.com/invite/ByRwuEEgH4)


### 🌐 Поддръжка на няколко езика

#### Поддържа се чрез GitHub Action (Автоматично и винаги актуално)

# 🚀 Учебна програма за Model Context Protocol (MCP) за начинаещи

## **Научете MCP с практически примери на C#, Java, JavaScript, Python и TypeScript**

## 🧠 Преглед на учебната програма за Model Context Protocol

**Model Context Protocol (MCP)** е модерна рамка, създадена да стандартизира взаимодействията между AI модели и клиентски приложения. Тази отворена учебна програма предлага структурирано обучение с практически кодови примери и реални приложения на популярни програмни езици като C#, Java, JavaScript, TypeScript и Python.

Независимо дали сте AI разработчик, системен архитект или софтуерен инженер, това ръководство е вашият изчерпателен ресурс за овладяване на основите и стратегиите за внедряване на MCP.

## 🔗 Официални ресурси за MCP

- 📘 [MCP Documentation](https://modelcontextprotocol.io/) – Подробни уроци и потребителски ръководства  
- 📜 [MCP Specification](https://spec.modelcontextprotocol.io/) – Архитектура на протокола и технически справки  
- 🧑‍💻 [MCP GitHub Repository](https://github.com/modelcontextprotocol) – Отворен код на SDK-та, инструменти и кодови примери  

## 🧭 Пълна структура на учебната програма MCP

| Гл | Заглавие | Описание | Връзка |
|--|--|--|--|
| 00 | **Въведение в MCP** | Преглед на Model Context Protocol и значението му в AI процесите, включително какво представлява MCP, защо е важна стандартизацията и практически приложения и ползи | [Въведение](./00-Introduction/README.md) |
| 01 | **Обяснение на основните концепции** | Подробно разглеждане на основните концепции на MCP, включително клиент-сървър архитектура, ключови компоненти на протокола и модели на съобщения | [Основни концепции](./01-CoreConcepts/README.md) |
| 02 | **Сигурност в MCP** | Идентифициране на заплахи за сигурността в MCP-базирани системи, техники и най-добри практики за защитено внедряване | [Сигурност](./02-Security/README.md) |
| 03 | **Започване с MCP** | Настройка и конфигуриране на среда, създаване на базови MCP сървъри и клиенти, интеграция на MCP с вече съществуващи приложения | [Започване](./03-GettingStarted/README.md) |
| 3.1 | **Първи сървър** | Настройка на базов сървър с MCP протокола, разбиране на взаимодействието сървър-клиент и тестване на сървъра | [Първи сървър](./03-GettingStarted/01-first-server/README.md) |
| 3.2 | **Първи клиент** | Настройка на базов клиент с MCP протокола, разбиране на взаимодействието клиент-сървър и тестване на клиента | [Първи клиент](./03-GettingStarted/02-client/README.md) |
| 3.3 | **Клиент с LLM** | Настройка на клиент с MCP протокола, използващ Large Language Model (LLM) | [Клиент с LLM](./03-GettingStarted/03-llm-client/README.md) |
| 3.4 | **Използване на сървър с Visual Studio Code** | Настройка на Visual Studio Code за работа със сървъри чрез MCP протокола | [Използване на сървър с Visual Studio Code](./03-GettingStarted/04-vscode/README.md) |
| 3.5 | **Създаване на сървър с SSE** | SSE ни помага да изложим сървър в интернет. Тази част ще ви помогне да създадете сървър с помощта на SSE | [Създаване на сървър с SSE](./03-GettingStarted/05-sse-server/README.md) |
| 3.6 | **HTTP стрийминг** | Научете как да имплементирате HTTP стрийминг за пренос на данни в реално време между клиенти и MCP сървъри | [HTTP стрийминг](./03-GettingStarted/06-http-streaming/README.md) |
| 3.7 | **Използване на AI Toolkit** | AI toolkit е страхотен инструмент, който ще ви помогне да управлявате AI и MCP работните си процеси | [Използване на AI Toolkit](./03-GettingStarted/07-aitk/README.md) |
| 3.8 | **Тестване на вашия сървър** | Тестването е важна част от разработката. Тази част ще ви покаже как да използвате различни инструменти за тестове | [Тестване на вашия сървър](./03-GettingStarted/08-testing/README.md) |
| 3.9 | **Деплой на вашия сървър** | Как да преминете от локална разработка към продукция? Тази част ще ви помогне да разработите и внедрите вашия сървър | [Деплой на вашия сървър](./03-GettingStarted/09-deployment/README.md) |
| 04 | **Практическа имплементация** | Използване на SDK-та на различни езици, дебъгване, тестване и валидиране, създаване на повторно използваеми шаблони и работни процеси | [Практическа имплементация](./04-PracticalImplementation/README.md) |
| 05 | **Разширени теми в MCP** | Мултимодални AI работни процеси и разширяемост, сигурни стратегии за скалиране, MCP в корпоративни екосистеми | [Разширени теми](./05-AdvancedTopics/README.md) |
| 5.1 | **Интеграция на MCP с Azure** | Показва интеграция с Azure | [Интеграция на MCP с Azure](./05-AdvancedTopics/mcp-integration/README.md) |
| 5.2 | **Мултимодалност** | Показва как да работите с различни модалности като изображения и други | [Мултимодалност](./05-AdvancedTopics/mcp-multi-modality/README.md) |
| 5.3 | **MCP OAuth2 демонстрация** | Минимално Spring Boot приложение, показващо OAuth2 с MCP, както като Authorization, така и като Resource Server. Демонстрира сигурно издаване на токени, защитени крайни точки, внедряване в Azure Container Apps и интеграция с API Management | [MCP OAuth2 демонстрация](./05-AdvancedTopics/mcp-oauth2-demo/README.md) |
| 5.4 | **Root Contexts** | Научете повече за root context и как да ги имплементирате | [Root Contexts](./05-AdvancedTopics/mcp-root-contexts/README.md) |
| 5.5 | **Маршрутизиране** | Научете различни видове маршрутизиране | [Маршрутизиране](./05-AdvancedTopics/mcp-routing/README.md) |
| 5.6 | **Семплиране** | Научете как да работите със семплиране | [Семплиране](./05-AdvancedTopics/mcp-sampling/README.md) |
| 5.7 | **Скалиране** | Научете за скалирането на MCP сървъри, включително хоризонтални и вертикални стратегии, оптимизация на ресурсите и настройка на производителността | [Скалиране](./05-AdvancedTopics/mcp-scaling/README.md) |
| 5.8 | **Сигурност** | Защитете вашия MCP сървър, включително стратегии за автентикация, авторизация и защита на данните | [Сигурност](./05-AdvancedTopics/mcp-security/README.md) |
| 5.9 | **Web Search MCP** | Python MCP сървър и клиент, интегрирани със SerpAPI за търсене в уеб, новини, продукти и въпроси и отговори в реално време. Демонстрира мулти-инструментна оркестрация, интеграция с външни API-та и стабилно обработване на грешки | [Web Search MCP](./05-AdvancedTopics/web-search-mcp/README.md) |
| 5.10 | **Реално време стрийминг** | Потокът на данни в реално време се превърна в ключов елемент в съвременния свят, където бизнесите и приложенията изискват незабавен достъп до информация за своевременни решения | [Реално време стрийминг](./05-AdvancedTopics/mcp-realtimestreaming/README.md) |
| 5.11 | **Реално време уеб търсене** | Как MCP трансформира уеб търсенето в реално време, предоставяйки стандартизиран подход към управлението на контекста между AI модели, търсачки и приложения | [Реално време уеб търсене](./05-AdvancedTopics/mcp-realtimesearch/README.md) |
| 06 | **Приноси от общността** | Как да допринасяте с код и документация, сътрудничество чрез GitHub, подобрения и обратна връзка от общността | [Приноси от общността](./06-CommunityContributions/README.md) |
| 07 | **Уроци от ранното приемане** | Практически реализации и какво сработи, изграждане и внедряване на решения базирани на MCP, тенденции и бъдеща пътна карта | [Insights](./07-LessonsFromEarlyAdoption/README.md) |
| 08 | **Добри практики за MCP** | Оптимизация и настройка на производителността, проектиране на устойчиви на грешки MCP системи, стратегии за тестване и устойчивост | [Best Practices](./08-BestPractices/README.md) |
| 09 | **Казуси за MCP** | Задълбочен анализ на архитектури на MCP решения, планове за внедряване и съвети за интеграция, анотирани диаграми и обяснения на проекти | [Case Studies](./09-CaseStudy/README.md) |
| 10 | **Оптимизиране на AI работни потоци: Създаване на MCP сървър с AI Toolkit** | Изчерпателен практически семинар, комбиниращ MCP с AI Toolkit на Microsoft за VS Code. Научете как да изграждате интелигентни приложения, свързващи AI модели с реални инструменти чрез практически модули, обхващащи основите, разработка на персонализиран сървър и стратегии за внедряване в продукция. | [Hands On Lab](./10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/README.md) |

## Примерни проекти

### 🧮 Примерни проекти на MCP калкулатор:
<details>
  <summary><strong>Разгледайте имплементации по езици</strong></summary>

  - [Пример MCP сървър на C#](./03-GettingStarted/samples/csharp/README.md)
  - [MCP калкулатор на Java](./03-GettingStarted/samples/java/calculator/README.md)
  - [MCP демонстрация на JavaScript](./03-GettingStarted/samples/javascript/README.md)
  - [MCP сървър на Python](../../03-GettingStarted/samples/python/mcp_calculator_server.py)
  - [MCP пример на TypeScript](./03-GettingStarted/samples/typescript/README.md)

</details>

### 💡 Разширени MCP калкулаторни проекти:
<details>
  <summary><strong>Разгледайте разширени примери</strong></summary>

  - [Разширен пример на C#](./04-PracticalImplementation/samples/csharp/README.md)
  - [Пример на контейнерно приложение на Java](./04-PracticalImplementation/samples/java/containerapp/README.md)
  - [Разширен пример на JavaScript](./04-PracticalImplementation/samples/javascript/README.md)
  - [Сложна имплементация на Python](../../04-PracticalImplementation/samples/python/mcp_sample.py)
  - [Пример на контейнер на TypeScript](./04-PracticalImplementation/samples/typescript/README.md)

</details>


## 🎯 Предварителни изисквания за учене на MCP

За да извлечете максимума от тази учебна програма, трябва да имате:

- Основни познания по C#, Java или Python  
- Разбиране на клиент-сървър модел и API-та  
- (По избор) Познания по машинно обучение  

## 📚 Учебно ръководство

Наличен е изчерпателен [Учебен наръчник](./study_guide.md), който ще ви помогне да се ориентирате ефективно в това хранилище. Наръчникът включва:

- Визуална карта на учебната програма с всички разгледани теми  
- Подробно описание на всяка секция от хранилището  
- Насоки за използване на примерните проекти  
- Препоръчани пътеки за обучение за различни нива на умения  
- Допълнителни ресурси за подпомагане на обучението ви  

## 🛠️ Как да използвате тази учебна програма ефективно

Всяка лекция в това ръководство включва:

1. Ясни обяснения на MCP концепциите  
2. Живи кодови примери на няколко езика  
3. Упражнения за създаване на реални MCP приложения  
4. Допълнителни ресурси за напреднали учащи  

## 📜 Лицензионна информация

Това съдържание е лицензирано под **MIT License**. За условията вижте [LICENSE](../../LICENSE).

## 🤝 Насоки за принос

Този проект приветства приноси и предложения. Повечето приноси изискват да се съгласите с
Contributor License Agreement (CLA), с който декларирате, че имате право и действително предоставяте
правата ни да използваме вашия принос. За подробности посетете <https://cla.opensource.microsoft.com>.

Когато подадете pull request, CLA бот автоматично ще определи дали трябва да предоставите
CLA и ще маркира PR подходящо (напр. проверка на статус, коментар). Просто следвайте инструкциите,
които ботът ви дава. Това се прави само веднъж за всички хранилища, използващи нашия CLA.

Този проект е приел [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
За повече информация вижте [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) или се свържете с [opencode@microsoft.com](mailto:opencode@microsoft.com) при допълнителни въпроси или коментари.

## 🎒 Други курсове
Нашият екип предлага и други курсове! Вижте:

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
- [Овладяване на GitHub Copilot за съвместно програмиране с изкуствен интелект](https://aka.ms/GitHubCopilotAI?WT.mc_id=academic-105485-koreyst)
- [Овладяване на GitHub Copilot за разработчици на C#/.NET](https://github.com/microsoft/mastering-github-copilot-for-dotnet-csharp-developers?WT.mc_id=academic-105485-koreyst)
- [Избери своето приключение с Copilot](https://github.com/microsoft/CopilotAdventures?WT.mc_id=academic-105485-koreyst)


## ™️ Уведомление за търговска марка

Този проект може да съдържа търговски марки или лога на проекти, продукти или услуги. Употребата на търговски марки или лога на Microsoft е разрешена само при спазване на
[Правилата за търговски марки и бранд на Microsoft](https://www.microsoft.com/legal/intellectualproperty/trademarks/usage/general).
Използването на търговски марки или лога на Microsoft в модифицирани версии на този проект не трябва да създава объркване или да предполага спонсорство от Microsoft.
Всяко използване на търговски марки или лога на трети страни е предмет на политиките на тези трети страни.

**Отказ от отговорност**:  
Този документ е преведен с помощта на AI преводаческа услуга [Co-op Translator](https://github.com/Azure/co-op-translator). Въпреки че се стремим към точност, моля, имайте предвид, че автоматизираните преводи могат да съдържат грешки или неточности. Оригиналният документ на неговия език трябва да се счита за авторитетен източник. За критична информация се препоръчва професионален човешки превод. Ние не носим отговорност за никакви недоразумения или неправилни тълкувания, произтичащи от използването на този превод.