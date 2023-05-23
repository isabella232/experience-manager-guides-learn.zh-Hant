---
title: 非UUID到UUID內容遷移
description: 瞭解如何將非UUID遷移到UUID內容
source-git-commit: 5ac066bb8db32944abd046f64da11eeb1bdbe467
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---


# 非UUID到UUID內容遷移 {#id226TI0U20XA}

>[!IMPORTANT]
>
> 可以將非UUID內容遷移到UUID伺服器。 要遷移到UUID伺服器，您應安裝非UUID服AEM務器，其上安裝了4.0版指南。

執行以下步驟以遷移非UUID內容：

>[!NOTE]
>
> 每個步驟都至關重要，如果缺少任何步驟，則可能導致伺服器資料失敗或損壞。 確保完成所有步驟。

1. 確保 **啟用後處理工作流啟動程式** 在 *com.adobe.fmdita.config.ConfigManager* 和 **啟用版本後處理** 在 *com.adobe.fmdita.postprocess.version.PostProcessVersionObservation* 的子菜單。

   ```http
   http://<server name>:<port>/system/console/configMgr/com.adobe.fmdita.config.ConfigManager
   ```

1. 在非UUID版本上安裝下一個主發行版的UUID版本。 例如，如果使用4.0非UUID內部版本，則需要安裝UUID版本4.1。

1. 在「啟動程式」頁籤中，禁用以下工作流和在/content/dam上運行的任何其他工作流， `http://localhost:4502/libs/cq/workflow/content/console.html`:

   - **DAM更新資產** 工作流
   - **DAM元資料寫回** 工作流

1. 禁用 **啟用後處理工作流啟動程式** 在 *com.adobe.fmdita.config.ConfigManager* 禁用 **啟用版本後處理** 在 *com.adobe.fmdita.postprocess.version.PostProcessVersionObservation*。

   ```http
   http://<server name>:<port>/system/console/configMgr/com.adobe.fmdita.config.ConfigManager
   ```

1. 添加單獨的記錄器 `com.adobe.fmdita.uuid.upgrade.UuidUpgrade.`

   瀏覽器響應也可在/content/uuid-upgrade/logs中找到。

1. 在包含較小資料的資料夾上運行給定查詢 `doReviews=false` 在/內容/資料庫上運行它之前： `http://localhost:4502/bin/dxml/uuid_upgrade?root=/content/dam/test&doReviews=false`

   >[!TIP]
   >
   >  您可以檢查資料夾中的所有檔案是否已正確升級，且所有功能是否僅用於該資料夾。

**查詢的參數：**

    - &#39;root&#39;:必須升級的根資料夾\(對所有儲存庫使用/content/dam。\)
    - &#39;doReviems&#39;:true/false \(如果評論必須升級或不升級。 預設值為false。\)
    - &#39;doBaselines&#39;:true/false \(如果基線必須升級或不升級。 預設值為true。\)
    - &#39;processLevel&#39;:-1\（未恢復失敗\）、0\（還原失敗\）、1\（失敗\，錯誤\）、2\（成功升級\）\(失敗後重試指令碼時，只會再次處理具有&quot;fmUpgradeStatus&quot; &lt;= processLevel的檔案，否則將忽略它。 預設值為 1。\)
    - &#39;ignoreImageVersions&#39;:true/false \(忽略對映像版本的處理。 預設值為false。\)
    >[！注釋]
    >
    >我們可以在資料夾級別或完整內容/資料庫或同一資料夾\（重新運行遷移\）上運行內容遷移。

1. 成功遷移伺服器後，將啟用以下工作流和後處理以繼續在伺服器上工作：

   - **DAM更新資產** 工作流
   - **DAM元資料** 工作流

>[!NOTE]
>
> 如果某些檔案在遷移之前未被處理或已損壞，則即使在遷移後，它們也會保持損壞狀態。

