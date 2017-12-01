---
title: "方法: 単純な PLINQ クエリを作成して実行する"
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
helpviewer_keywords: PLINQ queries, how to create
ms.assetid: 983b4213-bddd-4a44-9262-cbe59186df4c
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a99eedc05bbf8d4dcd58e46b484bd57c29f70886
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-and-execute-a-simple-plinq-query"></a>方法: 単純な PLINQ クエリを作成して実行する
次の例に、ソース シーケンスに対する <xref:System.Linq.ParallelEnumerable.AsParallel%2A> 拡張メソッドを使用して単純な並列 LINQ クエリを作成し、<xref:System.Linq.ParallelEnumerable.ForAll%2A> メソッドを使用して、そのクエリを実行する方法を示します。  
  
> [!NOTE]
>  ここでは、ラムダ式を使用して PLINQ でデリゲートを定義します。 C# または Visual Basic のラムダ式についての情報が必要な場合は、「[Lambda Expressions in PLINQ and TPL (PLINQ および TPL のラムダ式)](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)」を参照してください。  
  
## <a name="example"></a>例  
 [!code-csharp[PLINQ#11](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/create1.cs#11)]
 [!code-vb[PLINQ#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/create1.vb#11)]  
  
 この例で示しているのは、結果シーケンスの順序付けが重要ではない場合に、並列 LINQ クエリを作成して実行する基本的なパターンです。通常、順序なしのクエリは、順序ありのクエリより高速になります。 このクエリはソースを、複数のスレッドで非同期的に実行した複数のタスクにパーティション分割します。 各タスクが完了する順序は、その特定のパーティションに含まれる要素を処理するために必要な作業量だけでなく、オペレーティング システムが各スレッドをどのようにスケジュールするかといった外部要因にも依存します。 この例は、使用方法を示すことを意図したものであるため、同等の順次的な LINQ to Objects クエリほど高速ではない可能性があります。 高速化の詳細については、次を参照してください。 [PLINQ で高速化について](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)です。 クエリ内の要素の順序を維持する方法の詳細については、次を参照してください。[する方法: PLINQ クエリの順序付けコントロール](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md)です。  
  
## <a name="see-also"></a>関連項目  
 [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
