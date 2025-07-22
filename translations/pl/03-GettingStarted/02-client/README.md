<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "22afa94e3912cd37af9ff20cf4aebc93",
  "translation_date": "2025-07-22T09:00:31+00:00",
  "source_file": "03-GettingStarted/02-client/README.md",
  "language_code": "pl"
}
-->
# Tworzenie klienta

Klienci to niestandardowe aplikacje lub skrypty, które komunikują się bezpośrednio z serwerem MCP w celu żądania zasobów, narzędzi i podpowiedzi. W przeciwieństwie do korzystania z narzędzia inspektora, które oferuje graficzny interfejs do interakcji z serwerem, napisanie własnego klienta umożliwia programistyczne i zautomatyzowane interakcje. Dzięki temu deweloperzy mogą integrować możliwości MCP z własnymi procesami, automatyzować zadania i budować niestandardowe rozwiązania dostosowane do konkretnych potrzeb.

## Przegląd

Ta lekcja wprowadza pojęcie klientów w ekosystemie Model Context Protocol (MCP). Dowiesz się, jak napisać własnego klienta i połączyć go z serwerem MCP.

## Cele nauki

Po ukończeniu tej lekcji będziesz w stanie:

- Zrozumieć, co może robić klient.
- Napisać własnego klienta.
- Połączyć i przetestować klienta z serwerem MCP, aby upewnić się, że działa zgodnie z oczekiwaniami.

## Co jest potrzebne do napisania klienta?

Aby napisać klienta, musisz wykonać następujące kroki:

- **Zaimportować odpowiednie biblioteki**. Użyjesz tej samej biblioteki co wcześniej, ale z innymi konstrukcjami.
- **Utworzyć instancję klienta**. Obejmuje to stworzenie instancji klienta i połączenie jej z wybraną metodą transportu.
- **Zdecydować, jakie zasoby wylistować**. Twój serwer MCP oferuje zasoby, narzędzia i podpowiedzi, musisz zdecydować, które z nich wylistować.
- **Zintegrować klienta z aplikacją hostującą**. Gdy poznasz możliwości serwera, musisz zintegrować je z aplikacją hostującą, aby użytkownik mógł wywoływać odpowiednie funkcje serwera, wpisując podpowiedź lub inne polecenie.

Teraz, gdy rozumiemy ogólny zarys tego, co zamierzamy zrobić, przejdźmy do przykładu.

### Przykład klienta

Przyjrzyjmy się przykładowemu klientowi:

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

W powyższym kodzie:

- Importujemy biblioteki.
- Tworzymy instancję klienta i łączymy ją za pomocą stdio jako metody transportu.
- Wylistowujemy podpowiedzi, zasoby i narzędzia oraz wywołujemy je wszystkie.

I oto mamy klienta, który może komunikować się z serwerem MCP.

W następnej sekcji ćwiczeń poświęcimy czas na rozbicie każdego fragmentu kodu i wyjaśnienie, co się dzieje.

## Ćwiczenie: Pisanie klienta

Jak wspomniano wcześniej, poświęćmy czas na wyjaśnienie kodu. Możesz również kodować równolegle, jeśli chcesz.

### -1- Importowanie bibliotek

Zaimportujmy potrzebne biblioteki. Będziemy potrzebować odniesień do klienta i wybranego protokołu transportowego, stdio. stdio to protokół przeznaczony do uruchamiania na lokalnym komputerze. SSE to inny protokół transportowy, który pokażemy w przyszłych rozdziałach, ale to Twoja alternatywa. Na razie jednak kontynuujmy ze stdio.

#### TypeScript

```typescript
import { Client } from "@modelcontextprotocol/sdk/client/index.js";
import { StdioClientTransport } from "@modelcontextprotocol/sdk/client/stdio.js";
```

#### Python

```python
from mcp import ClientSession, StdioServerParameters, types
from mcp.client.stdio import stdio_client
```

#### .NET

