---
title: 使用資料夾設定檔的Java型API
description: 瞭解如何使用資料夾設定檔的Java型API
source-git-commit: 880cd344ceb65ea339be699ebcad41c0d62e168a
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---

# 使用資料夾設定檔的Java型API {#id175UB30E05Z}

以下Java型API可讓您將條件屬性新增至資料夾層級的設定檔。 此API可以套件形式提供。 您必須在程式碼中包含此套件組合才能使用此API。

套件組合詳細資料：

- 群組ID： **com.adobe.fmdita**

- 成品ID： **api**

- 版本： **3.2**

- 封裝： **com.adobe.fmdita.api.profiles**

- 類別詳細資料：

  ```JAVA
  public class FolderProfileUtils extends Object
  ```

  此 **`FolderProfileUtils`** 類別包含將條件屬性加入資料夾設定檔中的方法。


## 將條件屬性新增至資料夾設定檔

此 ``addAttributeProfiles`` 方法將條件屬性新增到資料夾層級的設定檔。

**語法**：

```JAVA
public static boolean addAttributeProfiles
(List
<String> attributeNames, 
List
    <String> values, 
List
        <String> labels,
String profileName, 
Session session) throws GuidesApiException
```

**引數**： |名稱|型別|說明| --------資----------- |``attributeNames``|字串|屬性名稱清單。| |``values``|字串|指定屬性的值清單。| |`labels`|字串|的標籤清單 `attribute`- `value` 配對。 [1](#fntarg_1)| |`profileName`|字串|必須套用這些屬性、值和標籤的資料夾層級設定檔名稱。 **重要：** 設定檔中定義的所有現有屬性 — 值 — 標籤都會被覆寫。| |`session`|javax.jcr.Session|有效的JCR工作階段。|

**傳回**：
`true` 以取得成功。 如果失敗，系統會擲回例外狀況。

**例外**：擲回 ``java.lang.Exception`` 在下列情況中：

- 如果API無法 `resourceResolverFactory` 物件。 在這種情況下，您應該重新啟動該套件組合。
- 如果傳遞至API的引數無效。
- 如果透過未經授權的使用者工作階段呼叫API，例如不是指定資料夾設定檔管理員的使用者。

[1](#fnsrc_1) 此 `attributeNames`， `values`、和 `labels` 在陣列清單中的相同索引上，必須對應至相同的專案。
