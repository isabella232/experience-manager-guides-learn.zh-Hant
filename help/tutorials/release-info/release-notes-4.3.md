---
title: 發行說明 |在Adobe Experience Manager Guides 4.3.0版本中的升級指示和修正問題
description: 瞭解錯誤修正以及如何升級至Adobe Experience Manager Guides 4.3.0版
source-git-commit: b53f76c2f0234c1ef6c65d954311e3f8c980ffe2
workflow-type: tm+mt
source-wordcount: '998'
ht-degree: 5%

---

# Adobe Experience Manager Guides 4.3.0版（2023年7月）

此發行說明涵蓋升級指示、相容性矩陣，以及Adobe Experience Manager Guides 4.3.0版修正的問題(以下稱 *AEM指南*)。

如需新功能和增強功能的詳細資訊，請參閱 [Adobe Experience Manager Guides 4.3.0版的新增功能](./whats-new-4.3-release.md).

## 升級至AEM Guides的4.3.0版


您可以輕鬆地將目前版本的AEM Guides升級至4.3.0版。在繼續升級至AEM Guides 4.3.0版之前，您必須考慮以下幾點：您可以將目前的AEM Guides版本升級至4.3.0版

- 如果您是使用4.2或4.2.x版，則可以直接升級至4.3.0版。
- 如果您使用的是4.1或4.1.x版，則必須先升級至4.2或4.2.x版，才能升級至4.3.0版。
- 如果您使用的是4.0版，則必須先升級至4.2版，才能升級至4.3.0版。
- 如果您使用的是3.8.5版，則必須先升級至4.0版，才能升級至4.2版。
- 如果您使用的是3.8.5之前的版本，請參閱產品特定安裝指南中的升級AEM Guides區段。



>[!NOTE]
>
>您必須先安裝AEM Service Pack，才能升級AEM Guides版本。

如需詳細資訊，請參閱 [升級指示](../install-guide/upgrade-xml-documentation.md).

## 相容性矩陣

本節列出AEM Guides 4.3.0版本支援之軟體應用程式的相容性矩陣。

### Adobe Experience Manager

**4.3.0非UUID**
版本6.5 Service Pack 18、17、16、15或14

**4.3.0 UUID**
版本6.5 Service Pack 18、17、16、15或14

如需詳細資訊，請參閱 *技術需求* 安裝與設定Adobe Experience Manager指南中的區段。

### FrameMaker和FrameMaker Publishing Server

| 發行 | FMPS 2022 | FMPS 2020 | Fm 2022 | Fm 2020 |
| --- | --- | --- | --- | --- |
| 4.3.0 （非UUID） | 2022或更高 | 2020.2或更新版本* | 2022或更高 | 2020.3或更高版本 |
| 4.3.0 (UUID) | 2022或更高 | 2020.2或更新版本* | 2022或更高 | 2020.4或更新版本 |
| | | | |

*從2020.2開始的FMPS版本支援AEM中建立的基準和條件。

### 氧氣聯結器

| 發行 | 氧氣聯結器視窗 | 氧氣聯結器Mac | 在氧氣視窗中編輯 | 在氧氣Mac中編輯 |
| --- | --- | --- |--- |--- |
| 4.3.0 （非UUID） | 2.3-regular-5 | 2.3-regular-5 | 1.6 | 1.6 |
| 4.3.0 (UUID) | 3.0-uuid-4 | 3.0-uuid-3 | 2.3 | 2.3 |
|  |  |   |

## 已修正的問題

以下列出各種區域中修正的錯誤：

### 編寫

