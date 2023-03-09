---
title: FMPS和AEM指南
description: 使用AEM指南發佈FMPS
source-git-commit: 5c53f89a811571c2193769bb4821657df3212dc0
workflow-type: tm+mt
source-wordcount: '686'
ht-degree: 0%

---


# FrameMaker Publishing Server(FMPS)和AEM指南

**如果您想要高品質的自動發佈，AEM指南與FrameMaker Publishing Server整合可能是您的解決方案。\
以下文章將幫助您使用AEM指南來設定和運行FMPS。**

## FMPS與AEM指南的相容性：

- 與4.1 AEM指南相容： [連結](https://experienceleague.adobe.com/docs/experience-manager-guides-learn/tutorials/release-info/release-notes/on-prem-release-notes/release-notes-4.1.html?lang=en/#compatibility-matrix)
- 與4.0 AEM指南的相容性： [連結](https://helpx.adobe.com/xml-documentation-for-experience-manager/release-note/release-notes-xml-documentation-solution-4-0.html/#Compatibility%20matrix)
- 未來版本： [連結](https://experienceleague.adobe.com/docs/experience-manager-guides-learn/tutorials/release-info/latest-release-info.html?lang=en)

## 安裝:

### AEM指南：

安裝和配置指： [連結](https://helpx.adobe.com/content/dam/help/en/xml-documentation-solution/4-1-2/Adobe-Experience-Manager-Guides_Installation-Configuration-Guide_EN.pdf)

### FMPS:

對於FMPS安裝，您可以參考 [影片連結](https://www.youtube.com/watch?v=2deelyM5VA8&amp;t) 或 [檔案](https://help.adobe.com/en_US/framemaker/server/index.html#t=fmps-user-guide%2Finstall_config_fmps.html%23install_config_fmps&amp;rhtocid=_2)

## 所需配置：

您的DITA內容可使用FrameMaker Publishing Server(FMPS)輸出。 您可以以FMPS支援的任意格式建立輸出。 在Web主控台中，修改com.adobe.fmdita.config.ConfigManager套件組合的下列屬性，以設定AEM參考線以使用FMPS。

若要開啟Web主控台，請前往URL存取http://\&lt;server name=&quot;&quot;>:\&lt;port>/system/console/configMgr。

**配置屬性及其說明：** [連結](https://helpx.adobe.com/content/dam/help/en/xml-documentation-solution/4-1-2/Adobe-Experience-Manager-Guides_Installation-Configuration-Guide_EN.pdf#page=89)

## 運行測試：

您可以使用FMPS自動發佈 **PDF，回應式HTML5**，和 **Epub** DITA和FM資產。

從「使用生成PDF」菜單中，選擇「FrameMaker發佈伺服器」。

使用者可提供「設定檔案(.sts)」和「ditaval」。 會根據您提供的條件，使用雙變數進行篩選。

- **設定檔案**:FrameMaker /FMPS發佈設定，包含發佈時要FMPS執行的所有設定。例如：使用自訂範本產生輸出、產生標籤和出血(PDF)、使用目錄產生PDF、索引等。
- **FMPS存在：** 預先定義的分頁和設定檔案組合。使用者不必提供個別的分頁和設定檔案，而可以預先建立FMPS預設集，供重新用於發佈需求。

**注意：** 如果您未選擇任何設定或FMPS預設集，則FMPS將使用預設系統設定發佈。

如果您已選取FMPS預設集，並且從AEM提供了設定/ditaval檔案，則這將會發生衝突，而FMPS預設集將優先於自訂設定/ditaval檔案。

### 使用FMPS發佈基線：

您可以使用FMPS2020.0.2或更新版本發佈已建立的基線。

**要開始使用的FMPS設定檔案（.sts檔案）示例：** [連結](https://acrobat.adobe.com/link/track?uri=urn:aaid:scds:US:ef750752-7a7e-4e51-923e-6b7d9861ed54) （將此檔案解壓縮）

## 常見問題集和疑難排解：

- FMPS發佈失敗，出現「逾時例外」。

檢查並增加/system/console/configMgr/com.adobe.fmdita.config.ConfigManager中「FMPS逾時」（秒）的值

- 無法在下拉式清單中取得FMPS預設集。

確保伺服器上已建立預定義的FMPS預設集，並且您的連接設定正確。

- 我在發佈時收到空白PDF。

如果您使用UUID，請確定您已針對非UUID AEM參考線，在FrameMaker「編輯偏好設定」中勾選「使用UUID型參考」，反之亦然。

- 我的設定/ditaval未套用至最終發佈的輸出。

請確定您未並行選取設定/ditaval檔案和FMPS預設集。 使用FrameMaker手動驗證輸出。

- 未從FMPS發佈基線。

基線發佈與FMPS2020.0.2或更新版本相容。\
請確定已正確建立基線，以確認前往「對應控制面板主題下載對映」並選取「使用基線」。

- 從FMPS發佈任務所花的時間比其他引擎長。

將有理想的固定標頭，大約100個 僅從FMPS發佈時3-4分鐘（如果您認為FMPS超過其他引擎），請洽詢您的FMPS管理員或聯絡Adobe支援。

## 其他資源：

[FMPS學習與支援](https://helpx.adobe.com/support/framemaker-publishing-server.html)

[AEM學習與支援](https://helpx.adobe.com/in/support/xml-documentation-for-experience-manager.html)

[FrameMaker和FMPS社群](https://community.adobe.com/t5/framemaker/ct-p/ct-framemaker?page=1&amp;sort=latest_replies&amp;lang=all&amp;tabid=all)

[AEM指南社群](https://experienceleaguecommunities.adobe.com/t5/experience-manager-guides/ct-p/aem-xml-documentation)
