---
title: 拼寫檢查和查找/替換
description: 在參考線中使用拼寫檢查和查找/替AEM換
exl-id: 5f39618d-a919-4d3c-a4de-2896f2d1bf20
source-git-commit: 0b4326b02ef52f5de77c3f26c18feec84567cebb
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# 拼寫檢查和查找/替換

指南編AEM輯器具有強大的拼寫檢查和查找和替換功能。

>[!VIDEO](https://video.tv.adobe.com/v/342768)

更正拼寫錯誤

1. 在開啟的主題中查找錯誤，用紅色下划線顯示。

2. 按住Ctrl並按一下單詞中的輔助滑鼠按鈕。

3. 從建議中選擇正確的拼寫。

如果不建議正確拼寫，則始終可以手動編輯該詞。

## 切換到拼AEM寫檢查

您可能希望使用瀏覽器預設字典以外的拼寫檢查工具。

1. 導航到 **編輯器設定**。

2. 選擇 **常規** 頁籤。

   ![拼寫檢查配置](images/lesson-11/configure-dictionary.png)

3. 有兩種選擇：

   - **瀏覽器拼寫檢查**  — 拼寫檢查使用瀏覽器的內置詞典的預設設定。

   - **拼AEM寫檢查**  — 使用此命令使用自定義詞典生成自AEM定義詞清單。

4. 選擇 **拼AEM寫檢查**。

5. 按一下「[!UICONTROL **儲存**]」。

配置自定義詞典

管理員可以更改設定，AEM以便字典識別自定義詞，如公司名稱。

1. 導航到 **工具** 的子菜單。

2. 登錄到 **CRXDE Lite**。

   ![UIAEMCRXDE Lite表徵圖](images/lesson-11/crxde-lite.png)

3. 導航到 **_/apps/fmdita/config節點_**。

   ![CRXDE Lite配置節點](images/lesson-11/config-node.png)

4. 建立新檔案。

   a.按一下右鍵配置資料夾。

   b.選擇 **建立>建立檔案**。

   ![新建字典檔案建立](images/lesson-11/new-dictionary-file.png)

   c.命名檔案 _**user_dictionary.txt**_。

   ![用戶詞典文本](images/lesson-11/user-dictionary.png)

   d.按一下 [!UICONTROL **確定**]。

5. 開啟檔案。

6. 添加要包含在自定義詞典中的單詞清單。

7. 按一下 [!UICONTROL **全部保存**]。

8. 關閉檔案。

作者可能需要重新啟動其Web編輯器會話，以在詞典中獲取更新的自定義AEM詞清單。

## 在單個檔案中查找和替換

1. 按一下頂部工具欄上的「查找和替換」表徵圖。

   ![查找替換表徵圖](images/lesson-11/find-replace-icon.png)

2. 在底部工具欄中，鍵入單詞或短語。

3. 按一下 [!UICONTROL **查找**]。

4. 如果需要，鍵入一個詞以替換找到的詞。

5. 按一下 [!UICONTROL **替換**]。

## 在儲存庫中查找和替換

1. 導航到 **儲存庫**。

2. 按一下 [!UICONTROL **查找和替換**] 表徵圖。

3. 按一下 [!UICONTROL **顯示設定**] 表徵圖

4. 選擇

   - **替換前簽出檔案**  — 如果由管理員啟用，則在替換搜索項之前將自動簽出檔案。

   - **僅全字**  — 限制搜索僅返回輸入的確切字詞或短語。

   ![在儲存庫中查找替換](images/lesson-11/repository-find-replace.png)

5. 按一下 [!UICONTROL **應用篩選器**] 表徵圖，以在要執行搜索的儲存庫中選擇路徑。

6. 輸入要查找和替換的術語。

7. 如果需要，請選擇 **替換後建立新版本**。

8. 按一下 [!UICONTROL **查找**]。

9. 開啟所需檔案，然後使用箭頭從一個找到的結果導航到下一個結果。

   ![查找替換導航UI](images/lesson-11/find-replace-navigation.png)
