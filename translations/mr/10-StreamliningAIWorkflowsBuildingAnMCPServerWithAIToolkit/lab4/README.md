<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "f83bc722dc758efffd68667d6a1db470",
  "translation_date": "2025-06-10T06:45:47+00:00",
  "source_file": "10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab4/README.md",
  "language_code": "mr"
}
-->
# 🐙 Module 4: Practical MCP Development - Custom GitHub Clone Server

![Duration](https://img.shields.io/badge/Duration-30_minutes-blue?style=flat-square)
![Difficulty](https://img.shields.io/badge/Difficulty-Intermediate-orange?style=flat-square)
![MCP](https://img.shields.io/badge/MCP-Custom%20Server-purple?style=flat-square&logo=github)
![VS Code](https://img.shields.io/badge/VS%20Code-Integration-blue?style=flat-square&logo=visualstudiocode)
![GitHub Copilot](https://img.shields.io/badge/GitHub%20Copilot-Agent%20Mode-green?style=flat-square&logo=github)

> **⚡ जलद प्रारंभ:** फक्त 30 मिनिटांत GitHub रिपॉजिटरी क्लोनिंग आणि VS Code इंटिग्रेशन ऑटोमेट करणारा प्रोडक्शन-तयार MCP सर्व्हर तयार करा!

## 🎯 शिकण्याचे उद्दिष्टे

या लॅबच्या शेवटी, तुम्ही करू शकणार:

- ✅ रिअल-वर्ल्ड विकासासाठी कस्टम MCP सर्व्हर तयार करणे
- ✅ MCP वापरून GitHub रिपॉजिटरी क्लोनिंग फंक्शनॅलिटी अंमलात आणणे
- ✅ कस्टम MCP सर्व्हर VS Code आणि Agent Builder सोबत इंटिग्रेट करणे
- ✅ GitHub Copilot Agent Mode कस्टम MCP टूल्ससह वापरणे
- ✅ प्रोडक्शन एन्व्हायर्नमेंटमध्ये कस्टम MCP सर्व्हर टेस्ट आणि डिप्लॉय करणे

## 📋 पूर्वअट

- Labs 1-3 पूर्ण केलेले असणे (MCP मूलतत्त्वे आणि प्रगत विकास)
- GitHub Copilot सदस्यत्व ([मुफ्त साइनअप उपलब्ध](https://github.com/github-copilot/signup))
- VS Code मध्ये AI Toolkit आणि GitHub Copilot एक्सटेंशन्स इन्स्टॉल केलेले असणे
- Git CLI इन्स्टॉल आणि कॉन्फिगर केलेले असणे

## 🏗️ प्रोजेक्टचा आढावा

### **रिअल-वर्ल्ड विकास आव्हान**
विकसक म्हणून, आपण बर्‍याचदा GitHub वरून रिपॉजिटरी क्लोन करून ती VS Code किंवा VS Code Insiders मध्ये उघडतो. हा मॅन्युअल प्रोसेस खालीलप्रमाणे असतो:
1. टर्मिनल/कमांड प्रॉम्प्ट उघडणे
2. इच्छित डायरेक्टरीमध्ये नेव्हिगेट करणे
3. `git clone` कमांड चालवणे
4. क्लोन केलेल्या डायरेक्टरीमध्ये VS Code उघडणे

**आपल्या MCP सोल्यूशनमुळे हा सगळा प्रोसेस एका स्मार्ट कमांडमध्ये सुलभ होतो!**

### **तुम्ही काय तयार करणार आहात**
एक **GitHub Clone MCP Server** (`git_mcp_server`) जो खालील सेवा देतो:

| वैशिष्ट्य | वर्णन | फायदा |
|---------|-------------|---------|
| 🔄 **स्मार्ट रिपॉजिटरी क्लोनिंग** | GitHub रेपोज क्लोन करा आणि व्हॅलिडेशन करा | त्रुटी तपासणी स्वयंचलित |
| 📁 **इंटेलिजेंट डायरेक्टरी मॅनेजमेंट** | डायरेक्टरी सुरक्षितपणे तपासा आणि तयार करा | ओव्हरराइटिंग टाळते |
| 🚀 **क्रॉस-प्लॅटफॉर्म VS Code इंटिग्रेशन** | प्रोजेक्ट्स VS Code/Insiders मध्ये उघडा | सुरळीत वर्कफ्लो ट्रांझिशन |
| 🛡️ **मजबूत त्रुटी हाताळणी** | नेटवर्क, परवानगी, आणि पाथ समस्यांवर नियंत्रण | प्रोडक्शन-तयार विश्वसनीयता |

---

## 📖 टप्प्याटप्प्याने अंमलबजावणी

### टप्पा 1: Agent Builder मध्ये GitHub Agent तयार करा

1. AI Toolkit एक्सटेंशनमधून **Agent Builder सुरू करा**
2. पुढील कॉन्फिगरेशनसह **नवीन एजंट तयार करा:**
   ```
   Agent Name: GitHubAgent
   ```

3. **कस्टम MCP सर्व्हर सुरू करा:**
   - **Tools** → **Add Tool** → **MCP Server** मध्ये जा
   - **"Create A new MCP Server"** निवडा
   - जास्त लवचीकतेसाठी **Python टेम्प्लेट** निवडा
   - **Server Name:** `git_mcp_server`

### टप्पा 2: GitHub Copilot Agent Mode कॉन्फिगर करा

1. VS Code मध्ये **GitHub Copilot उघडा** (Ctrl/Cmd + Shift + P → "GitHub Copilot: Open")
2. Copilot इंटरफेसमध्ये **Agent Model निवडा**
3. सुधारित विचारसरणीसाठी **Claude 3.7 मॉडेल निवडा**
4. टूल प्रवेशासाठी **MCP इंटिग्रेशन सक्षम करा**

> **💡 प्रो टिप:** Claude 3.7 विकास वर्कफ्लो आणि त्रुटी हाताळणी पॅटर्न्सची उत्कृष्ट समज देते.

### टप्पा 3: मुख्य MCP सर्व्हर फंक्शनॅलिटी अंमलात आणा

**GitHub Copilot Agent Mode सोबत खालील तपशीलवार प्रॉम्प्ट वापरा:**

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

### टप्पा 4: तुमचा MCP सर्व्हर टेस्ट करा

#### 4a. Agent Builder मध्ये टेस्टिंग

1. Agent Builder साठी **डिबग कॉन्फिगरेशन सुरू करा**
2. तुमच्या एजंटसाठी खालील सिस्टम प्रॉम्प्ट सेट करा:

```
SYSTEM_PROMPT:
You are my intelligent coding repository assistant. You help developers efficiently clone GitHub repositories and set up their development environment. Always provide clear feedback about operations and handle errors gracefully.
```

3. वास्तविक वापरकर्ता परिस्थितींसह टेस्ट करा:

```
USER_PROMPT EXAMPLES:

Scenario : Basic Clone and Open
"Clone {Your GitHub Repo link such as https://github.com/kinfey/GHCAgentWorkshop
 } and save to {The global path you specify}, then open it with VS Code Insiders"
```

![Agent Builder Testing](../../../../translated_images/DebugAgent.81d152370c503241b3b39a251b8966f7f739286df19dd57f9147f6402214a012.mr.png)

**अपेक्षित निकाल:**
- ✅ पाथ पुष्टीसह यशस्वी क्लोनिंग
- ✅ VS Code आपोआप सुरू होणे
- ✅ चुकीच्या परिस्थितीसाठी स्पष्ट त्रुटी संदेश
- ✅ कोपऱ्याच्या प्रकरणांची योग्य हाताळणी

#### 4b. MCP Inspector मध्ये टेस्ट करा

![MCP Inspector Testing](../../../../translated_images/DebugInspector.eb5c95f94c69a8ba36944941b9a3588309a3a2fae101ace470ee09bde41d1667.mr.png)

---

**🎉 अभिनंदन!** तुम्ही यशस्वीपणे एक व्यावहारिक, प्रोडक्शन-तयार MCP सर्व्हर तयार केला आहे जो विकास वर्कफ्लोच्या आव्हानांना सोडवतो. तुमचा कस्टम GitHub क्लोन सर्व्हर MCP च्या सामर्थ्याचे उदाहरण आहे ज्यामुळे विकासकांची उत्पादकता वाढते.

### 🏆 मिळवलेले कौशल्य:
- ✅ **MCP Developer** - कस्टम MCP सर्व्हर तयार केला
- ✅ **Workflow Automator** - विकास प्रक्रियांचा सुलभ प्रवाह निर्माण केला  
- ✅ **Integration Expert** - अनेक विकास टूल्स कनेक्ट केले
- ✅ **Production Ready** - डिप्लॉय करण्यायोग्य सोल्यूशन्स तयार केली

---

## 🎓 वर्कशॉप पूर्णता: Model Context Protocol सह तुमचा प्रवास

**प्रिय वर्कशॉप सहभागी,**

Model Context Protocol वर्कशॉपचे सर्व चार मॉड्यूल पूर्ण केल्याबद्दल अभिनंदन! तुम्ही AI Toolkit च्या मूलभूत संकल्पना समजून घेण्यापासून प्रोडक्शन-तयार MCP सर्व्हर्स तयार करण्यापर्यंत खूप काही शिकलात.

### 🚀 तुमचा शिकण्याचा प्रवास:

**[Module 1](../lab1/README.md)**: AI Toolkit मूलतत्त्वे, मॉडेल टेस्टिंग, आणि तुमचा पहिला AI एजंट तयार करणे.

**[Module 2](../lab2/README.md)**: MCP आर्किटेक्चर समजून घेणे, Playwright MCP इंटिग्रेट करणे, आणि पहिला ब्राउझर ऑटोमेशन एजंट तयार करणे.

**[Module 3](../lab3/README.md)**: Weather MCP सर्व्हर सोबत कस्टम MCP सर्व्हर विकास आणि डिबगिंग टूल्समध्ये प्रावीण्य मिळवणे.

**[Module 4](../lab4/README.md)**: रिअल GitHub रिपॉजिटरी वर्कफ्लो ऑटोमेशन टूल तयार करणे.

### 🌟 तुम्ही काय पारंगत झाला आहात:

- ✅ **AI Toolkit इकोसिस्टम**: मॉडेल्स, एजंट्स, आणि इंटिग्रेशन पॅटर्न्स
- ✅ **MCP आर्किटेक्चर**: क्लायंट-सर्व्हर डिझाइन, ट्रान्सपोर्ट प्रोटोकॉल्स, आणि सुरक्षा
- ✅ **विकासक टूल्स**: Playground, Inspector, आणि प्रोडक्शन डिप्लॉयमेंट
- ✅ **कस्टम विकास**: स्वतःचे MCP सर्व्हर तयार करणे, टेस्ट करणे, आणि डिप्लॉय करणे
- ✅ **प्रॅक्टिकल अप्लिकेशन्स**: AI वापरून रिअल-वर्ल्ड वर्कफ्लो समस्यांचे निराकरण

### 🔮 पुढील पावले:

1. **तुमचा स्वतःचा MCP सर्व्हर तयार करा**: तुमचे खास वर्कफ्लो ऑटोमेट करा
2. **MCP समुदायात सहभागी व्हा**: तुमची निर्मिती शेअर करा आणि इतरांकडून शिका
3. **प्रगत इंटिग्रेशन एक्सप्लोर करा**: MCP सर्व्हर्स एंटरप्राइज सिस्टिम्सशी जोडा
4. **ओपन सोर्समध्ये योगदान द्या**: MCP टूलिंग आणि डॉक्युमेंटेशन सुधारण्यात मदत करा

हे वर्कशॉप फक्त सुरुवात आहे. Model Context Protocol इकोसिस्टम जलद विकसित होत आहे आणि तुम्ही आता AI-चालित विकास टूल्सच्या पुढाऱ्यांमध्ये आहात.

**तुमच्या सहभागासाठी आणि शिकण्याच्या समर्पणासाठी धन्यवाद!**

आशा आहे की हा वर्कशॉप तुम्हाला नवीन कल्पना देईल ज्यामुळे तुम्ही AI टूल्ससोबत तुमचा विकास प्रवास अधिक प्रभावी बनवाल.

**खुश coding!**

---

**अस्वीकरण**:  
हा दस्तऐवज AI भाषांतर सेवा [Co-op Translator](https://github.com/Azure/co-op-translator) वापरून भाषांतरित केला आहे. आम्ही अचूकतेसाठी प्रयत्न करतो, परंतु कृपया लक्षात ठेवा की स्वयंचलित भाषांतरांमध्ये चुका किंवा अचूकतेच्या त्रुटी असू शकतात. मूळ दस्तऐवज त्याच्या स्थानिक भाषेत अधिकृत स्रोत मानला जावा. महत्त्वाच्या माहितीसाठी व्यावसायिक मानवी भाषांतर शिफारसीय आहे. या भाषांतराच्या वापरामुळे उद्भवलेल्या कोणत्याही गैरसमजुती किंवा चुकीच्या अर्थलागी आम्ही जबाबदार नाही.