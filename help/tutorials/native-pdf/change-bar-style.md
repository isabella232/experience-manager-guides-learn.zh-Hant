---
title: 原生PDF發佈功能 |使用自訂變更列樣式
description: 瞭解如何在變更列上套用樣式。
exl-id: a81ec56c-ccbb-4599-a696-8edef7a73cdd
source-git-commit: 7b48633ef2418fa7c91842a8d2c2a4177017ef58
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# 使用自訂變更列樣式

變更列是垂直線，可在視覺上識別新內容或修訂的內容。 AEM Guides可讓您在主題內已變更內容的左側顯示變更列，也可在PDF輸出的目錄(TOC)中顯示已變更的主題。

如需顯示變更列的詳細資訊，請參閱 *在已發佈版本之間使用變更列建立PDF* 設定於 [發佈PDF輸出](../web-editor/native-pdf-web-editor.md).

## 主題中變更的內容

變更列會顯示在已插入、變更或刪除之主題的內容左側。

您可以修改下列樣式，以顯示變更的內容以及變更列。


>[!NOTE]
>
>這些樣式是 `layout.css` 檔案，您可以視需要加以編輯。

例如，您可以在 `.inserted-block` 樣式定義插入內容在發佈PDF輸出中的顯示方式。


```css
...
.inserted-block { 
  color: #2ECC40; 
  display: inline; 
  -ro-comment-content: " "; 
  -ro-comment-style: underline; 
  -ro-comment-title: "Inserted"; 
  -ro-comment-date: attr(data-time); 
  -ro-comment-dateformat: "yyyy/dd/MM HH:mm:ss"; 
} 
...
```

同樣地，您可以使用 `.deleted-block` 樣式來定義已刪除內容在發佈PDF輸出中的顯示方式。

```css
...
.deleted-block { 
  display: inline; 
  color: #FF6961; 
  text-decoration: line-through; 
  -ro-comment-content: " "; 
  -ro-comment-style: strikeout; 
  -ro-comment-title: "Deleted"; 
  -ro-comment-date: attr(data-time); 
  -ro-comment-dateformat: "yyyy/dd/MM HH:mm:ss"; 
} 
...
```

您可以使用 `.inserted-change-bar` 和 `.deleted-change-bar` 樣式來修改出現在更新內容左側的變更列的外觀。

例如，您可以使用 `-ro-change-bar-color` 中的屬性 `.inserted-change-bar` 以綠色顯示插入的變更列的樣式。 您也可以使用 `-ro-change-bar-color` 中的屬性 `.deleted-change-bar` 以紅色顯示刪除的變更列樣式。

```css
...
.inserted-change-bar { 
  -ro-change-bar-color: #2ECC40; 
} 

.deleted-change-bar { 
  -ro-change-bar-color: #FF6961; 
  } 
...
```

<img src="./assets/changed-bar-content.png" alt="變更的列主題內容" width="500">

## 目錄(TOC)中變更的主題

您也可以在PDF輸出的目錄，在已變更主題左側新增變更列。 您可以使用 `-ro-change-bar-color` 中的屬性 `.changed-topic` 樣式，以您選擇的顏色為目錄清單中更新的主題新增變更列。

例如，您可以新增綠色的變更列。

```css
...
.changed-topic { 
 -ro-change-bar-color: #2ECC40; 
}  
...
```


這會針對目錄中所有已完成部分更新的主題顯示綠色變更列。 您可以按一下目錄中已變更的主題，並檢視詳細的變更。

<img src="./assets/changed-bar-TOC.png" alt="變更的橫條目錄" width="500">
