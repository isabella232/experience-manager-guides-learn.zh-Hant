---
title: 在Web編輯器工具欄中配置其他特殊字元
description: 如何在Web編輯器工具欄中配置其他特殊字元
feature: Web Editor
role: User
exl-id: 0fbc05a5-a6b0-4f6b-bbc4-8fca03581d90
source-git-commit: b5e64512956f0a7f33c2021bc431d69239f2a088
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%

---

# 如何在Web編輯器工具欄中配置其他特殊字元

Web編輯器工具欄中有一個快捷方式選項，允許作者插入特殊字元。
下面的螢幕截圖中可以看到同樣的內容：

![特殊字元](assets/special-chars.png)


此處可配置這些字元清單。 如果需要為此添加更多字元，請執行以下步驟：

+ 登錄並AEM開啟CRXDE Lite模式。

+ 在以下位置建立symbols.json檔案：「/apps/fmdita/xmleditor/」(可以從 — &#39;/libs/fmdita/clientlibs/clientlibs/xmleditor/symbols.json&#39;位置複製預設值)

+ 將symbols.json檔案中的特殊字元定義添加為：

```
{
      "label": "Logical Symbols",
      "items": [
        {
          "name": "≥",
          "title": "Greater-Than or Equal To"
        },
        {
          "name": "≤",
          "title": "Smaller-Than or Equal To"
        }
      ]
}
```

symbols.json檔案的結構說明如下：

+ 「標籤」：&quot;邏輯符號&quot;:這指定特殊字元的類別。 在代碼段中，定義了名為「邏輯符號」的類別。

+ &quot;項目&quot;:這定義類別中特殊字元的集合。

+ &quot;名稱&quot;:&quot;≥&quot;、&quot;標題&quot;:「大於或等於」：這是特殊字元的定義。 它以「名稱」標籤開頭，不得更改。 名稱后跟特殊字元。 「title」是特殊字元的名稱或標題，它作為該特殊字元的工具提示顯示。

您可以定義類別中特殊字元的多個定義。

這將在特殊字元對話框中添加另一個類別：

![特殊符號類別](assets/special-char-category.png)

![插入特殊字元](assets/insert-special-char.png)

>[!MORELIKETHIS]
>
>+ [安裝及設定指南](https://helpx.adobe.com/content/dam/help/en/xml-documentation-solution/3-6/XML-Documentation-for-Adobe-Experience-Manager_Installation-Configuration-Guide_EN.pdf)

