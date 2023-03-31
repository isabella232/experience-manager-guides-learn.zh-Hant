---
title: 為原生AEM發佈設定PDF環境
description: 為原生AEM發佈設定PDF環境
source-git-commit: f26b8f94e1d7a3c9dd0aaab2eb196a77119e47ac
workflow-type: tm+mt
source-wordcount: '797'
ht-degree: 1%

---


# 為原生AEM發佈設定PDF環境

AEM指南包含原生PDF發佈引擎，可讓使用者以PDF格式設計、開發及發佈內容。

它提供建立不同頁面配置、CSS模板以及結合頁面配置和CSS設計PDF模板的功能。

在「AEM指南」中設定此原生PDF的步驟會因作業系統而異。 請根據安裝AEM的作業系統，使用下列設定步驟。

## 必備條件

設定本機PDF的最低要求：

- 已安裝Java Platform, Standard Edition 8或11 JDK(Java SE Development Kit)和JRE（Java SE運行時環境）
- AEM 6.5 SP13、SP12、SP11或SP10
- 參考線4.1及更新版本（非UUID或UUID）

原生PDF發佈引擎需要OracleJDK，才能在AEM crx-quickstart資料夾中產生節點模組。 依預設，它支援下列作業系統：

- Windows 10、Windows 2019伺服器及更高版本。
- Linux — （RHEL 8及以上版本、CentOS 7及以上版本、Ubuntu 18及以上版本）
- Mac OS（基於英特爾）

## 針對Windows伺服器的配置步驟(JAVA 11/8)

1. 確認AEM伺服器關閉。
2. 在Windows任務欄上，按一下右鍵Windows表徵圖並選擇系統。
3. 在「設定」窗口的「相關設定」下，按一下「高級系統設定」。
4. 在「進階」標籤上，按一下「環境變數」 。
5. 在系統變數區段中，按一下「_新增_」，建立新的環境變數。
6. 輸入變數名稱為JAVA_HOME。
7. 在值欄位中，提供Java安裝路徑，然後按一下確定。

   例如：

   JAVA 11:

   C:\Program Files\JAVA\jdk-11.0.15.1

   JAVA 8:

   C:\Program Files\JAVA\ jdk1.8.0_144

8. 添加從系統變數中選擇路徑，然後按一下編輯。

9. 現在，路徑變數內提供伺服器路徑的值，然後按一下確定。

   例如：

   JAVA 11:

   %JAVA_HOME%\bin\server\

   JAVA 8:

   %JAVA_HOME%\jre\bin\server\

10. 在「環境變數」對話方塊上，再按一下「確定」。
11. 在「系統屬性」對話框上，再次按一下「確定」。
12. 現在，啟動AEM伺服器。
13. 從網頁編輯器中的預設集產生原生PDF。

## 針對Linux伺服器(RHEL7/centOS 7)的配置步驟

1. 確認AEM伺服器關閉
2. 執行echo $JAVA_HOME以驗證JAVA_HOME變數
3. 如果未設定JAVA_HOME變數，請遵循步驟4。 否則，直接移至步驟5。
4. 根據安裝的java版本，使用以下命令設定JAVA_HOME變數

   例如：

   JAVA 11:

   1. 導出JAVA\_HOME=/usr/lib/jvm/java-11.0.15.1
   2. 導出路徑=$PATH:$JAVA\_HOME/bin
   3. 導出LD\_LIBRARY\_PATH=/usr/lib/jvm/jdk-11.0.15.1/lib/server:/usr/java/jdk-11.0.15.1/lib/server

   JAVA 8:

   1. 導出JAVA\_HOME=/usr/lib/jvm/java-11.0.15.1
   2. 導出路徑=$PATH:$JAVA\_HOME/bin


5. 重新啟動AEM Server
6. 複製「_node_modules.zip_&quot;附加至crx-quickstart/profiles/nodejs—b1aad0a7-9079-e56c-1ed8-6fcababe8166/目錄。
7. 在crx-quickstart/profiles/nodejs—b1aad0a7-9079-e56c-1ed8-6fcababe8166/位置中開啟終端機。
8. 使用以下命令刪除node_modules目錄

   **rm -rf節點模組**

9. 使用以下命令解壓縮node_modules.zip

   **unzip node_modules.zip**

10. 如果未安裝/識別unzip命令，則可以使用以下命令進行安裝

   **yum install unzip**

11. 安裝fontconfig包。
命令：yum install fontconfig
12. 從網頁編輯器中的預設集產生原生PDF。

**注意** :node_modules.zip套件可下載 [此處](https://acrobat.adobe.com/link/track?uri=urn:aaid:scds:US:295d8f03-41e1-429b-8465-2761ce3c2fb3).

手動匯入下載的Linux作業系統節點模組是使用指南4.1或更舊版本的使用者的因應措施。

## Mac電腦的配置步驟(JAVA 11/8)

1. 安裝OracleJAVA 11或OracleJAVA 8。
2. 將JAVA_HOME環境變數設定為已安裝的JAVA目錄。
3. 開啟Unix殼層。
（此處使用Bash來設定配置）

   命令：nano ~//bashrc

4. 根據安裝的java版本，使用以下命令設定JAVA_HOME變數

   例如：

   JAVA 11:

   導出JAVA\_HOME= /Library/Java/Java/JavaVirtualMachines/jdk-11.0.15.1.jdk/Contents/Home

5. 重裝巴什克

   命令：來源~/.bashrc。

6. 使用命令echo $JAVA_HOME驗證JAVA_HOME是否已設定

7. 從AEM安裝路徑執行以下三個命令

   C:/{aem-installation-folder}/crx-quickstart/profiles/nodejs—b1aad0a7-9079-e56c-1ed8-6fcababe8166

   i)找到。 -type d -exec chmod 0755 {} \;ii)找到。 -type f -exec chmod 0755 {} \;iii)。/node-darwin/bin/node node-darwin/lib/node_modules/npm/bin/npm-cli.js — 前置詞。 install —unsafe-perm —scripts-prepend-node-path

8. 使用以下命令驗證是否安裝了Java

   i)運行 **./node-darwin/bin/node** 來自/crx-quickstart/profiles/nodejs—b1aad0a7-9079-e56c-1ed8-6fcababe8166資料夾的命令

   ![Mac](../assets/publishing/mac.png)

   ii)a = require(&#39;java&#39;)

9. 安裝fontconfig包。
命令：apt install fontconfig

10. 從網頁編輯器中的預設集產生原生PDF。

## 疑難排解

以下是環境變數未正確設定時，在產生PDF期間可能發生的常見錯誤。

### Windows/Mac OS中出現Null指針異常

![空指針異常](../assets/publishing/null-pointer-exception.png)

### RHEL 7 Linux OS中缺少庫

![缺少庫](../assets/publishing/missing-libraries.png)

如果您在執行上述任何步驟時遇到任何問題，請將問題張貼至AEM指南社群 [論壇](https://experienceleaguecommunities.adobe.com/t5/experience-manager-guides/ct-p/aem-xml-documentation) 以求協助。
