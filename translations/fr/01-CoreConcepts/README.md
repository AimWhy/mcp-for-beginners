<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "056918462dca9b8f75901709fb8f470c",
  "translation_date": "2025-05-16T15:44:35+00:00",
  "source_file": "01-CoreConcepts/README.md",
  "language_code": "fr"
}
-->
# 📖 Concepts de base MCP : Maîtriser le Model Context Protocol pour l’intégration de l’IA

Le Model Context Protocol (MCP) est un cadre standardisé puissant qui optimise la communication entre les grands modèles de langage (LLM) et les outils, applications et sources de données externes. Ce guide optimisé pour le référencement vous présente les concepts clés du MCP, afin que vous compreniez son architecture client-serveur, ses composants essentiels, les mécanismes de communication et les meilleures pratiques d’implémentation.

## Vue d’ensemble

Cette leçon explore l’architecture fondamentale et les composants qui constituent l’écosystème du Model Context Protocol (MCP). Vous découvrirez l’architecture client-serveur, les composants clés et les mécanismes de communication qui animent les interactions MCP.

## 👩‍🎓 Objectifs d’apprentissage principaux

À la fin de cette leçon, vous serez capable de :

- Comprendre l’architecture client-serveur du MCP.
- Identifier les rôles et responsabilités des Hosts, Clients et Servers.
- Analyser les fonctionnalités principales qui font du MCP une couche d’intégration flexible.
- Appréhender le flux d’information au sein de l’écosystème MCP.
- Obtenir des exemples pratiques en .NET, Java, Python et JavaScript.

## 🔎 Architecture MCP : un regard approfondi

L’écosystème MCP repose sur un modèle client-serveur. Cette structure modulaire permet aux applications IA d’interagir efficacement avec des outils, bases de données, API et ressources contextuelles. Décomposons cette architecture en ses composants essentiels.

### 1. Hosts

Dans le Model Context Protocol (MCP), les Hosts jouent un rôle crucial en tant qu’interface principale par laquelle les utilisateurs interagissent avec le protocole. Les Hosts sont des applications ou environnements qui initient les connexions avec les serveurs MCP pour accéder aux données, outils et prompts. Par exemple, des environnements de développement intégrés (IDE) comme Visual Studio Code, des outils IA comme Claude Desktop, ou des agents personnalisés conçus pour des tâches spécifiques.

**Les Hosts** sont des applications LLM qui initient les connexions. Ils :

- Exécutent ou interagissent avec les modèles IA pour générer des réponses.
- Initient les connexions avec les serveurs MCP.
- Gèrent le déroulement des conversations et l’interface utilisateur.
- Contrôlent les permissions et les contraintes de sécurité.
- Gèrent le consentement utilisateur pour le partage de données et l’exécution d’outils.

### 2. Clients

Les Clients sont des composants essentiels qui facilitent l’interaction entre les Hosts et les serveurs MCP. Ils agissent comme intermédiaires, permettant aux Hosts d’accéder et d’utiliser les fonctionnalités fournies par les serveurs MCP. Ils jouent un rôle clé pour assurer une communication fluide et un échange de données efficace au sein de l’architecture MCP.

**Les Clients** sont des connecteurs intégrés à l’application Host. Ils :

- Envoient des requêtes aux serveurs avec des prompts/instructions.
- Négocient les capacités avec les serveurs.
- Gèrent les requêtes d’exécution d’outils provenant des modèles.
- Traitent et affichent les réponses aux utilisateurs.

### 3. Servers

Les Servers sont responsables du traitement des requêtes des clients MCP et de la fourniture des réponses appropriées. Ils gèrent diverses opérations telles que la récupération de données, l’exécution d’outils et la génération de prompts. Les serveurs garantissent une communication efficace et fiable entre clients et Hosts, tout en maintenant l’intégrité du processus d’interaction.

**Les Servers** sont des services qui fournissent contexte et capacités. Ils :

- Enregistrent les fonctionnalités disponibles (ressources, prompts, outils).
- Reçoivent et exécutent les appels d’outils du client.
- Fournissent des informations contextuelles pour améliorer les réponses du modèle.
- Restituent les résultats au client.
- Maintiennent l’état des interactions lorsque nécessaire.

Les serveurs peuvent être développés par quiconque pour étendre les capacités du modèle avec des fonctionnalités spécialisées.

### 4. Fonctionnalités des Servers

