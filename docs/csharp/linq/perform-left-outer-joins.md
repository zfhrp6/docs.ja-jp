---
title: "左外部結合の実行"
description: "方法: 左外部結合を実行する。"
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: f542cee6-3169-4dcf-a631-3a6a79ccd473
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d81f6e9df228dc6eec985253f53b70a95493ed42
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="perform-left-outer-joins"></a><span data-ttu-id="c3996-104">左外部結合の実行</span><span class="sxs-lookup"><span data-stu-id="c3996-104">Perform left outer joins</span></span>
<span data-ttu-id="c3996-105">左外部結合は、最初のコレクションの各要素を、2 つ目のコレクション内にある要素との相関関係の有無にかかわらず返す結合です。</span><span class="sxs-lookup"><span data-stu-id="c3996-105">A left outer join is a join in which each element of the first collection is returned, regardless of whether it has any correlated elements in the second collection.</span></span> <span data-ttu-id="c3996-106">LINQ を使用すると、グループ結合の結果に対して <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> メソッドを呼び出すことで、左外部結合を実行できます。</span><span class="sxs-lookup"><span data-stu-id="c3996-106">You can use LINQ to perform a left outer join by calling the <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> method on the results of a group join.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3996-107">例</span><span class="sxs-lookup"><span data-stu-id="c3996-107">Example</span></span>  
 <span data-ttu-id="c3996-108">次の例は、グループ結合の結果に対して <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> メソッドを使用し、左外部結合を実行する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="c3996-108">The following example demonstrates how to use the <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> method on the results of a group join to perform a left outer join.</span></span>  
  
 <span data-ttu-id="c3996-109">2 つのコレクションの左外部結合を作成するための最初のステップは、グループ結合を使用して内部結合を実行することです。</span><span class="sxs-lookup"><span data-stu-id="c3996-109">The first step in producing a left outer join of two collections is to perform an inner join by using a group join.</span></span> <span data-ttu-id="c3996-110">(このプロセスの詳細については、「[内部結合の実行](perform-inner-joins.md)」参照してください。)この例では、`Pet.Owner` に一致する `Person` オブジェクトに基づいて、`Person` オブジェクトの一覧が `Pet` オブジェクトの一覧に内部結合されています。</span><span class="sxs-lookup"><span data-stu-id="c3996-110">(See [Perform inner joins](perform-inner-joins.md) for an explanation of this process.) In this example, the list of `Person` objects is inner-joined to the list of `Pet` objects based on a `Person` object that matches `Pet.Owner`.</span></span>  
  
 <span data-ttu-id="c3996-111">2 つ目のステップは、最初 (左側) のコレクションの各要素を結果セットに含めることです。このとき、その要素と一致するものが右のコレクションにあるかどうかは考慮しません。</span><span class="sxs-lookup"><span data-stu-id="c3996-111">The second step is to include each element of the first (left) collection in the result set even if that element has no matches in the right collection.</span></span> <span data-ttu-id="c3996-112">これを行うには、グループ結合内の一致する要素の各シーケンスに対して、<xref:System.Linq.Enumerable.DefaultIfEmpty%2A> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c3996-112">This is accomplished by calling <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> on each sequence of matching elements from the group join.</span></span> <span data-ttu-id="c3996-113">この例では、`Pet` オブジェクトに一致する各シーケンスに対して、<xref:System.Linq.Enumerable.DefaultIfEmpty%2A> が呼び出されています。</span><span class="sxs-lookup"><span data-stu-id="c3996-113">In this example, <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> is called on each sequence of matching `Pet` objects.</span></span> <span data-ttu-id="c3996-114">このメソッドは、`Person` オブジェクトに対して一致する `Pet` オブジェクトのシーケンスが空である場合に、単一の既定値を含んだコレクションを返します。これにより、各 `Person` オブジェクトが結果コレクション内に表されることが保証されます。</span><span class="sxs-lookup"><span data-stu-id="c3996-114">The method returns a collection that contains a single, default value if the sequence of matching `Pet` objects is empty for any `Person` object, thereby ensuring that each `Person` object is represented in the result collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c3996-115">参照型の既定値は `null` です。そのためこのコード例では、各 `Pet` コレクションの各要素にアクセスする前に Null 参照がチェックされます。</span><span class="sxs-lookup"><span data-stu-id="c3996-115">The default value for a reference type is `null`; therefore, the example checks for a null reference before accessing each element of each `Pet` collection.</span></span>  
  
 <span data-ttu-id="c3996-116">[!code-cs[CsLINQProgJoining#7](../../../samples/snippets/csharp/concepts/linq/how-to-perform-left-outer-joins_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="c3996-116">[!code-cs[CsLINQProgJoining#7](../../../samples/snippets/csharp/concepts/linq/how-to-perform-left-outer-joins_1.cs)]</span></span>  
 
## <a name="see-also"></a><span data-ttu-id="c3996-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="c3996-117">See also</span></span>  
 <span data-ttu-id="c3996-118"><xref:System.Linq.Enumerable.Join%2A></span><span class="sxs-lookup"><span data-stu-id="c3996-118"><xref:System.Linq.Enumerable.Join%2A></span></span>   
 <span data-ttu-id="c3996-119"><xref:System.Linq.Enumerable.GroupJoin%2A></span><span class="sxs-lookup"><span data-stu-id="c3996-119"><xref:System.Linq.Enumerable.GroupJoin%2A></span></span>   
 <span data-ttu-id="c3996-120">[内部結合の実行](perform-inner-joins.md) </span><span class="sxs-lookup"><span data-stu-id="c3996-120">[Perform inner joins](perform-inner-joins.md) </span></span>  
 <span data-ttu-id="c3996-121">[グループ化結合の実行](perform-grouped-joins.md) </span><span class="sxs-lookup"><span data-stu-id="c3996-121">[Perform grouped joins](perform-grouped-joins.md) </span></span>  
 [<span data-ttu-id="c3996-122">匿名型</span><span class="sxs-lookup"><span data-stu-id="c3996-122">Anonymous types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)   
 

