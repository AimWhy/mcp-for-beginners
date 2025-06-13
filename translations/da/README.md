<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "a3b97186cd9162b9fe9b90261e63e32d",
  "translation_date": "2025-06-13T14:15:10+00:00",
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
1. **Fork Repositoryet**: Klik på [![GitHub forks](https://img.shields.io/github/forks/microsoft/mcp-for-beginners.svg?style=social&label=Fork)](https://GitHub.com/microsoft/mcp-for-beginners/fork)
2. **Klon Repositoryet**:   `git clone https://github.com/microsoft/mcp-for-beginners.git`
3. [**Deltag i Azure AI Foundry Discord og mød eksperter og andre udviklere**](https://discord.com/invite/ByRwuEEgH4)


### 🌐 Multisprog Support

#### Understøttet via GitHub Action (Automatiseret & Altid Opdateret)

# 🚀 Model Context Protocol (MCP) Curriculum for Beginners

## **Lær MCP med praktiske kodeeksempler i C#, Java, JavaScript, Python og TypeScript**

## 🧠 Oversigt over Model Context Protocol Curriculum

**Model Context Protocol (MCP)** er en banebrydende ramme designet til at standardisere interaktioner mellem AI-modeller og klientapplikationer. Dette open source curriculum tilbyder en struktureret læringsvej, komplet med praktiske kodeeksempler og virkelige anvendelsestilfælde på populære programmeringssprog som C#, Java, JavaScript, TypeScript og Python.

Uanset om du er AI-udvikler, systemarkitekt eller softwareingeniør, er denne guide din omfattende ressource til at mestre MCP-grundlæggende og implementeringsstrategier.

## 🔗 Officielle MCP Ressourcer

- 📘 [MCP Documentation](https://modelcontextprotocol.io/) – Detaljerede tutorials og brugerguider  
- 📜 [MCP Specification](https://spec.modelcontextprotocol.io/) – Protokolarkitektur og tekniske referencer  
- 🧑‍💻 [MCP GitHub Repository](https://github.com/modelcontextprotocol) – Open source SDK’er, værktøjer og kodeeksempler  

## 🧭 Fuldstændig MCP Curriculum Struktur

| Ch | Titel | Beskrivelse | Link |
|--|--|--|--|
| 00 | **Introduktion til MCP** | Oversigt over Model Context Protocol og dets betydning i AI-pipelines, herunder hvad Model Context Protocol er, hvorfor standardisering er vigtigt, samt praktiske anvendelsestilfælde og fordele | [Introduction](./00-Introduction/README.md) |
| 01 | **Kernebegreber forklaret** | Grundig gennemgang af MCP’s kernebegreber, herunder klient-server arkitektur, nøgleprotokolkomponenter og beskedmønstre | [Core Concepts](./01-CoreConcepts/README.md) |
| 02 | **Sikkerhed i MCP** | Identificering af sikkerhedstrusler i MCP-baserede systemer, teknikker og bedste praksis til at sikre implementeringer | [Security](/02-Security/README.md) |
| 03 | **Kom godt i gang med MCP** | Opsætning og konfiguration af miljø, oprettelse af grundlæggende MCP-servere og klienter, integration af MCP med eksisterende applikationer | [Getting Started](./03-GettingStarted/README.md) |
| 3.1 | **Første server** | Opsætning af en grundlæggende server ved hjælp af MCP-protokollen, forståelse af server-klient interaktionen og test af serveren | [First Server](./03-GettingStarted/01-first-server/README.md) |
| 3.2 | **Første klient**  | Opsætning af en grundlæggende klient ved hjælp af MCP-protokollen, forståelse af klient-server interaktionen og test af klienten | [First Client](./03-GettingStarted/02-client/README.md) |
| 3.3 | **Klient med LLM**  | Opsætning af en klient ved hjælp af MCP-protokollen med en stor sprogmodel (LLM) | [Client with LLM](./03-GettingStarted/03-llm-client/README.md) |
| 3.4 | **Forbrug af en server med Visual Studio Code** | Opsætning af Visual Studio Code til at forbruge servere ved hjælp af MCP-protokollen | [Consuming a server with Visual Studio Code](./03-GettingStarted/04-vscode/README.md) |
| 3.5 | **Oprettelse af en server ved hjælp af SSE** | SSE hjælper os med at eksponere en server på internettet. Dette afsnit hjælper dig med at oprette en server ved hjælp af SSE | [Creating a server using SSE](./03-GettingStarted/05-sse-server/README.md) |
| 3.6 | **HTTP Streaming** | Lær hvordan du implementerer HTTP streaming til realtidsdataoverførsel mellem klienter og MCP-servere | [HTTP Streaming](./03-GettingStarted/06-http-streaming/README.md) |
| 3.7 | **Brug AI Toolkit** | AI Toolkit er et fantastisk værktøj, der hjælper dig med at håndtere din AI- og MCP-workflow. | [Use AI Toolkit](./03-GettingStarted/07-aitk/README.md) |
| 3.8 | **Test din server** | Testning er en vigtig del af udviklingsprocessen. Dette afsnit hjælper dig med at teste ved hjælp af flere forskellige værktøjer. | [Testing your server](./03-GettingStarted/08-testing/README.md) |
| 3.9 | **Deploy din server** | Hvordan går du fra lokal udvikling til produktion? Dette afsnit hjælper dig med at udvikle og deployere din server. | [Deploy your server](./03-GettingStarted/09-deployment/README.md) |
| 04 | **Praktisk implementering** | Brug af SDK’er på tværs af forskellige sprog, debugging, test og validering, opbygning af genanvendelige promptskabeloner og workflows | [Practical Implementation](./04-PracticalImplementation/README.md) |
| 05 | **Avancerede emner i MCP** | Multimodale AI-workflows og udvidelsesmuligheder, sikre skaleringsstrategier, MCP i enterprise-økosystemer | [Advanced Topics](./05-AdvancedTopics/README.md) |
| 5.1 | **MCP integration med Azure** | Viser integration med Azure | [MCP Azure integration](./05-AdvancedTopics/mcp-integration/README.md) |
| 5.2 | **Multimodalitet** | Viser hvordan man arbejder med forskellige modaliteter som billeder og mere | [Multi modality](./05-AdvancedTopics/mcp-multi-modality/README.md) |
| 5.3 | **MCP OAuth2 Demo** | Minimal Spring Boot-app der viser OAuth2 med MCP, både som autorisations- og ressourcer-server. Demonstrerer sikker token-udstedelse, beskyttede endpoints, Azure Container Apps deployment og API Management integration. | [MCP OAuth2 Demo](./05-AdvancedTopics/mcp-oauth2-demo/README.md) |
| 5.4 | **Root Contexts** | Lær mere om root context og hvordan du implementerer dem | [Root Contexts](./05-AdvancedTopics/mcp-root-contexts/README.md) |
| 5.5 | **Routing** | Lær om forskellige typer routing | [Routing](./05-AdvancedTopics/mcp-routing/README.md) |
| 5.6 | **Sampling** | Lær hvordan man arbejder med sampling | [Sampling](./05-AdvancedTopics/mcp-sampling/README.md) |
| 5.7 | **Skalering** | Lær om skalering af MCP-servere, inklusive horisontale og vertikale skaleringsstrategier, ressourceoptimering og performance-tuning | [Scaling](./05-AdvancedTopics/mcp-scaling/README.md) |
| 5.8 | **Sikkerhed** | Sikr din MCP-server, herunder autentificering, autorisation og databeskyttelsesstrategier | [Security](./05-AdvancedTopics/mcp-security/README.md) |
| 5.9 | **Web Search MCP** | Python MCP-server og klient, der integrerer med SerpAPI for realtids web-, nyheds-, produkt-søgning og Q&A. Demonstrerer multi-værktøjs orkestrering, ekstern API-integration og robust fejlhåndtering | [Web Search MCP](./05-AdvancedTopics/web-search-mcp/README.md) |
| 5.10 | **Realtids Streaming** | Realtids data-streaming er blevet essentielt i dagens datadrevne verden, hvor virksomheder og applikationer har brug for øjeblikkelig adgang til information for at træffe rettidige beslutninger. | [Realtime Streaming](./05-AdvancedTopics/mcp-realtimestreaming/README.md) |
| 5.11 | **Realtids Web Search** | Realtids web-søgning: hvordan MCP transformerer realtids web-søgning ved at tilbyde en standardiseret tilgang til kontekststyring på tværs af AI-modeller, søgemaskiner og applikationer. | [Realtime Web Search](./05-AdvancedTopics/mcp-realtimesearch/README.md) |
| 06 | **Community Bidrag** | Hvordan man bidrager med kode og dokumentation, samarbejde via GitHub, community-drevne forbedringer og feedback | [Community Contributions](./06-CommunityContributions/README.md) |
| 07 | **Indsigter fra Tidlig Adoption** | Implementeringer i praksis og hvad der virkede, opbygning og udrulning af MCP-baserede løsninger, tendenser og fremtidig køreplan | [Insights](./07-LessonsFromEarlyAdoption/README.md) |
| 08 | **Bedste Praksis for MCP** | Ydelsesoptimering og tuning, design af fejltolerante MCP-systemer, test- og robusthedsstrategier | [Best Practices](./08-BestPractices/README.md) |
| 09 | **MCP Case Studier** | Dybdegående analyser af MCP-løsningsarkitekturer, udrulningsplaner og integrationsråd, annoterede diagrammer og projektgennemgange | [Case Studies](./09-CaseStudy/README.md) |
| 10 | **Effektivisering af AI-arbejdsgange: Byg en MCP-server med AI Toolkit** | Omfattende praktisk workshop, der kombinerer MCP med Microsofts AI Toolkit til VS Code. Lær at bygge intelligente applikationer, der forbinder AI-modeller med virkelige værktøjer gennem praktiske moduler, der dækker grundlæggende principper, tilpasset serverudvikling og produktionsudrulningsstrategier. | [Hands On Lab](./10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/README.md) |

## Sample Projects

### 🧮 MCP Calculator Sample Projects:
<details>
  <summary><strong>Udforsk kodeimplementeringer efter sprog</strong></summary>

  - [C# MCP Server Example](./03-GettingStarted/samples/csharp/README.md)
  - [Java MCP Calculator](./03-GettingStarted/samples/java/calculator/README.md)
  - [JavaScript MCP Demo](./03-GettingStarted/samples/javascript/README.md)
  - [Python MCP Server](../../03-GettingStarted/samples/python/mcp_calculator_server.py)
  - [TypeScript MCP Example](./03-GettingStarted/samples/typescript/README.md)

</details>

### 💡 MCP Advanced Calculator Projects:
<details>
  <summary><strong>Udforsk avancerede eksempler</strong></summary>

  - [Advanced C# Sample](./04-PracticalImplementation/samples/csharp/README.md)
  - [Java Container App Example](./04-PracticalImplementation/samples/java/containerapp/README.md)
  - [JavaScript Advanced Sample](./04-PracticalImplementation/samples/javascript/README.md)
  - [Python Complex Implementation](../../04-PracticalImplementation/samples/python/mcp_sample.py)
  - [TypeScript Container Sample](./04-PracticalImplementation/samples/typescript/README.md)

</details>


## 🎯 Forudsætninger for at lære MCP

For at få mest muligt ud af dette kursus bør du have:

- Grundlæggende kendskab til C#, Java eller Python  
- Forståelse for klient-server modellen og API’er  
- (Valgfrit) Kendskab til maskinlæringsbegreber  

## 📚 Studieguide

En omfattende [Study Guide](./study_guide.md) er tilgængelig for at hjælpe dig med at navigere effektivt i dette repository. Guiden indeholder:

- Et visuelt kursuskort, der viser alle dækkede emner  
- Detaljeret opdeling af hver sektion i repositoryet  
- Vejledning i brug af sample projects  
- Anbefalede læringsveje for forskellige færdighedsniveauer  
- Yderligere ressourcer til at supplere din læringsrejse  

## 🛠️ Sådan bruger du dette kursus effektivt

Hver lektion i denne guide indeholder:

1. Klare forklaringer på MCP-koncepter  
2. Live kodeeksempler på flere sprog  
3. Øvelser til at bygge rigtige MCP-applikationer  
4. Ekstra ressourcer til avancerede brugere  

## 📜 Licensinformation

Dette indhold er licenseret under **MIT License**. For vilkår og betingelser, se [LICENSE](../../LICENSE).

## 🤝 Bidragsretningslinjer

Dette projekt byder velkommen til bidrag og forslag. De fleste bidrag kræver, at du accepterer en Contributor License Agreement (CLA), der erklærer, at du har ret til, og faktisk giver os, rettighederne til at bruge dit bidrag. For detaljer, besøg <https://cla.opensource.microsoft.com>.

Når du sender en pull request, vil en CLA-bot automatisk afgøre, om du skal indsende en CLA og markere PR’en passende (fx statuscheck, kommentar). Følg blot instruktionerne fra botten. Du skal kun gøre dette én gang på tværs af alle repos, der bruger vores CLA.

Dette projekt har tilsluttet sig [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).  
For mere information, se [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) eller kontakt [opencode@microsoft.com](mailto:opencode@microsoft.com) med yderligere spørgsmål eller kommentarer.

## 🎒 Andre kurser  
Vores team laver også andre kurser! Tjek dem ud:

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


## ™️ Varemærke Meddelelse

Dette projekt kan indeholde varemærker eller logoer for projekter, produkter eller tjenester. Autoriseret brug af Microsofts
varemærker eller logoer er underlagt og skal følge
[Microsofts Varemærke- og Brandretningslinjer](https://www.microsoft.com/legal/intellectualproperty/trademarks/usage/general).
Brug af Microsofts varemærker eller logoer i ændrede versioner af dette projekt må ikke skabe forvirring eller antyde Microsofts sponsorskab.
Enhver brug af tredjeparts varemærker eller logoer er underlagt disse tredjeparts politikker.

**Ansvarsfraskrivelse**:  
Dette dokument er blevet oversat ved hjælp af AI-oversættelsestjenesten [Co-op Translator](https://github.com/Azure/co-op-translator). Selvom vi bestræber os på nøjagtighed, skal du være opmærksom på, at automatiserede oversættelser kan indeholde fejl eller unøjagtigheder. Det oprindelige dokument på dets oprindelige sprog bør betragtes som den autoritative kilde. For kritisk information anbefales professionel menneskelig oversættelse. Vi påtager os intet ansvar for misforståelser eller fejltolkninger, der opstår som følge af brugen af denne oversættelse.