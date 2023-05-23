---
title: 驗證指AEM南安裝
description: 瞭解如何驗證指南AEM的安裝
source-git-commit: 5ac066bb8db32944abd046f64da11eeb1bdbe467
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---


# 驗證指AEM南安裝 {#id213BD030FBE}

安裝指南AEM後，需要驗證安裝是否成功。 執行以下步驟驗證安裝過程：

1. 登錄到實AEM例並導航至「AEMWeb控制台捆綁包」頁。 訪問捆綁頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/bundles
   ```

   此時將顯示捆綁的清單。

1. 在篩選文本框中輸入fmdita，然後按 **輸入**。

   將過濾束清單，以顯示「參考線」安裝的束AEM。 如果安裝成功，則所有安裝的捆綁包都將 **狀態** 共 **活動**。

   如果任何束沒有 **活動** 狀態，然後檢查日誌AEM以排除安裝問題。


>[!IMPORTANT]
>
> 您可以考慮許多效能優化建議來改進系統效能。 請參閱 [Recommendations用於效能優化](download-install-recommend-perf-optimiz.md#) 的雙曲餘切值。

**父主題：**[&#x200B;下載並安裝](download-install.md)

