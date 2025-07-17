<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "8da8a0fd44d58fab5979d0f2914a1f37",
  "translation_date": "2025-07-17T09:51:47+00:00",
  "source_file": "03-GettingStarted/02-client/README.md",
  "language_code": "bn"
}
-->
# ক্লায়েন্ট তৈরি করা

ক্লায়েন্ট হলো কাস্টম অ্যাপ্লিকেশন বা স্ক্রিপ্ট যা সরাসরি MCP সার্ভারের সাথে যোগাযোগ করে রিসোর্স, টুলস এবং প্রম্পট অনুরোধ করে। ইন্সপেক্টর টুল ব্যবহারের থেকে আলাদা, যা সার্ভারের সাথে ইন্টারঅ্যাকশনের জন্য গ্রাফিক্যাল ইন্টারফেস দেয়, নিজের ক্লায়েন্ট লেখা প্রোগ্রাম্যাটিক এবং স্বয়ংক্রিয় ইন্টারঅ্যাকশন সম্ভব করে। এটি ডেভেলপারদের MCP এর ক্ষমতাগুলো তাদের নিজস্ব ওয়ার্কফ্লোতে একত্রিত করতে, কাজগুলো স্বয়ংক্রিয় করতে এবং নির্দিষ্ট চাহিদা অনুযায়ী কাস্টম সমাধান তৈরি করতে সাহায্য করে।

## ওভারভিউ

এই পাঠে MCP ইকোসিস্টেমের মধ্যে ক্লায়েন্টের ধারণা পরিচয় করানো হবে। আপনি শিখবেন কিভাবে নিজের ক্লায়েন্ট লিখতে হয় এবং সেটি MCP সার্ভারের সাথে সংযোগ স্থাপন করতে হয়।

## শেখার উদ্দেশ্য

এই পাঠ শেষ করার পর আপনি সক্ষম হবেন:

- বুঝতে ক্লায়েন্ট কী করতে পারে।
- নিজের ক্লায়েন্ট লিখতে।
- ক্লায়েন্টকে MCP সার্ভারের সাথে সংযোগ করে পরীক্ষা করতে যাতে নিশ্চিত হওয়া যায় সার্ভার প্রত্যাশিতভাবে কাজ করছে।

## ক্লায়েন্ট লেখার জন্য কী কী লাগে?

ক্লায়েন্ট লেখার জন্য আপনাকে নিম্নলিখিত কাজগুলো করতে হবে:

- **সঠিক লাইব্রেরি ইমপোর্ট করুন**। আপনি আগের মতো একই লাইব্রেরি ব্যবহার করবেন, শুধু বিভিন্ন কনস্ট্রাক্ট ব্যবহার করবেন।
- **ক্লায়েন্ট ইনস্ট্যান্স তৈরি করুন**। এর মধ্যে ক্লায়েন্টের একটি ইনস্ট্যান্স তৈরি করা এবং নির্বাচিত ট্রান্সপোর্ট পদ্ধতির সাথে সংযোগ স্থাপন করা থাকবে।
- **কোন রিসোর্স তালিকাভুক্ত করবেন তা নির্ধারণ করুন**। আপনার MCP সার্ভারে রিসোর্স, টুলস এবং প্রম্পট থাকে, আপনাকে সিদ্ধান্ত নিতে হবে কোনগুলো তালিকাভুক্ত করবেন।
- **ক্লায়েন্টকে হোস্ট অ্যাপ্লিকেশনের সাথে একত্রিত করুন**। সার্ভারের ক্ষমতাগুলো জানার পর আপনাকে এটি আপনার হোস্ট অ্যাপ্লিকেশনের সাথে একত্রিত করতে হবে যাতে ব্যবহারকারী যখন প্রম্পট বা অন্য কোনো কমান্ড টাইপ করে, সংশ্লিষ্ট সার্ভার ফিচারটি চালু হয়।

এখন যেহেতু আমরা উচ্চ স্তরে বুঝে গেছি কী করতে হবে, চলুন পরবর্তী উদাহরণ দেখি।

### একটি উদাহরণ ক্লায়েন্ট

এই উদাহরণ ক্লায়েন্টটি দেখি:

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

উপরের কোডে আমরা:

