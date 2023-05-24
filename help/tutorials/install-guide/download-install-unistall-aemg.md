---
title: 解除安裝AEM Guides
description: 瞭解如何解除安裝AEM Guides
source-git-commit: 5ac066bb8db32944abd046f64da11eeb1bdbe467
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 0%

---


# 解除安裝AEM Guides {#id21BHG0C0SXA}

您可以使用CRX封裝管理員解除安裝AEM Guides。 在解除安裝期間，存放庫的內容會還原為緊接在安裝套件之前建立的快照。

執行以下步驟以解除安裝AEM Guides：

1. 登入您的AEM執行個體並導覽至CRX封裝管理員。 存取封裝管理器的預設URL為：

   ```http
   http://<server name>:<port>/crx/packmgr/index.jsp
   ```

1. 搜尋com.adobe.fmdita套件。
1. 按一下封裝以將其展開。
1. 按一下 **更多** 以開啟下拉式清單。
1. 按一下 **解除安裝** 並等待解除安裝完成。
1. 如果您不再需要此套件，請按一下 **刪除** 解除安裝套件之後。

## 解除安裝之後

若要在解除安裝後清除剩餘檔案，請執行下列步驟：

1. 使用以下專案清除指令碼快取：

   ```http
   http://<host>:<port>/system/console/scriptcache
   ```

1. 您可以使用以下工具讓快取失效：

   ```http
   http://<host>:<port>/libs/granite/ui/content/dumplibs.rebuild.html?back=true
   ```

1. 按一下 **使快取失效**.
1. 清除瀏覽器的快取。

**父級主題：**[&#x200B;下載並安裝](download-install.md)

