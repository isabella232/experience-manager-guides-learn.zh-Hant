---
title: 設定UUID型連結的顯示方式
description: 瞭解如何設定顯示UUID型連結
source-git-commit: 880cd344ceb65ea339be699ebcad41c0d62e168a
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# 設定UUID型連結的顯示方式 {#id2035G20M0QN}

根據預設，當您在Web編輯器中使用「插入參照」或「插入重複使用內容」選項建立連結時，會使用參照內容的UUID來建立連結。 此 **連結** 參照內容的屬性\（在「屬性」面板中\）可設定為顯示參照內容的相對檔案路徑或UUID。 這個顯示是由 **啟用UUID** configMgr中的選項。 預設會開啟，這表示參考內容的UUID會顯示在「屬性」面板中。

執行以下步驟，在網頁編輯器中顯示參照內容的相對路徑或UUID：

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並按一下 **com.adobe.fmdita.xmleditor.config.XmlEditorConfig** 套件組合。

1. 在 *XmlEditorConfig* 設定， **啟用UUID** 選項預設為啟用。 這表示參照內容的UUID顯示在 **連結** 屬性。

   如果要顯示連結內容的相對路徑，請取消選取 **啟用UUID** 選項。

1. 按一下「**儲存**」。


**父級主題：**[&#x200B;自訂Web編輯器](conf-web-editor.md)
