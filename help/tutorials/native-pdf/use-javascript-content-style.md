---
title: 原生PDF發佈功能 |使用JavaScript處理內容或樣式
description: 瞭解如何建立使用樣式表及內容的樣式。
exl-id: 2f301f6a-0d1c-4194-84c2-0fddaef8d3ec
source-git-commit: 99ca14a816630f5f0ec1dc72ba77994ffa71dff6
workflow-type: tm+mt
source-wordcount: '519'
ht-degree: 0%

---

# 使用JavaScript處理內容或樣式

原生PDF發佈功能可讓您執行JavaScript，以在產生最終PDF之前操控內容上套用的內容或樣式。 此功能可讓您完全控制最終輸出的產生方式。 例如，您可能想要將法律宣告資訊新增至位於其他PDF中的PDF輸出。 使用JavaScript，您可以在為基本內容建立PDF後，但在產生最終PDF之前，新增法律宣告資訊。\
為了支援JavaScript執行，「原生PDF發佈」功能提供下列回呼函式：

* `window.pdfLayout.onBeforeCreateTOC(callback)`：此回呼函式會在產生目錄之前執行。
* `window.pdfLayout.onBeforePagination(callback)`：此回呼函式會在產生目錄之後、但在PDF中新增分頁符號之前執行。
* `window.pdfLayout.onAfterPagination(callback)`：此回呼函式會在PDF中新增目錄和分頁符號之後執行。

>[!NOTE]
>
>在內部，會維護這些圖說文字函式的執行順序。 首先執行onBeforeCreateTOC，接著執行onBeforePagination，最後執行onAfterPagination。

您可以根據要執行的內容型別或樣式修改，選擇要使用的回呼函式。 例如，如果您想要新增內容，建議在產生目錄之前進行。 同樣地，如果您想要進行一些樣式更新，則可以在分頁之前或之後完成這些更新。

在下列範例中，插圖示題的位置從影像上方變更為影像下方。 為此，您需要在預設集中啟用JavaScript執行選項。 要執行此操作，請執行下列步驟：

1. 開啟預設集以進行編輯。
1. 前往 **進階** 標籤。
1. 選取 **啟用JavaScript** 選項。
1. 儲存預設集並關閉。

接下來，使用下列程式碼建立JavaScript檔案，並將其儲存在範本的Resources資料夾中：

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
>此 `window.addEventListener('DOMContentLoaded', function ()` 必須先呼叫函式才能使用回呼函式。

接下來，必須從用來產生PDF輸出的範本檔案呼叫此指令碼。 例如，我們會將其新增到目錄範本中。 確保 `<script>` 標籤會新增到預先定義的 `<div>` 標籤內 `<body>` 標籤之間。 如果您將其新增至 `<head>` 標籤或外部 `<body>` 標籤時，不會執行指令碼。

<img src="./assets/js-added-resources-template.png" width="500">

使用此程式碼產生的輸出，以及範本在影像下方顯示圖示題：

<img src="./assets/fig-title-below-image.png" width="500">

## 在草稿檔案的PDF輸出中新增浮水印 {#watermark-draft-document}

您也可以使用JavaScript來新增條件式浮水印。 當滿足定義的條件時，這些浮水印會新增到您的檔案中。\
例如，您可以使用以下程式碼建立JavaScript檔案，為尚未核准的檔案的PDF輸出建立浮水印。 如果您為「已核准」docstate中的檔案產生PDF，則不會顯示此浮水印。

```css
...
/*
* This file can be used to add a watermark to the PDF output
* */

window.addEventListener('DOMContentLoaded', function () {
    var watermark = 'Draft'
    var metaTag = document.getElementsByTagName('meta')
    css = "@page {\n  @left-middle {\n    content: \"".concat(watermark, "\";\n    z-index: 100;\n    font-family: sans-serif;\n    font-size: 80pt;\n    font-weight: bold;\n    color: gray(0, 0.3);\n    text-align: center;\n    transform: rotate(-54.7deg);\n    position: absolute;\n    left: 0;\n    top: 0;\n    width: 100%;\n    height: 100%;\n  }\n}")
    head = document.head || document.getElementsByTagName('head')[0], style = document.createElement('style');
    style.appendChild(document.createTextNode(css));
    window.pdfLayout.onBeforePagination(function () {
        for (let i = 0; i < metaTag.length; i++) {
            if (metaTag[i].getAttribute('name') === 'docstate' && metaTag[i].getAttribute('value') !== 'Approved') {
                head.appendChild(style);
            }
        }
    })
});
...
```

使用此程式碼產生的PDF輸出會顯示浮水印 *草稿* 在檔案的封面頁上：

<img src="./assets/draft-watermark.png" width="500">
