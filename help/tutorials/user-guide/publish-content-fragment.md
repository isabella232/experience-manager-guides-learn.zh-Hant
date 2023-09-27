---
title: 發佈主題至內容片段
description: 在AEM Guides中將主題或主題內的元素發佈到內容片段。  瞭解如何檢視主題目前的內容片段並重新發佈。
source-git-commit: 6143bdcb4c8a9e1f35ea752cf1be142ab98a716b
workflow-type: tm+mt
source-wordcount: '613'
ht-degree: 1%

---


# 發佈至內容片段

內容片段是AEM中的分散式內容片段。 它們是以內容模型為基礎的結構化內容。 內容片段是純內容，沒有設計或版面配置資訊。 它們可以獨立於AEM支援的管道之外進行編寫和管理。 內容片段為模組化，其中內容會分成較小的元件。

AEM Guides可讓您將主題或主題內的元素發佈到內容片段。 您可以在主題和內容片段模型之間建立JSON型對應。 使用此對應將主題或主題內的元素發佈到內容片段。 然後，您可以在任何AEM網站中使用內容片段，或透過內容片段支援的API擷取詳細資訊。


若要建立內容片段，請執行以下步驟：

1. 建立 [內容片段模型](https://experienceleague.adobe.com/docs/experience-manager-65/assets/content-fragments/content-fragments-models.html?lang=zh-Hant) 在AEM Assets中。
1. 建立一個資料夾，您想在其中儲存根據內容片段模式建立的內容片段。 例如，「stock-content-fragments」。
1. 編輯資料夾的屬性（例如「stock-content-fragments」）並新增資料夾的路徑，其中包含雲端設定中的內容片段模式。
例如，新增 `/conf/we-retail` 在雲端設定中。 此設定將所有內容片段模型連線到資料夾。\
   ![在資料夾屬性中新增雲端設定詳細資料](images/fragment-folder-cloud-configuration.png){width="650" align="left"}
   *在資料夾屬性中新增雲端設定，以將其與片段模型連線。*
1. 選取您要發佈的主題 **存放庫檢視**.
1. 從 **選項** 功能表，選取 **發佈為** > **內容片段**.
1. 在 **發佈為內容片段** 對話方塊，請填入下列詳細資料：
   ![在「發佈為內容片段」對話方塊中新增片段模型和對應詳細資訊](images/content-fragment-publish.png){width="500" align="left"}
   *新增路徑、模型和對應詳細資訊，將主題或其元素發佈為內容片段。 您可以覆寫現有的內容片段。*

   * **路徑**：瀏覽並選取您要發佈內容片段的資料夾路徑。 您也可以選取現有的內容片段並加以發佈。
   * **標題**：輸入內容片段的標題。
   * **名稱**：輸入內容片段的名稱。
   * **模型**：選取您要用來建立內容片段的內容片段模式。 模型是從您已在雲端服務中設定的資料夾中選取。
   * **對應**：從下拉式清單中選取對應。 它會從 *contentFragmentMapping.json* 檔案。



     根據您的設定，您的管理員可以在以下位置新增對應： *contentFragmentMapping.json* 檔案。

     <details>
        <summary>雲端服務</summary>

     進一步瞭解如何 [建立主題與內容片段之間的對應](../cs-install-guide/conf-content-fragment-mapping-cs.md) 在Cloud Service安裝與設定指南中。
     </details>

     <details>
        <summary> 內部部署軟體</summary>

     進一步瞭解如何 [建立主題與內容片段之間的對應](../install-guide/conf-content-fragment-mapping.md) ，位於On-premise安裝與設定指南中。

     </details>
   * 選取 **覆寫** 核取方塊（如果您的內容片段已經存在且您想要覆寫它）。 如果您未勾選核取方塊，而且您的內容片段已存在，AEM Guides會顯示錯誤。
1. 按一下 **建立** 以發佈內容片段。
1. 您可以在底下檢視主題的內容片段 **片段** 中的區段 **檔案屬性**.

   ![檢視主題的內容片段](images/topic-content-fragments.png){width="300" align="left"}

   *檢視主題目前的內容片段並重新發佈。*

您也可以重新發佈內容片段，以DITA主題的最新內容更新內容片段。



發佈內容片段後，您也可以在任何AEM網站中使用這些片段。

