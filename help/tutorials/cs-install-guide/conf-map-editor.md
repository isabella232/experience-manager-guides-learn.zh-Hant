---
title: 將進階地圖編輯器設定為預設值
description: 瞭解如何將進階地圖編輯器設為預設值
source-git-commit: 880cd344ceb65ea339be699ebcad41c0d62e168a
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# 將進階地圖編輯器設定為預設值 {#id181AI0003PN}

AEM Guides隨附基本地圖編輯器和進階地圖編輯器。 基本地圖編輯器提供您建立地圖檔案所需的所有功能。 進階地圖編輯器功能更豐富，並整合在網頁編輯器中。 「進階對映編輯器」可讓作者使用易用的介面來建立和編輯DITA map檔案。

根據預設，每當建立新的對映檔案時，它都會在「基本對映編輯器」中開啟。 您可以讓設定預設為開啟「進階地圖編輯器」來變更此行為。

使用中提供的指示 [設定覆寫](download-install-additional-config-override.md#) 以建立組態檔。 在設定檔中，提供下列\(property\)詳細資訊，以啟用基本地圖編輯器：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | ``fmdita.hide.oldmapeditor`` | 布林值\(true/false\)。 如果您預設要使用「進階地圖編輯器」，請將此屬性設定為true。<br> **預設值**： false |

>[!NOTE]
>
> 依預設，當作者建立對應檔案並選擇開啟它以進行編輯時，就會啟動「基本對應編輯器」。 從Assets UI為對應檔案選取「編輯」選項時，也會在「基本對應編輯器」中開啟該選項。

**父級主題：**[&#x200B;自訂Web編輯器](conf-web-editor.md)
