<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "affcf199a44f60283a289dcb69dc144e",
  "translation_date": "2025-07-17T09:11:00+00:00",
  "source_file": "03-GettingStarted/02-client/complete_examples.md",
  "language_code": "no"
}
-->
# Fullstendige MCP-klienteksempler

Denne mappen inneholder komplette, fungerende eksempler på MCP-klienter i forskjellige programmeringsspråk. Hver klient demonstrerer full funksjonalitet som beskrevet i hovedtutorialen i README.md.

## Tilgjengelige klienter

### 1. Java-klient (`client_example_java.java`)
- **Transport**: SSE (Server-Sent Events) over HTTP
- **Målserver**: `http://localhost:8080`
- **Funksjoner**: 
  - Opprettelse av tilkobling og ping
  - Verktøyliste
  - Kalkulatoroperasjoner (addere, subtrahere, multiplisere, dividere, hjelp)
  - Feilhåndtering og resultatuttrekking

**For å kjøre:**
```bash
# Ensure your MCP server is running on localhost:8080
javac client_example_java.java
java client_example_java
```

### 2. C#-klient (`client_example_csharp.cs`)
- **Transport**: Stdio (Standard Input/Output)
- **Målserver**: Lokal .NET MCP-server via dotnet run
- **Funksjoner**:
  - Automatisk serveroppstart via stdio-transport
  - Liste over verktøy og ressurser
  - Kalkulatoroperasjoner
  - JSON-resultatparsing
  - Omfattende feilhåndtering

**For å kjøre:**
```bash
dotnet run
```

### 3. TypeScript-klient (`client_example_typescript.ts`)
- **Transport**: Stdio (Standard Input/Output)
- **Målserver**: Lokal Node.js MCP-server
- **Funksjoner**:
  - Full støtte for MCP-protokollen
  - Operasjoner for verktøy, ressurser og prompt
  - Kalkulatoroperasjoner
  - Ressurslesing og promptutførelse
  - Robust feilhåndtering

**For å kjøre:**
```bash
# First compile TypeScript (if needed)
npm run build

# Then run the client
npm run client
# or
node client_example_typescript.js
```

### 4. Python-klient (`client_example_python.py`)
- **Transport**: Stdio (Standard Input/Output)  
- **Målserver**: Lokal Python MCP-server
- **Funksjoner**:
  - Async/await-mønster for operasjoner
  - Oppdagelse av verktøy og ressurser
  - Testing av kalkulatoroperasjoner
  - Lesing av ressursinnhold
  - Klassebasert organisering

**For å kjøre:**
```bash
python client_example_python.py
```

## Felles funksjoner i alle klienter

Hver klientimplementasjon demonstrerer:

1. **Tilkoblingshåndtering**
   - Opprette tilkobling til MCP-server
   - Håndtere tilkoblingsfeil
   - Riktig opprydding og ressursstyring

2. **Serveroppdagelse**
   - Liste tilgjengelige verktøy
   - Liste tilgjengelige ressurser (der det støttes)
   - Liste tilgjengelige prompts (der det støttes)

3. **Verktøykall**
   - Grunnleggende kalkulatoroperasjoner (addere, subtrahere, multiplisere, dividere)
   - Hjelpekommando for serverinformasjon
   - Korrekt argumentoverføring og resultatbehandling

4. **Feilhåndtering**
   - Tilkoblingsfeil
   - Feil ved verktøykjøring
   - Elegant feilhåndtering og tilbakemelding til bruker

5. **Resultatbehandling**
   - Trekke ut tekstinnhold fra svar
   - Formatere utdata for lesbarhet
   - Håndtere ulike svarformater

## Forutsetninger

Før du kjører disse klientene, sørg for at du har:

1. **Den tilsvarende MCP-serveren kjørende** (fra `../01-first-server/`)
2. **Nødvendige avhengigheter installert** for ditt valgte språk
3. **Riktig nettverkstilkobling** (for HTTP-baserte transporter)

## Viktige forskjeller mellom implementasjonene

| Språk      | Transport | Serveroppstart | Async-modell | Viktige biblioteker |
|------------|-----------|----------------|--------------|---------------------|
| Java       | SSE/HTTP  | Ekstern        | Synkron      | WebFlux, MCP SDK    |
| C#         | Stdio     | Automatisk     | Async/Await  | .NET MCP SDK        |
| TypeScript | Stdio     | Automatisk     | Async/Await  | Node MCP SDK        |
| Python     | Stdio     | Automatisk     | AsyncIO      | Python MCP SDK      |

## Neste steg

Etter å ha utforsket disse klienteksemplene:

1. **Endre klientene** for å legge til nye funksjoner eller operasjoner
2. **Lag din egen server** og test den med disse klientene
3. **Eksperimenter med ulike transporter** (SSE vs. Stdio)
4. **Bygg en mer kompleks applikasjon** som integrerer MCP-funksjonalitet

## Feilsøking

### Vanlige problemer

1. **Connection refused**: Sørg for at MCP-serveren kjører på forventet port/sti
2. **Module not found**: Installer nødvendig MCP SDK for ditt språk
3. **Permission denied**: Sjekk filrettigheter for stdio-transport
4. **Tool not found**: Verifiser at serveren implementerer forventede verktøy

### Feilsøkingstips

1. **Aktiver detaljert logging** i din MCP SDK
2. **Sjekk serverlogger** for feilmeldinger
3. **Bekreft at verktøynavn og signaturer** stemmer mellom klient og server
4. **Test først med MCP Inspector** for å validere serverfunksjonalitet

## Relatert dokumentasjon

- [Main Client Tutorial](./README.md)
- [MCP Server Examples](../../../../03-GettingStarted/01-first-server)
- [MCP with LLM Integration](../../../../03-GettingStarted/03-llm-client)
- [Official MCP Documentation](https://modelcontextprotocol.io/)

**Ansvarsfraskrivelse**:  
Dette dokumentet er oversatt ved hjelp av AI-oversettelsestjenesten [Co-op Translator](https://github.com/Azure/co-op-translator). Selv om vi streber etter nøyaktighet, vennligst vær oppmerksom på at automatiske oversettelser kan inneholde feil eller unøyaktigheter. Det opprinnelige dokumentet på originalspråket skal anses som den autoritative kilden. For kritisk informasjon anbefales profesjonell menneskelig oversettelse. Vi er ikke ansvarlige for eventuelle misforståelser eller feiltolkninger som oppstår ved bruk av denne oversettelsen.