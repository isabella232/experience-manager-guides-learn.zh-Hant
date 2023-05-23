---
title: Recommendations用於效能優化
description: 瞭解Recommendations的效能優化
source-git-commit: 5ac066bb8db32944abd046f64da11eeb1bdbe467
workflow-type: tm+mt
source-wordcount: '959'
ht-degree: 0%

---


# Recommendations用於效能優化 {#id213BD0JG0XA}

## 配置資料儲存\（強制\）

**有什麼變化？**
設定 `minRecordLength` 屬性的值 `100` 在配置下 `org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.` 有關檔案日期儲存和S3資料儲存的詳細資訊，請參見 [在6中配置節點儲存和數AEM據儲存](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/data-store-config.html) 文章。

>[!NOTE]
>
> 對於S3資料儲存，在資料儲存中維護內容的成本也取決於請求數。 因此，在使用S3執行此設定時，還應考慮每個請求的設定成本和快取大小。

**何時配置？**
初始設定後，但遷移任何內容之前。 您甚至必須在現有系統上執行此更改，這可確保所有新內容都儲存在資料儲存中，而不是儲存段。

**此更改的結果**
DITA檔案保存在資料儲存中，而不是段儲存中。 這將段儲存大小保持在建議的限制之下，從而提高系統的響應能力。

## 更新Lucene索引\（強制\）

**有什麼變化？**
從oak:index/lucene中排除/var/dxml。

>[!NOTE]
>
> 參AEM考線從不使用Lucene索引在/var/dxml節點中搜索內容。

**何時配置？**
如果您在遷移內容之前在新系統上進行此更改，則只需更新oak:index/lucene。 否則，在內容已遷移的現有系統上，在更改oak:index/lucene後，為Lucene重建索引\(*可能需要幾個小時才能完成*\)。

**此更改的結果**
此更改會阻止/var/dxml節點被索引並儲存在段儲存中。

## Java記憶體優化\（強制\）

**有什麼變化？**
應根據基礎架構和磁碟大小仔細調整JVM啟動參數。 建議您咨詢Adobe支援以獲取訪問理想配置的幫助。 但是，您可以自己嘗試以下配置：

 — 將JVM堆大小設定為總可用記憶體的至少四分之一。 使用參數 `-Xmx<size>` 設定堆記憶體大小。 設定 — 的值`Xms` 等於 `-Xmx`。

 — 啟用 `-XX:+HeapDumpOnOutOfMemoryError` 並為 `-XX:HeapDumpPath=</path/to/folder``>`。

 — 將Java GC日誌啟用為：

`* -XX:+PrintGCDateStamps`

`* -verbose:gc`

`* -XX:+PrintGCDetails`

`* -XX:+PrintTenuringDistribution`

`* -Xloggc:</path/to/gc.log>`

 — 通常，對於Java 11，使用G1GC \(`-XX:+UseG1GC`\)，對於Java 8，使用CMS \(-`XX:+UseConcMarkSweepGC`\)。

 — 使用 `-XX:NewRatio` 控制新一代記憶體大小。 預設值為2，表示記憶體的1/3用於年輕一代。 由於有許多對象正在快速建立和銷毀，因此使用值1將將1/2的記憶體分配給年輕一代。

 — 使用 `-XX:MaxTenuringThreshold`。 使用值15 \（預設\）可在對象升級到舊代時延遲。

**何時配置？**
如果在現有系統上進行此更改，則需要重新啟動系統。 在進行新安裝時，應在啟動系統之前在啟動指令碼\(.bat或.sh\)檔案中進行此更改。

**此更改的結果**
這導致最佳堆大小和GC的調節執行。

## 作者實例的客戶端庫精簡\（可選\）

**有什麼變化？**
客戶端庫應設定為在「創作」實例中小型化。 這可確保用戶從不同位置瀏覽系統時下載的位元組數較少。 要進行此更改，請在 **HTML庫管理器** 費利克斯控制台。

**何時配置？**
這可以通過Felix控制台或通過代碼部署在運行時完成。

**此更改的結果**
此更改改善了Author實例上頁面的載入時間，因為為載入客戶端庫而傳輸的位元組數較少。

## 配置併發發佈線程\（必需，具體取決於使用情形\）

**有什麼變化？**
如果您使用DITA-OT發佈輸出，並且還定義了多個併發發佈線程，則需要進行此更改。

預設情況下，AEM參考線將發佈線程設定為CPU數+1。 但是，建議將此值設定為CPU總數的一半\(1/2\)或三分之一\(1/3\)。 要執行此操作，請設定 **層代池大小** 配置下的屬性 `com.adobe.fmdita.publish.manager.PublishThreadManagerImpl` 按照建議。

**何時配置？**
這可以通過Felix控制台或通過代碼部署在運行時完成。

**此更改的結果**
此更改可確保在正在運行的Author實例上沒有為發佈操作分配所有資源。 這也使系統資源可供作者使用，從而獲得更好的用戶體驗。

## 為站點輸出生成配AEM置節點的批處理大小\（必需，具體取決於用例\）

**什麼變化？**
如果要生成AEM Sites輸出，則需要此更改。

設定 **限AEM制堆中的站點頁** 財產 `com.adobe.fmdita.config.ConfigManager` 根據您的系統配置將其轉換為數字。 此屬性定義生成網站頁時要提交的節點的批大小。 例如，在CPU數量較大且堆大小較大的系統上，可以從 `500` 到更大的數字。 您需要test運行時的值已更改，以便達到此屬性的最佳值。

**何時配置？**
這可以通過Felix控制台或通過代碼部署在運行時完成。

**此更改的結果**
增加 **限AEM制堆中的站點頁** 屬性可優化AEMSite輸出生成過程。

## 優化後處理線程數\（必需，具體取決於用例\）

**有什麼變化？**
如果正在批量上載DITA內容，則需要此更改。

設定 **後處理線程** 財產 `com.adobe.fmdita.config.ConfigManager` 至 `1`。

**何時配置？**
這可以在運行時完成。

**此更改的結果**
此更改縮短了DITA檔案批量上載後處理時間。

**父主題：**[&#x200B;下載並安裝](download-install.md)

