---
title: 配置基於UUID的連結的顯示
description: 瞭解如何配置基於UUID的連結的顯示
source-git-commit: 801c306fa120e7889d4b9428fd5bee2849bf1956
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---


# 配置基於UUID的連結的顯示 {#id2035G20M0QN}

預設情況下，使用Web編輯器中的「插入引用」或「插入重用內容」選項建立連結時，該連結使用引用內容的UUID建立。 的 **連結** 可以將引用內容的屬性\（在屬性面板\中）配置為顯示引用內容或UUID的相對檔案路徑。 此顯示由 **啟用UUID** 選項。 預設情況下，它為ON，這表示引用內容的UUID顯示在「屬性」面板中。

執行以下步驟以在Web編輯器中顯示引用內容的相對路徑或UUID:

1. 開啟「Adobe Experience ManagerWeb控制台配置」頁。

   訪問配置頁的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索並按一下 **com.adobe.fmdita.xmleditor.config.XmlEditorConfig** 捆綁。

1. 在 *XmlEditor配置* 設定， **啟用UUID** 選項。 這表示引用內容的UUID顯示在 **連結** 屬性。

   如果要顯示連結內容的相對路徑，請取消選擇 **啟用UUID** 的雙曲餘切值。

1. 按一下「**儲存**」。


**父主題：**[&#x200B;自定義Web編輯器](conf-web-editor.md)

