---
title: 建立主題
description: 瞭解如何建立主題
exl-id: 336bbbff-f268-40be-ad3a-9c72923be71b
source-git-commit: e69665f3c4a0db10365719ac671cbd3ac0c455ec
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---

# 建立主題 {#id2056AL00O5Z}

AEM Guides可讓您建立型別的DITA主題 — 主題、工作、概念、參考、字彙表、DITAVAL等。 除了根據現成可用的範本建立主題外，您也可以定義自訂範本。 這些範本必須新增到資料夾設定檔中，才能顯示在範本選擇Blueprint和Web編輯器中。

請注意，全域和資料夾設定檔組態僅適用於資料夾層級的管理使用者。 如需設定全域和資料夾層級設定檔的詳細資訊，請參閱 *設定製作範本* 在安裝和設定適用於您設定的Adobe Experience Manager Guides中。

執行以下步驟來建立主題：

1. 在Assets UI中，導覽至您要建立主題的位置。

1. 若要建立新主題，請按一下 **建立** \> **DITA主題**.

1. 在Blueprint頁面上，選取您要建立的DITA檔案型別，然後按一下 **下一個**.

   ![](images/create_dita_topic.png){width="800" align="left"}

   依預設，AEM Guides提供最常用的DITA主題範本。 您可以根據組織要求設定更多主題範本，請參閱 *設定製作範本* 在安裝和設定適用於您設定的Adobe Experience Manager Guides中。

   >[!NOTE]
   >
   > 在Assets UI的清單檢視中，DITA主題型別在「型別」欄中顯示為「主題」、「任務」、「概念」、「參照」、「Glossentry」或「DITAVAL」。 DITA map會顯示為Map。

1. 在「屬性」頁面上，指定檔案 **標題**.

1. \(Optional\)指定檔案 **名稱**.

   如果您的管理員已根據UUID設定設定自動檔案名稱，則您將不會看到指定檔案名稱的選項。 系統會自動為檔案指派以UUID為基礎的檔案名稱。

   如果檔案命名選項可用，則會根據 **標題** （屬於您的檔案）。 如果您要手動指定檔名稱，請確定 **名稱** 不包含任何空格、單引號或大括弧，且結尾為.xml或.dita。 依預設，AEM Guides會以連字型大小取代所有特殊字元。 如需有關命名DITA檔案的最佳作法，請參閱最佳作法指南中的檔案名稱區段。

1. 按一下&#x200B;**建立**。將會顯示「建立主題」訊息。

   您可以選擇在Web編輯器中開啟主題進行編輯，或將主題檔案儲存在AEM存放庫中。

   您從Assets UI建立的每個新主題 **建立** \> **DITA主題** 或Web編輯器指派唯一的主題ID。 此ID的值是檔案名稱本身。 此外，新檔案會儲存為DAM中主題的最新工作副本。 除非您儲存新建立主題的修訂版本，否則在「版本記錄」中不會看到任何版本號碼。 如果您開啟主題進行編輯，版本資訊會顯示在主題檔案之索引標籤的右上角：

   ![](images/topic-version-none_cs.png){width="550" align="left"}

   新建立之主題的版本資訊顯示為 *無*. 儲存新版本時，系統會為其指派版本編號1.0。如需儲存新版本的詳細資訊，請參閱 [另存為新版本](web-editor-features.md#save-as-new-version-id209ME400GXA).


>[!NOTE]
>
> 如果您的管理員已將網頁編輯器設定為在編輯前簽出檔案，則您將無法編輯檔案，直到您簽出為止。 同樣地，如果已設定，您將被要求先入庫任何已出庫的檔案，然後再將其關閉。

>[!IMPORTANT]
>
> 建立DITA主題後，請繼續儲存對工作副本所做的變更，並在完成主題更新後建立新版本。

**父級主題：**[&#x200B;建立和預覽主題](create-preview-topics.md)
