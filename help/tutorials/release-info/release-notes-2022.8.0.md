---
title: 發行說明 | Adobe Experience Manager Guidesas a Cloud Service，2022年8月發行
description: Adobe Experience Manager Guidesas a Cloud Service8月版
source-git-commit: 880cd344ceb65ea339be699ebcad41c0d62e168a
workflow-type: tm+mt
source-wordcount: '1169'
ht-degree: 0%

---

# Adobe Experience Manager Guidesas a Cloud Service8月版

## 升級至8月版

as a Cloud Service升級您目前的Adobe Experience Manager Guides (稍後稱為 *AEM Guidesas a Cloud Service*)進行設定，請執行以下步驟：
1. 檢視Cloud Service的Git程式碼，並切換到在Cloud Service管線中設定的分支，該分支與您要升級的環境相對應。
1. 更新 `<dox.version>` 中的屬性 `/dox/dox.installer/pom.xml` 將Cloud Service Git程式碼的檔案設為2022.8.167。
1. 提交變更並執行Cloud Service管道，以升級至AEM Guides的8月版本as a Cloud Service。

## 相容性矩陣

本節列出AEM Guides 2022年8月as a Cloud Service發行版本支援之軟體應用程式的相容性矩陣。

### FrameMaker和FrameMaker Publishing Server

| FMPS | FrameMaker |
| --- | --- |
| 不相容 | 2020 Update 4及更新版本 |
| | |

*從2020.2開始的FMPS版本支援AEM中建立的基準和條件。

### 氧氣聯結器

| AEM Guides as a Cloud版本 | 氧氣聯結器視窗 | 氧氣聯結器Mac |
| --- | --- | --- |
| 2022.8.0 | 2.7.5 | 2.7.5 |
|  |  |  |


## 新功能和增強功能

AEM Guidesas a Cloud Service在8月版本中提供許多增強功能和新功能：

### 地圖編輯器中的版面配置檢視

現在您可以在Map編輯器中檢視DITA map的完整版面。 當您開啟地圖進行編輯時，它會開啟 **版面** 地圖編輯器的檢視。 在此檢視中，您可以在樹狀檢視中檢視對映階層，也可以在對映中組織或建構主題。

![版面配置檢視](assets/layout-view-map.png)

「版面」檢視包含個別的工具列，可協助您在地圖中的主題上執行許多工作。
您可以在地圖中插入主題參照、主題群組、索引鍵定義。 您可以透過向上移動、向下移動、向左移動或向右移動來重新組織地圖中顯示的主題。 您也可以拖放主題，在地圖中移動主題。 「對應編輯器」也提供圖示來鎖定或解除鎖定檔案、檢查版本記錄以及執行版本標籤管理。


「配置」檢視也提供 **檢視選項** 若要顯示或隱藏行號、顯示或隱藏核取方塊，或顯示地圖中主題的檔案名稱或標題。


![view-options](assets/view-options.png)

您也可以根據主題上套用的條件篩選器來檢視主題。

除了在地圖檔案中組織主題外，您還可以使用 **選項** 功能表可供配置檢視中的元素使用。 您也可以從存放庫面板將主題或地圖拖放至在「地圖編輯器」中開啟的地圖。

右側面板會顯示地圖編輯器的「版面」檢視中的「內容屬性」和「地圖屬性」 。 針對所選主題定義的「內嵌屬性」會針對「版面」檢視中的主題顯示。 例如，您可以快速找到所有將平台屬性定義為 `IOS`.

現在您也可以設定主題或地圖的中繼資料資訊。 您可以為所選主題或地圖定義導覽標題、連結文字、簡短說明和關鍵字。

![版面檢視右面板](assets/layout-inline-attributes.png)

如需詳細資訊，請參閱 *版面配置檢視* 區段在「使用Adobe Experience Manager Guides」中的as a Cloud Service。

### 編輯器設定中的內嵌屬性

AEM Guides現在允許設定 **內嵌屬性** 由您的管理員從 **編輯器設定**. 您也可以新增內嵌屬性，或從以下專案刪除現有屬性： **內嵌屬性** 索引標籤中的「編輯器設定」。
為主題定義的已設定內嵌屬性會針對「版面」檢視中的主題顯示。

![編輯器設定](assets/editor-settings-inline-attributes.png)


### 存放庫檢視中的其他篩選器

現在，存放庫檢視中的篩選器搜尋已變得更強大。 兩個新的搜尋條件， **上次修改時間** 和 **標籤** 已新增來篩選檔案，以及縮小您在AEM存放庫中的搜尋：
* **上次修改時間**：您可以尋找在選定日期之後但在選定日期之前上次修改的檔案。 您也可以選擇使用預先定義的條件，並尋找過去2小時、上週、上個月或去年上次修改的檔案。
* **標籤**：您也可以尋找已套用特定標籤的檔案。 您可以輸入標籤或從下拉式清單中選取標籤。

![存放庫檢視篩選器](assets/repo-filter-search.png)


## 已修正的問題

以下列出各種區域中修正的錯誤：

* /core/article-publish/src/main/java/com/adobe/dxml/article/publish/util/DoxUtils.java中使用過時的Lucene索引(9291)
* 更新的Node.js不用於發佈。 (9835)
* DITA主題不會隨著對所做的變更自動更新 **屬性** 頁面。 (8745)
* Frontmatter元素在新增至DITA bookmap時無法正常運作。 (9507)
* 原生PDF |使用時產生空白PDF **快速產生** 適用於多個檔案。 (9822)
* 原生PDF |附錄作為PDF輸出中的章節發佈。 (9829)
* 原生PDF |編輯SVG影像時，其未顯示在頁面配置中更新。 (9069)
* 一般連字元會在 `Nonbreaking Hyphen` 使用插入字元 **插入特殊字元** 對話方塊。 (8919)
* 如果更新後的影像已經過編輯，XML編輯器不會在主題中顯示這些影像。 (9500)
* 透過編輯器發佈輸出時，無法從刪除預設集 **輸出** 標籤。 (9100)
* DITA map的子地圖不會使用 **全選** 選項。 (9814)
* 無法從拖放地圖或主題範本 **範本** 功能表到網頁編輯器中的自訂地圖範本。 (9846)
* 無法在地圖或主題範本的子資料夾中建立新主題或地圖範本。 (9888)
* 目前沒有選項可瀏覽出現在地圖或主題範本的子資料夾中的主題或地圖。 (9889)
* 當與DITA檔案一起更新並儲存Schematron檔案時，不會顯示右側面板（如果DITA檔案破壞Schematron檔案中存在的驗證）。 (9986)
* 如果名稱與現有預設集相同，則可建立新的重複輸出預設集。 (9997)
* SVG影像已損毀，且在產生HTML輸出時無法正確發佈。 (9949)


## 已知問題

Adobe已確認2022年8月as a Cloud Service發行的AEM Guides存在下列已知問題。

### 因應措施的已知問題

針對下列已知問題使用指定的因應措施：

* 「配置圖編輯器」中看不到「配置圖檢視」。

  **因應措施**：更新資料夾設定檔中的ui_config.json。

* 已覆寫Symbols.json，因此會出現8919問題。

  **因應措施**：更新的symbols.json必須與覆寫的symbols.json合併。

### 其他已知問題

* 如果在對存放庫執行搜尋時從顯示的結果區段中選取了多個檔案，然後在作者檢視中拖放，則只會新增一個檔案。
