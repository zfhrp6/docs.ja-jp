---
title: 'メソッド ベースのクエリ構文例: 射影'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 505491fa-5920-43ce-8a96-c25389e125d8
ms.openlocfilehash: b938e32ae0e10498203e141c34d35a18a3515257
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="method-based-query-syntax-examples-projection"></a><span data-ttu-id="be54b-102">メソッド ベースのクエリ構文例: 射影</span><span class="sxs-lookup"><span data-stu-id="be54b-102">Method-Based Query Syntax Examples: Projection</span></span>
<span data-ttu-id="be54b-103">このトピックの例を使用する方法を示します、<xref:System.Linq.Enumerable.Select%2A>と<xref:System.Linq.Enumerable.SelectMany%2A>メソッドからクエリ、 [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832)メソッド ベースのクエリ構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="be54b-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methodsto query the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="be54b-104">これらの例で使用されている、AdventureWorks Sales Model は、AdventureWorks サンプル データベースの Contact、Address、Product、SalesOrderHeader、SalesOrderDetail の各テーブルから作成されています。</span><span class="sxs-lookup"><span data-stu-id="be54b-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="be54b-105">このトピックの例では、次を使用して`using` / `Imports`ステートメント。</span><span class="sxs-lookup"><span data-stu-id="be54b-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="select"></a><span data-ttu-id="be54b-106">選択</span><span class="sxs-lookup"><span data-stu-id="be54b-106">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="be54b-107">例</span><span class="sxs-lookup"><span data-stu-id="be54b-107">Example</span></span>  
 <span data-ttu-id="be54b-108">次の例では、<xref:System.Linq.Queryable.Select%2A> メソッドを使用して、`Product.Name` プロパティおよび `Product.ProductID` プロパティを一連の匿名型に射影します。</span><span class="sxs-lookup"><span data-stu-id="be54b-108">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to project the `Product.Name` and `Product.ProductID` properties into a sequence of anonymous types.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectAnonymousTypes_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectanonymoustypes_mq)]
 [!code-vb[DP L2E Examples#SelectAnonymousTypes_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectanonymoustypes_mq)]  
  
### <a name="example"></a><span data-ttu-id="be54b-109">例</span><span class="sxs-lookup"><span data-stu-id="be54b-109">Example</span></span>  
 <span data-ttu-id="be54b-110">次の例では、<xref:System.Linq.Enumerable.Select%2A> メソッドを使用して、一連の製品名だけを取得しています。</span><span class="sxs-lookup"><span data-stu-id="be54b-110">The following example uses the <xref:System.Linq.Enumerable.Select%2A> method to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple2_mq)]
 [!code-vb[DP L2E Examples#SelectSimple2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple2_mq)]  
  
## <a name="selectmany"></a><span data-ttu-id="be54b-111">SelectMany</span><span class="sxs-lookup"><span data-stu-id="be54b-111">SelectMany</span></span>  
  
### <a name="example"></a><span data-ttu-id="be54b-112">例</span><span class="sxs-lookup"><span data-stu-id="be54b-112">Example</span></span>  
 <span data-ttu-id="be54b-113">次の例では、<xref:System.Linq.Enumerable.SelectMany%2A> メソッドを使用して、`TotalDue` が 500.00 に満たないすべての注文を選択します。</span><span class="sxs-lookup"><span data-stu-id="be54b-113">The following example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom_mq)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom_mq)]  
  
### <a name="example"></a><span data-ttu-id="be54b-114">例</span><span class="sxs-lookup"><span data-stu-id="be54b-114">Example</span></span>  
 <span data-ttu-id="be54b-115">次の例では、<xref:System.Linq.Enumerable.SelectMany%2A> メソッドを使用して、2002 年 10 月 1 日以降に受けたすべての注文を選択します。</span><span class="sxs-lookup"><span data-stu-id="be54b-115">The following example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom2_mq)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom2_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="be54b-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="be54b-116">See Also</span></span>  
 [<span data-ttu-id="be54b-117">LINQ to Entities でのクエリ</span><span class="sxs-lookup"><span data-stu-id="be54b-117">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
