---
title: 發行說明 | 2023年6月發行的Adobe Experience Manager Guides中的升級指示和修正問題
description: 瞭解錯誤修正以及如何升級至2023年6月Adobe Experience Manager Guidesas a Cloud Service版本
source-git-commit: 03d90157f7169373a287f24ab666bfea634e0ca4
workflow-type: tm+mt
source-wordcount: '1126'
ht-degree: 3%

---

# 2023年6月發行的Adobe Experience Manager Guidesas a Cloud Service

本發行說明涵蓋2023年6月Adobe Experience Manager Guides版本中修正的升級指示、相容性矩陣和問題(以下稱 *AEM指南as a Cloud Service*)。

如需新功能和增強功能的詳細資訊，請參閱 [AEM Guidesas a Cloud Service版2023年6月的新增功能](whats-new-2023.6.0.md).

## 升級至2023年6月發行版本

請執行以下步驟，升級您目前的AEM Guidesas a Cloud Service設定：

1. 檢視Cloud Services的Git程式碼，並切換到在Cloud Services管道中設定的分支，該分支與您要升級的環境相對應。
2. 更新 `<dox.version>` 中的屬性 `/dox/dox.installer/pom.xml` 將Cloud Services Git程式碼的檔案設為2023.6.297。
3. 提交變更並執行Cloud Services管道，以升級至2023年6月版的AEM Guidesas a Cloud Service。

## 透過servlet啟用指令碼觸發的步驟

完成安裝後，您可以選擇「點選」觸發程式以開始翻譯工作：

POST：

```
http://localhost:4503/bin/guides/script/start?jobType=translation-map-upgrade
```

回應:

```
{
"msg": "Job is successfully submitted and lock node is created for future reference",
"lockNodePath": "/var/dxml/executor-locks/translation-map-upgrade/1683190032886",
"status": "SCHEDULED"
}
```

在上一個回應JSON中，索引鍵 `lockNodePath` 會保留在存放庫中建立的節點路徑，指向已提交的工作。 它會在作業完成後自動刪除，在此之前，您可以參照此節點來瞭解作業的目前狀態。

請等到此工作完成後，再繼續後續步驟。

>[!NOTE]
>
> 您應該檢查節點是否仍然存在，以及工作的狀態。

```
GET
http://<aem_domain>/var/dxml/executor-locks/translation-map-upgrade/1683190032886.json
```

## 後續處理現有內容以使用中斷連結報告的步驟

(僅適用於使用2023年6月AEM Guidesas a Cloud Service版之前的版本時)

執行以下步驟，後續處理現有內容並使用新的中斷連結報表：

1. （選用）如果系統中有超過100,000個dita檔案，請更新 `queryLimitReads` 在 `org.apache.jackrabbit.oak.query.QueryEngineSettingsService` 變更為較大的值（任何大於現有資產數的值，例如200,000），然後重新部署。

   - 使用中提供的指示 *設定覆寫* 安裝與設定Adobe Experience Manager Guidesas a Cloud Service一節中的以建立設定檔。
   - 在組態檔中，提供下列（屬性）詳細資訊以設定queryLimitReads選項：

      | PID | 屬性索引鍵 | 屬性值 |
      |---|---|---|
      | org.apache.jackrabbit.oak.query.QueryEngineSettingsService | queryLimitReads | 值：200000預設值： 100000 |

1. 對伺服器執行POST要求（使用正確的驗證） - `http://<server:port>//bin/guides/reports/upgrade`.

1. 此API將傳回jobId。 若要檢查作業的狀態，您可以將具有作業ID的GET要求傳送至相同的端點 —  `http://<server:port>/bin/guides/reports/upgrade?jobId= {jobId}`
(例如： 
`http://localhost:8080/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678`)

1. 工作完成後，先前的GET請求將會成功回應。 如果作業由於某個原因失敗，則可以從伺服器記錄中看到失敗。

1. 恢復為預設值或先前的現有值 `queryLimitReads` 如果您已在步驟1中加以變更。

## 為現有內容建立索引，以使用「報表」標籤下新的尋找和取代及主題清單的步驟：

(僅適用於使用2022年9月之前版本的AEM Guidesas a Cloud Service版本的情況)

執行以下步驟來索引現有內容，並在報告標籤下的地圖層級和主題清單中使用新的尋找和取代文字：

