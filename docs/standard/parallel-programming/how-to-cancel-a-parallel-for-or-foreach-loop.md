---
title: "方法: Parallel.For または ForEach ループを取り消す"
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
helpviewer_keywords:
- parallel foreach loop, how to cancel
- parallel for loops, how to cancel
ms.assetid: 9d19b591-ea95-4418-8ea7-b6266af9905b
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3f82c5758e02b4beebf035fe8f43f856447855a3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a>方法: Parallel.For または ForEach ループを取り消す
<xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>と<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>メソッドは、キャンセル トークンを使用して取り消しをサポートします。 取り消し処理の詳細については一般を参照してください[キャンセル](../../../docs/standard/threading/cancellation-in-managed-threads.md)です。 並列ループで指定する、<xref:System.Threading.CancellationToken>内のメソッドに、<xref:System.Threading.Tasks.ParallelOptions>パラメーター try catch ブロックで並列呼び出しを囲みます。  
  
## <a name="example"></a>例  
 次の例への呼び出しを取り消す方法を示しています。<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>です。 同じアプローチを適用することができます、<xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>呼び出します。  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 取り消しを通知するトークンが同じ場合はトークンで指定されている、<xref:System.Threading.Tasks.ParallelOptions>インスタンス、並列ループは、1 つをスローし、<xref:System.OperationCanceledException>キャンセルします。 その他のいくつかのトークンには、キャンセルが発生する場合、ループがスローされます、<xref:System.AggregateException>で、<xref:System.OperationCanceledException>内部例外として。  
  
## <a name="see-also"></a>関連項目  
 [データの並列化](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [PLINQ および TPL のラムダ式](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
