---
title: 翻譯內容
description: 瞭解如何翻譯內容
source-git-commit: 880cd344ceb65ea339be699ebcad41c0d62e168a
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 11%

---

# 翻譯內容 {#id181GB0400UI}

自動翻譯頁面內容、資產和使用者產生的內容，以建立和維護多語言網站。 若要自動化翻譯工作流程，您可以將翻譯服務提供商與 AEM 相整合，並建立用於將內容翻譯成多種語言的專案。AEM 支援人工和機器翻譯工作流程。

- 人工翻譯：內容會傳送給您的翻譯提供者，並由專業翻譯人員進行翻譯。 完成後，翻譯後的內容將傳回並匯入到 AEM 中。當您的翻譯提供者與AEM整合時，內容會自動在AEM和翻譯提供者之間交換

- 機器翻譯：機器翻譯服務會立即翻譯您的內容


翻譯內容涉及以下步驟：

1. 連線AEM與您的 [翻譯服務提供者](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/administering/reusing-content/translation/integration-framework.html?lang=en) 和建立翻譯整合框架設定。

1. 將語言主版的頁面與翻譯服務和框架設定建立關聯。

1. 識別型別 [要翻譯的內容](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/administering/reusing-content/translation/rules.html?lang=en).

1. 編寫語言主版並建立語言副本的根頁面，[以備妥內容進行翻譯](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/administering/reusing-content/translation/preparation.html?lang=en)。

1. 建立 [翻譯專案](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/administering/reusing-content/translation/managing-projects.html?lang=en) 收集要翻譯的內容並準備翻譯程式。

1. 使用翻譯專案至 [管理內容翻譯](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/administering/reusing-content/translation/managing-projects.html?lang=en) 程式。


如果您的翻譯服務提供者未提供聯結器來與AEM整合，則AEM支援手動匯出和匯入XML格式的翻譯內容。

>[!TIP]
>
> 請參閱 *翻譯* 最佳實務指南中的區段，以取得翻譯內容的最佳實務。

## 在DITA map控制面板上設定翻譯標籤

若要隱藏DITA map圖示板上的「轉譯」標籤，請執行下列步驟：

1. 使用中提供的指示 [設定覆寫](download-install-additional-config-override.md#) 以建立組態檔。
1. 在設定檔案中，提供下列\(property\)詳細資訊，以在地圖控制面板上設定翻譯標籤：

   | PID | 屬性索引鍵 | 屬性值 |
   |---|------------|--------------|
   | `com.adobe.fmdita.config.ConfigManager` | `tabs.translation` | 布林值\( true/ false\)。<br> **預設值**： `true` |

   >[!NOTE]
   >
   > 此設定預設為啟用，地圖控制面板上不提供翻譯標籤。


## 設定元件型翻譯工作流程

如果翻譯供應商的聯結器不支援DITA內容，則需要啟用元件型翻譯工作流程。 啟用後，可翻譯內容會以資產中繼資料的形式傳送。 但是，聯結器需要支援資產中繼資料轉譯，此工作流程才能運作。

根據設定中使用的翻譯工作流程，應設定元件型翻譯工作流程選項。 使用中提供的指示 [設定覆寫](download-install-additional-config-override.md#) 以建立組態檔。 在設定檔案中，提供下列\(property\)詳細資訊，以設定元件型翻譯工作流程：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.config.ConfigManager` | `component.translation` | 布林值： <br>  — 如果您使用人工翻譯，則 *停用* \( `false`\) **元件式翻譯工作流程** 選項。 <br>  — 如果您使用機器翻譯，則 *啟用\( `true`\)* 此 **元件式翻譯工作流程** 選項。 |

>[!NOTE]
>
> 如果您使用翻譯聯結器，請確定您已依照 *[設定翻譯整合框架](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/administering/reusing-content/translation/integration-framework.html?lang=en)* AEM檔案中的主題。

>[!IMPORTANT]
>
> 設定翻譯設定後，請務必在語言資料夾上設定適當的雲端設定。

## 設定暫存語言副本的後處理

當您啟動翻譯工作流程時，系統會建立來源內容的臨時語言副本。 您可以選擇啟用或停用這些暫存檔的後處理作業。 在後置處理作業中，會解析來自檔案的傳入和傳出參照、設定檔案狀態以及其他作業。 如果您啟用這些暫存檔的後處理，則翻譯過程可能需要更長的時間才能完成。 因此，建議停用後續處理選項。

使用中提供的指示 [設定覆寫](download-install-additional-config-override.md#) 以建立組態檔。 在設定檔案中，提供下列\(property\)詳細資訊，以設定暫存語言副本的後置處理：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.config.ConfigManager` | `postprocess.temporary.langcopies` | 布林值： <br>  — 如果不想對暫存檔執行後期處理作業，則 *停用* \( false\) **處理後語言副本** 選項。<br>  — 如果要在暫存檔上執行後續處理作業，則 *啟用* \( true\) **處理後語言副本** 選項。<br> **預設值**： false |
