<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "a22b7dd11cd7690f99f9195877cafdc3",
  "translation_date": "2025-06-10T05:50:59+00:00",
  "source_file": "10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab2/README.md",
  "language_code": "no"
}
-->
# 🌐 Modul 2: MCP med AI Toolkit Grunnleggende

[![Duration](https://img.shields.io/badge/Duration-20%20minutes-blue.svg)]()
[![Difficulty](https://img.shields.io/badge/Difficulty-Intermediate-yellow.svg)]()
[![Prerequisites](https://img.shields.io/badge/Prerequisites-Module%201%20Complete-orange.svg)]()

## 📋 Læringsmål

Ved slutten av dette modul vil du kunne:
- ✅ Forstå Model Context Protocol (MCP) arkitektur og fordeler
- ✅ Utforske Microsofts MCP server-økosystem
- ✅ Integrere MCP-servere med AI Toolkit Agent Builder
- ✅ Bygge en funksjonell nettleserautomatiseringsagent med Playwright MCP
- ✅ Konfigurere og teste MCP-verktøy i agentene dine
- ✅ Eksportere og distribuere MCP-drevne agenter for produksjonsbruk

## 🎯 Bygger videre på Modul 1

I Modul 1 mestret vi AI Toolkit grunnleggende og laget vår første Python Agent. Nå skal vi **gi ekstra kraft** til agentene dine ved å koble dem til eksterne verktøy og tjenester gjennom den revolusjonerende **Model Context Protocol (MCP)**.

Tenk på dette som en oppgradering fra en enkel kalkulator til en fullverdig datamaskin – AI-agentene dine vil få muligheten til å:
- 🌐 Surfe og samhandle med nettsider
- 📁 Få tilgang til og håndtere filer
- 🔧 Integrere med bedriftsystemer
- 📊 Behandle sanntidsdata fra API-er

## 🧠 Forstå Model Context Protocol (MCP)

### 🔍 Hva er MCP?

Model Context Protocol (MCP) er **"USB-C for AI-applikasjoner"** – en revolusjonerende åpen standard som kobler Store Språkmodeller (LLMs) til eksterne verktøy, datakilder og tjenester. På samme måte som USB-C fjernet kabelrot ved å tilby en universell kontakt, fjerner MCP kompleksiteten ved AI-integrasjon med én standardisert protokoll.

### 🎯 Problemet MCP løser

**Før MCP:**
- 🔧 Skreddersydde integrasjoner for hvert verktøy
- 🔄 Leverandørlås med proprietære løsninger  
- 🔒 Sikkerhetsrisikoer fra ad-hoc-tilkoblinger
- ⏱️ Måneder med utvikling for grunnleggende integrasjoner

**Med MCP:**
- ⚡ Plug-and-play integrasjon av verktøy
- 🔄 Leverandøruavhengig arkitektur
- 🛡️ Innebygde sikkerhetsrutiner
- 🚀 Minutter for å legge til nye funksjoner

### 🏗️ MCP Arkitektur – En grundig gjennomgang

MCP følger en **klient-server arkitektur** som skaper et sikkert og skalerbart økosystem:

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

**🔧 Kjernekomponenter:**

| Komponent | Rolle | Eksempler |
|-----------|-------|-----------|
| **MCP Hosts** | Applikasjoner som bruker MCP-tjenester | Claude Desktop, VS Code, AI Toolkit |
| **MCP Clients** | Protokollhåndterere (1:1 med servere) | Innebygd i host-applikasjoner |
| **MCP Servers** | Eksponerer funksjonalitet via standard protokoll | Playwright, Files, Azure, GitHub |
| **Transport Layer** | Kommunikasjonsmetoder | stdio, HTTP, WebSockets |


## 🏢 Microsofts MCP Server-økosystem

Microsoft leder MCP-økosystemet med en omfattende pakke av bedriftsservere som dekker reelle forretningsbehov.

### 🌟 Utvalgte Microsoft MCP Servere

#### 1. ☁️ Azure MCP Server
**🔗 Repository**: [azure/azure-mcp](https://github.com/azure/azure-mcp)
**🎯 Formål**: Omfattende administrasjon av Azure-ressurser med AI-integrasjon

**✨ Nøkkelfunksjoner:**
- Deklarativ infrastruktur-provisjonering
- Sanntidsressursovervåkning
- Anbefalinger for kostnadsoptimalisering
- Sikkerhets- og samsvarskontroll

**🚀 Bruksområder:**
- Infrastruktur-som-kode med AI-hjelp
- Automatisk ressurs-skalering
- Optimalisering av sky-kostnader
- Automatisering av DevOps-arbeidsflyt

#### 2. 📊 Microsoft Dataverse MCP
**📚 Dokumentasjon**: [Microsoft Dataverse Integration](https://go.microsoft.com/fwlink/?linkid=2320176)
**🎯 Formål**: Naturlig språkgrensesnitt for forretningsdata

**✨ Nøkkelfunksjoner:**
- Naturlige språkspørringer mot databaser
- Forståelse av forretningskontekst
- Tilpassede prompt-maler
- Bedriftsdata-governance

**🚀 Bruksområder:**
- Forretningsintelligens-rapportering
- Analyse av kundedata
- Innsikt i salgspipeline
- Spørringer for samsvarsdata

#### 3. 🌐 Playwright MCP Server
**🔗 Repository**: [microsoft/playwright-mcp](https://github.com/microsoft/playwright-mcp)
**🎯 Formål**: Nettleserautomatisering og web-interaksjon

**✨ Nøkkelfunksjoner:**
- Kryss-nettleserautomatisering (Chrome, Firefox, Safari)
- Intelligent elementgjenkjenning
- Skjermbilder og PDF-generering
- Nettverksovervåkning

**🚀 Bruksområder:**
- Automatiserte testarbeidsflyter
- Webskraping og datauttrekk
- Overvåkning av UI/UX
- Automatisering av konkurrentanalyse

#### 4. 📁 Files MCP Server
**🔗 Repository**: [microsoft/files-mcp-server](https://github.com/microsoft/files-mcp-server)
**🎯 Formål**: Intelligent filsystemhåndtering

**✨ Nøkkelfunksjoner:**
- Deklarativ filadministrasjon
- Innholdssynkronisering
- Versjonskontrollintegrasjon
- Metadatauttrekk

**🚀 Bruksområder:**
- Dokumentasjonshåndtering
- Organisering av kode-repositorier
- Arbeidsflyt for innholdspublisering
- Filhåndtering i datapipelines

#### 5. 📝 MarkItDown MCP Server
**🔗 Repository**: [microsoft/markitdown](https://github.com/microsoft/markitdown)
**🎯 Formål**: Avansert Markdown-behandling og manipulering

**✨ Nøkkelfunksjoner:**
- Rikt Markdown-parsing
- Formatkonvertering (MD ↔ HTML ↔ PDF)
- Analyse av innholdsstruktur
- Malbehandling

**🚀 Bruksområder:**
- Arbeidsflyter for teknisk dokumentasjon
- Innholdsstyringssystemer
- Rapportgenerering
- Automatisering av kunnskapsbaser

#### 6. 📈 Clarity MCP Server
**📦 Pakke**: [@microsoft/clarity-mcp-server](https://www.npmjs.com/package/@microsoft/clarity-mcp-server)
**🎯 Formål**: Webanalyse og innsikt i brukeradferd

**✨ Nøkkelfunksjoner:**
- Heatmap-dataanalyse
- Opptak av brukersesjoner
- Ytelsesmetrikker
- Analyse av konverteringstrakter

**🚀 Bruksområder:**
- Optimalisering av nettsider
- Brukeropplevelsesforskning
- A/B-testing-analyse
- Dashboards for forretningsintelligens

### 🌍 Fellesskapsøkosystemet

Utover Microsofts servere inkluderer MCP-økosystemet:
- **🐙 GitHub MCP**: Repositoriehåndtering og kodeanalyse
- **🗄️ Database MCP-er**: Integrasjoner for PostgreSQL, MySQL, MongoDB
- **☁️ Cloud Provider MCP-er**: Verktøy for AWS, GCP, Digital Ocean
- **📧 Kommunikasjons MCP-er**: Slack, Teams, E-post-integrasjoner

## 🛠️ Praktisk lab: Bygg en nettleserautomatiseringsagent

**🎯 Prosjektmål**: Lag en intelligent nettleserautomatiseringsagent med Playwright MCP-server som kan navigere på nettsider, hente ut informasjon og utføre avanserte web-interaksjoner.

### 🚀 Fase 1: Grunnleggende agentoppsett

#### Steg 1: Initialiser agenten din
1. **Åpne AI Toolkit Agent Builder**
2. **Opprett ny agent** med følgende konfigurasjon:
   - **Navn**: `BrowserAgent`
   - **Model**: Choose GPT-4o 

![BrowserAgent](../../../../translated_images/BrowserAgent.09c1adde5e136573b64ab1baecd830049830e295eac66cb18bebb85fb386e00a.no.png)


### 🔧 Phase 2: MCP Integration Workflow

#### Step 3: Add MCP Server Integration
1. **Navigate to Tools Section** in Agent Builder
2. **Click "Add Tool"** to open the integration menu
3. **Select "MCP Server"** from available options

![AddMCP](../../../../translated_images/AddMCP.afe3308ac20aa94469a5717b632d77b2197b9838a438b05d39aeb2db3ec47ef1.no.png)

**🔍 Understanding Tool Types:**
- **Built-in Tools**: Pre-configured AI Toolkit functions
- **MCP Servers**: External service integrations
- **Custom APIs**: Your own service endpoints
- **Function Calling**: Direct model function access

#### Step 4: MCP Server Selection
1. **Choose "MCP Server"** option to proceed
![AddMCPServer](../../../../translated_images/AddMCPServer.69b911ccef872cbd0d0c0c2e6a00806916e1673e543b902a23dee23e6ff54b4c.no.png)

2. **Browse MCP Catalog** to explore available integrations
![MCPCatalog](../../../../translated_images/MCPCatalog.a817d053145699006264f5a475f2b48fbd744e43633f656b6453c15a09ba5130.no.png)


### 🎮 Phase 3: Playwright MCP Configuration

#### Step 5: Select and Configure Playwright
1. **Click "Use Featured MCP Servers"** to access Microsoft's verified servers
2. **Select "Playwright"** from the featured list
3. **Accept Default MCP ID** or customize for your environment

![MCPID](../../../../translated_images/MCPID.67d446052979e819c945ff7b6430196ef587f5217daadd3ca52fa9659c1245c9.no.png)

#### Step 6: Enable Playwright Capabilities
**🔑 Critical Step**: Select **ALL** available Playwright methods for maximum functionality

![Tools](../../../../translated_images/Tools.3ea23c447b4d9feccbd7101e6dcf9e27cb0e5273f351995fde62c5abf9a78b4c.no.png)

**🛠️ Essential Playwright Tools:**
- **Navigation**: `goto`, `goBack`, `goForward`, `reload`
- **Interaction**: `click`, `fill`, `press`, `hover`, `drag`
- **Extraction**: `textContent`, `innerHTML`, `getAttribute`
- **Validation**: `isVisible`, `isEnabled`, `waitForSelector`
- **Capture**: `screenshot`, `pdf`, `video`
- **Network**: `setExtraHTTPHeaders`, `route`, `waitForResponse`

#### Steg 7: Verifiser vellykket integrasjon
**✅ Tegn på suksess:**
- Alle verktøy vises i Agent Builder-grensesnittet
- Ingen feilmeldinger i integrasjonspanelet
- Playwright-serverens status viser "Connected"

![AgentTools](../../../../translated_images/AgentTools.053cfb96a17e02199dcc6563010d2b324d4fc3ebdd24889657a6950647a52f63.no.png)

**🔧 Vanlige feilsøkingspunkter:**
- **Tilkobling mislyktes**: Sjekk internettforbindelse og brannmurinnstillinger
- **Manglende verktøy**: Sørg for at alle funksjoner ble valgt under oppsett
- **Tillatelsesfeil**: Bekreft at VS Code har nødvendige systemtillatelser

### 🎯 Fase 4: Avansert promptdesign

#### Steg 8: Design intelligente systemprompter
Lag avanserte prompter som utnytter Playwrights fulle funksjonalitet:

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

#### Steg 9: Lag dynamiske brukerprompter
Design prompter som demonstrerer ulike funksjoner:

**🌐 Eksempel på webanalyse:**
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

![Prompt](../../../../translated_images/Prompt.bfc846605db4999f4d9c1b09c710ef63cae7b3057444e68bf07240fb142d9f8f.no.png)

### 🚀 Fase 5: Kjøring og testing

#### Steg 10: Kjør din første automatisering
1. **Klikk "Run"** for å starte automatiseringssekvensen
2. **Følg med på sanntidsutførelsen**:
   - Chrome-nettleser åpnes automatisk
   - Agenten navigerer til mål-nettsiden
   - Skjermbilder tas av hvert hovedsteg
   - Analyseresultater vises i sanntid

![Browser](../../../../translated_images/Browser.ec011d0bd64d0d112c8a29bd8cc44c76d0bbfd0b019cb2983ef679328435ce5d.no.png)

#### Steg 11: Analyser resultater og innsikt
Se gjennom grundig analyse i Agent Builder-grensesnittet:

![Result](../../../../translated_images/Result.8638f2b6703e9ea6d58d4e4475e39456b6a51d4c787f9bf481bae694d370a69a.no.png)

### 🌟 Fase 6: Avanserte funksjoner og distribusjon

#### Steg 12: Eksporter og distribuer i produksjon
Agent Builder støtter flere distribusjonsmuligheter:

![Code](../../../../translated_images/Code.d9eeeead0b96db0ca19c5b10ad64cfea8c1d0d1736584262970a4d43e1403d13.no.png)

## 🎓 Modul 2 Oppsummering & Neste steg

### 🏆 Oppnåelse låst opp: MCP Integrasjonsmester

**✅ Ferdigheter mestret:**
- [ ] Forstå MCP-arkitektur og fordeler
- [ ] Navigere Microsofts MCP server-økosystem
- [ ] Integrere Playwright MCP med AI Toolkit
- [ ] Bygge avanserte nettleserautomatiseringsagenter
- [ ] Avansert promptdesign for webautomatisering

### 📚 Ekstra ressurser

- **🔗 MCP Spesifikasjon**: [Offisiell protokoll-dokumentasjon](https://modelcontextprotocol.io/)
- **🛠️ Playwright API**: [Fullstendig metodeoversikt](https://playwright.dev/docs/api/class-playwright)
- **🏢 Microsoft MCP Servere**: [Bedriftsintegrasjonsguide](https://github.com/microsoft/mcp-servers)
- **🌍 Fellesskaps-eksempler**: [MCP Server-galleri](https://github.com/modelcontextprotocol/servers)

**🎉 Gratulerer!** Du har nå mestret MCP-integrasjon og kan bygge produksjonsklare AI-agenter med eksterne verktøy!

### 🔜 Fortsett til neste modul

Klar for å ta MCP-ferdighetene dine til neste nivå? Gå videre til **[Modul 3: Avansert MCP-utvikling med AI Toolkit](../lab3/README.md)** hvor du vil lære å:
- Lage dine egne tilpassede MCP-servere
- Konfigurere og bruke den nyeste MCP Python SDK
- Sette opp MCP Inspector for feilsøking
- Mestre avanserte MCP server-utviklingsarbeidsflyter
- Bygge en vær-MCP-server fra bunnen av

**Ansvarsfraskrivelse**:  
Dette dokumentet er oversatt ved bruk av AI-oversettelsestjenesten [Co-op Translator](https://github.com/Azure/co-op-translator). Selv om vi streber etter nøyaktighet, vennligst vær oppmerksom på at automatiske oversettelser kan inneholde feil eller unøyaktigheter. Det opprinnelige dokumentet på originalspråket skal anses som den autoritative kilden. For kritisk informasjon anbefales profesjonell menneskelig oversettelse. Vi er ikke ansvarlige for eventuelle misforståelser eller feiltolkninger som oppstår ved bruk av denne oversettelsen.