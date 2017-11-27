---
title: "方法 : クエリで複合キーを処理する"
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
ms.assetid: ce2f14fd-1038-458a-91e3-a078c61f0d10
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 168e721eee7f5253412438a2185934f01bf081c1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-handle-composite-keys-in-queries"></a><span data-ttu-id="8edf8-102">方法 : クエリで複合キーを処理する</span><span class="sxs-lookup"><span data-stu-id="8edf8-102">How to: Handle Composite Keys in Queries</span></span>
<span data-ttu-id="8edf8-103">演算子によっては、引数を 1 つしか受け取らないものがあります。</span><span class="sxs-lookup"><span data-stu-id="8edf8-103">Some operators can take only one argument.</span></span> <span data-ttu-id="8edf8-104">1 つの演算子にデータベースの複数の列を含めるには、その組み合わせを表す匿名型を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8edf8-104">If your argument must include more than one column from the database, you must create an anonymous type to represent the combination.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8edf8-105">例</span><span class="sxs-lookup"><span data-stu-id="8edf8-105">Example</span></span>  
 <span data-ttu-id="8edf8-106">`GroupBy` 演算子を使用するクエリを次の例に示します。この演算子は、1 つの `key` 引数だけを受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="8edf8-106">The following example shows a query that invokes the `GroupBy` operator, which can take only one `key` argument.</span></span>  
  
 [!code-csharp[DLinqCompositeKeys#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#1)]
 [!code-vb[DLinqCompositeKeys#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="8edf8-107">例</span><span class="sxs-lookup"><span data-stu-id="8edf8-107">Example</span></span>  
 <span data-ttu-id="8edf8-108">次の例に示すように、結合の場合も同様です。</span><span class="sxs-lookup"><span data-stu-id="8edf8-108">The same situation pertains to joins, as in the following example:</span></span>  
  
 [!code-csharp[DLinqCompositeKeys#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#2)]
 [!code-vb[DLinqCompositeKeys#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="8edf8-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="8edf8-109">See Also</span></span>  
 [<span data-ttu-id="8edf8-110">クエリの概念</span><span class="sxs-lookup"><span data-stu-id="8edf8-110">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
