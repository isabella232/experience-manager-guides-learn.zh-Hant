---
title: 上傳檔案
description: 了解如何上傳檔案
source-git-commit: cc0fbca257d82cc82db5b5da8d263309fd71de55
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---


# 上傳檔案 {#id176FF000JUI}

您很可能擁有要與AEM指南搭配使用的現有DITA內容存放庫。 針對這類現有內容，您可以使用下列任何方法，將內容大量上傳至AEM存放庫：

>[!IMPORTANT]
>
> 請參閱 [將數位資產新增至Adobe Experience Manager as a Cloud Service Assets](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/manage/add-assets.html) 如需AEM中支援內容上傳方法的詳細資訊。

## Assets Console使用者介面

您可以在案頭上選取內容，然後拖曳至AEM使用者介面\（網頁瀏覽器\）至目的地資料夾。 如需詳細資訊，請參閱 [上傳資產](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/manage/add-assets.html#upload-assets) 在AEM檔案中。

## AEM 桌面應用程式

如果您是創意專業人員，且想要管理本機案頭上的資產，請使用AEM案頭應用程式。 您可以使用案頭應用程式開啟和編輯這些資產。 您也可以維護版本，並與其他使用者共用您的檔案。 如需詳細資訊，請參閱 [AEM案頭應用程式](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html).

## 資產大量內嵌

如果您有大規模移轉，偶爾會進行大量內嵌，請使用資產大量內嵌來上傳您的內容。 使用此工具，您可以從支援的資料存放區（例如Azure或S3）上傳大量內容。 如需詳細資訊，請參閱 [資產大量內嵌](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/manage/add-assets.html?lang=en#asset-bulk-ingestor).

## 使用FrameMaker進行大量上傳

Adobe FrameMaker隨附功能強大的AEM連接器，可讓您輕鬆上傳現有的DITA和其他FrameMaker檔案\(`.book` 和 `.fm`\)放入AEM。 您可以使用各種檔案上傳功能，例如上傳單一檔案、上傳包含或不含相依性的完整資料夾（例如內容參考、交叉參考和圖形）。

如需在FrameMaker中使用大量上傳功能的詳細資訊，請參閱區段 *建立CRX資料夾和上傳檔案* （在FrameMaker使用手冊中）。

## 上傳內容時處理錯誤 {#id201MI0I04Y4}

如果無法上傳一或多個檔案，上傳程式結束時會顯示提示，其中包含無法上傳的檔案清單：

![](images/uuid-files-failed-to-upload_cs.png){width="650" align="center"}

如需各種檔案上傳案例的詳細資訊，請參閱 [上傳DITA內容](authoring-file-management.md#).

如果您使用AEM案頭應用程式或資產大量擷取等工具，則對重複檔案執行的動作會由AEM伺服器中的設定控制。 請與系統管理員聯繫，了解此配置。

**上層主題：**[&#x200B;管理內容](authoring.md)

