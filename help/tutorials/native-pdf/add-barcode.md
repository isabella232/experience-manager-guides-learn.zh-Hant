---
title: 本機PDF發佈功能 |添加條形碼
description: 瞭解如何添加條形碼。
source-git-commit: 6cea7a92eed8f7b1d4a0763baae65ccccd71790e
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 2%

---

# 向PDF輸出添加條形碼

條形碼對於包括可由機器輕鬆處理的資訊是有用的。 同樣，QR碼用於閱讀器可以通過移動設備開啟的連結。

本教程幫助您在PDF輸出中的每頁頂部添加條形碼。

## 生成條形碼的步驟

要生成條形碼，請執行以下步驟：

### 將資源ID添加到DITA映射

將資源ID元素添加到DITA映射。 資源ID用作生成條形碼的主輸入。

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE map PUBLIC "-//OASIS//DTD DITA Map//EN" "technicalContent/dtd/map.dtd">
<map id="GUID-3c330691-4dac-4020-904a-d2d6246aeeb1-en">
  <title>Barcode Sample</title>
  <topicmeta>
    <resourceid id="7a5bda1c-b1db-4fd8-8763-a731e2e8abba">
    </resourceid>
  </topicmeta>
  <topicref href="GUID-139f6c64-bea3-4f17-8b22-ee131557e249-en.dita" type="topic">
  </topicref>
</map>  
```

也可以在「創作」模式下編輯資源ID。

<img src="./assets/barcode-map.png" alt="帶條形碼的示例輸出" width="700">


### 在模板標題中添加條形碼佔位符

修改 `Common.plt` 檔案 **基本** 在項目標題後添加條形碼的模板。

```html
...
  <div data-region="header">
    <p class="chapter-header"><span data-field="project-title" data-format="default">Project Title</span> </p>
    <p><span class="barcode" data-field="metadata" data-format="default" data-subtype="//resourceid/@id">Resource ID (barcode)</span></p>
  </div>
} 
...
```


### 更新模板的CSS以呈現條形碼值

修改 `content.css` 檔案，以在生成PDF期間呈現條形碼。 支援各種條形碼類型，如「qrcode」和「pdf417」。  有關詳細資訊，請參閱 [條形碼類型](#barcode-types)。



```css
...
.barcode {
  -ro-replacedelement: barcode;
  -ro-barcode-type: code128;
}
...
```

執行上述步驟後，可以使用條形碼生成PDF輸出。

下面的螢幕快照在PDF輸出中顯示示例條形碼。

<img src="./assets/barcode-output-sample.png" alt="帶條形碼的示例輸出" width="700">


## 條形碼類型 {#barcode-types}

| 類型 | CSS屬性 | 附加屬性 |
| ------------------------------- | ----------------------- | -------------------------- |
| QR碼 | q碼 |  |
| PDF417 | pdf417 |  |
| 資料矩陣 | 資料矩陣 |  |
| 阿茲特克代碼 | Aztec碼 |  |
| 網格矩陣 | 網格矩陣 |  |
| Maxicode | 最大碼模式4 |  |
| 微QR | 微核 |  |
| 代碼1 | 代碼1 |  |
| 科達布洛克足球會 | 科達布洛克克 |  |
| GS1資料庫有限公司 | 資料庫限制 |  |
| GS1資料庫全向 | 資料庫全向 |  |
| EAN-13 | ean-13 |  |
| GS1-128(EAN-128) | code128 | -ro條形碼編碼：gs1; |
| ITF-14 | itf14 |  |
| UPC-A | 升降 |  |
| 代碼128 | code128 |  |
| 交錯2個（共5個） | 2of5交錯 |  |
| POSTNET | 郵戳 |  |
| 荷蘭郵政Kixcode | KX碼 |  |
| 《韓國郵報》 | 《韓國郵報》 |  |
| 德意志郵報 | dp-leitcode |  |
| 《澳大利亞郵報》 | 奧斯本 |  |
| 洛格馬爾 | 日誌 |  |
| 藥典 | 藥典 |  |
| USPS OneCode（智慧郵件） | usps-onecode |  |


