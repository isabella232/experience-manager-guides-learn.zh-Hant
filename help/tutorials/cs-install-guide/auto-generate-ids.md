---
title: 自動產生元素ID
description: 瞭解如何自動產生元素ID
source-git-commit: 4f15166b1b250578f07e223b0260aacf402224be
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 1%

---


# 自動產生元素ID {#id20CIL40016I}

AEM Guides會為您建立的任何新檔案產生檔案ID。 例如，當您建立DITA map時，ID如下 `map.ditamap_random_digits` 指派給地圖的ID。 您也可以定義自動產生及指派ID的元素。

AEM Guides提供簡易的組態設定，您需在其中定義ID自動產生的元素及ID的模式。 依預設，某些元素包括 `section`， `table`， `ul`， `ol`，已設定為自動產生ID。 您可以新增其他元素至此清單，這樣當這些元素插入檔案中時，AEM Guides就會根據指定的模式產生並指派ID

使用中提供的指示 [設定覆寫](download-install-additional-config-override.md#) 以建立組態檔。 在設定檔案中，提供下列\(property\)詳細資料以設定自動產生的元素ID：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | `xmleditor.classes` | 指定以逗號分隔的元素清單。 <br> **預設值**： `"topic, section, table, simpletable, fig, image, ul, ol"` |

若要為自動產生的ID設定模式，請建立具有以下屬性的組態檔：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | `xmleditor.pattern` | 此欄位的預設值設為 `${elementName}_${id}`. 此 `${elementName}` 值會取代為元素的名稱。 此 `${id}` 變數會產生元素的序號。 例如，如果您將段落元素指派給具有自動產生的ID，則主題或檔案中的第一個段落將獲得p\_1之類的ID，而下一個段落將獲得p\_2等。 不過，在不同的檔案中，ID產生程式會重新啟動。 這表示在不同的檔案中，可以將p\_1和p\_2等ID指派給段落元素。 **預設值**： ``${elementName}_${id}`` |

**父級主題：**[&#x200B;自訂Web編輯器](conf-web-editor.md)

