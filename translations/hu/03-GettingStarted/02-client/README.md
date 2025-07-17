<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "8da8a0fd44d58fab5979d0f2914a1f37",
  "translation_date": "2025-07-17T10:29:26+00:00",
  "source_file": "03-GettingStarted/02-client/README.md",
  "language_code": "hu"
}
-->
# Ügyfél létrehozása

Az ügyfelek egyedi alkalmazások vagy szkriptek, amelyek közvetlenül kommunikálnak egy MCP szerverrel erőforrások, eszközök és promptok lekérésére. Ellentétben az inspector eszköz használatával, amely grafikus felületet biztosít a szerverrel való interakcióhoz, a saját ügyfél megírása programozott és automatizált műveleteket tesz lehetővé. Ezáltal a fejlesztők beépíthetik az MCP képességeit saját munkafolyamataikba, automatizálhatják a feladatokat, és testreszabott megoldásokat hozhatnak létre speciális igényekhez.

## Áttekintés

Ez a lecke bemutatja az ügyfelek fogalmát a Model Context Protocol (MCP) ökoszisztémán belül. Megtanulod, hogyan írj saját ügyfelet, és hogyan csatlakoztasd azt egy MCP szerverhez.

## Tanulási célok

A lecke végére képes leszel:

- Megérteni, mit tud egy ügyfél.
- Megírni a saját ügyfeledet.
- Csatlakoztatni és tesztelni az ügyfelet egy MCP szerverrel, hogy megbizonyosodj arról, hogy az megfelelően működik.

## Mi szükséges egy ügyfél megírásához?

Egy ügyfél megírásához a következőket kell tenned:

- **A megfelelő könyvtárak importálása.** Ugyanazt a könyvtárat használod, mint korábban, csak más konstrukciókkal.
- **Egy ügyfél példányosítása.** Ez magában foglalja egy ügyfél példány létrehozását és csatlakoztatását a kiválasztott szállítási módhoz.
- **Döntés arról, hogy mely erőforrásokat listázod.** Az MCP szervered erőforrásokat, eszközöket és promptokat kínál, el kell döntened, melyeket szeretnéd megjeleníteni.
- **Az ügyfél integrálása egy host alkalmazásba.** Miután ismered a szerver képességeit, integrálnod kell az ügyfelet a host alkalmazásba, hogy ha a felhasználó promptot vagy más parancsot ír be, a megfelelő szerver funkció meghívódjon.

Most, hogy nagy vonalakban értjük, mit fogunk csinálni, nézzünk meg egy példát.

### Egy példa ügyfél

Tekintsük meg ezt a példa ügyfelet:

### TypeScript

```typescript
import { Client } from "@modelcontextprotocol/sdk/client/index.js";
import { StdioClientTransport } from "@modelcontextprotocol/sdk/client/stdio.js";

const transport = new StdioClientTransport({
  command: "node",
  args: ["server.js"]
});

const client = new Client(
  {
    name: "example-client",
    version: "1.0.0"
  }
);

await client.connect(transport);

// List prompts
const prompts = await client.listPrompts();

// Get a prompt
const prompt = await client.getPrompt({
  name: "example-prompt",
  arguments: {
    arg1: "value"
  }
});

// List resources
const resources = await client.listResources();

// Read a resource
const resource = await client.readResource({
  uri: "file:///example.txt"
});

// Call a tool
const result = await client.callTool({
  name: "example-tool",
  arguments: {
    arg1: "value"
  }
});
```

A fenti kódban:

- Importáljuk a könyvtárakat
- Létrehozunk egy ügyfél példányt, és stdio szállítással csatlakozunk.
- Listázzuk a promptokat, erőforrásokat és eszközöket, majd mindet meghívjuk.

Íme, egy ügyfél, amely képes kommunikálni egy MCP szerverrel.

A következő gyakorlatban szánjunk időt arra, hogy részletesen átvesszük a kódrészleteket és elmagyarázzuk, mi történik.

## Gyakorlat: Ügyfél írása

