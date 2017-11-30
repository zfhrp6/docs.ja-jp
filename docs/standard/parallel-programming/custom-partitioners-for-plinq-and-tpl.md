---
title: "PLINQ および TPL 用のカスタム パーティショナー"
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
helpviewer_keywords: tasks, partitioners
ms.assetid: 96153688-9a01-47c4-8430-909cee9a2887
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 12d234b86b0067178d54d2fdcb5d37ceaee6109d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="custom-partitioners-for-plinq-and-tpl"></a>PLINQ および TPL 用のカスタム パーティショナー
データ ソースでの操作を並列化の重要な手順のいずれかを*パーティション*ソースを複数のセクションでは複数のスレッドで同時にアクセスできます。 PLINQ およびタスク並列ライブラリ (TPL) は、並列クエリを記述する場合に透過的に機能する既定のパーティションを提供または<xref:System.Threading.Tasks.Parallel.ForEach%2A>ループします。 高度なシナリオは、独自のパーティショナーで接続できます。  
  
## <a name="kinds-of-partitioning"></a>パーティション分割の種類  
 さまざまな方法でデータ ソースのパーティションがあります。 複数のスレッドが複数のサブシーケンスにソースを物理的に分離するのではなく、プロセス、元のソース シーケンスに連携して、最も効率的な方法では、します。 配列、およびその他のインデックス化されたソースなど<xref:System.Collections.IList>コレクションの長さがあらかじめわかっている*範囲パーティション分割*は最も単純な種類のパーティション分割します。 すべてのスレッドでは、ソースの範囲を上書きするか、他のスレッドによって上書きされることがなく処理できるように一意の開始と終了時刻、インデックスを受け取ります。 範囲パーティション分割に関連するオーバーヘッドが初期の作業の範囲を作成します。追加の同期は必要ありませんにします。 そのため、作業負荷が均等に限り、良好なパフォーマンスを実現できます。 範囲パーティション分割の欠点は、1 つのスレッドが早く終了した場合は、他のスレッドの作業を完了を支援ことできませんです。  
  
 リンク リストまたは他のコレクションの長さが不明の場合は、使用することができます*チャンクがパーティション分割*です。 チャンクがパーティション分割のすべてのスレッドまたはタスクを並列ループまたはクエリでいくつかの 1 つのチャンクでソース要素を使用、それらを処理返ってくると、追加の要素を取得します。 パーティショナーは、すべての要素が分散されると、重複がないようにします。 チャンクのサイズがあります。 説明されているパーティショナーなど[する方法: 実装の動的なパーティション](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md)1 つだけの要素が含まれているチャンクを作成します。 チャンクが大きすぎていない限り、この種類のパーティション分割は本質的に負荷分散のスレッドに要素の割り当てがあらかじめ決定されないためです。 ただし、パーティショナーはオーバーヘッドが増加する、同期、スレッドが別のチャンクを取得するたびにします。 このような場合に発生する同期の量は、チャンクのサイズに反比例します。  
  
 一般に、range パーティション分割は高速な場合にのみ、デリゲートの実行時間な小規模から中、ソースが多数の要素、および各パーティションの合計作業時間はほぼ同等です。 チャンクがパーティション分割は、ほとんどの場合、一般に高速ではこのためです。 少数の要素またはデリゲートの実行時間が長いと、ソース、チャンクと範囲パーティション分割のパフォーマンスはほぼ同じです。  
  
 TPL パーティショナーでは、パーティションの数が動的もサポートします。 つまり、たとえばパーティション上の実行時を作成できる場合、<xref:System.Threading.Tasks.Parallel.ForEach%2A>ループは新しいタスクを生成します。 この機能は、ループ自体と共にスケール パーティショナーを使用します。 動的パーティショナーも本質的に負荷分散できます。 カスタム パーティショナーを作成するときにから使用できるようにする動的なパーティショニングをサポートする必要があります、<xref:System.Threading.Tasks.Parallel.ForEach%2A>ループします。  
  
