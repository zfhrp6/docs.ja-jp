---
title: "Potential Pitfalls in Data and Task Parallelism | Microsoft Docs"
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
  - "parallel programming, pitfalls"
ms.assetid: 1e357177-e699-4b8f-9e49-56d3513ed128
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# Potential Pitfalls in Data and Task Parallelism
<xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=fullName> および <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName> を使用すると、多くの場合、通常の順次ループよりもパフォーマンスが大幅に向上します。  ただし、ループを並列化すると、複雑性が増すため、シーケンシャル コードにおいて一般的でない問題、またはめったにない問題を引き起こす場合があります。  このトピックでは、並列ループを記述するときに避ける必要がある点について示します。  
  
## 並列が常に速いとは限らないことを理解する  
 場合によっては、並列ループは同等の順次ループよりも実行速度が遅くなることがあります。  基本的には、反復処理が少なく高速なユーザー デリゲートを使用する並列ループでは、実行速度が大幅に向上することはほとんどありません。  ただし、パフォーマンスには多くの要因が関係するため、常に実際の結果を測定することをお勧めします。  
  
## 共有メモリの位置への書き込みを回避する  
 シーケンシャル コードでは、静的変数またはクラス フィールドから読み取ったり、これらの場所に書き込んだりすることは珍しくありません。  ただし、複数のスレッドがこれらの変数に同時にアクセスしているときは、著しい競合状態になる場合がよくあります。  ロックを使用して変数へのアクセスを同期させることもできますが、同期のコストによってパフォーマンスが低下するおそれがあります。  このため、並列ループにおける共有状態へのアクセスは、できるだけ回避するか、少なくとも制限することをお勧めします。  この場合の最適な方法は、ループの実行中に <xref:System.Threading.ThreadLocal%601?displayProperty=fullName> 変数を使用してスレッド ローカルの状態を格納する、<xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=fullName> および <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName> のオーバーロードを使用することです。  詳細については、「[How to: Write a Parallel.For Loop with Thread\-Local Variables](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)」および「[How to: Write a Parallel.ForEach Loop with Thread\-Local Variables](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-thread-local-variables.md)」を参照してください。  
  
## 過剰な並列化を避ける  
 並列ループを使用すると、ソース コレクションのパーティション分割およびワーカー スレッドの同期でオーバーヘッド コストが発生します。  並列化の利点は、コンピューター上のプロセッサ数によってさらに制限されます。  1 つのプロセッサで複数の計算主体のスレッドを実行しても、高速にはなりません。  このため、ループを過剰に並列化しないように注意する必要があります。  
  
 過剰な並列化における最も一般的なシナリオは、入れ子のループが発生することです。  多くの場合、次の条件のうち 1 つ以上に当てはまらない限り、外側のループのみを並列化するのが最適です。  
  
-   内側のループが非常に長い。  
  
-   各順序で負荷の大きい計算を実行している \(この例で示した操作の負荷は大きくありません\)。  
  
-   対象のシステムに、`cust.Orders` でクエリを並列化して生成されるスレッドの数を十分に処理できるプロセッサが備わっている。  
  
 ほとんどの場合、適切なクエリの形を決定する最適な方法は、テストして計測することです。  
  
