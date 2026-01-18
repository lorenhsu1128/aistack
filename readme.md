## Google Antigravity 安裝指南

以下是安裝 Google Antigravity 的詳細步驟：

### 1. 下載安裝程式

前往官方網站下載對應作業系統的版本：

* **官方網址：** `antigravity.google/download` (或 `antigravity.google`)
* **支援平台：** Windows, macOS, Linux
* **注意：** 下載時請選擇與您系統架構相符的版本（例如 Windows x64 或 Mac Apple Silicon）。

### 2. 安裝步驟 (Windows/Mac/Linux)

#### Windows

1. 執行下載的 `.exe` 安裝檔。
2. 按照螢幕提示進行安裝（通常只需點擊 "Next"）。
3. **WSL2 使用者注意：** 安裝過程中若詢問是否加入 PATH，建議勾選。安裝完成後，您可以在 WSL2 終端機中輸入 `antigravity .` 來在該目錄啟動 IDE（指令類似 `code .`）。

#### macOS

1. 打開下載的 `.dmg` 檔案。
2. 將 **Google Antigravity** 圖示拖曳到 **Applications** 資料夾中。
3. 首次開啟時若出現安全性提示，請點選「Open」。

### 3. 初次設定精靈 (Initial Setup)

首次啟動時，Antigravity 會進入設定引導流程：

1. **選擇設定來源 (Setup Flow)：**

* **Start Fresh：** 全新開始。
* **Import from VS Code：** 既然它是基於 VS Code 构建的，您可以直接匯入原本 VS Code 的按鍵綁定 (Keybindings)、擴充套件和設定。這對習慣原本開發環境的您最方便。

1. **選擇主題 (Theme)：** 預設提供 Dark, Light, Tokyo Night 等選項。
2. **登入 Google 帳號：** 必須登入 Google 帳號以啟用 Gemini 3 模型服務（預覽版期間通常是免費或包含在 Google One/Workspace 額度內）。

### 4. 關鍵擴充套件設定 (針對 Python 開發)

雖然 Antigravity 內建強大的 AI，但為了讓 Python 開發更順暢，建議手動確認以下設定：

* **安裝 Python Extension：** 進入擴充套件市場 (Extensions)，搜尋並安裝 Microsoft 的 `Python` 插件（如果沒有從 VS Code 匯入的話）。
* **推薦 BasedPyright：** 社群建議安裝 `BasedPyright` 來獲得比預設 Pylance 更快、更準確的型別檢查，特別是在處理 `tensorflow` 或 `torch` 這類大型庫時。
* 在擴充市場搜尋 `BasedPyright` (Publisher: DetachHead) 並安裝。
* 在設定 (`settings.json`) 中加入 `"python.languageServer": "None"` 以避免衝突。

### 5. 安裝瀏覽器代理擴充 (Browser Extension)

這是 Antigravity 最強大的功能之一，允許 AI 直接控制瀏覽器進行測試。

1. 在 Antigravity 中開啟一個專案，AI Agent 可能會提示您需要安裝瀏覽器擴充。
2. 或者直接在 Chrome 線上應用程式商店搜尋 **"Google Antigravity Browser Extension"**。
3. 安裝後，確保給予擴充套件 "Allow in Incognito" (若需要) 或必要的權限，這樣 AI 才能在您寫網頁應用（如 Flask/Django/FastAPI）時自動打開瀏覽器測試功能。

### 6. 驗證安裝

1. 開啟 Antigravity。
2. 按下 `Ctrl+Shift+P` (或 Cmd+Shift+P) 開啟命令列。
3. 輸入 `Antigravity: Open Agent Manager`。
4. 在右側 Agent 面板輸入一個簡單指令，例如：「建立一個 Python script 打印 Hello World 並執行它」。
5. 如果 IDE 自動建立了檔案並在終端機執行成功，代表安裝完成。

---

## Google Antigravity 快速上手

### 1. 軟體介紹與 Vibe Coding 概念

* **Google Antigravity**：Google 推出的 AI 開發工具，核心亮點是 **免費**，且可免費使用 Gemini 和 Claude 等強大模型
* **Vibe Coding (氛圍編碼)**：一種「意念驅動」的開發方式。你只需扮演產品經理的角色，提出想法和需求，由 AI（你的 24 小時待命程式設計師）負責架構、寫代碼和除錯。你只需關注最終成品是否滿意。

### 2. 安裝與初始化設置

* **下載與安裝**：從官網下載安裝。如果是 Windows 用戶且非管理員權限，遇到提示直接點確定即可。
* **初始設置嚮導**：
* **導入設置**：建議選擇「全新開始」以避免舊配置干擾。
* **AI 權限 (關鍵)**：Antigravity 需要執行終端命令、文件操作和瀏覽器 JS 命令。建議在學習階段選擇 **「Always Allow (總是允許)」** 或全自動模式，避免 AI 每做一步都要你確認，影響 Vibe Coding 的流暢度。
* **鍵盤模式**：建議選擇 **「Standard (常規模式)」** 而非 Vim 模式，因為 Vim 模式容易與 AI 的自動補全功能衝突。

### 3. 基礎操作與界面

