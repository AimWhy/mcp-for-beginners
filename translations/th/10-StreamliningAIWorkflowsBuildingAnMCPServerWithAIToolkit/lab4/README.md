<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "f83bc722dc758efffd68667d6a1db470",
  "translation_date": "2025-06-10T06:50:28+00:00",
  "source_file": "10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab4/README.md",
  "language_code": "th"
}
-->
# 🐙 Module 4: Practical MCP Development - Custom GitHub Clone Server

![Duration](https://img.shields.io/badge/Duration-30_minutes-blue?style=flat-square)
![Difficulty](https://img.shields.io/badge/Difficulty-Intermediate-orange?style=flat-square)
![MCP](https://img.shields.io/badge/MCP-Custom%20Server-purple?style=flat-square&logo=github)
![VS Code](https://img.shields.io/badge/VS%20Code-Integration-blue?style=flat-square&logo=visualstudiocode)
![GitHub Copilot](https://img.shields.io/badge/GitHub%20Copilot-Agent%20Mode-green?style=flat-square&logo=github)

> **⚡ เริ่มต้นอย่างรวดเร็ว:** สร้าง MCP server พร้อมใช้งานจริงที่ช่วยอัตโนมัติการโคลน repository บน GitHub และการเชื่อมต่อกับ VS Code ภายในเวลาเพียง 30 นาที!

## 🎯 วัตถุประสงค์การเรียนรู้

เมื่อจบแลปนี้ คุณจะสามารถ:

- ✅ สร้าง MCP server แบบกำหนดเองสำหรับกระบวนการพัฒนาจริง
- ✅ นำฟังก์ชันการโคลน repository ของ GitHub มาใช้งานผ่าน MCP
- ✅ เชื่อมต่อ MCP server แบบกำหนดเองกับ VS Code และ Agent Builder
- ✅ ใช้ GitHub Copilot ในโหมด Agent กับเครื่องมือ MCP แบบกำหนดเอง
- ✅ ทดสอบและนำ MCP server แบบกำหนดเองไปใช้งานในสภาพแวดล้อมจริง

## 📋 สิ่งที่ต้องเตรียม

- ผ่านแลป 1-3 (พื้นฐาน MCP และการพัฒนาขั้นสูง)
- สมัครสมาชิก GitHub Copilot ([สมัครฟรีได้ที่นี่](https://github.com/github-copilot/signup))
- ติดตั้ง VS Code พร้อมส่วนขยาย AI Toolkit และ GitHub Copilot
- ติดตั้งและตั้งค่า Git CLI เรียบร้อยแล้ว

## 🏗️ ภาพรวมโปรเจกต์

### **ความท้าทายในการพัฒนาจริง**
ในฐานะนักพัฒนา เรามักใช้ GitHub เพื่อโคลน repository และเปิดใน VS Code หรือ VS Code Insiders กระบวนการนี้ต้องทำด้วยมือซึ่งประกอบด้วย:
1. เปิด terminal/command prompt
2. ไปยังโฟลเดอร์ที่ต้องการ
3. รันคำสั่ง `git clone`
4. เปิด VS Code ในโฟลเดอร์ที่โคลนมา

**โซลูชัน MCP ของเราจะรวบรวมขั้นตอนเหล่านี้ให้เป็นคำสั่งอัจฉริยะคำเดียว!**

### **สิ่งที่คุณจะสร้าง**
**GitHub Clone MCP Server** (`git_mcp_server`) ที่มีฟีเจอร์ดังนี้:

| ฟีเจอร์ | คำอธิบาย | ประโยชน์ |
|---------|-------------|---------|
| 🔄 **โคลน repository อัจฉริยะ** | โคลน GitHub repos พร้อมตรวจสอบความถูกต้อง | ตรวจจับข้อผิดพลาดอัตโนมัติ |
| 📁 **จัดการไดเรกทอรีอย่างชาญฉลาด** | ตรวจสอบและสร้างไดเรกทอรีอย่างปลอดภัย | ป้องกันการเขียนทับข้อมูล |
| 🚀 **เชื่อมต่อ VS Code แบบข้ามแพลตฟอร์ม** | เปิดโปรเจกต์ใน VS Code/Insiders ได้ทันที | เปลี่ยนผ่านกระบวนการทำงานได้อย่างราบรื่น |
| 🛡️ **จัดการข้อผิดพลาดอย่างเข้มแข็ง** | รองรับปัญหาเครือข่าย สิทธิ์ และเส้นทางไฟล์ | พร้อมใช้งานในสภาพแวดล้อมจริง |

---

## 📖 การดำเนินการทีละขั้นตอน

### ขั้นตอนที่ 1: สร้าง GitHub Agent ใน Agent Builder

1. **เปิด Agent Builder** ผ่านส่วนขยาย AI Toolkit
2. **สร้าง agent ใหม่** โดยใช้การตั้งค่าดังนี้:
   ```
   Agent Name: GitHubAgent
   ```

3. **เริ่มต้น MCP server แบบกำหนดเอง:**
   - ไปที่ **Tools** → **Add Tool** → **MCP Server**
   - เลือก **"Create A new MCP Server"**
   - เลือก **Python template** เพื่อความยืดหยุ่นสูงสุด
   - **ชื่อ Server:** `git_mcp_server`

### ขั้นตอนที่ 2: ตั้งค่า GitHub Copilot Agent Mode

1. **เปิด GitHub Copilot** ใน VS Code (Ctrl/Cmd + Shift + P → "GitHub Copilot: Open")
2. **เลือก Agent Model** ในอินเทอร์เฟซของ Copilot
3. **เลือกโมเดล Claude 3.7** เพื่อเพิ่มความสามารถในการวิเคราะห์
4. **เปิดใช้งานการเชื่อมต่อ MCP** เพื่อเข้าถึงเครื่องมือ

> **💡 เคล็ดลับ:** Claude 3.7 มีความเข้าใจลึกซึ้งในกระบวนการพัฒนาและรูปแบบการจัดการข้อผิดพลาด

### ขั้นตอนที่ 3: พัฒนาฟังก์ชันหลักของ MCP Server

**ใช้ prompt รายละเอียดนี้ร่วมกับ GitHub Copilot Agent Mode:**

```
Create two MCP tools with the following comprehensive requirements:

🔧 TOOL A: clone_repository
Requirements:
- Clone any GitHub repository to a specified local folder
- Return the absolute path of the successfully cloned project
- Implement comprehensive validation:
  ✓ Check if target directory already exists (return error if exists)
  ✓ Validate GitHub URL format (https://github.com/user/repo)
  ✓ Verify git command availability (prompt installation if missing)
  ✓ Handle network connectivity issues
  ✓ Provide clear error messages for all failure scenarios

🚀 TOOL B: open_in_vscode
Requirements:
- Open specified folder in VS Code or VS Code Insiders
- Cross-platform compatibility (Windows/Linux/macOS)
- Use direct application launch (not terminal commands)
- Auto-detect available VS Code installations
- Handle cases where VS Code is not installed
- Provide user-friendly error messages

Additional Requirements:
- Follow MCP 1.9.3 best practices
- Include proper type hints and documentation
- Implement logging for debugging purposes
- Add input validation for all parameters
- Include comprehensive error handling
```

### ขั้นตอนที่ 4: ทดสอบ MCP Server ของคุณ

#### 4a. ทดสอบใน Agent Builder

1. **เริ่มการดีบัก** สำหรับ Agent Builder
2. **ตั้งค่า agent ด้วย system prompt นี้:**

```
SYSTEM_PROMPT:
You are my intelligent coding repository assistant. You help developers efficiently clone GitHub repositories and set up their development environment. Always provide clear feedback about operations and handle errors gracefully.
```

3. **ทดสอบด้วยสถานการณ์ผู้ใช้จริง:**

```
USER_PROMPT EXAMPLES:

Scenario : Basic Clone and Open
"Clone {Your GitHub Repo link such as https://github.com/kinfey/GHCAgentWorkshop
 } and save to {The global path you specify}, then open it with VS Code Insiders"
```

![Agent Builder Testing](../../../../translated_images/DebugAgent.81d152370c503241b3b39a251b8966f7f739286df19dd57f9147f6402214a012.th.png)

**ผลลัพธ์ที่คาดหวัง:**
- ✅ โคลนสำเร็จพร้อมยืนยันเส้นทาง
- ✅ เปิด VS Code อัตโนมัติ
- ✅ แสดงข้อความผิดพลาดชัดเจนในกรณีผิดพลาด
- ✅ จัดการกรณีพิเศษอย่างถูกต้อง

#### 4b. ทดสอบใน MCP Inspector

![MCP Inspector Testing](../../../../translated_images/DebugInspector.eb5c95f94c69a8ba36944941b9a3588309a3a2fae101ace470ee09bde41d1667.th.png)

---

**🎉 ยินดีด้วย!** คุณได้สร้าง MCP server ที่ใช้งานได้จริงและพร้อมใช้งานในสภาพแวดล้อมจริง ซึ่งช่วยแก้ไขปัญหากระบวนการพัฒนาจริงได้อย่างมีประสิทธิภาพ เซิร์ฟเวอร์โคลน GitHub แบบกำหนดเองของคุณแสดงให้เห็นถึงพลังของ MCP ในการอัตโนมัติและเพิ่มประสิทธิภาพการทำงานของนักพัฒนา

### 🏆 รางวัลที่ได้รับ:
- ✅ **MCP Developer** - สร้าง MCP server แบบกำหนดเอง
- ✅ **Workflow Automator** - ปรับปรุงกระบวนการพัฒนาให้รวดเร็วขึ้น
- ✅ **Integration Expert** - เชื่อมต่อเครื่องมือพัฒนาหลายตัวเข้าด้วยกัน
- ✅ **Production Ready** - สร้างโซลูชันพร้อมนำไปใช้งานจริง

---

## 🎓 การจบเวิร์กช็อป: การเดินทางของคุณกับ Model Context Protocol

**เรียน ผู้เข้าร่วมเวิร์กช็อป,**

ขอแสดงความยินดีที่คุณผ่านครบทั้งสี่โมดูลของเวิร์กช็อป Model Context Protocol! คุณได้เดินทางมาไกลตั้งแต่การเข้าใจพื้นฐาน AI Toolkit ไปจนถึงการสร้าง MCP server ที่พร้อมใช้งานจริงและแก้ไขปัญหากระบวนการพัฒนาจริง

### 🚀 สรุปเส้นทางการเรียนรู้ของคุณ:

**[Module 1](../lab1/README.md)**: เริ่มต้นด้วยการเรียนรู้พื้นฐาน AI Toolkit, การทดสอบโมเดล และสร้าง AI agent ตัวแรก

**[Module 2](../lab2/README.md)**: เรียนรู้สถาปัตยกรรม MCP, รวม Playwright MCP และสร้าง agent อัตโนมัติบนเบราว์เซอร์ตัวแรก

**[Module 3](../lab3/README.md)**: พัฒนาขึ้นสู่การสร้าง MCP server แบบกำหนดเองด้วย Weather MCP server และฝึกใช้เครื่องมือดีบัก

**[Module 4](../lab4/README.md)**: นำทุกอย่างมาประยุกต์ใช้สร้างเครื่องมืออัตโนมัติการจัดการ repository บน GitHub ที่ใช้งานได้จริง

### 🌟 สิ่งที่คุณเชี่ยวชาญ:

- ✅ **ระบบนิเวศ AI Toolkit**: โมเดล, agent และรูปแบบการรวมระบบ
- ✅ **สถาปัตยกรรม MCP**: การออกแบบ client-server, โปรโตคอลการสื่อสาร และความปลอดภัย
- ✅ **เครื่องมือสำหรับนักพัฒนา**: ตั้งแต่ Playground, Inspector จนถึงการนำไปใช้งานจริง
- ✅ **การพัฒนากำหนดเอง**: สร้าง, ทดสอบ และ deploy MCP server ของตัวเอง
- ✅ **การประยุกต์ใช้งานจริง**: แก้ปัญหากระบวนการพัฒนาด้วย AI

### 🔮 ก้าวต่อไปของคุณ:

1. **สร้าง MCP server ของตัวเอง**: ใช้ทักษะนี้เพื่ออัตโนมัติกระบวนการทำงานเฉพาะของคุณ
2. **เข้าร่วมชุมชน MCP**: แชร์ผลงานและเรียนรู้จากผู้อื่น
3. **สำรวจการเชื่อมต่อขั้นสูง**: เชื่อมต่อ MCP server กับระบบองค์กร
4. **ร่วมพัฒนาโอเพนซอร์ส**: ช่วยปรับปรุงเครื่องมือและเอกสารของ MCP

จำไว้ว่านี่เป็นเพียงจุดเริ่มต้น ระบบนิเวศ Model Context Protocol กำลังเติบโตอย่างรวดเร็ว และคุณพร้อมที่จะก้าวนำหน้าในโลกของเครื่องมือพัฒนาด้วย AI

**ขอบคุณที่เข้าร่วมและตั้งใจเรียนรู้!**

หวังว่าเวิร์กช็อปนี้จะจุดประกายไอเดียที่เปลี่ยนวิธีการสร้างและใช้งานเครื่องมือ AI ในเส้นทางพัฒนาของคุณ

**โค้ดอย่างมีความสุข!**

---

**ข้อจำกัดความรับผิดชอบ**:  
เอกสารนี้ได้รับการแปลโดยใช้บริการแปลภาษา AI [Co-op Translator](https://github.com/Azure/co-op-translator) แม้ว่าเราจะพยายามให้มีความถูกต้อง โปรดทราบว่าการแปลอัตโนมัติอาจมีข้อผิดพลาดหรือความไม่ถูกต้อง เอกสารต้นฉบับในภาษาดั้งเดิมควรถูกพิจารณาเป็นแหล่งข้อมูลที่เชื่อถือได้ สำหรับข้อมูลสำคัญแนะนำให้ใช้บริการแปลโดยผู้เชี่ยวชาญมนุษย์ เราไม่รับผิดชอบต่อความเข้าใจผิดหรือการตีความที่ผิดพลาดใด ๆ ที่เกิดจากการใช้การแปลนี้