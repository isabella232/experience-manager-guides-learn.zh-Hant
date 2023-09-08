---
title: 用於建立和啟用套件的Java型API
description: 瞭解用於建立和啟用套件的Java型API
source-git-commit: fad5049962f258bbe59c7d172436d82b3d6cd68f
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---


# 用於建立和啟用套件的Java型API {#id175UB30E05Z}

以下Java型API可讓您建立和啟用CRX套件。 此API可以套件形式提供。 您必須在程式碼中包含此套件組合才能使用此API。

套件組合詳細資料：

- 群組ID： **com.adobe.fmdita**

- 成品ID： **api**

- 版本： **3.3**

- 封裝： **com.adobe.fmdita.api.crxactivate**

- 類別詳細資料：

  ```JAVA
  public class CRXActivator
  ```

  此 **`CRXActivator`** 類別包含用來建立CRX套件並在發佈執行個體上復寫它的方法。


## 建立及啟用封裝

此 `activate` 方法會在製作執行個體上建立CRX套件，並視需要在發佈執行個體上復寫。 我們假設已在編寫執行個體上設定AEM復寫引數。 此方法會根據JSON字串中作為輸入引數提供的規則清單，建立CRX套件。
>[!NOTE]
>
> 在建立或啟動過程中遇到的錯誤會寫入 `outputstream`.

**語法**：

```JAVA
public static void activate
(
  String json, 
  OutputStream outputstream, 
  Session session
) 
throws GuidesApiException
```

**引數**： |名稱|型別|說明| --------資----------- |`json`|字串|決定要建置CRX套件的JSON字串。 使用以下格式建立JSON字串： <br>- `activate`：屬於布林型別\(`true`/`false`\)。 判斷是否將在製作執行個體中建立的CRX套件復寫至發佈執行個體。 <br> - `rules`：屬於JSON陣列型別。 一系列JSON規則，會依序處理以建置CRX套件。 <br> - `rootPath`：屬於字串型別。 執行節點/屬性查詢的基底路徑。 如果不存在節點/屬性查詢，則根路徑以及根路徑下存在的所有節點都會包含在CRX套件中。 <br> - `nodeQueries`：屬於Regex陣列型別。 規則運算式的陣列，用來包含根路徑下的特定檔案。 <br> - `propertyQueries`：屬於JSON陣列型別。 JSON物件陣列，其中每個JSON物件包含要在根路徑上執行的XPath查詢，以及執行查詢後每個JCR節點中存在的屬性名稱。 每個JCR節點中屬性的值應為路徑或路徑陣列。 此屬性中存在的路徑已新增到CRX套件中。| |`outputstream`|java.io.OutputStream|這用於撰寫不同階段的結果，例如查詢執行、檔案包含、CRX封裝建立或啟動。 在建立或啟動過程中遇到的任何錯誤都會寫入 `outputstream`. 這對於偵錯很有用。| |`session`|字串|具有啟用許可權的有效JCR工作階段。|

**例外**：擲回 ``java.io.IOException``.

**範例**：下列範例顯示如何建立JSON查詢：

```JSON
{
  "activate": true,
  "rules": [
    {
      "rootPath": "/content/dam/nested",
      "nodeQueries": [
        ".*\\.jpg",
        ".*\\.png",
        ".*\\.gif"        
      ]
    },
    {
      "rootPath": "/content/output/sites/hierarchy_ditamap"
    },
    {
      "rootPath": "/content/output/sites/hierarchy_ditamap",
      "propertyQueries": [
        {
          "query": "//*[@fileReference]",
          "property": "fileReference"
        }
      ]
    }
  ]
}
```

範例JSON查詢包含下列規則：

- 套件中只包含/content/dam/nested路徑下的.png、.jpg和.gif影像。
- /content/output/sites/hierarchy\_ditamap下的所有節點都會包含在套件中。
- 中存在的路徑 `fileReference` /content/output/sites/hierarchy\_ditamap下的節點屬性會包含在套件中。

