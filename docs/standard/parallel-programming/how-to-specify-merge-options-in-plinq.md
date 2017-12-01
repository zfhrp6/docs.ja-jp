---
title: "方法: PLINQ のマージ オプションを指定する"
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
helpviewer_keywords: PLINQ queries, how to use merge options
ms.assetid: 0f33b527-e91a-4550-a39a-e63e396fd831
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ec601e8bbefd31650fb91c438b032942cfc93101
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-merge-options-in-plinq"></a>方法: PLINQ のマージ オプションを指定する
この例では、PLINQ クエリのすべての後続演算子を適用するマージ オプションを指定する方法を示します。 マージ オプションを明示的に設定する必要はありませんが、パフォーマンスが向上する可能性があります。 マージ オプションの詳細については、次を参照してください。 [PLINQ のマージ オプション](../../../docs/standard/parallel-programming/merge-options-in-plinq.md)です。  
  
> [!WARNING]
>  この例は、使用方法を示すことを意図したものであるため、同等の順次的な LINQ to Objects クエリほど高速ではない可能性があります。 高速化の詳細については、次を参照してください。 [PLINQ で高速化について](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)です。  
  
## <a name="example"></a>例  
 次の例では、順序なしのソースがあり、すべての要素に高価な関数を適用する基本的なシナリオでのマージ オプションの動作を示します。  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 場合で、<xref:System.Linq.ParallelMergeOptions.AutoBuffered>オプションが前に、最初の要素が生成されるときに望ましくない待機時間を生じます、再試行してください、<xref:System.Linq.ParallelMergeOptions.NotBuffered>迅速かつよりスムーズに結果の要素を生成するにはオプションです。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Linq.ParallelMergeOptions>  
 [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
