---
title: 在指南中使用FrameMaker發佈伺服器(FMPS)發AEM布
description: 使用輔助線發佈FMPSAEM
exl-id: 05d4d876-f83b-473c-bf31-14d6565e80e2
source-git-commit: 7b48633ef2418fa7c91842a8d2c2a4177017ef58
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 0%

---

# 在指南中使用FrameMaker發佈伺服器(FMPS)發AEM布

如果AEM您希望獲得高質量的自動發佈，則與FrameMaker Publishing Server整合的指南可能是您的解決方案。\
文章幫助您設定和運行帶參考線的AEMFMPS。

## FMPS與指南的兼AEM容性

- 與4.1指南的兼AEM容性： [4.1相容性矩陣 ](https://experienceleague.adobe.com/docs/experience-manager-guides-learn/tutorials/release-info/release-notes/on-prem-release-notes/release-notes-4.1.html?lang=en/#compatibility-matrix)
- 與4.0指南的兼AEM容性： [4.0相容性矩陣](https://helpx.adobe.com/xml-documentation-for-experience-manager/release-note/release-notes-xml-documentation-solution-4-0.html/#Compatibility%20matrix)
- 最新版本： [最新版本資訊](https://experienceleague.adobe.com/docs/experience-manager-guides-learn/tutorials/release-info/latest-release-info.html?lang=en)

## 安裝

有關指南和AEMFMPS的安裝和配置，請參閱以下內容

### 參考AEM線

安裝和配置： [ 4.1安裝和配置 ](https://helpx.adobe.com/content/dam/help/en/xml-documentation-solution/4-1-2/Adobe-Experience-Manager-Guides_Installation-Configuration-Guide_EN.pdf)

### FMPS

對於FMPS安裝，可參考給定 [YouTube連結 ](https://www.youtube.com/watch?v=2deelyM5VA8&amp;t) 或 [FMPS安裝和配置 ](https://help.adobe.com/en_US/framemaker/server/index.html#t=fmps-user-guide%2Finstall_config_fmps.html%23install_config_fmps&amp;rhtocid=_2)

## 所需配置

FrameMaker發佈伺服器(FMPS)可用於生成DITA內容。 FMPS支援多種輸出格式。 修改Web控制台中的&quot;com.adobe.fmdita.config.ConfigManager捆綁包&quot;的以下屬性，以將指南配AEM置為使用FMPS。

要開啟Web控制台，請轉到URL訪問http://\&lt;server name=&quot;&quot;>:\&lt;port>/system/console/configMgr。

**配置屬性及其說明** [4.1安裝和配置 ](https://helpx.adobe.com/content/dam/help/en/xml-documentation-solution/4-1-2/Adobe-Experience-Manager-Guides_Installation-Configuration-Guide_EN.pdf#page=89)

## 運行Test:

使用FMPS，可以自動發佈 **PDF，響應HTML5**, **埃普** 和FM資產。

從「使用生成PDF」菜單中，選擇FrameMaker Publishing Server。

用戶可以提供「settings File(.sts)」和「ditaval」。 根據您提供的條件，使用雙曲線進行過濾。

- **設定檔案**:FrameMaker /FMPS發佈設定檔案，包含發佈時希望FMPS尊重的所有設定。 例如，使用自定義模板建立輸出，建立標籤和出血(PDF)，以及使用目錄建立PDF。
- **FMPS預設：** 它是ditaval和settings檔案的預定義組合。 用戶不能提供單獨的雙曲和設定檔案，而是可以預先建立FMPS預設，該預設可用於重新用於發佈需求。

**注：** 如果未選擇任何設定或FMPS預設，FMPS將使用預設系統設定發佈。

如果您選擇了FMPS預設，並且還從中提供了自定義設定或同位檔案，則此衝突AEM。 在這種情況下，FMPS預設優先於自定義設定或雙曲檔案。

### 使用FMPS進行基線發佈：

可以使用FMPS2020.0.2或更高版本發佈已建立的基線。

**要開始的FMPS設定檔案（.sts檔案）示例：** [示例FMPS設定檔案 ](https://acrobat.adobe.com/link/track?uri=urn:aaid:scds:US:ef750752-7a7e-4e51-923e-6b7d9861ed54) （解壓縮此檔案）

## 常見問題和故障排除：

- ### FMPS發佈失敗，出現「超時異常」

>檢查並增加/system/console/configMgr/com.adobe.fmdita.config.ConfigManager中的「FMPS timeout」（秒）的值

- ### 無法在下拉清單中獲取FMPS預設

>確保在伺服器上建立了預定義的FMPS預設，並且連接設定正確。

- ### 我在發佈時得到空白PDF

>如果使用UUID，請確保在FrameMaker編輯首選項中選中了「使用基於UUID的引用」，反之，您選中了非UUIDAEM參考線。

- ### 未在最終發佈的輸出中應用我的設定/雙曲

>驗證您沒有同時選擇FMPS預設和設定/顯示檔案。 使用FrameMaker手動檢查輸出。

- ### 未從FMPS發佈基線

>FMPS2020.0.2或更高版本與基線發佈相容。
>確保已正確建立基線；要檢查，請轉到「映射儀表板 — 主題 — 下載映射」並選擇「使用基線」。
- ### 從FMPS發佈任務比其他引擎花費的時間更長

>從FMPS發佈時，理想的固定報頭時間約為3-4分鐘；如果您認為時間較長，請與FMPS管理員或聯繫Adobe支援。

## 其他資源：

[FMPS學習和支援](https://helpx.adobe.com/support/framemaker-publishing-server.html)

[指AEM南學習和支援](https://helpx.adobe.com/in/support/xml-documentation-for-experience-manager.html)

[FrameMaker和FMPS社區](https://community.adobe.com/t5/framemaker/ct-p/ct-framemaker?page=1&amp;sort=latest_replies&amp;lang=all&amp;tabid=all)

[指AEM南社區](https://experienceleaguecommunities.adobe.com/t5/experience-manager-guides/ct-p/aem-xml-documentation)
