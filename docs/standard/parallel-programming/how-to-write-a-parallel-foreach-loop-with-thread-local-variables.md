---
title: "How to: Write a Parallel.ForEach Loop with Thread-Local Variables | Microsoft Docs"
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
  - "parallel foreach loop, how to use local state"
ms.assetid: 24b10041-b30b-45cb-aa65-66cf568ca76d
caps.latest.revision: 18
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 18
---
# How to: Write a Parallel.ForEach Loop with Thread-Local Variables
スレッド ローカル変数を持つ <xref:System.Threading.Tasks.Parallel.ForEach%2A> メソッドを記述する方法を次の例に示します。  <xref:System.Threading.Tasks.Parallel.ForEach%2A> ループが実行されると、そのソース コレクションが複数のパーティションに分割されます。  各パーティションには、"スレッド ローカル" 変数が個別にコピーされます   \("スレッド ローカル" という用語は少し不正確です。1 つのスレッド上で 2 つのパーティションが実行されることがあるからです\)。  
  
 この例のコードおよびパラメーターは、対応する <xref:System.Threading.Tasks.Parallel.For%2A> メソッドによく似ています。  詳細については、「[How to: Write a Parallel.For Loop with Thread\-Local Variables](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)」を参照してください。  
  
 <xref:System.Threading.Tasks.Parallel.ForEach%2A> ループでスレッド ローカル変数を使用するには、2 つのタイプのパラメーターを取るメソッド オーバーロードのうち、いずれか 1 つを呼び出す必要があります。  最初の型パラメーター `TSource` でソース要素の型を指定し、2 番目の型パラメーター `TLocal` でスレッド ローカル変数の型を指定します。  
  
## 使用例  
 以下の例では、<xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=fullName> のオーバーロードを呼び出して、100 万個の要素からなる配列の合計を計算します。  このオーバーロードには、4 つのパラメータがあります。  
  
-   `source`。データ ソースです。  これは、<xref:System.Collections.Generic.IEnumerable%601> を実装する必要があります。  この例のデータ ソースは、<xref:System.Linq.Enumerable.Range%2A?displayProperty=fullName> によって返される、100 万個のメンバーからなる `IEnumerable<Int32>` オブジェクトです。  
  
-   `localInit`。またはスレッド ローカル変数を初期化する関数です。  この関数は、<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName> 操作が実行される各パーティションで 1 回呼び出されます。  この例では、スレッド ローカル変数がゼロに初期化されます。  
  
-   `body`。ループの各反復処理に対して並列ループで呼び出される <xref:System.Func%604> です。  シグニチャは `Func\<TSource, ParallelLoopState, TLocal, TLocal>` です。  プログラマはデリゲートのコードを作成します。入力パラメーターはループから渡されます。これらの入力パラメーターは以下のとおりです。  
  
    -   <xref:System.Collections.Generic.IEnumerable%601> の現在の要素。  
  
    -   <xref:System.Threading.Tasks.ParallelLoopState> 変数。デリゲートのコードで、ループの状態を確認するために使用できます。  
  
    -   スレッド ローカル変数。  
  
     デリゲートからスレッド ローカル変数が返されると、その変数は、その特定のパーティションで実行されるループの次の反復処理に渡されます。  ループ パーティションごとに、この変数の個別のインスタンスが保持されます。  
  
     この例では、デリゲートによって個々の整数の値がスレッド ローカル変数に追加されます。スレッド ローカル変数には、そのパーティションで順次追加される整数要素の値の現在の合計が保持されます。  
  
-   `localFinally`。各パーティションでのループ操作が完了した時点で、<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName> によって呼び出される `Action<TLocal>` デリゲート。  <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName> メソッドは、`Action<TLocal>` デリゲートに、このスレッド \(ループ パーティション\) のスレッド ローカル変数の最終値を返します。プログラマは、このパーティションの結果と他のパーティションの結果を結合するために必要な操作を実行するコードを作成します。  このデリゲートは、複数のタスクで同時に呼び出すことができます。  このため、この例では `total` 変数へのアクセスを同期するために <xref:System.Threading.Interlocked.Add%28System.Int32%40%2CSystem.Int32%29?displayProperty=fullName> メソッドが使用されます。  デリゲート型は <xref:System.Action%601> であるため、戻り値はありません。  
  
 [!code-csharp[TPL_Parallel#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/foreachthreadlocal.cs#04)]
 [!code-vb[TPL_Parallel#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/foreachthreadlocal.vb#04)]  
  
## 参照  
 [Data Parallelism](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)   
 [How to: Write a Parallel.For Loop with Thread\-Local Variables](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)   
 [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)