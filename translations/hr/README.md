<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "c7fbf0cdaa44b3245daff0c8bb4f439e",
  "translation_date": "2025-06-11T16:29:42+00:00",
  "source_file": "README.md",
  "language_code": "hr"
}
-->
![MCP-for-beginners](../../translated_images/mcp-beginners.2ce2b317996369ff66c5b72e25eff9d4288ab2741fc70c0b4e523d1ae1e249fd.hr.png) 

[![GitHub contributors](https://img.shields.io/github/contributors/microsoft/mcp-for-beginners.svg)](https://GitHub.com/microsoft/mcp-for-beginners/graphs/contributors)
[![GitHub issues](https://img.shields.io/github/issues/microsoft/mcp-for-beginners.svg)](https://GitHub.com/microsoft/mcp-for-beginners/issues)
[![GitHub pull-requests](https://img.shields.io/github/issues-pr/microsoft/mcp-for-beginners.svg)](https://GitHub.com/microsoft/mcp-for-beginners/pulls)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)

[![GitHub watchers](https://img.shields.io/github/watchers/microsoft/mcp-for-beginners.svg?style=social&label=Watch)](https://GitHub.com/microsoft/mcp-for-beginners/watchers)
[![GitHub forks](https://img.shields.io/github/forks/microsoft/mcp-for-beginners.svg?style=social&label=Fork)](https://GitHub.com/microsoft/mcp-for-beginners/fork)
[![GitHub stars](https://img.shields.io/github/stars/microsoft/mcp-for-beginners?style=social&label=Star)](https://GitHub.com/microsoft/mcp-for-beginners/stargazers)


[![Microsoft Azure AI Foundry Discord](https://dcbadge.vercel.app/api/server/ByRwuEEgH4)](https://discord.com/invite/ByRwuEEgH4)


Slijedite ove korake da biste započeli s korištenjem ovih resursa:
1. **Forkajte repozitorij**: Kliknite [![GitHub forks](https://img.shields.io/github/forks/microsoft/mcp-for-beginners.svg?style=social&label=Fork)](https://GitHub.com/microsoft/mcp-for-beginners/fork)
2. **Klonirajte repozitorij**:   `git clone https://github.com/microsoft/mcp-for-beginners.git`
3. [**Pridružite se Azure AI Foundry Discordu i upoznajte stručnjake i druge developere**](https://discord.com/invite/ByRwuEEgH4)


### 🌐 Višejezična podrška

#### Podržano putem GitHub Action (Automatski i uvijek ažurirano)

# 🚀 Model Context Protocol (MCP) Kurikulum za početnike

## **Naučite MCP kroz praktične primjere koda u C#, Java, JavaScript, Python i TypeScript**

## 🧠 Pregled Model Context Protocol kurikuluma

**Model Context Protocol (MCP)** je napredni okvir osmišljen za standardizaciju interakcija između AI modela i klijentskih aplikacija. Ovaj open-source kurikulum nudi strukturirani put učenja, sa praktičnim primjerima koda i stvarnim slučajevima upotrebe, na popularnim programskim jezicima poput C#, Java, JavaScript, TypeScript i Python.

Bilo da ste AI developer, sistemski arhitekt ili softverski inženjer, ovaj vodič je vaš sveobuhvatni resurs za savladavanje osnova MCP-a i strategija implementacije.

## 🔗 Službeni MCP resursi

- 📘 [MCP Dokumentacija](https://modelcontextprotocol.io/) – Detaljni tutorijali i korisnički vodiči  
- 📜 [MCP Specifikacija](https://spec.modelcontextprotocol.io/) – Arhitektura protokola i tehničke reference  
- 🧑‍💻 [MCP GitHub repozitorij](https://github.com/modelcontextprotocol) – Open-source SDK-ovi, alati i primjeri koda  

## 🧭 Struktura kompletnog MCP kurikuluma

| Ch | Naslov | Opis | Link |
|--|--|--|--|
| 00 | **Uvod u MCP** | Pregled Model Context Protokola i njegova važnost u AI procesima, uključujući što je Model Context Protocol, zašto je standardizacija bitna te praktične primjere i koristi | [Uvod](./00-Introduction/README.md) |
| 01 | **Objašnjeni osnovni pojmovi** | Detaljno objašnjenje osnovnih pojmova MCP-a, uključujući klijent-server arhitekturu, ključne komponente protokola i obrasce poruka | [Osnovni pojmovi](./01-CoreConcepts/README.md) |
| 02 | **Sigurnost u MCP-u** | Identifikacija sigurnosnih prijetnji unutar sustava baziranih na MCP-u, tehnike i najbolje prakse za osiguranje implementacija | [Sigurnost](/02-Security/README.md) |
| 03 | **Početak rada s MCP-om** | Postavljanje okruženja i konfiguracija, kreiranje osnovnih MCP servera i klijenata, integracija MCP-a s postojećim aplikacijama | [Početak rada](./03-GettingStarted/README.md) |
| 3.1 | **Prvi server** | Postavljanje osnovnog servera koristeći MCP protokol, razumijevanje interakcije server-klijent i testiranje servera | [Prvi server](./03-GettingStarted/01-first-server/README.md) |
| 3.2 | **Prvi klijent**  | Postavljanje osnovnog klijenta koristeći MCP protokol, razumijevanje interakcije klijent-server i testiranje klijenta | [Prvi klijent](./03-GettingStarted/02-client/README.md) |
| 3.3 | **Klijent s LLM-om**  | Postavljanje klijenta koristeći MCP protokol s velikim jezičnim modelom (LLM) | [Klijent s LLM-om](./03-GettingStarted/03-llm-client/README.md) |
| 3.4 | **Korištenje servera u Visual Studio Code-u** | Postavljanje Visual Studio Code-a za korištenje servera putem MCP protokola | [Korištenje servera u Visual Studio Code-u](./03-GettingStarted/04-vscode/README.md) |
| 3.5 | **Kreiranje servera koristeći SSE** | SSE nam pomaže izložiti server internetu. Ovaj dio će vam pomoći da napravite server koristeći SSE | [Kreiranje servera koristeći SSE](./03-GettingStarted/05-sse-server/README.md) |
| 3.6 | **Korištenje AI Toolkit-a** | AI toolkit je odličan alat koji će vam pomoći u upravljanju AI i MCP radnim tokovima. | [Korištenje AI Toolkit-a](./03-GettingStarted/06-aitk/README.md) |
| 3.7 | **Testiranje vašeg servera** | Testiranje je važan dio razvojnog procesa. Ovaj dio će vam pomoći da koristite nekoliko različitih alata za testiranje. | [Testiranje vašeg servera](./03-GettingStarted/07-testing/README.md) |
| 3.8 | **Deploy vašeg servera** | Kako preći iz lokalnog razvoja u produkciju? Ovaj dio će vam pomoći da razvijete i postavite vaš server. | [Deploy vašeg servera](./03-GettingStarted/08-deployment/README.md) |
| 04 | **Praktična implementacija** | Korištenje SDK-ova na različitim jezicima, debugiranje, testiranje i validacija, izrada ponovo upotrebljivih predložaka i radnih tokova | [Praktična implementacija](./04-PracticalImplementation/README.md) |
| 05 | **Napredne teme u MCP-u** | Višemodalni AI radni tokovi i proširivost, sigurnosne strategije skaliranja, MCP u enterprise okruženjima | [Napredne teme](./05-AdvancedTopics/README.md) |
| 5.1 | **Integracija MCP-a s Azure-om** | Prikazuje integraciju s Azure-om | [Integracija MCP-a s Azure-om](./05-AdvancedTopics/mcp-integration/README.md) |
| 5.2 | **Višemodalnost** | Prikazuje rad s različitim modalitetima poput slika i drugih | [Višemodalnost](./05-AdvancedTopics/mcp-multi-modality/README.md) |
| 5.3 | **MCP OAuth2 Demo** | Minimalna Spring Boot aplikacija koja pokazuje OAuth2 s MCP-om, kao Authorization i Resource Server. Demonstrira sigurno izdavanje tokena, zaštićene endpoint-e, deployment na Azure Container Apps i integraciju s API Managementom. | [MCP OAuth2 Demo](./05-AdvancedTopics/mcp-oauth2-demo/README.md) |
| 5.4 | **Root Contexts** | Saznajte više o root contextu i kako ih implementirati | [Root Contexts](./05-AdvancedTopics/mcp-root-contexts/README.md) |
| 5.5 | **Routing** | Naučite različite vrste rutiranja | [Routing](./05-AdvancedTopics/mcp-routing/README.md) |
| 5.6 | **Sampling** | Naučite kako raditi s samplingom | [Sampling](./05-AdvancedTopics/mcp-sampling/README.md) |
| 5.7 | **Scaling** | Naučite o skaliranju MCP servera, uključujući horizontalne i vertikalne strategije skaliranja, optimizaciju resursa i podešavanje performansi | [Scaling](./05-AdvancedTopics/mcp-scaling/README.md) |
| 5.8 | **Sigurnost** | Osigurajte svoj MCP server, uključujući strategije autentikacije, autorizacije i zaštite podataka | [Sigurnost](./05-AdvancedTopics/mcp-security/README.md) |
| 5.9 | **Web Search MCP** | Python MCP server i klijent integrirani sa SerpAPI za pretraživanje weba, vijesti, proizvoda i Q&A u realnom vremenu. Demonstrira orkestraciju više alata, integraciju vanjskih API-ja i robusno rukovanje greškama | [Web Search MCP](./05-AdvancedTopics/web-search-mcp/README.md) |
| 5.10 | **Realtime Streaming** | Streaming podataka u realnom vremenu postao je ključan u današnjem svijetu vođenom podacima, gdje tvrtke i aplikacije trebaju trenutni pristup informacijama za pravovremene odluke.| [Realtime Streaming](./05-AdvancedTopics/mcp-realtimestreaming/README.md) |
| 06 | **Doprinosi zajednice** | Kako doprinijeti kodom i dokumentacijom, suradnja preko GitHub-a, poboljšanja i povratne informacije vođene zajednicom | [Doprinosi zajednice](./06-CommunityContributions/README.md) |
| 07 | **Uvidi iz ranog usvajanja** | Stvarne implementacije i što je uspjelo, izgradnja i postavljanje rješenja baziranih na MCP-u, trendovi i budući planovi | [Uvidi](./07-LessonsFromEarlyAdoption/README.md) |
| 08 | **Najbolje prakse za MCP** | Podešavanje performansi i optimizacija, dizajn otpornog MCP sustava, strategije testiranja i otpornosti | [Najbolje prakse](./08-BestPractices/README.md) |
| 09 | **MCP Studije slučaja** | Detaljni uvidi u MCP arhitekture rješenja, planove implementacije i savjete za integraciju, komentirani dijagrami i prikazi projekata | [Case Studies](./09-CaseStudy/README.md) |
| 10 | **Optimizacija AI radnih tokova: Izgradnja MCP servera s AI Toolkitom** | Sveobuhvatna praktična radionica koja kombinira MCP s Microsoftovim AI Toolkitom za VS Code. Naučite kako izgraditi inteligentne aplikacije koje povezuju AI modele s alatima iz stvarnog svijeta kroz praktične module koji pokrivaju osnove, razvoj prilagođenog servera i strategije produkcijske implementacije. | [Hands On Lab](./10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/README.md) |

## Primjerni projekti

### 🧮 MCP Calculator primjerni projekti:
<details>
  <summary><strong>Istražite implementacije koda po jeziku</strong></summary>

  - [C# MCP Server primjer](./03-GettingStarted/samples/csharp/README.md)
  - [Java MCP Calculator](./03-GettingStarted/samples/java/calculator/README.md)
  - [JavaScript MCP demo](./03-GettingStarted/samples/javascript/README.md)
  - [Python MCP Server](../../03-GettingStarted/samples/python/mcp_calculator_server.py)
  - [TypeScript MCP primjer](./03-GettingStarted/samples/typescript/README.md)

</details>

### 💡 MCP napredni kalkulator projekti:
<details>
  <summary><strong>Istražite napredne primjere</strong></summary>

  - [Napredni C# primjer](./04-PracticalImplementation/samples/csharp/README.md)
  - [Java Container App primjer](./04-PracticalImplementation/samples/java/containerapp/README.md)
  - [JavaScript napredni primjer](./04-PracticalImplementation/samples/javascript/README.md)
  - [Python složena implementacija](../../04-PracticalImplementation/samples/python/mcp_sample.py)
  - [TypeScript Container primjer](./04-PracticalImplementation/samples/typescript/README.md)

</details>

## 🎯 Preduvjeti za učenje MCP-a

Da biste maksimalno iskoristili ovaj kurikulum, trebali biste imati:

- Osnovno znanje C#, Java ili Python
- Razumijevanje modela klijent-server i API-ja
- (Opcionalno) Poznavanje koncepata strojnog učenja

## 📚 Vodič za učenje

Dostupan je sveobuhvatni [Study Guide](./study_guide.md) koji će vam pomoći da se efikasno snađete u ovom repozitoriju. Vodič uključuje:

- Vizualnu mapu kurikuluma sa svim obuhvaćenim temama
- Detaljan pregled svake sekcije repozitorija
- Upute za korištenje primjernih projekata
- Preporučene putanje učenja za različite razine znanja
- Dodatne resurse za nadopunu vašeg procesa učenja

## 🛠️ Kako učinkovito koristiti ovaj kurikulum

Svaka lekcija u ovom vodiču uključuje:

1. Jasna objašnjenja MCP koncepata  
2. Primjere koda uživo na više jezika  
3. Vježbe za izradu stvarnih MCP aplikacija  
4. Dodatne resurse za napredne učenike  

## 📜 Informacije o licenci

Ovaj sadržaj je licenciran pod **MIT License**. Za uvjete korištenja pogledajte [LICENSE](../../LICENSE).

## 🤝 Smjernice za doprinos

Ovaj projekt pozdravlja doprinose i prijedloge. Većina doprinosa zahtijeva da se složite s Contributor License Agreement (CLA) u kojem potvrđujete da imate pravo i stvarno dajete prava na korištenje vašeg doprinosa. Za detalje posjetite <https://cla.opensource.microsoft.com>.

Kada pošaljete pull request, CLA bot će automatski provjeriti trebate li dostaviti CLA i označiti PR prikladno (npr. status check, komentar). Jednostavno slijedite upute koje daje bot. Ovo je potrebno napraviti samo jednom za sve repozitorije koji koriste naš CLA.

Ovaj projekt je usvojio [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/). Za više informacija pogledajte [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) ili kontaktirajte [opencode@microsoft.com](mailto:opencode@microsoft.com) za dodatna pitanja ili komentare.

## 🎒 Ostali tečajevi
Naš tim proizvodi i druge tečajeve! Pogledajte:

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
- [Mastering GitHub Copilot for AI Paired Programming](https://aka.ms/GitHubCopilotAI?WT.mc_id=academic-105485-koreyst)
- [Mastering GitHub Copilot for C#/.NET Developers](https://github.com/microsoft/mastering-github-copilot-for-dotnet-csharp-developers?WT.mc_id=academic-105485-koreyst)
- [Odaberite svoju vlastitu Copilot avanturu](https://github.com/microsoft/CopilotAdventures?WT.mc_id=academic-105485-koreyst)


## ™️ Obavijest o žigu

Ovaj projekt može sadržavati žigove ili logotipe za projekte, proizvode ili usluge. Ovlaštena upotreba Microsoftovih
žigova ili logotipa podliježe i mora se pridržavati
[Microsoftovih smjernica za žigove i brendiranje](https://www.microsoft.com/legal/intellectualproperty/trademarks/usage/general).
Upotreba Microsoftovih žigova ili logotipa u izmijenjenim verzijama ovog projekta ne smije stvarati zabunu niti implicirati sponzorstvo Microsofta.
Svaka upotreba žigova ili logotipa trećih strana podliježe pravilima tih trećih strana.

**Odricanje od odgovornosti**:  
Ovaj je dokument preveden korištenjem AI usluge za prijevod [Co-op Translator](https://github.com/Azure/co-op-translator). Iako nastojimo postići točnost, imajte na umu da automatski prijevodi mogu sadržavati pogreške ili netočnosti. Izvorni dokument na izvornom jeziku treba smatrati službenim i autoritativnim izvorom. Za kritične informacije preporučuje se profesionalni ljudski prijevod. Ne snosimo odgovornost za bilo kakve nesporazume ili pogrešne interpretacije koje proizlaze iz korištenja ovog prijevoda.