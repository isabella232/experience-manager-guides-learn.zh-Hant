---
title: 發行說明 | Adobe Experience Manager Guidesas a Cloud Service，2023年3月發行
description: Adobe Experience Manager Guidesas a Cloud Service三月版
source-git-commit: 99ca14a816630f5f0ec1dc72ba77994ffa71dff6
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 1%

---


# 2023年3月發行的Adobe Experience Manager Guidesas a Cloud Service

此發行說明涵蓋升級指示、相容性矩陣，以及2023年3月Adobe Experience Manager Guides版本中修正的問題(後稱為 *AEM指南as a Cloud Service*)。

如需新功能和增強功能的詳細資訊，請參閱 [AEM Guidesas a Cloud Service版2023年3月的新增功能](whats-new-2023.3.0.md).

## 升級至2023年3月版本

請執行以下步驟，升級您目前的AEM Guidesas a Cloud Service設定：
1. 檢視Cloud Services的Git程式碼，並切換到在Cloud Services管道中設定的分支，該分支與您要升級的環境相對應。
2. 更新 `<dox.version>` 中的屬性 `/dox/dox.installer/pom.xml` 將Cloud Services Git程式碼的檔案設為2023.3.242。
3. 提交變更並執行Cloud Services管道，以升級至2023年3月版的AEM Guidesas a Cloud Service。

## 索引現有內容的步驟(僅限使用9月之前版本的AEM Guidesas a Cloud Service)

執行以下步驟，為現有內容編制索引，並在地圖層級使用新的尋找和取代文字：

* 對伺服器執行POST要求（使用正確的驗證） - `http://<server:port>/bin/guides/map-find/indexing`.
(可選：您可以傳遞地圖的特定路徑來為其建立索引，預設情況下，所有地圖都會建立索引 ||範例： `https://<Server:port>/bin/guides/map-find/indexing?paths=<map_path_in_repository>`)

* 此API將傳回jobId。 若要檢查作業的狀態，您可以將具有作業ID的GET要求傳送至相同的端點 —  `http://<server:port>/bin/guides/map-find/indexing?jobId={jobId}`
(例如： http://&lt;
_localhost：8080_>/bin/guides/map-find/indexing？jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678)

* 工作完成後，上述GET要求將回應為成功，並提及是否有任何地圖失敗。 可以從伺服器記錄檔確認已成功建立索引的對應。

## 相容性矩陣

本節列出AEM Guides 2023年3月as a Cloud Service發行版本支援之軟體應用程式的相容性矩陣。

### FrameMaker和FrameMaker Publishing Server

| AEM Guides as a Cloud版本 | FMPS | FrameMaker |
| --- | --- | --- |
| 2023.03.0 | 不相容 | 2022或更高 |
|  |  |  |


### 氧氣聯結器

| AEM Guides as a Cloud版本 | 氧氣聯結器視窗 | 氧氣聯結器Mac | 在氧氣視窗中編輯 | 在氧氣Mac中編輯 |
| --- | --- | --- | --- | --- |
| 2023.03.0 | 2.9-uuid-2 | 2.9-uuid-2 | 2.3 | 2.3 |
|  |  |  |  |


