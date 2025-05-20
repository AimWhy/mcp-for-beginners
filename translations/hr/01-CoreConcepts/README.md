<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "4bf553c18e7e226c3d76ab0cde627d26",
  "translation_date": "2025-05-20T22:42:37+00:00",
  "source_file": "01-CoreConcepts/README.md",
  "language_code": "hr"
}
-->
# 📖 MCP Core Concepts: Ovladavanje Model Context Protocolom za AI integraciju

Model Context Protocol (MCP) je moćan, standardizirani okvir koji optimizira komunikaciju između velikih jezičnih modela (LLM) i vanjskih alata, aplikacija i izvora podataka. Ovaj SEO-optimizirani vodič vodi vas kroz osnovne koncepte MCP-a, osiguravajući da razumijete njegovu klijent-poslužitelj arhitekturu, ključne komponente, mehanizme komunikacije i najbolje prakse implementacije.

## Pregled

Ova lekcija istražuje temeljnu arhitekturu i komponente koje čine Model Context Protocol (MCP) ekosustav. Naučit ćete o klijent-poslužitelj arhitekturi, ključnim komponentama i mehanizmima komunikacije koji pokreću MCP interakcije.

## 👩‍🎓 Ključni ciljevi učenja

Na kraju ove lekcije ćete:

- Razumjeti MCP klijent-poslužitelj arhitekturu.
- Prepoznati uloge i odgovornosti Hosts, Clients i Servers.
- Analizirati osnovne značajke koje MCP čine fleksibilnim slojem za integraciju.
- Naučiti kako informacije teku unutar MCP ekosustava.
- Steći praktične uvide kroz primjere koda u .NET, Java, Python i JavaScript.

## 🔎 MCP arhitektura: detaljniji pogled

MCP ekosustav temelji se na klijent-poslužitelj modelu. Ova modularna struktura omogućuje AI aplikacijama učinkovitu interakciju s alatima, bazama podataka, API-jima i kontekstualnim resursima. Razložimo ovu arhitekturu na njene osnovne komponente.

### 1. Hosts

U Model Context Protocolu (MCP), Hosts igraju ključnu ulogu kao primarni sučelje putem kojeg korisnici komuniciraju s protokolom. Hosts su aplikacije ili okruženja koja iniciraju veze s MCP poslužiteljima kako bi pristupila podacima, alatima i promptovima. Primjeri Hosts uključuju integrirana razvojna okruženja (IDE) poput Visual Studio Code, AI alate poput Claude Desktop ili prilagođene agente dizajnirane za specifične zadatke.

**Hosts** su LLM aplikacije koje iniciraju veze. Oni:

- Izvršavaju ili komuniciraju s AI modelima za generiranje odgovora.
- Iniciraju veze s MCP poslužiteljima.
- Upravljaju tijekom razgovora i korisničkim sučeljem.
- Kontroliraju dozvole i sigurnosne ograničenja.
- Rukovode korisničkim pristankom za dijeljenje podataka i izvršavanje alata.

### 2. Clients

Clients su ključne komponente koje olakšavaju interakciju između Hosts i MCP poslužitelja. Clients djeluju kao posrednici, omogućujući Hosts pristup i korištenje funkcionalnosti koje pružaju MCP poslužitelji. Imaju važnu ulogu u osiguravanju glatke komunikacije i učinkovite razmjene podataka unutar MCP arhitekture.

**Clients** su konektori unutar host aplikacije. Oni:

- Šalju zahtjeve poslužiteljima s promptovima/instrukcijama.
- Pregovaraju o mogućnostima s poslužiteljima.
- Upravljaju zahtjevima za izvršenje alata od modela.
- Procesiraju i prikazuju odgovore korisnicima.

### 3. Servers

Servers su odgovorni za obradu zahtjeva MCP klijenata i pružanje odgovarajućih odgovora. Upravljaju različitim operacijama poput dohvaćanja podataka, izvršenja alata i generiranja promptova. Servers osiguravaju da komunikacija između klijenata i Hosts bude učinkovita i pouzdana, održavajući integritet procesa interakcije.

**Servers** su servisi koji pružaju kontekst i mogućnosti. Oni:

- Registriraju dostupne značajke (resurse, promptove, alate)
- Primaju i izvršavaju pozive alata od klijenta
- Pružaju kontekstualne informacije za poboljšanje odgovora modela
- Vraćaju rezultate natrag klijentu
- Održavaju stanje tijekom interakcija kada je potrebno

