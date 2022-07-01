---
title: 發行說明 [!DNL AEM Guides]2022年3月發佈
description: 3月 [!DNL Adobe Experience Manager Guides] as a Cloud Service
exl-id: 885edbb5-dfe4-4bdc-bb66-0df64addb094
source-git-commit: b5e64512956f0a7f33c2021bc431d69239f2a088
workflow-type: tm+mt
source-wordcount: '768'
ht-degree: 2%

---

# 3月 [!DNL Adobe Experience Manager Guides] as a Cloud Service

## 升級到3月版本

升級當前 [!DNL Adobe Experience Manager Guides] as a Cloud Service(後者稱為 *[!DNL AEM Guides]as a Cloud Service*)，請執行以下步驟：
1. 檢出Cloud Services的Git代碼，並切換到在Cloud Services管道中配置的與要升級的環境對應的分支。
2. 更新 `<dox.version>` 物業 `/dox/dox.installer/pom.xml` Cloud ServicesGit代碼的檔案2022.3.123。
3. 提交更改並運行Cloud Services管道以升級到 [!DNL AEM Guides] as a Cloud Service。

## 相容性矩陣

本節列出了支援的軟體應用程式的相容性清單 [!DNL AEM Guides] as a Cloud Service2022年3月發佈。

### FrameMaker和FrameMaker發佈伺服器

| FMPS | 幀製作器 |
| --- | --- |
| 不相容 | 2020年更新4及更高版本 |
|  |  |


### 氧連接器

| [!DNL AEM Guides] 雲版本 | 氧連接器窗口 | 氧連接器Mac |
| --- | --- | --- |
| 2022.3.0 | 2.4.0 | 2.4.0 |
|  |  |  |

*從2020.2開始的AEMFMPS版本支援中建立的基線和條件。

## 新增功能和功能改善

### 新建基線儀表板

[!DNL AEM Guides] as a Cloud Service3月版本提供了整合在Web編輯器中的基線功能。 現在，您可以從Web編輯器建立基線，並使用它們發佈或翻譯不同版本的主題。

注：對於升級的系統，請更新最新 **ui_config_json** 資料夾配置檔案。

使用此功能可建立基線，其中特定版本的主題在特定日期和時間可用。 此外，您還可以獲得API支援，以使用為主題版本定義的標籤建立或更新基線。

![基線管理頁籤](assets/baseline-manage.png)

您可以根據檔案名或檔案位置搜索檔案。 您還可以過濾要在基線編輯窗口中顯示的主題，並根據特定列對它們進行排序。

![基線管理頁籤](assets/baseline-filter.png)

基線建立過程的效能得到進一步改進。 建立基線的過程是非同步的，因此可以在建立基線時繼續編輯Web編輯器中的其他檔案。 有關詳細資訊，請參閱 *從Web編輯器建立和管理基線* 的上界。

注：預設情況下，映射操控板上的「基線」(Baseline)頁籤處於隱藏狀態。 管理員可以在映射儀表板上啟用「基線」頁籤。

### 改進的Web編輯器刷新行為

現在，瀏覽器刷新操作在Web編輯器中提供了以下增強功能：

* 現在，在Web編輯器中編輯內容時，您將獲得刷新瀏覽器的支援。 如果在開啟一個或多個具有未保存更改的檔案進行編輯時按一下瀏覽器刷新表徵圖，則系統會提示您保存檔案或取消刷新操作。

* 即使刷新瀏覽器，左面板和右面板的視圖也會保留。

* 活動主題或DITA映射在內容編輯區中重新開啟。

### 發佈增強功能

隨著3月份的出版，出版過程得到進一步改善 [!DNL AEM Guides] as a Cloud Service:

* 基線已經得到遵守，因為網站輸出AEM的元資料。 您還可以將基線版本的屬性作為元資料進行處理。 如果未定義基線，則最新版本的屬性將作為元資料處理。

* 的 **檔案名** 和 **DITA-OT命令行參數** 已為HTML5、EPUB和自定義輸出預設添加了選項。 現在，您可以指定要用來保存輸出的檔案名。 還可以指定在生成輸出時希望DITA-OT處理的附加參數。

## 已修正的問題

以下列出了在不同區域修復的錯誤：

* 無法使用Web編輯器的「作者」視圖在書本映射中添加前面、後面元素。 (7652)
* 刪除主題並執行移動操作後，引用樹會斷開。 (8804)
* 上載資產後查看內容時收到異常。 (3638)
* 在Ox(使用 **在氧氣中編輯** 按鈕)。 (8918)
* 的 **在儲存庫中查找** 選項未在XML編輯器中找到並突出顯示DITA映射。 (8796)
* 在XML編輯器中將多個屬性添加到內容時，篩選不會顯示相應的結果。 (8795)
* 當用戶ID為數字時，將用戶添加為資料夾配置檔案中的管理員時出錯。 (8908)

## 已知問題

Adobe已在 [!DNL AEM Guides] as a Cloud Service的3月份發佈。

* 刪除直接參照上的標籤也會從間接參照中刪除標籤。

* 如果不手動刷新基線面板，則無法反映更新的基線標題。

* 「版本歷史記錄」面板中的版本預覽功能不顯示所選主題的預覽。
