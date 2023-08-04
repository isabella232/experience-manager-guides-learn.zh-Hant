---
title: 設定AEM環境以進行原生PDF發佈
description: 設定AEM環境以進行原生PDF發佈
exl-id: 40266ca0-0b0b-4418-b606-f70270addbaa
source-git-commit: 45dfe6078039001327e91ae85ea2a5beeacb2d59
workflow-type: tm+mt
source-wordcount: '906'
ht-degree: 1%

---

# 設定AEM環境以進行原生PDF發佈

AEM Guides包含原生PDF發佈引擎，可讓使用者設計、開發及發佈PDF格式的內容。

它提供建立不同頁面配置、CSS範本的功能，並搭配頁面配置和CSS設計PDF範本。

在AEM Guides中設定此原生PDF的步驟因作業系統而異。 請根據安裝AEM的作業系統，使用下列設定步驟。

## 必備條件

設定原生PDF的最低需求：

- 已安裝Java平台、Standard Edition 8或11 JDK （Java SE開發套件）和JRE （Java SE執行階段環境）
- AEM 6.5 SP13、SP12、SP11或SP10
- 指南4.1和更高版本（非UUID或UUID）

原生PDF發佈引擎需要OracleJDK，才能在AEM crx-quickstart資料夾中產生節點模組。 預設支援下列作業系統：

- Windows 10、windows 2019 server及更新版本。
- Linux - （RHEL 8及更高版本、CentOS 7及更高版本、Ubuntu 18及更高版本）
- Mac作業系統（Intel架構）

## Windows Server (JAVA 11/8)的設定步驟

1. 確認AEM伺服器已關閉。
2. 在Windows工作列上，以滑鼠右鍵按一下Windows圖示並選取系統。
3. 在「設定」視窗的「相關設定」下，按一下「進階系統設定」。
4. 在進階索引標籤上，按一下環境變數。
5. 在系統變數區段中，按一下「_新增_」以建立新的環境變數。
6. 輸入變數名稱做為JAVA_HOME。
7. 在值欄位中，提供Java安裝路徑，然後按一下「確定」。

   例如：

   JAVA 11：

   C:\Program Files\JAVA\jdk-11.0.15.1

   JAVA 8：

   C:\Program Files\JAVA\ jdk1.8.0_144

8. 從系統變數新增選取路徑，然後按一下編輯。

9. 現在，在路徑內變數提供伺服器路徑的值，然後按一下確定。

   例如：

   JAVA 11：

   %JAVA_HOME%\bin\server\

   JAVA 8：

   %JAVA_HOME%\jre\bin\server\

10. 在環境變數對話方塊中再次按一下「確定」。
11. 在[系統屬性]對話方塊中再次按一下[確定]。
12. 現在啟動AEM伺服器。
13. 從網頁編輯器中的預設集產生原生PDF。

## 針對Linux伺服器的設定步驟(RHEL7/centOS 7)

1. 確認AEM伺服器已關閉
2. 執行回應$JAVA_HOME以驗證JAVA_HOME變數
3. 如果未設定JAVA_HOME變數，請依照步驟4操作。 否則，請直接移至步驟5。
4. 根據安裝的Java版本，使用以下命令設定JAVA_HOME變數

   例如：

   JAVA 11：

   1. export JAVA\_HOME=/usr/lib/jvm/java-11.0.15.1
   2. 匯出路徑=$PATH： $JAVA\_HOME/bin
   3. export LD\_LIBRARY\_PATH=/usr/lib/jvm/jdk-11.0.15.1/lib/server:/usr/java/jdk-11.0.15.1/lib/server

   JAVA 8：

   1. export JAVA\_HOME=/usr/lib/jvm/java-11.0.15.1
   2. 匯出路徑=$PATH： $JAVA\_HOME/bin

