---
title: 原生PDF發佈功能 |使用JavaScript處理內容或樣式
description: 了解如何建立使用樣式表和建立內容的樣式。
source-git-commit: 09918abbdade934468dea1c55d0ca2cd60622b35
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---


# 使用JavaScript處理內容或樣式

「原生PDF發佈」功能可讓您在產生最終PDF之前，執行JavaScript以操控套用至內容的內容或樣式。 此功能可讓您完全控制最終輸出的產生方式。 例如，您可能想要將法律通知資訊新增至PDF輸出，而該輸出位於其他PDF。 使用JavaScript，您可以在為基本內容建立PDF後，但在產生最終PDF之前，新增法律通知資訊。\
為了支援JavaScript執行，原生PDF發佈功能提供下列回呼函式：

* `window.pdfLayout.onBeforeCreateTOC(callback)`:此回呼函式會在產生TOC之前執行。
* `window.pdfLayout.onBeforePagination(callback)`:此回呼函式會在產生TOC後，但在新增分頁符至PDF之前執行。
* `window.pdfLayout.onAfterPagination(callback)`:此回呼函式會在TOC之後執行，且PDF中會新增分頁符。

>[!NOTE]
>
>在內部，這些註解函式的執行順序會保持不變。 首先，會執行onBeforeCreateTOC，接著執行onBeforePagination，最後執行onAfterPagination。

您可以根據要執行的內容或樣式修改類型，選擇要使用的回呼函式。 例如，如果您想要新增內容，則建議在產生目錄之前執行。 同樣地，如果您想進行一些樣式更新，則可在分頁之前或之後完成。

在以下示例中，表徵圖的位置從影像上方更改為影像下方。 為此，您必須在預設集中啟用JavaScript執行選項。 要執行此操作，請執行以下步驟：

1. 開啟預設集以進行編輯。
1. 前往 **進階** 標籤。
1. 選取 **啟用JavaScript** 選項。
1. 儲存預設集並關閉。

接下來，使用下列程式碼建立JavaScript檔案，並將其儲存在範本的「資源」資料夾中：

```css
...
/*
* DITA only allows the figure title to be placed above images 
* This JavaScript code is used to move the figure title below the image
* */
window.addEventListener('DOMContentLoaded', function () {
    window.pdfLayout.onBeforeCreateTOC(function() {
        var titleNodes = document.querySelectorAll('.fig > .title')
        for (var i = 0; i < titleNodes.length; i++) {
            var titleNode = titleNodes[i]
            var figNode = titleNode.parentNode
            var imageNode = figNode.querySelector('.image')
            if(imageNode && imageNode.parentNode !== figNode) {
              imageNode = imageNode.parentNode
            }
            if (figNode && imageNode && imageNode.parentNode === figNode) {
                figNode.insertBefore(imageNode, titleNode)
            }
        }
    })
});
...
```

>[!NOTE]
>
>此 `window.addEventListener('DOMContentLoaded', function ()` 函式，才能使用回呼函式。

接下來，必須從用於產生PDF輸出的範本檔案中呼叫此指令碼。 例如，我們會在目錄範本中新增它。 確保 `<script>` 標籤會新增至預先定義的 `<div>` 標籤內 `<body>` 標籤。 若您將其新增至 `<head>` 標籤或在 `<body>` 標籤中，指令碼將不會執行。

<img src="./assets/js-added-resources-template.png" width="500">

使用此代碼生成的輸出，模板將在影像下顯示表徵圖：

<img src="./assets/fig-title-below-image.png" width="500">
