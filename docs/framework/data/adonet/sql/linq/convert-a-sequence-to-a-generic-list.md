---
title: "ジェネリック リストへのシーケンスの変換"
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
ms.assetid: 7ab76d93-6898-4e75-b76f-290a66ecead8
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 4b1fa6895e015ab7123bf454aac435812e4a23da
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="convert-a-sequence-to-a-generic-list"></a><span data-ttu-id="a73af-102">ジェネリック リストへのシーケンスの変換</span><span class="sxs-lookup"><span data-stu-id="a73af-102">Convert a Sequence to a Generic List</span></span>
<span data-ttu-id="a73af-103">シーケンスからジェネリック リストを作成するには、<xref:System.Linq.Enumerable.ToList%2A> を使用します。</span><span class="sxs-lookup"><span data-stu-id="a73af-103">Use <xref:System.Linq.Enumerable.ToList%2A> to create a generic List from a sequence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a73af-104">例</span><span class="sxs-lookup"><span data-stu-id="a73af-104">Example</span></span>  
 <span data-ttu-id="a73af-105">次のサンプルでは、<xref:System.Linq.Enumerable.ToList%2A> を使用して、クエリを直ちにジェネリック <xref:System.Collections.Generic.List%601> に評価します。</span><span class="sxs-lookup"><span data-stu-id="a73af-105">The following sample uses <xref:System.Linq.Enumerable.ToList%2A> to immediately evaluate a query into a generic <xref:System.Collections.Generic.List%601>.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#45](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#45)]
 [!code-vb[DLinqQueryExamples#45](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#45)]  
  
## <a name="see-also"></a><span data-ttu-id="a73af-106">参照</span><span class="sxs-lookup"><span data-stu-id="a73af-106">See Also</span></span>  
 [<span data-ttu-id="a73af-107">クエリの例</span><span class="sxs-lookup"><span data-stu-id="a73af-107">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
