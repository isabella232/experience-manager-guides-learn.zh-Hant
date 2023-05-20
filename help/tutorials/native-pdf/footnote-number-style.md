---
title: 本機PDF發佈功能 |在腳注中使用自定義樣式
description: 瞭解如何對腳注中的數字應用樣式。
exl-id: f1068f2f-2ace-4bdb-b5a4-46b03d4e43d6
source-git-commit: 7b48633ef2418fa7c91842a8d2c2a4177017ef58
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---

# 在腳注中使用自定義樣式

腳注是位於頁面底部的注釋，該頁面對文本的指定部分注釋或引用引用。

您可以對主題內容中出現的腳注調用和頁面底部的腳注標籤中的數字進行樣式化。 例如，可以在數字周圍添加括弧或更改其顏色。 這些樣式可幫助您輕鬆識別文檔中的腳注。

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

在給定示例中，在腳注調用和標籤之前和之後添加一個括弧：

* 使用中的內容屬性添加前置詞「（」和尾碼「）」 `footnote-call` 樣式，該樣式將在主題內容的腳注編號周圍添加方括弧。
* 使用中的內容屬性添加前置詞「（」和尾碼「）」 `footnote-marker` 樣式，該樣式將在頁面底部的腳注編號周圍添加括弧。

<img src="./assets/pdf-output-footer-numbers.png" alt="PDF輸出中的頁腳" width="500">
