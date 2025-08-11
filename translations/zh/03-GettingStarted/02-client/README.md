<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "ccdccbeb0247199f00a61a2fcd9e6ff8",
  "translation_date": "2025-08-11T09:42:31+00:00",
  "source_file": "03-GettingStarted/02-client/README.md",
  "language_code": "zh"
}
-->
# 创建客户端

客户端是与 MCP 服务器直接通信以请求资源、工具和提示的自定义应用程序或脚本。与使用提供图形界面的检查工具不同，编写自己的客户端可以实现程序化和自动化的交互。这使得开发者能够将 MCP 的功能集成到自己的工作流中，自动化任务，并根据特定需求构建定制化解决方案。

## 概述

本课程介绍了 Model Context Protocol (MCP) 生态系统中的客户端概念。您将学习如何编写自己的客户端并将其连接到 MCP 服务器。

## 学习目标

完成本课程后，您将能够：

- 理解客户端的功能。
- 编写自己的客户端。
- 连接并测试客户端与 MCP 服务器的交互，以确保服务器正常运行。

## 编写客户端需要做什么？

要编写一个客户端，您需要完成以下步骤：

- **导入正确的库**。您将使用之前相同的库，但需要不同的构造。
- **实例化一个客户端**。这包括创建一个客户端实例并将其连接到选定的传输方法。
- **决定列出哪些资源**。您的 MCP 服务器提供资源、工具和提示，您需要决定列出哪些内容。
- **将客户端集成到主机应用程序中**。一旦了解了服务器的功能，您需要将其集成到主机应用程序中，以便用户输入提示或其他命令时，能够调用相应的服务器功能。

现在我们已经了解了高层次的操作步骤，接下来让我们看一个示例。

### 示例客户端

以下是一个示例客户端：

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

在上述代码中，我们：

- 导入了库。
- 创建了一个客户端实例，并使用 stdio 作为传输方式进行连接。
- 列出了提示、资源和工具，并调用了它们。

这就是一个能够与 MCP 服务器通信的客户端。

接下来，我们将在练习部分逐段解析代码并解释其作用。

## 练习：编写客户端

如上所述，我们将逐步解释代码，您也可以边学边写代码。

### -1- 导入库

首先导入我们需要的库。我们需要引用客户端和选定的传输协议 stdio。stdio 是一种适用于本地运行的协议。SSE 是另一种传输协议，我们将在后续章节中介绍，但目前我们继续使用 stdio。

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

对于 Java，您将创建一个客户端，该客户端连接到之前练习中的 MCP 服务器。使用 [Getting Started with MCP Server](../../../../03-GettingStarted/01-first-server/solution/java) 中的 Java Spring Boot 项目结构，在 `src/main/java/com/microsoft/mcp/sample/client/` 文件夹中创建一个名为 `SDKClient` 的 Java 类，并添加以下导入：

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

#### Rust

您需要在 `Cargo.toml` 文件中添加以下依赖项。

```toml
[package]
name = "calculator-client"
version = "0.1.0"
edition = "2024"

[dependencies]
rmcp = { version = "0.3.0", features = ["client", "transport-child-process"] }
serde_json = "1.0.141"
tokio = { version = "1.46.1", features = ["rt-multi-thread"] }
```

然后，您可以在客户端代码中导入必要的库。

```rust
use rmcp::{
    RmcpError,
    model::CallToolRequestParam,
    service::ServiceExt,
    transport::{ConfigureCommandExt, TokioChildProcess},
};
use tokio::process::Command;
```

接下来，我们进行实例化。

### -2- 实例化客户端和传输

我们需要创建传输实例以及客户端实例：

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

在上述代码中，我们：

- 创建了一个 stdio 传输实例。注意它如何指定命令和参数以找到并启动服务器，这是我们在创建客户端时需要做的。

    ```typescript
    const transport = new StdioClientTransport({
        command: "node",
        args: ["server.js"]
    });
    ```

- 通过指定名称和版本实例化了一个客户端。

    ```typescript
    const client = new Client(
    {
        name: "example-client",
        version: "1.0.0"
    });
    ```

- 将客户端连接到选定的传输方式。

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

在上述代码中，我们：

- 导入了所需的库。
- 实例化了一个服务器参数对象，我们将使用它运行服务器，以便能够通过客户端连接到服务器。
- 定义了一个 `run` 方法，该方法调用 `stdio_client` 来启动客户端会话。
- 创建了一个入口点，在其中通过 `asyncio.run` 提供 `run` 方法。

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

在上述代码中，我们：

