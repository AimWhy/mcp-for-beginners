<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "9a14017adf28f7440f20c2d5e7f1d0f8",
  "translation_date": "2025-06-17T16:20:16+00:00",
  "source_file": "README.md",
  "language_code": "uk"
}
-->
![MCP-для-початківців](../../translated_images/mcp-beginners.2ce2b317996369ff66c5b72e25eff9d4288ab2741fc70c0b4e523d1ae1e249fd.uk.png) 

[![GitHub contributors](https://img.shields.io/github/contributors/microsoft/mcp-for-beginners.svg)](https://GitHub.com/microsoft/mcp-for-beginners/graphs/contributors)
[![GitHub issues](https://img.shields.io/github/issues/microsoft/mcp-for-beginners.svg)](https://GitHub.com/microsoft/mcp-for-beginners/issues)
[![GitHub pull-requests](https://img.shields.io/github/issues-pr/microsoft/mcp-for-beginners.svg)](https://GitHub.com/microsoft/mcp-for-beginners/pulls)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)

[![GitHub watchers](https://img.shields.io/github/watchers/microsoft/mcp-for-beginners.svg?style=social&label=Watch)](https://GitHub.com/microsoft/mcp-for-beginners/watchers)
[![GitHub forks](https://img.shields.io/github/forks/microsoft/mcp-for-beginners.svg?style=social&label=Fork)](https://GitHub.com/microsoft/mcp-for-beginners/fork)
[![GitHub stars](https://img.shields.io/github/stars/microsoft/mcp-for-beginners?style=social&label=Star)](https://GitHub.com/microsoft/mcp-for-beginners/stargazers)


[![Microsoft Azure AI Foundry Discord](https://dcbadge.vercel.app/api/server/ByRwuEEgH4)](https://discord.com/invite/ByRwuEEgH4)


Виконайте ці кроки, щоб почати користуватися цими ресурсами:
1. **Зробіть форк репозиторію**: Натисніть [![GitHub forks](https://img.shields.io/github/forks/microsoft/mcp-for-beginners.svg?style=social&label=Fork)](https://GitHub.com/microsoft/mcp-for-beginners/fork)
2. **Клонуйте репозиторій**:   `git clone https://github.com/microsoft/mcp-for-beginners.git`
3. [**Приєднуйтесь до Azure AI Foundry Discord, щоб зустріти експертів та інших розробників**](https://discord.com/invite/ByRwuEEgH4)


### 🌐 Підтримка кількох мов

#### Підтримується через GitHub Action (автоматично та завжди актуально)

# 🚀 Навчальна програма Model Context Protocol (MCP) для початківців

## **Вивчайте MCP на практичних прикладах коду на C#, Java, JavaScript, Python та TypeScript**

## 🧠 Огляд навчальної програми Model Context Protocol

**Model Context Protocol (MCP)** — це сучасний фреймворк, створений для стандартизації взаємодії між AI-моделями та клієнтськими додатками. Ця відкрита навчальна програма пропонує структурований шлях навчання з практичними прикладами коду та реальними кейсами на популярних мовах програмування: C#, Java, JavaScript, TypeScript і Python.

Незалежно від того, чи ви розробник AI, системний архітектор або інженер-програміст, цей посібник стане вашим повним ресурсом для опанування основ MCP та стратегій його впровадження.

## 🔗 Офіційні ресурси MCP

- 📘 [Документація MCP](https://modelcontextprotocol.io/) – Детальні навчальні матеріали та керівництва користувача  
- 📜 [Специфікація MCP](https://spec.modelcontextprotocol.io/) – Архітектура протоколу та технічні довідники  
- 🧑‍💻 [Репозиторій MCP на GitHub](https://github.com/modelcontextprotocol) – Відкриті SDK, інструменти та приклади коду  

## 🧭 Повна структура навчальної програми MCP

| Розд | Назва | Опис | Посилання |
|--|--|--|--|
| 00 | **Вступ до MCP** | Огляд Model Context Protocol та його значення в AI-процесах, що таке MCP, чому важлива стандартизація, практичні кейси та переваги | [Вступ](./00-Introduction/README.md) |
| 01 | **Пояснення основних концепцій** | Глибоке вивчення ключових понять MCP, включно з архітектурою клієнт-сервер, основними компонентами протоколу та патернами обміну повідомленнями | [Основні концепції](./01-CoreConcepts/README.md) |
| 02 | **Безпека в MCP** | Виявлення загроз безпеці у системах на базі MCP, методи та найкращі практики для захисту впроваджень | [Безпека](./02-Security/README.md) |
| 03 | **Початок роботи з MCP** | Налаштування середовища, створення базових MCP-серверів і клієнтів, інтеграція MCP з існуючими додатками | [Початок роботи](./03-GettingStarted/README.md) |
| 3.1 | **Перший сервер** | Налаштування базового сервера за допомогою MCP, розуміння взаємодії сервер-клієнт, тестування сервера | [Перший сервер](./03-GettingStarted/01-first-server/README.md) |
| 3.2 | **Перший клієнт** | Налаштування базового клієнта за допомогою MCP, розуміння взаємодії клієнт-сервер, тестування клієнта | [Перший клієнт](./03-GettingStarted/02-client/README.md) |
| 3.3 | **Клієнт з LLM** | Налаштування клієнта з використанням MCP та великої мовної моделі (LLM) | [Клієнт з LLM](./03-GettingStarted/03-llm-client/README.md) |
| 3.4 | **Використання сервера у Visual Studio Code** | Налаштування Visual Studio Code для роботи з серверами через MCP | [Використання сервера у Visual Studio Code](./03-GettingStarted/04-vscode/README.md) |
| 3.5 | **Створення сервера за допомогою SSE** | SSE допомагає зробити сервер доступним в інтернеті. Цей розділ допоможе створити сервер із використанням SSE | [Створення сервера за допомогою SSE](./03-GettingStarted/05-sse-server/README.md) |
| 3.6 | **HTTP-стрімінг** | Навчіться реалізовувати HTTP-стрімінг для передачі даних у реальному часі між клієнтами та MCP-серверами | [HTTP-стрімінг](./03-GettingStarted/06-http-streaming/README.md) |
| 3.7 | **Використання AI Toolkit** | AI Toolkit — чудовий інструмент для управління AI і MCP робочими процесами | [Використання AI Toolkit](./03-GettingStarted/07-aitk/README.md) |
| 3.8 | **Тестування вашого сервера** | Тестування — важлива частина розробки. Цей розділ допоможе вам перевірити сервер за допомогою різних інструментів | [Тестування вашого сервера](./03-GettingStarted/08-testing/README.md) |
| 3.9 | **Розгортання сервера** | Як перейти від локальної розробки до продакшн? Цей розділ допоможе розробити та розгорнути сервер | [Розгортання сервера](./03-GettingStarted/09-deployment/README.md) |
| 04 | **Практична реалізація** | Використання SDK на різних мовах, налагодження, тестування та валідація, створення повторно використовуваних шаблонів запитів і робочих процесів | [Практична реалізація](./04-PracticalImplementation/README.md) |
| 05 | **Поглиблені теми MCP** | Багатомодальні AI робочі процеси та розширюваність, безпечні стратегії масштабування, MCP в корпоративних екосистемах | [Поглиблені теми](./05-AdvancedTopics/README.md) |
| 5.1 | **Інтеграція MCP з Azure** | Демонстрація інтеграції з Azure | [Інтеграція MCP з Azure](./05-AdvancedTopics/mcp-integration/README.md) |
| 5.2 | **Багатомодальність** | Показано, як працювати з різними модальностями, такими як зображення та інше | [Багатомодальність](./05-AdvancedTopics/mcp-multi-modality/README.md) |
| 5.3 | **Демонстрація MCP OAuth2** | Мінімальний додаток Spring Boot, що демонструє OAuth2 з MCP як Authorization та Resource Server. Показано безпечне видавання токенів, захищені кінцеві точки, розгортання в Azure Container Apps та інтеграцію з API Management | [Демонстрація MCP OAuth2](./05-AdvancedTopics/mcp-oauth2-demo/README.md) |
| 5.4 | **Кореневі контексти** | Дізнайтеся більше про кореневі контексти та як їх реалізувати | [Кореневі контексти](./05-AdvancedTopics/mcp-root-contexts/README.md) |
| 5.5 | **Маршрутизація** | Вивчіть різні типи маршрутизації | [Маршрутизація](./05-AdvancedTopics/mcp-routing/README.md) |
| 5.6 | **Вибірка (Sampling)** | Навчіться працювати з вибіркою | [Вибірка](./05-AdvancedTopics/mcp-sampling/README.md) |
| 5.7 | **Масштабування** | Дізнайтеся про масштабування MCP-серверів, включно з горизонтальним і вертикальним масштабуванням, оптимізацією ресурсів та налаштуванням продуктивності | [Масштабування](./05-AdvancedTopics/mcp-scaling/README.md) |
| 5.8 | **Безпека** | Захистіть свій MCP сервер, включно з автентифікацією, авторизацією та стратегіями захисту даних | [Безпека](./05-AdvancedTopics/mcp-security/README.md) |
| 5.9 | **Web Search MCP** | MCP сервер і клієнт на Python, інтегровані з SerpAPI для пошуку в реальному часі у вебі, новинах, продуктах і Q&A. Демонструє оркестрацію кількох інструментів, інтеграцію зовнішніх API та надійну обробку помилок | [Web Search MCP](./05-AdvancedTopics/web-search-mcp/README.md) |
| 5.10 | **Потокова передача даних у реальному часі** | Потокова передача даних у реальному часі стала необхідністю в сучасному світі, де бізнеси та додатки потребують миттєвого доступу до інформації для прийняття своєчасних рішень | [Потокова передача даних у реальному часі](./05-AdvancedTopics/mcp-realtimestreaming/README.md) |
| 5.11 | **Пошук у вебі в реальному часі** | Як MCP змінює пошук у вебі в реальному часі, забезпечуючи стандартизований підхід до управління контекстом між AI-моделями, пошуковими системами та додатками | [Пошук у вебі в реальному часі](./05-AdvancedTopics/mcp-realtimesearch/README.md) |
| 06 | **Внесок спільноти** | Як долучатися до розробки коду та документації, співпраця через GitHub, покращення та відгуки від спільноти | [Внесок спільноти](./06-CommunityContributions/README.md) |
| 07 | **Висновки з раннього впровадження** | Реальні впровадження та що спрацювало, створення та розгортання рішень на базі MCP, тренди та майбутня дорожня карта | [Insights](./07-LessonsFromEarlyAdoption/README.md) |
| 08 | **Кращі практики для MCP** | Налаштування продуктивності та оптимізація, проєктування відмовостійких систем MCP, стратегії тестування та стійкості | [Best Practices](./08-BestPractices/README.md) |
| 09 | **Кейси MCP** | Детальний аналіз архітектур рішень MCP, шаблони розгортання та поради з інтеграції, анотовані діаграми та покрокові огляди проєктів | [Case Studies](./09-CaseStudy/README.md) |
| 10 | **Оптимізація AI-процесів: створення MCP-сервера з AI Toolkit** | Всеохопний практичний семінар, що поєднує MCP з AI Toolkit від Microsoft для VS Code. Навчіться створювати інтелектуальні додатки, які поєднують AI-моделі з реальними інструментами через практичні модулі, що охоплюють основи, розробку кастомного сервера та стратегії розгортання в продакшн. | [Hands On Lab](./10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/README.md) |

## Приклади проєктів

### 🧮 Приклади калькуляторів MCP:
<details>
  <summary><strong>Оглянути реалізації коду за мовами</strong></summary>

  - [Приклад MCP-сервера на C#](./03-GettingStarted/samples/csharp/README.md)
  - [Калькулятор MCP на Java](./03-GettingStarted/samples/java/calculator/README.md)
  - [Демо MCP на JavaScript](./03-GettingStarted/samples/javascript/README.md)
  - [MCP-сервер на Python](../../03-GettingStarted/samples/python/mcp_calculator_server.py)
  - [Приклад MCP на TypeScript](./03-GettingStarted/samples/typescript/README.md)

</details>

### 💡 Розширені проєкти калькуляторів MCP:
<details>
  <summary><strong>Оглянути розширені приклади</strong></summary>

  - [Розширений приклад на C#](./04-PracticalImplementation/samples/csharp/README.md)
  - [Приклад контейнерного додатку на Java](./04-PracticalImplementation/samples/java/containerapp/README.md)
  - [Розширений приклад на JavaScript](./04-PracticalImplementation/samples/javascript/README.md)
  - [Складна реалізація на Python](../../04-PracticalImplementation/samples/python/mcp_sample.py)
  - [Приклад контейнера на TypeScript](./04-PracticalImplementation/samples/typescript/README.md)

</details>


## 🎯 Вимоги для вивчення MCP

Щоб максимально ефективно використовувати цей курс, вам знадобиться:

- Базові знання C#, Java або Python  
- Розуміння клієнт-серверної моделі та API  
- (Опційно) Знайомство з концепціями машинного навчання  

## 📚 Посібник для навчання

Доступний детальний [Посібник для навчання](./study_guide.md), який допоможе вам ефективно орієнтуватися в цьому репозиторії. Посібник включає:

- Візуальну карту курсу з усіма темами  
- Детальний розбір кожного розділу репозиторію  
- Рекомендації щодо використання прикладів проєктів  
- Рекомендовані навчальні шляхи для різних рівнів підготовки  
- Додаткові ресурси для поглибленого вивчення  

## 🛠️ Як ефективно використовувати цей курс

Кожен урок цього посібника містить:

1. Чіткі пояснення концепцій MCP  
2. Живі приклади коду на кількох мовах  
3. Вправи для створення реальних MCP-додатків  
4. Додаткові ресурси для досвідчених користувачів  

## 📜 Ліцензія

Цей контент ліцензований за **MIT License**. Умови можна переглянути в [LICENSE](../../LICENSE).

## 🤝 Правила внеску

Цей проєкт відкритий до внесків і пропозицій. Більшість внесків вимагають вашої згоди з Contributor License Agreement (CLA), яка підтверджує, що ви маєте право і фактично надаєте нам права на використання вашого внеску. Детальніше дивіться на <https://cla.opensource.microsoft.com>.

Коли ви створюєте pull request, бот CLA автоматично визначить, чи потрібно надати CLA, і відповідно позначить PR (наприклад, статусом перевірки, коментарем). Просто дотримуйтесь інструкцій бота. Цю процедуру потрібно пройти лише один раз для всіх репозиторіїв, що використовують нашу CLA.

Цей проєкт прийняв [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/). Для додаткової інформації дивіться [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) або звертайтесь на [opencode@microsoft.com](mailto:opencode@microsoft.com) з будь-якими питаннями чи зауваженнями.

## 🎒 Інші курси  
Наша команда також створює інші курси! Ознайомтесь:

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
- [Опановування GitHub Copilot для спільного програмування з AI](https://aka.ms/GitHubCopilotAI?WT.mc_id=academic-105485-koreyst)
- [Опановування GitHub Copilot для розробників C#/.NET](https://github.com/microsoft/mastering-github-copilot-for-dotnet-csharp-developers?WT.mc_id=academic-105485-koreyst)
- [Виберіть свою пригоду з Copilot](https://github.com/microsoft/CopilotAdventures?WT.mc_id=academic-105485-koreyst)


## ™️ Повідомлення про торговельну марку

Цей проєкт може містити торговельні марки або логотипи проєктів, продуктів чи послуг. Авторизоване використання торговельних марок або логотипів Microsoft регулюється і має відповідати
[Правилам використання торговельних марок і брендів Microsoft](https://www.microsoft.com/legal/intellectualproperty/trademarks/usage/general).
Використання торговельних марок або логотипів Microsoft у змінених версіях цього проєкту не повинно викликати плутанину або створювати враження спонсорства з боку Microsoft.
Використання торговельних марок або логотипів третіх сторін підпорядковується політикам відповідних третіх сторін.

**Відмова від відповідальності**:  
Цей документ був перекладений за допомогою сервісу автоматичного перекладу [Co-op Translator](https://github.com/Azure/co-op-translator). Хоча ми прагнемо до точності, будь ласка, майте на увазі, що автоматичні переклади можуть містити помилки або неточності. Оригінальний документ рідною мовою слід вважати авторитетним джерелом. Для критично важливої інформації рекомендується звертатися до професійного людського перекладу. Ми не несемо відповідальності за будь-які непорозуміння або неправильні тлумачення, що виникли внаслідок використання цього перекладу.