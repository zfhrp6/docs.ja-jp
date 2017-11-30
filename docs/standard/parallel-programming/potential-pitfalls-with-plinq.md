---
title: "PLINQ の非利便性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: PLINQ queries, pitfalls
ms.assetid: 75a38b55-4bc4-488a-87d5-89dbdbdc76a2
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f7c971d2c039e6441669108e966eba472819fde5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="potential-pitfalls-with-plinq"></a>PLINQ の非利便性
多くの場合、PLINQ は、順次の LINQ to Objects クエリ経由で大幅なパフォーマンス向上を提供できます。 ただし、クエリの実行を並列化には、問題が発生するの順次のコードに、一般的ではないまたはめったにない可能性がある複雑さが導入されています。 このトピックでは、PLINQ クエリを記述するときを防ぐためのいくつかの事項を示します。  
  
## <a name="do-not-assume-that-parallel-is-always-faster"></a>並列処理が常に高速であると思い込まない  
 並列処理こともありますが、PLINQ クエリを同等のオブジェクトに、LINQ より時間がかかります実行発生します。 基本的な経験則は、いくつかのソース要素とユーザーの簡易デリゲートを持つクエリがないことにより高速化する可能性がはるかです。 ただし、パフォーマンスには、多くの要因が関係する、ため PLINQ を使用するかどうかを決定する前に、実際の結果を測定することお勧めします。 詳細については、「[Understanding Speedup in PLINQ (PLINQ での高速化について)](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)」を参照してください。  
  
## <a name="avoid-writing-to-shared-memory-locations"></a>共有メモリの位置への書き込みを回避する  
 逐次コードでは、静的変数またはクラス フィールドから読み取ることや、これらの場所に書き込むことはよくあります。 ただし、複数のスレッドからこのような変数に同時にアクセスしているときは、著しい競合状態になる場合がよくあります。 ロックを使用して変数へのアクセスを同期できる場合でも、同期のコストでパフォーマンスが低下する可能性があります。 したがって、することを避けるため、または少なくとも制限可能な限り PLINQ クエリ内の共有状態へのアクセスをお勧めします。  
  
