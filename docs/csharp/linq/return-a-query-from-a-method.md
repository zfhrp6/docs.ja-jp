---
title: "メソッドからクエリを返す"
description: "クエリを返す方法。"
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 747345f0a765bc6cbe947a2b0c7bc025eb599550
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a><span data-ttu-id="9dd5b-104">方法 : メソッドからクエリを返す (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="9dd5b-104">How to: Return a Query from a Method (C# Programming Guide)</span></span>
<span data-ttu-id="9dd5b-105">この例では、メソッドから、クエリを戻り値として返す方法と `out` パラメーターとして返す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9dd5b-105">This example shows how to return a query from a method as the return value and as an `out` parameter.</span></span>  
  
 <span data-ttu-id="9dd5b-106">クエリ オブジェクトはコンポーザブルです。つまり、メソッドからクエリを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="9dd5b-106">Query objects are composable, meaning that you can return a query from a method.</span></span> <span data-ttu-id="9dd5b-107">クエリを表すオブジェクトには、結果のコレクションではなく、必要に応じて結果を生成する手順が格納されます。</span><span class="sxs-lookup"><span data-stu-id="9dd5b-107">Objects that represent queries do not store the resulting collection, but rather the steps to produce the results when needed.</span></span> <span data-ttu-id="9dd5b-108">メソッドからクエリ オブジェクトを返すメリットは、そのオブジェクトをさらに構成したり変更したりできることです。</span><span class="sxs-lookup"><span data-stu-id="9dd5b-108">The advantage of returning query objects from methods is that they can be further composed or modified.</span></span> <span data-ttu-id="9dd5b-109">そのため、クエリを返すメソッドの戻り値または `out` パラメーターも同じ型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="9dd5b-109">Therefore any return value or `out` parameter of a method that returns a query must also have that type.</span></span> <span data-ttu-id="9dd5b-110">メソッドがクエリを具象型 <xref:System.Collections.Generic.List%601> または <xref:System.Array> に実体化する場合は、そのメソッドは、クエリ自体ではなくクエリ結果を返すと見なされます。</span><span class="sxs-lookup"><span data-stu-id="9dd5b-110">If a method materializes a query into a concrete <xref:System.Collections.Generic.List%601> or <xref:System.Array> type, it is considered to be returning the query results instead of the query itself.</span></span> <span data-ttu-id="9dd5b-111">メソッドから返されたクエリ変数は、引き続き構成または変更できます。</span><span class="sxs-lookup"><span data-stu-id="9dd5b-111">A query variable that is returned from a method can still be composed or modified.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9dd5b-112">例</span><span class="sxs-lookup"><span data-stu-id="9dd5b-112">Example</span></span>  
 <span data-ttu-id="9dd5b-113">次の例は、最初のメソッドはクエリを戻り値として返し、2 番目のメソッドはクエリを `out` パラメーターとして返しています。</span><span class="sxs-lookup"><span data-stu-id="9dd5b-113">In the following example, the first method returns a query as a return value, and the second method returns a query as an `out` parameter.</span></span> <span data-ttu-id="9dd5b-114">どちらの場合も返されるのはクエリであり、クエリ結果ではないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="9dd5b-114">Note that in both cases it is a query that is  returned, not query results.</span></span>  
  
 <span data-ttu-id="9dd5b-115">[!code-cs[csProgGuideLINQ#80](../../../samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="9dd5b-115">[!code-cs[csProgGuideLINQ#80](../../../samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="9dd5b-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="9dd5b-116">See Also</span></span>  
 [<span data-ttu-id="9dd5b-117">LINQ クエリ式</span><span class="sxs-lookup"><span data-stu-id="9dd5b-117">LINQ Query Expressions</span></span>](index.md)

