---
title: "定数式"
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
ms.assetid: 9d98a7be-b110-4edb-8eba-bed10f250b6d
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 328284ce07a0361dbfd25b0d765000b497156ff7
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="constant-expressions"></a><span data-ttu-id="c12ae-102">定数式</span><span class="sxs-lookup"><span data-stu-id="c12ae-102">Constant Expressions</span></span>
<span data-ttu-id="c12ae-103">定数式は、定数値で構成されています。</span><span class="sxs-lookup"><span data-stu-id="c12ae-103">A constant expression consists of a constant value.</span></span> <span data-ttu-id="c12ae-104">定数値は、クライアント側で変換されることなく、コマンド ツリーの定数式に直接変換されます。</span><span class="sxs-lookup"><span data-stu-id="c12ae-104">Constant values are directly converted to constant command tree expressions, without any translation on the client.</span></span> <span data-ttu-id="c12ae-105">これには、定数値になる式が含まれます。</span><span class="sxs-lookup"><span data-stu-id="c12ae-105">This includes expressions that result in a constant value.</span></span> <span data-ttu-id="c12ae-106">したがって、定数にかかわるすべての式でデータ ソースの動作が、予期したとおりになります。</span><span class="sxs-lookup"><span data-stu-id="c12ae-106">Therefore, data source behavior should be expected for all expressions involving constants.</span></span> <span data-ttu-id="c12ae-107">これは CLR の動作とは異なる結果となります。</span><span class="sxs-lookup"><span data-stu-id="c12ae-107">This can result in behavior that differs from CLR behavior.</span></span>  
  
 <span data-ttu-id="c12ae-108">次の例では、サーバーで評価される定数式を示します。</span><span class="sxs-lookup"><span data-stu-id="c12ae-108">The following example shows a constant expression that is evaluated on the server.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)]<span data-ttu-id="c12ae-109"> では、ユーザー クラスを定数として使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="c12ae-109"> does not support using a user class as a constant.</span></span> <span data-ttu-id="c12ae-110">ただし、ユーザー クラスのプロパティ参照は定数と見なされます。そのため、コマンド ツリーの定数式に変換され、データ ソースで実行されます。</span><span class="sxs-lookup"><span data-stu-id="c12ae-110">However, a property reference on a user class is considered a constant, and will be converted to a command tree constant expression and executed on the data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c12ae-111">参照</span><span class="sxs-lookup"><span data-stu-id="c12ae-111">See Also</span></span>  
 [<span data-ttu-id="c12ae-112">LINQ to Entities クエリ内の式</span><span class="sxs-lookup"><span data-stu-id="c12ae-112">Expressions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
