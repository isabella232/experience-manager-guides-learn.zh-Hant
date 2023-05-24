---
title: 自動產生元素ID
description: 瞭解如何自動產生元素ID
source-git-commit: 801c306fa120e7889d4b9428fd5bee2849bf1956
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---


# 自動產生元素ID {#id20CIL40016I}

AEM Guides會為您建立的任何新檔案產生檔案ID。 例如，當您建立DITA map時，ID如下 `map.ditamap_random_digits` 指派給地圖的ID。 您也可以定義自動產生及指派ID的元素。

AEM Guides提供簡易的組態設定，您需在其中定義ID自動產生的元素及ID的模式。 依預設，某些元素包括 `section`， `table`， `ul`， `ol`，已設定為自動產生ID。 您可以新增其他元素至此清單，這樣當這些元素插入檔案中時，AEM Guides就會根據指定的模式產生並指派ID

執行以下步驟，將元素設定為具有自動產生的ID：

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並按一下 **com.adobe.fmdita.xmleditor.config.XmlEditorConfig** 套件組合。

1. 在 *XmlEditorConfig* 設定，請在「 」中指定一個或多個元素 **自動產生元素標籤的ID** 欄位。

   >[!NOTE]
   >
   > 元素標籤是DITA元素名稱，例如 `body`， `title`， `codeblock`、等等。 若要指定多個元素，請以逗號分隔元素名稱。

1. 在&#x200B;**產生ID的模式** 欄位中，指定要產生ID的模式。

   此欄位的預設值設為 `${elementName}_${id}`. 此 `${elementName}` 值會取代為元素的名稱。 此 `${id}` 變數會產生元素的序號。 例如，如果您將段落元素指派給具有自動產生的ID，則主題或檔案中的第一個段落將獲得p\_1之類的ID，而下一個段落將獲得p\_2等。 不過，在不同的檔案中，ID產生程式會重新啟動。 這表示在不同的檔案中，可以將p\_1和p\_2等ID指派給段落元素。

   如果您的檔案已包含指定模式的ID，則自動產生程式不會將這些ID指派給新元素。

1. 按一下「**儲存**」。


**父級主題：**[&#x200B;自訂Web編輯器](conf-web-editor.md)

