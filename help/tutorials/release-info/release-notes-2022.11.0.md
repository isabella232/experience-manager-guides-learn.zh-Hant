---
title: 發行說明 | Adobe Experience Manager Guidesas a Cloud Service，2022年11月發行
description: Adobe Experience Manager Guidesas a Cloud Service版11月版
exl-id: 9f329ec1-dd74-47cc-8567-3fadd962584a
source-git-commit: 67ba514616a0bf4449aeda035161d1caae0c3f50
workflow-type: tm+mt
source-wordcount: '1372'
ht-degree: 2%

---

# Adobe Experience Manager Guidesas a Cloud Service版11月版

## 升級至11月版

as a Cloud Service升級您目前的Adobe Experience Manager Guides (稍後稱為 *AEM指南as a Cloud Service*)進行設定：
1. 檢視Cloud Services的Git程式碼，並切換到在Cloud Services管道中設定的分支，該分支與您要升級的環境相對應。
1. 更新 `<dox.version>` 中的屬性 `/dox/dox.installer/pom.xml` 將您的Cloud Services Git程式碼檔案改成2022.11.198。
1. 提交變更並執行Cloud Services管道，以升級至11月版的AEM Guidesas a Cloud Service。

## 索引現有內容的步驟(僅限使用9月之前版本的AEM Guidesas a Cloud Service)

執行以下步驟來索引現有內容，並在地圖層級使用新的尋找和取代文字：

* 對伺服器執行POST要求（使用正確的驗證） - `http://<server:port>/bin/guides/map-find/indexing`.
(可選：您可以傳遞地圖的特定路徑來為其建立索引，預設情況下，所有地圖都會建立索引 ||範例： `https://<Server:port>/bin/guides/map-find/indexing?paths=<map_path_in_repository>`)

* 此API將傳回jobId。 若要檢查作業的狀態，您可以將具有作業ID的GET要求傳送至相同的端點 —  `http://<server:port>/bin/guides/map-find/indexing?jobId={jobId}`
(例如： http://&lt;
_localhost：8080_>/bin/guides/map-find/indexing？jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678)

* 工作完成後，上述GET要求將回應為成功，並提及是否有任何地圖失敗。 可以從伺服器記錄檔確認已成功建立索引的對應。

## 相容性矩陣

本節列出AEM Guides 2022年11月as a Cloud Service發行版本支援之軟體應用程式的相容性矩陣。

### FrameMaker和FrameMaker Publishing Server

| FMPS | FrameMaker |
| --- | --- |
| 不相容 | 2020 Update 4及更高版本 |
|  |  |

*自2020.2開始的FMPS版本支援AEM中建立的基準和條件。

### 氧氣聯結器

| AEM Guides as a Cloud版本 | 氧氣聯結器視窗 | 氧氣聯結器Mac | 在氧氣視窗中編輯 | 在氧氣Mac中編輯 |
| --- | --- | --- | --- | --- |
| 2022.11.0 | 2.7.13 | 2.7.13 | 2.3 | 2.3 |
|  |  |  |  |


## 新增功能和功能改善

AEM Guidesas a Cloud Service在11月版本中提供增強功能和新功能：


### 從存放庫面板刪除檔案

現在您可以輕鬆刪除檔案（一次刪除一個檔案），從 **選項** 儲存庫面板中選取檔案的功能表。
<img src="assets/repository-delete-file.png" alt="從存放庫刪除" width="500">

刪除檔案前會顯示確認提示。 如果檔案未從任何其他檔案參照，則會刪除檔案並顯示成功訊息。

如果選取的檔案已出庫，則無法刪除該檔案，並會顯示錯誤訊息。 如果選取的檔案新增至我的最愛集合或從任何其他檔案參照，AEM guides會檢查您的確認，並提供您強制刪除它的選項。 如果您刪除參照的主題，並且已經開啟包含要編輯的參照的檔案，它將顯示參照檔案的斷開連結。

**注意**：您也可以使用鍵盤的Delete鍵刪除選取的檔案。


### 清除檔案的所選版本

當您建立和維護內容時，可能會為存放庫中的DITA檔案建立許多版本。 AEM Guides可讓您從儲存庫清除舊版的DITA檔案，並釋放磁碟空間。

<img src="assets/preview-purge-report.png" alt="預覽清除報告" width="500">


AEM Guides不會刪除檔案的第一個版本，或是包含在基準線中的版本，或是已套用標籤的版本。 清除作業甚至不會刪除翻譯或稽核工作流程中包含的檔案。 您可以選擇要保留的版本數量，也可以決定刪除早於定義天數的檔案。

在開始永久刪除作業之前，您可以預覽報表以檢視要永久刪除的版本。 然後，您可以決定啟動或取消整個清除作業。

