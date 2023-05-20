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

您可以下載包括DITA和非DITA檔案的資產。 您可以通過多種方式下載資產，有些方法是本地的，而AEM其他方法則受《指南》AEM支援。 有關本AEM機資產下載資訊，請參見 [從Adobe Experience Manager下載資產](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/manage/download-assets-from-aem.html) 的上AEM界。 下節將介紹通過指南中的DITA映射控制台下載檔案AEM的機制。

## 導出DITA映射檔案

將DITA映射檔案放在儲存庫AEM中後，您就可以下載映射檔案及其依存對象。 這樣，您就可以靈活地共用完整的映射檔案，以便離線編輯、驗證、審閱或僅建立備份。

執行以下步驟以下載DITA映射檔案及其從屬檔案：

1. 在資產UI中，導航到要下載的DITA映射。

1. 按一下DITA映射以在DITA映射控制台中開啟它。

1. 選擇 **主題** 頁籤，查看DITA映射中可用的主題清單。

1. 在主工具欄中，按一下 **下載映射**。

   出現「Download Map（下載映射）」對話框。

   ![](images/download-map.png){width="300" align="left"}

1. 按一下&#x200B;**下載**。在「下載映射」對話框中，可以選擇以下選項：

   - **使用基線**:選擇此選項可獲取為DITA映射建立的基線清單。 如果要根據特定基線下載映射檔案及其內容，請從下拉清單中選擇基線。 有關使用基線的詳細資訊，請參閱 [使用基線](generate-output-use-baseline-for-publishing.md#)。
   - **拼合檔案層次結構**:選擇此選項可將所有引用的主題和媒體檔案保存在單個資料夾中。

   >[!NOTE]
   >
   > 也可以下載映射檔案而不選擇任何選項。 在這種情況下，將下載所引用主題和媒體檔案的最後永續版本。

1. 按一下 **下載** 按鈕，映射下載請求已排隊。 地圖準備好下載後，您將收到以下通知。

   ![](images/download-map-prompt.png){width="550" align="left"}

   - 按一下 **下載** 以.zip格式下載映射檔案。

   - 按一下 **稍後下載** 以後下載映射檔案。 可以從通知收件箱訪AEM問下載連結。 按一下「收件箱」中生成的映射通知，以.zip格式下載映射。
   >[!NOTE]
   >
   > 預設情況下，下載的映射在通知收件箱中保AEM留5天。

![](images/download-map-inbox.png){width="300" align="left"}

下載映射後，您可以選擇映射並使用頂部的「開啟」表徵圖開啟選定的報表。

**父主題：**[&#x200B;管理內容](authoring.md)
