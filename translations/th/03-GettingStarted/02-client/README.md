<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "8da8a0fd44d58fab5979d0f2914a1f37",
  "translation_date": "2025-07-17T09:02:24+00:00",
  "source_file": "03-GettingStarted/02-client/README.md",
  "language_code": "th"
}
-->
# การสร้างไคลเอนต์

ไคลเอนต์คือแอปพลิเคชันหรือสคริปต์ที่เขียนขึ้นเองเพื่อสื่อสารโดยตรงกับ MCP Server เพื่อร้องขอทรัพยากร เครื่องมือ และพรอมต์ ต่างจากการใช้เครื่องมือ inspector ที่มีอินเทอร์เฟซแบบกราฟิกสำหรับโต้ตอบกับเซิร์ฟเวอร์ การเขียนไคลเอนต์ของคุณเองช่วยให้สามารถโต้ตอบแบบโปรแกรมและอัตโนมัติได้ ซึ่งช่วยให้นักพัฒนาสามารถผนวกความสามารถของ MCP เข้ากับเวิร์กโฟลว์ของตนเอง อัตโนมัติงานต่าง ๆ และสร้างโซลูชันที่ปรับแต่งตามความต้องการเฉพาะได้

## ภาพรวม

บทเรียนนี้จะแนะนำแนวคิดของไคลเอนต์ในระบบนิเวศของ Model Context Protocol (MCP) คุณจะได้เรียนรู้วิธีเขียนไคลเอนต์ของตัวเองและเชื่อมต่อกับ MCP Server

## วัตถุประสงค์การเรียนรู้

เมื่อจบบทเรียนนี้ คุณจะสามารถ:

- เข้าใจว่าไคลเอนต์ทำอะไรได้บ้าง
- เขียนไคลเอนต์ของตัวเอง
- เชื่อมต่อและทดสอบไคลเอนต์กับ MCP Server เพื่อให้แน่ใจว่าเซิร์ฟเวอร์ทำงานตามที่คาดหวัง

## อะไรบ้างที่ต้องทำเมื่อต้องเขียนไคลเอนต์?

เมื่อต้องเขียนไคลเอนต์ คุณจะต้องทำดังนี้:

- **นำเข้าห้องสมุดที่ถูกต้อง** คุณจะใช้ห้องสมุดเดียวกับที่เคยใช้ก่อนหน้านี้ แต่ใช้โครงสร้างที่แตกต่างกัน
- **สร้างอินสแตนซ์ของไคลเอนต์** ซึ่งจะรวมถึงการสร้างอินสแตนซ์ไคลเอนต์และเชื่อมต่อกับวิธีการขนส่งที่เลือก
- **ตัดสินใจว่าจะลิสต์ทรัพยากรอะไรบ้าง** เซิร์ฟเวอร์ MCP ของคุณมีทรัพยากร เครื่องมือ และพรอมต์ คุณต้องเลือกว่าจะลิสต์อะไรบ้าง
- **ผนวกไคลเอนต์เข้ากับแอปโฮสต์** เมื่อคุณรู้ความสามารถของเซิร์ฟเวอร์แล้ว คุณต้องผนวกไคลเอนต์นี้เข้ากับแอปโฮสต์ เพื่อให้เมื่อผู้ใช้พิมพ์พรอมต์หรือคำสั่งอื่น ๆ ฟีเจอร์ที่เกี่ยวข้องของเซิร์ฟเวอร์จะถูกเรียกใช้งาน

เมื่อเราเข้าใจภาพรวมคร่าว ๆ แล้ว มาดูตัวอย่างกันต่อไป

### ตัวอย่างไคลเอนต์

มาดูตัวอย่างไคลเอนต์นี้กัน:

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

ในโค้ดข้างต้น เราได้:

- นำเข้าห้องสมุด
- สร้างอินสแตนซ์ของไคลเอนต์และเชื่อมต่อโดยใช้ stdio เป็นวิธีการขนส่ง
- ลิสต์พรอมต์ ทรัพยากร และเครื่องมือ แล้วเรียกใช้งานทั้งหมด