- লাইব্রেরি ইমপোর্ট করেছি
- একটি ক্লায়েন্ট ইনস্ট্যান্স তৈরি করেছি এবং stdio ট্রান্সপোর্ট ব্যবহার করে সংযোগ করেছি।
- প্রম্পট, রিসোর্স এবং টুলস তালিকাভুক্ত করেছি এবং সেগুলো সক্রিয় করেছি।

এখানে আপনার কাছে একটি ক্লায়েন্ট আছে যা MCP সার্ভারের সাথে কথা বলতে পারে।

পরবর্তী অনুশীলন অংশে আমরা প্রতিটি কোড স্নিপেট বিশ্লেষণ করে বিস্তারিত ব্যাখ্যা করব।

## অনুশীলন: ক্লায়েন্ট লেখা

উপরোক্ত মতো, আসুন ধীরে ধীরে কোড ব্যাখ্যা করি, এবং ইচ্ছা করলে একসাথে কোড করতেও পারেন।

### -1- লাইব্রেরি ইমপোর্ট করা

প্রয়োজনীয় লাইব্রেরি ইমপোর্ট করি, আমাদের ক্লায়েন্ট এবং নির্বাচিত ট্রান্সপোর্ট প্রোটোকল stdio এর রেফারেন্স দরকার। stdio হলো এমন একটি প্রোটোকল যা আপনার লোকাল মেশিনে চলার জন্য উপযুক্ত। SSE আরেকটি ট্রান্সপোর্ট প্রোটোকল যা ভবিষ্যত অধ্যায়ে দেখানো হবে, তবে আপাতত stdio দিয়ে চলুন।

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

Java এর জন্য, আপনি আগের অনুশীলনের MCP সার্ভারের সাথে সংযোগকারী ক্লায়েন্ট তৈরি করবেন। [Getting Started with MCP Server](../../../../03-GettingStarted/01-first-server/solution/java) থেকে একই Java Spring Boot প্রকল্প কাঠামো ব্যবহার করে `src/main/java/com/microsoft/mcp/sample/client/` ফোল্ডারে `SDKClient` নামে একটি নতুন Java ক্লাস তৈরি করুন এবং নিম্নলিখিত ইমপোর্ট যোগ করুন:

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

এখন ইনস্ট্যান্সিয়েশন অংশে যাই।

### -2- ক্লায়েন্ট এবং ট্রান্সপোর্ট ইনস্ট্যান্ট করা

আমাদের ট্রান্সপোর্ট এবং ক্লায়েন্ট উভয়ের ইনস্ট্যান্স তৈরি করতে হবে:

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

উপরের কোডে আমরা:

- stdio ট্রান্সপোর্ট ইনস্ট্যান্স তৈরি করেছি। লক্ষ্য করুন এটি কমান্ড এবং আর্গুমেন্ট নির্দিষ্ট করে কিভাবে সার্ভার খুঁজে পেতে এবং চালু করতে হবে, যা ক্লায়েন্ট তৈরি করার সময় দরকার হবে।

    ```typescript
    const transport = new StdioClientTransport({
        command: "node",
        args: ["server.js"]
    });
    ```

- ক্লায়েন্ট ইনস্ট্যান্ট করেছি নাম এবং ভার্সন দিয়ে।

    ```typescript
    const client = new Client(
    {
        name: "example-client",
        version: "1.0.0"
    });
    ```

- ক্লায়েন্টকে নির্বাচিত ট্রান্সপোর্টের সাথে সংযুক্ত করেছি।

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

উপরের কোডে আমরা:

- প্রয়োজনীয় লাইব্রেরি ইমপোর্ট করেছি
- সার্ভার প্যারামিটার অবজেক্ট ইনস্ট্যান্ট করেছি যা সার্ভার চালানোর জন্য ব্যবহার করব যাতে ক্লায়েন্ট সংযোগ করতে পারে।
- `run` নামের একটি মেথড ডিফাইন করেছি যা `stdio_client` কল করে ক্লায়েন্ট সেশন শুরু করে।
- `asyncio.run` এ `run` মেথড প্রদান করে এন্ট্রি পয়েন্ট তৈরি করেছি।

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

উপরের কোডে আমরা:

- প্রয়োজনীয় লাইব্রেরি ইমপোর্ট করেছি।
- stdio ট্রান্সপোর্ট তৈরি করেছি এবং `mcpClient` নামে ক্লায়েন্ট তৈরি করেছি। এটি MCP সার্ভারের ফিচার তালিকা এবং কল করার জন্য ব্যবহার করব।

