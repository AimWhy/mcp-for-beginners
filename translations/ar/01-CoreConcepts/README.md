<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "4bf553c18e7e226c3d76ab0cde627d26",
  "translation_date": "2025-05-20T20:22:14+00:00",
  "source_file": "01-CoreConcepts/README.md",
  "language_code": "ar"
}
-->
# 📖 مفاهيم أساسية في MCP: إتقان بروتوكول سياق النموذج لتكامل الذكاء الاصطناعي

بروتوكول سياق النموذج (MCP) هو إطار عمل قوي وموحد يهدف إلى تحسين التواصل بين نماذج اللغة الكبيرة (LLMs) والأدوات الخارجية، التطبيقات، ومصادر البيانات. سيرشدك هذا الدليل المحسن لمحركات البحث عبر المفاهيم الأساسية لـ MCP، ليضمن فهمك لهندسة العميل-الخادم، المكونات الأساسية، آليات الاتصال، وأفضل ممارسات التنفيذ.

## نظرة عامة

تستعرض هذه الدرس البنية الأساسية والمكونات التي تشكل نظام بروتوكول سياق النموذج (MCP). ستتعرف على هندسة العميل-الخادم، المكونات الرئيسية، وآليات الاتصال التي تدعم تفاعلات MCP.

## 👩‍🎓 أهداف التعلم الرئيسية

بنهاية هذا الدرس، ستكون قادرًا على:

- فهم هندسة العميل-الخادم في MCP.
- تحديد أدوار ومسؤوليات المضيفين، العملاء، والخوادم.
- تحليل الميزات الأساسية التي تجعل MCP طبقة تكامل مرنة.
- التعرف على كيفية تدفق المعلومات داخل نظام MCP.
- اكتساب رؤى عملية من خلال أمثلة برمجية في .NET، Java، Python، وJavaScript.

## 🔎 هندسة MCP: نظرة أعمق

يعتمد نظام MCP على نموذج العميل-الخادم. تتيح هذه البنية المعيارية لتطبيقات الذكاء الاصطناعي التفاعل مع الأدوات، قواعد البيانات، واجهات برمجة التطبيقات، والموارد السياقية بكفاءة. دعونا نفصل هذه الهندسة إلى مكوناتها الأساسية.

### 1. المضيفون

في بروتوكول سياق النموذج (MCP)، يلعب المضيفون دورًا حيويًا كواجهة رئيسية يتفاعل من خلالها المستخدمون مع البروتوكول. المضيفون هم تطبيقات أو بيئات تبدأ الاتصالات مع خوادم MCP للوصول إلى البيانات، الأدوات، والتعليمات. من أمثلة المضيفين بيئات تطوير متكاملة مثل Visual Studio Code، أدوات الذكاء الاصطناعي مثل Claude Desktop، أو وكلاء مخصصين لأداء مهام محددة.

**المضيفون** هم تطبيقات LLM التي تبدأ الاتصالات. هم:

- ينفذون أو يتفاعلون مع نماذج الذكاء الاصطناعي لتوليد الردود.
- يبدأون الاتصالات مع خوادم MCP.
- يديرون تدفق المحادثة وواجهة المستخدم.
- يتحكمون في أذونات الأمان والقيود.
- يتعاملون مع موافقة المستخدم لمشاركة البيانات وتنفيذ الأدوات.

### 2. العملاء

العملاء مكونات أساسية تسهل التفاعل بين المضيفين وخوادم MCP. يعمل العملاء كوسطاء، مما يمكّن المضيفين من الوصول إلى واستخدام الوظائف التي توفرها خوادم MCP. لهم دور حاسم في ضمان تواصل سلس وتبادل بيانات فعال ضمن هندسة MCP.

**العملاء** هم موصلات داخل تطبيق المضيف. هم:

- يرسلون طلبات إلى الخوادم مع التعليمات أو المطالبات.
- يتفاوضون على القدرات مع الخوادم.
- يديرون طلبات تنفيذ الأدوات من النماذج.
- يعالجون ويعرضون الردود للمستخدمين.

### 3. الخوادم

الخوادم مسؤولة عن معالجة الطلبات من عملاء MCP وتقديم الردود المناسبة. تدير عمليات متعددة مثل استرجاع البيانات، تنفيذ الأدوات، وتوليد التعليمات. تضمن الخوادم أن يكون الاتصال بين العملاء والمضيفين فعالًا وموثوقًا، مع الحفاظ على سلامة عملية التفاعل.

