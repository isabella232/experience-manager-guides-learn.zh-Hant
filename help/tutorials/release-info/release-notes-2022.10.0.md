---
title: 發行說明 |Adobe Experience Manager指南as a Cloud Service,2022年10月發佈
description: 《Adobe Experience Manager指南》10月發行as a Cloud Service
exl-id: 38638080-625c-49c3-9e54-56cc23831546
source-git-commit: 67ba514616a0bf4449aeda035161d1caae0c3f50
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 4%

---

# 《Adobe Experience Manager指南》10月發行as a Cloud Service

## 升級到10月版

升級您當前的Adobe Experience Manager指南as a Cloud Service(稍後稱為 *導AEM線as a Cloud Service*)，請執行以下步驟：
1. 檢出Cloud Services的Git代碼，並切換到在Cloud Services管道中配置的與要升級的環境對應的分支。
1. 更新 `<dox.version>` 物業 `/dox/dox.installer/pom.xml` Cloud ServicesGit代碼的檔案2022.10.183。
1. 提交更改並運行Cloud Services管道以升級到10月版的「指南」AEMas a Cloud Service。

## 相容性矩陣

本節列出了2022年10月as a Cloud Service版本指南支AEM持的軟體應用程式的相容性表。

### FrameMaker和FrameMaker發佈伺服器

| FMPS | 幀製作器 |
| --- | --- |
| 不相容 | 2020年更新4及更高版本 |
|  |  |

*從2020.2開始的AEMFMPS版本支援中建立的基線和條件。

### 氧連接器

| 作AEM為雲版本的指南 | 氧連接器窗口 | 氧連接器Mac | 在氧氣窗口中編輯 | 在氧氣Mac編輯 |
| --- | --- | --- | --- | --- |
| 2022.10.0 | 2.7.13 | 2.7.13 | 2.3 | 2.3 |
|  |  |  |  |


## 新增功能和功能改善

指AEM南as a Cloud Service在10月版中提供了增強功能和新功能：


### 快速生成面板

「Now AEM Guides（現在參考線）」提供 **快速生成** 面板，幫助您快速生成和查看為DITA映射建立的預設的輸出。

![快速生成表徵圖](assets/quick-generate-icon.png)

在 **快速生成** 面板中，您可以看到為DITA映射建立的所有輸出預設的清單。

![快速生成面板](assets/quick-generate-panel.png)

選擇一個或多個預設並快速生成輸出。 您還可以快速查看為預設生成的輸出。 在輸出的生成上顯示成功消息。 如果輸出生成失敗，將顯示錯誤消息。 您還可以查看錯誤日誌，以查看生成過程中發生的錯誤的詳細資訊。


## 已修正的問題

以下列出了在不同區域修復的錯誤：

* 本地PDF |從PDF輸出中刪除僅資源主題時出錯。 (10554)
* 本地PDF |空鍵引用將出現在PDF輸出中。 (10553)
* 本地PDF | `navtitle` 為 `topichead` 沒有榮譽。 (10509)
* 本地PDF |需要支援amd64 JDK風格。 (10465)
* 本地PDF |無法從目錄中隱藏前言主題。 (10355)
* 本地PDF |重新啟動章節佈局中的頁碼會從上一章的末尾開始隨機編號。 (10154)
* Chrome瀏覽器 |在從UI中拖放任何元素時，螢幕將變為空白。 例如，在從「條件」面板中拖動條件時。 (10524)
* 在資產的複製貼上操作後，節點屬性將被刪除。 (10053)
* 按一下  **關閉** 用戶被重定向到「資產」 — 該體驗已被糾正，以將用戶帶到主AEM頁。 (9654)
