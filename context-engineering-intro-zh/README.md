# Context Engineering Template

一個全面的 template，用於開始使用 Context Engineering - 這是一門為 AI 編程助手設計 context 的學科，讓它們擁有端到端完成工作所需的信息。

> **Context Engineering 比 prompt engineering 好 10 倍，比 vibe coding 好 100 倍。**

## 🚀 快速開始

```bash
# 1. 複製此 template
git clone https://github.com/GitYCC/context-engineering-intro-zh.git
cd context-engineering-intro-zh

# 2. 設置您的專案規則（可選 - 已提供 template）
# 編輯 CLAUDE.md 以添加您的專案特定指導原則

# 3. 添加範例（強烈推薦）
# 將相關的程式碼範例放入 examples/ 資料夾

# 4. 創建您的初始功能請求
# 編輯 INITIAL.md 以包含您的功能需求

# 5. 產生全面的 PRP（Product Requirements Prompt）
# 在 Claude Code 中運行：
/generate-prp INITIAL.md

# 6. 執行 PRP 以實現您的功能
# 在 Claude Code 中運行：
/execute-prp PRPs/your-feature-name.md
```

## 📚 目錄

- [什麼是 Context Engineering？](#什麼是-context-engineering)
- [Template 結構](#template-結構)
- [步驟指南](#步驟指南)
- [編寫有效的 INITIAL.md 文件](#編寫有效的-initialmd-文件)
- [PRP 工作流程](#prp-工作流程)
- [有效使用範例](#有效使用範例)
- [最佳實踐](#最佳實踐)

## 什麼是 Context Engineering？

Context Engineering 代表了與傳統 prompt engineering 的範式轉換：

### Prompt Engineering vs Context Engineering

**Prompt Engineering：**
- 專注於聰明的措辭和特定的表達方式
- 僅限於如何表達任務
- 就像給某人一張便利貼

**Context Engineering：**
- 提供全面 context 的完整系統
- 包括文檔、範例、規則、模式和驗證
- 就像編寫一個包含所有細節的完整劇本

### 為什麼 Context Engineering 重要

1. **減少 AI 失敗**：大多數 agent 失敗不是模型失敗 - 而是 context 失敗
2. **確保一致性**：AI 遵循您的專案模式和慣例
3. **支援複雜功能**：AI 可以在適當的 context 下處理多步驟實現
4. **自我糾正**：驗證迴圈允許 AI 修正自己的錯誤

## Template 結構

```
context-engineering-intro/
├── .claude/
│   ├── commands/
│   │   ├── generate-prp.md    # 產生全面的 PRPs
│   │   └── execute-prp.md     # 執行 PRPs 以實現功能
│   └── settings.local.json    # Claude Code 權限
├── PRPs/
│   ├── templates/
│   │   └── prp_base.md       # PRPs 基礎 template
│   └── EXAMPLE_multi_agent_prp.md  # 完整 PRP 的範例
├── examples/                  # 您的程式碼範例（關鍵！）
├── CLAUDE.md                 # AI 助手的全域規則
├── INITIAL.md               # 功能請求的 template
├── INITIAL_EXAMPLE.md       # 功能請求範例
└── README.md                # 此文件
```

此 template 不專注於 RAG 和具有 context engineering 的工具，因為我很快就會有更多內容。;)

## 步驟指南

### 1. 設置全域規則（CLAUDE.md）

`CLAUDE.md` 文件包含專案範圍的規則，AI 助手將在每次對話中遵循這些規則。Template 包括：

- **專案意識**：閱讀規劃文檔、檢查任務
- **程式碼結構**：文件大小限制、模組組織
- **測試要求**：單元測試模式、覆蓋率期望
- **風格慣例**：語言偏好、格式化規則
- **文檔標準**：docstring 格式、註釋實踐

**您可以直接使用提供的 template 或為您的專案自訂它。**

### 2. 創建您的初始功能請求

編輯 `INITIAL.md` 以描述您想要構建的內容：

```markdown
## FEATURE:
[描述您想要構建的內容 - 具體說明功能和需求]

## EXAMPLES:
[列出 examples/ 資料夾中的任何範例文件並解釋應如何使用它們]

## DOCUMENTATION:
[包含相關文檔、APIs 或 MCP server 資源的連結]

## OTHER CONSIDERATIONS:
[提及任何陷阱、特定需求或 AI 助手通常遺漏的事項]
```

**請參閱 `INITIAL_EXAMPLE.md` 獲得完整範例。**

### 3. 產生 PRP

PRPs（Product Requirements Prompts）是全面的實現藍圖，包括：

- 完整的 context 和文檔
- 帶有驗證的實現步驟
- 錯誤處理模式
- 測試要求

它們類似於 PRDs（Product Requirements Documents），但更專門針對指導 AI 編程助手。

在 Claude Code 中運行：
```bash
/generate-prp INITIAL.md
```

**注意：** 斜線命令是在 `.claude/commands/` 中定義的自訂命令。您可以查看它們的實現：
- `.claude/commands/generate-prp.md` - 查看它如何研究和創建 PRPs
- `.claude/commands/execute-prp.md` - 查看它如何從 PRPs 實現功能

這些命令中的 `$ARGUMENTS` 變數接收您在命令名稱後傳遞的任何內容（例如，`INITIAL.md` 或 `PRPs/your-feature.md`）。

此命令將：
1. 讀取您的功能請求
2. 研究程式碼庫以找到模式
3. 搜索相關文檔
4. 在 `PRPs/your-feature-name.md` 中創建全面的 PRP

### 4. 執行 PRP

產生後，執行 PRP 以實現您的功能：

```bash
/execute-prp PRPs/your-feature-name.md
```

AI 編程助手將：
1. 從 PRP 讀取所有 context
2. 創建詳細的實現計劃
3. 執行每個步驟並進行驗證
4. 運行測試並修復任何問題
5. 確保滿足所有成功標準

## 編寫有效的 INITIAL.md 文件

### 重要部分說明

**FEATURE**：具體且全面
- ❌ "建立一個網頁爬蟲"
- ✅ "建立一個使用 BeautifulSoup 的異步網頁爬蟲，從電子商務網站提取產品數據，處理速率限制，並將結果存儲在 PostgreSQL 中"

**EXAMPLES**：利用 examples/ 資料夾
- 將相關程式碼模式放入 `examples/`
- 參考特定文件和要遵循的模式
- 解釋應該模仿哪些方面

**DOCUMENTATION**：包含所有相關資源
- API 文檔 URLs
- 函式庫指南
- MCP server 文檔
- 資料庫架構

**OTHER CONSIDERATIONS**：捕捉重要細節
- 身份驗證要求
- 速率限制或配額
- 常見陷阱
- 性能要求

## PRP 工作流程

### /generate-prp 的工作原理

命令遵循以下流程：

1. **研究階段**
   - 分析您的程式碼庫以找到模式
   - 搜索類似的實現
   - 識別要遵循的慣例

2. **文檔收集**
   - 獲取相關 API 文檔
   - 包含函式庫文檔
   - 添加陷阱和特殊情況

3. **藍圖創建**
   - 創建逐步實現計劃
   - 包含驗證關卡
   - 添加測試要求

4. **品質檢查**
   - 評分信心水平（1-10）
   - 確保包含所有 context

### /execute-prp 的工作原理

1. **載入 Context**：讀取整個 PRP
2. **規劃**：使用 TodoWrite 創建詳細任務列表
3. **執行**：實現每個組件
4. **驗證**：運行測試和 linting
5. **迭代**：修復發現的任何問題
6. **完成**：確保滿足所有要求

請參閱 `PRPs/EXAMPLE_multi_agent_prp.md` 獲得產生內容的完整範例。

## 有效使用範例

`examples/` 資料夾對成功**至關重要**。AI 編程助手在能夠看到要遵循的模式時表現更好。

### 在範例中包含什麼

1. **程式碼結構模式**
   - 如何組織模組
   - import 慣例
   - 類/函數模式

2. **測試模式**
   - 測試文件結構
   - mock 方法
   - assert 風格

3. **整合模式**
   - API 客戶端實現
   - 資料庫連接
   - 身份驗證流程

4. **CLI 模式**
   - 參數解析
   - 輸出格式化
   - 錯誤處理

### 範例結構

```
examples/
├── README.md           # 解釋每個範例演示的內容
├── cli.py             # CLI 實現模式
├── agent/             # Agent 架構模式
│   ├── agent.py      # Agent 創建模式
│   ├── tools.py      # 工具實現模式
│   └── providers.py  # 多提供者模式
└── tests/            # 測試模式
    ├── test_agent.py # 單元測試模式
    └── conftest.py   # Pytest 配置
```

## 最佳實踐

### 1. 在 INITIAL.md 中明確表達
- 不要假設 AI 知道您的偏好
- 包含特定需求和限制
- 自由參考範例

### 2. 提供全面的範例
- 更多範例 = 更好的實現
- 展示該做什麼和不該做什麼
- 包含錯誤處理模式

### 3. 使用驗證關卡
- PRPs 包含必須通過的測試命令
- AI 將迭代直到所有驗證成功
- 這確保第一次嘗試就能獲得有效的程式碼

### 4. 利用文檔
- 包含官方 API 文檔
- 添加 MCP server 資源
- 參考特定文檔章節

### 5. 自訂 CLAUDE.md
- 添加您的慣例
- 包含專案特定規則
- 定義編程標準

## 資源

- [Claude Code Documentation](https://docs.anthropic.com/en/docs/claude-code)
- [Context Engineering Best Practices](https://www.philschmid.de/context-engineering)
