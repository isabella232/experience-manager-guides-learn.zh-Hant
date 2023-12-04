---
title: 原生PDF |設定原生PDF發佈的節點程式
description: 瞭解如何設定原生PDF發佈的節點程式
source-git-commit: 880cd344ceb65ea339be699ebcad41c0d62e168a
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 1%

---

# 設定原生PDF發佈的節點程式

原生PDF發佈會啟動個別的NodeJs程式，將在發佈程式中產生的檔案轉換為最終PDF。 您可能需要調整此執行原生PDF發佈的節點程式的設定，以支援不同的情境。 例如，若要執行較大的工作負載，您應該增加衍生的NodeJs處理序可用的棧積大小上限。

使用中提供的指示 [設定覆寫](../cs-install-guide/download-install-additional-config-override.md) 以建立組態檔。在組態檔中，提供下列（屬性）詳細資訊：

| PID | 屬性索引鍵 | 屬性值 |
|---|---|---|
| `com.adobe.fmdita.config.ConfigManager` | `native.pdf.node.opts` | 要設定任何標準的字串值 `NODE_OPTIONS`.<BR> 預設值： &quot;&quot; |
