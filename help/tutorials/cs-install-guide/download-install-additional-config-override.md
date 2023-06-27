---
title: 設定覆寫
description: 瞭解如何設定覆寫
source-git-commit: 6051181e243cf71919901093c1b5590f21832545
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 0%

---


# 設定覆寫 {#id216IFC003XA}

在進行任何設定更新時，應使用下列通用方法：

1. 存取您的Cloud Manager的Git存放庫。

1. 在下列位置建立新的JSON檔案：

   src/main/content/jcr\_root/apps/fmditaCustom/config/

1. 以下列格式命名檔案：

   $\{PID\}.cfg.json

   在此，PID是設定的程式ID。

1. 使用以下格式在JSON檔案中新增屬性：

   ```
   {
      "aem.adminuname": "updatedUserjson",
      "valid.characters": "[-a-zA-Z0-9_@$]",
      "dita.serialization": true
   }
   ```

1. 認可變更並執行Cloud Manager管道以部署更新的設定。


**父級主題：**[&#x200B;下載並安裝](download-install.md)

