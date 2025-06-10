<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "f83bc722dc758efffd68667d6a1db470",
  "translation_date": "2025-06-10T06:57:34+00:00",
  "source_file": "10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab4/README.md",
  "language_code": "bg"
}
-->
# 🐙 Модул 4: Практическо разработване на MCP - Персонализиран GitHub Clone сървър

![Duration](https://img.shields.io/badge/Duration-30_minutes-blue?style=flat-square)
![Difficulty](https://img.shields.io/badge/Difficulty-Intermediate-orange?style=flat-square)
![MCP](https://img.shields.io/badge/MCP-Custom%20Server-purple?style=flat-square&logo=github)
![VS Code](https://img.shields.io/badge/VS%20Code-Integration-blue?style=flat-square&logo=visualstudiocode)
![GitHub Copilot](https://img.shields.io/badge/GitHub%20Copilot-Agent%20Mode-green?style=flat-square&logo=github)

> **⚡ Бърз старт:** Създайте готов за продукция MCP сървър, който автоматизира клонирането на GitHub хранилища и интеграцията с VS Code само за 30 минути!

## 🎯 Цели на обучението

След края на тази лаборатория ще можете да:

- ✅ Създавате персонализиран MCP сървър за реални разработвачески процеси
- ✅ Имплементирате функционалност за клониране на GitHub хранилища чрез MCP
- ✅ Интегрирате персонализирани MCP сървъри с VS Code и Agent Builder
- ✅ Използвате GitHub Copilot Agent Mode с персонализирани MCP инструменти
- ✅ Тествате и разгръщате персонализирани MCP сървъри в продукционна среда

## 📋 Предварителни изисквания

- Завършени лаборатории 1-3 (основи и напреднало разработване на MCP)
- Абонамент за GitHub Copilot ([налично безплатно записване](https://github.com/github-copilot/signup))
- VS Code с разширения AI Toolkit и GitHub Copilot
- Инсталиран и конфигуриран Git CLI

## 🏗️ Преглед на проекта

### **Реален разработвачески казус**
Като разработчици често използваме GitHub за клониране на хранилища и отварянето им във VS Code или VS Code Insiders. Този ръчен процес включва:
1. Отваряне на терминал/команден ред
2. Навигация до желаната директория
3. Изпълнение на командата `git clone`
4. Отваряне на VS Code в клонираната директория

**Нашето MCP решение обединява това в една интелигентна команда!**

### **Какво ще създадете**
**GitHub Clone MCP Server** (`git_mcp_server`), който предлага:

| Функция | Описание | Полза |
|---------|----------|-------|
| 🔄 **Умно клониране на хранилища** | Клонира GitHub репозитории с валидация | Автоматична проверка за грешки |
| 📁 **Интелигентно управление на директории** | Проверява и създава директории безопасно | Предпазва от презаписване |
| 🚀 **Кросплатформена интеграция с VS Code** | Отваря проекти във VS Code/Insiders | Безпроблемен преход в работния процес |
| 🛡️ **Здрава обработка на грешки** | Управлява проблеми с мрежа, права и пътища | Надеждност за продукционна среда |

---

## 📖 Стъпка по стъпка имплементация

### Стъпка 1: Създаване на GitHub агент в Agent Builder

1. **Стартирайте Agent Builder** през разширението AI Toolkit
2. **Създайте нов агент** с следната конфигурация:
   ```
   Agent Name: GitHubAgent
   ```

3. **Инициализирайте персонализиран MCP сървър:**
   - Отидете на **Tools** → **Add Tool** → **MCP Server**
   - Изберете **"Create A new MCP Server"**
   - Изберете **Python шаблон** за максимална гъвкавост
   - **Име на сървъра:** `git_mcp_server`

### Стъпка 2: Конфигуриране на GitHub Copilot Agent Mode

1. **Отворете GitHub Copilot** във VS Code (Ctrl/Cmd + Shift + P → "GitHub Copilot: Open")
2. **Изберете Agent Model** в интерфейса на Copilot
3. **Изберете модел Claude 3.7** за по-добри възможности за разсъждение
4. **Активирайте MCP интеграция** за достъп до инструменти

> **💡 Полезен съвет:** Claude 3.7 осигурява по-добро разбиране на разработващите процеси и модели за обработка на грешки.

### Стъпка 3: Имплементиране на основната функционалност на MCP сървъра

**Използвайте следния подробен prompt с GitHub Copilot Agent Mode:**

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

### Стъпка 4: Тествайте своя MCP сървър

#### 4a. Тест в Agent Builder

1. **Стартирайте debug конфигурацията** за Agent Builder
2. **Конфигурирайте агента с този системен prompt:**

```
SYSTEM_PROMPT:
You are my intelligent coding repository assistant. You help developers efficiently clone GitHub repositories and set up their development environment. Always provide clear feedback about operations and handle errors gracefully.
```

3. **Тествайте с реалистични потребителски сценарии:**

```
USER_PROMPT EXAMPLES:

Scenario : Basic Clone and Open
"Clone {Your GitHub Repo link such as https://github.com/kinfey/GHCAgentWorkshop
 } and save to {The global path you specify}, then open it with VS Code Insiders"
```

![Agent Builder Testing](../../../../translated_images/DebugAgent.81d152370c503241b3b39a251b8966f7f739286df19dd57f9147f6402214a012.bg.png)

**Очаквани резултати:**
- ✅ Успешно клониране с потвърждение на пътя
- ✅ Автоматично стартиране на VS Code
- ✅ Ясни съобщения за грешки при невалидни ситуации
- ✅ Коректна обработка на гранични случаи

#### 4b. Тест в MCP Inspector


![MCP Inspector Testing](../../../../translated_images/DebugInspector.eb5c95f94c69a8ba36944941b9a3588309a3a2fae101ace470ee09bde41d1667.bg.png)

---

**🎉 Поздравления!** Успешно създадохте практичен, готов за продукция MCP сървър, който решава реални предизвикателства в разработващите процеси. Вашият персонализиран GitHub clone сървър демонстрира силата на MCP за автоматизация и повишаване на продуктивността на разработчиците.

### 🏆 Постигнати умения:
- ✅ **MCP Developer** - Създаване на персонализиран MCP сървър
- ✅ **Workflow Automator** - Оптимизиране на разработващите процеси  
- ✅ **Integration Expert** - Свързване на множество разработващи инструменти
- ✅ **Production Ready** - Изграждане на решения за продукционна употреба

---

## 🎓 Завършване на работилницата: Вашето пътешествие с Model Context Protocol

**Уважаеми участник в работилницата,**

Поздравления за успешното завършване на всички четири модула на работилницата за Model Context Protocol! Изминахте дълъг път от разбирането на основите на AI Toolkit до създаването на готови за продукция MCP сървъри, които решават реални разработвачески предизвикателства.

### 🚀 Обзор на вашия учебен път:

**[Модул 1](../lab1/README.md)**: Започнахте с изучаване на основите на AI Toolkit, тестване на модели и създаване на първия си AI агент.

**[Модул 2](../lab2/README.md)**: Научихте архитектурата на MCP, интегрирахте Playwright MCP и изградихте първия си агент за браузърна автоматизация.

**[Модул 3](../lab3/README.md)**: Напреднахте към разработване на персонализирани MCP сървъри с Weather MCP сървър и овладяхте инструментите за дебъг.

**[Модул 4](../lab4/README.md)**: Приложихте всичко това за създаване на практичен инструмент за автоматизация на GitHub репозитории.

### 🌟 Какво овладяхте:

- ✅ **Екосистема AI Toolkit**: Модели, агенти и интеграционни модели
- ✅ **Архитектура MCP**: Клиент-сървър дизайн, транспортни протоколи и сигурност
- ✅ **Инструменти за разработчици**: От Playground до Inspector и продукционно разгръщане
- ✅ **Персонализирана разработка**: Създаване, тестване и разгръщане на собствени MCP сървъри
- ✅ **Практически приложения**: Решаване на реални предизвикателства в работните процеси с AI

### 🔮 Следващи стъпки:

1. **Създайте свой MCP сървър**: Приложете наученото, за да автоматизирате своите уникални процеси
2. **Присъединете се към MCP общността**: Споделяйте творенията си и учете от другите
3. **Изследвайте напреднали интеграции**: Свържете MCP сървъри с корпоративни системи
4. **Допринасяйте за Open Source**: Помагайте за подобряване на MCP инструментите и документацията

Запомнете, тази работилница е само началото. Екосистемата на Model Context Protocol се развива бързо и вече сте подготвени да сте в авангарда на AI-базираните инструменти за разработка.

**Благодарим ви за участието и отдадеността към ученето!**

Надяваме се тази работилница да е провокирала идеи, които ще променят начина, по който изграждате и взаимодействате с AI инструменти в своя разработващ път.

**Приятно кодиране!**

---

**Отказ от отговорност**:  
Този документ е преведен с помощта на AI преводаческа услуга [Co-op Translator](https://github.com/Azure/co-op-translator). Въпреки че се стремим към точност, моля, имайте предвид, че автоматизираните преводи могат да съдържат грешки или неточности. Оригиналният документ на неговия роден език трябва да се счита за авторитетен източник. За критична информация се препоръчва професионален човешки превод. Ние не носим отговорност за каквито и да е недоразумения или неправилни тълкувания, произтичащи от използването на този превод.