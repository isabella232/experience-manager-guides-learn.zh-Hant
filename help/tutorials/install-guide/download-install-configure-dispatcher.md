---
title: 設定 Dispatcher
description: 瞭解如何配置Dispatcher
source-git-commit: 9fe396dcfd2e3570ec386c958d7d4efdb4d608e5
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 7%

---


# 設定 Dispatcher {#id213BCM0M05U}

如果計畫使用Dispatcher on AEM Author實例和「參考線」AEM，則需要執行以下附加配置以完成安裝：

>[!NOTE]
>
> Dispatcher 是 Adobe Experience manager 的快取和/或負載平衡工具。有關使用Dispatcher的詳細資訊，請參見 [Dispatcher概述](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=zh-Hant)。

## 在URL中啟用AllowEncodedSlaches

預設情況下，在調度程式設定中未啟用帶編AEM碼斜槓的URL，但在「指南」中工AEM作時，需要啟用此功能。 為此，您需要將AllowEncodedSlaches參數設定為Apache配置中的On，如以下代碼段所示：

```XML
<VirtualHost *:80>
                ServerName www.geometrixx-outdoors.com
                **AllowEncodedSlashes On**
                <Directory />
                <IfModule disp_apache2.c>
                SetHandler dispatcher-handler
                </IfModule>
                Options FollowSymLinks
                AllowOverride None
                </Directory>
                </VirtualHost>
            
```

## 為DITA配置mime.types檔案

使用帶參考AEM線的Dispatcher時，必須確保DITA映射和主題檔案被呈現為HTML，以便作者查看預期的內容\（而不是原始文本格式\）。

執行以下步驟以更新mime.types檔案：

1. 使用SSH連接到Dispatcher伺服器並瀏覽到httpd.conf檔案。

1. 檢查「 mime.types」檔案的路徑。

1. 開啟mime.types檔案並搜索「 text/html」。 「text/html」的預設映射為：

   `text/html html htm`

1. 通過將ditamap和dita擴展添加為：更新映射

   `text/html html htm ditamap dita`

1. 保存並關閉檔案。


此配置更新確保Dispatcher呈現的DITA映射和主題檔案在資產UI中顯示為HTML。

## 允許用戶首選項請求URL

使用帶輔助線的AEMDispatcher時，如果「作者」實例前面有調度程式，則進行以下兩項更改：

- 白名單列出POST請求URL。 示例&quot; `/filters`&quot;規則在下面提供 — 將此規則添加到調度程式配置檔案：

```json
/xxxx {/type "allow" /method "POST" /url "/home/users/*/preferences"}
```

- 確保URL模式「 /libs/cq/security/userinfo.json」未在Author調度程式上快取，因此請在author\_dispatcher.any中添加規則\（如下\）

```json
/xxxx {
                /glob "/libs/cq/security/userinfo.json"
                /type "deny"
                }
```

**父主題：**[&#x200B;下載並安裝](download-install.md)

