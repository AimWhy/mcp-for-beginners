<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "f00defb149ee1ac4a799e44a9783c7fc",
  "translation_date": "2025-06-06T17:58:13+00:00",
  "source_file": "01-CoreConcepts/README.md",
  "language_code": "ar"
}
-->
# 📖 مفاهيم أساسية في MCP: إتقان بروتوكول سياق النموذج لتكامل الذكاء الاصطناعي

بروتوكول سياق النموذج (MCP) هو إطار قوي وموحد يُحسّن التواصل بين نماذج اللغة الكبيرة (LLMs) والأدوات الخارجية، والتطبيقات، ومصادر البيانات. سيرشدك هذا الدليل المحسّن لمحركات البحث عبر المفاهيم الأساسية لـ MCP، مع ضمان فهمك لهندسة العميل-الخادم، والمكونات الأساسية، وآليات التواصل، وأفضل ممارسات التنفيذ.

## نظرة عامة

تستكشف هذه الدرس الهندسة الأساسية والمكونات التي تشكل نظام بروتوكول سياق النموذج (MCP). ستتعرف على هندسة العميل-الخادم، والمكونات الرئيسية، وآليات التواصل التي تدعم تفاعلات MCP.

## 👩‍🎓 الأهداف التعليمية الرئيسية

بنهاية هذا الدرس، ستتمكن من:

- فهم هندسة العميل-الخادم في MCP.
- تحديد أدوار ومسؤوليات المضيفين، والعملاء، والخوادم.
- تحليل الميزات الأساسية التي تجعل MCP طبقة تكامل مرنة.
- تعلم كيفية تدفق المعلومات داخل نظام MCP.
- اكتساب رؤى عملية من خلال أمثلة برمجية في .NET، وجافا، وبايثون، وجافاسكريبت.

## 🔎 هندسة MCP: نظرة معمقة

يُبنى نظام MCP على نموذج العميل-الخادم. تتيح هذه البنية المعيارية لتطبيقات الذكاء الاصطناعي التفاعل بكفاءة مع الأدوات، وقواعد البيانات، وواجهات برمجة التطبيقات، والموارد السياقية. دعنا نفصل هذه الهندسة إلى مكوناتها الأساسية.

### 1. المضيفون

في بروتوكول سياق النموذج (MCP)، يلعب المضيفون دورًا حيويًا كواجهة رئيسية يتفاعل من خلالها المستخدمون مع البروتوكول. المضيفون هم تطبيقات أو بيئات تبدأ الاتصالات مع خوادم MCP للوصول إلى البيانات، والأدوات، والتعليمات. من أمثلة المضيفون بيئات التطوير المتكاملة مثل Visual Studio Code، وأدوات الذكاء الاصطناعي مثل Claude Desktop، أو وكلاء مخصصون مصممون لمهام معينة.

**المضيفون** هم تطبيقات LLM التي تبدأ الاتصالات. هم:

- ينفذون أو يتفاعلون مع نماذج الذكاء الاصطناعي لتوليد الردود.
- يبدأون الاتصالات مع خوادم MCP.
- يديرون سير المحادثة وواجهة المستخدم.
- يتحكمون في أذونات الأمان والقيود.
- يتعاملون مع موافقة المستخدم لمشاركة البيانات وتنفيذ الأدوات.

### 2. العملاء

يُعد العملاء مكونات أساسية تُسهل التفاعل بين المضيفين وخوادم MCP. يعمل العملاء كوسطاء، مما يمكّن المضيفين من الوصول إلى الوظائف التي توفرها خوادم MCP واستخدامها. يلعبون دورًا حيويًا في ضمان تواصل سلس وتبادل بيانات فعال داخل هندسة MCP.

**العملاء** هم موصلات داخل تطبيق المضيف. هم:

- يرسلون طلبات إلى الخوادم مع التعليمات/المطالبات.
- يتفاوضون على القدرات مع الخوادم.
- يديرون طلبات تنفيذ الأدوات من النماذج.
- يعالجون ويعرضون الردود للمستخدمين.

### 3. الخوادم

الخوادم مسؤولة عن معالجة طلبات عملاء MCP وتوفير الردود المناسبة. تدير عمليات مختلفة مثل استرجاع البيانات، وتنفيذ الأدوات، وتوليد التعليمات. تضمن الخوادم أن يكون التواصل بين العملاء والمضيفين فعالًا وموثوقًا، مع الحفاظ على سلامة عملية التفاعل.

