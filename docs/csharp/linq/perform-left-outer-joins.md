---
title: 左外部結合の実行
description: '方法: 左外部結合を実行する。'
ms.date: 12/1/2016
ms.assetid: f542cee6-3169-4dcf-a631-3a6a79ccd473
ms.openlocfilehash: aacab1ac6f4ab2c10b393cf0b2c578a13d9b9306
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="perform-left-outer-joins"></a><span data-ttu-id="50eeb-103">左外部結合の実行</span><span class="sxs-lookup"><span data-stu-id="50eeb-103">Perform left outer joins</span></span>
<span data-ttu-id="50eeb-104">左外部結合は、最初のコレクションの各要素を、2 つ目のコレクション内にある要素との相関関係の有無にかかわらず返す結合です。</span><span class="sxs-lookup"><span data-stu-id="50eeb-104">A left outer join is a join in which each element of the first collection is returned, regardless of whether it has any correlated elements in the second collection.</span></span> <span data-ttu-id="50eeb-105">LINQ を使用すると、グループ結合の結果に対して <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> メソッドを呼び出すことで、左外部結合を実行できます。</span><span class="sxs-lookup"><span data-stu-id="50eeb-105">You can use LINQ to perform a left outer join by calling the <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> method on the results of a group join.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50eeb-106">例</span><span class="sxs-lookup"><span data-stu-id="50eeb-106">Example</span></span>  
 <span data-ttu-id="50eeb-107">次の例は、グループ結合の結果に対して <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> メソッドを使用し、左外部結合を実行する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="50eeb-107">The following example demonstrates how to use the <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> method on the results of a group join to perform a left outer join.</span></span>  
  
 <span data-ttu-id="50eeb-108">2 つのコレクションの左外部結合を作成するための最初のステップは、グループ結合を使用して内部結合を実行することです。</span><span class="sxs-lookup"><span data-stu-id="50eeb-108">The first step in producing a left outer join of two collections is to perform an inner join by using a group join.</span></span> <span data-ttu-id="50eeb-109">(このプロセスの詳細については、「[内部結合の実行](perform-inner-joins.md)」参照してください。)この例では、`Pet.Owner` に一致する `Person` オブジェクトに基づいて、`Person` オブジェクトの一覧が `Pet` オブジェクトの一覧に内部結合されています。</span><span class="sxs-lookup"><span data-stu-id="50eeb-109">(See [Perform inner joins](perform-inner-joins.md) for an explanation of this process.) In this example, the list of `Person` objects is inner-joined to the list of `Pet` objects based on a `Person` object that matches `Pet.Owner`.</span></span>  
  
 <span data-ttu-id="50eeb-110">2 つ目のステップは、最初 (左側) のコレクションの各要素を結果セットに含めることです。このとき、その要素と一致するものが右のコレクションにあるかどうかは考慮しません。</span><span class="sxs-lookup"><span data-stu-id="50eeb-110">The second step is to include each element of the first (left) collection in the result set even if that element has no matches in the right collection.</span></span> <span data-ttu-id="50eeb-111">これを行うには、グループ結合内の一致する要素の各シーケンスに対して、<xref:System.Linq.Enumerable.DefaultIfEmpty%2A> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="50eeb-111">This is accomplished by calling <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> on each sequence of matching elements from the group join.</span></span> <span data-ttu-id="50eeb-112">この例では、`Pet` オブジェクトに一致する各シーケンスに対して、<xref:System.Linq.Enumerable.DefaultIfEmpty%2A> が呼び出されています。</span><span class="sxs-lookup"><span data-stu-id="50eeb-112">In this example, <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> is called on each sequence of matching `Pet` objects.</span></span> <span data-ttu-id="50eeb-113">このメソッドは、`Person` オブジェクトに対して一致する `Pet` オブジェクトのシーケンスが空である場合に、単一の既定値を含んだコレクションを返します。これにより、各 `Person` オブジェクトが結果コレクション内に表されることが保証されます。</span><span class="sxs-lookup"><span data-stu-id="50eeb-113">The method returns a collection that contains a single, default value if the sequence of matching `Pet` objects is empty for any `Person` object, thereby ensuring that each `Person` object is represented in the result collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="50eeb-114">参照型の既定値は `null` です。そのためこのコード例では、各 `Pet` コレクションの各要素にアクセスする前に Null 参照がチェックされます。</span><span class="sxs-lookup"><span data-stu-id="50eeb-114">The default value for a reference type is `null`; therefore, the example checks for a null reference before accessing each element of each `Pet` collection.</span></span>  
  
 [!code-csharp[CsLINQProgJoining#7](../../../samples/snippets/csharp/concepts/linq/how-to-perform-left-outer-joins_1.cs)]  
 
## <a name="see-also"></a><span data-ttu-id="50eeb-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="50eeb-115">See also</span></span>  
 <xref:System.Linq.Enumerable.Join%2A>  
 <xref:System.Linq.Enumerable.GroupJoin%2A>  
 [<span data-ttu-id="50eeb-116">内部結合の実行</span><span class="sxs-lookup"><span data-stu-id="50eeb-116">Perform inner joins</span></span>](perform-inner-joins.md)  
 [<span data-ttu-id="50eeb-117">グループ化結合の実行</span><span class="sxs-lookup"><span data-stu-id="50eeb-117">Perform grouped joins</span></span>](perform-grouped-joins.md)  
 [<span data-ttu-id="50eeb-118">匿名型</span><span class="sxs-lookup"><span data-stu-id="50eeb-118">Anonymous types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)  
 
