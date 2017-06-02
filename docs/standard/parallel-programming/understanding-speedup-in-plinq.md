---
title: "Understanding Speedup in PLINQ | Microsoft Docs"
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
  - "PLINQ queries, performance tuning"
ms.assetid: 53706c7e-397d-467a-98cd-c0d1fd63ba5e
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# Understanding Speedup in PLINQ
PLINQ の主な目的は、マルチコア コンピューターでクエリのデリゲートを並列で実行することにより、LINQ to Objects クエリの実行を高速化することです。  PLINQ は、ソース コレクションの各要素の処理が独立し、個別のデリゲート間に共有状態がない場合に、最大のパフォーマンスを発揮します。  このような操作は、LINQ to Objects および PLINQ では一般的であり、複数のスレッドでのスケジュール設定が容易であることから、"*適切な並列*" とも言われます。  しかし、すべてのクエリが適切な並列操作だけで構成されるわけではありません。ほとんどの場合、クエリには、並列化できない演算子や、並列実行では速度が低下する演算子がいくつか含まれています。  また、完全に適切な並列クエリでも、PLINQ ではデータ ソースをパーティション分割して作業をスレッド上でスケジュールし、通常はクエリが完了したときに結果をマージする必要があります。  これらすべての操作により、並列化の計算コストが増えます。このような並列化を加えることによるコストを、*オーバーヘッド*といいます。  PLINQ クエリで最適なパフォーマンスを実現するには、適切な並列の部分を最大化し、オーバーヘッドを要する部分を最小化することが目標です。  ここでは、できる限り効率的で、正しい結果を生成する PLINQ クエリを記述するのに役立つ情報を示します。  
  
## PLINQ クエリのパフォーマンスに影響を与える要因  
 ここでは、並列クエリのパフォーマンスに影響を与える最も重要な要因をいくつか示します。  これらは一般的な説明であり、これだけではすべてのケースのクエリのパフォーマンスを予測するには不十分です。  当然ながら、一連の代表的な構成および負荷を使用して、コンピューターで特定のクエリの実際のパフォーマンスを計測することが重要です。  
  
1.  作業全体の計算コスト。  
  
     高速化を実現するには、PLINQ クエリの適切な並列処理が、オーバーヘッドを相殺するのに十分な量である必要があります。  この量は、各デリゲートの計算コストを、ソース コレクション内の要素の数で乗算して表すことができます。  操作を並列化できると仮定した場合、その操作の計算コストが大きいほど、高速化の可能性は高くなります。  たとえば、関数の実行に 1 ミリ秒かかる場合、1,000 個の要素に対する順次クエリを実行するには 1 秒かかりますが、4 つのコアを備えるコンピューター上で並列クエリを実行した場合は 250 ミリ秒しかかかりません。  これにより、750 ミリ秒の高速化が実現します。  関数を各要素に対して実行するのに 1 秒かかる場合は、750 秒の高速化が実現します。  デリゲートがきわめて高コストである場合、PLINQ は、項目が数個しかないソース コレクションで大幅な高速化を実現することがあります。  逆に、デリゲートが低コストである小さなソース コレクションは、通常、PLINQ にふさわしい候補ではありません。  
  
     次の例では、queryA が PLINQ にふさわしい候補、Select 関数に大量の処理が含まれているからです。queryB は、Select ステートメントに十分な処理が、並列化のオーバーヘッドによって高速化ほとんどまたはすべてが相殺されるため、ふさわしい候補ではありません。  
  
    ```vb  
    Dim queryA = From num In numberList.AsParallel()  
                 Select ExpensiveFunction(num); 'good for PLINQ  
  
    Dim queryB = From num In numberList.AsParallel()  
                 Where num Mod 2 > 0  
                 Select num; 'not as good for PLINQ  
    ```  
  
    ```csharp  
    var queryA = from num in numberList.AsParallel()  
                 select ExpensiveFunction(num); //good for PLINQ  
  
    var queryB = from num in numberList.AsParallel()  
                 where num % 2 > 0  
                 select num; //not as good for PLINQ  
  
    ```  
  
2.  システムの論理コアの数 \(並列化の程度\)。  
  
     このポイントは、前のセクションの当然の帰結です。適切な並列クエリは、マシンのコア数が多いほど高速に実行されます。これは、より多くの同時スレッド間で処理を分割できるからです。  高速化の総量は、クエリの処理全体の何パーセントが並列化可能であるかによって異なります。  ただし、すべてのクエリが、8 コアのコンピューターでは 4 コアのコンピューターの 2 倍の速さで実行されるとは考えないでください。  最適なパフォーマンスを得るためにクエリを調整するときは、さまざまなコア数のコンピューターで実際の結果を計測することが重要です。  このポイントは 1 番目のポイントに関連しています。より多くのコンピューティング リソースを利用するには、より大きなデータセットが必要です。  
  
