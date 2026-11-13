# 電輔車互動比較工具

目前版本：**1.0 版（v1.0.0）**

以繁體中文呈現折疊電輔車規格、預算與重量篩選、逐筆卡片及個人評分排行。

## 使用方式

直接以瀏覽器開啟 `index.html`，不需建置或伺服器。

- 依預算與重量篩選車款。
- 切換完整表格、逐筆卡片與評分排行。
- 調整四項 1～5 分評分，放開滑桿後依總分排序。
- 將目前篩選結果及個人評分匯出為 UTF-8 CSV。
- 以地址開啟 Google 地圖搜尋。

評分只保留於當次頁面，重新整理會恢復預設值；需要保留時請先匯出 CSV。
車款價格、規格、保固、店家與地址沿用原始資料，尚未重新查證。地圖按鈕不代表店家已確認提供展示或試乘。

## 開發與測試

需要 Node.js 及 npm。

```sh
npm ci
npx playwright install chromium
npm test
```

如使用本機 Edge，可在 PowerShell 執行：

```powershell
$env:BROWSER_CHANNEL = 'msedge'
npm test
```

測試涵蓋初始顯示、預算與重量篩選、分頁、卡片循環、地圖網址、評分與排序、CSV 編碼及內容、手機卡片顯示與 JavaScript 錯誤檢查。截圖存於 `test-results/`。

## 檔案

- `index.html`：完整的單檔網頁、樣式與資料。
- `tests/browser.cjs`：Playwright 瀏覽器測試。
- `package.json`、`package-lock.json`：測試環境與依賴。

## 修復紀錄

2026-11-13：修復 HTML 樣板字串、補齊遭截斷的 JavaScript、分頁與篩選事件、評分排行與 CSV 匯出，並修正地圖搜尋網址。
