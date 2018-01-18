---
title: "System.TimeSpan メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9333fee8-1454-4374-855b-8c14c002f48f
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: baec7609ce1d2f04b1c24165c53bc7cce425f06d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="systemtimespan-methods"></a><span data-ttu-id="e1e52-102">System.TimeSpan メソッド</span><span class="sxs-lookup"><span data-stu-id="e1e52-102">System.TimeSpan Methods</span></span>
<span data-ttu-id="e1e52-103"><xref:System.TimeSpan?displayProperty=nameWithType> のメンバー サポートは、使用している .NET Framework と Microsoft SQL Server のバージョンに大きく依存します。</span><span class="sxs-lookup"><span data-stu-id="e1e52-103">Member support for <xref:System.TimeSpan?displayProperty=nameWithType> greatly depends on the versions of the .NET Framework and Microsoft SQL Server that you are using.</span></span>  
  
 <span data-ttu-id="e1e52-104">メソッド、演算子、またはプロパティがサポートされていなければ、LINQ to SQL でメンバーを変換して SQL Server で実行することができません。</span><span class="sxs-lookup"><span data-stu-id="e1e52-104">When a method, operator, or property is unsupported; it means that LINQ to SQL cannot translate the member for execution on the SQL Server.</span></span> <span data-ttu-id="e1e52-105">それでもこれらのメンバーをコードで使用することはできますが、</span><span class="sxs-lookup"><span data-stu-id="e1e52-105">You may still be able to use these members in your code.</span></span> <span data-ttu-id="e1e52-106">クエリが Transact-SQL に変換される前か、データベースから結果が取得された後で評価する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e1e52-106">However, they must be evaluated before the query is translated to Transact-SQL or after the results have been retrieved from the database.</span></span>  
  
## <a name="previous-limitations"></a><span data-ttu-id="e1e52-107">以前の制限</span><span class="sxs-lookup"><span data-stu-id="e1e52-107">Previous Limitations</span></span>  
 <span data-ttu-id="e1e52-108">.NET Framework 3.5 SP1 より前のバージョンの .NET Framework で LINQ to SQL を使用すると、SQL Server のデータベース フィールドを <xref:System.TimeSpan?displayProperty=nameWithType> にマッピングできません。</span><span class="sxs-lookup"><span data-stu-id="e1e52-108">When using LINQ to SQL with versions of the .NET Framework prior to .NET Framework 3.5 SP1, you cannot map SQL Server database fields to <xref:System.TimeSpan?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e1e52-109">ただし、<xref:System.TimeSpan> 値を <xref:System.TimeSpan> 減算から返したり、リテラル変数またはバインド変数として式に取り込んだりできるため、<xref:System.DateTime> の操作はサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e1e52-109">However, operations on <xref:System.TimeSpan> are supported because <xref:System.TimeSpan> values can be returned from <xref:System.DateTime> subtraction or introduced into an expression as a literal or bound variable.</span></span>  
  
## <a name="supported-systemtimespan-method-support"></a><span data-ttu-id="e1e52-110">サポートされている System.TimeSpan メソッド</span><span class="sxs-lookup"><span data-stu-id="e1e52-110">Supported System.TimeSpan Method Support</span></span>  
 <span data-ttu-id="e1e52-111">LINQ to SQL でサポートされている以下のメソッド、演算子、およびプロパティは、LINQ to SQL のクエリで使用できます。</span><span class="sxs-lookup"><span data-stu-id="e1e52-111">The following LINQ to SQL-supported methods, operators, and properties are available for you to use in your LINQ to SQL queries.</span></span> <span data-ttu-id="e1e52-112">オブジェクト モデルまたは外部マッピング ファイルにマッピングされると、LINQ to SQL クエリ内で <xref:System.TimeSpan?displayProperty=nameWithType> メンバーの多くを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="e1e52-112">Once mapped in the object model or external mapping file, LINQ to SQL allows you to call many of the <xref:System.TimeSpan?displayProperty=nameWithType> members inside your LINQ to SQL queries.</span></span>  
  
