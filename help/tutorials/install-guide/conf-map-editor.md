---
title: 將「進階地圖編輯器」設定為預設值
description: 瞭解如何將進階地圖編輯器設定為預設值
source-git-commit: 801c306fa120e7889d4b9428fd5bee2849bf1956
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 0%

---


# 將「進階地圖編輯器」設定為預設值 {#id181AI0003PN}

AEM Guides隨附基本地圖編輯器和進階地圖編輯器。 基本地圖編輯器提供您建立地圖檔案所需的所有功能。 進階地圖編輯器功能更豐富，並整合在網頁編輯器中。 「進階對映編輯器」可讓作者使用易用的介面來建立和編輯DITA map檔案。

根據預設，每當建立新地圖檔案時，都會在「基本地圖編輯器」中將其開啟。 您可以讓設定預設為開啟「進階地圖編輯器」來變更此行為。

執行下列步驟，讓「進階對映編輯器」成為對映檔案的預設編輯器：

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並按一下 **com.adobe.fmdita.xmleditor.config.XmlEditorConfig** 套件組合。

1. 選取 **隱藏基本地圖編輯器** 選項。

   選取此選項後，使用者在使用者介面中的任何位置都不會看到「基本地圖編輯器」連結。 依預設，對應檔案會在進階對應編輯器中開啟。


