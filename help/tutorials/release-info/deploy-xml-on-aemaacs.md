---
title: 如何新增 [!DNL AEM Guides] 至您的 [!DNL AEM as a Cloud Service] 環境
description: 瞭解如何新增 [!DNL AEM Guides] 至您的 [!DNL AEM as a Cloud Service] 環境
exl-id: a1e020c2-360c-4d71-b5fd-8179d9ceacda
source-git-commit: b5e64512956f0a7f33c2021bc431d69239f2a088
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---

# [!DNL AEM Guides] as a Cloud Service部署

瞭解如何新增 [!DNL Guides] 至您的 [!DNL AEM as a Cloud Service] 環境。

## 透過Cloud Manager Git管道手動部署

如果您已購買 [!DNL AEM Guides] 與2022年3月29日之前as a Cloud Service，請遵循下列部署指示：

* 如果您重新開始，可以取代自動產生的程式碼 [!UICONTROL Cloud Manager] 使用已整合XML外掛程式的下列存放庫程式碼： https://github.com/Adobe-TCS/XML-documentation-for-AEMaaCS

* 如果您在中已經簽入自訂 [!UICONTROL Cloud Manager] git repo，您可以參考以下存放庫，瞭解如何在現有程式碼中新增XML外掛程式的指示：https://github.com/Adobe-TCS/DoX-Installer-for-AEMaaCS

## 透過Cloud Manager部署

如果您是購買產品的客戶 [!DNL AEM Guides] 與2022年3月29日或之後as a Cloud Service，請依照下列指示新增 [!DNL Guides] 至您的 [!DNL AEM as a Cloud Service] 環境：

1. 登入 [!UICONTROL Cloud Manager].

1. 編輯您要設定的程式 [!DNL AEM Guides].

1. 切換至 **[!UICONTROL 解決方案和附加元件]** 標籤。

1. 在 **[!UICONTROL 解決方案和附加元件]** 表格，按一下 **[!UICONTROL 資產]**.

1. 選取 **[!UICONTROL 指南]** 並選取 **[!UICONTROL 儲存]**.

您已成功設定程式以自動布建AEM Guides解決方案。

![設定AEM Guides解決方案](assets/addon-configuration.png)

>[!NOTE]
>
>若要安裝 [!DNL AEM Guides] 在整合計畫下的任何環境中，您必須執行與環境關聯的管道。 您的CM Git程式碼基底中不需要進行額外的設定即可安裝 [!DNL AEM Guides].
