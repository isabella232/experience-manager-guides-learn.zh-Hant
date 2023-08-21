---
title: 將具有版本的非UUID內容轉換為UUID內容
description: 瞭解如何使用版本移轉非UUID內容。
source-git-commit: 33cdc1b14db0d123c01bbc719c2833ce0df4c9d9
workflow-type: tm+mt
source-wordcount: '1272'
ht-degree: 1%

---




# 使用版本移轉非UUID內容

執行這些步驟，將具有版本的非UUID內容移轉至UUID內容。

## 相容性矩陣

| 最新AEM Guides版本（非UUID） | 移轉至UUID的必要版本 | 支援的升級路徑 |
|---|---|---|
| 3.8.5 | 4.0非UUID | 安裝4.1 (UUID)並執行移轉 |
| 4.0、4.0.x、4.1或4.1.x | 與目前的非UUID相同 | 安裝4.1 (UUID)並執行移轉 |
| 4.2或更新版本 | 不適用 | 尚未支援 |

## 必要的套件

1. **版本清除**： `com.adobe.guides.version-purge-1.0.11.zip` （選擇性）
1. **移轉前**： `com.adobe.guides.pre-uuid-migration-1.0.7.zip`
1. **移轉**： `com.adobe.guides.uuid-upgrade-1.0.17`
1. **移轉後**： `com.adobe.guides.post-uuid-migration-1.0.2.zip`


## 移轉前

1. （可選）對內容執行版本清除以移除不必要的版本，並加快移轉程式。 若要在4.1版上執行版本清除（4.0版不支援），請安裝套件 `com.adobe.guides.version-purge-1.0.11.zip`，並使用此URL前往使用者介面 `http://<server-name> /libs/fmdita/clientlibs/xmleditor_version_purge/page.html`.

   >[!NOTE]
   >
   >此公用程式不會移除基準線或評論中使用的任何版本，或具有任何標籤。
1. 安裝移轉前套件(`com.adobe.guides.pre-uuid-migration-1.0.7.zip`)。

1. 執行以下查詢以取得包含移轉所需估計時間(ETA)的報告，並報告是否有任何檔案包含無法移轉的內容問題。

>[!NOTE]
>
>您需要管理員許可權才能執行移轉。


| 端點 URL | 請求型別 | 查詢引數 | 預期結果 |
|---|---|---|---|
| `/bin/guides/pre_uuid_upgrade` <br> <br>**例如**： http://localhost:4502/bin/guides/pre_uuid_upgrade?root=/content/dam | GET | **根**：根資料夾<br> **值**： `/content/dam` 用於整個存放庫。 | 將會建立移轉前報表(.csv)，列出檔案數、總版本和錯誤。 <br><br> **範例輸出**：<br>RootFolder： /content/dam <br>檔案總數：2697 <br>總計版本： 10380 <br>有錯誤的檔案數： 28 <br>詳細報告可透過AEM CRX取得，網址為 `/content/uuid-pgrade/UuidMigrationReport_1688400131039.csv` |

如果系統中有許多DITA檔案，此步驟可能會失敗。 若要解決此問題，請增加「 」的值，以增加對查詢中周遊檔案數量的限制。 *記憶體中的讀取限制(queryLimitReads)* 在Apache Jackrabbit查詢引擎設定服務中，從100000取大於系統中存在的DITA資產總數的數字。

## 移轉

### 步驟1：更新設定

1. 請確定可用的空間至少是AEM （crx-quickstart目錄）在移轉期間所佔用空間的10倍。 完成移轉後，您可以執行壓縮來回收大部分的磁碟空間(請參閱 [修訂清除](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/revision-cleanup.html?lang=en))。

1. 啟用 *啟用後處理工作流程啟動器* 在 `com.adobe.fmdita.config.ConfigManager` 和 *啟用版本後處理* 在 `com.adobe.fmdita.postprocess.version.PostProcessVersionObservation.`

