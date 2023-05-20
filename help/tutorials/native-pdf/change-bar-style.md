---
title: 本機PDF發佈功能 |使用自定義更改條樣式
description: 瞭解如何在更改條上應用樣式。
exl-id: a81ec56c-ccbb-4599-a696-8edef7a73cdd
source-git-commit: 7b48633ef2418fa7c91842a8d2c2a4177017ef58
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# 使用自定義更改條樣式

更改欄是可直觀標識新內容或修訂內容的垂直線。 參AEM考線允許您在主題內更改的內容左側顯示更改欄，也可在PDF輸出目錄中顯示更改的主題。

有關顯示更改欄的詳細資訊，請參閱 *在已發佈版本之間建立帶更改欄的PDF* 設定 [發佈PDF輸出](../web-editor/native-pdf-web-editor.md)。

## 主題內更改的內容

更改欄顯示在已插入、更改或刪除的主題的內容的左側。

可以修改以下樣式以顯示更改的內容以及更改條之間的內容。


>[!NOTE]
>
>這些樣式是 `layout.css` 檔案，您可以根據需要編輯它們。

例如，可以在 `.inserted-block` 樣式，以定義插入內容在已發佈PDF輸出中的顯示方式。


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

同樣，您可以 `.deleted-block` 樣式，以定義刪除內容在已發佈PDF輸出中的顯示方式。

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

您可以使用 `.inserted-change-bar` 和 `.deleted-change-bar` 樣式，修改更新內容左側顯示的更改條的外觀。

例如，您可以 `-ro-change-bar-color` 屬性 `.inserted-change-bar` 的子菜單。 您還可以使用 `-ro-change-bar-color` 屬性 `.deleted-change-bar` 的子菜單。

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

<img src="./assets/changed-bar-content.png" alt="更改的欄主題內容" width="500">

## 目錄(TOC)中更改的主題

也可以在PDF輸出的目錄中在更改主題的左側添加更改欄。 您可以使用 `-ro-change-bar-color` 屬性 `.changed-topic` 的子菜單。

例如，可以添加綠色更改欄。

```css
...
.changed-topic { 
 -ro-change-bar-color: #2ECC40; 
}  
...
```


這將針對TOC中的所有主題顯示一個綠色的更改欄，其中已進行了一些更新。 可以按一下目錄中的更改主題並查看詳細更改。

<img src="./assets/changed-bar-TOC.png" alt="更改的欄目目錄" width="500">
