---
title: 原生PDF發佈功能 |使用自訂變更列樣式
description: 了解如何在變更列上套用樣式。
source-git-commit: 79de97e667bffae8d120deee68a0a82011047cf5
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# 使用自訂變更列樣式

變更列是可視覺識別新內容或修訂內容的垂直線。 AEM指南可讓您在主題內已變更內容的左側顯示變更列，以及在PDF輸出的目錄中也顯示已變更的主題。

如需顯示變更列的詳細資訊，請參閱 *建立PDF，並在已發佈版本之間使用變更列* 設定
[發佈PDF輸出](../web-editor/native-pdf-web-editor.md).

## 變更主題內的內容

變更列會顯示在已插入、變更或刪除的主題中的內容左側。

您可以修改下列樣式以顯示已變更的內容，以及其中包含變更列。


>[!NOTE]
>
>這些樣式是 `layout.css` ，您可以視需要編輯它們。

例如，您可以在 `.inserted-block` 樣式來定義插入內容在已發佈PDF輸出中的顯示方式。


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

同樣地，您也可以使用 `.deleted-block` 樣式來定義已刪除內容在已發佈PDF輸出中的顯示方式。

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

您可以使用 `.inserted-change-bar` 和 `.deleted-change-bar` 樣式，修改顯示在更新內容左側的更改條的外觀。

例如，您可以使用 `-ro-change-bar-color` 屬性 `.inserted-change-bar` 的子菜單。 您也可以使用 `-ro-change-bar-color` 屬性 `.deleted-change-bar` 樣式以紅色顯示已刪除的更改欄。

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

<img src="./assets/changed-bar-content.png" alt="變更長條主題內容" width="500">

## 變更目錄(TOC)中的主題

您也可以在PDF輸出的目錄中，在已變更主題的左側新增變更列。 您可以使用 `-ro-change-bar-color` 屬性 `.changed-topic` 樣式，在目錄清單中針對更新的主題，在您選擇的顏色中新增變更列。

例如，您可以新增綠色的變更列。

```css
...
.changed-topic { 
 -ro-change-bar-color: #2ECC40; 
}  
...
```


這會針對目錄中已完成部分更新的所有主題，顯示綠色的變更列。 您可以在目錄中按一下已變更的主題，並檢視詳細變更。

<img src="./assets/changed-bar-TOC.png" alt="變更長條目錄" width="500">
