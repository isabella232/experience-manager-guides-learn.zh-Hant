---
title: 為AEM參考線設定全新的Microservice發佈as a Cloud Service
description: 了解如何為AEM指南設定全新的Microservice發佈。
source-git-commit: afbc1712cf45dd0b570e20683946af6a86edae7e
workflow-type: tm+mt
source-wordcount: '519'
ht-degree: 0%

---

# 為AEM參考線設定全新的Microservice發佈as a Cloud Service

新的發佈微服務可讓使用者在AEM指南as a Cloud Service上同時執行大型發佈工作負載，並運用業界領先的Adobe I/O Runtime無伺服器平台。

對於每個發佈請求，AEM指南會as a Cloud Service執行個別的容器，該容器會根據使用者請求水準縮放。 這可讓使用者執行多個發佈請求，並取得比大型內部AEM伺服器更佳的效能。

由於新雲端發佈服務是以Adobe IMS JWT驗證為基礎所保護，因此客戶應遵循下列指定步驟，將其環境與Adobe的安全代號驗證工作流程整合，並開始使用新的雲端可擴充發佈解決方案。


## 在Adobe Developer Console中建立IMS設定

**建立混淆所需的角色**:系統管理員

執行下列步驟以在Adobe Developer Console中建立IMS設定：

1. 開啟開發人員主控台： `https://developer.adobe.com/console`.

1. 切換至 **專案** 標籤。

   <img src="assets/projects-tab.png" alt="專案索引標籤" width="500">

1. 要建立新的空項目，請選擇 **空白專案** 從 **建立新專案** 下拉式清單。

   <img src="assets/create-new-project.png" alt="建立新專案" width="500">

1. 選擇 **API** 從 **新增至專案** 下拉式清單，將IO管理API新增至您的專案。

   <img src="assets/add-project.png" alt="新增專案" width="300">

   <img src="assets/io-management-api.png" alt="io管理" width="500">

1. 新增API時建立新的私密/公開金鑰組。 這會自動下載您系統上的私密金鑰。

   <img src="assets/generate-key-pair.png" alt="產生金鑰組" width="500">

1. 儲存已設定的API。

   <img src="assets/save-api.png" alt="儲存api" width="600">

1. 返回 **專案** 按一下 **專案概述** 左邊。

   <img src="assets/project-overview.png" alt="專案概述" width="500">

1. 按一下 **下載** 按鈕，下載服務JSON。

   <img src="assets/download-json.png" alt="下載json" width="500">

您現在已設定JWT驗證詳細資料，並且已下載私密金鑰和服務詳細資料JSON。 請讓這兩個檔案保持方便，因為下一節中需要這些檔案。

### 新增IMS設定至環境

執行下列步驟以將IMS設定新增至環境：

1. 開啟experience manager，然後選取包含您要設定之環境的方案。
1. 切換至 **環境** 標籤。
1. 按一下您要設定的環境名稱。 這應該會導覽至「環境資訊」頁面。
1. 切換至 **設定** 標籤。
1. 上傳私密金鑰和專案JSON，如下方螢幕擷取所示。 請確定您使用的名稱和設定與下方強調顯示的相同。

   <img src="assets/ims-config-environment.png" alt="ims設定" width="500">

>[!NOTE]
>
> 您需要開啟、複製和貼上私密金鑰和服務詳細資訊JSON檔案的內容，到「設定」面板的值欄，如上方螢幕擷取所示。

將IMS設定新增至環境後，請執行下列步驟，使用OSGi將這些屬性與AEM指南連結：

1. 在Cloud Manager Git專案程式碼中，新增下列兩個檔案(如需檔案內容，請參閱 [附錄](#appendix))。

   * `com.adobe.aem.guides.eventing.ImsConfiguratorService.cfg.json`
   * `com.adobe.fmdita.publishworkflow.PublishWorkflowConfigurationService.xml`
1. 請確定新新增的檔案已涵蓋在 `filter.xml`.
1. 提交並推送您的Git變更。
1. 執行管道以在環境上套用變更。

完成此作業後，您應該就能使用新的Microservice雲端發佈功能。

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

```
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:sling="http://sling.apache.org/jcr/sling/1.0"
          jcr:primaryType="sling:OsgiConfig"
          dxml.publish.microservice.url="https://adobeioruntime.net/api/v1/web/543112-guidespublisher/default/publishercaller.json"
          dxml.use.publish.microservice="{Boolean}true"
/>
```
