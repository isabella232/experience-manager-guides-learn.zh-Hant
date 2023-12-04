---
title: 原生PDF發佈功能 |在目錄專案和主題內容套用自訂樣式
description: 瞭解如何建立使用樣式表及內容的樣式。
source-git-commit: 880cd344ceb65ea339be699ebcad41c0d62e168a
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# 在目錄專案和主題內容套用自訂樣式

有時，您可能會想要在目錄專案或特定主題上套用自訂樣式。 這可以透過關聯 `outputclass` 屬性和 `<topicref>` DITA map中的元素。 此外，如果您想要將自訂格式套用至整個主題，也可以透過在CSS中擴充屬性的樣式定義來達成。

以您要傳送以供檢閱的新主題為例。 為方便識別更新的主題，您需要新增 `outputclass` 屬性至 `<topicref>` 元素，然後在CSS中為相同專案定義自訂樣式。

在以下範例中， *航班歷史記錄* 已將主題指派給 `outputclass` 屬性值為的屬性 `new-topic`.

<img src="./assets/new-topic-attribute-in-map.png" width="500">

的類別定義 `new-topic` 在CSS中，可讓您定義下列專案的樣式：
* 目錄或迷你目錄中的主要專案
* 主要內容中的主題標題
* 主題的整個內容，包括標題

讓我們看看如何在CSS中定義這些案例。 在下列的CSS定義中 `new-topic` 類別中，文字顏色已變更。

```css
…
.new-topic {
  color: #CC5309
}
…
```

此定義控制目錄中的文字顏色和主題標題。 下列PDF輸出顯示目錄專案上套用的不同顏色：

<img src="./assets/pdf-output-toc-entry.jpg" width="500">

主題的標題也會使用相同的顏色設定樣式。

<img src="./assets/pdf-output-topic-title.jpg" width="500">

如果您希望目錄專案和主題的標題有不同的樣式，可以分別定義它們，如下所示：

```css
...
/*for styling TOC entry */
.new-topic {
  color: #CC3509
}

/* for styling topic's title */
.new-topic.title {
  color: #092ACC
}
...
```

最後，您也可以在主題內的整個內容上套用樣式。 為此，您需要新增尾碼&quot;`-content`」至類別名稱。 在下列範例中，變更列已新增至主題的整個內容中：

```css
...
/* for styling the topic's content */
.new-topic-content {
  -ro-change-bar-color: #A609CC;
}
...
```

使用上述樣式屬性，變更列會新增至 *航班歷史記錄* 主題，如下所示：

<img src="./assets/pdf-output-topic-content.jpg" width="500">