```csharp
using Microsoft.Extensions.AI;
using Microsoft.Extensions.Configuration;
using Microsoft.Extensions.Hosting;
using ModelContextProtocol.Client;
using ModelContextProtocol.Protocol.Transport;
```

#### Java

Dla Javy utworzysz klienta, który łączy się z serwerem MCP z poprzedniego ćwiczenia. Korzystając z tej samej struktury projektu Java Spring Boot z [Pierwsze kroki z serwerem MCP](../../../../03-GettingStarted/01-first-server/solution/java), utwórz nową klasę Java o nazwie `SDKClient` w folderze `src/main/java/com/microsoft/mcp/sample/client/` i dodaj następujące importy:

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

Przejdźmy do instancjonowania.

### -2- Tworzenie instancji klienta i transportu

Musimy utworzyć instancję transportu oraz naszego klienta:

#### TypeScript

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

W powyższym kodzie:

- Utworzono instancję transportu stdio. Zwróć uwagę, jak określa polecenie i argumenty, aby znaleźć i uruchomić serwer, ponieważ jest to coś, co musimy zrobić podczas tworzenia klienta.

    ```typescript
    const transport = new StdioClientTransport({
        command: "node",
        args: ["server.js"]
    });
    ```

- Utworzono instancję klienta, podając jej nazwę i wersję.

    ```typescript
    const client = new Client(
    {
        name: "example-client",
        version: "1.0.0"
    });
    ```

- Połączono klienta z wybranym transportem.

    ```typescript
    await client.connect(transport);
    ```

#### Python

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

W powyższym kodzie:

- Zaimportowano potrzebne biblioteki.
- Utworzono obiekt parametrów serwera, który zostanie użyty do uruchomienia serwera, aby można było połączyć się z nim za pomocą klienta.
- Zdefiniowano metodę `run`, która wywołuje `stdio_client`, rozpoczynając sesję klienta.
- Utworzono punkt wejścia, w którym metoda `run` jest przekazywana do `asyncio.run`.

#### .NET

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

W powyższym kodzie:

- Zaimportowano potrzebne biblioteki.
- Utworzono transport stdio i klienta `mcpClient`. Ten ostatni będzie używany do listowania i wywoływania funkcji na serwerze MCP.

Uwaga: w "Arguments" możesz wskazać plik *.csproj* lub plik wykonywalny.

#### Java

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

W powyższym kodzie:

- Utworzono metodę główną, która konfiguruje transport SSE wskazujący na `http://localhost:8080`, gdzie będzie działał nasz serwer MCP.
- Utworzono klasę klienta, która przyjmuje transport jako parametr konstruktora.
- W metodzie `run` utworzono synchronicznego klienta MCP za pomocą transportu i zainicjowano połączenie.
- Użyto transportu SSE (Server-Sent Events), który jest odpowiedni do komunikacji HTTP z serwerami MCP opartymi na Java Spring Boot.

### -3- Listowanie funkcji serwera

Teraz mamy klienta, który może się połączyć, jeśli program zostanie uruchomiony. Jednak nie wylistowuje on jeszcze funkcji, więc zróbmy to teraz:

#### TypeScript

```typescript
// List prompts
const prompts = await client.listPrompts();

// List resources
const resources = await client.listResources();

// list tools
const tools = await client.listTools();
```

#### Python

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

Tutaj wylistowujemy dostępne zasoby za pomocą `list_resources()` oraz narzędzia za pomocą `list_tools` i je wypisujemy.

#### .NET

```dotnet
foreach (var tool in await client.ListToolsAsync())
{
    Console.WriteLine($"{tool.Name} ({tool.Description})");
}
```

Powyżej znajduje się przykład, jak można wylistować narzędzia na serwerze. Dla każdego narzędzia wypisujemy jego nazwę.

#### Java

```java
// List and demonstrate tools
ListToolsResult toolsList = client.listTools();
System.out.println("Available Tools = " + toolsList);

// You can also ping the server to verify connection
client.ping();
```

W powyższym kodzie:

