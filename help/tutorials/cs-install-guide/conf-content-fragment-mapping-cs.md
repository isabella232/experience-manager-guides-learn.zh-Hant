---
title: 設定主題與內容片段模型之間的JSON型對應。
description: 瞭解如何設定主題與內容片段模型之間的JSON型對應。
source-git-commit: dd677257d94015d888705e4b6a43ae877e58be4b
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---


# 建立主題與內容片段之間的對應

AEM Guides提供的功能可在主題和內容片段模型之間建立JSON型對應。 您可以使用此對應，將主題內部分或所有元素中存在的內容發佈到內容片段。

1. 若要下載 *contentFragmentMapping.json*，以管理員身分登入Adobe Experience Manager。
1. 選取頂端的Adobe Experience Manager連結，然後選擇 **工具**.
1. 從工具清單中選取「參考線」，然後選取 **資料夾設定檔**.
1. 選取 **全域設定檔** 圖磚。
1. 選取 **XML編輯器設定** 標籤並選取 **編輯** 圖示在頂端。
1. 選取 **下載** 圖示以下載 *contentFragmentMapping.json*  檔案。 您可以接著對檔案進行變更，然後上傳相同的檔案。

1. 您需要遵循下列驗證：

   1. 應該是JSON檔案
   2. 其中應包含至少包含一個物件的陣列，且每個物件應包含下列專案：


      `"name": string `

      `"mapping": array`

      每個對應物件都必須包含下列專案：

      `"modelField": string`

      `"xpath": string`

      `"outputType": string`
1. 儲存檔案並上傳。

範例檔案:

```
[
  {
    "mapping": [
      {
        "modelField": "title",
        "xpath": "/topic[1]/title[1]",
        "outputType": "textContent"
      },
      {
        "modelField": "shortdesc",
        "xpath": "/topic[1]/shortdesc[1]",
        "outputType": "textContent"
      },
      {
        "modelField": "topicData",
        "xpath": "/topic[1]/body[1]",
        "outputType": "outerHTML"
      }
    ],
    "name": "Full Topic"
  },
  {
    "mapping": [
      {
        "modelField": "title",
        "xpath": "/topic[1]/title[1]",
        "outputType": "textContent"
      },
      {
        "modelField": "shortdesc",
        "xpath": "/topic[1]/shortdesc[1]",
        "outputType": "textContent"
      },
      {
        "modelField": "heroImage",
        "xpath": "/topic[1]/body[1]/p[1]/image[1]",
        "outputType": "outerHTML"
      },
      {
        "modelField": "dataTable",
        "xpath": "/topic[1]/body[1]/table[1]",
        "outputType": "outerHTML"
      }
    ],
    "name": "Sample Example with XPath"
  }
]
```

您可以使用預設對應來發佈整個主題。 選取 `Full Topic` 從的下拉式清單進行對應 **發佈為內容片段** 對話方塊中，並在內容片段模型中具有「topicData」欄位。