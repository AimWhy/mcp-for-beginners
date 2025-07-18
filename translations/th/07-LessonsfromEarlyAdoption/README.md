<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "6755bc4f6d0293ce6c49cfc5efba0d8e",
  "translation_date": "2025-07-18T09:54:59+00:00",
  "source_file": "07-LessonsfromEarlyAdoption/README.md",
  "language_code": "th"
}
-->
# 🌟 บทเรียนจากผู้ใช้งานกลุ่มแรก

## 🎯 โมดูลนี้ครอบคลุมเรื่องอะไร

โมดูลนี้จะสำรวจว่าบริษัทและนักพัฒนาจริงๆ ใช้ Model Context Protocol (MCP) อย่างไรในการแก้ปัญหาจริงและขับเคลื่อนนวัตกรรม ผ่านกรณีศึกษาละเอียดและโครงการลงมือทำจริง คุณจะได้เรียนรู้ว่า MCP ช่วยให้การรวม AI ที่ปลอดภัยและขยายได้เชื่อมต่อโมเดลภาษา เครื่องมือ และข้อมูลองค์กรได้อย่างไร

### 📚 ดู MCP ในการใช้งานจริง

อยากเห็นหลักการเหล่านี้ถูกนำไปใช้กับเครื่องมือที่พร้อมใช้งานจริงหรือไม่? ลองดู [**10 Microsoft MCP Servers ที่เปลี่ยนแปลงประสิทธิภาพนักพัฒนา**](microsoft-mcp-servers.md) ซึ่งแสดงเซิร์ฟเวอร์ MCP จริงของ Microsoft ที่คุณสามารถใช้ได้วันนี้

## ภาพรวม

บทเรียนนี้จะสำรวจว่าผู้ใช้งานกลุ่มแรกได้นำ Model Context Protocol (MCP) ไปใช้แก้ปัญหาในโลกจริงและขับเคลื่อนนวัตกรรมในหลายอุตสาหกรรมอย่างไร ผ่านกรณีศึกษาละเอียดและโครงการลงมือทำจริง คุณจะเห็นว่า MCP ช่วยให้การรวม AI ที่เป็นมาตรฐาน ปลอดภัย และขยายได้เชื่อมต่อโมเดลภาษา เครื่องมือ และข้อมูลองค์กรในกรอบงานเดียวกันอย่างไร คุณจะได้ประสบการณ์จริงในการออกแบบและสร้างโซลูชันที่ใช้ MCP เรียนรู้รูปแบบการใช้งานที่พิสูจน์แล้ว และค้นพบแนวทางปฏิบัติที่ดีที่สุดสำหรับการนำ MCP ไปใช้ในสภาพแวดล้อมการผลิต บทเรียนยังเน้นแนวโน้มที่เกิดขึ้น ทิศทางในอนาคต และแหล่งข้อมูลโอเพนซอร์สที่จะช่วยให้คุณก้าวนำเทคโนโลยี MCP และระบบนิเวศที่กำลังพัฒนา

## วัตถุประสงค์การเรียนรู้

- วิเคราะห์การใช้งาน MCP ในโลกจริงในหลายอุตสาหกรรม
- ออกแบบและสร้างแอปพลิเคชันที่ใช้ MCP อย่างครบถ้วน
- สำรวจแนวโน้มและทิศทางในอนาคตของเทคโนโลยี MCP
- นำแนวทางปฏิบัติที่ดีที่สุดไปใช้ในสถานการณ์พัฒนาจริง

## การใช้งาน MCP ในโลกจริง

### กรณีศึกษา 1: ระบบอัตโนมัติสนับสนุนลูกค้าองค์กร

บริษัทข้ามชาติได้นำโซลูชันที่ใช้ MCP มาใช้เพื่อมาตรฐานการโต้ตอบ AI ในระบบสนับสนุนลูกค้าของพวกเขา ซึ่งช่วยให้:

- สร้างอินเทอร์เฟซเดียวสำหรับผู้ให้บริการ LLM หลายราย
- รักษาการจัดการ prompt ที่สอดคล้องกันในทุกแผนก
- นำมาตรการความปลอดภัยและการปฏิบัติตามกฎระเบียบที่เข้มงวดมาใช้
- สลับใช้โมเดล AI ต่างๆ ได้ง่ายตามความต้องการเฉพาะ

**การใช้งานทางเทคนิค:**  
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

**ผลลัพธ์:** ลดต้นทุนโมเดลลง 30% ปรับปรุงความสม่ำเสมอของการตอบกลับ 45% และเพิ่มการปฏิบัติตามกฎระเบียบทั่วโลก

### กรณีศึกษา 2: ผู้ช่วยวินิจฉัยทางการแพทย์

ผู้ให้บริการด้านสุขภาพพัฒนาโครงสร้างพื้นฐาน MCP เพื่อรวมโมเดล AI ทางการแพทย์เฉพาะทางหลายตัว พร้อมทั้งรักษาความปลอดภัยข้อมูลผู้ป่วยที่ละเอียดอ่อน:

