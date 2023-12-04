---
title: Recommendations的效能最佳化
description: 瞭解Recommendations的效能最佳化
source-git-commit: 880cd344ceb65ea339be699ebcad41c0d62e168a
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 0%

---

# Recommendations的效能最佳化 {#id213BD0JG0XA}

針對效能最佳化，請考量下列幾點：

- 若要最佳化內容和索引體驗，請參閱 [最佳化內容搜尋和索引](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html) 在AEM檔案中。

- 使用自訂DITA-OT進行發佈時修補Xerces Jar。 此為強制設定，取決於您的使用案例。 只有當您使用自訂DITA-OT來發佈輸出時，才需要此變更。

  *必要的設定*：將自訂DITA-OT套件中的Xerces Jar檔案取代為隨附的OOTB檔案。 預設的OOTB xercesImpl-2.11.0.jar檔案可在/libs/fmdita/dita\_resources/DITA-OT.zip檔案中使用。 請務必重新命名xercesImpl-2.11.0.jar檔案，以符合要取代的舊Xerces Jar檔案。 這可在執行階段完成。

  此變更可減少發佈時間和記憶體使用率，同時發佈包含大量主題的DITA map。


**父級主題：**[&#x200B;下載並安裝](download-install.md)
