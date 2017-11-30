---
title: "クエリ結果のグループ化"
description: "結果をグループ化する方法です。"
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 2e4ec27f-06fb-4de7-8973-0189906d4520
ms.openlocfilehash: ca68cf96a2c27bbd1999d5445c14fc93e8e2566c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="group-query-results"></a><span data-ttu-id="df2a4-104">クエリ結果のグループ化</span><span class="sxs-lookup"><span data-stu-id="df2a4-104">Group query results</span></span>

<span data-ttu-id="df2a4-105">グループ化は、LINQ の最も強力な機能の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="df2a4-105">Grouping is one of the most powerful capabilities of LINQ.</span></span> <span data-ttu-id="df2a4-106">次の例では、さまざまな方法でデータをグループ化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="df2a4-106">The following examples show how to group data in various ways:</span></span>  
  
-   <span data-ttu-id="df2a4-107">1 つのプロパティで。</span><span class="sxs-lookup"><span data-stu-id="df2a4-107">By a single property.</span></span>  
  
-   <span data-ttu-id="df2a4-108">文字列プロパティの最初の文字で。</span><span class="sxs-lookup"><span data-stu-id="df2a4-108">By the first letter of a string property.</span></span>  
  
-   <span data-ttu-id="df2a4-109">計算された数値の範囲で。</span><span class="sxs-lookup"><span data-stu-id="df2a4-109">By a computed numeric range.</span></span>  
  
-   <span data-ttu-id="df2a4-110">ブール述語またはその他の式で。</span><span class="sxs-lookup"><span data-stu-id="df2a4-110">By Boolean predicate or other expression.</span></span>  
  
