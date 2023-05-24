---
title: 版本注意事項 [!DNL AEM Guides]， 2022年3月發行
description: 三月版的 [!DNL Adobe Experience Manager Guides] as a Cloud Service
exl-id: 885edbb5-dfe4-4bdc-bb66-0df64addb094
source-git-commit: 67ba514616a0bf4449aeda035161d1caae0c3f50
workflow-type: tm+mt
source-wordcount: '768'
ht-degree: 2%

---

# 三月版的 [!DNL Adobe Experience Manager Guides] as a Cloud Service

## 升級至3月版

升級您目前的 [!DNL Adobe Experience Manager Guides] as a Cloud Service(稍後稱為 *[!DNL AEM Guides]as a Cloud Service*)進行設定：
1. 檢視Cloud Services的Git程式碼，並切換到在Cloud Services管道中設定的分支，該分支與您要升級的環境相對應。
1. 更新 `<dox.version>` 中的屬性 `/dox/dox.installer/pom.xml` 將您的Cloud Services Git程式碼檔案改成2022.3.123。
1. 提交變更並執行Cloud Services管道，以升級至3月版的 [!DNL AEM Guides] as a Cloud Service。

## 相容性矩陣

本節列出所支援軟體應用程式的相容性矩陣。 [!DNL AEM Guides] 2022年3月發行的as a Cloud Service版本。

### FrameMaker和FrameMaker Publishing Server

| FMPS | FrameMaker |
| --- | --- |
| 不相容 | 2020 Update 4及更高版本 |
|  |  |


### 氧氣聯結器

| [!DNL AEM Guides] 雲端版本 | 氧氣聯結器視窗 | 氧氣聯結器Mac |
| --- | --- | --- |
| 2022.3.0 | 2.4.0 | 2.4.0 |
|  |  |  |

*自2020.2開始的FMPS版本支援AEM中建立的基準和條件。

## 新增功能和功能改善

### 新增基準線儀表板

[!DNL AEM Guides] 三月版as a Cloud Service提供整合在網頁編輯器中的基準線功能。 您現在可以從網頁編輯器建立基準線，並使用它們來發佈或翻譯不同版本的主題。

注意：若為已升級的系統，請更新最新的 **ui_config.json** 資料夾設定檔的。

使用此功能可建立基準線，其中包含特定日期和時間可用的特定主題版本。 此外，您也獲得API支援，可使用為主題版本定義的標籤來建立或更新基準線。

![基線管理索引標籤](assets/baseline-manage.png)

您可以根據檔案名稱或檔案位置來搜尋檔案。 您也可以篩選要在基準線編輯視窗中顯示的主題，並根據特定欄排序。

![基線管理索引標籤](assets/baseline-filter.png)

基準線建立程式的效能已進一步改善。 建立基準線的程式不同步，因此您可以在建立基準線時繼續編輯網頁編輯器中的其他檔案。 如需詳細資訊，請參閱 *從Web編輯器建立和管理基準線* 使用手冊中的。

注意：預設會隱藏地圖圖示板上的「基準線」標籤。 您的管理員可以在地圖控制面板上啟用「基準線」標籤。

### 改善網頁編輯器重新整理行為

下列增強功能現在可用於網頁編輯器中的瀏覽器重新整理操作：

* 現在，當您在網頁編輯器中編輯內容時，您能夠獲得重新整理瀏覽器的支援。 如果您在開啟一或多個含有未儲存變更的檔案進行編輯時按下瀏覽器重新整理圖示，系統會提示您儲存檔案或取消重新整理動作。

* 即使重新整理瀏覽器，左側面板和右側面板的檢視也會保留。

* 活動主題或DITA map會在內容編輯區域中重新開啟。

### 發佈增強功能

發佈程式已透過3月發行版本進一步改善 [!DNL AEM Guides] as a Cloud Service：

* 已對AEM網站輸出的中繼資料使用基準線。 您也可以將基準版本的特性當作中繼資料來處理。 如果未定義基準線，則會將最新版本的屬性作為中繼資料處理。

* 此 **檔案名稱** 和 **DITA-OT命令列引數** 已新增HTML5、EPUB和自訂輸出預設集的選項。 現在，您可以指定要用來儲存輸出的檔案名稱。 您也可以指定在產生輸出時要DITA-OT處理的其他引數。

## 已修正的問題

修復了各種區域的錯誤如下所列：

* 無法使用網頁編輯器的作者檢視，將frontmatter、backmatter元素新增至Bookmap。 (7652)
* 移除主題並執行移動作業後，參照樹狀結構會中斷。 (8804)
* 上傳資產後檢視內容時收到例外狀況。 (3638)
* 當檔案名稱中的父資料夾含有特殊字元的檔案在Oxygon中開啟時(使用 **在氧氣中編輯** 按鈕)。 (8918)
* 此 **在存放庫中找到** 選項在XML編輯器中找不到並反白顯示DITA map。 (8796)
* 在XML編輯器中將多個屬性新增到內容時，篩選不會顯示適當的結果。 (8795)
* 當使用者ID為數值時，在資料夾設定檔中將使用者新增為管理員時發生錯誤。 (8908)

## 已知問題

Adobe已在中發現下列已知問題 [!DNL AEM Guides] 3月版本as a Cloud Service。

* 移除直接參照上的標籤也會從間接參照中移除標籤。

* 若未手動重新整理基線面板，則無法反映更新的基線標題。

* 「版本記錄」面板中的版本預覽功能不會顯示所選主題的預覽。
