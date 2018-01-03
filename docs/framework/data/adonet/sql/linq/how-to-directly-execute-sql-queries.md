---
title: "方法 : SQL クエリを直接実行する"
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
ms.assetid: e491b9bf-741a-4296-9f51-76c25ddf6a82
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e8bbeb0d7ce040387b263486b947e793eca39d29
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-directly-execute-sql-queries"></a><span data-ttu-id="f8655-102">方法 : SQL クエリを直接実行する</span><span class="sxs-lookup"><span data-stu-id="f8655-102">How to: Directly Execute SQL Queries</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="f8655-103"> は、作成したクエリをパラメーター化された SQL クエリ (テキスト形式) に変換し、それを SQL Server に送って処理します。</span><span class="sxs-lookup"><span data-stu-id="f8655-103"> translates the queries you write into parameterized SQL queries (in text form) and sends them to the SQL server for processing.</span></span>  
  
 <span data-ttu-id="f8655-104">アプリケーションでローカルに使用できるさまざまなメソッドの中には、SQL では実行できないものもあります。</span><span class="sxs-lookup"><span data-stu-id="f8655-104">SQL cannot execute the variety of methods that might be locally available to your application.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="f8655-105"> は、このようなローカル メソッドを、SQL 環境内で使用できる同等の操作や関数に変換しようとします。</span><span class="sxs-lookup"><span data-stu-id="f8655-105"> tries to convert these local methods to equivalent operations and functions that are available inside the SQL environment.</span></span> <span data-ttu-id="f8655-106">[!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] 組み込み型のほとんどのメソッドと演算子には、SQL コマンドに直接対応する変換が用意されています。</span><span class="sxs-lookup"><span data-stu-id="f8655-106">Most methods and operators on [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] built-in types have direct translations to SQL commands.</span></span> <span data-ttu-id="f8655-107">使用可能な関数から生成できるものもあります。</span><span class="sxs-lookup"><span data-stu-id="f8655-107">Some can be produced from the functions that are available.</span></span> <span data-ttu-id="f8655-108">生成できないものについては、ランタイム例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="f8655-108">Those that cannot be produced generate run-time exceptions.</span></span> <span data-ttu-id="f8655-109">詳細については、次を参照してください。 [SQL-CLR 型マッピング](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)です。</span><span class="sxs-lookup"><span data-stu-id="f8655-109">For more information, see [SQL-CLR Type Mapping](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span></span>  
  
 <span data-ttu-id="f8655-110">特殊なタスクに対して [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] クエリでは不十分な場合は、<xref:System.Data.Linq.DataContext.ExecuteQuery%2A> メソッドを使用して SQL クエリを実行し、そのクエリの結果をオブジェクトに直接変換できます。</span><span class="sxs-lookup"><span data-stu-id="f8655-110">In cases where a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query is insufficient for a specialized task, you can use the <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method to execute a SQL query, and then convert the result of your query directly into objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8655-111">例</span><span class="sxs-lookup"><span data-stu-id="f8655-111">Example</span></span>  
 <span data-ttu-id="f8655-112">次の例では、`Customer` クラスのデータが 2 つのテーブル (customer1 および customer2) にわたって格納されているものとします。</span><span class="sxs-lookup"><span data-stu-id="f8655-112">In the following example, assume that the data for the `Customer` class is spread over two tables (customer1 and customer2).</span></span> <span data-ttu-id="f8655-113">クエリは `Customer` オブジェクトのシーケンスを返します。</span><span class="sxs-lookup"><span data-stu-id="f8655-113">The query returns a sequence of `Customer` objects.</span></span>  
  
 [!code-csharp[DLinqQuerying#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#4)]
 [!code-vb[DLinqQuerying#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#4)]  
  
 <span data-ttu-id="f8655-114">表形式の結果内の列名には、エンティティ クラスの列のプロパティが一致する限り[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]SQL クエリからオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="f8655-114">As long as the column names in the tabular results match column properties of your entity class, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates your objects out of any SQL query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8655-115">例</span><span class="sxs-lookup"><span data-stu-id="f8655-115">Example</span></span>  
 <span data-ttu-id="f8655-116"><xref:System.Data.Linq.DataContext.ExecuteQuery%2A> メソッドは、パラメーターの使用にも対応しています。</span><span class="sxs-lookup"><span data-stu-id="f8655-116">The <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method also allows for parameters.</span></span> <span data-ttu-id="f8655-117">パラメーター化されたクエリを実行するには、次のようなコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="f8655-117">Use code such as the following to execute a parameterized query.</span></span>  
  
 [!code-csharp[DLinqQuerying#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#5)]
 [!code-vb[DLinqQuerying#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#5)]  
  
 <span data-ttu-id="f8655-118">クエリ テキスト内では、`Console.WriteLine()` および `String.Format()` で使用するのと同じ中かっこ表記を使用して、パラメーターを表現します。</span><span class="sxs-lookup"><span data-stu-id="f8655-118">The parameters are expressed in the query text by using the same curly notation used by `Console.WriteLine()` and `String.Format()`.</span></span> <span data-ttu-id="f8655-119">実際には、`String.Format()`などのパラメーター名の生成中、中かっこで囲んだパラメーターを置き換えることを指定するクエリ文字列で実際に呼び出される@p0、 @p1 ..., @p(n)。</span><span class="sxs-lookup"><span data-stu-id="f8655-119">In fact, `String.Format()` is actually called on the query string you provide, substituting the curly braced parameters with generated parameter names such as @p0, @p1 …, @p(n).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8655-120">参照</span><span class="sxs-lookup"><span data-stu-id="f8655-120">See Also</span></span>  
 [<span data-ttu-id="f8655-121">背景情報</span><span class="sxs-lookup"><span data-stu-id="f8655-121">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [<span data-ttu-id="f8655-122">データベースに対するクエリの実行</span><span class="sxs-lookup"><span data-stu-id="f8655-122">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
