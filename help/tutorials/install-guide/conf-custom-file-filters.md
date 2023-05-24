---
title: 設定檔案瀏覽對話方塊的篩選器
description: 瞭解如何設定檔案瀏覽對話方塊的篩選器
source-git-commit: 5ac066bb8db32944abd046f64da11eeb1bdbe467
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---


# 設定檔案瀏覽對話方塊的篩選器 {#id20CIL7009GN}

在Web編輯器中工作時，您需要使用檔案瀏覽對話方塊來插入影像、參照或關鍵參照等元素。 預設檔案瀏覽對話方塊不提供任何檔案篩選選項。 您可以新增自己的篩選器，讓您輕鬆快速地存取所需檔案。

執行以下步驟，將自訂檔案篩選選項新增至檔案瀏覽對話方塊：

1. 登入AEM並開啟CRXDE Lite模式。

1. 導覽至下列位置可用的預設組態檔：

   `/libs/fmdita/clientlibs/clientlibs/xmleditor/ui_config.json`

1. 在下列位置建立預設組態檔的復本：

   `/apps/fmdita/xmleditor/ui_config.json`

1. 導覽至並開啟 `ui_config.json` 中的檔案 `apps` 節點進行編輯。

1. 在 `ui_config.json` 檔案中，新增您要新增之篩選器的定義。

   下列程式碼片段顯示如何新增兩個篩選選項 — DITA檔案和影像檔案。

   ```json
   "browseFilters": [
       {
         "title": "DITA Files",
         "property": "jcr:content/metadata/dita_class",
         "operation": "exists"
       },
       {
         "title": "Image Files",
         "property": "jcr:content/metadata/dc:format",
         "value": [        
           "image/jpeg",
           "image/gif",
           "image/png"
         ]
       }
   ]
   ```

   在上述程式碼片段中，第一個篩選條件適用於DITA檔案。 篩選定義會採用下列引數：

   - **標題：**   篩選的顯示名稱。 此標題在檔案瀏覽對話方塊中顯示為篩選選項。

   - **屬性：**   要符合檔案中繼資料的屬性。 例如，若要僅允許具有 `dita_class` 屬性中的中繼資料，屬性篩選器會採用&quot;`jcr:content/metadata/dita_class`「」作為其值。

   - **作業：**   指定&quot;`exists`&quot;，以符合屬性引數中指定的值是否存在。

   第二個濾鏡是用於「影像檔案」。 這些引數類似於第一個篩選器，只是 `value` 引數。 此 `value` 引數會以一組影像型別作為其值。 系統會搜尋在value引數中指定的所有檔案型別，並在檔案瀏覽對話方塊中顯示，而會忽略所有其他檔案型別。

1. 儲存 *ui\_config.json* 檔案並重新載入網頁編輯器。

   當您啟動檔案瀏覽對話方塊時，會顯示在ui\_config.json檔案中設定的篩選選項。

   ![](assets/file-browse-custom-filters.png){width="300" align="left"}