### <a name="configuring-load-balancing-partitioners-for-plinq"></a>負荷分散の PLINQ パーティショナーを構成します。  
 一部のオーバー ロード、<xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType>メソッドでは、配列の場合、パーティショナーを作成できます。 または<xref:System.Collections.IList>ソースと、スレッド間でワークロードのバランスをとるしようとする必要がありますかどうかを指定します。 パーティショナーを負荷分散を構成する場合は、チャンクがパーティション分割を使用すると、し、要素に渡されます小さいチャンク内の各パーティションには要求に応じてします。 これにより、すべてのパーティションがまでループ全体を処理する要素を持つクエリが完了することを確認します。 負荷分散のいずれかのパーティション分割を提供するその他のオーバー ロードを使用できます<xref:System.Collections.IEnumerable>ソース。  
  
 一般に、負荷分散には、要素を要求する比較的多くの場合、パーティショナーからパーティションが必要です。 これに対し、静的パーティション分割を実行するパーティショナーで割り当てることができます要素各パーティショナーを一度にすべての範囲またはチャンクがパーティション分割を使用しています。 負荷分散よりも少ないオーバーヘッドが必要ですが、1 つのスレッドが他よりもはるかに多くの作業終了した場合の実行に長い時間がかかる場合があります。 既定では IList または、配列が渡される PLINQ 常に範囲パーティション分割を使用せず、負荷分散します。 PLINQ の負荷分散を有効にするを使用して、`Partitioner.Create`メソッドを次の例で示すようにします。  
  
 [!code-csharp[TPL_Partitioners#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#02)]
 [!code-vb[TPL_Partitioners#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionsnippets_vb.vb#02)]  
  
 かどうかをロードを使用する、特定のシナリオで分散テストし、代表的な負荷とコンピューターの構成を完了する操作に要する時間を測定する最善の方法です。 たとえば、静的パーティション分割が飛躍的に向上するいくつかのコアだけをあるマルチコア コンピューター上でが速度低下を比較的多くのコアを持つコンピューター上になることがあります。  
  
 次の表の使用可能なオーバー ロード、<xref:System.Collections.Concurrent.Partitioner.Create%2A>メソッドです。 これらのできるパーティショナーが PLINQ でのみ使用するだけではありませんか<xref:System.Threading.Tasks.Task>です。 また、任意のカスタム parallel コンストラクトにも使用できます。  
  
|オーバー ロード|使用して負荷分散|  
|--------------|-------------------------|  
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>|Always|  
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28%60%600%5B%5D%2CSystem.Boolean%29>|ブール型の引数が true として指定されている場合|  
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28System.Collections.Generic.IList%7B%60%600%7D%2CSystem.Boolean%29>|ブール型の引数が true として指定されている場合|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int32%2CSystem.Int32%29>|Never|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int32%2CSystem.Int32%2CSystem.Int32%29>|Never|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int64%2CSystem.Int64%29>|Never|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int64%2CSystem.Int64%2CSystem.Int64%29>|Never|  
  
### <a name="configuring-static-range-partitioners-for-parallelforeach"></a>Parallel.ForEach の静的範囲パーティショナーを構成します。  
 <xref:System.Threading.Tasks.Parallel.For%2A>ループ、ループの本体が代理人としてメソッドを提供します。 デリゲートを呼び出すのコストは、仮想メソッドの呼び出しとほぼ同じです。 一部のシナリオでは、並列ループの本体が小さい各ループ反復でデリゲートの呼び出しのコストが大幅になる可能性があります。 このような状況のいずれかを使用できる、<xref:System.Collections.Concurrent.Partitioner.Create%2A>オーバー ロードを作成する、<xref:System.Collections.Generic.IEnumerable%601>ソース要素の上の範囲パーティションのです。 次に、この範囲のコレクションを渡すことができます、<xref:System.Threading.Tasks.Parallel.ForEach%2A>メソッド本体を持つ、通常から成る`for`ループします。 この方法の利点は、デリゲートを呼び出すコストが、範囲ごとではなく、一度に 1 つの要素 1 回だけ発生することです。 次の例では、基本的なパターンを示します。  
  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 ループ内のすべてのスレッドが受け取る独自<xref:System.Tuple%602>最初と最後の指定されたサブ範囲のインデックス値を格納しています。 内部`for`ループには、`fromInclusive`と`toExclusive`にループ、配列値または<xref:System.Collections.IList>直接です。  
  
 1 つ、<xref:System.Collections.Concurrent.Partitioner.Create%2A>オーバー ロードでは、パーティション、およびパーティションの数のサイズを指定することができます。 このオーバー ロードは、要素ごとの作業が 1 つの要素の 1 つでも仮想メソッドの呼び出しがパフォーマンスに大きな影響を及ぼしますがかなり低いシナリオで使用できます。  
  
## <a name="custom-partitioners"></a>カスタム パーティショナー  
 一部のシナリオで意義またはであっても、独自のパーティショナーを実装する必要があります。 たとえば、既定のクラスの内部構造の知識に基づいてパーティショナー設定できるより効率的に分割するカスタム コレクション クラスがあります。 または、ソース コレクション内の異なる場所にある要素を処理する時間の知識に基づいてさまざまなサイズの範囲パーティションを作成することがあります。  
  
 基本的なカスタム パーティショナーを作成するには、派生クラスを<xref:System.Collections.Concurrent.Partitioner%601?displayProperty=nameWithType>し、次の表に示すように、仮想メソッドをオーバーライドします。  
  
|||  
|-|-|  
|<xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>|このメソッドは、メイン スレッドによって 1 回呼び出され、IList(IEnumerator(TSource)) を返します。 ループまたはクエリでは、各ワーカー スレッドを呼び出すことができます`GetEnumerator`を取得する一覧で、<xref:System.Collections.Generic.IEnumerator%601>個別のパーティション上でします。|  
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|返す`true`を実装する場合<xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>、それ以外の場合、`false`です。|  
|<xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>|場合<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>は`true`、このメソッドは、の代わりに必要に応じて呼び出すことができる<xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>です。|  
  
 結果は並べ替え可能なである必要があります、またはインデックス付きのアクセスを必要な要素から派生し、<xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType>次の表に示すように、仮想メソッドをオーバーライドします。  
  
|||  
|-|-|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetPartitions%2A>|このメソッドは、メイン スレッドによって 1 回呼び出されるを返します、`IList(IEnumerator(TSource))`です。 ループまたはクエリでは、各ワーカー スレッドを呼び出すことができます`GetEnumerator`を取得する一覧で、<xref:System.Collections.Generic.IEnumerator%601>個別のパーティション上でします。|  
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|返す`true`を実装する場合<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetDynamicPartitions%2A>。 それ以外の場合は false。|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetDynamicPartitions%2A>|通常、これだけ呼び出します<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A>です。|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A>|場合<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>は`true`、このメソッドは、の代わりに必要に応じて呼び出すことができる<xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>です。|  
  
 次の表に、追加方法の詳細については、3 種類のパーティショナーを実装の負荷分散、<xref:System.Collections.Concurrent.OrderablePartitioner%601>クラスです。  
  
|メソッドとプロパティ|IList 配列の負荷分散なし/|IList 配列の負荷分散/|IEnumerable|  
|----------------------|-------------------------------------------|----------------------------------------|-----------------|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A>|範囲パーティション分割を使用します。|使用して指定された partitionCount のリスト用に最適化された、チャンクがパーティション分割|静的な数のパーティションを作成することでパーティション分割チャンクを使用します。|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A?displayProperty=nameWithType>|例外のスローをサポートしていません。|使用してリスト用に最適化された、チャンクがパーティション分割および動的なパーティション|パーティションの数が動的に作成して使用してチャンクがパーティション分割します。|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysOrderedInEachPartition%2A>|`true` を返します。|`true` を返します。|`true` を返します。|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysOrderedAcrossPartitions%2A>|`true` を返します。|`false` を返します。|`false` を返します。|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysNormalized%2A>|`true` を返します。|`true` を返します。|`true` を返します。|  
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|`false` を返します。|`true` を返します。|`true` を返します。|  
  
### <a name="dynamic-partitions"></a>動的なパーティション  
 パーティショナーをで使用する場合、<xref:System.Threading.Tasks.Parallel.ForEach%2A>メソッド、する必要がありますを動的なパーティションの数を返します。 つまり、パーティショナーがループの実行中にいつでもは新しいパーティションのオンデマンドの列挙子を指定できる点です。 基本的には、ループは、新しい並列タスクを追加するたびに、そのタスク用の新しいパーティションを要求します。 並べ替え可能であるデータを必要とする場合から派生して<xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType>できるように、各パーティション内の各項目に一意のインデックスが割り当てられます。  
  
 詳細については、および例に、次を参照してください。[する方法: 動的パーティションを実装する](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md)です。  
  
### <a name="contract-for-partitioners"></a>パーティショナーのコントラクト  
 カスタム パーティショナーを実装するときにこれらのガイドラインに従ってを確実に正しい PLINQ 対話と<xref:System.Threading.Tasks.Parallel.ForEach%2A>TPL で。  
  
-   場合<xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>が 0 の引数を指定して呼び出された以下の`partitionsCount`、スロー<xref:System.ArgumentOutOfRangeException>です。 PLINQ および TPL に渡すことはありませんが、`partitionCount`を 0 に等しい、それでもをお勧めする可能性を防ぐ必要があります。  
  
-   <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>および<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A>を常に返します`partitionsCount`パーティションの数。 パーティショナーは、データが不足するいるし、メソッドは、残りのパーティションごとに空の列挙子を返す必要があります、要求されると、同じ数のパーティションを作成することはできません。 PLINQ および TPL の両方がそれ以外の場合、スローされます、<xref:System.InvalidOperationException>です。  
  
-   <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>、 <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A>、 <xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>、および<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A>返りません`null`(`Nothing` Visual Basic で)。 場合は、PLINQ は TPL をスロー/、<xref:System.InvalidOperationException>です。  
  
-   パーティションを返すメソッドでは、完全かつ一意に列挙できるデータ ソースのパーティションが返す常にする必要があります。 ありません、データ ソースまたはスキップした項目の重複するパーティショナーのデザインに必要な場合を除き、します。 この規則に従わない場合の出力順がスクランブルされる可能性があります。  
  
-   出力順がスクランブルないように、次のブール型の getter は、次の値を常に正確に返す必要があります。  
  
    -   `KeysOrderedInEachPartition`: 各パーティションは、増加するキーのインデックスを持つ要素を返します。  
  
    -   `KeysOrderedAcrossPartitions`: すべてのパーティションのパーティション内のキー インデックス、返された*すれば*パーティション内のキーのインデックスよりも高い*すれば*-1 です。  
  
    -   `KeysNormalized`: すべてのキー インデックスは 0 から始まる、置かず単調に増加します。  
  
-   すべてのインデックスは一意である必要があります。 インデックスを重複できない可能性があります。 この規則に従わない場合の出力順がスクランブルされる可能性があります。  
  
-   すべてのインデックスを負にする必要があります。 この規則に従わない場合、PLINQ/TPL は例外をスロー可能性があります。  
  
## <a name="see-also"></a>関連項目  
 [並列プログラミング](../../../docs/standard/parallel-programming/index.md)  
 [方法: 動的パーティションを実装する](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md)  
 [方法: 静的パーティション分割用にパーティショナーを実装する](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
