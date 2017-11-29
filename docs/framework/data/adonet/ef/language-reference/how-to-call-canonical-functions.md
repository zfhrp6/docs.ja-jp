---
title: "正規関数を呼び出す方法"
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
ms.assetid: b3d84873-7403-4957-8e20-b4ae39f50214
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 26bd528a7c2ad77cb801eb294c34e43c60d2bf76
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-canonical-functions"></a><span data-ttu-id="7bc4d-102">正規関数を呼び出す方法</span><span class="sxs-lookup"><span data-stu-id="7bc4d-102">How to: Call Canonical Functions</span></span>
<span data-ttu-id="7bc4d-103"><xref:System.Data.Objects.EntityFunctions> クラスには、LINQ to Entities クエリで使用する正規関数を公開するメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7bc4d-103">The <xref:System.Data.Objects.EntityFunctions> class contains methods that expose canonical functions to use in LINQ to Entities queries.</span></span> <span data-ttu-id="7bc4d-104">正規関数については、「[正規関数](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7bc4d-104">For information about canonical functions, see [Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7bc4d-105"><xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> クラスの <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> メソッドと <xref:System.Data.Objects.EntityFunctions> メソッドには正規関数に相当するものがありません。</span><span class="sxs-lookup"><span data-stu-id="7bc4d-105">The <xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> and <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> methods in the <xref:System.Data.Objects.EntityFunctions> class do not have canonical function equivalents.</span></span>  
  
 <span data-ttu-id="7bc4d-106">値のセットに対して計算を実行して 1 つの値を返す正規関数 (集計正規関数とも呼ばれる) は、直接呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="7bc4d-106">Canonical functions that perform a calculation on a set of values and return a single value (also known as aggregate canonical functions) can be directly invoked.</span></span> <span data-ttu-id="7bc4d-107">他の正規関数は、LINQ to Entities クエリの一部としてしか呼び出すことができません。</span><span class="sxs-lookup"><span data-stu-id="7bc4d-107">Other canonical functions can only be called as part of a LINQ to Entities query.</span></span> <span data-ttu-id="7bc4d-108">集計関数を直接呼び出すには、その関数に <xref:System.Data.Objects.ObjectQuery%601> を渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="7bc4d-108">To call an aggregate function directly, you must pass an <xref:System.Data.Objects.ObjectQuery%601> to the function.</span></span> <span data-ttu-id="7bc4d-109">詳細については、以下の 2 番目の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7bc4d-109">For more information, see the second example below.</span></span>  
  
 <span data-ttu-id="7bc4d-110">一部の正規関数は、LINQ to Entities クエリで共通言語ランタイム (CLR) メソッドを使用して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="7bc4d-110">You can call some canonical functions by using common language runtime (CLR) methods in LINQ to Entities queries.</span></span> <span data-ttu-id="7bc4d-111">正規関数にマップされる CLR メソッドの一覧は、次を参照してください。[正規の関数マッピングに CLR メソッド](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md)です。</span><span class="sxs-lookup"><span data-stu-id="7bc4d-111">For a list of CLR methods that map to canonical functions, see [CLR Method to Canonical Function Mapping](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7bc4d-112">例</span><span class="sxs-lookup"><span data-stu-id="7bc4d-112">Example</span></span>  
 <span data-ttu-id="7bc4d-113">次の例では、 [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832)です。</span><span class="sxs-lookup"><span data-stu-id="7bc4d-113">The following example uses the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832).</span></span> <span data-ttu-id="7bc4d-114">この例で実行される LINQ to Entities クエリは、<xref:System.Data.Objects.EntityFunctions.DiffDays%2A> メソッドを使用して、`SellEndDate` と `SellStartDate` の差が 365 日よりも少ないすべての製品を返します。</span><span class="sxs-lookup"><span data-stu-id="7bc4d-114">The example executes a LINQ to Entities query that uses the <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> method to return all products for which the difference between `SellEndDate` and `SellStartDate` is less than 365 days:</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#1)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="7bc4d-115">例</span><span class="sxs-lookup"><span data-stu-id="7bc4d-115">Example</span></span>  
 <span data-ttu-id="7bc4d-116">次の例では、 [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832)です。</span><span class="sxs-lookup"><span data-stu-id="7bc4d-116">The following example uses the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832).</span></span> <span data-ttu-id="7bc4d-117">この例では、<xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> の小計の標準偏差を返す集計 `SalesOrderHeader` メソッドを直接呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7bc4d-117">The example calls the aggregate <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> method directly to return the standard deviation of `SalesOrderHeader` subtotals.</span></span> <span data-ttu-id="7bc4d-118"><xref:System.Data.Objects.ObjectQuery%601> は関数に渡されているため、LINQ to Entities クエリに含まれていなくても呼び出すことができる点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="7bc4d-118">Note that an <xref:System.Data.Objects.ObjectQuery%601> is passed to the function, which allows it to be called without being part of a LINQ to Entities query.</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#2)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="7bc4d-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="7bc4d-119">See Also</span></span>  
 [<span data-ttu-id="7bc4d-120">LINQ to Entities クエリで関数の呼び出し</span><span class="sxs-lookup"><span data-stu-id="7bc4d-120">Calling Functions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)  
 [<span data-ttu-id="7bc4d-121">LINQ to Entities でのクエリ</span><span class="sxs-lookup"><span data-stu-id="7bc4d-121">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
