---
title: 根據自訂範本建立地圖
description: 了解如何根據自訂範本建立地圖
exl-id: 02513148-3876-4549-962a-9984f619030f
source-git-commit: 3bca42f0954afc2362ab24f369e698113324dbc3
workflow-type: tm+mt
source-wordcount: '870'
ht-degree: 0%

---

# 根據自訂範本建立地圖 {#id225VF0808MP}

您可以建立自定義的映射模板，並使用它們來建立DITA映射，以及映射模板中引用的主題模板和映射模板

您可以從自訂的地圖範本參考其他地圖範本和主題範本。 引用的地圖範本可以指各種地圖範本、主題範本、主題、地圖、影像、視訊和其他資產。 自定義的映射模板可以幫助您非常輕鬆地複製映射模板和整個引用的資料夾結構。 這些自定義模板對於建立和重新建立具有遞歸結構和引用的多個映射特別有用。

>[!NOTE]
>
> 不會遞回建立主題範本。 系統只會產生直接位於對映範本中的主題範本，且主題範本內的任何主題範本都會直接在上層參照。

## 建立自訂範本

AEM參考線可讓您從dita-templates資料夾建立自訂的地圖和主題。 您可以使用這些自訂範本來建立地圖和主題。 您也可以與作者共用這些範本，讓作者可以使用這些範本建立檔案。 使用這些範本，可讓作者保留範本資料夾中特定資源的個別副本。

>[!NOTE]
>
> 只要參照和維護的任何資源都必須保留在範本資料夾之外。

**主題範本**

執行下列步驟以建立主題範本：

1. 在 **Assets UI**，導覽至dita-templates資料夾。

   ![](images/dita-templates.png){width="800" align="left"}

1. 按一下 **主題** 要開啟的資料夾。按一下 **建立\> DITA範本**.
1. 在「Blueprint」頁面上，選取 **主題** 然後按一下 **下一個。**
1. 在「屬性」頁上，指定主題模板 **標題**.
1. 指定檔案 **名稱**

   >[!NOTE]
   >
   > 檔案名必須具有.dita副檔名。

1. \（選用\）新增說明。
1. 按一下&#x200B;**建立**。主題模板建立的消息隨即出現。 接著，您可以開啟主題範本並加以編輯。

**地圖範本**

執行下列步驟以建立映射模板：

1. 在 **Assets UI**，導覽至dita-templates資料夾。
1. 按一下 **地圖** 資料夾以開啟。
1. 按一下 **建立\> DITA範本。**

   ![](images/create-dita-template.png){width="300" align="left"}

1. 在「Blueprint」頁面上，選取 **地圖** 按一下 **下一個**.
1. 在「屬性」頁上，指定映射模板 **標題**.
1. 指定檔案 **名稱**.

   >[!NOTE]
   >
   > 檔案名稱的副檔名必須為.ditamap。

1. （選用\）新增說明。按一下 **建立**. 將顯示映射模板建立的消息。 然後，您可以開啟地圖範本並加以編輯。 您可以在對應範本中新增主題範本、對應範本以及其他資產的參考。

## 傳遞範本中定義的標題

如果要將範本內使用之主題或地圖的標題傳遞至使用該範本建立的DITA地圖，請在標題周圍使用大括弧。

範例

```XML
<pubtitle>
   <mainpubtitle outputclass="booktitle">
   {title}
   </mainpubtitle>
   <subtitle>Subtitle</subtitle>
</pubtitle>

The resultant DITA map with title "Rootmap1" will look like as follows:
<pubtitle>
   <mainpubtitle outputclass="booktitle">Rootmap1
   </mainpubtitle>
   <subtitle>Subtitle</subtitle>
</pubtitle>
```

>[!NOTE]
> 只有大括弧的第一個出現將替換為標題。

如果您未在標題周圍使用大括弧，則只會挑選第一個元素，且不會從範本中挑選標題的巢狀，其外觀如下：

```XML
<pubtitle> Rootmap1 </pubtitle>
```

>[!NOTE]
> 您也可以使用文字周圍的大括弧，將其巢狀結構從自訂範本傳遞至DITA映射。

範例

```XML
<title>    
    <sub>        
        <b>{title}</b>    
    </sub>
</title>
```

## 使用映射模板建立新映射

>[!NOTE]
>
> 必須配置映射模板，並使管理員可以編寫。 如需詳細資訊，請參閱 *設定製作範本* 一節中的「安裝及設定Adobe Experience Manager指南」as a Cloud Service。

執行下列步驟以使用自訂地圖範本建立地圖：

1. 在 **資產UI、** 導覽至您要建立地圖的資料夾。
1. 按一下 **建立\> DITA映射**.
1. 在「Blueprint」(Blueprint)頁面上，選擇要使用的映射模板，然後按一下 **下一個**. 例如，如果已建立映射模板「test-template」，請選擇它。
1. 在「屬性」頁面上，指定對應 **標題**.
1. 指定檔案 **名稱**.

   >[!NOTE]
   >
   > 檔案名稱的副檔名必須為.ditamap。

1. 按一下&#x200B;**建立**。將顯示建立的映射消息。


地圖會產生範本資料夾內參照的所有資產。 地圖中參考的某些資產類型如下：

- 如果地圖包含對主題模板的引用，則會在資料夾內建立其副本，其層次與主題資料夾中的主題資料夾位於 `dita-templates` 檔案夾。
- 如果地圖包含對地圖模板的引用，則會在資料夾內建立其副本，其層次與 `dita-templates` 檔案夾。
- 如果地圖包含外部主題或地圖的一般參考 `dita-templates/topics` 或 `dita-templates/maps` 資料夾中，僅參考相同，不會建立任何副本。

   >[!NOTE]
   >
   > `dita-templates/topics` 和 `dita-templates/maps` 是「參考線」中的預設路徑，且可設定。


   如果映射模板內有主題模板鍵定義，則會建立新鍵\（因此新主題\）並在映射中引用。

- 如果在資料夾的相同層級建立另一個地圖或主題，則新建立資產的名稱會附加0、1、2等。 您可以選擇開啟映射以進行編輯或將映射檔案保存在儲存庫中。

**上層主題：**[&#x200B;使用地圖編輯器](map-editor.md)