-   <span data-ttu-id="df2a4-111">複合キーで。</span><span class="sxs-lookup"><span data-stu-id="df2a4-111">By a compound key.</span></span>  
  
 <span data-ttu-id="df2a4-112">さらに、最後の 2 つのクエリは、学生の名と姓だけを含む新しい匿名型に結果を射影します。</span><span class="sxs-lookup"><span data-stu-id="df2a4-112">In addition, the last two queries project their results into a new anonymous type that contains only the student's first and last name.</span></span> <span data-ttu-id="df2a4-113">詳しくは、「[group 句](../language-reference/keywords/group-clause.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="df2a4-113">For more information, see the [group clause](../language-reference/keywords/group-clause.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="df2a4-114">例</span><span class="sxs-lookup"><span data-stu-id="df2a4-114">Example</span></span>  
 <span data-ttu-id="df2a4-115">このトピックのすべての例では、次のヘルパー クラスとデータ ソースを使います。</span><span class="sxs-lookup"><span data-stu-id="df2a4-115">All the examples in this topic use the following helper classes and data sources.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="df2a4-116">例</span><span class="sxs-lookup"><span data-stu-id="df2a4-116">Example</span></span>  
 <span data-ttu-id="df2a4-117">次の例では、要素の 1 つのプロパティをグループ化キーとして使って、ソース要素をグループ化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="df2a4-117">The following example shows how to group source elements by using a single property of the element as the group key.</span></span> <span data-ttu-id="df2a4-118">この場合、キーは学生の姓である `string` です。</span><span class="sxs-lookup"><span data-stu-id="df2a4-118">In this case the key is a `string`, the student's last name.</span></span> <span data-ttu-id="df2a4-119">また、キーの部分文字列を使うこともできます。</span><span class="sxs-lookup"><span data-stu-id="df2a4-119">It is also possible to use a substring for the key.</span></span> <span data-ttu-id="df2a4-120">グループ化操作では、型の既定の等値比較子を使います。</span><span class="sxs-lookup"><span data-stu-id="df2a4-120">The grouping operation uses the default equality comparer for the type.</span></span>  
  
 <span data-ttu-id="df2a4-121">次のメソッドを `StudentClass` クラスに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="df2a4-121">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="df2a4-122">`Main` メソッドの呼び出しステートメントを `sc.GroupBySingleProperty()` に変更します。</span><span class="sxs-lookup"><span data-stu-id="df2a4-122">Change the calling statement in the `Main` method to `sc.GroupBySingleProperty()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#17](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="df2a4-123">例</span><span class="sxs-lookup"><span data-stu-id="df2a4-123">Example</span></span>  
 <span data-ttu-id="df2a4-124">次の例では、オブジェクトのプロパティ以外の何かをグループ化キーとして使って、ソース要素をグループ化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="df2a4-124">The following example shows how to group source elements by using something other than a property of the object for the group key.</span></span> <span data-ttu-id="df2a4-125">この例では、キーは学生の姓の最初の文字です。</span><span class="sxs-lookup"><span data-stu-id="df2a4-125">In this example, the key is the first letter of the student's last name.</span></span>  
  
 <span data-ttu-id="df2a4-126">次のメソッドを `StudentClass` クラスに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="df2a4-126">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="df2a4-127">`Main` メソッドの呼び出しステートメントを `sc.GroupBySubstring()` に変更します。</span><span class="sxs-lookup"><span data-stu-id="df2a4-127">Change the calling statement in the `Main` method to `sc.GroupBySubstring()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#18](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="df2a4-128">例</span><span class="sxs-lookup"><span data-stu-id="df2a4-128">Example</span></span>  
 <span data-ttu-id="df2a4-129">次の例では、数値範囲をグループ化キーとして使って、ソース要素をグループ化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="df2a4-129">The following example shows how to group source elements by using a numeric range as a group key.</span></span> <span data-ttu-id="df2a4-130">クエリは、名と姓および学生が属しているパーセンタイル範囲のみを含む匿名型に、結果を投影します。</span><span class="sxs-lookup"><span data-stu-id="df2a4-130">The query then projects the results into an anonymous type that contains only the first and last name and the percentile range to which the student belongs.</span></span> <span data-ttu-id="df2a4-131">匿名型を使っているのは、結果を表示するために完全な `Student` オブジェクトを使う必要がないためです。</span><span class="sxs-lookup"><span data-stu-id="df2a4-131">An anonymous type is used because it is not necessary to use the complete `Student` object to display the results.</span></span> <span data-ttu-id="df2a4-132">`GetPercentile` は、学生の平均スコアに基づいてパーセンタイルを計算するヘルパー関数です。</span><span class="sxs-lookup"><span data-stu-id="df2a4-132">`GetPercentile` is a helper function that calculates a percentile based on the student's average score.</span></span> <span data-ttu-id="df2a4-133">メソッドは、0 から 10 の間の整数を返します。</span><span class="sxs-lookup"><span data-stu-id="df2a4-133">The method returns an integer between 0 and 10.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#50](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_4.cs)]  
  
 <span data-ttu-id="df2a4-134">次のメソッドを `StudentClass` クラスに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="df2a4-134">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="df2a4-135">`Main` メソッドの呼び出しステートメントを `sc.GroupByRange()` に変更します。</span><span class="sxs-lookup"><span data-stu-id="df2a4-135">Change the calling statement in the `Main` method to `sc.GroupByRange()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#19](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_5.cs)]  
  
## <a name="example"></a><span data-ttu-id="df2a4-136">例</span><span class="sxs-lookup"><span data-stu-id="df2a4-136">Example</span></span>  
 <span data-ttu-id="df2a4-137">次の例では、ブール比較式を使って、ソース要素をグループ化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="df2a4-137">The following example shows how to group source elements by using a Boolean comparison expression.</span></span> <span data-ttu-id="df2a4-138">この例のブール式は、学生の平均試験スコアが 75 より大きいかどうかをテストします。</span><span class="sxs-lookup"><span data-stu-id="df2a4-138">In this example, the Boolean expression tests whether a student's average exam score is greater than 75.</span></span> <span data-ttu-id="df2a4-139">前の例と同じように、完全なソース要素が必要ないため、結果を匿名型に投影します。</span><span class="sxs-lookup"><span data-stu-id="df2a4-139">As in previous examples, the results are projected into an anonymous type because the complete source element is not needed.</span></span> <span data-ttu-id="df2a4-140">匿名型のプロパティは `Key` メンバーのプロパティになり、クエリ実行時に名前でアクセスできることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="df2a4-140">Note that the properties in the anonymous type become properties on the `Key` member and can be accessed by name when the query is executed.</span></span>  
  
 <span data-ttu-id="df2a4-141">次のメソッドを `StudentClass` クラスに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="df2a4-141">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="df2a4-142">`Main` メソッドの呼び出しステートメントを `sc.GroupByBoolean()` に変更します。</span><span class="sxs-lookup"><span data-stu-id="df2a4-142">Change the calling statement in the `Main` method to `sc.GroupByBoolean()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#20](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_6.cs)]  
  
