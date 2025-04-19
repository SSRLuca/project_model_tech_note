# 📌 專案名稱：XXX系統

## 🗓️ 專案期間
2023 年 5 月 ～ 2024 年 3 月

## 👤 我的角色
後端軟體工程師 / 全端工程師（請選擇或修改）

## 🛠️ 使用技術
- C#
- ASP.NET WebAPI
- iTextSharp（PDF 處理）
- Vue.js（前端框架）
- JavaScript、HTML、CSS
- SQL Server / Oracle
- Git、Postman、Fiddler

## 📄 專案描述
此系統提供企業用戶在網頁上簽署 PDF 文件的功能，主要功能包含：
- 顯示 PDF 預覽並指定簽署位置
- 使用者可拖曳簽名圖片至 PDF
- 系統後端接收簽名圖片與座標資訊後合併到 PDF 檔案中
- 檔案可直接下載或發送到指定信箱
- 支援權限控管（主管、代理人簽名）

## 🔧 我的主要工作內容
- 設計 API 接收前端傳來的簽署資訊（圖片座標、頁碼等）
- 使用 iTextSharp 將圖片簽名合併至 PDF 對應頁面與位置
- 處理 PDF 多頁簽名合併的邏輯與效能優化
- 撰寫前端 Vue 元件與後端 API 串接測試
- 處理檔案上傳、下載、與前端 canvas 座標轉換
- 配合 Fiddler / Postman 進行除錯與測試

## 💡 解決的困難與經驗收穫
- **圖片與 PDF 座標轉換問題**：前端傳來的是像素（px），但 iTextSharp 使用的是 point（pt），需進行轉換並考慮 DPI。
- **PDF 多次合併效能問題**：使用 MemoryStream 與非同步處理方式降低資源佔用。
- **多人簽名順序管理**：建立簽名流程狀態欄位，控管簽署順序與權限。

## 🖼️ 補充資料（選填）
- 可附上畫面截圖（如有）
- 可附上簡化的程式碼片段（如核心邏輯）
```csharp
using (PdfReader reader = new PdfReader(inputPath))
using (PdfStamper stamper = new PdfStamper(reader, new FileStream(outputPath, FileMode.Create)))
{
    PdfContentByte canvas = stamper.GetOverContent(pageNumber);
    iTextSharp.text.Image img = iTextSharp.text.Image.GetInstance(imageBytes);
    img.SetAbsolutePosition(x, y);
    img.ScaleAbsolute(width, height);
    canvas.AddImage(img);
}
