<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "6755bc4f6d0293ce6c49cfc5efba0d8e",
  "translation_date": "2025-07-18T10:39:11+00:00",
  "source_file": "07-LessonsfromEarlyAdoption/README.md",
  "language_code": "uk"
}
-->
# 🌟 Уроки від ранніх користувачів

## 🎯 Що охоплює цей модуль

Цей модуль досліджує, як реальні організації та розробники використовують Model Context Protocol (MCP) для розв’язання реальних проблем і стимулювання інновацій. Через детальні кейс-стаді, практичні приклади, ви дізнаєтесь, як MCP забезпечує безпечну, масштабовану інтеграцію ШІ, що поєднує мовні моделі, інструменти та корпоративні дані.

### 📚 Побачити MCP у дії

Хочете побачити, як ці принципи застосовуються у готових до виробництва інструментах? Ознайомтеся з нашим [**переліком 10 Microsoft MCP серверів, які трансформують продуктивність розробників**](microsoft-mcp-servers.md), де представлені реальні Microsoft MCP сервери, які ви можете використовувати вже сьогодні.

## Огляд

У цьому уроці розглядається, як ранні користувачі застосували Model Context Protocol (MCP) для розв’язання реальних завдань і стимулювання інновацій у різних галузях. Через детальні кейс-стаді та практичні проєкти ви побачите, як MCP забезпечує стандартизовану, безпечну та масштабовану інтеграцію ШІ — поєднуючи великі мовні моделі, інструменти та корпоративні дані в єдиній системі. Ви отримаєте практичний досвід у проєктуванні та створенні рішень на основі MCP, навчитеся перевіреним патернам впровадження та дізнаєтесь найкращі практики розгортання MCP у виробничих середовищах. Урок також висвітлює нові тенденції, майбутні напрямки та відкриті ресурси, які допоможуть вам залишатися на передовій технології MCP та її розвитку.

## Цілі навчання

- Аналізувати реальні впровадження MCP у різних галузях
- Проєктувати та створювати повноцінні додатки на основі MCP
- Вивчати нові тенденції та майбутні напрямки розвитку MCP
- Застосовувати найкращі практики у реальних сценаріях розробки

## Реальні впровадження MCP

### Кейс-стаді 1: Автоматизація підтримки клієнтів у корпорації

Багатонаціональна корпорація впровадила рішення на основі MCP для стандартизації взаємодії ШІ у своїх системах підтримки клієнтів. Це дозволило їм:

- Створити уніфікований інтерфейс для кількох провайдерів LLM
- Підтримувати послідовне управління запитами у різних відділах
- Впровадити надійні заходи безпеки та відповідності
- Легко переключатися між різними моделями ШІ залежно від потреб

**Технічна реалізація:**  
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

**Результати:** Зниження витрат на моделі на 30%, покращення послідовності відповідей на 45% та підвищення відповідності вимогам у глобальних операціях.

### Кейс-стаді 2: Асистент діагностики у сфері охорони здоров’я

Медичний заклад розробив інфраструктуру MCP для інтеграції кількох спеціалізованих медичних моделей ШІ, забезпечуючи захист чутливих даних пацієнтів:

- Безшовне переключення між загальними та спеціалізованими медичними моделями
- Жорсткий контроль конфіденційності та ведення аудиту
- Інтеграція з існуючими системами електронних медичних записів (EHR)
- Послідовне формування запитів із медичною термінологією

**Технічна реалізація:**  
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

**Результати:** Покращені діагностичні рекомендації для лікарів при повній відповідності HIPAA та значне зменшення перемикання контекстів між системами.

### Кейс-стаді 3: Аналіз ризиків у фінансових послугах

Фінансова установа впровадила MCP для стандартизації процесів аналізу ризиків у різних відділах:

- Створено уніфікований інтерфейс для моделей кредитного ризику, виявлення шахрайства та інвестиційних ризиків
- Впроваджено суворий контроль доступу та версіонування моделей
- Забезпечено аудит усіх рекомендацій ШІ
- Підтримано послідовне форматування даних у різних системах

**Технічна реалізація:**  
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

**Результати:** Покращена відповідність регуляторним вимогам, на 40% швидший цикл розгортання моделей та підвищена послідовність оцінки ризиків у відділах.

### Кейс-стаді 4: Microsoft Playwright MCP Server для автоматизації браузера

