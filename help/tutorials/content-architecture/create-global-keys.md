---
title: 建立全局鍵
description: 如何建立要跨組織內容使用的全局鍵
role: Admin
exl-id: b8e3a6d2-ea82-4fdb-bd16-3f4b6594af52
source-git-commit: b5e64512956f0a7f33c2021bc431d69239f2a088
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---

# 建立全局鍵

組織應當在有一些可恢復的常見文本（如產品名稱或產品間距）時使用鍵，這些文本在許多地方都使用，但容易更改。 使用此類可重用文本的鍵，可以通過在單個位置（如鍵值）進行更改，在多個位置推送更新。

## 步驟1:建立用於儲存密鑰的全局映射

建立映射並添加 [!UICONTROL 鍵] 元素。

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE map PUBLIC "-//OASIS//DTD DITA Map//EN" "technicalContent/dtd/map.dtd">
<mapid="map.ditamap_ffbdbf06-8658-4311-ad84-1c631bba904f">
  <title>global-keys-map</title>
  <keydefkeys="adobe">
    <topicmeta>
      <linktext>Adobe Systems</linktext>
    </topicmeta>
  </keydef>
  <keydefkeys="AEM">
    <topicmeta>
      <linktext>Adobe Experience Manager</linktext>
    </topicmeta>
  </keydef>
</map>
```

在此，您定義了兩個定義，如上所示 [!UICONTROL 鍵] 如 _AEM_ 為 _Adobe Experience Manager_ 的子菜單。

## 步驟2:將此映射添加到發佈映射

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE map PUBLIC "-//OASIS//DTD DITA Map//EN" "technicalContent/dtd/map.dtd">
<mapid="map.ditamap_cbf4a96d-e382-4e8c-8830-bcc093fe6638">
  <title>sample-map</title>
  <topicrefhref="sample-topic-using-the-keys.dita"type="topic">
  </topicref>
  <maprefformat="ditamap"href="global-keys-map.ditamap"type="map">
  </mapref>
</map>
```

## 第3步：使用鍵引用全局鍵映射中定義的變數

+ 使用 [!UICONTROL 鍵]。
+ 如螢幕截圖所示，將出現一個小窗口，從中可以選擇關鍵字。 在添加「關鍵字」元素時，將顯示該資訊。
   ![插入元素](assets/insert_element.png)
   ![鍵引用](assets/key_ref.png)

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE topic PUBLIC "-//OASIS//DTD DITA Topic//EN" "technicalContent/dtd/topic.dtd">
<topicid="topic.dita_31b00e61-04b5-4193-af7a-68503e88b087">
  <title>sample-topic-using-the-keys</title>
  <shortdesc></shortdesc>
  <body>
    <p>This is a sample topic using the keys defined in the global map</p>
    <p>here i am using the key definition for AEM :<keywordkeyref="AEM"></keyword></p>
  </body>
</topic>
```