5. 如果您使用Guides 4.2版及更新版本，請重新啟動AEM伺服器並移至步驟12。
6. 複製&quot;_node_modules.zip_「附加到本文底部的crx-quickstart/profiles/nodejs—b1aad0a7-9079-e56c-1ed8-6fcababe8166/目錄。
7. 在crx-quickstart/profiles/nodejs—b1aad0a7-9079-e56c-1ed8-6fcababe8166/位置中開啟終端機。
8. 使用以下命令刪除node_modules目錄

   **rm -rf節點模組**

9. 使用以下命令解壓縮node_modules.zip

   **unzip node_modules.zip**

10. 如果unzip命令未安裝/識別，則可使用以下命令進行安裝

   **yum安裝unzip**

11. 安裝fontconfig套件。
命令： yum install fontconfig
12. 從網頁編輯器中的預設集產生原生PDF。

**注意** ：可以下載node_modules.zip套件 [此處](https://acrobat.adobe.com/link/track?uri=urn:aaid:scds:US:295d8f03-41e1-429b-8465-2761ce3c2fb3).

手動匯入Linux作業系統下載的節點模組是使用Guides 4.1或更早版本（步驟6-12）的使用者的因應措施

## Mac電腦的設定步驟(JAVA 11/8)

1. 安裝OracleJAVA 11或OracleJAVA 8。
2. 將JAVA_HOME環境變數設定為已安裝的JAVA目錄。
3. 開啟Unix殼層。
（此處使用Bash設定組態）

   命令： nano ~/.bashhrc

4. 根據安裝的Java版本，使用以下命令設定JAVA_HOME變數

   例如：

   JAVA 11：

   export JAVA\_HOME= /Library/Java/JavaVirtualMachines/jdk-11.0.15.1.jdk/Contents/Home

5. 重新載入bashhrc

   命令：來源~/.bashhrc。

6. 使用命令echo $JAVA_HOME驗證是否已設定JAVA_HOME

7. 從AEM安裝路徑執行以下三個命令

   C：/{aem-installation-folder}/crx-quickstart/profiles/nodejs—b1aad0a7-9079-e56c-1ed8-6fcababe8166

   i)尋找。 -type d -exec chmod 0755 {} \； ii)尋找。 -type f -exec chmod 0755 {} \； iii) 。/node-darwin/bin/node node-darwin/lib/node_modules/npm/bin/npm-cli.js —prefix 。 安裝 — unsafe-perm —scripts-prepend-node-path

8. 使用以下命令確認是否已安裝Java

   i)執行 **./node-darwin/bin/節點** /crx-quickstart/profiles/nodejs—b1aad0a7-9079-e56c-1ed8-6fcababe8166資料夾中的命令

   ![Mac](../assets/publishing/mac.png)

   ii) a = require(&#39;java&#39;)

9. 安裝fontconfig套件。
命令： apt install fontconfig

10. 從網頁編輯器中的預設集產生原生PDF。

## 疑難排解

以下是環境變數未正確設定時，PDF產生期間可能會發生的常見錯誤。

### Windows/Mac作業系統中的空指標例外狀況

![Null指標例外狀況](../assets/publishing/null-pointer-exception.png)

如果在更正Java環境設定後問題仍然存在，請重新驗證下列專案：

1. 檢查輸出預設集是否已正確定義，或建立不含空格的新輸出預設集。

2. 驗證/libs/fmdta/node_resources中的節點資源目錄，以確保在安裝期間安裝所有必要的程式庫。

### RHEL 7 Linux作業系統中遺失的程式庫

![缺少資料庫](../assets/publishing/missing-libraries.png)

### 發佈程式逾時。 處理未在指定時間0毫秒內完成

![發佈程式逾時](../assets/publishing/publish-process-timeout.png)

驗證CRX存放庫中/var/dxml/profiles/b1aad0a7-9079-e56c-1ed8-6fcababe8166/nodejs中nodejs節點的逾時屬性值。 預設值為 300。



如果您在執行上述任何步驟時遇到任何問題，請在AEM Guides社群中發佈您的問題 [論壇](https://experienceleaguecommunities.adobe.com/t5/experience-manager-guides/ct-p/aem-xml-documentation) 以取得協助。
