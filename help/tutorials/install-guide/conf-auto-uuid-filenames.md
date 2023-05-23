---
title: 基於UUID配置自動檔案名
description: 瞭解如何根據UUID配置自動檔案名
source-git-commit: 801c306fa120e7889d4b9428fd5bee2849bf1956
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---


# 基於UUID配置自動檔案名 {#id205QG070D5Z}

預設情況下，建立主題或映射檔案時，作者也會獲得一個選項來指定檔案名。 作者可以根據其要求自由指定檔案名。 但是，這會帶來不一致性，在大型文檔系統中可以看到大量檔案名稱。 作為管理員，您可以限製作者為在系統中建立的檔案分配檔案名。 對於每個新主題或映射檔案，您可以選擇自動分配基於UUID的檔案名。

執行以下步驟，自動為系統中建立的所有新檔案分配基於UUID的檔案名：

1. 開啟「Adobe Experience ManagerWeb控制台配置」頁。

   訪問配置頁的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索並按一下 *com.adobe.fmdita.xmleditor.config.XmlEditorConfig* 捆綁。

1. 選擇 **使用基於UUID的系統檔案名** 的雙曲餘切值。

1. 按一下「**儲存**」。


>[!NOTE]
>
> 預設情況下，此選項為OFF。 開啟此選項後，作者在建立新主題或映射檔案時將看不到指定檔案名的選項。 可以從資產UI和Web編輯器建立新主題或映射檔案。

**父主題：**[&#x200B;配置檔案名](conf-file-names.md)

