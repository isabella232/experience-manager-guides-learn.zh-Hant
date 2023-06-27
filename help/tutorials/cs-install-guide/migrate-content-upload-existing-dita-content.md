---
title: 上傳現有DITA內容
description: 瞭解如何上傳現有的DITA內容
source-git-commit: 4f15166b1b250578f07e223b0260aacf402224be
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 0%

---


# 上傳現有DITA內容 {#id176FF000JUI}

您很可能擁有要搭配AEM Guides使用的現有DITA內容的存放庫。 對於此類現有內容，您可以使用中說明的任何支援方法 [將數位資產新增至Adobe Experience Manager as a Cloud Service資產](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/manage/add-assets.html).

## 設定UUID檔案名稱模式

匯入內容時，檔案名稱不必以UUID為基礎。 在使用以UUID為基礎的檔案名稱的系統中，所有檔案都必須使用其UUID （而非原始檔案名稱）來參照。 如果匯入的檔案沒有以UUID為基礎的檔案名稱，您可以設定系統將UUID新增至其檔案屬性。 然後，會使用此UUID來參照未使用UUID來命名檔案的此類檔案。

使用中提供的指示 [設定覆寫](download-install-additional-config-override.md#) 以建立組態檔。 在設定檔案中，提供下列\(property\)詳細資料以設定UUID檔案名稱模式：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.config.ConfigManager` | `uuid.regex` | 指定UUID檔案名稱模式的規則運算式的字串。 <br> 如果檔案不遵循指定的模式，則會將UUID新增至檔案的屬性，並且所有對該檔案的參照都會以指派給該檔案的UUID更新。 <br> **預設值**： `"^GUID-(?<id>.*)"` |

## 使用curl指令

您也可以使用curl命令在DAM中建立資料夾、上傳檔案，以及在上傳的內容上新增中繼資料。

**建立資料夾**

執行以下命令，在AEM存放庫中建立資料夾：

```
curl --user <username>:<password> --data jcr:primaryType=sling:Folder "<server folder path>"
```

指定下列引數以建立資料夾：

- `<username>:<passowrd>`：指定存取AEM存放庫的使用者名稱和密碼。 此使用者必須擁有資料夾建立許可權。

- `jcr:primaryType=sling:Folder`：指定此引數 *原樣* 以建立資料夾型別資源。

- `<server folder path>`：完整的資料夾路徑，包括您要在AEM存放庫中建立的新資料夾名稱。 例如，如果您將路徑指定為 `http://192.168.1.1:4502/content/dam/projects/AEM-Guides`，然後資料夾 `AEM-Guides` 建立於 `projects` DAM資料夾。


**上傳檔案**

執行以下命令，在AEM存放庫中上傳檔案：

```
curl --user <username>:<password> -T "<local file path>" "<server folder path>"
```

指定下列引數以上傳檔案：

- `<username>:<passowrd>`：指定存取AEM存放庫的使用者名稱和密碼。 此使用者必須擁有 `server folder path`.

- ``local file path``：本機系統上您要上傳的完整檔案路徑。

- `<server folder path>`：您要上傳檔案的AEM伺服器上的完整資料夾路徑。


**新增中繼資料**

執行以下命令，在檔案上新增中繼資料：

```
curl --user <username>:<password> -F<attribute name>=<value> <metadata node path>
```

指定下列引數以新增中繼資料資訊：

- `<username>:<passowrd>`：指定存取AEM存放庫的使用者名稱和密碼。 此使用者必須擁有 ``metadata node path``.

- ``-F<attribute name>=<value>``：此 `<attribute name>` 是中繼資料屬性的名稱，例如 `audience` 和 `<value>` 可以是 `internal`. 您可以指定多個以空格分隔的屬性名稱 — 值組。

- `<metadata node path>`：完整的資料夾路徑，包括檔案名稱及其中繼資料節點。 例如，如果您將路徑指定為 `http://192.168.1.1:4502/content/dam/projects/AEM-Guides/intro.xml/jcr:content/metadata`，則指定的中繼資料資訊會設定在 `intro.xml` 檔案。


**父級主題：**[&#x200B;移轉現有內容](migrate-content.md)

