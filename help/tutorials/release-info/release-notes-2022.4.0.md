---
title: 發行說明 |Adobe Experience Manager指南as a Cloud Service,2022年4月發佈
description: 《Adobe Experience Manager指南》4月發行as a Cloud Service
exl-id: c735ba24-a803-454b-8723-57dacf90061b
source-git-commit: 67ba514616a0bf4449aeda035161d1caae0c3f50
workflow-type: tm+mt
source-wordcount: '799'
ht-degree: 3%

---

# 《Adobe Experience Manager指南》4月發行as a Cloud Service

## 升級到4月版

升級當前 [!DNL Adobe Experience Manager Guides] as a Cloud Service(後者稱為 *[!DNL AEM Guides]as a Cloud Service*)，請執行以下步驟：
1. 檢出Cloud Services的Git代碼，並切換到在Cloud Services管道中配置的與要升級的環境對應的分支。
1. 更新 `<dox.version>` 物業 `/dox/dox.installer/pom.xml` Cloud ServicesGit代碼的檔案2022.4.133。
1. 提交更改並運行Cloud Services管道以升級到 [!DNL AEM Guides] as a Cloud Service。

## 相容性矩陣

本節列出了支援的軟體應用程式的相容性清單 [!DNL AEM Guides] as a Cloud Service2022年4月發佈。

### FrameMaker和FrameMaker發佈伺服器

| FMPS | 幀製作器 |
| --- | --- |
| 不相容 | 2020年更新4及更高版本 |
|  |  |


### 氧連接器

| 指AEM南雲發佈 | 氧連接器窗口 | 氧連接器Mac |
| --- | --- | --- |
| 2022.4.0 | 2.5.6 | 2.5.6 |
|  |  |  |

*從2020.2開始的AEMFMPS版本支援中建立的基線和條件。

## 新增功能和功能改善

Web編輯器中添加了許多增強功能和新功能：

### 改進了密鑰解析

DITA內容鍵引用將一部分內容從一個主題插入另一個主題。 它使用一個鍵來定位內容。 需要解析與DITA主題關聯的鍵引用。 所選根映射的優先順序最高，用於解析鍵引用。

![用戶首選項對話框](assets/user-preferences.png)

現在，關鍵引用將根據根映射集按以下優先順序順序解析：

1. 使用者偏好設定
1. 「映射視圖」面板
1. 資料夾配置檔案

有關詳細資訊，請參閱 *解析鍵引用* 中。

### 在左面板中添加自定義面板

現在，您可以在Web編輯器的左面板中添加一個自定義面板。 您可以使用自定義面板進行各種目的，例如為項目提供幫助或進行測試。 如果已配置了自定義面板，則它還會出現在 **編輯器設定**。 可以切換開關以顯示或隱藏自定義面板。

### 能夠更改DITA映射中主題的文檔狀態

現在，您可以輕鬆更改DITA映射中選定主題的文檔狀態。 您還可以從 **更多選項** 按鈕。

![所選主題屬性](assets/map-view-properties.png)

### 在「預覽」模式下顯示的版本資訊

Web編輯器可幫助您管理版本。 現在，您還可以在主題的預覽模式下查看活動主題或主題檔案頁籤右上角的DITA映射的版本。

![預覽版本](assets/preview-version.png)

## 已修正的問題

以下列出了在不同區域修復的錯誤：

* 新標籤不會自動反映在「添加/刪除」標籤下拉清單中，而是需要「基線」刷新。 (9249)
* 如果基線是按標籤條件建立的，則無法編輯基線標題。 (9171)
* 如果基線狀態更改為「失敗」，則使用基線發佈作業將陷入「等待」狀態。 (9194)
* 刪除直接參照上的標籤也會從間接參照中刪除標籤。 (9257)
* 在鍵入時進行搜索會在「儲存庫」視圖中引發不需要的搜索請求。 (9307)
* 在頁籤的標題中使用任何關鍵字時會出現問題。 (9318)
* 基線在添加具有空格的標籤時失敗。 (9362)
* 站AEM點輸出未正確顯示辭彙表元素。 (8936)
* 開啟時出現控制台錯誤 **輸出** 的子菜單。 (8715)
* 通過Salesforce發佈手動記錄類型時顯示的錯誤消息不直觀。 (8952)
* 不會立即開啟條件屬性設定驗證，而是用戶需要重新開啟檔案以查看驗證。 (9300)
* 一旦DITA映射與元資料一起發佈，則無法刪除元資料。  (9178)
* 即使在映射編輯器中開啟DITA映射時，翻譯面板也可見。 (9053)
* 用戶定義的自定義DTD不優先於DITA-OT中嵌入的標準DITA DTD。 (9104)
* 在本機PDF功能中，非DITA和非映像檔案在模板中上載失敗。 (9070)
* 授權機制在某些特殊情況下執行兩個查詢而不是一個查詢。 (9221)
* 使用自AEM定義DTD發佈站點輸出失敗。 (9243)
* 按引用使用腳注不會滾動到站點輸出中的腳AEM注部分。 (9234)

## 已知問題

Adobe已在 [!DNL AEM Guides] as a Cloud Service的4月份。

* 當建立兩個或兩個以上具有相同名稱但有空格或大小寫差異的基線時，Web編輯器不會報告錯誤。 例如，&quot;adobe&quot;和&quot;Adobe&quot;或&quot;Adobe&quot;。
* 在執行頻繁登錄或註銷或在不同身份驗證類型之間切換時，氧連接器間歇性掛起。