**الخوادم** هي خدمات توفر السياق والقدرات. هي:

- تسجل الميزات المتاحة (الموارد، التعليمات، الأدوات).
- تستقبل وتنفذ استدعاءات الأدوات من العميل.
- توفر معلومات سياقية لتعزيز ردود النموذج.
- تعيد المخرجات إلى العميل.
- تحافظ على الحالة عبر التفاعلات عند الحاجة.

يمكن لأي شخص تطوير خوادم لتوسيع قدرات النموذج بوظائف متخصصة.

### 4. ميزات الخادم

توفر خوادم MCP لبنات أساسية تمكّن تفاعلات غنية بين العملاء، والمضيفين، ونماذج اللغة. صُممت هذه الميزات لتعزيز قدرات MCP من خلال تقديم سياق منظم، وأدوات، وتعليمات.

يمكن لخوادم MCP تقديم أي من الميزات التالية:

#### 📑 الموارد

تشمل الموارد في بروتوكول سياق النموذج (MCP) أنواعًا مختلفة من السياقات والبيانات التي يمكن للمستخدمين أو نماذج الذكاء الاصطناعي الاستفادة منها. وتشمل:

- **البيانات السياقية**: معلومات وسياقات يمكن للمستخدمين أو النماذج استخدامها لاتخاذ القرارات وتنفيذ المهام.
- **قواعد المعرفة ومستودعات الوثائق**: مجموعات من البيانات المنظمة وغير المنظمة مثل المقالات، والكتيبات، والأبحاث التي توفر رؤى ومعلومات قيمة.
- **الملفات وقواعد البيانات المحلية**: بيانات مخزنة محليًا على الأجهزة أو ضمن قواعد بيانات، متاحة للمعالجة والتحليل.
- **واجهات برمجة التطبيقات والخدمات الشبكية**: واجهات وخدمات خارجية توفر بيانات ووظائف إضافية، مما يمكّن التكامل مع موارد وأدوات عبر الإنترنت.

مثال على مورد يمكن أن يكون مخطط قاعدة بيانات أو ملف يمكن الوصول إليه كما يلي:

```text
file://log.txt
database://schema
```

### 🤖 التعليمات

تشمل التعليمات في بروتوكول سياق النموذج (MCP) قوالب وأنماط تفاعل محددة مسبقًا تهدف إلى تبسيط سير العمل للمستخدمين وتعزيز التواصل. وتشمل:

- **الرسائل والقوالب المهيكلة مسبقًا**: رسائل وعمليات منظمة توجه المستخدمين خلال مهام وتفاعلات محددة.
- **أنماط التفاعل المحددة مسبقًا**: تسلسلات موحدة من الإجراءات والردود تسهل تواصلًا متسقًا وفعالًا.
- **قوالب محادثات متخصصة**: قوالب قابلة للتخصيص مصممة لأنواع معينة من المحادثات، لضمان تفاعلات ملائمة وسياقية.

يمكن أن يبدو قالب التعليمات كما يلي:

```markdown
Generate a product slogan based on the following {{product}} with the following {{keywords}}
```

#### ⛏️ الأدوات

الأدوات في بروتوكول سياق النموذج (MCP) هي وظائف يمكن للنموذج الذكي تنفيذها لأداء مهام محددة. صُممت هذه الأدوات لتعزيز قدرات النموذج من خلال توفير عمليات منظمة وموثوقة. الجوانب الرئيسية تشمل:

- **وظائف يمكن للنموذج تنفيذها**: أدوات قابلة للتنفيذ يمكن للنموذج استدعاؤها لأداء مهام متنوعة.
- **اسم ووصف فريدان**: لكل أداة اسم مميز ووصف مفصل يشرح هدفها ووظيفتها.
- **المعلمات والمخرجات**: تقبل الأدوات معلمات محددة وتعيد مخرجات منظمة لضمان نتائج متسقة ومتوقعة.
- **وظائف منفصلة**: تقوم الأدوات بوظائف محددة مثل البحث على الويب، الحسابات، واستعلامات قواعد البيانات.

يمكن أن تبدو أداة مثال كما يلي:

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

في بروتوكول سياق النموذج (MCP)، يقدم العملاء عدة ميزات رئيسية للخوادم، تعزز الوظائف العامة والتفاعل داخل البروتوكول. إحدى الميزات الملحوظة هي Sampling.

### 👉 Sampling

