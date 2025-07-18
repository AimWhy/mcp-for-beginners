<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "6755bc4f6d0293ce6c49cfc5efba0d8e",
  "translation_date": "2025-07-18T09:16:33+00:00",
  "source_file": "07-LessonsfromEarlyAdoption/README.md",
  "language_code": "fa"
}
-->
# 🌟 درس‌هایی از پذیرندگان اولیه

## 🎯 این ماژول چه موضوعاتی را پوشش می‌دهد

این ماژول بررسی می‌کند که چگونه سازمان‌ها و توسعه‌دهندگان واقعی از Model Context Protocol (MCP) برای حل چالش‌های واقعی و پیشبرد نوآوری استفاده می‌کنند. از طریق مطالعات موردی دقیق، پروژه‌های عملی و مثال‌های کاربردی، خواهید دید که MCP چگونه امکان ادغام امن و مقیاس‌پذیر هوش مصنوعی را فراهم می‌کند که مدل‌های زبانی، ابزارها و داده‌های سازمانی را به هم متصل می‌کند.

### مطالعه موردی ۵: Azure MCP – پروتکل مدل کانتکست سازمانی به‌عنوان سرویس

Azure MCP ([https://aka.ms/azmcp](https://aka.ms/azmcp)) پیاده‌سازی مدیریت‌شده و سازمانی پروتکل مدل کانتکست توسط مایکروسافت است که برای ارائه قابلیت‌های سرور MCP مقیاس‌پذیر، امن و مطابق با مقررات به‌صورت سرویس ابری طراحی شده است. این مجموعه جامع شامل چندین سرور MCP تخصصی برای خدمات و سناریوهای مختلف Azure است.

> **🎯 ابزارهای آماده تولید**
> 
> این مطالعه موردی نمایانگر چندین سرور MCP آماده تولید است! درباره Azure MCP Server و سایر سرورهای یکپارچه با Azure در [**راهنمای سرورهای MCP مایکروسافت**](microsoft-mcp-servers.md#2--azure-mcp-server) بیشتر بدانید.

**ویژگی‌های کلیدی:**
- میزبانی کامل سرور MCP با مدیریت خودکار مقیاس، نظارت و امنیت
- یکپارچگی بومی با Azure OpenAI، Azure AI Search و سایر خدمات Azure
- احراز هویت و مجوز سازمانی از طریق Microsoft Entra ID
- پشتیبانی از ابزارهای سفارشی، قالب‌های پرامپت و کانکتورهای منابع
- تطابق با الزامات امنیتی و مقرراتی سازمانی
- بیش از ۱۵ کانکتور تخصصی خدمات Azure شامل پایگاه داده، نظارت و ذخیره‌سازی

**قابلیت‌های Azure MCP Server:**
- **مدیریت منابع**: مدیریت کامل چرخه عمر منابع Azure
- **کانکتورهای پایگاه داده**: دسترسی مستقیم به Azure Database برای PostgreSQL و SQL Server
- **Azure Monitor**: تحلیل لاگ‌ها و بینش‌های عملیاتی با KQL
- **احراز هویت**: الگوهای DefaultAzureCredential و managed identity
- **خدمات ذخیره‌سازی**: عملیات Blob Storage، Queue Storage و Table Storage
- **خدمات کانتینر**: مدیریت Azure Container Apps، Container Instances و AKS

### 📚 مشاهده MCP در عمل

می‌خواهید ببینید این اصول چگونه در ابزارهای آماده تولید به کار رفته‌اند؟ به [**۱۰ سرور MCP مایکروسافت که بهره‌وری توسعه‌دهندگان را متحول می‌کنند**](microsoft-mcp-servers.md) مراجعه کنید که سرورهای واقعی MCP مایکروسافت را که امروز می‌توانید استفاده کنید، نشان می‌دهد.

## مرور کلی

این درس بررسی می‌کند که چگونه پذیرندگان اولیه از Model Context Protocol (MCP) برای حل چالش‌های دنیای واقعی و پیشبرد نوآوری در صنایع مختلف استفاده کرده‌اند. از طریق مطالعات موردی دقیق و پروژه‌های عملی، خواهید دید که MCP چگونه ادغام استاندارد، امن و مقیاس‌پذیر هوش مصنوعی را ممکن می‌سازد—اتصال مدل‌های زبانی بزرگ، ابزارها و داده‌های سازمانی در یک چارچوب یکپارچه. شما تجربه عملی در طراحی و ساخت راه‌حل‌های مبتنی بر MCP کسب خواهید کرد، از الگوهای اثبات‌شده پیاده‌سازی خواهید آموخت و بهترین روش‌ها برای استقرار MCP در محیط‌های تولید را کشف خواهید کرد. این درس همچنین روندهای نوظهور، جهت‌گیری‌های آینده و منابع متن‌باز را برای کمک به شما در پیشرو ماندن در فناوری MCP و اکوسیستم در حال تحول آن برجسته می‌کند.

## اهداف یادگیری

- تحلیل پیاده‌سازی‌های واقعی MCP در صنایع مختلف  
- طراحی و ساخت برنامه‌های کامل مبتنی بر MCP  
- بررسی روندهای نوظهور و جهت‌گیری‌های آینده در فناوری MCP  
- به‌کارگیری بهترین روش‌ها در سناریوهای توسعه واقعی  

## پیاده‌سازی‌های واقعی MCP

### مطالعه موردی ۱: اتوماسیون پشتیبانی مشتری سازمانی

یک شرکت چندملیتی راه‌حلی مبتنی بر MCP پیاده‌سازی کرد تا تعاملات هوش مصنوعی را در سیستم‌های پشتیبانی مشتری خود استاندارد کند. این امکان را برای آن‌ها فراهم کرد تا:

- رابط کاربری یکپارچه برای چندین ارائه‌دهنده LLM ایجاد کنند  
- مدیریت پرامپت یکنواخت در بخش‌های مختلف حفظ شود  
- کنترل‌های امنیتی و تطابق قوی پیاده‌سازی شود  
- به‌راحتی بین مدل‌های مختلف هوش مصنوعی بر اساس نیازهای خاص جابجا شوند  

**پیاده‌سازی فنی:**  
```python
# Python MCP server implementation for customer support
import logging
import asyncio
from modelcontextprotocol import create_server, ServerConfig
from modelcontextprotocol.server import MCPServer
from modelcontextprotocol.transports import create_http_transport
from modelcontextprotocol.resources import ResourceDefinition
from modelcontextprotocol.prompts import PromptDefinition
from modelcontextprotocol.tool import ToolDefinition

# Configure logging
logging.basicConfig(level=logging.INFO)

async def main():
    # Create server configuration
    config = ServerConfig(
        name="Enterprise Customer Support Server",
        version="1.0.0",
        description="MCP server for handling customer support inquiries"
    )
    
    # Initialize MCP server
    server = create_server(config)
    
    # Register knowledge base resources
    server.resources.register(
        ResourceDefinition(
            name="customer_kb",
            description="Customer knowledge base documentation"
        ),
        lambda params: get_customer_documentation(params)
    )
    
    # Register prompt templates
    server.prompts.register(
        PromptDefinition(
            name="support_template",
            description="Templates for customer support responses"
        ),
        lambda params: get_support_templates(params)
    )
    
    # Register support tools
    server.tools.register(
        ToolDefinition(
            name="ticketing",
            description="Create and update support tickets"
        ),
        handle_ticketing_operations
    )
    
    # Start server with HTTP transport
    transport = create_http_transport(port=8080)
    await server.run(transport)

if __name__ == "__main__":
    asyncio.run(main())
```

**نتایج:** کاهش ۳۰٪ در هزینه‌های مدل، بهبود ۴۵٪ در ثبات پاسخ‌ها و افزایش تطابق در عملیات جهانی.

### مطالعه موردی ۲: دستیار تشخیص پزشکی

یک ارائه‌دهنده خدمات بهداشتی زیرساخت MCP را برای ادغام چندین مدل تخصصی پزشکی هوش مصنوعی توسعه داد در حالی که داده‌های حساس بیماران محافظت می‌شدند:

- جابجایی بدون درز بین مدل‌های پزشکی عمومی و تخصصی  
- کنترل‌های سختگیرانه حریم خصوصی و ردگیری حسابرسی  
- یکپارچگی با سیستم‌های موجود پرونده الکترونیکی سلامت (EHR)  
- مهندسی پرامپت یکنواخت برای اصطلاحات پزشکی  

**پیاده‌سازی فنی:**  
```csharp
// C# MCP host application implementation in healthcare application
using Microsoft.Extensions.DependencyInjection;
using ModelContextProtocol.SDK.Client;
using ModelContextProtocol.SDK.Security;
using ModelContextProtocol.SDK.Resources;

public class DiagnosticAssistant
{
    private readonly MCPHostClient _mcpClient;
    private readonly PatientContext _patientContext;
    
    public DiagnosticAssistant(PatientContext patientContext)
    {
        _patientContext = patientContext;
        
        // Configure MCP client with healthcare-specific settings
        var clientOptions = new ClientOptions
        {
            Name = "Healthcare Diagnostic Assistant",
            Version = "1.0.0",
            Security = new SecurityOptions
            {
                Encryption = EncryptionLevel.Medical,
                AuditEnabled = true
            }
        };
        
        _mcpClient = new MCPHostClientBuilder()
            .WithOptions(clientOptions)
            .WithTransport(new HttpTransport("https://healthcare-mcp.example.org"))
            .WithAuthentication(new HIPAACompliantAuthProvider())
            .Build();
    }
    
    public async Task<DiagnosticSuggestion> GetDiagnosticAssistance(
        string symptoms, string patientHistory)
    {
        // Create request with appropriate resources and tool access
        var resourceRequest = new ResourceRequest
        {
            Name = "patient_records",
            Parameters = new Dictionary<string, object>
            {
                ["patientId"] = _patientContext.PatientId,
                ["requestingProvider"] = _patientContext.ProviderId
            }
        };
        
        // Request diagnostic assistance using appropriate prompt
        var response = await _mcpClient.SendPromptRequestAsync(
            promptName: "diagnostic_assistance",
            parameters: new Dictionary<string, object>
            {
                ["symptoms"] = symptoms,
                patientHistory = patientHistory,
                relevantGuidelines = _patientContext.GetRelevantGuidelines()
            });
            
        return DiagnosticSuggestion.FromMCPResponse(response);
    }
}
```

**نتایج:** بهبود پیشنهادات تشخیصی برای پزشکان همراه با حفظ کامل تطابق با HIPAA و کاهش قابل توجه جابجایی بین سیستم‌ها.

### مطالعه موردی ۳: تحلیل ریسک خدمات مالی

یک مؤسسه مالی MCP را برای استانداردسازی فرآیندهای تحلیل ریسک در بخش‌های مختلف پیاده‌سازی کرد:

- ایجاد رابط کاربری یکپارچه برای مدل‌های ریسک اعتباری، تشخیص تقلب و ریسک سرمایه‌گذاری  
- پیاده‌سازی کنترل‌های دسترسی سختگیرانه و نسخه‌بندی مدل‌ها  
- تضمین قابلیت حسابرسی تمام توصیه‌های هوش مصنوعی  
- حفظ قالب‌بندی داده یکنواخت در سیستم‌های متنوع  

**پیاده‌سازی فنی:**  
```java
// Java MCP server for financial risk assessment
import org.mcp.server.*;
import org.mcp.security.*;

public class FinancialRiskMCPServer {
    public static void main(String[] args) {
        // Create MCP server with financial compliance features
        MCPServer server = new MCPServerBuilder()
            .withModelProviders(
                new ModelProvider("risk-assessment-primary", new AzureOpenAIProvider()),
                new ModelProvider("risk-assessment-audit", new LocalLlamaProvider())
            )
            .withPromptTemplateDirectory("./compliance/templates")
            .withAccessControls(new SOCCompliantAccessControl())
            .withDataEncryption(EncryptionStandard.FINANCIAL_GRADE)
            .withVersionControl(true)
            .withAuditLogging(new DatabaseAuditLogger())
            .build();
            
        server.addRequestValidator(new FinancialDataValidator());
        server.addResponseFilter(new PII_RedactionFilter());
        
        server.start(9000);
        
        System.out.println("Financial Risk MCP Server running on port 9000");
    }
}
```

**نتایج:** بهبود تطابق با مقررات، ۴۰٪ سرعت بیشتر در چرخه‌های استقرار مدل و افزایش ثبات ارزیابی ریسک در بخش‌ها.

### مطالعه موردی ۴: سرور Microsoft Playwright MCP برای اتوماسیون مرورگر

مایکروسافت سرور [Playwright MCP](https://github.com/microsoft/playwright-mcp) را برای امکان اتوماسیون مرورگر امن و استاندارد از طریق Model Context Protocol توسعه داد. این سرور آماده تولید به عوامل هوش مصنوعی و LLMها اجازه می‌دهد تا به صورت کنترل‌شده، قابل حسابرسی و قابل توسعه با مرورگرهای وب تعامل داشته باشند—امکان استفاده در مواردی مانند تست خودکار وب، استخراج داده و گردش‌های کاری انتها به انتها.

> **🎯 ابزار آماده تولید**  
> 
> این مطالعه موردی یک سرور MCP واقعی است که می‌توانید امروز استفاده کنید! درباره Playwright MCP Server و ۹ سرور MCP آماده تولید دیگر مایکروسافت در [**راهنمای سرورهای MCP مایکروسافت**](microsoft-mcp-servers.md#8--playwright-mcp-server) بیشتر بدانید.

**ویژگی‌های کلیدی:**  
- ارائه قابلیت‌های اتوماسیون مرورگر (ناوبری، پر کردن فرم، گرفتن اسکرین‌شات و غیره) به عنوان ابزارهای MCP  
- پیاده‌سازی کنترل‌های دسترسی سختگیرانه و محیط ایزوله برای جلوگیری از اقدامات غیرمجاز  
- ارائه لاگ‌های حسابرسی دقیق برای تمام تعاملات مرورگر  
- پشتیبانی از یکپارچگی با Azure OpenAI و سایر ارائه‌دهندگان LLM برای اتوماسیون مبتنی بر عامل  
- تأمین قدرت عامل کدنویسی GitHub Copilot با قابلیت مرور وب  

**پیاده‌سازی فنی:**  
```typescript
// TypeScript: Registering Playwright browser automation tools in an MCP server
import { createServer, ToolDefinition } from 'modelcontextprotocol';
import { launch } from 'playwright';

const server = createServer({
  name: 'Playwright MCP Server',
  version: '1.0.0',
  description: 'MCP server for browser automation using Playwright'
});

// Register a tool for navigating to a URL and capturing a screenshot
server.tools.register(
  new ToolDefinition({
    name: 'navigate_and_screenshot',
    description: 'Navigate to a URL and capture a screenshot',
    parameters: {
      url: { type: 'string', description: 'The URL to visit' }
    }
  }),
  async ({ url }) => {
    const browser = await launch();
    const page = await browser.newPage();
    await page.goto(url);
    const screenshot = await page.screenshot();
    await browser.close();
    return { screenshot };
  }
);

// Start the MCP server
server.listen(8080);
```

**نتایج:**  
- امکان اتوماسیون مرورگر برنامه‌ریزی‌شده و امن برای عوامل هوش مصنوعی و LLMها  
- کاهش تلاش‌های تست دستی و بهبود پوشش تست برنامه‌های وب  
- ارائه چارچوب قابل استفاده مجدد و توسعه‌پذیر برای ادغام ابزارهای مبتنی بر مرورگر در محیط‌های سازمانی  
- تأمین قدرت قابلیت‌های مرور وب GitHub Copilot  

**مراجع:**  
- [مخزن GitHub Playwright MCP Server](https://github.com/microsoft/playwright-mcp)  
- [راه‌حل‌های هوش مصنوعی و اتوماسیون مایکروسافت](https://azure.microsoft.com/en-us/products/ai-services/)

### مطالعه موردی ۵: Azure MCP – پروتکل مدل کانتکست سازمانی به‌عنوان سرویس

سرور Azure MCP ([https://aka.ms/azmcp](https://aka.ms/azmcp)) پیاده‌سازی مدیریت‌شده و سازمانی پروتکل مدل کانتکست توسط مایکروسافت است که برای ارائه قابلیت‌های سرور MCP مقیاس‌پذیر، امن و مطابق با مقررات به‌صورت سرویس ابری طراحی شده است. Azure MCP به سازمان‌ها امکان می‌دهد سرورهای MCP را به سرعت مستقر، مدیریت و با خدمات Azure AI، داده و امنیت یکپارچه کنند، که باعث کاهش بار عملیاتی و تسریع پذیرش هوش مصنوعی می‌شود.

> **🎯 ابزار آماده تولید**  
> 
> این یک سرور MCP واقعی است که می‌توانید امروز استفاده کنید! درباره Azure AI Foundry MCP Server در [**راهنمای سرورهای MCP مایکروسافت**](microsoft-mcp-servers.md) بیشتر بدانید.

- میزبانی کامل سرور MCP با مدیریت خودکار مقیاس، نظارت و امنیت  
- یکپارچگی بومی با Azure OpenAI، Azure AI Search و سایر خدمات Azure  
- احراز هویت و مجوز سازمانی از طریق Microsoft Entra ID  
- پشتیبانی از ابزارهای سفارشی، قالب‌های پرامپت و کانکتورهای منابع  
- تطابق با الزامات امنیتی و مقرراتی سازمانی  

**پیاده‌سازی فنی:**  
```yaml
# Example: Azure MCP server deployment configuration (YAML)
apiVersion: mcp.microsoft.com/v1
kind: McpServer
metadata:
  name: enterprise-mcp-server
spec:
  modelProviders:
    - name: azure-openai
      type: AzureOpenAI
      endpoint: https://<your-openai-resource>.openai.azure.com/
      apiKeySecret: <your-azure-keyvault-secret>
  tools:
    - name: document_search
      type: AzureAISearch
      endpoint: https://<your-search-resource>.search.windows.net/
      apiKeySecret: <your-azure-keyvault-secret>
  authentication:
    type: EntraID
    tenantId: <your-tenant-id>
  monitoring:
    enabled: true
    logAnalyticsWorkspace: <your-log-analytics-id>
```

**نتایج:**  
- کاهش زمان رسیدن به ارزش برای پروژه‌های هوش مصنوعی سازمانی با ارائه پلتفرم سرور MCP آماده و مطمئن  
- ساده‌سازی ادغام LLMها، ابزارها و منابع داده سازمانی  
- افزایش امنیت، قابلیت مشاهده و کارایی عملیاتی برای بارهای کاری MCP  
- بهبود کیفیت کد با بهترین شیوه‌های Azure SDK و الگوهای احراز هویت به‌روز  

**مراجع:**  
- [مستندات Azure MCP](https://aka.ms/azmcp)  
- [مخزن GitHub Azure MCP Server](https://github.com/Azure/azure-mcp)  
- [خدمات هوش مصنوعی Azure](https://azure.microsoft.com/en-us/products/ai-services/)

### مطالعه موردی ۶: NLWeb – پروتکل رابط وب زبان طبیعی

NLWeb نمایانگر چشم‌انداز مایکروسافت برای ایجاد لایه‌ای بنیادی برای وب هوش مصنوعی است. هر نمونه NLWeb همچنین یک سرور MCP است که از یک متد اصلی به نام `ask` پشتیبانی می‌کند، که برای پرسیدن سوال به یک وب‌سایت به زبان طبیعی استفاده می‌شود. پاسخ بازگشتی از schema.org بهره می‌برد، یک واژگان پرکاربرد برای توصیف داده‌های وب. به طور کلی، MCP برای NLWeb همان نقشی را دارد که HTTP برای HTML.

**ویژگی‌های کلیدی:**  
- **لایه پروتکل:** پروتکل ساده برای ارتباط با وب‌سایت‌ها به زبان طبیعی  
- **فرمت schema.org:** استفاده از JSON و schema.org برای پاسخ‌های ساختاریافته و قابل خواندن توسط ماشین  
- **پیاده‌سازی جامعه:** پیاده‌سازی ساده برای سایت‌هایی که می‌توانند به صورت فهرستی از آیتم‌ها (محصولات، دستور غذا، جاذبه‌ها، نقدها و غیره) انتزاع شوند  
- **ویجت‌های رابط کاربری:** اجزای رابط کاربری آماده برای رابط‌های مکالمه‌ای  

**اجزای معماری:**  
1. **پروتکل:** API ساده REST برای پرسش‌های زبان طبیعی به وب‌سایت‌ها  
2. **پیاده‌سازی:** استفاده از نشانه‌گذاری و ساختار سایت موجود برای پاسخ‌های خودکار  
3. **ویجت‌های رابط کاربری:** اجزای آماده برای ادغام رابط‌های مکالمه‌ای  

**مزایا:**  
- امکان تعامل انسان با سایت و عامل با عامل  
- ارائه پاسخ‌های داده‌ای ساختاریافته که سیستم‌های هوش مصنوعی به آسانی می‌توانند پردازش کنند  
- استقرار سریع برای سایت‌هایی با ساختار محتوای مبتنی بر فهرست  
- رویکرد استاندارد برای دسترسی هوش مصنوعی به وب‌سایت‌ها  

**نتایج:**  
- ایجاد پایه‌ای برای استانداردهای تعامل وب-هوش مصنوعی  
- ساده‌سازی ساخت رابط‌های مکالمه‌ای برای سایت‌های محتوایی  
- افزایش قابلیت کشف و دسترسی محتوای وب برای سیستم‌های هوش مصنوعی  
- ترویج همکاری بین عوامل هوش مصنوعی و خدمات وب مختلف  

**مراجع:**  
- [مخزن GitHub NLWeb](https://github.com/microsoft/NlWeb)  
- [مستندات NLWeb](https://github.com/microsoft/NlWeb)

### مطالعه موردی ۷: Azure AI Foundry MCP Server – ادغام عامل هوش مصنوعی سازمانی

سرورهای Azure AI Foundry MCP نشان می‌دهند که چگونه MCP می‌تواند برای هماهنگی و مدیریت عوامل هوش مصنوعی و گردش‌های کاری در محیط‌های سازمانی استفاده شود. با ادغام MCP با Azure AI Foundry، سازمان‌ها می‌توانند تعاملات عامل را استاندارد کنند، از مدیریت گردش کار Foundry بهره ببرند و استقرارهای امن و مقیاس‌پذیر را تضمین کنند.

> **🎯 ابزار آماده تولید**  
> 
> این یک سرور MCP واقعی است که می‌توانید امروز استفاده کنید! درباره Azure AI Foundry MCP Server در [**راهنمای سرورهای MCP مایکروسافت**](microsoft-mcp-servers.md#9--azure-ai-foundry-mcp-server) بیشتر بدانید.

**ویژگی‌های کلیدی:**  
- دسترسی جامع به اکوسیستم هوش مصنوعی Azure، شامل کاتالوگ مدل‌ها و مدیریت استقرار  
- نمایه‌سازی دانش با Azure AI Search برای برنامه‌های RAG  
- ابزارهای ارزیابی عملکرد مدل هوش مصنوعی و تضمین کیفیت  
- یکپارچگی با Azure AI Foundry Catalog و Labs برای مدل‌های تحقیقاتی پیشرفته  
- قابلیت‌های مدیریت و ارزیابی عامل برای سناریوهای تولید  

**نتایج:**  
- نمونه‌سازی سریع و نظارت قوی بر گردش‌های کاری عوامل هوش مصنوعی  
- ادغام بی‌وقفه با خدمات هوش مصنوعی Azure برای سناریوهای پیشرفته  
- رابط یکپارچه برای ساخت، استقرار و نظارت بر خطوط لوله عامل  
- بهبود امنیت، تطابق و کارایی عملیاتی برای سازمان‌ها  
- تسریع پذیرش هوش مصنوعی در حالی که کنترل فرآیندهای پیچیده عامل‌محور حفظ می‌شود  

**مراجع:**  
- [مخزن GitHub Azure AI Foundry MCP Server](https://github.com/azure-ai-foundry/mcp-foundry)  
- [ادغام عوامل هوش مصنوعی Azure با MCP (وبلاگ Microsoft Foundry)](https://devblogs.microsoft.com/foundry/integrating-azure-ai-agents-mcp/)

### مطالعه موردی ۸: Foundry MCP Playground – آزمایش و نمونه‌سازی

Foundry MCP Playground محیطی آماده برای آزمایش سرورهای MCP و ادغام‌های Azure AI Foundry فراهم می‌کند. توسعه‌دهندگان می‌توانند به سرعت مدل‌های هوش مصنوعی و گردش‌های کاری عامل را نمونه‌سازی، تست و ارزیابی کنند با استفاده از منابع کاتالوگ و آزمایشگاه‌های Azure AI Foundry. این محیط راه‌اندازی را ساده می‌کند، پروژه‌های نمونه ارائه می‌دهد و از توسعه مشارکتی پشتیبانی می‌کند، که کاوش بهترین روش‌ها و سناریوهای جدید را با کمترین پیچیدگی ممکن می‌سازد. این ابزار به ویژه برای تیم‌هایی مفید است که می‌خواهند ایده‌ها را اعتبارسنجی کنند، آزمایش‌ها را به اشتراک بگذارند و یادگیری را تسریع کنند بدون نیاز به زیرساخت پیچیده. با کاهش موانع ورود، این محیط به نوآوری و مشارکت جامعه در اکوسیستم MCP و Azure AI Foundry کمک می‌کند.

**مراجع:**  
- [مخزن GitHub Foundry MCP Playground](https://github.com/azure-ai-foundry/foundry-mcp-playground)

### مطالعه موردی ۹: Microsoft Learn Docs MCP Server – دسترسی به مستندات با هوش مصنوعی

سرور Microsoft Learn Docs MCP یک سرویس میزبانی ابری است که به دستیارهای هوش مصنوعی امکان دسترسی بلادرنگ به مستندات رسمی مایکروسافت را از طریق Model Context Protocol می‌دهد. این سرور آماده تولید به اکوسیستم جامع Microsoft Learn متصل است و جستجوی معنایی در تمام منابع رسمی مایکروسافت را ممکن می‌سازد.
> **🎯 ابزاری آماده برای تولید**
> 
> این یک سرور واقعی MCP است که می‌توانید همین امروز از آن استفاده کنید! برای اطلاعات بیشتر درباره سرور MCP مستندات Microsoft Learn، به [**راهنمای سرورهای MCP مایکروسافت**](microsoft-mcp-servers.md#1--microsoft-learn-docs-mcp-server) مراجعه کنید.
**ویژگی‌های کلیدی:**
- دسترسی بلادرنگ به مستندات رسمی مایکروسافت، مستندات Azure و مستندات Microsoft 365  
- قابلیت‌های پیشرفته جستجوی معنایی که زمینه و هدف را درک می‌کنند  
- اطلاعات همیشه به‌روز با انتشار محتوای Microsoft Learn  
- پوشش جامع در سراسر Microsoft Learn، مستندات Azure و منابع Microsoft 365  
- بازگرداندن تا ۱۰ بخش محتوای باکیفیت همراه با عناوین مقالات و URLها  

**چرا این موضوع حیاتی است:**  
- حل مشکل «دانش قدیمی هوش مصنوعی» برای فناوری‌های مایکروسافت  
- اطمینان از دسترسی دستیاران هوش مصنوعی به جدیدترین ویژگی‌های .NET، C#، Azure و Microsoft 365  
- ارائه اطلاعات معتبر و رسمی برای تولید دقیق کد  
- ضروری برای توسعه‌دهندگانی که با فناوری‌های مایکروسافت در حال تحول سریع کار می‌کنند  

**نتایج:**  
- بهبود چشمگیر دقت کد تولید شده توسط هوش مصنوعی برای فناوری‌های مایکروسافت  
- کاهش زمان صرف شده برای جستجوی مستندات به‌روز و بهترین شیوه‌ها  
- افزایش بهره‌وری توسعه‌دهنده با بازیابی مستندات آگاه به زمینه  
- ادغام بی‌وقفه با جریان‌های کاری توسعه بدون ترک محیط IDE  

**مراجع:**  
- [Microsoft Learn Docs MCP Server GitHub Repository](https://github.com/MicrosoftDocs/mcp)  
- [Microsoft Learn Documentation](https://learn.microsoft.com/)  

## پروژه‌های عملی

### پروژه ۱: ساخت یک سرور MCP چند ارائه‌دهنده

**هدف:** ایجاد یک سرور MCP که بتواند درخواست‌ها را بر اساس معیارهای مشخص به چند ارائه‌دهنده مدل هوش مصنوعی هدایت کند.

**نیازمندی‌ها:**  
- پشتیبانی از حداقل سه ارائه‌دهنده مدل مختلف (مثلاً OpenAI، Anthropic، مدل‌های محلی)  
- پیاده‌سازی مکانیزم مسیریابی بر اساس متادیتای درخواست  
- ایجاد سیستم پیکربندی برای مدیریت اطلاعات احراز هویت ارائه‌دهندگان  
- افزودن کش برای بهینه‌سازی عملکرد و هزینه‌ها  
- ساخت داشبورد ساده برای نظارت بر استفاده  

**مراحل پیاده‌سازی:**  
1. راه‌اندازی زیرساخت پایه سرور MCP  
2. پیاده‌سازی آداپتورهای ارائه‌دهنده برای هر سرویس مدل هوش مصنوعی  
3. ایجاد منطق مسیریابی بر اساس ویژگی‌های درخواست  
4. افزودن مکانیزم‌های کش برای درخواست‌های پرتکرار  
5. توسعه داشبورد نظارتی  
6. تست با الگوهای مختلف درخواست  

**فناوری‌ها:** انتخاب از بین Python (.NET/Java/Python بر اساس ترجیح شما)، Redis برای کش، و یک فریم‌ورک وب ساده برای داشبورد.  

### پروژه ۲: سیستم مدیریت پرامپت سازمانی

**هدف:** توسعه سیستمی مبتنی بر MCP برای مدیریت، نسخه‌بندی و استقرار قالب‌های پرامپت در سراسر سازمان.

**نیازمندی‌ها:**  
- ایجاد مخزن مرکزی برای قالب‌های پرامپت  
- پیاده‌سازی نسخه‌بندی و گردش کار تأیید  
- ساخت قابلیت‌های تست قالب با ورودی‌های نمونه  
- توسعه کنترل‌های دسترسی مبتنی بر نقش  
- ایجاد API برای بازیابی و استقرار قالب‌ها  

**مراحل پیاده‌سازی:**  
1. طراحی ساختار پایگاه داده برای ذخیره قالب‌ها  
2. ایجاد API اصلی برای عملیات CRUD قالب‌ها  
3. پیاده‌سازی سیستم نسخه‌بندی  
4. ساخت گردش کار تأیید  
5. توسعه چارچوب تست  
6. ایجاد رابط وب ساده برای مدیریت  
7. ادغام با سرور MCP  

**فناوری‌ها:** انتخاب فریم‌ورک بک‌اند، پایگاه داده SQL یا NoSQL، و فریم‌ورک فرانت‌اند برای رابط مدیریت.  

### پروژه ۳: پلتفرم تولید محتوا مبتنی بر MCP

**هدف:** ساخت پلتفرمی برای تولید محتوا که با استفاده از MCP نتایج یکسانی در انواع مختلف محتوا ارائه دهد.

**نیازمندی‌ها:**  
- پشتیبانی از فرمت‌های مختلف محتوا (مقالات وبلاگ، شبکه‌های اجتماعی، متن‌های بازاریابی)  
- پیاده‌سازی تولید مبتنی بر قالب با گزینه‌های سفارشی‌سازی  
- ایجاد سیستم بازبینی و بازخورد محتوا  
- ردیابی معیارهای عملکرد محتوا  
- پشتیبانی از نسخه‌بندی و تکرار محتوا  

**مراحل پیاده‌سازی:**  
1. راه‌اندازی زیرساخت کلاینت MCP  
2. ایجاد قالب‌ها برای انواع مختلف محتوا  
3. ساخت خط تولید تولید محتوا  
4. پیاده‌سازی سیستم بازبینی  
5. توسعه سیستم ردیابی معیارها  
6. ایجاد رابط کاربری برای مدیریت قالب‌ها و تولید محتوا  

**فناوری‌ها:** زبان برنامه‌نویسی، فریم‌ورک وب و سیستم پایگاه داده مورد علاقه شما.  

## جهت‌گیری‌های آینده فناوری MCP

### روندهای نوظهور

1. **MCP چندرسانه‌ای**  
   - گسترش MCP برای استانداردسازی تعامل با مدل‌های تصویر، صدا و ویدئو  
   - توسعه قابلیت‌های استدلال میان‌رسانه‌ای  
   - قالب‌های پرامپت استاندارد برای مدالیته‌های مختلف  

2. **زیرساخت فدرال MCP**  
   - شبکه‌های توزیع‌شده MCP که منابع را بین سازمان‌ها به اشتراک می‌گذارند  
   - پروتکل‌های استاندارد برای اشتراک‌گذاری امن مدل‌ها  
   - تکنیک‌های محاسبات حفظ حریم خصوصی  

3. **بازارهای MCP**  
   - اکوسیستم‌هایی برای به اشتراک‌گذاری و کسب درآمد از قالب‌ها و افزونه‌های MCP  
   - فرآیندهای تضمین کیفیت و صدور گواهی  
   - ادغام با بازارهای مدل  

4. **MCP برای محاسبات لبه‌ای**  
   - تطبیق استانداردهای MCP برای دستگاه‌های لبه‌ای با منابع محدود  
   - پروتکل‌های بهینه‌شده برای محیط‌های با پهنای باند کم  
   - پیاده‌سازی‌های تخصصی MCP برای اکوسیستم‌های IoT  

5. **چارچوب‌های نظارتی**  
   - توسعه افزونه‌های MCP برای انطباق با مقررات  
   - مسیرهای حسابرسی استاندارد و رابط‌های توضیح‌پذیری  
   - ادغام با چارچوب‌های حاکمیت هوش مصنوعی نوظهور  

### راهکارهای MCP از مایکروسافت

مایکروسافت و Azure چندین مخزن متن‌باز توسعه داده‌اند تا به توسعه‌دهندگان در پیاده‌سازی MCP در سناریوهای مختلف کمک کنند:

#### سازمان Microsoft  
1. [playwright-mcp](https://github.com/microsoft/playwright-mcp) - سرور MCP برای Playwright جهت اتوماسیون و تست مرورگر  
2. [files-mcp-server](https://github.com/microsoft/files-mcp-server) - پیاده‌سازی سرور MCP برای OneDrive جهت تست محلی و مشارکت جامعه  
3. [NLWeb](https://github.com/microsoft/NlWeb) - مجموعه‌ای از پروتکل‌های باز و ابزارهای متن‌باز مرتبط با آن، با تمرکز بر ایجاد لایه پایه برای وب هوش مصنوعی  

#### سازمان Azure-Samples  
1. [mcp](https://github.com/Azure-Samples/mcp) - لینک به نمونه‌ها، ابزارها و منابع برای ساخت و ادغام سرورهای MCP در Azure با زبان‌های مختلف  
2. [mcp-auth-servers](https://github.com/Azure-Samples/mcp-auth-servers) - سرورهای مرجع MCP که احراز هویت را با مشخصات فعلی Model Context Protocol نشان می‌دهند  
3. [remote-mcp-functions](https://github.com/Azure-Samples/remote-mcp-functions) - صفحه فرود برای پیاده‌سازی‌های سرور MCP از راه دور در Azure Functions با لینک به مخازن زبان‌های مختلف  
4. [remote-mcp-functions-python](https://github.com/Azure-Samples/remote-mcp-functions-python) - قالب شروع سریع برای ساخت و استقرار سرورهای MCP سفارشی با Python در Azure Functions  
5. [remote-mcp-functions-dotnet](https://github.com/Azure-Samples/remote-mcp-functions-dotnet) - قالب شروع سریع برای ساخت و استقرار سرورهای MCP سفارشی با .NET/C# در Azure Functions  
6. [remote-mcp-functions-typescript](https://github.com/Azure-Samples/remote-mcp-functions-typescript) - قالب شروع سریع برای ساخت و استقرار سرورهای MCP سفارشی با TypeScript در Azure Functions  
7. [remote-mcp-apim-functions-python](https://github.com/Azure-Samples/remote-mcp-apim-functions-python) - مدیریت API Azure به عنوان دروازه AI برای سرورهای MCP از راه دور با Python  
8. [AI-Gateway](https://github.com/Azure-Samples/AI-Gateway) - آزمایش‌های APIM ❤️ AI شامل قابلیت‌های MCP، ادغام با Azure OpenAI و AI Foundry  

این مخازن پیاده‌سازی‌ها، قالب‌ها و منابع متنوعی برای کار با Model Context Protocol در زبان‌های برنامه‌نویسی و سرویس‌های مختلف Azure ارائه می‌دهند. آن‌ها طیف وسیعی از موارد استفاده از پیاده‌سازی‌های پایه سرور تا احراز هویت، استقرار ابری و سناریوهای ادغام سازمانی را پوشش می‌دهند.  

#### دایرکتوری منابع MCP

دایرکتوری [MCP Resources](https://github.com/microsoft/mcp/tree/main/Resources) در مخزن رسمی MCP مایکروسافت مجموعه‌ای منتخب از نمونه منابع، قالب‌های پرامپت و تعاریف ابزار برای استفاده با سرورهای Model Context Protocol فراهم می‌کند. این دایرکتوری به توسعه‌دهندگان کمک می‌کند تا سریع‌تر با MCP شروع کنند و بلوک‌های ساختمانی قابل استفاده مجدد و نمونه‌های بهترین شیوه را ارائه می‌دهد برای:  

- **قالب‌های پرامپت:** قالب‌های آماده برای وظایف و سناریوهای رایج هوش مصنوعی که می‌توان آن‌ها را برای پیاده‌سازی‌های سرور MCP خود تطبیق داد.  
- **تعاریف ابزار:** نمونه‌های اسکیمای ابزار و متادیتا برای استانداردسازی ادغام و فراخوانی ابزارها در سرورهای مختلف MCP.  
- **نمونه‌های منابع:** تعاریف نمونه منابع برای اتصال به منابع داده، APIها و سرویس‌های خارجی در چارچوب MCP.  
- **پیاده‌سازی‌های مرجع:** نمونه‌های عملی که نشان می‌دهند چگونه منابع، پرامپت‌ها و ابزارها را در پروژه‌های واقعی MCP ساختاربندی و سازماندهی کنیم.  

این منابع توسعه را تسریع می‌کنند، استانداردسازی را ترویج می‌دهند و به تضمین بهترین شیوه‌ها در ساخت و استقرار راهکارهای مبتنی بر MCP کمک می‌کنند.  

#### دایرکتوری منابع MCP  
- [MCP Resources (Sample Prompts, Tools, and Resource Definitions)](https://github.com/microsoft/mcp/tree/main/Resources)  

### فرصت‌های پژوهشی

- تکنیک‌های بهینه‌سازی مؤثر پرامپت در چارچوب‌های MCP  
- مدل‌های امنیتی برای استقرارهای چند مستاجری MCP  
- بنچمارک عملکرد در پیاده‌سازی‌های مختلف MCP  
- روش‌های تأیید رسمی برای سرورهای MCP  

## نتیجه‌گیری

پروتکل مدل کانتکست (MCP) به سرعت آینده یکپارچه‌سازی استاندارد، امن و قابل همکاری هوش مصنوعی در صنایع مختلف را شکل می‌دهد. از طریق مطالعات موردی و پروژه‌های عملی این درس، مشاهده کردید که چگونه پذیرندگان اولیه—از جمله مایکروسافت و Azure—از MCP برای حل چالش‌های دنیای واقعی، تسریع پذیرش هوش مصنوعی و تضمین انطباق، امنیت و مقیاس‌پذیری استفاده می‌کنند. رویکرد مدولار MCP به سازمان‌ها امکان می‌دهد مدل‌های زبان بزرگ، ابزارها و داده‌های سازمانی را در چارچوبی یکپارچه و قابل حسابرسی متصل کنند. با ادامه تکامل MCP، مشارکت در جامعه، کاوش منابع متن‌باز و به‌کارگیری بهترین شیوه‌ها کلید ساخت راهکارهای هوش مصنوعی مقاوم و آماده آینده خواهد بود.  

## منابع اضافی

- [MCP Foundry GitHub Repository](https://github.com/azure-ai-foundry/mcp-foundry)  
- [Foundry MCP Playground](https://github.com/azure-ai-foundry/foundry-mcp-playground)  
- [Integrating Azure AI Agents with MCP (Microsoft Foundry Blog)](https://devblogs.microsoft.com/foundry/integrating-azure-ai-agents-mcp/)  
- [MCP GitHub Repository (Microsoft)](https://github.com/microsoft/mcp)  
- [MCP Resources Directory (Sample Prompts, Tools, and Resource Definitions)](https://github.com/microsoft/mcp/tree/main/Resources)  
- [MCP Community & Documentation](https://modelcontextprotocol.io/introduction)  
- [Azure MCP Documentation](https://aka.ms/azmcp)  
- [Playwright MCP Server GitHub Repository](https://github.com/microsoft/playwright-mcp)  
- [Files MCP Server (OneDrive)](https://github.com/microsoft/files-mcp-server)  
- [Azure-Samples MCP](https://github.com/Azure-Samples/mcp)  
- [MCP Auth Servers (Azure-Samples)](https://github.com/Azure-Samples/mcp-auth-servers)  
- [Remote MCP Functions (Azure-Samples)](https://github.com/Azure-Samples/remote-mcp-functions)  
- [Remote MCP Functions Python (Azure-Samples)](https://github.com/Azure-Samples/remote-mcp-functions-python)  
- [Remote MCP Functions .NET (Azure-Samples)](https://github.com/Azure-Samples/remote-mcp-functions-dotnet)  
- [Remote MCP Functions TypeScript (Azure-Samples)](https://github.com/Azure-Samples/remote-mcp-functions-typescript)  
- [Remote MCP APIM Functions Python (Azure-Samples)](https://github.com/Azure-Samples/remote-mcp-apim-functions-python)  
- [AI-Gateway (Azure-Samples)](https://github.com/Azure-Samples/AI-Gateway)  
- [Microsoft AI and Automation Solutions](https://azure.microsoft.com/en-us/products/ai-services/)  

## تمرین‌ها

1. یکی از مطالعات موردی را تحلیل کنید و رویکرد پیاده‌سازی جایگزینی پیشنهاد دهید.  
2. یکی از ایده‌های پروژه را انتخاب کرده و مشخصات فنی دقیقی تهیه کنید.  
3. صنعتی که در مطالعات موردی پوشش داده نشده را بررسی کنید و شرح دهید چگونه MCP می‌تواند چالش‌های خاص آن را حل کند.  
4. یکی از جهت‌گیری‌های آینده را کاوش کرده و مفهومی برای افزونه جدید MCP جهت پشتیبانی از آن ایجاد کنید.  

بعدی: [Microsoft MCP Server](../07-LessonsfromEarlyAdoption/microsoft-mcp-servers.md)

**سلب مسئولیت**:  
این سند با استفاده از سرویس ترجمه هوش مصنوعی [Co-op Translator](https://github.com/Azure/co-op-translator) ترجمه شده است. در حالی که ما در تلاش برای دقت هستیم، لطفاً توجه داشته باشید که ترجمه‌های خودکار ممکن است حاوی خطاها یا نواقصی باشند. سند اصلی به زبان بومی خود باید به عنوان منبع معتبر در نظر گرفته شود. برای اطلاعات حیاتی، ترجمه حرفه‌ای انسانی توصیه می‌شود. ما مسئول هیچ گونه سوءتفاهم یا تفسیر نادرستی که از استفاده این ترجمه ناشی شود، نیستیم.