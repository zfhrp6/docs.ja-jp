---
title: "PLINQ での高速化について"
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
helpviewer_keywords: PLINQ queries, performance tuning
ms.assetid: 53706c7e-397d-467a-98cd-c0d1fd63ba5e
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c3373cb6a2c535bd7d42eb062e1f9727952f7cfb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="understanding-speedup-in-plinq"></a>PLINQ での高速化について
PLINQ の主な目的では、実行速度を高めるの LINQ to Objects クエリ マルチコア コンピューターで並列クエリ デリゲートを実行することによってです。 PLINQ は、ソース コレクション内の各要素の処理が独立しており、個別のデリゲートの間で関係する共有状態がない場合に発揮します。 このような操作は LINQ to Objects および PLINQ では一般的とも呼ばれます"*適切な並列*"であることから簡単に複数のスレッドでのスケジュール設定します。 ただし、すべてのクエリのみで構成する適切な並列操作です。ほとんどの場合、クエリはいずれかを並行化できない、または並列実行速度が低下するいくつかの演算子ではします。 クエリを完全に適切な並列でも PLINQ 必要があります、データ ソースをパーティション分割と、スレッドに作業をスケジュール通常、クエリの完了時に結果をマージします。 これらすべての操作を並列化以外の計算コストを追加します。これらのコストを並列化を追加すると呼びます*オーバーヘッド*です。 PLINQ クエリの最適なパフォーマンスを得るには、目標は、適切な並列されている部分を最大化し、オーバーヘッドが必要な部分を最小限に抑えるです。 この記事では、正しい結果を生成できる限り効率的な PLINQ クエリを記述するうえで役立つ情報を提供します。  
  
## <a name="factors-that-impact-plinq-query-performance"></a>PLINQ クエリのパフォーマンスに影響する要因  
 次のセクションでは、並列クエリ パフォーマンスに影響する最も重要な要因のいくつか示します。 これらは、一般的なないステートメントを単独で常にクエリのパフォーマンスを予測するだけで十分です。 いつものように、コンピューター上の特定のクエリの代表的な構成と読み込みの範囲と実際のパフォーマンスを測定する重要なです。  
  
1.  全体的な作業のコストを計算します。  
  
     高速化を行うには、PLINQ クエリは、必要な適切な並列処理のオーバーヘッドを相殺をする必要があります。 作業は、ソース コレクション内の要素の数を掛けた値の各デリゲートの計算コストとして表現できます。 想定されるので、操作を並列化できますより計算負荷の高いことが、大きい高速化の機会です。 たとえば、関数が 1 ミリ秒を実行する場合、1000 個の要素になります、その操作を実行する 1 秒 4 つのコアを使用しているコンピューター上で並列クエリは順次クエリは 250 ミリ秒しかにかかる場合があります。 これには、750 ミリ秒の高速化が生成されます。 関数は、各要素に対して実行する 1 秒を必要な場合、高速化になります 750 秒です。 デリゲートが非常に多くの場合は、PLINQ はソース コレクション内のいくつかのアイテムのみが大幅に高速化を提供します。 逆に、単純なデリゲートで小さなソース コレクションは一般的に PLINQ の適切な候補です。  
  
     次の例では、簡易問い合わせと、その関数選択 にはに、多く作業にはが含まれていると仮定した場合、PLINQ で有力候補では可能性があります。 queryB は、Select ステートメントに十分な処理がないと、並列処理のオーバーヘッドは、高速化のほとんどまたはすべてをオフセットがあるために、適切な候補ではありません。  
  
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
  
2.  システム (並列処理の次数) 上の論理コアの数。  
  
     このポイントは、前のセクションに、明確な推論は、適切な並列クエリを上で実行高速マシンより多くのコアと同時実行性のスレッド間で作業を分けることがあるためです。 高速化の全体量は、クエリの全体的な作業の割合が並列化に依存します。 ただしと想定しないでとして 2 回、すべてのクエリを実行は、4 コアのコンピューターと 8 コアのコンピューターに高速です。 最適なパフォーマンスのクエリをチューニングするときは、さまざまなコア数のコンピューターで実際の結果を測定する必要があります。 このポイントが 1 のポイントに関連する: 大規模なデータセットがより多くのコンピューティング リソースを活用するために必要です。  
  
