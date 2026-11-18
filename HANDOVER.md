# 專案交接文件 (HANDOVER.md)

本文件記錄「我的網頁作品集 (`myworks`)」的專案架構、維護規範、歷史變更與日後擴充 SOP，供後續接手開發或 AI 協作參考。

---

## 1. 專案基本資訊

- **專案名稱**：我的網頁作品集 (My Web Portfolio)
- **GitHub 儲存庫**：`https://github.com/marco19790512/myworks`（Public / `main` 分支）
- **技術架構**：純前端靜態網站（HTML5 + Tailwind CSS CDN + FontAwesome CDN + Vanilla JavaScript），無須建置步驟（Zero-build），本機雙擊 `index.html` 或透過 GitHub Pages 即可運行。
- **目前收錄作品總數**：**42 件**
  - `apps/`（應用系統）：12 件
  - `games/`（互動遊戲）：6 件
  - `tools/`（實用工具）：7 件
  - `about/`（個人簡介）：5 件（含 1 網頁、4 圖表/頭像）
  - `art/`（藝術創作）：4 件
  - `idea/`（商業構想）：5 件
  - `assets/`（設計規範）：1 件（另有 `assets/previews/` 存放 27 張示意圖）
  - `music/`（音樂音訊）：1 件
  - `videos/`（影音短片）：1 件

---

## 2. 首頁 (`index.html`) 示意圖自動對應機制

`index.html` 中的 `renderProjects()` 會依據 `projects` 陣列內每個項目的 `type` 與 `path` 自動決定卡片頂部 16:9 預覽圖：

| `type` | 預覽圖來源規則 | 說明 |
| :--- | :--- | :--- |
| `"web"` | `assets/previews/<檔名不含.html>.svg` | 讀取專屬向量 UI 示意圖；點擊直接開新分頁開啟該網頁 |
| `"image"` | 直接使用 `p.path` | 顯示原圖縮圖；點擊開啟 Lightbox 高畫質預覽 |
| `"audio"` | `assets/previews/champagne-gold-afternoon-audio.svg` | 顯示專屬黑膠/聲波封面；點擊開啟內建音訊播放器 |
| `"video"` | `<video src="${p.path}#t=1" preload="metadata" muted>` | 顯示影片第 1 秒定格畫面與播放按鈕；點擊開啟影片播放器 |

> **⚠️ 注意**：所有 `type: "web"` 作品的 `.html` 檔名（不含副檔名）必須與 `assets/previews/` 內的 `.svg` 檔名完全一致，否則首頁卡片會破圖。

---

## 3. 日後新增 / 移除作品標準作業流程 (SOP)

### 新增作品時：
1. **命名與歸類**：將檔案以英文 `kebab-case` 命名，放入對應分類資料夾（`apps/`、`games/`、`tools/`、`about/`、`art/`、`idea/`、`assets/`、`music/`、`videos/`）。
2. **製作示意圖**（若為網頁或音訊）：於 `assets/previews/` 新增對應同名的 `.svg` 示意圖。
3. **更新 `index.html`**：
   - 在 `projects` 陣列對應分類區塊新增項目物件。
   - 更新頂部導覽列總數（`共收錄 XX 件數位創作與專案`）。
   - 更新 Hero 統計卡片數字（Apps / Games / Tools / 簡介創作與多媒體）。
   - 更新分類篩選按鈕括號內的數量（`(XX)`）。
4. **更新文件並推播**：同步更新 `README.md` 與本交接檔，執行 `git add .`、`git commit`、`git push origin main`。

### 移除作品時：
1. 使用 `git rm` 移除該作品檔案（及對應的 `assets/previews/<slug>.svg`）。
2. 同步移除 `index.html` 的 `projects` 項目並下修各處統計數字。
3. 更新 `README.md` 與本交接檔並 Push 至 GitHub。

---

## 4. 近期變更紀錄 (Changelog)

### 2026-11-18 — 全站作品首頁示意圖升級
- 為全數 42 件作品製作／配置首頁 16:9 視覺預覽。
- 於 `assets/previews/` 新增 **27 張專屬向量 SVG 示意圖**（涵蓋 26 個 HTML 作品與 1 個 MP3 封面）。
- 更新 `index.html` 卡片排版，加入懸停放大動畫、浮動分類/圖示徽章與點擊縮圖直接預覽/開啟功能。
- 建立本交接文件 `HANDOVER.md`。

### 2026-11-15 — 清理特定項目
- 移除 `apps/global-snack-group-buying-order-form.html` 與 `about/marco-tseng-consultant-profile.html`。
- 總數更新為 42 件，同步更新 `index.html` 與 `README.md` 並 Push。

### 2026-11-14 — 新增兩項 AI / 互動應用
- 加入 `apps/attention-magic-adventure.html`（注意力魔法大冒險）。
- 加入 `apps/ai-video-vibe-coding-trends-dashboard.html`（2026 AI 影片製作 Vibe Coding 決策儀表板）。

### 2026-11-09 — 專案初始化、頭像整合與 GitHub 上線
- 完成 `c:\myworks` 全檔案英文命名與 9 大分類歸檔。
- 建立 `index.html`（以 `about/cozy-creative-desk-diorama.png` 作為個人頭像）、`README.md`、`.gitignore`。
- 初始化 Git `main` 分支並 Push 至 GitHub 公開儲存庫。
