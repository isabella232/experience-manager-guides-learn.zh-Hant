---
title: 升級Adobe Experience Manager指南
description: 瞭解如何升級Adobe Experience Manager指南
source-git-commit: 629a3714e7b75af609238a506688da2674bf31cc
workflow-type: tm+mt
source-wordcount: '2750'
ht-degree: 1%

---


# 升級Adobe Experience Manager指南 {#id224MBE0M0XA}

>[!NOTE]
>
> 按照特定於產品許可版本的升級說明進行操作。

您可以將當前版本的AEM指南升級到4.2.1版
- 如果您使用的是4.1、4.1.x或4.2版，則可以直接升級到4.2.1版。
- 如果使用4.0版，則需要先升級到4.2版，然後再升級到4.2.1版。
- 如果使用3.8.5版，則需要先升級到4.0版，然後再升級到4.2版。
- 如果您的版本是3.8.5之前的版本，請參閱產品特定安裝指南AEM中的「升級指南」部分。

>[!NOTE]
>
> 必須先安AEM裝Service Pack，然後才能升AEM級Guides版本。

有關詳細資訊，請參閱以下步驟：

- [從3.8.5升級到4.0版](#id2256DK003E1)
- [升級到4.2版](#id22A3F500SXA)
- [升級到4.2.1版](#upgrade-version-4-2-1)


>[!IMPORTANT]
>
> 在開始升級之前，請進行完整的系統備份以避免資料丟失。

## 從3.8.5版升級到4.0版 {#id2256DK003E1}

如果使用的AEM是Guides 3.8.5版，則可以升級到4.0版的GuidesAEM。 使用升級功能，您不必卸載以前版本的指南AEM。

在運行進程之前，您必須完成某些任務。 以下子部分將指導您完成先決條件、報告生成和遷移過程。 此外，安裝AEMGuides 4.0版後，您可以根據客戶設定自定義各種配置。

>[!NOTE]
>
> 此升級過程僅適用於3.8.5版到4.0版。有關從3.4版或更高版本升級到3.8.5的過程，請參閱 *升級指AEM南* 產品特定安裝指南的 [幫助存檔頁面](https://helpx.adobe.com/xml-documentation-for-experience-manager/archive.html)。

****必備條件****

在啟動指南升AEM級過程之前，請確保：

1. 已導入開啟供審閱的主題中的審閱注釋。
1. 已關閉所有活動審閱。
1. 已關閉所有翻譯任務。
1. 卸載AEM在以前版本\（主要版本或修補程式版本\）的指南頂部安裝的任何指南熱修AEM復程式。

**安裝4.0版之前**

在安裝4.0版之前，請執行以下步驟：

1. 此時確AEM保「指南」在3.8.5版中。
1. 下載升級指令碼包。 為此，請在上搜索「XML Documentation解決方案4.0升級包」 [Adobe軟體分發門戶](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) 下載一個zip檔案。
1. 通過包管理器將AEM此包上載到並安裝此包。
1. 安裝升級軟體包後，按相同順序運行以下給定指令碼並按照給定說明操作：

**檢查升級相容性API**

此API旨在評估當前系統狀態，並報告是否可能進行升級。 要運行此指令碼，請觸發以下給定終結點：

|結束點|/bin/dxml/upgrade/3xto4x/report| |請求類型|**GET** 您可以使用Web瀏覽器，在該瀏覽器中，您以管理員AEM身份登錄到實例。| |預期響應| — 如果所有必需節點都可以移動，您將獲得通過的檢查。 <br> — 如果目標位置存在節點，您將收到相關錯誤。 清除儲存庫\(delete node /var/dxml\)並重新安裝升級包，然後再次觸發此終結點。 <br>**注：** 這不是常見錯誤，因為3.x參考線之前未使用目標AEM位置。 <br>  — 如果此指令碼未成功，請勿繼續，並向您的客戶成功團隊報告。|

**系統資料遷移API**

此API旨在遷移中所述的系統資料 [遷移映射](#id2244LE040XA) 的子菜單。

1. 如果Check升級相容性API失敗\（不繼續\），則不執行此指令碼。
1. 一旦Check升級相容性API返回成功，您就可以運行升級指令碼。

|結束點|/bin/dxml/upgrade/3xto4x| |請求類型|**POST** 此指令碼是POST請求，因此應通過Postman等代理執行。| |預期響應| — 遷移成功後，您可以安裝XML Documentation解決方案4.0版。<br> — 如果出現錯誤，請還原到最後一個檢查點，並與您的客戶成功團隊共用錯誤日誌和API輸出。|

**遷移映射**:上述API將源位置下的所有資料遷移到目標位置。

| 來源 | 目標 |
|------|------|
| /content/fmdita | /var/dxml |
| /content/dxml | /var/dxml |
| /etc/fmdita | /libs/fmdita |

## 安裝4.0版 {#id23598G006XA}

1. 僅在升級步驟成功時安裝4.0版。
1. 從下載4.0版軟體包 [Adobe軟體分發門戶](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html):

   - 如果使用UUID版本的軟體，請搜索「 4.0 UUID Release for AEM 6.5 for Solution for 6.5」。
   - 如果使用非UUID版本的軟體，請搜索「用於XML Documentation解決方案的4.0非UUID版本，AEM 6.5版」。
使用CRX包管理器將AEM包上載到現有伺服器實例\(s\)並安裝它。

   >[!NOTE]
   >
   > 等待所有系統元件啟動。

1. 安裝包後清除瀏覽器快取。
1. 如果在AEM Author實例上配置了調度程式，請執行以下步驟：
   - 確保在調度程式規則中處理以下內容：
   - URL模式/home/users/\*/preferences為白色。
   - 未快取URL模式/libs/cq/security/userinfo.json。
1. 清除調度程式快取\(清除任何 `clientlibs` 快取\)。

## 升級到4.2版 {#id22A3F500SXA}

升級到4.2版取決於當前版本的指南AEM。

如果您使用4.0、4.1或4.1.x版，則可以直接升級到4.2版。

****必備條件****

在啟動Guides 4.2AEM升級過程之前，請確保：

1. 已升AEM級到指南4.0、4.1或4.1.x版。
1. 已關閉所有翻譯任務。
1. 已將日誌級別更改為 **資訊** 為 `com.adobe.fmdita.translationservices.TranslationMapUpgradeScript` 類，並在新日誌檔案中追加這些日誌，例如， `logs/translation_upgrade.log.`

>[!NOTE]
>
> 您應關閉所有活動評論。 如果升級到4.2時未關閉審閱任務，則較舊的正在進行審閱任務將繼續讓用戶訪問較舊的審閱頁，而升級後建立的審閱任務將顯示功能的最新更新。

## 安裝4.2版 {#id2245IK0E0EV}

1. 從下載4.2版軟體包 [Adobe軟體分發門戶](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)。
1. 安裝4.2版軟體包。
1. 完成軟體包安裝後，請等待日誌中出現以下消息：

   `Completed the post deployment setup script`

   以上消息表示所有安裝步驟均已完成。

   如果遇到以下任何錯誤前置詞，請向客戶成功團隊報告：

   - 部署後安裝指令碼中出錯
   - 移植翻譯MAP時出現異常
   - 無法將屬性的轉換映射從v1埠到v2埠
1. 升級4.2版\（如果需要）發佈的氧連接器插件。
1. 安裝包後清除瀏覽器快取。
1. 繼續升級自定義項，如下一節中所詳述。

## 安裝4.2版之後 {#id2326F02004K}

>[!IMPORTANT]
>
> 升級的伺服器上未顯示高科技模板。 要在伺服器上包含高科技模板，可以複製：來源：/libs/fmdita/pdf/高科技目標：/content/dam/dita模板/pdf

安裝指南AEM後，可以將新安裝版本中適用的各種配置合併到安裝程式中。

>[!NOTE]
>
> 可以定制大壩更新資產模型。 因此，如果已進行了任何自定義，則我們需要將自定義項AEM和參考線同步到模型的工作副本中。

1. **DAM更新資產工作流\（後處理更改\）:**

1. 開啟URL:

   ```http
   http://localhost:4502/libs/cq/workflow/admin/console/content/models.html
   ```

1. 選擇 **DAM更新資產工作流**。
1. 按一下 **編輯**。
1. 如果 **DXML後進程啟動器** 元件已存在，請確保已同步自定義項。
1. 如果 **DXML後進程啟動器** 元件不存在，請執行以下步驟來插入它：

1. 按一下 **插入元件** \(負責將後AEM續處理作為流程中的最後一步\)。
1. 配置 **處理步驟** 具體如下：

   **常用頁籤**

   **標題：** DXML後進程啟動器

   **說明**:DXML後處理啟動器步驟，該步驟將觸發DXML後處理修改/建立的資產的Sling作業

   **「流程」頁籤**

   - 選擇 **DXML後進程啟動器**&#x200B;從 **進程** 下降

   - 選擇 **處理程式高級**

   - 選擇 **完成**

1. 按一下 **同步** 在右上角。 您將收到成功通知。

   >[!NOTE]
   >
   > 刷新並驗證自定義更改AEM和最終工作流模型中是否存在「指南」後處理步驟。

1. 一次 **DAM更新資產工作流**&#x200B;驗證後，檢查相應的啟動程式配置。 為此，請轉到「工作流」AEM介面和開放啟動程式。

   ```http
   http://localhost:4502/libs/cq/workflow/content/console.html
   ```

   查找並對以下兩個啟動器\（應處於活動狀態\）進行相應的更改 **DAM更新資產工作流**:

1. 「」的啟動程式&#x200B;*已建立節點*&quot; **DAM更新資產工作流** — 條件 `"jcr:content/jcr:mimeType!=video"`，「Globbing」值應為：

   ```json
   /content/dam(/((?!/subassets|/translation_output).)*/)renditions/original
   ```

   - 「excludeList」應具有 `"event-user-data:changedByWorkflowProcess"`。
   - 「」的啟動程式&#x200B;*節點已修改*&quot; **DAM更新資產工作流 —** 條件&quot;`jcr:content/jcr:mimeType!=video`&quot;
   - 
      - 「Globbing」值應為：

   ```json
   `"/content/dam(/((?!/subassets|/translation_output).)*/)renditions/original"`
   ```

   - 「excludeList」應具有 `"event-user-data:changedByWorkflowProcess"`。
1. 升級完成後，確保驗證和更新任何自定義/覆蓋以匹配新的應用程式碼。 以下是一些示例：
   - 應將從/libs/fmditaor/libs覆蓋的任何元件與新產品代碼進行比較，並應在下面/apps下覆蓋的檔案中完成更新。
   - 產品中使用的任何客戶端庫類別都應進行檢查，以查看是否有更改。 應將任何被覆蓋的配置\（下面的示例\）與最新的配置進行比較，以獲得最新的功能：
   - elementmapping.xml
   - ui\_config.json\(可能已在資料夾配置檔案中設定\
   - 修訂 `com.adobe.fmdita.config.ConfigManager`
   - 檢查任何自定義代碼是否使用任何舊路徑\(如 [遷移映射](#id2244LE040XA) 部分\) — 應更新到新路徑，以便自定義也按預期工作。
1. 閱讀有關當前版本中帶來的任何新配置\(檢查 [發行說明](../release-info/release-notes-4.2.md)\)並查看是否影響任何功能，然後採取相應的操作。 例如，可以使用4.0版中引入的「改進的檔案和版本處理」，您需要為其啟用配置。

## 為現有內容編製索引以使用新查找和替換的步驟：

執行以下步驟為現有內容編製索引，並在映射級別使用新查找和替代文字：

- 向伺服器運行POST請求\（使用正確的身份驗證\） —  `http://<server:port\>/bin/guides/map-find/indexing`。 \(可選：您可以傳遞映射的特定路徑以對其進行索引，預設情況下，所有映射都將被索引\|\|，例如： `https://<Server:port\>/bin/guides/map-find/indexing?paths=<map\_path\_in\_repository\>`\)

- API將返回jobId。 要檢查作業的狀態，您可以將具有作業ID的GET請求發送到同一端點 —  `http://<server:port\>/bin/guides/map-find/indexing?jobId=\{jobId\}`\(例如： `http://localhost:8080/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42`\)

- 作業完成後，上述GET請求將成功響應，並在任何映射失敗時提及。 可以從伺服器日誌中確認成功索引的映射。

## 升級到4.2.1版 {#upgrade-version-4-2-1}

升級到4.2.1版取決於當前版本的指南AEM。

如果您使用4.1或4.1.x或4.2版，則可以直接升級到4.2.1版。

>[!NOTE]
>
>後處理和索引可能需要幾個小時。 建議您在非高峰時段啟動升級過程。

****必備條件****

在啟動Guides AEM 4.2.1升級過程之前，請確保：

1. 已升AEM級到指南4.1、4.1.x或4.2版。
1. 已關閉所有翻譯任務。
1. 已將日誌級別更改為 **資訊** 為 `com.adobe.fmdita.translationservices.TranslationMapUpgradeScript` 類，並在新日誌檔案中追加這些日誌，例如， `logs/translation_upgrade.log.`

>[!NOTE]
>
> 您應關閉所有活動評論。 如果升級到4.2時未關閉審閱任務，則較舊的正在進行審閱任務將繼續讓用戶訪問較舊的審閱頁，而升級後建立的審閱任務將顯示功能的最新更新。

## 安裝4.2.1版

1. 從下載4.2.1版軟體包 [Adobe軟體分發門戶](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)。
1. 安裝4.2.1版軟體包。
1. 您可以選擇HIT觸發器以啟動轉換映射升級作業。 有關詳細資訊，請參閱 [通過Servlet啟用指令碼觸發器](#enable-trigger-serverlet)。


1. 完成軟體包安裝後，請等待日誌中出現以下消息：

   `Completed the post deployment setup script`

   以上消息表示所有安裝步驟均已完成。

   如果遇到以下任何錯誤前置詞，請向客戶成功團隊報告：

   - 部署後安裝指令碼中出錯
   - 移植翻譯MAP時出現異常
   - 無法將屬性的轉換映射從v1埠到v2埠
1. 升級4.2版\（如果需要）發佈的氧連接器插件。
1. 安裝包後清除瀏覽器快取。
1. 繼續升級自定義項，如下一節中所詳述。

### 通過Servlet啟用指令碼觸發器{#enable-trigger-serverlet}

POST:

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

在上述響應JSON中，鍵 `lockNodePath` 保存指向在儲存庫中建立的指向提交作業的節點的路徑。 作業完成後，系統會自動刪除它，然後，您可以參考此節點瞭解作業的當前狀態。

示例日誌：以下是觸發指令碼後將出現在日誌檔案中的日誌示例。

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

查找 `com.adobe.fmdita.translationservices.TranslationMapUpgradeScript Completed porting of translation map from V1 to V2` 和 `com.adobe.fmdita.xmltranslation.ots.TranslationMapUpgradeOTS Completed the thread to upgrade translation map from V1 to V2` 之後再執行後續步驟。



## 安裝4.2.1版後

>[!IMPORTANT]
>
> 升級的伺服器上未顯示高科技模板。 要在伺服器上包含高科技模板，可以複製：來源：/libs/fmdita/pdf/高科技目標：/content/dam/dita模板/pdf

安裝指南AEM後，可以將新安裝版本中適用的各種配置合併到安裝程式中。

>[!NOTE]
>
> 可以定制大壩更新資產模型。 因此，如果已進行了任何自定義，則我們需要將自定義項AEM和參考線同步到模型的工作副本中。

1. **DAM更新資產工作流\（後處理更改\）:**

1. 開啟URL:

   ```http
   http://localhost:4502/libs/cq/workflow/admin/console/content/models.html
   ```

1. 選擇 **DAM更新資產工作流**。
1. 按一下 **編輯**。
1. 如果 **DXML後進程啟動器** 元件已存在，請確保已同步自定義項。
1. 如果 **DXML後進程啟動器** 元件不存在，請執行以下步驟來插入它：

1. 按一下 **插入元件** \(負責將後AEM續處理作為流程中的最後一步\)。
1. 配置 **處理步驟** 具體如下：

   **常用頁籤**

   **標題：** DXML後進程啟動器

   **說明**:DXML後處理啟動器步驟，該步驟將觸發DXML後處理修改/建立的資產的Sling作業

   **「流程」頁籤**

   - 選擇 **DXML後進程啟動器**&#x200B;從 **進程** 下降

   - 選擇 **處理程式高級**

   - 選擇 **完成**

1. 按一下 **同步** 在右上角。 您將收到成功通知。

   >[!NOTE]
   >
   > 刷新並驗證自定義更改AEM和最終工作流模型中是否存在「指南」後處理步驟。

1. 一次 **DAM更新資產工作流**&#x200B;驗證後，檢查相應的啟動程式配置。 為此，請轉到「工作流」AEM介面和開放啟動程式。

   ```http
   http://localhost:4502/libs/cq/workflow/content/console.html
   ```

   查找並對以下兩個啟動器\（應處於活動狀態\）進行相應的更改 **DAM更新資產工作流**:

1. 「」的啟動程式&#x200B;*已建立節點*&quot; **DAM更新資產工作流** — 條件 `"jcr:content/jcr:mimeType!=video"`，「Globbing」值應為：

   ```json
   /content/dam(/((?!/subassets|/translation_output).)*/)renditions/original
   ```

   - 「excludeList」應具有 `"event-user-data:changedByWorkflowProcess"`。
   - 「」的啟動程式&#x200B;*節點已修改*&quot; **DAM更新資產工作流 —** 條件&quot;`jcr:content/jcr:mimeType!=video`&quot;,&quot;Globbing&quot;值應為：

   ```json
   `"/content/dam(/((?!/subassets|/translation_output).)*/)renditions/original"`
   ```

   - `excludeList` 應該 `"event-user-data:changedByWorkflowProcess"`。


1. 升級完成後，確保驗證和更新任何自定義/覆蓋以匹配新的應用程式碼。 以下是一些示例：
   - 應將從/libs/fmditaor/libs覆蓋的任何元件與新產品代碼進行比較，並應在下面/apps下覆蓋的檔案中完成更新。
   - 產品中使用的任何客戶端庫類別都應進行檢查，以查看是否有更改。 應將任何被覆蓋的配置\（下面的示例\）與最新的配置進行比較，以獲得最新的功能：
   - elementmapping.xml
   - ui\_config.json\(可能已在資料夾配置檔案中設定\
   - 修訂 `com.adobe.fmdita.config.ConfigManager`
   - 檢查任何自定義代碼是否使用任何舊路徑\(如 [遷移映射](#id2244LE040XA) 部分\) — 應更新到新路徑，以便自定義也按預期工作。
1. 閱讀有關當前版本中帶來的任何新配置\(檢查 [發行說明](../release-info/release-notes-4.2.1.md)\)並查看是否影響任何功能，然後採取相應的操作。 例如，可以使用4.0版中引入的「改進的檔案和版本處理」，您需要為其啟用配置。

## 為現有內容編製索引以使用新查找和替換的步驟：

執行以下步驟為現有內容編製索引，並在映射級別使用新查找和替代文字：

- 確保 `damAssetLucene` 索引已完成。 根據伺服器上存在的資料量，可能需要幾個小時。 您可以通過檢查在中重新索引欄位是否設定為false來確認重新索引已完成
   `http://<server:port>/oak:index/damAssetLucene`.  此外，如果在 `damAssetLucene`，可能需要再次應用。

- 向伺服器運行POST請求\（使用正確的身份驗證\） —  `http://<server:port\>/bin/guides/map-find/indexing`。 (可選：您可以傳遞映射的特定路徑以對其進行索引，預設情況下，所有映射都將被索引\|\|，例如： `https://<Server:port\>/bin/guides/map-find/indexing?paths=<map\_path\_in\_repository\>`)

- 您還可以傳遞根資料夾以為特定資料夾（及其子資料夾）的DITA映射編製索引。 比如說， `http://<server:port\>/bin/guides/map-find/indexing?root=/content/dam/test`。 請注意，如果同時傳遞路徑參數和根參數，則只考慮路徑參數。

- API將返回jobId。 要檢查作業的狀態，您可以將具有作業ID的GET請求發送到同一端點 —  `http://<server:port\>/bin/guides/map-find/indexing?jobId=\{jobId\}`\(例如： `http://localhost:8080/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42`\)


- 作業完成後，上述GET請求將成功響應，並在任何映射失敗時提及。 可以從伺服器日誌中確認成功索引的映射。

**父主題：**[&#x200B;下載並安裝](download-install.md)

