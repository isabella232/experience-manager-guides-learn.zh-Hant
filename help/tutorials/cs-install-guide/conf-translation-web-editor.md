---
title: 在網頁編輯器中設定翻譯功能
description: 瞭解如何在網頁編輯器中設定翻譯功能
source-git-commit: 880cd344ceb65ea339be699ebcad41c0d62e168a
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 0%

---

# 在網頁編輯器中設定翻譯功能 {#id21BONI0J0YR}

網頁編輯器提供強大的翻譯功能，可將您的內容翻譯成多種語言。

您可以使用 **管理** 索引標籤來翻譯您的內容。 此標籤預設為可用。

若要隱藏 **管理** 索引標籤中，執行下列步驟：

1. 登入 **Adobe Experience Manager** 作為管理員。
1. 按一下 **Adobe Experience Manager** 在頂端連結，然後選擇 **工具**.
1. 選取 **指南** 從工具清單中，按一下 **資料夾設定檔**.
1. 按一下 **全域設定檔** 圖磚。
1. 按一下 **XML編輯器設定**.
1. 按一下 **編輯** 圖示在頂端。
1. 下載 `ui\_config.json` file.從下載的檔案中移除下列程式碼片段：

   ```json
   {
       "component":"tab",
       "id":"workflow",
       "title":"Manage",
       "on-click":"APP_MODE_CHANGE",
       "items":
       [
           {
               "component":"label",
               "label":"Manage"
           }
       ]
   },
   ```

1. 上傳更新的ui\_config.json檔案。

請注意 **管理** 篩選器已無法使用。

**父級主題：**[&#x200B;自訂Web編輯器](conf-web-editor.md)
