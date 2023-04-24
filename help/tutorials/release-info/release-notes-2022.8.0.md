---
title: 發行說明 | Adobe Experience Manager指南as a Cloud Service,2022年8月發行版本
description: 8月發行Adobe Experience Manager指南as a Cloud Service
exl-id: a01bfe8a-4715-438c-bb94-aa1d31f6662d
source-git-commit: 67ba514616a0bf4449aeda035161d1caae0c3f50
workflow-type: tm+mt
source-wordcount: '1156'
ht-degree: 2%

---

# 8月發行Adobe Experience Manager指南as a Cloud Service

## 升級至8月版

升級您目前的Adobe Experience Manager指南as a Cloud Service(稍後稱為 *AEM指南as a Cloud Service*)，請執行下列步驟：
1. 查看Cloud Services的Git程式碼，並切換至Cloud Services管道中所設定的分支，該管道與您要升級的環境對應。
1. 更新 `<dox.version>` 屬性 `/dox/dox.installer/pom.xml` 檔案的Cloud ServicesGit程式碼。
1. 提交變更並執行Cloud Services管道，以升級至8月版AEM指南as a Cloud Service。

## 相容性矩陣

本節列出AEM指南as a Cloud Service2022年8月版本所支援軟體應用程式的相容性矩陣。

### FrameMaker和FrameMaker Publishing Server

| FMPS | FrameMaker |
| --- | --- |
| 不相容 | 2020更新4及更新版本 |
|  |  |

*從2020.2開始的FMPS版本支援在AEM中建立的基線和條件。

### 氧連接器

| AEM雲端版本指南 | 氧連接器窗口 | 氧連接器Mac |
| --- | --- | --- |
| 2022.8.0 | 2.7.5 | 2.7.5 |
|  |  |  |


## 新增功能和功能改善

AEM指南as a Cloud Service在8月版本中提供許多增強功能和新功能：

### 地圖編輯器中的版面檢視

現在，您可以在地圖編輯器中檢視DITA地圖的完整版面。 當您開啟地圖進行編輯時，它會開啟 **版面** 地圖編輯器的檢視。 在此檢視中，您可以在樹狀檢視中看到地圖階層，也可以在地圖中組織或建構主題。

![配置檢視](assets/layout-view-map.png)

「版面」檢視包含個別的工具列，可協助您對地圖中出現的主題執行許多工作。
您可以在地圖中插入主題參考、主題群組、索引鍵定義。 通過向上、向下、向左或向右移動，您可以重新組織地圖中呈現的主題。 您也可以拖放主題，以在地圖中移動主題。 地圖編輯器還提供可鎖定或解除鎖定檔案、檢查版本記錄，以及執行版本標籤管理的圖示。


「版面」檢視也提供 **檢視選項** 顯示或隱藏行號、顯示或隱藏複選框，或顯示映射中主題的檔案名或標題。


![view-options](assets/view-options.png)

您也可以根據套用至主題的條件篩選條件來檢視主題。

除了在映射檔案中組織主題外，您還可以使用 **選項** 「配置」視圖中的某個元素可用的菜單。 您也可以從存放庫面板拖放主題或地圖至地圖編輯器中開啟的地圖。

右側面板會在地圖編輯器的「版面」檢視中顯示「內容屬性」和「地圖屬性」。 為所選主題定義的內聯屬性將根據「佈局」視圖中的主題顯示。 例如，您可以快速找到將platform屬性定義為 `IOS`.

現在，您也可以設定主題或地圖的中繼資料資訊。 您可以定義所選主題或地圖的導覽標題、連結文字、簡短說明和關鍵字。

![「配置」視圖右面板](assets/layout-inline-attributes.png)

如需詳細資訊，請參閱 *版面檢視* 區段(使用Adobe Experience Manager指南as a Cloud Service)。

### 編輯器設定中的內嵌屬性

AEM指南現在允許設定 **內嵌屬性** 由管理員 **編輯器設定**. 您也可以新增內嵌屬性，或從 **內嵌屬性** 頁簽。
為主題定義的配置內聯屬性將根據「佈局」視圖中的主題顯示。

![編輯器設定](assets/editor-settings-inline-attributes.png)


### 儲存庫檢視中的其他篩選器

現在，存放庫檢視中的篩選器搜尋功能已變得更強大。 兩個新的搜索標準， **上次修改時間** 和 **標籤** 已新增，以篩選檔案和縮小AEM存放庫中的搜尋範圍：
* **上次修改時間**:您可以尋找在選取日期之後、在選取日期之前上次修改的檔案。 您也可以選擇使用預先定義的條件，並尋找在過去2小時、上週、上個月或去年修改過的檔案。
* **標籤**:您也可以尋找已套用特定標籤的檔案。 您可以輸入標籤，或從下拉式清單中選取標籤。

![儲存庫檢視篩選器](assets/repo-filter-search.png)


## 已修正的問題

以下列出各個區域中修正的錯誤：

* /core/article-publish/src/main/java/com/adobe/dxml/article/publish/util/DoxUtils.java(9291)中使用已棄用的Lucene索引
* 更新的Node.js不用於發佈。 (9835)
* DITA主題不會隨著在 **屬性** 頁面。 (8745)
* 新增至DITA書籤時，Frontmatter元素無法正常運作。 (9507)
* 原生PDF |會在使用 **快速產生** 的URL。 (9822)
* 原生PDF |附錄會發佈為PDF輸出中的章節。 (9829)
* 原生PDF |編輯SVG影像時，不會在頁面配置中顯示更新。 (9069)
* 當 `Nonbreaking Hyphen` 使用 **插入特殊字元** 對話框。 (8919)
* 如果已編輯更新的影像，則XML編輯器不會在主題中顯示這些影像。 (9500)
* 透過編輯器發佈輸出時，無法從 **輸出** 標籤。 (9100)
* DITA映射的子映射不會使用 **全選** 選項。 (9814)
* 無法從 **範本** 中的自定義映射模板。 (9846)
* 無法在映射或主題模板的子資料夾中建立新主題或映射模板。 (9888)
* 瀏覽存在於映射或主題模板的子資料夾中的主題或映射時，不存在任何選項。 (9889)
* 當Schematron檔案被更新並與DITA檔案一起保存時，不會顯示右面板（如果DITA檔案中斷了Schematron檔案中存在的驗證）。 (9986)
* 如果新的重複輸出預設集的名稱與現有預設集相同，則可建立此預設集。 (9997)
* SVG影像損毀，產生HTML輸出時無法正確發佈。 (9949)


## 已知問題

Adobe已找出下列AEM指南的已知問題(as a Cloud Service2022年8月發行)。

### 因應措施的已知問題

請針對下列已知問題使用指定的因應措施：

* 「佈局」視圖在「映射編輯器」中不可見。

   **因應措施**:更新資料夾設定檔中的ui_config.json。

* 已覆寫Symbols.json，因此發生問題8919。

   **因應措施**:更新的symbols.json必須與覆蓋的symbols.json合併。

### 其他已知問題

* 如果從對存放庫執行搜尋時顯示的結果區段中選取多個檔案，然後拖放至製作檢視中，則只會新增單一檔案。
