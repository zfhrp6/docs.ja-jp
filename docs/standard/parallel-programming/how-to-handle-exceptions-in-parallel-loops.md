---
title: "How to: Handle Exceptions in Parallel Loops | Microsoft Docs"
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
  - "parallel loops, how to handle exceptions"
ms.assetid: 512f0d5a-4636-4875-b766-88f20044f143
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# How to: Handle Exceptions in Parallel Loops
<xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=fullName> および <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName> のオーバーロード には、スローされる可能性のある例外を処理する特別な仕組みはありません。  この点では、標準の `for` ループおよび `foreach` ループ \(Visual Basic では `For` と `For Each`\) と似ており、処理されない例外でループはすぐに終了します。  
  
 独自の例外処理のロジックを並列ループに追加する場合は、同様の例外が複数のスレッドに同時にスローされるケース、および特定のスレッドにスローされる例外が、別のスレッドに別の例外をスローするケースを処理してください。  <xref:System.AggregateException?displayProperty=fullName> のループからすべての例外をラップすることで、両方のケースを処理できます。   考えられる方法の 1 つの例を次に示します。  
  
> [!NOTE]
>  \[マイ コードのみ\] が有効になっている場合、Visual Studio では、例外をスローする行で処理が中断され、"ユーザー コードで処理されない例外" に関するエラー メッセージが表示されることがあります。 このエラーは問題にはなりません。  F5 キーを押して、処理が中断された箇所から続行し、以下の例に示す例外処理動作を確認できます。  Visual Studio による処理が最初のエラーで中断しないようにするには、**\[ツール\] メニューの \[オプション\]、\[デバッグ\] の順にクリックし、\[全般\]** で \[マイ コードのみ\] チェック ボックスをオフにします。  
  
## 使用例  
 この例では、すべての例外がキャッチされた後に <xref:System.AggregateException?displayProperty=fullName> にラップされ、スローされます。    呼び出し元は、どの例外を処理するかを決定できます。  
  
 [!code-csharp[TPL_Exceptions#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#08)]
 [!code-vb[TPL_Exceptions#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionsinloops.vb#08)]  
  
## 参照  
 [Data Parallelism](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)   
 [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)