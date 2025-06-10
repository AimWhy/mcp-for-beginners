<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "f83bc722dc758efffd68667d6a1db470",
  "translation_date": "2025-06-10T06:57:01+00:00",
  "source_file": "10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab4/README.md",
  "language_code": "ro"
}
-->
# 🐙 Modulul 4: Dezvoltare Practică MCP - Server Personalizat de Clonare GitHub

![Duration](https://img.shields.io/badge/Duration-30_minutes-blue?style=flat-square)
![Difficulty](https://img.shields.io/badge/Difficulty-Intermediate-orange?style=flat-square)
![MCP](https://img.shields.io/badge/MCP-Custom%20Server-purple?style=flat-square&logo=github)
![VS Code](https://img.shields.io/badge/VS%20Code-Integration-blue?style=flat-square&logo=visualstudiocode)
![GitHub Copilot](https://img.shields.io/badge/GitHub%20Copilot-Agent%20Mode-green?style=flat-square&logo=github)

> **⚡ Start Rapid:** Construiește un server MCP gata de producție care automatizează clonarea depozitelor GitHub și integrarea cu VS Code în doar 30 de minute!

## 🎯 Obiective de Învățare

La finalul acestui laborator vei putea:

- ✅ Să creezi un server MCP personalizat pentru fluxuri de lucru reale de dezvoltare
- ✅ Să implementezi funcționalitatea de clonare a depozitelor GitHub prin MCP
- ✅ Să integrezi servere MCP personalizate cu VS Code și Agent Builder
- ✅ Să folosești GitHub Copilot Agent Mode cu uneltele MCP personalizate
- ✅ Să testezi și să implementezi servere MCP personalizate în medii de producție

## 📋 Cerințe Prealabile

- Finalizarea laboratoarelor 1-3 (fundamente MCP și dezvoltare avansată)
- Abonament GitHub Copilot ([înregistrare gratuită disponibilă](https://github.com/github-copilot/signup))
- VS Code cu extensiile AI Toolkit și GitHub Copilot instalate
- Git CLI instalat și configurat

## 🏗️ Prezentare Generală a Proiectului

### **Provocare Reală de Dezvoltare**
Ca dezvoltatori, folosim frecvent GitHub pentru a clona depozite și a le deschide în VS Code sau VS Code Insiders. Acest proces manual implică:
1. Deschiderea terminalului/command prompt
2. Navigarea către directorul dorit
3. Executarea comenzii `git clone`
4. Deschiderea VS Code în directorul clonat

**Soluția noastră MCP simplifică toate acestea într-o singură comandă inteligentă!**

### **Ce Vei Construi**
Un **GitHub Clone MCP Server** (`git_mcp_server`) care oferă:

| Funcționalitate | Descriere | Beneficiu |
|-----------------|-----------|-----------|
| 🔄 **Clonare Inteligentă a Depozitelor** | Clonează depozite GitHub cu validare | Verificare automată a erorilor |
| 📁 **Gestionare Inteligentă a Directorului** | Verifică și creează directoare în siguranță | Previne suprascrierea |
| 🚀 **Integrare Cross-Platform cu VS Code** | Deschide proiecte în VS Code/Insiders | Tranziție fluidă în fluxul de lucru |
| 🛡️ **Gestionare Robustă a Erorilor** | Gestionează probleme de rețea, permisiuni și căi | Fiabilitate pentru producție |

---

## 📖 Implementare Pas cu Pas

### Pasul 1: Creează Agent GitHub în Agent Builder

1. **Deschide Agent Builder** prin extensia AI Toolkit
2. **Creează un agent nou** cu următoarea configurație:
   ```
   Agent Name: GitHubAgent
   ```

3. **Inițializează serverul MCP personalizat:**
   - Accesează **Tools** → **Add Tool** → **MCP Server**
   - Selectează **"Create A new MCP Server"**
   - Alege **șablonul Python** pentru flexibilitate maximă
   - **Nume Server:** `git_mcp_server`

### Pasul 2: Configurează GitHub Copilot Agent Mode

1. **Deschide GitHub Copilot** în VS Code (Ctrl/Cmd + Shift + P → "GitHub Copilot: Open")
2. **Selectează Modelul Agent** în interfața Copilot
3. **Alege modelul Claude 3.7** pentru capacități avansate de raționament
4. **Activează integrarea MCP** pentru accesul la unelte

> **💡 Sfat Pro:** Claude 3.7 oferă o înțelegere superioară a fluxurilor de dezvoltare și modelelor de gestionare a erorilor.

### Pasul 3: Implementează Funcționalitatea Principală a Serverului MCP

**Folosește promptul detaliat următor cu GitHub Copilot Agent Mode:**

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

### Pasul 4: Testează Serverul MCP

#### 4a. Testare în Agent Builder

1. **Lansează configurația de debug** pentru Agent Builder
2. **Configurează agentul cu acest prompt de sistem:**

```
SYSTEM_PROMPT:
You are my intelligent coding repository assistant. You help developers efficiently clone GitHub repositories and set up their development environment. Always provide clear feedback about operations and handle errors gracefully.
```

3. **Testează cu scenarii realiste de utilizator:**

```
USER_PROMPT EXAMPLES:

Scenario : Basic Clone and Open
"Clone {Your GitHub Repo link such as https://github.com/kinfey/GHCAgentWorkshop
 } and save to {The global path you specify}, then open it with VS Code Insiders"
```

![Agent Builder Testing](../../../../translated_images/DebugAgent.81d152370c503241b3b39a251b8966f7f739286df19dd57f9147f6402214a012.ro.png)

**Rezultate Așteptate:**
- ✅ Clonare reușită cu confirmare a căii
- ✅ Lansare automată VS Code
- ✅ Mesaje clare de eroare pentru scenarii invalide
- ✅ Gestionare corectă a cazurilor limită

#### 4b. Testare în MCP Inspector

![MCP Inspector Testing](../../../../translated_images/DebugInspector.eb5c95f94c69a8ba36944941b9a3588309a3a2fae101ace470ee09bde41d1667.ro.png)

---

**🎉 Felicitări!** Ai creat cu succes un server MCP practic, gata de producție, care rezolvă provocările reale din fluxurile de dezvoltare. Serverul tău personalizat de clonare GitHub demonstrează puterea MCP în automatizarea și creșterea productivității dezvoltatorilor.

### 🏆 Realizări Deblocate:
- ✅ **Dezvoltator MCP** - Server MCP personalizat creat
- ✅ **Automatizator de Fluxuri** - Procese de dezvoltare optimizate  
- ✅ **Expert în Integrare** - Conectarea multiplă a uneltelor de dezvoltare
- ✅ **Gata pentru Producție** - Soluții pregătite pentru implementare

---

## 🎓 Finalizarea Workshop-ului: Călătoria Ta cu Model Context Protocol

**Dragă Participant la Workshop,**

Felicitări pentru finalizarea celor patru module ale workshop-ului Model Context Protocol! Ai parcurs un drum lung, de la înțelegerea conceptelor de bază AI Toolkit până la construirea serverelor MCP gata de producție care rezolvă provocări reale de dezvoltare.

### 🚀 Recapitulare a Căii Tale de Învățare:

**[Modulul 1](../lab1/README.md)**: Ai început explorând fundamentele AI Toolkit, testarea modelelor și crearea primului agent AI.

**[Modulul 2](../lab2/README.md)**: Ai învățat arhitectura MCP, ai integrat Playwright MCP și ai construit primul agent de automatizare browser.

**[Modulul 3](../lab3/README.md)**: Ai avansat în dezvoltarea serverelor MCP personalizate cu serverul Weather MCP și ai stăpânit uneltele de depanare.

**[Modulul 4](../lab4/README.md)**: Acum ai aplicat totul pentru a crea un instrument practic de automatizare a fluxului de lucru cu depozite GitHub.

### 🌟 Ce Ai Stăpânit:

- ✅ **Ecosistemul AI Toolkit**: Modele, agenți și modele de integrare
- ✅ **Arhitectura MCP**: Design client-server, protocoale de transport și securitate
- ✅ **Unelte pentru Dezvoltatori**: De la Playground la Inspector și implementare în producție
- ✅ **Dezvoltare Personalizată**: Construirea, testarea și implementarea propriilor servere MCP
- ✅ **Aplicații Practice**: Rezolvarea provocărilor reale din fluxurile de lucru cu AI

### 🔮 Pașii Următori:

1. **Construiește propriul server MCP**: Aplică aceste abilități pentru a automatiza fluxurile tale unice
2. **Alătură-te Comunității MCP**: Împărtășește creațiile și învață de la alții
3. **Explorează integrarea avansată**: Conectează servere MCP la sisteme enterprise
4. **Contribuie la Open Source**: Ajută la îmbunătățirea uneltelor și documentației MCP

Amintește-ți, acest workshop este doar începutul. Ecosistemul Model Context Protocol evoluează rapid, iar tu ești acum pregătit să fii în fruntea uneltelor de dezvoltare bazate pe AI.

**Îți mulțumim pentru participare și dedicarea ta în învățare!**

Sperăm că acest workshop ți-a oferit idei care vor transforma modul în care construiești și interacționezi cu uneltele AI în călătoria ta de dezvoltare.

**Codare plăcută!**

---

**Declinare a responsabilității**:  
Acest document a fost tradus folosind serviciul de traducere automată AI [Co-op Translator](https://github.com/Azure/co-op-translator). Deși ne străduim pentru acuratețe, vă rugăm să țineți cont că traducerile automate pot conține erori sau inexactități. Documentul original în limba sa nativă trebuie considerat sursa autoritară. Pentru informații critice, se recomandă traducerea profesională realizată de un traducător uman. Nu ne asumăm răspunderea pentru eventualele neînțelegeri sau interpretări greșite rezultate din utilizarea acestei traduceri.