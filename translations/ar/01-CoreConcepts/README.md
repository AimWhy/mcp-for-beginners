<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "056918462dca9b8f75901709fb8f470c",
  "translation_date": "2025-05-17T06:14:36+00:00",
  "source_file": "01-CoreConcepts/README.md",
  "language_code": "ar"
}
-->
# 📖 مفاهيم MCP الأساسية: إتقان بروتوكول سياق النموذج لدمج الذكاء الاصطناعي

بروتوكول سياق النموذج (MCP) هو إطار عمل قوي وموحد يهدف إلى تحسين الاتصال بين النماذج اللغوية الكبيرة (LLMs) والأدوات الخارجية والتطبيقات ومصادر البيانات. ستقودك هذه الدليل المحسّن لـ SEO عبر المفاهيم الأساسية لـ MCP، مما يضمن فهمك لبنيته المعمارية العميل-الخادم، والمكونات الأساسية، وآليات الاتصال، وأفضل الممارسات للتنفيذ.

## نظرة عامة

تستكشف هذه الدرس البنية المعمارية الأساسية والمكونات التي تشكل نظام بيئة بروتوكول سياق النموذج (MCP). ستتعلم عن بنية العميل-الخادم، والمكونات الرئيسية، وآليات الاتصال التي تدعم التفاعلات في MCP.

## 👩‍🎓 الأهداف التعليمية الرئيسية

بنهاية هذه الدرس، ستكون قادرًا على:

- فهم بنية العميل-الخادم في MCP.
- تحديد الأدوار والمسؤوليات للمضيفين والعملاء والخوادم.
- تحليل الميزات الأساسية التي تجعل MCP طبقة تكامل مرنة.
- تعلم كيفية تدفق المعلومات داخل نظام بيئة MCP.
- اكتساب رؤى عملية من خلال أمثلة البرمجة في .NET، Java، Python، وJavaScript.

## 🔎 بنية MCP: نظرة أعمق

نظام بيئة MCP مبني على نموذج العميل-الخادم. هذه البنية المعيارية تسمح لتطبيقات الذكاء الاصطناعي بالتفاعل بكفاءة مع الأدوات وقواعد البيانات وواجهات برمجة التطبيقات والموارد السياقية. دعونا نفكك هذه البنية إلى مكوناتها الأساسية.

### 1. المضيفون

في بروتوكول سياق النموذج (MCP)، يلعب المضيفون دورًا حيويًا باعتبارهم الواجهة الأساسية التي يتفاعل من خلالها المستخدمون مع البروتوكول. المضيفون هم تطبيقات أو بيئات تبدأ الاتصالات مع خوادم MCP للوصول إلى البيانات والأدوات والمحفزات. أمثلة على المضيفون تشمل بيئات التطوير المتكاملة (IDEs) مثل Visual Studio Code، أدوات الذكاء الاصطناعي مثل Claude Desktop، أو الوكلاء المخصصين المصممين لأداء مهام محددة.

**المضيفون** هم تطبيقات LLM التي تبدأ الاتصالات. هم:

- ينفذون أو يتفاعلون مع نماذج الذكاء الاصطناعي لتوليد الاستجابات.
- يبدأون الاتصالات مع خوادم MCP.
- يديرون تدفق المحادثة وواجهة المستخدم.
- يتحكمون في الأذونات والقيود الأمنية.
- يتعاملون مع موافقة المستخدم على مشاركة البيانات وتنفيذ الأدوات.

### 2. العملاء

العملاء هم مكونات أساسية تسهل التفاعل بين المضيفين وخوادم MCP. يعمل العملاء كوسيط، مما يمكن المضيفين من الوصول إلى والاستفادة من الوظائف التي تقدمها خوادم MCP. يلعبون دورًا حيويًا في ضمان التواصل السلس وتبادل البيانات بكفاءة داخل بنية MCP.

**العملاء** هم موصلات داخل تطبيق المضيف. هم:

- يرسلون طلبات إلى الخوادم مع المحفزات/التعليمات.
- يتفاوضون على القدرات مع الخوادم.
- يديرون طلبات تنفيذ الأدوات من النماذج.
- يعالجون ويعرضون الاستجابات للمستخدمين.

### 3. الخوادم

