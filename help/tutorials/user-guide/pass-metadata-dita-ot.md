---
title: 使用DITA-OT將中繼資料傳遞至輸出
description: 了解如何使用DITA-OT將中繼資料傳遞至輸出
source-git-commit: 8b6294425c6e60d1c5b37d98e99114014a104ee6
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---


# 使用DITA-OT將中繼資料傳遞至輸出 {#id21BJ00QD0XA}

中繼資料是有關輸出的其他資訊。 在AEM指南中，您可以傳遞現有中繼資料或建立自訂中繼資料標籤。 您可以使用DITA-OT發佈，將中繼資料傳遞至AEM、PDF、HTML5、EPUB和自訂格式輸出。

執行下列步驟，使用DITA-OT發佈將中繼資料傳遞至輸出：

1. 在 **Assets UI**，導覽至並按一下您要將中繼資料傳遞至DITA-OT的DITA對應檔案。
1. 選取並編輯您要傳遞中繼資料欄位的輸出預設集。 例如，選取PDF輸出預設集。
1. 選擇 **DITA-OT** 在「生成」下 &lt;output> 在選取的輸出預設集中使用選項。

   ![](images/custom-meta-data-output-preset.png)

1. 從「屬性」下拉式清單中，選取您要傳遞至DITA-OT發佈的中繼資料。

   屬性下拉式清單同時列出自訂和預設屬性。 例如，在上述螢幕擷取中，作者是自訂屬性，而 `dc:description`, `dc:language`, `dc:title`，和 `docstate` 為預設屬性。

   >[!NOTE]
   >
   > 這些屬性會從下列位置可用的metadataList檔案中挑選：`/libs/fmdita/config/metadataList`. 依預設，此檔案中列出四個屬性 —  `dc:description`, `dc:language`, `dc:title`，和 `docstate`.

   此檔案可覆蓋於： `/apps/fmdita/config/metadataList`.

   若要傳遞您已定義值的自訂屬性，請參閱 [在DITA-OTPDF輸出中使用AEM中繼資料](https://experienceleaguecommunities.adobe.com/t5/xml-documentation-discussions/use-aem-metadata-in-dita-ot-pdf-output/td-p/411880).

1. 從 **屬性** 下拉式清單，選取所需的自訂和預設屬性。 例如，選取 `author`, `dc:title`，和 `dc:description`. 這些是標準 `metadata/properties` 在建立檔案後建立的。 下拉式方塊下方會列出選取的屬性。

   ![](images/selected-metadata-properties.png)

1. 按一下 **完成** 以儲存變更。
1. 產生輸出。

所選元資料屬性將傳遞至使用DITA-OT產生的輸出。

**上層主題：**[&#x200B;產生輸出](generate-output.md)

