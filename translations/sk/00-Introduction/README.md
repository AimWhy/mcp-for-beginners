<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "25a94c681cf43612ff394d8cf78a74de",
  "translation_date": "2025-05-27T16:12:17+00:00",
  "source_file": "00-Introduction/README.md",
  "language_code": "sk"
}
-->
# Úvod do Model Context Protocol (MCP): Prečo je dôležitý pre škálovateľné AI aplikácie

Generatívne AI aplikácie predstavujú veľký krok vpred, pretože často umožňujú používateľovi komunikovať s aplikáciou pomocou prirodzených jazykových príkazov. Avšak, keď do takýchto aplikácií investujete viac času a zdrojov, chcete mať istotu, že môžete jednoducho integrovať funkcie a zdroje tak, aby bolo jednoduché ich rozširovať, aby vaša aplikácia zvládla používanie viacerých modelov a dokázala riešiť rôzne špecifiká modelov. Skrátka, budovanie generatívnych AI aplikácií je na začiatku jednoduché, no s rastom a zvyšujúcou sa zložitosťou je potrebné začať definovať architektúru a pravdepodobne sa spoľahnúť na štandard, ktorý zabezpečí konzistentné budovanie aplikácií. Práve tu prichádza MCP, ktorý veci organizuje a poskytuje štandard.

---

## **🔍 Čo je Model Context Protocol (MCP)?**

**Model Context Protocol (MCP)** je **otvorený, štandardizovaný rozhranie**, ktoré umožňuje veľkým jazykovým modelom (LLM) plynulo komunikovať s externými nástrojmi, API a zdrojmi dát. Poskytuje konzistentnú architektúru na rozšírenie funkčnosti AI modelov nad rámec ich trénovacích dát, čím umožňuje inteligentnejšie, škálovateľnejšie a pružnejšie AI systémy.

---

## **🎯 Prečo je štandardizácia v AI dôležitá**

Ako sa generatívne AI aplikácie stávajú zložitejšími, je nevyhnutné prijať štandardy, ktoré zabezpečia **škálovateľnosť, rozšíriteľnosť** a **udržateľnosť**. MCP rieši tieto potreby tým, že:

- Zjednocuje integrácie modelov s nástrojmi
- Znižuje krehké, jednorazové riešenia na mieru
- Umožňuje koexistenciu viacerých modelov v jednom ekosystéme

---

## **📚 Ciele učenia**

Na konci tohto článku budete schopní:

- Definovať **Model Context Protocol (MCP)** a jeho použitia
- Pochopiť, ako MCP štandardizuje komunikáciu model-nástroj
- Identifikovať základné komponenty architektúry MCP
- Preskúmať reálne použitia MCP v podnikových a vývojárskych prostrediach

---

## **💡 Prečo je Model Context Protocol (MCP) prelomový**

### **🔗 MCP rieši fragmentáciu v AI interakciách**

Pred MCP vyžadovala integrácia modelov s nástrojmi:

- Vlastný kód pre každý pár model-nástroj
- Nestandardné API pre každého dodávateľa
- Časté prerušenia kvôli aktualizáciám
- Slabú škálovateľnosť pri pridaní viacerých nástrojov

### **✅ Výhody štandardizácie MCP**

| **Výhoda**               | **Popis**                                                                       |
|--------------------------|---------------------------------------------------------------------------------|
| Interoperabilita         | LLM pracujú bez problémov s nástrojmi od rôznych dodávateľov                   |
| Konzistentnosť           | Jednotné správanie naprieč platformami a nástrojmi                             |
| Opätovná použiteľnosť    | Nástroje vytvorené raz môžu byť použité v rôznych projektoch a systémoch       |
| Rýchlejší vývoj          | Skrátenie času vývoja vďaka štandardizovaným, plug-and-play rozhraniam         |

---

## **🧱 Prehľad architektúry MCP na vysokej úrovni**

MCP funguje na princípe **klient-server modelu**, kde:

- **MCP Hosts** prevádzkujú AI modely
- **MCP Clients** iniciujú požiadavky
- **MCP Servers** poskytujú kontext, nástroje a schopnosti

