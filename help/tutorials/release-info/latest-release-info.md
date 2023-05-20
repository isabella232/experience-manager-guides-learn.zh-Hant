---
title: 指AEM南版本
description: 最新AEM指南版本和必備AEM版本
exl-id: 780697a9-bdc6-40c2-b258-64639fe30f88
source-git-commit: f836ad2178524b1ddfb89fdfa728a8b06cb02c2c
workflow-type: tm+mt
source-wordcount: '1188'
ht-degree: 0%

---

# [!DNL AEM Guides] 發行

[!DNL Adobe Experience Manager Guides] 是部署到的應AEM用程式 它是一個功能強大、企業級元件內容管理解決方案(CCMS)，它支援Adobe Experience Manager的本機DITA支援，AEM能夠處理基於DITA的內容建立和交付。

輔AEM助線包有兩種變體 — UUID生成和非UUID生成。

## UUID和非UUID生成

UUID和非UUID內部版本之間的關鍵區別如下：

|  | 非UUID生成 | UUID生成 |
|---|---|---|
| **資產標識** | 所有資產都使用儲存庫中資產的路徑標識。 | 所有資產都使用其UUID（系統在首次上載資產時生成的唯一ID）進行標識。 |
| **引用建立** | 所有內容引用都基於其路徑建立。 | 所有內容引用都基於其UUID建立。 |

### UUID生成的優點

* UUID安裝效能更高：
   * 參照與路徑無關：當引用是基於UUID而不是路徑建立的時，引用管理系統會知道這些連結。
   * 移動/更新操作非常有效：即使資源移動到儲存庫中的其他路徑，UUID仍保持不變。 因此，無需進行任何處理來修補移動/更新操作中的資產之間的引用。
* UUID生成是前瞻性的，因為我們也將此框架用於指南的AEM雲設定。


### 在兩個版本之間選擇

* 如果您是新客戶，建議您使用UUID內部版本。
* 如果您是現有客戶，則可以選擇移到UUID內部版本，因為現在可以從非UUID遷移到UUID內部版本。 有關詳細資訊，請參閱 *非UUID到UUID內容遷移* 的 **安裝和配置Adobe Experience Manager指南。**

>[!NOTE]
>
>* 客戶在首次安裝時需要在UUID和非UUID模式之間做出選擇（如果需要幫助，請與Customer Success Manager連接，以幫助您根據您的用戶做出決策）。
>* 從一個版本的指南升AEM級到更新的版本時，客戶需要確保他們選擇同一模式（UUID /非UUID）以匹配其現有模式。 不應直接升級到UUID生成。 從非UUID生成到UUID生成需要內容遷移。


**升級生成**

從舊版本升級到更新版本時 [!DNL AEM Guides]，可能需要執行遷移指令碼。 有關升級說明，請參閱發行說明和特定於版本的文檔。

