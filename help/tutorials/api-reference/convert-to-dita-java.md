---
title: 用於轉換工作流程的Java型API
description: 瞭解用於轉換工作流程的Java型API
source-git-commit: 880cd344ceb65ea339be699ebcad41c0d62e168a
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 0%

---

# 用於轉換工作流程的Java型API {#id175UB30E05Z}

下列Java型API可讓您將HTML和Word檔案轉換為DITA格式。 這些API以套件組合的形式提供。 您必須在程式碼中包含此套件組合，才能使用這些API。

**套件組合詳細資料**：

- 群組ID： **com.adobe.fmdita**

- 成品ID： **api**

- 版本： **3.2**

- 封裝： **com.adobe.fmdita.api.conversion**

- 類別詳細資料：

  ```JAVA
  public class ConversionUtils extends Object
  ```

  此 **ConversionUtils** 類別包含將HTML和Word檔案轉換為DITA格式的方法。


## 轉換HTML檔案

此 `convertHtmlToDita` 方法會將HTML檔案轉換為DITA格式。

**語法**：

```JAVA
public static void convertHtmlToDita(Session session, 
                  String inputFile, 
                  String destPath, 
                  boolean createRev) 
                  throws RepositoryException, WorkflowException
```

**引數**： |名稱|型別|說明| --------資----------- |`session`|javax.jcr.Session|有效的JCR工作階段。| |`inputFile`|字串|AEM存放庫中來源HTML檔案的絕對路徑。| |`destPath`|字串|將儲存轉換之DITA檔案的目的地位置的絕對路徑。| |`createRev`|布林值|指定是否建立檔案的修訂版本\( `true`\)是否在指定的目的地\( `false`\)。 只有在目的地位置包含轉換檔案的現有版本時，才會考慮使用此選項。|

**例外**：擲回 `RepositoryException`.

## 轉換Word檔案

此 ``convertWordToDita`` 方法會將Word檔案轉換為DITA格式。

**語法**：

```JAVA
public static void convertWordToDita(Session session, 
                  String inputFile,
                  String destPath, 
                  String style2tagMap, 
                  boolean createRev) 
                  throws RepositoryException, WorkflowException
```

**引數**： |名稱|型別|說明| --------資----------- |`session`|javax.jcr.Session|有效的JCR工作階段。| |`inputFile`|字串|AEM存放庫中來源Word檔案的絕對路徑。| |`destPath`|字串|將儲存轉換之DITA檔案的目的地位置的絕對路徑。| |`style2tagMap`|字串|用於轉換的樣式對應檔案的絕對路徑。| |`createRev`|布林值|指定是否建立檔案的修訂版本\( `true`\)是否在指定的目的地\( `false`\)。 只有在目的地位置包含轉換檔案的現有版本時，才會考慮使用此選項。|

**例外**：擲回 `RepositoryException`.
