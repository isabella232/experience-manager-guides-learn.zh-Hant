---
title: 在AEM指南中使用FrameMaker Publishing Server(FMPS)進行發佈
description: 使用AEM指南發佈FMPS
source-git-commit: 1d118aeda42d76b0a9f34ca29fdeedb0165739fd
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 0%

---


# 在AEM指南中使用FrameMaker Publishing Server(FMPS)進行發佈

如果您想要高品質的自動發佈，AEM指南與FrameMaker Publishing Server整合可能是您的解決方案。\
文章可協助您使用AEM指南來設定和執行FMPS。

## FMPS與AEM指南的相容性

- 與4.1 AEM指南相容： [4.1相容性矩陣 ](https://experienceleague.adobe.com/docs/experience-manager-guides-learn/tutorials/release-info/release-notes/on-prem-release-notes/release-notes-4.1.html?lang=en/#compatibility-matrix)
- 與4.0 AEM指南的相容性： [4.0相容性矩陣](https://helpx.adobe.com/xml-documentation-for-experience-manager/release-note/release-notes-xml-documentation-solution-4-0.html/#Compatibility%20matrix)
- 最新版本： [最新發行資訊](https://experienceleague.adobe.com/docs/experience-manager-guides-learn/tutorials/release-info/latest-release-info.html?lang=en)

## 安裝

請參閱以下內容，了解AEM指南和FMPS安裝及設定

### AEM指南

安裝和配置指： [ 4.1安裝和配置 ](https://helpx.adobe.com/content/dam/help/en/xml-documentation-solution/4-1-2/Adobe-Experience-Manager-Guides_Installation-Configuration-Guide_EN.pdf)

### FMPS

對於FMPS安裝，您可以參考 [YouTube連結 ](https://www.youtube.com/watch?v=2deelyM5VA8&amp;t) 或 [FMPS安裝和配置 ](https://help.adobe.com/en_US/framemaker/server/index.html#t=fmps-user-guide%2Finstall_config_fmps.html%23install_config_fmps&amp;rhtocid=_2)

## 必要配置

FrameMaker Publishing Server(FMPS)可用來產生DITA內容。 FMPS支援多種輸出格式。 修改Web控制台中「com.adobe.fmdita.config.ConfigManager套件」的下列屬性，以設定AEM參考線以使用FMPS。

若要開啟Web主控台，請前往URL存取http://\&lt;server name=&quot;&quot;>:\&lt;port>/system/console/configMgr。

**配置屬性及其說明** [4.1安裝與配置 ](https://helpx.adobe.com/content/dam/help/en/xml-documentation-solution/4-1-2/Adobe-Experience-Manager-Guides_Installation-Configuration-Guide_EN.pdf#page=89)

## 運行測試：

您可以使用FMPS自動發佈 **PDF，回應式HTML5**，和 **Epub** DITA和FM資產。

從「使用生成PDF」菜單中，選擇「FrameMaker發佈伺服器」。

使用者可提供「設定檔案(.sts)」和「ditaval」。 會根據您提供的條件，使用雙變數來進行篩選。

- **設定檔案**:FrameMaker /FMPS發佈設定檔案，包含發佈時要FMPS遵守的所有設定。 例如，使用自訂範本建立輸出、建立標籤和出血(PDF)，以及使用目錄建立PDF。
- **FMPS預設：** 這是預先定義的Ditaval和設定檔案組合。 使用者可以預先建立FMPS預設集，供重新用於發佈需求，而不需提供個別的編輯和設定檔案。

**注意：** 如果您未選擇任何設定或FMPS預設集，則FMPS將使用預設系統設定進行發佈。

如果您選擇FMPS預設集，並從AEM提供自訂設定或編輯檔案，則會發生衝突。 在這種情況下，FMPS預設集優先於自訂設定或分段檔案。

### 使用FMPS發佈基線：

您可以使用FMPS2020.0.2或更新版本發佈已建立的基線。

**要開始使用的FMPS設定檔案（.sts檔案）示例：** [FMPS設定檔案範例 ](https://acrobat.adobe.com/link/track?uri=urn:aaid:scds:US:ef750752-7a7e-4e51-923e-6b7d9861ed54) （將此檔案解壓縮）

## 常見問題集和疑難排解：

- ### FMPS發佈失敗，出現「逾時例外」

>檢查並增加/system/console/configMgr/com.adobe.fmdita.config.ConfigManager中「FMPS逾時」（秒）的值

- ### 無法在下拉式清單中取得FMPS預設集

>確保伺服器上已建立預定義的FMPS預設集，並且您的連接設定正確。

- ### 發佈時收到空白PDF

>如果您使用UUID，請確定您已在FrameMaker Edit Preferences中勾選「使用UUID型參考」，反之則針對非UUID AEM參考線。

- ### 未在最終發佈的輸出中套用我的設定/ditaval

>確認您不是同時選擇FMPS預設集和設定/維檔案。 使用FrameMaker手動檢查輸出。

- ### 未從FMPS發佈基線

>FMPS2020.0.2或更新版本與基線發佈相容。
>請確定已正確建立基線；要檢查，請轉至「映射控制面板 — 主題 — 下載映射」並選擇「使用基線」。
- ### 從FMPS發佈任務所花的時間比其他引擎長

>從FMPS發佈時，理想的固定標頭時間約為3-4分鐘；如果您認為時間更長，請洽詢您的FMPS管理員，或聯絡Adobe支援。

## 其他資源：

[FMPS學習與支援](https://helpx.adobe.com/support/framemaker-publishing-server.html)

[AEM指南學習與支援](https://helpx.adobe.com/in/support/xml-documentation-for-experience-manager.html)

[FrameMaker和FMPS社群](https://community.adobe.com/t5/framemaker/ct-p/ct-framemaker?page=1&amp;sort=latest_replies&amp;lang=all&amp;tabid=all)

[AEM指南社群](https://experienceleaguecommunities.adobe.com/t5/experience-manager-guides/ct-p/aem-xml-documentation)
