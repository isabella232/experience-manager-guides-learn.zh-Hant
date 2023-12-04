---
title: 發行說明 | Adobe Experience Manager Guidesas a Cloud Service，2023年4月發行
description: 2023年4月發行的Adobe Experience Manager Guidesas a Cloud Service
source-git-commit: 880cd344ceb65ea339be699ebcad41c0d62e168a
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# 2023年4月發行的Adobe Experience Manager Guidesas a Cloud Service新增功能

本文介紹2023年4月版Adobe Experience Manager Guides中的新功能和增強功能(以下稱為 *AEM Guidesas a Cloud Service*)。

如需有關升級指示、相容性矩陣，以及此版本中修正問題的詳細資訊，請參閱 [發行說明](release-notes-2023.4.0.md) 文章。

## PDF發佈中的進階中繼資料支援

AEM Guides現在為中繼資料提供進階支援，這些中繼資料已對應至PDF輸出中的中繼資料。 中繼資料選項包括有關檔案及其內容的資訊，例如作者姓名、檔案標題、關鍵字、版權資訊和其他資料欄位。

<img src="assets/pdf-metadata.png" alt=" 原生pdf中繼資料">

您可以匯入XMP檔案，AEM Guides可以從檔案中挑選資訊。 您也可以選擇使用下拉式清單提供中繼資料名稱和值。 您也可以直接在名稱欄位中輸入內容，以新增自訂中繼資料。


## 增強型大綱檢視面板

AEM Guides提供改良的「大綱檢視」面板，讓您取得檔案中使用的元素階層檢視。

<img src="assets/select-element-content-outline-view_cs.png" alt=" 原生pdf中繼資料">

「大綱檢視」提供下列增強功能：

* 「檢視選項」下拉式清單會顯示在「大綱檢視」面板上方。 如果元素有ID、屬性和文字，您可以從下拉式清單中選取它們，以便與元素一起顯示。 可在「大綱檢視」面板中顯示的屬性是由管理員在 **編輯器設定**.

* 您可以使用搜尋功能，依名稱、ID、文字或屬性值來搜尋元素。


## AEM Guides的微服務型發佈as a Cloud Service

AEM Guidesas a Cloud Service提供以微服務為基礎的發佈同時執行大型發佈工作負荷的功能，並利用業界領先的Adobe I/O Runtime無伺服器平台。

現在在4月版本中，您可以使用微服務型原生PDF發佈，同時執行多個發佈要求，並非常有效地產生大量PDF輸出。
如需詳細資訊，請參閱 [為AEM Guidesas a Cloud Service設定新的微服務型發佈](../knowledge-base/publishing/configure-microservices.md).
