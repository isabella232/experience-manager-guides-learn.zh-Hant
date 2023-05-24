---
title: 自訂工具列
description: 瞭解如何自訂工具列
source-git-commit: ef2e99db8c298d34af5777baa48886a55ac32590
workflow-type: tm+mt
source-wordcount: '894'
ht-degree: 0%

---


# 自訂工具列 {#id172FB00L0V6}

依預設，Web編輯器隨附任何DITA編輯器所需的最常見編輯功能。 編輯器中提供插入清單\（編號或專案符號\）型別、互動參照、內容參照、表格、段落和字元格式等元素的功能。 除了這些基本元素之外，您還可以自訂Web編輯器以插入在編寫環境中使用的元素。

自訂Web編輯器工具列有兩種方式：

- 將新功能新增至工具列

- 從工具列移除任何現有功能


## 在工具列中新增功能

將功能新增至Web編輯器涉及兩個主要工作 — 在中新增功能的圖示 *ui\_config.json* 檔案和在JavaScript中新增背景功能。

**在工具列中新增圖示**

執行以下步驟，將功能新增至Web編輯器的工具列：

1. 登入AEM並開啟CRXDE Lite模式。

1. 導覽至下列位置可用的預設組態檔：

   `/libs/fmdita/clientlibs/clientlibs/xmleditor/ui_config.json`

1. 在下列位置建立預設組態檔的復本：

   `/apps/fmdita/xmleditor/ui_config.json`

1. 導覽至並開啟 `ui_config.json` 中的檔案 `apps` 節點進行編輯。

1. 在 `ui_config.json` 檔案中，在工具列區段中新增新功能的定義。 通常，您可以建立新的工具列按鈕群組，並在其中新增一或多個工具列按鈕。 或者，您可以在現有的工具列群組中新增工具列按鈕。 建立新的工具列群組需要下列詳細資料：

   - **type：**Specify `blockGroup` 作為 `type` 值。 此值表示您正在建立包含一或多個工具列群組的區塊群組。

   - **類別：** 以空格分隔的一或多個類別的名稱。

   - **個專案：** 在工具列中指定所有群組的定義。 每個群組可以包含一或多個工具列圖示。 若要定義工具列群組中的圖示，您需要再次定義 `type` 內的屬性 `items`，並將其值設為 `buttonGroup`. 在中指定一或多個類別名稱 `extraclass` 屬性。 在中指定特徵名稱 `label` 屬性。 下列來自的程式碼片段 `ui_config.json` file顯示主要工具列區塊的定義，後面接著 `buttonGroup` 定義：

      ```json
      "toolbar": {    
        "type": "blockGroup",    
        "extraclass": 
        "toolbar operations",    
          "items": [      
            {        
              "type": "buttonGroup",        
              "extraclass": "left-controls",        
              "label": "Left Controls",        
              "items": [
      ```

      在內 `items` 收集時，您必須指定一或多個工具列圖示的定義。
您需要定義以下屬性以新增工具列圖示：

   - **型別：** 指定 `button` 作為 `type` 值。 此值表示您正在新增工具列按鈕。

   - **圖示：** 指定您要在工具列中使用的Coral圖示名稱。

   - **變體：** 指定 `quiet` 作為 `variant` 值。

   - **標題：** 指定圖示的工具提示。

   - **按一下：** 在JavaScript檔案中指定為特徵定義的命令名稱。 如果您的命令需要輸入引數，則將命令名稱指定為：

      ```JavaScript
      "on-click": {"name": "AUTHOR_INSERT_ELEMENT", "args": "simpletable"}
      ```

   - **顯示或隱藏：** 如果您要定義 `show` 屬性，然後指定圖示的顯示模式。 可能的值包括 —  `@isAuthorMode`， `@isSourceMode`， `@isPreviewMode`， `true` \（在所有模式中顯示\），或 `false` \（在所有模式中隱藏\）。

   取代 `show`，您也可以定義 `hide` 屬性。 可能的值與中的相同 `show` 屬性，唯一區別是圖示不會顯示在指定模式中。

1. 建立 *clientlib* 資料夾，並將您的JavaScript新增至此資料夾。

1. 更新「 」的「 」類別屬性 *clientlib* 資料夾，為其指派值 *apps.fmdita.xml\_editor.page\_overrides*.

1. 儲存 *ui\_config.json* 檔案並重新載入網頁編輯器。


**JavaScript程式碼範例**

本節提供兩個JavaScript程式碼範例，協助您開始新增自訂功能。 以下範例顯示使用者按一下工具列中的「顯示版本」圖示時AEM Guides的版本號碼。