1. 對伺服器執行POST要求\（使用正確的驗證\） - `http://<server:port\>/bin/guides/map-find/indexing`. (可選：您可以傳遞地圖的特定路徑來為其建立索引，預設情況下，所有地圖都將建立索引\|\|例如： `https://<Server:port\>/bin/guides/map-find/indexing?paths=<map\_path\_in\_repository\>`)

1. 您也可以傳遞根資料夾，以索引特定資料夾（及其子資料夾）的DITA map。 例如， `http://<server:port\>/bin/guides/map-find/indexing?root=/content/dam/test`. 請注意，如果同時傳遞了路徑引數和根引數，則只會考慮路徑引數。

1. 此API將傳回jobId。 若要檢查作業的狀態，您可以將具有作業ID的GET要求傳送至相同的端點 —  `http://<server:port\>/bin/guides/map-find/indexing?jobId=\{jobId\}`\(例如： `http://localhost:8080/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42`\)


1. 工作完成後，先前的GET請求將會以成功回應，並提及是否有任何地圖失敗。 可以從伺服器記錄檔確認已成功建立索引的對應。

## 相容性矩陣

本節列出AEM Guides 2023年6月as a Cloud Service版本支援之軟體應用程式的相容性矩陣。

### FrameMaker和FrameMaker Publishing Server

| AEM Guides as a Cloud版本 | FMPS | FrameMaker |
| --- | --- | --- |
| 2023.06.0 | 不相容 | 2022或更高 |
|  |  |  |


### 氧氣聯結器

| AEM Guides as a Cloud版本 | 氧氣聯結器視窗 | 氧氣聯結器Mac | 在氧氣視窗中編輯 | 在氧氣Mac中編輯 |
| --- | --- | --- | --- | --- |
| 2023.06.0 | 2.9-uuid-2 | 2.9-uuid-2 | 2.3 | 2.3 |
|  |  |  |  |


## 已修正的問題

修復了各種區域的錯誤如下所列：

### 編寫

- 從版面檢視切換至作者或來源檢視時，Navtitle會從content33中移除。 (12174)
- 有時按一下DITA map時發生應用程式錯誤。 (11842)
- 網頁編輯器 |編輯主題時在XML編輯器中新增不斷行空格。 (11786)
- 資產UI |在「清單」檢視中，無法合併覆蓋的可用欄。 (11528)
- 地圖檢視中未解析Keyref。 (11490)
- 透過XML編輯器導覽時，未出現頂端功能表。 (10868)
- `conref` 在ph標籤中 |顯示的瀏覽對話方塊不正確。 (9481)
- 指向其他元素的本機連結不會在Web編輯器中解析。 (8790)
- Matches()函式在schematron功能中無法運作。 (11224)


### 管理

- Web Editor UI中的「報表」索引標籤不會顯示4.2升級之前建立的舊DITA map的主題清單。 (11708)

- 4.2版中資產UI中斷的「上傳檔案」按鈕功能。 (11633)

### 發佈

- 從Pod讀取已重新整理或重新啟動的暫存檔時，發佈至AEM網站失敗。 (12113)
- 原生PDF |如果發佈的內容具有包含brackets()的輸出類別，會導致發佈凍結。 (11936)
- JSON輸出 |屬性值為「 」的中繼資料對應 `"value in spaces and double quotes"` 導致發佈錯誤。 (11933)
- 網頁編輯器 |無法在AEM預設集中選取輸出路徑和範本。 (11530)
- 原生PDF |自訂屬性不會傳播至暫時HTML或PDF引擎。 (DXML-12005)
- 原生PDF |發佈大型內容時發生Java OutOfMemoryError。 (11789)
- JSON輸出 | `fmUuid` json的jcr：content節點上的屬性與JSON內的「id」不同。 (11564)
- JSON輸出 |如果存在具有相同檔案名稱的對映和主題，則會移除對映的JSON。 (11524)
- 原生PDF | Xref正在列印href主題標題的內容而不是Xref標籤。 (11322)
- 原生PDF |無法儲存PDF範本設定。 (10751)
- 原生PDF |文字延伸超過包括多個xref上的欄寬。 (10876)
- 原生PDF | `<note>``</note>` 元素不會產生其型別的額外範圍標題。 (10549)



### 轉換

- 2月後的雲端版本(2302)中，所有翻譯內容都顯示「不同步」或「缺少副本」。 (11834)

### 評論

- 新的稽核UI |條件會反白顯示，並顯示隱藏的工作方式與在Web Editor中的工作方式不同。 (11628)
