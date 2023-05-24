---
title: 設定和自訂工作流程
description: 瞭解如何設定和自訂工作流程
source-git-commit: 9fe396dcfd2e3570ec386c958d7d4efdb4d608e5
workflow-type: tm+mt
source-wordcount: '1781'
ht-degree: 3%

---


# 設定和自訂工作流程 {#id181AI0OJ0RO}

工作流程可讓您自動化Adobe Experience Manager \(AEM\)活動。 工作流程包含一系列以特定順序執行的步驟。 您可以定義要在每個步驟上執行的不同活動。 例如，在建立主題稽核時，您可以傳送電子郵件通知給群組中的所有稽核者。 或者，在輸出產生任務完成時，傳送通知給發佈者。

如需AEM工作流程的詳細資訊，請參閱：

- [管理工作流程](https://helpx.adobe.com/tw/experience-manager/6-5/sites/administering/using/workflows.html)

- 套用和參與工作流程： [使用工作流程](https://helpx.adobe.com/tw/experience-manager/6-5/sites/authoring/using/workflows.html).

- 建立工作流程模型和擴充工作流程功能： [開發和擴充工作流程](https://helpx.adobe.com/tw/experience-manager/6-5/sites/developing/using/workflows.html).

- 改善使用大量伺服器資源的工作流程效能： [並行工作流程處理](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/configuring-performance.html#ConfiguringforPerformance).


本主題中的各節將逐步引導您瞭解AEM Guides隨附的預設工作流程中可以進行的各種自訂。

## 自訂稽核工作流程 {#id176NE0C00HS}

每個組織的內容製作團隊都會以特定方式運作，以符合其業務需求。 某些組織設有專屬的編輯人員，而其他組織則可設有自動編輯稽核系統。 例如，在組織中，典型的撰寫和發佈工作流程可能包括以下任務 — 每當作者完成編寫內容時，就會自動將其交給稽核者，當稽核完成時，它會交給發佈者，以生成最終輸出。 在AEM中，您對內容和資產執行的活動可以程式形式合併，並對應至AEM工作流程。 如需AEM工作流程的詳細資訊，請參閱 [管理工作流程](https://helpx.adobe.com/tw/experience-manager/6-5/sites/administering/using/workflows.html) 在AEM檔案中。

AEM Guides可讓您自訂預設的稽核工作流程。 您可以搭配其他撰寫或發佈工作流程，使用下列四個自訂檢閱相關流程。

- **建立評論**：此程式會準備建立稽核任務所需的中繼資料。 例如，它會指派稽核許可權給稽核者、將主題的狀態設定為稽核中、設定稽核時間表等。 在四個處理程式中，這是唯一必須包含在自訂工作流程中的強制處理程式。 在工作流程中，您可以選擇包含或排除其他三個處理序。

- **指派稽核任務**：此程式會建立稽核任務並將任務通知傳送給發起人和稽核者。

- **傳送稽核電子郵件**：此程式會將稽核電子郵件傳送給發起人和稽核者。

- **將工作排程為關閉檢閱**：此程式可確保稽核程式在到達截止日期時完成。


建立自訂稽核工作流程時，第一個任務是設定「建立稽核」流程所需的必要中繼資料。 若要這麼做，您可以建立ECMA指令碼。 指派中繼資料的ECMA指令碼範例如下：

```json
var workflowdata=workItem.getWorkflowData();
workflowdata.getMetaDataMap().put("initiator","admin");
workflowdata.getMetaDataMap().put("operation","AEM_REVIEW");
workflowdata.getMetaDataMap().put("orgTopics","/content/dam/xml-solution/review.xml");
workflowdata.getMetaDataMap().put("payloadJson","{\"base\":\"/content/dam/xml-solution\",\"asset\":[\"/content/dam/xml-solution/review.xml\"],\"referrer\":\""}");
workflowdata.getMetaDataMap().put("deadline","2017-06-27T13:19:00.000+05:30");
workflowdata.getMetaDataMap().put("title","Review through custom workflow");
workflowdata.getMetaDataMap().put("description","Initiate this review process using the AEM workflow");
workflowdata.getMetaDataMap().put("assignee","user-one", "user-two");
workflowdata.getMetaDataMap().put("status","1");
workflowdata.getMetaDataMap().put("projectPath","/content/projects/review");
workflowdata.getMetaDataMap().put("startTime", System.currentTimeMillis());
```

您可在以下位置建立此指令碼： `/etc/workflows/scripts` 節點。 下表說明此ECMA命令檔所指派的特性：

| 屬性 | 類型 | 說明 |
|--------|----|-----------|
| `initiator` | 字串 | 起始稽核任務之使用者的使用者ID。 |
| `operation` | 字串 | 設定為的靜態值 `AEM_REVIEW`. |
| `orgTopics` | 字串 | 共用供檢閱的主題路徑。 指定多個以逗號分隔的主題。 |
| `payloadJson` | json物件 | 指定下列值：<br> - `base`：包含已傳送以供檢閱之主題的父資料夾路徑。<br>- `asset`：傳送以供檢閱的主題路徑。 <br>- `referrer`：保留空白。 |
| `deadline` | 字串 | 指定時間 `yyyy-MM-dd'T'HH:mm:ss.SSSXXX` 格式。 |
| `title` | 字串 | 輸入稽核任務的標題。 |
| `description` | 字串 | 輸入複查工作的說明。 |
| `assignee` | 字串 | 要傳送主題以供檢閱之使用者的使用者ID。 |
| `status` | 整數 | 設定為1的靜態值。 |
| `startTime` | 長整數 | 使用 `System.currentTimeMillis()` 函式以取得目前系統時間。 |

建立指令碼後，請在工作流程中呼叫建立檢閱程式前呼叫它。 然後，根據您的需求，您可以呼叫其他稽核工作流程流程。

### 從清除設定中移除複查工作流程

若要改善工作流程引擎效能，您可以定期從AEM存放庫中清除已完成的工作流程執行個體。 如果您使用預設的AEM設定，則會在特定時段後清除所有已完成的工作流程執行個體。 這也會導致所有稽核工作流程從AEM存放庫清除。

您可以從自動永久刪除組態中移除稽核工作流程模型\(information\)，以防止稽核工作流程自動永久刪除。 您需要使用 **AdobeGranite工作流程清除設定** 以從自動永久刪除清單中移除「稽核工作流程模型」。

在 **AdobeGranite工作流程清除設定**，請確定您至少列出一個可以安全清除的工作流程。 例如，您可以使用AEM Guides建立的下列任何工作流程：

- /etc/workflow/models/publishditamap/jcr：content/model
- /etc/workflow/models/post-dita-project-creation-tasks/ jcr：content/model

在中新增工作流程 **AdobeGranite工作流程清除設定** 確保AEM只會清除設定中列出的工作流程。 這可防止AEM清除稽核工作流程資訊。

如需有關設定的詳細資訊 **AdobeGranite工作流程清除設定**，請參閱 *管理工作流程例項* 在AEM檔案中。

### 自訂電子郵件範本

許多AEM Guides工作流程會使用電子郵件通知。 例如，如果您啟動稽核工作，則會傳送電子郵件通知給稽核者。 不過，為確保電子郵件通知已傳送，您必須在AEM中啟用此功能。 若要在AEM中啟用電子郵件通知，請參閱文章 [設定電子郵件通知](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/previous-updates/aem-previous-versions.html?lang=zh-Hant) 在AEM檔案中。

AEM Guides包含一組您可自訂的電子郵件範本。 執行以下步驟來自訂這些範本：

1. 登入AEM並開啟CRXDE Lite模式。

1. 在「瀏覽」標籤中，移至下列位置：

   `/libs/fmdita/mail`

   >[!NOTE]
   >
   > 請勿讓預設組態檔案中的任何自訂都可在 ``libs`` 節點。 您必須建立 ``libs`` 中的節點 ``apps`` 節點並更新 ``apps`` 僅限節點。

1. 郵件資料夾包含下列可自訂的範本：

   | 範本檔案名稱 | 說明 |
   |-----------------|-----------|
   | closereview.html | 此電子郵件範本在評論任務關閉時使用。 |
   | createreview.html | 建立新稽核任務時會使用此電子郵件範本。 |
   | reviewapproval.css | 此CSS檔案包含電子郵件範本的樣式。 |


## 自訂輸出後產生工作流程 {#id17A6GI004Y4}

AEM Guides可讓您靈活地指定輸出後產生工作流程。 您可以在使用AEM Guides產生的輸出上執行一些後處理任務。 例如，您可能想要在產生的AEM Site輸出上套用一些CQ標籤，或在PDF輸出上設定某些屬性，或者您可能想要在產生輸出後向一組使用者傳送電子郵件。

您可以建立新的工作流程模型，以用作輸出後產生工作流程。 觸發輸出後產生工作流程時，輸出產生工作流程會透過工作流程中繼資料對應分享內容資訊，您可以使用這些資訊對產生的輸出執行處理。 下表說明作為中繼資料共用的內容資訊：

| 屬性 | 類型 | 說明 |
|--------|----|-----------|
| ``outputName`` | 字串 | 用來產生輸出的輸出預設集名稱。 |
| `generatedPath` | 字串 | DAM中儲存所產生輸出的路徑。 |
| `outputType` | com.adobe.fmdita.output.OutputType | 輸出預設集的型別。 |
| `outputTitle` | 字串 | 輸出預設集的標題。 |
| `outputHistoryPath` | 字串 | 歷史記錄節點的存放庫路徑。 |
| `isSuccess` | 布林值 | 描述輸出產生程式最終狀態（成功或失敗）的旗標。 |
| `logPath` | 字串 | DAM中儲存輸出產生記錄的路徑。 |
| `generatedTime` | 長整數 | 觸發輸出產生程式的時間。 |
| `initiator` | 字串 | 觸發輸出產生工作流程的使用者的使用者ID。 |

若要使用輸出產生中繼資料，您可以建立ECMA指令碼或OSGi套件。 使用中繼資料的ECMA指令碼範例如下：

>[!NOTE]
>
> 您可在以下位置建立此指令碼： ``/etc/workflows/scripts`` 節點。

```json
var session = workflowSession.getSession(); // Obtain session object to read/write the repository.
var payload = workItem.getWorkflowData().getPayload().toString(); // Get the workflow payload (the ditamap file on which the generation was triggered)
var metadata = workItem.getWorkflowData().getMetaDataMap(); // Get the workflow metadata object
var generatedPath = metadata.get("generatedPath"); // supplied by AEM Guides
var username = metadata.get("initiator"); // supplied by AEM Guides
var successful = metadata.get("isSuccess"); // supplied by AEM Guides
var title = metadata.get("outputTitle"); // supplied by AEM Guides
var subject = "Output Generation Finished";
var message = "Generation of output " + title + " just finished " + 
(successful ? "successfully. " : "unsuccessfully. ");
    message += "It was triggered by " + username;    
if (successful) {
    message += "<br/><br/>The path to the generated output is " + 
generatedPath;
}
/*
    MailerAPI.sendMail("dl-docs-authors", subject, message);
*/
```

建立指令碼後，請呼叫工作流程中的自訂指令碼。 然後，根據您的需求，您可以呼叫其他工作流程程式。 設計好自訂工作流程後，請呼叫 *完成產生貼文* 作為工作流程程式的最後一個步驟。 此 *完成產生貼文* 步驟可確保輸出產生任務的狀態更新為 *已完成* 輸出產生程式完成時。 建立自訂輸出後產生工作流程後，您可以使用任何輸出產生預設集進行設定。 在中選取所需的工作流程 *執行後期產生工作流程* 必要預設集的屬性。 當您使用已設定的輸出預設集執行輸出產生任務時，任務狀態\（在「輸出」標籤中\）會變更為 *後處理*.

## 自訂更新資產工作流程 {#id18C3D0I0B5Z}

根據預設， *DAM更新資產* 工作流程會在您建立或更新任何AEM資產\（XML或非XML\）時觸發。 例如，當您建立或更新主題時， *DAM更新資產* 工作流程會執行。 此 *DAM更新資產* 工作流程會嘗試從「資產」擷取相關中繼資料。 現成可用 *資產更新工作流程* 沒有任何步驟可從DITA檔案和 *DAM更新資產* 工作流程在執行時會產生許多記錄。 如果您想避免額外的記錄，可以設定工作流程以略過處理所有XML檔案。

執行以下步驟來自訂 *DAM更新資產* 工作流程：

1. 開啟 **工作流程啟動器** 頁面。

   存取「工作流程啟動器」頁面的預設URL為：

   ```http
   http://<server name>:<port>/libs/cq/workflow/admin/console/content/launchers.html
   ```

1. 從工作流程啟動器清單中，開啟 **DAM更新資產** 工作流程。

1. 使用下列運算式新增條件：

   ```json
   jcr:content/metadata/dc:format!=application/xml
   ```

1. 按一下 **儲存並關閉**


## 設定後處理XML工作流程 {#id18CJB03J0Y4}

AEM Guides會建立一系列工作流程，讓您在AEM中使用DITA內容。 例如，有些工作流程會在您上傳DITA內容或更新現有內容時執行。 這些工作流程會剖析DITA檔案並執行各種工作，例如設定中繼資料、將預設輸出預設集新增到新的DITA map，以及其他相關工作。

>[!NOTE]
>
> 若要自訂或擴充預設的後處理工作流程，您可以使用 *Adobe Experience Manager Guides的API參考*.

下列屬性控管AEM Guides執行後期處理工作流程的方式：

>[!NOTE]
>
> 您可透過Web主控台存取下列屬性： http://&lt;server name=&quot;&quot;>：&lt;port>/system/console/configMgr。

| 屬性 | 組合包名稱 | 說明 |
|--------|-----------|-----------|
| 動態輸出 | `com.adobe.fmdita.postprocess.PostProcessObservation` | 對於尚未執行後續處理的所有檔案，它會透過剖析主題檔案來擷取傳出參考。 建議停用此選項，因為如果要處理的檔案數量很大，此選項可能會讓系統過載。 |
| 後處理執行緒 | `com.adobe.fmdita.config.ConfigManager` | 設定用於後置處理工作流程的後置處理執行緒數目。 <br>預設值為 1。 |

