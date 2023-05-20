---
title: 本機PDF發佈功能 |使用JavaScript處理內容或樣式
description: 瞭解如何建立使用樣式表和為內容建立樣式。
exl-id: 2f301f6a-0d1c-4194-84c2-0fddaef8d3ec
source-git-commit: e2349fc14143e5e49f8672ef1bfa48984df3b1c7
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# 使用JavaScript處理內容或樣式

「本機PDF發佈」功能允許您運行JavaScript，以在生成最終PDF之前處理應用於內容的內容或樣式。 此功能使您能夠完全控制如何生成最終輸出。 例如，您可能希望將法律通知資訊添加到PDF輸出中，該輸出位於另一PDF中。 使用JavaScript，您可以在為基本內容建立PDF後，在生成最終PDF之前添加法律通知資訊。\
為支援JavaScript執行，本機PDF發佈功能提供了以下回調函式：

* `window.pdfLayout.onBeforeCreateTOC(callback)`:此回調函式在生成TOC之前執行。
* `window.pdfLayout.onBeforePagination(callback)`:此回調函式在生成TOC後執行，但在PDF中添加分頁符之前執行。
* `window.pdfLayout.onAfterPagination(callback)`:此回調函式在TOC後執行，並在PDF中添加分頁符。

>[!NOTE]
>
>在內部，這些標注函式將保持執行序列。 首先，執行onBeforeCreateTOC，然後執行onBeforePagination，最後執行onAfterPagination。

根據要執行的內容類型或樣式修改類型，可以選擇使用哪個回調函式。 例如，如果要添加內容，則建議在生成目錄之前先進行添加。 同樣，如果要進行一些樣式更新，則可以在分頁之前或之後完成這些更新。

在下例中，表徵圖的位置從影像上方更改為影像下方。 為此，需要在預設中啟用JavaScript執行選項。 為此，請執行以下步驟：

1. 開啟預設進行編輯。
1. 轉到 **高級** 頁籤。
1. 選擇 **啟用JavaScript** 的雙曲餘切值。
1. 保存預設並關閉。

接下來，使用以下代碼建立JavaScript檔案，並將其保存在模板的「資源」資料夾中：

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
>的 `window.addEventListener('DOMContentLoaded', function ()` 在使用回調函式之前必須調用函式。

接下來，必須從用於生成PDF輸出的模板檔案調用此指令碼。 例如，我們將在TOC模板中添加它。 確保 `<script>` 標籤被添加到預定義的 `<div>` 標籤在 `<body>` 標籤。 如果在 `<head>` 標籤或外部 `<body>` 標籤，指令碼將不執行。

<img src="./assets/js-added-resources-template.png" width="500">

使用此代碼生成的輸出，模板將在影像下顯示表徵圖：

<img src="./assets/fig-title-below-image.png" width="500">
