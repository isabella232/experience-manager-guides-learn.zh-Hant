---
title: 設定允許的特殊字元
description: 瞭解如何設定允許的特殊字元
source-git-commit: 801c306fa120e7889d4b9428fd5bee2849bf1956
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---


# 設定允許的特殊字元 {#id20CIL600035}

網頁編輯器可讓您直接插入一些特殊字元。 不過，您可以自訂作者可在檔案中插入的特殊字元清單。 如果您自訂特殊字元清單，則會覆寫預設的特殊字元集。 作者只能使用您在設定中新增的特殊字元。

執行以下步驟來覆寫預設的特殊字元清單：

1. 登入AEM並開啟CRXDE Lite模式。

1. 建立 `symbols.json` 檔案的位置：

   ```json
   /apps/fmdita/xmleditor/
   ```

1. 在中新增特殊字元定義 `symbols.json` 檔案為：

   ```json
   {"symbols": [{"label": "Arrows",
      "items": [
      {   "name": "←",   "title": "Left Arrow"   } 
      ,   
      {   "name": "↑",   "title": "Up Arrow"      } 
      ]   
      }   ]   }
   ```


的結構 `symbols.json` 檔案說明如下：

- `"label": "Arrows"`：這會指定特殊字元的類別。 在程式碼片段中，名稱為的類別 `"Arrows"` 已定義。
- `"items"`：這會定義類別中特殊字元的集合。
- `"name": "←", "title": "Left Arrow"`：這是特殊字元的定義。 它從 `"name"` 標籤，不可變更。 名稱后面接著特殊字元。 此 `"title"` 是特殊字元的名稱或標題，會顯示為該特殊字元的工具提示。

   您可以在類別中定義多個特殊字元的定義。


**父級主題：**[&#x200B;自訂Web編輯器](conf-web-editor.md)