## <a name="example"></a><span data-ttu-id="df2a4-143">例</span><span class="sxs-lookup"><span data-stu-id="df2a4-143">Example</span></span>  
 <span data-ttu-id="df2a4-144">次の例では、匿名型を使って、複数の値を含むキーをカプセル化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="df2a4-144">The following example shows how to use an anonymous type to encapsulate a key that contains multiple values.</span></span> <span data-ttu-id="df2a4-145">この例では、最初のキーの値は学生の姓の最初の文字です。</span><span class="sxs-lookup"><span data-stu-id="df2a4-145">In this example, the first key value is the first letter of the student's last name.</span></span> <span data-ttu-id="df2a4-146">2 番目のキーの値は、最初の試験での学生のスコアが 85 より高いかどうかを示すブール値です。</span><span class="sxs-lookup"><span data-stu-id="df2a4-146">The second key value is a Boolean that specifies whether the student scored over 85 on the first exam.</span></span> <span data-ttu-id="df2a4-147">キーの任意のプロパティでグループを並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="df2a4-147">You can order the groups by any property in the key.</span></span>  
  
 <span data-ttu-id="df2a4-148">次のメソッドを `StudentClass` クラスに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="df2a4-148">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="df2a4-149">`Main` メソッドの呼び出しステートメントを `sc.GroupByCompositeKey()` に変更します。</span><span class="sxs-lookup"><span data-stu-id="df2a4-149">Change the calling statement in the `Main` method to `sc.GroupByCompositeKey()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#21](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_7.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="df2a4-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="df2a4-150">See also</span></span>  
 <xref:System.Linq.Enumerable.GroupBy%2A>  
 <xref:System.Linq.IGrouping%602>  
 [<span data-ttu-id="df2a4-151">LINQ クエリ式</span><span class="sxs-lookup"><span data-stu-id="df2a4-151">LINQ Query Expressions</span></span>](index.md)  
 [<span data-ttu-id="df2a4-152">group 句</span><span class="sxs-lookup"><span data-stu-id="df2a4-152">group clause</span></span>](../language-reference/keywords/group-clause.md)  
 [<span data-ttu-id="df2a4-153">匿名型</span><span class="sxs-lookup"><span data-stu-id="df2a4-153">Anonymous Types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)  
 [<span data-ttu-id="df2a4-154">グループ化操作でサブクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="df2a4-154">Perform a Subquery on a Grouping Operation</span></span>](perform-a-subquery-on-a-grouping-operation.md)  
 [<span data-ttu-id="df2a4-155">入れ子になったグループを作成します。</span><span class="sxs-lookup"><span data-stu-id="df2a4-155">Create a Nested Group</span></span>](create-a-nested-group.md)  
 [<span data-ttu-id="df2a4-156">データのグループ化</span><span class="sxs-lookup"><span data-stu-id="df2a4-156">Grouping Data</span></span>](../programming-guide/concepts/linq/grouping-data.md)
