---
title: 上傳檔案
description: 瞭解如何將檔案上傳至AEM存放庫並處理錯誤。 瞭解資產控制檯使用者介面、AEM案頭應用程式、資產大量擷取器，以及使用FrameMaker進行大量上傳。
exl-id: d6a73953-94dd-4fa5-b09c-5e4c77fead62
source-git-commit: 8504a0a52d381044bf1f0d6e7de3585ebecf3a7b
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# 上傳檔案 {#id176FF000JUI}

最有可能的情況是，您擁有要搭配AEM Guides使用的現有DITA內容的存放庫。 對於這類現有內容，您可以使用下列任何一種方法，將內容大量上傳至AEM存放庫：

>[!IMPORTANT]
>
> 另請參閱 [將數位資產新增至Adobe Experience Manager as a Cloud Service資產](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/manage/add-assets.html) 以瞭解AEM支援的內容上傳方法的詳細資訊。

## Assets控制檯使用者介面

您可以在案頭上選取內容，並在AEM使用者介面\（網頁瀏覽器\）上拖曳至目的地資料夾。 如需詳細資訊，請參閱 [上傳資產](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/manage/add-assets.html#upload-assets) 在AEM檔案中。

## AEM 桌面應用程式

如果您是創意專業人員，且想要管理本機案頭上的資產，請使用AEM案頭應用程式。 您可以使用案頭應用程式開啟及編輯這些資產。 您也可以維護版本，並與其他使用者共用檔案。 如需詳細資訊，請參閱 [AEM案頭應用程式](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html).

## 資產大量擷取器

如果您有大規模移轉和偶爾的大量擷取，請使用資產大量擷取器來上傳您的內容。 使用此工具，您可以從支援的資料存放區（例如Azure或S3）上傳大量內容。 如需詳細資訊，請參閱 [資產大量擷取器](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/manage/add-assets.html?lang=en#asset-bulk-ingestor).

## 使用FrameMaker進行大量上傳

Adobe FrameMaker隨附強大的AEM聯結器，可讓您輕鬆上傳現有的DITA和其他FrameMaker檔案\(`.book` 和 `.fm`\)到AEM中。 您可以使用各種檔案上傳功能，例如上傳單一檔案、上傳具有或不具有相依性的完整資料夾\（如內容參照、交叉參照和圖形\）。

如需有關在FrameMaker中使用大量上傳功能的詳細資訊，請參閱區段 *建立CRX資料夾並上傳檔案* 在FrameMaker使用手冊中。

## 上傳內容時的錯誤處理 {#id201MI0I04Y4}

如果上傳一或多個檔案失敗，會在上傳程式結束時顯示提示，其中包含上傳失敗的檔案清單：

![](images/uuid-files-failed-to-upload_cs.png){width="650" align="center"}

如需各種檔案上傳情況的詳細資訊，請參閱 [上傳DITA內容](authoring-file-management.md#).

如果您使用AEM案頭應用程式或資產大量擷取器之類的工具，則對重複檔案執行的動作會由AEM伺服器中的設定控制。 請連絡您的系統管理員以瞭解此設定。

**父級主題：**[&#x200B;管理內容](authoring.md)
