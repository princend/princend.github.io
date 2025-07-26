---
title: 毛玻璃效果
categories:
- Frontend
- Tech
feature_image: "https://picsum.photos/2560/600?image=2"  
excerpt: |
 毛玻璃效果是一種將背景模糊且帶透明的視覺設計手法。常用於卡片、彈窗、選單等區塊，讓...
---

## 1. 毛玻璃（Glassmorphism）效果簡介
現代網頁設計中，「毛玻璃」即 Glassmorphism 效果越來越常見。這種風格不只美觀，還能有效提升 UI 元素的層次感。本篇將簡單介紹毛玻璃效果的原理、主要樣式，以及簡易實作。

### 什麼是毛玻璃（Glassmorphism）？
- 毛玻璃效果是一種將背景模糊且帶透明的視覺設計手法。常用於卡片、彈窗、選單等區塊，讓界面更有層次，並有一種「玻璃懸浮」於畫面上的現代感。

### 實作重點：哪些CSS屬性會影響毛玻璃？
- background
設定有透明度的背景色（如 rgba(255,255,255,0.2)），讓底層圖片或顏色能透出。

- backdrop-filter: blur(...)
這是製造模糊的關鍵屬性。數值越大，模糊越強，如 backdrop-filter: blur(10px)。

- -webkit-backdrop-filter: blur(...)
針對部分瀏覽器的前綴寫法，確保相容性。

- border-radius
圓角讓元素邊緣更柔和、富有玻璃質感。

- border
淡色細框（常帶透明度）更貼近真實玻璃的邊界。

- box-shadow
投影能強調玻璃的浮起感，讓區塊不單薄。


### 實際應用畫面
- 適合用於登入表單、提示卡片、底部導航浮窗等區块

- 彈窗、選單、數據看板都能快速提升層次感與美觀度

### 範例
<iframe height="400" style="width: 100%;" scrolling="no" title="frosted class 範例" src="https://codepen.io/Princend-the-selector/embed/jEbrJaw?default-tab=html%2Cresult" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/Princend-the-selector/pen/jEbrJaw">
  frosted class 範例</a> by Princend (<a href="https://codepen.io/Princend-the-selector">@Princend-the-selector</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>