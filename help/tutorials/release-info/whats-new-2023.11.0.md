---
title: 發行說明 | Adobe Experience Manager Guides的新增功能，2023年11月發行
description: 在2023年11月發行的Adobe Experience Manager Guidesas a Cloud Service中瞭解新增和增強功能。
exl-id: 83c04e01-92f1-41b0-8866-a202f4106b51
source-git-commit: 57ff1a3b6ceb9debc8e29065fd37cab21adc1b96
workflow-type: tm+mt
source-wordcount: '797'
ht-degree: 0%

---

# 2023年11月版Adobe Experience Manager Guides的as a Cloud Service新增功能

本文介紹2023年11月Adobe Experience Manager Guides版本的新功能和增強功能(以下稱為 *Experience Manager指南as a Cloud Service*)。

如需有關升級指示、相容性矩陣，以及此版本中修正問題的詳細資訊，請檢視 [發行說明](release-notes-2023.11.0.md).

## 原生PDF增強功能

下列原生PDF增強功能已在2023年11月版本中完成：

### 使用和複製現成可用的PDF範本

Experience Manager指南提供現成或原廠的PDF範本。 複製工廠PDF範本以建立自訂PDF範本。

現在，您也可以在建立和複製範本時，預覽範本的縮圖影像。 您也可以編輯或刪除此影像。 此功能對於品牌化或區分具有類似名稱的範本非常有用。
進一步瞭解 [PDF範本](../native-pdf/pdf-template.md).

![複製PDF範本對話方塊](assets/duplicate-template.png){width="550" align="left"}

*複製現有的PDF範本。*


### 變更頁面順序並每張工作表發佈多個頁面

除了根據來原始檔發佈頁面外，您也可以在發佈多頁檔案時，變更PDF的頁面順序。  這可讓您靈活地以各種順序發佈頁面，例如先發佈所有奇數或所有偶數頁面。 您也可以以小冊子的形式發佈，並像書籍一樣閱讀頁面。 您也可以決定要在單張紙上發佈的頁數。 如需詳細資訊，請檢視 [頁面組織](../native-pdf/components-pdf-template.md#page-organization) 區段。

### 根據排序索引鍵排序字彙表辭彙

現在，您也可以根據排序索引鍵來排序字彙表辭彙。 您可以使用標籤&#39;sort-as&#39;來定義辭彙表的排序索引鍵。 然後，您可以根據排序索引鍵來排序它們，以取代詞語。 這可讓您根據不同語言中使用的辭彙來排序字彙表辭彙。 您也可以為具有片語或一組字詞的辭彙表辭彙定義單一排序索引鍵。
如需詳細資訊，請檢視 [進階PDF設定](../native-pdf/components-pdf-template.md#advanced-pdf-settings).


### 改善原生PDF範本的資源管理

Experience Manager指南現在已改善原生PDF範本的資源管理。 您現在可以在多個原生PDF範本間共用及重複使用資源，例如影像、CSS檔案和字型檔案。 經過這項改善後，管理大量範本的資源就變得簡單多了。 您不需要為每個範本建立重複資源，您可以將它們儲存在共用資料夾中，並在所有原生PDF範本中使用它們。
如需詳細資訊，請檢視 [PDF範本](../native-pdf/pdf-template.md).

## Web Editor增強功能

下列Web Editor增強功能已在2023年11月版本中完成：


### 依標題或檔案名稱檢視檔案

您現在可以選擇在Web編輯器中檢視檔案的預設方式。 您可以從「作者」檢視中，依不同面板的標題或檔案名稱來檢視檔案清單。

![使用者偏好設定對話方塊](assets/user-preferences-2311.png){width="550" align="left"}

*變更檢視檔案的預設方式，從&#x200B;**使用者偏好設定**對話方塊。*


### 管理條件預設集

您可以在DITA主題中定義條件屬性。 然後，使用條件預設集中的條件屬性，在DITA map中發佈內容。 Experience Manager指南現在也可讓您從網頁編輯器建立和管理條件預設集。 您也可以輕鬆進行編輯、複製或刪除。

![來自網頁編輯器「管理」標籤的條件預設集 ](assets/web-editor-manage-condition-presets.png){width="550" align="left"}

如需詳細資訊，請檢視 [使用條件預設集](../user-guide/generate-output-use-condition-presets.md).

### 在重新整理瀏覽器時還原檔案索引標籤

當您重新整理瀏覽器時，「Experience Manager指南」會恢復網頁編輯器中已開啟檔案標籤的狀態。 如需詳細資訊，請檢視 **編輯檔案時重新整理瀏覽器** 區段在 [在網頁編輯器中編輯主題](../user-guide/web-editor-edit-topics.md).

### 輕鬆解除元素包裝

現在，您可以使用網頁編輯器元素內容功能表中的選項，輕鬆地將元素解除包裝。 這可協助您輕鬆地將元素的文字與其上層元素合併。
如需詳細資訊，請檢視 **解除元素包裝** 區段來自 [網頁編輯器中的其他功能](../user-guide/web-editor-other-features.md).

### 用來移動游標的鍵盤快速鍵

Experience Manager參考線現在也可讓您使用鍵盤快速鍵在網頁編輯器中移動游標。 您可以使用鍵盤快速鍵，快速向左或向右移動一個單字。 您也可以在鍵盤快速鍵的協助下移至行的開頭或結尾。
現在，您也可以使用鍵盤快速鍵，將游標移至下一個元素的開頭或上一個元素的結尾。
進一步瞭解 [網頁編輯器中的鍵盤快速鍵](../user-guide/web-editor-keyboard-shortcuts.md).
