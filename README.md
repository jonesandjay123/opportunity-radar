# Opportunity Radar 🛰️

> A JSON-driven, AI-powered system for discovering, structuring, and acting on real-world opportunity signals.

不是點子生成器，是**結構性機會探測引擎**。

## 核心理念

- 抓「已存在但沒被 productize 的需求」
- 訊號 > 意見，行動 > 分析
- Human-in-the-loop：Jones 是最終決策者
- JSON = single source of truth
- 設計預留多 agent 擴充

### 🧠 Jones 的三問（看到任何東西都問）

> 1. 這東西的「原始價值」是什麼？
> 2. 現在市場怎麼錯誤定價它？
> 3. 有沒有更好的敘事方式？

### ⚔️ 降維打擊定義

不是找一個很遠的地方去「降維」，而是找到一個**大家還在用舊方法解決問題的場域**。

降維打擊成立的三個條件：
- **資訊差（Information Asymmetry）** — 你知道的，他們還不知道
- **工具差（Tech Gap）** — 你有 AI/系統，他們用 Excel/手動/人肉
- **認知差（Mindset Gap）** — 你看到系統性機會，他們只看到日常

> 降維打擊 ≠ 去落後地區
> 降維打擊 = 去「低競爭 + 高摩擦」的場域

### 🏭 Physical × AI × Inefficiency 模型

最適合 Jones 的套利模型：

```
實體資產（機台/設備/服務）
    × AI 系統（定價/追蹤/自動化/優化）
    × 低效市場（傳統行業/第三世界/半數位化場域）
    = 穩定 cashflow + 降維打擊
```

**特徵：**
- 不用賣自己（不用當 influencer）
- 有 tangible 感（機器在跑、錢在進來）
- 可複製（一台跑通 → 複製到更多地點/市場）
- AI 是隱藏優勢（別人看到設備，你看到系統）

**適用場域：**
- 傳統小商業（餐廳/貼膜/改車/租借）
- 半數位化的企業流程
- 跨國套利（台灣↔美國↔東南亞）
- 低技術門檻但高摩擦的服務業

## 系統架構

```
[CRON: 每日觸發]
     ↓
[訊號收集（Reddit / HN / 社群）]
     ↓
[LLM 分析 + 結構化 + 打分]
     ↓
[寫入 JSON → data/opportunities/]
     ↓
[UI 顯示（Firestore-backed dashboard）]
     ↓
 (Jones 選擇 / 星號 / 留言)
     ↓
[Deep Dive Agent]
     ↓
[Decision Brief]
     ↓
 (Jones 批准)
     ↓
[Action Suggestions（不自動執行）]
```

## 機會篩選標準

每個機會必須至少滿足一項：
- ✅ 有人正在用 workaround（需求存在但沒被產品化）
- ✅ 有人付錢但很不爽（市場已驗證，solution 很爛）
- ✅ Jones 有特殊優勢（AI / 跨文化 / tech / 海外）

## 評分維度

| 維度 | 說明 |
|------|------|
| 需求強度 | 這是不是人真的痛 (1-5) |
| 痛苦頻率 | 每天發生 vs 偶發 (1-5) |
| 付費意願 | 人會不會掏錢 (1-5) |
| 自動化潛力 | 能不能搭成流水線 (1-5) |
| Jones 適配度 | 和 Jones 的能力/資源距離 (1-5) |
| 競爭空隙 | 紅海 vs 藍海 (1-5) |
| 跨國套利 | 能不能從一地搬到另一地 (1-5) |

## 狀態流

```
new → starred → selected → researching → actionable → done
                                                    → archived
                                                    → rejected
```

每個狀態可以由不同 agent 負責（目前全部由 Jarvis 處理）。

## 檔案結構

```
opportunity-radar/
├── README.md
├── data/
│   ├── opportunities/          # 每日機會 JSON
│   │   └── YYYY-MM-DD.json
│   └── deep-dives/             # 深入調查結果
│       └── {opportunity-id}.json
├── schema/
│   ├── opportunity.schema.json # 機會資料結構定義
│   └── deepdive.schema.json    # Deep dive 資料結構定義
└── roadmap.md
```

## 團隊分工

| 角色 | 誰 | 職責 |
|------|-----|------|
| 決策者 | Jones | 選擇、評分、批准行動 |
| 執行 agent | Jarvis | 訊號蒐集、分析、deep dive |
| 策略顧問 | GPT | 框架設計、方法論、review |

## 安全原則

⚠️ AI **不能**自動執行不可逆行動：
- ❌ 發公開貼文
- ❌ DM 真人
- ❌ 花錢
- ❌ 上架產品

✅ AI **可以**自動做：
- 訊號收集
- 競品調查
- 使用者語錄整理
- 市場規模估算

## Roadmap

### Phase 1 — Pipeline MVP
- [ ] 定義 JSON schema ✅
- [ ] CRON 每日訊號收集（Reddit / HN）
- [ ] LLM 分析 + 結構化輸出
- [ ] 第一份真實 Daily Brief
- [ ] Jones 確認品質

### Phase 2 — Dashboard
- [ ] Firestore 資料同步
- [ ] 簡單 UI（機會列表 + 篩選 + 星號 + 留言）
- [ ] Jarvis REST API 寫入通道

### Phase 3 — Deep Dive
- [ ] 選中機會自動 deep dive
- [ ] 競品分析
- [ ] 使用者語錄收集
- [ ] Action suggestions（人工批准）

### Phase 4 — Multi-Agent（未來）
- [ ] 不同 agent 負責不同 stage
- [ ] 自動驗證 pipeline
- [ ] 半自動行動執行

---

*建立日期：2026-03-17*
*靈感來源：Jones × GPT × Jarvis 三方協作*
