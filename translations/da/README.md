<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "26ab12045ee411ab7ad0eb0b1b7b1cbb",
  "translation_date": "2025-06-13T00:04:19+00:00",
  "source_file": "README.md",
  "language_code": "da"
}
-->
![MCP-for-beginners](../../translated_images/mcp-beginners.2ce2b317996369ff66c5b72e25eff9d4288ab2741fc70c0b4e523d1ae1e249fd.da.png) 

[![GitHub contributors](https://img.shields.io/github/contributors/microsoft/mcp-for-beginners.svg)](https://GitHub.com/microsoft/mcp-for-beginners/graphs/contributors)
[![GitHub issues](https://img.shields.io/github/issues/microsoft/mcp-for-beginners.svg)](https://GitHub.com/microsoft/mcp-for-beginners/issues)
[![GitHub pull-requests](https://img.shields.io/github/issues-pr/microsoft/mcp-for-beginners.svg)](https://GitHub.com/microsoft/mcp-for-beginners/pulls)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)

[![GitHub watchers](https://img.shields.io/github/watchers/microsoft/mcp-for-beginners.svg?style=social&label=Watch)](https://GitHub.com/microsoft/mcp-for-beginners/watchers)
[![GitHub forks](https://img.shields.io/github/forks/microsoft/mcp-for-beginners.svg?style=social&label=Fork)](https://GitHub.com/microsoft/mcp-for-beginners/fork)
[![GitHub stars](https://img.shields.io/github/stars/microsoft/mcp-for-beginners?style=social&label=Star)](https://GitHub.com/microsoft/mcp-for-beginners/stargazers)


[![Microsoft Azure AI Foundry Discord](https://dcbadge.vercel.app/api/server/ByRwuEEgH4)](https://discord.com/invite/ByRwuEEgH4)


Følg disse trin for at komme i gang med at bruge disse ressourcer:
1. **Fork Repository**: Klik på [![GitHub forks](https://img.shields.io/github/forks/microsoft/mcp-for-beginners.svg?style=social&label=Fork)](https://GitHub.com/microsoft/mcp-for-beginners/fork)
2. **Klon Repository**:   `git clone https://github.com/microsoft/mcp-for-beginners.git`
3. [**Deltag i Azure AI Foundry Discord og mød eksperter og andre udviklere**](https://discord.com/invite/ByRwuEEgH4)


### 🌐 Multisprog Understøttelse

#### Understøttet via GitHub Action (Automatiseret & Altid Opdateret)

# 🚀 Model Context Protocol (MCP) Læreplan for Begyndere

## **Lær MCP med Praktiske Kodeeksempler i C#, Java, JavaScript, Python og TypeScript**

## 🧠 Oversigt over Model Context Protocol Læreplan

**Model Context Protocol (MCP)** er en banebrydende ramme, der er designet til at standardisere interaktioner mellem AI-modeller og klientapplikationer. Denne open source læreplan tilbyder en struktureret læringsvej med praktiske kodeeksempler og virkelige anvendelsestilfælde på populære programmeringssprog som C#, Java, JavaScript, TypeScript og Python.

Uanset om du er AI-udvikler, systemarkitekt eller softwareingeniør, er denne guide din komplette ressource til at mestre MCP’s grundlæggende principper og implementeringsstrategier.

## 🔗 Officielle MCP Ressourcer

- 📘 [MCP Documentation](https://modelcontextprotocol.io/) – Detaljerede tutorials og brugervejledninger  
- 📜 [MCP Specification](https://spec.modelcontextprotocol.io/) – Protokollens arkitektur og tekniske referencer  
- 🧑‍💻 [MCP GitHub Repository](https://github.com/modelcontextprotocol) – Open source SDK’er, værktøjer og kodeeksempler  

## 🧭 Fuld MCP Læreplansstruktur

| Ch | Titel | Beskrivelse | Link |
|--|--|--|--|
| 00 | **Introduktion til MCP** | Oversigt over Model Context Protocol og dens betydning i AI-pipelines, herunder hvad Model Context Protocol er, hvorfor standardisering er vigtigt, samt praktiske anvendelser og fordele | [Introduction](./00-Introduction/README.md) |
| 01 | **Kernebegreber Forklaret** | Grundig gennemgang af MCP’s kernebegreber, inklusive klient-server arkitektur, nøgleprotokolkomponenter og beskedmønstre | [Core Concepts](./01-CoreConcepts/README.md) |
| 02 | **Sikkerhed i MCP** | Identificering af sikkerhedstrusler i MCP-baserede systemer, teknikker og bedste praksis til at sikre implementeringer | [Security](/02-Security/README.md) |
| 03 | **Kom godt i gang med MCP** | Opsætning og konfiguration af miljø, oprettelse af grundlæggende MCP-servere og klienter, integration af MCP med eksisterende applikationer | [Getting Started](./03-GettingStarted/README.md) |
| 3.1 | **Første server** | Opsætning af en grundlæggende server med MCP-protokollen, forståelse af server-klient interaktion og test af serveren | [First Server](./03-GettingStarted/01-first-server/README.md) |
| 3.2 | **Første klient**  | Opsætning af en grundlæggende klient med MCP-protokollen, forståelse af klient-server interaktion og test af klienten | [First Client](./03-GettingStarted/02-client/README.md) |
| 3.3 | **Klient med LLM**  | Opsætning af en klient med MCP-protokollen og en Large Language Model (LLM) | [Client with LLM](./03-GettingStarted/03-llm-client/README.md) |
| 3.4 | **Brug af Visual Studio Code til at tilgå server** | Opsætning af Visual Studio Code til at tilgå servere via MCP-protokollen | [Consuming a server with Visual Studio Code](./03-GettingStarted/04-vscode/README.md) |
| 3.5 | **Oprettelse af server med SSE** | SSE hjælper os med at eksponere en server til internettet. Denne sektion hjælper dig med at oprette en server med SSE | [Creating a server using SSE](./03-GettingStarted/05-sse-server/README.md) |
| 3.6 | **Brug AI Toolkit** | AI Toolkit er et fantastisk værktøj, der hjælper dig med at styre din AI- og MCP-arbejdsgang | [Use AI Toolkit](./03-GettingStarted/06-aitk/README.md) |
| 3.7 | **Test din server** | Testning er en vigtig del af udviklingsprocessen. Denne sektion hjælper dig med at teste ved hjælp af flere forskellige værktøjer | [Testing your server](./03-GettingStarted/07-testing/README.md) |
| 3.8 | **Deploy din server** | Hvordan går man fra lokal udvikling til produktion? Denne sektion hjælper dig med at udvikle og deployere din server | [Deploy your server](./03-GettingStarted/08-deployment/README.md) |
| 04 | **Praktisk Implementering** | Brug af SDK’er på forskellige sprog, debugging, test og validering, opbygning af genanvendelige promptskabeloner og arbejdsgange | [Practical Implementation](./04-PracticalImplementation/README.md) |
| 05 | **Avancerede Emner i MCP** | Multi-modal AI-arbejdsgange og udvidelsesmuligheder, sikre skaleringsstrategier, MCP i virksomhedsøkosystemer | [Advanced Topics](./05-AdvancedTopics/README.md) |
| 5.1 | **MCP Integration med Azure** | Viser integration med Azure | [MCP Azure integration](./05-AdvancedTopics/mcp-integration/README.md) |
| 5.2 | **Multi modalitet** | Viser hvordan man arbejder med forskellige modaliteter som billeder og mere | [Multi modality](./05-AdvancedTopics/mcp-multi-modality/README.md) |
| 5.3 | **MCP OAuth2 Demo** | Minimal Spring Boot app, der viser OAuth2 med MCP, både som Authorization og Resource Server. Demonstrerer sikker tokenudstedelse, beskyttede endpoints, Azure Container Apps deployment og API Management integration | [MCP OAuth2 Demo](./05-AdvancedTopics/mcp-oauth2-demo/README.md) |
| 5.4 | **Root Contexts** | Lær mere om root context og hvordan man implementerer dem | [Root Contexts](./05-AdvancedTopics/mcp-root-contexts/README.md) |
| 5.5 | **Routing** | Lær om forskellige typer routing | [Routing](./05-AdvancedTopics/mcp-routing/README.md) |
| 5.6 | **Sampling** | Lær hvordan man arbejder med sampling | [Sampling](./05-AdvancedTopics/mcp-sampling/README.md) |
| 5.7 | **Scaling** | Lær om skalering af MCP-servere, herunder horisontale og vertikale skaleringsstrategier, ressourceoptimering og performance tuning | [Scaling](./05-AdvancedTopics/mcp-scaling/README.md) |
| 5.8 | **Security** | Sikr din MCP-server, herunder autentificering, autorisation og databeskyttelsesstrategier | [Security](./05-AdvancedTopics/mcp-security/README.md) |
| 5.9 | **Web Search MCP** | Python MCP-server og klient, der integrerer med SerpAPI til realtidsweb-, nyheds-, produkt-søgning og Q&A. Demonstrerer multi-værktøjs orkestrering, ekstern API-integration og robust fejlhåndtering | [Web Search MCP](./05-AdvancedTopics/web-search-mcp/README.md) |
| 5.10 | **Realtime Streaming** | Realtidsdata-streaming er blevet essentielt i dagens datadrevne verden, hvor virksomheder og applikationer kræver øjeblikkelig adgang til information for at træffe rettidige beslutninger | [Realtime Streaming](./05-AdvancedTopics/mcp-realtimestreaming/README.md) |
| 5.11 | **Realtime Web Search** | Realtids web-søgning: hvordan MCP transformerer realtids web-søgning ved at tilbyde en standardiseret tilgang til kontekststyring på tværs af AI-modeller, søgemaskiner og applikationer | [Realtime Web Search](./05-AdvancedTopics/mcp-realtimesearch/README.md) |
| 06 | **Community Bidrag** | Hvordan man bidrager med kode og dokumentation, samarbejde via GitHub, fællesskabsdrevne forbedringer og feedback | [Community Contributions](./06-CommunityContributions/README.md) |
| 07 | **Erfaringer fra Tidlig Adoptering** | Virkelige implementeringer og hvad der virkede, opbygning og deployering af MCP-baserede løsninger, trends og fremtidig køreplan | [Insights](./07-LessonsFromEarlyAdoption/README.md) |
| 08 | **Bedste praksis for MCP** | Performanceoptimering og tuning, design af fejl-tolerante MCP-systemer, test- og robusthedsstrategier | [Best Practices](./08-BestPractices/README.md) |
| 09 | **MCP Case Studier** | Dybdegående gennemgang af MCP-løsningsarkitekturer, implementeringsplaner og integrationsråd, annoterede diagrammer og projektgennemgange | [Case Studies](./09-CaseStudy/README.md) |
| 10 | **Strømlining af AI-workflows: Opbygning af en MCP-server med AI Toolkit** | Omfattende hands-on workshop, der kombinerer MCP med Microsofts AI Toolkit til VS Code. Lær at bygge intelligente applikationer, der forbinder AI-modeller med virkelige værktøjer gennem praktiske moduler, der dækker grundlæggende principper, tilpasset serverudvikling og produktionsimplementeringsstrategier. | [Hands On Lab](./10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/README.md) |

## Eksempelprojekter

### 🧮 MCP Calculator Eksempelprojekter:
<details>
  <summary><strong>Udforsk kodeimplementeringer efter sprog</strong></summary>

  - [C# MCP Server Eksempel](./03-GettingStarted/samples/csharp/README.md)
  - [Java MCP Calculator](./03-GettingStarted/samples/java/calculator/README.md)
  - [JavaScript MCP Demo](./03-GettingStarted/samples/javascript/README.md)
  - [Python MCP Server](../../03-GettingStarted/samples/python/mcp_calculator_server.py)
  - [TypeScript MCP Eksempel](./03-GettingStarted/samples/typescript/README.md)

</details>

### 💡 MCP Avancerede Calculator Projekter:
<details>
  <summary><strong>Udforsk avancerede eksempler</strong></summary>

  - [Avanceret C# Eksempel](./04-PracticalImplementation/samples/csharp/README.md)
  - [Java Container App Eksempel](./04-PracticalImplementation/samples/java/containerapp/README.md)
  - [JavaScript Avanceret Eksempel](./04-PracticalImplementation/samples/javascript/README.md)
  - [Python Kompleks Implementering](../../04-PracticalImplementation/samples/python/mcp_sample.py)
  - [TypeScript Container Eksempel](./04-PracticalImplementation/samples/typescript/README.md)

</details>

## 🎯 Forudsætninger for at lære MCP

For at få mest muligt ud af dette kursus bør du have:

- Grundlæggende kendskab til C#, Java eller Python  
- Forståelse for klient-server modellen og APIs  
- (Valgfrit) Kendskab til maskinlæringsbegreber  

## 📚 Studievejledning

En omfattende [Studievejledning](./study_guide.md) er tilgængelig for at hjælpe dig med effektivt at navigere i dette repository. Guiden indeholder:

- Et visuelt kursuskort, der viser alle emner  
- Detaljeret opdeling af hver sektion i repositoryet  
- Vejledning i brug af eksempelprojekter  
- Anbefalede læringsveje for forskellige færdighedsniveauer  
- Yderligere ressourcer til at supplere din læringsrejse  

## 🛠️ Sådan bruger du dette kursus effektivt

Hver lektion i denne guide indeholder:

1. Klare forklaringer af MCP-koncepter  
2. Live kodeeksempler på flere sprog  
3. Øvelser til at bygge reelle MCP-applikationer  
4. Ekstra ressourcer til avancerede lærende  

## 📜 Licensinformation

Dette indhold er licenseret under **MIT License**. For vilkår og betingelser, se [LICENSE](../../LICENSE).

## 🤝 Retningslinjer for bidrag

Dette projekt byder velkommen til bidrag og forslag. De fleste bidrag kræver, at du accepterer en Contributor License Agreement (CLA), der erklærer, at du har retten til, og faktisk giver os retten til at bruge dit bidrag. For detaljer, besøg <https://cla.opensource.microsoft.com>.

Når du sender en pull request, vil en CLA-bot automatisk afgøre, om du skal indsende en CLA og markere PR’en passende (fx statuscheck, kommentar). Følg blot instruktionerne fra botten. Du skal kun gøre dette én gang på tværs af alle repositories, der bruger vores CLA.

Dette projekt har adopteret [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/). For mere information, se [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) eller kontakt [opencode@microsoft.com](mailto:opencode@microsoft.com) med yderligere spørgsmål eller kommentarer.

## 🎒 Andre kurser
Vores team producerer også andre kurser! Se:

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


## ™️ Varemærke-meddelelse

Dette projekt kan indeholde varemærker eller logoer for projekter, produkter eller tjenester. Autoriseret brug af Microsofts
varemærker eller logoer er underlagt og skal følge
[Microsofts varemærke- og brandretningslinjer](https://www.microsoft.com/legal/intellectualproperty/trademarks/usage/general).
Brug af Microsofts varemærker eller logoer i modificerede versioner af dette projekt må ikke skabe forvirring eller antyde Microsofts sponsorskab.
Enhver brug af tredjeparts varemærker eller logoer er underlagt disse tredjeparts politikker.

**Ansvarsfraskrivelse**:  
Dette dokument er blevet oversat ved hjælp af AI-oversættelsestjenesten [Co-op Translator](https://github.com/Azure/co-op-translator). Selvom vi bestræber os på nøjagtighed, bedes du være opmærksom på, at automatiserede oversættelser kan indeholde fejl eller unøjagtigheder. Det oprindelige dokument på dets oprindelige sprog bør betragtes som den autoritative kilde. For kritisk information anbefales professionel menneskelig oversættelse. Vi påtager os intet ansvar for misforståelser eller fejltolkninger, der opstår som følge af brugen af denne oversættelse.