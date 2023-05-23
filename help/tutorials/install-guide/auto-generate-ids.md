---
title: 自動生成元素ID
description: 瞭解如何自動生成元素ID
source-git-commit: 801c306fa120e7889d4b9428fd5bee2849bf1956
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---


# 自動生成元素ID {#id20CIL40016I}

輔助AEM線為您建立的任何新文檔生成文檔ID。 例如，建立DITA映射時，ID類似 `map.ditamap_random_digits` 分配給映射的ID。 也可以定義自動生成和分配ID的元素。

輔助AEM線提供了簡單的配置設定，在這些設定中，您需要定義ID自動生成的元素和ID的圖案。 預設情況下，某些元素 `section`。 `table`。 `ul`。 `ol`，配置為自動生成ID。 您可以將其他元素添加到此清單中，以便每當這些元素插入文檔時，「參考線」會根據AEM給定的模式生成並分配ID

執行以下步驟，將元素配置為具有自動生成的ID:

1. 開啟「Adobe Experience ManagerWeb控制台配置」頁。

   訪問配置頁的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索並按一下 **com.adobe.fmdita.xmleditor.config.XmlEditorConfig** 捆綁。

1. 在 *XmlEditor配置* 設定，在 **自動生成元素標籤的ID** 的子菜單。

   >[!NOTE]
   >
   > 元素標籤是DITA元素名稱，如 `body`。 `title`。 `codeblock`等等。 要指定多個元素，請用逗號分隔元素名稱。

1. 在&#x200B;**生成ID的模式** 欄位中，指定要生成ID的模式。

   此欄位的預設值設定為 `${elementName}_${id}`。 的 `${elementName}` 值將替換為元素的名稱。 的 `${id}` 變數為元素生成順序編號。 例如，如果將段落元素指定為具有自動生成的ID，則主題或文檔中的第一個段落將獲得像p\1這樣的ID，而下一個段落將獲得p\2等。 但是，在另一文檔中，ID生成過程將重新啟動。 這意味著，在其他文檔中，可以將p\_1和p\_2等ID分配給段落元素。

   如果文檔已包含指定模式中的ID，則自動生成過程不會將這些ID分配給新元素。

1. 按一下「**儲存**」。


**父主題：**[&#x200B;自定義Web編輯器](conf-web-editor.md)

