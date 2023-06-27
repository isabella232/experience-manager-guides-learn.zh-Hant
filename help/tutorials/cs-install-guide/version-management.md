---
title: 版本管理
description: 瞭解如何管理版本
source-git-commit: 4f15166b1b250578f07e223b0260aacf402224be
workflow-type: tm+mt
source-wordcount: '1498'
ht-degree: 0%

---


# 版本管理 {#id181GB000XY4}

版本設定是任何內容管理系統的一個重要方面。 它可讓您在特定時間點建立數位資產的快照。 數位資產已備妥版本，您可以還原並更新資產的必要版本。 通常，建立任何資產的版本時，您需要出庫併入庫所需的資產。

身為管理員，您可以強制實施規則，限制使用者編輯檔案而不將檔案出庫。 同樣地，您可以確保所有出庫檔案都入庫回來，以避免任何資料遺失。

在多用途環境中，確保使用者不會從系統刪除檔案也很重要。 這項要求對於其他使用者簽出的檔案更為重要。 為了防止使用者意外地從系統中刪除出庫的檔案，AEM Guides提供了您可以使用的配置。 除了出庫檔案外，您還可以控制刪除包含參照的檔案或從其他檔案參照的檔案。

## 為上傳的檔案建立新版本

>[!NOTE]
>
> 此設定僅適用於上傳檔案。

若要啟用 **為上傳的檔案建立新版本** 選項，請執行下列步驟：

