<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "22afa94e3912cd37af9ff20cf4aebc93",
  "translation_date": "2025-07-22T09:13:53+00:00",
  "source_file": "03-GettingStarted/02-client/README.md",
  "language_code": "hi"
}
-->
# क्लाइंट बनाना

क्लाइंट ऐसे कस्टम एप्लिकेशन या स्क्रिप्ट होते हैं जो सीधे MCP सर्वर से संवाद करते हैं ताकि संसाधन, टूल्स और प्रॉम्प्ट्स का अनुरोध किया जा सके। इंस्पेक्टर टूल का उपयोग करने के विपरीत, जो सर्वर के साथ इंटरैक्ट करने के लिए ग्राफिकल इंटरफेस प्रदान करता है, अपना क्लाइंट लिखने से प्रोग्रामेटिक और स्वचालित इंटरैक्शन संभव होता है। यह डेवलपर्स को MCP की क्षमताओं को अपने वर्कफ़्लो में एकीकृत करने, कार्यों को स्वचालित करने और विशिष्ट आवश्यकताओं के अनुसार कस्टम समाधान बनाने में सक्षम बनाता है।

## परिचय

यह पाठ MCP (मॉडल कॉन्टेक्स्ट प्रोटोकॉल) इकोसिस्टम में क्लाइंट्स की अवधारणा को पेश करता है। आप सीखेंगे कि अपना क्लाइंट कैसे लिखें और इसे MCP सर्वर से कैसे कनेक्ट करें।

## सीखने के उद्देश्य

इस पाठ के अंत तक, आप सक्षम होंगे:

- समझें कि क्लाइंट क्या कर सकता है।
- अपना क्लाइंट लिखें।
- MCP सर्वर के साथ क्लाइंट को कनेक्ट और टेस्ट करें ताकि यह सुनिश्चित हो सके कि सर्वर अपेक्षित रूप से काम कर रहा है।

## क्लाइंट लिखने में क्या शामिल है?

क्लाइंट लिखने के लिए, आपको निम्नलिखित करना होगा:

- **सही लाइब्रेरी आयात करें**। आप वही लाइब्रेरी उपयोग करेंगे जो पहले उपयोग की गई थी, बस अलग-अलग कंस्ट्रक्ट्स।
- **क्लाइंट को इंस्टेंटिएट करें**। इसमें क्लाइंट का एक इंस्टेंस बनाना और इसे चुने हुए ट्रांसपोर्ट मेथड से कनेक्ट करना शामिल होगा।
- **संसाधनों को सूचीबद्ध करने का निर्णय लें**। आपका MCP सर्वर संसाधन, टूल्स और प्रॉम्प्ट्स के साथ आता है, आपको तय करना होगा कि कौन सा सूचीबद्ध करना है।
- **क्लाइंट को होस्ट एप्लिकेशन में एकीकृत करें**। एक बार जब आप सर्वर की क्षमताओं को जान लेते हैं, तो आपको इसे अपने होस्ट एप्लिकेशन में एकीकृत करना होगा ताकि यदि कोई उपयोगकर्ता प्रॉम्प्ट या अन्य कमांड टाइप करता है, तो संबंधित सर्वर फीचर सक्रिय हो जाए।

अब जब हमने उच्च स्तर पर समझ लिया है कि हम क्या करने जा रहे हैं, तो चलिए अगले उदाहरण पर नज़र डालते हैं।

### एक उदाहरण क्लाइंट

आइए इस उदाहरण क्लाइंट को देखें:

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

उपरोक्त कोड में हमने:

- लाइब्रेरी आयात की।
- क्लाइंट का एक इंस्टेंस बनाया और इसे ट्रांसपोर्ट के लिए stdio का उपयोग करके कनेक्ट किया।
- प्रॉम्प्ट्स, संसाधन और टूल्स को सूचीबद्ध किया और उन्हें सक्रिय किया।

तो आपके पास एक क्लाइंट है जो MCP सर्वर से संवाद कर सकता है।

आइए अगले अभ्यास अनुभाग में समय लेकर प्रत्येक कोड स्निपेट को तोड़ें और समझाएं कि क्या हो रहा है।

## अभ्यास: क्लाइंट लिखना

