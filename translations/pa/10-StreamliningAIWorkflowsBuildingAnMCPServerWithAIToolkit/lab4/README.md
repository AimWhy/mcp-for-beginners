<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "f83bc722dc758efffd68667d6a1db470",
  "translation_date": "2025-06-10T06:46:57+00:00",
  "source_file": "10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab4/README.md",
  "language_code": "pa"
}
-->
# 🐙 ਮੋਡੀਊਲ 4: ਪ੍ਰੈਕਟਿਕਲ MCP ਵਿਕਾਸ - ਕਸਟਮ GitHub ਕਲੋਨ ਸਰਵਰ

![Duration](https://img.shields.io/badge/Duration-30_minutes-blue?style=flat-square)
![Difficulty](https://img.shields.io/badge/Difficulty-Intermediate-orange?style=flat-square)
![MCP](https://img.shields.io/badge/MCP-Custom%20Server-purple?style=flat-square&logo=github)
![VS Code](https://img.shields.io/badge/VS%20Code-Integration-blue?style=flat-square&logo=visualstudiocode)
![GitHub Copilot](https://img.shields.io/badge/GitHub%20Copilot-Agent%20Mode-green?style=flat-square&logo=github)

> **⚡ ਤੇਜ਼ ਸ਼ੁਰੂਆਤ:** ਸਿਰਫ 30 ਮਿੰਟਾਂ ਵਿੱਚ ਇੱਕ ਪ੍ਰੋਡਕਸ਼ਨ-ਤਿਆਰ MCP ਸਰਵਰ ਬਣਾਓ ਜੋ GitHub ਰਿਪੋਜ਼ਿਟਰੀ ਕਲੋਨਿੰਗ ਅਤੇ VS Code ਇੰਟੀਗ੍ਰੇਸ਼ਨ ਨੂੰ ਆਟੋਮੇਟ ਕਰਦਾ ਹੈ!

## 🎯 ਸਿੱਖਣ ਦੇ ਉਦੇਸ਼

ਇਸ ਲੈਬ ਦੇ ਅੰਤ ਤੱਕ, ਤੁਸੀਂ ਸਮਰੱਥ ਹੋਵੋਗੇ:

- ✅ ਅਸਲੀ ਦੁਨੀਆ ਦੇ ਵਿਕਾਸ ਵਰਕਫਲੋਜ਼ ਲਈ ਕਸਟਮ MCP ਸਰਵਰ ਬਣਾਉਣਾ
- ✅ MCP ਰਾਹੀਂ GitHub ਰਿਪੋਜ਼ਿਟਰੀ ਕਲੋਨਿੰਗ ਦੀ ਫੰਕਸ਼ਨਾਲਿਟੀ ਲਾਗੂ ਕਰਨਾ
- ✅ VS Code ਅਤੇ Agent Builder ਨਾਲ ਕਸਟਮ MCP ਸਰਵਰਾਂ ਨੂੰ ਇੰਟੀਗ੍ਰੇਟ ਕਰਨਾ
- ✅ GitHub Copilot Agent Mode ਨੂੰ ਕਸਟਮ MCP ਟੂਲਜ਼ ਨਾਲ ਵਰਤਣਾ
- ✅ ਪ੍ਰੋਡਕਸ਼ਨ ਵਾਤਾਵਰਨ ਵਿੱਚ ਕਸਟਮ MCP ਸਰਵਰਾਂ ਦੀ ਟੈਸਟਿੰਗ ਅਤੇ ਡਿਪਲੋਇਮੈਂਟ ਕਰਨਾ

## 📋 ਜ਼ਰੂਰੀ ਸ਼ਰਤਾਂ

- Labs 1-3 ਦੀ ਪੂਰੀ ਹੋਣੀ (MCP ਦੇ ਮੂਲ ਅਤੇ ਅਡਵਾਂਸਡ ਵਿਕਾਸ)
- GitHub Copilot ਦੀ ਸਬਸਕ੍ਰਿਪਸ਼ਨ ([ਮੁਫ਼ਤ ਸਾਈਨਅਪ ਉਪਲਬਧ](https://github.com/github-copilot/signup))
- VS Code ਜਿਸ ਵਿੱਚ AI Toolkit ਅਤੇ GitHub Copilot ਐਕਸਟੈਂਸ਼ਨ ਇੰਸਟਾਲ ਹੋਣ
- Git CLI ਇੰਸਟਾਲ ਅਤੇ ਕਨਫਿਗਰ ਕੀਤਾ ਹੋਇਆ

## 🏗️ ਪ੍ਰੋਜੈਕਟ ਦਾ ਜਾਇਜ਼ਾ

### **ਅਸਲੀ ਦੁਨੀਆ ਦਾ ਵਿਕਾਸ ਚੈਲੰਜ**  
ਡਿਵੈਲਪਰਾਂ ਵਜੋਂ ਅਸੀਂ ਅਕਸਰ GitHub ਤੋਂ ਰਿਪੋਜ਼ਿਟਰੀਜ਼ ਕਲੋਨ ਕਰਦੇ ਹਾਂ ਅਤੇ ਉਹਨਾਂ ਨੂੰ VS Code ਜਾਂ VS Code Insiders ਵਿੱਚ ਖੋਲ੍ਹਦੇ ਹਾਂ। ਇਹ ਮੈਨੁਅਲ ਪ੍ਰਕਿਰਿਆ ਵਿੱਚ ਸ਼ਾਮਲ ਹੈ:  
1. ਟਰਮੀਨਲ/ਕਮਾਂਡ ਪ੍ਰਾਂਪਟ ਖੋਲ੍ਹਣਾ  
2. ਚਾਹੀਦੇ ਡਾਇਰੈਕਟਰੀ ਵਿੱਚ ਜਾਣਾ  
3. `git clone` ਕਮਾਂਡ ਚਲਾਉਣਾ  
4. ਕਲੋਨ ਕੀਤੀ ਡਾਇਰੈਕਟਰੀ ਵਿੱਚ VS Code ਖੋਲ੍ਹਣਾ  

**ਸਾਡਾ MCP ਹੱਲ ਇਹ ਸਾਰਾ ਕੰਮ ਇੱਕ ਸਮਝਦਾਰ ਕਮਾਂਡ ਵਿੱਚ ਸਮੇਟਦਾ ਹੈ!**

### **ਤੁਸੀਂ ਕੀ ਬਣਾਉਗੇ**  
ਇੱਕ **GitHub Clone MCP Server** (`git_mcp_server`) ਜੋ ਇਹ ਮੁਹੱਈਆ ਕਰਵਾਉਂਦਾ ਹੈ:

| ਫੀਚਰ | ਵਰਣਨ | ਫਾਇਦਾ |
|---------|-------------|---------|
| 🔄 **ਸਮਾਰਟ ਰਿਪੋਜ਼ਿਟਰੀ ਕਲੋਨਿੰਗ** | GitHub ਰਿਪੋਜ਼ ਕਲੋਨ ਕਰੋ validation ਨਾਲ | ਆਟੋਮੈਟਿਕ ਗਲਤੀ ਚੈੱਕਿੰਗ |
| 📁 **ਸਮਝਦਾਰ ਡਾਇਰੈਕਟਰੀ ਪ੍ਰਬੰਧਨ** | ਡਾਇਰੈਕਟਰੀਆਂ ਨੂੰ ਸੁਰੱਖਿਅਤ ਤਰੀਕੇ ਨਾਲ ਚੈੱਕ ਅਤੇ ਬਣਾਓ | ਓਵਰਰਾਈਟਿੰਗ ਤੋਂ ਬਚਾਅ |
| 🚀 **ਕ੍ਰਾਸ-ਪਲੇਟਫਾਰਮ VS Code ਇੰਟੀਗ੍ਰੇਸ਼ਨ** | ਪ੍ਰੋਜੈਕਟ VS Code/Insiders ਵਿੱਚ ਖੋਲ੍ਹੋ | ਬਿਨਾਂ ਰੁਕਾਵਟ ਵਰਕਫਲੋਅ |
| 🛡️ **ਮਜ਼ਬੂਤ ਗਲਤੀ ਸੰਭਾਲ** | ਨੈੱਟਵਰਕ, ਪਰਮਿਸ਼ਨ ਅਤੇ ਪਾਥ ਸਮੱਸਿਆਵਾਂ ਦਾ ਹੱਲ | ਪ੍ਰੋਡਕਸ਼ਨ ਲਈ ਤਿਆਰ ਭਰੋਸੇਯੋਗਤਾ |

---

## 📖 ਕਦਮ-ਦਰ-कਦਮ ਲਾਗੂ ਕਰਨ ਦੀ ਪ੍ਰਕਿਰਿਆ

### ਕਦਮ 1: Agent Builder ਵਿੱਚ GitHub Agent ਬਣਾਓ

1. AI Toolkit ਐਕਸਟੈਂਸ਼ਨ ਰਾਹੀਂ **Agent Builder ਖੋਲ੍ਹੋ**  
2. ਹੇਠਾਂ ਦਿੱਤੀ ਕਨਫਿਗਰੇਸ਼ਨ ਨਾਲ **ਨਵਾਂ ਏਜੰਟ ਬਣਾਓ**:  
   ```
   Agent Name: GitHubAgent
   ```

3. **ਕਸਟਮ MCP ਸਰਵਰ ਸ਼ੁਰੂ ਕਰੋ:**  
   - **Tools** → **Add Tool** → **MCP Server** ਤੇ ਜਾਓ  
   - **"Create A new MCP Server"** ਚੁਣੋ  
   - ਵੱਧ ਤੋਂ ਵੱਧ ਲਚੀਲਾਪਣ ਲਈ **Python template** ਚੁਣੋ  
   - **Server Name:** `git_mcp_server`

### ਕਦਮ 2: GitHub Copilot Agent Mode ਸੈੱਟ ਕਰੋ

1. VS Code ਵਿੱਚ **GitHub Copilot ਖੋਲ੍ਹੋ** (Ctrl/Cmd + Shift + P → "GitHub Copilot: Open")  
2. Copilot ਇੰਟਰਫੇਸ ਵਿੱਚ **Agent Model ਚੁਣੋ**  
3. ਵਧੀਆ ਸੋਚ ਸਮਝ ਲਈ **Claude 3.7 ਮਾਡਲ** ਚੁਣੋ  
4. ਟੂਲ ਐਕਸੈਸ ਲਈ **MCP ਇੰਟੀਗ੍ਰੇਸ਼ਨ ਐਨੇਬਲ ਕਰੋ**

> **💡 ਪ੍ਰੋ ਟਿਪ:** Claude 3.7 ਵਿਕਾਸ ਵਰਕਫਲੋਜ਼ ਅਤੇ ਗਲਤੀ ਸੰਭਾਲ ਪੈਟਰਨਾਂ ਦੀ ਬਿਹਤਰ ਸਮਝ ਦਿੰਦਾ ਹੈ।

### ਕਦਮ 3: MCP ਸਰਵਰ ਦੀ ਮੁੱਖ ਫੰਕਸ਼ਨਾਲਿਟੀ ਲਾਗੂ ਕਰੋ

**GitHub Copilot Agent Mode ਨਾਲ ਹੇਠਾਂ ਦਿੱਤਾ ਵਿਸਥਾਰਪੂਰਕ ਪ੍ਰੰਪਟ ਵਰਤੋਂ:**

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

### ਕਦਮ 4: ਆਪਣੇ MCP ਸਰਵਰ ਦੀ ਟੈਸਟਿੰਗ ਕਰੋ

#### 4a. Agent Builder ਵਿੱਚ ਟੈਸਟ ਕਰੋ

1. Agent Builder ਲਈ **ਡਿਬੱਗ ਕਨਫਿਗਰੇਸ਼ਨ ਸ਼ੁਰੂ ਕਰੋ**  
2. ਹੇਠਾਂ ਦਿੱਤੇ ਸਿਸਟਮ ਪ੍ਰੰਪਟ ਨਾਲ ਆਪਣੇ ਏਜੰਟ ਨੂੰ ਕਨਫਿਗਰ ਕਰੋ:

```
SYSTEM_PROMPT:
You are my intelligent coding repository assistant. You help developers efficiently clone GitHub repositories and set up their development environment. Always provide clear feedback about operations and handle errors gracefully.
```

3. ਹਕੀਕਤੀ ਯੂਜ਼ਰ ਸਿਨਾਰਿਓਜ਼ ਨਾਲ ਟੈਸਟ ਕਰੋ:

```
USER_PROMPT EXAMPLES:

Scenario : Basic Clone and Open
"Clone {Your GitHub Repo link such as https://github.com/kinfey/GHCAgentWorkshop
 } and save to {The global path you specify}, then open it with VS Code Insiders"
```

![Agent Builder Testing](../../../../translated_images/DebugAgent.81d152370c503241b3b39a251b8966f7f739286df19dd57f9147f6402214a012.pa.png)

**ਉਮੀਦ ਕੀਤੇ ਨਤੀਜੇ:**  
- ✅ ਸਫਲ ਕਲੋਨਿੰਗ ਅਤੇ ਪਾਥ ਦੀ ਪੁਸ਼ਟੀ  
- ✅ VS Code ਦਾ ਆਟੋਮੈਟਿਕ ਸ਼ੁਰੂ ਹੋਣਾ  
- ✅ ਗਲਤ ਸਥਿਤੀਆਂ ਲਈ ਸਾਫ਼-ਸੁਥਰੇ ਗਲਤੀ ਸੁਨੇਹੇ  
- ✅ ਅਜਿਹੇ ਕੇਸਾਂ ਦੀ ਠੀਕ ਸੰਭਾਲ

#### 4b. MCP Inspector ਵਿੱਚ ਟੈਸਟ ਕਰੋ

![MCP Inspector Testing](../../../../translated_images/DebugInspector.eb5c95f94c69a8ba36944941b9a3588309a3a2fae101ace470ee09bde41d1667.pa.png)

---

**🎉 ਵਧਾਈ ਹੋਵੇ!** ਤੁਸੀਂ ਸਫਲਤਾਪੂਰਵਕ ਇੱਕ ਪ੍ਰੈਕਟਿਕਲ, ਪ੍ਰੋਡਕਸ਼ਨ-ਤਿਆਰ MCP ਸਰਵਰ ਬਣਾਇਆ ਹੈ ਜੋ ਅਸਲੀ ਵਿਕਾਸ ਵਰਕਫਲੋ ਚੈਲੰਜਾਂ ਦਾ ਹੱਲ ਹੈ। ਤੁਹਾਡਾ ਕਸਟਮ GitHub ਕਲੋਨ ਸਰਵਰ MCP ਦੀ ਤਾਕਤ ਨੂੰ ਦਰਸਾਉਂਦਾ ਹੈ ਜੋ ਡਿਵੈਲਪਰ ਦੀ ਉਤਪਾਦਕਤਾ ਨੂੰ ਆਟੋਮੇਟ ਅਤੇ ਸੁਧਾਰਦਾ ਹੈ।

### 🏆 ਪ੍ਰਾਪਤੀ:  
- ✅ **MCP Developer** - ਕਸਟਮ MCP ਸਰਵਰ ਬਣਾਇਆ  
- ✅ **Workflow Automator** - ਵਿਕਾਸ ਪ੍ਰਕਿਰਿਆਵਾਂ ਨੂੰ ਸੁਚਾਰੂ ਬਣਾਇਆ  
- ✅ **Integration Expert** - ਕਈ ਵਿਕਾਸ ਟੂਲਜ਼ ਨੂੰ ਜੋੜਿਆ  
- ✅ **Production Ready** - ਡਿਪਲੋਏ ਕਰਨ ਯੋਗ ਹੱਲ ਬਣਾਇਆ

---

## 🎓 ਵਰਕਸ਼ਾਪ ਪੂਰਾ: Model Context Protocol ਨਾਲ ਤੁਹਾਡਾ ਸਫਰ

**ਪਿਆਰੇ ਵਰਕਸ਼ਾਪ ਭਾਗੀਦਾਰ,**

Model Context Protocol ਵਰਕਸ਼ਾਪ ਦੇ ਸਾਰੇ ਚਾਰ ਮੋਡੀਊਲ ਪੂਰੇ ਕਰਨ ਲਈ ਵਧਾਈਆਂ! ਤੁਸੀਂ AI Toolkit ਦੇ ਮੂਲ ਸੰਕਲਪਾਂ ਨੂੰ ਸਮਝਣ ਤੋਂ ਲੈ ਕੇ ਪ੍ਰੋਡਕਸ਼ਨ-ਤਿਆਰ MCP ਸਰਵਰ ਬਣਾਉਣ ਤੱਕ ਦਾ ਲੰਮਾ ਸਫਰ ਤੈਅ ਕੀਤਾ ਹੈ ਜੋ ਅਸਲੀ ਦੁਨੀਆ ਦੇ ਵਿਕਾਸ ਚੈਲੰਜਾਂ ਨੂੰ ਹੱਲ ਕਰਦਾ ਹੈ।

### 🚀 ਤੁਹਾਡਾ ਸਿੱਖਣ ਦਾ ਰਸਤਾ:

**[Module 1](../lab1/README.md)**: AI Toolkit ਦੇ ਬੁਨਿਆਦੀ ਪਾਠ, ਮਾਡਲ ਟੈਸਟਿੰਗ ਅਤੇ ਆਪਣਾ ਪਹਿਲਾ AI ਏਜੰਟ ਬਣਾਉਣਾ।

**[Module 2](../lab2/README.md)**: MCP ਆਰਕੀਟੈਕਚਰ ਸਿੱਖਣਾ, Playwright MCP ਨੂੰ ਇੰਟੀਗ੍ਰੇਟ ਕਰਨਾ ਅਤੇ ਪਹਿਲਾ ਬ੍ਰਾਉਜ਼ਰ ਆਟੋਮੇਸ਼ਨ ਏਜੰਟ ਬਣਾਉਣਾ।

**[Module 3](../lab3/README.md)**: Weather MCP ਸਰਵਰ ਨਾਲ ਕਸਟਮ MCP ਸਰਵਰ ਵਿਕਾਸ ਅਤੇ ਡਿਬੱਗਿੰਗ ਟੂਲਜ਼ ਵਿੱਚ ਮਾਹਿਰ ਹੋਣਾ।

**[Module 4](../lab4/README.md)**: ਹੁਣ ਤੁਸੀਂ ਸਭ ਕੁਝ ਵਰਤ ਕੇ ਇੱਕ ਪ੍ਰੈਕਟਿਕਲ GitHub ਰਿਪੋਜ਼ਿਟਰੀ ਵਰਕਫਲੋ ਆਟੋਮੇਸ਼ਨ ਟੂਲ ਬਣਾਇਆ।

### 🌟 ਤੁਹਾਡੇ ਕੁਝ ਮੁੱਖ ਮਾਹਿਰਤਾ ਖੇਤਰ:

- ✅ **AI Toolkit Ecosystem**: ਮਾਡਲ, ਏਜੰਟ ਅਤੇ ਇੰਟੀਗ੍ਰੇਸ਼ਨ ਪੈਟਰਨ  
- ✅ **MCP ਆਰਕੀਟੈਕਚਰ**: ਕਲਾਇੰਟ-ਸਰਵਰ ਡਿਜ਼ਾਈਨ, ਟ੍ਰਾਂਸਪੋਰਟ ਪ੍ਰੋਟੋਕੋਲ ਅਤੇ ਸੁਰੱਖਿਆ  
- ✅ **ਡਿਵੈਲਪਰ ਟੂਲਜ਼**: Playground ਤੋਂ Inspector ਤੱਕ ਅਤੇ ਪ੍ਰੋਡਕਸ਼ਨ ਡਿਪਲੋਇਮੈਂਟ ਤੱਕ  
- ✅ **ਕਸਟਮ ਵਿਕਾਸ**: ਆਪਣੇ MCP ਸਰਵਰਾਂ ਨੂੰ ਬਣਾਉਣਾ, ਟੈਸਟ ਕਰਨਾ ਅਤੇ ਡਿਪਲੋਇ ਕਰਨਾ  
- ✅ **ਵਾਸਤਵਿਕ ਐਪਲੀਕੇਸ਼ਨ**: AI ਨਾਲ ਅਸਲੀ ਦੁਨੀਆ ਦੇ ਵਰਕਫਲੋ ਚੈਲੰਜਾਂ ਦਾ ਹੱਲ

### 🔮 ਤੁਹਾਡੇ ਅਗਲੇ ਕਦਮ:

1. **ਆਪਣਾ MCP ਸਰਵਰ ਬਣਾਓ**: ਆਪਣੀਆਂ ਵਿਲੱਖਣ ਵਰਕਫਲੋਜ਼ ਨੂੰ ਆਟੋਮੇਟ ਕਰਨ ਲਈ ਇਹ ਹੁਨਰ ਲਾਗੂ ਕਰੋ  
2. **MCP ਕਮਿਊਨਿਟੀ ਵਿੱਚ ਸ਼ਾਮਲ ਹੋਵੋ**: ਆਪਣੇ ਬਣਾਏ ਕੰਮ ਸਾਂਝੇ ਕਰੋ ਅਤੇ ਹੋਰਾਂ ਤੋਂ ਸਿੱਖੋ  
3. **ਅਡਵਾਂਸਡ ਇੰਟੀਗ੍ਰੇਸ਼ਨ ਖੋਜੋ**: MCP ਸਰਵਰਾਂ ਨੂੰ ਐਂਟਰਪ੍ਰਾਈਜ਼ ਸਿਸਟਮਾਂ ਨਾਲ ਜੋੜੋ  
4. **ਓਪਨ ਸੋర్స్ ਵਿੱਚ ਯੋਗਦਾਨ ਪਾਓ**: MCP ਟੂਲਿੰਗ ਅਤੇ ਡੌਕੂਮੈਂਟੇਸ਼ਨ ਨੂੰ ਬਿਹਤਰ ਬਣਾਉਣ ਵਿੱਚ ਮਦਦ ਕਰੋ

ਯਾਦ ਰੱਖੋ, ਇਹ ਵਰਕਸ਼ਾਪ ਸਿਰਫ ਸ਼ੁਰੂਆਤ ਹੈ। Model Context Protocol ਦਾ ਪਰਿਵਾਰ ਤੇਜ਼ੀ ਨਾਲ ਵਿਕਸਤ ਹੋ ਰਿਹਾ ਹੈ, ਅਤੇ ਤੁਸੀਂ ਹੁਣ AI-ਚਲਾਏ ਵਿਕਾਸ ਟੂਲਜ਼ ਦੇ ਅੱਗੇ ਰਹਿਣ ਲਈ ਤਿਆਰ ਹੋ।

**ਤੁਹਾਡੇ ਭਾਗੀਦਾਰੀ ਅਤੇ ਸਿੱਖਣ ਦੀ ਲਗਨ ਲਈ ਧੰਨਵਾਦ!**

ਅਸੀਂ ਉਮੀਦ ਕਰਦੇ ਹਾਂ ਕਿ ਇਹ ਵਰਕਸ਼ਾਪ ਤੁਹਾਡੇ ਵਿਚ ਅਜਿਹੀਆਂ ਸੋਚਾਂ ਜਗਾਏਗਾ ਜੋ ਤੁਹਾਡੇ ਵਿਕਾਸ ਯਾਤਰਾ ਵਿੱਚ AI ਟੂਲਜ਼ ਨਾਲ ਇੰਟਰੈਕਸ਼ਨ ਦੇ ਤਰੀਕੇ ਬਦਲ ਦੇਵੇਗਾ।

**ਖੁਸ਼ ਕੋਡਿੰਗ!**

---

**ਡਿਸਕਲੇਮਰ**:  
ਇਹ ਦਸਤਾਵੇਜ਼ AI ਅਨੁਵਾਦ ਸੇਵਾ [Co-op Translator](https://github.com/Azure/co-op-translator) ਦੀ ਵਰਤੋਂ ਨਾਲ ਅਨੁਵਾਦਿਤ ਕੀਤਾ ਗਿਆ ਹੈ। ਜਦੋਂ ਕਿ ਅਸੀਂ ਸਹੀਅਤ ਲਈ ਕੋਸ਼ਿਸ਼ ਕਰਦੇ ਹਾਂ, ਕਿਰਪਾ ਕਰਕੇ ਧਿਆਨ ਰੱਖੋ ਕਿ ਸਵੈਚਾਲਿਤ ਅਨੁਵਾਦਾਂ ਵਿੱਚ ਗਲਤੀਆਂ ਜਾਂ ਅਣਸਹੀਤੀਆਂ ਹੋ ਸਕਦੀਆਂ ਹਨ। ਮੂਲ ਦਸਤਾਵੇਜ਼ ਆਪਣੀ ਮੂਲ ਭਾਸ਼ਾ ਵਿੱਚ ਪ੍ਰਮਾਣਿਕ ਸਰੋਤ ਮੰਨਿਆ ਜਾਣਾ ਚਾਹੀਦਾ ਹੈ। ਮਹੱਤਵਪੂਰਨ ਜਾਣਕਾਰੀ ਲਈ, ਪ੍ਰੋਫੈਸ਼ਨਲ ਮਨੁੱਖੀ ਅਨੁਵਾਦ ਦੀ ਸਿਫਾਰਸ਼ ਕੀਤੀ ਜਾਂਦੀ ਹੈ। ਇਸ ਅਨੁਵਾਦ ਦੀ ਵਰਤੋਂ ਤੋਂ ਹੋਣ ਵਾਲੀਆਂ ਕਿਸੇ ਵੀ ਗਲਤਫਹਿਮੀਆਂ ਜਾਂ ਭ੍ਰਮਾਂ ਲਈ ਅਸੀਂ ਜ਼ਿੰਮੇਵਾਰ ਨਹੀਂ ਹਾਂ।