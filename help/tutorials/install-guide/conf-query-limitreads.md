---
title: 配置查詢的LimitReads數
description: 瞭解如何配置查詢的LimitReads數
source-git-commit: 801c306fa120e7889d4b9428fd5bee2849bf1956
workflow-type: tm+mt
source-wordcount: '99'
ht-degree: 2%

---


# 配置查詢的LimitReads數 {#id231RC0HL0ID}

要增加查詢一次可讀取的節點數，請執行以下步驟：

1. 開啟Adobe Experience ManagerWeb控制台JMX頁。

   訪問配置頁的預設URL為：

   ```http
   http://<server name>:<port>/system/console/jmx
   ```

1. 搜索並按一下 **查詢引擎設定**。

1. 更改屬性值 **限制讀取** 屬性。

1. 按一下「**儲存**」。


增加此屬性值時，它有助於為較大的DITA映射生成報告。

**父主題：**[&#x200B;自定義Web編輯器](conf-web-editor.md)

