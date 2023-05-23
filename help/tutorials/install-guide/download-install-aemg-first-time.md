---
title: 首次下載AEM和安裝指南
description: 瞭解如何首次下載AEM和安裝指南
source-git-commit: 5ac066bb8db32944abd046f64da11eeb1bdbe467
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 2%

---


# 首次下載AEM和安裝指南 {#id213BCL00KEV}

請執行以下步驟，首次在計AEM算機上下載並安裝指南：

>[!IMPORTANT]
>
> 如果要使用Livefyre和GuidesAEM，請確保在安裝Guides之前安裝Livefyre 3.0以AEM前的版本。 如果您使用的是Livefyre 3.0或更高版本，則沒有此類限制。

1. 從AdobeAEM軟體分發門戶下載指南。

1. 登錄到實AEM例並導航到CRX包管理器。 訪問包管理器的預設URL為：

   ```http
   http://<server name>:<port>/crx/packmgr/index.jsp
   ```

   包管理器管理本地安裝上的AEM包。 有關使用包管理器的詳細資訊，請參見 [如何使用包](https://helpx.adobe.com/tw/experience-manager/6-5/sites/administering/using/package-manager.html) 的上AEM界。

   ![](assets/package-manager.png){width="650" align="left"}

1. 要上載輔助AEM線包，請按一下 **上載包**。

1. 在「上載包」對話框中，導航至AEM您在步驟1中下載的「參考線」檔案，然後按一下 **確定**。

   包已上載到您的實AEM例。

1. 要安裝軟體包，請按一下 **安裝**。

   ![](assets/install-package.png){width="650" align="left"}

1. 在「安裝包」對話框中，按一下 **安裝**。

1. 要開始使用參考AEM線，請按一下「首頁」按鈕 ![](assets/home-button.png) 在CRX包管理器的左上角。


>[!NOTE]
>
> 對安裝程式中所有伺服器AEM實例執行安裝過程。

**父主題：**[&#x200B;下載並安裝](download-install.md)

