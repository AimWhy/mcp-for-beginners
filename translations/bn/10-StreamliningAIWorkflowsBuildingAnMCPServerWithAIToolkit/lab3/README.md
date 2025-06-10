<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "dd8da3f75addcef453fe11f02a270217",
  "translation_date": "2025-06-10T06:07:17+00:00",
  "source_file": "10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab3/README.md",
  "language_code": "bn"
}
-->
# 🔧 মডিউল ৩: AI Toolkit দিয়ে উন্নত MCP ডেভেলপমেন্ট

![Duration](https://img.shields.io/badge/Duration-20_minutes-blue?style=flat-square)
![AI Toolkit](https://img.shields.io/badge/AI_Toolkit-Required-orange?style=flat-square)
![Python](https://img.shields.io/badge/Python-3.10+-green?style=flat-square)
![MCP SDK](https://img.shields.io/badge/MCP_SDK-1.9.3-purple?style=flat-square)
![Inspector](https://img.shields.io/badge/MCP_Inspector-0.14.0-blue?style=flat-square)

## 🎯 শেখার লক্ষ্যসমূহ

এই ল্যাবের শেষে, আপনি সক্ষম হবেন:

- ✅ AI Toolkit ব্যবহার করে কাস্টম MCP সার্ভার তৈরি করতে
- ✅ সর্বশেষ MCP Python SDK (v1.9.3) কনফিগার ও ব্যবহার করতে
- ✅ MCP Inspector সেটআপ ও ডিবাগিংয়ে ব্যবহার করতে
- ✅ Agent Builder ও Inspector উভয় পরিবেশে MCP সার্ভার ডিবাগ করতে
- ✅ উন্নত MCP সার্ভার ডেভেলপমেন্ট ওয়ার্কফ্লো বুঝতে

## 📋 পূর্বপ্রয়োজনীয়তা

- ল্যাব ২ (MCP Fundamentals) সম্পন্ন করা
- VS Code এ AI Toolkit এক্সটেনশন ইনস্টল করা
- Python 3.10+ পরিবেশ
- Inspector সেটআপের জন্য Node.js ও npm

## 🏗️ আপনি যা তৈরি করবেন

এই ল্যাবে, আপনি একটি **Weather MCP Server** তৈরি করবেন যা প্রদর্শন করবে:
- কাস্টম MCP সার্ভার ইমপ্লিমেন্টেশন
- AI Toolkit Agent Builder এর সাথে ইন্টিগ্রেশন
- পেশাদার ডিবাগিং ওয়ার্কফ্লো
- আধুনিক MCP SDK ব্যবহারের প্যাটার্ন

---

## 🔧 মূল উপাদানসমূহের পরিচিতি

### 🐍 MCP Python SDK
Model Context Protocol Python SDK হল কাস্টম MCP সার্ভার তৈরির ভিত্তি। আপনি সংস্করণ 1.9.3 ব্যবহার করবেন যা উন্নত ডিবাগিং সুবিধা দেয়।

### 🔍 MCP Inspector
একটি শক্তিশালী ডিবাগিং টুল যা দেয়:
- রিয়েল-টাইম সার্ভার মনিটরিং
- টুল এক্সিকিউশনের ভিজ্যুয়ালাইজেশন
- নেটওয়ার্ক রিকোয়েস্ট/রেসপন্স পরিদর্শন
- ইন্টারেক্টিভ টেস্টিং পরিবেশ

---

## 📖 ধাপে ধাপে ইমপ্লিমেন্টেশন

### ধাপ ১: Agent Builder এ WeatherAgent তৈরি করুন

1. **Agent Builder চালু করুন** VS Code এর AI Toolkit এক্সটেনশন থেকে
2. **নতুন একটি এজেন্ট তৈরি করুন** নিম্নলিখিত কনফিগারেশন দিয়ে:
   - Agent Name: `WeatherAgent`

![Agent Creation](../../../../translated_images/Agent.c9c33f6a412b4cdedfb973fe5448bdb33de3f400055603111b875610e9b917ab.bn.png)

### ধাপ ২: MCP Server প্রজেক্ট ইনিশিয়ালাইজ করুন

1. **Agent Builder এ যান** → **Tools** → **Add Tool**
2. **"MCP Server" নির্বাচন করুন** উপলব্ধ অপশন থেকে
3. **"Create A new MCP Server" নির্বাচন করুন**
4. **`python-weather` টেমপ্লেট নির্বাচন করুন**
5. **আপনার সার্ভারের নাম দিন:** `weather_mcp`

![Python Template Selection](../../../../translated_images/Pythontemplate.9d0a2913c6491500bd673430f024dc44676af2808a27b5da9dcc0eb7063adc28.bn.png)

### ধাপ ৩: প্রজেক্ট খুলে পর্যালোচনা করুন

1. **জেনারেট করা প্রজেক্টটি VS Code এ খুলুন**
2. **প্রজেক্ট স্ট্রাকচার পর্যালোচনা করুন:**
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

### ধাপ ৪: সর্বশেষ MCP SDK এ আপগ্রেড করুন

> **🔍 কেন আপগ্রেড করবেন?** আমরা সর্বশেষ MCP SDK (v1.9.3) এবং Inspector সার্ভিস (0.14.0) ব্যবহার করতে চাই উন্নত ফিচার ও উন্নত ডিবাগিংয়ের জন্য।

#### ৪a. Python ডিপেন্ডেন্সি আপডেট করুন

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

**Edit `.vscode/launch.json` ফাইলগুলো সম্পাদনা করুন:**

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

**`.vscode/tasks.json` সম্পাদনা করুন:**

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

## 🚀 আপনার MCP সার্ভার রান ও টেস্ট করা

### ধাপ ৬: ডিপেন্ডেন্সি ইনস্টল করুন

কনফিগারেশন পরিবর্তনের পর, নিম্নলিখিত কমান্ডগুলো চালান:

**Python ডিপেন্ডেন্সি ইনস্টল করুন:**
```bash
uv sync
```

**Inspector ডিপেন্ডেন্সি ইনস্টল করুন:**
```bash
cd inspector
npm install
```

### ধাপ ৭: Agent Builder দিয়ে ডিবাগ করুন

1. **F5 চাপুন** অথবা **"Debug in Agent Builder"** কনফিগারেশন ব্যবহার করুন
2. **ডিবাগ প্যানেল থেকে কম্পাউন্ড কনফিগারেশন নির্বাচন করুন**
3. **সার্ভার শুরু হওয়া এবং Agent Builder খোলার জন্য অপেক্ষা করুন**
4. **আপনার weather MCP সার্ভার ন্যাচারাল ল্যাঙ্গুয়েজ কোয়েরি দিয়ে পরীক্ষা করুন**

এমন ইনপুট দিন

SYSTEM_PROMPT

```
You are my weather assistant
```

USER_PROMPT

```
How's the weather like in Seattle
```

![Agent Builder Debug Result](../../../../translated_images/Result.6ac570f7d2b1d5389c561ab0566970fe0f13e75bdd976b6a7f0270bc715d07f8.bn.png)

### ধাপ ৮: MCP Inspector দিয়ে ডিবাগ করুন

1. **"Debug in Inspector"** কনফিগারেশন ব্যবহার করুন (Edge বা Chrome)
2. **Inspector ইন্টারফেস খুলুন** `http://localhost:6274` এ
3. **ইন্টারেক্টিভ টেস্টিং পরিবেশ অন্বেষণ করুন:**
   - উপলব্ধ টুলগুলো দেখুন
   - টুল এক্সিকিউশন টেস্ট করুন
   - নেটওয়ার্ক রিকোয়েস্ট মনিটর করুন
   - সার্ভার রেসপন্স ডিবাগ করুন

![MCP Inspector Interface](../../../../translated_images/Inspector.5672415cd02fe8731774586cc0a1083e3275d2f8491602aecc8ac4d61f2c0d57.bn.png)

---

## 🎯 প্রধান শেখার ফলাফল

এই ল্যাব শেষ করার মাধ্যমে, আপনি:

- [x] **AI Toolkit টেমপ্লেট ব্যবহার করে কাস্টম MCP সার্ভার তৈরি করেছেন**
- [x] **সর্বশেষ MCP SDK (v1.9.3) এ আপগ্রেড করেছেন উন্নত ফিচারের জন্য**
- [x] **Agent Builder ও Inspector উভয়ের জন্য পেশাদার ডিবাগিং ওয়ার্কফ্লো কনফিগার করেছেন**
- [x] **ইন্টারেক্টিভ সার্ভার টেস্টিংয়ের জন্য MCP Inspector সেটআপ করেছেন**
- [x] **MCP ডেভেলপমেন্টের জন্য VS Code ডিবাগিং কনফিগারেশন আয়ত্ত করেছেন**

## 🔧 উন্নত ফিচারসমূহ অন্বেষণ

| ফিচার | বর্ণনা | ব্যবহারের ক্ষেত্র |
|---------|-------------|----------|
| **MCP Python SDK v1.9.3** | সর্বশেষ প্রোটোকল ইমপ্লিমেন্টেশন | আধুনিক সার্ভার ডেভেলপমেন্ট |
| **MCP Inspector 0.14.0** | ইন্টারেক্টিভ ডিবাগিং টুল | রিয়েল-টাইম সার্ভার টেস্টিং |
| **VS Code Debugging** | ইন্টিগ্রেটেড ডেভেলপমেন্ট এনভায়রনমেন্ট | পেশাদার ডিবাগিং ওয়ার্কফ্লো |
| **Agent Builder Integration** | সরাসরি AI Toolkit সংযোগ | এন্ড-টু-এন্ড এজেন্ট টেস্টিং |

## 📚 অতিরিক্ত রিসোর্স

- [MCP Python SDK ডকুমেন্টেশন](https://modelcontextprotocol.io/docs/sdk/python)
- [AI Toolkit এক্সটেনশন গাইড](https://code.visualstudio.com/docs/ai/ai-toolkit)
- [VS Code ডিবাগিং ডকুমেন্টেশন](https://code.visualstudio.com/docs/editor/debugging)
- [Model Context Protocol স্পেসিফিকেশন](https://modelcontextprotocol.io/docs/concepts/architecture)

---

**🎉 অভিনন্দন!** আপনি সফলভাবে ল্যাব ৩ সম্পন্ন করেছেন এবং এখন পেশাদার ডেভেলপমেন্ট ওয়ার্কফ্লো ব্যবহার করে কাস্টম MCP সার্ভার তৈরি, ডিবাগ ও ডিপ্লয় করতে পারবেন।

### 🔜 পরবর্তী মডিউলে যান

আপনার MCP দক্ষতাগুলো বাস্তব ডেভেলপমেন্ট ওয়ার্কফ্লোতে প্রয়োগ করতে প্রস্তুত? এগিয়ে যান **[মডিউল ৪: Practical MCP Development - Custom GitHub Clone Server](../lab4/README.md)** যেখানে আপনি:
- প্রোডাকশন-রেডি MCP সার্ভার তৈরি করবেন যা GitHub রেপোজিটরি অপারেশনগুলো স্বয়ংক্রিয় করবে
- MCP এর মাধ্যমে GitHub রেপোজিটরি ক্লোনিং ফিচার ইমপ্লিমেন্ট করবেন
- VS Code ও GitHub Copilot Agent Mode এর সাথে কাস্টম MCP সার্ভার ইন্টিগ্রেট করবেন
- প্রোডাকশন পরিবেশে কাস্টম MCP সার্ভার টেস্ট ও ডিপ্লয় করবেন
- ডেভেলপারদের জন্য ব্যবহারিক ওয়ার্কফ্লো অটোমেশন শিখবেন

**দ্রষ্টব্য**:  
এই নথিটি AI অনুবাদ সেবা [Co-op Translator](https://github.com/Azure/co-op-translator) ব্যবহার করে অনূদিত হয়েছে। আমরা যথাসাধ্য সঠিকতার চেষ্টা করি, তবে স্বয়ংক্রিয় অনুবাদে ত্রুটি বা ভুল থাকতে পারে। মূল নথি তার নিজ ভাষায়ই প্রামাণিক উৎস হিসেবে বিবেচনা করা উচিত। গুরুত্বপূর্ণ তথ্যের জন্য পেশাদার মানুষের দ্বারা অনুবাদ করানোই শ্রেয়। এই অনুবাদের ব্যবহার থেকে সৃষ্ট কোনো ভুল বোঝাবুঝি বা ভুল ব্যাখ্যার জন্য আমরা দায়ী নই।