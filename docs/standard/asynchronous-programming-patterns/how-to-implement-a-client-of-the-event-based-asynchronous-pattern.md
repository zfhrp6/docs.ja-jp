---
title: "How to: Implement a Client of the Event-based Asynchronous Pattern | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Event-based Asynchronous Pattern"
  - "ProgressChangedEventArgs class"
  - "BackgroundWorker component"
  - "events [.NET Framework], asynchronous"
  - "Asynchronous Pattern"
  - "AsyncOperationManager class"
  - "threading [.NET Framework], asynchronous features"
  - "components [.NET Framework], asynchronous"
  - "AsyncOperation class"
  - "threading [Windows Forms], asynchronous features"
  - "AsyncCompletedEventArgs class"
ms.assetid: 21a858c1-3c99-4904-86ee-0d17b49804fa
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# How to: Implement a Client of the Event-based Asynchronous Pattern
「[Event\-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)」に従ってコンポーネントを使用する方法のコード例を次に示します。  この例のフォームでは、「[How to: Implement a Component That Supports the Event\-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)」で説明した  `PrimeNumberCalculator`  コンポーネントを使用します。  
  
 この例を使用するプロジェクトを実行すると、"Prime Number Calculator" フォームにグリッドと 2 つのボタン \(**\[Start New Task\]** および **\[Cancel\]**\) が表示されます。  **\[Start New Task\]** ボタンは、続けて何度もクリックできます。クリックするたびに、非同期操作によって計算が開始され、ランダムに生成されたテスト数値が素数かどうかが調べられます。  フォームには定期的に進行状況およびインクリメンタル結果が表示されます。  各操作には一意のタスク ID が割り当てられます。  計算結果は **\[Result\]** 列に表示されます。テスト数値が素数でない場合は、**\[Composite\]** とラベルが付けられ、最初の約数が表示されます。  
  
 **\[Cancel\]** ボタンを使用すると、任意の保留中の操作をキャンセルできます。  複数選択できます。  
  
> [!NOTE]
>  大部分の数値は素数ではありません。  いくつもの操作を完了しても素数が見つからない場合は、さらにタスクを開始すると、いずれ素数が見つかります。  
  
## 使用例  
 [!code-csharp[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#10)]
 [!code-vb[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#10)]  
  
## 参照  
 <xref:System.ComponentModel.AsyncOperation>   
 <xref:System.ComponentModel.AsyncOperationManager>   
 <xref:System.Windows.Forms.WindowsFormsSynchronizationContext>