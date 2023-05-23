---
title: 為檔案瀏覽對話框配置篩選器
description: 瞭解如何為檔案瀏覽對話框配置篩選器
source-git-commit: 5ac066bb8db32944abd046f64da11eeb1bdbe467
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---


# 為檔案瀏覽對話框配置篩選器 {#id20CIL7009GN}

在Web編輯器中工作時，需要使用檔案瀏覽對話框來插入像影像、引用或鍵引用這樣的元素。 預設檔案瀏覽對話框不提供任何檔案篩選選項。 您可以添加自己的篩選器，以便您輕鬆快速地訪問所需的檔案。

執行以下步驟，將自定義檔案篩選選項添加到檔案瀏覽對話框：

1. 登錄並AEM開啟CRXDE Lite模式。

1. 導航到以下位置可用的預設配置檔案：

   `/libs/fmdita/clientlibs/clientlibs/xmleditor/ui_config.json`

1. 在以下位置建立預設配置檔案的副本：

   `/apps/fmdita/xmleditor/ui_config.json`

1. 導航到並開啟 `ui_config.json` 檔案 `apps` 的子菜單。

1. 在 `ui_config.json` 檔案，添加要添加的篩選器的定義。

   以下代碼段說明如何添加兩個篩選選項 — DITA檔案和映像檔案。

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

   在上述代碼段中，第一個篩選器是用於DITA檔案。 過濾器定義採用以下參數：

   - **標題：**   篩選器的顯示名稱。 此標題作為篩選選項出現在檔案瀏覽對話框中。

   - **屬性：**   檔案元資料中要匹配的屬性。 例如，僅允許那些具有 `dita_class` 元資料，屬性篩選器採用「`jcr:content/metadata/dita_class`值。

   - **操作：**   指定「」`exists`&quot;以匹配屬性參數中指定的值是否存在。

   第二個過濾器用於影像檔案。 這些參數與第一個篩選器類似，但 `value` 的下界。 的 `value` 參數將影像類型陣列作為其值。 將搜索值參數中指定的所有檔案類型並在檔案瀏覽對話框中顯示，忽略所有其他檔案類型。

1. 保存 *ui\_config_json* 檔案並重新載入Web編輯器。

   啟動檔案瀏覽對話框時，將顯示在ui\_config.json檔案中配置的篩選器選項。

   ![](assets/file-browse-custom-filters.png){width="300" align="left"}


