---
title: 配置自定義DITA映射模板
description: 瞭解如何配置自定義DITA映射模板
source-git-commit: 5ac066bb8db32944abd046f64da11eeb1bdbe467
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 1%

---


# 配置自定義DITA映射模板 {#id1774F04F05Z}

指AEM南附帶了兩個現成映射模板 — DITA映射和Bookmap。 可以根據這些模板建立地圖；或者，您可以定義自己的映射模板，這些模板隨後可用於建立新的映射。

執行以下步驟以添加自定義映射模板：

1. 以管理員身份登錄Adobe Experience Manager。

1. 在「資產」UI中，導航到配置為儲存映射模板檔案的資料夾。 預設情況下，所有映射模板都儲存在/content/dam/dita-templates/maps資料夾中。

   >[!NOTE]
   >
   > 要配置用於儲存主題或映射模板的自定義位置，請參閱 [配置自定義DITA模板資料夾路徑](conf-template-tags-custom-dita-topic-template.md#id191LCF0095Z)

1. 按一下 **建立** \> **DITA模板**。

1. 在「藍圖」(Bluinet)頁面上，選擇要建立的映射模板的類型。

   >[!NOTE]
   >
   > 您可以使用「映射」或「書籤」模板作為新模板的基礎。

1. 按一下&#x200B;**下一步**。

1. 在新模板「屬性」頁上，輸入 **標題** 和 **名稱** 的子菜單。

   >[!NOTE]
   >
   > 根據模板的「標題」自動建議名稱。 如果要手動指定名稱，請確保「名稱」不包含任何空格、撇號或大括弧，並以.ditamap結尾。

1. 按一下&#x200B;**建立**。

   將出現「Map Created（映射建立）」消息。

   您可以選擇在「映射編輯器」中開啟模板進行編輯，或將模板檔案保存在模板儲存位置。 建立模板後，您可以使用映射編輯器根據創作需要自定義模板。 模板到位後，請確保將其與全局或資料夾級配置檔案相關聯。


下次建立新映射時，模板將顯示在「藍圖」(Blueprient)頁面中。 有關建立DITA映射的詳細資訊，請參見 *使用Adobe Experience Manager指南*。

>[!TIP]
>
> 請參閱 [附錄.md\#](appendix.md#)這樣 *自定義模板* 最佳實踐指南中有關使用自定義映射模板的最佳實踐部分。

**父主題：**[&#x200B;配置主題和映射模板](conf-template-tags.md)

