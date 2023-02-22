---
title: 原生PDF發佈功能 |在PDF輸出中新增自訂書籤
description: 了解如何建立使用樣式表和建立內容的樣式。
source-git-commit: fb7ffbaefcdca4302e43d8369bc056c1f08a3ed6
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 0%

---


# 在PDF輸出中新增自訂書籤

通常，DITA映射中的TOC在最終PDF輸出中會複製為書籤。 此目錄是從DITA映射中的主題或區段標題建立。 有時，您可能會想要在PDF輸出中的特定內容上新增自訂書籤，以方便導覽。 這可借由新增 `outputclass` 屬性，並套用下列屬性至元素：

`bookmark-level: 3`

這裡， `bookmark-level` 是屬性和數字 `3` 是指出書籤階層中新增書籤的層級的值。 在以下示例中，第一級主題「聯繫人」有一個表，即「聯繫人清單」，我們已在其中添加了 `outputclass` 屬性值為 `custom-bookmark`.


<img src="./assets/custom-bookmark-attribute.png" width="500">

以下定義 `custom-bookmark` 類別會新增至CSS檔案中：

```css
…
/*Adding a custom bookmark*/
.custom-bookmark{
    bookmark-level: 2
}
…
```

在PDF輸出中， *聯繫人清單* 表格會新增在「PDF書籤」清單的第2層，如下所示：

<img src="./assets/custom-bookmark-in-pdf-output.png" width="500">

>[!NOTE]
>
>您必須選擇自訂書籤的新增位置。 如果指定的數字小於父主題的書籤，則自定義書籤將佔據父書籤的位置，所有其他書籤將顯示為子書籤。 這可能會導致非預期的書籤結構。

