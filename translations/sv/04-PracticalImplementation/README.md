<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "d88dbf928fa0f159b82312e9a6757ba0",
  "translation_date": "2025-06-18T09:11:36+00:00",
  "source_file": "04-PracticalImplementation/README.md",
  "language_code": "sv"
}
-->
# Praktisk Implementering

Praktisk implementering är där kraften i Model Context Protocol (MCP) blir påtaglig. Även om det är viktigt att förstå teorin och arkitekturen bakom MCP, uppstår det verkliga värdet när du tillämpar dessa koncept för att bygga, testa och distribuera lösningar som löser verkliga problem. Detta kapitel överbryggar klyftan mellan konceptuell kunskap och praktisk utveckling, och guidar dig genom processen att förverkliga MCP-baserade applikationer.

Oavsett om du utvecklar intelligenta assistenter, integrerar AI i affärsprocesser eller bygger anpassade verktyg för databehandling, erbjuder MCP en flexibel grund. Dess språkoberoende design och officiella SDK:er för populära programmeringsspråk gör det tillgängligt för en bred utvecklarkrets. Genom att utnyttja dessa SDK:er kan du snabbt prototypa, iterera och skala dina lösningar över olika plattformar och miljöer.

I de följande avsnitten hittar du praktiska exempel, kodexempel och distributionsstrategier som visar hur du implementerar MCP i C#, Java, TypeScript, JavaScript och Python. Du kommer också att lära dig hur du felsöker och testar dina MCP-servrar, hanterar API:er och distribuerar lösningar till molnet med Azure. Dessa praktiska resurser är utformade för att påskynda din inlärning och hjälpa dig att tryggt bygga robusta, produktionsfärdiga MCP-applikationer.

## Översikt

Den här lektionen fokuserar på praktiska aspekter av MCP-implementering över flera programmeringsspråk. Vi kommer att utforska hur man använder MCP SDK:er i C#, Java, TypeScript, JavaScript och Python för att bygga robusta applikationer, felsöka och testa MCP-servrar samt skapa återanvändbara resurser, prompts och verktyg.

## Lärandemål

I slutet av denna lektion kommer du att kunna:
- Implementera MCP-lösningar med officiella SDK:er i olika programmeringsspråk
- Felsöka och testa MCP-servrar systematiskt
- Skapa och använda serverfunktioner (Resources, Prompts och Tools)
- Designa effektiva MCP-arbetsflöden för komplexa uppgifter
- Optimera MCP-implementationer för prestanda och tillförlitlighet

## Officiella SDK-resurser

Model Context Protocol erbjuder officiella SDK:er för flera språk:

