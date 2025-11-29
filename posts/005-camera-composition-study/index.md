# 005 - 鏡頭語言研究：視角、景別與運鏡 (Cinematic Camera Language)

## 鏡頭語言的簡介

- **垂直視角 (Camera Angle)**: High, Low, Bird's-eye...
- **景別 (Shot Size)**: Close-up, Medium, Long shot...
- **水平視角 (Camera Viewpoint/Rotation)**: Front, Side, Back...

![Camera Angle Diagram](camera_angle.jpg)
![Shot Sizes Diagram](camera_shot_sizes.jpg)

## Multi-Modal Image Generation 實驗

* **實驗目的：** 測試 Nano Banana Pro 的 **「空間建構能力」** (適合從零創作)。
* **方法：** 使用相同的描述，僅替換鏡頭語言關鍵字，觀察 AI 如何構建透視。
* **Prompt 類型：** 描述式 (Description-based)。

> **Base Prompt:** `The Japanese man is hiking in front of Fuji mountain.`

| 輸入圖檔 (角色設定) | 生成結果 (未指定視角) |
| :---: | :---: |
| <img src="txt2img/input.png" width="200" /> | <img src="txt2img/output-default.png" width="200" /> |

| 關鍵字 | 生成結果 | Prompt | Description |
| :--- | :---: | :--- | :--- |
| `Aerial view` | <img src="txt2img/output-aerial_view.png" width="200" /> | `Aerial view of the Japanese man, who is hiking in front of Fuji mountain.` | 高空航拍視角。強調廣闊地形，人物通常極小如螞蟻，呈現地圖般的宏觀感。 |
| `Bird's-eye view` | <img src="txt2img/output-birds_eye_view.png" width="200" /> | `Bird's-eye view looking straight down at the Japanese man hiking in front of Fuji mountain.` | 垂直俯視圖（上帝視角）。強調幾何構圖，人物頭頂與肩膀可見，背景呈現平面化。 |
| `Top-down view` | <img src="txt2img/output-top_down_view.png" width="200" /> | `Top-down view of the Japanese man, who is hiking in front of Fuji mountain.` | 正頂視角。類似 Bird's-eye 但通常聚焦於人物本身，用於展示人物在環境中的位置佈局。 |
| `high angle view` | <img src="txt2img/output-high_angle_view.png" width="200" /> | `High angle view of the Japanese man, who is hiking in front of Fuji mountain.` | 高角度俯拍。使人物看起來較為渺小、脆弱或處於弱勢，背景地面佔比增加。 |
| `low angle view` | <img src="txt2img/output-low_angle_view.png" width="200" /> | `Low angle view looking up at the Japanese man, who is hiking in front of Fuji mountain.` | 低角度仰拍。賦予人物高大、強壯或英雄式的視覺心理暗示，背景通常帶到天空。 |
| `extremely low angle view` | <img src="txt2img/output-ext_low_angle_view.png" width="200" /> | `Extremely low angle view looking up at the Japanese man, who is hiking in front of Fuji mountain.` | 極端仰視。透視變形強烈，強調腿部線條修長與人物的壓迫感，背景可能完全是天空。 |
| `worm's-eye view` | <img src="txt2img/output-worms_eye_view.png" width="200" /> | `Directly from below, sole of shoes visible, worm's-eye view of the Japanese man, who is hiking in front of Fuji mountain.` | 蟲視視角（貼地視角）。Prompt 強調「可見鞋底」以測試模型對遮擋部位的幾何建構能力。 |
| `Dutch angle` | <img src="txt2img/output-dutch_angle.png" width="200" /> | `Dutch angle, tilted frame of the Japanese man hiking in front of Fuji mountain, dynamic composition. Preserve the original art style from the input character reference image.` | 荷蘭式傾斜。地平線歪斜，打破平衡，營造動態感、緊張或混亂的敘事氛圍。 |
| `tilted angle` | <img src="txt2img/output-tilted_angle.png" width="200" /> | `Tilted angle shot of the Japanese man hiking in front of Fuji mountain.` | 傾斜構圖。比 Dutch angle 稍微溫和，用於為靜態的登山畫面增加視覺流動性。 |
| `close-up view` | <img src="txt2img/output-close_up_view.png" width="200" /> | `Close-up view of the Japanese man's face, hiking in front of Fuji mountain, depth of field. Preserve the original art style from the input character reference image.` | 特寫鏡頭。聚焦於臉部表情，背景自動產生景深虛化 (Bokeh) 以突出主體，測試細節保留度。 |
| `Medium shot` | <img src="txt2img/output-medium_shot.png" width="200" /> | `Medium shot of the Japanese man, waist-up view, hiking in front of Fuji mountain.` | 中景。標準的「腰上景」，平衡展現人物動作與部分背景環境，最常用的敘事鏡頭。 |
| `Extreme close-up` | <img src="txt2img/output-extreme_close_up.png" width="200" /> | `Extreme close-up of the Japanese man's eyes, detailed skin texture, hiking in front of Fuji mountain.` | 極特寫（微距）。聚焦於局部（如眼睛），測試模型對皮膚紋理與細節的生成極限。 |
| `Full shot` | <img src="txt2img/output-full_shot.png" width="200" /> | `Full shot of the Japanese man, who is hiking in front of Fuji mountain.` | 全景。完整呈現人物從頭到腳，測試模型是否能保持肢體完整性（避免切腳）。 |
| `Establishing shot` | <img src="txt2img/output-establishing_shot.png" width="200" /> | `Establishing shot of the vast landscape of Fuji mountain with a Japanese man hiking in the distance.` | 建立鏡頭。重點在於交代環境全貌與地理位置，人物通常作為比例尺存在，佔比極小。 |
| `Long shot` | <img src="txt2img/output-long_shot.png" width="200" /> | `Long shot of the Japanese man hiking in the vast landscape in front of Fuji mountain.` | 遠景。強調人與大自然的關係，人物全身可見但被環境包圍。 |
| `Eye level` | <img src="txt2img/output-eye_level.png" width="200" /> | `Eye level shot of the Japanese man, who is hiking in front of Fuji mountain.` | 平視視角。客觀且中立的觀察角度，符合人類日常視覺經驗，畫面最為穩定。 |

