---
title: "方法 : シーケンスを配列に変換する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: bf0af444-890d-43e2-aeca-98589dd74ddf
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ea3db4a6e035a0a17d078908e06a7997d7c87ad6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="convert-a-sequence-to-an-array"></a><span data-ttu-id="6eab1-102">方法 : シーケンスを配列に変換する</span><span class="sxs-lookup"><span data-stu-id="6eab1-102">Convert a Sequence to an Array</span></span>
<span data-ttu-id="6eab1-103">シーケンスから配列を作成するには、<xref:System.Linq.Enumerable.ToArray%2A> を使用します。</span><span class="sxs-lookup"><span data-stu-id="6eab1-103">Use <xref:System.Linq.Enumerable.ToArray%2A> to create an array from a sequence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6eab1-104">例</span><span class="sxs-lookup"><span data-stu-id="6eab1-104">Example</span></span>  
 <span data-ttu-id="6eab1-105">次の例では、<xref:System.Linq.Enumerable.ToArray%2A> を使用して、クエリを直ちに配列に評価し、3 番目の要素を取得します。</span><span class="sxs-lookup"><span data-stu-id="6eab1-105">The following example uses <xref:System.Linq.Enumerable.ToArray%2A> to immediately evaluate a query into an array and to get the third element.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#44](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#44)]
 [!code-vb[DLinqQueryExamples#44](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#44)]  
  
## <a name="see-also"></a><span data-ttu-id="6eab1-106">関連項目</span><span class="sxs-lookup"><span data-stu-id="6eab1-106">See Also</span></span>  
 [<span data-ttu-id="6eab1-107">クエリの例</span><span class="sxs-lookup"><span data-stu-id="6eab1-107">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
