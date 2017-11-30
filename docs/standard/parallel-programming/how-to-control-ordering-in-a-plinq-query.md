---
title: "方法: PLINQ クエリの順序を制御する"
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
helpviewer_keywords: PLINQ queries, how to control ordering
ms.assetid: c67eccc7-004d-4b2f-987e-919cbbd62ef7
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b9e29aa825a68154e32a34a23ca170258092b88a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-control-ordering-in-a-plinq-query"></a>方法: PLINQ クエリの順序を制御する
これらの例を使用して PLINQ クエリの順序を制御する方法を示して、<xref:System.Linq.ParallelEnumerable.AsOrdered%2A>拡張メソッド。  
  
> [!WARNING]
>  これらの例は、使用法を説明するものでは、主に可能性がありますや、可能性がありますいないほど高速で、同等の連続した LINQ to Objects クエリ。  
  
## <a name="example"></a>例  
 次の例では、ソース シーケンスの順序を維持します。 これは、操作は必要です。など一部のクエリ演算子では、正しい結果を生成するために、順序付けられたソース シーケンスが必要です。  
  
 [!code-csharp[PLINQ#12](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#12)]
 [!code-vb[PLINQ#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#12)]  
  
## <a name="example"></a>例  
 クエリ演算子を順序付けるがソース シーケンスが求められるを次の例に示します。 これらの演算子は、順序なしのシーケンスで機能しますが、予期しない結果が生じる可能性があります。  
  
 [!code-csharp[PLINQ#14](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#14)]
 [!code-vb[PLINQ#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#14)]  
  
 このメソッドを実行する、PLINQDataSample クラス内に貼り付け、 [PLINQ データのサンプル](../../../docs/standard/parallel-programming/plinq-data-sample.md)プロジェクトし、F5 キーを押します。  
  
## <a name="example"></a>例  
 次の例では、クエリの最初の部分の順序を維持し、join 句のパフォーマンスを向上する順序を削除し、最終的な結果のシーケンスに順序を適用する方法を示します。  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 このメソッドを実行する、PLINQDataSample クラス内に貼り付け、 [PLINQ データのサンプル](../../../docs/standard/parallel-programming/plinq-data-sample.md)プロジェクトし、F5 キーを押します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Linq.ParallelEnumerable>  
 [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
