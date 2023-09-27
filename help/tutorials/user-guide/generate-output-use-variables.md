---
title: 使用變數來設定目的地路徑、網站名稱或檔案名稱選項
description: 瞭解如何使用變數來設定目的地路徑、網站名稱或檔案名稱選項。 瞭解AEM Guides支援的現成可用變數。
exl-id: e8d5b7c7-4f80-4ab6-9ad1-308bf0d4cf74
source-git-commit: 8504a0a52d381044bf1f0d6e7de3585ebecf3a7b
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# 使用變數來設定目的地路徑、網站名稱或檔案名稱選項


在AEM網站或PDF中產生輸出時，您可以使用變數來定義目的地路徑、AEM網站名稱或PDF檔案名稱選項。 您可以使用單一變數或變陣列合來定義這些選項。

下表列出現成支援的變數：

| 變數 | 最終目的地路徑 | 範例 |
| --- | --- | --- |
| `${map_filename}` | 使用DITA map檔案名稱來建立目的地路徑。 | **DITA map檔案名稱**：<br>`AEMGuides.ditamap`<br><br>**目的地路徑** 設定為：<br>`/content/output/sites/${map_filename}`<br><br>**最終輸出位置**：<br>`/content/output/sites/aemGuides/AEMGuides.html` |
| `${map_title}` | 使用DITA map標題來建立目的地路徑。 | **DITA map檔案名稱**：<br>`AEMGuides.ditamap`<br><br>**DITA map標題**：<br>`AEMGuides`<br><br>**目的地路徑** 設定為：<br>`/content/output/sites/${map_title}`<br><br>**最終輸出位置**：<br>`/content/output/sites/AEMGuides/AEMGuides.html` |
| `${preset_name}` | 使用輸出預設集名稱建立目的地路徑。 | **輸出預設集名稱**：<br>`AEM Guides PDF Output`<br><br>**DITA map檔案名稱**：<br>`SampleDita.ditamap`<br><br>**目的地路徑** 設定為：<br>`/content/output/sites/${preset_name}`<br><br>**最終輸出位置**：<br>`/content/output/sites/AEM Guides PDF Output/SampleDita.html` |
| `${language_code}` | 使用對應檔案所在的語言代碼來建立目的地路徑。 | **DITA map檔案名稱**：<br>`SampleDita.ditamap`<br><br>**DITA map檔案路徑**：<br>`/content/dam/projects/AEM-Guides/en/user-guide/`<br><br>**目的地路徑** 設定為：<br>`/content/output/sites/${language_code}`<br><br>**最終輸出位置**：<br>`/content/output/sites/en/SampleDita.html` |
| `${map_parentpath}` | 使用對應檔案的完整路徑來建立目的地路徑。<br><br>**注意**：此變數無法用於指定AEM網站名稱或PDF檔案名稱。 | **DITA map檔案名稱**：<br>`SampleDita.ditamap`<br><br>**DITA map檔案路徑**：<br>`/content/dam/projects/AEM-Guides/en/user-guide`/<br><br>**目的地路徑** 設定為：<br>`/content/output/sites/${map_parentpath}`<br><br>**最終輸出位置**：<br>`/content/output/sites/content/dam/projects/AEM-Guides/en/user-guide/SampleDita.html` |
| `${path_after_langfolder}` | 使用語言資料夾之後的對應檔案路徑來建立目的地路徑。<br><br>**注意**：此變數無法用於指定AEM網站名稱或PDF檔案名稱。 | **DITA map檔案名稱**：<br>`SampleDita.ditamap`<br><br>**DITA map檔案路徑**：<br>`/content/dam/projects/AEM-Guides/en/user-guide/`<br><br>**目的地路徑** 設定為：<br>`/content/output/sites/${path\_after\_langfolder}`<br><br>**最終輸出位置**：<br>`/content/output/sites/user-guide/SampleDita.html` |
| `${system_date}` | 使用目前的伺服器日期建立目的地路徑。 | **DITA map檔案名稱**： <br> `SampleDita.ditamap` <br><br> **DITA map檔案路徑：** <br> `/content/dam/projects/AEM-Guides/en/user-guide/` <br><br> **目的地路徑** 設定為： <br> `/content/output/sites/${system_date}` <br> <br> **最終輸出位置：** <br> /`content/output/sites/08252023/SampleDita.html` |
| `${system_time}` | 使用目前的伺服器時間建立目的地路徑。 | **DITA map檔案名稱：** <br>`SampleDita.ditamap` <br> <br> **DITA map檔案路徑：** <br>`/content/dam/projects/AEM-Guides/en/user-guide/` <br><Br>**目的地路徑** 設定為： <br> `/content/output/sites/${system_time}`<br><br>**最終輸出位置：**<br>`/content/output/sites/055612/SampleDita.html` |

此外，您也可以使用為DITA map或bookmap檔案定義的中繼資料作為變數。 中繼資料可在下找到 `/jcr:content/metadata` DITA map或書籤地圖檔案的節點。 例如，在中定義的其中一個中繼資料屬性 `/jcr:content/metadata` 節點為 `dc:title`. 您可以指定 `${dc:title}` 標題值會用於最終輸出中。
**父級主題：**[&#x200B;產生輸出](generate-output.md)
