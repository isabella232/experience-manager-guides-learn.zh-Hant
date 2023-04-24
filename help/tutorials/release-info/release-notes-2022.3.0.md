---
title: 的發行說明 [!DNL AEM Guides]、2022年3月發行版本
description: 3月發行 [!DNL Adobe Experience Manager Guides] as a Cloud Service
exl-id: 885edbb5-dfe4-4bdc-bb66-0df64addb094
source-git-commit: 67ba514616a0bf4449aeda035161d1caae0c3f50
workflow-type: tm+mt
source-wordcount: '768'
ht-degree: 2%

---

# 3月發行 [!DNL Adobe Experience Manager Guides] as a Cloud Service

## 升級至3月版

升級您目前的 [!DNL Adobe Experience Manager Guides] as a Cloud Service(稍後稱為 *[!DNL AEM Guides]as a Cloud Service*)，請執行下列步驟：
1. 查看Cloud Services的Git程式碼，並切換至Cloud Services管道中所設定的分支，該管道與您要升級的環境對應。
1. 更新 `<dox.version>` 屬性 `/dox/dox.installer/pom.xml` 檔案的Git程式碼。
1. 提交變更並執行Cloud Services管道以升級至的3月版 [!DNL AEM Guides] as a Cloud Service。

## 相容性矩陣

本節列出了支援的軟體應用程式的相容性矩陣 [!DNL AEM Guides] as a Cloud Service於2022年3月發行。

### FrameMaker和FrameMaker Publishing Server

| FMPS | FrameMaker |
| --- | --- |
| 不相容 | 2020更新4及更新版本 |
|  |  |


### 氧連接器

| [!DNL AEM Guides] 雲端版本 | 氧連接器窗口 | 氧連接器Mac |
| --- | --- | --- |
| 2022.3.0 | 2.4.0 | 2.4.0 |
|  |  |  |

*從2020.2開始的FMPS版本支援在AEM中建立的基線和條件。

## 新增功能和功能改善

### 新基線控制面板

[!DNL AEM Guides] as a Cloud Service於3月版本提供整合在Web編輯器中的基線功能。 您現在可以從Web編輯器建立基線，並使用它們來發佈或翻譯不同版本的主題。

注意：對於升級的系統，請更新 **ui_config.json** （適用於資料夾配置檔案）。

使用此功能建立基線，其中包含特定日期和時間上可用主題的特定版本。 此外，您還能取得API支援，以使用針對主題版本定義的標籤來建立或更新基線。

![基線管理標籤](assets/baseline-manage.png)

您可以根據檔案名或檔案位置搜索檔案。 您也可以篩選要在基線編輯視窗中顯示的主題，並根據特定欄來排序。

![基線管理標籤](assets/baseline-filter.png)

基線建立程式的效能已進一步改善。 建立基線的過程是非同步的，因此，在建立基線時，您可以繼續編輯Web編輯器中的其他檔案。 如需詳細資訊，請參閱 *從Web編輯器建立和管理基線* 中。

注意：預設情況下，會隱藏映射控制面板上的基線頁簽。 您的管理員可以在地圖控制面板上啟用基線索引標籤。

### 改善網頁編輯器重新整理行為

下列增強功能現在可在網頁編輯器中搭配瀏覽器重新整理作業使用：

* 現在，您獲得支援，可在網頁編輯器中編輯內容時重新整理瀏覽器。 如果您在開啟一或多個具有未儲存變更的檔案進行編輯時點擊瀏覽器重新整理圖示，系統會提示您儲存檔案或取消重新整理動作。

* 即使重新整理瀏覽器，也會保留左面板和右面板的檢視。

* 活動主題或DITA映射在內容編輯區中重新開啟。

### 發佈增強功能

3月發行版本後，發佈程式已進一步改善 [!DNL AEM Guides] as a Cloud Service:

* AEM網站輸出的中繼資料已接受基線。 您也可以以中繼資料的形式處理基線版本的屬性。 如果未定義基線，則最新版本的屬性會以中繼資料的形式處理。

* 此 **檔案名** 和 **DITA-OT命令行參數** 已針對「HTML5」、「EPUB」和「自訂輸出預設集」新增選項。 現在，您可以指定要用來儲存輸出的檔案名稱。 您也可以指定在產生輸出時要DITA-OT處理的其他引數。

## 已修正的問題

以下列出各個區域中修正的錯誤：

* 無法使用網頁編輯器的「作者」檢視，在書籤地圖中新增Frontmatter、Backmatter元素。 (7652)
* 移除主題和執行移動操作後，引用樹中斷。 (8804)
* 上傳資產後檢視內容時發生例外狀況。 (3638)
* 當父資料夾在檔案名中具有特殊字元的檔案在Oxin中開啟時(使用 **在氧氣中編輯** 按鈕)。 (8918)
* 此 **在儲存庫中找到** 選項不會在XML編輯器中找到並反白顯示DITA映射。 (8796)
* 在XML編輯器中將多個屬性新增至內容時，篩選不會顯示適當的結果。 (8795)
* 當使用者ID為數值時，在資料夾設定檔中將使用者新增為管理員時發生錯誤。 (8908)

## 已知問題

Adobe已在 [!DNL AEM Guides] as a Cloud Service3月發行。

* 移除直接參照上的標籤也會移除間接參照中的標籤。

* 若未手動重新整理基線面板，則無法反映更新的基線標題。

* 「版本歷史記錄」面板中的版本預覽功能不會顯示所選主題的預覽。