- 导入了所需的库。
- 创建了一个 stdio 传输，并创建了一个客户端 `mcpClient`。后者将用于列出和调用 MCP 服务器上的功能。

注意，在 "Arguments" 中，您可以指向 *.csproj* 文件或可执行文件。

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

在上述代码中，我们：

- 创建了一个主方法，该方法设置了一个 SSE 传输，指向 MCP 服务器运行的 `http://localhost:8080`。
- 创建了一个客户端类，该类将传输作为构造函数参数。
- 在 `run` 方法中，我们使用传输创建了一个同步 MCP 客户端并初始化了连接。
- 使用了适合基于 HTTP 的 Java Spring Boot MCP 服务器通信的 SSE（服务器发送事件）传输。

#### Rust

此 Rust 客户端假设服务器是同一目录下名为 "calculator-server" 的兄弟项目。以下代码将启动服务器并连接到它。

```rust
async fn main() -> Result<(), RmcpError> {
    // Assume the server is a sibling project named "calculator-server" in the same directory
    let server_dir = std::path::Path::new(env!("CARGO_MANIFEST_DIR"))
        .parent()
        .expect("failed to locate workspace root")
        .join("calculator-server");

    let client = ()
        .serve(
            TokioChildProcess::new(Command::new("cargo").configure(|cmd| {
                cmd.arg("run").current_dir(server_dir);
            }))
            .map_err(RmcpError::transport_creation::<TokioChildProcess>)?,
        )
        .await?;

    // TODO: Initialize

    // TODO: List tools

    // TODO: Call add tool with arguments = {"a": 3, "b": 2}

    client.cancel().await?;
    Ok(())
}
```

### -3- 列出服务器功能

现在，我们有了一个可以连接的客户端，但它实际上并没有列出功能，所以接下来让我们实现这一点：

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

在这里，我们列出了可用的资源 `list_resources()` 和工具 `list_tools`，并将它们打印出来。

#### .NET

```dotnet
foreach (var tool in await client.ListToolsAsync())
{
    Console.WriteLine($"{tool.Name} ({tool.Description})");
}
```

以上是一个列出服务器工具的示例。对于每个工具，我们打印出其名称。

#### Java

```java
// List and demonstrate tools
ListToolsResult toolsList = client.listTools();
System.out.println("Available Tools = " + toolsList);

// You can also ping the server to verify connection
client.ping();
```

在上述代码中，我们：

- 调用了 `listTools()` 以获取 MCP 服务器上的所有可用工具。
- 使用 `ping()` 验证与服务器的连接是否正常。
- `ListToolsResult` 包含所有工具的信息，包括它们的名称、描述和输入模式。

很好，现在我们已经捕获了所有功能。接下来的问题是何时使用它们？这个客户端相对简单，需要显式调用功能。在下一章中，我们将创建一个更高级的客户端，它可以访问自己的大型语言模型（LLM）。不过现在，让我们看看如何调用服务器上的功能：

#### Rust

在主函数中，初始化客户端后，我们可以初始化服务器并列出其一些功能。

```rust
// Initialize
let server_info = client.peer_info();
println!("Server info: {:?}", server_info);

// List tools
let tools = client.list_tools(Default::default()).await?;
println!("Available tools: {:?}", tools);
```

### -4- 调用功能

要调用功能，我们需要确保指定正确的参数，有时还需要指定要调用的名称。

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

在上述代码中，我们：

- 读取了一个资源，通过调用 `readResource()` 并指定 `uri`。以下是服务器端的代码：

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

    我们的 `uri` 值 `file://example.txt` 与服务器上的 `file://{name}` 匹配。`example.txt` 将映射到 `name`。

- 调用了一个工具，通过指定其 `name` 和 `arguments` 来调用：

    ```typescript
    const result = await client.callTool({
        name: "example-tool",
        arguments: {
            arg1: "value"
        }
    });
    ```

- 获取了一个提示，通过调用 `getPrompt()` 并提供 `name` 和 `arguments`。服务器代码如下：

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

    因此，匹配服务器声明的客户端代码如下：

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

在上述代码中，我们：

- 使用 `read_resource` 调用了一个名为 `greeting` 的资源。
- 使用 `call_tool` 调用了一个名为 `add` 的工具。

#### .NET

1. 添加一些代码以调用工具：

  ```csharp
  var result = await mcpClient.CallToolAsync(
      "Add",
      new Dictionary<string, object?>() { ["a"] = 1, ["b"] = 3  },
      cancellationToken:CancellationToken.None);
  ```

