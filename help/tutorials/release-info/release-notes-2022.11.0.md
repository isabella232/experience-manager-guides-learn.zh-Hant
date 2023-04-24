---
title: 發行說明 | Adobe Experience Manager指南as a Cloud Service,2022年11月發行版本
description: 11月版Adobe Experience Manager指南as a Cloud Service
exl-id: 9f329ec1-dd74-47cc-8567-3fadd962584a
source-git-commit: 67ba514616a0bf4449aeda035161d1caae0c3f50
workflow-type: tm+mt
source-wordcount: '1372'
ht-degree: 2%

---

# 11月版Adobe Experience Manager指南as a Cloud Service

## 升級至11月版

升級您目前的Adobe Experience Manager指南as a Cloud Service(稍後稱為 *AEM指南as a Cloud Service*)，請執行下列步驟：
1. 查看Cloud Services的Git程式碼，並切換至Cloud Services管道中所設定的分支，該管道與您要升級的環境對應。
1. 更新 `<dox.version>` 屬性 `/dox/dox.installer/pom.xml` 檔案中的Git程式碼。2022.11.198
1. 提交變更並執行Cloud Services管道，以升級至11月版的AEM指南as a Cloud Service。

## 為現有內容建立索引的步驟(僅限使用9月版AEM指南之前的版本時as a Cloud Service)

執行以下步驟來建立現有內容的索引，並在映射級別使用新的查找和替代文字：

* 對伺服器執行POST請求（使用正確的驗證） —  `http://<server:port>/bin/guides/map-find/indexing`.
(可選：您可以傳遞映射的特定路徑來為其建立索引，預設情況下，所有映射都將編製索引 ||範例： `https://<Server:port>/bin/guides/map-find/indexing?paths=<map_path_in_repository>`)

* API會傳回jobId。 要檢查作業的狀態，可以向相同的終點發送具有作業ID的GET請求 —  `http://<server:port>/bin/guides/map-find/indexing?jobId={jobId}`
(例如：http://&lt;
_localhost:8080_>/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678)

* 作業完成後，上述GET要求會以成功回應，並在地圖失敗時提及。 可以從伺服器日誌中確認已成功索引的映射。

## 相容性矩陣

本節列出AEM指南as a Cloud Service於2022年11月發行版本所支援軟體應用程式的相容性矩陣。

### FrameMaker和FrameMaker Publishing Server

| FMPS | FrameMaker |
| --- | --- |
| 不相容 | 2020更新4及更新版本 |
|  |  |

*從2020.2開始的FMPS版本支援在AEM中建立的基線和條件。

### 氧連接器

| AEM雲端版本指南 | 氧連接器窗口 | 氧連接器Mac | 在氧氣窗口中編輯 | 在Oxion Mac中編輯 |
| --- | --- | --- | --- | --- |
| 2022.11.0 | 2.7.13 | 2.7.13 | 2.3 | 2.3 |
|  |  |  |  |


## 新增功能和功能改善

AEM指南as a Cloud Service提供11月版本的增強功能和新功能：


### 從儲存庫面板刪除檔案

現在，您可以輕鬆從 **選項** 「儲存庫」面板中選定檔案的菜單。
<img src="assets/repository-delete-file.png" alt="從儲存庫刪除" width="500">

刪除檔案之前，會顯示確認提示。 如果未從任何其他檔案引用該檔案，則會刪除該檔案，並顯示成功消息。

如果選定的檔案已簽出，則無法將其刪除，並顯示錯誤消息。 如果選定的檔案已添加到收藏夾集合或從任何其他檔案引用，AEM參考線將檢查您的確認，並為您提供強制刪除該檔案的選項。 如果刪除引用的主題，並且已開啟包含要編輯的引用的檔案，則它將顯示引用檔案的斷開連結。

**附註**:您也可以使用鍵盤的Delete鍵來刪除選取的檔案。


### 清除選定版本的檔案

當您建立和維護內容時，可能會為儲存庫中的DITA檔案建立許多版本。 AEM指南可讓您從存放庫清除舊版DITA檔案並釋放磁碟空間。

<img src="assets/preview-purge-report.png" alt="預覽清除報表" width="500">


AEM參考線不會刪除檔案的第一個版本、基線中包含的版本或已套用標籤的版本。 清除操作甚至不會刪除翻譯或審核工作流中包含的檔案。 您可以選擇要保留的版本數，並決定刪除早於定義天數的檔案。

在開始清除操作之前，您可以預覽報表以查看要清除的版本。 然後，您可以決定啟動或取消清除操作。

