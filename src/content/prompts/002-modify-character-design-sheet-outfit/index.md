# 002 - 動畫風角色設定圖 - 服裝變更

## 🖼️ 生成結果

![角色設定圖結果](result-ai_studio-webui.jpeg)

## 🖼️ 輸入圖像

![Input Image](../001-create-character-design-sheet/result-ai_studio.jpeg)

## 📝 Prompt 解析

> Modify the character design sheet to change the character's outfit. He is now wearing a white shirt, a black necktie, a navy blue waistcoat, navy blue trousers, and brown oxford shoes. Preserve the character's facial features and the original art style from the input reference image.

### 語句結構拆解

1.  `Modify the character design sheet to change the character's outfit.`
    這是 **指令 (Instruction)**。明確告訴 AI 任務是「修改」而非「重新生成」，且鎖定修改範圍僅限於「服裝」，暗示應保留人物姿勢與面部特徵。

2.  `He is now wearing a white shirt, a black necktie, a navy blue waistcoat, navy blue trousers, and brown oxford shoes.`
    定義具體的 **服裝內容 (Content)**。詳細列出從頭到腳的配件與配色（白襯衫、黑領帶、深藍背心與長褲、牛津鞋），確保生成出的搭配符合設計需求。

3.  `Preserve the character's facial features and the original art style from the input reference image.`
    這是 **風格維持 (Style Consistency)** 的關鍵。明確要求保留臉部特徵 (Facial features) 和原始畫風 (Art style)，以減少圖生圖過程中的變異。

## 🧪 實驗筆記與技術雷點

### 臉部細節修復 (The Head Swap Technique)

生成後的圖像常常會發生臉部品質劣化，因為 AI 模型在 Image-to-Image 過程中將算力聚焦在衣服的重繪上，導致臉部特徵（尤其是眼睛）出現些微變形或模糊。

* **解決方案：** 利用 Gemini 3 Pro (Nano Banana Pro) 強大的骨架與構圖一致性，將生成後的圖像放入 Photoshop。將原始的高畫質「素體圖」放在上層，使用圖層遮色片 (Layer Mask) 僅保留頭部，覆蓋掉換裝後劣化版本。這樣既能擁有新衣服，又能保留完美的臉部細節。

### 不同介面用同 Nano Banana Pro 模型的結果差異

雖然是同樣用 Nano Banana Pro 模型，但不同介面的結果都差異很多:
- [Gemini Web UI](https://gemini.google.com/)：輸入圖檔都會被嚴重壓縮再傳入 server，導致畫質嚴重劣化
- Gemini iOS App：相比 Gemini Web UI，畫質劣化沒這麼嚴重，但描邊線條有明顯糊掉
- [AI Studio Web UI](https://aistudio.google.com/)：使用成本較高（按 Token 計價），但品質最好，描邊線條有保持銳利，無浮水印（但依然有 SynthID）

| Gemini Web UI | AI Studio Web UI |
|---------------|------------------|
| ![result-gemini-webui](result-gemini-webui-cropped.png) | ![result-ai_studio-webui](result-ai_studio-webui-cropped.jpeg) |