Les serveurs du Model Context Protocol (MCP) offrent des blocs de construction fondamentaux qui permettent des interactions riches entre clients, hosts et modèles de langage. Ces fonctionnalités visent à enrichir les capacités du MCP en proposant un contexte structuré, des outils et des prompts.

Les serveurs MCP peuvent proposer les fonctionnalités suivantes :

#### 📑 Ressources

Les ressources dans le Model Context Protocol (MCP) englobent différents types de contexte et de données utilisables par les utilisateurs ou les modèles IA. Elles comprennent :

- **Données contextuelles** : Informations et contexte que les utilisateurs ou modèles IA peuvent exploiter pour la prise de décision et l’exécution de tâches.
- **Bases de connaissances et dépôts documentaires** : Collections de données structurées et non structurées, telles que articles, manuels et publications scientifiques, offrant des informations précieuses.
- **Fichiers locaux et bases de données** : Données stockées localement sur des appareils ou dans des bases de données, accessibles pour traitement et analyse.
- **APIs et services web** : Interfaces et services externes fournissant des données et fonctionnalités supplémentaires, permettant l’intégration avec diverses ressources et outils en ligne.

Un exemple de ressource peut être un schéma de base de données ou un fichier accessible comme suit :

```text
file://log.txt
database://schema
```

### 🤖 Prompts

Les prompts dans le Model Context Protocol (MCP) incluent divers modèles prédéfinis et schémas d’interaction conçus pour fluidifier les flux de travail des utilisateurs et améliorer la communication. Ceux-ci comprennent :

- **Messages et workflows templatisés** : Messages et processus pré-structurés guidant les utilisateurs à travers des tâches et interactions spécifiques.
- **Schémas d’interaction prédéfinis** : Séquences standardisées d’actions et de réponses facilitant une communication cohérente et efficace.
- **Modèles de conversation spécialisés** : Templates personnalisables adaptés à des types spécifiques de conversations, garantissant des interactions pertinentes et contextuellement appropriées.

Un modèle de prompt peut ressembler à ceci :

```markdown
Generate a product slogan based on the following {{product}} with the following {{keywords}}
```

#### ⛏️ Outils

Les outils dans le Model Context Protocol (MCP) sont des fonctions que le modèle IA peut exécuter pour accomplir des tâches spécifiques. Ces outils sont conçus pour renforcer les capacités du modèle IA en fournissant des opérations structurées et fiables. Les points clés sont :

- **Fonctions exécutables par le modèle IA** : Les outils sont des fonctions que le modèle peut invoquer pour réaliser diverses tâches.
- **Nom unique et description** : Chaque outil possède un nom distinct et une description détaillée expliquant son objectif et sa fonctionnalité.
- **Paramètres et résultats** : Les outils acceptent des paramètres spécifiques et renvoient des sorties structurées, assurant des résultats cohérents et prévisibles.
- **Fonctions distinctes** : Les outils réalisent des fonctions précises comme des recherches web, des calculs ou des requêtes en base de données.

Un exemple d’outil pourrait ressembler à ceci :

```typescript
server.tool(
  "GetProducts"
  {
    pageSize: z.string().optional(),
    pageCount: z.string().optional()
  }, () => {
    // return results from API
  }
)
```

## Fonctionnalités des Clients

Dans le Model Context Protocol (MCP), les clients offrent plusieurs fonctionnalités clés aux serveurs, améliorant la fonctionnalité globale et l’interaction au sein du protocole. L’une des fonctionnalités notables est le Sampling.

### 👉 Sampling

- **Comportements agentiques initiés par le serveur** : Les clients permettent aux serveurs d’initier des actions ou comportements spécifiques de manière autonome, renforçant les capacités dynamiques du système.
- **Interactions récursives avec les LLM** : Cette fonctionnalité autorise des interactions récursives avec les grands modèles de langage, permettant un traitement plus complexe et itératif des tâches.
- **Demande de complétions supplémentaires du modèle** : Les serveurs peuvent solliciter des complétions additionnelles du modèle, garantissant que les réponses soient complètes et contextuellement pertinentes.

## Flux d’information dans MCP

Le Model Context Protocol (MCP) définit un flux structuré d’informations entre hosts, clients, serveurs et modèles. Comprendre ce flux clarifie la manière dont les requêtes utilisateur sont traitées et comment les outils externes et données sont intégrés aux réponses du modèle.

