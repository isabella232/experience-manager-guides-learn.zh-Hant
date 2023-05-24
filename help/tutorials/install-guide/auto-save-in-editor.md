---
title: 在網頁編輯器中設定檔案自動儲存
description: 瞭解如何在網頁編輯器中設定檔案自動儲存
source-git-commit: 801c306fa120e7889d4b9428fd5bee2849bf1956
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 1%

---


# 在網頁編輯器中設定檔案自動儲存 {#id199CC0J0M5Z}

瀏覽器式編輯器中最常見的功能之一，是可在特定時段後儲存資料。 AEM Guides的網頁編輯器也支援在指定的時間間隔自動儲存主題和地圖檔案。 觸發此功能時，會儲存主題或地圖的工作副本。 未建立新版本的主題或地圖。 若要建立新版本，您必須按一下Web編輯器工具列中的「儲存修訂版本」圖示。

預設不會啟用自動儲存功能，您需要從configMgr啟用此功能。 執行以下步驟，在Web編輯器中啟用自動儲存功能：

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並按一下 **com.adobe.fmdita.xmleditor.config.XmlEditorConfig** 套件組合。

1. 在 *XmlEditorConfig* 設定，選取 **自動儲存** 選項。

1. 在 **自動儲存間隔** 欄位中，指定觸發自動儲存功能的時間間隔（以秒為單位）。

1. 按一下「**儲存**」。


**父級主題：**[&#x200B;自訂Web編輯器](conf-web-editor.md)

