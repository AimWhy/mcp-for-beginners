<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "154c00dc3b2c792102e4845c19fbd166",
  "translation_date": "2025-05-20T15:48:34+00:00",
  "source_file": "01-CoreConcepts/README.md",
  "language_code": "ar"
}
-->
# 📖 مفاهيم أساسية في MCP: إتقان بروتوكول سياق النموذج لتكامل الذكاء الاصطناعي

بروتوكول سياق النموذج (MCP) هو إطار عمل قوي وموحد يعمل على تحسين التواصل بين نماذج اللغة الكبيرة (LLMs) والأدوات الخارجية، التطبيقات، ومصادر البيانات. سيرشدك هذا الدليل المحسّن لمحركات البحث خلال المفاهيم الأساسية لـ MCP، لضمان فهمك لهندسة العميل-الخادم، المكونات الأساسية، آليات الاتصال، وأفضل ممارسات التنفيذ.

## نظرة عامة

تستعرض هذه الدرس الهندسة الأساسية والمكونات التي تشكل نظام بروتوكول سياق النموذج (MCP). ستتعرف على هندسة العميل-الخادم، المكونات الرئيسية، وآليات الاتصال التي تدعم تفاعلات MCP.

## 👩‍🎓 أهداف التعلم الرئيسية

بنهاية هذا الدرس، ستكون قادرًا على:

- فهم هندسة العميل-الخادم في MCP.
- تحديد أدوار ومسؤوليات المضيفين، العملاء، والخوادم.
- تحليل الميزات الأساسية التي تجعل MCP طبقة تكامل مرنة.
- التعرف على كيفية تدفق المعلومات داخل نظام MCP.
- اكتساب رؤى عملية من خلال أمثلة برمجية في .NET، Java، Python، وJavaScript.

## 🔎 هندسة MCP: نظرة معمقة

يبنى نظام MCP على نموذج العميل-الخادم. تتيح هذه البنية المودولية لتطبيقات الذكاء الاصطناعي التفاعل مع الأدوات، قواعد البيانات، واجهات برمجة التطبيقات، والموارد السياقية بكفاءة. دعنا نحلل هذه الهندسة إلى مكوناتها الأساسية.

### 1. المضيفون

في بروتوكول سياق النموذج (MCP)، يلعب المضيفون دورًا حيويًا كواجهة رئيسية يتفاعل من خلالها المستخدمون مع البروتوكول. المضيفون هم تطبيقات أو بيئات تبدأ الاتصالات مع خوادم MCP للوصول إلى البيانات، الأدوات، والتعليمات. من أمثلة المضيفين بيئات تطوير متكاملة مثل Visual Studio Code، أدوات ذكاء اصطناعي مثل Claude Desktop، أو وكلاء مخصصون مصممون لمهام معينة.

**المضيفون** هم تطبيقات LLM تبدأ الاتصالات. وهم:

- ينفذون أو يتفاعلون مع نماذج الذكاء الاصطناعي لتوليد الردود.
- يبدأون الاتصالات مع خوادم MCP.
- يديرون سير المحادثة وواجهة المستخدم.
- يتحكمون في أذونات الأمان والقيود.
- يتعاملون مع موافقة المستخدم لمشاركة البيانات وتنفيذ الأدوات.

### 2. العملاء

العملاء هم مكونات أساسية تسهل التفاعل بين المضيفين وخوادم MCP. يعمل العملاء كوسطاء، مما يمكن المضيفين من الوصول إلى واستخدام الوظائف التي توفرها خوادم MCP. يلعبون دورًا حاسمًا في ضمان التواصل السلس وتبادل البيانات بكفاءة ضمن هندسة MCP.

**العملاء** هم موصلات داخل تطبيق المضيف. وهم:

- يرسلون طلبات إلى الخوادم مع التعليمات أو المطالبات.
- يتفاوضون على القدرات مع الخوادم.
- يديرون طلبات تنفيذ الأدوات من النماذج.
- يعالجون ويعرضون الردود للمستخدمين.

### 3. الخوادم

الخوادم مسؤولة عن معالجة الطلبات من عملاء MCP وتقديم الردود المناسبة. تدير عمليات متنوعة مثل استرجاع البيانات، تنفيذ الأدوات، وتوليد التعليمات. تضمن الخوادم أن يكون الاتصال بين العملاء والمضيفين فعالًا وموثوقًا، مع الحفاظ على سلامة عملية التفاعل.

