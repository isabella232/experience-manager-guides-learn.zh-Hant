---
title: 發行說明 | 2023年11月發行的Adobe Experience Manager Guides中的升級指示和修正問題
description: 瞭解錯誤修正以及如何升級至2023年11月版的Adobe Experience Manager Guidesas a Cloud Service
source-git-commit: 880cd344ceb65ea339be699ebcad41c0d62e168a
workflow-type: tm+mt
source-wordcount: '1673'
ht-degree: 0%

---

# 2023年11月版Adobe Experience Manager Guidesas a Cloud Service

本發行說明涵蓋升級指示、相容性矩陣，以及2023年11月版Adobe Experience Manager Guidesas a Cloud Service修正的問題(後稱為 *Experience Manager指南as a Cloud Service*)。

如需新功能和增強功能的詳細資訊，請檢視 [2023年11月版Experience Manager指南as a Cloud Service的新增功能](whats-new-2023.11.0.md).

## 升級至2023年11月發行版本

執行下列步驟，升級您目前的Experience Manager指南as a Cloud Service設定：

1. 檢視Cloud Service的Git程式碼，並切換到在Cloud Service管線中設定的分支，該分支與您要升級的環境相對應。
2. 更新 `<dox.version>` 中的屬性 `/dox/dox.installer/pom.xml` 將Cloud Service Git程式碼的檔案設為2023.11.0.406。
3. 提交變更並執行Cloud Service管道，以升級至2023年11月版本的Experience Manager指南as a Cloud Service。

## 透過servlet啟用指令碼觸發的步驟

(僅限使用2023年6月as a Cloud Service發行Experience Manager指南之前的版本時)

完成安裝後，您可以選擇點選觸發程式以開始翻譯工作：

POST：

```
http://localhost:4503/bin/guides/script/start?jobType=translation-map-upgrade
```

回應：

```
{
"msg": "Job is successfully submitted and lock node is created for future reference",
"lockNodePath": "/var/dxml/executor-locks/translation-map-upgrade/1683190032886",
"status": "SCHEDULED"
}
```

在上一個回應JSON中，索引鍵 `lockNodePath` 儲存指向存放庫中建立的、指向已提交作業的節點的路徑。 它將在作業完成後自動刪除，然後您可以參照此節點來瞭解作業的狀態。

請等到此工作完成後，再繼續後續步驟。

>[!NOTE]
>
> 您應該檢查節點是否仍然存在，以及工作的狀態。

```
GET
http://<aem_domain>/var/dxml/executor-locks/translation-map-upgrade/1683190032886.json
```

## 後續處理現有內容以使用中斷連結報告的步驟

(僅限使用2023年6月as a Cloud Service發行Experience Manager指南之前的版本時)

執行以下步驟後續處理現有內容並使用新的中斷連結報表：

1. （選擇性）如果系統中有超過100,000個DITA檔案，請更新 `queryLimitReads` 和 `queryLimitInMemory` 在 `org.apache.jackrabbit.oak.query.QueryEngineSettingsService` 變更為較大的值（任何大於現有資產數的值，例如200,000），然後重新部署。

   - 請依照以下說明操作： *設定覆寫* 安裝與設定Adobe Experience Manager Guidesas a Cloud Service一節中的以建立設定檔。
   - 在設定檔案中，提供下列（屬性）詳細資料以設定 `queryLimitReads` 和 `queryLimitInMemory` 選項：

     | PID | 屬性索引鍵 | 屬性值 |
     |---|---|---|
     | org.apache.jackrabbit.oak.query.QueryEngineSettingsService | querylimitereads | 值：200000預設值： 100000 |
     | org.apache.jackrabbit.oak.query.QueryEngineSettingsService | queryLimitInMemory | 值：200000預設值： 100000 |

1. 對伺服器執行POST要求（使用正確的驗證） - `http://<server:port>//bin/guides/reports/upgrade`.

1. 此API會傳回jobId。 若要檢查作業的狀態，您可以傳送作業識別碼的GET要求至相同的端點 —  `http://<server:port>/bin/guides/reports/upgrade?jobId= {jobId}`
(例如： `http://localhost:8080/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678`)

