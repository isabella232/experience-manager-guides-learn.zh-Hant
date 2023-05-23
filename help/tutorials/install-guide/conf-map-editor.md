---
title: 將「高級映射編輯器」設定為預設值
description: 瞭解如何將高級映射編輯器設定為預設
source-git-commit: 801c306fa120e7889d4b9428fd5bee2849bf1956
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 0%

---


# 將「高級映射編輯器」設定為預設值 {#id181AI0003PN}

參考AEM線附帶基本映射編輯器和高級映射編輯器。 「基本映射編輯器」(Basic Map Editor)為建立映射檔案提供了所有必要功能。 高級映射編輯器功能更豐富，它整合在Web編輯器中。 高級映射編輯器允許作者使用易於使用的介面建立和編輯DITA映射檔案。

預設情況下，每當建立新映射檔案時，都會在基本映射編輯器中開啟它。 通過啟用預設開啟高級映射編輯器的設定，可以更改此行為。

執行以下步驟，使「高級映射編輯器」成為映射檔案的預設編輯器：

1. 開啟「Adobe Experience ManagerWeb控制台配置」頁。

   訪問配置頁的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索並按一下 **com.adobe.fmdita.xmleditor.config.XmlEditorConfig** 捆綁。

1. 選擇 **隱藏基本映射編輯器** 的雙曲餘切值。

   選中此選項後，用戶將看不到用戶介面中任何位置的基本映射編輯器連結。 預設情況下，映射檔案將在高級映射編輯器中開啟。


