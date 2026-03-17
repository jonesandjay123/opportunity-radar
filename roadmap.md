# Opportunity Radar — Roadmap

## 🎯 目標

建一台「每天幫 Jones 變有錢一點點的系統」。

## 📅 Phase 1 — Pipeline MVP（當前）

**目標：** 每天自動產出 5 個結構化機會，品質夠讓 Jones 願意花 5 分鐘看。

| 項目 | 狀態 | 說明 |
|------|------|------|
| JSON schema | ✅ | opportunity + deepdive |
| Repo 骨架 | ✅ | data/ + schema/ + README |
| 訊號來源 v1 | 🔜 | Reddit（r/Entrepreneur, r/smallbusiness, r/SideProject 等） |
| LLM 分析 prompt | 🔜 | 結構化輸出 + 打分 + 強制篩選 |
| CRON job | 🔜 | OpenClaw cron, 每日一次 |
| 第一份真實 Brief | 🔜 | 手動跑一次驗證品質 |
| Jones review | 🔜 | 確認有靈氣 → 自動化 |

## 📅 Phase 2 — Dashboard

**目標：** Jones 可以在網頁上瀏覽、星號、留言、排序。

| 項目 | 狀態 | 說明 |
|------|------|------|
| Firestore 同步 | 📋 | JSON → Firestore |
| 簡單 UI | 📋 | Vite + React + Firebase |
| 星號 + 留言 | 📋 | 跟 Trip Planner 類似 |
| 篩選 + 排序 | 📋 | 依分數 / 日期 / 狀態 / 類別 |

## 📅 Phase 3 — Deep Dive Agent

**目標：** Jones 選了一個機會後，自動做背景調查。

| 項目 | 狀態 | 說明 |
|------|------|------|
| 競品搜索 | 📋 | 自動找類似產品/服務 |
| 使用者語錄 | 📋 | 從 Reddit/論壇抓真實抱怨 |
| 市場估算 | 📋 | 粗估 TAM/SAM |
| Action 建議 | 📋 | 不自動執行，需 Jones 批准 |

## 📅 Phase 4 — Multi-Agent（未來）

**目標：** 多個 agent 分工，pipeline 自動化。

- 不同 stage 由不同 agent 負責
- schema 欄位 `assignedTo` 支援任意 agent
- 半自動驗證和行動執行

## 🧠 設計決策記錄

| 決策 | 理由 |
|------|------|
| JSON 為主，Firestore 為輔 | 可 debug（GitHub）+ 可互動（Firestore） |
| 先 pipeline 後 UI | 資料品質是核心，UI 是包裝 |
| Human-in-the-loop | Jones 的直覺是最大 edge |
| 預留 multi-agent | 現在只有 Jarvis，但結構支援擴充 |
| 不自動執行行動 | 安全第一，所有不可逆行動需人工批准 |