Servers mogu razvijati bilo tko za proširenje mogućnosti modela specijaliziranim funkcionalnostima.

### 4. Značajke Servers

Servers u Model Context Protocolu (MCP) pružaju temeljne građevne blokove koji omogućuju bogate interakcije između klijenata, hosts i jezičnih modela. Ove značajke su dizajnirane da unaprijede mogućnosti MCP-a nudeći strukturirani kontekst, alate i promptove.

MCP poslužitelji mogu nuditi bilo koju od sljedećih značajki:

#### 📑 Resursi

Resursi u Model Context Protocolu (MCP) obuhvaćaju različite vrste konteksta i podataka koje korisnici ili AI modeli mogu koristiti. To uključuje:

- **Kontekstualni podaci**: Informacije i kontekst koje korisnici ili AI modeli mogu iskoristiti za donošenje odluka i izvršavanje zadataka.
- **Baze znanja i spremišta dokumenata**: Kolekcije strukturiranih i nestrukturiranih podataka, poput članaka, priručnika i znanstvenih radova, koje pružaju vrijedne uvide i informacije.
- **Lokalne datoteke i baze podataka**: Podaci pohranjeni lokalno na uređajima ili unutar baza podataka, dostupni za obradu i analizu.
- **API-ji i web servisi**: Vanjska sučelja i servisi koji nude dodatne podatke i funkcionalnosti, omogućujući integraciju s različitim online resursima i alatima.

Primjer resursa može biti shema baze podataka ili datoteka kojoj se može pristupiti na sljedeći način:

```text
file://log.txt
database://schema
```

### 🤖 Promptovi

Promptovi u Model Context Protocolu (MCP) uključuju različite unaprijed definirane predloške i obrasce interakcije dizajnirane za pojednostavljenje korisničkih radnih tokova i poboljšanje komunikacije. To uključuje:

- **Predložene poruke i radni tokovi**: Unaprijed strukturirane poruke i procesi koji vode korisnike kroz specifične zadatke i interakcije.
- **Unaprijed definirani obrasci interakcije**: Standardizirani slijedovi radnji i odgovora koji omogućuju dosljednu i učinkovitu komunikaciju.
- **Specijalizirani predlošci za razgovore**: Prilagodljivi predlošci namijenjeni za određene vrste razgovora, osiguravajući relevantne i kontekstualno prikladne interakcije.

Predložak prompta može izgledati ovako:

```markdown
Generate a product slogan based on the following {{product}} with the following {{keywords}}
```

#### ⛏️ Alati

Alati u Model Context Protocolu (MCP) su funkcije koje AI model može izvršiti za obavljanje određenih zadataka. Ovi alati su dizajnirani da unaprijede mogućnosti AI modela pružajući strukturirane i pouzdane operacije. Ključni aspekti uključuju:

- **Funkcije koje AI model može izvršiti**: Alati su izvršne funkcije koje AI model može pozvati za obavljanje različitih zadataka.
- **Jedinstveno ime i opis**: Svaki alat ima jedinstveno ime i detaljan opis koji objašnjava njegovu svrhu i funkcionalnost.
- **Parametri i izlazi**: Alati prihvaćaju određene parametre i vraćaju strukturirane rezultate, osiguravajući dosljedne i predvidive ishode.
- **Diskretne funkcije**: Alati obavljaju zasebne funkcije poput web pretraživanja, izračuna i upita baza podataka.

Primjer alata može izgledati ovako:

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

## Značajke klijenata

U Model Context Protocolu (MCP), klijenti nude nekoliko ključnih značajki poslužiteljima, poboljšavajući ukupnu funkcionalnost i interakciju unutar protokola. Jedna od značajki je Sampling.

### 👉 Sampling

- **Agentni postupci inicirani od strane poslužitelja**: Klijenti omogućuju poslužiteljima da samostalno iniciraju specifične radnje ili ponašanja, povećavajući dinamičke mogućnosti sustava.
- **Rekurzivne LLM interakcije**: Ova značajka omogućuje rekurzivne interakcije s velikim jezičnim modelima (LLM), omogućujući složeniju i iterativnu obradu zadataka.
- **Zahtjevanje dodatnih dovršetaka modela**: Poslužitelji mogu tražiti dodatne dovršetke od modela, osiguravajući da su odgovori iscrpni i kontekstualno relevantni.

## Tok informacija u MCP-u

