---
title: 使用基線和標籤的Java式API
description: 瞭解如何使用基線和標籤的Java式API
source-git-commit: fad5049962f258bbe59c7d172436d82b3d6cd68f
workflow-type: tm+mt
source-wordcount: '878'
ht-degree: 0%

---


# 使用基線和標籤的Java式API {#id175UB30E05Z}

下列Java式API可讓您建立基準線，並將標籤新增至基準線中的檔案。 這些API以套件組合的形式提供。 您必須在程式碼中包含此套件組合，才能使用這些API。

套件組合詳細資料：

- 群組ID： **com.adobe.fmdita**

- 成品ID： **api**

- 版本： **3.5**

- 封裝： **com.adobe.fmdita.api.baselines**

- 類別詳細資料：

  ```JAVA
  public class BaselineUtils extends Object
  ```

  此 **基準線公用程式** 類別包含建立基準線以及將標籤套用至基準線中的檔案的方法。


## 建立基準線

建立基準線方法有兩個版本 — 一個用於XML Documentation解決方案3.5版，另一個用於3.5版之前的版本\（包括3.4、3.3和3.2版\）。 3.5版API允許在對應檔案中使用標籤、直接參照和間接參照來建立基準線。

另一個版本的API會使用日期和時間建立基準。 保留此API是為了與使用XML Documentation解決方案3.4、3.3或3.2的系統保持回溯相容性。

**語法\（3.5版）**：

```JAVA
public static String createBaseline(Session session, 
String sourcePath, 
String baselineTitle, 
String label, 
LinkedHashMap directContext, 
LinkedHashMap indirectContext) 
throws GuidesApiException
```

**引數**： |名稱|型別|說明| --------資----------- |`session`|javax.jcr.Session|有效的JCR工作階段。 使用者工作階段需要同時擁有DITA map的讀取和寫入許可權，以及基準線中包含之所有參照檔案的讀取許可權。| |`sourcePath`|字串|AEM存放庫中DITA map檔案的絕對路徑。| |`baselineTitle`|字串|基準的唯一標題。| |`label`|字串|選取已套用指定標籤的主題版本。| |`directContext`|LinkedHashMap&lt;string object=&quot;&quot;>|選取直接參考主題\(content\)所依據的設定，依照對應中提及的順序來解析版本。 <br> 如果在對映的所有索引鍵執行反複專案之後，找不到任何版本，則基準線建立程式會失敗。 <br> 如果HashMap是空的\（傳送空白且預設值不是null的對應\），則預設會填入為： <br>`directContext.put("label", label);` <br> `directContext.put("latest", true);` <br> 如果您希望基準線建立僅能挑選指定標籤的版本，而且如果不存在此類版本，則會失敗，請將 `label` 索引鍵和您要在其上建立基準線的標籤。| |`indirectContext`|LinkedHashMap&lt;string object=&quot;&quot;>|選取間接參考主題\（參考的內容\）所依據的設定，依照對應中提及的順序來解析版本。 <br> 如果在對映的所有索引鍵執行反複專案之後，找不到任何版本，則基準線建立程式會失敗。 <br> 如果HashMap是空的\（傳送空白且預設值不是null的對應\），則預設會填入為： <br>`indirectContext.put("label", label);` <br>`indirectContext.put "pickAutomatically", null);` <br> 如果您希望它是最新版本，而不是自動擷取版本，請取代： <br>`indirectContext.put("pickAutomatically", null);` <br> _替換為:_ <br>`indirectContext.put("latest", true)`|

**傳回**：基準線的名稱，是JCR存放庫中基準線的節點名稱。 新建立之基準線的標題將顯示在DITA map的「基準線」頁面上。

**例外**：擲回 ``ItemExistExceptiom`` 如果具有相同標題的基準線已存在。

**語法\（3.4、3.3和3.2版）**

```JAVA
public static String createBaseline
(Session session, 
String sourcePath, 
String baselineTitle, 
Date versionDate) throws GuidesApiException
```

**引數**： |名稱|型別|說明| --------資----------- |`session`|javax.jcr.Session|有效的JCR工作階段。 使用者工作階段需要同時擁有DITA map的讀取和寫入許可權，以及基準線中包含之所有參照檔案的讀取許可權。| |``sourcePath``|字串|AEM存放庫中DITA map檔案的絕對路徑。| |`baselineTitle`|字串|基準的唯一標題。| |`versionDate`|日期|基準線是使用此日期的主題版本\（直接從DITA map參照\）建立的。 指定日期於 `d-MM-yyyy H:mm` 格式。|

**傳回**：基準線的名稱，是JCR存放庫中基準線的節點名稱。 新建立之基準線的標題將顯示在DITA map的「基準線」頁面上。

**例外**：擲回 ``RepositoryException.``

## 套用標籤

此 ``applyLabel`` 方法會將一或多個標籤套用至基準線中的檔案。

**語法**：

```JAVA
public static void applyLabel(Session session,
                  String sourcePath,
                  String baselineName,
                  String label)
                  throws RepositoryException, WorkflowException, Exception
```

**引數**： |名稱|型別|說明| --------資----------- |`session`|javax.jcr.Session|有效的JCR工作階段。| |`sourcePath`|字串|AEM存放庫中DITA map檔案的絕對路徑。| |``baselineName``|字串|必須套用標籤的基準節點名稱。 若要取得基準節點的名稱，您可以使用 [\#id185NFF0085Z](#id185NFF0085Z) 方法或檢查CRXDE中DITA map的基準線節點。<br> **注意：** 標籤會套用至從基線中的對應檔案直接參照的檔案版本。| |`label`|字串|套用至基線中檔案的標籤。 確保標籤不包含下列字元： &amp;sol； &amp;comma； &amp;colon； &amp;comma； &amp;lbrack； &amp;comma； &amp;rbrack； &amp;comma； &amp;vert； &amp;comma； &amp;ast； <br> 如果您想要設定多個標籤，請以逗號分隔標籤；例如Label1， Label2.|

**例外**：擲回 `RepositoryException`.

## 刪除標籤

此 ``deleteLabel`` 方法會從基準線中的檔案刪除一或多個標籤。

**語法**：

```JAVA
public static Map
<String, String> deleteLabel(Session session, 
String sourcePath, 
String baselineName, 
String label) throws GuidesApiException
```

**引數**： |名稱|型別|說明| --------資----------- |`session`|javax.jcr.Session|有效的JCR工作階段。| |`sourcePath`|字串|AEM存放庫中DITA map檔案的絕對路徑。| |`baselineName`|字串|必須從中刪除標籤的基準名稱。 <br> **注意：** 標籤會從從從基線中的對應檔案直接參照的檔案版本中刪除。| |`label`|字串|要從基準線檔案中刪除的標籤。 <br> 如果您想要刪除多個標籤，請以逗號分隔標籤；例如Label1， Label2.|

**傳回**：對應包含 *key：value* 配對 `path:deletedlabels` 基準線中的所有檔案。

**例外**：擲回 ``RepositoryException`, `VersionException`, `Exception``.