- 雖然已選取「解除鎖定檔案」選項和「不儲存」選項，但不會在Web編輯器中解除鎖定主題檔案。 (12558)
- 無法簽出網頁編輯器中的檔案，儘管選擇NO選項在簽入前捨棄變更。 (12557)
- 在Web編輯器內的主工具列中，鎖定和解鎖檔案圖示的工具提示與「存放庫檢視」中顯示的圖示不一致。(12555)
- 「取消簽出」和「解除鎖定」選項會顯示在Web編輯器中尚未在「地圖檢視」中籤出的檔案。 (12556)
- 無法在現有的「topicref」連結中選取PDF資產。 (12477).
- 在表格中執行合併和分割時，AEM Guides 4.2會產生額外的表格儲存格。 (11793)
- 在「存放庫檢視」中，使用搜尋/篩選功能後無法拖曳主題或影像。 (12396)
- 開啟一個搜尋的檔案後，「尋找和取代」面板中的搜尋結果會停用。 (12142)
- 側邊鍵盤上的「8」數字鍵在AEM Guides編輯器中無法運作。 (12106)
- 內嵌/顯示屬性不會顯示在網頁編輯器的「版面」檢視中。 (12498)
- 全域設定檔UI設定與資料夾設定檔不相符。 (11970)
- 複製和貼上DITA檔案時，內容參照會損毀。 (11959)
- 安裝AEM Guides後即無法在欄檢視中編輯內容片段。 (7342)
- 當未包裝的xref位於子元素標籤下時，內容會遺失。 (12532)
- 從右側面板的「檔案」屬性將dostate變更為「結束狀態」時，核准工作流程無法運作。 (11026)
- 資產UI |在「清單」檢視中，無法合併覆蓋的可用欄。 (11528)
- 地圖檢視中未解析Keyref。 (11490)
- 透過XML編輯器導覽時，未顯示最上方選單。 (10868)
- `conref` 在ph標籤中 |顯示的瀏覽對話方塊不正確。 (9481)
- 指向其他元素的本機連結不會在網頁編輯器中解析。 (8790)
- Matches()函式在schematron功能中無法運作。 (11224)



### 管理

- DITA map中繼資料屬性中的「標題」欄位會由覆寫 `<title>` 對應元素。 (10702)
- 當嘗試開啟或更新基準線中的主題版本時，「從伺服器擷取資訊」載入器會無限期執行。(12478)


### 評論

- 新檢閱UI |條件會醒目提示，且顯示隱藏的工作方式與在Web編輯器中有所不同。 (11628)

### 發佈

- 重新命名原生PDF預設集時發佈失敗。 (12564)
- 複製原生PDF範本會複製到預設範本位置，而不是提供的自訂範本位置。 (12563)
- 原生PDF |語言中繼資料無法在產生的PDF中設定以符合WCAG 2.0。 (12407)
- 從Pod讀取可能已重新整理或重新啟動的暫存檔時，發佈至AEM網站失敗。 (12113)
- 原生PDF |自訂屬性不會傳播至暫時HTML或PDF引擎。 (DXML-12005)
- 原生PDF |發佈大型內容時發生Java OutOfMemoryError。 (11789)
- 原生PDF | Xref正在列印href主題標題的內容而非Xref標籤。 (11322)
- 原生PDF |無法儲存PDF範本設定。 (10751)
- 原生PDF |文字延伸超過欄寬，包含多個xref。 (10876)
- 原生PDF | `<note>``</note>` 元素不會產生其型別的額外範圍標題。 (10549)
- JSON輸出 | `fmUuid` JSON的jcr：content節點上的屬性與JSON內的「id」不同。 (11564)
- JSON輸出 |如果存在具有相同檔案名稱的對映和主題，則會移除對映的JSON。 (11524)

## 已知問題

Adobe已發現AEM Guides 4.3.0版的下列已知問題：

- 基本範本中定義的通用頁面配置未套用為預設範本。

  解決方法：新增通用頁面版面作為封底和封面，然後它會開始出現每個頁面。
- 在AEM Service Pack 16或17的AEM網站輸出頁面中搜尋時，網站搜尋會發生問題。

  因應措施：

   1. 開啟檔案，路徑為： `/libs/foundation/components/search/search.jsp` 在 `crx/de`
   1. 將行號234取代為下列代碼：

      ```
      <a href="<c:url value="${hit.URL}" context="/"/>" onclick="trackSelectedResult(this, ${status.index + 1})"><%= xssAPI.filterHTML(((Search.Hit) pageContext.getAttribute("hit")).getTitle()) %></a>
      
      *(Add the missing closing anchor tag at the end).
      ```

   1. 儲存檔案。