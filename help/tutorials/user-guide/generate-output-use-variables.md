---
title: 使用變數設定「目標路徑」、「站點名稱」或「檔案名稱」選項
description: 了解如何使用變數來設定「目的地路徑」、「網站名稱」或「檔案名稱」選項
source-git-commit: 8b6294425c6e60d1c5b37d98e99114014a104ee6
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---


# 使用變數設定「目標路徑」、「站點名稱」或「檔案名稱」選項


在AEM網站或PDF中產生輸出時，您可以使用變數來定義「目標路徑」、AEM網站名稱或PDF檔案名稱選項。 您可以使用單一或變陣列合來定義這些選項。

下表列出可立即使用的支援變數：

| 變數 | 最終目的地路徑 | 範例 |
| --- | --- | --- |
| `${map_filename}` | 使用DITA映射檔案名建立目標路徑。 | **DITA映射檔案名**:<br>`AEMGuides.ditamap`<br><br>**目的地路徑** 設定為：<br>`/content/output/sites/${map_filename}`<br><br>**最終輸出位置**:<br>`/content/output/sites/aemGuides/AEMGuides.html` |
| `${map_title}` | 使用DITA映射標題建立目標路徑。 | **DITA映射檔案名**:<br>`AEMGuides.ditamap`<br><br>**DITA映射標題**:<br>`AEMGuides`<br><br>**目的地路徑** 設定為：<br>`/content/output/sites/${map_title}`<br><br>**最終輸出位置**:<br>`/content/output/sites/AEMGuides/AEMGuides.html` |
| `${preset_name}` | 使用輸出預設集名稱來建立目標路徑。 | **輸出預設集名稱**:<br>`AEM Guides PDF Output`<br><br>**DITA映射檔案名**:<br>`SampleDita.ditamap`<br><br>**目的地路徑** 設定為：<br>`/content/output/sites/${preset_name}`<br><br>**最終輸出位置**:<br>`/content/output/sites/AEM Guides PDF Output/SampleDita.html` |
| `${language_code}` | 使用映射檔案所在的語言代碼建立目標路徑。 | **DITA映射檔案名**:<br>`SampleDita.ditamap`<br><br>**DITA映射檔案路徑**:<br>`/content/dam/projects/AEM-Guides/en/user-guide/`<br><br>**目的地路徑** 設定為：<br>`/content/output/sites/${language_code}`<br><br>**最終輸出位置**:<br>`/content/output/sites/en/SampleDita.html` |
| `${map_parentpath}` | 使用映射檔案的完整路徑建立目標路徑。<br><br>**附註**：此變數無法用來指定AEM網站名稱或PDF檔案名稱。 | **DITA映射檔案名**:<br>`SampleDita.ditamap`<br><br>**DITA映射檔案路徑**:<br>`/content/dam/projects/AEM-Guides/en/user-guide`/<br><br>**目的地路徑** 設定為：<br>`/content/output/sites/${map_parentpath}`<br><br>**最終輸出位置**:<br>`/content/output/sites/content/dam/projects/AEM-Guides/en/user-guide/SampleDita.html` |
| `${path_after_langfolder}` | 使用語言資料夾之後的映射檔案路徑建立目標路徑。<br><br>**附註**:此變數無法用來指定AEM網站名稱或PDF檔案名稱。 | **DITA映射檔案名**:<br>`SampleDita.ditamap`<br><br>**DITA映射檔案路徑**:<br>`/content/dam/projects/AEM-Guides/en/user-guide/`<br><br>**目的地路徑** 設定為：<br>`/content/output/sites/${path\_after\_langfolder}`<br><br>**最終輸出位置**:<br>`/content/output/sites/user-guide/SampleDita.html` |

此外，您也可以將為DITA映射或書籤映射檔案定義的元資料用作變數。 中繼資料位於 `/jcr:content/metadata` DITA映射或書籤映射檔案的節點。 例如，在 `/jcr:content/metadata` 節點為 `dc:title`. 您可以指定 `${dc:title}` 並在最終輸出中使用標題值。
**上層主題：**[&#x200B;產生輸出](generate-output.md)

