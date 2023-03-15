---
title: 原生PDF發佈功能 |在腳注中使用自訂樣式
description: 了解如何對腳注中的數字套用樣式。
source-git-commit: ef562c43f5b70d3fe425427108ad8277e1456f24
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---

# 在腳注中使用自訂樣式

腳注是放在頁面底部的注釋，用於對文本的指定部分進行注釋或引用引用引用。

您可以設定主題內容中腳注呼叫中的數字樣式，以及頁面底部的腳注標籤。 例如，您可以在數字周圍加上方括弧或變更顏色。 這些樣式可幫助您輕鬆識別文檔中的腳注。

```css
...
.footnote::footnote-call { 
content: "(" counter(footnote, decimal) ")"; 
} 

.footnote::footnote-marker { 
content: "(" counter(footnote, decimal) ")"; 
} 

...
```

在給定示例中，在腳注調用和標籤之前和之後添加括弧：

* 使用中的內容屬性，新增字首「（」和尾碼「）」 `footnote-call` 樣式，在主題內容的腳注編號周圍添加方括弧。
* 使用中的內容屬性，新增字首「（」和尾碼「）」 `footnote-marker` 樣式，將在頁面底部的腳注編號周圍添加方括弧。

<img src="./assets/pdf-output-footer-numbers.png" alt="PDF輸出中的頁尾" width="500">