並非所有升級路徑都直接受支援。 例如，只能從3.8版直接升級到4.0版。如果您的版本是3.8之前的版本，請參閱特定於版本的文檔以獲取升級說明 [幫助存檔](https://helpx.adobe.com/xml-documentation-for-experience-manager/archive.html)。
請聯繫您的客戶成功經理以驗證升級路徑。

**[!DNL AEM Guides]生成**

以下清單包含最新 [!DNL AEM Guides] 可在AMS或On-Prem上安裝的軟體包、相AEM應版本（前提條件）、軟體包的下載連結以及其他有用資訊。 建議僅使用 [!DNL AEM Guides]。 如果出於某種原因，您需要訪問舊版本，請與您帳戶的客戶成功經理進行連接。

>[!NOTE]
>
>聯繫您的客戶成功經理，以獲得 [!DNL AEM Guides] 為AEMas a Cloud Service。

| [!DNL AEM Guides] 版 | 發行說明 | 必AEM備項 | 生成下載連結 |
|---|---|---|---|
| **指AEM南4.2** | [4.2發行說明](https://experienceleague.adobe.com/docs/experience-manager-guides-learn/tutorials/release-info/release-notes/on-prem-release-notes/release-notes-4.2.html) | **非UUID和UUID 4.2**<br><br> AEM6.5 SP15、SP14、SP13或SP12 <br><br>Java:十一、八個<br><br> | **非UUID**: <br> **AEM 6.5** <br>[4.2](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-2%2F4-2-non-uuid%2Fcom.adobe.fmdita-6.5-4.2.229.zip)<br><br> **UUID** <br>**AEM 6.5** <br>[4.2](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-2%2F4-2-uuid%2Fcom.adobe.fmdita-6.5-uuid-4.2.229.zip)<br> |
| **指AEM南4.1** | [4.1.x發行說明](https://experienceleague.adobe.com/docs/experience-manager-guides-learn/tutorials/release-info/release-notes/on-prem-release-notes/release-notes-4.1.html) | **非UUID和UUID 4.1.2**<br><br> AEM6.5 SP13、SP12、SP11或SP10 <br>Java:十一、八個&#x200B;<br><br>**非UUID和UUID 4.1**<br><br> AEM6.5 SP13、SP12、SP11或SP10 | **非UUID**: <br> **AEM 6.5** <br>[4.1](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-1%2F4-1-non-uuid%2Fcom.adobe.fmdita-6.5-4.1.159.zip)<br>[4.1.2](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-1-2%2F4-1-2-non-uuid%2Fcom.adobe.fmdita-6.5-sp-4.1.2.11.zip)<br>[4.1.3](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-1-3%2F4-1-3-non-uuid%2Fcom.adobe.fmdita-6.5-sp-4.1.3.2.zip)<br><br> **UUID** <br>**AEM 6.5** <br>[4.1](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-1%2F4-1-uuid%2Fcom.adobe.fmdita-6.5-uuid-4.1.159.zip)<br>[4.1.2](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-1-2%2F4-1-2-uuid%2Fcom.adobe.fmdita.uuid-6.5-sp-4.1.2.11.zip)<br>[4.1.3](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-1-3%2F4-1-3-uuid%2Fcom.adobe.fmdita.uuid-6.5-sp-4.1.3.2.zip) |
| **指AEM南4.0** | [4.0.x發行說明](https://helpx.adobe.com/xml-documentation-for-experience-manager/release-note/release-notes-xml-documentation-solution-4-0.html) | **非UUID和UUID 4.0.3**<br> AEM6.5 SP12 、 SP11 、 SP10或SP9 <br>Java:十一、八個 <br><br> <br>**非UUID和UUID 4.0.2** <br> AEM6.5 SP12 、 SP11 、 SP10或SP9 <br>Java:十一、八個 <br><br> **非UUID和UUID 4.0** <br> AEM6.5 SP11、SP10或SP9 | **非UUID**: <br> **AEM 6.5** <br>[4.0.3](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-0-3%2F4-0-2-non-uuid%2Fcom.adobe.fmdita-6.5-hotfix-4.0.3.1.zip)<br>[4.0.2](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-0-2%2F4-0-2-non-uuid%2Fcom.adobe.fmdita-6.5-sp-4.0.2.10.zip)  <br> [4.0](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/aemdox/4-0/4-0-non-uuid/com.adobe.fmdita-6.5-4.0.70.zip)  <br><br> **UUID** <br>**AEM 6.5**  <br>[4.0.3](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-0-3%2F4-0-3-uuid%2Fcom.adobe.fmdita.uuid-6.5-hotfix-4.0.3.1.zip) <br>[4.0.2](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-0-2%2F4-0-2-uuid%2Fcom.adobe.fmdita.uuid-6.5-sp-4.0.2.10.zip)<br> [4.0](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/aemdox/4-0/4-0-uuid/com.adobe.fmdita-6.5-uuid-4.0.70.zip) |
| **指AEM南3.8.5** <br> 3.8.5是3.8之上的SP版本。 <br>3.8版本不能單獨安裝，因為3.8.5 SP包含關鍵修復程式。 <br>客戶必須先安裝3.8，然後安裝SP 3.8.5。 | [3.8.x發行說明](https://helpx.adobe.com/xml-documentation-for-experience-manager/release-note/release-notes-xml-documentation-solution-3-8.html) | **非UUID** <br> AEM6.5 SP9或SP8 <br> AEM6.4 SP8 <br> AEM6.3 SP3 <br><br> **UUID** <br> AEM6.5 SP9或SP8 | **非UUID**: <br> **AEM 6.5** <br> [3.8.5 SP](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/aemdox/3-8-5/com.adobe.fmdita-6.5-hotfix-3.8.5.2.zip) <br>[3.8](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/aemdox/3-8/com.adobe.fmdita-6.5-3.8.166.zip)<br> **AEM 6.4** <br> [3.8.5 SP](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/aemdox/3-8-5/com.adobe.fmdita-6.4-hotfix-3.8.5.1.zip) <br>[3.8](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/aemdox/3-8/com.adobe.fmdita-6.4-3.8.166.zip) <br> **AEM 6.3** <br> [3.8.5 SP](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/aemdox/3-8-5/com.adobe.fmdita-6.3-hotfix-3.8.5.1.zip) <br>[3.8](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/aemdox/3-8/com.adobe.fmdita-6.3-3.8.166.zip) <br><br> **UUID** <br>**AEM 6.5** <br> [3.8.5 SP](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/aemdox/3-8-5uuid/com.adobe.fmdita.uuid-6.5-hotfix-3.8.5.2.zip) <br> [3.8](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/aemdox/3-8uuid/com.adobe.fmdita.uuid-6.5-3.8.168.zip) |
