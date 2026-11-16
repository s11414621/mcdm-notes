# AGENTS.md - MCDM 方法筆記庫開發規範

## 1. 專案目的 (Project Purpose)
本專案為「多準則決策分析（Multi-Criteria Decision Making, MCDM）方法筆記庫」，旨在以統一、結構化的網頁介面整理常見決策評估方法的核心概念、計算步驟與適用情境，方便研究查閱與後續持續擴充新方法。

## 2. 檔案結構與命名規則 (File Structure & Naming)
- 根目錄放置 `index.html`（首頁）與 `AGENTS.md`（本規範文件）。
- 樣式表統一放置於 `css/style.css`，禁止在 HTML 中寫行內樣式（inline style）或額外建立其他 CSS 檔案。
- 所有決策方法的獨立頁面一律放置於 `methods/` 資料夾內。
- 方法頁面檔名必須使用**全小寫英文縮寫**，例如：`topsis.html`、`copras.html`、`ahp.html`、`vikor.html`。

## 3. 視覺風格與樣式規範 (Visual & CSS Rules)
- 採用簡潔的學術知識庫風格：淺灰背景（`#f8fafc`）、純白內容區塊（`#ffffff`）、深藍主色調（`#1e3a8a`）與高對比文字。
- 首頁引入樣式路徑為 `css/style.css`；`methods/` 內的子頁面引入路徑一律為 `../css/style.css`。
- 禁止隨意更改既有 CSS class 名稱（如 `.container`、`.method-grid`、`.card`、`.section-box`），以確保全站版面一致。

## 4. 頁面結構規範 (Page Structure Templates)

### A. 首頁 (`index.html`)
1. **Header 區塊**：包含網站主標題與一句話專案定位說明。
2. **方法總覽網格 (`.method-grid`)**：以卡片形式列出所有已收錄的 MCDM 方法。每張卡片（`<a class="card">`）必須包含：
   - 方法類別標籤（`.badge`，如：`方案排序`、`權重計算`）
   - 方法英文縮寫與中文名稱（`<h3>`）
   - 一句話核心特色摘要（`<p>`）
   - 正確指向 `methods/<小寫檔名>.html` 的連結

### B. 方法子頁面 (`methods/<id>.html`)
每個方法頁面必須嚴格包含以下 5 個區塊，順序不可調換：
1. **頂部導覽列 (`.top-nav`)**：提供返回首頁的連結（`../index.html`）。
2. **方法標題區 (`.method-header`)**：顯示類別標籤（`.badge`）、英文縮寫與完整中文名稱。
3. **核心概念 (`<h2>1. 核心概念</h2>`)**：以 2～3 句白話說明該方法的基本邏輯與決策精神。
4. **計算步驟 (`<h2>2. 計算步驟</h2>`)**：使用 `<ol>` 有序清單條列標準計算流程（Step 1 至 Step N）。
5. **優缺點與適用情境 (`<h2>3. 優缺點與適用情境</h2>`)**：使用 `<ul>` 無序清單分別列出優點、限制與常見應用領域。

## 5. AI 新增或修改內容規則 (Rules for AI)
- **新增方法頁面時**：當使用者要求新增一個決策方法（例如：「新增 AHP 頁面」或「加入 VIKOR 方法」），AI 必須同時完成以下兩個動作：
  1. 在 `methods/` 資料夾下建立對應全小寫檔名的 HTML 檔案，嚴格套用「4-B 方法子頁面」的五段式結構與 `../css/style.css`。
  2. 同步更新 `index.html`，在 `<div class="method-grid">` 底部依照既有卡片格式新增一張對應卡片，確保首頁可點擊進入新頁面。
- **修改既有頁面時**：僅能針對文字內容進行補充或修正，不得刪除五段式區塊中的任何一項，也不得破壞相對路徑連結。