|<span data-ttu-id="e1e52-113">サポートされている <xref:System.TimeSpan> メソッド</span><span class="sxs-lookup"><span data-stu-id="e1e52-113">Supported <xref:System.TimeSpan> Methods</span></span>|<span data-ttu-id="e1e52-114">サポートされている <xref:System.TimeSpan> 演算子</span><span class="sxs-lookup"><span data-stu-id="e1e52-114">Supported <xref:System.TimeSpan> Operators</span></span>|<span data-ttu-id="e1e52-115">サポートされている <xref:System.TimeSpan> プロパティ</span><span class="sxs-lookup"><span data-stu-id="e1e52-115">Supported <xref:System.TimeSpan> Properties</span></span>|  
|------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.TimeSpan.Compare%2A>|<xref:System.TimeSpan.op_Equality%2A>|<xref:System.TimeSpan.Days%2A>|  
|<xref:System.TimeSpan.CompareTo%28System.TimeSpan%29>|<xref:System.TimeSpan.op_GreaterThan%2A>|<xref:System.TimeSpan.Hours%2A>|  
|<xref:System.TimeSpan.Duration%2A>|<xref:System.TimeSpan.op_GreaterThanOrEqual%2A>|<xref:System.TimeSpan.MaxValue>|  
|<xref:System.TimeSpan.Equals%28System.TimeSpan%2CSystem.TimeSpan%29>|<xref:System.TimeSpan.op_Inequality%2A>|<xref:System.TimeSpan.Milliseconds%2A>|  
|<xref:System.TimeSpan.Equals%28System.TimeSpan%29>|<xref:System.TimeSpan.op_LessThan%2A>|<xref:System.TimeSpan.Minutes%2A>|  
||<xref:System.TimeSpan.op_LessThanOrEqual%2A>|<!--zz <xref:System.TimeSpan.MinValue%2A>-->|  
  
> [!NOTE]
>  <span data-ttu-id="e1e52-116">LINQ to SQL で <xref:System.TimeSpan?displayProperty=nameWithType> を SQL の `TIME` 列にマッピングする機能を使用するには、.NET Framework 3.5 SP1 以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="e1e52-116">The ability to map <xref:System.TimeSpan?displayProperty=nameWithType> to a SQL `TIME` column with LINQ to SQL requires the .NET Framework 3.5 SP1 and beyond.</span></span> <span data-ttu-id="e1e52-117">SQL の `TIME` データ型は Microsoft SQL Server 2008 以降でのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="e1e52-117">The SQL `TIME` data type is only available in Microsoft SQL Server 2008 and beyond.</span></span>  
  
### <a name="addition-and-subtraction"></a><span data-ttu-id="e1e52-118">加算と減算</span><span class="sxs-lookup"><span data-stu-id="e1e52-118">Addition and Subtraction</span></span>  
 <span data-ttu-id="e1e52-119">加算と減算は、CLR の <xref:System.TimeSpan?displayProperty=nameWithType> 型ではサポートされていますが、SQL の `TIME` 型ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="e1e52-119">Although the CLR <xref:System.TimeSpan?displayProperty=nameWithType> type does support addition and subtraction, the SQL `TIME` type does not.</span></span> <span data-ttu-id="e1e52-120">そのため、LINQ to SQL クエリにより、SQL の `TIME` 型にマッピングしたときに加算や減算を試みると、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="e1e52-120">Because of this, your LINQ to SQL queries will generate errors if they attempt addition and subtraction when they are mapped to the SQL `TIME` type.</span></span> <span data-ttu-id="e1e52-121">SQL 日付と時刻型を操作するための他の考慮事項を見つけることができます[SQL-CLR 型マッピング](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)です。</span><span class="sxs-lookup"><span data-stu-id="e1e52-121">You can find other considerations for working with SQL date and time types in [SQL-CLR Type Mapping](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1e52-122">参照</span><span class="sxs-lookup"><span data-stu-id="e1e52-122">See Also</span></span>  
 [<span data-ttu-id="e1e52-123">クエリの概念</span><span class="sxs-lookup"><span data-stu-id="e1e52-123">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [<span data-ttu-id="e1e52-124">オブジェクト モデルの作成</span><span class="sxs-lookup"><span data-stu-id="e1e52-124">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)  
 [<span data-ttu-id="e1e52-125">SQL と CLR の型マッピング</span><span class="sxs-lookup"><span data-stu-id="e1e52-125">SQL-CLR Type Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)  
 [<span data-ttu-id="e1e52-126">データ型と関数</span><span class="sxs-lookup"><span data-stu-id="e1e52-126">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
