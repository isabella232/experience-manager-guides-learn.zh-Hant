---
title: 配置AEM本地PDF發佈環境
description: 配置AEM本地PDF發佈環境
exl-id: 40266ca0-0b0b-4418-b606-f70270addbaa
source-git-commit: 7b48633ef2418fa7c91842a8d2c2a4177017ef58
workflow-type: tm+mt
source-wordcount: '797'
ht-degree: 1%

---

# 配置AEM本地PDF發佈環境

指AEM南包括本機PDF發佈引擎，用戶可以設計、開發和發佈PDF格式的內容。

它提供了建立不同頁面佈局、CSS模板以及結合頁面佈局和CSS設計PDF模板的功能。

在指南中配置本機PDF的步AEM驟因作業系統而異。 根據安裝的作業系統，使用以下配AEM置步驟。

## 必備條件

設定本機PDF的最低要求：

- 已安裝Java平台、標準版8或11 JDK（Java SE開發工具包）和JRE（Java SE運行時環境）
- AEM6.5 SP13、SP12、SP11或SP10
- 參考線4.1及更高版本（非UUID或UUID）

本機PDF發佈引擎需要OracleJDK來生成crx-quickstart資料夾AEM中的節點模組。 預設情況下，它支援以下作業系統：

- Windows 10、Windows 2019伺服器及更高版本。
- Linux — （RHEL 8及更高版本、CentOS 7及更高版本、Ubuntu 18及更高版本）
- Mac作業系統（基於英特爾）

## Windows Server的配置步驟(JAVA 11/8)

1. 確保服AEM務器已關閉。
2. 在Windows任務欄上，按一下右鍵Windows表徵圖並選擇系統。
3. 在「設定」窗口的「相關設定」下，按一下「高級系統設定」。
4. 在「高級」(Advanced)頁籤上，按一下「環境變數」(Environment Variables)。
5. 在「系統變數」部分中，按一下「」_新建_」建立新環境變數。
6. 輸入變數名稱為JAVA_HOME。
7. 在值欄位中，提供Java安裝路徑，然後按一下確定。

   例如：

   JAVA 11:

   C:\Program Files\JAVA\jdk-11.0.15.1

   JAVA 8:

   C:\Program Files\JAVA\ jdk1.8.0_144

8. 添加從系統變數中選擇路徑，然後按一下編輯。

9. 現在，在路徑變數內提供伺服器路徑的值，然後按一下確定。

   例如：

   JAVA 11:

   %JAVA_HOME%\bin\server\

   JAVA 8:

   %JAVA_HOME%\jre\bin\server\

10. 在「環境變數」對話框上再次按一下「確定」。
11. 在「系統屬性」對話框上再次按一下「確定」。
12. 現在，啟動服AEM務器。
13. 從Web編輯器中的預設生成本機PDF。

## Linux伺服器配置步驟(RHEL7/centOS 7)

1. 確保服AEM務器已關閉
2. 通過執行echo $JAVA_HOME驗證JAVA_HOME變數
3. 如果未設定JAVA_HOME變數，則按步驟4操作。 否則，直接移到步驟5。
4. 根據已安裝的java版本使用以下命令設定JAVA_HOME變數

   例如：

   JAVA 11:

   1. 導出JAVA\_HOME=/usr/lib/jvm/java-11.0.15.1
   2. 導出路徑=$PATH:$JAVA\_HOME/bin
   3. 導出LD\_LIBRARY\_PATH=/usr/lib/jvm/jdk-11.0.15.1/lib/server:/usr/java/jdk-11.0.15.1/lib/server

   JAVA 8:

   1. 導出JAVA\_HOME=/usr/lib/jvm/java-11.0.15.1
   2. 導出路徑=$PATH:$JAVA\_HOME/bin


5. 重新啟動服AEM務器
6. 複製「_node_modules_zip_&quot;附於crx-quickstart/profiles/nodejs-b1aad0a7-9079-e56c-1ed8-6fcababe8166/目錄。
7. crx-quickstart/profiles/nodejs -b1aad0a7-9079-e56c-1ed8-6fcababe8166/ location中的開啟終端。
8. 使用以下命令刪除node_modules目錄

   **rm -rf節點模組**

9. 使用下面的命令解壓縮node_modules.zip

   **unzip node_modules_zip**

10. 如果未安裝/識別unzip命令，則可以使用以下命令安裝該命令

   **yum安裝解壓**

11. 安裝fontconfig包。
命令：yum安裝方案配置
12. 從Web編輯器中的預設生成本機PDF。

**注釋** :node_modules.zip包可下載 [這裡](https://acrobat.adobe.com/link/track?uri=urn:aaid:scds:US:295d8f03-41e1-429b-8465-2761ce3c2fb3)。

對於使用Guides 4.1或更早版本的用戶，手動導入Linux作業系統下載的節點模組是一種解決方法。

## Mac電腦的配置步驟(JAVA 11/8)

1. 安裝OracleJAVA 11或OracleJAVA 8。
2. 將JAVA_HOME環境變數設定為已安裝的JAVA目錄。
3. 開啟Unix外殼。
（此處使用Bash設定配置）

   命令：納米~/.bashrc

4. 根據已安裝的java版本使用以下命令設定JAVA_HOME變數

   例如：

   JAVA 11:

   導出JAVA\_HOME= /Library/Java/JavaVirtualMachines/jdk-11.0.15.1.jdk/Contents/Home

5. 重裝巴什克

   命令：來源~/.bashrc

6. 使用命令echo $JAVA_HOME驗證是否已設定JAVA_HOME

7. 從安裝路徑執行以下三AEM個命令

   C:/{aem-installation-folder}/crx-quickstart/profiles/nodejs-b1aad0a7-9079-e56c-1ed8-6fcababe8166

   i)查找。 -type d -exec chmod 0755 {} \;ii)查找。 -type f -exec chmod 0755 {} \;三)。/node-darwin/bin/node node-darwin/lib/node_modules/npm/bin/npm-cli.js — 前置詞。 install —unsafe-perm —scripts-prepend-node-path

8. 使用以下命令驗證是否安裝了Java

   i)運行 **。/node-darwin/bin/node** /crx-quickstart/profiles/nodejs -b1aad0a7-9079-e56c-1ed8-6fcababe8166資料夾中的命令

   ![Mac](../assets/publishing/mac.png)

   ii)a = require(&#39;java&#39;)

9. 安裝fontconfig包。
命令：apt install fontconfig

10. 從Web編輯器中的預設生成本機PDF。

## 疑難排解

以下是在未正確設定PDF變數時，在生成環境時可能出現的常見錯誤。

### Windows/MacOS中的空指針異常

![空指針異常](../assets/publishing/null-pointer-exception.png)

### RHEL 7 Linux作業系統中缺少庫

![缺少庫](../assets/publishing/missing-libraries.png)

如果在執行上述任何步驟時遇到任何問題，請將問題發佈到「指南」AEM社區 [論壇](https://experienceleaguecommunities.adobe.com/t5/experience-manager-guides/ct-p/aem-xml-documentation) 尋求幫助。
