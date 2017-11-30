---
title: "方法: 動的パーティションを実装する"
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
helpviewer_keywords: tasks, how to create a dynamic partitioner
ms.assetid: c875ad12-a161-43e6-ad1c-3d6927c536a7
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d1e5dc93997918e0f7da29fa1f94c434a556f19f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-dynamic-partitions"></a>方法: 動的パーティションを実装する
次の例は、カスタムを実装する方法を示しています。<xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType>を動的なパーティション分割を実装し、特定のオーバー ロードから使用できる<xref:System.Threading.Tasks.Parallel.ForEach%2A>と PLINQ の間です。  
  
## <a name="example"></a>例  
 パーティションを呼び出すたびに<xref:System.Collections.IEnumerator.MoveNext%2A>列挙子に対して、列挙子は 1 つのリストの要素を持つパーティションを提供します。 PLINQ の場合と<xref:System.Threading.Tasks.Parallel.ForEach%2A>、パーティションが、<xref:System.Threading.Tasks.Task>インスタンス。 要求は、複数のスレッドで同時に発生している、ため、現在のインデックスへのアクセスが同期されます。  
  
 [!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#04)]
 [!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  
  
 これは、パーティション分割、1 つの要素で構成される各チャンクをチャンクの例です。 を一度に複数の要素を提供するにはロックの競合を減らしでしたして理論的には高速なパフォーマンスを実現します。 ただし、いくつかの時点では、大きな単位必要があります負荷分散のロジックを追加、すべての作業が完了するまでのすべてのスレッドをビジー状態に保つためにします。  
  
## <a name="see-also"></a>関連項目  
 [PLINQ および TPL 用のカスタム パーティショナー](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)  
 [方法: 静的パーティション分割用にパーティショナーを実装する](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
