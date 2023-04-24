---
title: ePub預設集
description: 了解如何使用EPUB預設集
source-git-commit: 8b6294425c6e60d1c5b37d98e99114014a104ee6
workflow-type: tm+mt
source-wordcount: '802'
ht-degree: 1%

---


# ePub {#id205BED020YT}

您可以從對應控制面板建立EPUB預設集。

>[!NOTE]
>
> 您可以選擇使用DITA-OT或FMPS \（如果系統管理員已配置）生成HTML5的方法。

要開啟EPUB的輸出預設，請按一下DITA映射檔案，然後按一下輸出預設，然後按一下EPUB選項。 下列選項適用於EPUB輸出：

| ePub選項 | 說明 |
| --- | --- |
| 輸出類型 | 要生成的輸出類型。 要生成EPUB輸出，請選擇EPUB選項。 |
| 設定名稱 | 為您建立的EPUB輸出設定指定描述性名稱。 例如，您可以指定 _內部客戶輸出_ 或 _最終用戶輸出_. |
| DITA-OT命令行參數 | 指定在生成輸出時要DITA-OT處理的其他參數。 有關DITA-OT中支援的命令行參數的詳細資訊，請參見 [DITA-OT檔案](https://www.dita-ot.org/). |
| 使用產生EPUB | 選擇DITA-OT以生成EPUB輸出。 |
| 使用 | 選取下列其中一個選項：<br><br>* **未應用**:如果您不想對已發佈的輸出套用任何條件，請選取此選項。<br>* **DITAVal檔案**:選擇DITAVal檔案以生成個性化內容。 可以使用瀏覽對話框或鍵入檔案路徑來選擇多個DITAVal檔案。 使用檔案名稱附近的交叉圖示加以移除。 DITAVal檔案按指定的順序計算，因此第一個檔案中指定的條件優先於後一個檔案中指定的匹配條件。 您可以新增或刪除檔案，以維護檔案順序。 如果DITAVal檔案被移動到其他位置或被刪除，則不會從映射儀表板中自動刪除該檔案。 您必須更新位置，才能移動或刪除檔案。 您可以將滑鼠移至檔案名稱上方，查看儲存檔案之AEM存放庫的路徑。 只能選擇DITAVal檔案，如果已選擇任何其他檔案類型，則會顯示錯誤。 FrameMaker Publishing Server不支援多個DITAVAL檔案。<br>* **條件預設集**:從下拉式清單中選取條件預設集，以在發佈輸出時套用條件。 如果已添加DITA映射控制台的「條件預設集」頁簽中存在的條件，則會顯示選項。 若要深入了解條件預設，請參閱 [使用條件預設集](generate-output-use-condition-presets.md#id1825FL004PN). |
| 目的地路徑 | AEM存放庫內儲存EPUB輸出的路徑。 |
| 檔案名稱 | 指定要用其保存EPUB輸出的檔案名。<br><br>**附註**:如果您未提供檔案名，則DITA映射的標題將用於生成最終EPUB輸出檔案名。 如果映射沒有標題，則DITA映射的檔案名稱將用作最終EPUB輸出的名稱。 使用系統中配置的規則來處理任何無效字元，將清理檔案名。 |
| 轉換名稱 | 指定要生成的輸出類型。 如果您想使用已整合至DITA-OT外掛程式的自訂外掛程式產生輸出，則此為必要項目。 例如，如果要產生XHTML輸出，請指定 `xhtml`. 有關DITA-OT中可用的轉換的清單，請參見 [DITA-OT轉換（輸出格式）](http://www.dita-ot.org/2.3/user-guide/AvailableTransforms.md) 在OASIS DITA-OT使用手冊中。 |
| 清除DITA-OT臨時檔案 | 選擇此選項可清除DITA-OT生成的臨時檔案。 在輸出生成日誌中可找到DITA-OT儲存臨時檔案的位置。<br><br>如果您在透過DITA-OT產生輸出時遇到錯誤，您可以取消選取此選項以保留暫時檔案。 然後，您可以使用這些檔案來疑難排解輸出產生錯誤。 |
| 運行生成後工作流 | 選擇此選項後，會顯示新的「產生後的工作流程」下拉式清單，其中包含AEM中設定的所有工作流程。 您必須選取要在完成輸出產生工作流程後執行的工作流程。<br><br>**附註**:如需建立自訂輸出後產生工作流程的詳細資訊，請參閱 _自訂輸出後產生工作流程_ (在安裝及設定Adobe Experience Manager指南中)as a Cloud Service。 |
| 使用基線 | 如果已為所選DITA映射建立基線，請選擇此選項以指定要發佈的版本。<br><br>請參閱 [使用基線](generate-output-use-baseline-for-publishing.md#id1825FI0J0PF) 以取得更多詳細資訊。 |
| 屬性 | 選取您要以中繼資料處理的屬性。 這些屬性是從DITA映射或書籤映射檔案的「屬性」頁設定的。 您從下拉式清單中選取的屬性會列在「屬性」欄位下方，並從下拉式清單中移除。 設定後，這些屬性也會複製到對映中的主題中。<br><br>**附註**:您也可以使用DITA-OT發佈，將中繼資料傳遞至輸出。 如需更多詳細資訊，請參閱 [使用DITA-OT將中繼資料傳遞至輸出](pass-metadata-dita-ot.md#id21BJ00QD0XA). |

**上層主題：**[&#x200B;了解輸出預設集](generate-output-understand-presets.md)

