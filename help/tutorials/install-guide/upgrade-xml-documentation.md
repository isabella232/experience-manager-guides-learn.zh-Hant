---
title: 升級Adobe Experience Manager指南
description: 瞭解如何升級Adobe Experience Manager指南
exl-id: fdc395cf-a54f-4eca-b69f-52ef08d84a6e
source-git-commit: bb7e9ae6f02021354285aa4ca6b435bbea2e4cc0
workflow-type: tm+mt
source-wordcount: '3270'
ht-degree: 1%

---

# 升級Adobe Experience Manager指南 {#id224MBE0M0XA}

>[!NOTE]
>
> 請依照產品的授權版本專屬的升級指示操作。

您可以將目前版本的AEM Guides升級至4.3.0版

- 如果您是使用4.2版或4.2.x版，則可以直接升級至4.3.0版。
- 如果您使用的是4.1或4.1.x版，則必須先升級至4.2或4.2.x版，才能升級至4.3.0版。
- 如果您使用的是4.0版，則必須先升級至4.2版，才能升級至4.3.0版。
- 如果您使用的是3.8.5版，則必須先升級至4.0版，才能升級至4.2版。
- 如果您使用的是3.8.5之前的版本，請參閱產品特定安裝指南中的升級AEM Guides區段。


>[!NOTE]
>
> 您必須先安裝AEM Service Pack，才能升級AEM Guides版本。

如需詳細資訊，請參閱下列程式：

