<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "671162f2687253f22af11187919ed02d",
  "translation_date": "2025-06-21T13:38:14+00:00",
  "source_file": "09-CaseStudy/README.md",
  "language_code": "mo"
}
-->
# MCP 實戰：真實案例研究

Model Context Protocol (MCP) 正在改變 AI 應用程式與資料、工具及服務互動的方式。本節介紹多個真實案例，展示 MCP 在各種企業場景中的實際應用。

## 概述

本節展示 MCP 實作的具體範例，強調組織如何運用此協定解決複雜的商業挑戰。透過這些案例研究，你將深入了解 MCP 在真實場景中的多樣性、可擴展性及實際效益。

## 主要學習目標

透過探討這些案例，你將能夠：

- 了解 MCP 如何應用於解決特定的商業問題
- 學習不同的整合模式與架構方法
- 掌握在企業環境中實作 MCP 的最佳實踐
- 瞭解真實實作中遇到的挑戰與解決方案
- 發掘在自身專案中應用類似模式的機會

## 精選案例研究

### 1. [Azure AI 旅遊代理人 — 參考實作](./travelagentsample.md)

本案例探討微軟的完整參考解決方案，示範如何利用 MCP、Azure OpenAI 及 Azure AI Search 建構多代理人 AI 驅動的旅遊規劃應用。專案重點包括：

- 透過 MCP 進行多代理人協調
- 與 Azure AI Search 整合企業資料
- 使用 Azure 服務打造安全且可擴展的架構
- 可擴充的工具鏈與可重複使用的 MCP 元件
- 由 Azure OpenAI 支援的對話式使用者體驗

架構與實作細節提供了以 MCP 作為協調層構建複雜多代理系統的寶貴見解。

### 2. [從 YouTube 資料更新 Azure DevOps 項目](./UpdateADOItemsFromYT.md)

此案例展示 MCP 在自動化工作流程中的實際應用，說明如何利用 MCP 工具：

- 從線上平台（YouTube）擷取資料
- 更新 Azure DevOps 系統中的工作項目
- 建立可重複的自動化流程
- 跨系統整合資料

此範例說明即使是相對簡單的 MCP 實作，也能透過自動化例行工作與提升資料一致性，大幅提高效率。

### 3. [使用 MCP 進行即時文件檢索](./docs-mcp/README.md)

本案例引導你如何使用 Python 控制台客戶端連接 Model Context Protocol (MCP) 伺服器，檢索並記錄即時且具上下文的 Microsoft 文件。你將學會：

- 使用 Python 客戶端與官方 MCP SDK 連接 MCP 伺服器
- 利用串流 HTTP 客戶端高效取得即時資料
- 呼叫伺服器上的文件工具，並直接在控制台記錄回應
- 在不離開終端機的情況下，將最新 Microsoft 文件整合到工作流程中

本章包含實作練習、最小可用程式碼範例以及深入學習的資源連結。請參閱連結章節的完整操作與程式碼，了解 MCP 如何改變終端機環境中的文件存取與開發者生產力。

### 4. [使用 MCP 建構互動式學習計劃產生器網頁應用](./docs-mcp/README.md)

此案例示範如何使用 Chainlit 與 Model Context Protocol (MCP) 建立互動式網頁應用，為任何主題生成個人化學習計劃。使用者可指定科目（如「AI-900 證照」）及學習週期（例如 8 週），應用會提供逐週推薦內容。Chainlit 提供對話式聊天介面，讓體驗更具互動性與適應性。

- 由 Chainlit 支援的對話式網頁應用
- 使用者驅動的主題與時長輸入
- 利用 MCP 提供逐週內容推薦
- 聊天介面中即時且適應性的回應

此專案展示對話式 AI 與 MCP 如何結合，在現代網頁環境中打造動態且以使用者為中心的教育工具。

### 5. [在 VS Code 中使用 MCP 伺服器的內嵌文件](./docs-mcp/README.md)

本案例示範如何利用 MCP 伺服器將 Microsoft Learn 文件直接帶入 VS Code 環境，無需切換瀏覽器分頁！你將看到如何：

- 利用 MCP 面板或命令面板即時搜尋並閱讀 VS Code 內文件
- 直接在 README 或課程 Markdown 檔案中引用文件並插入連結
- 結合 GitHub Copilot 與 MCP，實現無縫的 AI 支援文件與程式碼工作流程
- 透過即時回饋與 Microsoft 官方準確度，驗證並強化文件內容
- 將 MCP 整合至 GitHub 工作流程，持續驗證文件品質

實作內容包含：
- `.vscode/mcp.json` 範例配置，方便快速設定
- 以截圖說明內嵌文件體驗流程
- 結合 Copilot 與 MCP 提升生產力的技巧

此情境非常適合課程作者、文件撰寫者及開發者，讓他們能專注於編輯器內作業，同時使用文件、Copilot 與驗證工具，皆由 MCP 驅動。

## 結語

這些案例強調 Model Context Protocol 在真實場景中的多樣性與實用性。從複雜的多代理系統到針對性的自動化工作流程，MCP 提供了一種標準化方式，連結 AI 系統與所需的工具及資料，創造價值。

透過研究這些實作，你能掌握架構模式、實作策略與最佳實踐，應用於自己的 MCP 專案。這些範例證明 MCP 不僅是理論框架，更是解決實際商業問題的有效方案。

## 附加資源

- [Azure AI Travel Agents GitHub Repository](https://github.com/Azure-Samples/azure-ai-travel-agents)
- [Azure DevOps MCP Tool](https://github.com/microsoft/azure-devops-mcp)
- [Playwright MCP Tool](https://github.com/microsoft/playwright-mcp)
- [Microsoft Docs MCP Server](https://github.com/MicrosoftDocs/mcp)
- [MCP Community Examples](https://github.com/microsoft/mcp)

**免責聲明**：  
本文件係使用 AI 翻譯服務 [Co-op Translator](https://github.com/Azure/co-op-translator) 進行翻譯。雖然我們力求準確，但請注意，自動翻譯可能包含錯誤或不準確之處。原始文件之母語版本應視為權威來源。對於重要資訊，建議採用專業人工翻譯。我們對因使用本翻譯而產生的任何誤解或誤釋概不負責。