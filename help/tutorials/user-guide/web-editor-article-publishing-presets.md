---
title: 從網頁編輯器建立輸出預設集
description: 瞭解如何從網頁編輯器建立輸出預設集
exl-id: 7fde0057-06a5-428e-a91b-9e9386a56270
source-git-commit: 3bca42f0954afc2362ab24f369e698113324dbc3
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# 從網頁編輯器建立輸出預設集 {#id218CL400JW3}

執行以下步驟來建立DITA map的輸出預設集：

1. 在Assets UI中，導覽至您要編輯的對映檔案。

1. 若要取得對映檔案的獨佔鎖定，請選取對映檔案並按一下 **簽出**.

1. 選取 **編輯主題** 對映檔案上動作選單中的選項。

   會開啟對應檔案，以便在網頁編輯器中編輯。

   >[!NOTE]
   >
   > 您可以使用「進階地圖編輯器」，在地圖中新增或刪除任何主題。 如需詳細資訊，請參閱 [使用進階地圖編輯器](map-editor-advanced-map-editor.md#).

1. 在 **輸出** 索引標籤中，選取+圖示以建立DITA map的輸出預設集。

   ![](images/output-tab-preset_cs.png){width="350" align="left"}

1. 在「新增預設集」對話方塊中輸入預設集名稱，然後按一下 **新增**.

1. 輸入下列組態詳細資料。

   1. 選取「 」中所需的選項 **一般** 標籤。 您可以選擇建立附帶或不附帶條件的輸出預設集。 您也可以使用DITVAL檔案。 AEM Guides也可讓您選取基準線，以發佈特定版本的DITA map。
   1. 在「 」中輸入「AEM網站」詳細資料 **AEM** 標籤。 **網站** 顯示AEM存放庫中可用的AEM Sites清單。 **類別**， **區段範本**、和 **文章範本** 是用於組織輸出外觀與感覺的結構元件。 這些在AEM網站範本中預先定義。

      >[!NOTE]
      >
      > 重新整理每個下拉式清單，以便在下一個下拉式清單中取得進一步的分類。

   1. 從 **文章** 標籤中，選取您要產生輸出的主題。
1. 選取 **產生預設集** 圖示以產生輸出。

   ![](images/add-preset-articles-tab_cs.png){width="800" align="left"}

1. 您將會看到輸出產生程式的狀態。 此 **主題** 欄會列出產生輸出的主題， **狀態** 欄會顯示每個主題的發佈狀態。

   若要檢視輸出，請將滑鼠指標停留在主題上，然後按一下「檢視輸出」。

   ![](images/add-preset-output-generated_cs.png){width="800" align="left"}


>[!NOTE]
>
> 您也可以從「選項」選單中「編輯」、「重新命名」、「複製」或「刪除」現有的輸出預設集。

![](images/edit-preset_cs.png){width="550" align="left"}

**父級主題：**[&#x200B;從Web編輯器以文章為基礎的發佈](web-editor-article-publishing.md)
