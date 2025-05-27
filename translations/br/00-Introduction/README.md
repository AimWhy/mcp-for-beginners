<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "25a94c681cf43612ff394d8cf78a74de",
  "translation_date": "2025-05-27T16:02:40+00:00",
  "source_file": "00-Introduction/README.md",
  "language_code": "br"
}
-->
# Introduction au Model Context Protocol (MCP) : Pourquoi c’est important pour les applications IA évolutives

Les applications d’IA générative représentent une avancée majeure, car elles permettent souvent à l’utilisateur d’interagir avec l’application via des instructions en langage naturel. Cependant, à mesure que l’on investit plus de temps et de ressources dans ces applications, il est important de pouvoir intégrer facilement des fonctionnalités et des ressources de manière à ce que l’extension soit simple, que l’application puisse gérer plusieurs modèles simultanément, et qu’elle prenne en compte les spécificités de chaque modèle. En résumé, créer des applications d’IA générative est simple au départ, mais à mesure qu’elles grandissent et deviennent plus complexes, il faut commencer à définir une architecture et s’appuyer sur une norme pour garantir une construction cohérente des applications. C’est là qu’intervient le MCP pour organiser tout cela et fournir un standard.

---

## **🔍 Qu’est-ce que le Model Context Protocol (MCP) ?**

Le **Model Context Protocol (MCP)** est une **interface ouverte et standardisée** qui permet aux grands modèles de langage (LLM) d’interagir sans accroc avec des outils externes, des API et des sources de données. Il offre une architecture cohérente pour enrichir les fonctionnalités des modèles d’IA au-delà de leurs données d’entraînement, permettant ainsi des systèmes d’IA plus intelligents, évolutifs et réactifs.

---

## **🎯 Pourquoi la standardisation est-elle importante en IA ?**

À mesure que les applications d’IA générative se complexifient, il devient essentiel d’adopter des standards garantissant **l’évolutivité, l’extensibilité** et la **maintenabilité**. MCP répond à ces besoins en :

- Unifiant les intégrations modèle-outil  
- Réduisant les solutions personnalisées fragiles et ponctuelles  
- Permettant à plusieurs modèles de coexister dans un même écosystème  

---

## **📚 Objectifs d’apprentissage**

À la fin de cet article, vous serez capable de :

- Définir le **Model Context Protocol (MCP)** et ses cas d’usage  
- Comprendre comment MCP standardise la communication entre modèles et outils  
- Identifier les composants clés de l’architecture MCP  
- Explorer des applications concrètes du MCP en entreprise et en développement  

---

## **💡 Pourquoi le Model Context Protocol (MCP) change la donne**

### **🔗 MCP résout la fragmentation dans les interactions IA**

Avant MCP, intégrer des modèles avec des outils nécessitait :

- Du code personnalisé pour chaque paire outil-modèle  
- Des API non standardisées propres à chaque fournisseur  
- Des ruptures fréquentes dues aux mises à jour  
- Une mauvaise évolutivité avec l’ajout d’outils  

### **✅ Avantages de la standardisation MCP**

| **Avantage**             | **Description**                                                               |
|-------------------------|-------------------------------------------------------------------------------|
| Interopérabilité        | Les LLM fonctionnent de manière fluide avec des outils de différents fournisseurs |
| Cohérence               | Comportement uniforme sur toutes les plateformes et outils                   |
| Réutilisabilité         | Les outils développés une fois peuvent être utilisés dans plusieurs projets  |
| Développement accéléré  | Réduction du temps de développement grâce à des interfaces standardisées et plug-and-play |

---

## **🧱 Vue d’ensemble de l’architecture MCP**

MCP suit un **modèle client-serveur**, où :

- Les **MCP Hosts** hébergent les modèles IA  
- Les **MCP Clients** initient les requêtes  
- Les **MCP Servers** fournissent contexte, outils et capacités  

### **Composants clés :**

- **Ressources** – Données statiques ou dynamiques pour les modèles  
- **Prompts** – Flux de travail prédéfinis pour une génération guidée  
- **Outils** – Fonctions exécutables comme la recherche, les calculs  
- **Sampling** – Comportement agentique via des interactions récursives  

---

## Fonctionnement des MCP Servers

Les serveurs MCP fonctionnent de la manière suivante :

- **Flux de requête** :  
    1. Le MCP Client envoie une requête au modèle IA hébergé dans un MCP Host.  
    2. Le modèle IA détecte quand il a besoin d’outils ou de données externes.  
    3. Le modèle communique avec le MCP Server via le protocole standardisé.

- **Fonctionnalités du MCP Server** :  
    - Registre des outils : Gère un catalogue des outils disponibles et leurs capacités.  
    - Authentification : Vérifie les permissions d’accès aux outils.  
    - Gestionnaire de requêtes : Traite les demandes d’outils venant du modèle.  
    - Formateur de réponses : Structure les sorties des outils dans un format compréhensible par le modèle.

- **Exécution des outils** :  
    - Le serveur redirige les requêtes vers les outils externes appropriés  
    - Les outils exécutent leurs fonctions spécialisées (recherche, calcul, requêtes en base, etc.)  
    - Les résultats sont retournés au modèle dans un format uniforme.

- **Finalisation de la réponse** :  
    - Le modèle IA intègre les résultats des outils dans sa réponse.  
    - La réponse finale est renvoyée à l’application cliente.

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

## 👨‍💻 Comment construire un MCP Server (avec exemples)

Les serveurs MCP vous permettent d’étendre les capacités des LLM en fournissant données et fonctionnalités.