1. 工作完成後，先前的GET請求會成功回應。 如果作業由於某個原因而失敗，則可以從伺服器記錄中看到失敗。

1. 還原為預設值或先前的現有值 `queryLimitReads` 如果您已在步驟1中加以變更。

## 為現有內容建立索引，以使用「報表」標籤下新的尋找和取代與主題清單的步驟：

(僅限使用2023年6月as a Cloud Service發行Experience Manager指南之前的版本時)

執行以下步驟來索引現有內容，並在報表標籤底下的對應層級和主題清單中使用新的尋找和取代文字：

1. 對伺服器執行POST要求（使用正確的驗證） - `http://<server:port>/bin/guides/map-find/indexing`. (選用：您可以傳遞地圖的特定路徑來編列索引，預設情況下，所有地圖都會編列索引 ||例如： `https://<Server:port>/bin/guides/map-find/indexing?paths=<map_path_in_repository>`)

1. 您也可以傳遞根資料夾，為特定資料夾（及其子資料夾）的DITA map建立索引。 例如 `http://<server:port>/bin/guides/map-find/indexing?root=/content/dam/test`。請注意，如果同時傳遞路徑引數和根引數，則只會考慮路徑引數。

1. 此API會傳回jobId。 若要檢查作業的狀態，您可以傳送作業識別碼的GET要求至相同的端點 —  `http://<server:port>/bin/guides/map-find/indexing?jobId={jobId}`(例如： `http://localhost:8080/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42`)


1. 工作完成後，先前的GET請求會以成功回應，並提及是否有任何地圖失敗。 可以從伺服器記錄檔確認已成功編制索引的對應。

## 處理問題的步驟 `'fmdita rewriter'` 衝突

