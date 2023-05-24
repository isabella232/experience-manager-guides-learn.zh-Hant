---
title: 在同一個索引標籤中開啟DITA主題或對應檔案
description: 瞭解如何在相同索引標籤中開啟DITA主題或對應檔案
source-git-commit: 801c306fa120e7889d4b9428fd5bee2849bf1956
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---


# 在同一個索引標籤中開啟DITA主題或對應檔案 {#id223HI0P202H}

在某些工作流程中，當您按一下主題或地圖檔案的連結時，它會在新標籤中開啟。 這可能會導致瀏覽器中開啟許多標籤，進而影響您的生產力。 您可以變更在新標籤中開啟主題或地圖檔案的行為，並在目前標籤中強制將其開啟。 要執行此操作，請執行以下組態變更：

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並按一下 **com.adobe.fmdita.xmleditor.config.XmlEditorConfig** 套件組合。

1. 選取 **在同一個標籤中開啟DITA主題/對應** 選項。

1. 按一下「**儲存**」。


此設定會影響您存取主題或對應檔案的下列位置：

- 建立DITA主題\(在工作流程結束時，當您按一下 **開啟主題** button\)

- 建立DITA Map \(在工作流程結束時，當您按一下 **開啟地圖** button\)

- DITA map主控台中的主題標籤

- DITA map主控台中的「基準線」索引標籤

- DITA map主控台中的「報表」標籤


**父級主題：**[&#x200B;自訂Web編輯器](conf-web-editor.md)

