---
title: 發行說明 | Adobe Experience Manager指南as a Cloud Service,2022年9月發行版本
description: 最新版Adobe Experience Manager指南as a Cloud Service
source-git-commit: 748a37298849b3fbf6079c19de3cb052dee3a464
workflow-type: tm+mt
source-wordcount: '1284'
ht-degree: 3%

---

# 最新版Adobe Experience Manager指南as a Cloud Service

## 升級至最新版本

升級您目前的Adobe Experience Manager指南as a Cloud Service(稍後稱為 *AEM指南as a Cloud Service*)，請執行下列步驟：
1. 查看Cloud Services的Git程式碼，並切換至Cloud Services管道中所設定的分支，該管道與您要升級的環境對應。
2. 更新 `<dox.version>` 屬性 `/dox/dox.installer/pom.xml` 檔案的Cloud ServicesGit程式碼。
3. 提交變更並執行Cloud Services管道，以升級至最新版本的AEM指南as a Cloud Service。

## 為現有內容建立索引的步驟

執行以下步驟來建立現有內容的索引，並在映射級別使用新的查找和替代文字：
* 對伺服器執行POST請求（使用正確的驗證） —  `http://<server:port>/bin/guides/map-find/indexin`.
(可選：您可以傳遞映射的特定路徑來為其建立索引，預設情況下，所有映射都將編製索引 ||範例：   `https://<Server:port>/bin/guides/map-find/indexing?paths=<map_path_in_repository>`)
* API會傳回jobId。 要檢查作業的狀態，可以向相同的終點發送具有作業ID的GET請求 —  `http://<server:port>/bin/guides/map-find/indexing?jobId={jobId}`
(例如： `http://<_localhost:8080_>/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678)`
* 作業完成後，上述GET要求會以成功回應，並在地圖失敗時提及。 可以從伺服器日誌中確認已成功索引的映射。


## 相容性矩陣

本節列出AEM指南as a Cloud Service於2022年9月發行版本所支援軟體應用程式的相容性矩陣。

### FrameMaker和FrameMaker Publishing Server

| FMPS | FrameMaker |
| --- | --- |
| 不相容 | 2020更新4及更新版本 |
|  |  |

*從2020.2開始的FMPS版本支援在AEM中建立的基線和條件。

### 氧連接器

| AEM雲端版本指南 | 氧連接器窗口 | 氧連接器Mac | 在氧氣窗口中編輯 | 在Oxion Mac中編輯 |
| --- | --- | --- | --- | --- |
| 2022.9.0 | 2.7.13 | 2.7.13 | 2.3 | 2.3 |
|  |  |  |  |


## 新增功能和功能改善

AEM指南as a Cloud Service在最新版本中提供許多增強功能和新功能：


### 根據標籤建立動態基線

現在「AEM指南」提供您根據標籤建立動態基線的功能。 如果生成基線、下載基線或使用基線建立翻譯項目，則會根據更新的標籤動態挑選檔案。 更新標籤時不需要修改基線，因此此功能很實用。
您也可以將基線的快照匯出為CSV。

![建立基線](assets/dynamic-baseline.png)

### 在地圖層級尋找並取代文字

您現在可以在地圖中搜尋包含特定文字的檔案。 在檔案中會反白顯示搜尋的文字。 您也可以將搜尋的字詞或片語取代為檔案中的其他字詞或片語。
選取 **取代** 表徵圖以替換當前出現的 **全部替換檔案** 表徵圖，替換選定檔案中的所有出現次數。

![在地圖中查找替換](assets/map-find-replace.png)

依預設，選項 **取代前的結帳檔案** 和 **替換後建立新版本** ，因此在替代文字之前會簽出檔案，並在替代文字後建立新版本。

### 從翻譯控制面板查看「不同步」檔案的版本差異

您現在可以選擇翻譯 **不同步** 檔案，根據主題兩個版本之間所做的變更。\
![翻譯控制面板](assets/translation-version-diff.png)
從翻譯控制面板，您可以輕鬆查看上次翻譯版本與所選檔案的目前版本之間的差異。

![版本差異對話](assets/version-diff.png)

您可以根據差異決定是否要翻譯主題。

### PDF預設集可用的中繼資料UI

您可以從DITA映射的輸出預設集設定元資料。 您可以設定標題、作者、主旨和關鍵字中繼資料。 此中繼資料會對應至輸出PDF的「檔案屬性」中的中繼資料。
此元資料會覆寫在書籍層級定義的中繼資料。 您可以在每個輸出預設集中具體定義中繼資料，並傳遞至輸出PDF。

![預設集中的中繼資料](assets/preset-metadata.png)


## 已修正的問題

以下列出各個區域中修正的錯誤：

* Web編輯器 |在主題內移動元素時，元素上指派的ID會由自動指派的ID覆寫。 (7895)
* 追蹤變更 |使用Enter鍵輸入新元素時，內容會遺失。 (10246)
* 未建立dita-templates中引用主映射的子映射。 (10231)
* XML編輯器 |複製貼上在製作模式中無法運作。 (10309)
* 選取多個版本標籤後，即不會取消選取。 (9561)
* 自動導覽至網站瀏覽對話方塊中的路徑，無法如同檔案瀏覽般運作。 (9920)
* 從切換時大綱面板不顯示內容 **作者** to **來源** 模式。 (10319)
* 在使用主題範本中的內容建立的新主題中建立Conref無法運作。 複製的雜湊ID不會在內容復本中更新。 (9890)
* 網頁編輯器 |從地圖範本建立地圖時，沒有載入器存在。 (9891)
* 新地圖編輯器 |如果從 **作者** 到 **版面** 檢視。 (10218)
* 新地圖編輯器 |無法從「佈局」(Layout)視圖中刪除應用於任何引用的條件。 (10213)
* 新地圖編輯器 |套用條件參考在「配置」檢視中無法如「作者」檢視般運作。 (10198)
* 新地圖編輯器 |如果不能向左移動引用，則從上下文菜單向左移動該引用。 (10219)
* 新地圖編輯器 |在使用「佈局」視圖建立的映射中，引用的表徵圖顯示不正確。 (10197)
* 存放庫面板 |在存放庫面板中按一下滑鼠右鍵會發生應用程式錯誤。 (10123)
* 查找和替換 |在網頁編輯器中無法讀取搜尋結果的深色模式。 (9978)
* 翻譯 |元資料和標籤不會傳播到翻譯的副本。 (4696)
* 複製貼上(ctrl+c/ctrl+v)內容會在製作模式中擲回錯誤。 (10304)
* PDF範本 |將背景影像新增至任何頁面版面配置時，會顯示「影像路徑」絕對值，而影像不會顯示在輸出PDF中。 (10297)
* 原生PDF |章節標題和章節標題在PDF發佈中無法運作。 (9947)
* 原生PDF | `xref` 無法正確解析特定DITA主題的概念。 (10229)
* 原生PDF |無法在生成的PDF輸出中查看表的標題文本。 (9827)
* 原生PDF |在PDF輸出中，附錄中的參考不會顯示為附錄。 (10182)
* 原生PDF |表的幀屬性不傳播到臨時HTML（作為類）。 (10353)
* 原生PDF |臨時HTML檔案將colsep和rowsep類添加到td和，即使它們的值在源DITA中為0。 (10352)
* 原生PDF |頁面配置中新增之條件的中繼資料不會接受。 (10377)
* 原生PDF |產生PDF會對特定內容失敗。 (9927)
* 原生PDF |不會在PDF輸出中顯示透過conkeyref的內容。 (9836)
* 原生PDF |沒有解析包含影像或外部連結的Keydef的關鍵引用。 (10063)
* 地圖的作者檢視未顯示表格清單和圖表清單的預留位置文字。 (10330)
* 建立新基線時，不會應用已選基線篩選器。 (9954)
* 如果父資料夾名稱包含空格字元，則基線中缺少視訊檔案。 10031)
* 當使用者時區與伺服器時區不同時，建立基線時不會挑選最新版本。 (10190)
* 在AEM 6.5.12上安裝AEM指南4.1後，Control + F快速鍵沒有在Assets Console上開啟瀏覽器搜尋強制回應視窗。 (10189)


## 已知問題

Adobe已找出下列AEM指南的已知問題(as a Cloud Service2022年9月版本)。


* 動態基線未與知識庫發佈整合。

* 翻譯 |由於目標內容中的任何更改，源內容的版本差異表徵圖將出現。