將下列程式碼新增至JavaScript檔案：

```JavaScript
/**
* This file contains an example to show AEM Guides version 
* number when a user clicks on the Show Version icon in the toolbar. 
* Step 1. Create a clientlib folder and add save a file with your *JavaScript code into this folder. A code sample is shared below.
* Step 2: Update the categories property of the clientlib folder by *assigning it the value of 
* "apps.fmdita.xml_editor.page_overrides".
* Step 3: Add the feature in the ui_config.json file as shown after the *sample code. Save the ui_config.json file and reload the Web Editor
 */

(function (window) {
  "use strict";

  window.addEventListener('DOMContentLoaded', function () {
    fmxml.ready(function () {
      fmxml.eventHandler.subscribe({
        key: 'user.alert',
        next: function next() {
          alert("AEM Guides version x.x");
        }
      });
    });
  });
})(window);
```

在ui\_config.json檔案中新增功能為：

```json
 {
      "type": "button",
      "icon": "alert",
      "title": "About AEM Guides",
      "variant": "quiet",

  "show": "true",
      "on-click": "user.alert"
  } 
```

以下範例說明如何將使用中檔案的檔案狀態變更為「稽核中」。

```JavaScript
/**
* This file contains an example to set the document state of an active *open documen to "In-Review". 
* Step 1. Create a clientlib folder and add save a file with your *JavaScript code into this folder. A code sample is shared below.
* Step 2: Update the categories property of the clientlib folder by *assigning it the value of 
* "apps.fmdita.xml_editor.page_overrides".
* Step 3: Add the feature in the ui_config.json file as shown after the *sample code. Save the ui_config.json file and reload the Web Editor
 */

(function (window) {
  "use strict";

  //Wait for the page has been completely loaded 

  window.addEventListener('DOMContentLoaded', function () {

    //Wait for the xml editor to start
    fmxml.ready(function () {

      //Subscribe to 'user.docstate.to.in-review' event
      fmxml.eventHandler.subscribe({
        key: 'user.docstate.to.in-review',
        next: function next() {
          var docstate = "In-Review"; // New docstate name
          var filePath = fmxml.curEditor.filePath; 
// Get the file path of active open file
          if (filePath) {
            //Call API to change the doc state
            $.ajax({
              type: 'POST',
              url: '/bin/fmdita/states',
              data: {
                paths: filePath,
                operation: "setdocstates",
                docstate: docstate
              }
            }).fail(function (xhr, textStatus, errorThrown) {
              console.error("Cannot update docstate to " + docstate);
            }).success(function (data) {
              console.log('docstate updated to ' + docstate);
            });
          }
        }
      });
    });
  });
})(window);
```

在ui\_config.json檔案中新增功能為：

```json
 {
      "type": "button",
      "icon": "actions",
      "title": "Change document state to In-Review",
      "variant": "quiet",
      "show": "true",
      "on-click": "user.docstate.to.in-review"
    } 
```

## 從工具列移除功能

有時您可能不想提供網頁編輯器中目前可用的所有功能，在這種情況下，您可以從網頁編輯器的工具列移除不需要的功能。

執行以下步驟，從工具列移除任何不需要的特徵：

1. 登入AEM並開啟CRXDE Lite模式。

1. 導覽至下列位置可用的預設組態檔：。

   `/libs/fmdita/clientlibs/clientlibs/xmleditor/ui_config.json`

1. 在下列位置建立預設組態檔的復本：

   `/apps/fmdita/xmleditor/ui_config.json`

1. 導覽至並開啟 `ui_config.json` 中的檔案 `apps` 節點進行編輯。
此 `ui_config.json` 檔案有三個區段：

- **工具列：**   本節包含編輯器工具列中所有可用功能的定義，例如「插入/移除編號清單」、「\(file\)關閉」、「儲存」、「註解」等。

- **捷徑：**   本節包含指定給編輯器中特定功能的鍵盤快速鍵定義。

- **範本：**   本節包含您可在檔案中使用的DITA元素的預先定義結構。 依照預設，「範本」區段包含段落、簡單表格、表格和本文元素的範本定義。 您可以為所要的元素新增有效的XML結構，以建立任何元素的範本定義。 例如，如果您想要新增 `p` 元素，每個新增 `li` 元素清單中，您可以在範本區段的結尾新增下列程式碼以達成此目的：

```HTML
"li": "<li><p></p></li>"
```

1. 從工具列區段中，移除您不想向使用者公開的功能專案。

1. 儲存 *ui\_config.json* 檔案並重新載入網頁編輯器。


**父級主題：**[&#x200B;自訂Web編輯器](conf-web-editor.md)

