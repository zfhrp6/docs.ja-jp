---
title: "Data Parallelism (Task Parallel Library) | Microsoft Docs"
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
  - "parallelism, data"
ms.assetid: 3f05f33f-f1da-4b16-81c2-9ceff1bef449
caps.latest.revision: 25
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 25
---
# Data Parallelism (Task Parallel Library)
*データの並列化*とは、ソース コレクションまたは配列の要素に対して、同じ操作を同時に \(つまり、並列で\) 実行するシナリオを意味します。  データの並列化操作では、複数のスレッドが異なるセグメント上で同時に操作できるようにソース コレクションがパーティション分割されます。  
  
 タスク並列ライブラリ \(TPL\) は <xref:System.Threading.Tasks.Parallel?displayProperty=fullName> クラスによって、データの並列化をサポートします。  このクラスでは、[for](../Topic/for%20\(C%23%20Reference\).md) ループおよび [foreach](../Topic/foreach,%20in%20\(C%23%20Reference\).md) ループ \(Visual Basic では `For` および `For Each`\) をメソッド ベースで並列実装できます。  <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=fullName> ループまたは <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName> ループに対するループのロジックは、順次ループを記述する場合と同等に記述します。  スレッドまたはキューの作業項目を作成する必要はありません。  基本のループでは、ロックを取得する必要はありません。  TPL では低水準の作業はすべて自動的に行われます。  <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=fullName> および <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName> の使用方法の詳細については、ドキュメント「[Patterns for Parallel Programming: Understanding and Applying Parallel Patterns with the .NET Framework 4 \(並列プログラミングのパターン: .NET Framework 4 の並列パターンの理解と適用\)](http://www.microsoft.com/download/details.aspx?id=19222)」をダウンロードしてください。  次のコード例では、単純な `foreach` ループおよびそのループに相当する並列を示しています。  
  
> [!NOTE]
>  ここでは、ラムダ式を使用して TPL でデリゲートを定義します。  C\# または Visual Basic のラムダ式についての情報が必要な場合は、「[Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)」を参照してください。  
  
 [!code-csharp[TPL#20](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#20)]
 [!code-vb[TPL#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/tpl_vb.vb#20)]  
  
 並列ループを実行すると、TPL はデータ ソースをパーティション分割して、ループで複数の部分を同時に操作できるようにします。  背後では、タスク スケジューラが、システム リソースおよび作業負荷に基づいてタスクをパーティション分割します。  作業負荷のバランスが崩れると、可能な場合、スケジューラは複数のスレッドとプロセッサ間で作業を再配分します。  
  
> [!NOTE]
>  固有のカスタム パーティショナーまたはスケジューラを使うこともできます。  詳細については、「[Custom Partitioners for PLINQ and TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)」および「[Task Schedulers](../Topic/Task%20Schedulers.md)」を参照してください。  
  
 <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=fullName> メソッドおよび <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName> メソッドの両方に、ループの実行を停止または中断させるオーバーロードが複数ある場合は、その他のスレッドのループ状態の監視、スレッド ローカルの状態の維持、スレッド ローカル オブジェクトの終了、同時実行の程度の制御などを行います。  この機能を有効にするヘルパー要素には、<xref:System.Threading.Tasks.ParallelLoopState>、<xref:System.Threading.Tasks.ParallelOptions>、<xref:System.Threading.Tasks.ParallelLoopResult>、<xref:System.Threading.CancellationToken>、および <xref:System.Threading.CancellationTokenSource> があります。  
  
 詳細については、「[Patterns of Parallel Programming \(並列プログラミングのパターン\)](http://go.microsoft.com/fwlink/p/?LinkId=265491)」を参照してください。  
  
 PLINQ では、宣言構文またはクエリ形式の構文によるデータの並列化がサポートされています。  詳細については、「[Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)」を参照してください。  
  
## 関連トピック  
  
|タイトル|説明|  
|----------|--------|  
|[How to: Write a Simple Parallel.For Loop](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md)|任意の配列またはインデックス可能な <xref:System.Threading.Tasks.Parallel.For%2A> ソース コレクションに対して <xref:System.Collections.Generic.IEnumerable%601> ループを記述する方法について説明します。|  
|[How to: Write a Simple Parallel.ForEach Loop](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-foreach-loop.md)|任意の <xref:System.Threading.Tasks.Parallel.ForEach%2A> ソース コレクションに対して <xref:System.Collections.Generic.IEnumerable%601> ループを記述する方法について説明します。|  
|[How to: Stop or Break from a Parallel.For Loop](http://msdn.microsoft.com/ja-jp/de52e4f1-9346-4ad5-b582-1a4d54dc7f7e)|並列ループを停止するかまたは抜けて、そのアクションがすべてのスレッドに通知されるようにする方法について説明します。|  
|[How to: Write a Parallel.For Loop with Thread\-Local Variables](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)|各スレッドが他のスレッドからは見えないプライベート変数を維持する <xref:System.Threading.Tasks.Parallel.For%2A> ループを記述する方法と、ループが完了したときにすべてのスレッドの結果を同期する方法について説明します。|  
|[How to: Write a Parallel.ForEach Loop with Thread\-Local Variables](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-thread-local-variables.md)|各スレッドが他のスレッドからは見えないプライベート変数を維持する <xref:System.Threading.Tasks.Parallel.ForEach%2A> ループを記述する方法と、ループが完了したときにすべてのスレッドの結果を同期する方法について説明します。|  
|[How to: Cancel a Parallel.For or ForEach Loop](../../../docs/standard/parallel-programming/how-to-cancel-a-parallel-for-or-foreach-loop.md)|<xref:System.Threading.CancellationToken?displayProperty=fullName> を使用して並列ループを取り消す方法について説明します。|  
|[How to: Speed Up Small Loop Bodies](../../../docs/standard/parallel-programming/how-to-speed-up-small-loop-bodies.md)|ループの本体がごく小さい場合に実行速度を向上させる方法の 1 つを説明します。|  
|[Task Parallel Library \(TPL\)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|タスク並列ライブラリの概要を示します。|  
|[Parallel Programming](../../../docs/standard/parallel-programming/index.md)|.NET Framework の並列プログラミングについて説明します。|  
  
## 参照  
 [Parallel Programming](../../../docs/standard/parallel-programming/index.md)