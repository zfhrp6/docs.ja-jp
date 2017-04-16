---
title: "Potential Pitfalls with PLINQ | Microsoft Docs"
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
  - "PLINQ queries, pitfalls"
ms.assetid: 75a38b55-4bc4-488a-87d5-89dbdbdc76a2
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 13
---
# Potential Pitfalls with PLINQ
PLINQ を使用すると、多くの場合、連続した LINQ to Objects クエリのパフォーマンスが大幅に向上します。  ただし、クエリの実行を並列化すると、複雑性が増すため、シーケンシャル コードにおいて一般的でない問題、またはめったにない問題を引き起こす場合があります。  このトピックでは、PLINQ クエリを記述するときに避ける必要がある点について示します。  
  
## 並列が常に速いとは限らないことを理解する  
 並列化することで、PLINQ クエリの実行速度が同等の LINQ to Objects より遅くなる場合があります。  基本の方針としては、クエリのソース要素を少なくし、高速化の可能性が低いユーザー デリゲートを使用することです。  ただし、パフォーマンスには多くの要因が関係するため、実際の結果を測定してから、PLINQ を使用するかどうかを決定することをお勧めします。  詳細については、「[Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)」を参照してください。  
  
## 共有メモリの位置への書き込みを回避する  
 シーケンシャル コードでは、静的変数またはクラス フィールドから読み取ったり、これらの場所に書き込んだりすることは珍しくありません。  ただし、複数のスレッドがこれらの変数に同時にアクセスしているときは、著しい競合状態になる場合がよくあります。  ロックを使用して変数へのアクセスを同期させることもできますが、同期のコストによってパフォーマンスが低下するおそれがあります。  このため、PLINQ クエリにおける共有状態へのアクセスは、できるだけ回避するか、少なくとも制限することをお勧めします。  
  