- **سلوكيات وكيل تبدأها الخوادم**: تمكن العملاء الخوادم من بدء إجراءات أو سلوكيات محددة بشكل مستقل، مما يعزز القدرات الديناميكية للنظام.
- **تفاعلات متكررة مع LLMs**: تتيح هذه الميزة تفاعلات متكررة مع نماذج اللغة الكبيرة، مما يمكّن معالجة أكثر تعقيدًا وتكرارية للمهام.
- **طلب إكمالات إضافية من النموذج**: يمكن للخوادم طلب إكمالات إضافية من النموذج، لضمان أن الردود شاملة وملائمة للسياق.

## تدفق المعلومات في MCP

يحدد بروتوكول سياق النموذج (MCP) تدفقًا منظمًا للمعلومات بين المضيفين، والعملاء، والخوادم، والنماذج. يساعد فهم هذا التدفق على توضيح كيفية معالجة طلبات المستخدم وكيفية دمج الأدوات والبيانات الخارجية في ردود النموذج.

- **المضيف يبدأ الاتصال**  
  يقوم تطبيق المضيف (مثل بيئة تطوير متكاملة أو واجهة دردشة) بإنشاء اتصال مع خادم MCP، عادة عبر STDIO، WebSocket، أو أي وسيلة نقل مدعومة أخرى.

- **التفاوض على القدرات**  
  يتبادل العميل (المضمن في المضيف) والخادم معلومات حول الميزات، والأدوات، والموارد، وإصدارات البروتوكول المدعومة. هذا يضمن فهم الطرفين للقدرات المتاحة للجلسة.

- **طلب المستخدم**  
  يتفاعل المستخدم مع المضيف (مثل إدخال تعليمات أو أمر). يجمع المضيف هذا الإدخال ويمرره إلى العميل للمعالجة.

- **استخدام مورد أو أداة**  
  - قد يطلب العميل سياقًا إضافيًا أو موارد من الخادم (مثل ملفات، سجلات قاعدة بيانات، أو مقالات قاعدة معرفة) لتعزيز فهم النموذج.
  - إذا قرر النموذج أن أداة مطلوبة (مثل جلب بيانات، إجراء حساب، أو استدعاء API)، يرسل العميل طلب استدعاء الأداة إلى الخادم مع تحديد اسم الأداة والمعلمات.

- **تنفيذ الخادم**  
  يستلم الخادم طلب المورد أو الأداة، وينفذ العمليات اللازمة (مثل تشغيل وظيفة، استعلام قاعدة بيانات، أو استرجاع ملف)، ويعيد النتائج إلى العميل بصيغة منظمة.

- **توليد الرد**  
  يدمج العميل ردود الخادم (بيانات الموارد، مخرجات الأدوات، إلخ) في التفاعل الجاري مع النموذج. يستخدم النموذج هذه المعلومات لتوليد رد شامل وملائم للسياق.

- **عرض النتيجة**  
  يستلم المضيف المخرجات النهائية من العميل ويعرضها للمستخدم، غالبًا متضمنة نص النموذج المُولد وأي نتائج من تنفيذ الأدوات أو البحث في الموارد.

يمكن لهذا التدفق أن يدعم تطبيقات ذكاء اصطناعي متقدمة، تفاعلية، وواعية للسياق من خلال ربط النماذج بسلاسة مع الأدوات والبيانات الخارجية.

## تفاصيل البروتوكول