দ্রষ্টব্য, "Arguments" এ আপনি *.csproj* অথবা এক্সিকিউটেবল ফাইলের পাথ দিতে পারেন।

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

উপরের কোডে আমরা:

- একটি মেইন মেথড তৈরি করেছি যা `http://localhost:8080` এ SSE ট্রান্সপোর্ট সেটআপ করে যেখানে MCP সার্ভার চলবে।
- একটি ক্লায়েন্ট ক্লাস তৈরি করেছি যা কনস্ট্রাক্টরে ট্রান্সপোর্ট নেয়।
- `run` মেথডে ট্রান্সপোর্ট ব্যবহার করে সিঙ্ক্রোনাস MCP ক্লায়েন্ট তৈরি এবং সংযোগ শুরু করেছি।
- SSE (Server-Sent Events) ট্রান্সপোর্ট ব্যবহার করেছি যা Java Spring Boot MCP সার্ভারের জন্য HTTP ভিত্তিক যোগাযোগের উপযুক্ত।

### -3- সার্ভারের ফিচার তালিকাভুক্ত করা

এখন আমাদের কাছে একটি ক্লায়েন্ট আছে যা প্রোগ্রাম চালালে সংযোগ করতে পারবে। তবে এটি ফিচারগুলো তালিকাভুক্ত করে না, তাই এখন তা করি:

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

এখানে আমরা উপলব্ধ রিসোর্স `list_resources()` এবং টুলস `list_tools` তালিকাভুক্ত করে প্রিন্ট করেছি।

### .NET

```dotnet
foreach (var tool in await client.ListToolsAsync())
{
    Console.WriteLine($"{tool.Name} ({tool.Description})");
}
```

উপরের উদাহরণে আমরা সার্ভারের টুলস তালিকাভুক্ত করেছি। প্রতিটি টুলের নাম প্রিন্ট করেছি।

### Java

```java
// List and demonstrate tools
ListToolsResult toolsList = client.listTools();
System.out.println("Available Tools = " + toolsList);

// You can also ping the server to verify connection
client.ping();
```

উপরের কোডে আমরা:

- MCP সার্ভার থেকে সব টুলস পেতে `listTools()` কল করেছি।
- সংযোগ কাজ করছে কিনা যাচাই করতে `ping()` ব্যবহার করেছি।
- `ListToolsResult` এ সব টুলের নাম, বর্ণনা এবং ইনপুট স্কিমা থাকে।

দারুণ, এখন আমরা সব ফিচার ক্যাপচার করেছি। প্রশ্ন হলো কখন এগুলো ব্যবহার করব? এই ক্লায়েন্টটি বেশ সিম্পল, অর্থাৎ ফিচারগুলো ব্যবহার করতে আমাদের স্পষ্টভাবে কল করতে হবে। পরবর্তী অধ্যায়ে আমরা আরও উন্নত ক্লায়েন্ট তৈরি করব যার নিজস্ব বড় ভাষার মডেল (LLM) থাকবে। আপাতত চলুন দেখি কিভাবে সার্ভারের ফিচারগুলো কল করা যায়:

### -4- ফিচার কল করা

ফিচার কল করতে সঠিক আর্গুমেন্ট এবং কখনো কখনো কল করার নাম নির্দিষ্ট করতে হবে।

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

উপরের কোডে আমরা:

- একটি রিসোর্স পড়েছি, `readResource()` কল করে `uri` নির্দিষ্ট করেছি। সার্ভার সাইডে এরকম দেখাবে:

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

    আমাদের `uri` মান `file://example.txt` সার্ভারের `file://{name}` এর সাথে মেলে। `example.txt` `name` এ ম্যাপ হবে।

- একটি টুল কল করেছি, এর নাম এবং আর্গুমেন্ট নির্দিষ্ট করে:

    ```typescript
    const result = await client.callTool({
        name: "example-tool",
        arguments: {
            arg1: "value"
        }
    });
    ```

- প্রম্পট পেতে `getPrompt()` কল করেছি `name` এবং `arguments` দিয়ে। সার্ভার কোড এরকম:

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

    তাই ক্লায়েন্ট কোডও সার্ভারের ডিক্লেয়ারেশন অনুযায়ী এরকম হবে:

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