นี่คือไคลเอนต์ที่สามารถสื่อสารกับ MCP Server ได้

ในส่วนถัดไปของแบบฝึกหัด เราจะใช้เวลาทำความเข้าใจโค้ดแต่ละส่วนและอธิบายว่ามันทำงานอย่างไร

## แบบฝึกหัด: การเขียนไคลเอนต์

อย่างที่กล่าวไว้ข้างต้น ให้เราใช้เวลาทำความเข้าใจโค้ด และถ้าคุณต้องการก็สามารถเขียนโค้ดไปพร้อมกันได้

### -1- นำเข้าห้องสมุด

เราจะนำเข้าห้องสมุดที่ต้องใช้ โดยเราจะต้องอ้างอิงถึงไคลเอนต์และโปรโตคอลการขนส่งที่เลือกคือ stdio stdio เป็นโปรโตคอลสำหรับสิ่งที่รันบนเครื่องของคุณโดยตรง ส่วน SSE เป็นโปรโตคอลขนส่งอีกแบบที่จะแสดงในบทถัดไป แต่ตอนนี้เราจะใช้ stdio ต่อไป

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

สำหรับ Java คุณจะสร้างไคลเอนต์ที่เชื่อมต่อกับ MCP Server จากแบบฝึกหัดก่อนหน้า โดยใช้โครงสร้างโปรเจกต์ Java Spring Boot เดิมจาก [Getting Started with MCP Server](../../../../03-GettingStarted/01-first-server/solution/java) สร้างคลาส Java ใหม่ชื่อ `SDKClient` ในโฟลเดอร์ `src/main/java/com/microsoft/mcp/sample/client/` และเพิ่มการนำเข้าดังนี้:

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

ต่อไปมาดูการสร้างอินสแตนซ์กัน

### -2- การสร้างอินสแตนซ์ของไคลเอนต์และการขนส่ง

เราจะต้องสร้างอินสแตนซ์ของการขนส่งและไคลเอนต์:

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

ในโค้ดข้างต้น เราได้:

- สร้างอินสแตนซ์ stdio transport โดยระบุคำสั่งและอาร์กิวเมนต์สำหรับการค้นหาและเริ่มเซิร์ฟเวอร์ ซึ่งเป็นสิ่งที่เราต้องทำเมื่อต้องสร้างไคลเอนต์

    ```typescript
    const transport = new StdioClientTransport({
        command: "node",
        args: ["server.js"]
    });
    ```

- สร้างอินสแตนซ์ไคลเอนต์โดยกำหนดชื่อและเวอร์ชัน

    ```typescript
    const client = new Client(
    {
        name: "example-client",
        version: "1.0.0"
    });
    ```

- เชื่อมต่อไคลเอนต์กับวิธีการขนส่งที่เลือก

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

ในโค้ดข้างต้น เราได้:

- นำเข้าห้องสมุดที่จำเป็น
- สร้างอ็อบเจ็กต์พารามิเตอร์เซิร์ฟเวอร์เพื่อใช้รันเซิร์ฟเวอร์และเชื่อมต่อกับไคลเอนต์
- กำหนดเมธอด `run` ที่เรียก `stdio_client` เพื่อเริ่มเซสชันไคลเอนต์
- สร้างจุดเริ่มต้นโดยใช้ `asyncio.run` เพื่อเรียกเมธอด `run`

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

ในโค้ดข้างต้น เราได้:

- นำเข้าห้องสมุดที่จำเป็น
- สร้าง stdio transport และไคลเอนต์ `mcpClient` ซึ่งจะใช้สำหรับลิสต์และเรียกใช้งานฟีเจอร์บน MCP Server

หมายเหตุ ในส่วน "Arguments" คุณสามารถชี้ไปยังไฟล์ *.csproj* หรือไฟล์ executable ก็ได้

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

ในโค้ดข้างต้น เราได้:

