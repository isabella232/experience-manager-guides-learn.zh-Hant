---
title: 下載檔案
description: 了解如何下載檔案
source-git-commit: cc0fbca257d82cc82db5b5da8d263309fd71de55
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---


# 下載檔案 {#id216MC0H0BE8}

您可以下載資產，包括DITA和非DITA檔案。 有多種方式可讓您下載資產、有些方法是AEM的原生方法，有些則受AEM指南支援。 如需原生AEM資產下載資訊，請參閱 [從Adobe Experience Manager下載資產](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/manage/download-assets-from-aem.html) 在AEM檔案中。 下節將說明在AEM參考線中透過DITA對應控制台下載檔案的機制。

## 導出DITA映射檔案

在AEM儲存庫中擁有DITA映射檔案後，您就可以下載映射檔案及其依存項。 這可讓您靈活地共用完整的映射檔案，以便離線編輯、驗證、審核或僅建立備份。

執行以下步驟來下載DITA映射檔案及其相依檔案：

1. 在資產UI中，導覽至您要下載的DITA對應。

1. 按一下DITA映射，在DITA映射控制台中開啟它。

1. 選取 **主題** 頁簽，查看DITA映射中可用的主題清單。

1. 在主工具列中，按一下 **下載地圖**.

   出現「Download Map（下載地圖）」對話框。

   ![](images/download-map.png){width="300" align="left"}

1. 按一下&#x200B;**下載**。在「下載地圖」對話方塊中，您可以選擇下列選項：

   - **使用基線**:選擇此選項可獲取為DITA映射建立的基線清單。 如果要根據特定基線下載映射檔案及其內容，請從下拉清單中選擇基線。 如需使用基線的詳細資訊，請參閱 [使用基線](generate-output-use-baseline-for-publishing.md#).
   - **平面化檔案階層**:選擇此選項可將所有引用的主題和媒體檔案保存在單個資料夾中。

   >[!NOTE]
   >
   > 您也可以下載對應檔案，而不需選取任何選項。 在這種情況下，會下載參考主題和媒體檔案的最後一個持續版本。

1. 在您按一下 **下載** 按鈕，則會排入佇列。 當地圖準備好下載後，您會收到下列通知。

   ![](images/download-map-prompt.png){width="550" align="left"}

   - 按一下 **下載** 下載.zip格式的對應檔案。

   - 按一下 **稍後下載** 以便稍後下載地圖檔案。 可從AEM通知收件匣存取下載連結。 按一下收件匣中產生的地圖通知，以下載.zip格式的地圖。
   >[!NOTE]
   >
   > 依預設，下載的地圖會在AEM通知收件匣中保留5天。

![](images/download-map-inbox.png){width="300" align="left"}

下載地圖後，您可以選取地圖，並使用頂端的「開啟」圖示來開啟選取的報表。

**上層主題：**[&#x200B;管理內容](authoring.md)

