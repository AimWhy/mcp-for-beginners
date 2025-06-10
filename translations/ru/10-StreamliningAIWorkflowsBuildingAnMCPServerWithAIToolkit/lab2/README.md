<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "a22b7dd11cd7690f99f9195877cafdc3",
  "translation_date": "2025-06-10T05:36:08+00:00",
  "source_file": "10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab2/README.md",
  "language_code": "ru"
}
-->
# 🌐 Модуль 2: Основы MCP с AI Toolkit

[![Duration](https://img.shields.io/badge/Duration-20%20minutes-blue.svg)]()
[![Difficulty](https://img.shields.io/badge/Difficulty-Intermediate-yellow.svg)]()
[![Prerequisites](https://img.shields.io/badge/Prerequisites-Module%201%20Complete-orange.svg)]()

## 📋 Цели обучения

К концу этого модуля вы сможете:
- ✅ Понимать архитектуру и преимущества Model Context Protocol (MCP)
- ✅ Ознакомиться с экосистемой MCP серверов Microsoft
- ✅ Интегрировать MCP серверы с AI Toolkit Agent Builder
- ✅ Создать функционального агента для автоматизации браузера с использованием Playwright MCP
- ✅ Настроить и протестировать инструменты MCP в ваших агентах
- ✅ Экспортировать и развертывать агентов с поддержкой MCP для использования в продакшене

## 🎯 Продолжение после Модуля 1

В Модуле 1 мы освоили основы AI Toolkit и создали нашего первого Python агента. Теперь мы **прокачаем** ваших агентов, подключив их к внешним инструментам и сервисам через революционный **Model Context Protocol (MCP)**.

Представьте, что вы переходите от простого калькулятора к полноценному компьютеру — ваши AI агенты получат возможность:
- 🌐 Просматривать и взаимодействовать с веб-сайтами
- 📁 Получать доступ и управлять файлами
- 🔧 Интегрироваться с корпоративными системами
- 📊 Обрабатывать данные в реальном времени через API

## 🧠 Понимание Model Context Protocol (MCP)

### 🔍 Что такое MCP?

Model Context Protocol (MCP) — это **«USB-C для AI-приложений»** — революционный открытый стандарт, который связывает большие языковые модели (LLM) с внешними инструментами, источниками данных и сервисами. Так же, как USB-C избавил нас от хаоса с кабелями, предоставив универсальный разъем, MCP упрощает интеграцию AI с помощью одного стандартизированного протокола.

### 🎯 Проблемы, которые решает MCP

**До MCP:**
- 🔧 Индивидуальные интеграции для каждого инструмента
- 🔄 Зависимость от поставщиков с проприетарными решениями
- 🔒 Уязвимости безопасности из-за разрозненных подключений
- ⏱️ Месяцы разработки для базовых интеграций

**С MCP:**
- ⚡ Интеграция инструментов по принципу «включил и работай»
- 🔄 Независимая от поставщиков архитектура
- 🛡️ Встроенные лучшие практики безопасности
- 🚀 Добавление новых возможностей за считанные минуты

### 🏗️ Глубокое погружение в архитектуру MCP

MCP использует **клиент-серверную архитектуру**, создавая безопасную и масштабируемую экосистему:

```mermaid
graph TB
    A[AI Application/Agent] --> B[MCP Client]
    B --> C[MCP Server 1: Files]
    B --> D[MCP Server 2: Web APIs]
    B --> E[MCP Server 3: Database]
    B --> F[MCP Server N: Custom Tools]
    
    C --> G[Local File System]
    D --> H[External APIs]
    E --> I[Database Systems]
    F --> J[Enterprise Systems]
```

**🔧 Основные компоненты:**

| Компонент      | Роль                                   | Примеры                         |
|----------------|---------------------------------------|--------------------------------|
| **MCP Hosts**  | Приложения, использующие MCP-сервисы | Claude Desktop, VS Code, AI Toolkit |
| **MCP Clients**| Обработчики протокола (1:1 с серверами) | Встроены в хост-приложения      |
| **MCP Servers**| Предоставляют возможности через стандартный протокол | Playwright, Files, Azure, GitHub |
| **Transport Layer** | Методы коммуникации               | stdio, HTTP, WebSockets        |


## 🏢 Экосистема MCP серверов Microsoft

Microsoft возглавляет экосистему MCP, предлагая комплексный набор серверов корпоративного уровня, которые решают реальные бизнес-задачи.

### 🌟 Основные MCP серверы Microsoft

#### 1. ☁️ Azure MCP Server  
**🔗 Репозиторий**: [azure/azure-mcp](https://github.com/azure/azure-mcp)  
**🎯 Назначение**: Комплексное управление ресурсами Azure с AI интеграцией

**✨ Ключевые возможности:**
- Декларативное управление инфраструктурой
- Мониторинг ресурсов в реальном времени
- Рекомендации по оптимизации затрат
- Проверка соответствия требованиям безопасности

**🚀 Сценарии использования:**
- Инфраструктура как код с поддержкой AI
- Автоматическое масштабирование ресурсов
- Оптимизация расходов на облако
- Автоматизация DevOps процессов

#### 2. 📊 Microsoft Dataverse MCP  
**📚 Документация**: [Microsoft Dataverse Integration](https://go.microsoft.com/fwlink/?linkid=2320176)  
**🎯 Назначение**: Интерфейс на естественном языке для бизнес-данных

**✨ Ключевые возможности:**
- Запросы к базе данных на естественном языке
- Понимание бизнес-контекста
- Пользовательские шаблоны подсказок
- Управление корпоративными данными

**🚀 Сценарии использования:**
- Отчеты бизнес-аналитики
- Анализ данных клиентов
- Аналитика продаж
- Запросы для соответствия требованиям

#### 3. 🌐 Playwright MCP Server  
**🔗 Репозиторий**: [microsoft/playwright-mcp](https://github.com/microsoft/playwright-mcp)  
**🎯 Назначение**: Автоматизация браузера и взаимодействие с вебом

**✨ Ключевые возможности:**
- Кросс-браузерная автоматизация (Chrome, Firefox, Safari)
- Интеллектуальное обнаружение элементов
- Создание скриншотов и PDF
- Мониторинг сетевого трафика

**🚀 Сценарии использования:**
- Автоматизация тестирования
- Веб-скрейпинг и извлечение данных
- Мониторинг UI/UX
- Автоматизация конкурентного анализа

#### 4. 📁 Files MCP Server  
**🔗 Репозиторий**: [microsoft/files-mcp-server](https://github.com/microsoft/files-mcp-server)  
**🎯 Назначение**: Интеллектуальные операции с файловой системой

**✨ Ключевые возможности:**
- Декларативное управление файлами
- Синхронизация содержимого
- Интеграция с системами контроля версий
- Извлечение метаданных

**🚀 Сценарии использования:**
- Управление документацией
- Организация репозиториев кода
- Рабочие процессы публикации контента
- Обработка файлов в дата-пайплайнах

#### 5. 📝 MarkItDown MCP Server  
**🔗 Репозиторий**: [microsoft/markitdown](https://github.com/microsoft/markitdown)  
**🎯 Назначение**: Продвинутая обработка и манипуляции Markdown

**✨ Ключевые возможности:**
- Глубокий парсинг Markdown
- Конвертация форматов (MD ↔ HTML ↔ PDF)
- Анализ структуры контента
- Обработка шаблонов

**🚀 Сценарии использования:**
- Рабочие процессы технической документации
- Системы управления контентом
- Генерация отчетов
- Автоматизация базы знаний

#### 6. 📈 Clarity MCP Server  
**📦 Пакет**: [@microsoft/clarity-mcp-server](https://www.npmjs.com/package/@microsoft/clarity-mcp-server)  
**🎯 Назначение**: Веб-аналитика и анализ поведения пользователей

**✨ Ключевые возможности:**
- Анализ тепловых карт
- Записи сессий пользователей
- Метрики производительности
- Анализ воронки конверсий

**🚀 Сценарии использования:**
- Оптимизация веб-сайтов
- Исследование пользовательского опыта
- Анализ A/B тестирования
- Дашборды бизнес-аналитики

### 🌍 Экосистема сообщества

Кроме серверов Microsoft, экосистема MCP включает:
- **🐙 GitHub MCP**: управление репозиториями и анализ кода
- **🗄️ MCP для баз данных**: интеграции с PostgreSQL, MySQL, MongoDB
- **☁️ MCP облачных провайдеров**: инструменты AWS, GCP, Digital Ocean
- **📧 MCP для коммуникаций**: интеграции Slack, Teams, Email

## 🛠️ Практическая лаборатория: Создание агента для автоматизации браузера

**🎯 Цель проекта**: Создать интеллектуального агента для автоматизации браузера с использованием Playwright MCP, который сможет навигировать по сайтам, извлекать информацию и выполнять сложные веб-взаимодействия.

### 🚀 Фаза 1: Настройка основы агента

#### Шаг 1: Инициализация агента  
1. **Откройте AI Toolkit Agent Builder**  
2. **Создайте нового агента** с конфигурацией:  
   - **Имя**: `BrowserAgent`
   - **Model**: Choose GPT-4o 

![BrowserAgent](../../../../translated_images/BrowserAgent.09c1adde5e136573b64ab1baecd830049830e295eac66cb18bebb85fb386e00a.ru.png)


### 🔧 Phase 2: MCP Integration Workflow

#### Step 3: Add MCP Server Integration
1. **Navigate to Tools Section** in Agent Builder
2. **Click "Add Tool"** to open the integration menu
3. **Select "MCP Server"** from available options

![AddMCP](../../../../translated_images/AddMCP.afe3308ac20aa94469a5717b632d77b2197b9838a438b05d39aeb2db3ec47ef1.ru.png)

**🔍 Understanding Tool Types:**
- **Built-in Tools**: Pre-configured AI Toolkit functions
- **MCP Servers**: External service integrations
- **Custom APIs**: Your own service endpoints
- **Function Calling**: Direct model function access

#### Step 4: MCP Server Selection
1. **Choose "MCP Server"** option to proceed
![AddMCPServer](../../../../translated_images/AddMCPServer.69b911ccef872cbd0d0c0c2e6a00806916e1673e543b902a23dee23e6ff54b4c.ru.png)

2. **Browse MCP Catalog** to explore available integrations
![MCPCatalog](../../../../translated_images/MCPCatalog.a817d053145699006264f5a475f2b48fbd744e43633f656b6453c15a09ba5130.ru.png)


### 🎮 Phase 3: Playwright MCP Configuration

#### Step 5: Select and Configure Playwright
1. **Click "Use Featured MCP Servers"** to access Microsoft's verified servers
2. **Select "Playwright"** from the featured list
3. **Accept Default MCP ID** or customize for your environment

![MCPID](../../../../translated_images/MCPID.67d446052979e819c945ff7b6430196ef587f5217daadd3ca52fa9659c1245c9.ru.png)

#### Step 6: Enable Playwright Capabilities
**🔑 Critical Step**: Select **ALL** available Playwright methods for maximum functionality

![Tools](../../../../translated_images/Tools.3ea23c447b4d9feccbd7101e6dcf9e27cb0e5273f351995fde62c5abf9a78b4c.ru.png)

**🛠️ Essential Playwright Tools:**
- **Navigation**: `goto`, `goBack`, `goForward`, `reload`
- **Interaction**: `click`, `fill`, `press`, `hover`, `drag`
- **Extraction**: `textContent`, `innerHTML`, `getAttribute`
- **Validation**: `isVisible`, `isEnabled`, `waitForSelector`
- **Capture**: `screenshot`, `pdf`, `video`
- **Network**: `setExtraHTTPHeaders`, `route`, `waitForResponse`

#### Шаг 7: Проверка успешной интеграции  
**✅ Признаки успеха:**  
- Все инструменты отображаются в интерфейсе Agent Builder  
- В панели интеграции отсутствуют ошибки  
- Статус сервера Playwright показывает «Connected»

![AgentTools](../../../../translated_images/AgentTools.053cfb96a17e02199dcc6563010d2b324d4fc3ebdd24889657a6950647a52f63.ru.png)

**🔧 Решение распространённых проблем:**  
- **Не удалось подключиться**: Проверьте интернет-соединение и настройки брандмауэра  
- **Отсутствуют инструменты**: Убедитесь, что все возможности были выбраны при настройке  
- **Ошибки разрешений**: Проверьте, что VS Code имеет необходимые системные права

### 🎯 Фаза 4: Продвинутое проектирование подсказок

#### Шаг 8: Создание интеллектуальных системных подсказок  
Разработайте сложные подсказки, использующие все возможности Playwright:

```markdown
# Web Automation Expert System Prompt

## Core Identity
You are an advanced web automation specialist with deep expertise in browser automation, web scraping, and user experience analysis. You have access to Playwright tools for comprehensive browser control.

## Capabilities & Approach
### Navigation Strategy
- Always start with screenshots to understand page layout
- Use semantic selectors (text content, labels) when possible
- Implement wait strategies for dynamic content
- Handle single-page applications (SPAs) effectively

### Error Handling
- Retry failed operations with exponential backoff
- Provide clear error descriptions and solutions
- Suggest alternative approaches when primary methods fail
- Always capture diagnostic screenshots on errors

### Data Extraction
- Extract structured data in JSON format when possible
- Provide confidence scores for extracted information
- Validate data completeness and accuracy
- Handle pagination and infinite scroll scenarios

### Reporting
- Include step-by-step execution logs
- Provide before/after screenshots for verification
- Suggest optimizations and alternative approaches
- Document any limitations or edge cases encountered

## Ethical Guidelines
- Respect robots.txt and rate limiting
- Avoid overloading target servers
- Only extract publicly available information
- Follow website terms of service
```

#### Шаг 9: Создание динамических пользовательских подсказок  
Создайте подсказки, демонстрирующие разные возможности:

**🌐 Пример анализа веб-страницы:**  
```markdown
Navigate to github.com/kinfey and provide a comprehensive analysis including:
1. Repository structure and organization
2. Recent activity and contribution patterns  
3. Documentation quality assessment
4. Technology stack identification
5. Community engagement metrics
6. Notable projects and their purposes

Include screenshots at key steps and provide actionable insights.
```

![Prompt](../../../../translated_images/Prompt.bfc846605db4999f4d9c1b09c710ef63cae7b3057444e68bf07240fb142d9f8f.ru.png)

### 🚀 Фаза 5: Запуск и тестирование

#### Шаг 10: Запустите первую автоматизацию  
1. **Нажмите «Run»** для запуска последовательности автоматизации  
2. **Следите за выполнением в реальном времени**:  
   - Автоматический запуск браузера Chrome  
   - Агент переходит на целевой сайт  
   - Скриншоты фиксируют каждый ключевой шаг  
   - Результаты анализа поступают в режиме реального времени

![Browser](../../../../translated_images/Browser.ec011d0bd64d0d112c8a29bd8cc44c76d0bbfd0b019cb2983ef679328435ce5d.ru.png)

#### Шаг 11: Анализ результатов и выводов  
Просмотрите полный анализ в интерфейсе Agent Builder:

![Result](../../../../translated_images/Result.8638f2b6703e9ea6d58d4e4475e39456b6a51d4c787f9bf481bae694d370a69a.ru.png)

### 🌟 Фаза 6: Продвинутые возможности и развертывание

#### Шаг 12: Экспорт и развертывание в продакшен  
Agent Builder поддерживает несколько вариантов развертывания:

![Code](../../../../translated_images/Code.d9eeeead0b96db0ca19c5b10ad64cfea8c1d0d1736584262970a4d43e1403d13.ru.png)

## 🎓 Итоги Модуля 2 и дальнейшие шаги

### 🏆 Достижение: Мастер интеграции MCP

**✅ Освоенные навыки:**  
- [ ] Понимание архитектуры и преимуществ MCP  
- [ ] Ориентация в экосистеме MCP серверов Microsoft  
- [ ] Интеграция Playwright MCP с AI Toolkit  
- [ ] Создание сложных агентов для автоматизации браузера  
- [ ] Продвинутое проектирование подсказок для веб-автоматизации

### 📚 Дополнительные ресурсы

- **🔗 Спецификация MCP**: [Официальная документация протокола](https://modelcontextprotocol.io/)  
- **🛠️ Playwright API**: [Полное описание методов](https://playwright.dev/docs/api/class-playwright)  
- **🏢 MCP серверы Microsoft**: [Руководство по корпоративной интеграции](https://github.com/microsoft/mcp-servers)  
- **🌍 Примеры из сообщества**: [Галерея MCP серверов](https://github.com/modelcontextprotocol/servers)

**🎉 Поздравляем!** Вы успешно освоили интеграцию MCP и теперь можете создавать готовых к продакшену AI агентов с поддержкой внешних инструментов!

### 🔜 Продолжайте к следующему модулю

Готовы поднять свои навыки MCP на новый уровень? Перейдите к **[Модулю 3: Продвинутая разработка MCP с AI Toolkit](../lab3/README.md)**, где вы научитесь:  
- Создавать собственные кастомные MCP серверы  
- Настраивать и использовать последний MCP Python SDK  
- Работать с MCP Inspector для отладки  
- Осваивать продвинутые рабочие процессы разработки MCP серверов  
- Создавать MCP сервер погоды с нуля

**Отказ от ответственности**:  
Этот документ был переведен с помощью сервиса автоматического перевода [Co-op Translator](https://github.com/Azure/co-op-translator). Несмотря на наши усилия по обеспечению точности, имейте в виду, что автоматические переводы могут содержать ошибки или неточности. Оригинальный документ на его исходном языке следует считать авторитетным источником. Для критически важной информации рекомендуется использовать профессиональный перевод, выполненный человеком. Мы не несем ответственности за любые недоразумения или неправильные толкования, возникшие в результате использования данного перевода.