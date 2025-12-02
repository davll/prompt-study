# 001 - 動畫風角色設定圖 - Base Body (素體)

## 🖼️ 生成結果

<img src="result-ai_studio.jpeg" width="300" />

## 📝 Prompt 解析

### Prompt 內容

> Generate a professional character design sheet of a 30-year-old English man, rendered in a classic American cartoon style.
> The layout features a full-body character rotation including frontal view, three-quarter view, side profile, and back view.
> He has a tall muscular build, and is shirtless and wearing only white underwear.
> He has a short hairstyle, a stubble, and green eyes.
> He stands still with arms relaxed by his sides.
> The lighting is bright and saturated against a solid plain white background.
> The image should be text-free and high quality.
> The aspect ratio is 16:9.

### 語句結構拆解

1. `Generate a professional character design sheet of a 30-year-old English man, rendered in a classic American cartoon style.`
   一開頭告訴 AI 說這張圖是一個角色設計圖，並初步描述角色的基本類型與畫風類型。
   * **畫風替換選項：**
      * `classic American cartoon style` (經典美式卡通)
      * `Showa-era Japanese anime style` (昭和時代日系風格)
      * `American cartoon style inspired by [作品名]` (指定美式作品風格)
      * `Japanese animation style inspired by [作品名]` (指定日系作品風格)

2. `The layout features a full-body character rotation including frontal view, three-quarter view, side profile, and back view.`
   說明這個角色設定圖是一個角色轉向圖 (character rotation)，並定義了四個視角(正前方視角、3/4視角、側面視角、背面視角)，並確保這四個視角的人物的高度一致性。

3. `He has a tall muscular build, and is shirtless and wearing only white underwear.`
   定義了身材與服裝。特別用 shirtless 是為了避免 AI 自作聰明加上了貼身背心或汗衫。
   在這裡僅生成穿著內褲的版本(作為 base body 用途)，之後會以這張生成後的設定圖為基礎去生成不同服裝的版本。
   * **身材替換選項：**
      * `tall muscular build`：運動員結實身材
      * `tall and hunky muscular build`：誇張的大肌肉健美身材

4. `He has a short hairstyle, a stubble, and green eyes.`
   定義了頭部的細節（例如：髮型、鬍型、眼睛虹膜顏色）。
   * **髮型替換選項：**
      * `buzz-cut hairstyle` (寸頭)
      * `short hairstyle` (短髮)
      * `faux hawk hairstyle` (仿莫霍克髮型)
   * **鬍型替換選項：**
      * `stubble` (鬍渣)
      * `boxed beard` (落腮鬍)

5. `He stands still with arms relaxed by his sides.`
   定義了姿勢(pose)，確保是標準設定圖站姿 (A-Pose 或 I-Pose)，避免遮擋身體結構。

6. `The lighting is bright and saturated against a solid plain white background.`
   定義光影與背景。高飽和度符合美式動畫風格，白底則方便去背。

7. `The image should be text-free and high quality.`
   提示這張圖無文字，圖像品質為高品質。(Gemini App 可以生成 1K or 2K 解析度)

8. `The aspect ratio is 16:9.`
   強制把生成的畫面比例固定為 16:9。如果不加上這句，預設生成的圖像會是正方形，四個視角會擠在一起甚至缺漏。

## 🧪 實驗筆記與技術雷點

* **多視角一致性修正：**
    Gemini 生成這類多視角圖（Character Sheet）時，偶爾會出現「側面圖和正面圖長得不像」的情況。如果發生這種狀況，可以在 Prompt 中加入一句：`Ensure consistent character features across all views.` (確保所有視角的角色特徵一致。)

* **平台選擇建議：**
    如果要生成正式版本的設定圖，建議用 **Google AI Studio**，原因如下：
    * 可以選最高畫質 **4K** (成本較高但細節最優)。
    * 無 Gemini 標誌的浮水印，便於商業使用或後製。

* **後期降噪處理 (Waifu2x)：**
    建議用 waifu2x 去處理生成後的設定圖。
    * **原因：** 因為 Diffusion 模型的基本原理是從一張 Noise Image 根據 Latent Space 的資訊還原出圖像來，所以生成後的圖像表面常帶有細微雜訊。此外，Gemini 3 Pro (Nano Banana Pro) 所生成的圖像偶爾帶有 JPEG 壓縮雜訊。
    * **操作：** 使用 waifu2x 以最高的強度 (`noise-level = 3`) 執行，可以消除大部分的雜訊，讓畫面更乾淨平滑，更像向量圖。
    * **工具參考：** [waifu2x-ncnn-vulkan](https://github.com/nihui/waifu2x-ncnn-vulkan)
      * 參考的命令參數：`-n 3 -m models-upconv_7_anime_style_art_rgb`
