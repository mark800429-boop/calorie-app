# 任務:食物照片熱量記錄 app 部署到 GitHub Pages

## 目前狀態(移植已完成,剩部署與測試)
- index.html:已從 Claude artifact(React JSX)移植完成的單檔版本
  - React 18 UMD + Babel standalone + Tailwind CDN,免建置直接可跑
  - window.storage 已改為 localStorage 相容層(介面不變)
  - API 改為「使用者自帶金鑰」模式:app 內有 ⚙️ 設定頁輸入金鑰,
    存 localStorage,請求帶 x-api-key + anthropic-version: 2023-06-01
    + anthropic-dangerous-direct-browser-access: true
- manifest.json:PWA 設定
- icon-180.png / icon-512.png:程式產生的暫用 icon,可之後換更好看的

## 待辦
1. 建立 GitHub repo(建議名:calorie-app),推上這四個檔案
   - GitHub 帳號:mark800429-boop(已有 stock-yield repo 的 Pages 部署經驗)
2. 開啟 GitHub Pages(main branch / root)
3. 測試清單:
   - 手機 Safari 開啟 → 加入主畫面 → 確認全螢幕(無網址列)
   - 設定頁輸入 API 金鑰 → 拍照分析一張 → 確認 JSON 解析與紀錄寫入
   - iPhone HEIC 照片(heic2any CDN fallback)
   - 月曆檢視、跨日期紀錄、刪除紀錄
4. 可選優化(之後再說):
   - Babel standalone 首次載入較慢,可改 Vite 建置消除
   - localStorage 約 5MB 上限,長期使用可把縮圖搬到 IndexedDB

## 注意
- 每位使用者的紀錄與金鑰都只存在自己手機,互不共享
- 分享方式:給網址即可,對方自行加入主畫面 + 輸入自己的金鑰
