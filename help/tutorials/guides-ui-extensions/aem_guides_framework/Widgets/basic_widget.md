---
sidebar_position: 1
source-git-commit: 0f20681fa4de859053c8d2baae0e53f347ce5859
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 0%

---



# Widget

如「元件」一節所述，可結合多個基本元件以產生Widget。
Widget可用來建立新的「更複雜」元件，或為元件專案提供結構。

讓我們來深入探討Widget的概念！

我們先製作一個簡單的Widget來顯示語言清單。

```js title="basicWidget.js"
const widgetJSON =  {
    "component": "div", 
    "id": "widget_languages", 
    "items": [ // adding components to the widget
        {
            "component": "div",
            "items": [
                {
                    "component": "icon",
                    "icon": "info"
                },
                {
                    "component": "label",
                    "label": "List of some languages"
                }
            ]
        },
        {
            "component": "list",
            "data": "@languages"
        }
    ]
},
```

此處， `@languages` 是模型中定義的陣列 `widget_languages` 作為： [「英文」、「法文」、「印地文」、「西班牙文」、「烏爾都文」]

演算後的基本Widget如下所示：

![basic_widget](imgs/basic_widget.png "基本Widget")