- สร้างเมธอด main ที่ตั้งค่า SSE transport ชี้ไปยัง `http://localhost:8080` ซึ่งเป็นที่ที่ MCP Server ของเราจะรัน
- สร้างคลาสไคลเอนต์ที่รับ transport เป็นพารามิเตอร์ในคอนสตรัคเตอร์
- ในเมธอด `run` เราสร้าง MCP client แบบ synchronous โดยใช้ transport และเริ่มต้นการเชื่อมต่อ
- ใช้ SSE (Server-Sent Events) transport ซึ่งเหมาะสำหรับการสื่อสารผ่าน HTTP กับ MCP Server ที่ใช้ Java Spring Boot

### -3- การลิสต์ฟีเจอร์ของเซิร์ฟเวอร์

ตอนนี้เรามีไคลเอนต์ที่สามารถเชื่อมต่อได้เมื่อรันโปรแกรมแล้ว แต่ยังไม่ได้ลิสต์ฟีเจอร์ของเซิร์ฟเวอร์ ดังนั้นมาลิสต์ฟีเจอร์กัน:

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

ที่นี่เราลิสต์ทรัพยากรที่มีด้วย `list_resources()` และเครื่องมือด้วย `list_tools` แล้วพิมพ์ออกมา

### .NET

```dotnet
foreach (var tool in await client.ListToolsAsync())
{
    Console.WriteLine($"{tool.Name} ({tool.Description})");
}
```

ตัวอย่างข้างต้นแสดงวิธีลิสต์เครื่องมือบนเซิร์ฟเวอร์ และสำหรับแต่ละเครื่องมือเราจะพิมพ์ชื่อออกมา

### Java

```java
// List and demonstrate tools
ListToolsResult toolsList = client.listTools();
System.out.println("Available Tools = " + toolsList);

// You can also ping the server to verify connection
client.ping();
```

ในโค้ดข้างต้น เราได้:

- เรียก `listTools()` เพื่อดึงเครื่องมือทั้งหมดที่มีจาก MCP Server
- ใช้ `ping()` เพื่อตรวจสอบการเชื่อมต่อกับเซิร์ฟเวอร์
- `ListToolsResult` จะเก็บข้อมูลเกี่ยวกับเครื่องมือทั้งหมด รวมถึงชื่อ คำอธิบาย และสคีมาของอินพุต

ดีมาก ตอนนี้เราลิสต์ฟีเจอร์ทั้งหมดแล้ว คำถามคือเราจะใช้ฟีเจอร์เหล่านี้เมื่อไหร่? ไคลเอนต์นี้ค่อนข้างเรียบง่าย หมายความว่าเราต้องเรียกใช้ฟีเจอร์เหล่านี้อย่างชัดเจนเมื่อเราต้องการ ในบทถัดไปเราจะสร้างไคลเอนต์ที่ซับซ้อนขึ้นซึ่งมีโมเดลภาษาใหญ่ (LLM) ของตัวเอง แต่ตอนนี้มาดูวิธีเรียกใช้ฟีเจอร์บนเซิร์ฟเวอร์กัน:

### -4- การเรียกใช้ฟีเจอร์

เพื่อเรียกใช้ฟีเจอร์ เราต้องระบุอาร์กิวเมนต์ที่ถูกต้อง และในบางกรณีต้องระบุชื่อของสิ่งที่เราต้องการเรียกใช้ด้วย

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

ในโค้ดข้างต้น เราได้:

- อ่านทรัพยากรโดยเรียก `readResource()` พร้อมระบุ `uri` ซึ่งบนฝั่งเซิร์ฟเวอร์น่าจะเป็นแบบนี้:

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

    ค่า `uri` ของเรา `file://example.txt` ตรงกับ `file://{name}` บนเซิร์ฟเวอร์ โดย `example.txt` จะถูกแมปเป็น `name`

- เรียกใช้เครื่องมือโดยระบุ `name` และ `arguments` ดังนี้:

    ```typescript
    const result = await client.callTool({
        name: "example-tool",
        arguments: {
            arg1: "value"
        }
    });
    ```

- ดึงพรอมต์โดยเรียก `getPrompt()` พร้อม `name` และ `arguments` โค้ดฝั่งเซิร์ฟเวอร์เป็นแบบนี้:

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

    ดังนั้นโค้ดไคลเอนต์ของคุณจะเป็นแบบนี้เพื่อให้ตรงกับที่ประกาศบนเซิร์ฟเวอร์:

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

