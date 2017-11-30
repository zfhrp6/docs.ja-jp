---
title: "PLINQ のマージ オプション"
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
helpviewer_keywords: PLINQ queries, merge options
ms.assetid: e8f7be3b-88de-4f33-ab14-dc008e76c1ba
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e9bf586c1805fc5b5f1cc5f96f4e6b08d80c199a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="merge-options-in-plinq"></a>PLINQ のマージ オプション
クエリが実行するときに並列、PLINQ パーティションとしてソース シーケンス複数のスレッドで作業できるさまざまな部分に同時に、通常別々 のスレッドでできるようにします。 結果を 1 つのスレッドで使用する場合など、 `foreach` (`For Each`で[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) ループ、そのすべてのスレッドからの結果を 1 つのシーケンスにマージする必要があります。 PLINQ を実行する結合の種類は、クエリに存在する演算子によって異なります。 たとえば、結果に新しい注文を課す演算子では、すべてのスレッドからすべての要素がバッファーに格納する必要があります。 (これはでも、アプリケーションのユーザーの) かかるスレッドの観点から、顕著な期間の最初の結果を生成する前に完全にバッファー内のクエリ可能性があります実行されます。 その他の演算子では、既定は部分的にバッファーに格納します。これらは、バッチ処理の結果をもたらします。 1 つの演算子<xref:System.Linq.ParallelEnumerable.ForAll%2A>が既定ではバッファーされていません。 として生成されるすべての要素のすべてのスレッドからすぐにします。  
  
 使用して、<xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A>メソッドを次の例で示すように提供できるヒント PLINQ を実行する結合の種類を示すです。  
  
 [!code-csharp[PLINQ#26](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#26)]
 [!code-vb[PLINQ#26](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#26)]  
  
 完了の例では、次を参照してください。[する方法: PLINQ のマージ オプションの指定](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)です。  
  
 特定のクエリで要求されたオプションがサポートされていない場合、オプションだけ無視されます。 ほとんどの場合、PLINQ クエリのマージ オプションを指定するはありません。 ただし、場合によっては、テストと、既定以外のモードでクエリの最適な実行測定によって検索可能性があります。 このオプションの一般的な用途は、応答性の高いユーザー インターフェイスを提供するためにその結果をストリーミングにチャンク結合演算子を強制的にです。  
  
## <a name="parallelmergeoptions"></a>ParallelMergeOptions  
 <xref:System.Linq.ParallelMergeOptions>列挙には、次のオプション指定する、図形はサポートされているクエリ、結果が 1 つのスレッドで使用される場合に、クエリの最終的な出力を生成する方法にはが含まれています。  
  
-   `Not Buffered`  
  
     <xref:System.Linq.ParallelMergeOptions.NotBuffered>オプションの設定により、生成されるとすぐに、各スレッドから返される各処理された要素。 この動作は、"streaming"出力に似ています。 場合、<xref:System.Linq.ParallelEnumerable.AsOrdered%2A>演算子は、クエリ内に存在`NotBuffered`ソース要素の順序が保持されます。 `NotBuffered`利用可能なとすぐに結果を生成を開始するには、および、結果がある可能性がありますすべてを生成するために時間の合計は、他のマージ オプションのいずれかを使用してより長くします。  
  
-   `Auto Buffered`  
  
     <xref:System.Linq.ParallelMergeOptions.AutoBuffered>オプションの設定により、バッファーに要素を収集し、バッファーの内容がかかるスレッドに一度にすべてを定期的に生成するクエリをします。 これは「ストリーミング」の動作を使用する代わりに「チャンク」でソース データを応答に似ています`NotBuffered`です。 `AutoBuffered`も長い時間がかかる`NotBuffered`がかかるスレッドでの最初の要素を使用できるようにします。 バッファーのサイズ、および正確な生成動作は構成できないと、クエリに関連するさまざまな要因によって異なる場合があります。  
  
-   `FullyBuffered`  
  
     <xref:System.Linq.ParallelMergeOptions.FullyBuffered>オプションの設定により、クエリの出力、全体に任意の要素が生成する前にバッファーに格納します。 このオプションを使用する場合、長い時間がかかる最初の要素がかかるスレッドで使用できますが、完全な結果を生成する可能性がある前に、他のオプションを使用して、高速です。  
  
## <a name="query-operators-that-support-merge-options"></a>マージ オプションをサポートするクエリ演算子  
 次の表では、指定された制限に従い、すべてのマージ オプション モードをサポートする演算子が一覧表示します。  
  
|演算子|制約|  
|--------------|------------------|  
|<xref:System.Linq.ParallelEnumerable.AsEnumerable%2A>|なし|  
|<xref:System.Linq.ParallelEnumerable.Cast%2A>|なし|  
|<xref:System.Linq.ParallelEnumerable.Concat%2A>|配列またはリスト ソースがのみ非順次のクエリです。|  
|<xref:System.Linq.ParallelEnumerable.DefaultIfEmpty%2A>|なし|  
|<xref:System.Linq.ParallelEnumerable.OfType%2A>|なし|  
|<xref:System.Linq.ParallelEnumerable.Reverse%2A>|配列またはリスト ソースがのみ非順次のクエリです。|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>|なし|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>|なし|  
|<xref:System.Linq.ParallelEnumerable.Skip%2A>|なし|  
|<xref:System.Linq.ParallelEnumerable.Take%2A>|なし|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>|なし|  
  
 他のすべての PLINQ クエリ演算子は、ユーザー指定のマージ オプションを無視する場合があります。 一部のクエリ演算子、たとえば、<xref:System.Linq.ParallelEnumerable.Reverse%2A>と<xref:System.Linq.ParallelEnumerable.OrderBy%2A>をすべて生成および順序を変更するまで、すべての要素を生成できません。 したがって、<xref:System.Linq.ParallelMergeOptions>などの演算子が含まれているクエリで使用<xref:System.Linq.ParallelEnumerable.Reverse%2A>マージの動作は適用されませんまでクエリでその演算子には、その結果によって生成された後にします。  
  
 マージ オプションを処理するいくつかの演算子の機能は、ソース シーケンスの種類によって異なります。 かどうかと、<xref:System.Linq.ParallelEnumerable.AsOrdered%2A>演算子がクエリ内で既に使用されています。 <xref:System.Linq.ParallelEnumerable.ForAll%2A>常に<xref:System.Linq.ParallelMergeOptions.NotBuffered>; すぐにその要素になります。 <xref:System.Linq.ParallelEnumerable.OrderBy%2A>常に<xref:System.Linq.ParallelMergeOptions.FullyBuffered>; として生成される前に、リスト全体を並べ替えるにする必要があります。  
  
## <a name="see-also"></a>関連項目  
 [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 [方法: PLINQ のマージ オプションを指定する](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)