- Wywołano `listTools()`, aby uzyskać wszystkie dostępne narzędzia z serwera MCP.
- Użyto `ping()`, aby zweryfikować, czy połączenie z serwerem działa.
- Obiekt `ListToolsResult` zawiera informacje o wszystkich narzędziach, w tym ich nazwach, opisach i schematach wejściowych.

Świetnie, teraz mamy wszystkie funkcje. Pytanie brzmi, kiedy ich używamy? Ten klient jest dość prosty, w tym sensie, że musimy jawnie wywoływać funkcje, kiedy ich potrzebujemy. W następnym rozdziale stworzymy bardziej zaawansowanego klienta, który będzie miał dostęp do własnego dużego modelu językowego (LLM). Na razie jednak zobaczmy, jak możemy wywoływać funkcje na serwerze:

### -4- Wywoływanie funkcji

Aby wywołać funkcje, musimy upewnić się, że podajemy poprawne argumenty, a w niektórych przypadkach nazwę tego, co chcemy wywołać.

#### TypeScript

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

W powyższym kodzie:

- Odczytujemy zasób, wywołując `readResource()` i podając `uri`. Oto jak to wygląda po stronie serwera:

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

    Nasza wartość `uri` `file://example.txt` odpowiada `file://{name}` na serwerze. `example.txt` zostanie przypisane do `name`.

- Wywołujemy narzędzie, podając jego `name` i `arguments` w następujący sposób:

    ```typescript
    const result = await client.callTool({
        name: "example-tool",
        arguments: {
            arg1: "value"
        }
    });
    ```

- Pobieramy podpowiedź, wywołując `getPrompt()` z `name` i `arguments`. Kod serwera wygląda następująco:

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

    A Twój kod klienta wygląda następująco, aby dopasować się do tego, co zadeklarowano na serwerze:

    ```typescript
    const promptResult = await client.getPrompt({
        name: "review-code",
        arguments: {
            code: "console.log(\"Hello world\")"
        }
    })
    ```

#### Python

```python
# Read a resource
print("READING RESOURCE")
content, mime_type = await session.read_resource("greeting://hello")

# Call a tool
print("CALL TOOL")
result = await session.call_tool("add", arguments={"a": 1, "b": 7})
print(result.content)
```

W powyższym kodzie:

- Wywołano zasób o nazwie `greeting` za pomocą `read_resource`.
- Wywołano narzędzie o nazwie `add` za pomocą `call_tool`.

#### .NET

1. Dodajmy kod do wywołania narzędzia:

  ```csharp
  var result = await mcpClient.CallToolAsync(
      "Add",
      new Dictionary<string, object?>() { ["a"] = 1, ["b"] = 3  },
      cancellationToken:CancellationToken.None);
  ```

1. Aby wydrukować wynik, oto kod obsługujący to:

  ```csharp
  Console.WriteLine(result.Content.First(c => c.Type == "text").Text);
  // Sum 4
  ```

#### Java

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

W powyższym kodzie:

- Wywołano wiele narzędzi kalkulatora za pomocą metody `callTool()` z obiektami `CallToolRequest`.
- Każde wywołanie narzędzia określa nazwę narzędzia i `Map` argumentów wymaganych przez to narzędzie.
- Narzędzia serwera oczekują określonych nazw parametrów (np. "a", "b" dla operacji matematycznych).
- Wyniki są zwracane jako obiekty `CallToolResult`, zawierające odpowiedź z serwera.

### -5- Uruchamianie klienta

Aby uruchomić klienta, wpisz następujące polecenie w terminalu:

#### TypeScript

Dodaj następujący wpis do sekcji "scripts" w pliku *package.json*:

```json
"client": "tsx && node build/client.js"
```

```sh
npm run client
```

#### Python

Uruchom klienta za pomocą następującego polecenia:

```sh
python client.py
```

#### .NET

```sh
dotnet run
```

#### Java

Najpierw upewnij się, że Twój serwer MCP działa na `http://localhost:8080`. Następnie uruchom klienta:

```bash
# Build you project
./mvnw clean compile

# Run the client
./mvnw exec:java -Dexec.mainClass="com.microsoft.mcp.sample.client.SDKClient"
```