जैसा कि ऊपर कहा गया है, आइए कोड को समझाने में समय लें, और यदि आप चाहें तो कोड के साथ अभ्यास करें।

### -1- लाइब्रेरी आयात करें

आइए उन लाइब्रेरी को आयात करें जिनकी हमें आवश्यकता है। हमें क्लाइंट और हमारे चुने हुए ट्रांसपोर्ट प्रोटोकॉल, stdio का संदर्भ चाहिए। stdio उन चीजों के लिए एक प्रोटोकॉल है जो आपके स्थानीय मशीन पर चलने के लिए बनाई गई हैं। SSE एक और ट्रांसपोर्ट प्रोटोकॉल है जिसे हम भविष्य के अध्यायों में दिखाएंगे, लेकिन यह आपका दूसरा विकल्प है। फिलहाल, आइए stdio के साथ जारी रखें।

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

Java के लिए, आप पिछले अभ्यास से MCP सर्वर से कनेक्ट करने के लिए एक क्लाइंट बनाएंगे। [Getting Started with MCP Server](../../../../03-GettingStarted/01-first-server/solution/java) से वही Java Spring Boot प्रोजेक्ट संरचना का उपयोग करते हुए, `src/main/java/com/microsoft/mcp/sample/client/` फ़ोल्डर में `SDKClient` नामक एक नया Java क्लास बनाएं और निम्नलिखित आयात जोड़ें:

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

आइए इंस्टेंटिएशन पर आगे बढ़ें।

### -2- क्लाइंट और ट्रांसपोर्ट को इंस्टेंटिएट करना

हमें ट्रांसपोर्ट का एक इंस्टेंस और हमारे क्लाइंट का एक इंस्टेंस बनाना होगा:

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

उपरोक्त कोड में हमने:

- stdio ट्रांसपोर्ट का एक इंस्टेंस बनाया। ध्यान दें कि यह सर्वर को ढूंढने और स्टार्टअप करने के लिए कमांड और आर्ग्स को निर्दिष्ट करता है क्योंकि यह कुछ ऐसा है जिसे हमें क्लाइंट बनाते समय करना होगा।

    ```typescript
    const transport = new StdioClientTransport({
        command: "node",
        args: ["server.js"]
    });
    ```

- क्लाइंट को एक नाम और संस्करण देकर इंस्टेंटिएट किया।

    ```typescript
    const client = new Client(
    {
        name: "example-client",
        version: "1.0.0"
    });
    ```

- क्लाइंट को चुने हुए ट्रांसपोर्ट से कनेक्ट किया।

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

उपरोक्त कोड में हमने:

- आवश्यक लाइब्रेरी आयात की।
- सर्वर पैरामीटर ऑब्जेक्ट को इंस्टेंटिएट किया क्योंकि हम इसका उपयोग सर्वर को चलाने के लिए करेंगे ताकि हम अपने क्लाइंट के साथ कनेक्ट कर सकें।
- एक `run` मेथड परिभाषित किया जो बदले में `stdio_client` को कॉल करता है जो एक क्लाइंट सेशन शुरू करता है।
- एक एंट्री पॉइंट बनाया जहां हम `run` मेथड को `asyncio.run` में प्रदान करते हैं।

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

उपरोक्त कोड में हमने:

- आवश्यक लाइब्रेरी आयात की।
- stdio ट्रांसपोर्ट बनाया और एक क्लाइंट `mcpClient` बनाया। बाद वाला कुछ ऐसा है जिसका उपयोग हम MCP सर्वर पर फीचर्स को सूचीबद्ध और सक्रिय करने के लिए करेंगे।

ध्यान दें, "Arguments" में, आप या तो *.csproj* या निष्पादन योग्य को इंगित कर सकते हैं।

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

उपरोक्त कोड में हमने:

- एक मुख्य मेथड बनाया जो `http://localhost:8080` पर चल रहे हमारे MCP सर्वर को इंगित करते हुए SSE ट्रांसपोर्ट सेट करता है।
- एक क्लाइंट क्लास बनाया जो ट्रांसपोर्ट को एक कंस्ट्रक्टर पैरामीटर के रूप में लेता है।
- `run` मेथड में, हमने ट्रांसपोर्ट का उपयोग करके एक सिंक्रोनस MCP क्लाइंट बनाया और कनेक्शन को इनिशियलाइज़ किया।
- SSE (Server-Sent Events) ट्रांसपोर्ट का उपयोग किया जो Java Spring Boot MCP सर्वर के साथ HTTP-आधारित संचार के लिए उपयुक्त है।