**الخوادم** هي خدمات توفر السياق والقدرات. وهي:

- تسجل الميزات المتاحة (الموارد، التعليمات، الأدوات)
- تستقبل وتنفذ استدعاءات الأدوات من العميل
- توفر معلومات سياقية لتعزيز ردود النموذج
- تعيد النتائج إلى العميل
- تحافظ على الحالة عبر التفاعلات عند الحاجة

يمكن لأي شخص تطوير الخوادم لتوسيع قدرات النموذج بوظائف متخصصة.

### 4. ميزات الخادم

تقدم خوادم MCP اللبنات الأساسية التي تمكن التفاعلات الغنية بين العملاء، المضيفين، ونماذج اللغة. صممت هذه الميزات لتعزيز قدرات MCP من خلال تقديم سياق منظم، أدوات، وتعليمات.

يمكن لخوادم MCP تقديم أي من الميزات التالية:

#### 📑 الموارد

تشمل الموارد في MCP أنواعًا مختلفة من السياق والبيانات التي يمكن للمستخدمين أو نماذج الذكاء الاصطناعي استخدامها. وتتضمن:

- **البيانات السياقية**: المعلومات والسياق التي يمكن للمستخدمين أو النماذج الاعتماد عليها لاتخاذ القرارات وتنفيذ المهام.
- **قواعد المعرفة ومستودعات الوثائق**: مجموعات من البيانات المنظمة وغير المنظمة، مثل المقالات، الكتيبات، والأبحاث التي توفر رؤى ومعلومات قيمة.
- **الملفات وقواعد البيانات المحلية**: البيانات المخزنة محليًا على الأجهزة أو ضمن قواعد البيانات، متاحة للمعالجة والتحليل.
- **واجهات برمجة التطبيقات والخدمات الإلكترونية**: الواجهات والخدمات الخارجية التي توفر بيانات ووظائف إضافية، مما يتيح التكامل مع موارد وأدوات عبر الإنترنت.

مثال على مورد يمكن أن يكون مخطط قاعدة بيانات أو ملف يمكن الوصول إليه كما يلي:

```text
file://log.txt
database://schema
```

### 🤖 التعليمات

تشمل التعليمات في MCP قوالب ونماذج تفاعل محددة مسبقًا تهدف إلى تبسيط سير عمل المستخدم وتحسين التواصل. وتتضمن:

- **رسائل وقوالب سير عمل مُنظمة مسبقًا**: رسائل وعمليات مهيكلة توجه المستخدمين خلال مهام وتفاعلات محددة.
- **أنماط تفاعل محددة مسبقًا**: تسلسلات موحدة من الإجراءات والردود تسهل التواصل المتسق والفعال.
- **قوالب محادثة متخصصة**: قوالب قابلة للتخصيص مصممة لأنواع محددة من المحادثات، لضمان تفاعلات ذات صلة وسياق مناسب.

يمكن أن تبدو قالب تعليمات كما يلي:

```markdown
Generate a product slogan based on the following {{product}} with the following {{keywords}}
```

#### ⛏️ الأدوات

الأدوات في MCP هي وظائف يمكن للنموذج الذكي تنفيذها لأداء مهام محددة. صممت هذه الأدوات لتعزيز قدرات النموذج من خلال توفير عمليات منظمة وموثوقة. الجوانب الرئيسية تشمل:

- **وظائف ينفذها نموذج الذكاء الاصطناعي**: الأدوات هي وظائف قابلة للتنفيذ يمكن للنموذج استدعاؤها لأداء مهام مختلفة.
- **اسم ووصف فريد**: لكل أداة اسم مميز ووصف تفصيلي يشرح هدفها ووظيفتها.
- **المعلمات والمخرجات**: تقبل الأدوات معلمات محددة وتُرجع مخرجات منظمة لضمان نتائج متسقة ومتوقعة.
- **وظائف منفصلة**: تؤدي الأدوات وظائف منفصلة مثل البحث على الويب، الحسابات، واستعلامات قواعد البيانات.

يمكن أن يبدو مثال على أداة كما يلي:

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

## ميزات العملاء

في MCP، يقدم العملاء عدة ميزات رئيسية للخوادم، مما يعزز الوظائف العامة والتفاعل داخل البروتوكول. من الميزات الملحوظة هي Sampling.

### 👉 Sampling

