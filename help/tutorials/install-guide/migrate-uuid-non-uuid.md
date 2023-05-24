---
title: 非UUID移轉至UUID內容
description: 瞭解如何將非UUID內容移轉至UUID內容
source-git-commit: 5ac066bb8db32944abd046f64da11eeb1bdbe467
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---


# 非UUID移轉至UUID內容 {#id226TI0U20XA}

>[!IMPORTANT]
>
> 您可以將非UUID內容移轉至UUID伺服器。 若要移轉至UUID伺服器，您應該安裝附有AEM guides 4.0版的非UUID伺服器。

執行以下步驟來移轉非UUID內容：

>[!NOTE]
>
> 每個步驟都很重要，若缺少任何步驟，可能會導致伺服器資料失敗或損毀。 請確定您已完成所有步驟。

1. 確定 **啟用後處理工作流程啟動器** 在 *com.adobe.fmdita.config.ConfigManager* 和 **啟用版本後處理** 在 *com.adobe.fmdita.postprocess.version.PostProcessVersionObservation* 已啟用。

   ```http
   http://<server name>:<port>/system/console/configMgr/com.adobe.fmdita.config.ConfigManager
   ```

1. 安裝下一個主要發行版本的UUID版本（而非非UUID版本）。 例如，如果您使用4.0非UUID版本編號，則需安裝UUID 4.1版。

1. 在「啟動器」標籤中，停用以下工作流程以及使用中的啟動器在/content/dam上執行的任何其他工作流程 `http://localhost:4502/libs/cq/workflow/content/console.html`：

   - **DAM更新資產** 工作流程
   - **DAM中繼資料回寫** 工作流程

1. 停用 **啟用後處理工作流程啟動器** 在 *com.adobe.fmdita.config.ConfigManager* 和停用 **啟用版本後處理** 在 *com.adobe.fmdita.postprocess.version.PostProcessVersionObservation*.

   ```http
   http://<server name>:<port>/system/console/configMgr/com.adobe.fmdita.config.ConfigManager
   ```

1. 新增單獨的記錄器 `com.adobe.fmdita.uuid.upgrade.UuidUpgrade.`

   瀏覽器回應也位於/content/uuid-upgrade/logs。

1. 在具有較小資料的資料夾上執行指定的查詢 `doReviews=false` 在/ content/dam上執行之前： `http://localhost:4502/bin/dxml/uuid_upgrade?root=/content/dam/test&doReviews=false`

   >[!TIP]
   >
   >  您可以檢查資料夾中的所有檔案是否已正確升級，且所有功能是否都只對該資料夾運作。

**查詢的引數：**

    - &#39;root&#39;：必須升級的根資料夾\（對所有存放庫使用/content/dam）。\)
    - &#39;doReviews&#39;： true/false \(如果必須升級檢閱，或不升級。 預設值為false。\)
    - &#39;doBaselines&#39;： true/false \(如果基線必須升級或不升級。 預設值為true。\)
    - &#39;processLevel&#39;： -1\（失敗但不還原\）、0\（失敗但還原\）、1\（失敗但出現錯誤\）、2\（已成功升級\） \(失敗後重試指令碼時，只會再次處理具有「fmUpgradeStatus」 &lt;= processLevel的檔案，否則會忽略該檔案。 預設值為 1。\)
    - &#39;ignoreImageVersions&#39;： true/false \(忽略影像版本的處理。 預設值為false。\)
    >[！NOTE]
    >
    >我們可以在資料夾層級或完整內容/dam或相同資料夾上執行內容移轉\（重新執行移轉\）。

1. 伺服器成功移轉後，請啟用下列工作流程和後續處理，以繼續在伺服器上運作：

   - **DAM更新資產** 工作流程
   - **DAM中繼資料** 工作流程

>[!NOTE]
>
> 如果某些檔案在移轉前未處理或損毀，即使在移轉後，也會維持損毀。