Experience Manager指南有 [**自訂sling重寫程式**](../cs-install-guide/conf-output-generation.md#custom-rewriter) 用於處理交叉地圖情況下產生的連結的模組（兩個不同地圖主題之間的連結）。

如果您的程式碼基底中有另一個自訂Sling重寫程式，請使用 `'order'` 值大於50，因為Experience Manager指南sling重寫程式使用 `'order'` 50.  若要覆寫此值，您需要大於50的值。 如需詳細資訊，請檢視 [輸出重寫管道](https://sling.apache.org/documentation/bundles/output-rewriting-pipelines-org-apache-sling-rewriter.html).

在此升級期間，由於 `'order'` 值從1000變更為50，您需要將現有的自訂重寫程式（如果有的話）與 `'fmdita-rewriter'`.


## 相容性矩陣

本節列出2023年11月as a Cloud Service發行的Experience Manager指南所支援之軟體應用程式的相容性矩陣。

### FrameMaker和FrameMaker Publishing Server

| 雲端版Experience Manager指南指南 | FMPS | FrameMaker |
| --- | --- | --- |
| 2023.11.0 | 不相容 | 2022或更高 |
| | | |


### 氧氣聯結器

| 雲端版Experience Manager指南 | 氧氣聯結器視窗 | 氧氣聯結器Mac | 在氧氣視窗中編輯 | 在氧氣Mac中編輯 |
| --- | --- | --- | --- | --- |
| 2023.11.0 | 3.2-uuid 5 | 3.2-uuid 5 | 2.3 | 2.3 |
|  |  |  |  |


### 知識庫範本版本

| 元件封裝名稱 | 元件版本 | 範本版本 |
|---|---|---|
| 適用於Cloud Service的Experience Manager指南元件內容套件 | dxml-components.all-1.2.2 | aem-site-template-dxml.all-1.0.15 |

## 已修正的問題

以下列出各種區域中修正的錯誤：



### 編寫

- conref後的空格 `<ph>` 儲存主題時，元素會消失。 (13642)
- 嘗試在後處理完成之前儲存DITA檔案時發生應用程式錯誤。 (13571)
- 如果主題的標題包含斜線 `/`，編輯器中的索引標籤只會顯示後面跟著的字母。 (13455)
- 在編輯器中顯示預覽後，影像預覽並未消失。 (13454)
- 在其他主題中使用根對映定義的索引鍵時，插入關鍵字快顯視窗沒有出現。 (12950)
- 在「版本記錄」面板中預覽高度很高的圖形時，無法看到關閉圖示。 (12867)
- 無法修改的時區 **版本建立日期** 「基準線」欄。 (12711)
- 此 **版本記錄** Assets UI中的面板會針對以下專案顯示不正確的時間戳記： **目前** 欄位。 (12624)
- 從檔案名稱以數字字元開頭的範本建立DITA檔案會導致名稱空間錯誤。 (12188)
- 在網頁編輯器中， **重要參考資料** 視窗會在插入時開啟 `varname` 標籤之間。 (10940)
- 網頁編輯器中無法辨識Zip檔案，而且您無法拖放它們。 (12709)
- 套用了一些屬性的內容在「作者」或「預覽」模式中不會反白顯示。 (11063)
- 在編輯主題後關閉主題時，系統會將您重新導向至AEM首頁，而非返回資料夾檢視。 (13306)
- 在處理已複製並貼入雲端服務的檔案時，會發生延遲。 (12457)
- 即使使用者未從「使用者偏好設定」明確設定，Rootmap設定仍會保留在網頁編輯器中。 (11551)


### 發佈

- 發佈為內容片段功能無法用於搜尋結果中列出的檔案。 (14090)
- 在原生PDF發佈中，範本配置上的背景顏色選擇需要在回復到時重新載入頁面 `None`. (13621)
- 在AEM網站發佈中具有範圍對等連結的大型DITA map中，提交至資料存放區時發生問題。 (13530)
- 在原生PDF發佈中，由於頁首和頁尾中的影像不顯示替代文字，導致協助工具受損。 (12829)
- 若沒有自動新增的副檔名，以原生PDF複製頁面版面配置將無法運作。 (12534)
- 使用原生PDF發佈產生PDF輸出時，檔案名稱會在句點後截斷。 (13620)
- 顯示的圖示和工具提示不正確  **編輯內容** 「原生PDF發佈」中所用「範本」的「頁面配置」工具列中的選項。 (13492)
- 自訂中繼資料無法在最終輸出中使用。 (12116)
- fmdita重寫程式與使用者的重寫程式設定衝突，並導致顯示長URL而非連結。 (12076)
- 在AEM網站預設集中，選擇以 **為每個主題產生個別PDF** 無法運作。 (11555)
- 原生PDF發佈不支援CMYK色域轉換。 (10754)
- 動態基準線呼叫使用名稱而非標題，導致匯出DITA map API失敗。 (14268)

### 管理

- 複製貼上具有不含GUID的自參照連結的DITA檔案時，內容參照會中斷。 (13540)
- 在Web編輯器中，基準線顯示先前版本（而非選取的DITA檔案版本）的標題。 (13444)
- 此 **報表** Web編輯器UI中的索引標籤無法顯示2023年7月Experience Manager指南as a Cloud Service升級之前建立的舊DITA map的主題清單。 (11852)
- 未建立大型DITA map的條件預設集。 (10936)
- 報表中的中斷連結清單下會顯示自我參照連結。 (13539)

### 評論

- 在2023年10月發行的《Experience Manager指南》as a Cloud Service中，網頁編輯器中舊版和最新版本的並排檢閱面板不正確。 (14156)
- 電子郵件範本自訂 **檢閱** 工作流程無法用於覆蓋節點。 (13954)
- 此 **關閉** 「Experience Manager指南」中「複查」頁面上的按鈕可帶使用者前往AEM首頁。 (13535)
- 以韓文建立片段時會出現損壞的字元。 (13489)
- Experience Manager指南稽核畫面中的韓文附件無法點選。 (13436)
- 在檢閱和共同作業畫面中，地圖示題遭到切斷，沒有檢視完整標題的選項。 (13012)

### 轉換

- 自動核准有時無法運作，且若上設定的值不正確，則會發生例外 **翻譯狀態**. (13607)
- 從「翻譯」儀表板匯出的基線會失敗，且不會以目標語言開啟。 (12993)

## 已知問題

Adobe已在2023年11月版本中找出下列已知問題。

- AEM Site輸出的選擇性主題重新產生失敗。