### -3- सर्वर फीचर्स को सूचीबद्ध करना

अब, हमारे पास एक क्लाइंट है जो कनेक्ट कर सकता है यदि प्रोग्राम चलाया जाए। हालांकि, यह वास्तव में अपने फीचर्स को सूचीबद्ध नहीं करता है, तो चलिए इसे अगला करते हैं:

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

यहां हमने उपलब्ध संसाधनों को `list_resources()` और टूल्स को `list_tools` के माध्यम से सूचीबद्ध किया और उन्हें प्रिंट किया।

#### .NET

```dotnet
foreach (var tool in await client.ListToolsAsync())
{
    Console.WriteLine($"{tool.Name} ({tool.Description})");
}
```

ऊपर एक उदाहरण है कि हम सर्वर पर टूल्स को कैसे सूचीबद्ध कर सकते हैं। प्रत्येक टूल के लिए, हमने उसका नाम प्रिंट किया।

#### Java

```java
// List and demonstrate tools
ListToolsResult toolsList = client.listTools();
System.out.println("Available Tools = " + toolsList);

// You can also ping the server to verify connection
client.ping();
```

उपरोक्त कोड में हमने:

- MCP सर्वर से सभी उपलब्ध टूल्स प्राप्त करने के लिए `listTools()` को कॉल किया।
- सर्वर से कनेक्शन काम कर रहा है यह सुनिश्चित करने के लिए `ping()` का उपयोग किया।
- `ListToolsResult` में सभी टूल्स की जानकारी होती है जिसमें उनके नाम, विवरण और इनपुट स्कीमा शामिल हैं।

बहुत अच्छा, अब हमने सभी फीचर्स को कैप्चर कर लिया है। अब सवाल यह है कि हम उन्हें कब उपयोग करते हैं? खैर, यह क्लाइंट काफी सरल है, सरल इस अर्थ में कि हमें फीचर्स को सक्रिय करने के लिए उन्हें स्पष्ट रूप से कॉल करना होगा। अगले अध्याय में, हम एक अधिक उन्नत क्लाइंट बनाएंगे जिसमें अपने बड़े भाषा मॉडल (LLM) तक पहुंच होगी। फिलहाल, चलिए देखते हैं कि हम सर्वर पर फीचर्स को कैसे सक्रिय कर सकते हैं:

### -4- फीचर्स को सक्रिय करना

फीचर्स को सक्रिय करने के लिए हमें यह सुनिश्चित करना होगा कि हम सही आर्ग्युमेंट्स और कुछ मामलों में उस चीज़ का नाम निर्दिष्ट करें जिसे हम सक्रिय करने की कोशिश कर रहे हैं।

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

उपरोक्त कोड में हमने:

- एक संसाधन पढ़ा, हमने `readResource()` को कॉल करके `uri` निर्दिष्ट किया। यह सर्वर साइड पर कुछ इस तरह दिखेगा:

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

    हमारा `uri` मान `file://example.txt` सर्वर पर `file://{name}` से मेल खाता है। `example.txt` को `name` पर मैप किया जाएगा।

- एक टूल को कॉल किया, हमने इसे इसके `name` और इसके `arguments` को निर्दिष्ट करके कॉल किया:

    ```typescript
    const result = await client.callTool({
        name: "example-tool",
        arguments: {
            arg1: "value"
        }
    });
    ```

- प्रॉम्प्ट प्राप्त किया, प्रॉम्प्ट प्राप्त करने के लिए, आप `getPrompt()` को `name` और `arguments` के साथ कॉल करते हैं। सर्वर कोड कुछ इस तरह दिखता है:

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

    और आपका परिणामी क्लाइंट कोड सर्वर पर घोषित किए गए से मेल खाने के लिए कुछ इस तरह दिखता है:

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

उपरोक्त कोड में हमने:

