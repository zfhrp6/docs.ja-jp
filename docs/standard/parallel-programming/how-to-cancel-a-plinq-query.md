---
title: "How to: Cancel a PLINQ Query | Microsoft Docs"
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
  - "PLINQ queries, how to cancel"
  - "cancellation, PLINQ"
ms.assetid: 80b14640-edfa-4153-be1b-3e003d3e9c1a
caps.latest.revision: 16
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 16
---
# How to: Cancel a PLINQ Query
次の例では、PLINQ クエリを取り消す 2 とおりの方法を示します。  最初の例では、そのほとんどがデータ走査で構成されるクエリを取り消す方法を示します。  2 番目の例では、負荷の大きいユーザー関数を含むクエリを取り消す方法を示します。  
  
> [!NOTE]
>  \[マイ コードのみ\] が有効になっている場合、Visual Studio では、例外をスローする行で処理が中断され、"ユーザー コードで処理されない例外" に関するエラー メッセージが表示されます。このエラーは問題にはなりません。  F5 キーを押して、処理が中断された箇所から続行し、以下の例に示す例外処理動作を確認できます。  Visual Studio による処理が最初のエラーで中断しないようにするには、**\[ツール\]** メニューの \[オプション\]、\[デバッグ\] の順にクリックし、\[全般\] で \[マイ コードのみ\] チェック ボックスをオフにします。  
>   
>  この例は使用法を示すことを目的としており、同等の LINQ to Objects 順次クエリよりも実行速度が遅い場合があります。  高速化の詳細については、「[Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)」を参照してください。  
  
## 使用例  
 [!code-csharp[PLINQ#16](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#16)]
 [!code-vb[PLINQ#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#16)]  
  
 PLINQ のフレームワークでは、単一の <xref:System.OperationCanceledException> は <xref:System.AggregateException?displayProperty=fullName> に組み込まれないため、<xref:System.OperationCanceledException> を独立した catch ブロックとして扱う必要があります。  一つ以上のユーザー デリゲートが OperationCanceledException PLINQ が <xref:System.AggregateException?displayProperty=fullName>ではなく単一の <xref:System.OperationCanceledException> \(externalCT\) を出力 \(externalCT\) \(外部 <xref:System.Threading.CancellationToken?displayProperty=fullName>を使用\)、他の例外スローしないし、クエリが `AsParallel().WithCancellation(externalCT)`と定義されている。  ただし、1 つのユーザー デリゲートが <xref:System.OperationCanceledException> をスローし、別のデリゲートがその他の例外の種類をスローした場合は、両方の例外が <xref:System.AggregateException> に組み込まれます。  
  
 キャンセルの一般的なガイダンスを次に示します。  
  
1.  ユーザー デリゲートのキャンセルを実行する場合は、PLINQ に外部の <xref:System.Threading.CancellationToken> を示して、<xref:System.OperationCanceledException>\(externalCT\) をスローする必要があります。  
  
2.  キャンセルが発生したときに別の例外がスローされていない場合は、<xref:System.AggregateException> ではなく、<xref:System.OperationCanceledException> を処理する必要があります。  
  
## 使用例  
 次の例は、ユーザー コードに負荷の大きい関数が含まれる場合に、キャンセルを処理する方法を示しています。  
  
 [!code-csharp[PLINQ#17](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#17)]
 [!code-vb[PLINQ#17](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#17)]  
  
 キャンセルをユーザー コードで処理する場合、クエリの定義で <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> を使用する必要はありません。  ただし、<xref:System.Linq.ParallelEnumerable.WithCancellation%2A> はクエリのパフォーマンスに影響を与えず、クエリ演算子とユーザー コードによってキャンセルを処理できるようになるため、これを使用することをお勧めします。  
  
 システムの応答性を確認するため、ミリ秒ごとに一度程度の頻度でキャンセルをチェックすることをお勧めします。ただし、適切な期間と見なされるのは最大で 10 ミリ秒です。  この頻度によってコードのパフォーマンスが低下することはありません。  
  
 たとえば、コードで、クエリ結果を反復処理している foreach \(Visual Basic では For Each\) ループを中断したときなど、列挙子が破棄された場合、クエリは取り消されますが、例外がスローされることはありません。  
  
## 参照  
 <xref:System.Linq.ParallelEnumerable>   
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)   
 [Cancellation in Managed Threads](../../../docs/standard/threading/cancellation-in-managed-threads.md)