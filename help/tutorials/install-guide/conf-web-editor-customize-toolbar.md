---
title: 自定義工具欄
description: 瞭解如何自定義工具欄
source-git-commit: ef2e99db8c298d34af5777baa48886a55ac32590
workflow-type: tm+mt
source-wordcount: '894'
ht-degree: 0%

---


# 自定義工具欄 {#id172FB00L0V6}

預設情況下，Web編輯器隨任何DITA編輯器所需的最常見編輯功能一起提供。 編輯器中提供了插入清單\（編號或項目符號\）類型的元素、交叉引用、內容引用、表、段落和字元格式等功能。 除了這些基本元素外，還可以自定義Web編輯器以插入在創作環境中使用的元素。

自定義Web編輯器工具欄有兩種方法：

- 向工具欄添加新功能

- 從工具欄中刪除任何現有功能


## 在工具欄中添加功能

向Web編輯器添加功能涉及兩個主要任務 — 在 *ui\_config_json* 檔案，並在JavaScript中添加後台功能。

**在工具欄中添加表徵圖**

執行以下步驟，將功能添加到Web編輯器的工具欄中：

1. 登錄並AEM開啟CRXDE Lite模式。

1. 導航到以下位置可用的預設配置檔案：

   `/libs/fmdita/clientlibs/clientlibs/xmleditor/ui_config.json`

1. 在以下位置建立預設配置檔案的副本：

   `/apps/fmdita/xmleditor/ui_config.json`

1. 導航到並開啟 `ui_config.json` 檔案 `apps` 的子菜單。

1. 在 `ui_config.json` 檔案，在工具欄部分中添加新功能的定義。 通常，可以建立新工具欄按鈕組並向其添加一個或多個工具欄按鈕。 或者，可以在現有工具欄組中添加新工具欄按鈕。 建立新工具欄組需要以下詳細資訊：

   - **類型：**指定 `blockGroup` 的 `type` 值。 此值表示您正在建立包含一個或多個工具欄組的塊組。

   - **提取類：** 用空格分隔的類或類的名稱。

   - **項目：** 指定工具欄中所有組的定義。 每個組可包含一個或多個工具欄表徵圖。 要在工具欄組中定義表徵圖，需要再次定義 `type` 屬性 `items`，將其值設定為 `buttonGroup`。 在 `extraclass` 屬性。 在 `label` 屬性。 以下代碼段 `ui_config.json` 檔案顯示主工具欄塊的定義，然後是 `buttonGroup` 定義：

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

      在 `items` ，您需要為一個或多個工具欄表徵圖指定定義。
要添加工具欄表徵圖，需要定義以下屬性：

   - **類型：** 指定 `button` 的 `type` 值。 此值表示您正在添加工具欄按鈕。

   - **表徵圖：** 指定要在工具欄中使用的珊瑚表徵圖的名稱。

   - **變型：** 指定 `quiet` 的 `variant` 值。

   - **標題：** 指定表徵圖的工具提示。

   - **按一下：** 在JavaScript檔案中指定為該功能定義的命令名。 如果命令需要輸入參數，則將命令名稱指定為：

      ```JavaScript
      "on-click": {"name": "AUTHOR_INSERT_ELEMENT", "args": "simpletable"}
      ```

   - **顯示或隱藏：** 如果要定義 `show` 屬性，然後指定表徵圖的顯示模式。 可能的值為 —  `@isAuthorMode`。 `@isSourceMode`。 `@isPreviewMode`。 `true` \（以所有模式顯示\），或 `false` \（在所有模式下隱藏\）。

   代替 `show`，也可以定義 `hide` 屬性。 可能的值與中相同 `show` 屬性的唯一區別是指定模式不顯示表徵圖。

1. 建立 *客戶端庫* 資料夾，並將JavaScript添加到此資料夾中。

1. 更新的類別屬性 *客戶端庫* 資料夾的值 *apps.fmdita.xml\_editor.page\_overrides*。

1. 保存 *ui\_config_json* 檔案並重新載入Web編輯器。


**JavaScript代碼示例**

本節提供了兩個JavaScript代碼示例，這些示例將幫助您開始添加自定義功能。 以下示例顯示AEM當用戶按一下工具欄中的「顯示版本」表徵圖時的「參考線」版本號。

將以下代碼添加到JavaScript檔案：

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

將ui\_config.json檔案中的功能添加為：

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

以下示例說明如何將文檔的活動檔案狀態更改為「正在審閱」。

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

將ui\_config.json檔案中的功能添加為：

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

## 從工具欄中刪除特徵

有時您可能不想提供Web編輯器中當前可用的所有功能，在這種情況下，您可以從Web編輯器的工具欄中刪除不需要的功能。

執行以下步驟，從工具欄中刪除任何不需要的特徵：

1. 登錄並AEM開啟CRXDE Lite模式。

1. 導航到以下位置可用的預設配置檔案：。

   `/libs/fmdita/clientlibs/clientlibs/xmleditor/ui_config.json`

1. 在以下位置建立預設配置檔案的副本：

   `/apps/fmdita/xmleditor/ui_config.json`

1. 導航到並開啟 `ui_config.json` 檔案 `apps` 的子菜單。
的 `ui_config.json` 檔案有三個部分：

- **工具欄：**   本節包含編輯器工具欄中可用的所有功能的定義，如插入/刪除編號清單、\(file\)關閉、保存、注釋等。

- **快捷方式：**   本節包含分配給編輯器中特定功能的鍵盤快捷鍵的定義。

- **模板：**   本節包含可在文檔中使用的DITA元素的預定義結構。 預設情況下，模板部分包含段落、簡單表、表和正文元素的模板定義。 通過為所需元素添加有效的XML結構，可以為任何元素建立模板定義。 例如，如果要添加 `p` 每個新元素 `li` 元素中，可以在模板部分的末尾添加以下代碼來實現此目的：

```HTML
"li": "<li><p></p></li>"
```

1. 在工具欄部分中，刪除您不想向用戶公開的功能條目。

1. 保存 *ui\_config_json* 檔案並重新載入Web編輯器。


**父主題：**[&#x200B;自定義Web編輯器](conf-web-editor.md)

