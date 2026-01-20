---
description: 將選定的程式碼邏輯轉換為 Mermaid 流程圖
---
1. 邏輯提取：分析選取的程式碼區塊或檔案。識別主要的控制流程（if/else, loops, function calls）。
2. 生成圖表：生成一段 Mermaid `flowchart TD` 或 `sequenceDiagram` 代碼。使用繁體中文標註節點名稱。
3. 寫入文件：檢查當前目錄是否有 `DESIGN.md`。如果沒有則建立。將生成的 Mermaid 代碼插入到文件中，並用 Markdown code block 包裹。
