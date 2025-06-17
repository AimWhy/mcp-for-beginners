<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "9a14017adf28f7440f20c2d5e7f1d0f8",
  "translation_date": "2025-06-17T15:48:20+00:00",
  "source_file": "README.md",
  "language_code": "th"
}
-->
![MCP-for-beginners](../../translated_images/mcp-beginners.2ce2b317996369ff66c5b72e25eff9d4288ab2741fc70c0b4e523d1ae1e249fd.th.png) 

[![GitHub contributors](https://img.shields.io/github/contributors/microsoft/mcp-for-beginners.svg)](https://GitHub.com/microsoft/mcp-for-beginners/graphs/contributors)
[![GitHub issues](https://img.shields.io/github/issues/microsoft/mcp-for-beginners.svg)](https://GitHub.com/microsoft/mcp-for-beginners/issues)
[![GitHub pull-requests](https://img.shields.io/github/issues-pr/microsoft/mcp-for-beginners.svg)](https://GitHub.com/microsoft/mcp-for-beginners/pulls)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)

[![GitHub watchers](https://img.shields.io/github/watchers/microsoft/mcp-for-beginners.svg?style=social&label=Watch)](https://GitHub.com/microsoft/mcp-for-beginners/watchers)
[![GitHub forks](https://img.shields.io/github/forks/microsoft/mcp-for-beginners.svg?style=social&label=Fork)](https://GitHub.com/microsoft/mcp-for-beginners/fork)
[![GitHub stars](https://img.shields.io/github/stars/microsoft/mcp-for-beginners?style=social&label=Star)](https://GitHub.com/microsoft/mcp-for-beginners/stargazers)


[![Microsoft Azure AI Foundry Discord](https://dcbadge.vercel.app/api/server/ByRwuEEgH4)](https://discord.com/invite/ByRwuEEgH4)


ทำตามขั้นตอนเหล่านี้เพื่อเริ่มต้นใช้งานทรัพยากรเหล่านี้:
1. **Fork ที่เก็บข้อมูล**: คลิกที่ [![GitHub forks](https://img.shields.io/github/forks/microsoft/mcp-for-beginners.svg?style=social&label=Fork)](https://GitHub.com/microsoft/mcp-for-beginners/fork)
2. **โคลนที่เก็บข้อมูล**:   `git clone https://github.com/microsoft/mcp-for-beginners.git`
3. [**เข้าร่วม Azure AI Foundry Discord เพื่อพบปะผู้เชี่ยวชาญและนักพัฒนาร่วมกัน**](https://discord.com/invite/ByRwuEEgH4)


### 🌐 รองรับหลายภาษา

#### รองรับผ่าน GitHub Action (อัตโนมัติและอัปเดตอยู่เสมอ)

# 🚀 หลักสูตร Model Context Protocol (MCP) สำหรับผู้เริ่มต้น

## **เรียนรู้ MCP ผ่านตัวอย่างโค้ดจริงในภาษา C#, Java, JavaScript, Python และ TypeScript**

## 🧠 ภาพรวมหลักสูตร Model Context Protocol

**Model Context Protocol (MCP)** คือกรอบงานล้ำสมัยที่ออกแบบมาเพื่อมาตรฐานการสื่อสารระหว่างโมเดล AI กับแอปพลิเคชันฝั่งลูกค้า หลักสูตรโอเพนซอร์สนี้นำเสนอเส้นทางการเรียนรู้ที่มีโครงสร้าง พร้อมตัวอย่างโค้ดและกรณีการใช้งานจริงในภาษายอดนิยมอย่าง C#, Java, JavaScript, TypeScript และ Python

ไม่ว่าคุณจะเป็นนักพัฒนา AI สถาปนิกระบบ หรือวิศวกรซอฟต์แวร์ คู่มือนี้คือแหล่งข้อมูลครบถ้วนสำหรับการเข้าใจพื้นฐาน MCP และวิธีการนำไปใช้งาน

## 🔗 แหล่งข้อมูล MCP อย่างเป็นทางการ

- 📘 [MCP Documentation](https://modelcontextprotocol.io/) – บทเรียนและคู่มือผู้ใช้แบบละเอียด  
- 📜 [MCP Specification](https://spec.modelcontextprotocol.io/) – สถาปัตยกรรมโปรโตคอลและข้อมูลทางเทคนิค  
- 🧑‍💻 [MCP GitHub Repository](https://github.com/modelcontextprotocol) – SDK โอเพนซอร์ส เครื่องมือ และตัวอย่างโค้ด  

## 🧭 โครงสร้างหลักสูตร MCP ฉบับสมบูรณ์

| บท | หัวข้อ | คำอธิบาย | ลิงก์ |
|--|--|--|--|
| 00 | **แนะนำ MCP** | ภาพรวมของ Model Context Protocol และความสำคัญในระบบ AI pipeline รวมถึงความหมายของ MCP เหตุผลที่ต้องมาตรฐาน และกรณีการใช้งานพร้อมประโยชน์จริง | [Introduction](./00-Introduction/README.md) |
| 01 | **อธิบายแนวคิดหลัก** | เจาะลึกแนวคิดหลักของ MCP เช่น สถาปัตยกรรม client-server ส่วนประกอบหลักของโปรโตคอล และรูปแบบการส่งข้อความ | [Core Concepts](./01-CoreConcepts/README.md) |
| 02 | **ความปลอดภัยใน MCP** | การระบุภัยคุกคามในระบบที่ใช้ MCP เทคนิคและแนวทางปฏิบัติที่ดีที่สุดเพื่อรักษาความปลอดภัยในการใช้งาน | [Security](/02-Security/README.md) |
| 03 | **เริ่มต้นกับ MCP** | การตั้งค่าสภาพแวดล้อมและการกำหนดค่า สร้างเซิร์ฟเวอร์และไคลเอนต์ MCP ขั้นพื้นฐาน การผสาน MCP กับแอปพลิเคชันที่มีอยู่ | [Getting Started](./03-GettingStarted/README.md) |
| 3.1 | **เซิร์ฟเวอร์ตัวแรก** | การตั้งค่าเซิร์ฟเวอร์พื้นฐานโดยใช้โปรโตคอล MCP เข้าใจการโต้ตอบระหว่างเซิร์ฟเวอร์และไคลเอนต์ พร้อมทดสอบเซิร์ฟเวอร์ | [First Server](./03-GettingStarted/01-first-server/README.md) |
| 3.2 | **ไคลเอนต์ตัวแรก**  | การตั้งค่าไคลเอนต์พื้นฐานโดยใช้โปรโตคอล MCP เข้าใจการโต้ตอบระหว่างไคลเอนต์และเซิร์ฟเวอร์ พร้อมทดสอบไคลเอนต์ | [First Client](./03-GettingStarted/02-client/README.md) |
| 3.3 | **ไคลเอนต์ที่ใช้ LLM**  | การตั้งค่าไคลเอนต์โดยใช้โปรโตคอล MCP พร้อม Large Language Model (LLM) | [Client with LLM](./03-GettingStarted/03-llm-client/README.md) |
| 3.4 | **ใช้งานเซิร์ฟเวอร์กับ Visual Studio Code** | การตั้งค่า Visual Studio Code เพื่อใช้งานเซิร์ฟเวอร์ผ่านโปรโตคอล MCP | [Consuming a server with Visual Studio Code](./03-GettingStarted/04-vscode/README.md) |
| 3.5 | **สร้างเซิร์ฟเวอร์โดยใช้ SSE** | SSE ช่วยให้เราเปิดเผยเซิร์ฟเวอร์สู่โลกออนไลน์ ส่วนนี้จะช่วยคุณสร้างเซิร์ฟเวอร์โดยใช้ SSE | [Creating a server using SSE](./03-GettingStarted/05-sse-server/README.md) |
| 3.6 | **HTTP Streaming** | เรียนรู้วิธีการใช้งาน HTTP streaming เพื่อถ่ายโอนข้อมูลแบบเรียลไทม์ระหว่างไคลเอนต์กับเซิร์ฟเวอร์ MCP | [HTTP Streaming](./03-GettingStarted/06-http-streaming/README.md) |
| 3.7 | **ใช้ AI Toolkit** | AI toolkit คือเครื่องมือที่ช่วยจัดการงาน AI และกระบวนการทำงาน MCP ของคุณได้อย่างดี | [Use AI Toolkit](./03-GettingStarted/07-aitk/README.md) |
| 3.8 | **ทดสอบเซิร์ฟเวอร์ของคุณ** | การทดสอบเป็นส่วนสำคัญของกระบวนการพัฒนา ส่วนนี้จะช่วยให้คุณใช้เครื่องมือต่างๆ ในการทดสอบ | [Testing your server](./03-GettingStarted/08-testing/README.md) |
| 3.9 | **ปรับใช้เซิร์ฟเวอร์ของคุณ** | จะทำอย่างไรเมื่อต้องย้ายจากการพัฒนาในเครื่องสู่การใช้งานจริง? ส่วนนี้จะช่วยให้คุณพัฒนาและปรับใช้เซิร์ฟเวอร์ | [Deploy your server](./03-GettingStarted/09-deployment/README.md) |
| 04 | **การใช้งานจริง** | การใช้ SDK ในหลายภาษา การดีบัก ทดสอบและตรวจสอบ สร้างเทมเพลต prompt และเวิร์กโฟลว์ที่นำกลับมาใช้ใหม่ได้ | [Practical Implementation](./04-PracticalImplementation/README.md) |
| 05 | **หัวข้อขั้นสูงใน MCP** | เวิร์กโฟลว์ AI แบบมัลติ-โมดอลและการขยายตัว กลยุทธ์การขยายแบบปลอดภัย MCP ในระบบองค์กร | [Advanced Topics](./05-AdvancedTopics/README.md) |
| 5.1 | **การผสาน MCP กับ Azure** | แสดงการผสาน MCP กับ Azure | [MCP Azure integration](./05-AdvancedTopics/mcp-integration/README.md) |
| 5.2 | **มัลติ-โมดาลิตี้** | แสดงวิธีการทำงานกับหลายโหมด เช่น รูปภาพและอื่นๆ | [Multi modality](./05-AdvancedTopics/mcp-multi-modality/README.md) |
| 5.3 | **MCP OAuth2 Demo** | แอป Spring Boot ขั้นพื้นฐานแสดงการใช้งาน OAuth2 กับ MCP ทั้งในฐานะ Authorization และ Resource Server สาธิตการออกโทเค็นอย่างปลอดภัย ป้องกัน endpoint การปรับใช้ใน Azure Container Apps และการผสาน API Management | [MCP OAuth2 Demo](./05-AdvancedTopics/mcp-oauth2-demo/README.md) |
| 5.4 | **Root Contexts** | เรียนรู้เพิ่มเติมเกี่ยวกับ root context และวิธีการนำไปใช้ | [Root Contexts](./05-AdvancedTopics/mcp-root-contexts/README.md) |
| 5.5 | **Routing** | เรียนรู้ประเภทต่างๆ ของ routing | [Routing](./05-AdvancedTopics/mcp-routing/README.md) |
| 5.6 | **Sampling** | เรียนรู้วิธีการทำงานกับ sampling | [Sampling](./05-AdvancedTopics/mcp-sampling/README.md) |
| 5.7 | **Scaling** | เรียนรู้การขยายเซิร์ฟเวอร์ MCP รวมถึงกลยุทธ์การขยายแนวนอนและแนวตั้ง การเพิ่มประสิทธิภาพทรัพยากร และการปรับจูนประสิทธิภาพ | [Scaling](./05-AdvancedTopics/mcp-scaling/README.md) |
| 5.8 | **Security** | รักษาความปลอดภัยเซิร์ฟเวอร์ MCP ของคุณ รวมถึงการตรวจสอบตัวตน การอนุญาต และกลยุทธ์การปกป้องข้อมูล | [Security](./05-AdvancedTopics/mcp-security/README.md) |
| 5.9 | **Web Search MCP** | เซิร์ฟเวอร์และไคลเอนต์ MCP ภาษา Python ผสานกับ SerpAPI สำหรับการค้นหาเว็บ ข่าว สินค้า และถามตอบแบบเรียลไทม์ สาธิตการประสานงานเครื่องมือหลายตัว การเชื่อมต่อ API ภายนอก และการจัดการข้อผิดพลาดอย่างเข้มแข็ง | [Web Search MCP](./05-AdvancedTopics/web-search-mcp/README.md) |
| 5.10 | **Realtime Streaming** | การสตรีมข้อมูลแบบเรียลไทม์กลายเป็นสิ่งจำเป็นในโลกที่ขับเคลื่อนด้วยข้อมูลทุกวันนี้ ที่ธุรกิจและแอปพลิเคชันต้องการเข้าถึงข้อมูลทันทีเพื่อการตัดสินใจอย่างรวดเร็ว | [Realtime Streaming](./05-AdvancedTopics/mcp-realtimestreaming/README.md) |
| 5.11 | **Realtime Web Search** | การค้นหาเว็บแบบเรียลไทม์ MCP เปลี่ยนวิธีการค้นหาเว็บแบบเรียลไทม์โดยให้แนวทางมาตรฐานในการจัดการบริบทระหว่างโมเดล AI เครื่องมือค้นหา และแอปพลิเคชัน | [Realtime Web Search](./05-AdvancedTopics/mcp-realtimesearch/README.md) |
| 06 | **การมีส่วนร่วมของชุมชน** | วิธีการส่งโค้ดและเอกสาร ร่วมมือผ่าน GitHub การพัฒนาและรับข้อเสนอแนะจากชุมชน | [Community Contributions](./06-CommunityContributions/README.md) |
| 07 | **ข้อคิดเห็นจากการนำไปใช้ในช่วงแรก** | การใช้งานจริงและสิ่งที่ได้ผล การสร้างและปรับใช้โซลูชันที่ใช้ MCP แนวโน้มและแผนงานในอนาคต | [Insights](./07-LessonsFromEarlyAdoption/README.md) |
| 08 | **แนวทางปฏิบัติที่ดีที่สุดสำหรับ MCP** | การปรับแต่งและเพิ่มประสิทธิภาพ การออกแบบระบบ MCP ที่ทนทานต่อข้อผิดพลาด การทดสอบและกลยุทธ์ความยืดหยุ่น | [Best Practices](./08-BestPractices/README.md) |
| 09 | **กรณีศึกษา MCP** | การเจาะลึกสถาปัตยกรรมโซลูชัน MCP แผนผังการปรับใช้และเคล็ดลับการบูรณาการ แผนภาพที่มีคำอธิบายและการสาธิตโครงการ | [Case Studies](./09-CaseStudy/README.md) |
| 10 | **การปรับปรุงกระบวนการทำงาน AI: การสร้าง MCP Server ด้วย AI Toolkit** | เวิร์กช็อปแบบลงมือทำอย่างครบวงจรรวม MCP กับ AI Toolkit ของ Microsoft สำหรับ VS Code เรียนรู้การสร้างแอปอัจฉริยะที่เชื่อมต่อโมเดล AI กับเครื่องมือในโลกจริงผ่านโมดูลปฏิบัติที่ครอบคลุมพื้นฐาน การพัฒนาเซิร์ฟเวอร์แบบกำหนดเอง และกลยุทธ์การปรับใช้ในสภาพแวดล้อมจริง | [Hands On Lab](./10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/README.md) |

## ตัวอย่างโครงการ

### 🧮 ตัวอย่างโครงการเครื่องคิดเลข MCP:
<details>
  <summary><strong>สำรวจการใช้งานโค้ดตามภาษา</strong></summary>

  - [ตัวอย่าง MCP Server ด้วย C#](./03-GettingStarted/samples/csharp/README.md)
  - [เครื่องคิดเลข MCP ด้วย Java](./03-GettingStarted/samples/java/calculator/README.md)
  - [ตัวอย่าง MCP ด้วย JavaScript](./03-GettingStarted/samples/javascript/README.md)
  - [MCP Server ด้วย Python](../../03-GettingStarted/samples/python/mcp_calculator_server.py)
  - [ตัวอย่าง MCP ด้วย TypeScript](./03-GettingStarted/samples/typescript/README.md)

</details>

### 💡 ตัวอย่างโครงการเครื่องคิดเลข MCP ขั้นสูง:
<details>
  <summary><strong>สำรวจตัวอย่างขั้นสูง</strong></summary>

  - [ตัวอย่างขั้นสูงด้วย C#](./04-PracticalImplementation/samples/csharp/README.md)
  - [ตัวอย่างแอป Container ด้วย Java](./04-PracticalImplementation/samples/java/containerapp/README.md)
  - [ตัวอย่างขั้นสูงด้วย JavaScript](./04-PracticalImplementation/samples/javascript/README.md)
  - [การใช้งานซับซ้อนด้วย Python](../../04-PracticalImplementation/samples/python/mcp_sample.py)
  - [ตัวอย่าง Container ด้วย TypeScript](./04-PracticalImplementation/samples/typescript/README.md)

</details>

## 🎯 ข้อกำหนดเบื้องต้นสำหรับการเรียน MCP

เพื่อให้ได้ประโยชน์สูงสุดจากหลักสูตรนี้ คุณควรมี:

- ความรู้พื้นฐานเกี่ยวกับ C#, Java หรือ Python
- ความเข้าใจในโมเดล client-server และ API
- (ถ้ามี) ความคุ้นเคยกับแนวคิดการเรียนรู้ของเครื่อง

## 📚 คู่มือการศึกษา

มี [คู่มือการศึกษา](./study_guide.md) ที่ครอบคลุมเพื่อช่วยให้คุณใช้งาน repository นี้ได้อย่างมีประสิทธิภาพ คู่มือประกอบด้วย:

- แผนที่หลักสูตรแบบภาพที่แสดงหัวข้อทั้งหมด
- การแยกย่อยรายละเอียดของแต่ละส่วนใน repository
- แนวทางการใช้ตัวอย่างโครงการ
- เส้นทางการเรียนรู้ที่แนะนำสำหรับระดับทักษะต่างๆ
- แหล่งข้อมูลเพิ่มเติมเพื่อเสริมการเรียนรู้ของคุณ

## 🛠️ วิธีใช้หลักสูตรนี้อย่างมีประสิทธิภาพ

แต่ละบทเรียนในคู่มือนี้ประกอบด้วย:

1. คำอธิบายที่ชัดเจนเกี่ยวกับแนวคิด MCP  
2. ตัวอย่างโค้ดสดในหลายภาษา  
3. แบบฝึกหัดเพื่อสร้างแอป MCP จริง  
4. แหล่งข้อมูลเพิ่มเติมสำหรับผู้เรียนขั้นสูง  

## 📜 ข้อมูลใบอนุญาต

เนื้อหานี้ได้รับอนุญาตภายใต้ **MIT License** สำหรับข้อกำหนดและเงื่อนไข ดูที่ [LICENSE](../../LICENSE)

## 🤝 แนวทางการมีส่วนร่วม

โครงการนี้ยินดีรับข้อเสนอแนะและการมีส่วนร่วม โดยส่วนใหญ่คุณจะต้องยอมรับ Contributor License Agreement (CLA) ซึ่งเป็นการประกาศว่าคุณมีสิทธิ์และอนุญาตให้เราใช้ผลงานของคุณ สำหรับรายละเอียดเพิ่มเติมเยี่ยมชม <https://cla.opensource.microsoft.com>

เมื่อคุณส่ง pull request ระบบ CLA bot จะตรวจสอบโดยอัตโนมัติว่าคุณต้องส่ง CLA หรือไม่ และแสดงสถานะที่เหมาะสม (เช่น การตรวจสอบสถานะ หรือคอมเมนต์) เพียงทำตามคำแนะนำที่บอทให้มา คุณจะต้องทำเพียงครั้งเดียวสำหรับทุก repository ที่ใช้ CLA ของเรา

โครงการนี้ได้นำ [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/) มาใช้  
สำหรับข้อมูลเพิ่มเติมดูที่ [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) หรือ ติดต่อ [opencode@microsoft.com](mailto:opencode@microsoft.com) หากมีคำถามหรือข้อเสนอแนะเพิ่มเติม

## 🎒 หลักสูตรอื่นๆ
ทีมงานของเรามีหลักสูตรอื่นๆ ด้วย! ลองดู:

- [AI Agents For Beginners](https://github.com/microsoft/ai-agents-for-beginners?WT.mc_id=academic-105485-koreyst)
- [Generative AI for Beginners using .NET](https://github.com/microsoft/Generative-AI-for-beginners-dotnet?WT.mc_id=academic-105485-koreyst)
- [Generative AI for Beginners using JavaScript](https://github.com/microsoft/generative-ai-with-javascript?WT.mc_id=academic-105485-koreyst)
- [Generative AI for Beginners](https://github.com/microsoft/generative-ai-for-beginners?WT.mc_id=academic-105485-koreyst)
- [ML for Beginners](https://aka.ms/ml-beginners?WT.mc_id=academic-105485-koreyst)
- [Data Science for Beginners](https://aka.ms/datascience-beginners?WT.mc_id=academic-105485-koreyst)
- [AI for Beginners](https://aka.ms/ai-beginners?WT.mc_id=academic-105485-koreyst)
- [Cybersecurity for Beginners](https://github.com/microsoft/Security-101??WT.mc_id=academic-96948-sayoung)
- [Web Dev for Beginners](https://aka.ms/webdev-beginners?WT.mc_id=academic-105485-koreyst)
- [IoT for Beginners](https://aka.ms/iot-beginners?WT.mc_id=academic-105485-koreyst)
- [XR Development for Beginners](https://github.com/microsoft/xr-development-for-beginners?WT.mc_id=academic-105485-koreyst)
- [การใช้งาน GitHub Copilot อย่างเชี่ยวชาญสำหรับการเขียนโปรแกรม AI คู่](https://aka.ms/GitHubCopilotAI?WT.mc_id=academic-105485-koreyst)
- [การใช้งาน GitHub Copilot อย่างเชี่ยวชาญสำหรับนักพัฒนา C#/.NET](https://github.com/microsoft/mastering-github-copilot-for-dotnet-csharp-developers?WT.mc_id=academic-105485-koreyst)
- [เลือกการผจญภัย Copilot ของคุณเอง](https://github.com/microsoft/CopilotAdventures?WT.mc_id=academic-105485-koreyst)

## ™️ ข้อกำหนดเครื่องหมายการค้า

โครงการนี้อาจมีเครื่องหมายการค้าหรือโลโก้ของโครงการ ผลิตภัณฑ์ หรือบริการ การใช้เครื่องหมายการค้าหรือโลโก้ของ Microsoft อย่างถูกต้องต้องเป็นไปตามและปฏิบัติตาม  
[แนวทางเครื่องหมายการค้าและแบรนด์ของ Microsoft](https://www.microsoft.com/legal/intellectualproperty/trademarks/usage/general)  
การใช้เครื่องหมายการค้าหรือโลโก้ของ Microsoft ในเวอร์ชันที่ดัดแปลงของโครงการนี้ต้องไม่ก่อให้เกิดความสับสนหรือสื่อถึงการสนับสนุนจาก Microsoft  
การใช้เครื่องหมายการค้าหรือโลโก้ของบุคคลที่สามต้องเป็นไปตามนโยบายของบุคคลที่สามเหล่านั้นเท่านั้น

**ข้อจำกัดความรับผิดชอบ**:  
เอกสารนี้ได้รับการแปลโดยใช้บริการแปลภาษาด้วย AI [Co-op Translator](https://github.com/Azure/co-op-translator) แม้เราจะพยายามให้ความถูกต้องสูงสุด แต่โปรดทราบว่าการแปลอัตโนมัติอาจมีข้อผิดพลาดหรือความไม่แม่นยำ เอกสารต้นฉบับในภาษาต้นทางควรถือเป็นแหล่งข้อมูลที่เชื่อถือได้ สำหรับข้อมูลที่สำคัญ ขอแนะนำให้ใช้การแปลโดยมนุษย์มืออาชีพ เราไม่รับผิดชอบต่อความเข้าใจผิดหรือการตีความที่ผิดพลาดใด ๆ ที่เกิดจากการใช้การแปลนี้