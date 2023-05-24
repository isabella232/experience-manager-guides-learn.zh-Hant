---
title: 設定查詢的LimitReads數目
description: 瞭解如何設定查詢的LimitReads數目
source-git-commit: 801c306fa120e7889d4b9428fd5bee2849bf1956
workflow-type: tm+mt
source-wordcount: '99'
ht-degree: 2%

---


# 設定查詢的LimitReads數目 {#id231RC0HL0ID}

若要增加查詢一次可讀取的節點數，請執行下列步驟：

1. 開啟Adobe Experience Manager Web Console JMX頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/jmx
   ```

1. 搜尋並按一下 **QueryEngineSettings**.

1. 變更的屬性值 **限制讀取** 屬性。

1. 按一下「**儲存**」。


當您增加這個屬性值時，它有助於您產生較大的DITA map報表。

**父級主題：**[&#x200B;自訂Web編輯器](conf-web-editor.md)

