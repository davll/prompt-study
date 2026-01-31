# 008 - 動作姿勢草圖提取實驗 (Action Pose Extraction)

## 🖼️ 工作流與結果展示 (Workflow & Result)

使用 Nano Banana Pro 進行圖生圖 (Image-to-Image) 轉換，目標是將輸入的圖像轉化為純結構參考圖。

| Prompt 版本 | 輸入圖像 / 參考圖 | 生成結果 |
| --- | --- | --- |
| A | <img src="input-1.jpeg" width="200" /> | <img src="result-1a.jpeg" width="200" /> |
| B | <img src="input-1.jpeg" width="200" /> | <img src="result-1b.jpeg" width="200" /> |
| A | <img src="input-2.jpg" width="200" /> | <img src="result-2a.jpeg" width="200" /> |
| B | <img src="input-2.jpg" width="200" /> | <img src="result-2b.jpeg" width="200" /> |

* 第二張輸入圖像取自七龍珠動畫截圖

## 📝 Prompt 解析

### Prompt 內容

**方案 A：幾何骨架 (Structure Focused)**

> A minimalist skeleton structure of a character in dynamic pose, consisting of simple colored lines and joint dots, openpose style, schematic diagram, pure white background, high contrast, 2D vector style. --no realistic, skin, face, eyes, hair, clothes, fabric, costume, shading

**方案 B：動態速寫 (Gesture Focused)**

> A simple gesture drawing of a human body doing dynamic action, minimalist black ink lines, featureless mannequin, no facial features, no hair, no clothes, isolated on white background, rough sketch style. --no realistic, complex details, texture, background, color

### 語句結構拆解

1. `minimalist skeleton structure` / `joint dots`
**定義任務目標：** 這是方案 A 的核心，強制模型將人體理解為「點與線」的幾何構成，模擬 OpenPose 的數據視覺化效果，而非藝術繪畫。
2. `featureless mannequin` / `schematic diagram`
**視覺/材質設定：** 使用「無特徵人偶」或「示意圖」這類詞彙，能有效剝離 Nano Banana Pro 對於「人像美感」的預設追求，避免它嘗試繪製五官。
3. `pure white background` + `high contrast`
**核心指令/權重詞：** 強制去背並提高對比度。這在後續製作遊戲資產或進行去背處理時非常關鍵，確保線條邊緣清晰乾淨。

## 🧪 實驗筆記與技術雷點

* **核心發現 / 關鍵字：**
  * **「OpenPose style」的魔力：** 在 Nano Banana Pro 中使用這個關鍵字，即使沒有安裝額外插件，模型也能傾向生成類似 3D 骨架的視覺效果，對於動作分析非常精準。
  * **負向提示詞的重要性：** 必須極端地排除 `clothing` 和 `fabric`，否則模型傾向於給火柴人穿上簡陋的 T-shirt，干擾關節點的判讀。


* **遇到的問題 / 雷點：**
  * **手部崩壞風險：** 雖然身體結構簡化了，但手指關節如果沒有特別指定 `mitten hands` (連指手套手) 或簡化指令，有時會變成一團混亂的線條。
  * **過度藝術化：** 方案 B 的 `rough sketch style` 有時會讓線條過於雜亂（草稿線太多），若需要乾淨線條，建議改用方案 A 的 `vector style`。


* **應用場景：**
  * **格鬥遊戲開發：** 快速產出大量攻擊動作的判定框參考，直接疊在遊戲引擎中測試打擊範圍。
  * **美術繪圖輔助：** 作為「動態參考底圖」，解決透視與人體比例崩壞的問題。


## References:

**關於參考資料：** 本實驗主要參考人體結構學與計算機視覺的骨架偵測概念。

* [OpenPose Library Concept](https://github.com/CMU-Perceptual-Computing-Lab/openpose) (僅作為視覺風格參考)
* [Gesture Drawing Basics](https://www.line-of-action.com/) (關於動態速寫的線條理論)