- `read_resource` का उपयोग करके `greeting` नामक एक संसाधन को कॉल किया।
- `call_tool` का उपयोग करके `add` नामक एक टूल को सक्रिय किया।

#### .NET

1. टूल को कॉल करने के लिए कुछ कोड जोड़ें:

  ```csharp
  var result = await mcpClient.CallToolAsync(
      "Add",
      new Dictionary<string, object?>() { ["a"] = 1, ["b"] = 3  },
      cancellationToken:CancellationToken.None);
  ```

1. परिणाम को प्रिंट करने के लिए, यहां कुछ कोड है जो इसे संभालता है:

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

उपरोक्त कोड में हमने:

- `CallToolRequest` ऑब्जेक्ट्स के साथ `callTool()` मेथड का उपयोग करके कई कैलकुलेटर टूल्स को कॉल किया।
- प्रत्येक टूल कॉल में उस टूल का नाम और उस टूल द्वारा आवश्यक आर्ग्युमेंट्स का `Map` निर्दिष्ट किया।
- सर्वर टूल्स विशिष्ट पैरामीटर नामों (जैसे "a", "b" गणितीय ऑपरेशनों के लिए) की अपेक्षा करते हैं।
- परिणाम `CallToolResult` ऑब्जेक्ट्स के रूप में लौटाए जाते हैं जो सर्वर से प्रतिक्रिया को शामिल करते हैं।

### -5- क्लाइंट चलाना

क्लाइंट चलाने के लिए, टर्मिनल में निम्नलिखित कमांड टाइप करें:

#### TypeScript

*package.json* में "scripts" सेक्शन में निम्नलिखित एंट्री जोड़ें:

```json
"client": "tsx && node build/client.js"
```

```sh
npm run client
```

#### Python

निम्नलिखित कमांड के साथ क्लाइंट को कॉल करें:

```sh
python client.py
```

#### .NET

```sh
dotnet run
```

#### Java

पहले, सुनिश्चित करें कि आपका MCP सर्वर `http://localhost:8080` पर चल रहा है। फिर क्लाइंट चलाएं:

```bash
# Build you project
./mvnw clean compile

# Run the client
./mvnw exec:java -Dexec.mainClass="com.microsoft.mcp.sample.client.SDKClient"
```

वैकल्पिक रूप से, आप समाधान फ़ोल्डर `03-GettingStarted\02-client\solution\java` में प्रदान किए गए पूर्ण क्लाइंट प्रोजेक्ट को चला सकते हैं:

```bash
# Navigate to the solution directory
cd 03-GettingStarted/02-client/solution/java

# Build and run the JAR
./mvnw clean package
java -jar target/calculator-client-0.0.1-SNAPSHOT.jar
```

## असाइनमेंट

इस असाइनमेंट में, आप जो कुछ भी आपने क्लाइंट बनाने में सीखा है उसका उपयोग करेंगे लेकिन अपना खुद का क्लाइंट बनाएंगे।

यहां एक सर्वर है जिसे आपको अपने क्लाइंट कोड के माध्यम से कॉल करना होगा, देखें कि क्या आप सर्वर में अधिक फीचर्स जोड़ सकते हैं ताकि यह अधिक रोचक हो।

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