الخوادم مسؤولة عن معالجة الطلبات من عملاء MCP وتقديم الاستجابات المناسبة. يديرون عمليات متنوعة مثل استرجاع البيانات، تنفيذ الأدوات، وتوليد المحفزات. الخوادم تضمن أن التواصل بين العملاء والمضيفين فعال وموثوق، مع الحفاظ على نزاهة عملية التفاعل.

**الخوادم** هي خدمات تقدم السياق والقدرات. هم:

- يسجلون الميزات المتاحة (الموارد، المحفزات، الأدوات)
- يتلقون وينفذون مكالمات الأدوات من العميل
- يقدمون معلومات سياقية لتعزيز استجابات النموذج
- يعيدون المخرجات إلى العميل
- يحافظون على الحالة عبر التفاعلات عند الحاجة

يمكن لأي شخص تطوير الخوادم لتمديد قدرات النموذج بوظائف متخصصة.

### 4. ميزات الخادم

الخوادم في بروتوكول سياق النموذج (MCP) توفر اللبنات الأساسية التي تمكن من تفاعلات غنية بين العملاء، المضيفين، والنماذج اللغوية. تم تصميم هذه الميزات لتعزيز قدرات MCP من خلال تقديم سياق منظم، أدوات، ومحفزات.

يمكن لخوادم MCP تقديم أي من الميزات التالية:

#### 📑 الموارد

الموارد في بروتوكول سياق النموذج (MCP) تشمل أنواع مختلفة من السياق والبيانات التي يمكن أن يستخدمها المستخدمون أو نماذج الذكاء الاصطناعي. هذه تشمل:

- **البيانات السياقية**: المعلومات والسياق الذي يمكن أن يستخدمه المستخدمون أو نماذج الذكاء الاصطناعي لاتخاذ القرارات وتنفيذ المهام.
- **قواعد المعرفة ومستودعات الوثائق**: مجموعات من البيانات المنظمة وغير المنظمة، مثل المقالات، الكتيبات، والأوراق البحثية، التي تقدم رؤى ومعلومات قيمة.
- **الملفات المحلية وقواعد البيانات**: البيانات المخزنة محليًا على الأجهزة أو داخل قواعد البيانات، قابلة للوصول للمعالجة والتحليل.
- **واجهات برمجة التطبيقات والخدمات الويب**: الواجهات الخارجية والخدمات التي تقدم بيانات ووظائف إضافية، مما يمكن من التكامل مع موارد وأدوات عبر الإنترنت متنوعة.

مثال على مورد يمكن أن يكون مخطط قاعدة بيانات أو ملف يمكن الوصول إليه على النحو التالي:

```text
file://log.txt
database://schema
```

### 🤖 المحفزات

المحفزات في بروتوكول سياق النموذج (MCP) تشمل قوالب وأنماط تفاعل مختلفة مسبقة التعريف مصممة لتبسيط سير عمل المستخدم وتحسين التواصل. هذه تشمل:

- **الرسائل والقوالب المهيكلة**: الرسائل والعمليات المسبقة الهيكلة التي توجه المستخدمين خلال مهام وتفاعلات محددة.
- **أنماط التفاعل المسبقة التعريف**: تسلسلات موحدة من الإجراءات والاستجابات التي تسهل التواصل المتسق والفعال.
- **قوالب المحادثة المتخصصة**: قوالب قابلة للتخصيص مصممة لأنواع محددة من المحادثات، مما يضمن تفاعلات ذات صلة ومناسبة للسياق.

يمكن أن يبدو قالب المحفز كما يلي:

```markdown
Generate a product slogan based on the following {{product}} with the following {{keywords}}
```

#### ⛏️ الأدوات

الأدوات في بروتوكول سياق النموذج (MCP) هي وظائف يمكن لنموذج الذكاء الاصطناعي تنفيذها لأداء مهام محددة. تم تصميم هذه الأدوات لتعزيز قدرات نموذج الذكاء الاصطناعي من خلال تقديم عمليات منظمة وموثوقة. تشمل الجوانب الرئيسية:

- **وظائف لتنفيذ نموذج الذكاء الاصطناعي**: الأدوات هي وظائف قابلة للتنفيذ يمكن لنموذج الذكاء الاصطناعي استدعاؤها لأداء مهام متنوعة.
- **اسم ووصف فريد**: كل أداة لها اسم مميز ووصف مفصل يشرح غرضها ووظيفتها.
- **المعلمات والمخرجات**: الأدوات تقبل معلمات محددة وتعيد مخرجات منظمة، مما يضمن نتائج متسقة وقابلة للتنبؤ.
- **وظائف منفصلة**: الأدوات تنفذ وظائف منفصلة مثل البحث على الويب، الحسابات، واستعلامات قواعد البيانات.

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

