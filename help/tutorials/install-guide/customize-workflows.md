---
title: 配置和自定義工作流
description: 瞭解如何配置和自定義工作流
source-git-commit: 9fe396dcfd2e3570ec386c958d7d4efdb4d608e5
workflow-type: tm+mt
source-wordcount: '1781'
ht-degree: 3%

---


# 配置和自定義工作流 {#id181AI0OJ0RO}

工作流使您能夠自動執行Adobe Experience Manager\AEM\活動。 工作流由一系列按特定順序執行的步驟組成。 您可以定義要在每個步驟上執行的不同活動。 例如，建立主題審閱時，您可以向組中的所有審閱者發送電子郵件通知。 或者，在輸出生成任務完成時向發佈者發送通知。

有關中工作流的詳細信AEM息，請參閱：

- [管理工作流程](https://helpx.adobe.com/tw/experience-manager/6-5/sites/administering/using/workflows.html)

- 應用和參與工作流： [使用工作流](https://helpx.adobe.com/tw/experience-manager/6-5/sites/authoring/using/workflows.html)。

- 建立工作流模型和擴展工作流功能： [開發和擴展工作流](https://helpx.adobe.com/tw/experience-manager/6-5/sites/developing/using/workflows.html)。

- 提高使用大量伺服器資源的工作流的效能： [併發工作流處理](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/configuring-performance.html#ConfiguringforPerformance)。


本主題中的各節將引導您完成在《指南》中提供的預設工作流中可進行的各種自AEM定義。

## 自定義審閱工作流 {#id176NE0C00HS}

每個組織的內容創作團隊都以特定方式工作以滿足其業務需求。 有些組織有專門的編輯，而另一些組織則可以建立自動編輯審查系統。 例如，在組織中，典型的創作和發佈工作流可能包括諸如以下任務：每當作者完成創作內容時，它會自動轉到審閱者，在審閱完成後，它將轉到發佈者以生成最終輸出。 在AEM中，您對內容和資產所執行的操作可以以流程的形式組合，並映射到工AEM作流。 有關中工作流的詳細信AEM息，請參見 [管理工作流](https://helpx.adobe.com/tw/experience-manager/6-5/sites/administering/using/workflows.html) 的上AEM界。

使用AEM參考線可以自定義預設審閱工作流。 您可以將以下四個與審閱相關的自定義流程與其他創作或發佈工作流一起使用。

- **建立審閱**:此進程準備建立審閱任務所需的元資料。 例如，它將為審閱者分配審閱權限、將要審閱的主題的狀態設定為、設定審閱時間表等。 在四個流程中，這是自定義工作流中必須包含的唯一強制流程。 在工作流中，您可以選擇包括或排除其他三個進程。

- **分配審閱任務**:此進程將建立審閱任務，並將任務通知發送給啟動器和審閱器。

- **發送審閱電子郵件**:此過程將審閱電子郵件發送給啟動器和審閱者。

- **計畫要關閉審閱的作業**:此過程確保審核過程在截止時間後完成。


建立自定義審閱工作流時，第一個任務是設定「建立審閱」流程所需的元資料。 為此，可以建立ECMA指令碼。 下面提供了分配元資料的ECMA指令碼示例：

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

可以在 `/etc/workflows/scripts` 的下界。 下表介紹了此ECMA指令碼所分配的屬性：

| 屬性 | 類型 | 說明 |
|--------|----|-----------|
| `initiator` | 字串 | 啟動審閱任務的用戶的用戶ID。 |
| `operation` | 字串 | 靜態值集為 `AEM_REVIEW`。 |
| `orgTopics` | 字串 | 要共用以供審閱的主題的路徑。 指定多個以逗號分隔的主題。 |
| `payloadJson` | JSON對象 | 指定以下值：<br> - `base`:包含已發送以供審閱的主題的父資料夾的路徑。<br>- `asset`:已發送以供審閱的主題的路徑。 <br>- `referrer`:留空。 |
| `deadline` | 字串 | 指定時間 `yyyy-MM-dd'T'HH:mm:ss.SSSXXX` 的子菜單。 |
| `title` | 字串 | 輸入審閱任務的標題。 |
| `description` | 字串 | 輸入複查任務的說明。 |
| `assignee` | 字串 | 要向其發送主題\(s\)以供審閱的用戶的用戶ID。 |
| `status` | 整數 | 靜態值設定為1。 |
| `startTime` | 長整數 | 使用 `System.currentTimeMillis()` 函式獲取當前系統時間。 |

建立指令碼後，在調用工作流中的「建立審閱」進程之前先調用它。 然後，根據您的要求，您可以調用其它審閱工作流進程。

### 從清除配置中刪除審閱工作流

要提高工作流引擎效能，您可以定期從儲存庫中清除已完成的工作AEM流實例。 如果使用預設配AEM置，則所有已完成的工作流實例將在特定時間段後進行清理。 這還會導致從儲存庫清除所有審閱工作AEM流。

通過從自動清除配置中刪除審閱工作流模型\（資訊\），可以阻止審閱工作流自動清除。 您需要使用 **Adobe花崗岩工作流清除配置** 將審閱工作流模型從自動清除清單中移除。

在 **Adobe花崗岩工作流清除配置**，確保列出至少一個可以安全清除的工作流。 例如，可以使用「參考線」建立的以下任何工AEM作流：

- /etc/workflow/models/publishditamap/jcr：內容/模型
- /etc/workflow/models/post-dita-project-creation-tasks/ jcr:content/model

在 **Adobe花崗岩工作流清除配置** 確保僅AEM清除配置中列出的工作流。 這會阻AEM止清除審閱工作流資訊。

有關配置的詳細資訊 **Adobe花崗岩工作流清除配置**，請參閱 *管理工作流實例* 的上AEM界。

### 自定義電子郵件模板

許多「指南」AEM工作流都使用電子郵件通知。 例如，如果您啟動審閱任務，則會向審閱者發送電子郵件通知。 但是，要確保發送電子郵件通知，您必須在中啟用此功AEM能。 要在中啟用電子郵件通AEM知，請參閱文章 [配置電子郵件通知](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/previous-updates/aem-previous-versions.html?lang=zh-Hant) 的上AEM界。

指AEM南包含一組可自定義的電子郵件模板。 執行以下步驟來定制這些模板：

1. 登錄並AEM開啟CRXDE Lite模式。

1. 在「導航」頁籤中，轉到以下位置：

   `/libs/fmdita/mail`

   >[!NOTE]
   >
   > 請勿在中的預設配置檔案中進行任何自定義 ``libs`` 的下界。 必須建立 ``libs`` 中的 ``apps`` 節點，並更新 ``apps`` 僅節點。

1. 郵件資料夾包含以下可自定義模板：

   | 模板檔案名 | 說明 |
   |-----------------|-----------|
   | closereview.html | 此電子郵件模板在審閱任務關閉時使用。 |
   | createreview.html | 建立新審閱任務時使用此電子郵件模板。 |
   | reviewapproval.css | 此CSS檔案包含電子郵件模板的樣式。 |


## 自定義輸出後生成工作流 {#id17A6GI004Y4}

指AEM南使您可以靈活地指定輸出後生成工作流。 您可以對使用「參考線」生成的輸出執行一些後處理AEM任務。 例如，您可能希望在生成的AEMSite輸出上應用某些CQ標籤，或在PDF輸出上設定某些屬性，或者在生成輸出後可能希望向一組用戶發送電子郵件。

您可以建立新工作流模型以用作輸出後生成工作流。 當觸發輸出後生成工作流時，輸出生成工作流通過工作流元資料映射共用上下文資訊，您可以使用這些資訊對生成的輸出執行處理。 下表描述了作為元資料共用的上下文資訊：

| 屬性 | 類型 | 說明 |
|--------|----|-----------|
| ``outputName`` | 字串 | 用於生成輸出的輸出預設的名稱。 |
| `generatedPath` | 字串 | DAM中儲存所生成輸出的路徑。 |
| `outputType` | com.adobe.fmdita.output.OutputType | 輸出預設的類型。 |
| `outputTitle` | 字串 | 輸出預設的標題。 |
| `outputHistoryPath` | 字串 | 歷史記錄節點的儲存庫路徑。 |
| `isSuccess` | 布林值 | 描述輸出生成過程的最終狀態的標誌 — 成功或失敗。 |
| `logPath` | 字串 | 保存輸出生成日誌的DAM中的路徑。 |
| `generatedTime` | 長整數 | 觸發輸出生成過程的時間。 |
| `initiator` | 字串 | 觸發輸出生成工作流的用戶的用戶ID。 |

要利用輸出生成元資料，可以建立ECMA指令碼或OSGi捆綁包。 下面提供了使用元資料的ECMA指令碼示例：

>[!NOTE]
>
> 可以在 ``/etc/workflows/scripts`` 的下界。

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

建立指令碼後，請在工作流中調用自定義指令碼。 然後，根據您的要求，您可以調用其他工作流進程。 設計完自定義工作流後，請致電 *完成後期生成* 作為工作流進程的最後一步。 的 *完成後期生成* 步驟確保輸出生成任務的狀態更新為 *已完成* 完成輸出生成過程。 建立自定義輸出後生成工作流後，可以使用任何輸出生成預設對其進行配置。 在 *運行生成後工作流* 所需預設的屬性。 使用配置的輸出預設運行輸出生成任務時，任務狀態\（在「輸出」頁籤\中）將更改為 *後處理*。

## 自定義更新資產工作流 {#id18C3D0I0B5Z}

預設情況下， *DAM更新資產* 建立或更新任何資AEM產\（XML或非XML\）時都會觸發工作流。 例如，建立或更新主題時， *DAM更新資產* 將執行工作流。 的 *DAM更新資產* 工作流嘗試從「資產」中提取相關元資料。 開箱即用 *資產更新工作流* 沒有從DITA檔案中提取任何相關元資料的任何步驟， *DAM更新資產* 工作流在執行時生成大量日誌。 如果要避免額外的日誌，可以配置工作流以跳過所有XML檔案的處理。

執行以下步驟來自定義 *DAM更新資產* 工作流：

1. 開啟 **工作流啟動程式** 的子菜單。

   訪問「工作流啟動程式」頁的預設URL為：

   ```http
   http://<server name>:<port>/libs/cq/workflow/admin/console/content/launchers.html
   ```

1. 從工作流啟動器清單中，開啟 **DAM更新資產** 工作流。

1. 添加具有以下表達式的條件：

   ```json
   jcr:content/metadata/dc:format!=application/xml
   ```

1. 按一下 **保存並關閉**


## 配置後處理XML工作流 {#id18CJB03J0Y4}

指AEM南會建立一組工作流，這些工作流允許您在中處理DITA內AEM容。 例如，在上載DITA內容或更新現有內容時，會執行一些工作流。 這些工作流會分析DITA文檔並執行各種任務，如設定元資料、將預設輸出預設添加到新DITA映射以及其他相關任務。

>[!NOTE]
>
> 要自定義或擴展預設的後處理工作流，可以使用中介紹的後處理事件處理程式 *Adobe Experience Manager指南的API參考*。

以下屬性控AEM制輔助線執行後處理工作流的方式：

>[!NOTE]
>
> 可通過Web控制台訪問以下屬性：http://&lt;server name=&quot;&quot;>:&lt;port>/system/console/configMgr。

| 屬性 | 組合包名稱 | 說明 |
|--------|-----------|-----------|
| 動態輸出 | `com.adobe.fmdita.postprocess.PostProcessObservation` | 對於尚未執行後處理的所有檔案，它通過分析主題檔案來檢索傳出引用。 建議禁用此選項，因為如果要處理的檔案數量很大，它可能會使系統超載。 |
| 後處理線程 | `com.adobe.fmdita.config.ConfigManager` | 設定用於後處理工作流的後處理線程數。 <br>預設值為 1。 |

