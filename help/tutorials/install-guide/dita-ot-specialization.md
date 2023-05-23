---
title: 使用自定義DITA-OT和DITA專用化
description: 瞭解如何使用自定義DITA-OT和DITA專用化
source-git-commit: 5ac066bb8db32944abd046f64da11eeb1bdbe467
workflow-type: tm+mt
source-wordcount: '2075'
ht-degree: 0%

---


# 使用自定義DITA-OT和DITA專用化 {#id181GAJ0005Z}

DITA Open Toolkit \(DITA-OT\)是一組基於Java的開源工具，可為DITA映射和主題內容提供處理。 指AEM南使您能夠輕鬆導入和使用自定義DITA-OT插件。 導入後AEM，可將參考線配置為使用自定義DITA-OT插件以任何格式生成輸出。 在生成輸出時，只需選擇DITA-OT選項，AEM參考線使用自定義DITA-OT插件來生成所需的輸出。

如果要在發佈任何輸出時處理Ant參數，AEM「參考線」為您提供了一種簡單的方法。 您可以指定要使用的Ant參數，然後由發佈進程處理。

>[!NOTE]
>
> DITA-AEMOT 3.3.2版隨附了指南。但是，AEM指南支援DITA-OT 1.7及更高版本。 有關DITA-OT版本的完整清單，請參見 [DITA-OT版本](http://www.dita-ot.org/download)。

>[!TIP]
>
> 查看 *DITA-OT配置檔案配置* 和 *使用自定義DITA-OT* 關於使用自定義DITA-OT插件的最佳實踐指南中的各節。

## 使用自定義DITA-OT插件 {#id181NH1020L7}

使用自定義DITA-OT插件進行發佈有兩種方法。 第一種方法是將自定義DITA-OT插件上載到儲存AEM庫。 另一種方法是將自定義DITA-OT插件保存在伺服器上，建立配置式，並在配置式中提供自定義DITA-OT插件的位置。

預設情況下，AEM參考線附帶一個預配置的配置檔案，其中包含用於編輯和發佈內容的預設模板的配置。 您可以建立自定義配置檔案，其中包含在編輯文檔和自定義DITA-OT插件以發佈內容時使用的自定義模板。

輔助線提供的預設DITA-OTAEM包隨Apache FOP XSL-FO處理器一起提供，該處理器不支援呈現MathML方程。 如果在內容中使用MathML方程式，請確保已將MathML呈現引擎插件整合到Apache FOP，或使用其他XSL-FO處理器。

>[!IMPORTANT]
>
> 如果已將AEM參考線從2.2版升級到2.5.1或2.6版，則通過配置管理器所做的所有更改將自動被拾取並儲存在預設配置檔案中。

執行以下步驟將自定義DITA-OT插件上載到儲存AEM庫：

1. 登錄並AEM開啟CRXDE Lite模式。

1. 下載 `DITA-OT.ZIP` 的子菜單。

   位置 `DITA-OT.ZIP` 檔案 `/libs/fmdita/dita_resources/DITA-OT.zip`。

   ![](assets/dita-ot-zip-in-crx.png)

1. 解壓伺服器上zip檔案的內容。

1. 使用DITA-OT插件整合器機制將新版本的DITA-OT與自定義DITA-OT插件整合。

   >[!NOTE]
   >
   > 插件ZIP檔案中的類路徑分隔符與作業系統相關，這意味著如果伺服器托管在Windows上，則類路徑分隔符將不同於Linux上使用的類路徑分隔符。 有關手動整合插件的詳細資訊，請參見 *手動安裝插件* DITA-OT文檔中的主題。

1. 再次建立ZIP檔案，並保留相同的名稱\(`DITA-OT.ZIP`\)和資料夾結構。

1. 將更新的ZIP檔案上載回存AEM儲庫。

   上載ZIP檔案之前，請確保執行以下檢查：

   - 在Mac/Linux作業系統上運行整合器\（安裝自定義插件\），以避免檔案分隔符問題 — 因為Windows和Linux作業系統具有不同的檔案分隔符，因此在Mac/Linux作業系統上整合的插件與Windows和Linux安裝程式相容。
   - 確保 `DITA-OT.ZIP` 檔案包含名為「DITA-OT」的資料夾，該資料夾包含所有相關插件和檔案。
   - 檢查 `DITA-OT.ZIP` 您建立的檔案屬於mimeType:&quot;nt:file&quot; \(這與上載到\時的ZIP檔案的主類AEM型相對應)。 使用WebDAV工具或代碼部署將此ZIP檔案上載到中的所需路AEM徑。 \(不要使用包管AEM理器部署此ZIP檔案，因為此ZIP不是內AEM容包，而只是存檔檔案。\)

   >[!NOTE]
   >
   > 建議不要覆蓋預設的DITA-OT包。 您應將包含插件的自定義DITA-OT包上載到 `apps` 的子菜單。

1. 開啟預設DITA配置檔案進行編輯，並保存它\（不進行任何更新\），以使更改生效。


執行以下步驟來建立新配置檔案，並將其配置為使用儲存在伺服器上的自定義DITA-OT插件：

1. 將自定義DITA-OT插件儲存在伺服器上。

   >[!NOTE]
   >
   > 用於儲存自定義DITA-OT插件的資料夾結構應為： `\*<parent-folder\>*\DITA-OT`。

1. 按一下頂部的Adobe Experience Manager連結，然後選擇 **工具**。

1. 選擇 **參考線** 的雙曲餘切值。

1. 按一下 **DITA配置檔案** 平鋪。

   >[!NOTE]
   >
   > 「配置檔案」(Profiles)頁面上顯示「預設配置檔案」(Default Profile)資訊。 如果已將AEM參考線從2.2版升級到2.5.1或2.6版，則通過配置管理器所做的所有更改將自動被拾取並儲存在預設配置檔案中。

1. 您可以選擇編輯預設配置檔案、建立新配置檔案或從預設配置檔案中複製設定以建立新配置檔案。

   >[!NOTE]
   >
   > 您可以更新預設配置檔案，但不能將其刪除。 但是，您可以編輯和刪除您建立的所有新配置檔案。

1. 配置以下屬性以使用自定義DITA-OT插件：

   | 屬性名稱 | 說明 |
   |-------------|-----------|
   | **設定檔屬性** |
   | 設定檔名稱 | 為此配置檔案提供唯一名稱。 |
   | 重用輸出 | *\（可選\）* 如果您的配置檔案基於現有配置檔案，則選擇此選項。 選擇此選項可AEM確保參考線不會再次提取DITA-OT包的內容並重新使用現有的DITA-OT包。 |
   | 配置檔案提取路徑 | *\（可選\）* 指定DITA-OT保留在磁碟上的路徑。 預設情況下，AEM參考線將DITA-OT包捆綁在其儲存庫中，並在此路徑的磁碟上提取。<br>**注釋** 可以使用任何現有系統變數或屬性定義此路徑。 請參閱 [DITA-OT環境變數](#id181NH0YN0AX) 的子菜單。 |
   | 分配的路徑 | \(*可選*\)指定此配置檔案適用的內容儲存庫中的路徑。 可以指定多個位置。 |
   | **DITA-OT屬性** |
   | DITA-OT超時 | \(*可選*\)指定指南等待DITA-OT插件AEM響應的時間\（秒\）。 如果在指定時間內收到任何響應，AEM則指南將終止發佈任務，並將任務標籤為失敗。 此外，故障日誌在輸出生成日誌檔案中可用。 <br>預設值：300秒\（5分鐘\） |
   | DITA-OTPDF參數 | 指定由自定義DITA-OT插件處理以生成PDF輸出的命令行參數。 對於所有自定義DITA-OT配置檔案，指定以下命令行參數：`-lib plugins/org.dita.pdf2.fop/lib/` |
   | DITA-OT參AEM數 | \(*可選*\)指定由自定義DITA-OT插件處理以生成站點輸出的自定義命令行AEM參數。 |
   | DITA-OT庫路徑 | \(*可選*\)指定DITA-OT插件的其他庫路徑。 |
   | DITA-OT生成XML | \(*可選*\)指定與自定義DITA-OT插件捆綁的自定義Ant生成指令碼的路徑。 此路徑相對於檔案系統上的DITA-OT目錄。 |
   | DITA-OT Ant指令碼資料夾 | \（可選\）指定DITA-OT Ant指令碼資料夾的路徑。 此路徑相對於檔案系統上的DITA-OT目錄。 |
   | DITA-OT環境變數 | *\（可選\）* 指定要傳遞到DITA-OT進程的環境變數。 預設情況下，「參考AEM線」會添加四個變數 —  `ANT_OPTS`。 `ANT_HOME`。 `PATH`, `CLASSPATH`。 <br> 您可以重新使用任何現有系統環境變數或屬性來構建新的環境變數。 例如，如果 `JAVA_HOME` 系統中定義的系統變數，並且您要定義稱為 `JAVA_BIN` 用 `JAVA_HOME`。 然後，可以添加 `JAVA_BIN` 為：<br> `JAVA_BIN= ${JAVA_HOME}/bin` <br> **注釋** 也可以使用Java系統屬性來生成環境變數。 例如，如果AEM啟動指令碼定義Java系統屬性 `java.io.tmpdir` 到臨時目錄時，可以使用此屬性將新變數定義為： `${java.io.tmpdir}/fmdita/dita_ot`。 <br> **重要** 要重用任何現有系統變數或屬性，必須將其包含在 `${}`。 |
   | 覆蓋DITA-OT輸出 | *\（可選\）* 如果選擇此選項，則可以指定本地系統上可用的DITA-OT包，以使用DITA-OT生成輸出。 此配置在激活ConfigManager時設定。 <br> 如果要指定儲存在伺服器上的DITA-OT包的路徑，AEM請取消選擇此選項。 |
   | AEMDITA-OT Zip路徑/本地DITA-OT目錄路徑 | 根據您在覆蓋DITA-OT輸出中的選擇，指定儲存自定義DITA-OT.zip檔案的完整路徑。 這可能是儲存庫或本AEM地系統中的路徑。 |
   | DITA-OT插件路徑 | 自定義插件的路徑。 此插件將自動與主DITA-OT包整合。 |
   | 整合目錄 | \(*可選*\)儲存庫中自定義DTD和XSD catalog.xml檔案的路AEM徑。 僅當DITA-OT包中缺少目錄時才應提供此選項。 這些目錄將作為插件自動與主DITA-OT整合。 |
   | 添加系統ID目錄 | \(*可選*\)僅當目錄中缺少公共ID項或DITA檔案僅使用與上載它們的伺服器路徑相對的系統ID時，才選擇此選項。 |
   | DITA-OT臨時路徑 | *\（可選\）* 指定複製DITA檔案以進行處理的臨時位置。 在DITA-OT處理檔案之前，這些檔案會在此臨時位置複製。 預設情況下，臨時儲存位置為： <br> **注釋** 可以使用任何現有系統變數或屬性定義此路徑。 請參閱 [DITA-OT環境變數](#id181NH0YN0AX) 的子菜單。 |

   >[!NOTE]
   >
   >  GuidesAEM安裝程式會建立兩個環境變數，您可以使用這些變數指定自定義DITA-OT插件檔案的路徑。 這些環境變數是：DITAOT\_DIR，它包含檔案系統上DITA-OT目錄的路徑；和DITAMAP\_DIR ，其中包含在檔案系統上提取DITA映射內容的路徑。

1. 按一下 **完成** 的子菜單。


>[!NOTE]
>
> 您可以將自定義DITA配置檔案導出為包，並上載到其AEM他參考線實例以節省時間。 有關詳細資訊，請參見 [附錄](appendix.md)。

## 整合DITA專用化 {#id211MB0E00XA}

DITA專用化是通過添加新元素或刪除現有元素來建立新DITA結構的過程。 要建立新的DITA元素，可以將現有DITA元素作為基，並根據創作要求對其進行修改。 本質上，DITA專業化允許您建立符合業務要求的自定義資訊模型，同時保留現有DITA體系結構的優勢。

可以使用配置檔案功能儲存自定義DITA專用化設定。 然後，在創作和發佈自定義DITA內容時可使用這些設定。 指AEM南允許您在自定義DTD/XSD中使用公共ID和系統ID。

>[!NOTE]
>
> 指AEM南Web編輯器不支援XSD。

執行以下步驟建立新配置檔案並將其配置為使用專用的DTD和XSDAEM指南：

1. 在本地電腦上建立包含專用DTD和XSD的專用資料夾。

1. 在 `catalog.xml` 必須包含在專用資料夾中的檔案。

   >[!NOTE]
   >
   > 在DITA 1.3的情況下，DTD的預設位置 `catalog.xml` 儲存庫中AEM的檔案為： `/libs/fmdita/dita_resources/DITA-1.3/dtd/catalog.xml`。

1. 在中指定XSD詳細資訊 `catalog.xml` 必須包含在專用資料夾中的檔案。

   >[!NOTE]
   >
   > 在DITA 1.3的情況下，儲存庫中XSD catalog.xml檔案的預設位AEM置是： `/libs/fmdita/dita_resources/DITA-1.3/xsd/catalog.xml`。

1. 將資料夾上載到以下位置：

   `/libs/fmdita/dita_resources`

1. 按一下頂部的Adobe Experience Manager連結，然後選擇 **工具**。

1. 選擇 **參考線** 的雙曲餘切值。

1. 按一下&#x200B;**DITA配置檔案** 平鋪。

   >[!NOTE]
   >
   > 「配置檔案」(Profiles)頁面上顯示「預設配置檔案」(Default Profile)資訊。 如果已將AEM參考線從2.2版升級到2.5.1或2.6版，則通過配置管理器所做的所有更改將自動被拾取並儲存在預設配置檔案中。

1. 您可以選擇編輯預設配置檔案、建立新配置檔案或從預設配置檔案中複製設定以建立新配置檔案。

   >[!NOTE]
   >
   > 無法刪除預設配置檔案。 但是，您可以編輯和刪除您建立的所有新配置檔案。

1. 在 **架構** \> **目錄** 設定，指定自定義DTD和XSD的路徑 `catalog.xml` 文AEM件。

1. 選擇 **添加系統ID目錄** 的雙曲餘切值。

   >[!NOTE]
   >
   > 僅當目錄中缺少公共ID條目，或DITA檔案僅使用相對於上載它們的本地檔案路徑的系統ID時，才選擇此選項。

   有關「概要檔案」頁上其他屬性的詳細資訊，請參閱中的「屬性」表 [步驟6](#id17A9F0D075Z) 的 [使用自定義DITA-OT插件](#id181NH1020L7) 的子菜單。

1. 按一下 **完成** 的子菜單。


>[!NOTE]
>
> 您可以將自定義DITA配置檔案導出為包，並上載到其AEM他參考線實例以節省時間。 有關詳細資訊，請參見 [附錄.md](appendix.md)。

