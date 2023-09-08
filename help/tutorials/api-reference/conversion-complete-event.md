---
title: 轉換程式事件處理常式
description: 了解轉換程式事件處理常式
source-git-commit: 8707acf3ba01b7488eea6597c434da73a901d037
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---


# 轉換程式事件處理常式 {#id175UB30E05Z}

AEM Guides會公開com/adobe/fmdita/conversion/complete事件，用於在檔案轉換程式完成後執行任何後續處理作業。 只要將非DITA檔案移轉至DITA檔案格式，就會觸發此事件。 例如，如果您執行Word至DITA轉換或InDesign至DITA轉換程式，則會在轉換程式結束後呼叫此事件。

您需要建立AEM事件處理常式，以讀取此事件中可用的屬性，並進行進一步處理。

事件詳細資訊說明如下：

**事件名稱**：

```HTTP
com/adobe/fmdita/conversion/complete 
```

**參數**:\
|名稱|型別|說明| --------資----------- |`status`|字串|所執行作業的傳回狀態。 可能的選項包括： — 成功：轉換程式已成功完成。 <br>  — 已完成，但發生錯誤：轉換程式已完成，但發生一些錯誤。 <br> — 失敗：轉換程式因某些嚴重錯誤而失敗。| |`filePath`|字串|AEM存放庫中來源檔案\（待轉換\）的絕對路徑。| |`outputPath`|字串|將儲存轉換之DITA檔案的目的地位置的絕對路徑。| |`logPath`|字串|將儲存轉換記錄檔之節點的絕對路徑。|

