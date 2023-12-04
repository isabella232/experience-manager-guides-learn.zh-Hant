---
title: 設定關閉時簽入檔案的提示
description: 瞭解如何設定關閉時簽入檔案的提示
source-git-commit: 880cd344ceb65ea339be699ebcad41c0d62e168a
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 1%

---

# 設定關閉時簽入檔案的提示 {#id222HC040PE8}

當使用者嘗試關閉在網頁編輯器中開啟的檔案(使用 **關閉** 按鈕或 **關閉**&#x200B;選項，如果檔案有未儲存的資料或未儲存的版本，則會出現一個對話方塊。 如果檔案已鎖定，系統會提示使用者解除鎖定。

此 **解鎖檔案** 預設不會啟用核取方塊，您必須從configMgr啟用此專案。 執行以下步驟，在Web編輯器中啟用預設選項：

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並按一下 **com.adobe.fmdita.xmleditor.config.XmlEditorConfig** 套件組合。

1. 選取 **關閉時要求籤入** 選項。

1. 按一下「**儲存**」。


啟用此設定時， **解鎖檔案** 對話方塊中的核取方塊預設為選取。

如需詳細資訊，請參閱 *檔案關閉並儲存案例* 使用Adobe Experience Manager指南as a Cloud Service指南中的區段。

**父級主題：**[&#x200B;自訂Web編輯器](conf-web-editor.md)
