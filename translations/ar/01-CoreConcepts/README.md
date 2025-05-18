<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "788eb17750e970a0bc3b5e7f2e99975b",
  "translation_date": "2025-05-18T14:55:09+00:00",
  "source_file": "01-CoreConcepts/README.md",
  "language_code": "ar"
}
-->
# 📖 مفاهيم أساسية في MCP: إتقان بروتوكول سياق النموذج لتكامل الذكاء الاصطناعي

بروتوكول سياق النموذج (MCP) هو إطار قوي وموحد يعمل على تحسين التواصل بين نماذج اللغة الكبيرة (LLMs) والأدوات والتطبيقات ومصادر البيانات الخارجية. سيرشدك هذا الدليل المحسن لتحسين محركات البحث عبر المفاهيم الأساسية لـ MCP، لضمان فهمك لهندسة العميل-الخادم، المكونات الأساسية، آليات الاتصال، وأفضل ممارسات التنفيذ.

## نظرة عامة

تستعرض هذه الدرس الهيكلية الأساسية والمكونات التي تشكل نظام بروتوكول سياق النموذج (MCP). ستتعرف على هندسة العميل-الخادم، المكونات الرئيسية، وآليات التواصل التي تدعم تفاعلات MCP.

## 👩‍🎓 الأهداف التعليمية الرئيسية

بنهاية هذا الدرس، ستتمكن من:

- فهم هندسة العميل-الخادم في MCP.
- التعرف على أدوار ومسؤوليات Hosts وClients وServers.
- تحليل الميزات الأساسية التي تجعل MCP طبقة تكامل مرنة.
- تعلم كيفية تدفق المعلومات داخل نظام MCP.
- اكتساب رؤى عملية من خلال أمثلة برمجية في .NET، Java، Python، وJavaScript.

## 🔎 هندسة MCP: نظرة معمقة

يُبنى نظام MCP على نموذج العميل-الخادم. تتيح هذه البنية المودولية لتطبيقات الذكاء الاصطناعي التفاعل بكفاءة مع الأدوات وقواعد البيانات وواجهات برمجة التطبيقات والموارد السياقية. دعونا نفصل هذه الهندسة إلى مكوناتها الأساسية.

### 1. Hosts

في بروتوكول سياق النموذج (MCP)، تلعب Hosts دورًا محوريًا كواجهة أساسية يتفاعل المستخدمون من خلالها مع البروتوكول. Hosts هي تطبيقات أو بيئات تبدأ الاتصالات مع خوادم MCP للوصول إلى البيانات والأدوات والتعليمات. من أمثلة Hosts بيئات التطوير المتكاملة (IDEs) مثل Visual Studio Code، وأدوات الذكاء الاصطناعي مثل Claude Desktop، أو وكلاء مخصصين مصممين لمهام محددة.

**Hosts** هي تطبيقات LLM التي تبدأ الاتصالات. تقوم بـ:

- تنفيذ أو التفاعل مع نماذج الذكاء الاصطناعي لتوليد الردود.
- بدء الاتصالات مع خوادم MCP.
- إدارة تدفق المحادثة وواجهة المستخدم.
- التحكم في أذونات الأمان والقيود.
- التعامل مع موافقة المستخدم لمشاركة البيانات وتنفيذ الأدوات.

### 2. Clients

يُعتبر Clients مكونات أساسية تسهل التفاعل بين Hosts وخوادم MCP. يعمل Clients كوسطاء، مما يمكّن Hosts من الوصول إلى واستخدام الوظائف التي توفرها خوادم MCP. يلعبون دورًا مهمًا في ضمان تواصل سلس وتبادل بيانات فعال داخل هندسة MCP.

**Clients** هم موصلات داخل تطبيق المضيف. يقومون بـ:

- إرسال الطلبات إلى الخوادم مع التعليمات/المطالبات.
- التفاوض على القدرات مع الخوادم.
- إدارة طلبات تنفيذ الأدوات من النماذج.
- معالجة وعرض الردود للمستخدمين.

### 3. Servers

يتولى Servers مسؤولية معالجة الطلبات الواردة من عملاء MCP وتقديم الردود المناسبة. يديرون عمليات مختلفة مثل استرجاع البيانات، تنفيذ الأدوات، وتوليد التعليمات. يضمن Servers أن يكون التواصل بين العملاء والمضيفين فعالًا وموثوقًا، مع الحفاظ على سلامة عملية التفاعل.

