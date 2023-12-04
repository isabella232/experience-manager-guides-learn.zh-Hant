---
title: 版本注意事項 [!DNL AEM Guides]， 2022年3月發行
description: 三月版的 [!DNL Adobe Experience Manager Guides] as a Cloud Service
source-git-commit: 880cd344ceb65ea339be699ebcad41c0d62e168a
workflow-type: tm+mt
source-wordcount: '777'
ht-degree: 0%

---

# 三月版的 [!DNL Adobe Experience Manager Guides] as a Cloud Service

## 升級至3月發行

升級您目前的 [!DNL Adobe Experience Manager Guides] as a Cloud Service(稍後稱為 *[!DNL AEM Guides]as a Cloud Service*)進行設定，請執行以下步驟：
1. 檢視Cloud Service的Git程式碼，並切換到在Cloud Service管線中設定的分支，該分支與您要升級的環境相對應。
1. 更新 `<dox.version>` 中的屬性 `/dox/dox.installer/pom.xml` 將Cloud Service Git程式碼的檔案設為2022.3.123。
1. 提交變更並執行Cloud Service管道，以升級至3月版本的 [!DNL AEM Guides] as a Cloud Service。

## 相容性矩陣

本節列出所支援軟體應用程式的相容性矩陣。 [!DNL AEM Guides] 2022年3月版本as a Cloud Service。

### FrameMaker和FrameMaker Publishing Server

| FMPS | FrameMaker |
| --- | --- |
| 不相容 | 2020 Update 4及更新版本 |
| | |


### 氧氣聯結器

| [!DNL AEM Guides] 雲端發行版本 | 氧氣聯結器視窗 | 氧氣聯結器Mac |
| --- | --- | --- |
| 2022.3.0 | 2.4.0 | 2.4.0 |
|  |  |  |

*從2020.2開始的FMPS版本支援AEM中建立的基準和條件。

## 新功能和增強功能

### 建立基準線儀表板

[!DNL AEM Guides] as a Cloud Service的3月發行版本提供整合在網頁編輯器中的基準線功能。 您現在可以從網頁編輯器建立基準線，並使用它們來發佈或翻譯不同版本的主題。

注意：對於升級的系統，請更新最新的 **ui_config.json** 資料夾設定檔的。

使用此功能可建立基準線，其中包含特定日期和時間可用的特定主題版本。 此外，您獲得API支援，可使用為主題版本定義的標籤來建立或更新基準線。

![基線管理索引標籤](assets/baseline-manage.png)

您可以根據檔案名稱或檔案位置來搜尋檔案。 您也可以篩選要在基準線編輯視窗中顯示的主題，並根據特定欄排序。

![基線管理索引標籤](assets/baseline-filter.png)

已進一步改善基準線建立程式的效能。 建立基準線的程式不同步，因此您可以在建立基準線時繼續編輯網頁編輯器中的其他檔案。 如需詳細資訊，請參閱 *從Web編輯器建立和管理基準線* 使用手冊中的。

注意：依照預設，對映圖示板上的「基線」標籤是隱藏的。 您的管理員可以在地圖控制面板上啟用基線標籤。

### 改善網頁編輯器重新整理行為

「網頁編輯器」中的瀏覽器重新整理作業現在提供下列增強功能：

* 現在當您在網頁編輯器中編輯內容時，可以取得重新整理瀏覽器的支援。 如果您在開啟一或多個含有未儲存變更的檔案進行編輯時按下瀏覽器重新整理圖示，系統會提示您儲存檔案或取消重新整理動作。

* 即使重新整理瀏覽器，左側面板和右側面板的檢視仍會保留。

* 活動主題或DITA map會在內容編輯區域中重新開啟。

### 發佈增強功能

發佈程式已透過3月發行版本進一步改善 [!DNL AEM Guides] as a Cloud Service：

* 已對AEM網站輸出的中繼資料使用基準線。 您也可以將基準版本的特性當作中繼資料來處理。 如果未定義基準線，則會將最新版本的屬性當作中繼資料處理。

* 此 **檔案名稱** 和 **DITA-OT命令列引數** 已為HTML5、EPUB和自訂輸出預設集新增選項。 現在您可以指定要用來儲存輸出的檔案名稱。 您也可以指定在產生輸出時希望DITA-OT處理的其他引數。

## 已修正的問題

以下列出各種區域中修正的錯誤：

* 無法使用網頁編輯器的作者檢視，在書籤地圖中新增frontmatter、backmatter元素。 (7652)
* 移除主題並執行移動作業後，參照樹狀結構會中斷。 (8804)
* 上傳資產後檢視內容時收到例外狀況。 (3638)
* 當檔案的父資料夾在檔案名稱中有特殊字元時，在Oxyor中開啟(使用 **在Oxygon中編輯** 按鈕)。 (8918)
* 此 **在存放庫中找到** 選項在XML編輯器中找不到並反白顯示DITA map。 (8796)
* 在XML編輯器中將多個屬性新增到內容時，篩選不會顯示適當的結果。 (8795)
* 當使用者ID為數值時，在資料夾設定檔中將使用者新增為管理員時發生錯誤。 (8908)

## 已知問題

Adobe已在中發現下列已知問題 [!DNL AEM Guides] 3月版本as a Cloud Service。

* 移除直接參照上的標籤也會從間接參照中移除標籤。

* 若不手動重新整理基線面板，則無法反映更新的基線標題。

* 「版本記錄」面板中的版本預覽功能不會顯示所選主題的預覽。