## 過剰な並列化を避ける  
 `AsParallel` 演算子を使用すると、ソース コレクションのパーティション分割およびワーカー スレッドの同期でオーバーヘッド コストが発生します。  並列化の利点は、コンピューター上のプロセッサ数によってさらに制限されます。  1 つのプロセッサで複数の計算主体のスレッドを実行しても、高速にはなりません。  このため、クエリを過剰に並列化しないように注意する必要があります。  
  
 過剰な並列化における最も一般的なシナリオは、次のスニペットで示すように、入れ子のクエリが発生することです。  
  
 [!code-csharp[PLINQ#20](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#20)]
 [!code-vb[PLINQ#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#20)]  
  
 この場合、次の条件のうち 1 つ以上が適用されない限り、外部データ ソース \(customers\) のみを並列化するのが最適です。  
  
-   内部データ ソース \(cust.Orders\) が非常に長い。  
  
-   各順序で負荷の大きい計算を実行している \(この例で示した操作の負荷は大きくありません\)。  
  
-   対象のシステムに、`cust.Orders` でクエリを並列化して生成されるスレッドの数を十分に処理できるプロセッサが備わっている。  
  
 ほとんどの場合、適切なクエリの形を決定する最適な方法は、テストして計測することです。  詳細については、「[How to: Measure PLINQ Query Performance](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md)」を参照してください。  
  
## スレッド セーフでないメソッドへの呼び出しを回避する  
 スレッド セーフでないインスタンス メソッドを PLINQ クエリから記述すると、プログラムで検知されない可能性があるデータ破損が発生するおそれがあります。  例外が発生する可能性もあります。  次の例では、複数のスレッドが、クラスでサポートされていない `Filestream.Write` メソッドの同時呼び出しを試みます。  
  
```vb  
Dim fs As FileStream = File.OpenWrite(…)  
a.Where(...).OrderBy(...).Select(...).ForAll(Sub(x) fs.Write(x))  
```  
  
```csharp  
FileStream fs = File.OpenWrite(...);  
a.Where(...).OrderBy(...).Select(...).ForAll(x => fs.Write(x));  
```  
  
## スレッド セーフなメソッドへの呼び出しを制限する  
 .NET Framework のほとんどの静的メソッドはスレッド セーフであり、複数のスレッドから同時に呼び出すことができます。  ただし、これらの場合でも、関連する同期によってはクエリの処理速度が著しく低下する場合があります。  
  
> [!NOTE]
>  これは、クエリ内に <xref:System.Console.WriteLine%2A> への呼び出しをいくつか挿入することでテストできます。  このメソッドは、ドキュメント例でデモのために使用されています。PLINQ クエリでは使用しないでください。  
  
## 不要な並べ替え操作を回避する  
 PLINQ を使用して 1 つのクエリを並列で実行すると、ソース シーケンスがパーティションに分割され、複数のスレッド上で同時に操作できるようになります。  既定では、パーティションが処理される順序と生成される結果は予測できません \(`OrderBy` などの演算子を除く\)。  PLINQ に、ソース シーケンスの順序を維持するように指示することもできますが、この操作はパフォーマンスの低下を招きます。  推奨される手順は、可能であれば、順序の維持に依存しないようにクエリを構成することです。  詳細については、「[Order Preservation in PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md)」を参照してください。  
  
## できる限り ForEach より ForAll を優先する  
 PLINQ では複数のスレッドで 1 つのクエリを実行しますが、`foreach` ループ \(Visual Basic の場合は `For Each`\) の結果を処理する場合、クエリ結果は 1 つのスレッドにマージされてから列挙子によって連続してアクセスされる必要があります。  これが避けられない場合もありますが、可能な場合は常に、`ForAll` メソッドを使用して各スレッドで固有の結果を出力できるようにします。たとえば、<xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=fullName> などのスレッド セーフなコレクションに書き込みます。  
  
 つまり、同じ問題が <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName>`source.AsParallel().Where().ForAll(...)` に厳密にどのように適用されます。  
  
 `Parallel.ForEach(source.AsParallel().Where(), ...)`.  
  
## スレッドの関係に注意する  
 シングルスレッド アパートメント \(STA: Single\-Threaded Apartment\) コンポーネント向けの COM 相互運用性、Windows フォーム、WPF \(Windows Presentation Foundation\) などのテクノロジでは、特定のスレッドで実行するコードを必要とするスレッドの関係が制限される場合があります。  たとえば、Windows フォームと WPF では、コントロールへのアクセスは、そのコントロールが作成されたスレッド上でしか行うことができません。  PLINQ クエリで Windows フォーム コントロールの共有状態にアクセスしようとすると、デバッガーを実行中である場合は例外が発生します \(この設定はオフにできます\)。ただし、クエリが UI スレッドで処理される場合は、コードが実行されるスレッドは 1 つだけであるため、クエリ結果を列挙する `foreach` ループからコントロールにアクセスできます。  
  
## ForEach、For、および ForAll の反復処理が常に並列実行されるとは限らないことを理解する  
 <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=fullName>、<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName>、または <xref:System.Linq.ParallelEnumerable.ForAll%2A> の各ループにおける個々の反復処理が必ずしも並列実行されるとは限らないことに注意してください。  したがって、反復処理の並列実行の正確性、または特定の順序による反復処理の実行の正確性に依存するコードは記述しないようにしてください。  
  
 たとえば、次のコードではデッドロックが発生する可能性があります。  
  
```vb  
Dim mre = New ManualResetEventSlim()  
    Enumerable.Range(0, ProcessorCount * 100).AsParallel().ForAll(Sub(j)   
  
                                                     If j = Environment.ProcessorCount Then  
  
                                                         Console.WriteLine("Set on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j)  
                                                         mre.Set()  
  
                                                     Else  
  
                                                         Console.WriteLine("Waiting on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j)  
                                                         mre.Wait()  
                                                     End If  
    End Sub) ' deadlocks  
```  
  
```csharp  
ManualResetEventSlim mre = new ManualResetEventSlim();  
            Enumerable.Range(0, ProcessorCount * 100).AsParallel().ForAll((j) =>  
            {  
                if (j == Environment.ProcessorCount)  
                {  
                    Console.WriteLine("Set on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j);  
                    mre.Set();  
                }  
                else  
                {  
                    Console.WriteLine("Waiting on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j);  
                    mre.Wait();  
                }  
            }); //deadlocks  
```  
  
 この例では、1 つの反復処理はイベントを設定し、その他の反復処理はそのイベントを待機します。  待機の反復処理は、イベント設定の反復処理が完了するまで完了できません。  ただし、待機の反復処理によって、並列ループの実行に使用されるすべてのスレッドがブロックされ、イベント設定の反復処理がまったく実行されなくなる可能性があります。  この場合、イベント設定の反復処理が実行されず、待機の反復処理が待機したままの状態になるデッドロックが発生します。  
  
 つまり、処理を適切に進めるには、並列ループの特定の反復処理でそのループの別の反復処理を待機するのは避ける必要があります。  並列ループにおいて、反復処理が逆の順序で順次スケジュールされた場合、デッドロックが発生します。  
  
## 参照  
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)