Ahogy fent említettük, szánjunk időt a kód magyarázatára, és természetesen, ha szeretnéd, kódolj velünk együtt.

### -1- Könyvtárak importálása

Importáljuk a szükséges könyvtárakat, szükségünk lesz hivatkozásokra az ügyfélhez és a választott szállítási protokollhoz, az stdio-hoz. Az stdio egy protokoll helyi gépen futó dolgokhoz. Az SSE egy másik szállítási protokoll, amit a későbbi fejezetekben mutatunk be, de most maradjunk az stdio-nál.

### TypeScript

```typescript
import { Client } from "@modelcontextprotocol/sdk/client/index.js";
import { StdioClientTransport } from "@modelcontextprotocol/sdk/client/stdio.js";
```

### Python

```python
from mcp import ClientSession, StdioServerParameters, types
from mcp.client.stdio import stdio_client
```

### .NET

```csharp
using Microsoft.Extensions.AI;
using Microsoft.Extensions.Configuration;
using Microsoft.Extensions.Hosting;
using ModelContextProtocol.Client;
using ModelContextProtocol.Protocol.Transport;
```

### Java

Java esetén egy olyan ügyfelet hozol létre, amely az előző gyakorlatban használt MCP szerverhez csatlakozik. A [Getting Started with MCP Server](../../../../03-GettingStarted/01-first-server/solution/java) Java Spring Boot projektstruktúráját használva hozz létre egy új Java osztályt `SDKClient` néven a `src/main/java/com/microsoft/mcp/sample/client/` mappában, és add hozzá a következő importokat:

```java
import java.util.Map;
import org.springframework.web.reactive.function.client.WebClient;
import io.modelcontextprotocol.client.McpClient;
import io.modelcontextprotocol.client.transport.WebFluxSseClientTransport;
import io.modelcontextprotocol.spec.McpClientTransport;
import io.modelcontextprotocol.spec.McpSchema.CallToolRequest;
import io.modelcontextprotocol.spec.McpSchema.CallToolResult;
import io.modelcontextprotocol.spec.McpSchema.ListToolsResult;
```

Folytassuk a példányosítással.

### -2- Ügyfél és szállítás példányosítása

Létre kell hoznunk egy példányt a szállításból és az ügyfélből:

### TypeScript

```typescript
const transport = new StdioClientTransport({
  command: "node",
  args: ["server.js"]
});

const client = new Client(
  {
    name: "example-client",
    version: "1.0.0"
  }
);

await client.connect(transport);
```

A fenti kódban:

- Létrehoztunk egy stdio szállítási példányt. Figyeld meg, hogy megadja a parancsot és az argumentumokat a szerver megtalálásához és elindításához, mert ezt meg kell tennünk az ügyfél létrehozásakor.

    ```typescript
    const transport = new StdioClientTransport({
        command: "node",
        args: ["server.js"]
    });
    ```

- Példányosítottunk egy ügyfelet, megadva neki nevet és verziót.

    ```typescript
    const client = new Client(
    {
        name: "example-client",
        version: "1.0.0"
    });
    ```

- Csatlakoztattuk az ügyfelet a kiválasztott szállításhoz.

    ```typescript
    await client.connect(transport);
    ```

### Python

```python
from mcp import ClientSession, StdioServerParameters, types
from mcp.client.stdio import stdio_client

# Create server parameters for stdio connection
server_params = StdioServerParameters(
    command="mcp",  # Executable
    args=["run", "server.py"],  # Optional command line arguments
    env=None,  # Optional environment variables
)

async def run():
    async with stdio_client(server_params) as (read, write):
        async with ClientSession(
            read, write
        ) as session:
            # Initialize the connection
            await session.initialize()

          

if __name__ == "__main__":
    import asyncio

    asyncio.run(run())
```

A fenti kódban:

- Importáltuk a szükséges könyvtárakat
- Létrehoztunk egy szerver paraméter objektumot, amelyet a szerver futtatásához használunk, hogy az ügyfél csatlakozni tudjon hozzá.
- Definiáltunk egy `run` metódust, amely meghívja a `stdio_client`-et, ami elindítja az ügyfél munkamenetet.
- Létrehoztunk egy belépési pontot, ahol az `asyncio.run`-nak adjuk át a `run` metódust.

