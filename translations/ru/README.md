<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "9a14017adf28f7440f20c2d5e7f1d0f8",
  "translation_date": "2025-06-17T15:11:27+00:00",
  "source_file": "README.md",
  "language_code": "ru"
}
-->
![MCP-for-beginners](../../translated_images/mcp-beginners.2ce2b317996369ff66c5b72e25eff9d4288ab2741fc70c0b4e523d1ae1e249fd.ru.png) 

[![GitHub contributors](https://img.shields.io/github/contributors/microsoft/mcp-for-beginners.svg)](https://GitHub.com/microsoft/mcp-for-beginners/graphs/contributors)
[![GitHub issues](https://img.shields.io/github/issues/microsoft/mcp-for-beginners.svg)](https://GitHub.com/microsoft/mcp-for-beginners/issues)
[![GitHub pull-requests](https://img.shields.io/github/issues-pr/microsoft/mcp-for-beginners.svg)](https://GitHub.com/microsoft/mcp-for-beginners/pulls)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)

[![GitHub watchers](https://img.shields.io/github/watchers/microsoft/mcp-for-beginners.svg?style=social&label=Watch)](https://GitHub.com/microsoft/mcp-for-beginners/watchers)
[![GitHub forks](https://img.shields.io/github/forks/microsoft/mcp-for-beginners.svg?style=social&label=Fork)](https://GitHub.com/microsoft/mcp-for-beginners/fork)
[![GitHub stars](https://img.shields.io/github/stars/microsoft/mcp-for-beginners?style=social&label=Star)](https://GitHub.com/microsoft/mcp-for-beginners/stargazers)


[![Microsoft Azure AI Foundry Discord](https://dcbadge.vercel.app/api/server/ByRwuEEgH4)](https://discord.com/invite/ByRwuEEgH4)


Следуйте этим шагам, чтобы начать использовать эти ресурсы:
1. **Создайте форк репозитория**: Нажмите [![GitHub forks](https://img.shields.io/github/forks/microsoft/mcp-for-beginners.svg?style=social&label=Fork)](https://GitHub.com/microsoft/mcp-for-beginners/fork)
2. **Клонируйте репозиторий**:   `git clone https://github.com/microsoft/mcp-for-beginners.git`
3. [**Присоединяйтесь к Azure AI Foundry Discord, чтобы познакомиться с экспертами и другими разработчиками**](https://discord.com/invite/ByRwuEEgH4)


### 🌐 Поддержка нескольких языков

#### Поддерживается через GitHub Action (автоматически и всегда актуально)

# 🚀 Учебная программа по Model Context Protocol (MCP) для начинающих

## **Изучайте MCP на практике с примерами кода на C#, Java, JavaScript, Python и TypeScript**

## 🧠 Обзор учебной программы по Model Context Protocol

**Model Context Protocol (MCP)** — это современный фреймворк, созданный для стандартизации взаимодействия между AI-моделями и клиентскими приложениями. Эта открытая учебная программа предлагает структурированный путь обучения с практическими примерами кода и реальными кейсами на популярных языках программирования: C#, Java, JavaScript, TypeScript и Python.

Будь вы разработчиком AI, системным архитектором или инженером-программистом, это руководство станет вашим полным ресурсом для освоения основ MCP и стратегий его внедрения.

## 🔗 Официальные ресурсы MCP

- 📘 [Документация MCP](https://modelcontextprotocol.io/) – подробные учебники и руководства пользователя  
- 📜 [Спецификация MCP](https://spec.modelcontextprotocol.io/) – архитектура протокола и технические справочники  
- 🧑‍💻 [Репозиторий MCP на GitHub](https://github.com/modelcontextprotocol) – открытые SDK, инструменты и примеры кода  

## 🧭 Полная структура учебной программы MCP

| Гл | Название | Описание | Ссылка |
|--|--|--|--|
| 00 | **Введение в MCP** | Обзор Model Context Protocol и его роли в AI-пайплайнах, что такое MCP, почему важна стандартизация, практические кейсы и преимущества | [Введение](./00-Introduction/README.md) |
| 01 | **Основные концепции** | Глубокое изучение ключевых понятий MCP: клиент-серверная архитектура, основные компоненты протокола, шаблоны обмена сообщениями | [Основные концепции](./01-CoreConcepts/README.md) |
| 02 | **Безопасность в MCP** | Выявление угроз безопасности в системах на базе MCP, методы и лучшие практики защиты реализации | [Безопасность](./02-Security/README.md) |
| 03 | **Начало работы с MCP** | Настройка окружения, создание базовых серверов и клиентов MCP, интеграция MCP с существующими приложениями | [Начало работы](./03-GettingStarted/README.md) |
| 3.1 | **Первый сервер** | Настройка простого сервера по протоколу MCP, понимание взаимодействия сервер-клиент, тестирование сервера | [Первый сервер](./03-GettingStarted/01-first-server/README.md) |
| 3.2 | **Первый клиент** | Настройка простого клиента по протоколу MCP, понимание взаимодействия клиент-сервер, тестирование клиента | [Первый клиент](./03-GettingStarted/02-client/README.md) |
| 3.3 | **Клиент с LLM** | Настройка клиента MCP с использованием большой языковой модели (LLM) | [Клиент с LLM](./03-GettingStarted/03-llm-client/README.md) |
| 3.4 | **Работа с сервером через Visual Studio Code** | Настройка Visual Studio Code для работы с серверами по протоколу MCP | [Работа с сервером через Visual Studio Code](./03-GettingStarted/04-vscode/README.md) |
| 3.5 | **Создание сервера с помощью SSE** | SSE помогает открыть сервер в интернет. В этом разделе вы научитесь создавать сервер с использованием SSE | [Создание сервера с помощью SSE](./03-GettingStarted/05-sse-server/README.md) |
| 3.6 | **HTTP стриминг** | Изучите, как реализовать HTTP стриминг для передачи данных в реальном времени между клиентами и MCP-серверами | [HTTP стриминг](./03-GettingStarted/06-http-streaming/README.md) |
| 3.7 | **Использование AI Toolkit** | AI Toolkit — отличный инструмент для управления вашим AI и MCP рабочим процессом | [Использование AI Toolkit](./03-GettingStarted/07-aitk/README.md) |
| 3.8 | **Тестирование сервера** | Тестирование — важная часть разработки. В этом разделе вы познакомитесь с несколькими инструментами для тестирования | [Тестирование сервера](./03-GettingStarted/08-testing/README.md) |
| 3.9 | **Развертывание сервера** | Как перейти от локальной разработки к продакшену? В этом разделе вы узнаете, как разрабатывать и развертывать сервер | [Развертывание сервера](./03-GettingStarted/09-deployment/README.md) |
| 04 | **Практическая реализация** | Использование SDK на разных языках, отладка, тестирование и валидация, создание повторно используемых шаблонов запросов и рабочих процессов | [Практическая реализация](./04-PracticalImplementation/README.md) |
| 05 | **Продвинутые темы MCP** | Мультимодальные AI-воркфлоу и расширяемость, безопасные стратегии масштабирования, MCP в корпоративных экосистемах | [Продвинутые темы](./05-AdvancedTopics/README.md) |
| 5.1 | **Интеграция MCP с Azure** | Демонстрация интеграции с Azure | [Интеграция MCP с Azure](./05-AdvancedTopics/mcp-integration/README.md) |
| 5.2 | **Мультимодальность** | Работа с разными типами данных, такими как изображения и другие | [Мультимодальность](./05-AdvancedTopics/mcp-multi-modality/README.md) |
| 5.3 | **Демо MCP OAuth2** | Минимальное приложение на Spring Boot, показывающее OAuth2 с MCP как Authorization и Resource Server. Демонстрирует безопасную выдачу токенов, защищённые эндпоинты, развертывание в Azure Container Apps и интеграцию с API Management. | [Демо MCP OAuth2](./05-AdvancedTopics/mcp-oauth2-demo/README.md) |
| 5.4 | **Корневые контексты** | Узнайте больше о корневом контексте и его реализации | [Корневые контексты](./05-AdvancedTopics/mcp-root-contexts/README.md) |
| 5.5 | **Маршрутизация** | Изучение различных типов маршрутизации | [Маршрутизация](./05-AdvancedTopics/mcp-routing/README.md) |
| 5.6 | **Сэмплирование** | Узнайте, как работать с сэмплированием | [Сэмплирование](./05-AdvancedTopics/mcp-sampling/README.md) |
| 5.7 | **Масштабирование** | Изучите масштабирование MCP серверов, включая горизонтальное и вертикальное масштабирование, оптимизацию ресурсов и настройку производительности | [Масштабирование](./05-AdvancedTopics/mcp-scaling/README.md) |
| 5.8 | **Безопасность** | Защитите свой MCP сервер: аутентификация, авторизация и стратегии защиты данных | [Безопасность](./05-AdvancedTopics/mcp-security/README.md) |
| 5.9 | **Web Search MCP** | MCP сервер и клиент на Python, интегрированные с SerpAPI для поиска в интернете, новостей, товаров и вопросов-ответов в реальном времени. Демонстрирует мультиинструментальную оркестрацию, интеграцию с внешними API и надежную обработку ошибок | [Web Search MCP](./05-AdvancedTopics/web-search-mcp/README.md) |
| 5.10 | **Потоковая передача в реальном времени** | Потоковая передача данных в реальном времени стала необходимостью в современном мире, где бизнесы и приложения требуют мгновенного доступа к информации для своевременных решений. | [Потоковая передача в реальном времени](./05-AdvancedTopics/mcp-realtimestreaming/README.md) |
| 5.11 | **Поиск в интернете в реальном времени** | Как MCP меняет поиск в интернете в реальном времени, предоставляя стандартизированный подход к управлению контекстом между AI-моделями, поисковыми системами и приложениями. | [Поиск в интернете в реальном времени](./05-AdvancedTopics/mcp-realtimesearch/README.md) |
| 06 | **Вклад сообщества** | Как вносить код и документацию, сотрудничество через GitHub, улучшения и обратная связь от сообщества | [Вклад сообщества](./06-CommunityContributions/README.md) |
| 07 | **Выводы из раннего внедрения** | Практические реализации и что сработало, создание и развертывание решений на базе MCP, тенденции и планы на будущее | [Insights](./07-LessonsFromEarlyAdoption/README.md) |
| 08 | **Лучшие практики для MCP** | Настройка производительности и оптимизация, проектирование отказоустойчивых систем MCP, стратегии тестирования и устойчивости | [Best Practices](./08-BestPractices/README.md) |
| 09 | **Кейсы MCP** | Подробный разбор архитектур решений MCP, шаблоны развертывания и советы по интеграции, аннотированные диаграммы и пошаговые обзоры проектов | [Case Studies](./09-CaseStudy/README.md) |
| 10 | **Оптимизация AI-рабочих процессов: создание MCP-сервера с AI Toolkit** | Всесторонний практический семинар, объединяющий MCP с AI Toolkit от Microsoft для VS Code. Изучите создание интеллектуальных приложений, связывающих AI-модели с реальными инструментами через практические модули, охватывающие основы, разработку кастомного сервера и стратегии развертывания в продакшн. | [Hands On Lab](./10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/README.md) |

## Примерные проекты

### 🧮 Примеры проектов калькулятора MCP:
<details>
  <summary><strong>Изучите реализации кода по языкам</strong></summary>

  - [Пример MCP-сервера на C#](./03-GettingStarted/samples/csharp/README.md)
  - [Калькулятор MCP на Java](./03-GettingStarted/samples/java/calculator/README.md)
  - [Демо MCP на JavaScript](./03-GettingStarted/samples/javascript/README.md)
  - [MCP-сервер на Python](../../03-GettingStarted/samples/python/mcp_calculator_server.py)
  - [Пример MCP на TypeScript](./03-GettingStarted/samples/typescript/README.md)

</details>

### 💡 Продвинутые проекты калькулятора MCP:
<details>
  <summary><strong>Изучите продвинутые примеры</strong></summary>

  - [Продвинутый пример на C#](./04-PracticalImplementation/samples/csharp/README.md)
  - [Пример контейнерного приложения на Java](./04-PracticalImplementation/samples/java/containerapp/README.md)
  - [Продвинутый пример на JavaScript](./04-PracticalImplementation/samples/javascript/README.md)
  - [Сложная реализация на Python](../../04-PracticalImplementation/samples/python/mcp_sample.py)
  - [Пример контейнера на TypeScript](./04-PracticalImplementation/samples/typescript/README.md)

</details>

## 🎯 Требования для изучения MCP

Чтобы максимально эффективно использовать этот курс, у вас должны быть:

- Базовые знания C#, Java или Python  
- Понимание модели клиент-сервер и API  
- (По желанию) Знакомство с основами машинного обучения  

## 📚 Руководство по обучению

Доступно подробное [Руководство по обучению](./study_guide.md), которое поможет вам эффективно ориентироваться в этом репозитории. В руководстве вы найдете:

- Визуальную карту учебной программы с охватом всех тем  
- Детальный разбор каждого раздела репозитория  
- Инструкции по использованию примерных проектов  
- Рекомендуемые пути обучения для разных уровней подготовки  
- Дополнительные ресурсы для углубленного изучения  

## 🛠️ Как эффективно использовать этот курс

Каждый урок в этом руководстве включает:

1. Понятные объяснения концепций MCP  
2. Примеры кода в нескольких языках программирования  
3. Задания для создания реальных MCP-приложений  
4. Дополнительные материалы для продвинутых пользователей  

## 📜 Лицензионная информация

Этот материал распространяется под **MIT License**. Условия использования смотрите в файле [LICENSE](../../LICENSE).

## 🤝 Руководство по внесению изменений

Этот проект приветствует ваши предложения и вклад. Большинство изменений требуют согласия с
Contributor License Agreement (CLA), подтверждающим, что вы имеете право и действительно предоставляете
нам права на использование вашего вклада. Подробнее на <https://cla.opensource.microsoft.com>.

При создании pull request бот CLA автоматически определит, нужно ли вам предоставлять CLA, и отметит PR соответствующим образом (например, проверкой статуса или комментарием). Просто следуйте инструкциям бота. Эту процедуру нужно пройти только один раз для всех репозиториев, использующих наш CLA.

Проект придерживается [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
Больше информации смотрите в [FAQ по Кодексу поведения](https://opensource.microsoft.com/codeofconduct/faq/) или пишите на [opencode@microsoft.com](mailto:opencode@microsoft.com) с вопросами и комментариями.

## 🎒 Другие курсы
Наша команда выпускает и другие курсы! Ознакомьтесь с ними:

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
- [Осваиваем GitHub Copilot для совместного программирования с ИИ](https://aka.ms/GitHubCopilotAI?WT.mc_id=academic-105485-koreyst)
- [Осваиваем GitHub Copilot для разработчиков C#/.NET](https://github.com/microsoft/mastering-github-copilot-for-dotnet-csharp-developers?WT.mc_id=academic-105485-koreyst)
- [Выбери своё собственное приключение с Copilot](https://github.com/microsoft/CopilotAdventures?WT.mc_id=academic-105485-koreyst)


## ™️ Уведомление о товарном знаке

В этом проекте могут использоваться товарные знаки или логотипы проектов, продуктов или услуг. Авторизованное использование товарных знаков или логотипов Microsoft регулируется и должно соответствовать  
[Руководству Microsoft по товарным знакам и брендам](https://www.microsoft.com/legal/intellectualproperty/trademarks/usage/general).  
Использование товарных знаков или логотипов Microsoft в изменённых версиях этого проекта не должно вводить в заблуждение или подразумевать спонсорство со стороны Microsoft.  
Любое использование товарных знаков или логотипов третьих сторон подчиняется политикам этих сторон.

**Отказ от ответственности**:  
Этот документ был переведен с помощью сервиса автоматического перевода [Co-op Translator](https://github.com/Azure/co-op-translator). Несмотря на наши усилия обеспечить точность, просим учитывать, что автоматические переводы могут содержать ошибки или неточности. Оригинальный документ на его исходном языке следует считать авторитетным источником. Для получения критически важной информации рекомендуется обращаться к профессиональному переводу, выполненному человеком. Мы не несем ответственности за любые недоразумения или неправильные толкования, возникшие в результате использования данного перевода.