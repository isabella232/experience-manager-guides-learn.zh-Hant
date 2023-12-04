---
title: 在同一個索引標籤中開啟DITA主題或對應檔案
description: 瞭解如何在相同標籤中開啟DITA主題或對應檔案
source-git-commit: 880cd344ceb65ea339be699ebcad41c0d62e168a
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 0%

---

# 在同一個索引標籤中開啟DITA主題或對應檔案 {#id223HH0301J3}

在某些工作流程中，當您按一下主題或地圖檔案的連結時，它會在新標籤中開啟。 這可能會導致瀏覽器中開啟許多索引標籤，進而影響您的生產力。 您可以變更在新標籤中開啟主題或地圖檔案的行為，並在目前標籤中強制開啟。

使用中提供的指示 [設定覆寫](download-install-additional-config-override.md#) 以建立組態檔。 在組態檔中，提供下列\(property\)詳細資訊，以開啟主題或在新索引標籤中對應檔案：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | `xmleditor.openinsametab` | 布林值\(true/false\)。 <br> **預設值**： `false` |

此設定會影響您存取主題或對應檔案的下列位置：

- 建立DITA主題\(在工作流程結束時，當您按一下 **開啟主題** button\)

- 建立DITA Map \(在工作流程結束時，當您按一下 **開啟地圖** button\)

- DITA map主控台中的主題標籤

- DITA map主控台中的「基準線」標籤

- DITA map主控台中的「報表」索引標籤


**父級主題：**[&#x200B;自訂Web編輯器](conf-web-editor.md)