### .NET

```dotnet
using Microsoft.Extensions.AI;
using Microsoft.Extensions.Configuration;
using Microsoft.Extensions.Hosting;
using ModelContextProtocol.Client;
using ModelContextProtocol.Protocol.Transport;

var builder = Host.CreateApplicationBuilder(args);

builder.Configuration
    .AddEnvironmentVariables()
    .AddUserSecrets<Program>();



var clientTransport = new StdioClientTransport(new()
{
    Name = "Demo Server",
    Command = "dotnet",
    Arguments = ["run", "--project", "path/to/file.csproj"],
});

await using var mcpClient = await McpClientFactory.CreateAsync(clientTransport);
```

A fenti kódban:

- Importáltuk a szükséges könyvtárakat.
- Létrehoztunk egy stdio szállítást és egy `mcpClient` ügyfelet. Ezt fogjuk használni az MCP szerver funkcióinak listázására és meghívására.

Megjegyzés: az "Arguments" mezőben vagy a *.csproj* fájlra, vagy a futtatható állományra mutathatsz.

### Java

```java
public class SDKClient {
    
    public static void main(String[] args) {
        var transport = new WebFluxSseClientTransport(WebClient.builder().baseUrl("http://localhost:8080"));
        new SDKClient(transport).run();
    }
    
    private final McpClientTransport transport;

    public SDKClient(McpClientTransport transport) {
        this.transport = transport;
    }

    public void run() {
        var client = McpClient.sync(this.transport).build();
        client.initialize();
        
        // Your client logic goes here
    }
}
```

A fenti kódban:

- Létrehoztunk egy main metódust, amely beállít egy SSE szállítást, amely a `http://localhost:8080` címre mutat, ahol az MCP szerver futni fog.
- Létrehoztunk egy ügyfél osztályt, amely a szállítást konstruktor paraméterként kapja.
- A `run` metódusban létrehozunk egy szinkron MCP ügyfelet a szállítással, és inicializáljuk a kapcsolatot.
- SSE (Server-Sent Events) szállítást használunk, amely alkalmas HTTP alapú kommunikációra Java Spring Boot MCP szerverekkel.

### -3- A szerver funkcióinak listázása

Most már van egy ügyfelünk, amely csatlakozni tud, ha a programot futtatjuk. Azonban még nem listázza a funkciókat, ezt tegyük meg most:

### TypeScript

```typescript
// List prompts
const prompts = await client.listPrompts();

// List resources
const resources = await client.listResources();

// list tools
const tools = await client.listTools();
```

### Python

```python
# List available resources
resources = await session.list_resources()
print("LISTING RESOURCES")
for resource in resources:
    print("Resource: ", resource)

# List available tools
tools = await session.list_tools()
print("LISTING TOOLS")
for tool in tools.tools:
    print("Tool: ", tool.name)
```

Itt listázzuk a rendelkezésre álló erőforrásokat `list_resources()` és eszközöket `list_tools`, majd kiírjuk őket.

### .NET

```dotnet
foreach (var tool in await client.ListToolsAsync())
{
    Console.WriteLine($"{tool.Name} ({tool.Description})");
}
```

Fent egy példa arra, hogyan listázhatjuk a szerveren lévő eszközöket. Minden eszköz nevét kiírjuk.

### Java

```java
// List and demonstrate tools
ListToolsResult toolsList = client.listTools();
System.out.println("Available Tools = " + toolsList);

// You can also ping the server to verify connection
client.ping();
```

A fenti kódban:

- Meghívtuk a `listTools()` metódust, hogy lekérjük az összes elérhető eszközt az MCP szerverről.
- Használtuk a `ping()` metódust, hogy ellenőrizzük a szerverrel való kapcsolatot.
- A `ListToolsResult` tartalmazza az összes eszköz nevét, leírását és bemeneti sémáit.

