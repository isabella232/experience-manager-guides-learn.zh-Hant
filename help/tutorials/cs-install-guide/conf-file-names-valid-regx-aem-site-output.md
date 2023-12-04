---
title: 設定AEM Site輸出的有效檔案名稱
description: 瞭解如何為AEM網站輸出設定有效的檔案名稱
source-git-commit: 880cd344ceb65ea339be699ebcad41c0d62e168a
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 1%

---

# 設定AEM Site輸出的有效檔案名稱 {#id214GK0X0KXA}

與DITA主題允許的有效檔案名稱字元清單類似，您也可以為AEM Site輸出設定有效的檔案名稱字元清單。 URL中不允許使用的部分已知字元包括： ``'<>`@$``. 這些字元已設定為自動轉換為底線»`_`&quot;產生AEM Site輸出檔案名稱時找到。

使用中提供的指示 [設定覆寫](download-install-additional-config-override.md#) 以建立組態檔。 在設定檔中，提供下列\(property\)詳細資訊，以設定AEM Site輸出中的有效字元：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.common.SanitizeNodeNameImpl` | `aemsite.DisallowedFileNameChars` | 在AEM Site輸出檔案名稱中新增要以底線取代的字元。 <br> **預設值**： ``'<\>\`@$`` |

**父級主題：**[&#x200B;設定檔案名稱](conf-file-names.md)