ในโค้ดข้างต้น เราได้:

- เรียกทรัพยากรชื่อ `greeting` โดยใช้ `read_resource`
- เรียกใช้เครื่องมือชื่อ `add` โดยใช้ `call_tool`

### .NET

1. เพิ่มโค้ดสำหรับเรียกใช้เครื่องมือ:

  ```csharp
  var result = await mcpClient.CallToolAsync(
      "Add",
      new Dictionary<string, object?>() { ["a"] = 1, ["b"] = 3  },
      cancellationToken:CancellationToken.None);
  ```

2. เพื่อพิมพ์ผลลัพธ์ นี่คือโค้ดสำหรับจัดการ:

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

ในโค้ดข้างต้น เราได้:

- เรียกใช้เครื่องมือเครื่องคิดเลขหลายตัวโดยใช้เมธอด `callTool()` กับอ็อบเจ็กต์ `CallToolRequest`
- แต่ละการเรียกเครื่องมือระบุชื่อเครื่องมือและ `Map` ของอาร์กิวเมนต์ที่เครื่องมือต้องการ
- เครื่องมือบนเซิร์ฟเวอร์คาดหวังพารามิเตอร์เฉพาะ (เช่น "a", "b" สำหรับการคำนวณทางคณิตศาสตร์)
- ผลลัพธ์จะถูกส่งกลับเป็นอ็อบเจ็กต์ `CallToolResult` ที่เก็บการตอบกลับจากเซิร์ฟเวอร์

### -5- การรันไคลเอนต์

เพื่อรันไคลเอนต์ ให้พิมพ์คำสั่งต่อไปนี้ในเทอร์มินัล:

### TypeScript

เพิ่มรายการนี้ในส่วน "scripts" ของ *package.json*:

```json
"client": "tsx && node build/client.js"
```

```sh
npm run client
```

### Python

เรียกไคลเอนต์ด้วยคำสั่งนี้:

```sh
python client.py
```

### .NET

```sh
dotnet run
```

### Java

ก่อนอื่นให้แน่ใจว่า MCP Server ของคุณกำลังรันที่ `http://localhost:8080` จากนั้นรันไคลเอนต์:

```bash
# Build you project
./mvnw clean compile

# Run the client
./mvnw exec:java -Dexec.mainClass="com.microsoft.mcp.sample.client.SDKClient"
```

หรือคุณสามารถรันโปรเจกต์ไคลเอนต์ที่สมบูรณ์ในโฟลเดอร์โซลูชัน `03-GettingStarted\02-client\solution\java` ได้:

```bash
# Navigate to the solution directory
cd 03-GettingStarted/02-client/solution/java

# Build and run the JAR
./mvnw clean package
java -jar target/calculator-client-0.0.1-SNAPSHOT.jar
```

## การบ้าน

ในการบ้านนี้ คุณจะใช้สิ่งที่เรียนรู้ในการสร้างไคลเอนต์ แต่ให้สร้างไคลเอนต์ของตัวเอง

นี่คือเซิร์ฟเวอร์ที่คุณสามารถใช้ได้ โดยคุณต้องเรียกผ่านโค้ดไคลเอนต์ของคุณ ลองเพิ่มฟีเจอร์ให้เซิร์ฟเวอร์เพื่อทำให้มันน่าสนใจขึ้น

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

