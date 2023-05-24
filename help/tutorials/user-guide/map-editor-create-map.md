---
title: 建立地圖
description: 瞭解如何建立地圖
exl-id: d35ee09f-f951-4866-a2b1-e4b19f76e7a1
source-git-commit: 3bca42f0954afc2362ab24f369e698113324dbc3
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# 建立地圖 {#id176FEN0D05Z}

AEM Guides提供兩種現成可用的地圖範本 — DITA map和Bookmap。 您也可以建立自己的地圖範本，並與作者共用這些範本，以建立地圖檔案。

執行以下步驟來建立對應檔案：

1. 在Assets UI中，導覽至您要建立對應檔案的位置。

1. 按一下 **建立** \> **DITA Map**.

1. 在Blueprint頁面上，選取您要使用的對應範本型別，然後按一下 **下一個**.

   >[!NOTE]
   >
   > 在對應檔案中參照主題的方式取決於對應範本。 例如，如果您選取「對應」範本，則主題會參照\(`topicref`\)是用來指稱主題。 如果是Bookmap，主題參照是使用 `chapter` DITA中的元素。

   ![](images/map-template.png){width="650" align="left"}

1. 在「屬性」頁面中，指定對應 **標題**.

1. \(Optional\)指定檔案 **名稱**.

   如果您的管理員已根據UUID設定設定自動檔案名稱，則您將不會看到指定檔案名稱的選項。 系統會自動為檔案指派以UUID為基礎的檔案名稱。

   如果檔案命名選項可用，也會根據地圖示題自動建議名稱。 如果您要手動指定對應檔案名稱，請確定檔案名稱不包含任何空格、單引號或大括弧，且結尾為 `.ditamap`.

1. 按一下&#x200B;**建立**。

   便會顯示「已建立對應」訊息。

   您從Assets UI建立的每個新對應檔案 **建立** \> **DITA Map** 或Web編輯器獲得唯一的地圖ID。 此外，新地圖也會儲存為DAM中的最新工作副本。 除非您儲存新建立地圖的修訂版本，否則在「版本記錄」中不會看到任何版本號碼。 如果您開啟地圖進行編輯，版本資訊會顯示在地圖檔案索引標籤的右上角：

   ![](images/first-version-map-none.png){width="650" align="left"}

   新建立的地圖的版本資訊顯示為 *無*. 儲存新版本時，系統會為其指派版本編號1.0。如需儲存新版本的詳細資訊，請參閱 [另存為新版本](web-editor-features.md#save-as-new-version-id209ME400GXA).

   您可以選擇在設定的對應編輯器中開啟對應以進行編輯，或將對應檔案儲存在AEM存放庫中。

   >[!NOTE]
   >
   > 若要使用「進階地圖編輯器」，請存取Web編輯器中的地圖檔案。 如果您的管理員已將「進階對應編輯器」設定為對應檔案中的預設編輯器，則對應檔案會直接在「進階對應編輯器」中開啟以進行編輯。 另請參閱 *將「進階地圖編輯器」設定為預設值* 部分(在as a Cloud Service安裝與設定Adobe Experience Manager Guides中)。


**父級主題：**[&#x200B;使用地圖編輯器](map-editor.md)
