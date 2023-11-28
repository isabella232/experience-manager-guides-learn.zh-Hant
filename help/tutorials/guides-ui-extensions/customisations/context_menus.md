---
sidebar_position: 2
source-git-commit: 42052b37724f97e34ab007db4cc3d9f9524ad3a2
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 0%

---


# 自訂內容功能表

下列前後關聯功能表可供自訂：

- `file_options`
控制器：
   - 地圖檢視： `ditamap_viewer_controller`
   - 存放庫面板： `repository_panel_controller`
   - 我的最愛面板： `collection_tree_controller`
   - 檔案屬性參考連結： `file_references_links_controller`
   - 存放庫搜尋面板： `repository_search_controller`
   - 主旨配置面板： `subject_scheme_tree_controller`

- `folder_options`
控制器：
   - 存放庫面板： `repository_panel_controller`
   - 我的最愛面板： `collection_tree_controller`

- `collection_options`
控制器：
   - 我的最愛面板： `collection_tree_controller`

- `map_view_options`
控制器：
   - 地圖檢視： `ditamap_viewer_controller`

- `baseline_panel_menu`
控制器：
   - 基線面板： `baseline_panel`

- `preset_item_menu`
控制器：
   - 預設面板： `preset_panel`

您也可以定義新的唯一ID，以建立自己的內容功能表。

現在，每個內容功能表都有 `controller id` 與其相關聯。 此控制器處理 `on-event` 各種前後關聯功能表選項的功能

讓我們以範例來瞭解

```js title=customise_context_menu.js"
const fileOptions = {
    id: "file_options",
    contextMenuWidget: "repository_panel",
    view: {
            items: [
                {
                    component: "div",
                    target: {
                        key:"displayName",value: "Delete",                    
                        viewState: VIEW_STATE.REPLACE
                    }
                },
                {
                    component: "div",
                    target: {
                        key:"displayName",value: "Edit",                    
                        viewState: VIEW_STATE.REPLACE
                    }
                },
                {
                    "displayName": "Download",
                    "data": {
                      "eventid": "downloadFile"
                    },
                    "icon": "downloadFromCloud",
                    "class": "menu-separator",         
                    target: {
                        key:"displayName",value: "Duplicate",                    
                        viewState: VIEW_STATE.REPLACE
                    }
                },
            ]

    },

    controller: {
        downloadFile(){
            const path  = this.model.selectedItem.path
            this.loader.loadDitaFile(path).then((file) => {
              function download_file(name, contents) {
                const mime_type = "text/plain";
        
                const blob = new Blob([contents], {type: mime_type});
        
                const dlink = document.createElement('a');
                dlink.download = name;
                dlink.href = window.URL.createObjectURL(blob);
                dlink.onclick = function() {
                    // revokeObjectURL needs a delay to work properly
                    const that = this;
                    setTimeout(function() {
                        window.URL.revokeObjectURL(that.href);
                    }, 1500);
                };
        
                dlink.click();
                dlink.remove();
            }
            download_file(path,file.xml)
            });
          }
    }
}
```

現在，讓我們瞭解此程式碼正在做什麼。

1. `id` 用於識別我們要自訂的內容功能表。
2. `contextMenuWidget` 用於定義 `widget id` 或 `component` 會呼叫內容功能表並處理 `events`.

其餘部分保持不變，其中 `view` 用於定義專案， `target` 會識別要在何處取代、附加或附加選項，以及 `contextMenuWidget` 控制器處理 `on-click` 事件。
