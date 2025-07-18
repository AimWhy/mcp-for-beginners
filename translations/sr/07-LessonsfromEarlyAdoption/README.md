<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "6755bc4f6d0293ce6c49cfc5efba0d8e",
  "translation_date": "2025-07-18T10:29:17+00:00",
  "source_file": "07-LessonsfromEarlyAdoption/README.md",
  "language_code": "sr"
}
-->
# 🌟 Учионице од раних корисника

## 🎯 Шта овај модул обухвата

Овај модул истражује како стварне организације и програмери користе Model Context Protocol (MCP) да реше конкретне изазове и подстакну иновације. Кроз детаљне студије случаја и практичне пројекте, открићете како MCP омогућава безбедну, скалабилну интеграцију вештачке интелигенције која повезује језичке моделе, алате и корпоративне податке.

### 📚 Погледајте MCP у пракси

Желите да видите како се ови принципи примењују у алатима спремним за производњу? Погледајте наш [**10 Microsoft MCP сервера који трансформишу продуктивност програмера**](microsoft-mcp-servers.md), који приказује стварне Microsoft MCP сервере које можете користити већ данас.

## Преглед

Ова лекција истражује како су рани корисници искористили Model Context Protocol (MCP) да реше стварне изазове и подстакну иновације у различитим индустријама. Кроз детаљне студије случаја и практичне пројекте, видећете како MCP омогућава стандардизовану, безбедну и скалабилну интеграцију вештачке интелигенције — повезујући велике језичке моделе, алате и корпоративне податке у јединственом оквиру. Стекнућете практично искуство у дизајнирању и изградњи решења заснованих на MCP-у, научити проверене шаблоне имплементације и открити најбоље праксе за примену MCP-а у продукцијским окружењима. Лекција такође истиче нове трендове, будуће смернице и ресурсе отвореног кода који ће вам помоћи да останете на челу MCP технологије и њеног развијајућег екосистема.

## Циљеви учења

- Анализирати стварне имплементације MCP-а у различитим индустријама  
- Дизајнирати и изградити комплетне апликације засноване на MCP-у  
- Истражити нове трендове и будуће смернице у MCP технологији  
- Применити најбоље праксе у стварним развојним сценаријима  

## Стварне имплементације MCP-а

### Студија случаја 1: Аутоматизација корисничке подршке у предузећима

Мултинационална корпорација је имплементирала решење засновано на MCP-у како би стандардизовала интеракције вештачке интелигенције у својим системима корисничке подршке. Ово им је омогућило да:

- Креирају јединствен интерфејс за више LLM провајдера  
- Одржавају доследно управљање упитима у различитим одељењима  
- Имплементирају робусне безбедносне и регулаторне контроле  
- Лако пребацују између различитих AI модела према специфичним потребама  

**Техничка имплементација:**  
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

**Резултати:** 30% смањење трошкова модела, 45% побољшање конзистентности одговора и унапређена усаглашеност у глобалним операцијама.

### Студија случаја 2: Дијагностички асистент у здравству

Здравствена установа је развила MCP инфраструктуру за интеграцију више специјализованих медицинских AI модела уз обезбеђивање заштите осетљивих података пацијената:

- Беспрекорно пребацивање између општих и специјализованих медицинских модела  
- Строге контроле приватности и ревизионе трагове  
- Интеграција са постојећим системима електронских здравствених евиденција (EHR)  
- Доследно креирање упита за медицинску терминологију  

**Техничка имплементација:**  
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

**Резултати:** Побољшани дијагностички предлози за лекаре уз пуну HIPAA усаглашеност и значајно смањење пребацивања контекста између система.

### Студија случаја 3: Анализа ризика у финансијским услугама

Финансијска институција је имплементирала MCP како би стандардизовала процесе анализе ризика у различитим одељењима:

- Креиран јединствен интерфејс за моделе кредитног ризика, детекције преваре и инвестиционог ризика  
- Имплементиране строге контроле приступа и верзионисање модела  
- Обезбеђена ревизија свих AI препорука  
- Одржана доследна форматација података у различитим системима  

**Техничка имплементација:**  
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

**Резултати:** Побољшана регулаторна усаглашеност, 40% бржи циклуси имплементације модела и унапређена конзистентност процене ризика у одељењима.

