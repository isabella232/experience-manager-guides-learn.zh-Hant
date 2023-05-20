---
title: 發行說明 |Adobe Experience Manager指南as a Cloud Service,2023年4月發佈
description: 最新版《Adobe Experience Manager指南》as a Cloud Service
exl-id: 3b09f0b3-cfa4-422d-91b7-733ab1c1896c
source-git-commit: cf612da41f79b0bf9da4c4d7454a0e3c86af7a4c
workflow-type: tm+mt
source-wordcount: '852'
ht-degree: 2%

---

# 《Adobe Experience Manager指南》4月發行as a Cloud Service

## 升級到最新版本

升級您當前的Adobe Experience Manager指南as a Cloud Service(稍後稱為 *導AEM線as a Cloud Service*)，請執行以下步驟：

1. 檢出Cloud Services的Git代碼，並切換到在Cloud Services管道中配置的與要升級的環境對應的分支。
2. 更新 `<dox.version>` 物業 `/dox/dox.installer/pom.xml` Cloud ServicesGit代碼的檔案2023.4.249。
3. 提交更改並運行Cloud Services管道以升級到最新版本的「指南」AEMas a Cloud Service。

## 為現有內容編製索引的步驟(僅當您在9月份發佈指南之前的版本AEMas a Cloud Service時)

執行以下步驟，為現有內容編製索引並使用新查找並替換映射級別的文本：

* 向伺服器運行POST請求（使用正確的身份驗證） —  `http://<server:port>/bin/guides/map-find/indexing`。
(可選：您可以傳遞映射的特定路徑以對其進行索引，預設情況下，所有映射都將被索引 ||示例： `https://<Server:port>/bin/guides/map-find/indexing?paths=<map_path_in_repository>`)

* API將返回jobId。 要檢查作業的狀態，您可以將具有作業ID的GET請求發送到同一端點 —  `http://<server:port>/bin/guides/map-find/indexing?jobId={jobId}`
(例如：http://&lt;
_localhost:8080_>/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678)

* 作業完成後，上述GET請求將成功響應，並在任何映射失敗時提及。 可以從伺服器日誌中確認成功索引的映射。

## 相容性矩陣

本節列出了2023年4月as a Cloud Service版本指南支援的軟AEM件應用程式的相容性清單。

### FrameMaker和FrameMaker發佈伺服器

| 作AEM為雲版本的指南 | FMPS | 幀製作器 |
| --- | --- | --- |
| 2023.04.0 | 不相容 | 2022年或更高 |
|  |  |  |


### 氧連接器

| 作AEM為雲版本的指南 | 氧連接器窗口 | 氧連接器Mac | 在氧氣窗口中編輯 | 在氧氣Mac編輯 |
| --- | --- | --- | --- | --- |
| 2023.04.0 | 2.9-uuid-2 | 2.9-uuid-2 | 2.3 | 2.3 |
|  |  |  |  |


## 新增功能和功能改善

指AEM南as a Cloud Service在最新版本中提供了增強功能和新功能：

### PDF發佈中的高級元資料支援

指AEM南現在為映射到PDF輸出中元資料的元資料提供高級支援。 元資料選項包括關於文檔及其內容的資訊，例如作者的名稱、文檔標題、關鍵字、版權資訊以及其他資料欄位。

<img src="assets/pdf-metadata.png" alt=" 本地pdf元資料">

可以導入文XMP件，「AEM參考線」可以從檔案中選取資訊。 您還可以選擇使用下拉菜單提供元資料名稱和值。 也可以通過在名稱欄位中直接鍵入來添加自定義元資料。


### 「增強的大綱視圖」面板

參考AEM線提供了一個改進的「大綱視圖」面板，在該面板中可以獲取文檔中使用的元素的分層視圖。

<img src="assets/select-element-content-outline-view_cs.png" alt=" 本地pdf元資料">

「大綱視圖」提供了以下增強：

* 「視圖選項」下拉清單顯示在「大綱視圖」面板的頂部。 如果元素具有ID、屬性和文本，則可以從下拉清單中選擇它們以與元素一起顯示它們。 可在「大綱視圖」面板中顯示的屬性由管理員在「大綱視圖」中配置的「顯示屬性」設定確定 **編輯器設定**。

* 使用搜索功能，可以按元素的名稱、id、文本或屬性值搜索元素。


### 基於微服務的指南AEMas a Cloud Service發佈

指AEM南as a Cloud Service提供了與基於微服務的發佈同時運行大型發佈工作負載的功能，並利用業界領先的Adobe I/O Runtime無伺服器平台。

現在，在4月份的發行版中，您可以同時運行多個發佈請求，並使用基於微服務的本地PDF發佈非常高效地生成批量PDF輸出。
有關詳細資訊，請參閱 [為指南as a Cloud Service配置新的基於微AEM服務的發佈](../knowledge-base/publishing/configure-microservices.md)。


## 已修正的問題

以下列出了在不同區域修復的錯誤：

* 本地PDF |發佈包含帶括弧()的輸出類的內容將導致發佈凍結。 (11596)
* 移動（拖放）以取代現有清單項，並在其上執行跟蹤更改時出現問題。 (11570)
* 將「跟蹤更改」作為新清單項移動（拖放）時出現問題。 (11569)
* 在「跟蹤更改」中，縮進或縮進清單項不能按預期工作。 (11568)
* 在開啟「跟蹤更改」的行上添加內容，然後關閉「跟蹤更改」實際上不會關閉它。 (11567)
* 拖放清單項時遇到困難，文本將移動到清單項的位置。 (11566)
* 已完成審閱未在只讀模式下開啟。 (11387)
* 站點搜AEM索中出現問題（在2-3級節點之外無效）。 (11352)
* 在以綠色（「跟蹤更改」）顯示的元素中創作時，新內容將顯示為跟蹤更改，即使已禁用跟蹤更改。 (7021)

### 已知問題，解決方法

Adobe已確定「指南」as a Cloud Service於2023AEM年4月版本的以下已知問題。

* 本地PDF |在顯式開啟輸出預設之前，不會填充舊元資料。
