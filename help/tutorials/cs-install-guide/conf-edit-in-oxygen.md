---
title: 設定在Oxygon中編輯的選項
description: 瞭解如何設定氧聯結器外掛程式中編輯的選項。
source-git-commit: a209e46e41055348402292e20c229890cd0c01cf
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 1%

---


# 設定在Oxygon中編輯的選項

AEM Guides也可讓使用者在氧氣聯結器外掛程式中編輯其DITA主題和DITA map。

使用中提供的指示 [設定覆寫](download-install-additional-config-override.md#) 以建立組態檔。 在設定檔案中，提供下列（屬性）詳細資料以設定 **在Oxygon中編輯** 選項：



| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | `xmleditor.editinoxygen` | 布林值\(true/false\)。 **預設值**： false |

>[!NOTE]
>
> 此設定預設為停用，且選項在網頁編輯器中無法使用。

**父級主題：**[&#x200B;自訂Web編輯器](conf-web-editor.md)