ดูโปรเจกต์นี้เพื่อดูวิธี [เพิ่มพรอมต์และทรัพยากร](https://github.com/modelcontextprotocol/csharp-sdk/blob/main/samples/EverythingServer/Program.cs)

นอกจากนี้ ตรวจสอบลิงก์นี้สำหรับวิธีการเรียกใช้ [พรอมต์และทรัพยากร](https://github.com/modelcontextprotocol/csharp-sdk/blob/main/src/ModelContextProtocol/Client/)

## โซลูชัน

**โฟลเดอร์โซลูชัน** ประกอบด้วยตัวอย่างไคลเอนต์ที่สมบูรณ์และพร้อมรัน ซึ่งแสดงแนวคิดทั้งหมดที่ครอบคลุมในบทเรียนนี้ โซลูชันแต่ละชุดประกอบด้วยโค้ดไคลเอนต์และเซิร์ฟเวอร์ที่จัดแยกเป็นโปรเจกต์แยกกันอย่างครบถ้วน

### 📁 โครงสร้างโซลูชัน

ไดเรกทอรีโซลูชันจัดเรียงตามภาษาโปรแกรม:

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

### 🚀 สิ่งที่แต่ละโซลูชันมีให้

โซลูชันสำหรับแต่ละภาษาจะมี:

- **การใช้งานไคลเอนต์ที่สมบูรณ์** พร้อมฟีเจอร์ทั้งหมดจากบทเรียน
- **โครงสร้างโปรเจกต์ที่ใช้งานได้จริง** พร้อมการตั้งค่าและการจัดการ dependencies ที่เหมาะสม
- **สคริปต์สำหรับ build และ run** เพื่อความสะดวกในการตั้งค่าและใช้งาน
- **README รายละเอียด** พร้อมคำแนะนำเฉพาะสำหรับแต่ละภาษา
- **ตัวอย่างการจัดการข้อผิดพลาด** และการประมวลผลผลลัพธ์

### 📖 การใช้งานโซลูชัน

1. **ไปยังโฟลเดอร์ภาษาที่คุณต้องการ**:
   ```bash
   cd solution/typescript/    # For TypeScript
   cd solution/java/          # For Java
   cd solution/python/        # For Python
   cd solution/dotnet/        # For .NET
   ```

2. **ทำตามคำแนะนำใน README** ในแต่ละโฟลเดอร์สำหรับ:
   - การติดตั้ง dependencies
   - การ build โปรเจกต์
   - การรันไคลเอนต์

3. **ตัวอย่างผลลัพธ์ที่คุณควรเห็น**:
   ```text
   Prompt: Please review this code: console.log("hello");
   Resource template: file
   Tool result: { content: [ { type: 'text', text: '9' } ] }
   ```

สำหรับเอกสารและคำแนะนำทีละขั้นตอนเพิ่มเติม ดูได้ที่: **[📖 เอกสารโซลูชัน](./solution/README.md)**

## 🎯 ตัวอย่างสมบูรณ์

เราได้จัดเตรียมตัวอย่างไคลเอนต์ที่สมบูรณ์และใช้งานได้จริงสำหรับทุกภาษาที่ครอบคลุมในบทเรียนนี้ ตัวอย่างเหล่านี้แสดงฟังก์ชันการทำงานทั้งหมดที่อธิบายไว้ข้างต้น และสามารถใช้เป็นตัวอย่างอ้างอิงหรือจุดเริ่มต้นสำหรับโปรเจกต์ของคุณเอง

### ตัวอย่างสมบูรณ์ที่มีให้

| ภาษา | ไฟล์ | คำอธิบาย |
|----------|------|-------------|
| **Java** | [`client_example_java.java`](../../../../03-GettingStarted/02-client/client_example_java.java) | ไคลเอนต์ Java สมบูรณ์ที่ใช้ SSE transport พร้อมการจัดการข้อผิดพลาดครบถ้วน |
| **C#** | [`client_example_csharp.cs`](../../../../03-GettingStarted/02-client/client_example_csharp.cs) | ไคลเอนต์ C# สมบูรณ์ที่ใช้ stdio transport พร้อมการสตาร์ทเซิร์ฟเวอร์อัตโนมัติ |
| **TypeScript** | [`client_example_typescript.ts`](../../../../03-GettingStarted/02-client/client_example_typescript.ts) | ไคลเอนต์ TypeScript สมบูรณ์ที่รองรับโปรโตคอล MCP เต็มรูปแบบ |
| **Python** | [`client_example_python.py`](../../../../03-GettingStarted/02-client/client_example_python.py) | ไคลเอนต์ Python สมบูรณ์ที่ใช้รูปแบบ async/await |

ตัวอย่างสมบูรณ์แต่ละตัวประกอบด้วย:

- ✅ **การเชื่อมต่อและการจัดการข้อผิดพลาด**
- ✅ **การค้นหาเซิร์ฟเวอร์** (เครื่องมือ ทรัพยากร พรอมต์ ตามที่มี)
- ✅ **การทำงานของเครื่องคิดเลข** (บวก ลบ คูณ หาร ช่วยเหลือ)
- ✅ **การประมวลผลผลลัพธ์** และการแสดงผลอย่างมีรูปแบบ
- ✅ **การจัดการข้อผิดพลาดอย่างครบถ้วน**
- ✅ **โค้ดที่สะอาดและมีคอมเมนต์อธิบายทีละขั้นตอน**

### เริ่มต้นกับตัวอย่างสมบูรณ์

1. **เลือกภาษาที่คุณต้องการ** จากตารางข้างต้น
2. **ศึกษาตัวอย่างไฟล์สมบูรณ์** เพื่อเข้าใจการใช้งานทั้งหมด
3. **รันตัวอย่าง** ตามคำแนะนำใน [`complete_examples.md`](./complete_examples.md)
4. **แก้ไขและขยาย** ตัวอย่างให้เหมาะกับกรณีใช้งานของคุณ

สำหรับเอกสารรายละเอียดเกี่ยวกับการรันและปรับแต่งตัวอย่างเหล่านี้ ดูได้ที่: **[📖 เอกสารตัวอย่างสมบูรณ์](./complete_examples.md)**

### 💡 โซลูชัน vs ตัวอย่างสมบูรณ์

| **โฟลเด
ทั้งสองวิธีมีคุณค่า - ใช้ **solution folder** สำหรับโปรเจกต์ที่สมบูรณ์ และ **complete examples** สำหรับการเรียนรู้และอ้างอิง  
## ข้อสรุปสำคัญ

ข้อสรุปสำคัญของบทนี้เกี่ยวกับ clients มีดังนี้:

- สามารถใช้เพื่อค้นหาและเรียกใช้ฟีเจอร์ต่างๆ บนเซิร์ฟเวอร์ได้  
- สามารถเริ่มเซิร์ฟเวอร์ในขณะที่ตัว client เริ่มทำงาน (เหมือนในบทนี้) แต่ client ก็สามารถเชื่อมต่อกับเซิร์ฟเวอร์ที่กำลังทำงานอยู่ได้เช่นกัน  
- เป็นวิธีที่ดีในการทดสอบความสามารถของเซิร์ฟเวอร์ควบคู่ไปกับทางเลือกอื่นๆ เช่น Inspector ตามที่อธิบายในบทก่อนหน้า  

## แหล่งข้อมูลเพิ่มเติม

- [Building clients in MCP](https://modelcontextprotocol.io/quickstart/client)

## ตัวอย่าง

- [Java Calculator](../samples/java/calculator/README.md)  
- [.Net Calculator](../../../../03-GettingStarted/samples/csharp)  
- [JavaScript Calculator](../samples/javascript/README.md)  
- [TypeScript Calculator](../samples/typescript/README.md)  
- [Python Calculator](../../../../03-GettingStarted/samples/python)  

## ต่อไปคืออะไร

- ต่อไป: [Creating a client with an LLM](../03-llm-client/README.md)

**ข้อจำกัดความรับผิดชอบ**:  
เอกสารนี้ได้รับการแปลโดยใช้บริการแปลภาษาอัตโนมัติ [Co-op Translator](https://github.com/Azure/co-op-translator) แม้เราจะพยายามให้ความถูกต้องสูงสุด แต่โปรดทราบว่าการแปลอัตโนมัติอาจมีข้อผิดพลาดหรือความไม่ถูกต้อง เอกสารต้นฉบับในภาษาต้นทางถือเป็นแหล่งข้อมูลที่เชื่อถือได้ สำหรับข้อมูลที่สำคัญ ขอแนะนำให้ใช้บริการแปลโดยผู้เชี่ยวชาญมนุษย์ เราไม่รับผิดชอบต่อความเข้าใจผิดหรือการตีความผิดใด ๆ ที่เกิดจากการใช้การแปลนี้