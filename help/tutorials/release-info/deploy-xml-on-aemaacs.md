---
title: 如何添加 [!DNL AEM Guides] 到 [!DNL AEM as a Cloud Service] 環境
description: 瞭解如何添加 [!DNL AEM Guides] 到 [!DNL AEM as a Cloud Service] 環境
exl-id: a1e020c2-360c-4d71-b5fd-8179d9ceacda
source-git-commit: b5e64512956f0a7f33c2021bc431d69239f2a088
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---

# [!DNL AEM Guides] as a Cloud Service部署

瞭解如何添加 [!DNL Guides] 到 [!DNL AEM as a Cloud Service] 環境。

## 通過Cloud Manager Git管道手動部署

如果您購買 [!DNL AEM Guides] as a Cloud Service於2022年3月29日之前，請遵循以下部署說明：

* 如果正在重新啟動，則可以替換由 [!UICONTROL 雲管理器] 與下面已整合XML插件的回購程式中的代碼一起使用：https://github.com/Adobe-TCS/XML-documentation-for-AEMaaCS

* 如果已在中籤入了自定義項 [!UICONTROL 雲管理器] git repo，有關如何在現有代碼中添加XML插件的說明，請參閱以下repo:https://github.com/Adobe-TCS/DoX-Installer-for-AEMaaCS

## 通過雲管理器部署

如果您是購買 [!DNL AEM Guides] as a Cloud Service於03/29/2022或之後，請按照以下說明添加 [!DNL Guides] 到 [!DNL AEM as a Cloud Service] 環境：

1. 登錄到 [!UICONTROL 雲管理器]。

1. 編輯要為其配置的程式 [!DNL AEM Guides]。

1. 切換到 **[!UICONTROL 解決方案和附加模組]** 頁籤。

1. 在 **[!UICONTROL 解決方案和附加模組]** 表格，按一下 **[!UICONTROL 資產]**。

1. 選擇 **[!UICONTROL 參考線]** 選擇 **[!UICONTROL 保存]**。

您已成功配置程式以自動預配「指南」解AEM決方案。

![配置指AEM南解決方案](assets/addon-configuration.png)

>[!NOTE]
>
>安裝 [!DNL AEM Guides] 在整合程式下的任何環境中，必須運行與該環境關聯的管道。 在CM git代碼庫中安裝不需要其他配置 [!DNL AEM Guides]。
