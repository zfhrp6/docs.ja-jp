---
title: "方法: 静的パーティション分割用にパーティショナーを実装する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: tasks, how to create a static partitioner
ms.assetid: f4410508-cac6-4ba7-bef1-c5e68b2794f3
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b28ff0bb8436fefc4956918889435e258ae98b12
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-implement-a-partitioner-for-static-partitioning"></a>方法: 静的パーティション分割用にパーティショナーを実装する
次の例は、plinq が静的パーティション分割を実行する場合は、単純なカスタム パーティショナーを実装する方法を示しています。 パーティショナーは動的なパーティションがサポートされていませんはから利用できる<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>です。 このパーティショナーは、データ ソースの各要素が大量の処理時間が必要です、既定の範囲パーティショナー経由で速度が向上する可能性があります。  
  
## <a name="example"></a>例  
 [!code-csharp[TPL_Partitioners#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#05)]  
  
 この例では、パーティションは処理時間の各要素を直線的に増加するという前提に基づいています。 この方法で処理時間を予測するが困難な現実世界があります。 静的パーティショナーで特定のデータ ソースを使用している場合、ソースの数式でパーティション分割を最適化、負荷分散のロジックを追加したり、使用に示すようにパーティション分割手法チャンク[する方法: 動的パーティションを実装します。](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).  
  
## <a name="see-also"></a>関連項目  
 [PLINQ および TPL 用のカスタム パーティショナー](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