1. 打印结果的代码如下：

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

在上述代码中，我们：

- 使用 `callTool()` 方法和 `CallToolRequest` 对象调用了多个计算器工具。
- 每个工具调用都指定了工具名称和工具所需参数的 `Map`。
- 服务器工具期望特定的参数名称（如数学操作中的 "a" 和 "b"）。
- 结果以 `CallToolResult` 对象的形式返回，包含服务器的响应。

#### Rust

```rust
// Call add tool with arguments = {"a": 3, "b": 2}
let a = 3;
let b = 2;
let tool_result = client
    .call_tool(CallToolRequestParam {
        name: "add".into(),
        arguments: serde_json::json!({ "a": a, "b": b }).as_object().cloned(),
    })
    .await?;
println!("Result of {:?} + {:?}: {:?}", a, b, tool_result);
```

### -5- 运行客户端

要运行客户端，请在终端中输入以下命令：

#### TypeScript

在 *package.json* 的 "scripts" 部分添加以下条目：

```json
"client": "tsc && node build/client.js"
```

```sh
npm run client
```

#### Python

使用以下命令调用客户端：

```sh
python client.py
```

#### .NET

```sh
dotnet run
```

#### Java

首先，确保您的 MCP 服务器运行在 `http://localhost:8080`。然后运行客户端：

```bash
# Build you project
./mvnw clean compile

# Run the client
./mvnw exec:java -Dexec.mainClass="com.microsoft.mcp.sample.client.SDKClient"
```

或者，您可以运行解决方案文件夹 `03-GettingStarted\02-client\solution\java` 中提供的完整客户端项目：

```bash
# Navigate to the solution directory
cd 03-GettingStarted/02-client/solution/java

# Build and run the JAR
./mvnw clean package
java -jar target/calculator-client-0.0.1-SNAPSHOT.jar
```

#### Rust

```bash
cargo fmt
cargo run
```

## 作业

在本次作业中，您将使用所学内容创建自己的客户端。

以下是一个服务器，您需要通过客户端代码调用它，尝试为服务器添加更多功能，使其更有趣。

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