- [從3.8.5升級至4.0版](#id2256DK003E1)
- [升級至4.2版](#id22A3F500SXA)
- [升級至4.2.1版](#upgrade-version-4-2-1)
- [升級至4.3.0版](#upgrade-version-4-3)


>[!IMPORTANT]
>
> 在開始升級之前，請先進行完整的系統備份，以避免任何資料遺失。

## 從3.8.5版升級至4.0版 {#id2256DK003E1}

如果您是使用AEM Guides 3.8.5版，則可升級至AEM Guides 4.0版。 使用升級功能，您不必解除安裝舊版的AEM Guides。

在執行程式之前，您必須先完成某些工作。 以下小節將逐步引導您瞭解先決條件、報表產生和移轉程式。 此外，安裝AEM Guides 4.0版後，您可以根據客戶設定自訂各種設定。

>[!NOTE]
>
> 此升級程式僅適用於3.8.5版到4.0版。如需從3.4版或更新版本升級至3.8.5的程式，請參閱 *升級AEM指南* 中提供的產品特定安裝指南部分 [說明封存頁面](https://helpx.adobe.com/xml-documentation-for-experience-manager/archive.html).

****必備條件****

在開始AEM Guides升級程式之前，請確定您擁有：

1. 已匯入開啟供稽核之主題中的稽核註釋。
1. 已關閉所有進行中的評論。
1. 已關閉所有翻譯任務。
1. 解除安裝安裝在AEM Guides舊版\（主要或修補程式版本\）頂端的AEM Guides修補程式。

**安裝4.0版之前**

安裝4.0版之前，請先執行下列步驟：

1. 確定此時的AEM Guides為3.8.5版。
1. 下載升級指令碼套件。 若要這麼做，請在上搜尋「XML Documentation解決方案4.0升級套件」 [Adobe軟體發佈入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) 將下載zip檔。
1. 透過封裝管理員將此封裝上傳到AEM並安裝此封裝。
1. 安裝升級套件後，請以相同順序執行下列指定指令碼，並依照指定指示執行：

**檢查升級相容性API**

此API的設計目的是評估目前的系統狀態，並報告升級是否可行。 若要執行此指令碼，請觸發以下指定的端點：

| 端點 | /bin/dxml/upgrade/3xto4x/report |
| --- | --- |
| 請求型別 | **GET** 您可以使用網頁瀏覽器，以管理員身分登入AEM執行個體。 |
| 預期回應 |  — 如果可以移動所有必要的節點，您將會獲得通過檢查。 <br> — 如果目標位置出現節點，您會看到相關錯誤。 清理存放庫\（刪除節點/var/dxml\）並重新安裝升級套件，然後再次觸發此端點。 <br>**注意：** 這不是常見的錯誤，因為3.x AEM Guides之前並未使用目標位置。 <br>  — 如果此指令碼失敗，請勿繼續並報告給您的客戶成功團隊。 |

**系統資料移轉API**

此API的設計用途是移轉系統資料，如 **移轉對應** 區段。

1. 如果Check upgrade compatibility API失敗，請勿執行此指令碼\（不要繼續\）。
1. 一旦Check upgrade compatibility API傳回成功，您就可以執行升級指令碼。

| 端點 | /bin/dxml/upgrade/3xto4x |
| --- | --- |
| 請求型別 | **POST** 此指令碼為POST請求，因此應透過Postman等代理程式執行。 |
| 預期回應 |  — 成功移轉後，您可以安裝XML Documentation解決方案4.0版。<br> — 發生錯誤時，請還原至最後一個查核點，並與您的客戶成功團隊共用錯誤記錄和API輸出。 |

**移轉對應**：上述API會將來源位置下的所有資料移轉至目標位置。

| 來源 | 目標 |
|------|------|
| /content/fmdita | /var/dxml |
| /content/dxml | /var/dxml |
| /etc/fmdita | /libs/fmdita |

## 安裝4.0版 {#id23598G006XA}

1. 只有在升級步驟成功時才安裝4.0版。
1. 從下載4.0版套件 [Adobe軟體發佈入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)：

   - 如果您使用UUID版本的軟體，請搜尋「適用於AEM 6.5的XML Documentation解決方案的4.0 UUID版本」。
   - 如果您使用非UUID版本的軟體，請搜尋「適用於AEM 6.5的XML Documentation解決方案的4.0非UUID版本」。
使用CRX封裝管理員將封裝上傳到現有的AEM伺服器執行個體並進行安裝。

   >[!NOTE]
   >
   > 等待所有系統元件啟動。

1. 安裝套件後清除瀏覽器快取。
1. 如果在AEM Author例項上設定Dispatcher，請執行以下步驟：
   - 請確定下列專案已在Dispatcher規則中處理：
   - URL模式/home/users/\*/preferences已加入白名單。
   - 不會快取URL模式/libs/cq/security/userinfo.json 。
1. 清除Dispatcher快取\(以清除任何 `clientlibs` cached\)。

## 升級至4.2版 {#id22A3F500SXA}

升級至4.2版須視目前AEM Guides的版本而定。

如果您是使用4.0、4.1或4.1.x版，則可以直接升級至4.2版。

****必備條件****

在開始AEM Guides 4.2升級程式之前，請確定您擁有：

1. 升級至AEM Guides 4.0、4.1或4.1.x版。
1. 已關閉所有翻譯任務。
1. 將記錄層級變更為 **資訊** 的 `com.adobe.fmdita.translationservices.TranslationMapUpgradeScript` 類別並將這些記錄附加至新的記錄檔中，例如， `logs/translation_upgrade.log.`

>[!NOTE]
>
> 您應該關閉所有作用中的評論。 若在升級至4.2時未關閉稽核任務，則舊版進行中的稽核任務會持續將使用者帶入舊版稽核頁面，且升級後建立的稽核任務會在功能中顯示最新的更新。

## 安裝4.2版 {#id2245IK0E0EV}

1. 從下載4.2版本的套件 [Adobe軟體發佈入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).
1. 安裝4.2版本的套件。
1. 完成套件安裝後，請等候記錄中的下列訊息：

   `Completed the post deployment setup script`

   上述訊息表示安裝的所有步驟均已完成。

   如果您遇到以下任何錯誤首碼，請向您的客戶成功團隊報告：

   - 部署後安裝指令碼發生錯誤
   - 移植翻譯MAP時發生例外狀況
   - 無法將屬性的轉譯對應從v1連線至v2
1. 升級氧氣聯結器外掛程式，隨版本4.2發行\（如有需要\）。
1. 安裝套件後清除瀏覽器快取。
1. 繼續升級自訂，如下一節所述。

## 安裝4.2版之後 {#id2326F02004K}

>[!IMPORTANT]
>
> 升級後的伺服器上未顯示高科技範本。 若要在伺服器上加入高科技範本，您可以複製該範本：來源： /libs/fmdita/pdf/Hi-Tech目的地： /content/dam/dita-templates/pdf

安裝AEM Guides後，您可以將適用於新安裝版本的各種設定合併到您的設定中。

>[!NOTE]
>
> 可以自訂dam-update-asset模型。 因此，如果已完成任何自訂，則需要將自訂和AEM Guides同步到模型的工作副本中。

1. **DAM更新資產工作流程\（後處理變更\）：**

1. 開啟URL：

   ```http
   http://localhost:4502/libs/cq/workflow/admin/console/content/models.html
   ```

1. 選取 **DAM更新資產工作流程**.
1. 按一下 **編輯**.
1. 如果 **DXML後續程式發起人** 元件存在，請確定自訂已同步。
1. 如果 **DXML後續程式發起人** 元件不存在，請執行以下步驟來插入它：

1. 按一下 **插入元件** \(負責AEM Guides後續處理，將此作為程式的最後一步\)。
1. 設定 **程式步驟** 詳細資料如下：

   **通用標籤**

   **標題：** DXML後續程式發起人

   **說明**：DXML後續處理啟動器步驟，此步驟將觸發用於已修改/已建立資產的DXML後續處理的Sling工作

   **「處理」標籤**

   - 選取 **DXML後續程式發起人**&#x200B;從 **程式** 下拉式清單

   - 選取 **處理常式前進**

   - 選取 **完成**

1. 按一下 **同步** 完成變更後於右上角顯示。 您將會收到成功通知。

   >[!NOTE]
   >
   > 重新整理並確認自訂變更和AEM Guides後處理步驟出現在最終工作流程模型中。

1. 一次 **DAM更新資產工作流程**&#x200B;已驗證，請檢查對應的啟動器設定。 若要這麼做，請前往AEM Workflow介面並開啟啟動器。

   ```http
   http://localhost:4502/libs/cq/workflow/content/console.html
   ```

   尋找下列兩個啟動器\（若有需要\）並進行變更\（應該為作用中\），其對應至 **DAM更新資產工作流程**：

1. 「 」的啟動器&#x200B;*節點已建立*「 for **DAM更新資產工作流程** — 適用於條件 `"jcr:content/jcr:mimeType!=video"`，萬用字元值應為：

   ```json
   /content/dam(/((?!/subassets|/translation_output).)*/)renditions/original
   ```

   - &#39;excludeList&#39;應該有 `"event-user-data:changedByWorkflowProcess"`.
   - 「 」的啟動器&#x200B;*節點已修改*「 for **DAM更新資產工作流程 —** 條件&quot;`jcr:content/jcr:mimeType!=video`「，
   - 「萬用字元」值應為：

   ```json
   /content/dam(/((?!/subassets|/translation_output).)*/)renditions/original
   ```

   - &#39;excludeList&#39;應該有 `"event-user-data:changedByWorkflowProcess"`.
1. 升級完成後，請確定所有自訂/覆蓋圖均已驗證並更新，以符合新的應用程式程式碼。 以下提供一些範例：
   - 從/libs/fmditor/libsis覆寫的任何元件都應與新的產品程式碼進行比較，且更新應在/apps下方的覆寫檔案中完成。
   - 產品中使用的任何clientlib類別都應檢閱是否有變更。 任何覆寫的設定\（範例如下\）都應與最新的設定進行比較，以取得最新的功能：
   - elementmapping.xml
   - ui\_config.json\（可能已在資料夾設定檔中設定\）
   - 已修改 `com.adobe.fmdita.config.ConfigManager`
   - 檢查是否有任何自訂程式碼使用任何舊路徑\(如 [移轉對應](#id2244LE040XA) section\) — 應更新為新路徑，以便自訂也能如預期運作。
1. 閱讀最新版本中的任何新設定\(檢查 [發行說明](../release-info/release-notes-4.3.md)\)並檢視是否有任何功能受到影響，然後採取適當的動作。 例如使用4.0版中引進的「改善檔案和版本處理」，您需要為此啟用設定。

## 為現有內容建立索引以使用新尋找和取代的步驟：

執行以下步驟來索引現有內容，並在地圖層級使用新的尋找和取代文字：

- 對伺服器執行POST要求\（使用正確的驗證\） - `http://<server:port\>/bin/guides/map-find/indexing`. \(選用：您可以傳遞地圖的特定路徑來編列索引，預設情況下，所有地圖都會編列索引\|\|例如： `https://<Server:port\>/bin/guides/map-find/indexing?paths=<map\_path\_in\_repository\>`\)

- 此API將傳回jobId。 若要檢查作業的狀態，您可以傳送作業識別碼的GET要求至相同的端點 — 

`http://<server:port\>/bin/guides/map-find/indexing?jobId=\{jobId\}`\(例如： `http://localhost:8080/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42`\)

- 工作完成後，上述GET要求將回應為成功，並提及是否有任何地圖失敗。 可以從伺服器記錄檔確認已成功編制索引的對應。

如果升級作業失敗，錯誤記錄會顯示下列錯誤：

「此 *查詢* 讀取或周遊多於 *100000節點*. 為了避免影響其他工作，已停止處理。」

因為未針對升級中使用的查詢正確設定索引，所以可能發生這種情況。 您可以嘗試下列因應措施：

1. 在damAssetLucene Oak索引中，新增布林值屬性 `indexNodeName` 作為 `true` 在節點中。
   `/oak:index/damAssetLucene/indexRules/dam:Asset`
1. 在節點底下新增名稱為excert的新節點。

   `/oak:index/damAssetLucene/indexRules/dam:Asset/properties`
並在節點中設定下列屬性：

   ```
   name - rep:excerpt
   propertyIndex - {Boolean}true
   notNullCheckEnabled - {Boolean}true
   ```

   的結構 `damAssetLucene` 應該看起來像這樣：

   ```
   <damAssetLucene compatVersion="{Long}2" async="async, nrt" jcr:primaryType="oak:QueryIndexDefinition" evaluatePathRestrictions="{Boolean}true" type="lucene">
   <indexRules jcr:primaryType="nt:unstructured">
     <dam:Asset indexNodeName="{Boolean}true" jcr:primaryType="nt:unstructured">
       <properties jcr:primaryType="nt:unstructured">
         <excerpt name="rep:excerpt" propertyIndex="{Boolean}true" jcr:primaryType="nt:unstructured" notNullCheckEnabled="{Boolean}true"/>
       </properties>
       </dam:Asset>
     </indexRules>
   </damAssetLucene>    
   ```


   （以及其他現有節點和屬性）

1. 重新索引 `damAssetLucene` 索引(將重新索引標幟設為 `true` 在底下，並等待它成為 `false` 再次（這表示重新索引已完成）。 請注意，視索引大小而定，這可能需要幾個小時。
1. 執行先前的步驟，再次執行索引指令碼。


## 升級至4.2.1版 {#upgrade-version-4-2-1}

升級至4.2.1版須視AEM Guides的目前版本而定。

如果您是使用4.1版、4.1.x版或4.2版，則可以直接升級至4.2.1版。

>[!NOTE]
>
>後期處理和索引可能需要幾個小時。 我們建議您在非尖峰時段開始升級程式。

****必備條件****

在開始AEM Guides 4.2.1升級程式之前，請確定您已：

1. 升級至AEM Guides 4.1、4.1.x或4.2版。
1. 已關閉所有翻譯任務。
1. 將記錄層級變更為 **資訊** 的 `com.adobe.fmdita.translationservices.TranslationMapUpgradeScript` 類別並將這些記錄附加至新的記錄檔中，例如， `logs/translation_upgrade.log.`

>[!NOTE]
>
> 您應該關閉所有作用中的評論。 若在升級至4.2時未關閉稽核任務，則舊版進行中的稽核任務會持續將使用者帶入舊版稽核頁面，且升級後建立的稽核任務會在功能中顯示最新的更新。

## 安裝4.2.1版

1. 從下載4.2.1版套件 [Adobe軟體發佈入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).
1. 安裝4.2.1版本的套件。
1. 您可以選擇點選觸發器，以啟動翻譯對應升級工作。 如需詳細資訊，請參閱 [透過Servlet啟用指令碼的觸發](#enable-trigger-serverlet).


1. 完成套件安裝後，請等候記錄中的下列訊息：

   `Completed the post deployment setup script`

   上述訊息表示安裝的所有步驟均已完成。

   如果您遇到以下任何錯誤首碼，請向您的客戶成功團隊報告：

   - 部署後安裝指令碼發生錯誤
   - 移植翻譯MAP時發生例外狀況
   - 無法將屬性的轉譯對應從v1連線至v2
1. 升級氧氣聯結器外掛程式，隨版本4.2發行\（如有需要\）。
1. 安裝套件後清除瀏覽器快取。
1. 繼續升級自訂，如下一節所述。

### 透過Servlet啟用指令碼的觸發{#enable-trigger-serverlet}

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

在上述回應JSON中，索引鍵 `lockNodePath` 儲存指向存放庫中建立的、指向已提交作業的節點的路徑。 它會在作業完成後自動刪除，在此之前，您可以參照此節點來瞭解作業的目前狀態。

範例記錄：以下是觸發指令碼後記錄檔中顯示的記錄範例。

```
04.05.2023 14:17:12.876 *INFO* [[0:0:0:0:0:0:0:1] [1683190032736] POST /bin/guides/script/start HTTP/1.1] com.adobe.dxml.common.executor.RunnableSynchronizedOTS Acquiring lock for job : translation-map-upgrade
04.05.2023 14:17:12.897 *INFO* [pool-59-thread-1] com.adobe.fmdita.xmltranslation.ots.TranslationMapUpgradeOTS Starting the thread to upgrade translation map from V1 to V2
04.05.2023 14:17:12.899 *INFO* [pool-59-thread-1] com.adobe.dxml.common.executor.RunnableSynchronizedOTS Initiating lock for node : /var/dxml/executor-locks/translation-map-upgrade/1683190032886
04.05.2023 14:17:12.901 *INFO* [pool-59-thread-1] com.adobe.fmdita.translationservices.TranslationMapUpgradeScript Starting porting of translation map from V1 to V2
04.05.2023 14:17:12.904 *INFO* [pool-59-thread-1] com.adobe.fmdita.translationservices.TranslationMapUpgradeScript Memory increase is of : 764 kB
04.05.2023 14:17:12.906 *INFO* [pool-59-thread-1] com.adobe.fmdita.translationservices.TranslationMapUpgradeScript Completed porting of translation map from V1 to V2
04.05.2023 14:17:12.907 *INFO* [pool-59-thread-1] com.adobe.dxml.common.executor.RunnableSynchronizedOTS Releasing lock for node : /var/dxml/executor-locks/translation-map-upgrade/1683190032886
04.05.2023 14:17:12.909 *INFO* [pool-59-thread-1] com.adobe.fmdita.xmltranslation.ots.TranslationMapUpgradeOTS Completed the thread to upgrade translation map from V1 to V2
```

尋找 `com.adobe.fmdita.translationservices.TranslationMapUpgradeScript Completed porting of translation map from V1 to V2` 和 `com.adobe.fmdita.xmltranslation.ots.TranslationMapUpgradeOTS Completed the thread to upgrade translation map from V1 to V2` 然後再繼續進行後續步驟。



## 安裝4.2.1版之後

>[!IMPORTANT]
>
> 升級後的伺服器上未顯示高科技範本。 若要在伺服器上加入高科技範本，您可以複製該範本：來源： /libs/fmdita/pdf/Hi-Tech目的地： /content/dam/dita-templates/pdf

安裝AEM Guides後，您可以將適用於新安裝版本的各種設定合併到您的設定中。

>[!NOTE]
>
> 可以自訂dam-update-asset模型。 因此，如果已完成任何自訂，則需要將自訂和AEM Guides同步到模型的工作副本中。

1. **DAM更新資產工作流程\（後處理變更\）：**

1. 開啟URL：

   ```http
   http://localhost:4502/libs/cq/workflow/admin/console/content/models.html
   ```

1. 選取 **DAM更新資產工作流程**.
1. 按一下 **編輯**.
1. 如果 **DXML後續程式發起人** 元件存在，請確定自訂已同步。
1. 如果 **DXML後續程式發起人** 元件不存在，請執行以下步驟來插入它：

1. 按一下 **插入元件** \(負責AEM Guides後續處理，將此作為程式的最後一步\)。
1. 設定 **程式步驟** 詳細資料如下：

   **通用標籤**

   **標題：** DXML後續程式發起人

   **說明**：DXML後續處理啟動器步驟，此步驟將觸發用於已修改/已建立資產的DXML後續處理的Sling工作

   **「處理」標籤**

   - 選取 **DXML後續程式發起人**&#x200B;從 **程式** 下拉式清單

   - 選取 **處理常式前進**

   - 選取 **完成**

1. 按一下 **同步** 完成變更後於右上角顯示。 您將會收到成功通知。

   >[!NOTE]
   >
   > 重新整理並確認自訂變更和AEM Guides後處理步驟出現在最終工作流程模型中。

1. 一次 **DAM更新資產工作流程**&#x200B;已驗證，請檢查對應的啟動器設定。 若要這麼做，請前往AEM Workflow介面並開啟啟動器。

   ```http
   http://localhost:4502/libs/cq/workflow/content/console.html
   ```

   尋找下列兩個啟動器\（若有需要\）並進行變更\（應該為作用中\），其對應至 **DAM更新資產工作流程**：

1. 「 」的啟動器&#x200B;*節點已建立*「 for **DAM更新資產工作流程** — 適用於條件 `"jcr:content/jcr:mimeType!=video"`，萬用字元值應為：

   ```json
   /content/dam(/((?!/subassets|/translation_output).)*/)renditions/original
   ```

   - &#39;excludeList&#39;應該有 `"event-user-data:changedByWorkflowProcess"`.
   - 「 」的啟動器&#x200B;*節點已修改*「 for **DAM更新資產工作流程 —** 條件&quot;`jcr:content/jcr:mimeType!=video`&quot;，&#39;萬用字元&#39;值應該是：

   ```json
   /content/dam(/((?!/subassets|/translation_output).)*/)renditions/original
   ```

   - `excludeList` 應該有 `"event-user-data:changedByWorkflowProcess"`.

1. 升級完成後，請確定所有自訂/覆蓋圖均已驗證並更新，以符合新的應用程式程式碼。 以下提供一些範例：
   - 從/libs/fmditor/libsis覆寫的任何元件都應與新的產品程式碼進行比較，且更新應在/apps下方的覆寫檔案中完成。
   - 產品中使用的任何clientlib類別都應檢閱是否有變更。 任何覆寫的設定\（範例如下\）都應與最新的設定進行比較，以取得最新的功能：
   - elementmapping.xml
   - ui\_config.json\（可能已在資料夾設定檔中設定\）
   - 已修改 `com.adobe.fmdita.config.ConfigManager`
   - 檢查是否有任何自訂程式碼使用任何舊路徑\(如 [移轉對應](#id2244LE040XA) section\) — 應更新為新路徑，以便自訂也能如預期運作。
1. 閱讀最新版本中的任何新設定\(檢查 [發行說明](../release-info/release-notes-4.2.1.md)\)並檢視是否有任何功能受到影響，然後採取適當的動作。 例如使用4.0版中引進的「改善檔案和版本處理」，您需要為此啟用設定。

## 為現有內容建立索引以使用新尋找和取代的步驟：

執行以下步驟來索引現有內容，並在地圖層級使用新的尋找和取代文字：

- 確保 `damAssetLucene` 索引已完成。 視伺服器上呈現的資料量而定，最多可能需要幾個小時。 您可以透過檢查中重新索引欄位是否設定為false來確認重新索引已完成
  `http://<server:port>/oak:index/damAssetLucene`.  此外，如果您已在以下專案新增任何自訂： `damAssetLucene`，您可能需要再次套用這些變數。

- 對伺服器執行POST要求\（使用正確的驗證\） - `http://<server:port\>/bin/guides/map-find/indexing`. (選用：您可以傳遞地圖的特定路徑來編列索引，預設情況下，所有地圖都會編列索引\|\|例如： `https://<Server:port\>/bin/guides/map-find/indexing?paths=<map\_path\_in\_repository\>`)

- 您也可以傳遞根資料夾，為特定資料夾（及其子資料夾）的DITA map建立索引。 例如 `http://<server:port\>/bin/guides/map-find/indexing?root=/content/dam/test`。請注意，如果同時傳遞路徑引數和根引數，則只會考慮路徑引數。

- 此API將傳回jobId。 若要檢查作業的狀態，您可以傳送作業識別碼的GET要求至相同的端點 —  `http://<server:port\>/bin/guides/map-find/indexing?jobId=\{jobId\}`\(例如： `http://localhost:8080/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42`\)


- 工作完成後，上述GET要求將回應為成功，並提及是否有任何地圖失敗。 可以從伺服器記錄檔確認已成功編制索引的對應。


## 升級至4.3.0版 {#upgrade-version-4-3}

升級至4.3.0版須視目前AEM Guides的版本而定。 如果您是使用4.2或4.2.x版，則可以直接升級至4.3.0版。

>[!NOTE]
>
>後期處理和索引可能需要幾個小時。 我們建議您在非尖峰時段開始升級程式。

****必備條件****

在開始AEM Guides 4.3.0升級程式之前，請確定您擁有：

1. 已升級至AEM Guides 4.2或4.2.x版，並完成各自的安裝步驟。
1. 已關閉所有翻譯任務。



## 安裝4.3.0版

1. 從下載4.3.0版本套件 [Adobe軟體發佈入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).
1. 安裝4.3.0版本的套件。
1. 安裝套件後清除瀏覽器快取。
1. 升級 `ui_config.json` 來自的檔案 **XML編輯器設定** 索引標籤中的資料夾設定檔。


## 安裝4.3.0版之後

安裝AEM Guides後，您可以將適用於新安裝版本的各種設定合併到您的設定中。

## 後續處理現有內容以使用中斷連結報告的步驟


執行以下步驟後續處理現有內容並使用新的中斷連結報表：

1. （選用）如果系統中有超過100,000個dita檔案，請更新 `queryLimitReads` 在 `org.apache.jackrabbit.oak.query.QueryEngineSettingsService` 變更為較大的值（任何大於現有資產數的值，例如200,000），然後重新部署。

   | PID | 屬性索引鍵 | 屬性值 |
   |---|---|---|
   | org.apache.jackrabbit.oak.query.QueryEngineSettingsService | querylimitereads | 值： 200000 <br> 預設值： 100000 |

1. 執行下列API以對所有檔案執行後續處理：

   | 端點 | /bin/guides/reports/upgrade |
   |---|---|
   | 請求型別 | **POST**  此指令碼為POST請求，因此應透過Postman等代理程式執行。 |
   | 預期回應 | 此API將傳回jobId。 若要檢查作業的狀態，您可以將具有作業ID的GET請求傳送至相同的端點。<br> 範例URL： `http://<server:port>/bin/guides/reports/upgrade` |

   | 端點 | /bin/guides/reports/upgrade |
   |---|---|
   | 請求型別 | **GET** |
   | 引數 | jobId：傳遞從上一個post請求收到的jobId。 |
   | 預期回應 |  — 工作完成後，GET要求會成功回應。 <br>  — 如果發生錯誤，請和您的客戶成功團隊共用錯誤記錄以及API輸出。  <br>範例URL： `http://<server:port>/bin/guides/reports/upgrade?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678` |


1. 恢復為預設值或先前的現有值 `queryLimitReads` 如果您已在步驟1中加以變更。

**父級主題：**[&#x200B;下載並安裝](download-install.md)

