---
title: 發行說明 |Adobe Experience Manager指南as a Cloud Service,2023年3月發佈
description: 《Adobe Experience Manager指南》3月發行as a Cloud Service
exl-id: b3fe7cc8-1654-467a-ab18-6e6912855ecc
source-git-commit: 8073716bccacbe8d6a158b44d5106b083e3a5dcd
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 2%

---

# 《Adobe Experience Manager指南》3月發行as a Cloud Service

## 升級到3月版本

升級您當前的Adobe Experience Manager指南as a Cloud Service(稍後稱為 *導AEM線as a Cloud Service*)，請執行以下步驟：
1. 檢出Cloud Services的Git代碼，並切換到在Cloud Services管道中配置的與要升級的環境對應的分支。
2. 更新 `<dox.version>` 物業 `/dox/dox.installer/pom.xml` Cloud ServicesGit代碼的檔案2023.3.242。
3. 提交更改並運行Cloud Services管道以升級到3月版的「指南」AEMas a Cloud Service。

## 為現有內容編製索引的步驟(僅當您在9月份發佈指南之前的版本AEMas a Cloud Service時)

執行以下步驟，為現有內容編製索引並使用新查找並替換映射級別的文本：

* 向伺服器運行POST請求（使用正確的身份驗證） —  `http://<server:port>/bin/guides/map-find/indexing`。
(可選：您可以傳遞映射的特定路徑以對其進行索引，預設情況下，所有映射都將被索引 ||示例： `https://<Server:port>/bin/guides/map-find/indexing?paths=<map_path_in_repository>`)

* API將返回jobId。 要檢查作業的狀態，您可以將具有作業ID的GET請求發送到同一端點 —  `http://<server:port>/bin/guides/map-find/indexing?jobId={jobId}`
(例如：http://&lt;
_localhost:8080_>/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678)

* 作業完成後，上述GET請求將成功響應，並在任何映射失敗時提及。 可以從伺服器日誌中確認成功索引的映射。

## 相容性矩陣

本節列出了《指南》as a Cloud Service2023年3月版本支援的軟體應AEM用程式的相容性清單。

### FrameMaker和FrameMaker發佈伺服器

| 作AEM為雲版本的指南 | FMPS | 幀製作器 |
| --- | --- | --- |
| 2023.03.0 | 不相容 | 2022年或更高 |
|  |  |  |


### 氧連接器

| 作AEM為雲版本的指南 | 氧連接器窗口 | 氧連接器Mac | 在氧氣窗口中編輯 | 在氧氣Mac編輯 |
| --- | --- | --- | --- | --- |
| 2023.03.0 | 2.9-uuid-2 | 2.9-uuid-2 | 2.3 | 2.3 |
|  |  |  |  |


## 新增功能和功能改善

《指南AEM》as a Cloud Service在2023年3月發佈時提供了增強功能和新功能：

### 在Web編輯器中開啟和播放視頻或音頻檔案

指AEM南現在提供了在Web編輯器中開啟和播放音頻或視頻檔案的功能。 可以更改音量或視頻的視圖。 在快捷菜單中，您還可以 **下載**&#x200B;更改 **回放速度**&#x200B;或 **圖片**。

<img src="assets/video-web-editor.png" alt="播放視頻" width="600">


## 已修正的問題

以下列出了在不同區域修復的錯誤：

* 下載PDF進程在Web編輯器中不能正常工作。 (11496)
* JSON輸出 |將具有屬性值的元資料映射為 `"value in spaces and double quotes"` 導致發佈錯誤。 (11438)
* 以YouTube格式插入音頻和視頻多媒體檔案失敗， **插入多媒體** 表徵圖 (11320)
* 當使用具有專用標題元素的模板建立映射時，會發生驗證錯誤。 (11212)
* 本地PDF |表頭中的腳注導致PDF輸出中相應頁腳中的粗體和居中對齊文本。 (10610)
>[!NOTE]
>
>要反映本機PDF更改，請刪除位於/content/dam/dita-templates的PDF資料夾，然後升級到最新的生成。 (10610)

### 已知問題，解決方法

Adobe已確定「指南」as a Cloud Service版2023AEM年3月的以下已知問題。

* 用戶無法保存或建立重複資產的版本。

**解決方法**:在對重複資產進行任何更改之前，請從資產UI中重新處理它。