**Servers** هي خدمات توفر السياق والقدرات. تقوم بـ:

- تسجيل الميزات المتاحة (الموارد، التعليمات، الأدوات).
- استقبال وتنفيذ استدعاءات الأدوات من العميل.
- توفير المعلومات السياقية لتعزيز ردود النموذج.
- إعادة النتائج إلى العميل.
- الحفاظ على الحالة عبر التفاعلات عند الحاجة.

يمكن لأي شخص تطوير Servers لتوسيع قدرات النموذج بوظائف متخصصة.

### 4. ميزات الخادم

توفر خوادم MCP اللبنات الأساسية التي تمكّن التفاعلات الغنية بين العملاء والمضيفين ونماذج اللغة. صُممت هذه الميزات لتعزيز قدرات MCP من خلال تقديم سياق منظم، أدوات، وتعليمات.

يمكن لخوادم MCP تقديم أي من الميزات التالية:

#### 📑 الموارد

تشمل الموارد في MCP أنواعًا مختلفة من السياق والبيانات التي يمكن للمستخدمين أو نماذج الذكاء الاصطناعي استخدامها. تتضمن:

- **البيانات السياقية**: المعلومات والسياق التي يمكن للمستخدمين أو النماذج الاستفادة منها لاتخاذ القرارات وتنفيذ المهام.
- **قواعد المعرفة ومستودعات الوثائق**: مجموعات من البيانات المهيكلة وغير المهيكلة، مثل المقالات، الكتيبات، والأبحاث، التي توفر رؤى ومعلومات قيمة.
- **الملفات وقواعد البيانات المحلية**: بيانات مخزنة محليًا على الأجهزة أو ضمن قواعد بيانات، متاحة للمعالجة والتحليل.
- **واجهات برمجة التطبيقات والخدمات الشبكية**: واجهات وخدمات خارجية تقدم بيانات ووظائف إضافية، مما يتيح التكامل مع مصادر وأدوات عبر الإنترنت.

يمكن أن يكون مثال على مورد مخطط قاعدة بيانات أو ملف يمكن الوصول إليه كما يلي:

```text
file://log.txt
database://schema
```

### 🤖 التعليمات

تشمل التعليمات في MCP قوالب وأنماط تفاعل محددة مسبقًا تهدف إلى تبسيط سير عمل المستخدم وتحسين التواصل. تتضمن:

- **رسائل وقوالب سير عمل منظمة**: رسائل وعمليات مهيكلة مسبقًا توجه المستخدمين خلال مهام وتفاعلات محددة.
- **أنماط تفاعل محددة مسبقًا**: تسلسلات موحدة من الإجراءات والردود تسهل التواصل المتسق والفعال.
- **قوالب محادثة متخصصة**: قوالب قابلة للتخصيص مصممة لأنواع معينة من المحادثات لضمان تفاعلات ملائمة وسياقية.

يمكن أن تبدو قالب التعليمات كما يلي:

```markdown
Generate a product slogan based on the following {{product}} with the following {{keywords}}
```

#### ⛏️ الأدوات

الأدوات في MCP هي وظائف يمكن للنموذج تنفيذها لأداء مهام محددة. تهدف هذه الأدوات إلى تعزيز قدرات النموذج من خلال توفير عمليات منظمة وموثوقة. الجوانب الرئيسية تشمل:

- **وظائف يمكن للنموذج تنفيذها**: أدوات هي وظائف قابلة للتنفيذ يمكن للنموذج استدعاؤها لأداء مهام مختلفة.
- **اسم ووصف فريد**: لكل أداة اسم مميز ووصف مفصل يوضح غرضها ووظيفتها.
- **المعلمات والمخرجات**: تقبل الأدوات معلمات محددة وتعيد مخرجات منظمة لضمان نتائج متسقة ومتوقعة.
- **وظائف منفصلة**: تقوم الأدوات بوظائف مستقلة مثل البحث على الويب، الحسابات، واستعلامات قواعد البيانات.

يمكن أن يبدو مثال على أداة كما يلي:

```typescript
server.tool(
  "GetProducts"
  {
    pageSize: z.string().optional(),
    pageCount: z.string().optional()
  }, () => {
    // return results from API
  }
)
```

## ميزات العميل

في MCP، يقدم العملاء عدة ميزات رئيسية للخوادم، تعزز الوظائف والتفاعل داخل البروتوكول. من الميزات الملحوظة هي Sampling.

