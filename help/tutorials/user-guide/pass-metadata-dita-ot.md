---
title: 使用DITA-OT將中繼資料傳遞至輸出
description: 瞭解如何使用DITA-OT將中繼資料傳遞至輸出
exl-id: 637895e5-aece-4827-a32e-f2ae3e3704ef
source-git-commit: c74badebbcb4733fb9caa79c646b1d1e5c8bfe8e
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# 使用DITA-OT將中繼資料傳遞至輸出 {#id21BJ00QD0XA}

中繼資料是關於輸出的其他資訊。 在AEM Guides中，您可以傳遞現有的中繼資料或建立自訂中繼資料標籤。 您可以使用DITA-OT發佈將中繼資料傳遞至AEM、PDF、HTML5、EPUB和自訂格式輸出。

執行以下步驟，使用DITA-OT發佈將中繼資料傳遞至輸出：

1. 在 **Assets UI**，導覽至您要為其將中繼資料傳遞至DITA-OT的DITA map檔案，並按一下該檔案。
1. 選取並編輯您要傳遞中繼資料欄位的輸出預設集。 例如，選取「PDF輸出預設集」。
1. 選取 **DITA-OT** 在「產生」下 &lt;output> 使用所選輸出預設集中的選項。

   ![](images/custom-meta-data-output-preset.png){width="800" align="left"}

1. 從屬性下拉式清單中選取您要傳遞至DITA-OT發佈的中繼資料。

   「屬性」下拉式清單會列出自訂和預設屬性。 例如，在上述熒幕擷圖作者中，是自訂屬性，而 `dc:description`， `dc:language`， `dc:title`、和 `docstate` 是預設屬性。

   >[!NOTE]
   >
   > 這些屬性是從以下位置可用的metadataList檔案中挑選的：`/libs/fmdita/config/metadataList`. 依預設，此檔案中列出四個屬性 —  `dc:description`， `dc:language`， `dc:title`、和 `docstate`.

   此檔案可覆蓋於： `/apps/fmdita/config/metadataList`.

   若要傳遞您已為其定義值的自訂屬性，請參閱 [在DITA-OTPDF輸出中使用AEM中繼資料](https://experienceleaguecommunities.adobe.com/t5/xml-documentation-discussions/use-aem-metadata-in-dita-ot-pdf-output/td-p/411880).

1. 從 **屬性** 在下拉式清單中，選取所需的自訂和預設屬性。 例如，選取 `author`， `dc:title`、和 `dc:description`. 這些是標準 `metadata/properties` 建立檔案後便會建立該檔案。 選取的屬性會列在Dropbox下方。

   ![](images/selected-metadata-properties.png){width="300" align="left"}

1. 按一下 **完成** 以儲存變更。
1. 產生輸出。

所選的中繼資料屬性將傳遞至使用DITA-OT產生的輸出。

**父級主題：**[&#x200B;輸出產生](generate-output.md)
