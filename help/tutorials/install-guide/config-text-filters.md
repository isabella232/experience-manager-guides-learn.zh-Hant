---
title: 配置文本篩選器
description: 瞭解如何配置文本篩選器
source-git-commit: 5ac066bb8db32944abd046f64da11eeb1bdbe467
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---


# 配置文本篩選器 {#id21BPD0FK0XA}

指AEM南提供了搜索儲存庫選定路徑上的檔案中文本的AEM功能。 可以使用篩選器搜索從儲存庫面板搜索檔案或瀏覽檔案。 在Web編輯器中工作時，需要使用檔案瀏覽對話框來插入像影像、引用或鍵引用這樣的元素。

預設情況下，可以使用一些增強的篩選器來搜索儲存庫中AEM的檔案。 可以篩選所選路徑上存在的所有DITA檔案或非DITA檔案。 您還可以在DITA元素的屬性中搜索特定值。 您還可以查找由指定用戶簽出的檔案。

>[!NOTE]
>
> 您還可以配置全局配置檔案並添加更多篩選器以進行搜索。

執行以下步驟來配置文本篩選器：

1. 以管理員身份登錄Adobe Experience Manager。
1. 按一下&#x200B;**Adobe Experience Manager** 在頂部連結，然後選擇 **工具**。
1. 選擇 **參考線** 按一下 **資料夾配置檔案**。
1. 按一下 **全局配置檔案** 平鋪。
1. 按一下 **XML編輯器配置**。
1. 按一下 **編輯** 表徵圖。
1. 下載ui\_config.json檔案。
1. 在檔案中配置篩選器。 您還可以添加自定義篩選器，如下例所示：

   以下代碼段說明如何添加篩選選項DITA檔案、非DITA、DITA元素和由檔案簽出。 它還包含自定義篩選器 — Tags。

   ```json
   [
     {
       "title": "DITA files",
       "property": "jcr:content/metadata/dita_class",
       "operation": "like",
       "children": [
         {
           "title": "DITA Topics",
           "value": "- topic/topic",
           "checked": true
         },
         {
           "title": "DITA Maps",
           "value": "- map/map",
           "checked": true
         }
       ]
     },
     {
       "title": "DITA elements",
       "property": "jcr:content/ditameta",
       "widgetId": "dita_filter",
       "operation": "like"
     },
     {
       "title": "Checked out by",
       "property": "jcr:content/cq:drivelock",
       "operation": "like",
       "itemConfig": {
         "component": "textfield",
         "placeholder": "Checked out by"
       },
       "children": [
         {
           "title": "Check out"
         }
       ]
     },
     {
       "title": "Tags",
       "property": "jcr:content/metadata/cq:tags",
       "itemConfig": {
         "component": "textfield",
         "placeholder": "Enter Tag"
       },
       "children": [
         {
           "title": "Tags"
         }
       ]
     }
   ]
   ```

   在上述代碼段中，第一個篩選器是用於DITA檔案。 過濾器定義採用以下參數：

   - **標題：** 篩選器的顯示名稱。 此標題作為篩選選項出現在檔案瀏覽對話框中。

   - **屬性：** 檔案元資料中要匹配的屬性。 例如，要僅允許在其屬性中包含dita\class元資料的檔案，屬性篩選器將「jcr:content/metadata/dita\class」作為其值。

   - **操作** 指定&quot;exists&quot;以匹配屬性參數中指定的值是否存在

1. 上載包含已添加篩選器的已更新的ui\_config.json檔案。

配置的篩選器可在篩選器面板中找到。

**父主題：**[&#x200B;自定義Web編輯器](conf-web-editor.md)

