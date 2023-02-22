---
title: 原生PDF發佈功能 |對目錄項目和主題內容套用自訂樣式
description: 了解如何建立使用樣式表和建立內容的樣式。
source-git-commit: 09918abbdade934468dea1c55d0ca2cd60622b35
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---


# 對目錄項目和主題內容套用自訂樣式

有時候，您可能會想要在目錄項目或特定主題上套用自訂樣式。 這可借由將 `outputclass` 屬性 `<topicref>` 元素。 此外，如果您想將自訂格式套用至整個主題，則也可在CSS中擴充屬性的樣式定義來達成此目的。

以您要傳送以供審核的新主題為例。 為了輕鬆識別更新的主題，您需要新增 `outputclass` 屬性 `<topicref>` 元素，然後在CSS中定義相同的自訂樣式。

在下列範例中， *飛行歷史* 已指派主題 `outputclass` 屬性值為 `new-topic`.

<img src="./assets/new-topic-attribute-in-map.png" width="500">

的類別定義 `new-topic` 在CSS中，可讓您定義下列項目的樣式：
* 目錄或迷你目錄中的主要項目
* 主要內容中的主題標題
* 主題的整個內容，包括標題

讓我們查看如何在CSS中定義這些案例。 在下列的CSS定義中 `new-topic` 類，文本顏色已更改。

```css
…
.new-topic {
  color: #CC5309
}
…
```

此定義會控制目錄和主題標題中的文字顏色。 下列PDF輸出顯示套用在TOC項目上的不同顏色：

<img src="./assets/pdf-output-toc-entry.jpg" width="500">

主題的標題也使用相同顏色設定樣式。

<img src="./assets/pdf-output-topic-title.jpg" width="500">

如果您希望TOC項目和主題標題有不同的樣式，則可以分別定義它們，如下所示：

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

最後，您也可以對主題內的整個內容套用樣式。 為此，您需要新增尾碼「`-content`&quot;到類名。 在下列範例中，已在主題的整個內容上新增變更列：

```css
...
/* for styling the topic's content */
.new-topic-content {
  -ro-change-bar-color: #A609CC;
}
...
```

使用上述樣式屬性，變更列會新增至 *飛行史* 主題，如下所示：

<img src="./assets/pdf-output-topic-content.jpg" width="500">


