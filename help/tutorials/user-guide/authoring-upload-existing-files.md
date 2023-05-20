---
title: 上載檔案
description: 瞭解如何上載檔案
exl-id: d6a73953-94dd-4fa5-b09c-5e4c77fead62
source-git-commit: 8073716bccacbe8d6a158b44d5106b083e3a5dcd
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# 上載檔案 {#id176FF000JUI}

您很可能擁有一個儲存有要與指南一起使用的現有DITA內容的存AEM儲庫。 對於此類現有內容，您可以使用以下任何方法將內容批量上載到儲存AEM庫：

>[!IMPORTANT]
>
> 請參閱 [將數字資產添加到Adobe Experience Manager as a Cloud Service資產](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/manage/add-assets.html) 中的受支援內容上載方法的詳細資訊AEM。

## 資產控制台用戶介面

您可以選擇案頭上的內容，然後AEM將用戶介面\（web瀏覽器\）拖動到目標資料夾。 有關詳細資訊，請參閱 [上載資產](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/manage/add-assets.html#upload-assets) 的上AEM界。

## AEM 桌面應用程式

如果您AEM是具有創意的專業人員，並且希望管理本地案頭上的資產，請使用案頭應用。 您可以使用案頭應用程式開啟和編輯這些資產。 您還可以維護版本，並與其他用戶共用您的檔案。 有關詳細資訊，請參閱 [AEM案頭應用](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html)。

## 資產批量導入

如果您有大規模遷移和偶爾的批量遷移，請使用「資產批量遷移」來上載您的內容。 使用此工具，您可以從受支援的資料儲存（如Azure或S3）上載批量內容。 有關詳細資訊，請參閱 [資產批量導入](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/manage/add-assets.html?lang=en#asset-bulk-ingestor)。

## 使用FrameMaker進行批量上載

Adobe FrameMaker帶有功能強AEM大的連接器，使您能夠輕鬆上載現有的DITA和其他FrameMaker文檔\(`.book` 和 `.fm`\)到AEM。 可以使用各種檔案上載功能，如上載單個檔案、上載包含或不包含依賴項的完整資料夾\（如內容引用、交叉引用和圖形\）。

有關在FrameMaker中使用批量上載功能的詳細資訊，請參閱一節 *建立CRX資料夾並上載檔案* 中。

## 上載內容時處理錯誤 {#id201MI0I04Y4}

如果上載一個或多個檔案失敗，上載過程結束時將顯示提示，其中列出了無法上載的檔案：

![](images/uuid-files-failed-to-upload_cs.png){width="650" align="center"}

有關各種檔案上載方案的詳細資訊，請參見 [上載DITA內容](authoring-file-management.md#)。

如果您使用案頭應用或AEM資產批量導入工具等工具，則對重複檔案執行的操作由伺服器中的設定AEM控制。 請與系統管理員聯繫以瞭解此配置。

**父主題：**[&#x200B;管理內容](authoring.md)