Remek, most már megvannak az összes funkció. De mikor használjuk őket? Ez az ügyfél elég egyszerű, azaz explicit módon kell meghívnunk a funkciókat, amikor szükségünk van rájuk. A következő fejezetben egy fejlettebb ügyfelet készítünk, amely saját nagy nyelvi modellel (LLM) rendelkezik. Addig is nézzük meg, hogyan hívhatjuk meg a szerver funkcióit:

### -4- Funkciók meghívása

A funkciók meghívásához meg kell győződnünk arról, hogy a megfelelő argumentumokat adjuk meg, és bizonyos esetekben a meghívni kívánt név is szükséges.

### TypeScript

```typescript

// Read a resource
const resource = await client.readResource({
  uri: "file:///example.txt"
});

// Call a tool
const result = await client.callTool({
  name: "example-tool",
  arguments: {
    arg1: "value"
  }
});

// call prompt
const promptResult = await client.getPrompt({
    name: "review-code",
    arguments: {
        code: "console.log(\"Hello world\")"
    }
})
```

A fenti kódban:

- Egy erőforrást olvasunk be, a `readResource()`-t hívjuk meg, megadva a `uri`-t. Íme, hogyan nézhet ki ez a szerveren:

    ```typescript
    server.resource(
        "readFile",
        new ResourceTemplate("file://{name}", { list: undefined }),
        async (uri, { name }) => ({
          contents: [{
            uri: uri.href,
            text: `Hello, ${name}!`
          }]
        })
    );
    ```

    A `uri` értékünk `file://example.txt` megfelel a szerveren lévő `file://{name}`-nek. Az `example.txt` a `name`-hez lesz hozzárendelve.

- Egy eszközt hívunk meg, megadva a `name`-t és az `arguments`-t így:

    ```typescript
    const result = await client.callTool({
        name: "example-tool",
        arguments: {
            arg1: "value"
        }
    });
    ```

- Promptot kérünk, a `getPrompt()`-ot hívjuk meg `name` és `arguments` paraméterekkel. A szerver kódja így néz ki:

    ```typescript
    server.prompt(
        "review-code",
        { code: z.string() },
        ({ code }) => ({
            messages: [{
            role: "user",
            content: {
                type: "text",
                text: `Please review this code:\n\n${code}`
            }
            }]
        })
    );
    ```

    Így a kliens kódod is így néz ki, hogy megfeleljen a szerveren deklaráltnak:

    ```typescript
    const promptResult = await client.getPrompt({
        name: "review-code",
        arguments: {
            code: "console.log(\"Hello world\")"
        }
    })
    ```

### Python

```python
# Read a resource
print("READING RESOURCE")
content, mime_type = await session.read_resource("greeting://hello")

# Call a tool
print("CALL TOOL")
result = await session.call_tool("add", arguments={"a": 1, "b": 7})
print(result.content)
```

A fenti kódban:

- Meghívtunk egy `greeting` nevű erőforrást a `read_resource` segítségével.
- Meghívtunk egy `add` nevű eszközt a `call_tool` segítségével.

### .NET

1. Adjunk hozzá kódot egy eszköz meghívásához:

  ```csharp
  var result = await mcpClient.CallToolAsync(
      "Add",
      new Dictionary<string, object?>() { ["a"] = 1, ["b"] = 3  },
      cancellationToken:CancellationToken.None);
  ```

1. Az eredmény kiíratásához itt egy példa kód:

  ```csharp
  Console.WriteLine(result.Content.First(c => c.Type == "text").Text);
  // Sum 4
  ```

### Java

```java
// Call various calculator tools
CallToolResult resultAdd = client.callTool(new CallToolRequest("add", Map.of("a", 5.0, "b", 3.0)));
System.out.println("Add Result = " + resultAdd);

CallToolResult resultSubtract = client.callTool(new CallToolRequest("subtract", Map.of("a", 10.0, "b", 4.0)));
System.out.println("Subtract Result = " + resultSubtract);

CallToolResult resultMultiply = client.callTool(new CallToolRequest("multiply", Map.of("a", 6.0, "b", 7.0)));
System.out.println("Multiply Result = " + resultMultiply);

CallToolResult resultDivide = client.callTool(new CallToolRequest("divide", Map.of("a", 20.0, "b", 4.0)));
System.out.println("Divide Result = " + resultDivide);

CallToolResult resultHelp = client.callTool(new CallToolRequest("help", Map.of()));
System.out.println("Help = " + resultHelp);
```

