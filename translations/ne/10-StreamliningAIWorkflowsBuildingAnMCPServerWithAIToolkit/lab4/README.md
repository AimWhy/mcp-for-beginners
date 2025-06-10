<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "f83bc722dc758efffd68667d6a1db470",
  "translation_date": "2025-06-10T06:46:30+00:00",
  "source_file": "10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab4/README.md",
  "language_code": "ne"
}
-->
# 🐙 Module 4: व्यावहारिक MCP विकास - कस्टम GitHub क्लोन सर्वर

![Duration](https://img.shields.io/badge/Duration-30_minutes-blue?style=flat-square)
![Difficulty](https://img.shields.io/badge/Difficulty-Intermediate-orange?style=flat-square)
![MCP](https://img.shields.io/badge/MCP-Custom%20Server-purple?style=flat-square&logo=github)
![VS Code](https://img.shields.io/badge/VS%20Code-Integration-blue?style=flat-square&logo=visualstudiocode)
![GitHub Copilot](https://img.shields.io/badge/GitHub%20Copilot-Agent%20Mode-green?style=flat-square&logo=github)

> **⚡ त्वरित शुरुआत:** सिर्फ 30 मिनट में एक प्रोडक्शन-रेडी MCP सर्वर बनाएं जो GitHub रिपॉजिटरी क्लोनिंग और VS Code इंटीग्रेशन को स्वचालित करता है!

## 🎯 सीखने के उद्देश्य

इस लैब के अंत तक, आप सक्षम होंगे:

- ✅ वास्तविक विकास वर्कफ़्लो के लिए एक कस्टम MCP सर्वर बनाना
- ✅ MCP के माध्यम से GitHub रिपॉजिटरी क्लोनिंग कार्यक्षमता लागू करना
- ✅ कस्टम MCP सर्वर को VS Code और Agent Builder के साथ इंटीग्रेट करना
- ✅ GitHub Copilot Agent Mode का उपयोग कस्टम MCP टूल्स के साथ करना
- ✅ प्रोडक्शन एनवायरनमेंट में कस्टम MCP सर्वर का परीक्षण और डिप्लॉय करना

## 📋 पूर्व आवश्यकताएँ

- Labs 1-3 (MCP मूल बातें और उन्नत विकास) पूरा किया हुआ हो
- GitHub Copilot सदस्यता ([फ्री साइनअप उपलब्ध](https://github.com/github-copilot/signup))
- VS Code जिसमें AI Toolkit और GitHub Copilot एक्सटेंशन्स इंस्टॉल हों
- Git CLI इंस्टॉल और कॉन्फ़िगर किया हुआ हो

## 🏗️ प्रोजेक्ट अवलोकन

### **वास्तविक विकास चुनौती**
डेवलपर्स के रूप में, हम अक्सर GitHub से रिपॉजिटरी क्लोन करते हैं और उन्हें VS Code या VS Code Insiders में खोलते हैं। यह मैनुअल प्रक्रिया होती है:
1. टर्मिनल/कमांड प्रॉम्प्ट खोलना
2. इच्छित डायरेक्टरी में नेविगेट करना
3. `git clone` कमांड चलाना
4. क्लोन की गई डायरेक्टरी में VS Code खोलना

**हमारा MCP समाधान इसे एक ही स्मार्ट कमांड में बदल देता है!**

### **आप क्या बनाएंगे**
एक **GitHub Clone MCP Server** (`git_mcp_server`) जो निम्न प्रदान करता है:

| फीचर | विवरण | लाभ |
|---------|-------------|---------|
| 🔄 **स्मार्ट रिपॉजिटरी क्लोनिंग** | GitHub रिपॉजिटरी को वैलिडेशन के साथ क्लोन करें | ऑटोमैटिक एरर चेकिंग |
| 📁 **इंटेलिजेंट डायरेक्टरी मैनेजमेंट** | डायरेक्टरी को सुरक्षित तरीके से चेक और क्रिएट करें | ओवरराइटिंग से बचाव |
| 🚀 **क्रॉस-प्लेटफॉर्म VS Code इंटीग्रेशन** | प्रोजेक्ट्स को VS Code/Insiders में खोलें | सहज वर्कफ़्लो ट्रांजिशन |
| 🛡️ **मजबूत एरर हैंडलिंग** | नेटवर्क, परमिशन और पाथ इश्यूज़ को संभालें | प्रोडक्शन-रेडी विश्वसनीयता |

---

## 📖 चरण-दर-चरण कार्यान्वयन

### चरण 1: Agent Builder में GitHub Agent बनाएं

1. **Agent Builder लॉन्च करें** AI Toolkit एक्सटेंशन के माध्यम से
2. **नया एजेंट बनाएं** निम्न कॉन्फ़िगरेशन के साथ:
   ```
   Agent Name: GitHubAgent
   ```

3. **कस्टम MCP सर्वर इनिशियलाइज़ करें:**
   - **Tools** → **Add Tool** → **MCP Server** पर जाएं
   - **"Create A new MCP Server"** चुनें
   - अधिकतम फ्लेक्सिबिलिटी के लिए **Python टेम्पलेट** चुनें
   - **Server Name:** `git_mcp_server`

### चरण 2: GitHub Copilot Agent Mode कॉन्फ़िगर करें

1. VS Code में **GitHub Copilot खोलें** (Ctrl/Cmd + Shift + P → "GitHub Copilot: Open")
2. Copilot इंटरफ़ेस में **Agent Model चुनें**
3. बेहतर reasoning के लिए **Claude 3.7 मॉडल चुनें**
4. टूल एक्सेस के लिए **MCP इंटीग्रेशन सक्षम करें**

> **💡 प्रो टिप:** Claude 3.7 विकास वर्कफ़्लो और एरर हैंडलिंग पैटर्न की बेहतर समझ प्रदान करता है।

### चरण 3: मुख्य MCP सर्वर कार्यक्षमता लागू करें

**GitHub Copilot Agent Mode के साथ निम्न विस्तृत प्रॉम्प्ट का उपयोग करें:**

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

### चरण 4: अपने MCP सर्वर का परीक्षण करें

#### 4a. Agent Builder में परीक्षण

1. Agent Builder के लिए **डिबग कॉन्फ़िगरेशन लॉन्च करें**
2. इस सिस्टम प्रॉम्प्ट के साथ अपने एजेंट को कॉन्फ़िगर करें:

```
SYSTEM_PROMPT:
You are my intelligent coding repository assistant. You help developers efficiently clone GitHub repositories and set up their development environment. Always provide clear feedback about operations and handle errors gracefully.
```

3. यथार्थवादी उपयोगकर्ता परिदृश्यों के साथ परीक्षण करें:

```
USER_PROMPT EXAMPLES:

Scenario : Basic Clone and Open
"Clone {Your GitHub Repo link such as https://github.com/kinfey/GHCAgentWorkshop
 } and save to {The global path you specify}, then open it with VS Code Insiders"
```

![Agent Builder Testing](../../../../translated_images/DebugAgent.81d152370c503241b3b39a251b8966f7f739286df19dd57f9147f6402214a012.ne.png)

**अपेक्षित परिणाम:**
- ✅ सफल क्लोनिंग और पाथ पुष्टि
- ✅ स्वचालित VS Code लॉन्च
- ✅ अमान्य परिदृश्यों के लिए स्पष्ट त्रुटि संदेश
- ✅ किनारे के मामलों का सही प्रबंधन

#### 4b. MCP Inspector में परीक्षण

![MCP Inspector Testing](../../../../translated_images/DebugInspector.eb5c95f94c69a8ba36944941b9a3588309a3a2fae101ace470ee09bde41d1667.ne.png)

---

**🎉 बधाई हो!** आपने एक व्यावहारिक, प्रोडक्शन-रेडी MCP सर्वर सफलतापूर्वक बनाया है जो वास्तविक विकास वर्कफ़्लो की समस्याओं को हल करता है। आपका कस्टम GitHub क्लोन सर्वर MCP की शक्ति को दिखाता है जो डेवलपर उत्पादकता को स्वचालित और बेहतर बनाता है।

### 🏆 उपलब्धियां:
- ✅ **MCP Developer** - कस्टम MCP सर्वर बनाया
- ✅ **Workflow Automator** - विकास प्रक्रियाओं को सुव्यवस्थित किया  
- ✅ **Integration Expert** - कई विकास टूल्स को जोड़ा
- ✅ **Production Ready** - डिप्लॉय करने योग्य समाधान बनाए

---

## 🎓 कार्यशाला पूर्णता: Model Context Protocol के साथ आपकी यात्रा

**प्रिय कार्यशाला प्रतिभागी,**

Model Context Protocol कार्यशाला के चारों मॉड्यूल पूरा करने पर बधाई! आपने AI Toolkit की मूल अवधारणाओं को समझने से लेकर वास्तविक विकास चुनौतियों को हल करने वाले प्रोडक्शन-रेडी MCP सर्वर बनाने तक लंबा सफर तय किया है।

### 🚀 आपकी सीखने की यात्रा का सारांश:

**[Module 1](../lab1/README.md)**: AI Toolkit की मूल बातें, मॉडल परीक्षण, और पहला AI एजेंट बनाना।

**[Module 2](../lab2/README.md)**: MCP आर्किटेक्चर सीखना, Playwright MCP इंटीग्रेशन, और पहला ब्राउज़र ऑटोमेशन एजेंट बनाना।

**[Module 3](../lab3/README.md)**: Weather MCP सर्वर के साथ कस्टम MCP सर्वर विकास और डिबगिंग टूल्स में महारत हासिल करना।

**[Module 4](../lab4/README.md)**: अब आपने एक व्यावहारिक GitHub रिपॉजिटरी वर्कफ़्लो ऑटोमेशन टूल बनाया है।

### 🌟 आपने क्या महारत हासिल की:

- ✅ **AI Toolkit इकोसिस्टम**: मॉडल, एजेंट, और इंटीग्रेशन पैटर्न
- ✅ **MCP आर्किटेक्चर**: क्लाइंट-सर्वर डिज़ाइन, ट्रांसपोर्ट प्रोटोकॉल, और सुरक्षा
- ✅ **डेवलपर टूल्स**: Playground से Inspector तक और प्रोडक्शन डिप्लॉयमेंट तक
- ✅ **कस्टम विकास**: अपने MCP सर्वर बनाना, टेस्ट करना, और डिप्लॉय करना
- ✅ **व्यावहारिक अनुप्रयोग**: AI के साथ वास्तविक वर्कफ़्लो चुनौतियों को हल करना

### 🔮 आपके अगले कदम:

1. **अपना खुद का MCP सर्वर बनाएं**: इन कौशलों का उपयोग कर अपने अनूठे वर्कफ़्लो को स्वचालित करें
2. **MCP समुदाय में शामिल हों**: अपनी रचनाएँ साझा करें और दूसरों से सीखें
3. **उन्नत इंटीग्रेशन एक्सप्लोर करें**: MCP सर्वर को एंटरप्राइज सिस्टम से कनेक्ट करें
4. **ओपन सोर्स में योगदान दें**: MCP टूलिंग और डॉक्यूमेंटेशन को बेहतर बनाएं

याद रखें, यह कार्यशाला केवल शुरुआत है। Model Context Protocol इकोसिस्टम तेजी से विकसित हो रहा है, और अब आप AI-संचालित विकास टूल्स के अग्रिम पंक्ति में हैं।

**आपकी भागीदारी और सीखने के लिए धन्यवाद!**

हमें उम्मीद है कि इस कार्यशाला ने आपके लिए नए विचार जगाए होंगे जो आपके विकास सफर में AI टूल्स के साथ आपके इंटरैक्शन को बदल देंगे।

**खुशहाल कोडिंग!**

---

**अस्वीकरण**:  
यो दस्तावेज AI अनुवाद सेवा [Co-op Translator](https://github.com/Azure/co-op-translator) को प्रयोग गरी अनुवाद गरिएको हो। हामी शुद्धताका लागि प्रयास गर्छौं, तर कृपया ध्यान दिनुहोस् कि स्वचालित अनुवादमा त्रुटिहरू वा गलतफहमीहरू हुन सक्छन्। मूल दस्तावेज यसको मूल भाषामा नै अधिकारिक स्रोत मानिनुपर्छ। महत्वपूर्ण जानकारीको लागि व्यावसायिक मानवीय अनुवाद सिफारिस गरिन्छ। यस अनुवादको प्रयोगबाट उत्पन्न कुनै पनि गलत बुझाइ वा गलत व्याख्याका लागि हामी जिम्मेवार छैनौं।