- [C# SDK](https://github.com/modelcontextprotocol/csharp-sdk)
- [Java SDK](https://github.com/modelcontextprotocol/java-sdk) 
- [TypeScript SDK](https://github.com/modelcontextprotocol/typescript-sdk)
- [Python SDK](https://github.com/modelcontextprotocol/python-sdk)
- [Kotlin SDK](https://github.com/modelcontextprotocol/kotlin-sdk)

## Arbeta med MCP SDK:er

Detta avsnitt ger praktiska exempel på MCP-implementeringar i flera programmeringsspråk. Du hittar exempel i katalogen `samples` organiserade efter språk.

### Tillgängliga exempel

Förrådet inkluderar [exempel på implementationer](../../../04-PracticalImplementation/samples) i följande språk:

- [C#](./samples/csharp/README.md)
- [Java](./samples/java/containerapp/README.md)
- [TypeScript](./samples/typescript/README.md)
- [JavaScript](./samples/javascript/README.md)
- [Python](./samples/python/README.md)

Varje exempel demonstrerar viktiga MCP-koncept och implementationsmönster för just det språket och ekosystemet.

## Kärnfunktioner för servern

MCP-servrar kan implementera vilken kombination som helst av dessa funktioner:

### Resources
Resources tillhandahåller kontext och data för användaren eller AI-modellen att använda:
- Dokumentarkiv
- Kunskapsbaser
- Strukturerade datakällor
- Filsystem

### Prompts
Prompts är mallade meddelanden och arbetsflöden för användare:
- Fördefinierade konversationsmallar
- Guidad interaktionsmönster
- Specialiserade dialogstrukturer

### Tools
Tools är funktioner som AI-modellen kan köra:
- Verktyg för databehandling
- Integrationer med externa API:er
- Beräkningskapacitet
- Sökmöjligheter

## Exempel på implementationer: C#

Det officiella C# SDK-förrådet innehåller flera exempel som visar olika aspekter av MCP:

- **Basic MCP Client**: Ett enkelt exempel som visar hur man skapar en MCP-klient och anropar verktyg
- **Basic MCP Server**: Minimal serverimplementation med grundläggande verktygsregistrering
- **Advanced MCP Server**: Fullfjädrad server med verktygsregistrering, autentisering och felhantering
- **ASP.NET-integration**: Exempel som visar integration med ASP.NET Core
- **Verktygsimplementeringsmönster**: Olika mönster för att implementera verktyg med varierande komplexitet

MCP C# SDK är i förhandsgranskning och API:er kan ändras. Vi kommer att kontinuerligt uppdatera denna blogg i takt med att SDK:n utvecklas.

### Viktiga funktioner
- [C# MCP Nuget ModelContextProtocol](https://www.nuget.org/packages/ModelContextProtocol)

- Bygg din [första MCP-server](https://devblogs.microsoft.com/dotnet/build-a-model-context-protocol-mcp-server-in-csharp/).

För kompletta C#-implementationsexempel, besök det [officiella C# SDK-exempelförrådet](https://github.com/modelcontextprotocol/csharp-sdk)

## Exempel på implementation: Java Implementation

Java SDK erbjuder robusta MCP-implementeringsalternativ med företagsklassade funktioner.

### Viktiga funktioner

- Integration med Spring Framework
- Stark typkontroll
- Stöd för reaktiv programmering
- Omfattande felhantering

För ett komplett Java-implementationsprov, se [MCPSample.java](../../../04-PracticalImplementation/samples/java/MCPSample.java) i exempel-katalogen.

## Exempel på implementation: JavaScript Implementation

JavaScript SDK erbjuder ett lättviktigt och flexibelt sätt att implementera MCP.

### Viktiga funktioner

- Stöd för Node.js och webbläsare
- Promise-baserat API
- Enkel integration med Express och andra ramverk
- WebSocket-stöd för streaming

För ett komplett JavaScript-exempel, se [mcp_sample.js](../../../04-PracticalImplementation/samples/javascript/mcp_sample.js) i exempel-katalogen.

## Exempel på implementation: Python Implementation

Python SDK erbjuder ett pythoniskt sätt att implementera MCP med utmärkta integrationer för ML-ramverk.

### Viktiga funktioner

- Async/await-stöd med asyncio
- Integration med Flask och FastAPI
- Enkel verktygsregistrering
- Native integration med populära ML-bibliotek

För ett komplett Python-exempel, se [mcp_sample.py](../../../04-PracticalImplementation/samples/python/mcp_sample.py) i exempel-katalogen.

## API-hantering

Azure API Management är ett utmärkt sätt att säkra MCP-servrar. Idén är att placera en Azure API Management-instans framför din MCP-server och låta den hantera funktioner som du troligen vill ha, som:

- hastighetsbegränsning
- tokenhantering
- övervakning
- lastbalansering
- säkerhet

### Azure-exempel

Här är ett Azure-exempel som gör just detta, dvs [skapar en MCP-server och säkrar den med Azure API Management](https://github.com/Azure-Samples/remote-mcp-apim-functions-python).

Se hur auktoriseringsflödet sker i bilden nedan:

![APIM-MCP](https://github.com/Azure-Samples/remote-mcp-apim-functions-python/blob/main/mcp-client-authorization.gif?raw=true) 

I bilden ovan sker följande:

- Autentisering/Auktorisering sker via Microsoft Entra.
- Azure API Management fungerar som en gateway och använder policies för att styra och hantera trafiken.
- Azure Monitor loggar alla förfrågningar för vidare analys.

#### Auktoriseringsflöde

Låt oss titta närmare på auktoriseringsflödet:

![Sequence Diagram](https://github.com/Azure-Samples/remote-mcp-apim-functions-python/blob/main/infra/app/apim-oauth/diagrams/images/mcp-client-auth.png?raw=true)

#### MCP auktoriseringsspecifikation

Läs mer om [MCP Authorization specification](https://modelcontextprotocol.io/specification/2025-03-26/basic/authorization#2-10-third-party-authorization-flow)

## Distribuera Remote MCP Server till Azure

Låt oss se om vi kan distribuera exemplet vi nämnde tidigare:

1. Klona repot

    ```bash
    git clone https://github.com/Azure-Samples/remote-mcp-apim-functions-python.git
    cd remote-mcp-apim-functions-python
    ```

2. Registrera `Microsoft.App` med följande kommando och vänta tills registreringen är klar:

    ` resource provider.
    * If you are using Azure CLI, run `az provider register --namespace Microsoft.App --wait`.
    * If you are using Azure PowerShell, run `Register-AzResourceProvider -ProviderNamespace Microsoft.App`. Then run `(Get-AzResourceProvider -ProviderNamespace Microsoft.App).RegistrationState

3. Kör detta [azd](https://aka.ms/azd) kommando för att provisionera API Management-tjänsten, function app (med kod) och alla andra nödvändiga Azure-resurser:

    ```shell
    azd up
    ```

    Detta kommando bör distribuera alla molnresurser på Azure.

### Testa din server med MCP Inspector

1. I ett **nytt terminalfönster**, installera och kör MCP Inspector

    ```shell
    npx @modelcontextprotocol/inspector
    ```

    Du bör se ett gränssnitt som liknar detta:

    ![Connect to Node inspector](../../../translated_images/connect.141db0b2bd05f096fb1dd91273771fd8b2469d6507656c3b0c9df4b3c5473929.sv.png) 

2. CTRL-klicka för att ladda MCP Inspector webbappen från den URL som appen visar (t.ex. http://127.0.0.1:6274/#resources)
3. Ställ in transporttypen till `SSE`
1. Set the URL to your running API Management SSE endpoint displayed after `azd up` och **Connect**:

    ```shell
    https://<apim-servicename-from-azd-output>.azure-api.net/mcp/sse
    ```

5. **Lista verktyg**. Klicka på ett verktyg och **Run Tool**.  

Om alla steg fungerat ska du nu vara ansluten till MCP-servern och ha kunnat anropa ett verktyg.

## MCP-servrar för Azure

[Remote-mcp-functions](https://github.com/Azure-Samples/remote-mcp-functions-dotnet): Detta set av repor är snabbstartsmallar för att bygga och distribuera anpassade fjärr-MCP-servrar (Model Context Protocol) med Azure Functions i Python, C# .NET eller Node/TypeScript.

Exemplen erbjuder en komplett lösning som gör det möjligt för utvecklare att:

- Bygga och köra lokalt: Utveckla och felsöka en MCP-server på en lokal maskin
- Distribuera till Azure: Enkelt distribuera till molnet med ett enkelt azd up-kommando
- Ansluta från klienter: Anslut till MCP-servern från olika klienter inklusive VS Code:s Copilot agent-läge och MCP Inspector-verktyget

### Viktiga funktioner:

- Säkerhet som standard: MCP-servern är skyddad med nycklar och HTTPS
- Autentiseringsalternativ: Stödjer OAuth med inbyggd autentisering och/eller API Management
- Nätverksisolering: Möjliggör nätverksisolering med Azure Virtual Networks (VNET)
- Serverlös arkitektur: Använder Azure Functions för skalbar, händelsestyrd körning
- Lokal utveckling: Omfattande stöd för lokal utveckling och felsökning
- Enkel distribution: Strömlinjeformad distributionsprocess till Azure

Förrådet innehåller alla nödvändiga konfigurationsfiler, källkod och infrastrukturbeskrivningar för att snabbt komma igång med en produktionsklar MCP-serverimplementation.

- [Azure Remote MCP Functions Python](https://github.com/Azure-Samples/remote-mcp-functions-python) - Exempel på MCP-implementation med Azure Functions i Python

- [Azure Remote MCP Functions .NET](https://github.com/Azure-Samples/remote-mcp-functions-dotnet) - Exempel på MCP-implementation med Azure Functions i C# .NET

- [Azure Remote MCP Functions Node/Typescript](https://github.com/Azure-Samples/remote-mcp-functions-typescript) - Exempel på MCP-implementation med Azure Functions i Node/TypeScript.

## Viktiga insikter

- MCP SDK:er erbjuder språksspecifika verktyg för att implementera robusta MCP-lösningar
- Felsöknings- och testprocessen är avgörande för pålitliga MCP-applikationer
- Återanvändbara promptmallar möjliggör konsekventa AI-interaktioner
- Väl utformade arbetsflöden kan orkestrera komplexa uppgifter med flera verktyg
- Implementering av MCP-lösningar kräver hänsyn till säkerhet, prestanda och felhantering

## Övning

Designa ett praktiskt MCP-arbetsflöde som löser ett verkligt problem inom ditt område:

1. Identifiera 3-4 verktyg som skulle vara användbara för att lösa detta problem
2. Skapa ett arbetsflödesdiagram som visar hur dessa verktyg samverkar
3. Implementera en grundläggande version av ett av verktygen i ditt föredragna språk
4. Skapa en promptmall som hjälper modellen att effektivt använda ditt verktyg

## Ytterligare resurser


---

Nästa: [Avancerade ämnen](../05-AdvancedTopics/README.md)

**Ansvarsfriskrivning**:  
Detta dokument har översatts med hjälp av AI-översättningstjänsten [Co-op Translator](https://github.com/Azure/co-op-translator). Även om vi strävar efter noggrannhet, vänligen observera att automatiska översättningar kan innehålla fel eller brister. Det ursprungliga dokumentet på dess modersmål bör betraktas som den auktoritativa källan. För kritisk information rekommenderas professionell mänsklig översättning. Vi ansvarar inte för eventuella missförstånd eller feltolkningar som uppstår vid användning av denna översättning.