请参阅此项目以了解如何 [添加提示和资源](https://github.com/modelcontextprotocol/csharp-sdk/blob/main/samples/EverythingServer/Program.cs)。

同时，查看此链接以了解如何调用 [提示和资源](https://github.com/modelcontextprotocol/csharp-sdk/blob/main/src/ModelContextProtocol/Client/)。

### Rust

在 [上一节](../../../../03-GettingStarted/01-first-server) 中，您学习了如何使用 Rust 创建一个简单的 MCP 服务器。您可以继续基于此构建，或者查看此链接以获取更多基于 Rust 的 MCP 服务器示例：[MCP Server Examples](https://github.com/modelcontextprotocol/rust-sdk/tree/main/examples/servers)

## 解决方案

**解决方案文件夹**包含完整的、可运行的客户端实现，展示了本教程中涵盖的所有概念。每个解决方案包括客户端和服务器代码，组织为独立的项目。

### 📁 解决方案结构

解决方案目录按编程语言组织：

```text
solution/
├── typescript/          # TypeScript client with npm/Node.js setup
│   ├── package.json     # Dependencies and scripts
│   ├── tsconfig.json    # TypeScript configuration
│   └── src/             # Source code
├── java/                # Java Spring Boot client project
│   ├── pom.xml          # Maven configuration
│   ├── src/             # Java source files
│   └── mvnw             # Maven wrapper
├── python/              # Python client implementation
│   ├── client.py        # Main client code
│   ├── server.py        # Compatible server
│   └── README.md        # Python-specific instructions
├── dotnet/              # .NET client project
│   ├── dotnet.csproj    # Project configuration
│   ├── Program.cs       # Main client code
│   └── dotnet.sln       # Solution file
├── rust/                # Rust client implementation
|  ├── Cargo.lock        # Cargo lock file
|  ├── Cargo.toml        # Project configuration and dependencies
|  ├── src               # Source code
|  │   └── main.rs       # Main client code
└── server/              # Additional .NET server implementation
    ├── Program.cs       # Server code
    └── server.csproj    # Server project file
```

### 🚀 每个解决方案包含的内容

每个语言特定的解决方案提供：

- **完整的客户端实现**，包含教程中的所有功能
- **工作项目结构**，具有正确的依赖项和配置
- **构建和运行脚本**，便于设置和执行
- **详细的 README**，提供语言特定的说明
- **错误处理** 和结果处理示例

### 📖 使用解决方案

1. **导航到您选择的语言文件夹**：

   ```bash
   cd solution/typescript/    # For TypeScript
   cd solution/java/          # For Java
   cd solution/python/        # For Python
   cd solution/dotnet/        # For .NET
   ```

2. **按照每个文件夹中的 README 指南**：
   - 安装依赖项
   - 构建项目
   - 运行客户端

3. **您应该看到的示例输出**：

   ```text
   Prompt: Please review this code: console.log("hello");
   Resource template: file
   Tool result: { content: [ { type: 'text', text: '9' } ] }
   ```

有关完整文档和分步说明，请参阅：**[📖 解决方案文档](./solution/README.md)**

## 🎯 完整示例

我们提供了所有编程语言的完整、可运行的客户端实现。这些示例展示了上述功能的完整实现，可用作参考实现或您自己项目的起点。

### 可用的完整示例

| 语言       | 文件                              | 描述                                   |
|------------|-----------------------------------|----------------------------------------|
| **Java**   | [`client_example_java.java`](../../../../03-GettingStarted/02-client/client_example_java.java) | 使用 SSE 传输的完整 Java 客户端，包含全面的错误处理 |
| **C#**     | [`client_example_csharp.cs`](../../../../03-GettingStarted/02-client/client_example_csharp.cs) | 使用 stdio 传输的完整 C# 客户端，支持自动服务器启动 |
| **TypeScript** | [`client_example_typescript.ts`](../../../../03-GettingStarted/02-client/client_example_typescript.ts) | 完整的 TypeScript 客户端，支持 MCP 协议的所有功能 |
| **Python** | [`client_example_python.py`](../../../../03-GettingStarted/02-client/client_example_python.py) | 使用 async/await 模式的完整 Python 客户端 |
| **Rust**   | [`client_example_rust.rs`](../../../../03-GettingStarted/02-client/client_example_rust.rs) | 使用 Tokio 进行异步操作的完整 Rust 客户端 |
每个完整示例包括：

- ✅ **连接建立**和错误处理  
- ✅ **服务器发现**（工具、资源、提示等）  
- ✅ **计算器操作**（加、减、乘、除、帮助）  
- ✅ **结果处理**和格式化输出  
- ✅ **全面的错误处理**  
- ✅ **干净且有注释的代码**，包含逐步说明  

### 开始使用完整示例

1. **从上表中选择您偏好的语言**  
2. **查看完整示例文件**以了解完整实现  
3. **按照[`complete_examples.md`](./complete_examples.md)中的说明运行示例**  
4. **根据您的具体需求修改和扩展示例**  

有关运行和自定义这些示例的详细文档，请参阅：**[📖 完整示例文档](./complete_examples.md)**  

### 💡 解决方案与完整示例的区别

| **解决方案文件夹** | **完整示例** |
|--------------------|--------------------- |
| 包含构建文件的完整项目结构 | 单文件实现 |
| 带依赖项的即用型代码 | 专注于代码示例 |
| 类生产环境的设置 | 教学参考 |
| 特定语言的工具支持 | 跨语言比较 |

两种方法都很有价值——使用**解决方案文件夹**来完成项目，使用**完整示例**进行学习和参考。

## 关键要点

本章关于客户端的关键要点如下：

- 客户端既可以用于发现服务器功能，也可以调用服务器功能。  
- 客户端可以在自身启动时启动服务器（如本章所述），也可以连接到正在运行的服务器。  
- 客户端是测试服务器功能的绝佳方式，与上一章描述的Inspector等替代方案相比也非常有用。  

## 其他资源

- [在MCP中构建客户端](https://modelcontextprotocol.io/quickstart/client)  

## 示例

- [Java计算器](../samples/java/calculator/README.md)  
- [.Net计算器](../../../../03-GettingStarted/samples/csharp)  
- [JavaScript计算器](../samples/javascript/README.md)  
- [TypeScript计算器](../samples/typescript/README.md)  
- [Python计算器](../../../../03-GettingStarted/samples/python)  
- [Rust计算器](../../../../03-GettingStarted/samples/rust)  

## 接下来

- 下一步：[使用LLM创建客户端](../03-llm-client/README.md)  

**免责声明**：  
本文档使用AI翻译服务 [Co-op Translator](https://github.com/Azure/co-op-translator) 进行翻译。尽管我们努力确保翻译的准确性，但请注意，自动翻译可能包含错误或不准确之处。原始语言的文档应被视为权威来源。对于关键信息，建议使用专业人工翻译。我们不对因使用此翻译而产生的任何误解或误读承担责任。