Prêt à essayer ? Voici des exemples pour créer un serveur MCP simple dans différents langages :

- **Exemple Python** : https://github.com/modelcontextprotocol/python-sdk

- **Exemple TypeScript** : https://github.com/modelcontextprotocol/typescript-sdk

- **Exemple Java** : https://github.com/modelcontextprotocol/java-sdk

- **Exemple C#/.NET** : https://github.com/modelcontextprotocol/csharp-sdk


## 🌍 Cas d’usage concrets pour MCP

MCP permet une large gamme d’applications en étendant les capacités de l’IA :

| **Application**              | **Description**                                                                 |
|------------------------------|---------------------------------------------------------------------------------|
| Intégration de données en entreprise | Connecter les LLM aux bases de données, CRM ou outils internes                  |
| Systèmes IA agentiques       | Permettre aux agents autonomes d’accéder aux outils et de suivre des workflows décisionnels |
| Applications multimodales    | Combiner texte, image et audio dans une application IA unifiée                  |
| Intégration de données en temps réel | Intégrer des données en direct dans les interactions IA pour des résultats plus précis et actuels |

### 🧠 MCP = Standard universel pour les interactions IA

Le Model Context Protocol (MCP) agit comme un standard universel pour les interactions IA, à l’image de la normalisation USB-C pour les connexions physiques des appareils. Dans l’univers de l’IA, MCP fournit une interface cohérente, permettant aux modèles (clients) de s’intégrer sans effort aux outils externes et fournisseurs de données (serveurs). Cela élimine le besoin de protocoles personnalisés et variés pour chaque API ou source de données.

Avec MCP, un outil compatible (appelé serveur MCP) suit une norme unifiée. Ces serveurs peuvent lister les outils ou actions qu’ils proposent et exécuter ces actions lorsqu’un agent IA les sollicite. Les plateformes d’agents IA compatibles MCP peuvent découvrir les outils disponibles sur les serveurs et les invoquer via ce protocole standard.

### 💡 Facilite l’accès à la connaissance

Au-delà de la fourniture d’outils, MCP facilite aussi l’accès à la connaissance. Il permet aux applications de fournir du contexte aux grands modèles de langage (LLM) en les reliant à diverses sources de données. Par exemple, un serveur MCP peut représenter le dépôt documentaire d’une entreprise, permettant aux agents de récupérer des informations pertinentes à la demande. Un autre serveur pourrait gérer des actions spécifiques comme l’envoi d’e-mails ou la mise à jour d’enregistrements. Du point de vue de l’agent, ce sont simplement des outils utilisables : certains retournent des données (contexte de connaissance), d’autres effectuent des actions. MCP gère efficacement les deux.

Un agent connecté à un serveur MCP apprend automatiquement les capacités et données accessibles via un format standard. Cette standardisation permet une disponibilité dynamique des outils. Par exemple, ajouter un nouveau serveur MCP au système d’un agent rend ses fonctions immédiatement utilisables sans nécessiter de personnalisation supplémentaire des instructions de l’agent.

Cette intégration fluide correspond au flux illustré dans le diagramme mermaid, où les serveurs fournissent à la fois outils et connaissances, assurant une collaboration sans faille entre les systèmes.

### 👉 Exemple : Solution d’agent évolutive

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

### 🔄 Scénarios avancés MCP avec intégration LLM côté client

Au-delà de l’architecture MCP basique, il existe des scénarios avancés où client et serveur contiennent tous deux des LLM, permettant des interactions plus sophistiquées :

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

## 🔐 Avantages pratiques du MCP

Voici les bénéfices concrets de l’utilisation du MCP :

- **Actualité** : Les modèles peuvent accéder à des informations à jour, au-delà de leurs données d’entraînement  
- **Extension des capacités** : Les modèles peuvent utiliser des outils spécialisés pour des tâches non couvertes par leur entraînement  
- **Réduction des hallucinations** : Les sources de données externes apportent un ancrage factuel  
- **Confidentialité** : Les données sensibles peuvent rester dans des environnements sécurisés sans être intégrées aux prompts  

## 📌 Points clés à retenir

Voici les points essentiels à retenir sur l’utilisation du MCP :

- **MCP** standardise la manière dont les modèles IA interagissent avec outils et données  
- Favorise **extensibilité, cohérence et interopérabilité**  
- MCP aide à **réduire le temps de développement, améliorer la fiabilité et étendre les capacités des modèles**  
- L’architecture client-serveur **permet des applications IA flexibles et extensibles**  

## 🧠 Exercice

Réfléchissez à une application IA que vous souhaitez développer.

- Quels **outils ou données externes** pourraient améliorer ses capacités ?  
- Comment MCP pourrait-il rendre l’intégration **plus simple et plus fiable** ?  

## Ressources supplémentaires

- [MCP GitHub Repository](https://github.com/modelcontextprotocol)


## Et après ?

Suivant : [Chapitre 1 : Concepts de base](/01-CoreConcepts/README.md)

**Aviso Legal**:  
Este documento foi traduzido utilizando o serviço de tradução por IA [Co-op Translator](https://github.com/Azure/co-op-translator). Embora nos esforcemos para garantir a precisão, esteja ciente de que traduções automáticas podem conter erros ou imprecisões. O documento original em seu idioma nativo deve ser considerado a fonte autorizada. Para informações críticas, recomenda-se a tradução profissional humana. Não nos responsabilizamos por quaisquer mal-entendidos ou interpretações incorretas decorrentes do uso desta tradução.