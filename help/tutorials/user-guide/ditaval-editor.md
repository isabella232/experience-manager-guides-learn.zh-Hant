---
title: 使用DITAVAL編輯器
description: 瞭解如何使用DITAVAL編輯器
source-git-commit: c6eceb8ea3ce41f12ea1f689dc8aeab2b4ba3d9c
workflow-type: tm+mt
source-wordcount: '758'
ht-degree: 0%

---


# DITAVAL編輯器 {#ditaval-editor}

DITAVAL檔案用於生成條件輸出。 在單個主題中，可以使用元素屬性添加條件以條件化內容。 然後，建立DITAVAL檔案，在該檔案中，您指定了生成內容時應選取的條件，以及最終輸出中應遺漏的條件。

使AEM用參考線可以使用DITAVAL編輯器輕鬆建立和編輯DITAVAL檔案。 DITAVAL編輯器將檢索系統中定義的屬性\（或標籤\），您可以使用這些屬性建立或編輯DITAVAL檔案。 有關在中建立和管理標籤的詳細信AEM息，請參見 [管理標籤](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/features/tags.html?lang=en) 的上AEM界。

## 建立DITAVAL檔案

執行以下步驟建立DITAVAL檔案：

1. 在「資產」UI中，導航到要建立DITAVAL檔案的位置。

1. 按一下 **建立** \> **DITA主題**。

1. 在「藍圖」(Bluinet)頁面上，選擇DITAVAL檔案模板，然後按一下 **下一個**。

1. 在「屬性」頁上，指定 **標題** 和 **名稱** DITAVAL檔案。

   >[!NOTE]
   >
   > 根據檔案的「標題」自動建議名稱。 如果要手動指定檔案名，請確保「名稱」不包含任何空格、撇號或大括弧，並以.ditaval結尾。

1. 按一下&#x200B;**建立**。出現「Topic Created（建立主題）」消息。

   您可以選擇在DITAVAL編輯器中開啟DITAVAL檔案進行編輯，或在儲存庫中保存主AEM題檔案。


## 編輯DITAVAL檔案

執行以下步驟編輯DITAVAL檔案：

1. 在「資產」UI中，導航到要編輯的DITAVAL檔案。

1. 要獲取檔案的獨佔鎖，請選擇該檔案，然後按一下 **簽出**。

1. 選擇檔案並按一下 **編輯** 在「參考線」DITAVAL編AEM輯器中開啟檔案。

   DITAVAL編輯器允許您執行以下任務：

   答：切換左面板切換左面板視圖。 如果已通過DITA映射開啟DITAVAL檔案，則此面板中將顯示映射和儲存庫。 有關通過DITA映射開啟檔案的詳細資訊，請參見 [通過DITA映射編輯主題](map-editor-advanced-map-editor.md#id17ACJ0F0FHS)。

   B:保存保存在檔案中所做的更改。 所有更改都保存在檔案的當前版本中。

   C:添加屬性在DITAVAL檔案中添加單個屬性。

   ![](images/ditaval-editor-props.png)

   第一個下拉框列出了可在DITAVAL檔案中使用的允許的DITA屬性。 支援五個屬性 —  `audience`。 `platform`。 `product`。 `props`, `otherprops`。

   第二個下拉清單顯示為所選屬性配置的值。 然後，下一個下拉清單顯示可在選定屬性上配置的操作。 操作下拉清單中允許的值為 —  `include`。 `exclude`。 `passthrough`, `flag`。 有關這些值的詳細資訊，請參閱 [托](http://docs.oasis-open.org/dita/dita/v1.3/errata01/os/complete/part3-all-inclusive/langRef/ditaval/ditaval-prop.html#ditaval-prop) OASIS DITA文檔中的元素

   D:添加所有屬性如果要添加系統中定義的所有條件屬性或屬性，只需按一下一次，則使用添加所有屬性功能。

   >[!NOTE]
   >
   > 如果DITAVAL檔案中已存在所有已定義的條件屬性，則不能添加更多屬性。 您在此方案中會收到錯誤消息。

   ![](images/ditaval-all-props.png)

1. 編輯完DITAVAL檔案後，按一下 **保存**。

   >[!NOTE]
   >
   > 如果關閉檔案而不保存，則更改將丟失。 如果不想將更改提交到儲存AEM庫，請按一下 **關閉**，然後按一下 **關閉而不保存** 的 **未保存的更改** 對話框。


## DITAVAL編輯器視圖

輔助AEM線的DITAVAL編輯器支援以兩種不同模式或視圖查看DITAVAL檔案：

**作者**:這是DITAVAL編輯器的典型「您看到的內容」視圖\(WYSISYG\)。 可以使用簡單用戶介面添加或刪除屬性，該介面在下拉清單中顯示屬性、其值和操作。 在「作者」視圖中，您可以選擇插入單個屬性，並通過按一下插入所有屬性。

您還可以通過將指針懸停在檔案名上來找到當前正在處理的DITAVAL檔案的版本。

**源**:「源」視圖顯示組成DITAVAL檔案的基礎XML。 除了在此視圖中進行常規文本編輯外，作者還可以使用智慧目錄添加或編輯屬性。

要調用智慧目錄，請將游標置於任何屬性定義的末尾，然後輸入「&lt;」。 編輯器將顯示可在該位置插入的所有有效XML元素的清單。

![](images/ditaval-source-view.png)

