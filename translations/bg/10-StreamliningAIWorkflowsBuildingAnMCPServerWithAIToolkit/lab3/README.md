<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "dd8da3f75addcef453fe11f02a270217",
  "translation_date": "2025-06-10T06:19:32+00:00",
  "source_file": "10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab3/README.md",
  "language_code": "bg"
}
-->
# 🔧 Модул 3: Разширена разработка на MCP с AI Toolkit

![Duration](https://img.shields.io/badge/Duration-20_minutes-blue?style=flat-square)
![AI Toolkit](https://img.shields.io/badge/AI_Toolkit-Required-orange?style=flat-square)
![Python](https://img.shields.io/badge/Python-3.10+-green?style=flat-square)
![MCP SDK](https://img.shields.io/badge/MCP_SDK-1.9.3-purple?style=flat-square)
![Inspector](https://img.shields.io/badge/MCP_Inspector-0.14.0-blue?style=flat-square)

## 🎯 Учебни цели

Към края на тази лаборатория ще можете да:

- ✅ Създавате персонализирани MCP сървъри с помощта на AI Toolkit
- ✅ Конфигурирате и използвате най-новото MCP Python SDK (v1.9.3)
- ✅ Настроите и използвате MCP Inspector за отстраняване на грешки
- ✅ Отстранявате грешки в MCP сървъри както в Agent Builder, така и в Inspector
- ✅ Разбирате напреднали работни процеси за разработка на MCP сървъри

## 📋 Предварителни изисквания

- Завършване на Лаборатория 2 (Основи на MCP)
- VS Code с инсталирано AI Toolkit разширение
- Python 3.10+ среда
- Node.js и npm за настройка на Inspector

## 🏗️ Какво ще изградите

В тази лаборатория ще създадете **Weather MCP Server**, който демонстрира:
- Персонализирана имплементация на MCP сървър
- Интеграция с AI Toolkit Agent Builder
- Професионални работни процеси за отстраняване на грешки
- Модерни модели на използване на MCP SDK

---

## 🔧 Преглед на основните компоненти

### 🐍 MCP Python SDK
Model Context Protocol Python SDK предоставя основата за изграждане на персонализирани MCP сървъри. Ще използвате версия 1.9.3 с подобрени възможности за отстраняване на грешки.

### 🔍 MCP Inspector
Мощен инструмент за отстраняване на грешки, който предлага:
- Наблюдение на сървъра в реално време
- Визуализация на изпълнението на инструменти
- Инспекция на мрежови заявки и отговори
- Интерактивна тестова среда

---

## 📖 Стъпка по стъпка изпълнение

### Стъпка 1: Създайте WeatherAgent в Agent Builder

1. **Стартирайте Agent Builder** във VS Code чрез AI Toolkit разширението
2. **Създайте нов агент** с следната конфигурация:
   - Име на агента: `WeatherAgent`

![Agent Creation](../../../../translated_images/Agent.c9c33f6a412b4cdedfb973fe5448bdb33de3f400055603111b875610e9b917ab.bg.png)

### Стъпка 2: Инициализирайте MCP Server проект

1. **Отидете на Tools** → **Add Tool** в Agent Builder
2. **Изберете "MCP Server"** от наличните опции
3. **Изберете "Create A new MCP Server"**
4. **Изберете шаблона `python-weather`**
5. **Наименувайте сървъра си:** `weather_mcp`

![Python Template Selection](../../../../translated_images/Pythontemplate.9d0a2913c6491500bd673430f024dc44676af2808a27b5da9dcc0eb7063adc28.bg.png)

### Стъпка 3: Отворете и разгледайте проекта

1. **Отворете генерирания проект** във VS Code
2. **Прегледайте структурата на проекта:**
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

### Стъпка 4: Ъпгрейд към най-новото MCP SDK

> **🔍 Защо ъпгрейд?** Искаме да използваме най-новото MCP SDK (v1.9.3) и Inspector версия (0.14.0) за разширени функции и по-добро отстраняване на грешки.

#### 4a. Актуализиране на Python зависимости

**Редактирайте `pyproject.toml`:** update [./code/weather_mcp/pyproject.toml](../../../../10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab3/code/weather_mcp/pyproject.toml)


#### 4b. Update Inspector Configuration

**Edit `inspector/package.json`:** update [./code/weather_mcp/inspector/package.json](../../../../10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab3/code/weather_mcp/inspector/package.json)

#### 4c. Update Inspector Dependencies

**Edit `inspector/package-lock.json`:** update [./code/weather_mcp/inspector/package-lock.json](../../../../10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab3/code/weather_mcp/inspector/package-lock.json)

> **📝 Note:** This file contains extensive dependency definitions. Below is the essential structure - the full content ensures proper dependency resolution.


> **⚡ Full Package Lock:** The complete package-lock.json contains ~3000 lines of dependency definitions. The above shows the key structure - use the provided file for complete dependency resolution.

### Step 5: Configure VS Code Debugging

*Note: Please copy the file in the specified path to replace the corresponding local file*

#### 5a. Update Launch Configuration

**Edit `.vscode/launch.json`:**

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

**Редактирайте `.vscode/tasks.json`:**

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

## 🚀 Стартиране и тестване на вашия MCP сървър

### Стъпка 6: Инсталиране на зависимости

След като направите конфигурационните промени, изпълнете следните команди:

**Инсталирайте Python зависимости:**
```bash
uv sync
```

**Инсталирайте зависимости за Inspector:**
```bash
cd inspector
npm install
```

### Стъпка 7: Отстраняване на грешки с Agent Builder

1. **Натиснете F5** или използвайте конфигурацията **"Debug in Agent Builder"**
2. **Изберете комбинираната конфигурация** от панела за отстраняване на грешки
3. **Изчакайте сървърът да стартира** и Agent Builder да се отвори
4. **Тествайте вашия weather MCP сървър** с естествени езикови заявки

Въведете заявка като тази

SYSTEM_PROMPT

```
You are my weather assistant
```

USER_PROMPT

```
How's the weather like in Seattle
```

![Agent Builder Debug Result](../../../../translated_images/Result.6ac570f7d2b1d5389c561ab0566970fe0f13e75bdd976b6a7f0270bc715d07f8.bg.png)

### Стъпка 8: Отстраняване на грешки с MCP Inspector

1. **Използвайте конфигурацията "Debug in Inspector"** (Edge или Chrome)
2. **Отворете интерфейса на Inspector** на адрес `http://localhost:6274`
3. **Разгледайте интерактивната тестова среда:**
   - Преглед на наличните инструменти
   - Тестване на изпълнението на инструменти
   - Мониторинг на мрежови заявки
   - Отстраняване на грешки в отговорите на сървъра

![MCP Inspector Interface](../../../../translated_images/Inspector.5672415cd02fe8731774586cc0a1083e3275d2f8491602aecc8ac4d61f2c0d57.bg.png)

---

## 🎯 Основни резултати от обучението

След като завършихте тази лаборатория, вие:

- [x] **Създадохте персонализиран MCP сървър** с помощта на AI Toolkit шаблони
- [x] **Ъпгрейднахте до най-новото MCP SDK** (v1.9.3) за разширена функционалност
- [x] **Конфигурирахте професионални работни процеси за отстраняване на грешки** както в Agent Builder, така и в Inspector
- [x] **Настроихте MCP Inspector** за интерактивно тестване на сървъра
- [x] **Овладяхте VS Code конфигурациите за отстраняване на грешки** при разработка на MCP

## 🔧 Изследвани разширени функции

| Функция | Описание | Приложение |
|---------|-------------|----------|
| **MCP Python SDK v1.9.3** | Най-нова имплементация на протокола | Модерна разработка на сървъри |
| **MCP Inspector 0.14.0** | Интерактивен инструмент за отстраняване на грешки | Тестване на сървъра в реално време |
| **VS Code Debugging** | Интегрирана среда за разработка | Професионален работен процес за отстраняване на грешки |
| **Agent Builder Integration** | Директна връзка с AI Toolkit | Пълноценен краен тест на агенти |

## 📚 Допълнителни ресурси

- [MCP Python SDK Documentation](https://modelcontextprotocol.io/docs/sdk/python)
- [AI Toolkit Extension Guide](https://code.visualstudio.com/docs/ai/ai-toolkit)
- [VS Code Debugging Documentation](https://code.visualstudio.com/docs/editor/debugging)
- [Model Context Protocol Specification](https://modelcontextprotocol.io/docs/concepts/architecture)

---

**🎉 Поздравления!** Успешно завършихте Лаборатория 3 и вече можете да създавате, отстранявате грешки и внедрявате персонализирани MCP сървъри с професионални работни процеси.

### 🔜 Продължете към следващия модул

Готови ли сте да приложите MCP уменията си в реален работен процес? Продължете към **[Модул 4: Практическа разработка на MCP - Персонализиран GitHub Clone сървър](../lab4/README.md)**, където ще:
- Изградите готов за продукция MCP сървър, който автоматизира операции с GitHub репозитории
- Имплементирате функционалност за клониране на GitHub репозитории чрез MCP
- Интегрирате персонализирани MCP сървъри с VS Code и GitHub Copilot Agent Mode
- Тествате и внедрявате персонализирани MCP сървъри в продукционна среда
- Научите практически автоматизирани работни процеси за разработчици

**Отказ от отговорност**:  
Този документ е преведен с помощта на AI преводаческа услуга [Co-op Translator](https://github.com/Azure/co-op-translator). Въпреки че се стремим към точност, моля, имайте предвид, че автоматизираните преводи могат да съдържат грешки или неточности. Оригиналният документ на неговия роден език трябва да се счита за авторитетен източник. За критична информация се препоръчва професионален човешки превод. Ние не носим отговорност за каквито и да е недоразумения или неправилни тълкувания, произтичащи от използването на този превод.