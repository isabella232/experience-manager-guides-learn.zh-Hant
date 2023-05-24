---
title: 原生PDF發佈功能 |在PDF輸出中新增自訂書籤
description: 瞭解如何建立使用樣式表及內容的樣式。
exl-id: 6e6dbba3-da41-4066-b7b2-735a3d92b70a
source-git-commit: e2349fc14143e5e49f8672ef1bfa48984df3b1c7
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 0%

---

# 在PDF輸出中新增自訂書籤

一般而言，DITA map中的TOC會復製為最終PDF輸出中的書籤。 此TOC是根據DITA map中的主題或區段標題建立的。 有時您可能想要在PDF輸出中的特定內容上新增自訂書籤，以方便瀏覽。 這可透過新增 `outputclass` 屬性，並將下列屬性套用至該元素：

`bookmark-level: 3`

在此， `bookmark-level` 是屬性和數字 `3` 是指示書籤階層中新增書籤的層級的值。 在下列範例中，第一層級主題「連絡人」有一個表格「連絡人清單」，我們已在該表格上新增 `outputclass` 屬性值為的屬性 `custom-bookmark`.


<img src="./assets/custom-bookmark-attribute.png" width="500">

下列定義 `custom-bookmark` 類別已新增至CSS檔案：

```css
…
/*Adding a custom bookmark*/
.custom-bookmark{
    bookmark-level: 2
}
…
```

在PDF輸出中， *連絡人清單* 表格會新增至PDF書籤清單的第2層，如下所示：

<img src="./assets/custom-bookmark-in-pdf-output.png" width="500">

>[!NOTE]
>
>您必須選擇新增自訂書籤的正確層級。 如果您指定的數字小於父級主題的書籤，則自訂書籤會佔據父級書籤的位置，而所有其他書籤都會顯示為子系。 這可能會導致意外的書籤結構。
