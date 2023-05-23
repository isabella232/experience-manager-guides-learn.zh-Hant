---
title: 卸載指AEM南
description: 瞭解如何卸載指南AEM
source-git-commit: 5ac066bb8db32944abd046f64da11eeb1bdbe467
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 0%

---


# 卸載指AEM南 {#id21BHG0C0SXA}

可以使用CRXAEM包管理器卸載指南。 在卸載過程中，儲存庫的內容將還原為在安裝軟體包之前立即建立的快照。

執行以下步驟卸載指AEM南：

1. 登錄到實AEM例並導航到CRX包管理器。 訪問包管理器的預設URL為：

   ```http
   http://<server name>:<port>/crx/packmgr/index.jsp
   ```

1. 搜索com.adobe.fmdita包。
1. 按一下包展開它。
1. 按一下 **更多** 開啟下拉清單。
1. 按一下 **卸載** 並等待卸載完成。
1. 如果您不再需要此包，請按一下 **刪除** 卸載軟體包後。

## 卸載後

要在卸載後清除剩餘檔案，請執行以下步驟：

1. 使用：

   ```http
   http://<host>:<port>/system/console/scriptcache
   ```

1. 可以使用以下方法使快取無效：

   ```http
   http://<host>:<port>/libs/granite/ui/content/dumplibs.rebuild.html?back=true
   ```

1. 按一下 **失效快取**。
1. 清除瀏覽器的快取。

**父主題：**[&#x200B;下載並安裝](download-install.md)

