---
title: 重設轉換工作流程的API
description: 了解轉換工作流程的REST API
source-git-commit: 880cd344ceb65ea339be699ebcad41c0d62e168a
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# 重設轉換工作流程的API {#id175UB30E05Z}

下列REST API可讓您將Word、HTML和InDesign檔案轉換為DITA格式。

## 轉換Word檔案

將Word檔案轉換為DITA格式的GET方法。

**請求URL**： http://*&lt;aem-guides-server>*： *&lt;port-number>*/bin/fmdita/conversion

**引數**： |名稱|型別|必要|說明| --------------------------- |``operation``|字串|是|要呼叫的作業名稱。 此引數的值為 ``word2dita``. <br> **注意：** 值不區分大小寫。 | |`inputFile`|字串|是|AEM存放庫中來源Word檔案的絕對路徑。| |`destPath`|字串|是|將儲存轉換的DITA檔案之目的地位置的絕對路徑。| |`createRev`|布林值|是|指定是否建立檔案的修訂版本\( `true`\)是否在指定的目的地\( `false`\)。 僅當目的地位置包含轉換檔案的現有版本時，才會考慮這種情況。| |`style2tagMap`|字串|是|用於轉換的樣式對應檔案的絕對路徑。|

**回應值**：傳回HTTP 200 \(Successful\)回應。

## 轉換HTML檔案

將HTML檔案轉換為DITA格式的GET方法。

**請求URL**： http://*&lt;aem-guides-server>*： *&lt;port-number>*/bin/fmdita/conversion

**引數**： |名稱|型別|必要|說明| --------------------------- |`operation`|字串|是|要呼叫的作業名稱。 此引數的值為 ``html2dita``. <br> **注意：** 值不區分大小寫。| |`inputFile`|字串|是|AEM存放庫中來源HTML檔案的絕對路徑。| |`destPath`|字串|是|將儲存轉換的DITA檔案之目的地位置的絕對路徑。| |`createRev`|布林值|是|指定是否建立檔案的修訂版本\( `true`\)是否在指定的目的地\( `false`\)。 只有在目的地位置包含轉換檔案的現有版本時，才會考慮使用此選項。|

**回應值**：傳回HTTP 200 \(Successful\)回應。

## 轉換InDesign檔案

將InDesign檔案轉換為DITA格式的GET方法。

**請求URL**： http://*&lt;aem-guides-server>*： *&lt;port-number>*/bin/fmdita/conversion

**引數**： |名稱|型別|必要|說明| --------------------------- |``operation``|字串|是|要呼叫的作業名稱。 此引數的值為 ``idml2dita``. <br> **注意：** 值不區分大小寫。| |`inputFile`|字串|是|AEM存放庫中來源InDesign檔案的絕對路徑。| |`destPath`|字串|是|將儲存轉換的DITA檔案之目的地位置的絕對路徑。| |`createRev`|布林值|是|指定是否建立檔案的修訂版本\( `true`\)是否在指定的目的地\( `false`\)。 只有在目的地位置包含轉換檔案的現有版本時，才會考慮使用此選項。|

**回應值**：傳回HTTP 200 \(Successful\)回應。