<img src="assets/download-purge-report.png" alt="PDownload清除報告" width="500">

永久刪除作業完成後，您可以檢查永久刪除報表，檢視已永久刪除的檔案。

### 管理全域和資料夾設定檔輸出預設集

AEM Guides提供您為全域和資料夾設定檔建立和管理輸出預設集的功能。 然後，您就可以輕鬆地使用這些輸出預設集來產生與該全域或資料夾設定檔相關的所有對應的輸出。

<img src="assets/add-global-output-preset.png" alt="新增全域設定檔" width="400">

**注意** 只有檔案夾層級的管理使用者才能建立全域和檔案夾設定檔預設集。

這些全域預設集會顯示在 **輸出** 標籤。 您可以使用它們來產生所有相關地圖的輸出。 您可以選取預設集作為預設PDF預設集，以產生PDF輸出。 您也可以 **編輯**， **重新命名**， **複製**，或 **刪除** 來自的現有輸出預設集 **選項** 功能表。

### 版本標籤欄已新增到翻譯儀表板

在翻譯控制面板中，您也可以看到「版本標籤」欄。 這會顯示來源檔案之所選版本的標籤。 這可以協助您選取所有具有特定標籤的檔案，並一次翻譯它們。

<img src="assets/send-translation.png" alt="傳送以進行翻譯" width="600">


### 原生PDF |含有顯示檔案版本之間差異之變更列的PDF

現在您可以使用變更列建立PDF，顯示兩個版本之間的內容差異。 您可以選擇將目前版本與先前版本的基準進行比較，或比較兩個選取的基準版本。

<img src="assets/pdf-change-version.png" alt="spdf-change-version" width="600">

PDF中會出現變更列，指出已修改、插入或刪除的內容。 您也可以選擇執行下列動作：
* 以綠色和底線顯示插入的內容
* 以紅色顯示刪除的內容，並標示刪除線

### 原生PDF |輸出路徑和PDF檔案名稱的變數支援

現在您也可以使用下列現成可用的變數來定義輸出路徑和PDF檔案。 您可以使用單一變數或變陣列合來定義這些選項：
* `${map_filename}`
* `${map_title}`
* `${preset_name}`
* `${language_code}`
* `${map_parentpath}` （僅適用於輸出路徑）
* `${path_after_langfolder}` （僅適用於輸出路徑）


### 原生PDF |產生DITA map的目錄並重新排序頁面配置

現在您也可以使用範本的進階PDF設定在DITA map中產生TOC。 您可以選擇啟用或停用各種頁面配置圖的顯示，也可以重新排序其位置。

## 已修正的問題

修復了各種區域的錯誤如下所列：

* 原生PDF | `conkeyref` 不會在產生的PDF輸出中解析。 (10564)
* 原生PDF |存取PDF輸出中的對應中繼資料時發生問題。 (10556)
* 原生PDF |內嵌樣式是用來產生標籤，而非類別名稱。  (10498)
* Web編輯器會間歇性地載入空白頁面。 (10678)
* 如果我們透過複製現有預設集來建立預設集，PDF發佈會失敗。 (10584)
* **檢視記錄** 預設集的PDF產生失敗時，按鈕無法運作。 (10576)
* 預覽中未顯示作為conref的para標籤內的備註。 (10559)
* 在清單專案結尾點選退格鍵會移除整個清單。 (10540)
* 使用原生PDF時，匯出巢狀 `<indexterm>` 未巢狀內嵌在索引中。 (10521)
* **自動縮排** 「來源檢視」中缺少工具列中的按鈕。 (10448)
* 在編輯器中編寫清單時，清單專案的第一個字元會遺失。 (10447)
* 如果在基準線編輯視窗中變更並儲存任何DITA資產版本，則會出現多個彈出視窗。 (10399)
* 按一下時發生應用程式錯誤 **編輯** 按鈕後，即可從「快速產生」面板選取所有輸出預設集。 (10388)
* 從Assets UI執行複製貼上動作時，不會保留DITA主題的自訂中繼資料。 (10367)
* 資產存在於使用中翻譯專案的整個語言資料夾的後處理遭到封鎖。 (10332)
* 資料夾設定檔管理員看不到XML編輯器中的範本索引標籤。 (10266)
* Web Editor 4.0升級後會發生導覽問題。 (10159)
* 預覽模式下不會顯示SVG檔案。 (10010)
* 如果編輯器的輸出索引標籤包含更多預設集，則預設集區段無法捲動，並且所有預設集都不會顯示。 (9787)
* **編輯** 和 **註釋** 影像的選項在欄檢視中無法正常運作。 (8758)
* 對等連結未解析並在產生的輸出中顯示為一般文字。 (7774)