## <a name="avoid-over-parallelization"></a>過剰な並列化を回避する  
 使用して、`AsParallel`ソース コレクションを分割して、ワーカー スレッドの同期のオーバーヘッド コストが発生する演算子です。 並列化の利点は、コンピューター上のプロセッサ数によってさらに制限されます。 1 つのプロセッサで複数の計算主体のスレッドを実行しても、高速化は実現しません。 したがって、過剰なクエリの並列化しないように注意する必要があります。  
  
 最も一般的なシナリオでは、次のスニペットに示すように、入れ子になったクエリではどの過剰な並列化が発生することができます。  
  
 [!code-csharp[PLINQ#20](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#20)]
 [!code-vb[PLINQ#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#20)]  
  
 ここを次の条件の 1 つ以上を適用しない限り、外部データ ソース (顧客) だけを並列化することをお勧めします。  
  
-   内部データ ソース (cust です。注文) は非常に長い呼ばれます。  
  
-   各順序で高負荷の計算を実行している  (この例に示す操作の負荷は大きくありません)。  
  
-   対象システムに、`cust.Orders` でクエリを並列化することで生成されるスレッドの数を十分に処理できるプロセッサが存在している。  
  
 どの場合も、最適なクエリの形式を決定する最善の方法は、テストおよび測定することです。 詳細については、次を参照してください。[する方法: PLINQ クエリのパフォーマンスを測定](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md)です。  
  
## <a name="avoid-calls-to-non-thread-safe-methods"></a>スレッド セーフでないメソッドの呼び出しを回避する  
 クエリは、PLINQ から非スレッド セーフなインスタンス メソッドへの書き込みがあり、プログラムで検出されない可能性がありますいないデータが破損する可能性があります。 例外が発生する可能性もあります。 次の例では、複数のスレッドとする呼び出しを試みると、`Filestream.Write`メソッド、クラスによってサポートされていない、同時にします。  
  
```vb  
Dim fs As FileStream = File.OpenWrite(…)  
a.Where(...).OrderBy(...).Select(...).ForAll(Sub(x) fs.Write(x))  
```  
  
```csharp  
FileStream fs = File.OpenWrite(...);  
a.Where(...).OrderBy(...).Select(...).ForAll(x => fs.Write(x));  
```  
  
## <a name="limit-calls-to-thread-safe-methods"></a>スレッド セーフなメソッドの呼び出しを制限する  
 .NET Framework のほとんどの静的メソッドはスレッド セーフであり、複数のスレッドから同時に呼び出すことができます。 ただし、このような場合でも、関連する同期によっては、クエリの処理速度が大幅に低下する可能性があります。  
  
> [!NOTE]
>  テストできますこの自分でいくつかの呼び出しを挿入することで<xref:System.Console.WriteLine%2A>クエリにします。 このメソッドは、デモンストレーションのためのドキュメントの例で使用されますが、PLINQ クエリで使用しないでください。  
  
## <a name="avoid-unnecessary-ordering-operations"></a>不要な並べ替え操作を回避します。  
 PLINQ では、並列クエリを実行したときに、ソース シーケンスを処理できる同時に複数のスレッドでのパーティションに分割します。 既定では、パーティションが処理され、結果が配信されるの順序は予測可能な (などの演算子を除く`OrderBy`)。 任意のソース シーケンスの順序を保持するために PLINQ に指示できますが、パフォーマンスに悪影響を及ぼしますこれです。 ベスト プラクティス、可能な限りはクエリを構築する順序の維持に依存しないようにします。 詳細については、「[Order Preservation in PLINQ (PLINQ における順序維持)](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md)」を参照してください。  
  
## <a name="prefer-forall-to-foreach-when-it-is-possible"></a>ForAll (_n) 可能であれば ForEach と  
 PLINQ クエリを実行、複数のスレッドの結果を処理する場合は、`foreach`ループ (`For Each` Visual Basic で)、クエリの結果を 1 つのスレッドに反映され、列挙子が順番にアクセスする必要があります。 場合によっては、これは回避できません。ただし、可能な限り、使用、`ForAll`など、スレッド セーフ コレクションへの書き込みなど、独自の結果を出力するには、各スレッドを有効にするメソッド<xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>です。  
  
 同じ問題の適用対象<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>言い換えれば、`source.AsParallel().Where().ForAll(...)`を強く推奨される必要があります  
  
 `Parallel.ForEach(source.AsParallel().Where(), ...)`。  
  
## <a name="be-aware-of-thread-affinity-issues"></a>スレッド アフィニティの問題に注意する  
 シングル スレッド アパートメント (STA) コンポーネント向けの COM 相互運用性、Windows フォーム、Windows Presentation Foundation (WPF) などの一部のテクノロジでは、特定のスレッド上で実行するコードを必要とするスレッド アフィニティが制限される場合があります。 たとえば、Windows フォームと WPF では、コントロールへのアクセスは、そのコントロールが作成されたスレッド上でしか行うことができません。 PLINQ クエリの Windows フォーム コントロールの共有状態にアクセスしようとする場合は、デバッガーで実行している場合に、例外が発生します。 (この設定はオフにすることができます)。ただし場合、UI スレッドで、クエリを使用すると、し、アクセスできますからコントロール、 `foreach` 1 つのスレッドでそのコードが実行されるため、クエリを列挙するループになります。  
  
## <a name="do-not-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a>ForEach、For および ForAll のイテレーションが必ず並列実行されているとは限らない  
 その個々 の繰り返しに留意することが重要な<xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>、<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>または<xref:System.Linq.ParallelEnumerable.ForAll%2A>月のループが並列で実行する必要はありません。 そのため、イテレーションの並列実行の正確性、または特定の順序でのイテレーションの実行の正確性に依存するコードを記述しないでください。  
  
 たとえば、次のコードはデッドロックが起こる可能性があります。  
  
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
  
 この例では、1 つのイテレーションでイベントを設定し、その他のすべてのイテレーションでイベントを待機します。 待機のイテレーションは、イベント設定のイテレーションが完了するまで完了できません。 ただし、待機のイテレーションによって、並列ループの実行に使用されるすべてのスレッドがブロックされ、イベント設定のイテレーションがまったく実行されなくなる可能性があります。 これにより、イベント設定のイテレーションが実行されず、待機のイテレーションが開始されないままの状態になるデッドロックが発生します。  
  
 具体的には、処理を適切に進めるには、並列ループの特定のイテレーションでそのループの別のイテレーションを待機するのは避ける必要があります。 並列ループで、イテレーションが逆の順序で順次スケジュールされた場合、デッドロックが発生します。  
  
## <a name="see-also"></a>関連項目  
 [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
