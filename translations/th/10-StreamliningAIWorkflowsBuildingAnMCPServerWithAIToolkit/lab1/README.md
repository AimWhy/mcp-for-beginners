<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "2aa9dbc165e104764fa57e8a0d3f1c73",
  "translation_date": "2025-06-10T05:22:11+00:00",
  "source_file": "10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab1/README.md",
  "language_code": "th"
}
-->
# 🚀 Module 1: พื้นฐาน AI Toolkit

[![Duration](https://img.shields.io/badge/Duration-15%20minutes-blue.svg)]()
[![Difficulty](https://img.shields.io/badge/Difficulty-Beginner-green.svg)]()
[![Prerequisites](https://img.shields.io/badge/Prerequisites-VS%20Code-orange.svg)]()

## 📋 วัตถุประสงค์การเรียนรู้

เมื่อจบโมดูลนี้ คุณจะสามารถ:
- ✅ ติดตั้งและตั้งค่า AI Toolkit สำหรับ Visual Studio Code
- ✅ สำรวจ Model Catalog และเข้าใจแหล่งที่มาของโมเดลต่างๆ
- ✅ ใช้ Playground เพื่อทดสอบและทดลองโมเดล
- ✅ สร้าง AI agents แบบกำหนดเองด้วย Agent Builder
- ✅ เปรียบเทียบประสิทธิภาพของโมเดลจากผู้ให้บริการต่างๆ
- ✅ นำแนวปฏิบัติที่ดีที่สุดสำหรับการออกแบบ prompt มาใช้

## 🧠 แนะนำ AI Toolkit (AITK)

**AI Toolkit สำหรับ Visual Studio Code** คือส่วนขยายหลักของ Microsoft ที่เปลี่ยน VS Code ให้เป็นสภาพแวดล้อมพัฒนา AI ครบวงจร เชื่อมโยงงานวิจัย AI กับการพัฒนาแอปพลิเคชันจริง ทำให้ AI สร้างสรรค์เข้าถึงได้ง่ายสำหรับนักพัฒนาทุกระดับ

### 🌟 ความสามารถหลัก

| ฟีเจอร์ | คำอธิบาย | กรณีใช้งาน |
|---------|-------------|----------|
| **🗂️ Model Catalog** | เข้าถึงโมเดลกว่า 100 โมเดลจาก GitHub, ONNX, OpenAI, Anthropic, Google | ค้นหาและเลือกโมเดล |
| **🔌 BYOM Support** | รวมโมเดลของคุณเอง (ในเครื่อง/ระยะไกล) | นำโมเดลเฉพาะไปใช้งาน |
| **🎮 Interactive Playground** | ทดสอบโมเดลแบบเรียลไทม์ผ่านแชท | สร้างต้นแบบและทดสอบอย่างรวดเร็ว |
| **📎 Multi-Modal Support** | รองรับข้อความ, รูปภาพ และไฟล์แนบ | แอป AI ที่ซับซ้อน |
| **⚡ Batch Processing** | รันหลาย prompt พร้อมกัน | เพิ่มประสิทธิภาพการทดสอบ |
| **📊 Model Evaluation** | มีเมตริกในตัว (F1, ความเกี่ยวข้อง, ความคล้ายคลึง, ความสอดคล้อง) | ประเมินผลการทำงาน |

### 🎯 ทำไม AI Toolkit ถึงสำคัญ

- **🚀 เร่งการพัฒนา**: จากไอเดียสู่ต้นแบบในไม่กี่นาที
- **🔄 เวิร์กโฟลว์รวมศูนย์**: อินเทอร์เฟซเดียวสำหรับผู้ให้บริการ AI หลายราย
- **🧪 ทดลองง่าย**: เปรียบเทียบโมเดลโดยไม่ต้องตั้งค่าซับซ้อน
- **📈 พร้อมใช้งานจริง**: เปลี่ยนจากต้นแบบสู่การใช้งานได้อย่างราบรื่น

## 🛠️ ข้อกำหนดเบื้องต้นและการตั้งค่า

### 📦 ติดตั้ง AI Toolkit Extension

**ขั้นตอนที่ 1: เข้า Marketplace ของ Extensions**
1. เปิด Visual Studio Code
2. ไปที่มุมมอง Extensions (`Ctrl+Shift+X` หรือ `Cmd+Shift+X`)
3. ค้นหา "AI Toolkit"

**ขั้นตอนที่ 2: เลือกเวอร์ชันของคุณ**
- **🟢 Release**: แนะนำสำหรับการใช้งานจริง
- **🔶 Pre-release**: เข้าถึงฟีเจอร์ใหม่ก่อนใคร

**ขั้นตอนที่ 3: ติดตั้งและเปิดใช้งาน**

![AI Toolkit Extension](../../../../translated_images/aitkext.d28945a03eed003c39fc39bc96ae655af9b64b9b922e78e88b07214420ed7985.th.png)

### ✅ รายการตรวจสอบการยืนยัน
- [ ] ไอคอน AI Toolkit ปรากฏในแถบด้านข้างของ VS Code
- [ ] ส่วนขยายถูกเปิดใช้งานและทำงานแล้ว
- [ ] ไม่มีข้อผิดพลาดในการติดตั้งในแผงผลลัพธ์

## 🧪 แบบฝึกหัด 1: สำรวจโมเดล GitHub

**🎯 เป้าหมาย**: เชี่ยวชาญ Model Catalog และทดสอบโมเดล AI ตัวแรกของคุณ

### 📊 ขั้นตอนที่ 1: สำรวจ Model Catalog

Model Catalog คือประตูสู่ระบบนิเวศ AI รวมโมเดลจากผู้ให้บริการหลายราย ช่วยให้ค้นหาและเปรียบเทียบได้ง่าย

**🔍 คู่มือการนำทาง:**

คลิกที่ **MODELS - Catalog** ในแถบด้านข้างของ AI Toolkit

![Model Catalog](../../../../translated_images/aimodel.263ed2be013d8fb0e2265c4f742cfe490f6f00eca5e132ec50438c8e826e34ed.th.png)

**💡 เคล็ดลับ**: มองหาโมเดลที่มีความสามารถเฉพาะตรงกับการใช้งานของคุณ (เช่น สร้างโค้ด, เขียนเชิงสร้างสรรค์, วิเคราะห์)

**⚠️ หมายเหตุ**: โมเดลที่โฮสต์บน GitHub (GitHub Models) ใช้งานได้ฟรีแต่มีข้อจำกัดเรื่องจำนวนคำขอและโทเคน หากต้องการเข้าถึงโมเดลที่ไม่ใช่ของ GitHub (เช่น โมเดลภายนอกที่โฮสต์ผ่าน Azure AI หรือจุดเชื่อมต่ออื่น) คุณจะต้องใส่คีย์ API หรือการยืนยันตัวตนที่เหมาะสม

### 🚀 ขั้นตอนที่ 2: เพิ่มและตั้งค่าโมเดลตัวแรกของคุณ

**กลยุทธ์การเลือกโมเดล:**
- **GPT-4.1**: เหมาะสำหรับการวิเคราะห์และเหตุผลที่ซับซ้อน
- **Phi-4-mini**: ตอบสนองรวดเร็ว เหมาะกับงานง่ายๆ

**🔧 ขั้นตอนการตั้งค่า:**
1. เลือก **OpenAI GPT-4.1** จากแค็ตตาล็อก
2. คลิก **Add to My Models** เพื่อเพิ่มโมเดลสำหรับใช้งาน
3. เลือก **Try in Playground** เพื่อเปิดสภาพแวดล้อมทดสอบ
4. รอการเริ่มต้นโมเดล (การตั้งค่าแรกอาจใช้เวลาสักครู่)

![Playground Setup](../../../../translated_images/playground.dd6f5141344878ca4d4f3de819775da7b113518941accf37c291117c602f85db.th.png)

**⚙️ ทำความเข้าใจพารามิเตอร์ของโมเดล:**
- **Temperature**: ควบคุมความคิดสร้างสรรค์ (0 = ตายตัว, 1 = สร้างสรรค์)
- **Max Tokens**: ความยาวสูงสุดของคำตอบ
- **Top-p**: การสุ่มตัวอย่างแบบนิวเคลียสเพื่อความหลากหลายของคำตอบ

### 🎯 ขั้นตอนที่ 3: เชี่ยวชาญอินเทอร์เฟซของ Playground

Playground คือห้องทดลองสำหรับทดลอง AI นี่คือวิธีใช้ให้เต็มประสิทธิภาพ:

**🎨 แนวปฏิบัติที่ดีที่สุดสำหรับการออกแบบ prompt:**
1. **เจาะจง**: คำสั่งที่ชัดเจนและละเอียดช่วยให้ได้ผลลัพธ์ดีขึ้น
2. **ให้บริบท**: รวมข้อมูลพื้นฐานที่เกี่ยวข้อง
3. **ใช้ตัวอย่าง**: แสดงให้โมเดลเห็นว่าคุณต้องการอะไรด้วยตัวอย่าง
4. **ปรับปรุง**: แก้ไข prompt ตามผลลัพธ์เบื้องต้น

**🧪 สถานการณ์ทดสอบ:**
```markdown
# Example 1: Code Generation
"Write a Python function that calculates the factorial of a number using recursion. Include error handling and docstrings."

# Example 2: Creative Writing
"Write a professional email to a client explaining a project delay, maintaining a positive tone while being transparent about challenges."

# Example 3: Data Analysis
"Analyze this sales data and provide insights: [paste your data]. Focus on trends, anomalies, and actionable recommendations."
```

![Testing Results](../../../../translated_images/result.1dfcf211fb359cf65902b09db191d3bfc65713ca15e279c1a30be213bb526949.th.png)

### 🏆 แบบฝึกหัดท้าทาย: เปรียบเทียบประสิทธิภาพโมเดล

**🎯 เป้าหมาย**: เปรียบเทียบโมเดลต่างๆ โดยใช้ prompt เดียวกันเพื่อเข้าใจจุดแข็งของแต่ละตัว

**📋 คำแนะนำ:**
1. เพิ่ม **Phi-4-mini** ลงในพื้นที่ทำงานของคุณ
2. ใช้ prompt เดียวกันสำหรับทั้ง GPT-4.1 และ Phi-4-mini

![set](../../../../translated_images/set.88132df189ecde2cbbda256c1841db5aac8e9bdeba1a4e343dfa031b9545d6c9.th.png)

3. เปรียบเทียบคุณภาพคำตอบ ความเร็ว และความแม่นยำ
4. บันทึกผลลัพธ์ในส่วนผลลัพธ์

![Model Comparison](../../../../translated_images/compare.97746cd0f907495503c1fc217739f3890dc76ea5f6fd92379a6db0cc331feb58.th.png)

**💡 ข้อมูลสำคัญที่ควรค้นพบ:**
- เมื่อใดควรใช้ LLM กับ SLM
- การแลกเปลี่ยนระหว่างค่าใช้จ่ายกับประสิทธิภาพ
- ความสามารถเฉพาะตัวของโมเดลแต่ละตัว

## 🤖 แบบฝึกหัด 2: สร้าง Agent แบบกำหนดเองด้วย Agent Builder

**🎯 เป้าหมาย**: สร้าง AI agents เฉพาะทางสำหรับงานและเวิร์กโฟลว์ที่ต้องการ

### 🏗️ ขั้นตอนที่ 1: ทำความเข้าใจ Agent Builder

Agent Builder คือจุดเด่นของ AI Toolkit ช่วยให้คุณสร้างผู้ช่วย AI ที่ออกแบบมาเฉพาะโดยผสมผสานพลังของ LLM กับคำสั่งเฉพาะ พารามิเตอร์ และความรู้เฉพาะทาง

**🧠 องค์ประกอบสถาปัตยกรรมของ Agent:**
- **Core Model**: LLM หลัก (GPT-4, Groks, Phi ฯลฯ)
- **System Prompt**: กำหนดบุคลิกและพฤติกรรมของ agent
- **Parameters**: การตั้งค่าปรับแต่งเพื่อประสิทธิภาพสูงสุด
- **Tools Integration**: เชื่อมต่อกับ API ภายนอกและบริการ MCP
- **Memory**: บริบทการสนทนาและการเก็บสถานะเซสชัน

![Agent Builder Interface](../../../../translated_images/agentbuilder.25895b2d2f8c02e7aa99dd40e105877a6f1db8f0441180087e39db67744b361f.th.png)

### ⚙️ ขั้นตอนที่ 2: เจาะลึกการตั้งค่า Agent

**🎨 การสร้าง System Prompt ที่มีประสิทธิภาพ:**
```markdown
# Template Structure:
## Role Definition
You are a [specific role] with expertise in [domain].

## Capabilities
- List specific abilities
- Define scope of knowledge
- Clarify limitations

## Behavior Guidelines
- Response style (formal, casual, technical)
- Output format preferences
- Error handling approach

## Examples
Provide 2-3 examples of ideal interactions
```

*แน่นอน คุณยังสามารถใช้ Generate System Prompt เพื่อให้ AI ช่วยสร้างและปรับแต่ง prompt ได้*

**🔧 การปรับแต่งพารามิเตอร์:**
| พารามิเตอร์ | ช่วงที่แนะนำ | กรณีใช้งาน |
|-----------|------------------|----------|
| **Temperature** | 0.1-0.3 | ตอบกลับเชิงเทคนิค/ข้อเท็จจริง |
| **Temperature** | 0.7-0.9 | งานสร้างสรรค์/ระดมไอเดีย |
| **Max Tokens** | 500-1000 | คำตอบกระชับ |
| **Max Tokens** | 2000-4000 | คำอธิบายละเอียด |

### 🐍 ขั้นตอนที่ 3: แบบฝึกหัดปฏิบัติ - Agent โปรแกรมมิ่ง Python

**🎯 ภารกิจ**: สร้างผู้ช่วยโค้ด Python เฉพาะทาง

**📋 ขั้นตอนการตั้งค่า:**

1. **เลือกโมเดล**: เลือก **Claude 3.5 Sonnet** (เหมาะสำหรับโค้ด)

2. **ออกแบบ System Prompt**:
```markdown
# Python Programming Expert Agent

## Role
You are a senior Python developer with 10+ years of experience. You excel at writing clean, efficient, and well-documented Python code.

## Capabilities
- Write production-ready Python code
- Debug complex issues
- Explain code concepts clearly
- Suggest best practices and optimizations
- Provide complete working examples

## Response Format
- Always include docstrings
- Add inline comments for complex logic
- Suggest testing approaches
- Mention relevant libraries when applicable

## Code Quality Standards
- Follow PEP 8 style guidelines
- Use type hints where appropriate
- Handle exceptions gracefully
- Write readable, maintainable code
```

3. **ตั้งค่าพารามิเตอร์**:
   - Temperature: 0.2 (สำหรับโค้ดที่สม่ำเสมอและเชื่อถือได้)
   - Max Tokens: 2000 (คำอธิบายละเอียด)
   - Top-p: 0.9 (ความคิดสร้างสรรค์สมดุล)

![Python Agent Configuration](../../../../translated_images/pythonagent.5e51b406401c165fcabfd66f2d943c27f46b5fed0f9fb73abefc9e91ca3489d4.th.png)

### 🧪 ขั้นตอนที่ 4: ทดสอบ Python Agent ของคุณ

**สถานการณ์ทดสอบ:**
1. **ฟังก์ชันพื้นฐาน**: "สร้างฟังก์ชันค้นหาจำนวนเฉพาะ"
2. **อัลกอริทึมซับซ้อน**: "สร้าง binary search tree พร้อมฟังก์ชัน insert, delete, และ search"
3. **ปัญหาในโลกจริง**: "สร้างเว็บสแครปเปอร์ที่จัดการกับการจำกัดอัตราการร้องขอและการลองใหม่"
4. **แก้บั๊ก**: "แก้ไขโค้ดนี้ [วางโค้ดที่มีบั๊ก]"

**🏆 เกณฑ์ความสำเร็จ:**
- ✅ โค้ดทำงานไม่มีข้อผิดพลาด
- ✅ มีเอกสารประกอบอย่างเหมาะสม
- ✅ ปฏิบัติตามแนวทางปฏิบัติที่ดีที่สุดของ Python
- ✅ ให้คำอธิบายที่ชัดเจน
- ✅ เสนอแนะการปรับปรุง

## 🎓 สรุป Module 1 & ขั้นตอนถัดไป

### 📊 ตรวจสอบความรู้

ทดสอบความเข้าใจของคุณ:
- [ ] อธิบายความแตกต่างระหว่างโมเดลในแค็ตตาล็อกได้หรือไม่?
- [ ] สร้างและทดสอบ agent แบบกำหนดเองสำเร็จหรือไม่?
- [ ] เข้าใจวิธีปรับแต่งพารามิเตอร์สำหรับกรณีใช้งานต่างๆ หรือไม่?
- [ ] ออกแบบ system prompt ที่มีประสิทธิภาพได้หรือไม่?

### 📚 แหล่งข้อมูลเพิ่มเติม

- **AI Toolkit Documentation**: [Official Microsoft Docs](https://github.com/microsoft/vscode-ai-toolkit)
- **Prompt Engineering Guide**: [Best Practices](https://platform.openai.com/docs/guides/prompt-engineering)
- **Models in AI Toolkit**: [Models in Develpment](https://github.com/microsoft/vscode-ai-toolkit/blob/main/doc/models.md)

**🎉 ยินดีด้วย!** คุณได้เชี่ยวชาญพื้นฐานของ AI Toolkit และพร้อมที่จะสร้างแอป AI ขั้นสูงมากขึ้นแล้ว!

### 🔜 ไปยังโมดูลถัดไป

พร้อมสำหรับความสามารถขั้นสูงขึ้นหรือยัง? ไปที่ **[Module 2: MCP with AI Toolkit Fundamentals](../lab2/README.md)** เพื่อเรียนรู้วิธี:
- เชื่อมต่อ agents กับเครื่องมือภายนอกด้วย Model Context Protocol (MCP)
- สร้าง agents อัตโนมัติบนเบราว์เซอร์ด้วย Playwright
- รวม MCP servers กับ AI Toolkit agents ของคุณ
- เพิ่มพลังให้ agents ด้วยข้อมูลและความสามารถภายนอก

**ข้อจำกัดความรับผิดชอบ**:  
เอกสารฉบับนี้ได้รับการแปลโดยใช้บริการแปลภาษาด้วย AI [Co-op Translator](https://github.com/Azure/co-op-translator) แม้เราจะพยายามให้การแปลมีความถูกต้อง แต่โปรดทราบว่าการแปลอัตโนมัติอาจมีข้อผิดพลาดหรือความไม่แม่นยำ เอกสารต้นฉบับในภาษาต้นทางควรถือเป็นแหล่งข้อมูลที่เชื่อถือได้ สำหรับข้อมูลที่มีความสำคัญ ควรใช้การแปลโดยผู้เชี่ยวชาญด้านภาษามนุษย์ เราจะไม่รับผิดชอบต่อความเข้าใจผิดหรือการตีความที่ผิดพลาดที่เกิดขึ้นจากการใช้การแปลนี้