# 發票轉報稅 Excel

上傳電子發票照片 → 自動辨識 → 下載可匯入報稅軟體的 Excel。純前端、單一檔案（`index.html`），不需要後端。

## 部署到 GitHub Pages

1. 在 GitHub 建立新的 repository（例如 `invoice-app`）
2. 把 `index.html` 和 `README.md` 上傳到 repository 根目錄
3. 到 **Settings → Pages**，Source 選 **Deploy from a branch**，Branch 選 `main`、資料夾 `/ (root)`，按 Save
4. 約 1 分鐘後，網址為 `https://<你的帳號>.github.io/invoice-app/`

> 建議把 repository 設為 Private（GitHub Pages 的私有 repo 需付費方案），或確認程式碼內沒有公司機密。固定設定（稅籍代號等）預設值寫在 `index.html` 的 `DEF` 物件，公開 repo 請改掉或留空，改在網頁上輸入（只存在該裝置的瀏覽器）。

## 辨識方式

1. **QR Code（預設，免費）**：電子發票左側 QR Code 內含發票號碼、日期、銷售額、總額、買賣方統編，直接解碼，最準確。稅額 = 總額 − 銷售額。
2. **Claude AI（備援）**：QR 拍不清楚時使用，需在「AI 備援設定」填入自己的 Anthropic API Key。Key 只存在瀏覽器 localStorage，**請勿寫進程式碼或上傳到 GitHub**。

## 使用提示

- 拍照時 QR Code 要清楚、不反光、不要被手指或其他發票遮住
- 年月依發票開立日期自動歸類，項次依年月與日期排序後從 `0000001` 遞增
- 表格內的紅字會提示可能的問題（統編/字軌/號碼格式、買方統編不符、重複發票、稅額不是 5%）
- 匯入報稅軟體前，請務必核對一次

## Excel 欄位順序（固定）

格式代號、稅籍代號、項次、年月、買受人統一編號、廠商統一編號、字軌、發票號碼、金額、扣抵代號、稅額、課稅別
