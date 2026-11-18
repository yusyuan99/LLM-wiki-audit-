# 教學型 HTML 簡報設計與驗收規格書 (SLIDE_SPEC)

本規格書為本碩士論文文獻回顧知識庫（主題：董監事責任險 D&O 與審計報告延遲 ARL，考量董監事股權質押的調節效果）產出教學型 HTML 簡報的最高設計與驗收準則。

---

## 1. 知識來源與出處規範 (Knowledge Provenance)
- **100% 知識庫溯源**：所有簡報內容必須嚴格萃取自 `wiki/` 知識庫內容，嚴禁憑空編造數據、假說或推論。
- **頁尾強制標註出處**：每一頁投影片底部（Footer）必須清楚標示對應的 Wiki 條目名稱與原始實證文獻出處（例如：`出處：wiki/papers/2011_Lin_DO_Acquisitions.md | Lin, Officer, and Zou (2011, JFE)`）。

---

## 2. 溫潤舒適視覺風格規範 (Warm & Comfortable Visual Design)
- **護眼底色**：採用溫潤米白／淺亞麻底色（Background: `#FAF8F5` 或 `#F5F3EF`），避免純白（#FFFFFF）造成的視覺疲勞。
- **閱讀文字主色**：主內文採用深炭灰／鐵灰（Text: `#2D3142` 或 `#333745`），次要文字與標籤採用灰藍（`#5F6368`），保持對比度適中且柔和。
- **莫蘭迪色彩點綴**：
  - 重點標示/正向機制：莫蘭迪綠／鼠尾草綠（`#5C7869` 或 `#4A7C59`）
  - 警示/負向/道德風險：莫蘭迪磚紅／陶土粉（`#B85B56` 或 `#C9655D`）
  - 強調/調節效果：暖金黃／琥珀色（`#D49B55`）
  - 卡片底色：卡其乳白（`#FFFFFF` 搭配極淺陰影 `box-shadow: 0 4px 20px rgba(0,0,0,0.04)`，細邊框 `#EAE6E1`）
- **多變版面排版**：拒絕死板統一的 bullet points；靈活運用雙欄對照（Comparison Cards）、因果橫向流程圖（Process Flow）、文獻摘要卡片（Evidence Badges）與矩陣排列，保有充裕的留白（Padding & Margin）。

---

## 3. 觀念深度與文字充實度規範 (Concept Depth & Content Richness)
- **觀念聚焦**：每頁投影片聚焦 2～4 個核心觀念區塊。
- **單頁字數**：每個觀念區塊約 **100～150 個中文字**，單頁文字總量約 **250～400 個中文字**，兼具簡報可讀性與教科書級的扎實深度。
- **三段式邏輯交代**：每一核心論述均須完整交代「**前因動機 → 運作機制 → 實證結論與對本論文啟示**」。
- **舒適閱讀版式**：內文行距設定為 `line-height: 1.75～1.85`，段落間距清楚，避免文字擠壓。

---

## 4. 圖表與容器防跑版規範 (Anti-Overflow & Responsive Layout)
- **嚴格尺寸防護**：
  - 所有投影片主畫布設定標準比例（例如 `16:9`，以 `max-width: 1200px; min-height: 675px` 置中封裝）。
  - 所有圖表、卡片容器一律設定 `max-width: 100%; box-sizing: border-box;`。
- **彈性佈局**：全面採用 CSS Flexbox 與 CSS Grid 進行自適應對齊，確保文字長度增加時卡片自動均勻伸縮，文字不溢出、不重疊、不被裁切。
- **字體層級規範**：標題（`28px～32px`）、區塊副標（`18px～22px`）、內文（`14px～16px`）、頁尾引註（`11px～12px`）。

---

## 5. 初學者教學節奏 (Pedagogical Flow)
整份簡報循序漸進引導讀者掌握論文核心脈絡：
1. **封面 (Title)**：研究題目、研究背景與核心變數。
2. **破題白話比喻 (Intuitive Metaphor)**：用生活化案例（保全顧問 vs 防彈背心、抵押房契的賭徒）建立直覺。
3. **兩大對立理論基石 (Theories in Conflict)**：外部監督假說 vs 道德風險／壕溝假說。
4. **核心機制深入剖析 (Mechanisms)**：D&O 如何影響查核會計師決策與審計報告延遲（ARL）。
5. **調節變數關鍵作用 (Moderating Effect)**：董監質押（PLEDGE）在台灣市場的特殊成因與加乘風險。
6. **5 篇文獻實證檢驗 (Empirical Evidences)**：逐篇檢視林琛 (2011)、Yuan et al. (2016)、O'Sullivan (1997)、Chalmers et al. (2002)、高蘭芬 et al. (2004) 的假說與實證結果。
7. **台灣法規背景與制度意涵 (Taiwan Institutional Background)**：公司法第193條之1與第197條之1。
8. **總結與研究假說推導 (Synthesis & Hypotheses Development)**：碩論 H1 與 H2 的理論建構與研究缺口填補。

---

## 6. 技術交付標準 (Technical Delivery)
- **單一交付檔案**：`output/presentation.html`，純原生 HTML/CSS/JavaScript，零外部 CDN 依賴，本機雙擊即可流暢開啟。
- **互動控制功能**：
  - 支援鍵盤左／右方向鍵（`ArrowLeft`, `ArrowRight`）切換頁面。
  - 畫面右下角提供「上一頁（Prev）」、「下一頁（Next）」實體按鈕。
  - 正上方或右下角即時顯示頁碼（如 `Page 3 / 9`）與進度條（Progress Bar）。