1. 安裝支援發行版本的UUID版本，而非非UUID版本。 舉例來說，如果您使用4.0版的非UUID組建或4.1版的非UUID組建，便需要安裝UUID 4.1版。

1. 安裝新的套件以進行uuid移轉(`com.adobe.guides.uuid-upgrade-1.0.17`)。

1. 停用下列工作流程以及執行的任何其他工作流程 `/content/dam` 在中使用啟動器 `http://localhost:4502/libs/cq/workflow/content/console.html`.

   * DAM更新資產工作流程
   * dam中繼資料回寫工作流程

1. 停用 *啟用後處理工作流程啟動器* 在 `com.adobe.fmdita.config.ConfigManager` 和停用 *啟用版本後處理* 在 `com.adobe.fmdita.postprocess.version.PostProcessVersionObservation`.

1. 停用屬性啟用驗證(`validation.enabled`)。

1. 確定 `uuid.regex` 屬性資料夾在中已正確設定 `com.adobe.fmdita.config.ConfigManager`. 如果空白，則設定為預設值 —  `^GUID-(?<id>.*)`.
1. 新增單獨的記錄器 `com.adobe.fmdita.uuid.upgrade.UuidUpgrade` 瀏覽器回應也可在以下網址取得： `/content/uuid-upgrade/logs`.

### 步驟2：執行指令碼並驗證

在資料夾中較小型的資料夾上執行指定的查詢後，再於其上執行 `/content/dam`.

>[!TIP]
>
>您可以檢查資料夾中的所有檔案是否已正確升級，以及所有功能是否只適用於該資料夾。

| 端點 URL | 請求型別 | 查詢引數 | 預期結果 |
|---|---|---|---|
| `/bin/guides/uuid_upgrade`<br><br> **例如**： `http://localhost:4502/bin/guides/uuid_upgrade?root=/content/dam/test` | GET | **根**：根資料夾 <br>**值**： /content/dam整個存放庫。<br><br>**ignoreImageVersion**<br> **值**： true/false (忽略影像版本的處理。 預設值為false) | 包含檔案清單的移轉報告已成功移轉、升級失敗、升級時發生錯誤，以及總共花費的時間。 <br><br> **範例輸出**： <br> [資訊] 失敗的檔案清單：0 <br>[資訊] 不適用。 檔案升級成功： 2241 <br>[資訊] 不適用。 已升級但有錯誤的檔案數： 28 <br>[資訊] 不適用。 無法升級的檔案： 0 <br> [資訊] 花費的總時間： 0:37:03.131 |

>[!NOTE]
>
> 內容移轉可在檔案夾層級或完整上執行 `/content/dam` 或在相同資料夾中（重新執行移轉）。

此外，請務必確實針對所有媒體資產完成內容移轉，例如您在DITA內容中使用的影像和圖形。

#### 基準線移轉

在您已經移轉的資料夾上執行查詢，以移轉其上的基準線。

| 端點 URL | 請求型別 | 查詢引數 | 預期結果 |
|---|---|---|---|
| `/bin/guides/baseline_uuid_upgrade`<br><br> **例如**： ` http://localhost:4502/bin/guides/baseline_uuid_upgrade?root=/content/dam/test` | GET | **根**：根資料夾 <br> **值**： /content/dam整個存放庫。 <br><br> **ignoreImageVersion**<br> **值**： true/false <br>(忽略影像版本的處理。 預設值為false) <br><br> **doReviews** <br> **值**： true/false <br> (是否必須升級檢閱。 預設值為false。) 包含檔案清單的移轉報告已成功移轉、升級失敗、升級時發生錯誤，以及總共花費的時間。 <br> <br> **範例輸出**：<br>[資訊] 檔案清單失敗 <br> [資訊] 不適用。 個檔案已順利升級2241<br> [資訊] 不適用。 個檔案已升級，但有錯誤28<br>[資訊] 不適用。 個檔案無法升級0<br>[資訊] 花費的總時間： 0:37:03.131 |


### 步驟3：還原設定