## スレッド セーフでないメソッドへの呼び出しを回避する  
 並列ループからスレッド セーフでないインスタンス メソッドへの書き込みを行うと、プログラムで検知されない可能性があるデータ破損が発生するおそれがあります。  例外が発生する可能性もあります。  次の例では、複数のスレッドが、クラスでサポートされていない <xref:System.IO.FileStream.WriteByte%2A?displayProperty=fullName> メソッドの同時呼び出しを試みます。  
  
 [!code-csharp[TPL_Pitfalls#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#04)]
 [!code-vb[TPL_Pitfalls#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#04)]  
  
## スレッド セーフなメソッドへの呼び出しを制限する  
 .NET Framework のほとんどの静的メソッドはスレッド セーフであり、複数のスレッドから同時に呼び出すことができます。  ただし、これらの場合でも、関連する同期によってはクエリの処理速度が著しく低下する場合があります。  
  
> [!NOTE]
>  これは、クエリ内に <xref:System.Console.WriteLine%2A> への呼び出しをいくつか挿入することでテストできます。  このメソッドは、ドキュメント例でデモのために使用されています。必要がない限り並列ループでは使用しないでください。  
  
## スレッドの関係に注意する  
 シングルスレッド アパートメント \(STA: Single\-Threaded Apartment\) コンポーネント向けの COM 相互運用性、Windows フォーム、WPF \(Windows Presentation Foundation\) などのテクノロジでは、特定のスレッドで実行するコードを必要とするスレッドの関係が制限される場合があります。  たとえば、Windows フォームと WPF では、コントロールへのアクセスは、そのコントロールが作成されたスレッド上でしか行うことができません。  つまり、例を挙げると、UI スレッド上のみで処理をスケジュールするようにスレッド スケジューラを構成しない限り、並列ループからはリスト コントロールを更新できません。  詳細については、「[How to: Schedule Work on the User Interface \(UI\) Thread](../Topic/How%20to:%20Schedule%20Work%20on%20the%20User%20Interface%20\(UI\)%20Thread.md)」を参照してください。  
  
## Parallel.Invoke によって呼び出されるデリゲートで待機する場合は注意する  
 状況によっては、タスク並列ライブラリでタスクをインライン展開します。つまり、現在実行されているスレッドでそのタスクが実行されます \(詳細については、「[Task Schedulers](../Topic/Task%20Schedulers.md)」を参照してください\)。場合によっては、このパフォーマンスの最適化により、デッドロックが発生することがあります。  たとえば、2 つのタスクで同じデリゲート コードを実行するとします。また、そのデリゲート コードは、イベントが発生することを通知し、もう一方のタスクが通知するまで待機するとします。  この場合、2 番目のタスクが 1 番目のタスクと同じスレッド上にインライン展開され、1 番目のタスクが待機状態になると、2 番目のタスクはイベントを通知できなくなってしまいます。  このような問題を避けるため、待機操作に対してタイムアウトを指定するか、明示的なスレッド コンストラクターを使用して、一方のタスクが他方のタスクをブロックしないようにすることができます。  
  
## ForEach、For、および ForAll の反復処理が常に並列実行されるとは限らないことを理解する  
 <xref:System.Threading.Tasks.Parallel.For%2A>、<xref:System.Threading.Tasks.Parallel.ForEach%2A>、または <xref:System.Linq.ParallelEnumerable.ForAll%2A> の各ループにおける個々の反復処理が必ずしも並列実行されるとは限らないことに注意してください。  したがって、反復処理の並列実行の正確性、または特定の順序による反復処理の実行の正確性に依存するコードは記述しないようにしてください。  たとえば、次のコードではデッドロックが発生する可能性があります。  
  
 [!code-csharp[TPL_Pitfalls#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#01)]
 [!code-vb[TPL_Pitfalls#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#01)]  
  
 この例では、1 つの反復処理はイベントを設定し、その他の反復処理はそのイベントを待機します。  待機の反復処理は、イベント設定の反復処理が完了するまで完了できません。  ただし、待機の反復処理によって、並列ループの実行に使用されるすべてのスレッドがブロックされ、イベント設定の反復処理がまったく実行されなくなる可能性があります。  この場合、イベント設定の反復処理が実行されず、待機の反復処理が待機したままの状態になるデッドロックが発生します。  
  
 つまり、処理を適切に進めるには、並列ループの特定の反復処理でそのループの別の反復処理を待機するのは避ける必要があります。  並列ループにおいて、反復処理が逆の順序で順次スケジュールされた場合、デッドロックが発生します。  
  
## UI スレッドでの並列ループの実行は避ける  
 アプリケーションのユーザー インターフェイス \(UI\) では、その応答性を保つ必要があります。  並列化が必要になる量の処理が 1 つの操作で行われる場合、その操作を UI スレッドで実行するのは良い方法ではありません。代わりに、バックグラウンド スレッドで実行されるその操作をオフロードしてください。  たとえば、特定のデータを計算し、その結果を UI コントロールに表示するために、並列ループを使用する場合は、UI イベント ハンドラーで直接実行するのではなく、タスク インスタンス内でループを実行することを検討する必要があります。主な計算が完了したときにだけ、UI 更新を UI スレッドにマーシャリングするようにします。  
  
 UI スレッドで並列ループを実行する場合は、そのループ内から UI コントロールを更新しないように注意する必要があります。  UI スレッドで実行されている並列ループ内から UI コントロールを更新しようとすると、UI 更新の呼び出し方法によっては、状態の破損、例外、更新の遅れ、さらにはデッドロックが発生する場合があります。  次の例では、並列ループが実行されている UI スレッドは、すべての反復処理が完了するまでループによってブロックされます。  ただし、このループの反復処理がバックグラウンド スレッドで実行されると \(<xref:System.Threading.Tasks.Parallel.For%2A> と同じ処理を行う\)、Invoke の呼び出しによって UI スレッドにメッセージが送信され、そのメッセージが処理されるのを待機することになります。  <xref:System.Threading.Tasks.Parallel.For%2A> を実行中の UI スレッドはブロックされているので、メッセージが処理されることはなく、UI スレッドでデッドロックが発生します。  
  
 [!code-csharp[TPL_Pitfalls#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#02)]
 [!code-vb[TPL_Pitfalls#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#02)]  
  
 タスク インスタンス内でループを実行することによってこのデッドロックを避ける方法を次の例に示します。  UI スレッドはループによってブロックされず、メッセージを処理できます。  
  
 [!code-csharp[TPL_Pitfalls#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#03)]
 [!code-vb[TPL_Pitfalls#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#03)]  
  
## 参照  
 [Parallel Programming](../../../docs/standard/parallel-programming/index.md)   
 [Potential Pitfalls with PLINQ](../../../docs/standard/parallel-programming/potential-pitfalls-with-plinq.md)   
 [Parallel Programming のパターン: .NET Framework 4 の Understanding and Applying Parallel Patterns](http://go.microsoft.com/fwlink/?LinkID=185142)