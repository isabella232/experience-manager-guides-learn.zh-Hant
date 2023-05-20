---
title: ePub預設
description: 瞭解如何使用EPUB預設
exl-id: 19425ed2-fd7e-49c2-8f84-fc559a1db81b
source-git-commit: 8073716bccacbe8d6a158b44d5106b083e3a5dcd
workflow-type: tm+mt
source-wordcount: '802'
ht-degree: 1%

---

# ePub {#id205BED020YT}

可以從映射操控板建立EPUB預設。

>[!NOTE]
>
> 您可以選擇使用DITA-OT或FMPS \（如果系統管理員已配置）生成HTML5的方法。

要開啟輸出預設以進行EPUB，請按一下DITA映射檔案，然後按一下輸出預設，然後按一下EPUB選項。 以下選項可用於EPUB輸出：

| ePub選項 | 說明 |
| --- | --- |
| 輸出類型 | 要生成的輸出類型。 要生成EPUB輸出，請選擇EPUB選項。 |
| 設定名稱 | 為正在建立的EPUB輸出設定指定描述性名稱。 例如，可以指定 _內部客戶輸出_ 或 _最終用戶輸出_。 |
| DITA-OT命令行參數 | 指定在生成輸出時希望DITA-OT處理的其他參數。 有關DITA-OT中支援的命令行參數的詳細資訊，請參見 [DITA-OT文檔](https://www.dita-ot.org/)。 |
| 生成EPUB | 選擇DITA-OT以生成EPUB輸出。 |
| 使用 | 選擇以下選項之一：<br><br>* **未應用**:如果不想對已發佈的輸出應用任何條件，請選擇此選項。<br>* **DITAVal檔案**:選擇DITAVal檔案以生成個性化內容。 可以使用瀏覽對話框或鍵入檔案路徑來選擇多個DITAVal檔案。 使用檔案名附近的交叉表徵圖將其刪除。 DITAVal檔案按指定的順序計算，因此在第一個檔案中指定的條件優先於在以後的檔案中指定的匹配條件。 可以通過添加或刪除檔案來維護檔案順序。 如果DITAVal檔案被移動到其他位置或被刪除，則不會自動從映射儀表板中刪除該檔案。 在移動或刪除檔案時，需要更新位置。 可以將滑鼠懸停在檔案名上，查看儲存文AEM件的儲存庫中的路徑。 只能選擇DITAVal檔案，如果選擇了任何其他檔案類型，則會顯示錯誤。 FrameMaker發佈伺服器不支援多個DITAVAL檔案。<br>* **條件預設**:從下拉清單中選擇條件預設，以便在發佈輸出時應用條件。 如果已在DITA映射控制台的「條件預設」頁籤中添加了條件，則該選項可見。 要瞭解有關條件預設的詳細資訊，請參閱 [使用條件預設](generate-output-use-condition-presets.md#id1825FL004PN)。 |
| 目的地路徑 | 儲存庫AEM中EPUB輸出的路徑。 |
| 檔案名稱 | 指定要保存EPUB輸出的檔案名。<br><br>**注釋**:如果未提供檔案名，則DITA映射的標題將用於生成最終EPUB輸出檔案名。 如果映射沒有標題，則DITA映射的檔案名用於命名是最終的EPUB輸出。 使用系統中配置的規則處理任何無效字元，對檔案名進行清理。 |
| 轉換名稱 | 指定要生成的輸出類型。 如果要使用自己的自定義插件生成輸出，則此操作是必需的，該插件已整合到DITA-OT插件中。 例如，如果要生成XHTML輸出，請指定 `xhtml`。 有關DITA-OT中可用的轉換的清單，請參見 [DITA-OT轉換（輸出格式）](http://www.dita-ot.org/2.3/user-guide/AvailableTransforms.md) OASIS DITA-OT使用手冊。 |
| 清除DITA-OT臨時檔案 | 選擇此選項可清除由DITA-OT生成的臨時檔案。 DITA-OT儲存臨時檔案的位置可在輸出生成日誌中找到。<br><br>如果在通過DITA-OT生成輸出時遇到錯誤，則可以取消選擇此選項以保留臨時檔案。 然後，您可以使用這些檔案排除輸出生成錯誤。 |
| 運行生成後工作流 | 選擇此選項後，將顯示一個新的「生成後工作流」下拉清單，其中包含中配置的所有工AEM作流。 必須選擇要在完成輸出生成工作流後執行的工作流。<br><br>**注釋**:有關建立自定義輸出後生成工作流的詳細資訊，請參閱 _自定義輸出後生成工作流_ 在安裝和配置Adobe Experience Manager指南as a Cloud Service。 |
| 使用基線 | 如果已為所選DITA映射建立基線，請選擇此選項以指定要發佈的版本。<br><br>請參閱 [使用基線](generate-output-use-baseline-for-publishing.md#id1825FI0J0PF) 的雙曲餘切值。 |
| 屬性 | 選擇要作為元資料處理的屬性。 這些屬性是從DITA映射或書籤映射檔案的「屬性」頁中設定的。 從下拉清單中選擇的屬性列在「屬性」欄位下方，並從下拉清單中刪除。 設定後，這些屬性也會複製到映射中的主題中。<br><br>**注釋**:您還可以使用DITA-OT發佈將元資料傳遞到輸出。 有關詳細資訊，請參閱 [使用DITA-OT將元資料傳遞到輸出](pass-metadata-dita-ot.md#id21BJ00QD0XA)。 |

**父主題：**[&#x200B;瞭解輸出預設](generate-output-understand-presets.md)
