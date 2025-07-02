<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "292f96c64f54ba097daea9598111ed82",
  "translation_date": "2025-07-02T05:48:30+00:00",
  "source_file": "README.md",
  "language_code": "sr"
}
-->
![MCP-for-beginners](../../translated_images/mcp-beginners.2ce2b317996369ff66c5b72e25eff9d4288ab2741fc70c0b4e523d1ae1e249fd.sr.png) 

[![GitHub contributors](https://img.shields.io/github/contributors/microsoft/mcp-for-beginners.svg)](https://GitHub.com/microsoft/mcp-for-beginners/graphs/contributors)
[![GitHub issues](https://img.shields.io/github/issues/microsoft/mcp-for-beginners.svg)](https://GitHub.com/microsoft/mcp-for-beginners/issues)
[![GitHub pull-requests](https://img.shields.io/github/issues-pr/microsoft/mcp-for-beginners.svg)](https://GitHub.com/microsoft/mcp-for-beginners/pulls)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)

[![GitHub watchers](https://img.shields.io/github/watchers/microsoft/mcp-for-beginners.svg?style=social&label=Watch)](https://GitHub.com/microsoft/mcp-for-beginners/watchers)
[![GitHub forks](https://img.shields.io/github/forks/microsoft/mcp-for-beginners.svg?style=social&label=Fork)](https://GitHub.com/microsoft/mcp-for-beginners/fork)
[![GitHub stars](https://img.shields.io/github/stars/microsoft/mcp-for-beginners?style=social&label=Star)](https://GitHub.com/microsoft/mcp-for-beginners/stargazers)


[![Microsoft Azure AI Foundry Discord](https://dcbadge.limes.pink/api/server/ByRwuEEgH4)](https://discord.com/invite/ByRwuEEgH4)

Пратите ове кораке да бисте почели да користите ове ресурсе:
1. **Направите форк репозиторијума**: Кликните на [![GitHub forks](https://img.shields.io/github/forks/microsoft/mcp-for-beginners.svg?style=social&label=Fork)](https://GitHub.com/microsoft/mcp-for-beginners/fork)
2. **Клонирајте репозиторијум**:   `git clone https://github.com/microsoft/mcp-for-beginners.git`
3. [**Придружите се Azure AI Foundry Discord-у и упознајте експерте и друге програмере**](https://discord.com/invite/ByRwuEEgH4)


### 🌐 Подршка за више језика

#### Подржано преко GitHub Action-а (аутоматски и увек ажурирано)

# 🚀 Наставни план за Model Context Protocol (MCP) за почетнике

## **Учите MCP кроз практичне примере кода у C#, Java, JavaScript, Python и TypeScript**

## 🧠 Преглед наставног плана за Model Context Protocol

**Model Context Protocol (MCP)** је савремени оквир дизајниран да стандардује интеракције између AI модела и клијент апликација. Овај отворени наставни план нуди структуриран пут учења, са практичним примерима кода и стварним примерима коришћења, у популарним програмским језицима као што су C#, Java, JavaScript, TypeScript и Python.

Без обзира да ли сте AI програмер, системски архитекта или софтверски инжењер, овај водич је ваш свеобухватни ресурс за савладавање основа MCP-а и стратегија имплементације.

## 🔗 Званични MCP ресурси

- 📘 [MCP Documentation](https://modelcontextprotocol.io/) – Детаљни туторијали и кориснички приручници  
- 📜 [MCP Specification](https://spec.modelcontextprotocol.io/) – Архитектура протокола и техничке референце  
- 🧑‍💻 [MCP GitHub Repository](https://github.com/modelcontextprotocol) – Отворени SDK-ови, алати и примерци кода  

## 🧭 Преглед наставног плана MCP

### Основе Model Context Protocol-а  
<details>
  <summary><strong> Лекције 1-3: Основе Model Context Protocol-а</strong></summary>

- **00. Увод у MCP**  
  Преглед Model Context Protocol-а и његов значај у AI процесима. [Прочитај више](./00-Introduction/README.md)
- **01. Објашњење кључних појмова**  
  Детаљно објашњење основних концепата MCP-а. [Прочитај више](./01-CoreConcepts/README.md)
- **02. Безбедност у MCP-у**  
  Безбедносне претње и најбоље праксе. [Прочитај више](./02-Security/README.md)
- **03. Почетак рада са MCP-ом**  
  Подешавање окружења, основни сервери/клијенти, интеграција. [Прочитај више](./03-GettingStarted/README.md)
</details>

### Креирање и покретање првог MCP сервера и клијента и практичне вежбе и сценарији  
<details>
  <summary><strong> Лекција 3: Креирање и покретање првог MCP сервера и клијента</strong></summary>

- **3.1. Први сервер** – [Водич](./03-GettingStarted/01-first-server/README.md)
- **3.2. Први клијент** – [Водич](./03-GettingStarted/02-client/README.md)
- **3.3. Клијент са LLM-ом** – [Водич](./03-GettingStarted/03-llm-client/README.md)
- **3.4. Коришћење сервера у Visual Studio Code-у** – [Водич](./03-GettingStarted/04-vscode/README.md)
- **3.5. Креирање сервера коришћењем SSE-а** – [Водич](./03-GettingStarted/05-sse-server/README.md)
- **3.6. HTTP стриминг** – [Водич](./03-GettingStarted/06-http-streaming/README.md)
- **3.7. Коришћење AI Toolkit-а** – [Водич](./03-GettingStarted/07-aitk/README.md)
- **3.8. Тестирање вашег сервера** – [Водич](./03-GettingStarted/08-testing/README.md)
- **3.9. Деплојовање сервера** – [Водич](./03-GettingStarted/09-deployment/README.md)
</details>

### Практичне имплементације и напредне теме Model Context Protocol-а  
<details>
  <summary><strong> Лекције 4-5: Практично и напредно</strong></summary>

- **04. Практична имплементација**  
  SDK-ови, дебаговање, тестирање, поновно употребљиви шаблони за упите. [Прочитај више](./04-PracticalImplementation/README.md)
- **05. Напредне теме у MCP-у**  
  Мултимодални AI, скалабилност, коришћење у предузећима. [Прочитај више](./05-AdvancedTopics/README.md)
- **5.1. MCP интеграција са Azure-ом** – [Водич](./05-AdvancedTopics/mcp-integration/README.md)
- **5.2. Мултимодалност** – [Водич](./05-AdvancedTopics/mcp-multi-modality/README.md)
- **5.3. MCP OAuth2 демо** – [Водич](./05-AdvancedTopics/mcp-oauth2-demo/README.md)
- **5.4. Root Contexts** – [Водич](./05-AdvancedTopics/mcp-root-contexts/README.md)
- **5.5. Routing** – [Водич](./05-AdvancedTopics/mcp-routing/README.md)
- **5.6. Sampling** – [Водич](./05-AdvancedTopics/mcp-sampling/README.md)
- **5.7. Scaling** – [Водич](./05-AdvancedTopics/mcp-scaling/README.md)
- **5.8. Security** – [Водич](./05-AdvancedTopics/mcp-security/README.md)
- **5.9. Web Search MCP** – [Водич](./05-AdvancedTopics/web-search-mcp/README.md)
- **5.10. Realtime Streaming** – [Водич](./05-AdvancedTopics/mcp-realtimestreaming/README.md)
- **5.11. Realtime Web Search** – [Водич](./05-AdvancedTopics/mcp-realtimesearch/README.md)
- **5.12. Entra ID Authentication за Model Context Protocol сервере** – [Водич](./05-AdvancedTopics/mcp-security-entra/README.md)
</details>

### Најбоље праксе за Model Context Protocol  
<details>
  <summary><strong> Лекције 6-9: Заједница, најбоље праксе и лабораторијске вежбе</strong></summary>
- **06. Дoprинoси заједнице** – [Водич](./06-CommunityContributions/README.md)
- **07. Увид из ране примене** – [Водич](./07-LessonsFromEarlyAdoption/README.md)
- **08. Најбоље праксе за MCP** – [Водич](./08-BestPractices/README.md)
- **09. Студије случаја MCP** – [Водич](./09-CaseStudy/README.md)
</details>

### Model Context Protocol Практични рад са AI Toolkit за VScode
<details>
  <summary><strong>Лекција 10: Практични рад на изградњи MCP сервера са AI Toolkit за VScode </summary>
    
- **10. Поједностављивање AI радних токова: изградња MCP сервера са AI Toolkit** – [Практични рад](./10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/README.md)
</details>

## Model Context Protocol Пример пројеката: Изградња MCP калкулатора у Java, C#, JavaScript, TypeScript и Python

### 🧮 Пример MCP калкулатора у Java, C#, JavaScript, TypeScript и Python
<details>
  <summary><strong>Истражите имплементације кода по језику</strong></summary>

  - [C# пример MCP сервера](./03-GettingStarted/samples/csharp/README.md)
  - [Java MCP калкулатор](./03-GettingStarted/samples/java/calculator/README.md)
  - [JavaScript MCP демонстрација](./03-GettingStarted/samples/javascript/README.md)
  - [Python MCP сервер](../../03-GettingStarted/samples/python/mcp_calculator_server.py)
  - [TypeScript MCP пример](./03-GettingStarted/samples/typescript/README.md)

</details>

### 💡 Напредно MCP решење: Калкулатор пројекти у C#, Java, JavaScript, TypeScript и Python
<details>
  <summary><strong>Истражите напредне примере</strong></summary>

  - [Напредни C# пример](./04-PracticalImplementation/samples/csharp/README.md)
  - [Java пример апликације у контејнеру](./04-PracticalImplementation/samples/java/containerapp/README.md)
  - [JavaScript напредни пример](./04-PracticalImplementation/samples/javascript/README.md)
  - [Python комплексна имплементација](../../04-PracticalImplementation/samples/python/mcp_sample.py)
  - [TypeScript пример у контејнеру](./04-PracticalImplementation/samples/typescript/README.md)

</details>


## 🎯 Претпоставке за учење MCP

Да бисте извукли максимум из овог курикулума, требало би да имате:

- Основно знање C#, Java или Python
- Разумевање клијент-сервер модела и API-ја
- (Опционо) Познавање концепата машинског учења

## 📚 Водич за учење

Доступан је свеобухватан [Водич за учење](./study_guide.md) који ће вам помоћи да ефикасно користите овај репозиторијум. Водич укључује:

- Визуелну мапу курикулума са свим обрађеним темама
- Детаљан преглед сваког дела репозиторијума
- Упутства за коришћење пример пројеката
- Препоручене путеве учења за различите нивое знања
- Додатне ресурсе који ће употпунити ваше учење

## 🛠️ Како ефикасно користити овај курикулум

Свака лекција у овом водичу укључује:

1. Јасна објашњења MCP концепата  
2. Примере кода уживо на више језика  
3. Вежбе за изградњу стварних MCP апликација  
4. Додатне ресурсе за напредне ученике


## 🌟 Захвалност заједници

Захваљујемо Microsoft Valued Professional [Shivam Goyal](https://www.linkedin.com/in/shivam2003/) на доприносу важних примера кода.

## 📜 Информације о лиценци

Овај садржај је лиценциран под **MIT лиценцом**. За услове коришћења погледајте [LICENSE](../../LICENSE).

## 🤝 Упутства за допринос

Овај пројекат поздравља доприносе и предлоге. Већина доприноса захтева да се сложите са
Уговором о лиценцирању доприноса (CLA) у коме потврђујете да имате право и заиста нам дајете
права за коришћење вашег доприноса. За детаље посетите <https://cla.opensource.microsoft.com>.

Када пошаљете pull request, CLA бот ће аутоматски одредити да ли морате да доставите
CLA и одговарајуће означити PR (нпр. провера статуса, коментар). Само пратите упутства
која даје бот. Ово морате урадити само једном за све репозиторијуме који користе наш CLA.

Овај пројекат је усвојио [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
За више информација погледајте [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) или
контактирајте [opencode@microsoft.com](mailto:opencode@microsoft.com) за додатна питања или коментаре.

## 🎒 Остали курсеви
Наш тим производи и друге курсеве! Погледајте:

- [AI Agents For Beginners](https://github.com/microsoft/ai-agents-for-beginners?WT.mc_id=academic-105485-koreyst)
- [Generative AI for Beginners using .NET](https://github.com/microsoft/Generative-AI-for-beginners-dotnet?WT.mc_id=academic-105485-koreyst)
- [Generative AI for Beginners using JavaScript](https://github.com/microsoft/generative-ai-with-javascript?WT.mc_id=academic-105485-koreyst)
- [Generative AI for Beginners](https://github.com/microsoft/generative-ai-for-beginners?WT.mc_id=academic-105485-koreyst)
- [ML for Beginners](https://aka.ms/ml-beginners?WT.mc_id=academic-105485-koreyst)
- [Data Science for Beginners](https://aka.ms/datascience-beginners?WT.mc_id=academic-105485-koreyst)
- [AI for Beginners](https://aka.ms/ai-beginners?WT.mc_id=academic-105485-koreyst)
- [Cybersecurity for Beginners](https://github.com/microsoft/Security-101??WT.mc_id=academic-96948-sayoung)
- [Web Dev for Beginners](https://aka.ms/webdev-beginners?WT.mc_id=academic-105485-koreyst)
- [Интернет ствари за почетнике](https://aka.ms/iot-beginners?WT.mc_id=academic-105485-koreyst)
- [XR развој за почетнике](https://github.com/microsoft/xr-development-for-beginners?WT.mc_id=academic-105485-koreyst)
- [Мастеринг GitHub Copilot за AI парско програмирање](https://aka.ms/GitHubCopilotAI?WT.mc_id=academic-105485-koreyst)
- [Мастеринг GitHub Copilot за C#/.NET програмере](https://github.com/microsoft/mastering-github-copilot-for-dotnet-csharp-developers?WT.mc_id=academic-105485-koreyst)
- [Изабери своју Copilot авантуру](https://github.com/microsoft/CopilotAdventures?WT.mc_id=academic-105485-koreyst)


## ™️ Обавештење о жигу

Овај пројекат може садржати жигове или логотипе за пројекте, производе или услуге. Овлашћена употреба Microsoft
жигова или логотипа подлеже и мора бити у складу са
[Microsoft-овим смерницама за жигове и бренд](https://www.microsoft.com/legal/intellectualproperty/trademarks/usage/general).
Употреба Microsoft жигова или логотипа у измењеним верзијама овог пројекта не сме изазивати конфузију нити имплицирати спонзорство од стране Microsoft-а.
Свака употреба жигова или логотипа трећих страна подлеже правилима тих трећих страна.

**Одрицање од одговорности**:  
Овај документ је преведен коришћењем АИ услуге за превођење [Co-op Translator](https://github.com/Azure/co-op-translator). Иако се трудимо да превод буде тачан, имајте у виду да аутоматизовани преводи могу садржати грешке или нетачности. Оригинални документ на његовом изворном језику треба сматрати ауторитетним извором. За критичне информације препоручује се професионални људски превод. Нисмо одговорни за било каква неспоразума или погрешна тумачења настала употребом овог превода.