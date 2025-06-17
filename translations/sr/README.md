<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "9a14017adf28f7440f20c2d5e7f1d0f8",
  "translation_date": "2025-06-17T16:14:23+00:00",
  "source_file": "README.md",
  "language_code": "sr"
}
-->
![MCP-za-početnike](../../translated_images/mcp-beginners.2ce2b317996369ff66c5b72e25eff9d4288ab2741fc70c0b4e523d1ae1e249fd.sr.png) 

[![GitHub contributors](https://img.shields.io/github/contributors/microsoft/mcp-for-beginners.svg)](https://GitHub.com/microsoft/mcp-for-beginners/graphs/contributors)
[![GitHub issues](https://img.shields.io/github/issues/microsoft/mcp-for-beginners.svg)](https://GitHub.com/microsoft/mcp-for-beginners/issues)
[![GitHub pull-requests](https://img.shields.io/github/issues-pr/microsoft/mcp-for-beginners.svg)](https://GitHub.com/microsoft/mcp-for-beginners/pulls)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)

[![GitHub watchers](https://img.shields.io/github/watchers/microsoft/mcp-for-beginners.svg?style=social&label=Watch)](https://GitHub.com/microsoft/mcp-for-beginners/watchers)
[![GitHub forks](https://img.shields.io/github/forks/microsoft/mcp-for-beginners.svg?style=social&label=Fork)](https://GitHub.com/microsoft/mcp-for-beginners/fork)
[![GitHub stars](https://img.shields.io/github/stars/microsoft/mcp-for-beginners?style=social&label=Star)](https://GitHub.com/microsoft/mcp-for-beginners/stargazers)


[![Microsoft Azure AI Foundry Discord](https://dcbadge.vercel.app/api/server/ByRwuEEgH4)](https://discord.com/invite/ByRwuEEgH4)


Пратите ове кораке да бисте почели да користите ове ресурсе:
1. **Направите форк репозиторијума**: Кликните [![GitHub forks](https://img.shields.io/github/forks/microsoft/mcp-for-beginners.svg?style=social&label=Fork)](https://GitHub.com/microsoft/mcp-for-beginners/fork)
2. **Клонирајте репозиторијум**:   `git clone https://github.com/microsoft/mcp-for-beginners.git`
3. [**Придружите се Azure AI Foundry Discord-у и упознајте стручњаке и друге програмере**](https://discord.com/invite/ByRwuEEgH4)


### 🌐 Подршка за више језика

#### Подржано преко GitHub Action-а (аутоматски и увек ажурирано)

# 🚀 Наставни план за Model Context Protocol (MCP) за почетнике

## **Учите MCP кроз практичне примере кода у C#, Java, JavaScript, Python и TypeScript**

## 🧠 Преглед наставног плана за Model Context Protocol

**Model Context Protocol (MCP)** је савремени оквир дизајниран да стандардује интеракције између AI модела и клијентских апликација. Овај отворени наставни план нуди структуриран пут учења, са практичним примерима кода и стварним случајевима коришћења, у популарним програмским језицима као што су C#, Java, JavaScript, TypeScript и Python.

Без обзира да ли сте AI програмер, системски архитекта или софтверски инжењер, овај водич је ваш свеобухватни ресурс за савладавање основа MCP и стратегија имплементације.

## 🔗 Званични MCP ресурси

- 📘 [MCP документација](https://modelcontextprotocol.io/) – Детаљни туторијали и кориснички водичи  
- 📜 [MCP спецификација](https://spec.modelcontextprotocol.io/) – Архитектура протокола и техничке референце  
- 🧑‍💻 [MCP GitHub репозиторијум](https://github.com/modelcontextprotocol) – Отворени SDK-ови, алати и примери кода  

## 🧭 Комплетна структура наставног плана MCP

| Чл | Наслов | Опис | Линк |
|--|--|--|--|
| 00 | **Увод у MCP** | Преглед Model Context Protocol и његов значај у AI процесима, укључујући шта је Model Context Protocol, зашто је стандардизација важна и практичне примере коришћења и предности | [Увод](./00-Introduction/README.md) |
| 01 | **Објашњење основних појмова** | Детаљно објашњење основних појмова MCP-а, укључујући архитектуру клијент-сервер, кључне компоненте протокола и шаблоне комуникације | [Основни појмови](./01-CoreConcepts/README.md) |
| 02 | **Безбедност у MCP-у** | Идентификовање безбедносних претњи у системима заснованим на MCP-у, технике и најбоље праксе за обезбеђење имплементација | [Безбедност](./02-Security/README.md) |
| 03 | **Започињање рада са MCP-ом** | Подешавање окружења и конфигурација, креирање основних MCP сервера и клијената, интеграција MCP-а са постојећим апликацијама | [Започињање](./03-GettingStarted/README.md) |
| 3.1 | **Први сервер** | Подешавање основног сервера користећи MCP протокол, разумевање интеракције сервер-клијент и тестирање сервера | [Први сервер](./03-GettingStarted/01-first-server/README.md) |
| 3.2 | **Први клијент** | Подешавање основног клијента користећи MCP протокол, разумевање интеракције клијент-сервер и тестирање клијента | [Први клијент](./03-GettingStarted/02-client/README.md) |
| 3.3 | **Клијент са LLM-ом** | Подешавање клијента користећи MCP протокол са Large Language Model (LLM) | [Клијент са LLM](./03-GettingStarted/03-llm-client/README.md) |
| 3.4 | **Коришћење Visual Studio Code за приступ серверу** | Подешавање Visual Studio Code-а за приступ серверима користећи MCP протокол | [Коришћење Visual Studio Code](./03-GettingStarted/04-vscode/README.md) |
| 3.5 | **Креирање сервера користећи SSE** | SSE нам омогућава да изложимо сервер на интернет. Овај део ће вам помоћи да направите сервер користећи SSE | [Креирање сервера користећи SSE](./03-GettingStarted/05-sse-server/README.md) |
| 3.6 | **HTTP стриминг** | Научите како да имплементирате HTTP стриминг за пренос података у реалном времену између клијената и MCP сервера | [HTTP стриминг](./03-GettingStarted/06-http-streaming/README.md) |
| 3.7 | **Коришћење AI Toolkit-а** | AI toolkit је одличан алат који ће вам помоћи у управљању вашим AI и MCP радним токовима. | [Коришћење AI Toolkit-а](./03-GettingStarted/07-aitk/README.md) |
| 3.8 | **Тестирање вашег сервера** | Тестирање је важан део развојног процеса. Овај део ће вам помоћи да тестирате користећи више различитих алата. | [Тестирање вашег сервера](./03-GettingStarted/08-testing/README.md) |
| 3.9 | **Деплој вашег сервера** | Како прећи са локалног развоја на продукцију? Овај део ће вам помоћи да развијете и деплојујете ваш сервер. | [Деплој вашег сервера](./03-GettingStarted/09-deployment/README.md) |
| 04 | **Практична имплементација** | Коришћење SDK-ова у различитим језицима, дебаговање, тестирање и валидација, израда поновно употребљивих шаблона и радних токова | [Практична имплементација](./04-PracticalImplementation/README.md) |
| 05 | **Напредне теме у MCP-у** | Мултимодални AI радни токови и проширивост, безбедне стратегије скалирања, MCP у предузетничким екосистемима | [Напредне теме](./05-AdvancedTopics/README.md) |
| 5.1 | **Интеграција MCP-а са Azure-ом** | Приказ интеграције са Azure-ом | [Интеграција MCP-а са Azure-ом](./05-AdvancedTopics/mcp-integration/README.md) |
| 5.2 | **Мултимодалност** | Приказ рада са различитим модалитетима као што су слике и други | [Мултимодалност](./05-AdvancedTopics/mcp-multi-modality/README.md) |
| 5.3 | **MCP OAuth2 демонстрација** | Минимална Spring Boot апликација која показује OAuth2 са MCP-ом, и као Authorization и Resource Server. Демонстрира безбедно издавање токена, заштићене крајње тачке, деплој на Azure Container Apps и интеграцију са API Management-ом. | [MCP OAuth2 демонстрација](./05-AdvancedTopics/mcp-oauth2-demo/README.md) |
| 5.4 | **Root Contexts** | Сазнајте више о root context-у и како их имплементирати | [Root Contexts](./05-AdvancedTopics/mcp-root-contexts/README.md) |
| 5.5 | **Роутинг** | Научите различите типове рутирања | [Роутинг](./05-AdvancedTopics/mcp-routing/README.md) |
| 5.6 | **Sampling** | Научите како да радите са sampling-ом | [Sampling](./05-AdvancedTopics/mcp-sampling/README.md) |
| 5.7 | **Скалирање** | Сазнајте о скалирању MCP сервера, укључујући хоризонталне и вертикалне стратегије скалирања, оптимизацију ресурса и подешавање перформанси | [Скалирање](./05-AdvancedTopics/mcp-scaling/README.md) |
| 5.8 | **Безбедност** | Обезбедите ваш MCP сервер, укључујући аутентификацију, ауторизацију и стратегије заштите података | [Безбедност](./05-AdvancedTopics/mcp-security/README.md) |
| 5.9 | **Web Search MCP** | Python MCP сервер и клијент који се интегришу са SerpAPI за претрагу веба, новости, производа и Q&A у реалном времену. Демонстрира мулти-алатску оркестрацију, интеграцију спољних API-ја и робусно руковање грешкама | [Web Search MCP](./05-AdvancedTopics/web-search-mcp/README.md) |
| 5.10 | **Realtime Streaming** | Стриминг података у реалном времену постао је незамењив у данашњем свету вођеном подацима, где предузећа и апликације захтевају тренутан приступ информацијама за правовремене одлуке. | [Realtime Streaming](./05-AdvancedTopics/mcp-realtimestreaming/README.md) |
| 5.11 | **Realtime Web Search** | Како MCP трансформише претрагу веба у реалном времену пружајући стандардизован приступ управљању контекстом између AI модела, претраживача и апликација. | [Realtime Web Search](./05-AdvancedTopics/mcp-realtimesearch/README.md) |
| 06 | **Заједнички доприноси** | Како допринети кодом и документацијом, сарадња преко GitHub-а, побољшања и повратне информације од заједнице | [Заједнички доприноси](./06-CommunityContributions/README.md) |
| 07 | **Увид из ране примене** | Примена у стварном свету и шта је функционисало, развој и имплементација решења заснованих на MCP-у, трендови и будући планови | [Insights](./07-LessonsFromEarlyAdoption/README.md) |
| 08 | **Најбоље праксе за MCP** | Подешавање перформанси и оптимизација, дизајн MCP система отпорних на грешке, стратегије тестирања и отпорности | [Best Practices](./08-BestPractices/README.md) |
| 09 | **MCP студије случаја** | Детаљни прегледи архитектура MCP решења, планови имплементације и савети за интеграцију, коментарисани дијаграми и корак-по-корак пројекти | [Case Studies](./09-CaseStudy/README.md) |
| 10 | **Поједностављивање AI радних токова: Изградња MCP сервера са AI алатима** | Свеобухватна практична радионица која комбинује MCP са Microsoft-овим AI алатима за VS Code. Научите како да направите интелигентне апликације које повезују AI моделе са стварним алатима кроз практичне модуле који обухватају основе, развој прилагођених сервера и стратегије производног издавања. | [Hands On Lab](./10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/README.md) |

## Пример пројеката

### 🧮 Пример MCP калкулатора:
<details>
  <summary><strong>Истражите имплементације кода по језицима</strong></summary>

  - [C# пример MCP сервера](./03-GettingStarted/samples/csharp/README.md)
  - [Java MCP калкулатор](./03-GettingStarted/samples/java/calculator/README.md)
  - [JavaScript MCP демонстрација](./03-GettingStarted/samples/javascript/README.md)
  - [Python MCP сервер](../../03-GettingStarted/samples/python/mcp_calculator_server.py)
  - [TypeScript MCP пример](./03-GettingStarted/samples/typescript/README.md)

</details>

### 💡 Напредни MCP калкулатор пројекти:
<details>
  <summary><strong>Истражите напредне примере</strong></summary>

  - [Напредни C# пример](./04-PracticalImplementation/samples/csharp/README.md)
  - [Java пример апликације у контејнеру](./04-PracticalImplementation/samples/java/containerapp/README.md)
  - [JavaScript напредни пример](./04-PracticalImplementation/samples/javascript/README.md)
  - [Python комплексна имплементација](../../04-PracticalImplementation/samples/python/mcp_sample.py)
  - [TypeScript пример у контејнеру](./04-PracticalImplementation/samples/typescript/README.md)

</details>

## 🎯 Предуслови за учење MCP-а

Да бисте максимално искористили овај програм, требало би да имате:

- Основно знање C#, Java или Python језика
- Разумевање клијент-сервер модела и API-ја
- (Опционо) Познавање концепата машинског учења

## 📚 Водич за учење

Доступан је свеобухватан [Водич за учење](./study_guide.md) који ће вам помоћи да ефикасно користите овај репозиторијум. Водич укључује:

- Визуелну мапу курикулума са свим обрађеним темама
- Детаљан преглед сваког дела репозиторијума
- Упутства за коришћење пример пројеката
- Препоручене путеве учења за различите нивое знања
- Додатне ресурсе који ће употпунити ваш процес учења

## 🛠️ Како ефикасно користити овај курикулум

Свака лекција у овом водичу садржи:

1. Јасна објашњења MCP концепата  
2. Примере кода уживо на више језика  
3. Вежбе за развој стварних MCP апликација  
4. Додатне ресурсе за напредне ученике  

## 📜 Лиценца

Овај садржај је лиценциран под **MIT лиценцом**. За услове коришћења погледајте [LICENSE](../../LICENSE).

## 🤝 Упутства за допринос

Овај пројекат поздравља доприносе и предлоге. Већина доприноса захтева да се сложите са
Уговором о лиценци за сараднике (CLA) у коме изјављујете да имате право и заиста нам дајете
права да користимо ваш допринос. За детаље посетите <https://cla.opensource.microsoft.com>.

Када пошаљете pull request, CLA бот ће аутоматски одредити да ли треба да доставите
CLA и означити PR на одговарајући начин (нпр. провера статуса, коментар). Само пратите упутства
која вам бот даје. Ово ћете морати урадити само једном за све репозиторијуме који користе наш CLA.

Овај пројекат је усвојио [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
За више информација погледајте [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) или
контактирајте [opencode@microsoft.com](mailto:opencode@microsoft.com) за додатна питања или коментаре.

## 🎒 Остали курсеви
Наш тим прави и друге курсеве! Погледајте:

- [AI агенти за почетнике](https://github.com/microsoft/ai-agents-for-beginners?WT.mc_id=academic-105485-koreyst)
- [Генеративни AI за почетнике уз .NET](https://github.com/microsoft/Generative-AI-for-beginners-dotnet?WT.mc_id=academic-105485-koreyst)
- [Генеративни AI за почетнике уз JavaScript](https://github.com/microsoft/generative-ai-with-javascript?WT.mc_id=academic-105485-koreyst)
- [Генеративни AI за почетнике](https://github.com/microsoft/generative-ai-for-beginners?WT.mc_id=academic-105485-koreyst)
- [ML за почетнике](https://aka.ms/ml-beginners?WT.mc_id=academic-105485-koreyst)
- [Data Science за почетнике](https://aka.ms/datascience-beginners?WT.mc_id=academic-105485-koreyst)
- [AI за почетнике](https://aka.ms/ai-beginners?WT.mc_id=academic-105485-koreyst)
- [Cybersecurity за почетнике](https://github.com/microsoft/Security-101??WT.mc_id=academic-96948-sayoung)
- [Web Development за почетнике](https://aka.ms/webdev-beginners?WT.mc_id=academic-105485-koreyst)
- [IoT за почетнике](https://aka.ms/iot-beginners?WT.mc_id=academic-105485-koreyst)
- [XR развој за почетнике](https://github.com/microsoft/xr-development-for-beginners?WT.mc_id=academic-105485-koreyst)
- [Мастеринг GitHub Copilot-а за AI парско програмирање](https://aka.ms/GitHubCopilotAI?WT.mc_id=academic-105485-koreyst)
- [Мастеринг GitHub Copilot-а за C#/.NET програмере](https://github.com/microsoft/mastering-github-copilot-for-dotnet-csharp-developers?WT.mc_id=academic-105485-koreyst)
- [Изаберите своју Copilot авантуру](https://github.com/microsoft/CopilotAdventures?WT.mc_id=academic-105485-koreyst)


## ™️ Обавештење о трговачкој марки

Овај пројекат може да садржи трговачке марке или логотипе пројеката, производа или услуга. Овлашћена употреба Microsoft трговачких марки или логотипа подлеже и мора да се придржава  
[Microsoft-ових смерница за трговачке марке и бренд](https://www.microsoft.com/legal/intellectualproperty/trademarks/usage/general).  
Употреба Microsoft трговачких марки или логотипа у модификованим верзијама овог пројекта не сме да доведе до забуне нити да имплицира да Microsoft спонзорише пројекат.  
Свака употреба трговачких марки или логотипа трећих страна подлеже правилима тих трећих страна.

**Одрицање одговорности**:  
Овај документ је преведен коришћењем АИ услуге за превођење [Co-op Translator](https://github.com/Azure/co-op-translator). Иако тежимо тачности, молимо вас да имате у виду да аутоматски преводи могу садржати грешке или нетачности. Изворни документ на његовом оригиналном језику треба сматрати ауторитетним извором. За критичне информације препоручује се професионални људски превод. Нисмо одговорни за било какве неспоразуме или погрешне тумачења која произилазе из коришћења овог превода.