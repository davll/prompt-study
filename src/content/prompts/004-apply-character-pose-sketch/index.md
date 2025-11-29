# 004 - 從姿勢草圖與角色設定圖合成一個動作差分立繪

## 🖼️ 工作流與結果展示 (Dual-Input Workflow)

| 輸入 A: 結構 (Pose) | 輸入 B: 角色 (Character) | ➡️ 最終結果 (Final Result) |
| :---: | :---: | :---: |
| ![Pose Input](../003-convert-to-character-pose-sketch/result.jpeg) | ![Character Ref](../002-modify-character-design-sheet-outfit/result-ai_studio-webui.jpeg) | ![Final Result](./result.png) |

## 📝 Prompt 解析

> Generate a high-quality illustration based on the two provided input images.
>
> 1.  **Pose Reference:** Use the image containing the **red pencil structure sketch** to strictly determine the character's pose, perspective, and body composition.
> 2.  **Character Reference:** Use the image containing the **character design sheet** (the man in the blue waistcoat suit) to strictly determine the character's facial features, body proportions, and outfit details.
>
> - **Task:** Render the specific character from the design sheet performing the exact action shown in the sketch.
> - **Style:** Preserve the original art style from the input character design sheet. Plain white background.

### 語句結構拆解

1.  **Base Instruction (基礎指令):**
    `Generate a high-quality illustration based on the two provided input images.`
    開宗明義告訴 AI 這次的任務核心在於「整合兩張輸入圖片」的資訊。

2.  **Input Image Assignment (輸入圖像指派):**
    這是 Prompt 最關鍵的部分。由於上傳圖片的順序可能不定，我們透過**描述圖片特徵**來指定用途，而非僅用 "Image 1" 或 "Image 2"。
    * **Pose Reference:** 指定那張「紅筆結構草圖 (`red pencil structure sketch`)」是動作與透視的唯一依據。
    * **Character Reference:** 指定那張「角色設定圖 (`character design sheet`)」是外觀、長相與服裝的唯一依據。

3.  **Style Locking (畫風鎖定):**
    `Preserve the original art style...`
    要求 AI 繼承設定圖中的風格參數（賽璐珞上色、向量線條），避免因為輸入了草稿圖，導致 AI 誤以為要畫成「完稿的素描」或改變畫風。

## 🧪 實驗筆記與技術雷點

### 1. 多模態提示技巧 (Multimodal Prompting)
在同時上傳多張圖片時，Gemini 有時會混淆哪張圖是重點。
**成功關鍵：** 在 Prompt 中明確指出「圖片的視覺特徵」來做區隔（例如："Red pencil sketch" vs "Blue waistcoat suit"）。這能幫助模型在內部 Attention 機制中正確分配權重——把結構權重給草圖，把材質權重給設定圖。

### 2. 關於 Character Consistency
相較於純文字描述，直接餵給 AI 一張 Character Sheet 的效果通常更穩定，特別是對於複雜的服裝細節（如領帶顏色、背心款式）。但要注意，有時 AI 會過度模仿設定圖的「站姿」，導致生成出來的動態不夠像草稿那麼大。這時可以在 Prompt 中加強語氣：`Strictly follow the pose in the sketch`。

### 3. 工作流價值
這個 `Sketch (#003) + Sheet (#002) = Final (#004)` 的流程證明了：我們可以在不依賴 ControlNet 等外部工具的情況下，僅透過原生的 Multimodal LLM 達成一定程度的「可控生成」。
