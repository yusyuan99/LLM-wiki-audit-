# AGENTS.md - 董監事責任險（D&O）與審計報告延遲文獻回顧知識庫規範

本知識庫遵循 Andrej Karpathy 的 **LLM Wiki** 模式，專為碩士論文文獻回顧章節打造。
知識庫的核心研究主題為：**董監事責任險（Directors' and Officers' Liability Insurance, D&O）與審計報告延遲（Audit Report Lag, ARL），並考量董監事股權質押比例（Director & Officer Share Pledging）的調節效果（Moderating Effect）**。

---

## 1. 核心原則與規範

1. **語言與術語**：
   - 內文解析與討論一律使用**繁體中文（台灣學術與實務習慣用語）**。
   - 專有名詞、理論名稱、變數名稱（Variables）、模型縮寫及論文英文標題**務必保留英文原文或以中英對照呈現**（例如：Audit Report Lag (ARL)、Directors' and Officers' Liability Insurance (D&O)、Director Share Pledging (PLEDGE)、Managerial Entrenchment Hypothesis、Moral Hazard、Monitoring Hypothesis、Two-Stage Least Squares (2SLS) 等）。
2. **台灣法規特別強調**：
   - 強調台灣法律規範與實務背景（例如：公司法第193條之1董監責任險條款、證券交易法、金管會推動公司治理藍圖/評鑑、投保金額揭露規範、公開發行公司董監質押超過選任時持股半數之表決權限制等）。
3. **持之以恆的知識複利（Compounding）**：
   - Wiki 不是單純的摘要堆疊，而是互聯的論文庫。每攝入一篇論文，除了摘要單篇外，**必須主動更新關聯的概念頁、機制頁、調節變數頁與矛盾爭議矩陣**。

---

## 2. 目錄架構

```text
LLM Wiki/
├── raw/                      # 原始文獻層（由上傳的 PDF 轉出之 Markdown 全文/詳細筆記，唯讀不可篡改）
│   └── papers/               # 命名：[年份]_[第一作者姓氏]_[核心關鍵詞].md
├── wiki/                     # 維基衍生層（LLM 完全維護，全雙向鏈結 [[PageName]]）
│   ├── papers/               # 單篇論文結構化解構頁面
│   ├── theories/             # 理論基礎（如：代理理論、壕溝假說、外部監督假說、道德風險、資訊不對稱）
│   ├── mechanisms/           # 核心因果機制與主題（如：D&O 與 ARL、D&O 與 審計風險/審計公費、審計定價）
│   ├── moderators/           # 調節變數分析（特別是：董監股權質押 Share Pledging、家族企業控制、董事會獨立性）
│   ├── taiwan_regulations/   # 台灣法規環境與實務制度（公司法、證交法、公司治理評鑑要求、質押規範）
│   ├── methodology/          # 實證方法與變數衡量（ARL 衡量、D&O 衡量指標、內生性處理如 2SLS/Heckman/PSM/DID）
│   └── synthesis/            # 論文第二章文獻回顧合成稿、假說推導草稿與比較矩陣
├── assets/                   # 圖表、概念架構圖（未來 HTML 簡報用）
├── index.md                  # 全知識庫目錄索引（依分類列出所有 Wiki 頁面與一頁摘要）
├── log.md                    # 變更與操作日誌（追加式紀錄每一次文獻攝入、查詢與 Lint）
└── AGENTS.md                 # 本系統規範指南（Schema）
```

---

## 3. 三大操作流程（Workflows）

### 流程一：文獻攝取（Ingest Workflow）
當使用者上傳新論文 PDF 或提供文獻時，Agent 執行以下 SOP：

1. **轉換與落盤至 `raw/papers/`**：
   - 提取論文文字並轉為結構化 Markdown，檔名規則：`YYYY_Author_Keywords.md`（例如：`2020_Chen_DO_AuditDelay.md`）。保留完整實證結果與數據表。
2. **建立單篇結構化解構頁至 `wiki/papers/`**：
   - 必須包含以下標準 YAML Frontmatter 與段落（參考第 4 節範本）。
3. **知識交叉回饋與雙向鏈結（Compounding & Cross-referencing）**：
   - **更新理論頁（`wiki/theories/`）**：本篇支持哪種理論假說？（例如支持 `[[壕溝假說]]` 還是 `[[外部監督假說]]`？將該篇的實證結果簡要追加至該理論頁）。
   - **更新核心機制頁（`wiki/mechanisms/`）**：本篇如何解釋 D&O 對 ARL 或審計師行為的影響？（支持顯著正向、顯著負向、抑或不顯著？）。
   - **更新調節變數頁（`wiki/moderators/`）**：若有探討董監股權質押（Share Pledging）或治理結構，立即更新 `[[董監質押對ARL的調節效果]]`。
   - **更新衝突與爭議矩陣**：若實證結果與既有文獻不同，記錄其樣本特徵與可能的潛在原因（如國家、法規環境差異）。
