---
title: 本機PDF發佈功能 |對目錄條目和主題內容應用自定義樣式
description: 瞭解如何建立使用樣式表和為內容建立樣式。
exl-id: f65c9683-a1fc-432a-854b-83e8f39d7dae
source-git-commit: e2349fc14143e5e49f8672ef1bfa48984df3b1c7
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# 對目錄條目和主題內容應用自定義樣式

有時，您可能希望對目錄條目或特定主題應用自定義樣式。 這可以通過關聯 `outputclass` 屬性 `<topicref>` DITA映射中的元素。 此外，如果要將自定義格式應用於整個主題，也可以通過在CSS中擴展屬性的樣式定義來實現。

讓我們舉一個要發送以供審閱的新主題的示例。 為了方便地識別更新的主題，您需要添加 `outputclass` 屬性 `<topicref>` 在DITA映射中定義元素，然後在CSS中為其定義自定義樣式。

在以下示例中， *飛行歷史* 已分配主題 `outputclass` 值為 `new-topic`。

<img src="./assets/new-topic-attribute-in-map.png" width="500">

的類定義 `new-topic` 在CSS中，可以定義以下項的樣式：
* TOC或mini-TOC中的主條目
* 主要內容中主題的標題
* 主題的整個內容，包括標題

讓我們看一下CSS中如何定義這些方案。 在以下CSS定義中 `new-topic` 文本顏色已更改。

```css
…
.new-topic {
  color: #CC5309
}
…
```

此定義控制目錄中文本的顏色和主題標題。 以下PDF輸出顯示了TOC條目上應用的不同顏色：

<img src="./assets/pdf-output-toc-entry.jpg" width="500">

主題的標題也使用相同顏色進行樣式設定。

<img src="./assets/pdf-output-topic-title.jpg" width="500">

如果希望目錄條目和主題標題具有不同的樣式，則可以分別定義它們，如下所示：

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

最後，您還可以對主題內的整個內容應用樣式。 為此，需要添加尾碼「」`-content`&quot;到類名。 在以下示例中，在主題的整個內容上添加了一個更改欄：

```css
...
/* for styling the topic's content */
.new-topic-content {
  -ro-change-bar-color: #A609CC;
}
...
```

使用上述樣式屬性，在 *飛行史* 主題，如下所示：

<img src="./assets/pdf-output-topic-content.jpg" width="500">
