---
title: AEM Guides中的FrameMaker Publishing Server (FMPS)發佈功能
description: 使用AEM Guides以FMPS發佈
source-git-commit: 880cd344ceb65ea339be699ebcad41c0d62e168a
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 0%

---

# AEM Guides中的FrameMaker Publishing Server (FMPS)發佈功能

如果您想要尋找高品質的自動化發佈，AEM Guides與FrameMaker Publishing Server的整合可能是您的解決方案。\
文章可協助您使用AEM Guides設定及執行FMPS。

## FMPS與AEM Guides的相容性

- 與4.1 AEM Guides的相容性： [4.1相容性矩陣](https://experienceleague.adobe.com/docs/experience-manager-guides-learn/tutorials/release-info/release-notes/on-prem-release-notes/release-notes-4.1.html?lang=en/#compatibility-matrix)
- 與4.0 AEM Guides的相容性： [4.0相容性矩陣](https://helpx.adobe.com/xml-documentation-for-experience-manager/release-note/release-notes-xml-documentation-solution-4-0.html/#Compatibility%20matrix)
- 最新版本： [最新版本資訊](https://experienceleague.adobe.com/docs/experience-manager-guides-learn/tutorials/release-info/latest-release-info.html?lang=en)

## 安裝

請參閱以下內容，以瞭解AEM Guides和FMPS的安裝與設定

### AEM指南

安裝及設定請參考： [4.1安裝與設定](https://helpx.adobe.com/content/dam/help/en/xml-documentation-solution/4-1-2/Adobe-Experience-Manager-Guides_Installation-Configuration-Guide_EN.pdf)

### FMPS

若為FMPS安裝，您可以參考以下資訊： [YouTube連結](https://www.youtube.com/watch?v=2deelyM5VA8&amp;t) 或 [FMPS安裝與設定](https://help.adobe.com/en_US/framemaker/server/index.html#t=fmps-user-guide%2Finstall_config_fmps.html%23install_config_fmps&amp;rhtocid=_2)

## 必要的設定

FrameMaker Publishing Server (FMPS)可用來產生您的DITA內容。 FMPS支援多種輸出格式。 修改Web主控台中「com.adobe.fmdita.config.ConfigManager套件」的下列屬性，以設定AEM Guides使用FMPS。

若要開啟Web主控台，請前往URL存取http://\&lt;server name=&quot;&quot;>：\&lt;port>/system/console/configMgr。

**設定屬性及其說明** [4.1安裝與設定](https://helpx.adobe.com/content/dam/help/en/xml-documentation-solution/4-1-2/Adobe-Experience-Manager-Guides_Installation-Configuration-Guide_EN.pdf#page=89)

## 正在執行測試：

使用FMPS時，您可以自動發佈 **PDF，回應式HTML5**、和 **Epub** 用於您的DITA和FM資產。

從「使用產生PDF」選單中，選擇「FrameMaker Publishing Server」。

使用者可以提供「設定File(.sts)」和「ditaval」。 根據您提供的條件，使用雙精度篩選器完成篩選。

- **設定檔案**：FrameMaker/FMPS發佈設定檔案，其中包含您希望FMPS在發佈時遵循的所有設定。 例如，使用自訂範本建立輸出、建立「標籤和出血」(PDF)以及使用TOC建立PDF。
- **FMPS預設集：** 它是預先定義的Ditaval和設定檔案組合。 使用者可以預先建立FMPS預設集，而不是提供個別的記錄和設定檔案，這些預設集可重複用於發佈需求。

**注意：** 如果您未選擇任何設定或FMPS預設集，FMPS會使用預設系統設定進行發佈。

如果您選擇FMPS預設集，並且也提供了來自AEM的自訂設定或Ditaval檔案，則會發生衝突。 在此情況下，FMPS預設集會優先於自訂設定或Ditaval檔案。

### 使用FMPS的基準線發佈：

您可以使用FMPS2020.0.2或更新版本發佈已建立的基準線。

**開始使用的FMPS設定檔範例（.sts檔）：** [FMPS設定檔範例](https://acrobat.adobe.com/link/track?uri=urn:aaid:scds:US:ef750752-7a7e-4e51-923e-6b7d9861ed54) （解壓縮此檔案）

## 常見問題集和疑難排解：

- ### FMPS發佈失敗，並出現「逾時例外狀況」

>檢查並增加/system/console/configMgr/com.adobe.fmdita.config.ConfigManager中「FMPS逾時」（秒）的值

- ### 無法在下拉式清單中取得FMPS預設集

>確定您在伺服器上建立了預先定義的FMPS預設集，且您的連線設定正確無誤。

- ### 發佈時收到空白PDF

>如果您使用UUID，請確定您已核取「FrameMaker編輯偏好設定」中的「使用UUID型參考」，並反之針對非UUID AEM參考線。

- ### 我的設定/對話方塊未套用到最終發佈的輸出

>確認您並未同時選擇FMPS預設集和設定/對話方塊檔案。 使用FrameMaker手動檢查輸出。

- ### 未從FMPS發佈基準線

>FMPS2020.0.2或更新版本與基準線發佈相容。
>請確定基準線已正確建立；若要檢查，請前往「地圖儀表板 — 主題 — 下載地圖」，然後選擇「使用基準線」。
- ### 從FMPS發佈任務所花的時間比其他引擎多

>從FMPS發佈時，理想的固定標題時間約為3至4分鐘；如果您認為時間更長，請洽詢FMPS管理員或聯絡Adobe支援。

## 其他資源：

[FMPS學習與支援](https://helpx.adobe.com/support/framemaker-publishing-server.html)

[AEM Guides學習與支援](https://helpx.adobe.com/in/support/xml-documentation-for-experience-manager.html)

[FrameMaker和FMPS社群](https://community.adobe.com/t5/framemaker/ct-p/ct-framemaker?page=1&amp;sort=latest_replies&amp;lang=all&amp;tabid=all)

[AEM Guides社群](https://experienceleaguecommunities.adobe.com/t5/experience-manager-guides/ct-p/aem-xml-documentation)
