---
title: 發行說明 | Adobe Experience Manager指南as a Cloud Service,2022年10月發行
description: 10月版Adobe Experience Manager指南as a Cloud Service
exl-id: 38638080-625c-49c3-9e54-56cc23831546
source-git-commit: 4183162142f5f6291fdb6e832e10b46a3c0da73a
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 4%

---

# 10月版Adobe Experience Manager指南as a Cloud Service

## 升級至10月版

升級您目前的Adobe Experience Manager指南as a Cloud Service(稍後稱為 *AEM指南as a Cloud Service*)，請執行下列步驟：
1. 查看Cloud Services的Git程式碼，並切換至Cloud Services管道中所設定的分支，該管道與您要升級的環境對應。
2. 更新 `<dox.version>` 屬性 `/dox/dox.installer/pom.xml` 檔案中的Git程式碼。2022.10.183
3. 提交變更並執行Cloud Services管道，以升級至10月版的AEM指南as a Cloud Service。

## 相容性矩陣

本節列出AEM指南as a Cloud Service於2022年10月發行的軟體應用程式的相容性矩陣。

### FrameMaker和FrameMaker Publishing Server

| FMPS | FrameMaker |
| --- | --- |
| 不相容 | 2020更新4及更新版本 |
|  |  |

*從2020.2開始的FMPS版本支援在AEM中建立的基線和條件。

### 氧連接器

| AEM雲端版本指南 | 氧連接器窗口 | 氧連接器Mac | 在氧氣窗口中編輯 | 在Oxion Mac中編輯 |
| --- | --- | --- | --- | --- |
| 2022.10.0 | 2.7.13 | 2.7.13 | 2.3 | 2.3 |
|  |  |  |  |


## 新增功能和功能改善

AEM指南as a Cloud Service提供10月發行版本的增強功能和新功能：


### 快速產生面板

現在，AEM指南提供 **快速產生** 面板，可協助您快速產生並檢視為DITA映射建立的預設集輸出。

![快速生成表徵圖](assets/quick-generate-icon.png)

在 **快速產生** 面板中，您可以查看為DITA映射建立的所有輸出預設集的清單。

![快速產生面板](assets/quick-generate-panel.png)

選取一或多個預設集並快速產生輸出。 您也可以快速檢視為預設集產生的輸出。 產生輸出時會顯示成功訊息。 如果輸出產生失敗，則會顯示錯誤訊息。 您也可以檢視錯誤記錄，以查看產生程式中發生之錯誤的詳細資訊。


## 已修正的問題

以下列出各個區域中修正的錯誤：

* 原生PDF |從PDF輸出中刪除僅資源主題時出錯。 (10554)
* 原生PDF |空的「鍵參」(Keyref)出現在PDF輸出中。 (10553)
* 原生PDF | `navtitle` for `topichead` 不遵守。 (10509)
* 原生PDF |支援amd64 JDK的風格。 (10465)
* 原生PDF |無法隱藏目錄中的Frontmatter主題。 (10355)
* 原生PDF |重新啟動章節版面中的頁碼會隨機從上一章的結尾開始編號。 (10154)
* Chrome瀏覽器 |從UI拖放任何元素時，畫面會變空。 例如，從「條件」面板拖曳條件時。 (10524)
* 資產的複製貼上作業後，節點屬性會遭到移除。 (10053)
* 按一下  **關閉** 系統將使用者重新導向至assets — 已修正體驗，將使用者帶往AEM首頁。 (9654)
