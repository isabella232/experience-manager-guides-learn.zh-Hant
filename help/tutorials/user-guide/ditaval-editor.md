---
title: 使用DITAVAL編輯器
description: 瞭解如何使用AEM Guides中的DIVATAL Editor建立和編輯DITAVAL檔案。 瞭解DITAVAL編輯器如何在製作和來源檢視中支援DITAVAL檔案。
source-git-commit: 880cd344ceb65ea339be699ebcad41c0d62e168a
workflow-type: tm+mt
source-wordcount: '758'
ht-degree: 0%

---

# DITAVAL編輯器 {#ditaval-editor}

DITAVAL檔案用於產生條件輸出。 在單一主題中，您可以使用元素屬性來新增條件，以條件化內容。 然後，您會建立DITAVAL檔案，在其中指定應擷取以產生內容的條件，以及應從最終輸出中排除哪些條件。

AEM Guides可讓您使用DITAVAL編輯器輕鬆建立及編輯DITAVAL檔案。 DITAVAL編輯器會擷取您系統中定義的屬性\（或標籤\），您可以使用它們來建立或編輯DITAVAL檔案。 如需有關在AEM中建立和管理標籤的詳細資訊，請參閱 [管理標籤](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/features/tags.html?lang=en) 一節(在AEM檔案中)。

## 建立DITAVAL檔案

執行以下步驟來建立DITAVAL檔案：

1. 在Assets UI中，導覽至您要建立DITAVAL檔案的位置。

1. 按一下 **建立** \> **DITA主題**.

1. 在Blueprint頁面上，選取DITAVAL檔案範本並按一下 **下一個**.

1. 在「特性」頁面中指定 **標題** 和 **名稱** 用於DITAVAL檔案。

   >[!NOTE]
   >
   > 系統會根據檔案的標題自動建議名稱。 如果您要手動指定檔案名稱，請確定「名稱」不含任何空格、單引號或大括弧，且結尾為.ditaval。

1. 按一下「**建立**」。「主題已建立」訊息便會顯示。

   您可以選擇開啟DITAVAL檔案以在DITAVAL編輯器中編輯，或將主題檔案儲存在AEM存放庫中。


## 編輯DITAVAL檔案

執行以下步驟來編輯DITAVAL檔案：

1. 在Assets UI中，導覽至您要編輯的DITAVAL檔案。

1. 若要取得檔案的獨佔鎖定，請選取檔案並按一下 **簽出**.

1. 選取檔案並按一下 **編輯** 以在AEM Guides DITAVAL編輯器中開啟檔案。

   DITAVAL編輯器可讓您執行下列工作：

   A：切換左側面板切換左側面板檢視。 如果您已透過DITA map開啟DITAVAL檔案，則地圖和存放庫會顯示在此面板中。 如需有關透過DITA map開啟檔案的詳細資訊，請參閱 [透過DITA map編輯主題](map-editor-advanced-map-editor.md#id17ACJ0F0FHS).

   B：儲儲存存您在檔案中所做的變更。 所有變更都會儲存在檔案的目前版本中。

   C：新增屬性在您的DITAVAL檔案中新增單一屬性。

   ![](images/ditaval-editor-props.png)

   第一個下拉式清單列出可在DITAVAL檔案中使用的允許DITA屬性。 有五個支援的屬性 —  `audience`， `platform`， `product`， `props`、和 `otherprops`.

   第二個下拉式清單會顯示為選取的屬性設定的值。 然後，下一個下拉式清單會顯示您可在選取的屬性上設定的動作。 動作下拉式清單允許的值為 —  `include`， `exclude`， `passthrough`、和 `flag`. 如需這些值的詳細資訊，請參閱 [prop](http://docs.oasis-open.org/dita/dita/v1.3/errata01/os/complete/part3-all-inclusive/langRef/ditaval/ditaval-prop.html#ditaval-prop) OASIS DITA檔案中的元素

   D：新增所有特性如果您只要按一下即可新增系統中定義的所有條件特性或屬性，請使用「新增所有特性」功能。

   >[!NOTE]
   >
   > 如果DITAVAL檔案中已存在所有已定義的條件屬性，則無法新增更多屬性。 在此案例中，您會收到一則錯誤訊息。

   ![](images/ditaval-all-props.png)

1. 完成編輯DITAVAL檔案後，請按一下 **儲存**.

   >[!NOTE]
   >
   > 如果您關閉檔案而不儲存，變更將會遺失。 如果您不想將變更提交至AEM存放庫，請按一下 **關閉**，然後按一下 **關閉而不儲存** 在 **未儲存的變更** 對話方塊。


## DITAVAL編輯器檢視

AEM Guides的DITAVAL編輯器支援以兩種不同的模式或檢視檢視DITAVAL檔案：

**作者**：這是一般您看到的DITAVAL編輯器的內容\(WYSISYG\)檢視。 您可以使用簡單使用者介面新增或移除屬性，該介面會在下拉式清單中顯示屬性、屬性和動作。 在「作者」檢視中，您有選項可按一下插入個別屬性，以及插入所有屬性。

您也可以將指標暫留在檔案名稱上，找到目前使用的DITAVAL檔案版本。

**來源**：來源檢視會顯示構成DITAVAL檔案的基礎XML。 除了在此檢視中進行一般文字編輯外，作者也可以使用「智慧型目錄」新增或編輯屬性。

若要叫用智慧型錄，請將游標放在任何屬性定義的結尾並輸入&quot;&lt;&quot;。 編輯器將顯示您可以在該位置插入的所有有效XML元素清單。

![](images/ditaval-source-view.png)