**الخوادم** هي خدمات توفر السياق والقدرات. هم:

- يسجلون الميزات المتاحة (الموارد، التعليمات، الأدوات).
- يستقبلون وينفذون نداءات الأدوات من العميل.
- يقدمون معلومات سياقية لتعزيز ردود النموذج.
- يعيدون النتائج إلى العميل.
- يحافظون على الحالة عبر التفاعلات عند الحاجة.

يمكن لأي شخص تطوير خوادم لتوسيع قدرات النموذج بوظائف متخصصة.

### 4. ميزات الخادم

توفر خوادم MCP اللبنات الأساسية التي تمكّن تفاعلات غنية بين العملاء، المضيفين، ونماذج اللغة. صممت هذه الميزات لتعزيز قدرات MCP من خلال تقديم سياق منظم، أدوات، وتعليمات.

يمكن لخوادم MCP تقديم أي من الميزات التالية:

#### 📑 الموارد

تشمل الموارد في MCP أنواعًا مختلفة من السياق والبيانات التي يمكن للمستخدمين أو نماذج الذكاء الاصطناعي الاستفادة منها. هذه تشمل:

- **البيانات السياقية**: معلومات وسياق يمكن للمستخدمين أو النماذج الاستعانة بها لاتخاذ القرارات وتنفيذ المهام.
- **قواعد المعرفة ومستودعات الوثائق**: مجموعات من البيانات المنظمة وغير المنظمة، مثل المقالات، الكتيبات، والأوراق البحثية التي توفر رؤى ومعلومات قيمة.
- **الملفات المحلية وقواعد البيانات**: بيانات مخزنة محليًا على الأجهزة أو ضمن قواعد البيانات، متاحة للمعالجة والتحليل.
- **واجهات برمجة التطبيقات وخدمات الويب**: واجهات وخدمات خارجية توفر بيانات إضافية ووظائف، مما يمكّن التكامل مع موارد وأدوات عبر الإنترنت.

مثال على مورد يمكن أن يكون مخطط قاعدة بيانات أو ملف يمكن الوصول إليه كما يلي:

```text
file://log.txt
database://schema
```

### 🤖 التعليمات

تشمل التعليمات في MCP قوالب وأنماط تفاعل محددة مسبقًا مصممة لتبسيط سير عمل المستخدم وتحسين التواصل. تتضمن:

- **رسائل وسير عمل قالبية**: رسائل وعمليات منظمة مسبقًا توجه المستخدمين خلال مهام وتفاعلات محددة.
- **أنماط تفاعل معرفة مسبقًا**: تسلسلات موحدة من الإجراءات والردود تسهل التواصل المتسق والفعال.
- **قوالب محادثة متخصصة**: قوالب قابلة للتخصيص موجهة لأنواع محددة من المحادثات لضمان تفاعلات ملائمة وسياقية.

يمكن أن تبدو قالب التعليمات كما يلي:

```markdown
Generate a product slogan based on the following {{product}} with the following {{keywords}}
```

#### ⛏️ الأدوات

الأدوات في MCP هي وظائف يمكن للنموذج تنفيذها لأداء مهام محددة. صممت هذه الأدوات لتعزيز قدرات النموذج من خلال توفير عمليات منظمة وموثوقة. الجوانب الرئيسية تشمل:

- **وظائف يمكن للنموذج تنفيذها**: الأدوات هي وظائف قابلة للتنفيذ يمكن للنموذج استدعاؤها لأداء مهام متنوعة.
- **اسم ووصف فريد**: لكل أداة اسم مميز ووصف مفصل يشرح هدفها ووظيفتها.
- **المعلمات والمخرجات**: تقبل الأدوات معلمات محددة وتعيد مخرجات منظمة، لضمان نتائج متسقة ومتوقعة.
- **وظائف منفصلة**: تؤدي الأدوات وظائف منفصلة مثل البحث على الويب، الحسابات، واستعلامات قواعد البيانات.

يمكن أن يكون مثال أداة كما يلي:

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

## ميزات العميل

في MCP، يقدم العملاء عدة ميزات رئيسية للخوادم، تعزز الوظائف العامة والتفاعل ضمن البروتوكول. واحدة من الميزات الملحوظة هي Sampling.

### 👉 Sampling

