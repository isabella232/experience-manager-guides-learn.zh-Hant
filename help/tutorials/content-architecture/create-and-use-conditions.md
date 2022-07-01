---
title: 建立和使用條件
description: 瞭解如何建立條件，然後在中設定條件內容生成 [!DNL AEM Guides]
role: User
exl-id: a86007e3-48d1-458b-84a7-b683e113e5b2
source-git-commit: b5e64512956f0a7f33c2021bc431d69239f2a088
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# 建立和使用條件並生成條件輸出

**用例**

* 作者可以設定內容條件，以便控制內容是否顯示在輸出中。

* 作者可在發佈時選擇顯示/隱藏不同的條件。

* 例如，作者可以在內容中添加作為版本1.0和版本2.0的屬性，並使用條件將版本1.0包括在版本1.0中，並排除版本2.0。

**步驟 1**

定義與中的文檔相關的條件 [!UICONTROL 資料夾配置檔案]:請參閱部分 **配置全局或資料夾級配置檔案的條件屬性** 在 [《安裝及設定指南》第64頁](https://helpx.adobe.com/content/dam/help/en/xml-documentation-solution/3-8/XML-Documentation-for-Adobe-Experience-Manager_Installation-Configuration-Guide_EN.pdf)

![在資料夾配置檔案中配置條件](assets/conditions-in-profiles.png)

**步驟2**

選擇 **[!UICONTROL 資料夾配置檔案]** 在第1步中定義 **用戶首選項** 在XML編輯器中：請參閱部分 **用戶首選項** 在 [《使用手冊》第39頁](https://helpx.adobe.com/content/dam/help/en/xml-documentation-solution/3-8/XML-Documentation-for-Adobe-Experience-Manager_User-Guide_EN.pdf)


**步驟3**

使用條件對內容的節進行條件化：請參閱部分 **條件** 在 [使用手冊第81頁](https://helpx.adobe.com/content/dam/help/en/xml-documentation-solution/3-8/XML-Documentation-for-Adobe-Experience-Manager_User-Guide_EN.pdf)

![Web編輯器中的使用條件](assets/conditions-in-web-editor.png)

**步驟4**

在映射級別定義條件預設，以選擇要在輸出中啟用的條件：請參閱部分 **使用條件預設** 在 [《使用手冊》第184頁](https://helpx.adobe.com/content/dam/help/en/xml-documentation-solution/3-8/XML-Documentation-for-Adobe-Experience-Manager_User-Guide_EN.pdf)