উপরের কোডে আমরা:

- `greeting` নামের রিসোর্স `read_resource` দিয়ে কল করেছি।
- `add` নামের টুল `call_tool` দিয়ে কল করেছি।

### .NET

1. একটি টুল কল করার কোড যোগ করি:

  ```csharp
  var result = await mcpClient.CallToolAsync(
      "Add",
      new Dictionary<string, object?>() { ["a"] = 1, ["b"] = 3  },
      cancellationToken:CancellationToken.None);
  ```

2. ফলাফল প্রিন্ট করার জন্য কোড:

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

উপরের কোডে আমরা:

- একাধিক ক্যালকুলেটর টুল `callTool()` মেথড দিয়ে `CallToolRequest` অবজেক্ট ব্যবহার করে কল করেছি।
- প্রতিটি টুল কল টুলের নাম এবং প্রয়োজনীয় আর্গুমেন্টের `Map` নির্দিষ্ট করে।
- সার্ভার টুলগুলো নির্দিষ্ট প্যারামিটার নাম (যেমন "a", "b") আশা করে।
- ফলাফল `CallToolResult` অবজেক্ট হিসেবে ফিরে আসে যা সার্ভারের রেসপন্স ধারণ করে।

### -5- ক্লায়েন্ট চালানো

ক্লায়েন্ট চালাতে টার্মিনালে নিচের কমান্ড টাইপ করুন:

### TypeScript

*package.json* এর "scripts" সেকশনে নিচের এন্ট্রি যোগ করুন:

```json
"client": "tsx && node build/client.js"
```

```sh
npm run client
```

### Python

ক্লায়েন্ট কল করুন:

```sh
python client.py
```

### .NET

```sh
dotnet run
```

### Java

প্রথমে নিশ্চিত করুন MCP সার্ভার `http://localhost:8080` এ চলছে। তারপর ক্লায়েন্ট চালান:

```bash
# Build you project
./mvnw clean compile

# Run the client
./mvnw exec:java -Dexec.mainClass="com.microsoft.mcp.sample.client.SDKClient"
```

অথবা, সম্পূর্ণ ক্লায়েন্ট প্রজেক্ট `03-GettingStarted\02-client\solution\java` ফোল্ডার থেকে রান করতে পারেন:

```bash
# Navigate to the solution directory
cd 03-GettingStarted/02-client/solution/java

# Build and run the JAR
./mvnw clean package
java -jar target/calculator-client-0.0.1-SNAPSHOT.jar
```

## অ্যাসাইনমেন্ট

এই অ্যাসাইনমেন্টে আপনি শিখেছেন ক্লায়েন্ট তৈরি করবেন, তবে নিজের ক্লায়েন্ট তৈরি করবেন।

এখানে একটি সার্ভার আছে যা আপনাকে আপনার ক্লায়েন্ট কোড দিয়ে কল করতে হবে, দেখুন আপনি সার্ভারে আরও ফিচার যোগ করতে পারেন কিনা যাতে এটি আরও আকর্ষণীয় হয়।

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

