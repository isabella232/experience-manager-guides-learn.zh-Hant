---
title: 翻譯指南中的AEM內容
description: 瞭解如何翻譯內容
source-git-commit: 9fe396dcfd2e3570ec386c958d7d4efdb4d608e5
workflow-type: tm+mt
source-wordcount: '758'
ht-degree: 11%

---


# 翻譯內容 {#id181GB0400UI}

自動翻譯頁面內容、資產和用戶生成的內容，以建立和維護多語言網站。 若要自動化翻譯工作流程，您可以將翻譯服務提供商與 AEM 相整合，並建立用於將內容翻譯成多種語言的專案。AEM 支援人工和機器翻譯工作流程。

- 人工翻譯：內容將傳送給您的翻譯提供商並由專業翻譯人員翻譯。完成後，翻譯後的內容將傳回並匯入到 AEM 中。當翻譯提供商與之整合AEM時，內容將自動在翻譯提供AEM商之間交換

- 機器翻譯：機器翻譯服務可立即翻譯您的內容


翻譯內容涉及以下步驟：

1. 連AEM接 [翻譯服務提供商](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/tc-tic.html#ConnectingtoaTranslationServiceProvider) 建立 [翻譯整合框架配置](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/tc-tic.html#CreatingaTranslationIntegrationConfiguration)。

1. 將語言首頁與 [翻譯服務和框架配置](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/tc-tic.html#ConfiguringPagesforTranslation)。

1. 確定 [翻譯內容](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/tc-rules.html)。

1. 編寫語言主版並建立語言副本的根頁面，[以備妥內容進行翻譯](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/tc-prep.html)。

1. 建立 [翻譯項目](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/tc-manage.html) 收集要翻譯的內容並準備翻譯過程。

1. 使用翻譯項目 [管理內容翻譯](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/tc-manage.html) 處理。


如果您的翻譯服務提供商未提供與整合的連接AEM器，則AEM支援以XML格式手動導出和導入翻譯的內容。

>[!TIP]
>
> 查看 *翻譯*&#x200B;中的「最佳做法指南」中的「關於翻譯內容的最佳做法」一節。

## 在DITA映射儀表板上配置轉換頁籤

預設情況下未啟用「隱藏轉換頁籤」選項，您需要從configMgr中啟用該選項。 要隱藏DITA映射儀表板上的「轉換」頁籤，請執行以下步驟：

1. 開啟「Adobe Experience ManagerWeb控制台配置」頁。

   訪問配置頁的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索並按一下 **com.adobe.fmdita.config.ConfigManager** 捆綁。

1. 選擇 **隱藏翻譯頁籤** 的子菜單。

   >[!NOTE]
   >
   > 預設情況下，此屬性處於禁用狀態，並且「轉換」頁籤在映射儀表板上可用。

1. 按一下「**儲存**」。

## 配置基於元件的翻譯工作流

如果翻譯供應商的連接器不支援DITA內容，則需要啟用基於元件的翻譯工作流。 一旦啟用，可翻譯內容將作為資產元資料發送。 但是，連接器需要支援此工作流的資產元資料轉換才能正常工作。

根據設定中使用的翻譯工作流，應按如下方式配置基於元件的翻譯工作流選項：

1. 開啟「Adobe Experience ManagerWeb控制台配置」頁。

   訪問配置頁的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索並按一下 **com.adobe.fmdita.config.ConfigManager** 捆綁。

1. 配置 **基於元件的DITA轉換工作流** 選項：

   - 如果你用人類翻譯 *禁用* 這樣 **基於元件的翻譯工作流** 的雙曲餘切值。

   - 如果使用機器翻譯，則 *啟用* 這樣 **基於元件的翻譯工作流** 的雙曲餘切值。
   >[!NOTE]
   >
   > 如果使用的是翻譯連接器，請確保已按照中的說明配置了連接器 *[配置翻譯整合框架](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/tc-tic.html)* 文檔中AEM的主題。

1. 按一下「**儲存**」。


>[!IMPORTANT]
>
> 設定翻譯配置後，請確保在語言資料夾上設定相應的雲配置。

## 配置臨時語言副本的後處理

啟動翻譯工作流時，系統會建立源內容的臨時語言副本。 您可以選擇啟用或禁用這些臨時檔案的後處理操作。 在後處理操作中，解析來自檔案的傳入和傳出引用，設定文檔狀態以及其它操作。 如果對這些臨時檔案啟用後處理，則翻譯過程可能需要更長的時間才能完成。 因此，建議禁用後處理選項。

預設情況下，會禁用臨時檔案的後處理選項。 您可以通過執行以下步驟來配置此選項：

1. 開啟「Adobe Experience ManagerWeb控制台配置」頁。

   訪問配置頁的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索並按一下 **com.adobe.fmdita.config.ConfigManager** 捆綁。

1. 配置 **後處理語言副本** 選項：

   - \(*預設*\)如果您不想對臨時檔案運行後處理操作，則 *禁用* 這樣 **後處理語言副本** 的雙曲餘切值。

   - 如果要對臨時檔案運行後處理操作，則 *啟用* 這樣 **後處理語言副本** 的雙曲餘切值。

1. 按一下「**儲存**」。