- สลับใช้โมเดลทางการแพทย์ทั่วไปและเฉพาะทางได้อย่างราบรื่น
- ควบคุมความเป็นส่วนตัวและบันทึกตรวจสอบอย่างเข้มงวด
- รวมเข้ากับระบบบันทึกสุขภาพอิเล็กทรอนิกส์ (EHR) ที่มีอยู่
- จัดการ prompt สำหรับคำศัพท์ทางการแพทย์อย่างสม่ำเสมอ

**การใช้งานทางเทคนิค:**  
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

**ผลลัพธ์:** ปรับปรุงคำแนะนำวินิจฉัยสำหรับแพทย์ พร้อมรักษาการปฏิบัติตาม HIPAA อย่างเต็มที่ และลดการสลับบริบทระหว่างระบบอย่างมีนัยสำคัญ

### กรณีศึกษา 3: การวิเคราะห์ความเสี่ยงในบริการทางการเงิน

สถาบันการเงินนำ MCP มาใช้เพื่อมาตรฐานกระบวนการวิเคราะห์ความเสี่ยงในหลายแผนก:

- สร้างอินเทอร์เฟซเดียวสำหรับโมเดลความเสี่ยงเครดิต การตรวจจับการฉ้อโกง และความเสี่ยงการลงทุน
- นำมาตรการควบคุมการเข้าถึงและการจัดการเวอร์ชันโมเดลมาใช้
- รับรองความสามารถในการตรวจสอบคำแนะนำ AI ทั้งหมด
- รักษารูปแบบข้อมูลที่สอดคล้องกันในระบบที่หลากหลาย

**การใช้งานทางเทคนิค:**  
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

**ผลลัพธ์:** ปฏิบัติตามกฎระเบียบได้ดีขึ้น ลดเวลาการนำโมเดลไปใช้ 40% และปรับปรุงความสม่ำเสมอของการประเมินความเสี่ยงในแผนกต่างๆ

### กรณีศึกษา 4: Microsoft Playwright MCP Server สำหรับการอัตโนมัติบนเบราว์เซอร์

