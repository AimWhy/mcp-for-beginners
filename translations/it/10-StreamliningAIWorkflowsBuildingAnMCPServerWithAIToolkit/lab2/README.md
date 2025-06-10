<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "a22b7dd11cd7690f99f9195877cafdc3",
  "translation_date": "2025-06-10T05:46:39+00:00",
  "source_file": "10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab2/README.md",
  "language_code": "it"
}
-->
# 🌐 Modulo 2: Fondamenti di MCP con AI Toolkit

[![Duration](https://img.shields.io/badge/Duration-20%20minutes-blue.svg)]()
[![Difficulty](https://img.shields.io/badge/Difficulty-Intermediate-yellow.svg)]()
[![Prerequisites](https://img.shields.io/badge/Prerequisites-Module%201%20Complete-orange.svg)]()

## 📋 Obiettivi di Apprendimento

Al termine di questo modulo, sarai in grado di:
- ✅ Comprendere l'architettura e i vantaggi del Model Context Protocol (MCP)
- ✅ Esplorare l’ecosistema dei server MCP di Microsoft
- ✅ Integrare i server MCP con AI Toolkit Agent Builder
- ✅ Costruire un agente di automazione browser funzionante usando Playwright MCP
- ✅ Configurare e testare gli strumenti MCP all'interno dei tuoi agenti
- ✅ Esportare e distribuire agenti basati su MCP per l’uso in produzione

## 🎯 Sviluppare sulle Basi del Modulo 1

Nel Modulo 1 abbiamo imparato le basi di AI Toolkit e creato il nostro primo Python Agent. Ora potenzieremo i tuoi agenti collegandoli a strumenti e servizi esterni tramite il rivoluzionario **Model Context Protocol (MCP)**.

Pensalo come un upgrade da una semplice calcolatrice a un computer completo: i tuoi agenti AI avranno la capacità di:
- 🌐 Navigare e interagire con siti web
- 📁 Accedere e gestire file
- 🔧 Integrarsi con sistemi aziendali
- 📊 Elaborare dati in tempo reale da API

## 🧠 Comprendere il Model Context Protocol (MCP)

### 🔍 Cos’è MCP?

Il Model Context Protocol (MCP) è il **“USB-C per le applicazioni AI”**: uno standard aperto rivoluzionario che collega i Large Language Models (LLM) a strumenti esterni, fonti di dati e servizi. Proprio come USB-C ha eliminato il caos dei cavi offrendo un connettore universale, MCP elimina la complessità dell’integrazione AI con un protocollo standardizzato.

### 🎯 Il Problema che MCP Risolve

**Prima di MCP:**
- 🔧 Integrazioni personalizzate per ogni strumento
- 🔄 Dipendenza da fornitori con soluzioni proprietarie  
- 🔒 Vulnerabilità di sicurezza dovute a connessioni ad hoc
- ⏱️ Mesi di sviluppo per integrazioni base

**Con MCP:**
- ⚡ Integrazione plug-and-play degli strumenti
- 🔄 Architettura indipendente dal fornitore
- 🛡️ Best practice di sicurezza integrate
- 🚀 Minuti per aggiungere nuove funzionalità

### 🏗️ Architettura MCP in Dettaglio

MCP segue un’**architettura client-server** che crea un ecosistema sicuro e scalabile:

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

**🔧 Componenti Principali:**

| Componente | Ruolo | Esempi |
|------------|-------|--------|
| **MCP Hosts** | Applicazioni che consumano i servizi MCP | Claude Desktop, VS Code, AI Toolkit |
| **MCP Clients** | Gestori del protocollo (1:1 con i server) | Integrati nelle applicazioni host |
| **MCP Servers** | Espongono funzionalità tramite protocollo standard | Playwright, Files, Azure, GitHub |
| **Transport Layer** | Metodi di comunicazione | stdio, HTTP, WebSockets |


## 🏢 Ecosistema dei Server MCP di Microsoft

Microsoft guida l’ecosistema MCP con una suite completa di server enterprise che rispondono a esigenze aziendali reali.

### 🌟 Server MCP Microsoft in Evidenza

#### 1. ☁️ Azure MCP Server
**🔗 Repository**: [azure/azure-mcp](https://github.com/azure/azure-mcp)  
**🎯 Scopo**: Gestione completa delle risorse Azure con integrazione AI

**✨ Caratteristiche principali:**
- Provisioning infrastrutturale dichiarativo
- Monitoraggio risorse in tempo reale
- Raccomandazioni per ottimizzazione dei costi
- Verifica della conformità alla sicurezza

**🚀 Casi d’uso:**
- Infrastructure-as-Code con assistenza AI
- Scalabilità automatica delle risorse
- Ottimizzazione dei costi cloud
- Automazione dei workflow DevOps

#### 2. 📊 Microsoft Dataverse MCP
**📚 Documentazione**: [Microsoft Dataverse Integration](https://go.microsoft.com/fwlink/?linkid=2320176)  
**🎯 Scopo**: Interfaccia in linguaggio naturale per dati aziendali

**✨ Caratteristiche principali:**
- Query di database in linguaggio naturale
- Comprensione del contesto aziendale
- Template personalizzati per prompt
- Governance dei dati enterprise

**🚀 Casi d’uso:**
- Reportistica di business intelligence
- Analisi dati clienti
- Insights sul pipeline di vendita
- Query per conformità normativa

#### 3. 🌐 Playwright MCP Server
**🔗 Repository**: [microsoft/playwright-mcp](https://github.com/microsoft/playwright-mcp)  
**🎯 Scopo**: Automazione browser e interazione web

**✨ Caratteristiche principali:**
- Automazione cross-browser (Chrome, Firefox, Safari)
- Rilevamento intelligente degli elementi
- Generazione screenshot e PDF
- Monitoraggio traffico di rete

**🚀 Casi d’uso:**
- Workflow di testing automatizzato
- Web scraping ed estrazione dati
- Monitoraggio UI/UX
- Automazione analisi competitiva

#### 4. 📁 Files MCP Server
**🔗 Repository**: [microsoft/files-mcp-server](https://github.com/microsoft/files-mcp-server)  
**🎯 Scopo**: Operazioni intelligenti sul file system

**✨ Caratteristiche principali:**
- Gestione file dichiarativa
- Sincronizzazione contenuti
- Integrazione controllo versioni
- Estrazione metadati

**🚀 Casi d’uso:**
- Gestione documentazione
- Organizzazione repository di codice
- Workflow di pubblicazione contenuti
- Gestione file per pipeline dati

#### 5. 📝 MarkItDown MCP Server
**🔗 Repository**: [microsoft/markitdown](https://github.com/microsoft/markitdown)  
**🎯 Scopo**: Elaborazione avanzata di Markdown

**✨ Caratteristiche principali:**
- Parsing ricco di Markdown
- Conversione formati (MD ↔ HTML ↔ PDF)
- Analisi struttura contenuti
- Elaborazione template

**🚀 Casi d’uso:**
- Workflow di documentazione tecnica
- Sistemi di gestione contenuti
- Generazione report
- Automazione knowledge base

#### 6. 📈 Clarity MCP Server
**📦 Package**: [@microsoft/clarity-mcp-server](https://www.npmjs.com/package/@microsoft/clarity-mcp-server)  
**🎯 Scopo**: Analisi web e insight sul comportamento utenti

**✨ Caratteristiche principali:**
- Analisi dati heatmap
- Registrazioni sessioni utente
- Metriche di performance
- Analisi funnel di conversione

**🚀 Casi d’uso:**
- Ottimizzazione siti web
- Ricerca esperienza utente
- Analisi A/B testing
- Dashboard business intelligence

### 🌍 Ecosistema della Community

Oltre ai server Microsoft, l’ecosistema MCP include:
- **🐙 GitHub MCP**: Gestione repository e analisi codice
- **🗄️ Database MCP**: integrazioni PostgreSQL, MySQL, MongoDB
- **☁️ Cloud Provider MCP**: strumenti AWS, GCP, Digital Ocean
- **📧 Communication MCP**: integrazioni Slack, Teams, Email

## 🛠️ Laboratorio Pratico: Costruire un Agente di Automazione Browser

**🎯 Obiettivo del Progetto**: Creare un agente intelligente di automazione browser usando Playwright MCP server che possa navigare siti, estrarre informazioni ed eseguire interazioni web complesse.

### 🚀 Fase 1: Setup Fondamentale dell’Agente

#### Passo 1: Inizializza il tuo Agente
1. **Apri AI Toolkit Agent Builder**  
2. **Crea un Nuovo Agente** con la seguente configurazione:  
   - **Nome**: `BrowserAgent`
   - **Model**: Choose GPT-4o 

![BrowserAgent](../../../../translated_images/BrowserAgent.09c1adde5e136573b64ab1baecd830049830e295eac66cb18bebb85fb386e00a.it.png)


### 🔧 Phase 2: MCP Integration Workflow

#### Step 3: Add MCP Server Integration
1. **Navigate to Tools Section** in Agent Builder
2. **Click "Add Tool"** to open the integration menu
3. **Select "MCP Server"** from available options

![AddMCP](../../../../translated_images/AddMCP.afe3308ac20aa94469a5717b632d77b2197b9838a438b05d39aeb2db3ec47ef1.it.png)

**🔍 Understanding Tool Types:**
- **Built-in Tools**: Pre-configured AI Toolkit functions
- **MCP Servers**: External service integrations
- **Custom APIs**: Your own service endpoints
- **Function Calling**: Direct model function access

#### Step 4: MCP Server Selection
1. **Choose "MCP Server"** option to proceed
![AddMCPServer](../../../../translated_images/AddMCPServer.69b911ccef872cbd0d0c0c2e6a00806916e1673e543b902a23dee23e6ff54b4c.it.png)

2. **Browse MCP Catalog** to explore available integrations
![MCPCatalog](../../../../translated_images/MCPCatalog.a817d053145699006264f5a475f2b48fbd744e43633f656b6453c15a09ba5130.it.png)


### 🎮 Phase 3: Playwright MCP Configuration

#### Step 5: Select and Configure Playwright
1. **Click "Use Featured MCP Servers"** to access Microsoft's verified servers
2. **Select "Playwright"** from the featured list
3. **Accept Default MCP ID** or customize for your environment

![MCPID](../../../../translated_images/MCPID.67d446052979e819c945ff7b6430196ef587f5217daadd3ca52fa9659c1245c9.it.png)

#### Step 6: Enable Playwright Capabilities
**🔑 Critical Step**: Select **ALL** available Playwright methods for maximum functionality

![Tools](../../../../translated_images/Tools.3ea23c447b4d9feccbd7101e6dcf9e27cb0e5273f351995fde62c5abf9a78b4c.it.png)

**🛠️ Essential Playwright Tools:**
- **Navigation**: `goto`, `goBack`, `goForward`, `reload`
- **Interaction**: `click`, `fill`, `press`, `hover`, `drag`
- **Extraction**: `textContent`, `innerHTML`, `getAttribute`
- **Validation**: `isVisible`, `isEnabled`, `waitForSelector`
- **Capture**: `screenshot`, `pdf`, `video`
- **Network**: `setExtraHTTPHeaders`, `route`, `waitForResponse`

#### Passo 7: Verifica il Successo dell’Integrazione
**✅ Indicatori di Successo:**
- Tutti gli strumenti appaiono nell’interfaccia di Agent Builder
- Nessun messaggio di errore nel pannello di integrazione
- Lo stato del server Playwright mostra “Connected”

![AgentTools](../../../../translated_images/AgentTools.053cfb96a17e02199dcc6563010d2b324d4fc3ebdd24889657a6950647a52f63.it.png)

**🔧 Risoluzione Problemi Comuni:**
- **Connessione Fallita**: Controlla la connettività internet e le impostazioni firewall
- **Strumenti Mancanti**: Assicurati che tutte le funzionalità siano state selezionate durante la configurazione
- **Errori di Permessi**: Verifica che VS Code abbia i permessi di sistema necessari

### 🎯 Fase 4: Prompt Engineering Avanzato

#### Passo 8: Progetta Prompt di Sistema Intelligenti
Crea prompt sofisticati che sfruttino appieno le capacità di Playwright:

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

#### Passo 9: Crea Prompt Utente Dinamici
Progetta prompt che mostrino varie funzionalità:

**🌐 Esempio di Analisi Web:**
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

![Prompt](../../../../translated_images/Prompt.bfc846605db4999f4d9c1b09c710ef63cae7b3057444e68bf07240fb142d9f8f.it.png)

### 🚀 Fase 5: Esecuzione e Test

#### Passo 10: Esegui la Prima Automazione
1. **Clicca su "Run"** per avviare la sequenza di automazione  
2. **Monitora l’Esecuzione in Tempo Reale**:  
   - Il browser Chrome si avvia automaticamente  
   - L’agente naviga sul sito target  
   - Vengono catturati screenshot a ogni step importante  
   - I risultati dell’analisi vengono mostrati in tempo reale

![Browser](../../../../translated_images/Browser.ec011d0bd64d0d112c8a29bd8cc44c76d0bbfd0b019cb2983ef679328435ce5d.it.png)

#### Passo 11: Analizza Risultati e Insight
Esamina l’analisi completa nell’interfaccia di Agent Builder:

![Result](../../../../translated_images/Result.8638f2b6703e9ea6d58d4e4475e39456b6a51d4c787f9bf481bae694d370a69a.it.png)

### 🌟 Fase 6: Funzionalità Avanzate e Distribuzione

#### Passo 12: Esporta e Distribuisci in Produzione
Agent Builder supporta diverse opzioni di deployment:

![Code](../../../../translated_images/Code.d9eeeead0b96db0ca19c5b10ad64cfea8c1d0d1736584262970a4d43e1403d13.it.png)

## 🎓 Riepilogo Modulo 2 & Prossimi Passi

### 🏆 Obiettivo Raggiunto: Maestro dell’Integrazione MCP

**✅ Competenze Acquisite:**
- [ ] Comprendere architettura e vantaggi MCP
- [ ] Navigare l’ecosistema dei server MCP Microsoft
- [ ] Integrare Playwright MCP con AI Toolkit
- [ ] Costruire agenti di automazione browser sofisticati
- [ ] Prompt engineering avanzato per automazione web

### 📚 Risorse Aggiuntive

- **🔗 Specifica MCP**: [Documentazione Ufficiale del Protocollo](https://modelcontextprotocol.io/)  
- **🛠️ API Playwright**: [Riferimento Completo Metodi](https://playwright.dev/docs/api/class-playwright)  
- **🏢 Server MCP Microsoft**: [Guida all’Integrazione Enterprise](https://github.com/microsoft/mcp-servers)  
- **🌍 Esempi dalla Community**: [Galleria Server MCP](https://github.com/modelcontextprotocol/servers)  

**🎉 Congratulazioni!** Hai padroneggiato l’integrazione MCP e ora puoi costruire agenti AI pronti per la produzione con capacità di strumenti esterni!

### 🔜 Prosegui al Modulo Successivo

Pronto a portare le tue competenze MCP al livello successivo? Procedi a **[Modulo 3: Sviluppo Avanzato MCP con AI Toolkit](../lab3/README.md)** dove imparerai a:
- Creare i tuoi server MCP personalizzati
- Configurare e utilizzare l’ultima SDK Python MCP
- Impostare MCP Inspector per il debugging
- Padroneggiare i workflow avanzati di sviluppo server MCP
- Costruire da zero un Weather MCP Server

**Disclaimer**:  
Questo documento è stato tradotto utilizzando il servizio di traduzione AI [Co-op Translator](https://github.com/Azure/co-op-translator). Pur impegnandoci per l'accuratezza, si prega di notare che le traduzioni automatiche possono contenere errori o imprecisioni. Il documento originale nella sua lingua nativa deve essere considerato la fonte autorevole. Per informazioni critiche, si raccomanda la traduzione professionale effettuata da un umano. Non siamo responsabili per eventuali malintesi o interpretazioni errate derivanti dall'uso di questa traduzione.