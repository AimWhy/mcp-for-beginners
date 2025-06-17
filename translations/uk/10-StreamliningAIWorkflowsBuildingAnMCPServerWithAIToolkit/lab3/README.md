<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "dd8da3f75addcef453fe11f02a270217",
  "translation_date": "2025-06-17T16:34:44+00:00",
  "source_file": "10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab3/README.md",
  "language_code": "uk"
}
-->
# 🔧 Модуль 3: Розширена розробка MCP з AI Toolkit

![Duration](https://img.shields.io/badge/Duration-20_minutes-blue?style=flat-square)
![AI Toolkit](https://img.shields.io/badge/AI_Toolkit-Required-orange?style=flat-square)
![Python](https://img.shields.io/badge/Python-3.10+-green?style=flat-square)
![MCP SDK](https://img.shields.io/badge/MCP_SDK-1.9.3-purple?style=flat-square)
![Inspector](https://img.shields.io/badge/MCP_Inspector-0.14.0-blue?style=flat-square)

## 🎯 Цілі навчання

До кінця цієї лабораторної роботи ви зможете:

- ✅ Створювати власні MCP сервери за допомогою AI Toolkit
- ✅ Налаштовувати і використовувати останню версію MCP Python SDK (v1.9.3)
- ✅ Налаштовувати та використовувати MCP Inspector для налагодження
- ✅ Налагоджувати MCP сервери в середовищах Agent Builder та Inspector
- ✅ Розуміти розширені робочі процеси розробки MCP серверів

## 📋 Вимоги

- Завершення Лабораторної роботи 2 (Основи MCP)
- VS Code з встановленим розширенням AI Toolkit
- Середовище Python 3.10+
- Node.js та npm для налаштування Inspector

## 🏗️ Що ви створите

У цій лабораторній роботі ви створите **Weather MCP Server**, який демонструє:
- Власну реалізацію MCP сервера
- Інтеграцію з AI Toolkit Agent Builder
- Професійні робочі процеси налагодження
- Сучасні патерни використання MCP SDK

---

## 🔧 Огляд основних компонентів

### 🐍 MCP Python SDK  
Model Context Protocol Python SDK є основою для створення власних MCP серверів. Ви використовуватимете версію 1.9.3 з покращеними можливостями налагодження.

### 🔍 MCP Inspector  
Потужний інструмент для налагодження, що надає:
- Моніторинг сервера в реальному часі
- Візуалізацію виконання інструментів
- Перевірку мережевих запитів/відповідей
- Інтерактивне тестування

---

## 📖 Покрокова реалізація

### Крок 1: Створення WeatherAgent в Agent Builder

1. **Запустіть Agent Builder** у VS Code через розширення AI Toolkit  
2. **Створіть нового агента** з такою конфігурацією:  
   - Ім’я агента: `WeatherAgent`

![Agent Creation](../../../../translated_images/Agent.c9c33f6a412b4cdedfb973fe5448bdb33de3f400055603111b875610e9b917ab.uk.png)

### Крок 2: Ініціалізація проекту MCP сервера

1. **Перейдіть у Tools** → **Add Tool** в Agent Builder  
2. **Виберіть "MCP Server"** зі списку опцій  
3. **Обрати "Create A new MCP Server"**  
4. **Виберіть шаблон `python-weather`**  
5. **Назвіть свій сервер:** `weather_mcp`

![Python Template Selection](../../../../translated_images/Pythontemplate.9d0a2913c6491500bd673430f024dc44676af2808a27b5da9dcc0eb7063adc28.uk.png)

### Крок 3: Відкрийте та ознайомтеся з проектом

1. **Відкрийте створений проект** у VS Code  
2. **Перегляньте структуру проекту:**  
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

### Крок 4: Оновлення до останньої версії MCP SDK

> **🔍 Чому оновлювати?** Ми хочемо використовувати останню версію MCP SDK (v1.9.3) та сервіс Inspector (0.14.0) для розширених функцій і кращих можливостей налагодження.

#### 4a. Оновлення Python залежностей

**Відредагуйте `pyproject.toml`:** update [./code/weather_mcp/pyproject.toml](../../../../10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab3/code/weather_mcp/pyproject.toml)


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

**Відредагуйте `.vscode/tasks.json`:**

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

## 🚀 Запуск і тестування MCP сервера

### Крок 6: Встановлення залежностей

Після внесення змін у конфігурацію виконайте такі команди:

**Встановіть Python залежності:**  
```bash
uv sync
```

**Встановіть залежності Inspector:**  
```bash
cd inspector
npm install
```

### Крок 7: Налагодження через Agent Builder

1. **Натисніть F5** або виберіть конфігурацію **"Debug in Agent Builder"**  
2. **Виберіть compound конфігурацію** у панелі налагодження  
3. **Дочекайтесь запуску сервера та відкриття Agent Builder**  
4. **Перевірте роботу вашого Weather MCP Server** за допомогою запитів природною мовою

Введіть запит у такому вигляді

SYSTEM_PROMPT

```
You are my weather assistant
```

USER_PROMPT

```
How's the weather like in Seattle
```

![Agent Builder Debug Result](../../../../translated_images/Result.6ac570f7d2b1d5389c561ab0566970fe0f13e75bdd976b6a7f0270bc715d07f8.uk.png)

### Крок 8: Налагодження через MCP Inspector

1. **Використайте конфігурацію "Debug in Inspector"** (Edge або Chrome)  
2. **Відкрийте інтерфейс Inspector** за адресою `http://localhost:6274`  
3. **Огляньте інтерактивне тестове середовище:**  
   - Перегляд доступних інструментів  
   - Тестування виконання інструментів  
   - Моніторинг мережевих запитів  
   - Налагодження відповідей сервера

![MCP Inspector Interface](../../../../translated_images/Inspector.5672415cd02fe8731774586cc0a1083e3275d2f8491602aecc8ac4d61f2c0d57.uk.png)

---

## 🎯 Основні результати навчання

Виконавши цю лабораторну роботу, ви:

- [x] **Створили власний MCP сервер** за допомогою шаблонів AI Toolkit  
- [x] **Оновилися до останньої версії MCP SDK** (v1.9.3) для розширених можливостей  
- [x] **Налаштували професійні робочі процеси налагодження** для Agent Builder та Inspector  
- [x] **Підготували MCP Inspector** для інтерактивного тестування серверів  
- [x] **Опановували конфігурації налагодження у VS Code** для розробки MCP

## 🔧 Досліджені розширені функції

| Функція | Опис | Випадок використання |
|---------|-------|---------------------|
| **MCP Python SDK v1.9.3** | Остання реалізація протоколу | Сучасна розробка серверів |
| **MCP Inspector 0.14.0** | Інтерактивний інструмент налагодження | Тестування серверів у реальному часі |
| **Налагодження у VS Code** | Інтегроване середовище розробки | Професійний робочий процес налагодження |
| **Інтеграція з Agent Builder** | Пряме підключення AI Toolkit | Повний цикл тестування агентів |

## 📚 Додаткові ресурси

- [Документація MCP Python SDK](https://modelcontextprotocol.io/docs/sdk/python)
- [Посібник по розширенню AI Toolkit](https://code.visualstudio.com/docs/ai/ai-toolkit)
- [Документація налагодження VS Code](https://code.visualstudio.com/docs/editor/debugging)
- [Специфікація Model Context Protocol](https://modelcontextprotocol.io/docs/concepts/architecture)

---

**🎉 Вітаємо!** Ви успішно завершили Лабораторну роботу 3 і тепер можете створювати, налагоджувати та розгортати власні MCP сервери з використанням професійних робочих процесів розробки.

### 🔜 Продовжуйте до наступного модуля

Готові застосувати навички MCP у реальному робочому процесі? Продовжуйте до **[Модуля 4: Практична розробка MCP - Кастомний GitHub Clone Server](../lab4/README.md)**, де ви:  
- Створите MCP сервер, готовий до продакшену, який автоматизує операції з репозиторіями GitHub  
- Реалізуєте функціонал клонування репозиторіїв GitHub через MCP  
- Інтегруєте власні MCP сервери з VS Code та GitHub Copilot Agent Mode  
- Тестуватимете і розгортатимете кастомні MCP сервери у виробничому середовищі  
- Вивчите практичну автоматизацію робочих процесів для розробників

**Відмова від відповідальності**:  
Цей документ був перекладений за допомогою сервісу автоматичного перекладу [Co-op Translator](https://github.com/Azure/co-op-translator). Хоча ми прагнемо до точності, будь ласка, майте на увазі, що автоматичні переклади можуть містити помилки або неточності. Оригінальний документ рідною мовою слід вважати авторитетним джерелом. Для критично важливої інформації рекомендується звертатися до професійного людського перекладу. Ми не несемо відповідальності за будь-які непорозуміння або неправильні тлумачення, що виникли внаслідок використання цього перекладу.