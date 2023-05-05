---
title: 使用DITAVAL編輯器
description: 了解如何使用DITAVAL編輯器
source-git-commit: c6eceb8ea3ce41f12ea1f689dc8aeab2b4ba3d9c
workflow-type: tm+mt
source-wordcount: '758'
ht-degree: 0%

---


# DITAVAL編輯器 {#ditaval-editor}

DITAVAL檔案用於生成條件輸出。 在單一主題中，您可以使用元素屬性來新增條件，以條件化內容。 然後，建立DITAVAL檔案，在其中指定應提取哪些條件以生成內容，以及哪些條件應從最終輸出中保留。

AEM參考線允許您使用DITAVAL編輯器輕鬆建立和編輯DITAVAL檔案。 DITAVAL編輯器檢索系統中定義的屬性\（或標籤\），您可以使用這些屬性來建立或編輯DITAVAL檔案。 如需在AEM中建立和管理標籤的詳細資訊，請參閱 [管理標籤](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/features/tags.html?lang=en) 一節。

## 建立DITAVAL檔案

執行以下步驟以建立DITAVAL檔案：

1. 在「資產」UI中，導覽至您要建立DITAVAL檔案的位置。

1. 按一下 **建立** \> **DITA主題**.

1. 在「Blueprint」(Blueprint)頁面上，選擇「DITAVAL檔案模板」(DITAVAL file template)，然後按一下 **下一個**.

1. 在「屬性」頁面上，指定 **標題** 和 **名稱** DITAVAL檔案。

   >[!NOTE]
   >
   > 系統會根據檔案的標題自動建議名稱。 如果要手動指定檔案名，請確保「名稱」中不包含任何空格、縮寫符號或大括弧，並以.ditaval結尾。

1. 按一下&#x200B;**建立**。此時將顯示「已建立主題」消息。

   您可以選擇在DITAVAL編輯器中開啟DITAVAL檔案進行編輯，或在AEM儲存庫中保存主題檔案。


## 編輯DITAVAL檔案

執行以下步驟來編輯DITAVAL檔案：

1. 在「資產」UI中，導覽至您要編輯的DITAVAL檔案。

1. 要獲取對檔案的獨佔鎖定，請選擇該檔案並按一下 **結帳**.

1. 選取檔案，然後按一下 **編輯** 以在AEM參考線DITAVAL編輯器中開啟檔案。

   DITAVAL編輯器允許您執行以下任務：

   答：切換「左側面板」切換左側面板檢視。 如果您已透過DITA映射開啟DITAVAL檔案，則此面板中會顯示映射和儲存庫。 有關通過DITA映射開啟檔案的詳細資訊，請參見 [透過DITA映射編輯主題](map-editor-advanced-map-editor.md#id17ACJ0F0FHS).

   B:保存保存在檔案中所做的更改。 所有變更都會儲存在檔案的目前版本中。

   C:添加屬性在DITAVAL檔案中添加單個屬性。

   ![](images/ditaval-editor-props.png)

   第一個下拉式清單列出可在DITAVAL檔案中使用的允許DITA屬性。 支援5個屬性 —  `audience`, `platform`, `product`, `props`，和 `otherprops`.

   第二個下拉式清單顯示為所選屬性設定的值。 然後，下一個下拉式清單會顯示您可以在選取的屬性上設定的動作。 動作下拉式清單中允許的值為 —  `include`, `exclude`, `passthrough`，和 `flag`. 如需這些值的詳細資訊，請參閱 [prop](http://docs.oasis-open.org/dita/dita/v1.3/errata01/os/complete/part3-all-inclusive/langRef/ditaval/ditaval-prop.html#ditaval-prop) OASIS DITA檔案中的元素

   D:添加所有屬性如果只要按一下即可添加系統中定義的所有條件屬性或屬性，請使用添加所有屬性功能。

   >[!NOTE]
   >
   > 如果DITAVAL檔案中已存在所有已定義的條件屬性，則無法添加更多屬性。 您會在此案例中收到錯誤訊息。

   ![](images/ditaval-all-props.png)

1. 完成DITAVAL檔案的編輯後，按一下 **儲存**.

   >[!NOTE]
   >
   > 如果您未儲存即關閉檔案，變更將會遺失。 如果您不想將變更提交至AEM存放庫，請按一下 **關閉**，然後按一下 **關閉而不保存** 在 **未儲存的變更** 對話框。


## DITAVAL編輯器視圖

AEM參考線的DITAVAL編輯器支援以兩種不同模式或檢視來檢視DITAVAL檔案：

**作者**:這是DITAVAL編輯器的典型「What You Get \(WYSISYG\)(您看到的是DITAVAL編輯器的\(WYSISYG\))」視圖。 您可以使用簡單的使用者介面來新增或移除屬性，其中會顯示下拉式清單中的屬性、其值和動作。 在「作者」檢視中，您有選項可以插入個別屬性，並只要按一下即可插入所有屬性。

您也可以將指針移至檔案名稱上方，以找到目前使用的DITAVAL檔案版本。

**來源**:「源」視圖顯示組成DITAVAL檔案的基礎XML。 除了在此檢視中進行一般文字編輯外，作者也可以使用智慧型目錄來新增或編輯屬性。

要調用智慧目錄，請將游標置於任何屬性定義的末尾，然後輸入&quot;&lt;&quot;。 編輯器將顯示可在該位置插入的所有有效XML元素的清單。

![](images/ditaval-source-view.png)

