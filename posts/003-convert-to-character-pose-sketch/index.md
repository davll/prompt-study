# 003 - 圖像轉動態姿勢草稿 (Pose Construction)

## 🖼️ 工作流與結果展示 (Dual-Input Workflow)

| 輸入圖像 | 生成結果 |
|---------|---------|
| <img src="input.jpeg" width="200" /> | <img src="result.jpeg" width="200" /> |

* 輸入圖片取自 [The Moves Make the Man Part 2](https://www.ign.com/articles/2002/09/18/the-moves-make-the-man-part-2)

## 📝 Prompt 解析

### Prompt 內容

> A rough construction sketch based on the pose in the image. The drawing should be made of red pencil lines on a plain white background. It shows the basic body structure using geometric shapes, cylinders for limbs, circles for joints, and guide lines on the face. Unfinished, preparatory drawing style.

### 語句結構拆解

1.  `A rough construction sketch based on the pose in the image.`
    定義任務目標。要求 AI 忽略原圖的材質、光影與細節，僅提取「姿勢 (Pose)」資訊，並轉化為「結構草圖 (Construction sketch)」。

2.  `The drawing should be made of red pencil lines on a plain white background.`
    定義媒材與風格。指定「紅筆線條 (Red pencil)」是為了模仿傳統動畫或原畫師常用的 Col-Erase 鉛筆草稿質感；白底則能去除背景干擾，讓動作一目瞭然。

3.  `It shows the basic body structure using geometric shapes, cylinders for limbs, circles for joints,`
    這是核心指令。強制 AI 使用「幾何結構」來理解人體（四肢畫成圓柱體、關節畫成球體）。這能防止 AI 只是單純地描邊 (Tracing)，而是真正地去建構人物的 3D 體積感。

4.  `and guide lines on the face.`
    要求畫出臉部的十字定位線，確認頭部的轉向與透視。

5.  `Unfinished, preparatory drawing style.`
    定義完成度。強調這是「未完成、準備階段」的圖，讓線條保持潦草與生動，避免 AI 過度渲染或修飾線條。

## 🧪 實驗筆記與技術雷點

* **逆向學習工具：** 這個 Prompt 非常適合用來「拆解」大師的作品。當你看到一張很帥的遊戲截圖或插畫，但看不懂它的透視時，用這個 Prompt 可以讓 AI 幫你把骨架「透視」出來。

* **幾何化的重要性：** 關鍵字 `cylinders` (圓柱) 和 `geometric shapes` (幾何形狀) 非常重要。如果沒加這些詞，AI 傾向於生成單純的輪廓線稿 (Line art)，而非強調體積的結構稿 (Construction)，對於學習人體結構的幫助會大打折扣。

## References:

**關於參考資料：** 本次測試使用了 *Splinter Cell* (縱橫諜海) 系列的動作設計作為參考。Sam Fisher 的標誌性蹲姿與潛行動作具有極強的重心轉移與張力，非常適合作為動態練習的素材。

* [The Moves Make the Man Part 1](https://www.ign.com/articles/2002/09/16/the-moves-make-the-man-part-1)
* [The Moves Make the Man Part 2](https://www.ign.com/articles/2002/09/18/the-moves-make-the-man-part-2)
* [The Moves Make the Man Part 3](https://www.ign.com/articles/2002/09/20/the-moves-make-the-man-part-3)
