---
title: 發行說明 | Adobe Experience Manager Guides 4.3.1版的新增功能
description: 瞭解Adobe Experience Manager Guides 4.3.1版的新增和增強功能
source-git-commit: a865630527045574ef5a96622537e767eacd9fc2
workflow-type: tm+mt
source-wordcount: '1119'
ht-degree: 0%

---

# Adobe Experience Manager Guides 4.3.1版的新增功能（2023年10月）

本文介紹Adobe Experience Manager Guides 4.3.1版的新增和增強功能(以下稱為 *Experience Manager指南*)。

如需有關升級指示、相容性矩陣，以及此版本中修正問題的詳細資訊，請參閱 [發行說明](./release-notes-4.3.1.md).

## 連線至資料來源並插入主題

Experience Manager指南提供現成的聯結器，可協助您連線資料來源，讓Experience Manager指南成為真正的內容中樞。 這可讓您節省原本用於手動新增或複製資料的時間和精力。

除了現有的現成可用聯結器(例如JIRA和SQL (MySQL、PostgreSQL、SQL Server、SQLite)，您的管理員還可以為MariaDB、H2DB、AdobeCommerce和Elasticsearch資料庫設定聯結器。 它們也可以藉由擴充預設介面來新增其他聯結器。

您可以在「 」下方檢視已設定的聯結器 **資料來源** 網頁編輯器中的面板。

<img src="assets/data-sources.png" alt="面板中的資料來源清單" width="300">

*檢視連線的資料來源。*

您現在也可以從連線的資料來源建立主題。 主題可以包含各種格式的資料，例如表格、清單和段落。 它也可讓您為所有主題建立DITA map。 從資料來源提取時，您可以將中繼資料與主題建立關聯。

如需詳細資訊，請檢視 [使用來自您的資料來源的資料](../user-guide/web-editor-content-snippet.md).

## 從使用者介面設定資料來源聯結器

Experience Manager指南現在也提供 **資料來源** 可協助您為資料來源設定現成可用聯結器的工具。 您可以輕鬆建立JIRA、SQL (MySQL、PostgreSQL、Microsoft SQL Server、SQLite、MariaDB、H2DB)、AdobeCommerce和Elasticsearch資料庫的聯結器。

您也可以輕鬆編輯、重新連線、複製或刪除資料來源聯結器。 進一步瞭解如何 [從使用者介面輕鬆設定資料來源聯結器](../install-guide/conf-data-source-connector-tools.md).

![「資料來源」面板中列出的資料來源聯結器](assets/data-sources-create-window.png){width="550" align="left"}

*從資料來源面板建立和檢視資料來源聯結器。*

## 檢視主題產生器的記錄

您現在也可以檢視內容產生記錄檔。 此記錄檔可協助您檢查警告、錯誤和例外。  進一步瞭解 [主題產生器的選項](../user-guide/web-editor-content-snippet.md#options-for-a-topic-generator) 協助您輕鬆產生和管理主題產生器。

## 支援資料來源範本中的Velocity工具

您現在可以在「Experience Manager參考線」範本中使用Velocity工具。 這些工具可協助您將各種功能套用至從資料來源擷取的資料。 建立內容片段或主題時，您可以使用範本。 此功能可協助您節省時間和精力，以手動方式將相同的函式套用至每個資料集。  這樣還可以確保獲得準確的結果。
例如，您可以使用$mathTool來執行數學函式。
進一步瞭解如何 [在資料來源範本中使用Velocity工具](../user-guide/web-editor-content-snippet.md#use-velocity-tools).


## 原生PDF增強功能

下列原生PDF增強功能已在2023年10月版本中完成：

### 重設版面第一頁的頁碼

在原生PDF輸出中，您可以重新啟動頁碼並指定開始編號的編號。 現在，您也只能對第一次出現的截面開始編號。
進一步瞭解如何 [使用頁面配置的頁面屬性](../native-pdf/design-page-layout.md#page-props-page-layout).


### 在目錄中檢視沒有自動編號的章節

Experience Manager指南在目錄(TOC)中顯示章節編號以及章節名稱。 現在您可以選擇只發佈章節名稱，而不發佈章節編號。 檢視如何設定的詳細資訊 [範本的進階PDF設定](../native-pdf/components-pdf-template.md#advanced-pdf-settings).

## 從網頁編輯器下載地圖

現在，您不僅可以在網頁編輯器的地圖檢視中編輯地圖，也可以下載地圖。 您可以選擇使用特定基準下載地圖。 您也可以選擇將階層平面化，並將所有檔案和資料夾儲存在單一資料夾中。

如需詳細資訊，請參閱 **地圖檢視** 內的功能說明 [左側面板](../user-guide/web-editor-features.md#id2051EA0M0HS) 區段。

![存放庫檢視中檔案的選項功能表](assets/options-menu-repo-view-file-level-2310.png){width="550" align="left"}

*在存放庫檢視中選取檔案，然後選擇選項以在檔案上執行動作。*


## 支援單一分項清單定義中的多個主旨定義

您現在可以在一個對應中定義一或多個主旨定義，並在另一個對應中定義列舉定義，然後新增對應參照。 主旨 — 列舉參照是在相同對應或參照的對應中進行解析。

您現在也可以定義條件，並將其套用至主題中的某些特定元素。  條件僅對這些特定元素可見，而不會對所有其他元素可見。

如需處理主旨定義與分項清單之階層定義的詳細資訊，請檢視 [左側面板](../user-guide/web-editor-features.md#id2051EA0M0HS) 區段。




## 內容功能表的增強預覽體驗

使用快顯功能表快速預覽檔案（.dita、.xml、音訊、視訊或影像），而不需開啟它。 您現在可以調整預覽窗格的大小，如果內容包含任何參考連結，您可以選取它，以在新標籤中開啟它。

![預覽窗格 ](assets/quick-preview_cs.png){width="800" align="left"}

*在窗格中預覽檔案。*

如需內容功能表的詳細資訊，請參閱 **檔案的選項** 中的功能說明 [左側面板](../user-guide/web-editor-features.md#id2051EA0M0HS) 區段。

## 在氧氣聯結器外掛程式中編輯檔案

Experience Manager指南現在可讓您在網頁編輯器中選取檔案，然後選擇在氧氣聯結器外掛程式中編輯檔案。 這個選項並未啟用為現成支援的一部分。

如需詳細資訊，請參閱 **檔案的選項** 內的功能說明 [左側面板](../user-guide/web-editor-features.md#id2051EA0M0HS) 區段。

## 在「目的地路徑」、「網站名稱」或「檔案名稱」選項中，使用目前日期和時間的變數

在AEM網站或PDF中產生輸出時，您可以使用變數來設定 **目的地路徑**， **網站名稱**，或 **檔案名稱** 選項。 您現在也可以使用 `${system_date}`和 `${system_time}` 變數。 這些變數可協助您將目前日期和時間附加至這些選項。

瞭解如何 [使用變數來設定目的地路徑、網站名稱或檔案名稱選項](../user-guide/generate-output-use-variables.md).


## 在網頁編輯器中移動游標的鍵盤快速鍵

Experience Manager參考線現在也可讓您使用鍵盤快速鍵在網頁編輯器中移動游標。 您可以使用鍵盤快速鍵，快速向左或向右移動一個單字。 您也可以在鍵盤快速鍵的協助下移至行的開頭或結尾。

進一步瞭解 [網頁編輯器中的鍵盤快速鍵](../user-guide/web-editor-keyboard-shortcuts.md).