Microsoft розробила [Playwright MCP server](https://github.com/microsoft/playwright-mcp) для забезпечення безпечної, стандартизованої автоматизації браузера через Model Context Protocol. Цей готовий до виробництва сервер дозволяє агентам ШІ та LLM взаємодіяти з веб-браузерами у контрольованому, аудиторському та розширюваному режимі — підтримуючи такі сценарії, як автоматизоване тестування вебу, вилучення даних та повні робочі процеси.

> **🎯 Готовий до виробництва інструмент**  
> Цей кейс демонструє реальний MCP сервер, який ви можете використовувати вже сьогодні! Дізнайтеся більше про Playwright MCP Server та 9 інших готових Microsoft MCP серверів у нашому [**посібнику Microsoft MCP Servers Guide**](microsoft-mcp-servers.md#8--playwright-mcp-server).

**Ключові особливості:**  
- Надає можливості автоматизації браузера (навігація, заповнення форм, знімки екрана тощо) як MCP інструменти  
- Впроваджує суворий контроль доступу та ізоляцію для запобігання несанкціонованим діям  
- Забезпечує детальні журнали аудиту для всіх взаємодій з браузером  
- Підтримує інтеграцію з Azure OpenAI та іншими провайдерами LLM для агентської автоматизації  
- Працює як основа для Coding Agent GitHub Copilot з можливістю веб-перегляду

**Технічна реалізація:**  
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

**Результати:**  
- Забезпечено безпечну програмну автоматизацію браузера для агентів ШІ та LLM  
- Зменшено ручні зусилля з тестування та покращено покриття тестами веб-додатків  
- Надано багаторазову, розширювану платформу для інтеграції браузерних інструментів у корпоративних середовищах  
- Підтримує можливості веб-перегляду GitHub Copilot

**Посилання:**  
- [Playwright MCP Server GitHub Repository](https://github.com/microsoft/playwright-mcp)  
- [Microsoft AI and Automation Solutions](https://azure.microsoft.com/en-us/products/ai-services/)

### Кейс-стаді 5: Azure MCP – корпоративний Model Context Protocol як сервіс

Azure MCP Server ([https://aka.ms/azmcp](https://aka.ms/azmcp)) — це керована Microsoft корпоративна реалізація Model Context Protocol, створена для надання масштабованих, безпечних і відповідних MCP серверних можливостей як хмарної послуги. Azure MCP дозволяє організаціям швидко розгортати, керувати та інтегрувати MCP сервери з Azure AI, даними та службами безпеки, знижуючи операційні витрати та прискорюючи впровадження ШІ.

> **🎯 Готовий до виробництва інструмент**  
> Це реальний MCP сервер, який ви можете використовувати вже сьогодні! Дізнайтеся більше про Azure AI Foundry MCP Server у нашому [**посібнику Microsoft MCP Servers Guide**](microsoft-mcp-servers.md).

- Повністю керований хостинг MCP серверів з вбудованим масштабуванням, моніторингом та безпекою  
- Рідна інтеграція з Azure OpenAI, Azure AI Search та іншими сервісами Azure  
- Корпоративна автентифікація та авторизація через Microsoft Entra ID  
- Підтримка кастомних інструментів, шаблонів запитів та конекторів ресурсів  
- Відповідність корпоративним вимогам безпеки та регуляторним нормам

**Технічна реалізація:**  
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

**Результати:**  
- Скорочення часу до отримання результату для корпоративних ШІ проєктів завдяки готовій до використання, відповідній платформі MCP серверів  
- Спрощена інтеграція LLM, інструментів та корпоративних джерел даних  
- Підвищена безпека, спостережуваність та операційна ефективність MCP навантажень  
- Покращена якість коду завдяки найкращим практикам Azure SDK та сучасним патернам автентифікації

**Посилання:**  
- [Azure MCP Documentation](https://aka.ms/azmcp)  
- [Azure MCP Server GitHub Repository](https://github.com/Azure/azure-mcp)  
- [Azure AI Services](https://azure.microsoft.com/en-us/products/ai-services/)

### Кейс-стаді 6: NLWeb – протокол природномовного веб-інтерфейсу

NLWeb відображає бачення Microsoft щодо створення базового шару для AI Web. Кожен екземпляр NLWeb також є MCP сервером, який підтримує один основний метод `ask`, що використовується для запитання сайту природною мовою. Отримана відповідь використовує schema.org — широко вживаний словник для опису веб-даних. У вільному розумінні, MCP для NLWeb — це те саме, що HTTP для HTML.

**Ключові особливості:**  
- **Протокольний рівень:** Простий протокол для взаємодії з вебсайтами природною мовою  
- **Формат schema.org:** Використання JSON та schema.org для структурованих, машинозчитуваних відповідей  
- **Реалізація спільнотою:** Легка реалізація для сайтів, які можна подати як списки елементів (продукти, рецепти, атракції, відгуки тощо)  
- **UI віджети:** Готові компоненти інтерфейсу для розмовних інтерфейсів

**Компоненти архітектури:**  
1. **Протокол:** Простий REST API для природномовних запитів до сайтів  
2. **Реалізація:** Використання існуючої розмітки та структури сайту для автоматичних відповідей  
3. **UI віджети:** Готові компоненти для інтеграції розмовних інтерфейсів

**Переваги:**  
- Забезпечує взаємодію як людина-сайт, так і агент-агент  
- Надає структуровані дані, які легко обробляють системи ШІ  
- Швидке розгортання для сайтів зі списковою структурою контенту  
- Стандартизований підхід для забезпечення доступності сайтів для ШІ

**Результати:**  
- Встановлено основу для стандартів взаємодії AI з вебом  
- Спрощено створення розмовних інтерфейсів для контентних сайтів  
- Покращено виявлення та доступність веб-контенту для систем ШІ  
- Сприяння сумісності між різними агентами ШІ та веб-сервісами

**Посилання:**  
- [NLWeb GitHub Repository](https://github.com/microsoft/NlWeb)  
- [NLWeb Documentation](https://github.com/microsoft/NlWeb)

### Кейс-стаді 7: Azure AI Foundry MCP Server – інтеграція корпоративних AI агентів

Сервери Azure AI Foundry MCP демонструють, як MCP можна використовувати для оркестрації та керування AI агентами і робочими процесами в корпоративних середовищах. Інтегруючи MCP з Azure AI Foundry, організації можуть стандартизувати взаємодію агентів, використовувати управління робочими процесами Foundry та забезпечувати безпечне, масштабоване розгортання.

> **🎯 Готовий до виробництва інструмент**  
> Це реальний MCP сервер, який ви можете використовувати вже сьогодні! Дізнайтеся більше про Azure AI Foundry MCP Server у нашому [**посібнику Microsoft MCP Servers Guide**](microsoft-mcp-servers.md#9--azure-ai-foundry-mcp-server).

**Ключові особливості:**  
- Повний доступ до екосистеми Azure AI, включно з каталогами моделей та управлінням розгортаннями  
- Індексація знань за допомогою Azure AI Search для RAG-застосунків  
- Інструменти оцінки продуктивності моделей ШІ та контролю якості  
- Інтеграція з Azure AI Foundry Catalog та Labs для передових дослідницьких моделей  
- Керування агентами та можливості оцінки для виробничих сценаріїв

**Результати:**  
- Швидке прототипування та надійний моніторинг робочих процесів AI агентів  
- Безшовна інтеграція з Azure AI сервісами для складних сценаріїв  
- Уніфікований інтерфейс для створення, розгортання та моніторингу агентських конвеєрів  
- Покращена безпека, відповідність та операційна ефективність для підприємств  
- Прискорене впровадження ШІ при збереженні контролю над складними агентськими процесами

**Посилання:**  
- [Azure AI Foundry MCP Server GitHub Repository](https://github.com/azure-ai-foundry/mcp-foundry)  
- [Інтеграція Azure AI агентів з MCP (блог Microsoft Foundry)](https://devblogs.microsoft.com/foundry/integrating-azure-ai-agents-mcp/)

### Кейс-стаді 8: Foundry MCP Playground – експерименти та прототипування

Foundry MCP Playground пропонує готове середовище для експериментів з MCP серверами та інтеграціями Azure AI Foundry. Розробники можуть швидко прототипувати, тестувати та оцінювати моделі ШІ та робочі процеси агентів, використовуючи ресурси з Azure AI Foundry Catalog та Labs. Плейграунд спрощує налаштування, надає приклади проєктів і підтримує спільну розробку, що полегшує вивчення найкращих практик і нових сценаріїв з мінімальними витратами. Особливо корисний для команд, які хочуть перевірити ідеї, поділитися експериментами та прискорити навчання без складної інфраструктури. Завдяки зниженню бар’єрів входу, плейграунд сприяє інноваціям і внескам спільноти в екосистему MCP та Azure AI Foundry.

**Посилання:**  
- [Foundry MCP Playground GitHub Repository](https://github.com/azure-ai-foundry/foundry-mcp-playground)

### Кейс-стаді 9: Microsoft Learn Docs MCP Server – доступ до документації з підтримкою ШІ

Microsoft Learn Docs MCP Server — це хмарний сервіс, який надає AI асистентам доступ у реальному часі до офіційної документації Microsoft через Model Context Protocol. Цей готовий до виробництва сервер підключається до всебічної екосистеми Microsoft Learn і забезпечує семантичний пошук по всіх офіційних джерелах Microsoft.
> **🎯 Інструмент, готовий до використання у виробництві**
> 
> Це справжній MCP сервер, який ви можете використовувати вже сьогодні! Дізнайтеся більше про Microsoft Learn Docs MCP Server у нашому [**Посібнику з Microsoft MCP Servers**](microsoft-mcp-servers.md#1--microsoft-learn-docs-mcp-server).
**Ключові особливості:**
- Доступ у реальному часі до офіційної документації Microsoft, Azure та Microsoft 365
- Розвинений семантичний пошук, який розуміє контекст і наміри
- Завжди актуальна інформація, оскільки контент Microsoft Learn публікується вчасно
- Комплексне охоплення Microsoft Learn, документації Azure та джерел Microsoft 365
- Повертає до 10 якісних фрагментів контенту з назвами статей та URL

**Чому це важливо:**
- Вирішує проблему «застарілих знань ШІ» щодо технологій Microsoft
- Забезпечує доступ AI-помічників до останніх функцій .NET, C#, Azure та Microsoft 365
- Надає авторитетну інформацію з першоджерел для точного генерування коду
- Необхідно для розробників, які працюють з швидкозмінними технологіями Microsoft

**Результати:**
- Значно покращена точність коду, згенерованого ШІ для технологій Microsoft
- Скорочення часу на пошук актуальної документації та кращих практик
- Підвищення продуктивності розробників завдяки контекстно-залежному пошуку документації
- Безшовна інтеграція у робочі процеси розробки без виходу з IDE

**Посилання:**
- [Microsoft Learn Docs MCP Server GitHub Repository](https://github.com/MicrosoftDocs/mcp)
- [Microsoft Learn Documentation](https://learn.microsoft.com/)

## Практичні проєкти

### Проєкт 1: Створення MCP сервера з підтримкою кількох провайдерів

**Мета:** Розробити MCP сервер, який може маршрутизувати запити до кількох провайдерів AI-моделей на основі певних критеріїв.

**Вимоги:**
- Підтримка щонайменше трьох різних провайдерів моделей (наприклад, OpenAI, Anthropic, локальні моделі)
- Реалізація механізму маршрутизації на основі метаданих запиту
- Створення системи конфігурації для керування обліковими даними провайдерів
- Додавання кешування для оптимізації продуктивності та зниження витрат
- Розробка простого дашборду для моніторингу використання

**Кроки реалізації:**
1. Налаштувати базову інфраструктуру MCP сервера
2. Реалізувати адаптери провайдерів для кожного AI-сервісу
3. Створити логіку маршрутизації на основі атрибутів запиту
4. Додати механізми кешування для частих запитів
5. Розробити дашборд для моніторингу
6. Протестувати з різними патернами запитів

**Технології:** Вибір між Python (.NET/Java/Python залежно від уподобань), Redis для кешування та простий веб-фреймворк для дашборду.

### Проєкт 2: Система управління промптами для підприємств

**Мета:** Розробити систему на базі MCP для керування, версіонування та розгортання шаблонів промптів у межах організації.

**Вимоги:**
- Створити централізований репозиторій шаблонів промптів
- Реалізувати версіонування та робочі процеси затвердження
- Забезпечити можливості тестування шаблонів з прикладами вхідних даних
- Розробити контроль доступу на основі ролей
- Створити API для отримання та розгортання шаблонів

**Кроки реалізації:**
1. Спроєктувати схему бази даних для зберігання шаблонів
2. Створити основний API для CRUD-операцій з шаблонами
3. Реалізувати систему версіонування
4. Побудувати робочий процес затвердження
5. Розробити тестову платформу
6. Створити простий веб-інтерфейс для управління
7. Інтегрувати з MCP сервером

**Технології:** Вибір бекенд-фреймворку, SQL або NoSQL бази даних, а також фронтенд-фреймворку для інтерфейсу управління.

### Проєкт 3: Платформа генерації контенту на базі MCP

**Мета:** Побудувати платформу генерації контенту, яка використовує MCP для забезпечення послідовних результатів для різних типів контенту.

**Вимоги:**
- Підтримка кількох форматів контенту (блог-пости, соціальні мережі, маркетингові тексти)
- Реалізація генерації на основі шаблонів з можливістю налаштування
- Створення системи перегляду контенту та зворотного зв’язку
- Відстеження метрик ефективності контенту
- Підтримка версіонування та ітерацій контенту

**Кроки реалізації:**
1. Налаштувати інфраструктуру MCP клієнта
2. Створити шаблони для різних типів контенту
3. Побудувати конвеєр генерації контенту
4. Реалізувати систему перегляду
5. Розробити систему відстеження метрик
6. Створити інтерфейс користувача для управління шаблонами та генерації контенту

**Технології:** Обрана мова програмування, веб-фреймворк та система бази даних.

## Майбутні напрямки розвитку технології MCP

### Нові тенденції

1. **Мультимодальний MCP**
   - Розширення MCP для стандартизації взаємодії з моделями зображень, аудіо та відео
   - Розробка можливостей крос-модального логічного мислення
   - Стандартизовані формати промптів для різних модальностей

2. **Федеративна інфраструктура MCP**
   - Розподілені мережі MCP, які можуть ділитися ресурсами між організаціями
   - Стандартизовані протоколи для безпечного обміну моделями
   - Техніки обчислень з захистом приватності

3. **Маркетплейси MCP**
   - Екосистеми для обміну та монетизації шаблонів і плагінів MCP
   - Процеси контролю якості та сертифікації
   - Інтеграція з маркетплейсами моделей

4. **MCP для Edge Computing**
   - Адаптація стандартів MCP для пристроїв з обмеженими ресурсами на периферії
   - Оптимізовані протоколи для середовищ з низькою пропускною здатністю
   - Спеціалізовані реалізації MCP для IoT-екосистем

5. **Регуляторні рамки**
   - Розробка розширень MCP для відповідності регуляторним вимогам
   - Стандартизовані аудиторські сліди та інтерфейси пояснюваності
   - Інтеграція з новими рамками управління ШІ

### Рішення MCP від Microsoft

Microsoft та Azure розробили кілька відкритих репозиторіїв, які допомагають розробникам впроваджувати MCP у різних сценаріях:

#### Організація Microsoft
1. [playwright-mcp](https://github.com/microsoft/playwright-mcp) – MCP сервер Playwright для автоматизації браузера та тестування
2. [files-mcp-server](https://github.com/microsoft/files-mcp-server) – Реалізація MCP сервера для OneDrive для локального тестування та внеску спільноти
3. [NLWeb](https://github.com/microsoft/NlWeb) – NLWeb – це набір відкритих протоколів та пов’язаних інструментів з відкритим кодом. Основна мета – створення базового шару для AI Web

#### Організація Azure-Samples
1. [mcp](https://github.com/Azure-Samples/mcp) – Посилання на приклади, інструменти та ресурси для створення та інтеграції MCP серверів на Azure з використанням різних мов
2. [mcp-auth-servers](https://github.com/Azure-Samples/mcp-auth-servers) – Зразкові MCP сервери з демонстрацією аутентифікації за поточною специфікацією Model Context Protocol
3. [remote-mcp-functions](https://github.com/Azure-Samples/remote-mcp-functions) – Лендінг для реалізацій Remote MCP Server в Azure Functions з посиланнями на репозиторії для різних мов
4. [remote-mcp-functions-python](https://github.com/Azure-Samples/remote-mcp-functions-python) – Шаблон швидкого старту для створення та розгортання кастомних Remote MCP серверів на Azure Functions з Python
5. [remote-mcp-functions-dotnet](https://github.com/Azure-Samples/remote-mcp-functions-dotnet) – Шаблон швидкого старту для створення та розгортання кастомних Remote MCP серверів на Azure Functions з .NET/C#
6. [remote-mcp-functions-typescript](https://github.com/Azure-Samples/remote-mcp-functions-typescript) – Шаблон швидкого старту для створення та розгортання кастомних Remote MCP серверів на Azure Functions з TypeScript
7. [remote-mcp-apim-functions-python](https://github.com/Azure-Samples/remote-mcp-apim-functions-python) – Azure API Management як AI Gateway до Remote MCP серверів з Python
8. [AI-Gateway](https://github.com/Azure-Samples/AI-Gateway) – Експерименти APIM ❤️ AI, включно з можливостями MCP, інтеграція з Azure OpenAI та AI Foundry

Ці репозиторії пропонують різні реалізації, шаблони та ресурси для роботи з Model Context Protocol на різних мовах програмування та сервісах Azure. Вони охоплюють широкий спектр випадків використання — від базових серверних реалізацій до аутентифікації, хмарного розгортання та інтеграції в корпоративні сценарії.

#### Каталог ресурсів MCP

[Каталог ресурсів MCP](https://github.com/microsoft/mcp/tree/main/Resources) в офіційному репозиторії Microsoft MCP містить добірку прикладів ресурсів, шаблонів промптів та визначень інструментів для використання з MCP серверами. Цей каталог допомагає розробникам швидко почати роботу з MCP, пропонуючи повторно використовувані компоненти та приклади найкращих практик для:

- **Шаблони промптів:** Готові шаблони для типових завдань і сценаріїв ШІ, які можна адаптувати для власних реалізацій MCP серверів.
- **Визначення інструментів:** Приклади схем інструментів і метаданих для стандартизації інтеграції та виклику інструментів у різних MCP серверах.
- **Приклади ресурсів:** Приклади визначень ресурсів для підключення до джерел даних, API та зовнішніх сервісів у рамках MCP.
- **Референсні реалізації:** Практичні приклади, які демонструють, як структурувати та організовувати ресурси, промпти та інструменти у реальних MCP проєктах.

Ці ресурси прискорюють розробку, сприяють стандартизації та допомагають дотримуватися найкращих практик при створенні та розгортанні рішень на базі MCP.

#### Каталог ресурсів MCP
- [MCP Resources (Sample Prompts, Tools, and Resource Definitions)](https://github.com/microsoft/mcp/tree/main/Resources)

### Можливості для досліджень

- Ефективні методи оптимізації промптів у рамках MCP
- Моделі безпеки для мультиорендних MCP розгортань
- Порівняльне тестування продуктивності різних реалізацій MCP
- Формальні методи верифікації MCP серверів

## Висновок

Model Context Protocol (MCP) швидко формує майбутнє стандартизованої, безпечної та сумісної інтеграції ШІ у різних галузях. Через кейс-стаді та практичні проєкти цього уроку ви побачили, як ранні користувачі — зокрема Microsoft та Azure — використовують MCP для розв’язання реальних задач, прискорення впровадження ШІ та забезпечення відповідності, безпеки й масштабованості. Модульний підхід MCP дозволяє організаціям об’єднувати великі мовні моделі, інструменти та корпоративні дані в єдину, аудиторську систему. У міру розвитку MCP важливо залишатися активним у спільноті, досліджувати відкриті ресурси та застосовувати найкращі практики для створення надійних, готових до майбутнього AI-рішень.

## Додаткові ресурси

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

## Вправи

1. Проаналізуйте один із кейс-стаді та запропонуйте альтернативний підхід до реалізації.
2. Оберіть одну з ідей проєктів і створіть детальну технічну специфікацію.
3. Дослідіть галузь, не охоплену кейс-стаді, і опишіть, як MCP може вирішити її специфічні виклики.
4. Вивчіть один із майбутніх напрямків і розробіть концепцію нового розширення MCP для його підтримки.

Наступне: [Microsoft MCP Server](../07-LessonsfromEarlyAdoption/microsoft-mcp-servers.md)

**Відмова від відповідальності**:  
Цей документ було перекладено за допомогою сервісу автоматичного перекладу [Co-op Translator](https://github.com/Azure/co-op-translator). Хоча ми прагнемо до точності, будь ласка, майте на увазі, що автоматичні переклади можуть містити помилки або неточності. Оригінальний документ рідною мовою слід вважати авторитетним джерелом. Для критично важливої інформації рекомендується звертатися до професійного людського перекладу. Ми не несемо відповідальності за будь-які непорозуміння або неправильні тлумачення, що виникли внаслідок використання цього перекладу.