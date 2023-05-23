---
title: 配置允許的特殊字元
description: 瞭解如何配置允許的特殊字元
source-git-commit: 801c306fa120e7889d4b9428fd5bee2849bf1956
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---


# 配置允許的特殊字元 {#id20CIL600035}

Web編輯器允許您在開箱內插入一些特殊字元。 但是，您可以自定義作者可以在其文檔中插入的特殊字元清單。 如果自定義特殊字元清單，則它將覆蓋預設特殊字元集。 只有您在配置中添加的那些特殊字元才可供作者使用。

執行以下步驟以覆蓋預設的特殊字元清單：

1. 登錄並AEM開啟CRXDE Lite模式。

1. 建立 `symbols.json` 檔案的位置：

   ```json
   /apps/fmdita/xmleditor/
   ```

1. 在中添加特殊字元定義 `symbols.json` 檔案為：

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

- `"label": "Arrows"`:這指定特殊字元的類別。 在代碼段中，一個具有名稱的類別 `"Arrows"` 。
- `"items"`:這定義類別中特殊字元的集合。
- `"name": "←", "title": "Left Arrow"`:這是特殊字元的定義。 它從 `"name"` 標籤，不能更改。 名稱后跟特殊字元。 的 `"title"` 是作為該特殊字元的工具提示顯示的特殊字元的名稱或標題。

   您可以定義類別中特殊字元的多個定義。


**父主題：**[&#x200B;自定義Web編輯器](conf-web-editor.md)