- **سلوكيات وكيل مُبادرة من الخادم**: تمكّن العملاء الخوادم من بدء إجراءات أو سلوكيات محددة بشكل مستقل، مما يعزز القدرات الديناميكية للنظام.
- **تفاعلات متكررة مع LLM**: تتيح هذه الميزة تفاعلات متكررة مع نماذج اللغة الكبيرة، مما يمكن من معالجة أكثر تعقيدًا وتكرارًا للمهام.
- **طلب استكمالات إضافية للنموذج**: يمكن للخوادم طلب استكمالات إضافية من النموذج لضمان أن تكون الردود شاملة وذات صلة سياقية.

## تدفق المعلومات في MCP

يحدد MCP تدفقًا منظمًا للمعلومات بين المضيفين، العملاء، الخوادم، والنماذج. فهم هذا التدفق يساعد على توضيح كيفية معالجة طلبات المستخدم وكيفية دمج الأدوات والبيانات الخارجية في ردود النموذج.

- **المضيف يبدأ الاتصال**  
  يفتح تطبيق المضيف (مثل بيئة تطوير متكاملة أو واجهة دردشة) اتصالًا بخادم MCP، عادة عبر STDIO، WebSocket، أو وسيلة نقل مدعومة أخرى.

- **التفاوض على القدرات**  
  يتبادل العميل (المضمن في المضيف) والخادم معلومات حول الميزات، الأدوات، الموارد، وإصدارات البروتوكول المدعومة. هذا يضمن فهم الطرفين للقدرات المتاحة للجلسة.

- **طلب المستخدم**  
  يتفاعل المستخدم مع المضيف (مثلاً، بإدخال مطالبة أو أمر). يجمع المضيف هذا الإدخال ويمرره إلى العميل للمعالجة.

- **استخدام مورد أو أداة**  
  - قد يطلب العميل سياقًا إضافيًا أو موارد من الخادم (مثل ملفات، مدخلات قواعد البيانات، أو مقالات قاعدة المعرفة) لتعزيز فهم النموذج.
  - إذا قرر النموذج أن أداة مطلوبة (مثل جلب بيانات، إجراء حساب، أو استدعاء API)، يرسل العميل طلب استدعاء أداة إلى الخادم، محددًا اسم الأداة والمعلمات.

- **تنفيذ الخادم**  
  يستقبل الخادم طلب المورد أو الأداة، ينفذ العمليات اللازمة (مثل تشغيل وظيفة، استعلام قاعدة بيانات، أو استرجاع ملف)، ويعيد النتائج إلى العميل بشكل منظم.

- **توليد الرد**  
  يدمج العميل ردود الخادم (بيانات الموارد، مخرجات الأدوات، إلخ) في التفاعل الجاري مع النموذج. يستخدم النموذج هذه المعلومات لتوليد رد شامل وملائم سياقيًا.

- **عرض النتيجة**  
  يستلم المضيف المخرجات النهائية من العميل ويعرضها للمستخدم، غالبًا بما يشمل نص النموذج المولد وأي نتائج من تنفيذ الأدوات أو البحث في الموارد.

يمكن لهذا التدفق دعم تطبيقات ذكاء اصطناعي متقدمة، تفاعلية، وواعية للسياق من خلال ربط النماذج بسلاسة مع الأدوات والبيانات الخارجية.

## تفاصيل البروتوكول

