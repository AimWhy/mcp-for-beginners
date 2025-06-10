<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "dd8da3f75addcef453fe11f02a270217",
  "translation_date": "2025-06-10T06:08:17+00:00",
  "source_file": "10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab3/README.md",
  "language_code": "ne"
}
-->
# 🔧 Module 3: AI Toolkit सँग उन्नत MCP विकास

![Duration](https://img.shields.io/badge/Duration-20_minutes-blue?style=flat-square)
![AI Toolkit](https://img.shields.io/badge/AI_Toolkit-Required-orange?style=flat-square)
![Python](https://img.shields.io/badge/Python-3.10+-green?style=flat-square)
![MCP SDK](https://img.shields.io/badge/MCP_SDK-1.9.3-purple?style=flat-square)
![Inspector](https://img.shields.io/badge/MCP_Inspector-0.14.0-blue?style=flat-square)

## 🎯 सिकाइका उद्देश्यहरू

यो प्रयोगशालाको अन्त्यसम्म, तपाईं सक्षम हुनुहुनेछ:

- ✅ AI Toolkit प्रयोग गरेर कस्टम MCP सर्भरहरू सिर्जना गर्न
- ✅ नवीनतम MCP Python SDK (v1.9.3) कन्फिगर र प्रयोग गर्न
- ✅ डिबगिङका लागि MCP Inspector सेटअप र उपयोग गर्न
- ✅ Agent Builder र Inspector दुवै वातावरणमा MCP सर्भरहरू डिबग गर्न
- ✅ उन्नत MCP सर्भर विकास कार्यप्रवाहहरू बुझ्न

## 📋 पूर्वआवश्यकताहरू

- Lab 2 (MCP Fundamentals) पूरा भएको हुनुपर्छ
- AI Toolkit एक्सटेन्सन सहित VS Code स्थापना गरिएको हुनुपर्छ
- Python 3.10+ वातावरण
- Inspector सेटअपका लागि Node.js र npm

## 🏗️ तपाईंले के बनाउनुहुनेछ

यस प्रयोगशालामा, तपाईंले **Weather MCP Server** बनाउनुहुनेछ जसले देखाउँछ:
- कस्टम MCP सर्भर कार्यान्वयन
- AI Toolkit Agent Builder सँग एकीकरण
- व्यावसायिक डिबगिङ कार्यप्रवाहहरू
- आधुनिक MCP SDK प्रयोगका तरिका

---

## 🔧 मुख्य कम्पोनेन्टहरूको अवलोकन

### 🐍 MCP Python SDK
Model Context Protocol Python SDK कस्टम MCP सर्भर बनाउनको लागि आधार हो। तपाईंले संस्करण 1.9.3 प्रयोग गर्नुहुनेछ जसमा सुधारिएको डिबगिङ सुविधा छ।

### 🔍 MCP Inspector
एक शक्तिशाली डिबगिङ उपकरण जसले प्रदान गर्दछ:
- रियल-टाइम सर्भर अनुगमन
- टुल कार्यान्वयन दृश्यता
- नेटवर्क अनुरोध/प्रतिक्रिया निरीक्षण
- अन्तरक्रियात्मक परीक्षण वातावरण

---

## 📖 चरण-दर-चरण कार्यान्वयन

### चरण 1: Agent Builder मा WeatherAgent सिर्जना गर्नुहोस्

1. **VS Code मा AI Toolkit एक्सटेन्सनबाट Agent Builder सुरु गर्नुहोस्**
2. **नयाँ एजेन्ट सिर्जना गर्नुहोस्** निम्न कन्फिगरेसनसहित:
   - Agent Name: `WeatherAgent`

![Agent Creation](../../../../translated_images/Agent.c9c33f6a412b4cdedfb973fe5448bdb33de3f400055603111b875610e9b917ab.ne.png)

### चरण 2: MCP Server परियोजना सुरु गर्नुहोस्

1. Agent Builder मा **Tools** → **Add Tool** मा जानुहोस्
2. उपलब्ध विकल्पहरूबाट **"MCP Server"** चयन गर्नुहोस्
3. **"Create A new MCP Server"** रोज्नुहोस्
4. `python-weather` टेम्प्लेट चयन गर्नुहोस्
5. आफ्नो सर्भरको नाम राख्नुहोस्: `weather_mcp`

![Python Template Selection](../../../../translated_images/Pythontemplate.9d0a2913c6491500bd673430f024dc44676af2808a27b5da9dcc0eb7063adc28.ne.png)

### चरण 3: परियोजना खोल्नुहोस् र समीक्षा गर्नुहोस्

1. VS Code मा सिर्जना गरिएको परियोजना खोल्नुहोस्
2. परियोजना संरचना समीक्षा गर्नुहोस्:
   ```
   weather_mcp/
   ├── src/
   │   ├── __init__.py
   │   └── server.py
   ├── inspector/
   │   ├── package.json
   │   └── package-lock.json
   ├── .vscode/
   │   ├── launch.json
   │   └── tasks.json
   ├── pyproject.toml
   └── README.md
   ```

### चरण 4: नवीनतम MCP SDK मा अपग्रेड गर्नुहोस्

> **🔍 किन अपग्रेड गर्ने?** हामी नवीनतम MCP SDK (v1.9.3) र Inspector सेवा (0.14.0) प्रयोग गर्न चाहन्छौं जसले थप सुविधा र राम्रो डिबगिङ क्षमता दिन्छ।

#### 4a. Python निर्भरता अपडेट गर्नुहोस्

**`pyproject.toml`:** update [./code/weather_mcp/pyproject.toml](../../../../10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab3/code/weather_mcp/pyproject.toml)


#### 4b. Update Inspector Configuration

**Edit `inspector/package.json`:** update [./code/weather_mcp/inspector/package.json](../../../../10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab3/code/weather_mcp/inspector/package.json)

#### 4c. Update Inspector Dependencies

**Edit `inspector/package-lock.json`:** update [./code/weather_mcp/inspector/package-lock.json](../../../../10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab3/code/weather_mcp/inspector/package-lock.json)

> **📝 Note:** This file contains extensive dependency definitions. Below is the essential structure - the full content ensures proper dependency resolution.


> **⚡ Full Package Lock:** The complete package-lock.json contains ~3000 lines of dependency definitions. The above shows the key structure - use the provided file for complete dependency resolution.

### Step 5: Configure VS Code Debugging

*Note: Please copy the file in the specified path to replace the corresponding local file*

#### 5a. Update Launch Configuration

**Edit `.vscode/launch.json` सम्पादन गर्नुहोस्:**

```json
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Attach to Local MCP",
      "type": "debugpy",
      "request": "attach",
      "connect": {
        "host": "localhost",
        "port": 5678
      },
      "presentation": {
        "hidden": true
      },
      "internalConsoleOptions": "neverOpen",
      "postDebugTask": "Terminate All Tasks"
    },
    {
      "name": "Launch Inspector (Edge)",
      "type": "msedge",
      "request": "launch",
      "url": "http://localhost:6274?timeout=60000&serverUrl=http://localhost:3001/sse#tools",
      "cascadeTerminateToConfigurations": [
        "Attach to Local MCP"
      ],
      "presentation": {
        "hidden": true
      },
      "internalConsoleOptions": "neverOpen"
    },
    {
      "name": "Launch Inspector (Chrome)",
      "type": "chrome",
      "request": "launch",
      "url": "http://localhost:6274?timeout=60000&serverUrl=http://localhost:3001/sse#tools",
      "cascadeTerminateToConfigurations": [
        "Attach to Local MCP"
      ],
      "presentation": {
        "hidden": true
      },
      "internalConsoleOptions": "neverOpen"
    }
  ],
  "compounds": [
    {
      "name": "Debug in Agent Builder",
      "configurations": [
        "Attach to Local MCP"
      ],
      "preLaunchTask": "Open Agent Builder",
    },
    {
      "name": "Debug in Inspector (Edge)",
      "configurations": [
        "Launch Inspector (Edge)",
        "Attach to Local MCP"
      ],
      "preLaunchTask": "Start MCP Inspector",
      "stopAll": true
    },
    {
      "name": "Debug in Inspector (Chrome)",
      "configurations": [
        "Launch Inspector (Chrome)",
        "Attach to Local MCP"
      ],
      "preLaunchTask": "Start MCP Inspector",
      "stopAll": true
    }
  ]
}
```

**`.vscode/tasks.json` सम्पादन गर्नुहोस्:**

```
{
  "version": "2.0.0",
  "tasks": [
    {
      "label": "Start MCP Server",
      "type": "shell",
      "command": "python -m debugpy --listen 127.0.0.1:5678 src/__init__.py sse",
      "isBackground": true,
      "options": {
        "cwd": "${workspaceFolder}",
        "env": {
          "PORT": "3001"
        }
      },
      "problemMatcher": {
        "pattern": [
          {
            "regexp": "^.*$",
            "file": 0,
            "location": 1,
            "message": 2
          }
        ],
        "background": {
          "activeOnStart": true,
          "beginsPattern": ".*",
          "endsPattern": "Application startup complete|running"
        }
      }
    },
    {
      "label": "Start MCP Inspector",
      "type": "shell",
      "command": "npm run dev:inspector",
      "isBackground": true,
      "options": {
        "cwd": "${workspaceFolder}/inspector",
        "env": {
          "CLIENT_PORT": "6274",
          "SERVER_PORT": "6277",
        }
      },
      "problemMatcher": {
        "pattern": [
          {
            "regexp": "^.*$",
            "file": 0,
            "location": 1,
            "message": 2
          }
        ],
        "background": {
          "activeOnStart": true,
          "beginsPattern": "Starting MCP inspector",
          "endsPattern": "Proxy server listening on port"
        }
      },
      "dependsOn": [
        "Start MCP Server"
      ]
    },
    {
      "label": "Open Agent Builder",
      "type": "shell",
      "command": "echo ${input:openAgentBuilder}",
      "presentation": {
        "reveal": "never"
      },
      "dependsOn": [
        "Start MCP Server"
      ],
    },
    {
      "label": "Terminate All Tasks",
      "command": "echo ${input:terminate}",
      "type": "shell",
      "problemMatcher": []
    }
  ],
  "inputs": [
    {
      "id": "openAgentBuilder",
      "type": "command",
      "command": "ai-mlstudio.agentBuilder",
      "args": {
        "initialMCPs": [ "local-server-weather_mcp" ],
        "triggeredFrom": "vsc-tasks"
      }
    },
    {
      "id": "terminate",
      "type": "command",
      "command": "workbench.action.tasks.terminate",
      "args": "terminateAll"
    }
  ]
}
```


---

## 🚀 आफ्नो MCP सर्भर चलाउनुहोस् र परीक्षण गर्नुहोस्

### चरण 6: निर्भरता स्थापना गर्नुहोस्

कन्फिगरेसन परिवर्तन गरेपछि तलका आदेशहरू चलाउनुहोस्:

**Python निर्भरता स्थापना गर्नुहोस्:**
```bash
uv sync
```

**Inspector निर्भरता स्थापना गर्नुहोस्:**
```bash
cd inspector
npm install
```

### चरण 7: Agent Builder मा डिबग गर्नुहोस्

1. **F5 थिच्नुहोस्** वा **"Debug in Agent Builder"** कन्फिगरेसन प्रयोग गर्नुहोस्
2. डिबग प्यानलबाट संयुक्त कन्फिगरेसन चयन गर्नुहोस्
3. सर्भर सुरु हुन र Agent Builder खुल्न पर्खनुहोस्
4. आफ्नो weather MCP सर्भर प्राकृतिक भाषा क्वेरीहरूसँग परीक्षण गर्नुहोस्

यसरी इनपुट दिनुहोस्

SYSTEM_PROMPT

```
You are my weather assistant
```

USER_PROMPT

```
How's the weather like in Seattle
```

![Agent Builder Debug Result](../../../../translated_images/Result.6ac570f7d2b1d5389c561ab0566970fe0f13e75bdd976b6a7f0270bc715d07f8.ne.png)

### चरण 8: MCP Inspector मा डिबग गर्नुहोस्

1. **"Debug in Inspector"** कन्फिगरेसन प्रयोग गर्नुहोस् (Edge वा Chrome)
2. `http://localhost:6274` मा Inspector इन्टरफेस खोल्नुहोस्
3. अन्तरक्रियात्मक परीक्षण वातावरण अन्वेषण गर्नुहोस्:
   - उपलब्ध उपकरणहरू हेर्नुहोस्
   - टुल कार्यान्वयन परीक्षण गर्नुहोस्
   - नेटवर्क अनुरोधहरू अनुगमन गर्नुहोस्
   - सर्भर प्रतिक्रियाहरू डिबग गर्नुहोस्

![MCP Inspector Interface](../../../../translated_images/Inspector.5672415cd02fe8731774586cc0a1083e3275d2f8491602aecc8ac4d61f2c0d57.ne.png)

---

## 🎯 मुख्य सिकाइ परिणामहरू

यस प्रयोगशाला पूरा गरेर, तपाईंले:

- [x] AI Toolkit टेम्प्लेटहरू प्रयोग गरेर कस्टम MCP सर्भर सिर्जना गर्नुभएको छ
- [x] थप कार्यक्षमताका लागि नवीनतम MCP SDK (v1.9.3) मा अपग्रेड गर्नुभएको छ
- [x] Agent Builder र Inspector दुवैका लागि व्यावसायिक डिबगिङ कार्यप्रवाहहरू कन्फिगर गर्नुभएको छ
- [x] अन्तरक्रियात्मक सर्भर परीक्षणका लागि MCP Inspector सेटअप गर्नुभएको छ
- [x] MCP विकासका लागि VS Code डिबगिङ कन्फिगरेसनहरूमा दक्षता हासिल गर्नुभएको छ

## 🔧 अन्वेषण गरिएका उन्नत सुविधाहरू

| सुविधा | विवरण | प्रयोग केस |
|---------|-------------|----------|
| **MCP Python SDK v1.9.3** | नवीनतम प्रोटोकल कार्यान्वयन | आधुनिक सर्भर विकास |
| **MCP Inspector 0.14.0** | अन्तरक्रियात्मक डिबगिङ उपकरण | रियल-टाइम सर्भर परीक्षण |
| **VS Code Debugging** | एकीकृत विकास वातावरण | व्यावसायिक डिबगिङ कार्यप्रवाह |
| **Agent Builder Integration** | प्रत्यक्ष AI Toolkit कनेक्शन | अन्तदेखि अन्त एजेन्ट परीक्षण |

## 📚 अतिरिक्त स्रोतहरू

- [MCP Python SDK Documentation](https://modelcontextprotocol.io/docs/sdk/python)
- [AI Toolkit Extension Guide](https://code.visualstudio.com/docs/ai/ai-toolkit)
- [VS Code Debugging Documentation](https://code.visualstudio.com/docs/editor/debugging)
- [Model Context Protocol Specification](https://modelcontextprotocol.io/docs/concepts/architecture)

---

**🎉 बधाई छ!** तपाईंले सफलतापूर्वक Lab 3 पूरा गर्नुभयो र अब व्यावसायिक विकास कार्यप्रवाहहरू प्रयोग गरी कस्टम MCP सर्भरहरू सिर्जना, डिबग र डिप्लोय गर्न सक्नुहुन्छ।

### 🔜 अर्को मोड्युलमा अगाडि बढ्नुहोस्

वास्तविक विकास कार्यप्रवाहमा तपाईंको MCP कौशल प्रयोग गर्न तयार हुनुहुन्छ? **[Module 4: Practical MCP Development - Custom GitHub Clone Server](../lab4/README.md)** मा अगाडि बढ्नुहोस् जहाँ तपाईंले:
- GitHub रिपोजिटरी अपरेसनहरू स्वचालित गर्ने उत्पादन-तय MCP सर्भर बनाउनुहुनेछ
- MCP मार्फत GitHub रिपोजिटरी क्लोनिङ कार्यान्वयन गर्नुहुनेछ
- VS Code र GitHub Copilot Agent Mode सँग कस्टम MCP सर्भरहरू एकीकृत गर्नुहुनेछ
- उत्पादन वातावरणमा कस्टम MCP सर्भरहरू परीक्षण र डिप्लोय गर्नुहुनेछ
- विकासकर्ताहरूका लागि व्यावहारिक कार्यप्रवाह स्वचालन सिक्नुहुनेछ

**अस्वीकरण**:  
यो दस्तावेज़ AI अनुवाद सेवा [Co-op Translator](https://github.com/Azure/co-op-translator) प्रयोग गरेर अनुवाद गरिएको हो। हामी सटीकताको प्रयास गर्छौं, तर कृपया ध्यान दिनुहोस् कि स्वचालित अनुवादहरूमा त्रुटिहरू वा असंगतिहरू हुन सक्छन्। मूल दस्तावेज़लाई यसको मूल भाषामा आधिकारिक स्रोतको रूपमा मान्नुपर्छ। महत्वपूर्ण जानकारीको लागि व्यावसायिक मानव अनुवाद सिफारिस गरिन्छ। यस अनुवादको प्रयोगबाट उत्पन्न कुनै पनि गलतफहमी वा गलत व्याख्याका लागि हामी जिम्मेवार छैनौं।