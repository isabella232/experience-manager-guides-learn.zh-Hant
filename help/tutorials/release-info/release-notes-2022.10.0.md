---
title: 發行說明 | Adobe Experience Manager Guidesas a Cloud Service，2022年10月發行
description: Adobe Experience Manager Guidesas a Cloud Service10月版
exl-id: 38638080-625c-49c3-9e54-56cc23831546
source-git-commit: 67ba514616a0bf4449aeda035161d1caae0c3f50
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 4%

---

# Adobe Experience Manager Guidesas a Cloud Service10月版

## 升級至10月版

as a Cloud Service升級您目前的Adobe Experience Manager Guides (稍後稱為 *AEM指南as a Cloud Service*)進行設定：
1. 檢視Cloud Services的Git程式碼，並切換到在Cloud Services管道中設定的分支，該分支與您要升級的環境相對應。
1. 更新 `<dox.version>` 中的屬性 `/dox/dox.installer/pom.xml` 將您的Cloud Services Git程式碼檔案改成2022.10.183。
1. 提交變更並執行Cloud Services管道，以升級至10月版的AEM Guidesas a Cloud Service。

## 相容性矩陣

本節列出AEM Guides 2022年10月as a Cloud Service發行版本支援之軟體應用程式的相容性矩陣。

### FrameMaker和FrameMaker Publishing Server

| FMPS | FrameMaker |
| --- | --- |
| 不相容 | 2020 Update 4及更高版本 |
|  |  |

*自2020.2開始的FMPS版本支援AEM中建立的基準和條件。

### 氧氣聯結器

| AEM Guides as a Cloud版本 | 氧氣聯結器視窗 | 氧氣聯結器Mac | 在氧氣視窗中編輯 | 在氧氣Mac中編輯 |
| --- | --- | --- | --- | --- |
| 2022.10.0 | 2.7.13 | 2.7.13 | 2.3 | 2.3 |
|  |  |  |  |


## 新增功能和功能改善

AEM Guidesas a Cloud Service在10月發行版本中提供增強功能和新功能：


### 快速產生面板

現在AEM Guides提供 **快速產生** 面板可協助您快速產生並檢視針對DITA map建立的預設集輸出。

![「快速產生」圖示](assets/quick-generate-icon.png)

在 **快速產生** 面板中，您可以看到為DITA map建立的所有輸出預設集清單。

![快速產生面板](assets/quick-generate-panel.png)

選取一或多個預設集並快速產生輸出。 您也可以快速檢視針對預設集產生的輸出。 成功訊息會顯示在產生的輸出上。 如果輸出產生失敗，則會顯示錯誤訊息。 您也可以檢視錯誤記錄，以檢視產生程式中所發生錯誤的詳細資訊。


## 已修正的問題

修復了各種區域的錯誤如下所列：

* 原生PDF |從PDF輸出中移除僅限資源的主題時發生錯誤。 (10554)
* 原生PDF |PDF輸出中出現空白的Keyref。 (10553)
* 原生PDF | `navtitle` 的 `topichead` 不接受。 (10509)
* 原生PDF |支援amd64 JDK風格。 (10465)
* 原生PDF |無法從目錄隱藏前導主題。 (10355)
* 原生PDF |在章節版面中隨機重新啟動頁碼會從上一個章節的結尾開始編號。 (10154)
* Chrome瀏覽器 |從UI拖放任何元素時，畫面會變空白。 例如，從「條件」面板拖曳條件時。 (10524)
* 在資產的複製貼上操作後，節點屬性會被移除。 (10053)
* 按一下  **關閉** 已將使用者重新導向至資產 — 已更正體驗，將使用者帶至AEM首頁。 (9654)
