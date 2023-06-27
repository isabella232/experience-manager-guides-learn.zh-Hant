---
title: 設定自訂DITA map範本
description: 瞭解如何設定自訂DITA map範本
source-git-commit: 6051181e243cf71919901093c1b5590f21832545
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 1%

---


# 設定自訂DITA map範本 {#id1774F04F05Z}

AEM Guides隨附兩個現成可用的地圖範本：DITA map和Bookmap。 您可以根據這些範本建立對映；或者，您可以定義自己的對映範本，然後將其用於建立新對映。

執行以下步驟以新增自訂地圖範本：

1. 以管理員身分登入Adobe Experience Manager。

1. 在Assets UI中，導覽至設定用來儲存對應範本檔案的資料夾。 依預設，所有對應範本都會儲存在/content/dam/dita-templates/maps資料夾中。

   >[!NOTE]
   >
   > 若要設定自訂位置以儲存主題或對應範本，請參閱 [設定自訂DITA範本資料夾路徑](conf-template-tags-custom-dita-topic-template.md#id191LCF0095Z)

1. 按一下 **建立** \> **DITA範本**.

1. 在Blueprint頁面上，選取您要建立的對應範本型別。

   >[!NOTE]
   >
   > 您可以使用Map或Bookmap範本作為新範本的基礎。

1. 按一下&#x200B;**下一步**。

1. 在新範本的「屬性」頁面上，輸入 **標題** 和 **名稱** 範本的。

   >[!NOTE]
   >
   > 系統會根據範本的標題自動建議名稱。 如果您要手動指定名稱，請確定名稱不包含任何空格、單引號或大括弧，且結尾為.ditamap。

1. 按一下&#x200B;**建立**。

   便會顯示「已建立對應」訊息。

   您可以選擇在「對映編輯器」中開啟範本以進行編輯，或將範本檔案儲存在範本存放區位置。 建立範本後，您就可以根據編寫需求，使用地圖編輯器來自訂範本。 設定好範本後，請確定您將其與全域或資料夾層級設定檔建立關聯。


下次您建立新地圖時，範本會顯示在Blueprint頁面中。 如需有關建立DITA map的詳細資訊，請參閱使用Adobe Experience Manager Guidesas a Cloud Service指南。

>[!TIP]
>
> 另請參閱 *自訂範本* 最佳作法指南中的區段，以瞭解使用自訂地圖範本的最佳作法。

**父級主題：**[&#x200B;設定主題和對應範本](conf-template-tags.md)