伺服器成功移轉後，請啟用後續處理、標籤和下列工作流程（包括移轉期間最初停用的所有其他工作流程）以繼續在伺服器上運作。

* DAM更新資產工作流程
* DAM中繼資料工作流程

>[!NOTE]
>
>如果某些檔案在移轉前未處理或損毀，則會在移轉前損毀，甚至在移轉後仍會損毀。

## 移轉驗證

1. 安裝uuid移轉後的套件(`com.adobe.guides.post-uuid-migration-1.0.2.zip`)。

1. 執行以下查詢來驗證移轉期間沒有造成任何連結中斷的錯誤。 此指令碼會識別是否有任何之前未中斷但現在因任何原因而中斷的連結。

   | 端點 URL | 請求型別 | 查詢引數 | 預期結果 |
   |---|---|---|---|
   | `/bin/guides/get_broken_links` <br> <br> **例如**：<br>`http://localhost:4502/bin/guides/get_broken_links` | GET | 不適用 | 移轉報告，其中包含UUID損毀的檔案總數及其各自的檔案路徑。 <br> <br> **範例輸出**：<br>[偵錯] 檢查內容中是否使用了所有這些GUID。<br>[偵錯] 可能具有損毀UUID的檔案總數：0 <br>[偵錯] 可能具有中斷的UUID的路徑：0 |

1. 完成移轉後，可執行壓縮以回收大部分的磁碟空間(請參閱 `https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/revision-cleanup.html?lang=en`)。

## 差異內容移轉

1. 若要將差異內容從作用中伺服器（非UUID）移轉至目前的uuid伺服器，請在非UUID伺服器上安裝移轉前指令碼。

1. 在整個資料集（或子資料夾）上執行下列查詢，以識別並匯出在指定時間戳記之後修改的所有檔案：時間戳記使用ISO8601格式作為日期和時間( YYYY-MM-DDTHH:mm:ss.SSSZ)並允許部分表示，如YYYY-MM-DD。

   | 端點 URL | 請求型別 | 查詢引數 | 預期結果 |
   |---|---|---|---|
   | `/bin/guides/data_export`<br><br>**例如**： <br> `http://localhost:4502/bin/guides/data_export?timestamp=2023-07-11&root=/content/dam` | GET | **timestamp** <br> **值**： YYYY-MM-DD<br><br> **根**：根資料夾 <br> **值**： `/content/dam` 用於整個存放庫。 | 在/var/dxml/exports會建立包含差異內容的zip檔案。 <br> <br>**範例**： dataexport_1689761491218.zip （已建立檔案） |

1. 下載由指令碼匯出的zip檔案。 最後一行回應應該會提供所產生zip檔案（儲存在系統中的/var/dxml/exports中）的路徑。

1. 將zip檔案上傳至Assets UI中所需路徑的uuid伺服器。

1. 請確定uuid伺服器上已安裝移轉後套件。

1. 執行以下指定的查詢，將差異內容從上傳的zip檔案匯入系統。 查詢應包括已上傳zip檔案的路徑，以正確識別及處理資料。

   | 端點 URL | 請求型別 | 查詢引數 | 預期結果 |
   |---|---|---|---|
   | `/bin/guides/data_import`<br> **例如**：`http://localhost:4502/bin/guides/data_import?path=/content/dam/dataexport_1689344927551.zip&createVersion=true` | POST | **path**<br> **值**： `/content/dam/filename.zip`（已上傳的檔案位置） **createVersion** <br> **值**： true/false<br>（ createVersion的預設值為false）。 | 檔案會上傳至所需的內容路徑。<br><br>**範例**： `dataexport_1689761491218.zip`<br><br> (上一步中匯出的相同檔案會上傳至中的所需路徑 `/content/dam`)。 |

1. 如果指令碼不存在，則會建立新檔案；如果已修改，則會覆寫現有檔案。

>[!NOTE]
>
> 版本歷史記錄和伺服器上所做的任何其他變更（例如工作流程和檢閱）需要手動更新。
