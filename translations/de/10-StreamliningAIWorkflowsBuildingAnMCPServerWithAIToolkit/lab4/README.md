<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "f83bc722dc758efffd68667d6a1db470",
  "translation_date": "2025-06-10T06:39:59+00:00",
  "source_file": "10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab4/README.md",
  "language_code": "de"
}
-->
# 🐙 Modul 4: Praktische MCP-Entwicklung – Eigener GitHub Clone Server

![Duration](https://img.shields.io/badge/Duration-30_minutes-blue?style=flat-square)
![Difficulty](https://img.shields.io/badge/Difficulty-Intermediate-orange?style=flat-square)
![MCP](https://img.shields.io/badge/MCP-Custom%20Server-purple?style=flat-square&logo=github)
![VS Code](https://img.shields.io/badge/VS%20Code-Integration-blue?style=flat-square&logo=visualstudiocode)
![GitHub Copilot](https://img.shields.io/badge/GitHub%20Copilot-Agent%20Mode-green?style=flat-square&logo=github)

> **⚡ Schnellstart:** Baue in nur 30 Minuten einen produktionsreifen MCP-Server, der das Klonen von GitHub-Repositories und die VS Code-Integration automatisiert!

## 🎯 Lernziele

Am Ende dieses Labs wirst du in der Lage sein:

- ✅ Einen eigenen MCP-Server für reale Entwicklungs-Workflows zu erstellen
- ✅ Die Funktionalität zum Klonen von GitHub-Repositories über MCP zu implementieren
- ✅ Eigene MCP-Server in VS Code und Agent Builder zu integrieren
- ✅ Den GitHub Copilot Agent Mode mit eigenen MCP-Tools zu nutzen
- ✅ Eigene MCP-Server in produktiven Umgebungen zu testen und bereitzustellen

## 📋 Voraussetzungen

- Abschluss der Labs 1-3 (MCP-Grundlagen und fortgeschrittene Entwicklung)
- GitHub Copilot Abonnement ([kostenlose Anmeldung verfügbar](https://github.com/github-copilot/signup))
- VS Code mit AI Toolkit und GitHub Copilot Erweiterungen
- Git CLI installiert und konfiguriert

## 🏗️ Projektübersicht

### **Herausforderung aus der Praxis**
Als Entwickler nutzen wir häufig GitHub, um Repositories zu klonen und in VS Code oder VS Code Insiders zu öffnen. Dieser manuelle Prozess umfasst:
1. Terminal/Command Prompt öffnen
2. Zum gewünschten Verzeichnis navigieren
3. `git clone` Befehl ausführen
4. VS Code im geklonten Verzeichnis öffnen

**Unsere MCP-Lösung fasst das in einem einzigen intelligenten Befehl zusammen!**

### **Was du bauen wirst**
Einen **GitHub Clone MCP Server** (`git_mcp_server`), der folgende Funktionen bietet:

| Funktion | Beschreibung | Vorteil |
|---------|-------------|---------|
| 🔄 **Intelligentes Klonen von Repositories** | Klonen von GitHub-Repos mit Validierung | Automatische Fehlerüberprüfung |
| 📁 **Intelligente Verzeichnisverwaltung** | Sichere Prüfung und Erstellung von Verzeichnissen | Verhindert Überschreiben |
| 🚀 **Plattformübergreifende VS Code Integration** | Öffnen von Projekten in VS Code/Insiders | Nahtloser Workflow-Wechsel |
| 🛡️ **Robuste Fehlerbehandlung** | Umgang mit Netzwerk-, Berechtigungs- und Pfadproblemen | Produktionsreife Zuverlässigkeit |

---

## 📖 Schritt-für-Schritt Umsetzung

### Schritt 1: GitHub Agent im Agent Builder erstellen

1. **Agent Builder** über die AI Toolkit Erweiterung starten
2. **Neuen Agenten erstellen** mit folgender Konfiguration:
   ```
   Agent Name: GitHubAgent
   ```

3. **Eigenen MCP-Server initialisieren:**
   - Gehe zu **Tools** → **Add Tool** → **MCP Server**
   - Wähle **"Create A new MCP Server"**
   - Wähle die **Python-Vorlage** für maximale Flexibilität
   - **Servername:** `git_mcp_server`

### Schritt 2: GitHub Copilot Agent Mode konfigurieren

1. **GitHub Copilot in VS Code öffnen** (Strg/Cmd + Shift + P → "GitHub Copilot: Open")
2. **Agentenmodell auswählen** in der Copilot-Oberfläche
3. **Claude 3.7 Modell wählen** für verbesserte Schlussfolgerungen
4. **MCP-Integration aktivieren** für Toolzugriff

> **💡 Profi-Tipp:** Claude 3.7 bietet ein besseres Verständnis von Entwicklungs-Workflows und Fehlerbehandlungsmustern.

### Schritt 3: Kernfunktionalität des MCP-Servers implementieren

**Nutze folgenden detaillierten Prompt mit GitHub Copilot Agent Mode:**

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

### Schritt 4: Deinen MCP-Server testen

#### 4a. Test im Agent Builder

1. **Debug-Konfiguration** im Agent Builder starten
2. **Agenten mit folgendem Systemprompt konfigurieren:**

```
SYSTEM_PROMPT:
You are my intelligent coding repository assistant. You help developers efficiently clone GitHub repositories and set up their development environment. Always provide clear feedback about operations and handle errors gracefully.
```

3. **Tests mit realistischen Benutzerszenarien durchführen:**

```
USER_PROMPT EXAMPLES:

Scenario : Basic Clone and Open
"Clone {Your GitHub Repo link such as https://github.com/kinfey/GHCAgentWorkshop
 } and save to {The global path you specify}, then open it with VS Code Insiders"
```

![Agent Builder Testing](../../../../translated_images/DebugAgent.81d152370c503241b3b39a251b8966f7f739286df19dd57f9147f6402214a012.de.png)

**Erwartete Ergebnisse:**
- ✅ Erfolgreiches Klonen mit Pfadbestätigung
- ✅ Automatischer Start von VS Code
- ✅ Klare Fehlermeldungen bei ungültigen Szenarien
- ✅ Saubere Behandlung von Sonderfällen

#### 4b. Test im MCP Inspector

![MCP Inspector Testing](../../../../translated_images/DebugInspector.eb5c95f94c69a8ba36944941b9a3588309a3a2fae101ace470ee09bde41d1667.de.png)

---

**🎉 Herzlichen Glückwunsch!** Du hast erfolgreich einen praktischen, produktionsreifen MCP-Server erstellt, der reale Entwicklungs-Workflow-Herausforderungen löst. Dein eigener GitHub Clone Server zeigt die Stärke von MCP zur Automatisierung und Steigerung der Entwicklerproduktivität.

### 🏆 Errungenschaften freigeschaltet:
- ✅ **MCP Developer** – Eigenen MCP-Server erstellt
- ✅ **Workflow Automator** – Entwicklungsprozesse optimiert  
- ✅ **Integrationsexperte** – Mehrere Entwicklungstools verbunden
- ✅ **Produktionsreif** – Bereit für den Einsatz in der Praxis

---

## 🎓 Workshop-Abschluss: Deine Reise mit dem Model Context Protocol

**Liebe Workshop-Teilnehmerin, lieber Workshop-Teilnehmer,**

herzlichen Glückwunsch zum Abschluss aller vier Module des Model Context Protocol Workshops! Du hast einen weiten Weg zurückgelegt – vom Verständnis der AI Toolkit-Grundlagen bis hin zum Bau produktionsreifer MCP-Server, die reale Entwicklungsprobleme lösen.

### 🚀 Rückblick auf deinen Lernpfad:

**[Modul 1](../lab1/README.md)**: Einstieg in AI Toolkit Grundlagen, Modelltests und Erstellung deines ersten AI-Agenten.

**[Modul 2](../lab2/README.md)**: Verständnis der MCP-Architektur, Integration von Playwright MCP und Bau eines Browser-Automatisierungsagenten.

**[Modul 3](../lab3/README.md)**: Fortgeschrittene MCP-Server-Entwicklung mit dem Weather MCP Server und Beherrschung von Debugging-Tools.

**[Modul 4](../lab4/README.md)**: Anwendung aller Kenntnisse zur Erstellung eines praktischen GitHub Repository Workflow Automatisierungstools.

### 🌟 Deine Erfolge:

- ✅ **AI Toolkit Ökosystem**: Modelle, Agenten und Integrationsmuster
- ✅ **MCP-Architektur**: Client-Server-Design, Transportprotokolle und Sicherheit
- ✅ **Entwicklertools**: Vom Playground über Inspector bis hin zur produktiven Bereitstellung
- ✅ **Eigene Entwicklung**: Erstellen, Testen und Ausrollen eigener MCP-Server
- ✅ **Praxisnahe Anwendungen**: Lösung realer Workflow-Herausforderungen mit KI

### 🔮 Deine nächsten Schritte:

1. **Eigenen MCP-Server bauen**: Nutze dein Wissen, um individuelle Workflows zu automatisieren
2. **MCP-Community beitreten**: Teile deine Projekte und lerne von anderen
3. **Fortgeschrittene Integration erforschen**: Verbinde MCP-Server mit Unternehmenssystemen
4. **Open Source beitragen**: Unterstütze die Weiterentwicklung von MCP-Tools und Dokumentation

Denke daran, dieser Workshop ist erst der Anfang. Das Model Context Protocol-Ökosystem entwickelt sich rasant weiter, und du bist jetzt bestens gerüstet, um an der Spitze KI-gestützter Entwicklungstools zu stehen.

**Vielen Dank für deine Teilnahme und dein Engagement beim Lernen!**

Wir hoffen, dieser Workshop hat dir Impulse gegeben, wie du KI-Tools in deiner Entwicklung effizient nutzen und gestalten kannst.

**Viel Erfolg beim Programmieren!**

---

**Haftungsausschluss**:  
Dieses Dokument wurde mit dem KI-Übersetzungsdienst [Co-op Translator](https://github.com/Azure/co-op-translator) übersetzt. Obwohl wir uns um Genauigkeit bemühen, beachten Sie bitte, dass automatisierte Übersetzungen Fehler oder Ungenauigkeiten enthalten können. Das Originaldokument in seiner Ursprungssprache ist als maßgebliche Quelle zu betrachten. Für wichtige Informationen wird eine professionelle menschliche Übersetzung empfohlen. Wir übernehmen keine Haftung für Missverständnisse oder Fehlinterpretationen, die aus der Verwendung dieser Übersetzung entstehen.