## Image Editing 實驗 (修改設定圖)

* **實驗目的：** 測試 Nano Banana Pro 的 **「理解與編輯能力」** (適合微調)。
* **方法：** 使用相同的角色原圖，僅替換鏡頭語言關鍵字，觀察 AI 是否能在不破壞角色的前提下改變構圖。
* **Prompt 類型：** 指令式 (Instruction-based)。

| 關鍵字 (Keyword) | 輸入圖檔 | 生成結果 | Prompt | Description |
| :--- | :---: | :---: | :--- | :--- |
| `low angle view` | <img src="img2img/input.png" width="200" /> | <img src="img2img/output-low_angle_view.png" width="200" /> | `change the camera angle to low angle view` | 修改為仰視。觀察 AI 是否能重新計算下巴與身體的透視關係，而不破壞臉部特徵。 |
| `high angle view` | <img src="img2img/input.png" width="200" /> | <img src="img2img/output-high_angle_view.png" width="200" /> | `change the camera angle to high angle view` | 修改為俯視。測試 AI 能否在保留原圖姿勢的前提下，改變背景透視（如看到更多地面）。 |
| `close-up view` | <img src="img2img/input.png" width="200" /> | <img src="img2img/output-close_up_view.png" width="200" /> | `change the camera angle to close-up view` | 修改為特寫。測試 AI 的裁切與重繪能力，觀察是否能拉近鏡頭並自動增加背景虛化效果。 |
| `front view` | <img src="img2img/input.png" width="200" /> | <img src="img2img/output-front_view.png" width="200" /> | `Change the view to a strictly front view` | 修改為正視圖。要求 AI 將人物旋轉至正對鏡頭，需檢查五官對稱性與視線是否直視前方。 |
| `side profile view` | <img src="img2img/input.png" width="200" /> | <img src="img2img/output-side_view.png" width="200" /> | `Change the view to a side profile view` | 修改為側視圖（90度）。測試 AI 能否推算出原本不可見的側臉輪廓（鼻子高度、後腦杓結構）。 |
| `back view` | <img src="img2img/input.png" width="200" /> | <img src="img2img/output-back_view.png" width="200" /> | `Change the view to a back view` | 修改為背視圖（180度）。**最高難度測試**。AI 必須完全擦除臉部特徵，並憑空「腦補」出髮型背面與背部服裝細節。 |
| `three-quarter view` | <img src="img2img/input.png" width="200" /> | <img src="img2img/output-34_view.png" width="200" /> | `Change the view to a three-quarter view` | 修改為 3/4 側視圖（45度）。最標準的肖像角度，測試 AI 能否呈現自然的立體感與臉部轉向。 |
| `three-quarter back view` | <img src="img2img/input.png" width="200" /> | <img src="img2img/output-34_back_view.png" width="200" /> | `Change the view to a three-quarter back view` | 修改為 3/4 背視圖。電影感強烈的角度，常用於過肩鏡頭。觀察重點在於下顎線與脖子後方的連接處理是否自然。 |