### **Kľúčové komponenty:**

- **Resources** – statické alebo dynamické dáta pre modely  
- **Prompts** – preddefinované pracovné postupy pre riadenú generáciu  
- **Tools** – spustiteľné funkcie ako vyhľadávanie, výpočty  
- **Sampling** – agentné správanie cez rekurzívne interakcie

---

## Ako MCP servery fungujú

MCP servery pracujú nasledovne:

- **Priebeh požiadavky**: 
    1. MCP klient pošle požiadavku AI modelu bežiacemu na MCP hostiteľovi.
    2. AI model rozpozná, kedy potrebuje externé nástroje alebo dáta.
    3. Model komunikuje s MCP serverom pomocou štandardizovaného protokolu.

- **Funkcie MCP servera**:
    - Registrácia nástrojov: Udržiava katalóg dostupných nástrojov a ich schopností.
    - Overovanie: Kontroluje oprávnenia na prístup k nástrojom.
    - Spracovanie požiadaviek: Spracováva prichádzajúce požiadavky na nástroje od modelu.
    - Formátovanie odpovedí: Štrukturuje výstupy nástrojov do formátu, ktorý model rozumie.

- **Vykonávanie nástrojov**: 
    - Server smeruje požiadavky na príslušné externé nástroje
    - Nástroje vykonávajú svoje špecializované funkcie (vyhľadávanie, výpočty, databázové dotazy atď.)
    - Výsledky sa vracajú modelu v konzistentnom formáte.

- **Dokončenie odpovede**: 
    - AI model začleňuje výstupy nástrojov do svojej odpovede.
    - Konečná odpoveď sa posiela späť klientskej aplikácii.

```mermaid
graph TD
    A[AI Model in MCP Host] <-->|MCP Protocol| B[MCP Server]
    B <-->|Tool Interface| C[Tool 1: Web Search]
    B <-->|Tool Interface| D[Tool 2: Calculator]
    B <-->|Tool Interface| E[Tool 3: Database Access]
    B <-->|Tool Interface| F[Tool 4: File System]
    
    Client[MCP Client/Application] -->|Sends Request| A
    A -->|Returns Response| Client
    
    subgraph "MCP Server Components"
        B
        G[Tool Registry]
        H[Authentication]
        I[Request Handler]
        J[Response Formatter]
    end
    
    B <--> G
    B <--> H
    B <--> I
    B <--> J
    
    style A fill:#f9d5e5,stroke:#333,stroke-width:2px
    style B fill:#eeeeee,stroke:#333,stroke-width:2px
    style Client fill:#d5e8f9,stroke:#333,stroke-width:2px
    style C fill:#c2f0c2,stroke:#333,stroke-width:1px
    style D fill:#c2f0c2,stroke:#333,stroke-width:1px
    style E fill:#c2f0c2,stroke:#333,stroke-width:1px
    style F fill:#c2f0c2,stroke:#333,stroke-width:1px    
```

## 👨‍💻 Ako vytvoriť MCP server (s príkladmi)

MCP servery vám umožňujú rozšíriť schopnosti LLM tým, že poskytujú dáta a funkcionalitu.

Chcete to vyskúšať? Tu sú príklady vytvorenia jednoduchého MCP servera v rôznych jazykoch:

- **Python príklad**: https://github.com/modelcontextprotocol/python-sdk

- **TypeScript príklad**: https://github.com/modelcontextprotocol/typescript-sdk

- **Java príklad**: https://github.com/modelcontextprotocol/java-sdk

- **C#/.NET príklad**: https://github.com/modelcontextprotocol/csharp-sdk

## 🌍 Reálne použitia MCP

MCP umožňuje širokú škálu aplikácií rozširujúcich schopnosti AI:

| **Použitie**                | **Popis**                                                                    |
|-----------------------------|------------------------------------------------------------------------------|
| Integrácia podnikových dát  | Prepojenie LLM s databázami, CRM alebo internými nástrojmi                   |
| Agentné AI systémy          | Umožnenie autonómnych agentov s prístupom k nástrojom a rozhodovacími procesmi|
| Multimodálne aplikácie      | Kombinácia textových, obrazových a audio nástrojov v jednej AI aplikácii     |
| Integrácia dát v reálnom čase | Vkladanie živých dát do AI interakcií pre presnejšie a aktuálne výstupy     |

