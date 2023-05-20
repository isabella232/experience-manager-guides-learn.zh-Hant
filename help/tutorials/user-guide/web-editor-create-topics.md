---
title: 建立主題
description: 瞭解如何建立主題
exl-id: 336bbbff-f268-40be-ad3a-9c72923be71b
source-git-commit: 8073716bccacbe8d6a158b44d5106b083e3a5dcd
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 0%

---

# 建立主題 {#id2056AL00O5Z}

指AEM南允許您建立類型的DITA主題 — 主題、任務、概念、引用、辭彙表、DITAVAL等。 除了基於現成模板建立主題外，您還可以定義自定義模板。 有關使用自定義DITA模板的詳細資訊，請參見 *配置用於創作的模板和標籤* 在安裝和配置Adobe Experience Manager指南as a Cloud Service。

執行以下步驟建立主題：

1. 在「資產」UI中，導航到要建立主題的位置。

1. 要建立新主題，請按一下 **建立** \> **DITA主題**。

1. 在「藍圖」頁面上，選擇要建立的DITA文檔類型，然後按一下 **下一個**。

   ![](images/create_dita_topic.png){width="800" align="left"}

   預設情況下，AEM參考線提供最常用的DITA主題模板。 您可以根據組織要求配置更多主題模板，請參閱 *配置用於創作的模板和標籤* 在安裝和配置Adobe Experience Manager指南as a Cloud Service。

   >[!NOTE]
   >
   > 在資產UI的清單視圖中，DITA主題類型在「類型」列中顯示為「主題」、「任務」、「概念」、「引用」、「Glossentry」或「DITAVAL」。 DITA映射顯示為映射。

1. 在「屬性」頁上，指定文檔 **標題**。

1. \（可選\）指定檔案 **名稱**。

   如果管理員已基於UUID設定配置了自動檔案名，則您將看不到指定檔案名的選項。 基於UUID的檔案名將自動分配給該檔案。

   如果檔案命名選項可用，則還會根據 **標題** 的雙曲餘切值。 如果要手動指定文檔名稱，請確保 **名稱** 不包含任何空格、撇號或大括弧，並以.xml或.dita結尾。 預設情況下，「AEM參考線」會用連字元替換所有特殊字元。 有關命名DITA檔案的最佳實踐，請參閱最佳實踐指南中的「檔案名」部分。

1. 按一下&#x200B;**建立**。出現「Topic Created（建立主題）」消息。

   您可以選擇在Web編輯器中開啟主題進行編輯，或將主題檔案保存在儲存AEM庫中。

   從資產UI建立的每個新主題 **建立** \> **DITA主題** 或為Web編輯器分配唯一的主題ID。 此ID的值是檔案名本身。 此外，新文檔將保存為DAM中主題的最新工作副本。 在保存新建立主題的修訂版之前，您不會在版本歷史記錄中看到任何版本號。 如果開啟主題進行編輯，則版本資訊顯示在主題檔案頁籤的右上角：

   ![](images/topic-version-none_cs.png){width="550" align="left"}

   新建立主題的版本資訊顯示為 *無*。 保存新版本時，系統會為其分配版本號1.0。有關保存新版本的詳細資訊，請參見 [另存為新版本](web-editor-features.md#save-as-new-version-id209ME400GXA)。


>[!NOTE]
>
> 如果管理員已將Web編輯器配置為在編輯前簽出檔案，則在簽出檔案之前，您將無法編輯該檔案。 同樣，如果配置了，系統會要求您在關閉任何簽出檔案之前先將其簽入。

>[!IMPORTANT]
>
> 建立DITA主題後，繼續保存對工作副本所做的更改，並在完成對主題的更新後建立新版本。

**父主題：**[&#x200B;建立和預覽主題](create-preview-topics.md)