Alternatywnie możesz uruchomić kompletny projekt klienta znajdujący się w folderze rozwiązania `03-GettingStarted\02-client\solution\java`:

```bash
# Navigate to the solution directory
cd 03-GettingStarted/02-client/solution/java

# Build and run the JAR
./mvnw clean package
java -jar target/calculator-client-0.0.1-SNAPSHOT.jar
```

## Zadanie

W tym zadaniu wykorzystasz zdobytą wiedzę, aby stworzyć własnego klienta.

Oto serwer, którego możesz użyć i który musisz wywołać za pomocą swojego kodu klienta. Spróbuj dodać więcej funkcji do serwera, aby uczynić go bardziej interesującym.

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

Zobacz ten projekt, aby dowiedzieć się, jak [dodawać podpowiedzi i zasoby](https://github.com/modelcontextprotocol/csharp-sdk/blob/main/samples/EverythingServer/Program.cs).

Sprawdź również ten link, aby dowiedzieć się, jak wywoływać [podpowiedzi i zasoby](https://github.com/modelcontextprotocol/csharp-sdk/blob/main/src/ModelContextProtocol/Client/).

## Rozwiązanie

Folder **solution** zawiera kompletne, gotowe do uruchomienia implementacje klientów, które demonstrują wszystkie omawiane w tym samouczku koncepcje. Każde rozwiązanie zawiera zarówno kod klienta, jak i serwera, zorganizowane w oddzielne, samodzielne projekty.

### 📁 Struktura rozwiązania

Katalog rozwiązania jest zorganizowany według języków programowania:

```text
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

### 🚀 Co zawiera każde rozwiązanie

Każde rozwiązanie specyficzne dla języka oferuje:

- **Kompletną implementację klienta** z wszystkimi funkcjami opisanymi w samouczku.
- **Działającą strukturę projektu** z odpowiednimi zależnościami i konfiguracją.
- **Skrypty budowania i uruchamiania** dla łatwej konfiguracji i wykonania.
- **Szczegółowy plik README** z instrukcjami specyficznymi dla języka.
- **Przykłady obsługi błędów** i przetwarzania wyników.

### 📖 Korzystanie z rozwiązań

1. **Przejdź do folderu preferowanego języka**:

   ```bash
   cd solution/typescript/    # For TypeScript
   cd solution/java/          # For Java
   cd solution/python/        # For Python
   cd solution/dotnet/        # For .NET
   ```

2. **Postępuj zgodnie z instrukcjami README** w każdym folderze, aby:
   - Zainstalować zależności.
   - Zbudować projekt.
   - Uruchomić klienta.

3. **Przykładowy wynik**, który powinieneś zobaczyć:

   ```text
   Prompt: Please review this code: console.log("hello");
   Resource template: file
   Tool result: { content: [ { type: 'text', text: '9' } ] }
   ```

Aby uzyskać pełną dokumentację i instrukcje krok po kroku, zobacz: **[📖 Dokumentacja rozwiązania](./solution/README.md)**

## 🎯 Kompletny przykład

Udostępniliśmy kompletne, działające implementacje klientów dla wszystkich języków programowania omawianych w tym samouczku. Przykłady te demonstrują pełną funkcjonalność opisaną powyżej i mogą być używane jako implementacje referencyjne lub punkty wyjścia do własnych projektów.

### Dostępne kompletne przykłady

| Język | Plik | Opis |
|-------|------|------|
| **Java** | [`client_example_java.java`](../../../../03-GettingStarted/02-client/client_example_java.java) | Kompletny klient Java korzystający z transportu SSE z kompleksową obsługą błędów |
| **C#** | [`client_example_csharp.cs`](../../../../03-GettingStarted/02-client/client_example_csharp.cs) | Kompletny klient C# korzystający z transportu stdio z automatycznym uruchamianiem serwera |
| **TypeScript** | [`client_example_typescript.ts`](../../../../03-GettingStarted/02-client/client_example_typescript.ts) | Kompletny klient TypeScript z pełnym wsparciem protokołu MCP |
| **Python** | [`client_example_python.py`](../../../../03-GettingStarted/02-client/client_example_python.py) | Kompletny klient Python korzystający z wzorców async/await |

Każdy kompletny przykład zawiera:

- ✅ **Nawiązywanie połączenia** i obsługę błędów.
- ✅ **Odkrywanie serwera** (narzędzia, zasoby, podpowiedzi, jeśli dotyczy).
- ✅ **Operacje kalkulatora** (dodawanie, odejmowanie, mnożenie, dzielenie, pomoc).
- ✅ **Przetwarzanie wyników** i formatowane wyjście.
- ✅ **Kompleksową obsługę błędów**.
- ✅ **Czysty, udokumentowany kod** z komentarzami krok po kroku.

### Rozpoczęcie pracy z kompletnymi przykładami

1. **Wybierz preferowany język** z powyższej tabeli.
2. **Przejrzyj plik z kompletnym przykładem**, aby zrozumieć pełną implementację.
3. **Uruchom przykład**, postępując zgodnie z instrukcjami w [`complete_examples.md`](./complete_examples.md).
4. **Zmodyfikuj i rozbuduj** przykład do własnych potrzeb.

Aby uzyskać szczegółową dokumentację dotyczącą uruchamiania i dostosowywania tych przykładów, zobacz: **[📖 Dokumentacja kompletnych przykładów](./complete_examples.md)**

### 💡 Rozwiązanie vs. Kompletny przykład

| **Folder rozwiązania** | **Kompletny przykład** |
|-------------------------|------------------------|
| Pełna struktura projektu z plikami budowania | Implementacje w jednym pliku |
| Gotowe do uruchomienia z zależnościami | Skoncentrowane przykłady kodu |
| Konfiguracja przypominająca produkcyjną | Edukacyjne odniesienie |
| Narzędzia specyficzne dla języka | Porównanie między językami |
Oba podejścia są wartościowe - używaj **folderu rozwiązania** dla kompletnych projektów oraz **kompletnych przykładów** do nauki i jako punktu odniesienia.

## Kluczowe informacje

Kluczowe informacje z tego rozdziału dotyczące klientów to:

- Mogą być używane zarówno do odkrywania, jak i wywoływania funkcji na serwerze.
- Mogą uruchamiać serwer podczas swojego startu (jak w tym rozdziale), ale klienci mogą również łączyć się z już działającymi serwerami.
- Są świetnym sposobem na testowanie możliwości serwera, obok alternatyw takich jak Inspektor, opisany w poprzednim rozdziale.

## Dodatkowe zasoby

- [Budowanie klientów w MCP](https://modelcontextprotocol.io/quickstart/client)

## Przykłady

- [Kalkulator w Javie](../samples/java/calculator/README.md)
- [Kalkulator w .Net](../../../../03-GettingStarted/samples/csharp)
- [Kalkulator w JavaScript](../samples/javascript/README.md)
- [Kalkulator w TypeScript](../samples/typescript/README.md)
- [Kalkulator w Pythonie](../../../../03-GettingStarted/samples/python)

## Co dalej

- Następny: [Tworzenie klienta z LLM](../03-llm-client/README.md)

**Zastrzeżenie**:  
Ten dokument został przetłumaczony za pomocą usługi tłumaczenia AI [Co-op Translator](https://github.com/Azure/co-op-translator). Chociaż dokładamy wszelkich starań, aby zapewnić poprawność tłumaczenia, prosimy pamiętać, że automatyczne tłumaczenia mogą zawierać błędy lub nieścisłości. Oryginalny dokument w jego języku źródłowym powinien być uznawany za wiarygodne źródło. W przypadku informacji o kluczowym znaczeniu zaleca się skorzystanie z profesjonalnego tłumaczenia przez człowieka. Nie ponosimy odpowiedzialności za jakiekolwiek nieporozumienia lub błędne interpretacje wynikające z użycia tego tłumaczenia.