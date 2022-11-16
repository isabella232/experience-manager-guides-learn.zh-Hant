---
title: AEM指南發行版本
description: 最新AEM指南發行和必要的AEM版本
exl-id: 780697a9-bdc6-40c2-b258-64639fe30f88
source-git-commit: 4066b22849271f29b5339dbd2f1bfa0946cdbd8b
workflow-type: tm+mt
source-wordcount: '888'
ht-degree: 0%

---

# [!DNL AEM Guides] 版本

[!DNL Adobe Experience Manager Guides] 是部署至AEM的應用程式。 這是功能強大、企業級的元件內容管理解決方案(CCMS)，可在Adobe Experience Manager中啟用原生DITA支援，讓AEM能夠處理DITA型內容的建立和傳送。

## UUID與非UUID的比較說明

[!DNL AEM Guides] 套件分為兩種模式：UUID組建和非UUID組建。

客戶在首次設定時，將需要決定是UUID模式還是非UUID模式（請連線您的客戶成功經理，協助您根據使用情況做出決策）。

從 [!DNL AEM Guides] 至於較新版本，客戶將需要確定選擇相同的模式（UUID/非UUID），以符合其現有模式。 非UUID組建版本不應直接升級為UUID組建版本。 從非UUID組建移轉至UUID組建時，需要移轉內容。

**升級組建**

當您從舊版升級為 [!DNL AEM Guides]，您可能需要執行一些移轉指令碼。 如需升級指示，請參閱發行說明和版本專屬檔案。

並非所有升級路徑都直接受支援。 例如，只能從3.8版直接升級到4.0版。如果您使用3.8版之前的版本，請參閱版本特定的文檔以獲取升級說明 [說明封存](https://helpx.adobe.com/xml-documentation-for-experience-manager/archive.html).
請洽詢您的客戶成功經理以驗證升級路徑。

**[!DNL AEM Guides]組建**

下列清單包含最新的 [!DNL AEM Guides] 可在AMS或On-Prem上安裝的套件、對應的AEM版本（先決條件）、套件的下載連結，以及其他實用資訊。 建議僅使用 [!DNL AEM Guides]. 如果因故需要存取舊組建，請連線您帳戶的客戶成功經理。

>[!NOTE]
>
>請洽詢您的客戶成功經理，以取得 [!DNL AEM Guides] 針對AEMas a Cloud Service建置。

| [!DNL AEM Guides] 版 | 發行說明 | AEM先決條件 | 建立下載連結 |
|---|---|---|---|
| **AEM指南4.1** | [4.1.x發行說明](https://experienceleague.adobe.com/docs/experience-manager-guides-learn/tutorials/release-info/release-notes/on-prem-release-notes/release-notes-4.1.html) | **非UUID和UUID 4.1.2**<br><br> AEM 6.5 SP13、SP12、SP11或SP10 <br>Java:11或8 <br><br>**非UUID和UUID 4.1**<br><br> AEM 6.5 SP13、SP12、SP11或SP10 | **非UUID**: <br> **AEM 6.5** <br>[4.1](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-1%2F4-1-non-uuid%2Fcom.adobe.fmdita-6.5-4.1.159.zip)<br>[4.1.2](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-1-2%2F4-1-2-non-uuid%2Fcom.adobe.fmdita-6.5-sp-4.1.2.11.zip)<br>[4.1.3](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-1-3%2F4-1-3-non-uuid%2Fcom.adobe.fmdita-6.5-sp-4.1.3.2.zip)<br><br> **UUID** <br>**AEM 6.5** <br>[4.1](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-1%2F4-1-uuid%2Fcom.adobe.fmdita-6.5-uuid-4.1.159.zip)<br>[4.1.2](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-1-2%2F4-1-2-uuid%2Fcom.adobe.fmdita.uuid-6.5-sp-4.1.2.11.zip)<br>[4.1.3](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-1-3%2F4-1-3-uuid%2Fcom.adobe.fmdita.uuid-6.5-sp-4.1.3.2.zip) |
| **AEM指南4.0** | [4.0.x發行說明](https://helpx.adobe.com/xml-documentation-for-experience-manager/release-note/release-notes-xml-documentation-solution-4-0.html) | **非UUID和UUID 4.0.3**<br> AEM 6.5 SP12、SP11、SP10或SP9 <br>Java:11或8 <br><br> <br>**非UUID和UUID 4.0.2** <br> AEM 6.5 SP12、SP11、SP10或SP9 <br>Java:11或8 <br><br> **非UUID和UUID 4.0** <br> AEM 6.5 SP11、SP10或SP9 | **非UUID**: <br> **AEM 6.5** <br>[4.0.3](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-0-3%2F4-0-2-non-uuid%2Fcom.adobe.fmdita-6.5-hotfix-4.0.3.1.zip)<br>[4.0.2](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-0-2%2F4-0-2-non-uuid%2Fcom.adobe.fmdita-6.5-sp-4.0.2.10.zip)  <br> [4.0](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/aemdox/4-0/4-0-non-uuid/com.adobe.fmdita-6.5-4.0.70.zip)  <br><br> **UUID** <br>**AEM 6.5**  <br>[4.0.3](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-0-3%2F4-0-3-uuid%2Fcom.adobe.fmdita.uuid-6.5-hotfix-4.0.3.1.zip) <br>[4.0.2](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-0-2%2F4-0-2-uuid%2Fcom.adobe.fmdita.uuid-6.5-sp-4.0.2.10.zip)<br> [4.0](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/aemdox/4-0/4-0-uuid/com.adobe.fmdita-6.5-uuid-4.0.70.zip) |
| **AEM指南3.8.5** <br> 3.8.5是3.8之前的SP版本。 <br>3.8版不能獨立安裝，因為3.8.5 SP包含嚴重修正。 <br>客戶必須先安裝3.8，然後安裝SP 3.8.5。 | [3.8.x發行說明](https://helpx.adobe.com/xml-documentation-for-experience-manager/release-note/release-notes-xml-documentation-solution-3-8.html) | **非UUID** <br> AEM 6.5 SP9或SP8 <br> AEM 6.4 SP8 <br> AEM 6.3 SP3 <br><br> **UUID** <br> AEM 6.5 SP9或SP8 | **非UUID**: <br> **AEM 6.5** <br> [3.8.5 SP](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/aemdox/3-8-5/com.adobe.fmdita-6.5-hotfix-3.8.5.2.zip) <br>[3.8](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/aemdox/3-8/com.adobe.fmdita-6.5-3.8.166.zip)<br> **AEM 6.4** <br> [3.8.5 SP](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/aemdox/3-8-5/com.adobe.fmdita-6.4-hotfix-3.8.5.1.zip) <br>[3.8](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/aemdox/3-8/com.adobe.fmdita-6.4-3.8.166.zip) <br> **AEM 6.3** <br> [3.8.5 SP](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/aemdox/3-8-5/com.adobe.fmdita-6.3-hotfix-3.8.5.1.zip) <br>[3.8](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/aemdox/3-8/com.adobe.fmdita-6.3-3.8.166.zip) <br><br> **UUID** <br>**AEM 6.5** <br> [3.8.5 SP](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/aemdox/3-8-5uuid/com.adobe.fmdita.uuid-6.5-hotfix-3.8.5.2.zip) <br> [3.8](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/aemdox/3-8uuid/com.adobe.fmdita.uuid-6.5-3.8.168.zip) |
