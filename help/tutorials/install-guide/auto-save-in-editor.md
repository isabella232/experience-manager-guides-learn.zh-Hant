---
title: 在Web編輯器中配置檔案自動保存
description: 瞭解如何在Web編輯器中配置檔案自動保存
source-git-commit: 801c306fa120e7889d4b9428fd5bee2849bf1956
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 1%

---


# 在Web編輯器中配置檔案自動保存 {#id199CC0J0M5Z}

在基於瀏覽器的編輯器中，最常見的功能之一是能夠在特定時間段後保存資料。 指南AEM的Web編輯器還支援在指定時間間隔內自動保存主題和映射檔案。 觸發此功能後，將保存主題或映射的工作副本。 未建立主題或映射的新版本。 要建立新版本，必須按一下Web編輯器工具欄中的「保存修訂版」表徵圖。

預設情況下未啟用自動保存功能，您需要從configMgr中啟用此功能。 執行以下步驟以在Web編輯器中啟用自動保存功能：

1. 開啟「Adobe Experience ManagerWeb控制台配置」頁。

   訪問配置頁的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索並按一下 **com.adobe.fmdita.xmleditor.config.XmlEditorConfig** 捆綁。

1. 在 *XmlEditor配置* 設定，選擇 **自動保存** 的雙曲餘切值。

1. 在 **自動保存間隔** 欄位，指定觸發自動保存功能的時間間隔（秒）。

1. 按一下「**儲存**」。


**父主題：**[&#x200B;自定義Web編輯器](conf-web-editor.md)