### 🧠 MCP = Univerzálny štandard pre AI interakcie

Model Context Protocol (MCP) funguje ako univerzálny štandard pre AI interakcie, podobne ako USB-C štandardizoval fyzické pripojenia zariadení. V AI svete MCP poskytuje konzistentné rozhranie, ktoré umožňuje modelom (klientom) plynulo integrovať externé nástroje a poskytovateľov dát (servery). Tým odstraňuje potrebu rôznych, vlastných protokolov pre každé API alebo dátový zdroj.

Pod MCP je nástroj kompatibilný s MCP (nazývaný MCP server) navrhnutý podľa jednotného štandardu. Tieto servery môžu uvádzať nástroje alebo akcie, ktoré ponúkajú, a vykonávať ich na požiadanie AI agenta. Platformy AI agentov podporujúce MCP dokážu objavovať dostupné nástroje na serveroch a vyvolávať ich prostredníctvom tohto štandardného protokolu.

### 💡 Uľahčuje prístup k vedomostiam

Okrem poskytovania nástrojov MCP uľahčuje aj prístup k vedomostiam. Umožňuje aplikáciám poskytovať kontext veľkým jazykovým modelom (LLM) prepojením na rôzne zdroje dát. Napríklad MCP server môže predstavovať firemnú dokumentačnú databázu, čo umožňuje agentom na požiadanie vyhľadávať relevantné informácie. Iný server môže spravovať konkrétne akcie, ako je odosielanie e-mailov alebo aktualizácia záznamov. Z pohľadu agenta sú to jednoducho nástroje, ktoré môže použiť – niektoré vracajú dáta (vedomostný kontext), iné vykonávajú akcie. MCP efektívne spravuje obe.

Agent pripojený k MCP serveru automaticky získa informácie o dostupných schopnostiach a prístupných dátach cez štandardný formát. Táto štandardizácia umožňuje dynamickú dostupnosť nástrojov. Napríklad pridaním nového MCP servera do systému agenta sa jeho funkcie okamžite stanú použiteľnými bez nutnosti ďalšej úpravy inštrukcií agenta.

Táto zjednodušená integrácia korešponduje s priebehom znázorneným v mermaid diagrame, kde servery poskytujú nástroje aj vedomosti, čím zabezpečujú hladkú spoluprácu medzi systémami.

### 👉 Príklad: škálovateľné riešenie agenta

```mermaid
graph TD
    User -->|Prompt| LLM
    LLM -->|Response| User
    LLM -->|MCP| ServerA
    LLM -->|MCP| ServerB
    ServerA -->|Universal connector| ServerB
    ServerA --> KnowledgeA
    ServerA --> ToolsA
    ServerB --> KnowledgeB
    ServerB --> ToolsB

    subgraph Server A
        KnowledgeA[Knowledge]
        ToolsA[Tools]
    end

    subgraph Server B
        KnowledgeB[Knowledge]
        ToolsB[Tools]
    end
```

### 🔄 Pokročilé scenáre MCP s integráciou LLM na strane klienta

Nad rámec základnej architektúry MCP existujú pokročilé scenáre, kde klient aj server obsahujú LLM, čo umožňuje sofistikovanejšie interakcie:

