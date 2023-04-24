---
title: 發行說明 | Adobe Experience Manager指南as a Cloud Service,2022年4月發行版本
description: 4月發行的Adobe Experience Manager指南as a Cloud Service
exl-id: c735ba24-a803-454b-8723-57dacf90061b
source-git-commit: 67ba514616a0bf4449aeda035161d1caae0c3f50
workflow-type: tm+mt
source-wordcount: '799'
ht-degree: 3%

---

# 4月發行的Adobe Experience Manager指南as a Cloud Service

## 升級至4月版

升級您目前的 [!DNL Adobe Experience Manager Guides] as a Cloud Service(稍後稱為 *[!DNL AEM Guides]as a Cloud Service*)，請執行下列步驟：
1. 查看Cloud Services的Git程式碼，並切換至Cloud Services管道中所設定的分支，該管道與您要升級的環境對應。
1. 更新 `<dox.version>` 屬性 `/dox/dox.installer/pom.xml` 檔案的Git程式碼。
1. 提交變更並執行Cloud Services管道以升級至的4月版 [!DNL AEM Guides] as a Cloud Service。

## 相容性矩陣

本節列出了支援的軟體應用程式的相容性矩陣 [!DNL AEM Guides] as a Cloud Service於2022年4月發行。

### FrameMaker和FrameMaker Publishing Server

| FMPS | FrameMaker |
| --- | --- |
| 不相容 | 2020更新4及更新版本 |
|  |  |


### 氧連接器

| AEM指南雲端版本 | 氧連接器窗口 | 氧連接器Mac |
| --- | --- | --- |
| 2022.4.0 | 2.5.6 | 2.5.6 |
|  |  |  |

*從2020.2開始的FMPS版本支援在AEM中建立的基線和條件。

## 新增功能和功能改善

網頁編輯器中已新增許多增強功能和新功能：

### 改進密鑰解析度

DITA內容索引鍵參考會將一部分內容從一個主題插入另一個主題。 它會使用鍵來尋找內容。 需要解析與DITA主題相關聯的鍵引用。 所選根映射的優先順序最高，以解析鍵引用。

![用戶首選項對話框](assets/user-preferences.png)

現在，關鍵參考會根據根映射集，依下列優先順序加以解析：

1. 使用者偏好設定
1. 地圖檢視面板
1. 資料夾配置檔案

如需詳細資訊，請參閱 *解析關鍵引用* 一節。

### 在左側面板中新增自訂面板

現在，您可以在Web編輯器的左側面板中新增自訂面板。 您可以將自訂面板用於各種用途，例如提供協助或針對專案進行測試。 若已設定自訂面板，該面板也會出現在 **編輯器設定**. 您可以切換開關以顯示或隱藏自訂面板。

### 能夠更改DITA映射中主題的文檔狀態

現在，您可以輕鬆更改DITA映射中所選主題的文檔狀態。 您也可以從 **更多選項** 菜單。

![所選主題屬性](assets/map-view-properties.png)

### 在「預覽」模式中顯示的版本資訊

網頁編輯器可協助您管理版本。 現在，您也可以在主題的「預覽」模式中，在主題的檔案索引標籤的右上角看到活動主題或DITA映射的版本。

![預覽版本](assets/preview-version.png)

## 已修正的問題

以下列出各個區域中修正的錯誤：

* 新標籤不會自動反映在新增/移除標籤下拉式清單中，而是需要基線重新整理。 (9249)
* 如果基線是由標籤條件建立，則無法編輯基線標題。 (9171)
* 如果基線狀態變更為「失敗」，使用基線的發佈工作會卡在「等候」狀態。 (9194)
* 移除直接參照上的標籤也會移除間接參照中的標籤。 (9257)
* 在您鍵入時進行搜索會導致在「儲存庫」視圖中出現不想要的搜索請求。 (9307)
* 在索引標籤的標題中使用任何關鍵字時會發生問題。 (9318)
* 基線無法新增含有空格的標籤。 (9362)
* AEM網站輸出未正確顯示辭彙元素。 (8936)
* 開啟 **輸出** 頁簽。 (8715)
* 通過Salesforce發佈手動記錄類型時顯示的錯誤消息不直觀。 (8952)
* 使用條件屬性設定進行驗證時不會立即開啟，而是使用者需要重新開啟檔案才能查看驗證。 (9300)
* 使用中繼資料發佈DITA映射後，無法移除中繼資料。  (9178)
* 即使在地圖編輯器中開啟DITA映射時，也會顯示翻譯面板。 (9053)
* 用戶定義的自定義DTD不優先於DITA-OT中嵌入的標準DITA DTD。 (9104)
* 在原生PDF功能中，範本中的上傳對非DITA和非影像檔案失敗。 (9070)
* 在某些特殊情況下，授權機制會執行兩個查詢，而非一個查詢。 (9221)
* 使用自定義DTD發佈AEM站點輸出失敗。 (9243)
* 逐項參考腳注不會捲動至AEM網站輸出中的腳注區段。 (9234)

## 已知問題

Adobe已在 [!DNL AEM Guides] as a Cloud Service於4月發行。

* 以相同名稱建立兩個或多個基線，但有空間或大小寫差異時，Web編輯器不會報告錯誤。 例如，「adobe」和「Adobe」或「Adobe」。
* 在執行頻繁登錄或註銷或在不同身份驗證類型之間切換時，氧連接器間歇性掛起。