يُبنى MCP على [JSON-RPC 2.0](https://www.jsonrpc.org/)، مقدّمًا تنسيق رسائل موحد وغير خاص بلغة معينة للتواصل بين المضيفين، العملاء، والخوادم. هذا الأساس يتيح تفاعلات موثوقة، منظمة، وقابلة للتوسيع عبر منصات ولغات برمجة متنوعة.

### ميزات البروتوكول الرئيسية

يوسع MCP JSON-RPC 2.0 باتفاقيات إضافية لاستدعاء الأدوات، الوصول إلى الموارد، وإدارة التعليمات. يدعم طبقات نقل متعددة (STDIO، WebSocket، SSE) ويمكّن اتصالًا آمنًا، قابلًا للتوسيع، وغير خاص بلغة بين المكونات.

#### 🧢 البروتوكول الأساسي

- **تنسيق رسائل JSON-RPC**: جميع الطلبات والردود تستخدم مواصفة JSON-RPC 2.0، مما يضمن هيكلًا متسقًا لاستدعاءات الطرق، المعلمات، النتائج، ومعالجة الأخطاء.
- **اتصالات حالة مستمرة**: تحافظ جلسات MCP على الحالة عبر طلبات متعددة، داعمة المحادثات المستمرة، تراكم السياق، وإدارة الموارد.
- **التفاوض على القدرات**: خلال إعداد الاتصال، يتبادل العملاء والخوادم معلومات حول الميزات المدعومة، إصدارات البروتوكول، الأدوات، والموارد المتاحة. يضمن هذا فهم الطرفين لقدرات بعضهما البعض والتكيف بناءً عليها.

#### ➕ أدوات إضافية

فيما يلي بعض الأدوات والامتدادات التي يوفرها MCP لتعزيز تجربة المطور وتمكين سيناريوهات متقدمة:

- **خيارات التكوين**: يسمح MCP بتكوين ديناميكي لمعلمات الجلسة، مثل أذونات الأدوات، الوصول إلى الموارد، وإعدادات النموذج، مخصصة لكل تفاعل.
- **تتبع التقدم**: يمكن للعمليات طويلة الأمد الإبلاغ عن تحديثات التقدم، مما يتيح واجهات مستخدم استجابية وتجربة مستخدم أفضل أثناء المهام المعقدة.
- **إلغاء الطلبات**: يمكن للعملاء إلغاء الطلبات الجارية، مما يسمح للمستخدمين بوقف العمليات غير الضرورية أو التي تستغرق وقتًا طويلاً.
- **تقرير الأخطاء**: رسائل وأكواد أخطاء موحدة تساعد في تشخيص المشكلات، التعامل مع الفشل بسلاسة، وتوفير ملاحظات قابلة للتنفيذ للمستخدمين والمطورين.
- **التسجيل**: يمكن لكل من العملاء والخوادم إصدار سجلات منظمة لأغراض التدقيق، التصحيح، ومراقبة التفاعلات البروتوكولية.

باستخدام هذه الميزات، يضمن MCP اتصالًا قويًا، آمنًا، ومرنًا بين نماذج اللغة والأدوات أو مصادر البيانات الخارجية.

### 🔐 اعتبارات الأمان

يجب أن تلتزم تطبيقات MCP بعدة مبادئ أمنية رئيسية لضمان تفاعلات آمنة وموثوقة:

- **موافقة المستخدم والتحكم**: يجب أن يقدم المستخدمون موافقة صريحة قبل الوصول إلى أي بيانات أو تنفيذ أي عمليات. يجب أن يكون لديهم تحكم واضح في البيانات المشتركة والإجراءات المصرح بها، مدعومًا بواجهات مستخدم بديهية لمراجعة والموافقة على الأنشطة.

- **خصوصية البيانات**: يجب أن تُعرض بيانات المستخدم فقط بموافقته الصريحة ويجب حمايتها بضوابط وصول مناسبة. يجب على تطبيقات MCP حماية البيانات من النقل غير المصرح به وضمان الحفاظ على الخصوصية طوال التفاعلات.

- **سلامة الأدوات**: قبل استدعاء أي أداة، يجب الحصول على موافقة صريحة من المستخدم. يجب أن يكون لدى المستخدمين فهم واضح لوظيفة كل أداة، ويجب فرض حدود أمنية قوية لمنع تنفيذ الأدوات غير المقصود أو غير الآمن.

باتباع هذه المبادئ، يضمن MCP الحفاظ على ثقة المستخدم، خصوصيته، وسلامته عبر جميع تفاعلات البروتوكول.

## أمثلة على الشيفرة: المكونات الرئيسية

فيما يلي أمثلة برمجية بعدة لغات شائعة توضح كيفية تنفيذ مكونات خادم MCP الرئيسية والأدوات.

### مثال .NET: إنشاء خادم MCP بسيط مع أدوات

هنا مثال عملي باستخدام .NET يوضح كيفية تنفيذ خادم MCP بسيط مع أدوات مخصصة. يعرض هذا المثال كيفية تعريف وتسجيل الأدوات، معالجة الطلبات، وربط الخادم باستخدام بروتوكول سياق النموذج.

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

### مثال Java: مكونات خادم MCP

يوضح هذا المثال نفس خادم MCP وتسجيل الأدوات كما في مثال .NET أعلاه، لكنه منفذ بلغة Java.

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

### مثال Python: بناء خادم MCP

في هذا المثال نعرض كيفية بناء خادم MCP باستخدام Python. كما نعرض طريقتين مختلفتين لإنشاء الأدوات.

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

### مثال JavaScript: إنشاء خادم MCP

يعرض هذا المثال إنشاء خادم MCP باستخدام JavaScript وكيفية تسجيل أداتين مرتبطتين بالطقس.

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

يُظهر هذا المثال في JavaScript كيفية إنشاء عميل MCP يتصل بخادم، يرسل مطالبة، ويعالج الرد بما في ذلك أي نداءات للأدوات تم تنفيذها.

## الأمان والتفويض

يتضمن MCP عدة مفاهيم وآليات مدمجة لإدارة الأمان والتفويض طوال البروتوكول:

1. **التحكم في أذونات الأدوات**  
   يمكن للعملاء تحديد الأدوات التي يُسمح للنموذج باستخدامها خلال الجلسة. يضمن هذا الوصول فقط للأدوات المصرح بها صراحة، مما يقلل من خطر العمليات غير المقصودة أو غير الآمنة. يمكن تكوين الأذونات ديناميكيًا بناءً على تفضيلات المستخدم، سياسات المؤسسة، أو سياق التفاعل.

2. **المصادقة**  
   يمكن للخوادم طلب المصادقة قبل منح الوصول إلى الأدوات، الموارد، أو العمليات الحساسة. قد يشمل ذلك مفاتيح API، رموز OAuth، أو أنظمة مصادقة أخرى. تضمن المصادقة الصحيحة أن العملاء والمستخدمين الموثوقين فقط يمكنهم استدعاء قدرات الخادم.

3. **التحقق**  
   يتم فرض التحقق من المعلمات لجميع استدعاءات الأدوات. تعرف كل أداة أنواع، صيغ، وقيود المعلمات المتوقعة، ويقوم الخادم بالتحقق من الطلبات الواردة وفقًا لذلك. يمنع هذا الإدخال غير الصحيح أو الخبيث من الوصول إلى تنفيذ الأدوات ويساعد في الحفاظ على سلامة العمليات.

4. **تحديد المعدل**  
   لمنع سوء الاستخدام وضمان الاستخدام العادل لموارد الخادم، يمكن لخوادم MCP تنفيذ تحديد معدل لاستدعاءات الأدوات والوصول إلى الموارد. يمكن تطبيق حدود المعدل لكل مستخدم، لكل جلسة، أو على المستوى العالمي، وتساعد في الحماية من هجمات الحرمان من الخدمة أو الاستهلاك المفرط للموارد.

بدمج هذه الآليات، يوفر MCP أساسًا آمنًا لتكامل نماذج اللغة مع الأدوات ومصادر البيانات الخارجية، مع منح المستخدمين والمطورين تحكمًا دقيقًا في الوصول والاستخدام.

## رسائل البروتوكول

يستخدم MCP رسائل JSON منظمة لتسهيل تفاعلات واضحة وموثوقة بين العملاء، الخوادم، والنماذج. تشمل أنواع الرسائل الرئيسية:

- **طلب العميل**  
  يُرسل من العميل إلى الخادم، ويتضمن عادةً:
  - مطالبة أو أمر المستخدم
  - سجل المحادثة للسياق
  - تكوين الأداة والأذونات
  - أي بيانات وصفية إضافية أو معلومات الجلسة

- **رد النموذج**  
  يُعاد من النموذج (عبر العميل)، ويحتوي على:
  - نص مولد أو استكمال بناءً على المطالبة والسياق
  - تعليمات استدعاء أداة اختيارية إذا قرر النموذج استدعاء أداة
  - مراجع إلى الموارد أو سياق إضافي حسب الحاجة

- **طلب الأداة**  
  يُرسل من العميل إلى الخادم عندما يلزم تنفيذ أداة. تتضمن هذه الرسالة:
  - اسم الأداة المطلوب استدعاؤها
  - المعلمات المطلوبة للأداة (تم التحقق منها وفقًا لمخطط الأداة)
  - معلومات سياقية أو معرفات لتتبع الطلب

- **رد الأداة**  
  يُعاد من الخادم بعد تنفيذ

**إخلاء المسؤولية**:  
تمت ترجمة هذا المستند باستخدام خدمة الترجمة الآلية [Co-op Translator](https://github.com/Azure/co-op-translator). بينما نسعى جاهدين للدقة، يرجى العلم أن الترجمات الآلية قد تحتوي على أخطاء أو عدم دقة. يجب اعتبار المستند الأصلي بلغته الأصلية المصدر الموثوق به. للمعلومات الحساسة، يُنصح بالاعتماد على الترجمة البشرية المهنية. نحن غير مسؤولين عن أي سوء فهم أو تفسير ناتج عن استخدام هذه الترجمة.