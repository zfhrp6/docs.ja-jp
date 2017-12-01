---
title: "方法: カスタムの PLINQ 集約関数を記述する"
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
helpviewer_keywords: PLINQ queries, how to create aggregate function
ms.assetid: 5a70dd49-ab2a-4798-b551-196ee7042b1a
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8b098f21e29d0d59cd99ddbb64af6246d9953a3a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-a-custom-plinq-aggregate-function"></a>方法: カスタムの PLINQ 集約関数を記述する
この例を使用する方法を示しています、<xref:System.Linq.ParallelEnumerable.Aggregate%2A>ソース シーケンスに、カスタム集計関数を適用する方法です。  
  
> [!WARNING]
>  この例は、使用方法を示すことを意図したものであるため、同等の順次的な LINQ to Objects クエリほど高速ではない可能性があります。 高速化の詳細については、次を参照してください。 [PLINQ で高速化について](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)です。  
  
## <a name="example"></a>例  
 次の例では、整数のシーケンスの標準偏差を計算します。  
  
 [!code-csharp[PLINQ#31](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#31)]
 [!code-vb[PLINQ#31](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#31)]  
  
 この例では、PLINQ 固有の集計の標準クエリ演算子のオーバー ロードを使用します。 このオーバー ロードは余分な<xref:System.Func%603?displayProperty=nameWithType>3 番目の入力パラメーターとして。 このデリゲートは、集計の結果の最終的な計算が実行する前に、すべてのスレッドからの結果を結合します。 この例では合計が追加のすべてのスレッドからです。  
  
 ラムダ式の本体は、単一の式の戻り値の場合、<xref:System.Func%602?displayProperty=nameWithType>デリゲートは、式の値。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Linq.ParallelEnumerable>  
 [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