* **Tab 智能補全**：AI 會預測你的意圖。例如修改變量命名風格，AI 會自動識別並建議修改其他相關變量，按 Tab 鍵即可採納。這不僅限於代碼，也適用於文檔排版（如縮進、序號）。
* **AI 對話框操作**：
* **@ 符號**：引用特定文件或上下文發送給模型。
* **/** (斜線)：調用自定義工作流 (Workflow) 或命令。
* **Ctrl+I**：調出臨時 AI 窗口，對選中的代碼進行修改或提問。
* **Ctrl+L**：將選中內容添加到右側對話框。
* **Ctrl+K S**：一次性保存所有已修改的文件。

### 4. 核心功能配置

* **Rules (系統提示詞)**：
* 可在 `Agent` -> `Customization` -> `Rules` 中設置。
* 分為 **全局 (Global)** 和 **項目級 (Project)**。
* 建議設置：要求 AI 始終使用中文回覆、定義文件路徑習慣等。

---

#### 4.1. 我的全局 (Global) Rules

1. **核心語言原則**
    * 語言設定：所有的思考過程、註釋、聊天回應以及任務介面（包含任務名稱、狀態、摘要）都必須使用繁體中文。
    * 產出物 (Artifacts)：生成的文檔（如 task.md、實作計畫等）其內文必須使用繁體中文撰寫。但在程式碼區塊中的檔案名稱與變數名稱應保留為英文。

2. **程式碼品質**
    * 程式碼必須包含清晰的繁體中文註解，解釋複雜邏輯。
    * 修改程式碼前，請先閱讀現有的程式碼風格，並保持一致性。
    * PEP 8 風格：確保所有 Python 程式碼都符合 PEP 8 風格指南。
    * 單元測試：為每個檔案和每個方法生成單元測試。
    * 測試命名：確保單元測試檔名與原檔案相似，但加上 test_ 前綴。
    * 執行進入點：在腳本中始終包含 `if __name__ == "__main__":`區塊。

3. **工作流程**
    * 規劃模式：對於複雜任務、研究或架構設計，請務必先產出一份完整的 implementation_plan.md（實作計畫）。
    * 快速模式：對於簡單任務（如重新命名、小修正），直接執行，無需產生過多的規劃文檔。
    * 遇到錯誤時，不要盲目嘗試修復；請先分析錯誤訊息，並解釋原因後再行動。
    * Python專案必須使用 `uv` 進行函式庫依賴管理與執行腳本。
    * 安装函式庫：使用命令 `uv add <package_name>`，如果不行採用 `uv pip install <package_name>` 安装
    * 執行腳本：使用命令 `uv run python <script_name>`

4. **深度思考模式 (Cognitive Protocol)**
    * 思維鏈 (Chain of Thought)：在處理複雜任務或編寫核心邏輯前，請先輸出一個 `### 思考過程` 區塊。
        * 分析技術難點。
        * 預判可能的邊緣情況（Edge Cases）。
        * 評估對現有架構的影響。

5. **安全性與權限 (Security Protocol)**
    * 憑證安全：絕對禁止在程式碼中硬編碼（Hardcode）任何 API Key 或密碼。
        * 必須使用環境變數（`.env`）讀取。
        * 如果發現缺少必要的金鑰，請立即暫停並詢問我，不要自行填寫假資料。
    * 危險指令攔截：在執行任何具破壞性的終端機指令（如 `rm -rf`、`sudo`、修改系統權限）之前，**必須**先獲得我的明確「允許」。
    * 範圍限制**：嚴禁修改當前專案資料夾以外的任何檔案。

6. **自我紅隊測試 (Self-Correction)**
    * 在產出最終程式碼前，請先進行自我審查。
        * 這段程式碼有效率嗎？（例如：避免不必要的 O(n^2) 迴圈）
        * 是否符合 DRY (Don't Repeat Yourself) 原則？
        * 是否遺漏了錯誤處理（Try-Catch）？

7. **技術棧規範 (Tech Stack Rules)**
    * Python 開發：
        * **型別提示**：所有函式定義必須包含 Type Hints (例如 `def my_func(a: int) -> str:`)。
        * **現代化工具**：優先使用 `uv` 進行依賴管理，而非單純的 `pip`。
        * **錯誤處理**：不要只寫 `pass`；捕捉異常時必須記錄 Log 或印出錯誤訊息。
    * Flutter 開發：
        * **Widget 結構**：優先將複雜的 UI 拆分為獨立的小型 Widget，避免單一檔案超過 300 行。
        * **狀態管理**：清楚說明將使用哪種狀態管理（Provider, Riverpod, Bloc），並保持一致。
        * **Null Safety**：嚴格遵守 Null Safety 規範，避免使用 `!` 強制解包，除非你 100% 確定。
    * Mermaid & 文件化：
        * **視覺化解釋**：當解釋複雜的系統流程或資料流向時，**主動**生成 Mermaid 流程圖或時序圖來輔助說明。
        * **圖表代碼**：請將 Mermaid 代碼包在 markdown code block 中，方便預覽。

---

### 5. 進階功能：MCP 與 Workflow

* **使用MCP Server前需要先安裝docker**，<https://www.docker.com/products/docker-desktop/> ，安裝完並啟動。如果是 Windows11 在安裝時可選擇 Use WSL 2 instead of Hyper-V (recommended)`。
* 可在 `Agent` -> `MCP Servers` 中設置。
* **MCP (Model Context Protocol) 工具**：
* **用途**：讓 AI 連接外部工具。
* **實例 - 上傳到 Git搜尋 Github
  * 在 MCP Server 商店安裝 **GitHub** 工具。
  * 去 GitHub 設置頁面生成 Personal Access Token (需勾選 repo 相關權限)。
    * <https://github.com/settings/tokens/new>
    * 建議只勾選 repo 相關權限
      * Administration、Commit statuses、Contents、Issues、Metadata。
  * 將 Token 填入 Antigravity 的配置中（需確保 Docker 已開啟，因為 MCP 運行在 Docker 上）。
  * 在對話中用 `@GitHub` 調用工具，讓 AI 自動創建倉庫並上傳代碼。

* **Workflow (工作流) 自動化**：
* 可以將常用動作（如「生成繁體中文 README」、「Git 初始化」）設置為 Workflow。
* 設置後，通過 `/` 命令即可一鍵觸發這些複雜的動作序列。
