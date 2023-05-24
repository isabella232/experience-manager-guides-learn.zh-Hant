---
title: 檢視輸出產生任務的狀態
description: 瞭解如何檢視輸出產生任務的狀態
exl-id: 6fdaa547-8446-4ce5-95c3-a63d9c1f27d2
source-git-commit: c74badebbcb4733fb9caa79c646b1d1e5c8bfe8e
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---

# 檢視輸出產生任務的狀態 {#viewing_output_history}

啟動FrameMaker檔案的輸出產生任務後，AEM Guides會將此任務傳送至輸出產生佇列。 此佇列會即時更新，顯示佇列中每個輸出產生任務的狀態。

執行以下步驟來檢視輸出產生佇列：

1. 在Assets UI中，導覽至並按一下您要檢查其輸出產生狀態的FrameMaker檔案。

1. 按一下「輸出」。

   ![](images/output-queued-fm.png){width="800" align="left"}

1. 「輸出」頁面分為兩個部分：

   - **佇列輸出：**

      列出等待產生或正在產生過程中的輸出。 您也可以找到用於已排入佇列之任務的輸出產生設定或預設集、型別、起始任務的使用者、自任務排入佇列以來的時間以及目前狀態。

   - **產生的輸出**

      列出已完成的輸出工作。 同樣地，此處顯示的資訊類似於「排入佇列的輸出」區段，只有輸出產生時間的差異。

      在此清單中，您可能會有成功執行或失敗的任務。 對於已成功完成的工作，發佈程式會建立記錄檔\(logs.txt\)，按一下「產生時間」欄中的連結即可存取該記錄檔。


**父級主題：**[&#x200B;產生FrameMaker檔案的輸出](fm-output-generatation.md)
