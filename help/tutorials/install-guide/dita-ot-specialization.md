---
title: 使用自訂DITA-OT和DITA專業化
description: 瞭解如何使用自訂DITA-OT和DITA專業化
source-git-commit: 5ac066bb8db32944abd046f64da11eeb1bdbe467
workflow-type: tm+mt
source-wordcount: '2075'
ht-degree: 0%

---


# 使用自訂DITA-OT和DITA專業化 {#id181GAJ0005Z}

DITA Open Toolkit \(DITA-OT\)是一組Java型開放原始碼工具，可處理DITA map和主題內容。 AEM Guides可讓您輕鬆匯入和使用自訂DITA-OT外掛程式。 匯入後，AEM Guides可設定為使用自訂DITA-OT外掛程式來產生任何格式的輸出。 產生輸出時，只要選取DITA-OT選項即可，AEM Guides會使用自訂DITA-OT外掛程式來產生所需的輸出。

如果您想在發佈任何輸出時處理Ant引數，AEM Guides會為您提供簡單的方法。 您可以指定要使用的Ant引數，然後由發佈程式處理相同的引數。

>[!NOTE]
>
> AEM Guides隨DITA-OT版本3.3.2提供。不過，AEM Guides支援DITA-OT 1.7版及更新版本。 如需DITA-OT版本的完整清單，請參閱 [DITA-OT版本](http://www.dita-ot.org/download).

>[!TIP]
>
> 請參閱 *DITA-OT設定檔組態* 和 *使用自訂DITA-OT* 最佳作法指南中的區段，以取得使用自訂DITA-OT外掛程式的最佳作法。

## 使用自訂DITA-OT外掛程式 {#id181NH1020L7}

有兩種方式可使用自訂DITA-OT外掛程式進行發佈。 第一種方法是將自訂DITA-OT外掛程式上傳至AEM存放庫。 另一種方法是在伺服器上儲存自訂DITA-OT外掛程式、建立設定檔並在設定檔中提供自訂DITA-OT外掛程式的位置。

根據預設，AEM Guides隨附預先設定的設定檔，其中包含用於編輯和發佈內容的預設範本設定。 您可以使用自訂範本建立自訂設定檔，以便在編輯檔案時以及自訂DITA-OT外掛程式以發佈內容時使用。

AEM Guides提供的預設DITA-OT套件附帶Apache FOP XSL-FO處理器，該處理器不支援轉譯MathML方程式。 如果您在內容中使用MathML方程式，請確定您已整合適用於Apache FOP的MathML轉譯引擎外掛程式，或使用不同的XSL-FO處理器。

>[!IMPORTANT]
>
> 如果您已將AEM Guides從2.2版升級至2.5.1版或2.6版，則會自動挑選透過Configuration Manager進行的所有變更，並儲存在「預設設定檔」中。

執行以下步驟，將自訂DITA-OT外掛程式上傳至AEM存放庫：

1. 登入AEM並開啟CRXDE Lite模式。

1. 下載 `DITA-OT.ZIP` 檔案。

   的位置 `DITA-OT.ZIP` 檔案為 `/libs/fmdita/dita_resources/DITA-OT.zip`.

   ![](assets/dita-ot-zip-in-crx.png)

1. 解壓縮伺服器上zip檔案的內容。

1. 使用DITA-OT外掛程式整合器機制，將新版DITA-OT與自訂DITA-OT外掛程式整合。

   >[!NOTE]
   >
   > 外掛程式ZIP檔案中的類別路徑分隔符號取決於作業系統，這表示如果您的伺服器託管於Windows上，則類別路徑分隔符號將不同於Linux上使用的類別。 如需手動整合外掛程式的詳細資訊，請參閱 *手動安裝外掛程式* DITA-OT檔案中的主題。

1. 再次建立ZIP檔案，保留相同的名稱\(`DITA-OT.ZIP`\)和資料夾結構。

1. 將更新後的ZIP檔案上傳回AEM存放庫。

   上傳ZIP檔案之前，請先確認下列檢查：

   - 在Mac/Linux作業系統上執行整合程式\（以安裝自訂外掛程式\），以避免檔案分隔符號的問題 — 由於Windows和Linux作業系統有不同的檔案分隔符號，所以在Mac/Linux作業系統上整合的外掛程式會與Windows和Linux安裝程式相容。
   - 確保 `DITA-OT.ZIP` 檔案包含名為「DITA-OT」的資料夾，其中包含所有相關的外掛程式和檔案。
   - 檢查 `DITA-OT.ZIP` 您建立的檔案為mimeType： &quot;nt：file&quot; \(這與上傳至AEM時的ZIP檔案主要型別相對應\)。 使用WebDAV工具或程式碼部署，將此ZIP檔案上傳至AEM中的所需路徑。 \(請勿使用AEM封裝管理員來部署此ZIP檔案，因為此ZIP不是AEM內容封裝，而只是封存檔案。\)

   >[!NOTE]
   >
   > 建議不要覆寫預設的DITA-OT套件。 您應該將包含外掛程式的自訂DITA-OT套件上傳至 `apps` 資料夾。

1. 開啟預設的DITA設定檔進行編輯並儲存\（不進行任何更新\），以使變更生效。


執行以下步驟來建立新的設定檔，並將其設定為使用儲存在伺服器上的自訂DITA-OT外掛程式：

1. 將自訂DITA-OT外掛程式儲存在伺服器上。

   >[!NOTE]
   >
   > 儲存自訂DITA-OT外掛程式的資料夾結構應為： `\*<parent-folder\>*\DITA-OT`.

1. 按一下頂端的Adobe Experience Manager連結，然後選擇 **工具**.

1. 選取 **指南** 工具清單中的。

1. 按一下 **DITA設定檔** 圖磚。

   >[!NOTE]
   >
   > 「預設設定檔」資訊會顯示在「設定檔」頁面上。 如果您已將AEM Guides從2.2版升級至2.5.1版或2.6版，則會自動挑選透過Configuration Manager進行的所有變更，並儲存在「預設設定檔」中。

1. 您可以選擇編輯「預設設定檔」、建立新設定檔，或從「預設設定檔」複製設定以建立新設定檔。

   >[!NOTE]
   >
   > 您可以更新預設設定檔，但無法刪除它。 但是，您可以編輯和刪除您建立的所有新設定檔。

1. 設定下列屬性以使用自訂DITA-OT外掛程式：

   | 屬性名稱 | 說明 |
   |-------------|-----------|
   | **設定檔屬性** |
   | 設定檔名稱 | 為此設定檔提供唯一名稱。 |
   | 重複使用輸出 | *\（可選\）* 如果您的設定檔是以現有的設定檔為基礎，請選取此選項。 選取此選項可確保AEM Guides不會再次擷取DITA-OT套件的內容，而會重複使用現有的DITA-OT套件。 |
   | 設定檔擷取路徑 | *\（可選\）* 指定DITA-OT保留在磁碟上的路徑。 依預設，AEM Guides會將DITA-OT套件組合到其存放庫中，並在此路徑解壓縮到磁碟上。<br>**注意** 您可以使用任何現有系統變數或屬性來定義此路徑。 請參閱說明 [dita-OT環境變數](#id181NH0YN0AX) 屬性以取得詳細資訊。 |
   | 指派的路徑 | \(*可選*\)指定此設定檔適用的內容存放庫路徑。 您可以指定多個位置。 |
   | **DITA-OT屬性** |
   | DITA-OT逾時 | \(*可選*\)指定AEM Guides等待來自DITA-OT外掛程式之回應的時間\（以秒為單位）。 如果在指定時間內未收到回應，AEM Guides會終止發佈工作，並將工作標籤為失敗。 此外，輸出產生記錄檔中也提供了失敗記錄。 <br>預設值： 300秒\（5分鐘\） |
   | dita-OTPDF引數 | 指定由自訂DITA-OT外掛程式處理以產生PDF輸出的命令列引數。 對於所有自訂DITA-OT設定檔，請指定下列命令列引數：`-lib plugins/org.dita.pdf2.fop/lib/` |
   | DITA-OT AEM引數 | \(*可選*\)指定自訂DITA-OT外掛程式處理用來產生AEM Site輸出的自訂命令列引數。 |
   | DITA-OT程式庫路徑 | \(*可選*\)指定DITA-OT外掛程式的其他程式庫路徑。 |
   | DITA-OT建置XML | \(*可選*\)指定自訂DITA-OT外掛程式隨附的自訂Ant建置指令碼路徑。 此路徑是相對於檔案系統上的DITA-OT目錄。 |
   | DITA-OT Ant指令碼資料夾 | \（可選\）指定DITA-OT Ant指令碼資料夾的路徑。 此路徑是相對於檔案系統上的DITA-OT目錄。 |
   | dita-OT環境變數 | *\（可選\）* 指定要傳遞至DITA-OT程式的環境變數。 AEM Guides預設會新增四個變數 —  `ANT_OPTS`， `ANT_HOME`， `PATH`、和 `CLASSPATH`. <br> 您可以重複使用任何現有的系統環境變數或屬性來建立新的環境變數。 例如，如果您擁有 `JAVA_HOME` 系統中定義的系統變數，而您想要定義一個新的環境變數，稱為 `JAVA_BIN` 建立方式 `JAVA_HOME`. 然後，您可以新增的定義 `JAVA_BIN` 作為：<br> `JAVA_BIN= ${JAVA_HOME}/bin` <br> **注意** 您也可以使用Java系統屬性來建置環境變數。 例如，如果AEM啟動指令碼定義Java系統屬性 `java.io.tmpdir` 至暫存目錄，您可以使用此屬性來定義新變數為： `${java.io.tmpdir}/fmdita/dita_ot`. <br> **重要** 若要重複使用任何現有的系統變數或屬性，必須將它括在 `${}`. |
   | 覆寫DITA-OT輸出 | *\（可選\）* 如果選取此選項，則您可以指定本機系統上可用的DITA-OT套件，以使用DITA-OT產生輸出。 此設定是在ConfigManager啟動時設定。 <br> 如果要指定儲存在AEM伺服器上的DITA-OT套件的路徑，請取消選取此選項。 |
   | AEM DITA-OT Zip路徑/本機DITA-OT目錄路徑 | 根據您在「覆寫DITA-OT輸出」中所做的選擇，指定儲存自訂DITA-OT.zip檔案的完整路徑。 這可能是您的AEM存放庫或本機系統中的路徑。 |
   | DITA-OT外掛程式路徑 | 自訂外掛程式的路徑。 此外掛程式會自動與主要DITA-OT套件整合。 |
   | 整合目錄 | \(*可選*\) AEM存放庫中自訂DTD和XSD catalog.xml檔案的路徑。 只有在DITA-OT套件中遺漏目錄時，才應提供此專案。 這些目錄會作為外掛程式自動與主要DITA-OT整合。 |
   | 新增系統ID目錄 | \(*可選*\)只有在目錄中有遺失的公用ID專案，或DITA檔案僅使用與檔案上傳來源伺服器路徑相關的系統ID時，才選取此選項。 |
   | DITA-OT暫時路徑 | *\（可選\）* 指定複製DITA檔案以進行處理的暫存位置。 在DITA-OT處理檔案之前，它們會複製到這個暫存位置。 預設情況下，暫存位置為： <br> **注意** 您可以使用任何現有系統變數或屬性來定義此路徑。 請參閱說明 [dita-OT環境變數](#id181NH0YN0AX) 屬性以取得詳細資訊。 |

   >[!NOTE]
   >
   >  AEM Guides安裝程式會建立兩個環境變數，可用來指定自訂DITA-OT外掛程式檔案的路徑。 這些環境變數為：DITAOT\_DIR，包含檔案系統上DITA-OT目錄的路徑；以及DITAMAP\_DIR，包含檔案系統上DITA map內容擷取的路徑。

1. 按一下 **完成** 以儲存設定檔。


>[!NOTE]
>
> 您可以將自訂DITA設定檔匯出為套件，並上傳至其他AEM Guides執行個體以節省時間。 如需詳細資訊，請參閱 [附錄](appendix.md).

## 整合DITA專業化 {#id211MB0E00XA}

DITA專業化是透過新增元素或移除現有元素來建立新DITA結構的程式。 若要建立新的DITA元素，您可以以現有DITA元素為基底，並根據編寫需求對其進行修改。 本質上，DITA專業化可讓您建立符合業務需求的自訂資訊模型，同時保留現有DITA架構的優點。

您可以使用設定檔功能來儲存自訂DITA專業化設定。 然後，您可以在製作和發佈自訂DITA內容時使用這些設定。 AEM Guides可讓您在自訂DTD/XSD中使用公用ID和系統ID。

>[!NOTE]
>
> AEM Guides Web Editor不支援XSD。

執行以下步驟來建立新的設定檔，並將其設定為使用專用的DTD和XSD AEM Guides：

1. 在本機電腦上建立包含專用DTD和XSD的專用資料夾。

1. 在「 」中指定DTD詳細資料 `catalog.xml` 檔案中必須包含的specialization資料夾。

   >[!NOTE]
   >
   > 若是DITA 1.3，則為DTD的預設位置 `catalog.xml` AEM存放庫中的檔案為： `/libs/fmdita/dita_resources/DITA-1.3/dtd/catalog.xml`.

1. 在「 」中指定XSD詳細資料 `catalog.xml` 檔案中必須包含的specialization資料夾。

   >[!NOTE]
   >
   > 若是DITA 1.3，AEM存放庫中XSD catalog.xml檔案的預設位置為： `/libs/fmdita/dita_resources/DITA-1.3/xsd/catalog.xml`.

1. 上傳資料夾至下列位置：

   `/libs/fmdita/dita_resources`

1. 按一下頂端的Adobe Experience Manager連結，然後選擇 **工具**.

1. 選取 **指南** 工具清單中的。

1. 按一下&#x200B;**DITA設定檔** 圖磚。

   >[!NOTE]
   >
   > 「預設設定檔」資訊會顯示在「設定檔」頁面上。 如果您已將AEM Guides從2.2版升級至2.5.1版或2.6版，則會自動挑選透過Configuration Manager進行的所有變更，並儲存在「預設設定檔」中。

1. 您可以選擇編輯「預設設定檔」、建立新設定檔，或從「預設設定檔」複製設定以建立新設定檔。

   >[!NOTE]
   >
   > 您無法刪除預設設定檔。 但是，您可以編輯和刪除您建立的所有新設定檔。

1. 在 **結構描述** \> **目錄** 設定，指定自訂DTD和XSD的路徑 `catalog.xml` 您的AEM存放庫中的檔案。

1. 選取 **新增系統ID目錄** 選項。

   >[!NOTE]
   >
   > 僅當目錄中有遺失的公用ID專案，或DITA檔案僅使用相對於其上傳來源本機檔案路徑的系統ID時，才選取此選項。

   如需「設定檔」頁面上其他屬性的詳細資訊，請參閱屬性表格： [步驟6](#id17A9F0D075Z) 的 [使用自訂DITA-OT外掛程式](#id181NH1020L7) 區段。

1. 按一下 **完成** 以儲存設定檔。


>[!NOTE]
>
> 您可以將自訂DITA設定檔匯出為套件，並上傳至其他AEM Guides執行個體以節省時間。 如需詳細資訊，請參閱 [Appendix.md](appendix.md).