Microsoft พัฒนา [Playwright MCP server](https://github.com/microsoft/playwright-mcp) เพื่อให้สามารถทำการอัตโนมัติบนเว็บเบราว์เซอร์ได้อย่างปลอดภัยและเป็นมาตรฐานผ่าน Model Context Protocol เซิร์ฟเวอร์ที่พร้อมใช้งานนี้ช่วยให้เอเจนต์ AI และ LLM สามารถโต้ตอบกับเว็บเบราว์เซอร์ได้อย่างควบคุม ตรวจสอบได้ และขยายได้ รองรับกรณีใช้งานเช่น การทดสอบเว็บอัตโนมัติ การดึงข้อมูล และเวิร์กโฟลว์แบบครบวงจร

> **🎯 เครื่องมือพร้อมใช้งานจริง**  
> กรณีศึกษานี้แสดงเซิร์ฟเวอร์ MCP จริงที่คุณใช้ได้วันนี้! เรียนรู้เพิ่มเติมเกี่ยวกับ Playwright MCP Server และเซิร์ฟเวอร์ Microsoft MCP อีก 9 ตัวใน [**Microsoft MCP Servers Guide**](microsoft-mcp-servers.md#8--playwright-mcp-server)

**คุณสมบัติหลัก:**  
- เปิดใช้งานความสามารถอัตโนมัติบนเบราว์เซอร์ (การนำทาง กรอกแบบฟอร์ม ถ่ายภาพหน้าจอ ฯลฯ) ในรูปแบบเครื่องมือ MCP  
- นำมาตรการควบคุมการเข้าถึงและ sandboxing อย่างเข้มงวดเพื่อป้องกันการกระทำที่ไม่ได้รับอนุญาต  
- ให้บันทึกตรวจสอบรายละเอียดสำหรับการโต้ตอบกับเบราว์เซอร์ทั้งหมด  
- รองรับการรวมกับ Azure OpenAI และผู้ให้บริการ LLM อื่นๆ สำหรับการอัตโนมัติที่ขับเคลื่อนโดยเอเจนต์  
- สนับสนุนความสามารถการท่องเว็บของ GitHub Copilot’s Coding Agent

**การใช้งานทางเทคนิค:**  
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

**ผลลัพธ์:**  
- เปิดใช้งานการอัตโนมัติบนเบราว์เซอร์ที่ปลอดภัยและเป็นโปรแกรมสำหรับเอเจนต์ AI และ LLM  
- ลดความพยายามในการทดสอบด้วยมือและเพิ่มความครอบคลุมของการทดสอบเว็บแอปพลิเคชัน  
- ให้กรอบงานที่นำกลับมาใช้ใหม่และขยายได้สำหรับการรวมเครื่องมือบนเบราว์เซอร์ในสภาพแวดล้อมองค์กร  
- สนับสนุนความสามารถการท่องเว็บของ GitHub Copilot

**เอกสารอ้างอิง:**  
- [Playwright MCP Server GitHub Repository](https://github.com/microsoft/playwright-mcp)  
- [Microsoft AI and Automation Solutions](https://azure.microsoft.com/en-us/products/ai-services/)

### กรณีศึกษา 5: Azure MCP – Model Context Protocol ระดับองค์กรในรูปแบบบริการ

Azure MCP Server ([https://aka.ms/azmcp](https://aka.ms/azmcp)) คือการนำ Model Context Protocol มาใช้ในระดับองค์กรที่ Microsoft บริหารจัดการให้ เป็นบริการคลาวด์ที่มีความสามารถของเซิร์ฟเวอร์ MCP ที่ขยายได้ ปลอดภัย และปฏิบัติตามข้อกำหนด Azure MCP ช่วยให้องค์กรสามารถปรับใช้ จัดการ และรวมเซิร์ฟเวอร์ MCP กับบริการ Azure AI ข้อมูล และความปลอดภัยได้อย่างรวดเร็ว ลดภาระการดำเนินงานและเร่งการนำ AI มาใช้

> **🎯 เครื่องมือพร้อมใช้งานจริง**  
> นี่คือเซิร์ฟเวอร์ MCP จริงที่คุณใช้ได้วันนี้! เรียนรู้เพิ่มเติมเกี่ยวกับ Azure AI Foundry MCP Server ใน [**Microsoft MCP Servers Guide**](microsoft-mcp-servers.md)

- โฮสต์เซิร์ฟเวอร์ MCP ที่บริหารจัดการเต็มรูปแบบ พร้อมการปรับขนาด การตรวจสอบ และความปลอดภัยในตัว  
- รวมเข้ากับ Azure OpenAI, Azure AI Search และบริการ Azure อื่นๆ อย่างเนทีฟ  
- การยืนยันตัวตนและอนุญาตระดับองค์กรผ่าน Microsoft Entra ID  
- รองรับเครื่องมือที่กำหนดเอง เทมเพลต prompt และตัวเชื่อมต่อทรัพยากร  
- ปฏิบัติตามข้อกำหนดด้านความปลอดภัยและกฎระเบียบขององค์กร

**การใช้งานทางเทคนิค:**  
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

**ผลลัพธ์:**  
- ลดเวลาสู่คุณค่าสำหรับโครงการ AI องค์กรด้วยแพลตฟอร์มเซิร์ฟเวอร์ MCP ที่พร้อมใช้งานและปฏิบัติตามข้อกำหนด  
- ทำให้ง่ายต่อการรวม LLM เครื่องมือ และแหล่งข้อมูลองค์กร  
- เพิ่มความปลอดภัย การสังเกตการณ์ และประสิทธิภาพการดำเนินงานสำหรับงาน MCP  
- ปรับปรุงคุณภาพโค้ดด้วยแนวทางปฏิบัติที่ดีที่สุดของ Azure SDK และรูปแบบการยืนยันตัวตนปัจจุบัน

**เอกสารอ้างอิง:**  
- [Azure MCP Documentation](https://aka.ms/azmcp)  
- [Azure MCP Server GitHub Repository](https://github.com/Azure/azure-mcp)  
- [Azure AI Services](https://azure.microsoft.com/en-us/products/ai-services/)

### กรณีศึกษา 6: NLWeb – โปรโตคอลอินเทอร์เฟซเว็บภาษาธรรมชาติ

NLWeb คือวิสัยทัศน์ของ Microsoft ในการสร้างชั้นพื้นฐานสำหรับ AI Web ทุกอินสแตนซ์ของ NLWeb ยังเป็นเซิร์ฟเวอร์ MCP ที่รองรับเมธอดหลักหนึ่งตัวคือ `ask` ใช้สำหรับถามเว็บไซต์เป็นภาษาธรรมชาติ คำตอบที่ได้จะใช้ schema.org ซึ่งเป็นคำศัพท์ที่ใช้กันอย่างแพร่หลายสำหรับอธิบายข้อมูลเว็บ กล่าวโดยง่าย MCP ต่อ NLWeb ก็เหมือน HTTP ต่อ HTML

**คุณสมบัติหลัก:**  
- **ชั้นโปรโตคอล:** โปรโตคอลง่ายๆ สำหรับเชื่อมต่อกับเว็บไซต์ด้วยภาษาธรรมชาติ  
- **รูปแบบ Schema.org:** ใช้ JSON และ schema.org สำหรับการตอบกลับที่มีโครงสร้างและอ่านโดยเครื่องได้  
- **การใช้งานในชุมชน:** การใช้งานง่ายสำหรับเว็บไซต์ที่สามารถสรุปเป็นรายการของรายการ (สินค้า สูตรอาหาร สถานที่ท่องเที่ยว รีวิว ฯลฯ)  
- **วิดเจ็ต UI:** ส่วนประกอบอินเทอร์เฟซผู้ใช้ที่สร้างไว้ล่วงหน้าสำหรับอินเทอร์เฟซสนทนา

**ส่วนประกอบสถาปัตยกรรม:**  
1. **โปรโตคอล:** REST API ง่ายๆ สำหรับการถามเว็บไซต์ด้วยภาษาธรรมชาติ  
2. **การใช้งาน:** ใช้ประโยชน์จากมาร์กอัปและโครงสร้างเว็บไซต์ที่มีอยู่สำหรับการตอบกลับอัตโนมัติ  
3. **วิดเจ็ต UI:** ส่วนประกอบพร้อมใช้งานสำหรับการรวมอินเทอร์เฟซสนทนา

**ประโยชน์:**  
- รองรับการโต้ตอบทั้งระหว่างมนุษย์กับเว็บไซต์และเอเจนต์กับเอเจนต์  
- ให้ข้อมูลที่มีโครงสร้างซึ่งระบบ AI สามารถประมวลผลได้ง่าย  
- การปรับใช้รวดเร็วสำหรับเว็บไซต์ที่มีโครงสร้างเนื้อหาแบบรายการ  
- แนวทางมาตรฐานในการทำให้เว็บไซต์เข้าถึงได้โดย AI

**ผลลัพธ์:**  
- สร้างรากฐานสำหรับมาตรฐานการโต้ตอบ AI กับเว็บ  
- ทำให้ง่ายขึ้นในการสร้างอินเทอร์เฟซสนทนาสำหรับเว็บไซต์เนื้อหา  
- เพิ่มการค้นพบและการเข้าถึงเนื้อหาเว็บสำหรับระบบ AI  
- ส่งเสริมความสามารถในการทำงานร่วมกันระหว่างเอเจนต์ AI และบริการเว็บต่างๆ

**เอกสารอ้างอิง:**  
- [NLWeb GitHub Repository](https://github.com/microsoft/NlWeb)  
- [NLWeb Documentation](https://github.com/microsoft/NlWeb)

### กรณีศึกษา 7: Azure AI Foundry MCP Server – การรวมเอเจนต์ AI ระดับองค์กร

เซิร์ฟเวอร์ Azure AI Foundry MCP แสดงให้เห็นว่า MCP สามารถใช้ในการจัดการและควบคุมเอเจนต์ AI และเวิร์กโฟลว์ในสภาพแวดล้อมองค์กรได้อย่างไร โดยการรวม MCP กับ Azure AI Foundry องค์กรสามารถมาตรฐานการโต้ตอบของเอเจนต์ ใช้ประโยชน์จากการจัดการเวิร์กโฟลว์ของ Foundry และรับประกันการปรับใช้ที่ปลอดภัยและขยายได้

> **🎯 เครื่องมือพร้อมใช้งานจริง**  
> นี่คือเซิร์ฟเวอร์ MCP จริงที่คุณใช้ได้วันนี้! เรียนรู้เพิ่มเติมเกี่ยวกับ Azure AI Foundry MCP Server ใน [**Microsoft MCP Servers Guide**](microsoft-mcp-servers.md#9--azure-ai-foundry-mcp-server)

**คุณสมบัติหลัก:**  
- เข้าถึงระบบนิเวศ AI ของ Azure อย่างครบถ้วน รวมถึงแคตตาล็อกโมเดลและการจัดการการปรับใช้  
- การจัดทำดัชนีความรู้ด้วย Azure AI Search สำหรับแอป RAG  
- เครื่องมือประเมินประสิทธิภาพและคุณภาพของโมเดล AI  
- การรวมกับ Azure AI Foundry Catalog และ Labs สำหรับโมเดลวิจัยล้ำสมัย  
- การจัดการและประเมินเอเจนต์สำหรับสถานการณ์การผลิต

**ผลลัพธ์:**  
- การสร้างต้นแบบอย่างรวดเร็วและการตรวจสอบเวิร์กโฟลว์เอเจนต์ AI อย่างเข้มงวด  
- การรวมกับบริการ Azure AI อย่างราบรื่นสำหรับสถานการณ์ขั้นสูง  
- อินเทอร์เฟซเดียวสำหรับการสร้าง ปรับใช้ และตรวจสอบสายงานเอเจนต์  
- ปรับปรุงความปลอดภัย การปฏิบัติตามกฎระเบียบ และประสิทธิภาพการดำเนินงานสำหรับองค์กร  
- เร่งการนำ AI มาใช้ในขณะที่ควบคุมกระบวนการที่ซับซ้อนที่ขับเคลื่อนโดยเอเจนต์

**เอกสารอ้างอิง:**  
- [Azure AI Foundry MCP Server GitHub Repository](https://github.com/azure-ai-foundry/mcp-foundry)  
- [Integrating Azure AI Agents with MCP (Microsoft Foundry Blog)](https://devblogs.microsoft.com/foundry/integrating-azure-ai-agents-mcp/)

### กรณีศึกษา 8: Foundry MCP Playground – การทดลองและสร้างต้นแบบ

Foundry MCP Playground เป็นสภาพแวดล้อมพร้อมใช้งานสำหรับทดลองกับเซิร์ฟเวอร์ MCP และการรวม Azure AI Foundry นักพัฒนาสามารถสร้างต้นแบบ ทดสอบ และประเมินโมเดล AI และเวิร์กโฟลว์เอเจนต์ได้อย่างรวดเร็วโดยใช้ทรัพยากรจาก Azure AI Foundry Catalog และ Labs สนามเด็กเล่นนี้ช่วยให้การตั้งค่าง่ายขึ้น มีโครงการตัวอย่าง และสนับสนุนการพัฒนาร่วมกัน ทำให้ง่ายต่อการสำรวจแนวทางปฏิบัติที่ดีที่สุดและสถานการณ์ใหม่ๆ โดยมีภาระงานต่ำ เหมาะสำหรับทีมที่ต้องการยืนยันไอเดีย แบ่งปันการทดลอง และเร่งการเรียนรู้โดยไม่ต้องใช้โครงสร้างพื้นฐานที่ซับซ้อน สนามเด็กเล่นช่วยส่งเสริมนวัตกรรมและการมีส่วนร่วมของชุมชนในระบบนิเวศ MCP และ Azure AI Foundry

**เอกสารอ้างอิง:**  
- [Foundry MCP Playground GitHub Repository](https://github.com/azure-ai-foundry/foundry-mcp-playground)

### กรณีศึกษา 9: Microsoft Learn Docs MCP Server – การเข้าถึงเอกสารด้วย AI

Microsoft Learn Docs MCP Server เป็นบริการโฮสต์บนคลาวด์ที่ให้ผู้ช่วย AI เข้าถึงเอกสารทางการของ Microsoft แบบเรียลไทม์ผ่าน Model Context Protocol เซิร์ฟเวอร์ที่พร้อมใช้งานนี้เชื่อมต่อกับระบบนิเวศ Microsoft Learn อย่างครบถ้วนและเปิดใช้งานการค้นหาเชิงความหมายในแหล่งข้อมูลทางการทั้งหมดของ Microsoft
> **🎯 เครื่องมือพร้อมใช้งานจริงในงานผลิต**
> 
> นี่คือเซิร์ฟเวอร์ MCP จริงที่คุณสามารถใช้งานได้ทันที! เรียนรู้เพิ่มเติมเกี่ยวกับ Microsoft Learn Docs MCP Server ได้ใน [**Microsoft MCP Servers Guide**](microsoft-mcp-servers.md#1--microsoft-learn-docs-mcp-server)
**คุณสมบัติหลัก:**
- เข้าถึงเอกสารทางการของ Microsoft, เอกสาร Azure และ Microsoft 365 แบบเรียลไทม์
- ความสามารถในการค้นหาเชิงความหมายขั้นสูงที่เข้าใจบริบทและเจตนา
- ข้อมูลที่อัปเดตเสมอเมื่อเนื้อหา Microsoft Learn ถูกเผยแพร่
- ครอบคลุมเนื้อหาอย่างครบถ้วนทั้ง Microsoft Learn, เอกสาร Azure และแหล่งข้อมูล Microsoft 365
- ส่งคืนเนื้อหาคุณภาพสูงสูงสุด 10 ชิ้นพร้อมชื่อบทความและ URL

**ทำไมจึงสำคัญ:**
- แก้ปัญหาความรู้ AI ที่ล้าสมัยสำหรับเทคโนโลยี Microsoft
- ทำให้ผู้ช่วย AI เข้าถึงฟีเจอร์ล่าสุดของ .NET, C#, Azure และ Microsoft 365 ได้
- ให้ข้อมูลที่น่าเชื่อถือจากแหล่งข้อมูลหลักเพื่อการสร้างโค้ดที่แม่นยำ
- จำเป็นสำหรับนักพัฒนาที่ทำงานกับเทคโนโลยี Microsoft ที่เปลี่ยนแปลงอย่างรวดเร็ว

**ผลลัพธ์:**
- เพิ่มความแม่นยำของโค้ดที่สร้างโดย AI สำหรับเทคโนโลยี Microsoft อย่างมาก
- ลดเวลาที่ใช้ในการค้นหาเอกสารและแนวทางปฏิบัติที่ดีที่สุด
- เพิ่มประสิทธิภาพการทำงานของนักพัฒนาด้วยการดึงข้อมูลเอกสารที่เข้าใจบริบท
- ผสานรวมกับกระบวนการพัฒนาได้อย่างราบรื่นโดยไม่ต้องออกจาก IDE

**แหล่งอ้างอิง:**
- [Microsoft Learn Docs MCP Server GitHub Repository](https://github.com/MicrosoftDocs/mcp)
- [Microsoft Learn Documentation](https://learn.microsoft.com/)

## โครงการฝึกปฏิบัติ

### โครงการ 1: สร้าง Multi-Provider MCP Server

**วัตถุประสงค์:** สร้าง MCP server ที่สามารถส่งคำขอไปยังผู้ให้บริการโมเดล AI หลายรายตามเกณฑ์ที่กำหนด

**ข้อกำหนด:**
- รองรับผู้ให้บริการโมเดลอย่างน้อยสามราย (เช่น OpenAI, Anthropic, โมเดลภายใน)
- ใช้กลไกการกำหนดเส้นทางตามเมตาดาต้าของคำขอ
- สร้างระบบการตั้งค่าสำหรับจัดการข้อมูลรับรองของผู้ให้บริการ
- เพิ่มระบบแคชเพื่อเพิ่มประสิทธิภาพและลดค่าใช้จ่าย
- สร้างแดชบอร์ดง่ายๆ สำหรับติดตามการใช้งาน

**ขั้นตอนการดำเนินการ:**
1. ตั้งค่าโครงสร้างพื้นฐาน MCP server เบื้องต้น
2. พัฒนา provider adapters สำหรับแต่ละบริการโมเดล AI
3. สร้างตรรกะการกำหนดเส้นทางตามคุณสมบัติของคำขอ
4. เพิ่มกลไกแคชสำหรับคำขอที่ใช้บ่อย
5. พัฒนาแดชบอร์ดสำหรับการติดตาม
6. ทดสอบด้วยรูปแบบคำขอต่างๆ

**เทคโนโลยี:** เลือกใช้ Python (.NET/Java/Python ตามความชอบ), Redis สำหรับแคช และเว็บเฟรมเวิร์กง่ายๆ สำหรับแดชบอร์ด

### โครงการ 2: ระบบจัดการ Prompt สำหรับองค์กร

**วัตถุประสงค์:** พัฒนาระบบบนพื้นฐาน MCP สำหรับจัดการ เวอร์ชัน และปรับใช้เทมเพลต prompt ในองค์กร

**ข้อกำหนด:**
- สร้างคลังเทมเพลต prompt กลาง
- ใช้ระบบเวอร์ชันและเวิร์กโฟลว์อนุมัติ
- สร้างความสามารถในการทดสอบเทมเพลตด้วยข้อมูลตัวอย่าง
- พัฒนาการควบคุมการเข้าถึงตามบทบาท
- สร้าง API สำหรับดึงและปรับใช้เทมเพลต

**ขั้นตอนการดำเนินการ:**
1. ออกแบบโครงสร้างฐานข้อมูลสำหรับเก็บเทมเพลต
2. สร้าง API หลักสำหรับ CRUD เทมเพลต
3. พัฒนาระบบเวอร์ชัน
4. สร้างเวิร์กโฟลว์อนุมัติ
5. พัฒนากรอบการทดสอบ
6. สร้างอินเทอร์เฟซเว็บง่ายๆ สำหรับการจัดการ
7. ผสานรวมกับ MCP server

**เทคโนโลยี:** เลือกใช้เฟรมเวิร์ก backend, ฐานข้อมูล SQL หรือ NoSQL และเฟรมเวิร์ก frontend สำหรับอินเทอร์เฟซจัดการ

### โครงการ 3: แพลตฟอร์มสร้างเนื้อหาบนพื้นฐาน MCP

**วัตถุประสงค์:** สร้างแพลตฟอร์มสร้างเนื้อหาที่ใช้ MCP เพื่อให้ผลลัพธ์สม่ำเสมอในเนื้อหาหลากหลายประเภท

**ข้อกำหนด:**
- รองรับรูปแบบเนื้อหาหลายประเภท (บทความบล็อก, โซเชียลมีเดีย, ข้อความการตลาด)
- ใช้การสร้างเนื้อหาจากเทมเพลตพร้อมตัวเลือกปรับแต่ง
- สร้างระบบตรวจสอบและรับข้อเสนอแนะเนื้อหา
- ติดตามตัวชี้วัดประสิทธิภาพเนื้อหา
- รองรับการเวอร์ชันและการปรับปรุงเนื้อหา

**ขั้นตอนการดำเนินการ:**
1. ตั้งค่าโครงสร้างพื้นฐาน MCP client
2. สร้างเทมเพลตสำหรับเนื้อหาประเภทต่างๆ
3. สร้าง pipeline การสร้างเนื้อหา
4. พัฒนาระบบตรวจสอบ
5. สร้างระบบติดตามตัวชี้วัด
6. สร้างอินเทอร์เฟซผู้ใช้สำหรับจัดการเทมเพลตและสร้างเนื้อหา

**เทคโนโลยี:** เลือกใช้ภาษาการเขียนโปรแกรม, เว็บเฟรมเวิร์ก และระบบฐานข้อมูลที่คุณถนัด

## แนวทางในอนาคตของเทคโนโลยี MCP

### แนวโน้มที่เกิดขึ้นใหม่

1. **Multi-Modal MCP**
   - ขยาย MCP เพื่อมาตรฐานการโต้ตอบกับโมเดลภาพ, เสียง และวิดีโอ
   - พัฒนาความสามารถในการวิเคราะห์ข้ามโหมด
   - มาตรฐานรูปแบบ prompt สำหรับสื่อประเภทต่างๆ

2. **โครงสร้างพื้นฐาน Federated MCP**
   - เครือข่าย MCP แบบกระจายที่แชร์ทรัพยากรข้ามองค์กร
   - โปรโตคอลมาตรฐานสำหรับการแชร์โมเดลอย่างปลอดภัย
   - เทคนิคการคำนวณที่รักษาความเป็นส่วนตัว

3. **ตลาด MCP**
   - ระบบนิเวศสำหรับแชร์และสร้างรายได้จากเทมเพลตและปลั๊กอิน MCP
   - กระบวนการประกันคุณภาพและการรับรอง
   - การผสานรวมกับตลาดโมเดล

4. **MCP สำหรับ Edge Computing**
   - ปรับมาตรฐาน MCP สำหรับอุปกรณ์ edge ที่มีทรัพยากรจำกัด
   - โปรโตคอลที่เหมาะสมกับสภาพแวดล้อมแบนด์วิดท์ต่ำ
   - การใช้งาน MCP เฉพาะสำหรับระบบนิเวศ IoT

5. **กรอบกฎหมายและข้อบังคับ**
   - พัฒนา MCP ขยายเพื่อรองรับการปฏิบัติตามกฎระเบียบ
   - มาตรฐานการตรวจสอบและอินเทอร์เฟซอธิบายผล
   - การผสานรวมกับกรอบการกำกับดูแล AI ที่เกิดขึ้นใหม่

### โซลูชัน MCP จาก Microsoft

Microsoft และ Azure ได้พัฒนาที่เก็บข้อมูลโอเพนซอร์สหลายแห่งเพื่อช่วยนักพัฒนาในการใช้งาน MCP ในสถานการณ์ต่างๆ:

#### องค์กร Microsoft
1. [playwright-mcp](https://github.com/microsoft/playwright-mcp) - MCP server สำหรับ Playwright เพื่อการทดสอบและอัตโนมัติบนเบราว์เซอร์
2. [files-mcp-server](https://github.com/microsoft/files-mcp-server) - การใช้งาน MCP server สำหรับ OneDrive เพื่อทดสอบในเครื่องและชุมชน
3. [NLWeb](https://github.com/microsoft/NlWeb) - ชุดโปรโตคอลเปิดและเครื่องมือโอเพนซอร์สที่เน้นการสร้างชั้นฐานสำหรับ AI Web

#### องค์กร Azure-Samples
1. [mcp](https://github.com/Azure-Samples/mcp) - ตัวอย่าง เครื่องมือ และทรัพยากรสำหรับสร้างและผสาน MCP servers บน Azure ด้วยหลายภาษา
2. [mcp-auth-servers](https://github.com/Azure-Samples/mcp-auth-servers) - ตัวอย่าง MCP servers ที่แสดงการยืนยันตัวตนตามสเปค Model Context Protocol ปัจจุบัน
3. [remote-mcp-functions](https://github.com/Azure-Samples/remote-mcp-functions) - หน้าเริ่มต้นสำหรับการใช้งาน Remote MCP Server บน Azure Functions พร้อมลิงก์ไปยัง repo ตามภาษา
4. [remote-mcp-functions-python](https://github.com/Azure-Samples/remote-mcp-functions-python) - เทมเพลตเริ่มต้นสำหรับสร้างและปรับใช้ Remote MCP servers ด้วย Azure Functions และ Python
5. [remote-mcp-functions-dotnet](https://github.com/Azure-Samples/remote-mcp-functions-dotnet) - เทมเพลตเริ่มต้นสำหรับสร้างและปรับใช้ Remote MCP servers ด้วย Azure Functions และ .NET/C#
6. [remote-mcp-functions-typescript](https://github.com/Azure-Samples/remote-mcp-functions-typescript) - เทมเพลตเริ่มต้นสำหรับสร้างและปรับใช้ Remote MCP servers ด้วย Azure Functions และ TypeScript
7. [remote-mcp-apim-functions-python](https://github.com/Azure-Samples/remote-mcp-apim-functions-python) - Azure API Management เป็น AI Gateway สำหรับ Remote MCP servers ด้วย Python
8. [AI-Gateway](https://github.com/Azure-Samples/AI-Gateway) - การทดลอง APIM ❤️ AI รวมความสามารถ MCP ผสานกับ Azure OpenAI และ AI Foundry

ที่เก็บเหล่านี้มีตัวอย่างการใช้งาน เทมเพลต และทรัพยากรสำหรับทำงานกับ Model Context Protocol ในหลายภาษาและบริการ Azure ครอบคลุมตั้งแต่การสร้าง server พื้นฐาน การยืนยันตัวตน การปรับใช้บนคลาวด์ ไปจนถึงการผสานรวมในองค์กร

#### ไดเรกทอรีทรัพยากร MCP

[ไดเรกทอรี MCP Resources](https://github.com/microsoft/mcp/tree/main/Resources) ใน repo MCP อย่างเป็นทางการของ Microsoft รวบรวมตัวอย่างทรัพยากร เทมเพลต prompt และคำจำกัดความเครื่องมือสำหรับใช้กับ MCP servers โดยออกแบบมาเพื่อช่วยนักพัฒนาเริ่มต้นใช้งาน MCP ได้อย่างรวดเร็วด้วยบล็อกที่นำกลับมาใช้ใหม่ได้และตัวอย่างแนวทางปฏิบัติที่ดีที่สุดสำหรับ:

- **Prompt Templates:** เทมเพลต prompt พร้อมใช้สำหรับงานและสถานการณ์ AI ทั่วไป ปรับแต่งได้ตามการใช้งาน MCP server ของคุณ
- **Tool Definitions:** ตัวอย่างสคีมาเครื่องมือและเมตาดาต้าเพื่อมาตรฐานการผสานรวมและเรียกใช้เครื่องมือใน MCP servers ต่างๆ
- **Resource Samples:** ตัวอย่างคำจำกัดความทรัพยากรสำหรับเชื่อมต่อกับแหล่งข้อมูล, API และบริการภายนอกในกรอบ MCP
- **Reference Implementations:** ตัวอย่างใช้งานจริงที่แสดงวิธีจัดโครงสร้างและจัดการทรัพยากร, prompt และเครื่องมือในโครงการ MCP จริง

ทรัพยากรเหล่านี้ช่วยเร่งการพัฒนา ส่งเสริมมาตรฐาน และช่วยให้มั่นใจในแนวทางปฏิบัติที่ดีที่สุดเมื่อสร้างและปรับใช้โซลูชันบนพื้นฐาน MCP

#### ไดเรกทอรี MCP Resources
- [MCP Resources (Sample Prompts, Tools, and Resource Definitions)](https://github.com/microsoft/mcp/tree/main/Resources)

### โอกาสในการวิจัย

- เทคนิคการปรับแต่ง prompt อย่างมีประสิทธิภาพในกรอบ MCP
- รูปแบบความปลอดภัยสำหรับการใช้งาน MCP แบบ multi-tenant
- การวัดประสิทธิภาพเปรียบเทียบระหว่างการใช้งาน MCP ต่างๆ
- วิธีการตรวจสอบอย่างเป็นทางการสำหรับ MCP servers

## สรุป

Model Context Protocol (MCP) กำลังเปลี่ยนแปลงอนาคตของการผสาน AI ที่มีมาตรฐาน ปลอดภัย และทำงานร่วมกันได้ในหลายอุตสาหกรรม ผ่านกรณีศึกษาและโครงการฝึกปฏิบัติในบทเรียนนี้ คุณได้เห็นว่าผู้ใช้งานรายแรกๆ รวมถึง Microsoft และ Azure ใช้ MCP เพื่อแก้ปัญหาในโลกจริง เร่งการนำ AI มาใช้ และรับรองความสอดคล้อง ความปลอดภัย และความสามารถในการขยาย MCP มีแนวทางแบบโมดูลาร์ที่ช่วยให้องค์กรเชื่อมต่อโมเดลภาษาใหญ่ เครื่องมือ และข้อมูลองค์กรในกรอบงานที่ตรวจสอบได้ เมื่อ MCP พัฒนาต่อไป การมีส่วนร่วมกับชุมชน การสำรวจทรัพยากรโอเพนซอร์ส และการใช้แนวทางปฏิบัติที่ดีที่สุดจะเป็นกุญแจสำคัญในการสร้างโซลูชัน AI ที่แข็งแกร่งและพร้อมสำหรับอนาคต

## แหล่งข้อมูลเพิ่มเติม

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

## แบบฝึกหัด

1. วิเคราะห์หนึ่งในกรณีศึกษาและเสนอแนวทางการใช้งานทางเลือก
2. เลือกหนึ่งในไอเดียโครงการและสร้างข้อกำหนดทางเทคนิคอย่างละเอียด
3. ศึกษาอุตสาหกรรมที่ไม่ได้กล่าวถึงในกรณีศึกษาและร่างแนวทางที่ MCP จะช่วยแก้ปัญหาเฉพาะได้อย่างไร
4. สำรวจหนึ่งในแนวทางในอนาคตและสร้างแนวคิดสำหรับส่วนขยาย MCP ใหม่เพื่อรองรับแนวทางนั้น

ถัดไป: [Microsoft MCP Server](../07-LessonsfromEarlyAdoption/microsoft-mcp-servers.md)

**ข้อจำกัดความรับผิดชอบ**:  
เอกสารนี้ได้รับการแปลโดยใช้บริการแปลภาษาอัตโนมัติ [Co-op Translator](https://github.com/Azure/co-op-translator) แม้เราจะพยายามให้ความถูกต้องสูงสุด แต่โปรดทราบว่าการแปลอัตโนมัติอาจมีข้อผิดพลาดหรือความไม่ถูกต้อง เอกสารต้นฉบับในภาษาต้นทางถือเป็นแหล่งข้อมูลที่เชื่อถือได้ สำหรับข้อมูลที่สำคัญ ขอแนะนำให้ใช้บริการแปลโดยผู้เชี่ยวชาญมนุษย์ เราไม่รับผิดชอบต่อความเข้าใจผิดหรือการตีความผิดใด ๆ ที่เกิดจากการใช้การแปลนี้