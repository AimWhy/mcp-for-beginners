<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "4458d89100952180348d8775b149295e",
  "translation_date": "2025-06-02T19:37:21+00:00",
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
1. **Forkajte spremište**: Kliknite [![GitHub forks](https://img.shields.io/github/forks/microsoft/mcp-for-beginners.svg?style=social&label=Fork)](https://GitHub.com/microsoft/mcp-for-beginners/fork)
2. **Klonirajte spremište**:   `git clone https://github.com/microsoft/mcp-for-beginners.git`
3. [**Pridružite se Azure AI Foundry Discord zajednici i upoznajte stručnjake i druge developere**](https://discord.com/invite/ByRwuEEgH4)


### 🌐 Višejezična podrška

#### Podržano putem GitHub Action (Automatski i uvijek ažurno)

# 🚀 Kurikulum Model Context Protocol (MCP) za Početnike

## **Naučite MCP kroz praktične primjere koda u C#, Java, JavaScript, Python i TypeScript**

## 🧠 Pregled kurikuluma Model Context Protocol

**Model Context Protocol (MCP)** je najsuvremeniji okvir dizajniran za standardizaciju interakcija između AI modela i klijentskih aplikacija. Ovaj otvoreni kurikulum nudi strukturirani put učenja, s praktičnim primjerima koda i stvarnim slučajevima upotrebe, na popularnim programskim jezicima poput C#, Java, JavaScript, TypeScript i Python.

Bilo da ste AI developer, sistemski arhitekt ili softverski inženjer, ovaj vodič je vaš sveobuhvatni resurs za savladavanje osnovnih principa MCP-a i strategija implementacije.

## 🔗 Službeni MCP resursi

- 📘 [MCP Dokumentacija](https://modelcontextprotocol.io/) – Detaljni tutorijali i korisnički vodiči  
- 📜 [MCP Specifikacija](https://spec.modelcontextprotocol.io/) – Arhitektura protokola i tehničke reference  
- 🧑‍💻 [MCP GitHub Repozitorij](https://github.com/modelcontextprotocol) – Open-source SDK-ovi, alati i primjeri koda  

## 🧭 Struktura kompletnog MCP kurikuluma

| Ch | Naslov | Opis | Link |
|--|--|--|--|
| 00 | **Uvod u MCP** | Pregled Model Context Protokola i njegove važnosti u AI pipeline-ima, uključujući što je Model Context Protocol, zašto je standardizacija bitna te praktične primjere i prednosti | [Uvod](./00-Introduction/README.md) |
| 01 | **Objašnjeni osnovni koncepti** | Detaljna analiza osnovnih pojmova MCP-a, uključujući klijent-server arhitekturu, ključne komponente protokola i obrasce razmjene poruka | [Osnovni koncepti](./01-CoreConcepts/README.md) |
| 02 | **Sigurnost u MCP-u** | Identifikacija sigurnosnih prijetnji u MCP baziranim sustavima, tehnike i najbolje prakse za sigurnu implementaciju | [Sigurnost](/02-Security/README.md) |
| 03 | **Početak rada s MCP-om** | Postavljanje i konfiguracija okruženja, kreiranje osnovnih MCP servera i klijenata, integracija MCP-a u postojeće aplikacije | [Početak rada](./03-GettingStarted/README.md) |
| 3.1 | **Prvi server** | Postavljanje osnovnog servera koristeći MCP protokol, razumijevanje interakcije server-klijent i testiranje servera | [Prvi server](./03-GettingStarted/01-first-server/README.md) |
| 3.2 | **Prvi klijent**  | Postavljanje osnovnog klijenta koristeći MCP protokol, razumijevanje interakcije klijent-server i testiranje klijenta | [Prvi klijent](./03-GettingStarted/02-client/README.md) |
| 3.3 | **Klijent s LLM-om**  | Postavljanje klijenta koristeći MCP protokol s velikim jezičnim modelom (LLM) | [Klijent s LLM](./03-GettingStarted/03-llm-client/README.md) |
| 3.4 | **Konzumiranje servera u Visual Studio Code-u** | Postavljanje Visual Studio Code-a za korištenje servera putem MCP protokola | [Konzumiranje servera u Visual Studio Code-u](./03-GettingStarted/04-vscode/README.md) |
| 3.5 | **Kreiranje servera koristeći SSE** | SSE nam pomaže da izložimo server na internetu. Ovaj dio će vam pomoći da kreirate server koristeći SSE | [Kreiranje servera koristeći SSE](./03-GettingStarted/05-sse-server/README.md) |
| 3.6 | **Korištenje AI Toolkit-a** | AI toolkit je izvrstan alat koji će vam pomoći upravljati AI i MCP workflow-om | [Korištenje AI Toolkit-a](./03-GettingStarted/06-aitk/README.md) |
| 3.7 | **Testiranje vašeg servera** | Testiranje je važan dio procesa razvoja. Ovaj dio će vam pomoći da testirate koristeći nekoliko različitih alata | [Testiranje vašeg servera](./03-GettingStarted/07-testing/README.md) |
| 3.8 | **Deploy vašeg servera** | Kako prijeći s lokalnog razvoja na produkciju? Ovaj dio će vam pomoći da razvijete i postavite vaš server | [Deploy vašeg servera](./03-GettingStarted/08-deployment/README.md) |
| 04 | **Praktična implementacija** | Korištenje SDK-ova na različitim jezicima, debugiranje, testiranje i validacija, kreiranje ponovo upotrebljivih predložaka promptova i workflow-a | [Praktična implementacija](./04-PracticalImplementation/README.md) |
| 05 | **Napredne teme u MCP-u** | Multi-modalni AI workflow-i i proširivost, sigurne strategije skaliranja, MCP u enterprise ekosustavima | [Napredne teme](./05-AdvancedTopics/README.md) |
| 5.1 | **Integracija MCP-a s Azure-om** | Prikazuje integraciju s Azure-om | [Integracija MCP Azure](./05-AdvancedTopics/mcp-integration/README.md) |
| 5.2 | **Multi modalnost** | Prikazuje kako raditi s različitim modalitetima poput slika i više | [Multi modalnost](./05-AdvancedTopics/mcp-multi-modality/README.md) |
| 5.3 | **MCP OAuth2 Demo** | Minimalna Spring Boot aplikacija koja pokazuje OAuth2 s MCP-om, kao Authorization i Resource Server. Demonstrira sigurno izdavanje tokena, zaštićene endpoint-e, Azure Container Apps deployment i integraciju s API Managementom | [MCP OAuth2 Demo](./05-AdvancedTopics/mcp-oauth2-demo/README.md) |
| 5.4 | **Root Contexts** | Saznajte više o root contextu i kako ga implementirati | [Root Contexts](./05-AdvancedTopics/mcp-root-contexts/README.md) |
| 5.5 | **Routing** | Naučite različite vrste rutiranja | [Routing](./05-AdvancedTopics/mcp-routing/README.md) |
| 5.6 | **Sampling** | Naučite kako raditi sa samplingom | [Sampling](./05-AdvancedTopics/mcp-sampling/README.md) |
| 5.7 | **Scaling** | Naučite o skaliranju MCP servera, uključujući horizontalne i vertikalne strategije skaliranja, optimizaciju resursa i podešavanje performansi | [Scaling](./05-AdvancedTopics/mcp-scaling/README.md) |
| 5.8 | **Sigurnost** | Osigurajte svoj MCP server, uključujući autentifikaciju, autorizaciju i strategije zaštite podataka | [Sigurnost](./05-AdvancedTopics/mcp-security/README.md) |
| 5.9 | **Web Search MCP** | Python MCP server i klijent integrirani sa SerpAPI za pretraživanje weba, vijesti, proizvoda i Q&A u stvarnom vremenu. Prikazuje multi-alatnu orkestraciju, integraciju vanjskih API-ja i robusno rukovanje greškama | [Web Search MCP](./05-AdvancedTopics/web-search-mcp/README.md) |
| 06 | **Doprinosi zajednice** | Kako doprinositi kodu i dokumentaciji, suradnja putem GitHub-a, poboljšanja i povratne informacije vođene zajednicom | [Doprinosi zajednice](./06-CommunityContributions/README.md) |
| 07 | **Uvidi iz ranih primjena** | Stvarne implementacije i što je funkcioniralo, izgradnja i deploy MCP baziranih rješenja, trendovi i buduća mapa puta | [Uvidi](./07-LessonsFromEarlyAdoption/README.md) |
| 08 | **Najbolje prakse za MCP** | Podešavanje performansi i optimizacija, dizajn otpornog MCP sustava, strategije testiranja i otpornosti | [Najbolje prakse](./08-BestPractices/README.md) |
| 09 | **MCP Studije slučaja** | Dubinske analize MCP arhitektura rješenja, planovi implementacije i savjeti za integraciju, anotirane dijagrame i prikaze projekata | [Studije slučaja](./09-CaseStudy/README.md) |

## Primjerni projekti

### 🧮 MCP Kalkulator Primjerni Projekti:
<details>
  <summary><strong>Istražite implementacije koda po jeziku</strong></summary>
- [C# MCP Server Example](./03-GettingStarted/samples/csharp/README.md)
  - [Java MCP Calculator](./03-GettingStarted/samples/java/calculator/README.md)
  - [JavaScript MCP Demo](./03-GettingStarted/samples/javascript/README.md)
  - [Python MCP Server](../../03-GettingStarted/samples/python/mcp_calculator_server.py)
  - [TypeScript MCP Example](./03-GettingStarted/samples/typescript/README.md)

</details>

### 💡 MCP Advanced Calculator Projects:
<details>
  <summary><strong>Istražite napredne primjere</strong></summary>

  - [Advanced C# Sample](./04-PracticalImplementation/samples/csharp/README.md)
  - [Java Container App Example](./04-PracticalImplementation/samples/java/containerapp/README.md)
  - [JavaScript Advanced Sample](./04-PracticalImplementation/samples/javascript/README.md)
  - [Python Complex Implementation](../../04-PracticalImplementation/samples/python/mcp_sample.py)
  - [TypeScript Container Sample](./04-PracticalImplementation/samples/typescript/README.md)

</details>


## 🎯 Preduvjeti za učenje MCP-a

Da biste maksimalno iskoristili ovaj kurikulum, trebali biste imati:

- Osnovno znanje C#, Java ili Python  
- Razumijevanje klijent-server modela i API-ja  
- (Opcionalno) Poznavanje pojmova iz područja strojnog učenja  

## 🛠️ Kako učinkovito koristiti ovaj kurikulum

Svaka lekcija u ovom vodiču uključuje:

1. Jasna objašnjenja MCP koncepata  
2. Primjere koda uživo na više jezika  
3. Vježbe za izgradnju stvarnih MCP aplikacija  
4. Dodatne resurse za napredne učenike  

## 📜 Informacije o licenci

Ovaj sadržaj je licenciran pod **MIT licencom**. Za uvjete korištenja pogledajte [LICENSE](../../LICENSE).

## 🤝 Smjernice za doprinos

Ovaj projekt rado prihvaća doprinose i prijedloge. Većina doprinosa zahtijeva da pristanete na
Contributor License Agreement (CLA) kojim potvrđujete da imate pravo i doista dajete prava za korištenje vašeg doprinosa. Za detalje posjetite <https://cla.opensource.microsoft.com>.

Kada pošaljete pull request, CLA bot će automatski provjeriti trebate li dostaviti
CLA i označiti PR na odgovarajući način (npr. status provjere, komentar). Jednostavno slijedite upute
koje vam bot pruži. Ovo trebate napraviti samo jednom za sve repozitorije koji koriste naš CLA.

Ovaj projekt je usvojio [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
Za više informacija pogledajte [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) ili
kontaktirajte [opencode@microsoft.com](mailto:opencode@microsoft.com) za dodatna pitanja ili komentare.

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
- [Choose Your Own Copilot Adventure](https://github.com/microsoft/CopilotAdventures?WT.mc_id=academic-105485-koreyst)


## ™️ Obavijest o zaštitnom znaku

Ovaj projekt može sadržavati zaštitne znakove ili logotipe za projekte, proizvode ili usluge. Ovlaštena upotreba Microsoftovih
zaštitnih znakova ili logotipa podliježe i mora se pridržavati
[Microsoftovih smjernica za zaštitne znakove i brendove](https://www.microsoft.com/legal/intellectualproperty/trademarks/usage/general).
Korištenje Microsoftovih zaštitnih znakova ili logotipa u izmijenjenim verzijama ovog projekta ne smije izazvati zabunu niti implicirati sponzorstvo Microsofta.
Svaka upotreba zaštitnih znakova ili logotipa trećih strana podliježe pravilima tih trećih strana.

**Odricanje od odgovornosti**:  
Ovaj dokument preveden je korištenjem AI usluge za prijevod [Co-op Translator](https://github.com/Azure/co-op-translator). Iako nastojimo postići točnost, imajte na umu da automatski prijevodi mogu sadržavati pogreške ili netočnosti. Izvorni dokument na izvornom jeziku treba smatrati službenim i autoritativnim izvorom. Za kritične informacije preporučuje se profesionalni ljudski prijevod. Nismo odgovorni za bilo kakva nesporazuma ili pogrešna tumačenja koja proizlaze iz korištenja ovog prijevoda.