يبنى MCP (بروتوكول سياق النموذج) على [JSON-RPC 2.0](https://www.jsonrpc.org/)، مما يوفر صيغة رسائل موحدة وغير مرتبطة بلغة معينة للتواصل بين المضيفين، والعملاء، والخوادم. يتيح هذا الأساس تفاعلات موثوقة، منظمة، وقابلة للتوسيع عبر منصات ولغات برمجة متنوعة.

### ميزات البروتوكول الرئيسية

يوسع MCP JSON-RPC 2.0 مع اتفاقيات إضافية لاستدعاء الأدوات، والوصول إلى الموارد، وإدارة التعليمات. يدعم عدة طبقات نقل (STDIO، WebSocket، SSE) ويتيح تواصلًا آمنًا، قابلًا للتوسيع، وغير مرتبط بلغة بين المكونات.

#### 🧢 البروتوكول الأساسي

- **صيغة رسالة JSON-RPC**: تستخدم جميع الطلبات والردود مواصفة JSON-RPC 2.0، مما يضمن هيكلًا متسقًا لاستدعاءات الطرق، والمعلمات، والنتائج، والتعامل مع الأخطاء.
- **اتصالات حالة الحالة**: تحافظ جلسات MCP على الحالة عبر طلبات متعددة، داعمة المحادثات المستمرة، تراكم السياق، وإدارة الموارد.
- **التفاوض على القدرات**: أثناء إعداد الاتصال، يتبادل العملاء والخوادم معلومات حول الميزات المدعومة، إصدارات البروتوكول، الأدوات المتاحة، والموارد. هذا يضمن فهم الطرفين لقدرات بعضهما البعض والقدرة على التكيف.

#### ➕ أدوات مساعدة إضافية

فيما يلي بعض الأدوات الإضافية وامتدادات البروتوكول التي يوفرها MCP لتعزيز تجربة المطور وتمكين سيناريوهات متقدمة:

- **خيارات التكوين**: يسمح MCP بتكوين ديناميكي لمعلمات الجلسة، مثل أذونات الأدوات، الوصول إلى الموارد، وإعدادات النموذج، مصممة لكل تفاعل.
- **تتبع التقدم**: يمكن للعمليات طويلة الأمد تقديم تحديثات تقدم، مما يمكّن واجهات مستخدم تفاعلية وتجربة أفضل أثناء المهام المعقدة.
- **إلغاء الطلبات**: يمكن للعملاء إلغاء الطلبات الجارية، مما يسمح للمستخدمين بوقف العمليات غير الضرورية أو التي تستغرق وقتًا طويلاً.
- **الإبلاغ عن الأخطاء**: تساعد رسائل وأكواد الخطأ الموحدة في تشخيص المشكلات، التعامل مع الفشل بسلاسة، وتوفير ملاحظات قابلة للتنفيذ للمستخدمين والمطورين.
- **التسجيل**: يمكن لكل من العملاء والخوادم إصدار سجلات منظمة لأغراض التدقيق، وتصحيح الأخطاء، ومراقبة تفاعلات البروتوكول.

باستخدام هذه الميزات، يضمن MCP تواصلًا قويًا، آمنًا، ومرنًا بين نماذج اللغة والأدوات أو مصادر البيانات الخارجية.

### 🔐 اعتبارات الأمان

يجب على تطبيقات MCP الالتزام بعدة مبادئ أمنية رئيسية لضمان تفاعلات آمنة وموثوقة:

- **موافقة المستخدم والتحكم**: يجب أن يقدم المستخدمون موافقة صريحة قبل الوصول إلى أي بيانات أو تنفيذ أي عمليات. يجب أن يكون لديهم تحكم واضح فيما يتم مشاركته من بيانات وما هي الإجراءات المصرح بها، مدعومة بواجهات مستخدم بديهية لمراجعة واعتماد الأنشطة.

- **خصوصية البيانات**: يجب الكشف عن بيانات المستخدم فقط بموافقة صريحة ويجب حمايتها من خلال ضوابط وصول مناسبة. يجب على تطبيقات MCP الحماية من نقل البيانات غير المصرح به وضمان الحفاظ على الخصوصية خلال جميع التفاعلات.

- **سلامة الأدوات**: قبل استدعاء أي أداة، يجب الحصول على موافقة صريحة من المستخدم. يجب أن يكون لدى المستخدمين فهم واضح لوظائف كل أداة، ويجب فرض حدود أمنية قوية لمنع تنفيذ الأدوات غير المقصود أو غير الآمن.

باتباع هذه المبادئ، يضمن MCP الحفاظ على ثقة المستخدم، وخصوصيته، وسلامته عبر جميع تفاعلات البروتوكول.

## أمثلة على الكود: المكونات الأساسية

فيما يلي أمثلة برمجية بعدة لغات برمجة شهيرة توضح كيفية تنفيذ مكونات خادم MCP الرئيسية والأدوات.

### مثال .NET: إنشاء خادم MCP بسيط مع أدوات

هنا مثال عملي في .NET يوضح كيفية تنفيذ خادم MCP بسيط مع أدوات مخصصة. يعرض هذا المثال كيفية تعريف الأدوات وتسجيلها، التعامل مع الطلبات، وربط الخادم باستخدام بروتوكول سياق النموذج.

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

### مثال جافا: مكونات خادم MCP

يوضح هذا المثال نفس خادم MCP وتسجيل الأدوات كما في مثال .NET أعلاه، لكنه مُنفذ بلغة جافا.

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

### مثال بايثون: بناء خادم MCP

في هذا المثال نعرض كيفية بناء خادم MCP في بايثون. كما نوضح طريقتين مختلفتين لإنشاء الأدوات.

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

# Instantiate the class to register its tools
weather_tools = WeatherTools()

# Start the server using stdio transport
if __name__ == "__main__":
    asyncio.run(serve_stdio(mcp))
```

### مثال جافاسكريبت: إنشاء خادم MCP

يعرض هذا المثال إنشاء خادم MCP باستخدام جافاسكريبت وكيفية تسجيل أداتين متعلقتين بالطقس.

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

يُظهر هذا المثال في جافاسكريبت كيفية إنشاء عميل MCP يتصل بالخادم، يرسل مطالبة، ويعالج الرد بما في ذلك أي استدعاءات أدوات تمت.

## الأمان والتفويض

يشمل MCP عدة مفاهيم وآليات مدمجة لإدارة الأمان والتفويض عبر البروتوكول:

1. **التحكم في أذونات الأدوات**:  
   يمكن للعملاء تحديد الأدوات التي يُسمح للنموذج باستخدامها خلال الجلسة. هذا يضمن أن الأدوات المصرح بها فقط متاحة، مما يقلل من خطر العمليات غير المقصودة أو غير الآمنة. يمكن تكوين الأذونات ديناميكيًا بناءً على تفضيلات المستخدم، سياسات المؤسسة، أو سياق التفاعل.

2. **المصادقة**:  
   يمكن للخوادم طلب المصادقة قبل منح الوصول إلى الأدوات، الموارد، أو العمليات الحساسة. قد يشمل ذلك مفاتيح API، رموز OAuth، أو أنظمة مصادقة أخرى. تضمن المصادقة الصحيحة أن العملاء والمستخدمين الموثوقين فقط يمكنهم استدعاء قدرات الخادم.

3. **التحقق**:  
   يُطبق التحقق على المعلمات لجميع استدعاءات الأدوات. تحدد كل أداة أنواع، صيغ، وقيود المعلمات المتوقعة، ويقوم الخادم بالتحقق من الطلبات الواردة وفقًا لذلك. يمنع هذا إدخال بيانات خاطئة أو خبيثة إلى تنفيذ الأدوات ويساعد في الحفاظ على سلامة العمليات.

4. **تحديد المعدل**:  
   لمنع سوء الاستخدام وضمان استخدام عادل لموارد الخادم، يمكن لخوادم MCP تطبيق تحديد معدل لاستدعاءات الأدوات والوصول إلى الموارد. يمكن تطبيق حدود المعدل لكل مستخدم، لكل جلسة، أو بشكل عام، وتساعد في الحماية من هجمات حجب الخدمة أو استهلاك الموارد المفرط.

من خلال دمج هذه الآليات، يوفر MCP أساسًا آمنًا لتكامل نماذج اللغة مع الأدوات ومصادر البيانات الخارجية، مع منح المستخدمين والمطورين تحكمًا دقيقًا في الوصول والاستخدام.

## رسائل البروتوكول

يستخدم تواصل MCP رسائل JSON منظمة لتسهيل تفاعلات واضحة وموثوقة بين العملاء، والخوادم، والنماذج. تشمل أنواع الرسائل الرئيسية:

- **طلب العميل**  
  يُرسل من العميل إلى الخادم، وعادةً ما يتضمن:
  - مطالبة المستخدم أو الأمر
  - سجل المحادثة للسياق
  - تكوين الأداة والأذونات
  - أي بيانات وصفية إضافية أو معلومات الجلسة

- **رد النموذج**  
  يُعاد من النموذج (عبر العميل)، ويحتوي على:
  - نص مولد أو إكمال بناءً على المطال

**إخلاء المسؤولية**:  
تمت ترجمة هذا المستند باستخدام خدمة الترجمة الآلية [Co-op Translator](https://github.com/Azure/co-op-translator). بينما نسعى لتحقيق الدقة، يرجى العلم أن الترجمات الآلية قد تحتوي على أخطاء أو عدم دقة. يجب اعتبار المستند الأصلي بلغته الأصلية المصدر الموثوق به. بالنسبة للمعلومات الحساسة، يُنصح بالترجمة البشرية المهنية. نحن غير مسؤولين عن أي سوء فهم أو تفسير خاطئ ناتج عن استخدام هذه الترجمة.