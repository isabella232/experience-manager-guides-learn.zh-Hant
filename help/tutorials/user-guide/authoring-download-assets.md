---
title: 下載檔案
description: 瞭解如何下載檔案
exl-id: 3b588256-da30-4a98-be5c-fa36cfa8a80b
source-git-commit: 8073716bccacbe8d6a158b44d5106b083e3a5dcd
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# 下載檔案 {#id216MC0H0BE8}

您可以下載資產，包括DITA和非DITA檔案。 您可以透過多種方式下載資產，有些是AEM的原生方法，有些則受到AEM Guides支援。 如需原生AEM資產下載資訊，請參閱 [從Adobe Experience Manager下載資產](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/manage/download-assets-from-aem.html) 在AEM檔案中。 以下章節說明透過AEM Guides中的DITA map主控台下載檔案的機制。

## 匯出DITA map檔案

在AEM存放庫中擁有DITA map檔案後，您就可以下載map檔案及其相依專案。 這可讓您彈性地共用完整的對應檔案，以進行離線編輯、驗證、檢閱或只是建立備份。

執行以下步驟來下載DITA map檔案及其相依檔案：

1. 在「資產」UI中，導覽至您要下載的DITA map。

1. 按一下DITA map以在DITA map主控台中開啟它。

1. 選取 **主題** 標籤以檢視DITA map中可用的主題清單。

1. 在主工具列中，按一下 **下載地圖**.

   「下載地圖」對話方塊隨即顯示。

   ![](images/download-map.png){width="300" align="left"}

1. 按一下&#x200B;**下載**。在「下載對應」對話方塊中，您可以選擇下列選項：

   - **使用基準線**：選取此選項可取得為DITA map建立的基準線清單。 如果要根據特定基準線下載對應檔案及其內容，請從下拉式清單中選取「基準線」。 如需有關使用基準線的詳細資訊，請參閱 [使用基準線](generate-output-use-baseline-for-publishing.md#).
   - **平面化檔案階層**：選取此選項，將所有參照的主題和媒體檔案儲存在單一資料夾中。

   >[!NOTE]
   >
   > 您也可以在不選取任何選項的情況下下載地圖檔案。 在這種情況下，會下載參照主題和媒體檔案的最後一個儲存版本。

1. 在您按一下 **下載** 按鈕時，對應下載請求會排入佇列。 一旦地圖可供下載，您將會收到以下通知。

   ![](images/download-map-prompt.png){width="550" align="left"}

   - 按一下 **下載** 以下載.zip格式的對映檔案。

   - 按一下 **稍後下載** 以稍後下載地圖檔案。 可從AEM通知收件匣存取下載連結。 按一下收件匣中產生的對應通知，以下載.zip格式的對應。
   >[!NOTE]
   >
   > 依預設，下載的地圖會在AEM通知收件匣中保留五天。

![](images/download-map-inbox.png){width="300" align="left"}

下載地圖後，您可以選取地圖，並使用頂端的開啟圖示來開啟選取的報表。

**父級主題：**[&#x200B;管理內容](authoring.md)
