---
title: "方法: 並列および順次の LINQ クエリを連結する"
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
helpviewer_keywords: parallel queries, combine parallel and sequential
ms.assetid: 1167cfe6-c8aa-4096-94ba-c66c3a4edf4c
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4da91ff535059b181baa637164a854cd75d06334
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-combine-parallel-and-sequential-linq-queries"></a>方法: 並列および順次の LINQ クエリを連結する
この例を使用する方法を示しています、 <xref:System.Linq.ParallelEnumerable.AsSequential%2A> PLINQ クエリのすべての後続演算子を順番に処理するように指示します。 順次処理は通常、並列処理よりも遅くなりますが、場合によっては必要正しい結果を生成します。  
  
> [!WARNING]
>  この例は、使用方法を示すことを意図したものであるため、同等の順次的な LINQ to Objects クエリほど高速ではない可能性があります。 高速化の詳細については、次を参照してください。 [PLINQ で高速化について](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)です。  
  
## <a name="example"></a>例  
 次の例では、1 つのシナリオを示しますを<xref:System.Linq.ParallelEnumerable.AsSequential%2A>つまりする、必要なクエリの前の句で確立された順序を保持します。  
  
 [!code-csharp[PLINQ#24](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#24)]
 [!code-vb[PLINQ#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#24)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 コンパイルして、このコードを実行、貼り付けます、 [PLINQ データのサンプル](../../../docs/standard/parallel-programming/plinq-data-sample.md)プロジェクトで、行を追加してからメソッドを呼び出す`Main`、f5 キーを押します。  
  
## <a name="see-also"></a>関連項目  
 [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
