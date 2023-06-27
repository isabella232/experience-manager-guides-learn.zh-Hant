---
title: 驗證AEM Guides安裝
description: 瞭解如何驗證AEM Guides安裝
source-git-commit: 6051181e243cf71919901093c1b5590f21832545
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 0%

---


# 驗證AEM Guides安裝 {#id213BD030FBE}

安裝AEM Guides後，您必須確認安裝是否成功。 執行以下步驟來驗證安裝：

1. 存取您Cloud Service的開發人員主控台。

   如需存取開發人員控制檯的詳細資訊，請參閱 [開發人員控制檯存取](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html) 在AEM檔案中。

1. 存取AEM中的OSGi套件組合清單。

   如需存取套裝的詳細資訊，請參閱 [套裝](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html?lang=en#bundles) 在AEM檔案中。

1. 在套件組合清單中搜尋fmdita並檢查其狀態。

   狀態應顯示 *作用中* 適用於成功部署的組合。 如果任何套件組合的狀態不是「作用中」，請檢查AEM記錄檔以疑難排解安裝問題。


**父級主題：**[&#x200B;下載並安裝](download-install.md)