### 👉 Sampling

- **سلوكيات وكيل تبدأ من الخادم**: تمكّن العملاء الخوادم من بدء إجراءات أو سلوكيات محددة بشكل مستقل، مما يعزز القدرات الديناميكية للنظام.
- **تفاعلات متكررة مع LLM**: تسمح هذه الميزة بتفاعلات متكررة مع نماذج اللغة الكبيرة، مما يمكن من معالجة مهام أكثر تعقيدًا وتكرارًا.
- **طلب استكمالات إضافية للنموذج**: يمكن للخوادم طلب استكمالات إضافية من النموذج، لضمان أن الردود شاملة وذات صلة سياقية.

## تدفق المعلومات في MCP

يحدد بروتوكول سياق النموذج (MCP) تدفقًا منظمًا للمعلومات بين المضيفين، العملاء، الخوادم، والنماذج. يساعد فهم هذا التدفق على توضيح كيفية معالجة طلبات المستخدم وكيف يتم دمج الأدوات والبيانات الخارجية في ردود النموذج.

- **المضيف يبدأ الاتصال**  
  يثبت تطبيق المضيف (مثل IDE أو واجهة محادثة) اتصالًا بخادم MCP، عادة عبر STDIO، WebSocket، أو وسيلة نقل مدعومة أخرى.

- **التفاوض على القدرات**  
  يتبادل العميل (المضمن في المضيف) والخادم معلومات حول الميزات، الأدوات، الموارد، وإصدارات البروتوكول المدعومة. يضمن هذا فهم الطرفين للقدرات المتاحة للجلسة.

- **طلب المستخدم**  
  يتفاعل المستخدم مع المضيف (مثل إدخال مطالبة أو أمر). يجمع المضيف هذا الإدخال ويمرره إلى العميل للمعالجة.

- **استخدام الموارد أو الأدوات**  
  - قد يطلب العميل سياقًا إضافيًا أو موارد من الخادم (مثل ملفات، مدخلات قاعدة بيانات، أو مقالات قاعدة المعرفة) لتعزيز فهم النموذج.
  - إذا قرر النموذج أن أداة مطلوبة (مثل لجلب بيانات، إجراء حساب، أو استدعاء API)، يرسل العميل طلب استدعاء الأداة إلى الخادم، محددًا اسم الأداة والمعلمات.

- **تنفيذ الخادم**  
  يستقبل الخادم طلب المورد أو الأداة، ينفذ العمليات اللازمة (مثل تشغيل وظيفة، استعلام قاعدة بيانات، أو استرجاع ملف)، ويعيد النتائج إلى العميل بصيغة منظمة.

- **توليد الرد**  
  يدمج العميل ردود الخادم (بيانات الموارد، مخرجات الأدوات، إلخ) في التفاعل المستمر مع النموذج. يستخدم النموذج هذه المعلومات لتوليد رد شامل وذو صلة سياقية.

- **عرض النتيجة**  
  يستلم المضيف المخرجات النهائية من العميل ويعرضها للمستخدم، غالبًا متضمنة نص النموذج المولد وأي نتائج من تنفيذ الأدوات أو استعلامات الموارد.

يمكن لهذا التدفق دعم تطبيقات ذكاء اصطناعي متقدمة، تفاعلية، وواعية بالسياق من خلال ربط النماذج بسلاسة مع الأدوات والبيانات الخارجية.

## تفاصيل البروتوكول

