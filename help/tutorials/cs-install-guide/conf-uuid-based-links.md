---
title: 設定UUID型連結的顯示
description: 瞭解如何設定顯示UUID型連結
source-git-commit: 4f15166b1b250578f07e223b0260aacf402224be
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 1%

---


# 設定UUID型連結的顯示 {#id2035G20M0QN}

根據預設，當您在Web編輯器中使用「插入參照」或「插入重複使用內容」選項建立連結時，會使用參照內容的UUID來建立連結。 此 **連結** 參照內容的屬性\（在「屬性」面板中\）可設定為顯示參照內容的相對檔案路徑或UUID。 根據預設，參考內容的UUID會顯示在「屬性」面板中。

使用中提供的指示 [設定覆寫](download-install-additional-config-override.md#) 以建立組態檔。 在設定檔中，提供下列\(property\)詳細資訊，以在網頁編輯器中顯示參照內容的相對路徑或UUID：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | `xmleditor.uuid` | 布林值\(true/false\)。 如果要顯示連結內容的相對路徑，請將此屬性設定為false。 <br> **預設值**： true |

**父級主題：**[&#x200B;自訂Web編輯器](conf-web-editor.md)

