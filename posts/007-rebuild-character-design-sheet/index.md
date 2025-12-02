# 007 - 從舊圖重建出角色設定圖

## 🖼️ 工作流與結果展示 (Dual-Input Workflow)

| Prompt | 輸入圖像 | ➡️ 最終結果 (Final Result) |
|:---|:---:|:---:|
| A | <img src="input-1.png" width="300" /> | <img src="result-1a.jpeg" width="600" /> |
| B | <img src="input-1.png" width="300" /> | <img src="result-1b.jpeg" width="600" /> |
| A | <img src="input-2.png" width="300" /> | <img src="result-2a.jpeg" width="600" /> |

## 📝 Prompt 解析

### Prompt A - 內容

> Generate a high-quality design sheet of the character without any accessory.
> The layout features a full-body character rotation including frontal view, three-quarter view, side profile, and back view.
> The character is standing still with their arms relaxed.
> Preserve the character's facial features, outfit details and the original art style from the input reference images.
> The whole image is saturated and bright, and has no text.
> The aspect ratio is 16:9.

### Prompt A - 語句結構拆解

- \[核心任務 & 負向約束\]：Generate a high-quality design sheet + without any accessory (將核心目標與排除項前置，確保執行優先級)。
- \[佈局與術語\]：layout features a full-body character rotation (使用專業術語 "Rotation" 強化多視角的連續性邏輯)。
- \[視圖定義\]：frontal view, three-quarter view, side profile, and back view (明確列舉所需角度)。
- \[姿勢控制\]：standing still with their arms relaxed (標準 A-Pose/I-Pose 描述)。
- \[一致性控制 (Reference)\]：Preserve the character's facial features... and the original art style (強調忠於原圖的重建，而非風格重繪)。
- \[畫面參數\]：saturated and bright + no text + 16:9。

### Prompt B - 內容

> Generate a high-quality design sheet of the character and their accessories.
>
> The layout features two main sections:
> - A full-body character rotation including frontal view, side profile, and back view. (The character is strictly without accessories, standing in a relaxed pose).
> - A side panel including their accessories only.
>
> Preserve the character's facial features, outfit details and the original art style from the input reference images.
> The whole image is saturated and bright, and has no text.
> The aspect ratio is 16:9.

### Prompt B - 語句結構拆解

- \[任務定義\]：Generate a high-quality design sheet of the character and their accessories (明確告知模型這張圖包含兩個主體：人 + 物)。
- [空間佈局策略 (關鍵)\]：The layout features two main sections (引入分區概念，降低人與物混在一起的機率)。
  * \[左側：角色區\]：full-body character rotation... (strictly without accessories...) (使用括號強勢插入限制條件，確保素體乾淨)。
  * \[右側：配件區\]：side panel including their accessories only (定義獨立展示區)。
- \[一致性控制\]：Preserve... facial features, outfit details and the original art style (維持輸入圖的特徵)。
- \[畫面參數\]：saturated and bright + no text + 16:9。

## 🧪 實驗筆記與技術雷點