يُبنى MCP على [JSON-RPC 2.0](https://www.jsonrpc.org/) ويوفر صيغة رسائل موحدة وغير مرتبطة بلغة معينة للتواصل بين المضيفين، العملاء، والخوادم. تتيح هذه القاعدة تفاعلات موثوقة ومنظمة وقابلة للتوسع عبر منصات ولغات برمجة متنوعة.

### الميزات الرئيسية للبروتوكول

يمتد MCP على JSON-RPC 2.0 مع اتفاقيات إضافية لاستدعاء الأدوات، الوصول إلى الموارد، وإدارة التعليمات. يدعم عدة طبقات نقل (STDIO، WebSocket، SSE) ويمكنه توفير اتصال آمن، قابل للتوسع، وغير مرتبط بلغة معينة بين المكونات.

#### 🧢 البروتوكول الأساسي

- **صيغة رسائل JSON-RPC**: تستخدم جميع الطلبات والردود مواصفات JSON-RPC 2.0، مما يضمن هيكلًا متسقًا لاستدعاءات الطرق، المعلمات، النتائج، ومعالجة الأخطاء.
- **اتصالات حالية**: تحافظ جلسات MCP على الحالة عبر عدة طلبات، داعمة المحادثات المستمرة، تراكم السياق، وإدارة الموارد.
- **التفاوض على القدرات**: خلال إعداد الاتصال، يتبادل العملاء والخوادم معلومات حول الميزات المدعومة، إصدارات البروتوكول، الأدوات، والموارد المتاحة. يضمن هذا فهم الطرفين لقدرات بعضهما البعض وقدرتهما على التكيف.

#### ➕ أدوات إضافية

فيما يلي بعض الأدوات والامتدادات التي يقدمها MCP لتعزيز تجربة المطور وتمكين السيناريوهات المتقدمة:

- **خيارات التكوين**: يسمح MCP بتكوين ديناميكي لمعلمات الجلسة، مثل أذونات الأدوات، الوصول إلى الموارد، وإعدادات النموذج، مخصصة لكل تفاعل.
- **تتبع التقدم**: يمكن للعمليات طويلة الأمد الإبلاغ عن تحديثات التقدم، مما يمكّن واجهات مستخدم تفاعلية وتجربة أفضل خلال المهام المعقدة.
- **إلغاء الطلبات**: يمكن للعملاء إلغاء الطلبات الجارية، مما يسمح للمستخدمين بإيقاف العمليات التي لم تعد ضرورية أو تستغرق وقتًا طويلاً.
- **الإبلاغ عن الأخطاء**: تساعد رسائل وأكواد الأخطاء الموحدة على تشخيص المشكلات، التعامل مع الفشل برشاقة، وتقديم تغذية راجعة قابلة للتنفيذ للمستخدمين والمطورين.
- **التسجيل**: يمكن لكل من العملاء والخوادم إصدار سجلات منظمة للمراجعة، التصحيح، ومراقبة تفاعلات البروتوكول.

من خلال استغلال هذه الميزات، يضمن MCP تواصلًا قويًا، آمنًا، ومرنًا بين نماذج اللغة والأدوات أو مصادر البيانات الخارجية.

### 🔐 اعتبارات الأمان

يجب أن تلتزم تطبيقات MCP بعدة مبادئ أمنية رئيسية لضمان تفاعلات آمنة وموثوقة:

- **موافقة المستخدم والتحكم**: يجب أن يقدم المستخدمون موافقة صريحة قبل الوصول إلى أي بيانات أو تنفيذ عمليات. يجب أن يكون لديهم تحكم واضح فيما يُشارك من بيانات وما هي الإجراءات المصرح بها، مدعومًا بواجهات مستخدم بديهية لمراجعة والموافقة على الأنشطة.

- **خصوصية البيانات**: يجب ألا تُكشف بيانات المستخدم إلا بموافقة صريحة، ويجب حمايتها بضوابط وصول مناسبة. يجب على تطبيقات MCP حماية البيانات من النقل غير المصرح به وضمان الحفاظ على الخصوصية طوال التفاعلات.

- **أمان الأدوات**: قبل استدعاء أي أداة، يجب الحصول على موافقة صريحة من المستخدم. يجب أن يكون لدى المستخدمين فهم واضح لوظائف كل أداة، ويجب فرض حدود أمان صارمة لمنع تنفيذ الأدوات بشكل غير مقصود أو غير آمن.

باتباع هذه المبادئ، يضمن MCP الحفاظ على ثقة المستخدم، الخصوصية، والسلامة عبر جميع تفاعلات البروتوكول.

## أمثلة على الأكواد: المكونات الرئيسية

فيما يلي أمثلة برمجية بعدة لغات شهيرة توضح كيفية تنفيذ مكونات خادم MCP الرئيسية والأدوات.

### مثال .NET: إنشاء خادم MCP بسيط مع أدوات

هنا مثال عملي في .NET يوضح كيفية تنفيذ خادم MCP بسيط مع أدوات مخصصة. يعرض هذا المثال كيفية تعريف الأدوات وتسجيلها، معالجة الطلبات، وربط الخادم باستخدام بروتوكول سياق النموذج.

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

يوضح هذا المثال نفس خادم MCP وتسجيل الأدوات كما في مثال .NET أعلاه، لكن تم تنفيذه بلغة Java.

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

في هذا المثال نوضح كيفية بناء خادم MCP باستخدام Python. كما نعرض طريقتين مختلفتين لإنشاء الأدوات.

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

يعرض هذا المثال إنشاء خادم MCP باستخدام JavaScript ويبين كيفية تسجيل أداتين متعلقتين بالطقس.

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
   يمكن للعملاء تحديد الأدوات التي يُسمح للنموذج باستخدامها خلال الجلسة. يضمن هذا أن الأدوات المصرح بها فقط متاحة، مما يقلل من خطر العمليات غير المقصودة أو غير الآمنة. يمكن تكوين الأذونات ديناميكيًا بناءً على تفضيلات المستخدم، سياسات المؤسسة، أو سياق التفاعل.

2. **المصادقة**  
   قد تطلب الخوادم المصادقة قبل منح الوصول إلى الأدوات، الموارد، أو العمليات الحساسة. قد يشمل ذلك مفاتيح API، رموز OAuth، أو مخططات مصادقة أخرى. تضمن المصادقة الصحيحة أن العملاء والمستخدمين الموثوق بهم فقط يمكنهم استدعاء قدرات الخادم.

3. **التحقق**  
   يُفرض التحقق من المعلمات لجميع استدعاءات الأدوات. تحدد كل أداة الأنواع، الصيغ، والقيود المتوقعة لمعلماتها، ويتحقق الخادم من الطلبات الواردة وفقًا لذلك. يمنع هذا إدخال بيانات غير صحيحة أو خبيثة إلى تنفيذ الأدوات ويساعد في الحفاظ على سلامة العمليات.

4. **تحديد المعدل**  
   لمنع الإساءة وضمان الاستخدام العادل لموارد الخادم، يمكن لخوادم MCP تطبيق تحديد معدل لاستدعاءات الأدوات والوصول إلى الموارد. يمكن تطبيق حدود المعدل لكل مستخدم، لكل جلسة، أو على مستوى عام، وتساعد في الحماية من هجمات الحرمان من الخدمة أو الاستهلاك المفرط للموارد.

بدمج هذه الآليات، يوفر MCP أساسًا آمنًا لدمج نماذج اللغة مع الأدوات ومصادر البيانات الخارجية، مع منح المستخدمين والمطورين تحكمًا دقيقًا في الوصول والاستخدام.

## رسائل البروتوكول

يستخدم MCP رسائل JSON منظمة لتسهيل تفاعلات واضحة وموثوقة بين العملاء، الخوادم، والنماذج. تشمل أنواع الرسائل الرئيسية:

- **طلب العميل**  
  يُرسل من العميل إلى الخادم، وعادة ما يتضمن:
  - مطالبة المستخدم أو الأمر
  - سجل المحادثة للسياق
  - تكوين الأداة والأذونات
  - أي بيانات وصفية إضافية أو معلومات الجلسة

- **رد النموذج**  
  يُعاد من النموذج (عبر العميل)، ويحتوي على:
  - نص مولد أو استكمال بناءً على المطالبة والسياق
  - تعليمات استدعاء أداة اختيارية إذا قرر النموذج استدعاء أداة
  - مراجع للموارد أو السياق الإضافي حسب الحاجة

- **طلب الأداة**  
  يُرسل من العميل إلى الخادم عند الحاجة لتنفيذ أداة. تتضمن الرسالة:
  - اسم الأداة المراد استدعاؤها
  - المعلمات المطلوبة للأداة (تم التحقق منها مقابل مخطط الأداة)
  - معلومات سياقية أو معرفات لتتبع الطلب

- **رد الأداة**  
  يُعاد من الخادم بعد تنفيذ الأداة. توفر الرسالة:
  - نتائج تنفيذ الأداة (بيانات منظمة أو محتوى)
  - أي أخطاء أو معلومات

**إخلاء المسؤولية**:  
تمت ترجمة هذا المستند باستخدام خدمة الترجمة الآلية [Co-op Translator](https://github.com/Azure/co-op-translator). بينما نسعى لتحقيق الدقة، يرجى العلم أن الترجمات الآلية قد تحتوي على أخطاء أو عدم دقة. يجب اعتبار المستند الأصلي بلغته الأصلية المصدر الموثوق به. للمعلومات الحرجة، يُنصح بالاعتماد على الترجمة البشرية المهنية. نحن غير مسؤولين عن أي سوء فهم أو تفسير ناتج عن استخدام هذه الترجمة.