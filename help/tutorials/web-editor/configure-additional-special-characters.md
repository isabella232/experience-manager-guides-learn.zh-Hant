---
title: 在網頁編輯器工具列中設定其他特殊字元
description: 瞭解如何在AEM Guides的網頁編輯器中設定其他特殊字元。
feature: Web Editor
role: User
exl-id: 0fbc05a5-a6b0-4f6b-bbc4-8fca03581d90
source-git-commit: 8504a0a52d381044bf1f0d6e7de3585ebecf3a7b
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 0%

---

# 如何在網頁編輯器工具列中設定其他特殊字元

網頁編輯器工具列中有一個捷徑選項，可讓作者插入特殊字元。
以下熒幕擷圖亦顯示相同內容：

![特殊字元](assets/special-chars.png)


您可以在此處設定這些字元清單。 如果您需要新增更多字元至此，請遵循下列步驟：

+ 登入AEM並開啟CRXDE Lite模式。

+ 在下列位置建立symbols.json檔案： &#39;/apps/fmdita/xmleditor/&#39; (您可以從 — &#39;/libs/fmdita/clientlibs/clientlibs/xmleditor/symbols.json&#39;位置複製預設值)

+ 在symbols.json檔案中新增特殊字元定義，如下所示：

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

+ &quot;label&quot;： &quot;Logical Symbols&quot;：這會指定特殊字元的類別。 在程式碼片段中，會定義名稱為「邏輯符號」的類別。

+ &quot;items&quot;：這定義了類別中特殊字元的集合。

+ &quot;name&quot;： &quot;≥&quot;， &quot;title&quot;： &quot;Greater-Than or Equal To&quot;：這是特殊字元的定義。 它以「name」標籤開始，此標籤不可變更。 名稱后面接著特殊字元。 「標題」是特殊字元的名稱或標題，會顯示為該特殊字元的工具提示。

您可以在類別中定義多個特殊字元的定義。

這會在特殊字元對話方塊中新增另一個類別：

![特殊符號類別](assets/special-char-category.png)

![插入特殊字元](assets/insert-special-char.png)

>[!MORELIKETHIS]
>
>+ [安裝及設定指南](https://helpx.adobe.com/content/dam/help/en/xml-documentation-solution/3-6/XML-Documentation-for-Adobe-Experience-Manager_Installation-Configuration-Guide_EN.pdf)