इस प्रोजेक्ट को देखें कि आप [प्रॉम्प्ट्स और संसाधन कैसे जोड़ सकते हैं](https://github.com/modelcontextprotocol/csharp-sdk/blob/main/samples/EverythingServer/Program.cs)।

साथ ही, इस लिंक को देखें कि [प्रॉम्प्ट्स और संसाधन कैसे सक्रिय करें](https://github.com/modelcontextprotocol/csharp-sdk/blob/main/src/ModelContextProtocol/Client/)।

## समाधान

**सॉल्यूशन फ़ोल्डर** में इस ट्यूटोरियल में शामिल सभी अवधारणाओं को प्रदर्शित करने वाले पूर्ण, रेडी-टू-रन क्लाइंट इम्प्लीमेंटेशन शामिल हैं। प्रत्येक समाधान में क्लाइंट और सर्वर कोड अलग-अलग, स्व-निहित प्रोजेक्ट्स में व्यवस्थित होते हैं।

### 📁 समाधान संरचना

सॉल्यूशन डायरेक्टरी प्रोग्रामिंग भाषा के अनुसार व्यवस्थित है:

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

### 🚀 प्रत्येक समाधान में क्या शामिल है

प्रत्येक भाषा-विशिष्ट समाधान प्रदान करता है:

- **पूर्ण क्लाइंट इम्प्लीमेंटेशन** ट्यूटोरियल के सभी फीचर्स के साथ
- **कार्यशील प्रोजेक्ट संरचना** उचित डिपेंडेंसी और कॉन्फ़िगरेशन के साथ
- **बिल्ड और रन स्क्रिप्ट्स** आसान सेटअप और निष्पादन के लिए
- **विस्तृत README** भाषा-विशिष्ट निर्देशों के साथ
- **एरर हैंडलिंग** और परिणाम प्रोसेसिंग के उदाहरण

### 📖 समाधान का उपयोग करना

1. **अपनी पसंदीदा भाषा फ़ोल्डर पर जाएं**:

   ```bash
   cd solution/typescript/    # For TypeScript
   cd solution/java/          # For Java
   cd solution/python/        # For Python
   cd solution/dotnet/        # For .NET
   ```

2. **प्रत्येक फ़ोल्डर में README निर्देशों का पालन करें**:
   - डिपेंडेंसी इंस्टॉल करना
   - प्रोजेक्ट को बिल्ड करना
   - क्लाइंट को चलाना

3. **उदाहरण आउटपुट** जो आपको देखना चाहिए:

   ```text
   Prompt: Please review this code: console.log("hello");
   Resource template: file
   Tool result: { content: [ { type: 'text', text: '9' } ] }
   ```

पूर्ण दस्तावेज़ और चरण-दर-चरण निर्देशों के लिए देखें: **[📖 समाधान दस्तावेज़](./solution/README.md)**

## 🎯 पूर्ण उदाहरण

हमने इस ट्यूटोरियल में शामिल सभी प्रोग्रामिंग भाषाओं के लिए पूर्ण, कार्यशील क्लाइंट इम्प्लीमेंटेशन प्रदान किए हैं। ये उदाहरण ऊपर वर्णित सभी कार्यक्षमता का प्रदर्शन करते हैं और आपके अपने प्रोजेक्ट्स के लिए संदर्भ इम्प्लीमेंटेशन या प्रारंभिक बिंदु के रूप में उपयोग किए जा सकते हैं।

### उपलब्ध पूर्ण उदाहरण

| भाषा | फ़ाइल | विवरण |
|------|-------|--------|
| **Java** | [`client_example_java.java`](../../../../03-GettingStarted/02-client/client_example_java.java) | SSE ट्रांसपोर्ट का उपयोग करने वाला पूर्ण Java क्लाइंट जिसमें व्यापक एरर हैंडलिंग है |
| **C#** | [`client_example_csharp.cs`](../../../../03-GettingStarted/02-client/client_example_csharp.cs) | stdio ट्रांसपोर्ट का उपयोग करने वाला पूर्ण C# क्लाइंट जिसमें स्वचालित सर्वर स्टार्टअप है |
| **TypeScript** | [`client_example_typescript.ts`](../../../../03-GettingStarted/02-client/client_example_typescript.ts) | MCP प्रोटोकॉल समर्थन के साथ पूर्ण TypeScript क्लाइंट |
| **Python** | [`client_example_python.py`](../../../../03-GettingStarted/02-client/client_example_python.py) | async/await पैटर्न का उपयोग करने वाला पूर्ण Python क्लाइंट |

प्रत्येक पूर्ण उदाहरण में शामिल है:

- ✅ **कनेक्शन स्थापना** और एरर हैंडलिंग
- ✅ **सर्वर डिस्कवरी** (टूल्स, संसाधन, प्रॉम्प्ट्स जहां लागू हो)
- ✅ **कैलकुलेटर ऑपरेशन्स** (जोड़ना, घटाना, गुणा करना, भाग देना, मदद)
- ✅ **परिणाम प्रोसेसिंग** और स्वरूपित आउटपुट
- ✅ **व्यापक एरर हैंडलिंग**
- ✅ **साफ, प्रलेखित कोड** चरण-दर-चरण टिप्पणियों के साथ

### पूर्ण उदाहरण के साथ शुरुआत करना

1. **ऊपर दी गई तालिका से अपनी पसंदीदा भाषा चुनें**।
2. **पूर्ण उदाहरण फ़ाइल की समीक्षा करें** ताकि पूरी इम्प्लीमेंटेशन को समझा जा सके।
3. **उदाहरण चलाएं** [`complete_examples.md`](./complete_examples.md) में दिए गए निर्देशों का पालन करते हुए।
4. **उदाहरण को संशोधित और विस्तारित करें** अपने विशिष्ट उपयोग के मामले के लिए।

पूर्ण उदाहरणों को चलाने और अनुकूलित करने के बारे में विस्तृत दस्तावेज़ के लिए देखें: **[📖 पूर्ण उदाहरण दस्तावेज़](./complete_examples.md)**

### 💡 समाधान बनाम पूर्ण उदाहरण

| **सॉल्यूशन फ़ोल्डर** | **पूर्ण उदाहरण** |
|--------------------|--------------------- |
| बिल्ड फ़ाइलों के साथ पूर्ण प्रोजेक्ट संरचना | सिंगल-फ़ाइल इम्प्लीमेंटेशन |
| डिपेंडेंसी के साथ रेडी-टू-रन | केंद्रित कोड उदाहरण |
| प्रोडक्शन-जैसा सेटअप | शैक्षिक संदर्भ |
| भाषा-विशिष्ट टूलिंग | क्रॉस-लैंग्वेज तुलना |
दोनों दृष्टिकोण महत्वपूर्ण हैं - **समाधान फ़ोल्डर** का उपयोग पूर्ण प्रोजेक्ट्स के लिए करें और **पूर्ण उदाहरणों** का उपयोग सीखने और संदर्भ के लिए करें।

## मुख्य बातें

इस अध्याय के लिए मुख्य बातें निम्नलिखित हैं, जो क्लाइंट्स के बारे में हैं:

- सर्वर पर फीचर्स को खोजने और उपयोग करने के लिए क्लाइंट्स का उपयोग किया जा सकता है।
- क्लाइंट्स खुद को शुरू करते समय सर्वर को भी शुरू कर सकते हैं (जैसा कि इस अध्याय में बताया गया है), लेकिन क्लाइंट्स पहले से चल रहे सर्वर्स से भी कनेक्ट कर सकते हैं।
- सर्वर की क्षमताओं को जांचने के लिए यह एक शानदार तरीका है, अन्य विकल्पों जैसे कि पिछले अध्याय में वर्णित Inspector के साथ।

## अतिरिक्त संसाधन

- [MCP में क्लाइंट्स बनाना](https://modelcontextprotocol.io/quickstart/client)

## नमूने

- [जावा कैलकुलेटर](../samples/java/calculator/README.md)
- [.Net कैलकुलेटर](../../../../03-GettingStarted/samples/csharp)
- [जावास्क्रिप्ट कैलकुलेटर](../samples/javascript/README.md)
- [टाइपस्क्रिप्ट कैलकुलेटर](../samples/typescript/README.md)
- [पायथन कैलकुलेटर](../../../../03-GettingStarted/samples/python)

## आगे क्या

- अगला: [LLM के साथ क्लाइंट बनाना](../03-llm-client/README.md)

**अस्वीकरण**:  
यह दस्तावेज़ AI अनुवाद सेवा [Co-op Translator](https://github.com/Azure/co-op-translator) का उपयोग करके अनुवादित किया गया है। जबकि हम सटीकता सुनिश्चित करने का प्रयास करते हैं, कृपया ध्यान दें कि स्वचालित अनुवाद में त्रुटियां या अशुद्धियां हो सकती हैं। मूल भाषा में उपलब्ध मूल दस्तावेज़ को प्रामाणिक स्रोत माना जाना चाहिए। महत्वपूर्ण जानकारी के लिए, पेशेवर मानव अनुवाद की सिफारिश की जाती है। इस अनुवाद के उपयोग से उत्पन्न किसी भी गलतफहमी या गलत व्याख्या के लिए हम उत्तरदायी नहीं हैं।