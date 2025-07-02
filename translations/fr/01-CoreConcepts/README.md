<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "b3b4a6ad10c3c0edbf7fa7cfa0ec496b",
  "translation_date": "2025-07-02T06:50:44+00:00",
  "source_file": "01-CoreConcepts/README.md",
  "language_code": "fr"
}
-->
# 📖 Concepts fondamentaux de MCP : Maîtriser le Model Context Protocol pour l’intégration de l’IA

Le [Model Context Protocol (MCP)](https://github.com/modelcontextprotocol) est un cadre puissant et standardisé qui optimise la communication entre les grands modèles de langage (LLM) et les outils, applications et sources de données externes. Ce guide optimisé pour le SEO vous fera découvrir les concepts clés du MCP, en vous assurant de bien comprendre son architecture client-serveur, ses composants essentiels, ses mécanismes de communication et les meilleures pratiques de mise en œuvre.

## Vue d’ensemble

Cette leçon explore l’architecture fondamentale et les composants qui composent l’écosystème du Model Context Protocol (MCP). Vous apprendrez l’architecture client-serveur, les composants clés et les mécanismes de communication qui alimentent les interactions MCP.

## 👩‍🎓 Objectifs d’apprentissage clés

À la fin de cette leçon, vous serez capable de :

- Comprendre l’architecture client-serveur du MCP.
- Identifier les rôles et responsabilités des Hosts, Clients et Servers.
- Analyser les fonctionnalités principales qui font du MCP une couche d’intégration flexible.
- Appréhender le flux d’information au sein de l’écosystème MCP.
- Obtenir des connaissances pratiques grâce à des exemples de code en .NET, Java, Python et JavaScript.

## 🔎 Architecture MCP : Un regard approfondi

L’écosystème MCP repose sur un modèle client-serveur. Cette structure modulaire permet aux applications d’IA d’interagir efficacement avec des outils, bases de données, API et ressources contextuelles. Décortiquons cette architecture en ses composants principaux.

Au cœur, MCP suit une architecture client-serveur où une application hôte peut se connecter à plusieurs serveurs :

```mermaid
flowchart LR
    subgraph "Your Computer"
        Host["Host with MCP VScode, IDEs, Tools)"]
        S1["MCP Server A"]
        S2["MCP Server B"]
        S3["MCP Server C"]
        Host <-->|"MCP Protocol"| S1
        Host <-->|"MCP Protocol"| S2
        Host <-->|"MCP Protocol"| S3
        S1 <--> D1[("Local\Data Source A")]
        S2 <--> D2[("Local\Data Source B")]
    end
    subgraph "Internet"
        S3 <-->|"Web APIs"| D3[("Remote\Services")]
    end
```

- **MCP Hosts** : Programmes comme VSCode, Claude Desktop, IDEs, ou outils d’IA souhaitant accéder aux données via MCP
- **MCP Clients** : Clients du protocole qui maintiennent des connexions 1:1 avec les serveurs
- **MCP Servers** : Programmes légers exposant chacun des capacités spécifiques via le Model Context Protocol standardisé
- **Sources de données locales** : Fichiers, bases de données et services de votre ordinateur auxquels les serveurs MCP peuvent accéder de manière sécurisée
- **Services distants** : Systèmes externes accessibles via internet que les serveurs MCP peuvent joindre via des API.

Le protocole MCP est une norme en évolution, vous pouvez consulter les dernières mises à jour dans la [spécification du protocole](https://modelcontextprotocol.io/specification/2025-06-18/)

### 1. Hosts

Dans le Model Context Protocol (MCP), les Hosts jouent un rôle crucial en tant qu’interface principale par laquelle les utilisateurs interagissent avec le protocole. Les Hosts sont des applications ou environnements qui initient les connexions aux serveurs MCP pour accéder aux données, outils et prompts. Parmi les exemples de Hosts, on trouve des environnements de développement intégrés (IDEs) comme Visual Studio Code, des outils d’IA comme Claude Desktop, ou des agents personnalisés conçus pour des tâches spécifiques.

Les **Hosts** sont des applications LLM qui initient les connexions. Ils :

- Exécutent ou interagissent avec les modèles d’IA pour générer des réponses.
- Initient les connexions avec les serveurs MCP.
- Gèrent le déroulement de la conversation et l’interface utilisateur.
- Contrôlent les permissions et les contraintes de sécurité.
- Gèrent le consentement utilisateur pour le partage de données et l’exécution d’outils.

### 2. Clients

Les Clients sont des composants essentiels qui facilitent l’interaction entre les Hosts et les serveurs MCP. Ils jouent le rôle d’intermédiaires, permettant aux Hosts d’accéder et d’utiliser les fonctionnalités fournies par les serveurs MCP. Ils assurent une communication fluide et un échange de données efficace au sein de l’architecture MCP.

Les **Clients** sont des connecteurs au sein de l’application hôte. Ils :

- Envoient des requêtes aux serveurs avec des prompts/instructions.
- Négocient les capacités avec les serveurs.
- Gèrent les demandes d’exécution d’outils provenant des modèles.
- Traitent et affichent les réponses aux utilisateurs.

### 3. Servers

Les Servers sont responsables de la gestion des requêtes des clients MCP et de la fourniture des réponses appropriées. Ils gèrent diverses opérations telles que la récupération de données, l’exécution d’outils et la génération de prompts. Les serveurs garantissent une communication efficace et fiable entre clients et Hosts, en maintenant l’intégrité du processus d’interaction.

Les **Servers** sont des services fournissant contexte et capacités. Ils :

- Enregistrent les fonctionnalités disponibles (ressources, prompts, outils)
- Reçoivent et exécutent les appels d’outils depuis le client
- Fournissent des informations contextuelles pour enrichir les réponses du modèle
- Restituent les résultats au client
- Maintiennent l’état entre les interactions si nécessaire

Les serveurs peuvent être développés par n’importe qui pour étendre les capacités des modèles avec des fonctionnalités spécialisées.

### 4. Fonctionnalités des Servers

Les serveurs dans le Model Context Protocol (MCP) fournissent les blocs fondamentaux qui permettent des interactions riches entre clients, hosts et modèles de langage. Ces fonctionnalités sont conçues pour renforcer les capacités du MCP en offrant un contexte structuré, des outils et des prompts.

Les serveurs MCP peuvent proposer l’une des fonctionnalités suivantes :

#### 📑 Ressources

Les ressources dans le Model Context Protocol (MCP) englobent différents types de contexte et de données pouvant être utilisés par les utilisateurs ou les modèles d’IA. Cela inclut :

- **Données contextuelles** : Informations et contexte que les utilisateurs ou modèles d’IA peuvent exploiter pour la prise de décision et l’exécution des tâches.
- **Bases de connaissances et dépôts de documents** : Collections de données structurées et non structurées, telles que articles, manuels et publications de recherche, fournissant des informations précieuses.
- **Fichiers et bases de données locales** : Données stockées localement sur les appareils ou dans des bases de données, accessibles pour traitement et analyse.
- **APIs et services web** : Interfaces externes offrant des données et fonctionnalités supplémentaires, permettant l’intégration avec diverses ressources et outils en ligne.

Un exemple de ressource peut être un schéma de base de données ou un fichier accessible ainsi :

```text
file://log.txt
database://schema
```

### 🤖 Prompts

Les prompts dans le Model Context Protocol (MCP) incluent divers modèles pré-définis et schémas d’interaction conçus pour fluidifier les flux de travail utilisateur et améliorer la communication. Ils comprennent :

- **Messages et workflows modélisés** : Messages et processus pré-structurés guidant les utilisateurs dans des tâches et interactions spécifiques.
- **Schémas d’interaction pré-définis** : Séquences standardisées d’actions et de réponses facilitant une communication cohérente et efficace.
- **Modèles de conversation spécialisés** : Templates personnalisables adaptés à des types spécifiques de conversations, garantissant des interactions pertinentes et contextuellement adaptées.

Un modèle de prompt peut ressembler à ceci :

```markdown
Generate a product slogan based on the following {{product}} with the following {{keywords}}
```

#### ⛏️ Outils

Les outils dans le Model Context Protocol (MCP) sont des fonctions que le modèle d’IA peut exécuter pour accomplir des tâches spécifiques. Ces outils sont conçus pour renforcer les capacités du modèle en fournissant des opérations structurées et fiables. Les points clés incluent :

- **Fonctions exécutables par le modèle d’IA** : Les outils sont des fonctions que le modèle peut invoquer pour réaliser diverses tâches.
- **Nom unique et description** : Chaque outil possède un nom distinct et une description détaillée expliquant son objectif et son fonctionnement.
- **Paramètres et résultats** : Les outils acceptent des paramètres spécifiques et renvoient des résultats structurés, garantissant des retours cohérents et prévisibles.
- **Fonctions discrètes** : Les outils effectuent des fonctions précises comme des recherches web, calculs ou requêtes en base de données.

Un exemple d’outil pourrait ressembler à ceci :

```typescript
server.tool(
  "GetProducts",
  {
    pageSize: z.string().optional(),
    pageCount: z.string().optional()
  }, () => {
    // return results from API
  }
)
```

## Fonctionnalités des Clients

Dans le Model Context Protocol (MCP), les clients offrent plusieurs fonctionnalités clés aux serveurs, améliorant la fonctionnalité globale et les interactions au sein du protocole. L’une des fonctionnalités notables est le Sampling.

### 👉 Sampling

- **Comportements agentiques initiés par le serveur** : Les clients permettent aux serveurs d’initier des actions ou comportements spécifiques de manière autonome, renforçant les capacités dynamiques du système.
- **Interactions récursives avec les LLM** : Cette fonctionnalité permet des interactions récursives avec les grands modèles de langage, facilitant un traitement plus complexe et itératif des tâches.
- **Demande de complétions supplémentaires du modèle** : Les serveurs peuvent solliciter des complétions supplémentaires du modèle, garantissant des réponses complètes et contextuellement pertinentes.

## Flux d’information dans MCP

Le Model Context Protocol (MCP) définit un flux structuré d’informations entre hosts, clients, serveurs et modèles. Comprendre ce flux clarifie comment les requêtes utilisateur sont traitées et comment les outils et données externes sont intégrés aux réponses du modèle.

- **Le Host initie la connexion**  
  L’application hôte (comme un IDE ou une interface de chat) établit une connexion à un serveur MCP, généralement via STDIO, WebSocket ou un autre transport supporté.

- **Négociation des capacités**  
  Le client (intégré dans le host) et le serveur échangent des informations sur leurs fonctionnalités, outils, ressources et versions du protocole supportées. Cela garantit que les deux parties comprennent les capacités disponibles pour la session.

- **Requête utilisateur**  
  L’utilisateur interagit avec le host (par exemple en saisissant un prompt ou une commande). Le host collecte cette entrée et la transmet au client pour traitement.

- **Utilisation de ressources ou d’outils**  
  - Le client peut demander un contexte ou des ressources supplémentaires au serveur (fichiers, entrées de base de données, articles de base de connaissances) pour enrichir la compréhension du modèle.
  - Si le modèle détermine qu’un outil est nécessaire (par exemple pour récupérer des données, effectuer un calcul ou appeler une API), le client envoie une requête d’invocation d’outil au serveur, en précisant le nom de l’outil et ses paramètres.

- **Exécution par le serveur**  
  Le serveur reçoit la requête de ressource ou d’outil, exécute les opérations nécessaires (exécution de fonction, requête base de données, récupération de fichier), puis renvoie les résultats au client sous un format structuré.

- **Génération de la réponse**  
  Le client intègre les réponses du serveur (données ressources, résultats d’outils, etc.) dans l’interaction en cours avec le modèle. Le modèle utilise ces informations pour générer une réponse complète et pertinente dans son contexte.

- **Présentation du résultat**  
  Le host reçoit la sortie finale du client et la présente à l’utilisateur, souvent en incluant à la fois le texte généré par le modèle et les résultats des exécutions d’outils ou recherches de ressources.

Ce flux permet à MCP de supporter des applications d’IA avancées, interactives et conscientes du contexte, en connectant de manière fluide les modèles avec des outils et sources de données externes.

## Détails du protocole

MCP (Model Context Protocol) est construit sur [JSON-RPC 2.0](https://www.jsonrpc.org/), fournissant un format de message standardisé et indépendant du langage pour la communication entre hosts, clients et serveurs. Cette base permet des interactions fiables, structurées et extensibles sur diverses plateformes et langages de programmation.

### Fonctionnalités clés du protocole

MCP étend JSON-RPC 2.0 avec des conventions supplémentaires pour l’invocation d’outils, l’accès aux ressources et la gestion des prompts. Il supporte plusieurs couches de transport (STDIO, WebSocket, SSE) et permet une communication sécurisée, extensible et indépendante du langage entre les composants.

#### 🧢 Protocole de base

- **Format des messages JSON-RPC** : Toutes les requêtes et réponses utilisent la spécification JSON-RPC 2.0, assurant une structure cohérente pour les appels de méthodes, paramètres, résultats et gestion des erreurs.
- **Connexions avec état** : Les sessions MCP maintiennent un état sur plusieurs requêtes, supportant les conversations en cours, l’accumulation de contexte et la gestion des ressources.
- **Négociation des capacités** : Lors de l’établissement de la connexion, clients et serveurs échangent des informations sur les fonctionnalités supportées, versions du protocole, outils et ressources disponibles. Cela garantit que les deux parties comprennent leurs capacités respectives et peuvent s’adapter en conséquence.

#### ➕ Utilitaires supplémentaires

Voici quelques utilitaires et extensions du protocole que MCP offre pour améliorer l’expérience développeur et permettre des scénarios avancés :

- **Options de configuration** : MCP permet une configuration dynamique des paramètres de session, tels que les permissions d’outils, l’accès aux ressources et les réglages du modèle, adaptés à chaque interaction.
- **Suivi de progression** : Les opérations longues peuvent signaler des mises à jour de progression, permettant des interfaces utilisateur réactives et une meilleure expérience pendant les tâches complexes.
- **Annulation de requêtes** : Les clients peuvent annuler des requêtes en cours, permettant aux utilisateurs d’interrompre des opérations devenues inutiles ou trop longues.
- **Rapport d’erreurs** : Des messages et codes d’erreur standardisés aident à diagnostiquer les problèmes, gérer les échecs avec élégance et fournir des retours exploitables aux utilisateurs et développeurs.
- **Journalisation** : Clients et serveurs peuvent émettre des logs structurés pour audit, débogage et surveillance des interactions du protocole.

En tirant parti de ces fonctionnalités, MCP assure une communication robuste, sécurisée et flexible entre modèles de langage et outils ou sources de données externes.

### 🔐 Considérations de sécurité

Les implémentations MCP doivent respecter plusieurs principes clés de sécurité pour garantir des interactions sûres et fiables :

- **Consentement et contrôle utilisateur** : Les utilisateurs doivent donner un consentement explicite avant tout accès aux données ou exécution d’opérations. Ils doivent disposer d’un contrôle clair sur les données partagées et les actions autorisées, soutenu par des interfaces utilisateur intuitives pour examiner et approuver les activités.

- **Confidentialité des données** : Les données utilisateur ne doivent être exposées qu’avec consentement explicite et doivent être protégées par des contrôles d’accès appropriés. Les implémentations MCP doivent prévenir toute transmission non autorisée de données et garantir la confidentialité tout au long des interactions.

- **Sécurité des outils** : Avant d’invoquer un outil, un consentement utilisateur explicite est requis. Les utilisateurs doivent comprendre clairement la fonctionnalité de chaque outil, et des frontières de sécurité robustes doivent être appliquées pour éviter des exécutions d’outils non souhaitées ou dangereuses.

En suivant ces principes, MCP garantit que la confiance, la confidentialité et la sécurité des utilisateurs sont maintenues dans toutes les interactions du protocole.

## Exemples de code : Composants clés

Voici des exemples de code dans plusieurs langages populaires illustrant comment implémenter des composants clés de serveurs MCP et des outils.

### Exemple .NET : Créer un serveur MCP simple avec des outils

Voici un exemple concret en .NET montrant comment implémenter un serveur MCP simple avec des outils personnalisés. Cet exemple illustre la définition et l’enregistrement d’outils, la gestion des requêtes et la connexion du serveur via le Model Context Protocol.

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

### Exemple Java : Composants serveur MCP

Cet exemple montre le même serveur MCP et l’enregistrement d’outils que dans l’exemple .NET ci-dessus, mais implémenté en Java.

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

### Exemple Python : Construire un serveur MCP

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

# Instantiate the class to register its tools
weather_tools = WeatherTools()

# Start the server using stdio transport
if __name__ == "__main__":
    asyncio.run(serve_stdio(mcp))
```

### Exemple JavaScript : Créer un serveur MCP

Cet exemple montre la création d’un serveur MCP en JavaScript et l’enregistrement de deux outils liés à la météo.

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

Cet exemple JavaScript illustre comment créer un client MCP qui se connecte à un serveur, envoie un prompt et traite la réponse, y compris les appels d’outils effectués.

## Sécurité et autorisation

MCP intègre plusieurs concepts et mécanismes intégrés pour gérer la sécurité et l’autorisation tout au long du protocole :

1. **Contrôle des permissions d’outils**  
   Les clients peuvent spécifier quels outils un modèle est autorisé à utiliser durant une session. Cela garantit que seuls les outils explicitement autorisés sont accessibles, réduisant le risque d’opérations non souhaitées ou dangereuses. Les permissions peuvent être configurées dynamiquement selon les préférences utilisateur, les politiques organisationnelles ou le contexte de l’interaction.

2. **Authentification**  
   Les serveurs peuvent exiger une authentification avant de donner accès aux outils, ressources ou opérations sensibles. Cela peut impliquer des clés API, des tokens OAuth ou d’autres schémas d’authentification. Une authentification appropriée assure que seuls les clients et utilisateurs de confiance peuvent invoquer les capacités côté serveur.

3. **Validation**  
   La validation des paramètres est appliquée à toutes les invocations d’outils. Chaque outil définit les types, formats et contraintes attendus pour ses paramètres, et le serveur valide les requêtes entrantes en conséquence. Cela empêche les entrées malformées ou malveillantes d’atteindre les implémentations d’outils et contribue à maintenir l’intégrité des opérations.

4. **Limitation de débit**  
   Pour prévenir les abus et assurer une utilisation équitable des ressources serveur, les serveurs MCP peuvent mettre en place des limitations de débit pour les appels d’outils et l’accès aux ressources. Les limites peuvent être appliquées par utilisateur, par session ou globalement, protégeant contre les attaques par déni de service ou une consommation excessive des ressources.

En combinant ces mécanismes, MCP fournit une base sécurisée pour intégrer les modèles de langage avec des outils et sources de données externes, tout en offrant aux utilisateurs et développeurs un contrôle précis sur l’accès et l’utilisation.

## Messages du protocole

La communication MCP utilise des messages JSON structurés pour faciliter des interactions claires et fiables entre clients, serveurs et modèles. Les principaux types de messages comprennent :

- **Requête client**  
  Envoyée du client au serveur, ce message inclut généralement :
  - Le prompt ou la commande de l’utilisateur
  - L’historique de la conversation pour le contexte
  - La configuration et les permissions des outils


**Avertissement** :  
Ce document a été traduit à l’aide du service de traduction automatique [Co-op Translator](https://github.com/Azure/co-op-translator). Bien que nous nous efforçons d’assurer l’exactitude, veuillez noter que les traductions automatiques peuvent contenir des erreurs ou des inexactitudes. Le document original dans sa langue d’origine doit être considéré comme la source faisant autorité. Pour les informations critiques, il est recommandé de recourir à une traduction professionnelle réalisée par un humain. Nous ne sommes pas responsables des malentendus ou des mauvaises interprétations résultant de l’utilisation de cette traduction.