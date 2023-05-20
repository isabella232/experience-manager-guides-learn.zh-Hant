---
title: 從Web編輯器建立輸出預設
description: 瞭解如何從Web編輯器建立輸出預設
exl-id: 7fde0057-06a5-428e-a91b-9e9386a56270
source-git-commit: 3bca42f0954afc2362ab24f369e698113324dbc3
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# 從Web編輯器建立輸出預設 {#id218CL400JW3}

執行以下步驟為DITA映射建立輸出預設：

1. 在資產UI中，導航到要編輯的映射檔案。

1. 要獲取映射檔案上的獨佔鎖，請選擇映射檔案，然後按一下 **簽出**。

1. 選擇 **編輯主題** 選項。

   映射檔案在Web編輯器中開啟以供編輯。

   >[!NOTE]
   >
   > 可以使用高級映射編輯器從映射中添加或刪除任何主題。 有關詳細資訊，請參閱 [使用高級映射編輯器](map-editor-advanced-map-editor.md#)。

1. 在 **輸出** 頁籤，選擇+表徵圖為DITA映射建立輸出預設。

   ![](images/output-tab-preset_cs.png){width="350" align="left"}

1. 在「添加預設」對話框中輸入預設的名稱，然後按一下 **添加**。

1. 輸入以下配置詳細資訊。

   1. 在 **常規** 頁籤。 您可以選擇建立帶條件或不帶條件的輸出預設。 您還可以使用DITVAL檔案。 AEM參考線還允許您選擇用於發佈特定版本的DITA映射的基線。
   1. 在中AEM輸入站點詳細資訊 **AEM** 頁籤。 **站點** 顯示儲存庫上可用的AEM SitesAEM清單。 **類別**。 **節模板**, **文章模板** 是用於組織輸出外觀的結構元件。 這些是在「站點」模AEM板中預定義的。

      >[!NOTE]
      >
      > 刷新每個下拉清單以在下一個下拉清單中獲取進一步的分類。

   1. 從 **條目** 頁籤，選擇要為其生成輸出的主題。
1. 選擇 **生成預設** 表徵圖以生成輸出。

   ![](images/add-preset-articles-tab_cs.png){width="800" align="left"}

1. 您將看到輸出生成進程的狀態。 的 **主題** 列列出在 **狀態** 列顯示每個主題的發佈狀態。

   要查看輸出，請將滑鼠指針懸停在主題上，然後按一下「查看輸出」。

   ![](images/add-preset-output-generated_cs.png){width="800" align="left"}


>[!NOTE]
>
> 也可以從「選項」菜單中編輯、更名、複製或刪除現有輸出預設。

![](images/edit-preset_cs.png){width="550" align="left"}

**父主題：**[&#x200B;基於文章的Web編輯器發佈](web-editor-article-publishing.md)
