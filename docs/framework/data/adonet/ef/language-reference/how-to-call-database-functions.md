---
title: データベース関数を呼び出す方法
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 79038efa-15bf-464a-83e2-35fe145252ce
ms.openlocfilehash: b885cedbb324ee0a076990bceb28bf256814bb26
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760649"
---
# <a name="how-to-call-database-functions"></a><span data-ttu-id="4d96a-102">データベース関数を呼び出す方法</span><span class="sxs-lookup"><span data-stu-id="4d96a-102">How to: Call Database Functions</span></span>
<span data-ttu-id="4d96a-103"><xref:System.Data.Objects.SqlClient.SqlFunctions> クラスには、LINQ to Entities クエリで使用する SQL Server 関数を公開するメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="4d96a-103">The <xref:System.Data.Objects.SqlClient.SqlFunctions> class contains methods that expose SQL Server functions to use in LINQ to Entities queries.</span></span> <span data-ttu-id="4d96a-104">LINQ to Entities クエリで <xref:System.Data.Objects.SqlClient.SqlFunctions> メソッドを使用すると、対応するデータベース関数がデータベースで実行されます。</span><span class="sxs-lookup"><span data-stu-id="4d96a-104">When you use <xref:System.Data.Objects.SqlClient.SqlFunctions> methods in LINQ to Entities queries, the corresponding database functions are executed in the database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4d96a-105">値のセットに対して計算を実行して 1 つの値を返すデータベース関数 (集計データベース関数とも呼ばれる) は、直接呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="4d96a-105">Database functions that perform a calculation on a set of values and return a single value (also known as aggregate database functions) can be directly invoked.</span></span> <span data-ttu-id="4d96a-106">他の正規関数は、LINQ to Entities クエリの一部としてしか呼び出すことができません。</span><span class="sxs-lookup"><span data-stu-id="4d96a-106">Other canonical functions can only be called as part of a LINQ to Entities query.</span></span> <span data-ttu-id="4d96a-107">集計関数を直接呼び出すには、その関数に <xref:System.Data.Objects.ObjectQuery%601> を渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="4d96a-107">To call an aggregate function directly, you must pass an <xref:System.Data.Objects.ObjectQuery%601> to the function.</span></span> <span data-ttu-id="4d96a-108">詳細については、以下の 2 番目の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4d96a-108">For more information, see the second example below.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4d96a-109"><xref:System.Data.Objects.SqlClient.SqlFunctions> クラスのメソッドは、SQL Server 関数に固有です。</span><span class="sxs-lookup"><span data-stu-id="4d96a-109">The methods in the <xref:System.Data.Objects.SqlClient.SqlFunctions> class are specific to SQL Server functions.</span></span> <span data-ttu-id="4d96a-110">他のプロバイダーから、データベース関数を公開する同様のクラスを入手できることがあります。</span><span class="sxs-lookup"><span data-stu-id="4d96a-110">Similar classes that expose database functions may be available through other providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d96a-111">例</span><span class="sxs-lookup"><span data-stu-id="4d96a-111">Example</span></span>  
 <span data-ttu-id="4d96a-112">次の例では、 [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832)です。</span><span class="sxs-lookup"><span data-stu-id="4d96a-112">The following example uses the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832).</span></span> <span data-ttu-id="4d96a-113">この例では、<xref:System.Data.Objects.SqlClient.SqlFunctions.CharIndex%2A> メソッドを使用する LINQ to Entities クエリを実行して、姓が "Si" で始まる連絡先をすべて返します。</span><span class="sxs-lookup"><span data-stu-id="4d96a-113">The example executes a LINQ to Entities query that uses the <xref:System.Data.Objects.SqlClient.SqlFunctions.CharIndex%2A> method to return all contacts whose last name starts with "Si":</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#3)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="4d96a-114">例</span><span class="sxs-lookup"><span data-stu-id="4d96a-114">Example</span></span>  
 <span data-ttu-id="4d96a-115">次の例では、 [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832)です。</span><span class="sxs-lookup"><span data-stu-id="4d96a-115">The following example uses the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832).</span></span> <span data-ttu-id="4d96a-116">この例では、集計 <xref:System.Data.Objects.SqlClient.SqlFunctions.ChecksumAggregate%2A> メソッドを直接呼び出します。</span><span class="sxs-lookup"><span data-stu-id="4d96a-116">The example calls the aggregate <xref:System.Data.Objects.SqlClient.SqlFunctions.ChecksumAggregate%2A> method directly.</span></span> <span data-ttu-id="4d96a-117"><xref:System.Data.Objects.ObjectQuery%601> は関数に渡されているため、LINQ to Entities クエリに含まれていなくても呼び出すことができる点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="4d96a-117">Note that an <xref:System.Data.Objects.ObjectQuery%601> is passed to the function, which allows it to be called without being part of a LINQ to Entities query.</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#4)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="4d96a-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="4d96a-118">See Also</span></span>  
 [<span data-ttu-id="4d96a-119">LINQ to Entities クエリ内の関数の呼び出し</span><span class="sxs-lookup"><span data-stu-id="4d96a-119">Calling Functions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)  
 [<span data-ttu-id="4d96a-120">LINQ to Entities でのクエリ</span><span class="sxs-lookup"><span data-stu-id="4d96a-120">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
