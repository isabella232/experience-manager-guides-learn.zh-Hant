---
title: 為指南as a Cloud Service配置新的基於微AEM服務的發佈
description: 瞭解如何為指南配置新的基於微服務的AEM發佈。
exl-id: 92e3091d-6337-4dc6-9609-12b1503684cd
source-git-commit: 95c89acd02b798d42c817b52f6f8e0710a0abb76
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 0%

---

# 為指南as a Cloud Service配置新的基於微AEM服務的發佈

新的發佈微服務使用戶能夠在指南as a Cloud Service上同時運行大AEM型發佈工作負載，並利用業界領先的Adobe I/O Runtime無伺服器平台。

對於每個發佈請AEM求，指南as a Cloud Service運行一個單獨的容器，該容器根據用戶請求水準擴展。 這為用戶提供了運行多個發佈請求並獲得比其大型預置伺服器更好的效能的AEM能力。

>[!NOTE]
>
> 目前，指南中基於微服務的發AEM布僅支援使用本機PDF發佈或通過DITA-OT的PDF輸出。 我們將在未來版本中添加基於微服務的發佈支援，以支援更多輸出類型。

由於新的雲發佈服務由基於Adobe IMS JWT的身份驗證保護，客戶應遵循以下給定步驟將其環境與Adobe的安全基於令牌的身份驗證工作流整合，並開始使用新的基於雲的可擴展發佈解決方案。


## 在Adobe Developer控制台中建立IMS配置

**建立混亂所需的角色**:系統管理員

執行以下步驟在Adobe Developer控制台中建立IMS配置：

1. 開啟開發人員控制台： `https://developer.adobe.com/console`。

1. 切換到 **項目** 的子菜單。

   <img src="assets/projects-tab.png" alt="項目頁籤" width="500">

1. 要建立新的空項目，請選擇 **空項目** 從 **建立新項目** 下拉清單。

   <img src="assets/create-new-project.png" alt="新建項目" width="500">

1. 選擇 **API** 從 **添加到項目** 下拉菜單，將IO管理API添加到項目。

   <img src="assets/add-project.png" alt="添加項目" width="300">

   <img src="assets/io-management-api.png" alt="io管理" width="500">

1. 在添加API時建立新的私鑰/公鑰對。 這將自動下載系統上的私鑰。

   <img src="assets/generate-key-pair.png" alt="生成密鑰對" width="500">

1. 保存已配置的API。

   <img src="assets/save-api.png" alt="保存api" width="600">

1. 返回 **項目** 頁籤 **項目概述** 左邊。

   <img src="assets/project-overview.png" alt="項目概述" width="500">

1. 按一下 **下載** 按鈕，下載服務JSON。

   <img src="assets/download-json.png" alt="下載json" width="500">

您現在已配置JWT身份驗證詳細資訊，並已下載私鑰和服務詳細資訊JSON。 在下一節中，請保持這兩個檔案的方便性，因為這些檔案是必需的。

### 將IMS配置添加到環境

執行以下步驟將IMS配置添加到環境：

1. 開啟體驗管理器，然後選擇包含要配置的環境的程式。
1. 切換到 **環境** 頁籤。
1. 按一下要配置的環境名稱。 這應導航到「環境資訊」頁。
1. 切換到 **配置** 頁籤。
1. 如下螢幕快照所示，上載私鑰和項目JSON。 確保使用的名稱和配置與下面突出顯示的相同。

   <img src="assets/ims-config-environment.png" alt="ims配置" width="500">

>[!NOTE]
>
> 您需要開啟、複製和貼上私鑰和服務詳細資訊JSON檔案的內容到「配置」面板的值列，如上面的螢幕快照所示。

將IMS配置添加到環境後，請執行以下步驟，使用OSGi將這些屬性與「AEM參考線」連結：

1. 在雲管理器Git項目代碼中，添加以下給定的兩個檔案(有關檔案內容，請參見 [附錄](#appendix))。

   * `com.adobe.aem.guides.eventing.ImsConfiguratorService.cfg.json`
   * `com.adobe.fmdita.publishworkflow.PublishWorkflowConfigurationService.xml`
1. 確保新添加的檔案被您 `filter.xml`。
1. 提交並推送Git更改。
1. 運行管線以在環境中應用更改。

完成此操作後，您應該能夠使用新的基於微服務的雲發佈。

## 附錄 {#appendix}

**檔案**:
`com.adobe.aem.guides.eventing.ImsConfiguratorService.cfg.json`

**內容**:

```
{
  "service.account.details": "$[secret:SERVICE_ACCOUNT_DETAILS]",
  "private.key": "$[secret:PRIVATE_KEY]"
}
```

**檔案**: `com.adobe.fmdita.publishworkflow.PublishWorkflowConfigurationService.xml`

**內容**:
* `dxml.use.publish.microservice`:切換以使用DITA-OT啟用基於微服務的PDF發佈
* `dxml.use.publish.microservice.native.pdf`:切換以啟用基於微服務的本機PDF發佈

```
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:sling="http://sling.apache.org/jcr/sling/1.0"
          jcr:primaryType="sling:OsgiConfig"
          dxml.publish.microservice.url="https://adobeioruntime.net/api/v1/web/543112-guidespublisher/default/publishercaller.json"
          dxml.use.publish.microservice="{Boolean}true"
          dxml.use.publish.microservice.native.pdf="{Boolean}true"
/>
```
