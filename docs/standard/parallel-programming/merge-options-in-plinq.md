---
title: "Merge Options in PLINQ | Microsoft Docs"
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
  - "PLINQ queries, merge options"
ms.assetid: e8f7be3b-88de-4f33-ab14-dc008e76c1ba
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# Merge Options in PLINQ
クエリが並列実行される場合、PLINQ は、複数のスレッドが別の部分 \(通常は別のスレッド\) で同時に動作できるよう、ソース シーケンスをパーティション分割します。  結果が、`foreach` \([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] の `For Each`\) ループなど、1 つのスレッドで消費される場合は、すべてのスレッドからの結果を 1 つのシーケンスに再度マージする必要があります。  PLINQ によって実行されるマージの種類は、クエリに存在する演算子に依存します。  たとえば、結果に対して新しい順序を課す演算子は、すべてのスレッドからのすべての要素をバッファーに格納する必要があります。  \(アプリケーション ユーザーの観点でもある\) consumer スレッドの観点からは、完全にバッファーに格納されたクエリは、最初の結果を生成するまでに長時間にわたって実行される可能性があります。  他の演算子は、既定では部分的にバッファーに格納され、結果はバッチで生成されます。  <xref:System.Linq.ParallelEnumerable.ForAll%2A> という演算子は、既定ではバッファーに格納されません。  すべてのスレッドからの全要素を直ちに生成します。  
  
 次の例に示すように、<xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A> メソッドを使用して、実行するマージの種類を示すヒントを PLINQ に提供できます。  
  
 [!code-csharp[PLINQ#26](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#26)]
 [!code-vb[PLINQ#26](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#26)]  
  
 コード例全体については、「[How to: Specify Merge Options in PLINQ](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)」を参照してください。  
  
 特定のクエリが要求されたオプションをサポートできない場合は、そのオプションは無視されます。  ほとんどの場合は、PLINQ クエリに対してマージ オプションを指定する必要はありません。  ただし、場合によっては、テストと測定によって、既定以外のモードで最も効率よくクエリが実行されることが判明することもあります。  このオプションの一般的な用途は、チャンク マージ演算子を強制的に処理してその結果をストリーミングし、より応答性の高いユーザー インターフェイスを提供することです。  
  
## ParallelMergeOptions  
 <xref:System.Linq.ParallelMergeOptions> 列挙型には、サポートされるクエリの形態について、1 つのスレッドで結果が消費されたときにクエリの最終的な出力がどのように生成されるかを指定する、次のオプションが含まれます。  
  
-   `Not Buffered`  
  
     <xref:System.Linq.ParallelMergeOptions> オプションを使用すると、処理された各要素が生成されると同時に各スレッドから返されます。  この動作は出力の "ストリーミング" と同じです。  クエリに <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> 演算子がある場合、`NotBuffered` はソース要素の順番を保持します。  `NotBuffered` は、結果が使用可能になると同時に結果の生成を開始しますが、すべての結果が生成されるまでの合計時間は、他のマージ操作にかかる合計時間よりも長くなることがあります。  
  
-   `Auto Buffered`  
  
     <xref:System.Linq.ParallelMergeOptions> オプションを使用すると、要素を収集してバッファーに格納し、その後定期的に consumer スレッドにバッファーの内容を一度に生成します。  これは、`NotBuffered` の "ストリーミング" 動作を使用する代わりに、ソース データを "チャンク" として生成するのと同じです。  `AutoBuffered` では、consumer スレッドで最初の要素を使用できるようになるまで、`NotBuffered` よりも長い時間がかかることがあります。  バッファーのサイズと正確な生成動作を構成できないため、クエリに関連するさまざまな要因に左右されることがあります。  
  
-   `FullyBuffered`  
  
     <xref:System.Linq.ParallelMergeOptions> オプションを使用すると、要素が生成される前に、クエリ全体の出力がバッファーに格納されます。  このオプションを使用すると、consumer スレッドで最初の要素が使用できるようになるまで時間がかかることがありますが、完全な結果は、他のオプションを使用するよりも短時間で生成されます。  
  
## マージ オプションをサポートするクエリ演算子  
 次の表に、すべてのマージ オプションをサポートする演算子を示します。ただし、ここに示す制約があります。  
  
|演算子|制約|  
|---------|--------|  
|<xref:System.Linq.ParallelEnumerable.AsEnumerable%2A>|なし。|  
|<xref:System.Linq.ParallelEnumerable.Cast%2A>|なし。|  
|<xref:System.Linq.ParallelEnumerable.Concat%2A>|配列ソースまたはリスト ソースしか持たない、順序なしのクエリ|  
|<xref:System.Linq.ParallelEnumerable.DefaultIfEmpty%2A>|なし。|  
|<xref:System.Linq.ParallelEnumerable.OfType%2A>|なし。|  
|<xref:System.Linq.ParallelEnumerable.Reverse%2A>|配列ソースまたはリスト ソースしか持たない、順序なしのクエリ|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>|なし。|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>|なし。|  
|<xref:System.Linq.ParallelEnumerable.Skip%2A>|なし。|  
|<xref:System.Linq.ParallelEnumerable.Take%2A>|なし。|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>|なし。|  
  
 その他すべての PLINQ クエリ演算子は、ユーザー指定のマージ オプションを無視することがあります。  <xref:System.Linq.ParallelEnumerable.Reverse%2A> や <xref:System.Linq.ParallelEnumerable.OrderBy%2A> のようなクエリ演算子は、すべての要素が生成され、並べ替えられるまでは、どの要素も生成できません。  したがって、<xref:System.Linq.ParallelEnumerable.Reverse%2A> などの演算子も含むクエリで <xref:System.Linq.ParallelMergeOptions> が使用される場合、マージ動作は、その演算子が結果を生成するまで、クエリには適用されません。  
  
 マージ オプションを処理する一部の演算子の機能は、ソース シーケンスの種類と、クエリの前半で <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> 演算子が使用されたかどうかによって異なります。  <xref:System.Linq.ParallelEnumerable.ForAll%2A> は常に <xref:System.Linq.ParallelMergeOptions> であり、要素を即座に生成します。  <xref:System.Linq.ParallelEnumerable.OrderBy%2A> は常に <xref:System.Linq.ParallelMergeOptions> です。したがって、要素を生成する前にリスト全体を並べ替える必要があります。  
  
## 参照  
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)   
 [How to: Specify Merge Options in PLINQ](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)