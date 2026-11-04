# 遊戲背景圖片整合與開發需求說明書 (PRD)
## 遊戲名稱：The City That Lost Its Thought (失去思考的城市)

---

### 1. 專案概述 (Project Overview)
本說明書旨在指導開發團隊（或第二個 AI 平台）將已準備好的 **7 張高品質 16:9 日本動漫風格背景圖片** 完美整合至互動遊戲中，並確保遊戲在不同螢幕尺寸（桌機、平板、手機端）均能正確縮放與展示。

* **遊戲類型**：互動式視覺小說 (Visual Novel / CYOA Game)
* **目標受眾**：小學四年級至六年級學生 (P4-P6)。
* **語言要求**：**全英文 (A2-B1 級別)**，無中文字幕。
* **核心主題**：AI 素養與獨立思考能力 (AI Literacy & Critical Thinking)。

---

### 2. 背景圖片資源映射表 (Asset Mapping Table)

開發者需將上傳的圖片重新命名或直接對應至以下場景 ID：

| 圖片檔名 | 適用場景 / 章節 | 場景描述與用途 | CSS 渲染需求 |
| :--- | :--- | :--- | :--- |
| **`1.png`** | **Scene 0 (Start & Intro)** | 2050年「智城」白天的未來都市景觀（標題畫面與引言）。 | 需疊加 30% 半透明黑罩以突顯白色標題文字。 |
| **`7.png`** | **Scene 1 (Chapter 1)** | 第一章：高科技小學教室（教師派發節約用水功課）。 | 全螢幕涵蓋，過渡時間 0.5 秒淡入。 |
| **`6.png`** | **Scene 2 (Chapter 2)** | 第二章：未來學校科學實驗室（組員質疑 AI 實驗方案）。 | 全螢幕涵蓋。 |
| **`5.png`** | **Scene 3 (Chapter 3)** | 第三章：夕陽下的公園/校園小徑（與好友阿軒發生衝突）。 | 全螢幕涵蓋，表現溫暖黃昏氛圍。 |
| **`4.png`** | **Scene 4 (Chapter 4)** | 第四章：深夜停電的城市黑夜（全城斷電與網絡中斷）。 | 色調偏暗，Spark 角色需套用灰階/暗色濾鏡。 |
| **`3.png`** | **Scene 5 (Chapter 5)** | 第五章：停電三天後的混亂/廢棄教室（大家陷入困境）。 | 表現無光的昏暗室內感。 |
| **`2.png`** | **True Ending (End 4)** | 隱藏真結局：充滿生機與日出的未 can 重建都市（創造者）。 | 配合金色/黃色系結局文字與輝光特效。 |

*(註：結局 1、2、3 可根據氛圍沿用 `3.png` 或 `1.png`，真結局指定使用 `2.png`)*

---

### 3. 背景圖片的 CSS 與響應式展示規範 (Responsive Image Styling)

為了保證背景圖片在所有手機與電腦螢幕上都不會變形、拉伸或留下白邊，**必須嚴格遵守以下 CSS 規則**：

```css
/* 背景圖層基礎樣式 */
.game-background {
    width: 100%;
    height: 100%;
    background-size: cover;          /* 強制圖片填滿容器且保持比例，裁切多餘部分 */
    background-position: center;     /* 圖片始終置中對齊 */
    background-repeat: no-repeat;    /* 避免圖片重複平鋪 */
    transition: background-image 0.8s ease-in-out; /* 場景切換時的流暢淡入淡出特效 */
}

/* 標題頁與對話框背景防干擾遮罩 */
.bg-overlay {
    background: rgba(15, 23, 42, 0.45); /* 45% 半透明黑色 */
    backdrop-filter: blur(4px);          /* 毛玻璃模糊效果，提升文字可讀性 */
}
```

---

### 4. UI 介面與層級結構 (UI Layer Architecture)

畫面由下至上必須分為 **4 個獨立圖層 (Z-Index)**：

1. **Layer 1 (Z-Index: 10) - 背景圖層 (Background Layer)**
   * 動態載入 `1.png` 到 `7.png`，負責呈現當前劇情氛圍。
2. **Layer 2 (Z-Index: 20) - 角色立繪圖層 (Character Layer)**
   * 放置 AI 助手 "Spark" 的 SVG 或 PNG 浮動動畫（僅在 Scene 1-4 顯示，Scene 5 及結局隱藏）。
3. **Layer 3 (Z-Index: 30) - 遊戲 UI 與對話框 (HUD & Dialogue Layer)**
   * **頂部**：4 個膠囊狀數值按鈕 (`Dependence`, `Thinking`, `Cooperation`, `Empathy`)，採用半透明背景，不遮擋背景圖。
   * **底部**：對話框與選項按鈕。對話框需採用 `rgba(15, 23, 42, 0.85)` 高對比半透明底色，確保文字在任何圖片上都清晰可讀。
4. **Layer 4 (Z-Index: 50) - 結局與選單圖層 (Overlay/Ending Layer)**
   * 當遊戲結束時覆蓋整個畫面，展示分數結算與重玩按鈕。

---

### 5. 數據邏輯與結局判定 (Data & Ending Logic)

#### 5.1 初始數值 (Initial State)
* `Dependence = 0`
* `Thinking = 0`
* `Cooperation = 0`
* `Empathy = 0`

#### 5.2 結局觸發演算法 (Ending Trigger Algorithm)
請按以下嚴格優先順序檢查條件：

```javascript
if (thinking >= 10 && cooperation >= 3 && empathy >= 2) {
    // 🌟 True Ending: The Creator (使用背景 2.png)
} else if (thinking >= 8) {
    // ✅ Ending 3: The Wise User
} else if (dependence >= 8 && thinking <= 3) {
    // ❌ Ending 1: The Unthinking Person (使用背景 3.png)
} else {
    // ⚠️ Ending 2: The Half-Dependent (保底結局)
}
```

---

### 6. 開發者檢查清單 (Developer Checklist)

在其他 AI 或平台開發時，請確保：
* [ ] 所有圖片路徑正確（建議將 `1.png` 至 `7.png` 放在同一根目錄下）。
* [ ] 點擊「Start Game」後背景能立即順暢切換至 `7.png` (Classroom)。
* [ ] 手機橫向 (Landscape) 與直向 (Portrait) 下，文字框均不會擠壓遮擋背景中央的主題元素。
* [ ] 所有按鈕在點擊時均有明確的視覺反饋（如顏色加深或輕微放大）。
* [ ] 全英文文本（包含對話、按鈕、結局文字）無簡繁體中文遺漏。