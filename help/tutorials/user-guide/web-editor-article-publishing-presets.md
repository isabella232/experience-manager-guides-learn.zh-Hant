---
title: 從Web編輯器建立輸出預設集
description: 了解如何從網頁編輯器建立輸出預設集
exl-id: 7fde0057-06a5-428e-a91b-9e9386a56270
source-git-commit: 3bca42f0954afc2362ab24f369e698113324dbc3
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# 從Web編輯器建立輸出預設集 {#id218CL400JW3}

執行以下步驟為DITA映射建立輸出預設集：

1. 在資產UI中，導覽至您要編輯的對應檔案。

1. 要獲取映射檔案的獨佔鎖，請選擇映射檔案，然後按一下 **結帳**.

1. 選取 **編輯主題** 選項。

   地圖檔案在Web編輯器中開啟以進行編輯。

   >[!NOTE]
   >
   > 您可以使用進階地圖編輯器從地圖新增或刪除任何主題。 如需詳細資訊，請參閱 [使用進階地圖編輯器](map-editor-advanced-map-editor.md#).

1. 在 **輸出** 頁簽，選擇+表徵圖以為DITA映射建立輸出預設集。

   ![](images/output-tab-preset_cs.png){width="350" align="left"}

1. 在「新增預設集」對話方塊中輸入預設集名稱，然後按一下 **新增**.

1. 輸入以下配置詳細資訊。

   1. 在 **一般** 標籤。 您可以選擇使用或不使用條件來建立輸出預設集。 您也可以使用DITVAL檔案。 AEM參考線也可讓您選取用於發佈特定版本DITA映射的基線。
   1. 在 **AEM** 標籤。 **網站** 顯示AEM存放庫上可用的AEM Sites清單。 **類別**, **區段範本**，和 **文章範本** 是用於組織輸出外觀和感覺的結構元件。 這些預先定義於AEM網站範本中。

      >[!NOTE]
      >
      > 重新整理每個下拉式清單，以在下一個下拉式清單中取得更多分類。

   1. 從 **文章** 頁簽，選擇要為其生成輸出的主題。
1. 選取 **產生預設集** 圖示以產生輸出。

   ![](images/add-preset-articles-tab_cs.png){width="800" align="left"}

1. 您將看到輸出生成過程的狀態。 此 **主題** 欄會列出在 **狀態** 欄顯示每個主題的發佈狀態。

   要查看輸出，請將滑鼠指針懸停在主題上，然後按一下「查看輸出」。

   ![](images/add-preset-output-generated_cs.png){width="800" align="left"}


>[!NOTE]
>
> 您也可以從「選項」菜單中「編輯」、「更名」、「複製」或「刪除現有輸出預設集」。

![](images/edit-preset_cs.png){width="550" align="left"}

**上層主題：**[&#x200B;從網頁編輯器發佈以文章為基礎](web-editor-article-publishing.md)