- **Le Host initie la connexion**  
  L’application host (comme un IDE ou une interface de chat) établit une connexion avec un serveur MCP, généralement via STDIO, WebSocket ou un autre transport supporté.

- **Négociation des capacités**  
  Le client (intégré dans le host) et le serveur échangent des informations sur leurs fonctionnalités, outils, ressources et versions de protocole supportés. Cela garantit que les deux parties comprennent les capacités disponibles pour la session.

- **Requête utilisateur**  
  L’utilisateur interagit avec le host (par exemple, en saisissant un prompt ou une commande). Le host collecte cette entrée et la transmet au client pour traitement.

- **Utilisation de ressources ou d’outils**  
  - Le client peut demander au serveur un contexte ou des ressources supplémentaires (fichiers, entrées de base de données, articles de base de connaissances) pour enrichir la compréhension du modèle.  
  - Si le modèle détermine qu’un outil est nécessaire (par exemple pour récupérer des données, effectuer un calcul ou appeler une API), le client envoie une requête d’invocation d’outil au serveur, en précisant le nom de l’outil et ses paramètres.

- **Exécution côté serveur**  
  Le serveur reçoit la requête de ressource ou d’outil, exécute les opérations nécessaires (comme lancer une fonction, interroger une base de données ou récupérer un fichier), et renvoie les résultats au client dans un format structuré.

- **Génération de la réponse**  
  Le client intègre les réponses du serveur (données ressources, résultats d’outils, etc.) dans l’interaction en cours avec le modèle. Le modèle utilise ces informations pour produire une réponse complète et contextuellement pertinente.

- **Présentation du résultat**  
  Le host reçoit la sortie finale du client et la présente à l’utilisateur, souvent en combinant le texte généré par le modèle avec les résultats des exécutions d’outils ou des recherches de ressources.

Ce flux permet au MCP de soutenir des applications IA avancées, interactives et conscientes du contexte, en connectant harmonieusement les modèles avec des outils et sources de données externes.

## Détails du protocole

