---
title: 本機PDF發佈功能 |在PDF輸出中添加自定義書籤
description: 瞭解如何建立使用樣式表和為內容建立樣式。
exl-id: 6e6dbba3-da41-4066-b7b2-735a3d92b70a
source-git-commit: e2349fc14143e5e49f8672ef1bfa48984df3b1c7
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 0%

---

# 在PDF輸出中添加自定義書籤

通常，DITA映射中的目錄在最終PDF輸出中被複製為書籤。 此目錄是從DITA映射中的主題或節標題建立的。 有時，您可能希望在PDF輸出中的特定內容上添加自定義書籤，以便輕鬆導航。 這可以通過添加 `outputclass` 元素上的屬性，並將以下屬性應用於元素：

`bookmark-level: 3`

這裡， `bookmark-level` 是屬性和數字 `3` 是指示添加書籤的書籤層次結構中的級別的值。 在以下示例中，第一級主題「聯繫人」有一個表，「聯繫人清單」，我們已在其上添加了 `outputclass` 值為 `custom-bookmark`。


<img src="./assets/custom-bookmark-attribute.png" width="500">

以下定義 `custom-bookmark` 類添加到CSS檔案中：

```css
…
/*Adding a custom bookmark*/
.custom-bookmark{
    bookmark-level: 2
}
…
```

在PDF輸出中， *聯繫人清單* 表添加在PDF書籤清單的第2級，如下所示：

<img src="./assets/custom-bookmark-in-pdf-output.png" width="500">

>[!NOTE]
>
>必須選擇添加自定義書籤的正確級別。 如果指定的數字小於父主題的書籤，則自定義書籤將佔據父書籤的位置，所有其他書籤都顯示為子書籤。 這可能導致意外的書籤結構。
