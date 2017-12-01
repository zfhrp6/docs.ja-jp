---
title: "方法: PLINQ の実行モードを指定する"
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
helpviewer_keywords: PLINQ queries, how to use execution mode
ms.assetid: e52ff26c-c5d3-4fab-9fec-c937fb387963
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 745ceae9832582c7b66a56075d128f9cf1c8ff69
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a>方法: PLINQ の実行モードを指定する
この例では、PLINQ を既定のヒューリスティックをバイパスし、クエリの図形に関係なくクエリを並列化を強制する方法を示します。  
  
> [!WARNING]
>  この例は、使用方法を示すことを意図したものであるため、同等の順次的な LINQ to Objects クエリほど高速ではない可能性があります。 高速化の詳細については、次を参照してください。 [PLINQ で高速化について](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)です。  
  
## <a name="example"></a>例  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 PLINQ が並列化の機会を利用するよう設計されています。 ただし、すべてのクエリは並列実行を享受できます。 たとえば、クエリには、ほとんどの処理を行う単一のユーザー デリゲートが含まれている、クエリは、通常実行順番に高速化します。 これは、並列実行を有効にするのにはオーバーヘッドが取得される速度よりも高価であるためです。 したがって、PLINQ は自動的には並列化しないすべてのクエリ。 まず、クエリおよび構成するさまざまな演算子の図形を調べます。 この分析に基づき、既定の実行モードで PLINQ があります、クエリの一部またはすべてを順番に実行します。 ただし、場合によってはするがわかっている場合より、クエリに関する PLINQ は、分析から判断するよりもします。 たとえば、デリゲートが非常に不経済とするクエリは並列化を確実に利用がわかっている場合があります。 このような場合に使用することができます、<xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A>メソッドを指定し、<xref:System.Linq.ParallelExecutionMode.ForceParallelism>常に並列としてクエリを実行するために PLINQ に指示する値。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 切り取って貼り付けるには、このコード、 [PLINQ データのサンプル](../../../docs/standard/parallel-programming/plinq-data-sample.md)からメソッドを呼び出すと`Main`です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Linq.ParallelEnumerable.AsSequential%2A>  
 [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