### Студија случаја 4: Microsoft Playwright MCP сервер за аутоматизацију прегледача

Microsoft је развио [Playwright MCP сервер](https://github.com/microsoft/playwright-mcp) који омогућава безбедну, стандардизовану аутоматизацију прегледача преко Model Context Protocol-а. Овај сервер спреман за производњу омогућава AI агентима и LLM-овима да интерагују са веб прегледачима на контролисан, ревидирајући и проширив начин — омогућавајући примене као што су аутоматизовано тестирање веба, екстракција података и крај-до-крај радни токови.

> **🎯 Алат спреман за производњу**  
> Ова студија случаја приказује стварни MCP сервер који можете користити већ данас! Сазнајте више о Playwright MCP серверу и још 9 других Microsoft MCP сервера у нашем [**Microsoft MCP Servers Guide**](microsoft-mcp-servers.md#8--playwright-mcp-server).

**Кључне карактеристике:**  
- Излаже могућности аутоматизације прегледача (навигација, попуњавање формулара, снимање екрана итд.) као MCP алате  
- Имплементира строге контроле приступа и sandboxing како би спречио неовлашћене радње  
- Обезбеђује детаљне ревизијске записе за све интеракције са прегледачем  
- Подржава интеграцију са Azure OpenAI и другим LLM провајдерима за аутоматизацију вођену агентима  
- Покреће GitHub Copilot Coding Agent са могућностима веб прегледања  

**Техничка имплементација:**  
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

**Резултати:**  
- Омогућена безбедна, програмска аутоматизација прегледача за AI агенте и LLM-ове  
- Смањен ручни напор у тестирању и побољшано покривање тестова за веб апликације  
- Обезбеђен поновљив и проширив оквир за интеграцију алата заснованих на прегледачу у корпоративним окружењима  
- Покреће могућности веб прегледања GitHub Copilota  

**Референце:**  
- [Playwright MCP Server GitHub репозиторијум](https://github.com/microsoft/playwright-mcp)  
- [Microsoft AI and Automation Solutions](https://azure.microsoft.com/en-us/products/ai-services/)

### Студија случаја 5: Azure MCP – Model Context Protocol као услуга за предузећа

Azure MCP сервер ([https://aka.ms/azmcp](https://aka.ms/azmcp)) је Microsoft-ова управљана, корпоративна имплементација Model Context Protocol-а, дизајнирана да пружи скалабилне, безбедне и усаглашене MCP сервер капацитете као cloud услугу. Azure MCP омогућава организацијама брзо распоређивање, управљање и интеграцију MCP сервера са Azure AI, подацима и безбедносним сервисима, смањујући оперативне трошкове и убрзавајући усвајање AI технологија.

> **🎯 Алат спреман за производњу**  
> Ово је стварни MCP сервер који можете користити већ данас! Сазнајте више о Azure AI Foundry MCP серверу у нашем [**Microsoft MCP Servers Guide**](microsoft-mcp-servers.md).

- Потпуно управљано хостовање MCP сервера са уграђеним скалирањем, мониторингом и безбедношћу  
- Нативна интеграција са Azure OpenAI, Azure AI Search и другим Azure сервисима  
- Корпоративна аутентификација и ауторизација преко Microsoft Entra ID  
- Подршка за прилагођене алате, шаблоне упита и конекторе ресурса  
- Усаглашеност са корпоративним безбедносним и регулаторним захтевима  

**Техничка имплементација:**  
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

**Резултати:**  
- Скратило време до вредности за корпоративне AI пројекте пружајући спремну, усаглашену MCP сервер платформу  
- Поједностављена интеграција LLM-ова, алата и извора корпоративних података  
- Побољшана безбедност, посматрање и оперативна ефикасност за MCP радне оптерећења  
- Унапређен квалитет кода уз најбоље праксе Azure SDK-а и актуелне аутентификационе шаблоне  

**Референце:**  
- [Azure MCP документација](https://aka.ms/azmcp)  
- [Azure MCP Server GitHub репозиторијум](https://github.com/Azure/azure-mcp)  
- [Azure AI Services](https://azure.microsoft.com/en-us/products/ai-services/)

### Студија случаја 6: NLWeb – Протокол природног језичког веб интерфејса

NLWeb представља Microsoft-ову визију успостављања основног слоја за AI веб. Сваки NLWeb инстанца је такође MCP сервер који подржава једну основну методу, `ask`, која се користи за постављање питања веб сајту на природном језику. Враћени одговор користи schema.org, широко коришћен вокабулар за описивање веб података. У слободном преводу, MCP је за NLWeb као што је HTTP за HTML.

**Кључне карактеристике:**  
- **Протоколски слој:** Једноставан протокол за комуникацију са веб сајтовима на природном језику  
- **Schema.org формат:** Користи JSON и schema.org за структуриране, машински читљиве одговоре  
- **Заједничка имплементација:** Једноставна имплементација за сајтове који се могу апстраховати као листе ставки (производи, рецепти, атракције, рецензије итд.)  
- **UI видгети:** Унапред направљени кориснички интерфејс за конверзацијске интерфејсе  

**Компоненте архитектуре:**  
1. **Протокол:** Једноставан REST API за природне језичке упите ка веб сајтовима  
2. **Имплементација:** Користи постојећу структуру и ознаке сајта за аутоматизоване одговоре  
3. **UI видгети:** Спремни за употребу компоненти за интеграцију конверзацијских интерфејса  

**Предности:**  
- Омогућава интеракцију човек-сајт и агент-агент  
- Пружа структуриране одговоре које AI системи лако обрађују  
- Брза имплементација за сајтове са садржајем у облику листа  
- Стандардизован приступ за омогућавање AI приступа веб сајтовима  

**Резултати:**  
- Успостављена основа за стандарде интеракције AI и веба  
- Поједностављено креирање конверзацијских интерфејса за сајтове са садржајем  
- Побољшана откривеност и приступачност веб садржаја за AI системе  
- Подстакнута интероперабилност између различитих AI агената и веб сервиса  

**Референце:**  
- [NLWeb GitHub репозиторијум](https://github.com/microsoft/NlWeb)  
- [NLWeb документација](https://github.com/microsoft/NlWeb)

### Студија случаја 7: Azure AI Foundry MCP сервер – Интеграција AI агената у предузећима

Azure AI Foundry MCP сервери показују како се MCP може користити за оркестрацију и управљање AI агентима и радним токовима у корпоративним окружењима. Интеграцијом MCP-а са Azure AI Foundry, организације могу стандардизовати интеракције агената, користити Foundry за управљање радним токовима и обезбедити безбедна, скалабилна решења.

> **🎯 Алат спреман за производњу**  
> Ово је стварни MCP сервер који можете користити већ данас! Сазнајте више о Azure AI Foundry MCP серверу у нашем [**Microsoft MCP Servers Guide**](microsoft-mcp-servers.md#9--azure-ai-foundry-mcp-server).

**Кључне карактеристике:**  
- Комплетан приступ Azure AI екосистему, укључујући каталоге модела и управљање распоређивањем  
- Индексирање знања уз Azure AI Search за RAG апликације  
- Алати за процену перформанси AI модела и контролу квалитета  
- Интеграција са Azure AI Foundry Catalog и Labs за најсавременије истраживачке моделе  
- Управљање агентима и могућности процене за продукцијске сценарије  

**Резултати:**  
- Брзо прототиповање и робусно праћење радних токова AI агената  
- Беспрекорна интеграција са Azure AI сервисима за напредне сценарије  
- Јединствени интерфејс за изградњу, распоређивање и праћење агената  
- Побољшана безбедност, усаглашеност и оперативна ефикасност у предузећима  
- Убрзано усвајање AI технологија уз контролу сложених процеса вођених агентима  

**Референце:**  
- [Azure AI Foundry MCP Server GitHub репозиторијум](https://github.com/azure-ai-foundry/mcp-foundry)  
- [Интеграција Azure AI агената са MCP (Microsoft Foundry блог)](https://devblogs.microsoft.com/foundry/integrating-azure-ai-agents-mcp/)

### Студија случаја 8: Foundry MCP Playground – Експериментисање и прототиповање

Foundry MCP Playground нуди спремно окружење за експериментисање са MCP серверима и интеграцијама Azure AI Foundry. Програмери могу брзо прототиповати, тестирати и процењивати AI моделе и радне токове агената користећи ресурсе из Azure AI Foundry Catalog и Labs. Playground поједностављује подешавање, пружа примерке пројеката и подржава колаборативни развој, олакшавајући истраживање најбољих пракси и нових сценарија уз минималан напор. Посебно је користан тимовима који желе да верификују идеје, деле експерименте и убрзају учење без потребе за сложеном инфраструктуром. Смањењем баријера за улазак, playground подстиче иновације и доприносе заједнице у MCP и Azure AI Foundry екосистему.

**Референце:**  
- [Foundry MCP Playground GitHub репозиторијум](https://github.com/azure-ai-foundry/foundry-mcp-playground)

### Студија случаја 9: Microsoft Learn Docs MCP сервер – Приступ документацији уз помоћ AI

Microsoft Learn Docs MCP сервер је cloud сервис који пружа AI асистентима приступ званичној Microsoft документацији у реалном времену преко Model Context Protocol-а. Овај сервер спреман за производњу повезује се са свеобухват
> **🎯 Алат спреман за производњу**
> 
> Ово је прави MCP сервер који можете користити одмах! Сазнајте више о Microsoft Learn Docs MCP серверу у нашем [**Водичу за Microsoft MCP сервере**](microsoft-mcp-servers.md#1--microsoft-learn-docs-mcp-server).
**Кључне карактеристике:**
- Приступ у реалном времену званичној Microsoft документацији, Azure документацији и Microsoft 365 документацији
- Напредне семантичке претраге које разумеју контекст и намеру
- Увек ажуриране информације како се садржај Microsoft Learn објављује
- Обухватан приступ Microsoft Learn, Azure документацији и изворима Microsoft 365
- Враћа до 10 висококвалитетних делова садржаја са насловима чланака и URL адресама

**Зашто је критично:**
- Решава проблем „застарелог знања вештачке интелигенције“ за Microsoft технологије
- Обезбеђује да AI асистенти имају приступ најновијим функцијама .NET, C#, Azure и Microsoft 365
- Пружа ауторитетне, првокласне информације за прецизно генерисање кода
- Неопходно за програмере који раде са брзо развијајућим Microsoft технологијама

**Резултати:**
- Драстично побољшана прецизност AI-генерисаног кода за Microsoft технологије
- Смањено време проведено у претрази актуелне документације и најбољих пракси
- Побољшана продуктивност програмера уз документацију која разуме контекст
- Беспрекорна интеграција у развојне токове без напуштања IDE-а

**Референце:**
- [Microsoft Learn Docs MCP Server GitHub Repository](https://github.com/MicrosoftDocs/mcp)
- [Microsoft Learn Documentation](https://learn.microsoft.com/)

## Практични пројекти

### Пројекат 1: Изградња MCP сервера са више провајдера

**Циљ:** Креирати MCP сервер који може усмеравати захтеве ка више провајдера AI модела на основу одређених критеријума.

**Захтеви:**
- Подршка за најмање три различита провајдера модела (нпр. OpenAI, Anthropic, локални модели)
- Имплементација механизма усмеравања заснованог на метаподацима захтева
- Креирање система за конфигурацију и управљање акредитивима провајдера
- Додавање кеширања ради оптимизације перформанси и трошкова
- Изградња једноставне контролне табле за праћење коришћења

**Кораци имплементације:**
1. Поставити основну инфраструктуру MCP сервера
2. Имплементирати адаптере провајдера за сваки AI модел сервис
3. Креирати логику усмеравања на основу атрибута захтева
4. Додати механизме кеширања за честе захтеве
5. Развити контролну таблу за праћење
6. Тестирати са различитим обрасцима захтева

**Технологије:** Изаберите између Python (.NET/Java/Python према вашем избору), Redis за кеширање и једноставан веб фрејмворк за контролну таблу.

### Пројекат 2: Систем за управљање предлозима у предузећу

**Циљ:** Развити систем заснован на MCP-у за управљање, верзионисање и имплементацију шаблона предлога у организацији.

**Захтеви:**
- Креирати централизовани репозиторијум за шаблоне предлога
- Имплементирати верзионисање и процесе одобравања
- Изградити могућности тестирања шаблона са примерима уноса
- Развити контролу приступа засновану на улогама
- Креирати API за преузимање и имплементацију шаблона

**Кораци имплементације:**
1. Дизајнирати шему базе података за чување шаблона
2. Креирати основни API за CRUD операције над шаблонима
3. Имплементирати систем верзионисања
4. Изградити процес одобравања
5. Развити оквир за тестирање
6. Креирати једноставан веб интерфејс за управљање
7. Интегрисати са MCP сервером

**Технологије:** По избору backend фрејмворк, SQL или NoSQL база података и frontend фрејмворк за интерфејс за управљање.

### Пројекат 3: Платформа за генерисање садржаја заснована на MCP-у

**Циљ:** Изградити платформу за генерисање садржаја која користи MCP за доследне резултате у различитим типовима садржаја.

**Захтеви:**
- Подршка за више формата садржаја (блог постови, друштвени медији, маркетиншки текстови)
- Имплементација генерисања заснованог на шаблонима са опцијама прилагођавања
- Креирати систем за преглед и повратне информације о садржају
- Пратити метрике перформанси садржаја
- Подршка за верзионисање и итерацију садржаја

**Кораци имплементације:**
1. Поставити MCP клијентску инфраструктуру
2. Креирати шаблоне за различите типове садржаја
3. Изградити пипелине за генерисање садржаја
4. Имплементирати систем прегледа
5. Развити систем за праћење метрика
6. Креирати кориснички интерфејс за управљање шаблонима и генерисање садржаја

**Технологије:** Ваш омиљени програмски језик, веб фрејмворк и систем базе података.

## Будући правци MCP технологије

### Нови трендови

1. **Мултимодални MCP**
   - Проширење MCP-а за стандардизацију интеракција са моделима слика, звука и видеа
   - Развој способности крос-модалног резоновања
   - Стандардизовани формати предлога за различите модалитете

2. **Федерисана MCP инфраструктура**
   - Распоређене MCP мреже које могу делити ресурсе између организација
   - Стандардизовани протоколи за безбедно дељење модела
   - Технике рачунања које штите приватност

3. **MCP тржишта**
   - Екосистеми за дељење и монетизацију MCP шаблона и додатака
   - Процеси осигурања квалитета и сертификације
   - Интеграција са тржиштима модела

4. **MCP за Edge рачунарство**
   - Прилагођавање MCP стандарда за уређаје са ограниченим ресурсима
   - Оптимизовани протоколи за окружења са ниском пропусношћу
   - Специјализоване MCP имплементације за IoT екосистеме

5. **Регулаторни оквири**
   - Развој MCP проширења за усаглашеност са регулативама
   - Стандардизовани трагови ревизије и интерфејси за објашњивост
   - Интеграција са новим оквирима за управљање AI-јем

### MCP решења од Microsoft-а

Microsoft и Azure су развили неколико open-source репозиторијума који помажу програмерима да имплементирају MCP у различитим сценаријима:

#### Microsoft Organization
1. [playwright-mcp](https://github.com/microsoft/playwright-mcp) - Playwright MCP сервер за аутоматизацију и тестирање прегледача
2. [files-mcp-server](https://github.com/microsoft/files-mcp-server) - Имплементација OneDrive MCP сервера за локално тестирање и допринос заједници
3. [NLWeb](https://github.com/microsoft/NlWeb) - NLWeb је скуп отворених протокола и повезаних алата. Главни фокус је успостављање основног слоја за AI Web

#### Azure-Samples Organization
1. [mcp](https://github.com/Azure-Samples/mcp) - Линкови ка примерима, алатима и ресурсима за изградњу и интеграцију MCP сервера на Azure-у користећи више језика
2. [mcp-auth-servers](https://github.com/Azure-Samples/mcp-auth-servers) - Референтни MCP сервери који демонстрирају аутентификацију према тренутној спецификацији Model Context Protocol-а
3. [remote-mcp-functions](https://github.com/Azure-Samples/remote-mcp-functions) - Почетна страница за имплементације Remote MCP сервера у Azure Functions са линковима ка језичким репозиторijумима
4. [remote-mcp-functions-python](https://github.com/Azure-Samples/remote-mcp-functions-python) - Брзи почетак за изградњу и деплојовање прилагођених Remote MCP сервера користећи Azure Functions и Python
5. [remote-mcp-functions-dotnet](https://github.com/Azure-Samples/remote-mcp-functions-dotnet) - Брзи почетак за изградњу и деплојовање прилагођених Remote MCP сервера користећи Azure Functions и .NET/C#
6. [remote-mcp-functions-typescript](https://github.com/Azure-Samples/remote-mcp-functions-typescript) - Брзи почетак за изградњу и деплојовање прилагођених Remote MCP сервера користећи Azure Functions и TypeScript
7. [remote-mcp-apim-functions-python](https://github.com/Azure-Samples/remote-mcp-apim-functions-python) - Azure API Management као AI Gateway ка Remote MCP серверима користећи Python
8. [AI-Gateway](https://github.com/Azure-Samples/AI-Gateway) - APIM ❤️ AI експерименти укључујући MCP могућности, интеграцију са Azure OpenAI и AI Foundry

Ови репозиторијуми пружају различите имплементације, шаблоне и ресурсе за рад са Model Context Protocol-ом у различитим програмским језицима и Azure сервисима. Обухватају широк спектар употреба од основних сервера до аутентификације, cloud деплоја и интеграције у предузећима.

#### MCP Resources Directory

[Директоријум MCP Resources](https://github.com/microsoft/mcp/tree/main/Resources) у званичном Microsoft MCP репозиторијуму пружа курирани скуп примерка ресурса, шаблона предлога и дефиниција алата за коришћење са Model Context Protocol серверима. Овај директоријум је дизајниран да помогне програмерима да брзо почну са MCP-ом нудећи поновно употребљиве грађевинске блокове и примере најбољих пракси за:

- **Prompt Templates:** Спремни шаблони предлога за уобичајене AI задатке и сценарије, које можете прилагодити за своје MCP сервер имплементације.
- **Tool Definitions:** Примери шема алата и метаподатака за стандардизацију интеграције и позивања алата у различитим MCP серверима.
- **Resource Samples:** Примери дефиниција ресурса за повезивање са изворима података, API-јима и спољним сервисима у оквиру MCP оквира.
- **Reference Implementations:** Практични примери који показују како структуирати и организовати ресурсе, предлоге и алате у реалним MCP пројектима.

Ови ресурси убрзавају развој, промовишу стандардизацију и помажу у обезбеђивању најбољих пракси приликом изградње и имплементације решења заснованих на MCP-у.

#### MCP Resources Directory
- [MCP Resources (Sample Prompts, Tools, and Resource Definitions)](https://github.com/microsoft/mcp/tree/main/Resources)

### Истраживачке могућности

- Ефикасне технике оптимизације предлога у MCP оквирима
- Безбедносни модели за мулти-тенант MCP имплементације
- Поређење перформанси различитих MCP имплементација
- Формалне методе верификације MCP сервера

## Закључак

Model Context Protocol (MCP) брзо обликује будућност стандардизоване, безбедне и интероперабилне AI интеграције у различитим индустријама. Кроз студије случаја и практичне пројекте у овој лекцији, видели сте како рани корисници — укључујући Microsoft и Azure — користе MCP за решавање стварних изазова, убрзавање усвајања AI технологија и обезбеђивање усаглашености, безбедности и скалабилности. Модуларни приступ MCP-а омогућава организацијама да повежу велике језичке моделе, алате и податке предузећа у јединствени, ревидирани оквир. Како MCP наставља да се развија, ангажовање у заједници, истраживање open-source ресурса и примена најбољих пракси биће кључни за изградњу робусних, спремних за будућност AI решења.

## Додатни ресурси

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

## Вежбе

1. Анализирајте једну од студија случаја и предложите алтернативни приступ имплементацији.
2. Изаберите једну од идеја за пројекат и направите детаљну техничку спецификацију.
3. Истражите индустрију која није обухваћена студијама случаја и опишите како MCP може решити њене специфичне изазове.
4. Истражите један од будућих праваца и креирајте концепт новог MCP проширења које би га подржало.

Следеће: [Microsoft MCP Server](../07-LessonsfromEarlyAdoption/microsoft-mcp-servers.md)

**Одрицање од одговорности**:  
Овај документ је преведен коришћењем AI сервиса за превођење [Co-op Translator](https://github.com/Azure/co-op-translator). Иако тежимо прецизности, молимо вас да имате у виду да аутоматски преводи могу садржати грешке или нетачности. Оригинални документ на његовом изворном језику треба сматрати ауторитетним извором. За критичне информације препоручује се професионални људски превод. Нисмо одговорни за било каква неспоразума или погрешна тумачења која произилазе из коришћења овог превода.