في بروتوكول سياق النموذج (MCP)، يقدم العملاء عدة ميزات رئيسية للخوادم، مما يعزز الوظيفة العامة والتفاعل داخل البروتوكول. واحدة من الميزات البارزة هي أخذ العينات.

### 👉 أخذ العينات

- **سلوكيات الوكيل التي يبدأها الخادم**: تمكن العملاء الخوادم من بدء إجراءات أو سلوكيات محددة بشكل مستقل، مما يعزز القدرات الديناميكية للنظام.
- **تفاعلات LLM المتكررة**: تتيح هذه الميزة تفاعلات متكررة مع النماذج اللغوية الكبيرة (LLMs)، مما يمكن من معالجة أكثر تعقيدًا ومتكررة للمهام.
- **طلب استكمالات إضافية للنموذج**: يمكن للخوادم طلب استكمالات إضافية من النموذج، مما يضمن أن تكون الاستجابات شاملة وذات صلة بالسياق.

## تدفق المعلومات في MCP

يعرف بروتوكول سياق النموذج (MCP) تدفقًا منظمًا للمعلومات بين المضيفين، العملاء، الخوادم، والنماذج. فهم هذا التدفق يساعد في توضيح كيفية معالجة طلبات المستخدم وكيفية دمج الأدوات والبيانات الخارجية في استجابات النموذج.

- **يبدأ المضيف الاتصال**  
  يقوم تطبيق المضيف (مثل بيئة التطوير المتكاملة أو واجهة الدردشة) بإنشاء اتصال مع خادم MCP، عادةً عبر STDIO أو WebSocket أو طبقة نقل مدعومة أخرى.

- **التفاوض على القدرات**  
  يقوم العميل (المضمن في المضيف) والخادم بتبادل المعلومات حول الميزات والأدوات والموارد وإصدارات البروتوكول المدعومة لديهم. يضمن هذا أن يفهم الجانبان ما هي القدرات المتاحة للجلسة.

- **طلب المستخدم**  
  يتفاعل المستخدم مع المضيف (مثل إدخال محفز أو أمر). يجمع المضيف هذا الإدخال ويمرره إلى العميل للمعالجة.

- **استخدام الموارد أو الأدوات**  
  - قد يطلب العميل سياقًا أو موارد إضافية من الخادم (مثل الملفات أو إدخالات قاعدة البيانات أو مقالات قاعدة المعرفة) لتعزيز فهم النموذج.
  - إذا حدد النموذج أن أداة ضرورية (مثل لجلب البيانات أو إجراء حساب أو استدعاء API)، يرسل العميل طلب استدعاء الأداة إلى الخادم، محددًا اسم الأداة والمعلمات.

- **تنفيذ الخادم**  
  يتلقى الخادم طلب الموارد أو الأداة، وينفذ العمليات اللازمة (مثل تشغيل وظيفة أو استعلام قاعدة بيانات أو استرجاع ملف)، ويعيد النتائج إلى العميل في صيغة منظمة.

- **توليد الاستجابة**  
  يدمج العميل استجابات الخادم (بيانات الموارد، مخرجات الأداة، إلخ) في التفاعل المستمر للنموذج. يستخدم النموذج هذه المعلومات لتوليد استجابة شاملة وذات صلة بالسياق.

- **عرض النتيجة**  
  يتلقى المضيف المخرجات النهائية من العميل ويعرضها للمستخدم، غالبًا بما في ذلك النص الذي يولده النموذج وأي نتائج من تنفيذ الأدوات أو البحث عن الموارد.

هذا التدفق يمكّن MCP من دعم تطبيقات الذكاء الاصطناعي المتقدمة والتفاعلية والمدركة للسياق عن طريق ربط النماذج بسلاسة مع الأدوات والبيانات الخارجية.

## تفاصيل البروتوكول