A fenti kódban:

- Több számológép eszközt hívtunk meg a `callTool()` metódussal, `CallToolRequest` objektumokat használva.
- Minden eszköz hívás megadja az eszköz nevét és egy `Map`-et az eszköz által igényelt argumentumokkal.
- A szerver eszközök specifikus paraméterneveket várnak (például "a", "b" matematikai műveletekhez).
- Az eredmények `CallToolResult` objektumokként érkeznek, amelyek tartalmazzák a szerver válaszát.

### -5- Az ügyfél futtatása

Az ügyfél futtatásához írd be a következő parancsot a terminálba:

### TypeScript

Add hozzá a következő bejegyzést a *package.json* "scripts" szekciójához:

```json
"client": "tsx && node build/client.js"
```

```sh
npm run client
```

### Python

Futtasd az ügyfelet a következő paranccsal:

```sh
python client.py
```

### .NET

```sh
dotnet run
```

### Java

Először győződj meg róla, hogy az MCP szerver fut a `http://localhost:8080` címen. Ezután futtasd az ügyfelet:

```bash
# Build you project
./mvnw clean compile

# Run the client
./mvnw exec:java -Dexec.mainClass="com.microsoft.mcp.sample.client.SDKClient"
```

Alternatívaként futtathatod a teljes kliens projektet, amely megtalálható a `03-GettingStarted\02-client\solution\java` megoldás mappában:

```bash
# Navigate to the solution directory
cd 03-GettingStarted/02-client/solution/java

# Build and run the JAR
./mvnw clean package
java -jar target/calculator-client-0.0.1-SNAPSHOT.jar
```

## Feladat

Ebben a feladatban a tanultakat felhasználva készítsd el a saját ügyfeledet.

Itt egy szerver, amelyet használhatsz, és amelyet az ügyfél kódoddal kell meghívnod. Próbálj meg több funkciót hozzáadni a szerverhez, hogy érdekesebb legyen.

### TypeScript

```typescript
import { McpServer, ResourceTemplate } from "@modelcontextprotocol/sdk/server/mcp.js";
import { StdioServerTransport } from "@modelcontextprotocol/sdk/server/stdio.js";
import { z } from "zod";

// Create an MCP server
const server = new McpServer({
  name: "Demo",
  version: "1.0.0"
});

// Add an addition tool
server.tool("add",
  { a: z.number(), b: z.number() },
  async ({ a, b }) => ({
    content: [{ type: "text", text: String(a + b) }]
  })
);

// Add a dynamic greeting resource
server.resource(
  "greeting",
  new ResourceTemplate("greeting://{name}", { list: undefined }),
  async (uri, { name }) => ({
    contents: [{
      uri: uri.href,
      text: `Hello, ${name}!`
    }]
  })
);

// Start receiving messages on stdin and sending messages on stdout

async function main() {
  const transport = new StdioServerTransport();
  await server.connect(transport);
  console.error("MCPServer started on stdin/stdout");
}

main().catch((error) => {
  console.error("Fatal error: ", error);
  process.exit(1);
});
```

### Python

```python
# server.py
from mcp.server.fastmcp import FastMCP

# Create an MCP server
mcp = FastMCP("Demo")


# Add an addition tool
@mcp.tool()
def add(a: int, b: int) -> int:
    """Add two numbers"""
    return a + b


# Add a dynamic greeting resource
@mcp.resource("greeting://{name}")
def get_greeting(name: str) -> str:
    """Get a personalized greeting"""
    return f"Hello, {name}!"

```

### .NET