Model Context Protocol (MCP) definira strukturirani tok informacija između hosts, clients, servers i modela. Razumijevanje ovog toka pomaže razjasniti kako se korisnički zahtjevi obrađuju i kako se vanjski alati i podaci integriraju u odgovore modela.

- **Host inicira vezu**  
  Host aplikacija (poput IDE-a ili chat sučelja) uspostavlja vezu s MCP poslužiteljem, obično preko STDIO, WebSocket ili drugog podržanog prijenosa.

- **Pregovaranje o mogućnostima**  
  Klijent (ugrađen u host) i poslužitelj razmjenjuju informacije o podržanim značajkama, alatima, resursima i verzijama protokola. Ovo osigurava da obje strane razumiju koje su mogućnosti dostupne za sesiju.

- **Korisnički zahtjev**  
  Korisnik komunicira s hostom (npr. unosi prompt ili naredbu). Host prikuplja ovaj unos i prosljeđuje ga klijentu na obradu.

- **Korištenje resursa ili alata**  
  - Klijent može zatražiti dodatni kontekst ili resurse od poslužitelja (poput datoteka, unosa u bazu podataka ili članaka iz baze znanja) kako bi obogatio razumijevanje modela.
  - Ako model procijeni da je potreban alat (npr. za dohvat podataka, izvođenje izračuna ili pozivanje API-ja), klijent šalje zahtjev za poziv alata poslužitelju, navodeći ime alata i parametre.

- **Izvršenje na poslužitelju**  
  Poslužitelj prima zahtjev za resursom ili alatom, izvršava potrebne operacije (npr. pokretanje funkcije, upit baze podataka ili dohvat datoteke) i vraća rezultate klijentu u strukturiranom obliku.

- **Generiranje odgovora**  
  Klijent integrira odgovore poslužitelja (podatke resursa, izlaze alata itd.) u tekuću interakciju modela. Model koristi ove informacije za generiranje sveobuhvatnog i kontekstualno relevantnog odgovora.

- **Prikaz rezultata**  
  Host prima konačni rezultat od klijenta i prikazuje ga korisniku, često uključujući i generirani tekst modela i sve rezultate izvršenja alata ili pretraživanja resursa.

Ovaj tok omogućuje MCP-u podršku naprednim, interaktivnim i kontekstualno svjesnim AI aplikacijama besprijekornim povezivanjem modela s vanjskim alatima i izvorima podataka.

## Detalji protokola

