# 投資組合追蹤系統 Portfolio Tracker

一個純前端的股票 / 基金投資組合追蹤網頁，不需要後端伺服器，資料存於瀏覽器 localStorage。

## 功能

- 📈 **即時股價更新** — Yahoo Finance v7 API（支援台股、美股、ETF）
- 🏦 **MoneyDJ 基金報價** — 透過 IMPORTXML 方式抓取共同基金淨值
- 📊 **Dashboard** — 資產分配圓餅圖、市場配置圖、持倉排行
- ✏️ **CRUD 操作** — 新增、編輯、刪除持倉
- 🔃 **拖曳排序** — 同市場內自由調整顯示順序
- 💱 **匯率換算** — 自動取得 USD/TWD 匯率
- 📁 **匯入 / 匯出** — JSON 格式備份與還原

## 本地開發

```bash
# 啟動本地伺服器（macOS）
python3 -m http.server 3000
# 開啟 http://localhost:3000
```

## 線上版本

部署於 GitHub Pages，每次 push 到 `main` 後自動更新。

## CI/CD

| 觸發 | 動作 |
|------|------|
| push / PR → `main` | HTML 驗證 |
| push → `main` | 部署至 GitHub Pages |

## 持倉資料格式

```json
{
  "id": 1,
  "market": "台股",
  "symbol": "2330",
  "yahoo": "2330.TW",
  "name": "台積電",
  "shares": 100,
  "currency": "TWD",
  "price": 850,
  "priceDate": "2025-01-01",
  "note": "",
  "target": 10,
  "moneydj": ""
}
```

### MoneyDJ 基金格式
`moneydj` 欄位填入 `URL::XPath`，等同 Google Sheets 的 `=IMPORTXML("URL", "XPath")`。