এই প্রজেক্টটি দেখুন কিভাবে [প্রম্পট এবং রিসোর্স যোগ করবেন](https://github.com/modelcontextprotocol/csharp-sdk/blob/main/samples/EverythingServer/Program.cs)।

এছাড়াও, এই লিঙ্কে দেখুন কিভাবে [প্রম্পট এবং রিসোর্স কল করবেন](https://github.com/modelcontextprotocol/csharp-sdk/blob/main/src/ModelContextProtocol/Client/)।

## সলিউশন

**সলিউশন ফোল্ডার**-এ সম্পূর্ণ, রান করার জন্য প্রস্তুত ক্লায়েন্ট ইমপ্লিমেন্টেশন রয়েছে যা এই টিউটোরিয়ালে আলোচিত সব ধারণা প্রদর্শন করে। প্রতিটি সলিউশন আলাদা, স্বতন্ত্র প্রজেক্ট হিসেবে ক্লায়েন্ট এবং সার্ভার কোড নিয়ে গঠিত।

### 📁 সলিউশন স্ট্রাকচার

সলিউশন ডিরেক্টরি প্রোগ্রামিং ভাষা অনুযায়ী সাজানো:

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

### 🚀 প্রতিটি সলিউশনে যা আছে

প্রতিটি ভাষাভিত্তিক সলিউশন দেয়:

- **সম্পূর্ণ ক্লায়েন্ট ইমপ্লিমেন্টেশন** টিউটোরিয়ালের সব ফিচারসহ
- **কার্যকর প্রজেক্ট স্ট্রাকচার** সঠিক ডিপেন্ডেন্সি ও কনফিগারেশন সহ
- **বিল্ড এবং রান স্ক্রিপ্ট** সহজ সেটআপ ও এক্সিকিউশনের জন্য
- **বিস্তারিত README** ভাষাভিত্তিক নির্দেশনা সহ
- **এরর হ্যান্ডলিং** এবং ফলাফল প্রক্রিয়াকরণের উদাহরণ

### 📖 সলিউশন ব্যবহার

1. **আপনার পছন্দের ভাষার ফোল্ডারে যান**:
   ```bash
   cd solution/typescript/    # For TypeScript
   cd solution/java/          # For Java
   cd solution/python/        # For Python
   cd solution/dotnet/        # For .NET
   ```

2. **প্রতিটি ফোল্ডারের README অনুসরণ করুন**:
   - ডিপেন্ডেন্সি ইনস্টল করা
   - প্রজেক্ট বিল্ড করা
   - ক্লায়েন্ট চালানো

3. **আপনি যা দেখতে পাবেন তার উদাহরণ**:
   ```text
   Prompt: Please review this code: console.log("hello");
   Resource template: file
   Tool result: { content: [ { type: 'text', text: '9' } ] }
   ```

সম্পূর্ণ ডকুমেন্টেশন এবং ধাপে ধাপে নির্দেশনার জন্য দেখুন: **[📖 সলিউশন ডকুমেন্টেশন](./solution/README.md)**

## 🎯 সম্পূর্ণ উদাহরণ

আমরা এই টিউটোরিয়ালে আলোচিত সব প্রোগ্রামিং ভাষার জন্য সম্পূর্ণ, কার্যকর ক্লায়েন্ট ইমপ্লিমেন্টেশন প্রদান করেছি। এই উদাহরণগুলো উপরের সব ফিচার দেখায় এবং রেফারেন্স বা আপনার নিজস্ব প্রজেক্টের জন্য শুরু করার পয়েন্ট হিসেবে ব্যবহার করা যেতে পারে।

### উপলব্ধ সম্পূর্ণ উদাহরণ

| ভাষা    | ফাইল                         | বর্ণনা                                               |
|---------|------------------------------|-----------------------------------------------------|
| **Java**  | [`client_example_java.java`](../../../../03-GettingStarted/02-client/client_example_java.java)       | SSE ট্রান্সপোর্ট ব্যবহার করে সম্পূর্ণ Java ক্লায়েন্ট, ব্যাপক এরর হ্যান্ডলিং সহ |
| **C#**    | [`client_example_csharp.cs`](../../../../03-GettingStarted/02-client/client_example_csharp.cs)       | stdio ট্রান্সপোর্ট ব্যবহার করে সম্পূর্ণ C# ক্লায়েন্ট, স্বয়ংক্রিয় সার্ভার স্টার্টআপ সহ |
| **TypeScript** | [`client_example_typescript.ts`](../../../../03-GettingStarted/02-client/client_example_typescript.ts) | MCP প্রোটোকলের পূর্ণ সমর্থন সহ সম্পূর্ণ TypeScript ক্লায়েন্ট |
| **Python** | [`client_example_python.py`](../../../../03-GettingStarted/02-client/client_example_python.py)       | async/await প্যাটার্ন ব্যবহার করে সম্পূর্ণ Python ক্লায়েন্ট |

প্রতিটি সম্পূর্ণ উদাহরণে রয়েছে:

- ✅ **সংযোগ স্থাপন** এবং এরর হ্যান্ডলিং
- ✅ **সার্ভার আবিষ্কার** (টুলস, রিসোর্স, প্রম্পট যেখানে প্রযোজ্য)
- ✅ **ক্যালকুলেটর অপারেশন** (যোগ, বিয়োগ, গুণ, ভাগ, সাহায্য)
- ✅ **ফলাফল প্রক্রিয়াকরণ** এবং ফরম্যাটেড আউটপুট
- ✅ **বিস্তৃত এরর হ্যান্ডলিং**
- ✅ **পরিষ্কার, ডকুমেন্টেড কোড** ধাপে ধাপে মন্তব্যসহ

### সম্পূর্ণ উদাহরণ শুরু করা

1. উপরের টেবিল থেকে আপনার পছন্দের ভাষা নির্বাচন করুন
2. সম্পূর্ণ উদাহরণ ফাইল পর্যালোচনা করুন পুরো ইমপ্লিমেন্টেশন বুঝতে
3. [`complete_examples.md`](./complete_examples.md) এ নির্দেশনা অনুসরণ করে উদাহরণ রান করুন
4. আপনার নির্দিষ্ট ব্যবহারের জন্য উদাহরণ পরিবর্তন ও সম্প্রসারণ করুন

বিস্তারিত ডকুমেন্টেশনের জন্য দেখুন: **[📖 সম্পূর্ণ উদাহরণ ডকুমেন্টেশন](./complete_examples.md)**

### 💡 সলিউশন বনাম সম্পূর্ণ উদাহরণ

| **সলিউশন ফোল্ডার**          | **সম্পূর্ণ উদাহরণ**               |
|-----------------------------|---------------------------------|
| পূর্ণ প্রজেক্ট স্ট্রাকচার ও বিল্ড ফাইল | একক ফাইল ইমপ্লিমেন্টেশন          |
| ডিপেন্ডেন্সিসহ রান করার জন্য প্রস্তুত | ফোকাসড কোড উদাহরণ               |
| প্রোডাকশন-সদৃশ সেটআপ          | শিক্ষামূলক রেফারেন্স             |
| ভাষাভিত্তিক টুলিং            | ভাষা-সাপেক্ষ তুলনা                |
উভয় পদ্ধতিই মূল্যবান - সম্পূর্ণ প্রকল্পের জন্য **solution folder** ব্যবহার করুন এবং শেখার ও রেফারেন্সের জন্য **complete examples** ব্যবহার করুন।  
## মূল বিষয়সমূহ

এই অধ্যায়ের মূল বিষয়সমূহ ক্লায়েন্ট সম্পর্কে নিম্নরূপ:

- সার্ভারের ফিচারগুলো আবিষ্কার এবং কল করার জন্য ব্যবহার করা যায়।  
- নিজেই শুরু হওয়ার সময় একটি সার্ভার শুরু করতে পারে (যেমন এই অধ্যায়ে) তবে ক্লায়েন্টরা চলমান সার্ভারের সাথে সংযোগ করতেও পারে।  
- পূর্ববর্তী অধ্যায়ে বর্ণিত Inspector-এর মতো বিকল্পের পাশাপাশি সার্ভারের ক্ষমতা পরীক্ষা করার একটি চমৎকার উপায়।  

## অতিরিক্ত সম্পদ

- [Building clients in MCP](https://modelcontextprotocol.io/quickstart/client)

## নমুনা

- [Java Calculator](../samples/java/calculator/README.md)  
- [.Net Calculator](../../../../03-GettingStarted/samples/csharp)  
- [JavaScript Calculator](../samples/javascript/README.md)  
- [TypeScript Calculator](../samples/typescript/README.md)  
- [Python Calculator](../../../../03-GettingStarted/samples/python)  

## পরবর্তী কী

- পরবর্তী: [Creating a client with an LLM](../03-llm-client/README.md)

**অস্বীকৃতি**:  
এই নথিটি AI অনুবাদ সেবা [Co-op Translator](https://github.com/Azure/co-op-translator) ব্যবহার করে অনূদিত হয়েছে। আমরা যথাসাধ্য সঠিকতার চেষ্টা করি, তবে স্বয়ংক্রিয় অনুবাদে ত্রুটি বা অসঙ্গতি থাকতে পারে। মূল নথিটি তার নিজস্ব ভাষায়ই কর্তৃত্বপূর্ণ উৎস হিসেবে বিবেচিত হওয়া উচিত। গুরুত্বপূর্ণ তথ্যের জন্য পেশাদার মানব অনুবাদ গ্রহণ করার পরামর্শ দেওয়া হয়। এই অনুবাদের ব্যবহারে সৃষ্ট কোনো ভুল বোঝাবুঝি বা ভুল ব্যাখ্যার জন্য আমরা দায়ী নই।