<img src="assets/download-purge-report.png" alt="PDownload清除報表" width="500">

完成清除操作後，您可以檢查清除報告以查看已清除的檔案。

### 管理全局和資料夾配置檔案輸出預設集

AEM指南提供您建立和管理全域和資料夾設定檔輸出預設集的功能。 然後，您可以輕鬆使用這些輸出預設集為與該全局或資料夾配置檔案相關的所有映射生成輸出。

<img src="assets/add-global-output-preset.png" alt="新增全域設定檔" width="400">

**附註** 只有資料夾級別管理用戶才能建立全局和資料夾配置檔案預設集。

這些全域預設集會顯示在 **輸出** 標籤。 您可以使用它們為所有相關映射生成輸出。 您可以選取預設PDF預設集，以產生PDF輸出。 您也可以 **編輯**, **重新命名**, **複製**，或 **刪除** 來自 **選項** 功能表。

### 「版本標籤」欄已添加到翻譯控制面板

在翻譯控制面板中，您也可以看到「版本標籤」欄。 這將顯示所選源檔案版本的標籤。 這可協助您選取所有具有特定標籤的檔案，並一次轉譯。

<img src="assets/send-translation.png" alt="傳送以翻譯" width="600">


### 原生PDF |帶更改欄的PDF顯示文檔版本之間的差異

現在，您可以使用變更列，建立顯示兩個版本之間內容差異的PDF。 您可以選擇將當前版本與以前版本的基線進行比較，或在兩個選定的基線版本之間進行比較。

<img src="assets/pdf-change-version.png" alt="spdf-change-version" width="600">

PDF中會出現變更列，指出已修改、插入或刪除的內容。 您也可以選擇執行下列動作：
* 以綠色顯示插入的內容並加下下划線
* 以紅色顯示已刪除的內容，並加上刪除線

### 原生PDF |支援輸出路徑和PDF檔案名

現在，您也可以使用下列現成變數來定義輸出路徑和PDF檔案。 您可以使用單一或變陣列合來定義下列選項：
* `${map_filename}`
* `${map_title}`
* `${preset_name}`
* `${language_code}`
* `${map_parentpath}` （僅限輸出路徑）
* `${path_after_langfolder}` （僅限輸出路徑）


### 原生PDF |為DITA映射生成目錄並重新排序頁面佈局

現在，您也可以使用範本的進階PDF設定，在DITA映射中產生TOC。 您可以選擇啟用或禁用各種頁面佈局的顯示，並重新排序其位置。

## 已修正的問題

以下列出各個區域中修正的錯誤：

* 原生PDF | `conkeyref` 不會在產生的PDF輸出中解析。 (10564)
* 原生PDF |存取PDF輸出中對應的中繼資料時發生問題。 (10556)
* 原生PDF |內嵌樣式用於產生標籤，而非類別名稱。  (10498)
* 網頁編輯器會間歇性載入空白頁面。 (10678)
* 如果我們透過複製現有預設集來建立預設集，PDF發佈就會失敗。 (10584)
* **檢視記錄** 當預設集的PDF產生失敗時，按鈕無法運作。 (10576)
* 段落標籤內的備注（即conref）不會顯示在預覽中。 (10559)
* 點擊清單項目結尾的空格會移除整個清單。 (10540)
* 使用原生PDF時，會匯出巢狀 `<indexterm>` 不嵌套在索引中。 (10521)
* **自動縮進** 「源視圖」中缺少工具欄中的按鈕。 (10448)
* 在編輯器中編寫清單時，清單項的第一個字元會遺失。 (10447)
* 如果任何DITA資產版本已變更並儲存在基線編輯視窗中，則會顯示多個快顯視窗。 (10399)
* 按一下時發生應用程式錯誤 **編輯** 按鈕。 (10388)
* 從資產UI執行複製貼上動作時，不會保留DITA主題的自訂中繼資料。 (10367)
* 對於資產存在於作用中翻譯專案的整個語言資料夾，會封鎖後期處理。 (10332)
* 資料夾配置檔案管理員看不到XML編輯器中的模板頁簽。 (10266)
* 4.0升級後，Web編輯器中發生導覽問題。 (10159)
* SVG檔案未在預覽模式中顯示。 (10010)
* 如果編輯器的「輸出」頁簽包含更多預設集，則無法滾動預設集節，並且不顯示所有預設集。 (9787)
* **編輯** 和 **注釋** 在欄檢視中，影像的選項無法正常運作。 (8758)
* 對等連結未解析，在生成的輸出中顯示為普通文本。 (7774)
