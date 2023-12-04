---
title: 根據UUID設定自動檔案名稱
description: 瞭解如何根據UUID設定自動檔案名稱
source-git-commit: 880cd344ceb65ea339be699ebcad41c0d62e168a
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---

# 根據UUID設定自動檔案名稱 {#id205QG070D5Z}

依預設，建立主題或地圖檔案時，作者也可以選擇指定檔案名稱。 作者可自由依需求指派檔案名稱。 不過，這可能會導致不一致，在大型檔案系統中可以看到各種檔案名稱。 身為管理員，您可以限製作者為他們在系統中建立的檔案指定檔案名稱。 對於每個新主題或對應檔案，您可以選擇自動指派以UUID為基礎的檔案名稱。

執行以下步驟，自動為系統中建立的所有新檔案指派以UUID為基礎的檔案名稱：

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並按一下 *com.adobe.fmdita.xmleditor.config.XmlEditorConfig* 套件組合。

1. 選取 **使用以UUID為基礎的系統檔案名稱** 選項。

1. 按一下「**儲存**」。


>[!NOTE]
>
> 依預設，此選項是關閉的。 開啟此選項後，作者在建立新主題或對應檔案時，看不到指定檔案名稱的選項。 您可以從Assets UI和Web編輯器建立新的主題或地圖檔案。

**父級主題：**[&#x200B;設定檔案名稱](conf-file-names.md)