```csharp
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Hosting;
using Microsoft.Extensions.Logging;
using ModelContextProtocol.Server;
using System.ComponentModel;

var builder = Host.CreateApplicationBuilder(args);
builder.Logging.AddConsole(consoleLogOptions =>
{
    // Configure all logs to go to stderr
    consoleLogOptions.LogToStandardErrorThreshold = LogLevel.Trace;
});

builder.Services
    .AddMcpServer()
    .WithStdioServerTransport()
    .WithToolsFromAssembly();
await builder.Build().RunAsync();

[McpServerToolType]
public static class CalculatorTool
{
    [McpServerTool, Description("Adds two numbers")]
    public static string Add(int a, int b) => $"Sum {a + b}";
}
```

Nézd meg ezt a projektet, hogy hogyan tudsz [promptokat és erőforrásokat hozzáadni](https://github.com/modelcontextprotocol/csharp-sdk/blob/main/samples/EverythingServer/Program.cs).

Ezenkívül nézd meg ezt a linket, hogy hogyan lehet [promptokat és erőforrásokat meghívni](https://github.com/modelcontextprotocol/csharp-sdk/blob/main/src/ModelContextProtocol/Client/).

## Megoldás

A **megoldás mappa** teljes, futtatható ügyfél implementációkat tartalmaz, amelyek bemutatják a tutorialban tárgyalt összes fogalmat. Minden megoldás tartalmazza az ügyfél és a szerver kódját, különálló, önálló projektekben rendszerezve.

### 📁 Megoldás struktúrája

A megoldás könyvtár programozási nyelv szerint van rendezve:

```
solution/
├── typescript/          # TypeScript client with npm/Node.js setup
│   ├── package.json     # Dependencies and scripts
│   ├── tsconfig.json    # TypeScript configuration
│   └── src/             # Source code
├── java/                # Java Spring Boot client project
│   ├── pom.xml          # Maven configuration
│   ├── src/             # Java source files
│   └── mvnw            # Maven wrapper
├── python/              # Python client implementation
│   ├── client.py        # Main client code
│   ├── server.py        # Compatible server
│   └── README.md        # Python-specific instructions
├── dotnet/              # .NET client project
│   ├── dotnet.csproj    # Project configuration
│   ├── Program.cs       # Main client code
│   └── dotnet.sln       # Solution file
└── server/              # Additional .NET server implementation
    ├── Program.cs       # Server code
    └── server.csproj    # Server project file
```

### 🚀 Mit tartalmaz minden megoldás

Minden nyelvspecifikus megoldás tartalmaz:

- **Teljes ügyfél implementációt** a tutorial összes funkciójával
- **Működő projektstruktúrát** megfelelő függőségekkel és konfigurációval
- **Build és futtató szkripteket** az egyszerű beállításhoz és futtatáshoz
- **Részletes README-t** nyelvspecifikus utasításokkal
- **Hibakezelési és eredményfeldolgozási példákat**

### 📖 A megoldások használata

1. **Navigálj a választott nyelv mappájába**:
   ```bash
   cd solution/typescript/    # For TypeScript
   cd solution/java/          # For Java
   cd solution/python/        # For Python
   cd solution/dotnet/        # For .NET
   ```

2. **Kövesd a README utasításait** az adott mappában:
   - Függőségek telepítése
   - Projekt buildelése
   - Ügyfél futtatása

3. **Példa kimenet, amit látnod kell:**
   ```text
   Prompt: Please review this code: console.log("hello");
   Resource template: file
   Tool result: { content: [ { type: 'text', text: '9' } ] }
   ```

A teljes dokumentációért és lépésről lépésre útmutatóért lásd: **[📖 Megoldás dokumentáció](./solution/README.md)**

## 🎯 Teljes példák

Teljes, működő ügyfél implementációkat biztosítunk minden, a tutorialban tárgyalt programozási nyelvhez. Ezek a példák bemutatják a fent leírt teljes funkcionalitást, és használhatók referenciaként vagy kiindulópontként saját projektjeidhez.

### Elérhető teljes példák

| Nyelv    | Fájl                          | Leírás                                                      |
|----------|-------------------------------|-------------------------------------------------------------|
| **Java** | [`client_example_java.java`](../../../../03-GettingStarted/02-client/client_example_java.java)       | Teljes Java ügyfél SSE szállítással, átfogó hibakezeléssel  |
| **C#**   | [`client_example_csharp.cs`](../../../../03-GettingStarted/02-client/client_example_csharp.cs)       | Teljes C# ügyfél stdio szállítással, automatikus szerverindítással |
| **TypeScript** | [`client_example_typescript.ts`](../../../../03-GettingStarted/02-client/client_example_typescript.ts) | Teljes TypeScript ügyfél teljes MCP protokoll támogatással  |
| **Python** | [`client_example_python.py`](../../../../03-GettingStarted/02-client/client_example_python.py)       | Teljes Python ügyfél async/await mintákkal                   |

Minden teljes példa tartalmaz:

- ✅ **Kapcsolat létrehozását** és hibakezelést
- ✅ **Szerver felfedezést** (eszközök, erőforrások, promptok ahol alkalmazható)
- ✅ **Számológép műveleteket** (összeadás, kivonás, szorzás, osztás, segítség)
- ✅ **Eredmény feldolgozást** és formázott kimenetet
- ✅ **Átfogó hibakezelést**
- ✅ **Tiszta, dokumentált kódot** lépésről lépésre kommentekkel

### Kezdés a teljes példákkal

1. **Válaszd ki a preferált nyelvet** a fenti táblázatból
2. **Nézd át a teljes példa fájlt**, hogy megértsd a teljes implementációt
3. **Futtasd a példát** a [`complete_examples.md`](./complete_examples.md) útmutató szerint
4. **Módosítsd és bővítsd** a példát a saját igényeid szerint

A példák futtatásáról és testreszabásáról részletes dokumentációt találsz itt: **[📖 Teljes példák dokumentáció](./complete_examples.md)**

### 💡 Megoldás vs. Teljes példák

| **Megoldás mappa**           | **Teljes példák**                  |
|-----------------------------|----------------------------------|
| Teljes projektstruktúra build fájlokkal | Egyszerű, egylapos implementációk       |
| Függősége
Mindkét megközelítés értékes – a **solution folder** teljes projektekhez, míg a **complete examples** tanuláshoz és referenciaként használható.

## Főbb tanulságok

Ebben a fejezetben a kliensekkel kapcsolatban a következőket érdemes megjegyezni:

- Használhatók a szerver funkcióinak felfedezésére és meghívására egyaránt.
- Elindíthatnak egy szervert, miközben maguk is elindulnak (ahogy ebben a fejezetben), de a kliensek már futó szerverekhez is csatlakozhatnak.
- Kiváló módja a szerver képességeinek tesztelésére, az Inspectorhoz hasonló alternatívák mellett, ahogy az előző fejezetben is bemutattuk.

## További források

- [Building clients in MCP](https://modelcontextprotocol.io/quickstart/client)

## Minták

- [Java Calculator](../samples/java/calculator/README.md)
- [.Net Calculator](../../../../03-GettingStarted/samples/csharp)
- [JavaScript Calculator](../samples/javascript/README.md)
- [TypeScript Calculator](../samples/typescript/README.md)
- [Python Calculator](../../../../03-GettingStarted/samples/python)

## Mi következik

- Következő: [Creating a client with an LLM](../03-llm-client/README.md)

**Jogi nyilatkozat**:  
Ez a dokumentum az AI fordító szolgáltatás, a [Co-op Translator](https://github.com/Azure/co-op-translator) segítségével készült. Bár a pontosságra törekszünk, kérjük, vegye figyelembe, hogy az automatikus fordítások hibákat vagy pontatlanságokat tartalmazhatnak. Az eredeti dokumentum az anyanyelvén tekintendő hiteles forrásnak. Kritikus információk esetén professzionális emberi fordítást javaslunk. Nem vállalunk felelősséget a fordítás használatából eredő félreértésekért vagy téves értelmezésekért.