- **سلوكيات وكيل مُبادرة من الخادم**: تمكّن العملاء الخوادم من بدء إجراءات أو سلوكيات معينة بشكل مستقل، مما يعزز القدرات الديناميكية للنظام.
- **تفاعلات LLM متكررة**: تتيح هذه الميزة التفاعلات المتكررة مع نماذج اللغة الكبيرة (LLMs)، مما يمكن من معالجة أكثر تعقيدًا وتكرارية للمهام.
- **طلب إكمالات إضافية من النموذج**: يمكن للخوادم طلب إكمالات إضافية من النموذج، لضمان أن تكون الردود شاملة وذات صلة سياقية.

## تدفق المعلومات في MCP

يعرف MCP تدفقًا منظمًا للمعلومات بين المضيفين، العملاء، الخوادم، والنماذج. يساعد فهم هذا التدفق على توضيح كيفية معالجة طلبات المستخدم وكيفية دمج الأدوات والبيانات الخارجية في ردود النموذج.

- **المضيف يبدأ الاتصال**  
  يقوم تطبيق المضيف (مثل بيئة تطوير متكاملة أو واجهة دردشة) بإنشاء اتصال بخادم MCP، عادة عبر STDIO، WebSocket، أو وسيلة نقل مدعومة أخرى.

- **التفاوض على القدرات**  
  يتبادل العميل (المدمج في المضيف) والخادم معلومات حول الميزات، الأدوات، الموارد، وإصدارات البروتوكول المدعومة. هذا يضمن فهم الطرفين للقدرات المتاحة للجلسة.

- **طلب المستخدم**  
  يتفاعل المستخدم مع المضيف (مثل إدخال مطالبة أو أمر). يجمع المضيف هذا الإدخال ويمرره إلى العميل للمعالجة.

- **استخدام الموارد أو الأدوات**  
  - قد يطلب العميل سياقًا إضافيًا أو موارد من الخادم (مثل ملفات، مدخلات قواعد بيانات، أو مقالات قاعدة معرفة) لتعزيز فهم النموذج.
  - إذا قرر النموذج أن أداة مطلوبة (مثل جلب بيانات، إجراء حساب، أو استدعاء API)، يرسل العميل طلب استدعاء أداة إلى الخادم، محددًا اسم الأداة والمعلمات.

- **تنفيذ الخادم**  
  يستقبل الخادم طلب المورد أو الأداة، ينفذ العمليات اللازمة (مثل تشغيل وظيفة، استعلام قاعدة بيانات، أو استرجاع ملف)، ويعيد النتائج إلى العميل بصيغة منظمة.

- **توليد الرد**  
  يدمج العميل ردود الخادم (بيانات الموارد، مخرجات الأدوات، إلخ) في التفاعل الجاري مع النموذج. يستخدم النموذج هذه المعلومات لتوليد رد شامل وذو صلة سياقية.

- **عرض النتيجة**  
  يستقبل المضيف المخرجات النهائية من العميل ويعرضها للمستخدم، غالبًا متضمنة نص النموذج المُولد وأي نتائج من تنفيذ الأدوات أو استرجاع الموارد.

يمكن لهذا التدفق أن يدعم تطبيقات ذكاء اصطناعي متقدمة، تفاعلية، وواعية للسياق من خلال ربط النماذج بسلاسة مع الأدوات الخارجية ومصادر البيانات.

## تفاصيل البروتوكول

