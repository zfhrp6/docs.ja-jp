---
title: "メソッド ベースのクエリ構文例: パーティション分割"
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
ms.assetid: b7b64874-c3c8-4bdb-862c-89a168d07827
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f4db203ece2431bd19cc05879dc7d3db88159dec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="method-based-query-syntax-examples-partitioning"></a><span data-ttu-id="c2d00-102">メソッド ベースのクエリ構文例: パーティション分割</span><span class="sxs-lookup"><span data-stu-id="c2d00-102">Method-Based Query Syntax Examples: Partitioning</span></span>
<span data-ttu-id="c2d00-103">このトピックの例を使用する方法を示します、 <xref:System.Linq.Enumerable.Skip%2A>、および<xref:System.Linq.Enumerable.Take%2A>を照会する方法、 [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832)クエリ式の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="c2d00-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Take%2A> methods to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) using query expression syntax.</span></span> <span data-ttu-id="c2d00-104">これらの例で使用されている、AdventureWorks Sales Model は、AdventureWorks サンプル データベースの Contact、Address、Product、SalesOrderHeader、SalesOrderDetail の各テーブルから作成されています。</span><span class="sxs-lookup"><span data-stu-id="c2d00-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="c2d00-105">このトピックの例では、次を使用して`using` / `Imports`ステートメント。</span><span class="sxs-lookup"><span data-stu-id="c2d00-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="skip"></a><span data-ttu-id="c2d00-106">Skip</span><span class="sxs-lookup"><span data-stu-id="c2d00-106">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="c2d00-107">例</span><span class="sxs-lookup"><span data-stu-id="c2d00-107">Example</span></span>  
 <span data-ttu-id="c2d00-108">次の例では、Contact テーブルから最初の 5 つを除くすべての連絡先を、<xref:System.Linq.Enumerable.Skip%2A> メソッドを使って取得します。</span><span class="sxs-lookup"><span data-stu-id="c2d00-108">The following example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first five contacts of the Contact table.</span></span>  
  
 [!code-csharp[DP L2E Examples#SkipSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipsimple)]
 [!code-vb[DP L2E Examples#SkipSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipsimple)]  
  
### <a name="example"></a><span data-ttu-id="c2d00-109">例</span><span class="sxs-lookup"><span data-stu-id="c2d00-109">Example</span></span>  
 <span data-ttu-id="c2d00-110">次の例では、Seattle から最初の 2 つを除くすべての住所を、<xref:System.Linq.Enumerable.Skip%2A> メソッドを使って取得します。</span><span class="sxs-lookup"><span data-stu-id="c2d00-110">The following example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#SkipNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP L2E Examples#SkipNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipnested)]  
  
## <a name="take"></a><span data-ttu-id="c2d00-111">Take</span><span class="sxs-lookup"><span data-stu-id="c2d00-111">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="c2d00-112">例</span><span class="sxs-lookup"><span data-stu-id="c2d00-112">Example</span></span>  
 <span data-ttu-id="c2d00-113">次の例では、Contact テーブルから最初の 5 つの連絡先だけを、<xref:System.Linq.Enumerable.Take%2A> メソッドを使って取得します。</span><span class="sxs-lookup"><span data-stu-id="c2d00-113">The following example uses the <xref:System.Linq.Enumerable.Take%2A> method to get only the first five contacts from the Contact table.</span></span>  
  
 [!code-csharp[DP L2E Examples#TakeSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takesimple)]
 [!code-vb[DP L2E Examples#TakeSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takesimple)]  
  
### <a name="example"></a><span data-ttu-id="c2d00-114">例</span><span class="sxs-lookup"><span data-stu-id="c2d00-114">Example</span></span>  
 <span data-ttu-id="c2d00-115">次の例では、Seattle から最初の 3 つの住所を、<xref:System.Linq.Enumerable.Take%2A> メソッドを使って取得します。</span><span class="sxs-lookup"><span data-stu-id="c2d00-115">The following example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#TakeNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takenested)]
 [!code-vb[DP L2E Examples#TakeNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takenested)]  
  
## <a name="see-also"></a><span data-ttu-id="c2d00-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="c2d00-116">See Also</span></span>  
 [<span data-ttu-id="c2d00-117">LINQ to Entities でのクエリ</span><span class="sxs-lookup"><span data-stu-id="c2d00-117">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
