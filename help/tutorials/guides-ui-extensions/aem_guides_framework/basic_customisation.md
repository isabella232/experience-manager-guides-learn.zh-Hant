---
sidebar_position: 3
source-git-commit: 42052b37724f97e34ab007db4cc3d9f9524ad3a2
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---

# 自訂應用程式

我們的應用程式採用MVC （模型、檢視、控制器）結構

## 模型

模型會定義各種屬性並儲存其值。 可使用語法從控制器存取儲存在模型中的各種屬性的值

```typescript
this.model.attributeName
```

為了在應用程式中進行自訂，所有新建立的屬性都會新增到模型中的對應下。
若要在模型中設定新屬性，我們將在控制器中使用下列語法：

```typescript
this.model.extraProps.set("key", value)
```

若要存取新增至模型的屬性，我們將使用下列語法：

```typescript
const value = this.model.extraProps.get("key")
```

## 檢視

此檢視會定義應用程式的UI。 我們使用JSON檔案來定義檔案的檢視。 在此，我們會定義元件和css （如元件外部範例中所提供），並轉譯儲存在模型中的值。
在我們的應用程式中，每個檢視都是使用JSON來定義。 JSON是使用稱為的唯一ID來參照 `id`.

## 控制器

控制器是用來處理事件及處理資料。 控制器是用來從伺服器擷取及傳送資料，是UI上顯示與儲存在後端之間的介面。

- 若要在初始化時設定值，我們使用 `init` 函式。
- 若要將方法新增至控制器，請使用下列語法：

```typescript
methodName: function(args){
    // functionality
}
```

此 `methodName` 這裡將用作 `key` 以參照JSON （檢視）或其他函式中的方法

- 若要呼叫控制器中的方法，請使用語法

```typescript
this.next('methodName', args)
```

## 範例

現在，讓我們以簡單範例說明這3個元件如何彼此互動。
我們將新增一個按鈕，可在點按時切換其標籤值

### 檢視範例

以下是我們為顯示儲存在模型中變數名稱下的動態文字的按鈕定義JSON `buttonLabel`.
在此範例中，按一下按鈕會變更其標籤。

```JSON
{
    "component": "button",
    "label": "@extraProps.buttonLabel",
    "variant": "cta",
    "on-click": "switchButtonLabel",
}
```

### 模型範例

在這種情況下， `extraProps.buttonLabel` 保留按鈕的標籤

### 控制器範例

```typescript
  controller: {
    init: function () {
      this.model.extraProps.set("buttonLabel", "Submit")
    },

    switchButtonLabel(){
        const buttonLabel = this.model.extraProps.get("buttonLabel") === "Submit"? "Cancel" : "Submit"
        this.model.extraProps.set("buttonLabel", buttonLabel)
    }
  }
```

以下GIF顯示上述程式碼的實際運作中
![basic_customization](imgs/basic_customisation.gif "基本自訂按鈕")
