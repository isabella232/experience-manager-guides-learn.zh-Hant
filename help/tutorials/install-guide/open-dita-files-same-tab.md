---
title: 在同一頁籤中開啟DITA主題或映射檔案
description: 瞭解如何在同一頁籤中開啟DITA主題或映射檔案
source-git-commit: 801c306fa120e7889d4b9428fd5bee2849bf1956
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---


# 在同一頁籤中開啟DITA主題或映射檔案 {#id223HI0P202H}

在某些工作流中，按一下主題或映射檔案的連結時，會在新頁籤中開啟該連結。 這會導致瀏覽器中開啟許多頁籤，從而影響您的工作效率。 您可以更改在新頁籤中開啟主題或映射檔案的行為，並強制在當前頁籤本身中開啟它。 為此，請執行以下配置更改：

1. 開啟「Adobe Experience ManagerWeb控制台配置」頁。

   訪問配置頁的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索並按一下 **com.adobe.fmdita.xmleditor.config.XmlEditorConfig** 捆綁。

1. 選擇 **在同一頁籤中開啟DITA主題/映射** 的雙曲餘切值。

1. 按一下「**儲存**」。


此設定會影響以下位置，您可以從這些位置訪問主題或映射檔案：

- 建立DITA主題\(在工作流結束時，按一下 **開啟主題** 按鈕\)

- 建立DITA映射\(在工作流結束時，按一下 **開啟映射** 按鈕\)

- DITA映射控制台中的主題頁籤

- DITA映射控制台中的基線頁籤

- DITA映射控制台中的「報告」頁籤


**父主題：**[&#x200B;自定義Web編輯器](conf-web-editor.md)

