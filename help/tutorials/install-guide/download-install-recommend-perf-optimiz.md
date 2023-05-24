---
title: 適用於效能最佳化的Recommendations
description: 瞭解效能最佳化的Recommendations
source-git-commit: 5ac066bb8db32944abd046f64da11eeb1bdbe467
workflow-type: tm+mt
source-wordcount: '959'
ht-degree: 0%

---


# 適用於效能最佳化的Recommendations {#id213BD0JG0XA}

## 設定資料存放區\（必要\）

**有什麼改變？**
設定 `minRecordLength` 屬性變更為值 `100` 在設定下 `org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.` 如需檔案日期存放區和S3資料存放區的詳細資訊，請參閱 [在AEM 6中設定節點存放區和資料存放區](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/data-store-config.html) 文章。

>[!NOTE]
>
> 對於S3資料存放區，維護資料存放區內容的成本也取決於請求數量。 因此，在使用S3進行此設定時，也應考量每個請求的設定成本和快取大小。

**何時設定？**
初始設定之後，但在移轉任何內容之前。 您甚至必須在現有系統上執行此變更，以確保所有新內容都儲存在資料存放區，而不是區段存放區。

**此變更的結果**
DITA檔案儲存在資料存放區中，而不是區段存放區中。 這會將區段存放區大小保持在建議的限制內，進而改善系統的回應能力。

## 更新Lucene索引\（強制\）

**有什麼改變？**
從oak：index/lucene排除/var/dxml。

>[!NOTE]
>
> AEM Guides從未使用Lucene索引來搜尋/var/dxml節點中的內容。

**何時設定？**
如果您在移轉內容之前在新系統上進行了此變更，則只需更新oak：index/lucene。 否則，在內容已移轉的現有系統上，然後在oak：index/lucene中進行變更後，為Lucene重建索引\(*可能需要幾個小時才能完成*\)。

**此變更的結果**
此變更會防止/var/dxml節點建立索引並儲存在區段存放區中。

## Java記憶體最佳化\（必要\）

**有什麼改變？**
JVM啟動引數應根據基礎架構和磁碟大小仔細調整。 建議您洽詢Adobe支援，以取得存取理想設定的協助。 不過，您可以自行嘗試下列設定：

 — 將JVM棧積大小設定為可用的記憶體總數的1/4。 使用引數 `-Xmx<size>` 以設定棧積記憶體大小。 設定 — `Xms` 等於 `-Xmx`.

 — 啟用 `-XX:+HeapDumpOnOutOfMemoryError` 並設定路徑 `-XX:HeapDumpPath=</path/to/folder``>`.

 — 啟用Java GC記錄為：

`* -XX:+PrintGCDateStamps`

`* -verbose:gc`

`* -XX:+PrintGCDetails`

`* -XX:+PrintTenuringDistribution`

`* -Xloggc:</path/to/gc.log>`

 — 一般而言，針對Java 11，請使用G1GC \(`-XX:+UseG1GC`\)和Java 8使用CMS \(-`XX:+UseConcMarkSweepGC`\)。

 — 使用 `-XX:NewRatio` 控制新一代記憶體大小。 預設值為2，這表示記憶體的1/3用於年輕一代使用。 由於有許多物件會快速建立並銷毀，使用值1會將記憶體的1/2配置給年輕一代。

 — 使用控制要提升至舊世代的物件數目 `-XX:MaxTenuringThreshold`. 使用值15 \(default\)可在物件升級至舊世代時延遲。

**何時設定？**
如果您要在現有系統上進行此變更，則需要重新啟動系統。 若是全新安裝，此變更應在系統啟動前於啟動指令碼\(.bat或.sh\)檔案中進行。

**此變更的結果**
這會產生最佳棧積大小並規範GC的執行。

## 製作執行個體上的使用者端資料庫縮制\（選用\）

**有什麼改變？**
使用者端程式庫應設定為在編寫執行個體中縮小。 這可確保在使用者從不同位置瀏覽系統時，要下載的位元組較少。 若要進行此變更，請在以下位置設定設定： **HTML程式庫管理員** 從Felix主控台。

**何時設定？**
這可在執行階段透過Felix主控台或透過程式碼部署完成。

**此變更的結果**
這項變更可改善編寫執行個體上頁面的載入時間，因為用來載入使用者端程式庫的傳輸位元組較少。

## 設定同時發佈的執行緒\（必要，視使用案例而定\）

**有什麼改變？**
如果您使用DITA-OT來發佈輸出，並且也定義了多個並行發佈執行緒，則需要此變更。

根據預設，AEM Guides會將發佈執行緒設定為CPU+1的數量。 不過，建議將此值設定為CPU總數的一半\(1/2\)或三分之一\(1/3\)。 若要這麼做，請設定 **產生集區大小** 設定下的屬性 `com.adobe.fmdita.publish.manager.PublishThreadManagerImpl` 根據建議。

**何時設定？**
這可在執行階段透過Felix主控台或透過程式碼部署完成。

**此變更的結果**
此變更可確保在執行中的作者執行個體上，所有資源都不會配置給發佈作業。 這樣可以讓作者也能使用系統資源，進而獲得更佳的使用者體驗。

## 設定產生AEM Site輸出的批次節點大小\（必要，視使用案例而定\）

**有什麼改變？**
如果您產生AEM Sites輸出，則必須進行此變更。

設定 **限制棧積中的AEM網站頁面** 下的屬性 `com.adobe.fmdita.config.ConfigManager` 至根據您系統組態的數字。 此屬性會定義產生網站頁面時要認可的節點批次大小。 例如，在CPU數目較多且棧積大小較大的系統上，您可以增加預設值，從 `500` 轉換為較大的數字。 您必須使用變更的值來測試回合，才能達到此屬性的最佳值。

**何時設定？**
這可在執行階段透過Felix主控台或透過程式碼部署完成。

**此變更的結果**
增加的 **限制棧積中的AEM網站頁面** 屬性會最佳化AEM Site輸出產生程式。

## 最佳化後續處理執行緒的數量\（必要，視使用案例而定\）

**有什麼改變？**
如果您大量上傳DITA內容，則必須進行此變更。

設定 **後處理執行緒** 下的屬性 `com.adobe.fmdita.config.ConfigManager` 至 `1`.

**何時設定？**
這可在執行階段完成。

**此變更的結果**
此變更可縮短大量上傳DITA檔案的後置處理時間。

**父級主題：**[&#x200B;下載並安裝](download-install.md)

