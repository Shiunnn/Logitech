# Logi Lab：測出你的校園生存命定裝備

Logitech 第六屆校園大使申請｜加分題互動網頁。單一 `index.html`，零依賴（不使用 CDN），可直接部署到 GitHub Pages。

## 檔案

| 檔案 | 用途 |
|---|---|
| `index.html` | 整個網站（HTML + CSS + JS） |
| `og.png` | 1200×630 社群預覽圖（Threads / LINE / FB 貼連結時顯示） |
| `企劃書_修訂版.md` | 修訂後的企劃書 |

## 部署（GitHub Pages）

```bash
git init
git add index.html og.png README.md
git commit -m "Logi Lab v1"
git branch -M main
git remote add origin https://github.com/Shiunnn/Logitech.git
git push -u origin main
```

接著到 repo 的 **Settings → Pages → Branch: main / (root)**，網址會是 `https://shiunnn.github.io/Logitech/`。

> repo 名稱如果不是 `Logitech`，記得改 `index.html` 裡的 `og:url`、`og:image`。

## 數據追蹤（建議開）

1. 到 https://www.goatcounter.com 免費註冊（例如代號 `logilab`）
2. 修改 `index.html` 的 `const ANALYTICS_ENDPOINT = 'https://logilab.goatcounter.com/count'`

會記錄的事件：`start`、`complete`、`result-{speed|eff|quiet|look}`、`copy`、`share`、`story`、`flip`、`browse-*`、`from-share-*`。送出表單時可以附上完成數和結果分布。

## 計分規則

- 每題 4 個選項，各對應 1 種屬性，選了就 +2，所以每種屬性滿分 10。
- 隨機作答的話，4 種結果的機率**都是 25%**（1024 種組合全部跑過驗證）。
- 同分處理：從 Q5 往回找，最後一個選到的同分屬性勝出（「掏錢包」題權重最高）。

## 分享機制

- `#r=speed|eff|quiet|look`：朋友點進分享連結時，會先看到分享者的結果，下面有「我也要測」按鈕。
- 限動圖：Canvas 即時產生 1080×1920 PNG，不讀外部圖片，沒有 CORS 問題。IG 內建瀏覽器無法下載時，可以長按圖片儲存。
- 複製：先試 Clipboard API，失敗改用 `execCommand`，再失敗就跳 `prompt` 讓使用者手動複製（IG 內建瀏覽器常擋 Clipboard API）。
