---
title: 為AEM Guidesas a Cloud Service設定新的微服務型發佈
description: 瞭解如何為AEM Guides設定新的微服務型發佈。
exl-id: 92e3091d-6337-4dc6-9609-12b1503684cd
source-git-commit: aa71a2b8ff5f83365ff2f3562bb2b77061a3da8e
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 0%

---

# 為AEM Guidesas a Cloud Service設定新的微服務型發佈

新的發佈微服務可讓使用者在AEM Guidesas a Cloud Service上同時執行大型發佈工作負載，並利用業界領先的Adobe I/O Runtime無伺服器平台。

對於每個發佈請求，AEM Guidesas a Cloud Service會執行單獨的容器，其會根據使用者請求水平縮放。 這可讓使用者執行多個發佈請求，並獲得比其大型內部部署AEM伺服器更好的效能。

>[!NOTE]
>
> AEM Guides中以微服務為基礎的發佈可支援PDF（原生和DITA-OT型）、HTML5、JSON和CUSTOM型別的輸出預設集。

由於新的雲端發佈服務受到Adobe IMS JWT型驗證的保護，客戶應該遵循以下指定步驟，將其環境與Adobe的安全權杖型驗證工作流程整合，並開始使用新的雲端型可擴充發佈解決方案。


## 在Adobe Developer Console中建立IMS設定

**建立設定所需的角色**：系統管理員

執行以下步驟，在Adobe Developer主控台中建立IMS設定：

1. 開啟開發人員主控台： `https://developer.adobe.com/console`.

1. 切換至 **專案** 從頂端跳出。

   <img src="assets/projects-tab.png" alt="專案索引標籤" width="500">

1. 若要建立新的空白專案，請選取 **空白專案** 從 **建立新專案** 下拉式清單。

   <img src="assets/create-new-project.png" alt="建立新專案" width="500">

1. 選取 **API** 從 **新增至專案** 用來新增IO Management API至專案的下拉式清單。

   <img src="assets/add-project.png" alt="新增專案" width="300">

   <img src="assets/io-management-api.png" alt="io管理" width="500">

1. 新增API時，建立新的私人/公開金鑰組。 這將會自動在您的系統上下載私密金鑰。

   <img src="assets/generate-key-pair.png" alt="產生金鑰組" width="500">

1. 儲存已設定的API。

   <img src="assets/save-api.png" alt="儲存api" width="600">

1. 返回至 **專案** 標籤並按一下 **專案概述** 左側。

   <img src="assets/project-overview.png" alt="專案概述" width="500">

1. 按一下 **下載** 按鈕來下載服務JSON。

   <img src="assets/download-json.png" alt="下載json" width="500">

您現在已設定JWT驗證詳細資訊，並且已下載私密金鑰和服務詳細資訊JSON。 保留這兩個檔案方便使用，因為下一個區段需要這些檔案。

### 將IMS設定新增至環境

執行以下步驟，將IMS設定新增至環境：

1. 開啟Experience Manager，然後選取包含您要設定環境的程式。
1. 切換至 **環境** 標籤。
1. 按一下您要設定的環境名稱。 這應該會將您導覽至環境資訊頁面。
1. 切換至 **設定** 標籤。
1. 上傳私人金鑰和專案JSON，如下方熒幕擷圖所示。 請確定您使用的名稱和設定與以下醒目提示的名稱和設定相同。

   <img src="assets/ims-config-environment.png" alt="ims設定" width="500">

>[!NOTE]
>
> 您需要開啟、複製私密金鑰和服務詳細資料JSON檔案的內容，並將其貼到設定面板的值欄，如上面的熒幕擷取所示。

新增IMS設定至環境後，請使用OSGi執行以下步驟將這些屬性與AEM Guides連結：

1. 在您的Cloud Manager Git專案程式碼中，新增以下兩個指定的檔案(如需檔案內容，請參閱 [附錄](#appendix))。

   * `com.adobe.aem.guides.eventing.ImsConfiguratorService.cfg.json`
   * `com.adobe.fmdita.publishworkflow.PublishWorkflowConfigurationService.xml`
1. 確保新新增的檔案包含在您的 `filter.xml`.
1. 認可並推送您的Git變更。
1. 執行管道以在環境中套用變更。

完成此操作後，您應該能夠使用新的微服務型雲端發佈。

## 常見問題

1. 單一金鑰是否可用於多個雲端環境？
   * 是的，您可以產生一個私密金鑰並用於所有環境，但您必須為所有環境設定環境變數，並使用相同的金鑰。
1. 如果啟用使用微服務的OSGi設定，發佈程式是否可以在具有相同程式碼基底的本機AEM伺服器上運作？
   * 否，如果旗標 `dxml.use.publish.microservice` 設為 `true` 然後它一律會尋找微服務組態。 設定 `dxml.use.publish.microservice` 至 `false` 讓發佈功能在本機上運作。
1. 使用以微服務為基礎的發佈時，為DITA程式分配了多少記憶體？ 這是透過DITA輪廓ant引數驅動嗎？
   * 使用以微服務為基礎的發佈，記憶體配置不會透過DITA設定檔ant引數驅動。 服務容器上可用的記憶體總計為8 GB，其中6 GB配置給DITA-OT處理序。


## 附錄 {#appendix}

**檔案**：
`com.adobe.aem.guides.eventing.ImsConfiguratorService.cfg.json`

**內容**:

```
{
  "service.account.details": "$[secret:SERVICE_ACCOUNT_DETAILS]",
  "private.key": "$[secret:PRIVATE_KEY]"
}
```

**檔案**： `com.adobe.fmdita.publishworkflow.PublishWorkflowConfigurationService.xml`

**內容**:
* `dxml.use.publish.microservice`：切換以啟用使用DITA-OT的微服務型發佈
* `dxml.use.publish.microservice.native.pdf`：切換以啟用微服務型原生PDF發佈

```
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:sling="http://sling.apache.org/jcr/sling/1.0"
          jcr:primaryType="sling:OsgiConfig"
          dxml.publish.microservice.url="https://adobeioruntime.net/api/v1/web/543112-guidespublisher/default/publishercaller.json"
          dxml.use.publish.microservice="{Boolean}true"
          dxml.use.publish.microservice.native.pdf="{Boolean}true"
/>
```
