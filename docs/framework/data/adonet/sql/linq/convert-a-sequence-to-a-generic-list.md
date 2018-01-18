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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 066ea4d3c4232137fa6dbd758c8a3be1feec9e61
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="convert-a-sequence-to-a-generic-list"></a><span data-ttu-id="71290-102">ジェネリック リストへのシーケンスの変換</span><span class="sxs-lookup"><span data-stu-id="71290-102">Convert a Sequence to a Generic List</span></span>
<span data-ttu-id="71290-103">シーケンスからジェネリック リストを作成するには、<xref:System.Linq.Enumerable.ToList%2A> を使用します。</span><span class="sxs-lookup"><span data-stu-id="71290-103">Use <xref:System.Linq.Enumerable.ToList%2A> to create a generic List from a sequence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71290-104">例</span><span class="sxs-lookup"><span data-stu-id="71290-104">Example</span></span>  
 <span data-ttu-id="71290-105">次のサンプルでは、<xref:System.Linq.Enumerable.ToList%2A> を使用して、クエリを直ちにジェネリック <xref:System.Collections.Generic.List%601> に評価します。</span><span class="sxs-lookup"><span data-stu-id="71290-105">The following sample uses <xref:System.Linq.Enumerable.ToList%2A> to immediately evaluate a query into a generic <xref:System.Collections.Generic.List%601>.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#45](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#45)]
 [!code-vb[DLinqQueryExamples#45](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#45)]  
  
## <a name="see-also"></a><span data-ttu-id="71290-106">参照</span><span class="sxs-lookup"><span data-stu-id="71290-106">See Also</span></span>  
 [<span data-ttu-id="71290-107">クエリの例</span><span class="sxs-lookup"><span data-stu-id="71290-107">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