MCP (Model Context Protocol) est construit sur [JSON-RPC 2.0](https://www.jsonrpc.org/), offrant un format de message standardisé et indépendant du langage pour la communication entre hosts, clients et serveurs. Cette base permet des interactions fiables, structurées et extensibles sur diverses plateformes et langages de programmation.

### Fonctionnalités clés du protocole

MCP étend JSON-RPC 2.0 avec des conventions supplémentaires pour l’invocation d’outils, l’accès aux ressources et la gestion des prompts. Il supporte plusieurs couches de transport (STDIO, WebSocket, SSE) et permet une communication sécurisée, extensible et indépendante du langage entre les composants.

#### 🧢 Protocole de base

- **Format des messages JSON-RPC** : Toutes les requêtes et réponses utilisent la spécification JSON-RPC 2.0, garantissant une structure cohérente pour les appels de méthode, paramètres, résultats et gestion des erreurs.
- **Connexions avec état** : Les sessions MCP maintiennent l’état à travers plusieurs requêtes, supportant les conversations continues, l’accumulation de contexte et la gestion des ressources.
- **Négociation des capacités** : Lors de l’établissement de la connexion, clients et serveurs échangent des informations sur les fonctionnalités supportées, versions de protocole, outils et ressources disponibles. Cela garantit que les deux parties comprennent leurs capacités respectives et peuvent s’adapter en conséquence.

#### ➕ Utilitaires supplémentaires

Voici quelques utilitaires et extensions du protocole que MCP offre pour améliorer l’expérience développeur et permettre des scénarios avancés :

- **Options de configuration** : MCP permet la configuration dynamique des paramètres de session, comme les permissions d’outils, l’accès aux ressources et les réglages du modèle, adaptés à chaque interaction.
- **Suivi de progression** : Les opérations longues peuvent rapporter des mises à jour de progression, permettant des interfaces utilisateur réactives et une meilleure expérience lors de tâches complexes.
- **Annulation de requêtes** : Les clients peuvent annuler des requêtes en cours, offrant aux utilisateurs la possibilité d’interrompre des opérations devenues inutiles ou trop longues.
- **Rapport d’erreurs** : Des messages et codes d’erreur standardisés facilitent le diagnostic, la gestion élégante des échecs et fournissent un retour exploitable aux utilisateurs et développeurs.
- **Journalisation** : Clients et serveurs peuvent émettre des logs structurés pour l’audit, le débogage et la surveillance des interactions du protocole.

En tirant parti de ces fonctionnalités, MCP garantit une communication robuste, sécurisée et flexible entre modèles de langage et outils ou sources de données externes.

### 🔐 Considérations de sécurité

Les implémentations MCP doivent respecter plusieurs principes clés de sécurité pour garantir des interactions sûres et fiables :

- **Consentement et contrôle utilisateur** : Les utilisateurs doivent donner un consentement explicite avant tout accès aux données ou exécution d’opérations. Ils doivent pouvoir contrôler clairement les données partagées et les actions autorisées, soutenus par des interfaces intuitives pour examiner et approuver les activités.

- **Confidentialité des données** : Les données utilisateur ne doivent être exposées qu’avec consentement explicite et protégées par des contrôles d’accès appropriés. Les implémentations MCP doivent prévenir toute transmission non autorisée et assurer la confidentialité tout au long des interactions.

- **Sécurité des outils** : Avant d’invoquer un outil, un consentement explicite est nécessaire. Les utilisateurs doivent comprendre clairement la fonctionnalité de chaque outil, et des frontières de sécurité solides doivent être appliquées pour éviter toute exécution non intentionnelle ou dangereuse.

En suivant ces principes, MCP garantit que la confiance, la confidentialité et la sécurité des utilisateurs sont préservées dans toutes les interactions du protocole.

## Exemples de code : composants clés

Voici des exemples de code dans plusieurs langages populaires illustrant comment implémenter des composants clés de serveurs MCP et des outils.

### Exemple .NET : créer un serveur MCP simple avec des outils

Voici un exemple pratique en .NET montrant comment implémenter un serveur MCP simple avec des outils personnalisés. Cet exemple illustre la définition et l’enregistrement d’outils, la gestion des requêtes et la connexion du serveur via le Model Context Protocol.

```csharp
using System;
using System.Threading.Tasks;
using ModelContextProtocol.Server;
using ModelContextProtocol.Server.Transport;
using ModelContextProtocol.Server.Tools;

public class WeatherServer
{
    public static async Task Main(string[] args)
    {
        // Create an MCP server
        var server = new McpServer(
            name: "Weather MCP Server",
            version: "1.0.0"
        );
        
        // Register our custom weather tool
        server.AddTool<string, WeatherData>("weatherTool", 
            description: "Gets current weather for a location",
            execute: async (location) => {
                // Call weather API (simplified)
                var weatherData = await GetWeatherDataAsync(location);
                return weatherData;
            });
        
        // Connect the server using stdio transport
        var transport = new StdioServerTransport();
        await server.ConnectAsync(transport);
        
        Console.WriteLine("Weather MCP Server started");
        
        // Keep the server running until process is terminated
        await Task.Delay(-1);
    }
    
    private static async Task<WeatherData> GetWeatherDataAsync(string location)
    {
        // This would normally call a weather API
        // Simplified for demonstration
        await Task.Delay(100); // Simulate API call
        return new WeatherData { 
            Temperature = 72.5,
            Conditions = "Sunny",
            Location = location
        };
    }
}

public class WeatherData
{
    public double Temperature { get; set; }
    public string Conditions { get; set; }
    public string Location { get; set; }
}
```

### Exemple Java : composants serveur MCP

Cet exemple montre le même serveur MCP et l’enregistrement d’outils que l’exemple .NET ci-dessus, mais implémenté en Java.

```java
import io.modelcontextprotocol.server.McpServer;
import io.modelcontextprotocol.server.McpToolDefinition;
import io.modelcontextprotocol.server.transport.StdioServerTransport;
import io.modelcontextprotocol.server.tool.ToolExecutionContext;
import io.modelcontextprotocol.server.tool.ToolResponse;

public class WeatherMcpServer {
    public static void main(String[] args) throws Exception {
        // Create an MCP server
        McpServer server = McpServer.builder()
            .name("Weather MCP Server")
            .version("1.0.0")
            .build();
            
        // Register a weather tool
        server.registerTool(McpToolDefinition.builder("weatherTool")
            .description("Gets current weather for a location")
            .parameter("location", String.class)
            .execute((ToolExecutionContext ctx) -> {
                String location = ctx.getParameter("location", String.class);
                
                // Get weather data (simplified)
                WeatherData data = getWeatherData(location);
                
                // Return formatted response
                return ToolResponse.content(
                    String.format("Temperature: %.1f°F, Conditions: %s, Location: %s", 
                    data.getTemperature(), 
                    data.getConditions(), 
                    data.getLocation())
                );
            })
            .build());
        
        // Connect the server using stdio transport
        try (StdioServerTransport transport = new StdioServerTransport()) {
            server.connect(transport);
            System.out.println("Weather MCP Server started");
            // Keep server running until process is terminated
            Thread.currentThread().join();
        }
    }
    
    private static WeatherData getWeatherData(String location) {
        // Implementation would call a weather API
        // Simplified for example purposes
        return new WeatherData(72.5, "Sunny", location);
    }
}

class WeatherData {
    private double temperature;
    private String conditions;
    private String location;
    
    public WeatherData(double temperature, String conditions, String location) {
        this.temperature = temperature;
        this.conditions = conditions;
        this.location = location;
    }
    
    public double getTemperature() {
        return temperature;
    }
    
    public String getConditions() {
        return conditions;
    }
    
    public String getLocation() {
        return location;
    }
}
```

### Exemple Python : construire un serveur MCP

Dans cet exemple, nous montrons comment construire un serveur MCP en Python. Deux méthodes différentes pour créer des outils sont également présentées.

```python
#!/usr/bin/env python3
import asyncio
from mcp.server.fastmcp import FastMCP
from mcp.server.transports.stdio import serve_stdio

# Create a FastMCP server
mcp = FastMCP(
    name="Weather MCP Server",
    version="1.0.0"
)

@mcp.tool()
def get_weather(location: str) -> dict:
    """Gets current weather for a location."""
    # This would normally call a weather API
    # Simplified for demonstration
    return {
        "temperature": 72.5,
        "conditions": "Sunny",
        "location": location
    }

# Alternative approach using a class
class WeatherTools:
    @mcp.tool()
    def forecast(self, location: str, days: int = 1) -> dict:
        """Gets weather forecast for a location for the specified number of days."""
        # This would normally call a weather API forecast endpoint
        # Simplified for demonstration
        return {
            "location": location,
            "forecast": [
                {"day": i+1, "temperature": 70 + i, "conditions": "Partly Cloudy"}
                for i in range(days)
            ]
        }

# Initialize class for its methods to be registered as tools
weather_tools = WeatherTools()

if __name__ == "__main__":
    # Start the server with stdio transport
    print("Weather MCP Server starting...")
    asyncio.run(serve_stdio(mcp))
```

### Exemple JavaScript : création d’un serveur MCP

Cet exemple illustre la création d’un serveur MCP en JavaScript et l’enregistrement de deux outils liés à la météo.

```javascript
// Using the official Model Context Protocol SDK
import { McpServer } from "@modelcontextprotocol/sdk/server/mcp.js";
import { StdioServerTransport } from "@modelcontextprotocol/sdk/server/stdio.js";
import { z } from "zod"; // For parameter validation

// Create an MCP server
const server = new McpServer({
  name: "Weather MCP Server",
  version: "1.0.0"
});

// Define a weather tool
server.tool(
  "weatherTool",
  {
    location: z.string().describe("The location to get weather for")
  },
  async ({ location }) => {
    // This would normally call a weather API
    // Simplified for demonstration
    const weatherData = await getWeatherData(location);
    
    return {
      content: [
        { 
          type: "text", 
          text: `Temperature: ${weatherData.temperature}°F, Conditions: ${weatherData.conditions}, Location: ${weatherData.location}` 
        }
      ]
    };
  }
);

// Define a forecast tool
server.tool(
  "forecastTool",
  {
    location: z.string(),
    days: z.number().default(3).describe("Number of days for forecast")
  },
  async ({ location, days }) => {
    // This would normally call a weather API
    // Simplified for demonstration
    const forecast = await getForecastData(location, days);
    
    return {
      content: [
        { 
          type: "text", 
          text: `${days}-day forecast for ${location}: ${JSON.stringify(forecast)}` 
        }
      ]
    };
  }
);

// Helper functions
async function getWeatherData(location) {
  // Simulate API call
  return {
    temperature: 72.5,
    conditions: "Sunny",
    location: location
  };
}

async function getForecastData(location, days) {
  // Simulate API call
  return Array.from({ length: days }, (_, i) => ({
    day: i + 1,
    temperature: 70 + Math.floor(Math.random() * 10),
    conditions: i % 2 === 0 ? "Sunny" : "Partly Cloudy"
  }));
}

// Connect the server using stdio transport
const transport = new StdioServerTransport();
server.connect(transport).catch(console.error);

console.log("Weather MCP Server started");
```

Cet exemple JavaScript montre comment créer un client MCP qui se connecte à un serveur, envoie un prompt et traite la réponse, y compris les appels d’outils effectués.

## Sécurité et autorisation

MCP intègre plusieurs concepts et mécanismes pour gérer la sécurité et l’autorisation tout au long du protocole :

1. **Contrôle des permissions des outils**  
  Les clients peuvent spécifier quels outils un modèle est autorisé à utiliser durant une session. Cela garantit que seuls les outils explicitement autorisés sont accessibles, réduisant le risque d’opérations non intentionnelles ou dangereuses. Les permissions peuvent être configurées dynamiquement selon les préférences utilisateur, les politiques organisationnelles ou le contexte de l’interaction.

2. **Authentification**  
  Les serveurs peuvent exiger une authentification avant d’accorder l’accès aux outils, ressources ou opérations sensibles. Cela peut impliquer des clés API, tokens OAuth ou autres schémas d’authentification. Une authentification adéquate garantit que seuls les clients et utilisateurs de confiance peuvent invoquer les capacités côté serveur.

3. **Validation**  
  La validation des paramètres est appliquée pour toutes les invocations d’outils. Chaque outil définit les types, formats et contraintes attendus pour ses paramètres, et le serveur valide les requêtes entrantes en conséquence. Cela empêche les entrées malformées ou malveillantes d’atteindre les implémentations d’outils et aide à préserver l’intégrité des opérations.

4. **Limitation du débit**  
  Pour prévenir les abus et assurer un usage équitable des ressources serveur, les serveurs MCP peuvent appliquer une limitation du débit pour les appels d’outils et l’accès aux ressources. Les limites peuvent être appliquées par utilisateur, par session ou globalement, et contribuent à protéger contre les attaques par déni de service ou la consommation excessive de ressources.

En combinant ces mécanismes, MCP offre une base sécurisée pour intégrer les modèles de langage avec des outils et sources de données externes, tout en donnant aux utilisateurs et développeurs un contrôle précis sur l’accès et l’utilisation.

## Messages du protocole

La communication MCP utilise des messages JSON structurés pour faciliter des interactions claires et fiables entre clients, serveurs et modèles. Les principaux types de messages comprennent :

- **Requête client**  
  Envoyée du client au serveur, ce message inclut généralement :  
  - Le prompt ou la commande de l’utilisateur  
  - L’historique de conversation pour le contexte  
  - La configuration et les permissions des outils  
  - Toute métadonnée ou information de session supplémentaire

- **Réponse du modèle**  
  Renvoyée par le modèle (via le client), ce message contient :  
  - Le texte généré ou la complétion basée sur le prompt et le contexte  
  - Des instructions d’appel d’outil optionnelles si le modèle juge qu’un outil doit être invoqué  
  - Des références à des ressources ou contexte additionnel si nécessaire

- **Requête d’outil**  
  Envoyée du client au serveur lorsqu’un outil doit être exécuté. Ce message comprend :  
  - Le nom de l’outil à invoquer  
  - Les paramètres requis par l’outil (validés selon le schéma de l’outil)  
  - Des informations contextuelles ou identifiants pour suivre la requête

- **Réponse d’outil**  
  Renvoyée par le serveur après exécution d’un outil. Ce message fournit :  
  - Les résultats de l’exécution de l’outil (données structurées ou contenu)  
  - Les erreurs ou informations de statut si l’appel d’outil a échoué  
  - Éventuellement, des métadonnées ou logs supplémentaires liés à l’exécution

Ces messages structurés garantissent que chaque étape du workflow MCP est explicite, traç

**Avertissement** :  
Ce document a été traduit à l’aide du service de traduction automatique [Co-op Translator](https://github.com/Azure/co-op-translator). Bien que nous nous efforcions d’assurer l’exactitude, veuillez noter que les traductions automatiques peuvent contenir des erreurs ou des inexactitudes. Le document original dans sa langue d’origine doit être considéré comme la source faisant foi. Pour les informations critiques, une traduction professionnelle réalisée par un humain est recommandée. Nous déclinons toute responsabilité en cas de malentendus ou d’interprétations erronées résultant de l’utilisation de cette traduction.