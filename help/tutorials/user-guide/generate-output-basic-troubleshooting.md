---
title: 基本疑難排解
description: 瞭解基本疑難排解
exl-id: b5ab2618-6f11-4aaa-8471-09521f8bb512
source-git-commit: c74badebbcb4733fb9caa79c646b1d1e5c8bfe8e
workflow-type: tm+mt
source-wordcount: '669'
ht-degree: 0%

---

# 基本疑難排解 {#id1821I0Y0G0A}

使用AEM Guides時，在發佈或開啟檔案時可能會發生錯誤。 這類錯誤可能在DITA map、主題或AEM Guides處理本身中出現。 本節提供如何存取及剖析輸出產生記錄檔中資訊的相關資訊。 此外，如果您的DITA主題太大，您可能會看到JSP編譯錯誤。 本節也提供如何解決JSP編譯錯誤的資訊。

## 檢視並檢查記錄檔 {#id1822G0P0CHS}

執行以下步驟來檢視及檢查輸出產生記錄檔：

1. 啟動輸出產生程式後，請按一下 **輸出** DITA map主控台中的。

   此 **一般** 的欄 **產生的輸出** 顯示圖示，以提供輸出產生成功或失敗的視覺化提示。

   ![](images/output-general-settings.png){width="300" align="left"}

   在上面的熒幕擷圖中，第一個和第三個圖示顯示無法產生的輸出。 第二個圖示會顯示成功的輸出產生，但會有訊息。 最後一個是成功產生輸出，且沒有任何訊息。

1. 按一下 **產生時間** 工作完成後的欄。

   記錄檔會在新標籤中開啟。

   ![](images/log-file.png){width="800" align="left"}

1. 套用下列篩選器以反白標示記錄檔中的文字：
   - 致命：以粉紅色標示記錄檔中的嚴重錯誤。
   - 錯誤：以橘色標示記錄檔中的錯誤。
   - 警告：以紫色醒目提示記錄檔中的警告。
   - 資訊：以藍色反白標示記錄檔中的資訊訊息。
   - 例外：以黃色反白標示記錄檔中的例外。
1. 使用向上和向下導覽按鈕跳至記錄檔案中反白顯示的文字。

   或者，捲動記錄檔並檢查訊息。


## 在文字編輯器中複製並檢查記錄檔

執行以下步驟，在文字編輯器中複製並檢查輸出產生記錄檔：

1. 啟動輸出產生程式後，請按一下 **輸出** DITA map主控台中的。

1. 按一下 **產生時間** 工作完成後的欄。

   記錄檔會在新標籤中開啟。

1. 按一下 **複製記錄** 按鈕。 記錄檔會複製到剪貼簿。
1. 開啟文字編輯器，並在編輯器中貼上記錄檔。

1. 捲動記錄檔並檢查訊息。

   下列資訊可協助您判斷DITA檔案或AEM Guides處理序中是否有錯誤：

   - *DITA map檔案相關錯誤*：如果在DITA map檔案或DITA map中包含的任何其他檔案中發現錯誤，記錄檔將包含字串「BUILD FAILED」。 您可以檢查記錄檔中提供的資訊，以找出錯誤的檔案並修正問題。

   在以下記錄檔片段範例中，您可以看到 `BUILD FAILED` 訊息以及錯誤原因。

   ![](images/dita-error-in-log-file.png){width="650" align="left"}

   - *AEM Guides相關錯誤*：您可以在記錄檔中識別的其他錯誤型別，與AEM Guides程式本身有關。 在此情況下，DITA map檔案剖析成功，但輸出產生程式因AEM Guides中的某些內部錯誤而失敗。 對於這類錯誤，您必須尋求技術支援團隊的協助。

   在以下記錄檔片段範例中，您可以看到 `BUILD SUCCESSFUL` 訊息，接著顯示其他技術錯誤。

   ![](images/process-error-in-log-file.png){width="650" align="left"}


## 解決JSP編譯錯誤

如果您的DITA主題太大，您可能會看到JSP編譯錯誤\(`org.apache.sling.api.request.TooManyCallsException`\)時。 當您開啟主題進行編輯、稽核或發佈時，可能會出現此錯誤。

執行以下步驟以解決此問題：

1. 從「全域導覽」中，選取「工具」，然後選擇「作業」\>「Web主控台」。

   便會顯示「Adobe Experience Manager Web主控台組態」頁面。

1. 搜尋並按一下 *Apache Sling主要Servlet* 元件。

   隨即顯示Apache Sling主要Servlet的可設定選項。

1. 增加 *每個請求的呼叫數* 引數。


**父級主題：**[&#x200B;輸出產生](generate-output.md)
