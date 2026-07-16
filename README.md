# CLIP ViT-B/32 智能食物辨識（純 HTML）

這個網頁使用 Transformers.js 和 `Xenova/clip-vit-base-patch32` 進行零樣本影像分類，
毋須 Python 後端，也毋須自行訓練模型。

最新版 Word 清單的 156 項資料已直接內置於 `index.html`。其中155個可從外觀辨認的
食品會在同一次 CLIP 運算中直接比較，避免第一層分類錯誤後停止。網頁會顯示三個中文
候選結果及真正可按的確認按鈕；使用者確認後，結果也會在瀏覽器中保存。隔夜餸應按
存放時間判斷，不會交由相片模型猜測。

## 在電腦測試

```bash
cd clip_food_html
python3 -m http.server 8000
```

在 Chrome 開啟 <http://127.0.0.1:8000>。第一次使用需要連線下載 Transformers.js
及量化 CLIP 模型，之後瀏覽器會快取模型檔案。

## 放到 GitHub Pages

把 `index.html` 和 `.nojekyll` 上載到儲存庫，然後在 GitHub Pages 發佈 `main`
分支的根目錄。用 iPhone 開啟 GitHub Pages 網址後，可拍照或從相簿選擇食物照片。

注意：CLIP 的相似度不能判斷食物是否安全、新鮮或真正存放過夜；到期日期仍需由包裝日期、
使用者輸入或另一套日期辨識功能提供。