1. 使用中提供的指示 [設定覆寫](download-install-additional-config-override.md#) 以建立組態檔。
1. 在設定檔案中，提供下列\(property\)詳細資料以設定 **為上傳的檔案建立新版本** 選項：


   | PID | 屬性索引鍵 | 屬性值 |
   |---|------------|--------------|
   | `com.adobe.fmdita.confi g.ConfigManager` | `create.ver.new.content` | 布林值\(true/false\)。<br> **預設值**： `true` |

>[!NOTE]
>
> 選取選項後，就會發生新版本管理機制，並覆寫任何後續上傳的預設上傳行為，會將上傳檔案的內容儲存為新版本。 如果取消選取選項，AEM Guides會使用AEM預設版本管理機制。

## 設定允許編輯已取出檔案的設定

AEM Guides網頁編輯器可讓您建立和更新DITA主題。 您可以設定Web編輯器，僅允許編輯已從存放庫出庫的檔案。 這樣可確保其他寫入器不會意外覆寫其他寫入器開啟供編輯的主題。 一旦開啟主題進行編輯後，作者就可以在關閉檔案時簽入檔案。

另一個重要規則是確保已出庫的檔案會入庫回系統。 這可防止使用者不小心關閉檔案而不將其重新簽入。

使用中提供的指示 [設定覆寫](download-install-additional-config-override.md#) 以建立組態檔。 在設定檔案中，提供下列\(property\)詳細資訊，以設定對出庫檔案的編輯：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | `xmleditor.autocheckout` | 布林值\(true/false\)。<br> **預設值**： `false` |

此外，您也可以設定當已出庫的檔案關閉時，顯示警告訊息，而不儲存或將它簽回存放庫。

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | `xmleditor.checkin` | 布林值\(true/false\)。<br> **預設值**： `false` |

>[!NOTE]
>
> 無論您是開啟還是關閉此功能，在主題預覽中總是可以使用「出庫」和「入庫」檔案選項。

## 上傳時覆寫已簽出的檔案

>[!NOTE]
>
> *此設定僅適用於從Assets UI建立檔案時，而不適用於使用WebDAV工具上傳檔案時。*

若要允許使用者在上傳時覆寫他們或其他使用者已簽出的檔案，請執行以下步驟：

1. 使用中提供的指示 [設定覆寫](download-install-additional-config-override.md#) 以建立組態檔。
1. 在設定檔案中，提供下列\(property\)詳細資料以設定 **上傳時覆寫已簽出的檔案** 選項：


| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.confi g.ConfigManager` | `overwrite.checkout.onupload` | 布林值\(true/false\)。<br> **預設值**： `false` |

>[!NOTE]
>
> 此選項預設為OFF。 選取此選項後，使用者將可覆寫已出庫的檔案。 如果未選取該選項，則當檔案已由他們或其他使用者出庫時，將無法覆寫檔案。

## 防止刪除已出庫的檔案

使用中提供的指示 [設定覆寫](download-install-additional-config-override.md#) 以建立組態檔。 在設定檔中，提供下列\(property\)詳細資訊，以防止使用者意外刪除已出庫的檔案：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | `xmleditor.preventcheckedoutcontentdeletion` | 布林值\(true/false\)。 <br> **預設值**： `true` |

## 防止刪除參照的檔案

管理員可以控制誰可以從AEM存放庫中刪除檔案。 具體而言，如果檔案包含參照或被其他某個檔案參照，則您可以定義誰可以刪除這類檔案。

使用此設定，您可以允許或不允許所有使用者刪除檔案，或只允許特定使用者群組刪除檔案。 如果允許刪除檔案，則遵循以下程式：

- 如果您要刪除包含所有參照和參照檔案的資料夾，則會刪除所有檔案。 程式會先刪除不包含任何參照的所有檔案，接著刪除包含參照或被參照的檔案。

- 如果您要刪除資料夾，而該資料夾內的任何檔案由該資料夾外的檔案參照，則在刪除檔案之前，系統會提示您移除該參照。


使用中提供的指示 [設定覆寫](download-install-additional-config-override.md#) 以建立組態檔。 在組態檔中，提供下列\(property\)詳細資訊，以定義誰可以刪除包含參照的檔案或由其他檔案參照的檔案：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.config.ConfigManager` | `block.unsafe.delete` | 可能的值包括： <br> - allow\_unsafe\_delete\_for\_all <br> - allow\_unsafe\_delete\_for\_delete\_assets\_group <br> - block\_unsafe\_delete\_for\_all <br> **預設值**： `allow_unsafe_delete_for_delete_assets_group` <br> 這些常數的詳細資訊如下。 |

根據您想要授予刪除存取權的對象，指定下列其中一個常數：

- allow\_unsafe\_delete\_for\_all：授予所有使用者刪除檔案的許可權。 在這種情況下，如果檔案\(s\)包含參照或被其他檔案參照，那麼您也可以強制刪除此類檔案\(s\)。 刪除檔案之前，您會看到一個包含參照的提示，您可以取消刪除操作、移除參照，最後刪除檔案。 或者，您可以強制刪除檔案而不移除參照。

  ![](assets/allow_unsafe_delete-force-delete.PNG)

- allow\_unsafe\_delete\_for\_delete\_assets\_group：屬於下列專案的管理員或使用者： *delete-assets* 允許群組刪除檔案。 如果任何其他使用者嘗試刪除包含任何參照的檔案，則在移除所有參照之前，不允許他們刪除此類檔案。 沒有許可權的使用者嘗試刪除檔案時，會出現下列熒幕擷圖。

  ![](assets/allow_unsafe_delete_for_delete_assets_group.PNG)

- block\_unsafe\_delete\_for\_all：不允許所有使用者\（包括管理員\）刪除檔案，直到對檔案的參照和從檔案的參照被移除。


## 清除舊版的DITA檔案

當您更新內容並建立新版本時，舊版的DITA檔案會保留在存放庫中。 可能會在一段時間內為您的DITA檔案建立許多版本，並且可能會共同佔用存放庫中的大量空間。 AEM Guides可讓您設定應從存放庫刪除的舊版本。

如果您有管理許可權，則可以使用指定的URL存取此公用程式：

`<server folder path> /libs/fmdita/clientlibs/xmleditor_version_purge/page.html`

會維護且不會清除符合任何指定准則的DITA檔案版本：

- 是檔案的第一個版本
- 包含在基準線中
- 包含在任何翻譯或稽核工作流程中
- 已套用標籤
- 符合定義的年齡或版本數量標準

執行以下步驟來清除舊版：

1. 輸入下列欲清除檔案的詳細資訊：

   ![](assets/preview-purge-report.png)

1. 
   - **從最新版本保留的版本數目**：輸入應保留且不應永久刪除的版本數目。 例如，如果輸入5，則會保留最後5個版本，而之前的版本則符合清除條件，可以清除該版本之前的版本。
- **保留在時間內建立的版本\（以天為單位）**：輸入版本的最長存留期（以天為單位）。 如果符合其他清除條件，則符合清除指定天數之前的版本。 例如，如果輸入100，則符合其他永久刪除條件時，所有在100天前建立的版本都符合永久刪除的條件。
- **路徑**：選取您要清除其檔案的檔案或資料夾的路徑。

  >[!NOTE]
  >
  > 您只能清除DITA檔案。

1. 按一下 **預覽清除報告**.

   >[!NOTE]
   >
   > 一次只能有一個清除任務。 如果另一個版本正在處理中，則無法起始另一個版本永久刪除作業。

   產生版本清除報告。

1. 下載版本清除報告，並檢查要清除的檔案和版本。
1. 您可以選擇 **取消清除** 或 **開始清除**.

   ![](assets/download-purge-report.png)

   系統會顯示清除狀態。

   按一下 **下載版本清除報告** 以檢視已清除的版本。 此報表提供所有版本的清除狀態，以及保留特定版本或清除該版本的原因。


>[!NOTE]
>
> 報表下載位置如下： `/var/dxml/versionpurge`