3.  数と操作の種類。  
  
     PLINQ では、ソース シーケンス内の要素の順序を維持するために必要な場合に、AsOrdered 演算子を提供します。 順序付けに関連するコストが、このコストは通常中程度。 同様に、GroupBy および結合操作には、オーバーヘッドが発生します。 PLINQ は、任意の順序でソース コレクション内の要素を処理し、準備が完了するとすぐに次の演算子に渡すことができる場合に発揮します。 詳細については、「[Order Preservation in PLINQ (PLINQ における順序維持)](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md)」を参照してください。  
  
4.  クエリの実行の形式。  
  
     ToArray または ToList を呼び出すことによって、クエリの結果を格納する場合は、1 つのデータ構造にすべての並列スレッドの結果をマージする必要があります。 これには、ロックベースの計算コストが含まれます。 同様に、foreach (Visual Basic では各) For ループを使用して、結果を反復処理する場合、ワーカー スレッドからの結果を列挙子のスレッドにシリアル化される必要があります。 各スレッドの結果に基づいてアクションを実行する場合は、複数のスレッドでこの作業を実行する ForAll メソッドを使用することができます。  
  
5.  マージ オプションの種類。  
  
     PLINQ は、いずれかの出力をバッファリングして作成のチャンクまたは一度に結果セット全体が作成された後、または else 個々 の結果をストリームが生成されるように構成できます。 前者の場合は、全体の実行時間を短縮および後者結果の生成される要素間の遅延が減少します。  マージ オプションが常に主要な影響のない全体的なクエリ パフォーマンス、中に影響を与えること見かけ上のパフォーマンス、ユーザーはどのくらいの時間を制御するための結果を表示するまで待機する必要があります。 詳細については、「[Merge Options in PLINQ (PLINQ のマージ オプション)](../../../docs/standard/parallel-programming/merge-options-in-plinq.md)」を参照してください。  
  
6.  パーティション分割の種類。  
  
     場合によっては、インデックス可能なソース コレクションに対する PLINQ クエリが不均衡の作業負荷にあります。 この場合は、カスタム パーティショナーを作成することで、クエリのパフォーマンスを向上させることができます。 詳細については、「[Custom Partitioners for PLINQ and TPL (PLINQ および TPL 用のカスタム パーティショナー)](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)」を参照してください。  
  
## <a name="when-plinq-chooses-sequential-mode"></a>PLINQ が順次モードを選択すると  
 PLINQ は常に、以上の速度でクエリを順次実行とクエリの実行を試みます。 PLINQ は負荷の大きい計算方法を参照できませんが高価なユーザー デリゲートが、または大きさ入力ソースが、特定のクエリ「の図形です」を探しては 具体的には、クエリ演算子または並列モードで実行速度が低下するクエリが通常発生演算子の組み合わせの検索します。 このような図形が検出されると、既定では、PLINQ は、シーケンシャル モードに戻ります。  
  
 ただし、特定のクエリのパフォーマンスを測定した後には、実際に実行される高速並列モードでを判断可能性があります。 このような場合に使用することができます、<xref:System.Linq.ParallelExecutionMode.ForceParallelism?displayProperty=nameWithType>フラグを使用して、<xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A>クエリを並列化するために PLINQ に指示するメソッド。 詳細については、「[How to: Specify the Execution Mode in PLINQ (方法: PLINQ の実行モードを指定する)](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md)」を参照してください。  
  
 次の一覧には、シーケンシャル モードで実行されます。 既定で PLINQ クエリの図形がについて説明します。  
  
-   ここで、インデックス付きの SelectMany にインデックス付けを選択を含むクエリまたは順序またはフィルター演算子が削除されたか、元のインデックスを再配置した後に ElementAt 句を指定します。  
  
-   Take、TakeWhile、スキップ、SkipWhile 演算子が含まれており、ここで、ソース シーケンス内のインデックスは順番がない、元のクエリ。  
  
-   またはを含む Zip SequenceEquals、ない場合は、最初の並べ替えられたインデックスのデータ ソースのいずれかが、その他のデータ ソース [indexable] クエリ (つまり、配列または IList(T)) です。  
  
-   インデックス可能なデータ ソースに適用されている場合を除き、Concat を含むクエリ。  
  
-   含むクエリは、インデックス可能データ ソースに適用される場合を除き、反転します。  
  
## <a name="see-also"></a>関連項目  
 [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