4. **更新索引與日誌**：
   - 在 `index.md` 加入該文獻與新增頁面連結。
   - 在 `log.md` 新增一行標準紀錄（例如：`## [2026-11-18] ingest | 2020_Chen_DO_AuditDelay`）。

---

### 流程二：回顧查詢與合成（Query & Synthesis Workflow）
當使用者進行文獻探討、推導假說或撰寫第二章段落時：

1. **跨頁面檢索與整合**：
   - 優先讀取 `index.md`，調閱相關的 `theories/`、`mechanisms/` 與 `moderators/` 頁面。
2. **產出結構化文獻比較**：
   - 包含實證文獻整理表格（包含：作者年份、研究樣本與國別、D&O 衡量方式、質押衡量方式、實證結論、內生性處理）。
   - 撰寫學術風格之假說推導論述（Hypothesis Development：H1a 正向 vs H1b 負向；H2 質押之調節效果）。
3. **沉澱回 Wiki**：
   - 若生成的文獻回顧或比較矩陣具長期參考價值，存入 `wiki/synthesis/`（例如：`wiki/synthesis/假說推導草稿_H1與H2.md`），使成果累積不遺失。

---

### 流程三：知識庫健檢（Lint Workflow）
定期檢查知識庫品質：
- 檢查是否有孤島頁面（Orphan Pages，未被任何頁面或 index.md 鏈結）。
- 檢查專有名詞是否前後一致（例如統一使用 Audit Report Lag 而非混用不同簡稱）。
- 檢查是否有未建立概念頁的核心概念。
- 指出當前文獻庫的 **研究缺口（Research Gaps）**，建議下一步應搜尋或補充的文獻面向。

---

## 4. 單篇論文 Page 標準範本（Template）

在 `wiki/papers/YYYY_Author_Keywords.md` 應遵循此格式：

```markdown
---
title: "[英文論文完整標題]"
authors: "[作者群]"
year: YYYY
journal: "[期刊名稱 (Volume/Issue)]"
sample: "[研究樣本國別、市場、年份區間，如：台灣上市櫃公司 2008-2022]"
core_variables:
  dependent: "Audit Report Lag (ARL)"
  independent: "D&O Insurance (投保與否/投保額度/保費率)"
  moderator: "Director Share Pledging (質押比率)"
theories: ["[[代理理論]]", "[[壕溝假說]]", "[[道德風險假說]]"]
empirical_result: "D&O 與 ARL 呈現[顯著正向/顯著負向/U型]，且[質押變數]具有顯著調節效果"
---

# [英文論文完整標題]

## 1. 研究問題與動機 (Research Questions & Motivation)
- 研究背景與核心切入點
- 研究主要貢獻

## 2. 理論基礎與假說推導 (Theoretical Background & Hypotheses)
- 採用的核心理論（例如：[[壕溝假說]]、[[監督假說]]）
- 提出的假說：
  - H1: ...
  - H2 (調節效果): ...

## 3. 實證研究設計 (Research Design)
- **樣本與資料來源**：
- **主要變數定義**：
  - 被解釋變數 (DV)：
  - 解釋變數 (IV)：
  - 調節變數 (Moderator)：
  - 主要控制變數 (Controls)：
- **實證模型 (Empirical Model)**：
- **內生性問題處理 (Endogeneity Treatments)**：（如 2SLS, Heckman, PSM, Fixed Effects 等）

## 4. 實證結果與核心發現 (Empirical Findings)
- 主迴歸分析結果：
- 調節效果分析（若有）：
- 穩健性檢定 (Robustness Checks)：

## 5. 與本碩士論文主題的關聯與啟示 (Relevance to Master Thesis)
- 對本論文 H1（D&O 與 ARL）之啟示：
- 對本論文 H2（董監質押之調節效果）之啟示：
- 值得借鏡的控制變數或模型設定：

## 6. 關聯維基頁面 (Cross-References)
- 理論：[[代理理論]]、[[壕溝假說]]
- 機制：[[D&O與審計報告延遲機制]]
- 調節：[[董監股權質押的治理效應]]
- 法規：[[台灣董監事責任險發展與法規背景]]
```

---

## 5. Log 紀錄標準規範

`log.md` 的所有新增紀錄必須嚴格遵循以下格式：
`## [YYYY-MM-DD] [操作類型] | [主題或檔案名稱]`
操作類型包含：`ingest`、`query`、`synthesis`、`lint`。
下方附帶 1~2 行簡要異動或新增內容說明。
