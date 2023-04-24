---
title: 拼寫檢查和查找/替換
description: 在AEM指南中使用拼字檢查和尋找/取代
exl-id: 5f39618d-a919-4d3c-a4de-2896f2d1bf20
source-git-commit: 67ba514616a0bf4449aeda035161d1caae0c3f50
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# 拼寫檢查和查找/替換

AEM指南編輯器具有強大的拼字檢查和尋找及取代功能。

>[!VIDEO](https://video.tv.adobe.com/v/342768?quality=12&learn=on)

更正拼寫錯誤

1. 在開啟的主題中找出錯誤，顯示為紅色底線。

1. 按住Ctrl鍵並按一下單詞內的滑鼠輔助按鈕。

1. 從建議中選擇正確的拼字。

如果不建議正確拼寫，則始終可以手動編輯單詞。

## 切換至AEM拼字檢查

您可能想使用瀏覽器預設字典以外的拼字檢查工具。

1. 導覽至 **編輯器設定**.

1. 選取 **一般** 設定標籤。

   ![拼字檢查配置](images/lesson-11/configure-dictionary.png)

1. 有兩個選項：

   - **瀏覽器拼字檢查**  — 拼寫檢查使用瀏覽器內建字典的預設設定。

   - **AEM拼字檢查**  — 使用它來使用AEM自訂字典建立自訂字詞清單。

1. 選擇 **AEM拼字檢查**.

1. 按一下「[!UICONTROL **儲存**]」。

設定自訂字典

管理員可以變更設定，讓AEM字典辨識自訂單字，例如公司名稱。

1. 導覽至 **工具** 框。

1. 登入 **CRXDE Lite**.

   ![AEM UICRXDE Lite圖示](images/lesson-11/crxde-lite.png)

1. 導覽至 **_/apps/fmdita/config節點_**.

   ![CRXDE Lite配置節點](images/lesson-11/config-node.png)

1. 建立新檔案。

   a.以滑鼠右鍵按一下設定資料夾。

   b.選擇 **建立>建立檔案**.

   ![新建字典檔案](images/lesson-11/new-dictionary-file.png)

   c.為檔案命名 _**user_dictionary.txt**_.

   ![用戶字典文本](images/lesson-11/user-dictionary.png)

   d.按一下 [!UICONTROL **確定**].

1. 開啟檔案。

1. 新增您要加入自訂字典的單字清單。

1. 按一下 [!UICONTROL **全部儲存**].

1. 關閉檔案。

作者可能需要重新啟動其網頁編輯器工作階段，才能在AEM字典中取得更新的自訂字詞清單。

## 在單一檔案中尋找和取代

1. 按一下頂端工具列上的「尋找和取代」圖示。

   ![查找替換表徵圖](images/lesson-11/find-replace-icon.png)

1. 在底部工具列中，輸入字詞或片語。

1. 按一下 [!UICONTROL **查找**].

1. 如果需要，鍵入一個詞替換找到的詞。

1. 按一下 [!UICONTROL **取代**].

## 在整個儲存庫中查找和替換

1. 導覽至 **存放庫**.

1. 按一下 [!UICONTROL **查找和替換**] 圖示。

1. 按一下 [!UICONTROL **顯示設定**] 表徵圖。

1. 選擇

   - **取代前的結帳檔案**  — 如果由管理員啟用，則在替換搜索詞之前會自動簽出該檔案。

   - **僅全字**  — 限制搜索只返回輸入的確切字詞或片語。

   ![在儲存庫中查找替換](images/lesson-11/repository-find-replace.png)

1. 按一下 [!UICONTROL **套用篩選**] 表徵圖，以在要執行搜索的儲存庫中選擇路徑。

1. 輸入要查找和替換的術語。

1. 如果需要，請選擇 **替換後建立新版本**.

1. 按一下 [!UICONTROL **查找**].

1. 開啟所需的檔案，並使用箭頭從一個找到的結果導覽至下一個結果。

   ![查找替換導航UI](images/lesson-11/find-replace-navigation.png)