يبنى MCP على [JSON-RPC 2.0](https://www.jsonrpc.org/)، موفرًا صيغة رسائل موحدة وغير مرتبطة بلغة معينة للتواصل بين المضيفين، العملاء، والخوادم. تمكّن هذه القاعدة التفاعلات الموثوقة، المنظمة، والقابلة للتوسيع عبر منصات ولغات برمجة متنوعة.

### ميزات البروتوكول الرئيسية

يمتد MCP على JSON-RPC 2.0 بإضافة اتفاقيات لاستدعاء الأدوات، الوصول إلى الموارد، وإدارة التعليمات. يدعم عدة طبقات نقل (STDIO، WebSocket، SSE) ويتيح تواصلًا آمنًا، قابلًا للتوسيع، وغير مرتبط بلغة محددة بين المكونات.

#### 🧢 البروتوكول الأساسي

- **صيغة رسالة JSON-RPC**: جميع الطلبات والردود تستخدم مواصفة JSON-RPC 2.0، مما يضمن هيكلًا متسقًا لاستدعاءات الطرق، المعلمات، النتائج، والتعامل مع الأخطاء.
- **اتصالات ذات حالة**: تحافظ جلسات MCP على الحالة عبر طلبات متعددة، داعمة المحادثات المستمرة، تراكم السياق، وإدارة الموارد.
- **التفاوض على القدرات**: أثناء إعداد الاتصال، يتبادل العملاء والخوادم معلومات حول الميزات المدعومة، إصدارات البروتوكول، الأدوات، والموارد المتاحة. هذا يضمن فهم الطرفين لقدرات بعضهما البعض والتكيف وفقًا لذلك.

#### ➕ أدوات إضافية

فيما يلي بعض الأدوات والامتدادات البروتوكولية التي يقدمها MCP لتحسين تجربة المطور وتمكين السيناريوهات المتقدمة:

- **خيارات التكوين**: يسمح MCP بتكوين ديناميكي لمعلمات الجلسة، مثل أذونات الأدوات، الوصول إلى الموارد، وإعدادات النموذج، مخصصة لكل تفاعل.
- **تتبع التقدم**: يمكن للعمليات طويلة الأمد الإبلاغ عن تحديثات التقدم، مما يمكن واجهات المستخدم من الاستجابة وتحسين تجربة المستخدم أثناء المهام المعقدة.
- **إلغاء الطلبات**: يمكن للعملاء إلغاء الطلبات الجارية، مما يسمح للمستخدمين بقطع العمليات غير المرغوب فيها أو التي تستغرق وقتًا طويلاً.
- **الإبلاغ عن الأخطاء**: رسائل وأكواد خطأ موحدة تساعد في تشخيص المشاكل، التعامل مع الإخفاقات بسلاسة، وتوفير ملاحظات قابلة للتنفيذ للمستخدمين والمطورين.
- **التسجيل**: يمكن لكل من العملاء والخوادم إصدار سجلات منظمة للمراجعة، التصحيح، ومراقبة التفاعلات البروتوكولية.

من خلال الاستفادة من هذه الميزات، يضمن MCP تواصلًا قويًا، آمنًا، ومرنًا بين نماذج اللغة والأدوات أو مصادر البيانات الخارجية.

### 🔐 اعتبارات الأمان

يجب على تطبيقات MCP الالتزام بعدة مبادئ أمنية رئيسية لضمان تفاعلات آمنة وموثوقة:

- **موافقة المستخدم والتحكم**: يجب أن يقدم المستخدمون موافقة صريحة قبل الوصول إلى أي بيانات أو تنفيذ أي عمليات. ينبغي أن يكون لديهم تحكم واضح فيما يتم مشاركته وما هي الإجراءات المصرح بها، مدعومًا بواجهات مستخدم بديهية لمراجعة والموافقة على الأنشطة.

- **خصوصية البيانات**: يجب الكشف عن بيانات المستخدم فقط بموافقته الصريحة ويجب حمايتها بواسطة ضوابط وصول مناسبة. يجب على تطبيقات MCP الحماية من النقل غير المصرح به للبيانات وضمان الحفاظ على الخصوصية طوال جميع التفاعلات.

- **سلامة الأدوات**: قبل استدعاء أي أداة، يجب الحصول على موافقة صريحة من المستخدم. يجب أن يكون لدى المستخدمين فهم واضح لوظيفة كل أداة، ويجب فرض حدود أمان قوية لمنع تنفيذ الأدوات غير المقصود أو غير الآمن.

باتباع هذه المبادئ، يضمن MCP الحفاظ على ثقة المستخدم، الخصوصية، والسلامة عبر جميع التفاعلات البروتوكولية.

## أمثلة برمجية: المكونات الأساسية

فيما يلي أمثلة برمجية بعدة لغات برمجة شائعة توضح كيفية تنفيذ مكونات خادم MCP الرئيسية والأدوات.

### مثال .NET: إنشاء خادم MCP بسيط مع أدوات

هنا مثال عملي بلغة .NET يوضح كيفية تنفيذ خادم MCP بسيط مع أدوات مخصصة. يعرض هذا المثال كيفية تعريف الأدوات، تسجيلها، معالجة الطلبات، وربط الخادم باستخدام بروتوكول سياق النموذج.

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

يعرض هذا المثال نفس خادم MCP وتسجيل الأدوات كما في مثال .NET أعلاه، لكن تم تنفيذه بلغة Java.

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

في هذا المثال نوضح كيفية بناء خادم MCP بلغة Python. كما نعرض طريقتين مختلفتين لإنشاء الأدوات.

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

يعرض هذا المثال إنشاء خادم MCP بلغة JavaScript وكيفية تسجيل أداتين مرتبطتين بالطقس.

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

يوضح هذا المثال في JavaScript كيفية إنشاء عميل MCP يتصل بخادم، يرسل مطالبة، ويعالج الرد بما في ذلك أي استدعاءات أدوات تمت.

## الأمان والتفويض

يتضمن MCP عدة مفاهيم وآليات مدمجة لإدارة الأمان والتفويض عبر البروتوكول:

1. **التحكم في أذونات الأدوات**  
   يمكن للعملاء تحديد الأدوات التي يُسمح للنموذج باستخدامها خلال الجلسة. يضمن هذا أن تكون الأدوات المصرح بها فقط متاحة، مما يقلل من مخاطر العمليات غير المقصودة أو غير الآمنة. يمكن تكوين الأذونات ديناميكيًا بناءً على تفضيلات المستخدم، سياسات المؤسسة، أو سياق التفاعل.

2. **المصادقة**  
   يمكن للخوادم طلب المصادقة قبل منح الوصول إلى الأدوات، الموارد، أو العمليات الحساسة. قد يشمل ذلك مفاتيح API، رموز OAuth، أو أنظمة مصادقة أخرى. تضمن المصادقة الصحيحة أن العملاء والمستخدمين الموثوق بهم فقط يمكنهم استدعاء قدرات الخادم.

3. **التحقق**  
   يتم فرض التحقق من المعلمات لجميع استدعاءات الأدوات. تعرف كل أداة أنواع، صيغ، وقيود المعلمات المتوقعة، ويقوم الخادم بالتحقق من الطلبات الواردة وفقًا لذلك. يمنع هذا وصول إدخالات مشوهة أو خبيثة إلى تنفيذ الأدوات ويساعد في الحفاظ على سلامة العمليات.

4. **تحديد المعدل**  
   لمنع سوء الاستخدام وضمان الاستخدام العادل لموارد الخادم، يمكن لخوادم MCP تطبيق تحديد معدلات لاستدعاءات الأدوات والوصول إلى الموارد. يمكن تطبيق حدود المعدل لكل مستخدم، لكل جلسة، أو عالميًا، وتساعد في الحماية من هجمات حجب الخدمة أو استهلاك الموارد المفرط.

من خلال دمج هذه الآليات، يوفر MCP أساسًا آمنًا لتكامل نماذج اللغة مع الأدوات ومصادر البيانات الخارجية، مع منح المستخدمين والمطورين تحكمًا دقيقًا في الوصول والاستخدام.

## رسائل البروتوكول

يستخدم MCP رسائل JSON منظمة لتسهيل تفاعلات واضحة وموثوقة بين العملاء، الخوادم، والنماذج. تشمل أنواع الرسائل الرئيسية:

- **طلب العميل**  
  يُرسل من العميل إلى الخادم، ويشمل عادةً:
  - مطالبة المستخدم أو الأمر
  - سجل المحادثة للسياق
  - تكوين الأدوات والأذونات
  - أي بيانات وصفية إضافية أو معلومات الجلسة

- **رد النموذج**  
  يُعاد من النموذج (عبر العميل)، ويحتوي على:
  - نص مولد أو إكمال بناءً على المطالبة والسياق
  - تعليمات استدعاء أداة اختيارية إذا قرر النموذج استدعاء أداة
  - مراجع للموارد أو سياق إضافي حسب الحاجة

- **طلب الأداة**  
  يُرسل من العميل إلى الخادم عند الحاجة لتنفيذ أداة. تشمل الرسالة:
  - اسم الأداة المراد استدعاؤها
  - المعلمات المطلوبة للأداة (تم التحقق منها مقابل مخطط الأ

**تنويه**:  
تمت ترجمة هذا المستند باستخدام خدمة الترجمة الآلية [Co-op Translator](https://github.com/Azure/co-op-translator). بينما نسعى لتحقيق الدقة، يرجى العلم أن الترجمات الآلية قد تحتوي على أخطاء أو عدم دقة. يجب اعتبار المستند الأصلي بلغته الأصلية المصدر الموثوق به. للمعلومات الهامة، يُنصح بالترجمة الاحترافية البشرية. نحن غير مسؤولين عن أي سوء فهم أو تفسير ناتج عن استخدام هذه الترجمة.