```mermaid
sequenceDiagram
    autonumber
    actor User as 👤 User
    participant ClientApp as 🖥️ Client App
    participant ClientLLM as 🧠 Client LLM
    participant Server1 as 🔧 MCP Server 1
    participant Server2 as 📚 MCP Server 2
    participant ServerLLM as 🤖 Server LLM
    
    %% Discovery Phase
    rect rgb(220, 240, 255)
        Note over ClientApp, Server2: TOOL DISCOVERY PHASE
        ClientApp->>+Server1: Request available tools/resources
        Server1-->>-ClientApp: Return tool list (JSON)
        ClientApp->>+Server2: Request available tools/resources
        Server2-->>-ClientApp: Return tool list (JSON)
        Note right of ClientApp: Store combined tool<br/>catalog locally
    end
    
    %% User Interaction
    rect rgb(255, 240, 220)
        Note over User, ClientLLM: USER INTERACTION PHASE
        User->>+ClientApp: Enter natural language prompt
        ClientApp->>+ClientLLM: Forward prompt + tool catalog
        ClientLLM->>-ClientLLM: Analyze prompt & select tools
    end
    
    %% Scenario A: Direct Tool Calling
    alt Direct Tool Calling
        rect rgb(220, 255, 220)
            Note over ClientApp, Server1: SCENARIO A: DIRECT TOOL CALLING
            ClientLLM->>+ClientApp: Request tool execution
            ClientApp->>+Server1: Execute specific tool
            Server1-->>-ClientApp: Return results
            ClientApp->>+ClientLLM: Process results
            ClientLLM-->>-ClientApp: Generate response
            ClientApp-->>-User: Display final answer
        end
    
    %% Scenario B: Feature Negotiation (VS Code style)
    else Feature Negotiation (VS Code style)
        rect rgb(255, 220, 220)
            Note over ClientApp, ServerLLM: SCENARIO B: FEATURE NEGOTIATION
            ClientLLM->>+ClientApp: Identify needed capabilities
            ClientApp->>+Server2: Negotiate features/capabilities
            Server2->>+ServerLLM: Request additional context
            ServerLLM-->>-Server2: Provide context
            Server2-->>-ClientApp: Return available features
            ClientApp->>+Server2: Call negotiated tools
            Server2-->>-ClientApp: Return results
            ClientApp->>+ClientLLM: Process results
            ClientLLM-->>-ClientApp: Generate response
            ClientApp-->>-User: Display final answer
        end
    end
```

## 🔐 Praktické výhody MCP

Tu sú praktické výhody použitia MCP:

- **Aktuálnosť**: Modely majú prístup k najnovším informáciám nad rámec trénovacích dát
- **Rozšírenie schopností**: Modely môžu využiť špecializované nástroje pre úlohy, na ktoré neboli trénované
- **Zníženie halucinácií**: Externé zdroje dát poskytujú faktické základy
- **Súkromie**: Citlivé dáta môžu zostať v zabezpečených prostrediach namiesto vloženia do promptov

## 📌 Kľúčové poznatky

Nasledujúce sú kľúčové poznatky pre použitie MCP:

- **MCP** štandardizuje spôsob, akým AI modely komunikujú s nástrojmi a dátami
- Podporuje **rozšíriteľnosť, konzistentnosť a interoperabilitu**
- MCP pomáha **skrátiť čas vývoja, zlepšiť spoľahlivosť a rozšíriť schopnosti modelov**
- Klient-server architektúra **umožňuje flexibilné, rozšíriteľné AI aplikácie**

## 🧠 Cvičenie

Premyslite si AI aplikáciu, ktorú by ste chceli vytvoriť.

- Aké **externé nástroje alebo dáta** by mohli zlepšiť jej schopnosti?
- Ako by MCP mohol uľahčiť integráciu a spraviť ju spoľahlivejšou?

## Dodatočné zdroje

- [MCP GitHub Repository](https://github.com/modelcontextprotocol)

## Čo bude ďalej

Ďalej: [Chapter 1: Core Concepts](/01-CoreConcepts/README.md)

**Zrieknutie sa zodpovednosti**:  
Tento dokument bol preložený pomocou AI prekladateľskej služby [Co-op Translator](https://github.com/Azure/co-op-translator). Hoci sa snažíme o presnosť, prosím, majte na pamäti, že automatické preklady môžu obsahovať chyby alebo nepresnosti. Originálny dokument v jeho pôvodnom jazyku by mal byť považovaný za autoritatívny zdroj. Pre kritické informácie sa odporúča profesionálny ľudský preklad. Nie sme zodpovední za akékoľvek nedorozumenia alebo nesprávne interpretácie vyplývajúce z použitia tohto prekladu.