3.  操作の数と種類。  
  
     PLINQ には、ソース シーケンス内の要素の順序を維持する必要がある状況に備えて、AsOrdered 演算子が用意されています。  順序操作にはコストがかかりますが、このコストは通常はそれほど大きくありません。  同様に、GroupBy 操作と Join 操作でもオーバーヘッドが生じます。  PLINQ は、ソース コレクション内の要素を任意の順序で処理でき、それらの要素を準備完了と同時に次の演算子に渡すことができる場合に、最大のパフォーマンスを発揮します。  詳細については、「[Order Preservation in PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md)」を参照してください。  
  
4.  クエリ実行の形式。  
  
     ToArray または ToList を呼び出してクエリの結果を格納する場合、すべての並列スレッドの結果を単一のデータ構造にマージする必要があります。  この場合、計算コストが必ず生じます。  同様に、foreach \(Visual Basic では For Each\) ループを使用して結果を反復処理する場合、ワーカー スレッドの結果を列挙子スレッドにシリアル化する必要があります。  しかし、各スレッドの結果に基づいて何らかのアクションを実行するだけであれば、ForAll メソッドを使用して、この処理を複数のスレッドで実行できます。  
  
5.  マージ オプションの種類。  
  
     PLINQ は、出力をバッファーに格納し、それをチャンク単位で生成するか、結果セット全体が生成された後で一度に生成するように構成するか、または個別の結果を生成時にストリーミングするように構成できます。  前者の場合は、全体的な実行時間が減少し、後者の場合は、生成される要素間の遅延が減少します。マージ オプションは、クエリのパフォーマンス全体に大きな影響を与えるとは限りませんが、ユーザーが結果を目にするまでの時間を制御するため、知覚されるパフォーマンスに影響を与えることがあります。  詳細については、「[Merge Options in PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md)」を参照してください。  
  
6.  パーティション分割の種類。  
  
     場合によっては、インデックス可能なソース コレクションに対する PLINQ クエリで、作業負荷のバランスが崩れることがあります。  この場合、カスタム パーティショナーを作成することにより、クエリのパフォーマンスを改善できることがあります。  詳細については、「[Custom Partitioners for PLINQ and TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)」を参照してください。  
  
## PLINQ が順次モードを選択するケース  
 PLINQ は、少なくとも順次実行した場合と同じ速さでクエリを実行しようと常に試みます。  PLINQ は、ユーザー デリゲートの計算コストの大きさや、入力ソースの大きさは確認しませんが、クエリの特定の "形態"は確認します。具体的には、クエリの並列モードでの実行を低速化させる原因となるクエリ演算子または演算子の組み合わせを検索します。  そのような形態を見つけた場合、PLINQ は、既定で順次モードに戻ります。  
  
 しかし、特定のクエリのパフォーマンスを計測した後で、実際には並列モードのほうが高速に実行されることがわかる場合があります。  そのような場合、<xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A?displayProperty=fullName> メソッドを通じて <xref:System.Linq.ParallelExecutionMode> フラグを使用して、クエリを並列化するように PLINQ に指示できます。  詳細については、「[How to: Specify the Execution Mode in PLINQ](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md)」を参照してください。  
  
 PLINQ が既定で順次モードで実行するクエリの形態は次のとおりです。  
  
-   元のインデックスを削除または再配列した順序設定またはフィルター処理の演算子の後に、Select 句、インデックス付きの Where 句、インデックス付きの SelectMany 句、または ElementAt 句を含むクエリ。  
  
-   Take 演算子、TakeWhile 演算子、Skip 演算子、または SkipWhile 演算子を含み、ソース シーケンスのインデックスが元の順序ではないクエリ。  
  
-   データ ソースの 1 つがに順序付けられたインデックスがあると、Zip または SequenceEquals を含むクエリは他のデータ ソースがです \(つまり配列または IList \(T\)\)。  
  
-   Concat を含むクエリ。ただし、Concat がインデックス可能なデータ ソースに適用されている場合を除きます。  
  
-   Reverse を含むクエリ。ただし、Reverse がインデックス可能なデータ ソースに適用されている場合を除きます。  
  
## 参照  
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)