تم بناء MCP (بروتوكول سياق النموذج) على أساس [JSON-RPC 2.0](https://www.jsonrpc.org/)، مما يوفر صيغة رسالة موحدة وغير معتمدة على اللغة للتواصل بين المضيفين والعملاء والخوادم. يتيح هذا الأساس تفاعلات موثوقة ومنظمة وقابلة للتوسيع عبر منصات ولغات برمجة متنوعة.

### ميزات البروتوكول الرئيسية

يمدد MCP JSON-RPC 2.0 بتقاليد إضافية لاستدعاء الأدوات، الوصول إلى الموارد، وإدارة المحفزات. يدعم طبقات نقل متعددة (STDIO، WebSocket، SSE) ويتيح التواصل الآمن والقابل للتوسيع وغير المعتمد على اللغة بين المكونات.

#### 🧢 بروتوكول أساسي

- **صيغة رسالة JSON-RPC**: جميع الطلبات والاستجابات تستخدم مواصفات JSON-RPC 2.0، مما يضمن بنية متسقة لاستدعاء الطرق، المعلمات، النتائج، ومعالجة الأخطاء.
- **اتصالات مستمرة**: جلسات MCP تحافظ على الحالة عبر طلبات متعددة، مما يدعم المحادثات المستمرة، تراكم السياق، وإدارة الموارد.
- **التفاوض على القدرات**: أثناء إعداد الاتصال، يتبادل العملاء والخوادم المعلومات حول الميزات المدعومة، إصدارات البروتوكول، الأدوات المتاحة، والموارد. يضمن هذا أن يفهم الجانبان قدرات بعضهم البعض ويمكنهم التكيف وفقًا لذلك.

#### ➕ أدوات إضافية

فيما يلي بعض الأدوات الإضافية وامتدادات البروتوكول التي يوفرها MCP لتحسين تجربة المطور وتمكين السيناريوهات المتقدمة:

- **خيارات التكوين**: يسمح MCP بتكوين ديناميكي لمعايير الجلسة، مثل أذونات الأدوات، الوصول إلى الموارد، وإعدادات النموذج، مخصصة لكل تفاعل.
- **تتبع التقدم**: يمكن للعمليات الطويلة الإبلاغ عن تحديثات التقدم، مما يتيح واجهات مستخدم مستجيبة وتجربة مستخدم أفضل أثناء المهام المعقدة.
- **إلغاء الطلب**: يمكن للعملاء إلغاء الطلبات أثناء التنفيذ، مما يسمح للمستخدمين بوقف العمليات التي لم تعد ضرورية أو تستغرق وقتًا طويلًا.
- **الإبلاغ عن الأخطاء**: تساعد الرسائل والرموز القياسية للأخطاء في تشخيص المشكلات، التعامل مع الإخفاقات بشكل سلس، وتقديم ملاحظات قابلة للتنفيذ للمستخدمين والمطورين.
- **التسجيل**: يمكن للعملاء والخوادم إصدار سجلات منظمة للمراجعة، التصحيح، ومراقبة تفاعلات البروتوكول.

من خلال الاستفادة من ميزات البروتوكول هذه، يضمن MCP التواصل القوي والآمن والمرن بين النماذج اللغوية والأدوات أو مصادر البيانات الخارجية.

### 🔐 اعتبارات الأمان

يجب أن تلتزم تنفيذات MCP بعدة مبادئ أمان رئيسية لضمان تفاعلات آمنة وموثوقة:

- **موافقة المستخدم والسيطرة**: يجب على المستخدمين تقديم موافقة صريحة قبل الوصول إلى أي بيانات أو تنفيذ عمليات. يجب أن يكون لديهم سيطرة واضحة على البيانات التي تتم مشاركتها والإجراءات التي يتم السماح بها، مدعومة بواجهات مستخدم بديهية لمراجعة الأنشطة والموافقة عليها.

- **خصوصية البيانات**: يجب أن يتم كشف بيانات المستخدم فقط بموافقة صريحة ويجب أن تكون محمية بواسطة ضوابط الوصول المناسبة. يجب أن تضمن تنفيذات MCP الحماية من نقل البيانات غير المصرح به وضمان الحفاظ على الخصوصية طوال جميع التفاعلات.

- **سلامة الأدوات**: قبل استدعاء أي أداة، يتطلب موافقة صريحة من المستخدم. يجب أن يكون لدى المستخدمين فهم واضح لوظيفة كل أداة، ويجب فرض حدود أمان قوية لمنع تنفيذ الأدوات غير المقصود أو غير الآمن.

من خلال اتباع هذه المبادئ، يضمن MCP الحفاظ على ثقة المستخدم، الخصوصية، والأمان عبر جميع تفاعلات البروتوكول.

## أمثلة البرمجة: المكونات الرئيسية

فيما يلي أمثلة البرمجة في عدة لغات برمجة شهيرة توضح كيفية تنفيذ مكونات خادم MCP الأساسية والأدوات.

### مثال .NET: إنشاء خادم MCP بسيط مع أدوات

فيما يلي مثال برمجة عملي في .NET يوضح كيفية تنفيذ خادم MCP بسيط مع أدوات مخصصة. يعرض هذا المثال كيفية تعريف وتسجيل الأدوات، معالجة الطلبات، وربط الخادم باستخدام بروتوكول سياق النموذج.

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

يظهر هذا المثال نفس تسجيل الخادم والأداة MCP كما في المثال .NET أعلاه، ولكنه يتم تنفيذه في Java.

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

في هذا المثال نعرض كيفية بناء خادم MCP في Python. يتم أيضًا عرض طريقتين مختلفتين لإنشاء الأدوات.

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

يظهر هذا المثال إنشاء خادم MCP في JavaScript ويعرض كيفية تسجيل أداتين تتعلقان بالطقس.

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

هذا المثال JavaScript يوضح كيفية إنشاء عميل MCP يتصل بخادم، يرسل محفزًا، ويعالج الاستجابة بما في ذلك أي استدعاءات للأدوات التي تم إجراؤها.

## الأمان والتفويض

يتضمن MCP عدة مفاهيم وآليات مدمجة لإدارة الأمان والتفويض عبر البروتوكول:

1. **التحكم في أذونات الأدوات**:  
  يمكن للعملاء تحديد الأدوات التي يسمح للنموذج باستخدامها خلال الجلسة. يضمن هذا أن تكون الأدوات المصرح بها فقط قابلة للوصول، مما يقلل من خطر العمليات غير المقصودة أو غير الآمنة. يمكن تكوين الأذونات ديناميكيًا بناءً على تفضيلات المستخدم، سياسات المنظمة، أو سياق التفاعل.

2. **المصادقة**:  
  يمكن للخوادم طلب المصادقة قبل منح الوصول إلى الأدوات أو الموارد أو العمليات الحساسة. قد يتضمن هذا مفاتيح API، رموز OAuth، أو مخططات مصادقة أخرى. تضمن المصادقة المناسبة أن العملاء والمستخدمين الموثوق بهم فقط يمكنهم استدعاء القدرات الخادمة.

3. **التحقق**:  
  يتم فرض التحقق من المعلمات لجميع استدعاءات الأدوات. كل أداة تحدد الأنواع والتنسيقات والقيود المتوقعة لمعلماتها، ويقوم الخادم بالتحقق من الطلبات الواردة وفقًا لذلك. يمنع هذا الإدخال المشوه أو الضار من الوصول إلى تنفيذات الأدوات ويساعد في الحفاظ على نزاهة العمليات.

4. **تحديد معدل الاستخدام**:  
  لمنع الإساءة وضمان الاستخدام العادل لموارد الخادم، يمكن لخوادم MCP تنفيذ تحديد معدل الاستخدام لاستدعاءات الأدوات والوصول إلى الموارد. يمكن تطبيق تحديد المعدل لكل مستخدم، لكل جلسة، أو عالميًا، ويساعد في الحماية من هجمات رفض الخدمة أو الاستهلاك المفرط للموارد.

من خلال الجمع بين هذه الآليات، يوفر MCP أساسًا آمنًا لدمج النماذج اللغوية مع الأدوات والبيانات الخارجية، مع منح المستخدمين والمطورين تحكمًا دقيقًا في الوصول والاستخدام.

## رسائل البروتوكول

يستخدم MCP رسائل JSON منظمة لتسهيل التفاعلات الواضحة والموثوقة بين العملاء، الخوادم، والن

**إخلاء المسؤولية**:  
تمت ترجمة هذه الوثيقة باستخدام خدمة الترجمة بالذكاء الاصطناعي [Co-op Translator](https://github.com/Azure/co-op-translator). بينما نسعى لتحقيق الدقة، يُرجى العلم أن الترجمات الآلية قد تحتوي على أخطاء أو عدم دقة. يجب اعتبار الوثيقة الأصلية بلغتها الأم هي المصدر الموثوق. للحصول على معلومات حساسة، يُوصى بالترجمة البشرية الاحترافية. نحن غير مسؤولين عن أي سوء فهم أو تفسيرات خاطئة ناتجة عن استخدام هذه الترجمة.