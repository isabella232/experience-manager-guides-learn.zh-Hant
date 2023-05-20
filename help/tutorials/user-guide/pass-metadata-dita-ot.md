---
title: 使用DITA-OT將元資料傳遞到輸出
description: 瞭解如何使用DITA-OT將元資料傳遞到輸出
exl-id: 637895e5-aece-4827-a32e-f2ae3e3704ef
source-git-commit: c74badebbcb4733fb9caa79c646b1d1e5c8bfe8e
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# 使用DITA-OT將元資料傳遞到輸出 {#id21BJ00QD0XA}

元資料是有關輸出的其他資訊。 在指AEM南中，您可以傳遞現有元資料或建立自定義元資料標籤。 可以使用DITA-OT發佈將元AEM資料傳遞到、PDF、HTML5、EPUB和自定義格式輸出。

執行以下步驟，使用DITA-OT發佈將元資料傳遞到輸出：

1. 在 **資產UI**，導航到要將元資料傳遞給DITA-OT的DITA映射檔案並按一下該檔案。
1. 選擇並編輯要向其傳遞元資料欄位的輸出預設。 例如，選擇PDF輸出預設。
1. 選擇 **DITA-OT** 在生成 &lt;output> 在所選輸出預設中使用選項。

   ![](images/custom-meta-data-output-preset.png){width="800" align="left"}

1. 從「屬性」下拉清單中，選擇要傳遞到DITA-OT發佈的元資料。

   屬性下拉清單同時列出自定義屬性和預設屬性。 例如，在上面的螢幕截圖作者中是自定義屬性， `dc:description`。 `dc:language`。 `dc:title`, `docstate` 是預設屬性。

   >[!NOTE]
   >
   > 這些屬性是從以下位置可用的metadataList檔案中選取的：`/libs/fmdita/config/metadataList`。 預設情況下，此檔案中列有四個屬性。 `dc:description`。 `dc:language`。 `dc:title`, `docstate`。

   可以在以下位置覆蓋此檔案： `/apps/fmdita/config/metadataList`。

   要傳遞已定義值的自定義屬性，請參見 [在AEMDITA-OTPDF輸出中使用元資料](https://experienceleaguecommunities.adobe.com/t5/xml-documentation-discussions/use-aem-metadata-in-dita-ot-pdf-output/td-p/411880)。

1. 從 **屬性** 下拉菜單，選擇所需的自定義和預設屬性。 例如，選擇 `author`。 `dc:title`, `dc:description`。 這些是 `metadata/properties` 建立檔案後建立的。 所選屬性列在下拉清單框下方。

   ![](images/selected-metadata-properties.png){width="300" align="left"}

1. 按一下 **完成** 的子菜單。
1. 生成輸出。

選定的元資料屬性將傳遞給使用DITA-OT生成的輸出。

**父主題：**[&#x200B;輸出生成](generate-output.md)
