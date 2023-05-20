---
title: 使用變數設定「目標路徑」、「站點名稱」或「檔案名」選項
description: 瞭解如何使用變數設定目標路徑、站點名稱或檔案名選項
exl-id: e8d5b7c7-4f80-4ab6-9ad1-308bf0d4cf74
source-git-commit: 8073716bccacbe8d6a158b44d5106b083e3a5dcd
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# 使用變數設定「目標路徑」、「站點名稱」或「檔案名」選項


在「站點」或「AEMPDF」中生成輸出時，可以使用變數定義「目標路徑」、「站點AEM名稱」或「PDF檔案名」選項。 可以使用單個或多個變數的組合來定義這些選項。

下表列出了現有支援的變數：

| 變數 | 最終目標路徑 | 範例 |
| --- | --- | --- |
| `${map_filename}` | 使用DITA映射檔案名建立目標路徑。 | **DITA映射檔案名**:<br>`AEMGuides.ditamap`<br><br>**目標路徑** 配置為：<br>`/content/output/sites/${map_filename}`<br><br>**最終輸出位置**:<br>`/content/output/sites/aemGuides/AEMGuides.html` |
| `${map_title}` | 使用DITA映射標題建立目標路徑。 | **DITA映射檔案名**:<br>`AEMGuides.ditamap`<br><br>**DITA映射標題**:<br>`AEMGuides`<br><br>**目標路徑** 配置為：<br>`/content/output/sites/${map_title}`<br><br>**最終輸出位置**:<br>`/content/output/sites/AEMGuides/AEMGuides.html` |
| `${preset_name}` | 使用輸出預設名稱建立目標路徑。 | **輸出預設名稱**:<br>`AEM Guides PDF Output`<br><br>**DITA映射檔案名**:<br>`SampleDita.ditamap`<br><br>**目標路徑** 配置為：<br>`/content/output/sites/${preset_name}`<br><br>**最終輸出位置**:<br>`/content/output/sites/AEM Guides PDF Output/SampleDita.html` |
| `${language_code}` | 使用映射檔案所在的語言代碼建立目標路徑。 | **DITA映射檔案名**:<br>`SampleDita.ditamap`<br><br>**DITA映射檔案路徑**:<br>`/content/dam/projects/AEM-Guides/en/user-guide/`<br><br>**目標路徑** 配置為：<br>`/content/output/sites/${language_code}`<br><br>**最終輸出位置**:<br>`/content/output/sites/en/SampleDita.html` |
| `${map_parentpath}` | 使用映射檔案的完整路徑建立目標路徑。<br><br>**注釋**：此變數不能用於指定站AEM點名或PDF檔案名。 | **DITA映射檔案名**:<br>`SampleDita.ditamap`<br><br>**DITA映射檔案路徑**:<br>`/content/dam/projects/AEM-Guides/en/user-guide`/<br><br>**目標路徑** 配置為：<br>`/content/output/sites/${map_parentpath}`<br><br>**最終輸出位置**:<br>`/content/output/sites/content/dam/projects/AEM-Guides/en/user-guide/SampleDita.html` |
| `${path_after_langfolder}` | 使用語言資料夾後的映射檔案的路徑建立目標路徑。<br><br>**注釋**:此變數不能用於指定站AEM點名或PDF檔案名。 | **DITA映射檔案名**:<br>`SampleDita.ditamap`<br><br>**DITA映射檔案路徑**:<br>`/content/dam/projects/AEM-Guides/en/user-guide/`<br><br>**目標路徑** 配置為：<br>`/content/output/sites/${path\_after\_langfolder}`<br><br>**最終輸出位置**:<br>`/content/output/sites/user-guide/SampleDita.html` |

此外，還可以將為DITA映射或書籤映射檔案定義的元資料用作變數。 元資料可在 `/jcr:content/metadata` DITA映射或書籤映射檔案的節點。 例如，在 `/jcr:content/metadata` 節點 `dc:title`。 可以指定 `${dc:title}` 標題值用於最終輸出。
**父主題：**[&#x200B;輸出生成](generate-output.md)
