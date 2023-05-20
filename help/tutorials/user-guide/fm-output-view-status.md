---
title: 查看輸出生成任務的狀態
description: 瞭解如何查看輸出生成任務的狀態
exl-id: 6fdaa547-8446-4ce5-95c3-a63d9c1f27d2
source-git-commit: c74badebbcb4733fb9caa79c646b1d1e5c8bfe8e
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---

# 查看輸出生成任務的狀態 {#viewing_output_history}

一旦您為FrameMaker文檔啟動輸出生成任務，「參考AEM線」會將此任務發送到輸出生成隊列。 此隊列將即時更新，顯示隊列中每個輸出生成任務的狀態。

執行以下步驟查看輸出生成隊列：

1. 在「資產」UI中，導航到要檢查其輸出生成狀態的FrameMaker文檔並按一下。

1. 按一下「Outputs（輸出）」。

   ![](images/output-queued-fm.png){width="800" align="left"}

1. 「輸出」(Outputs)頁面分為兩部分：

   - **排隊輸出：**

      列出等待生成或正在生成的輸出。 您還可以找到用於排隊任務的輸出生成設定或預設、類型、啟動任務的用戶、自任務排隊以來的時間以及當前狀態。

   - **生成的輸出**

      列出已完成的輸出任務。 同樣，此處顯示的資訊與「排隊輸出」部分類似，只有輸出生成時間的差異。

      在此清單中，您可能有成功執行的任務或失敗的任務。 對於成功完成的任務，發佈過程會建立日誌檔案\(logs.txt\)，通過按一下「生成時間」列中的連結可以訪問該檔案。


**父主題：**[&#x200B;生成FrameMaker文檔的輸出](fm-output-generatation.md)