MCP (Model Context Protocol) je izgrađen na temelju [JSON-RPC 2.0](https://www.jsonrpc.org/), pružajući standardizirani, jezično-neovisan format poruka za komunikaciju između hosts, clients i servers. Ova osnova omogućuje pouzdane, strukturirane i proširive interakcije na različitim platformama i programskim jezicima.

### Ključne značajke protokola

MCP proširuje JSON-RPC 2.0 dodatnim konvencijama za pozivanje alata, pristup resursima i upravljanje promptovima. Podržava višestruke slojeve prijenosa (STDIO, WebSocket, SSE) i omogućuje sigurnu, proširivu i jezično-neovisnu komunikaciju između komponenti.

#### 🧢 Osnovni protokol

- **JSON-RPC format poruka**: Svi zahtjevi i odgovori koriste JSON-RPC 2.0 specifikaciju, osiguravajući dosljednu strukturu za pozive metoda, parametre, rezultate i obradu pogrešaka.
- **Veze s održavanjem stanja**: MCP sesije održavaju stanje kroz više zahtjeva, podržavajući kontinuirane razgovore, akumulaciju konteksta i upravljanje resursima.
- **Pregovaranje o mogućnostima**: Tijekom uspostave veze, klijenti i poslužitelji razmjenjuju informacije o podržanim značajkama, verzijama protokola, dostupnim alatima i resursima. Ovo osigurava da obje strane razumiju mogućnosti jedna druge i mogu se prilagoditi.

#### ➕ Dodatne usluge

Ispod su neke dodatne usluge i proširenja protokola koje MCP nudi za poboljšanje iskustva programera i omogućavanje naprednih scenarija:

- **Opcije konfiguracije**: MCP omogućuje dinamičku konfiguraciju parametara sesije, poput dozvola za alate, pristupa resursima i postavki modela, prilagođenih svakoj interakciji.
- **Praćenje napretka**: Operacije koje traju dulje mogu izvještavati o napretku, omogućujući responzivna korisnička sučelja i bolje korisničko iskustvo tijekom složenih zadataka.
- **Otkaži zahtjev**: Klijenti mogu otkazati zahtjeve u tijeku, dopuštajući korisnicima da prekinu operacije koje više nisu potrebne ili traju predugo.
- **Izvještavanje o pogreškama**: Standardizirane poruke i kodovi pogrešaka pomažu u dijagnosticiranju problema, elegantnom rukovanju neuspjesima i pružanju korisnih povratnih informacija korisnicima i programerima.
- **Logiranje**: I klijenti i poslužitelji mogu emitirati strukturirane zapise za reviziju, otklanjanje pogrešaka i nadzor interakcija protokola.

Iskorištavanjem ovih značajki protokola, MCP osigurava robusnu, sigurnu i fleksibilnu komunikaciju između jezičnih modela i vanjskih alata ili izvora podataka.

### 🔐 Sigurnosne smjernice

Implementacije MCP-a trebaju se pridržavati nekoliko ključnih sigurnosnih principa kako bi osigurale sigurne i pouzdane interakcije:

- **Korisnički pristanak i kontrola**: Korisnici moraju dati izričit pristanak prije nego što se pristupi bilo kojim podacima ili izvrše operacije. Trebaju imati jasnu kontrolu nad time koje se podatke dijele i koje su radnje ovlaštene, podržano intuitivnim korisničkim sučeljima za pregled i odobravanje aktivnosti.

- **Privatnost podataka**: Korisnički podaci trebaju biti dostupni samo uz izričiti pristanak i moraju biti zaštićeni odgovarajućim kontrolama pristupa. Implementacije MCP-a moraju spriječiti neovlašteni prijenos podataka i osigurati da privatnost bude očuvana tijekom svih interakcija.

- **Sigurnost alata**: Prije poziva bilo kojeg alata potreban je izričit korisnički pristanak. Korisnici trebaju jasno razumjeti funkcionalnost svakog alata, a moraju se provoditi stroge sigurnosne granice kako bi se spriječilo neželjeno ili nesigurno izvršavanje alata.

Slijedeći ove principe, MCP osigurava da se povjerenje korisnika, privatnost i sigurnost održavaju kroz sve interakcije protokola.

## Primjeri koda: ključne komponente

Ispod su primjeri koda u nekoliko popularnih programskih jezika koji ilustriraju kako implementirati ključne MCP poslužiteljske komponente i alate.

### .NET primjer: Kreiranje jednostavnog MCP poslužitelja s alatima

Ovdje je praktični .NET primjer koda koji pokazuje kako implementirati jednostavan MCP poslužitelj s prilagođenim alatima. Ovaj primjer prikazuje kako definirati i registrirati alate, obrađivati zahtjeve i povezati poslužitelj koristeći Model Context Protocol.

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

### Java primjer: MCP poslužiteljske komponente

Ovaj primjer prikazuje isti MCP poslužitelj i registraciju alata kao i .NET primjer gore, ali implementiran u Javi.

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

### Python primjer: Izgradnja MCP poslužitelja

U ovom primjeru pokazujemo kako izgraditi MCP poslužitelj u Pythonu. Također su prikazana dva različita načina za kreiranje alata.

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

### JavaScript primjer: Kreiranje MCP poslužitelja

Ovaj primjer pokazuje kreiranje MCP poslužitelja u JavaScriptu i kako registrirati dva alata vezana uz vremensku prognozu.

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

Ovaj JavaScript primjer demonstrira kako kreirati MCP klijenta koji se povezuje na poslužitelj, šalje prompt i obrađuje odgovor uključujući pozive alata koji su napravljeni.

## Sigurnost i autorizacija

MCP uključuje nekoliko ugrađenih koncepata i mehanizama za upravljanje sigurnošću i autorizacijom tijekom protokola:

1. **Kontrola dozvola za alate**  
  Klijenti mogu specificirati koje alate model smije koristiti tijekom sesije. Ovo osigurava da

**Izjava o odricanju odgovornosti**:  
Ovaj je dokument preveden korištenjem AI prevoditeljskog servisa [Co-op Translator](https://github.com/Azure/co-op-translator). Iako težimo točnosti, imajte na umu da automatski prijevodi mogu sadržavati pogreške ili netočnosti. Izvorni dokument na izvornom jeziku treba smatrati autoritativnim izvorom. Za kritične informacije preporučuje se profesionalni ljudski prijevod. Ne snosimo odgovornost za bilo kakva nesporazumevanja ili pogrešna tumačenja proizašla iz korištenja ovog prijevoda.