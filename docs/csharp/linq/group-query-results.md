---
title: "クエリ結果のグループ化"
description: "結果をグループ化する方法です。"
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 2e4ec27f-06fb-4de7-8973-0189906d4520
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1c1639651699afbe5fb768db26b98a9b2d734315
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="group-query-results"></a><span data-ttu-id="8f47b-104">クエリ結果のグループ化</span><span class="sxs-lookup"><span data-stu-id="8f47b-104">Group query results</span></span>

<span data-ttu-id="8f47b-105">グループ化は、LINQ の最も強力な機能の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="8f47b-105">Grouping is one of the most powerful capabilities of LINQ.</span></span> <span data-ttu-id="8f47b-106">次の例では、さまざまな方法でデータをグループ化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8f47b-106">The following examples show how to group data in various ways:</span></span>  
  
-   <span data-ttu-id="8f47b-107">1 つのプロパティで。</span><span class="sxs-lookup"><span data-stu-id="8f47b-107">By a single property.</span></span>  
  
-   <span data-ttu-id="8f47b-108">文字列プロパティの最初の文字で。</span><span class="sxs-lookup"><span data-stu-id="8f47b-108">By the first letter of a string property.</span></span>  
  
-   <span data-ttu-id="8f47b-109">計算された数値の範囲で。</span><span class="sxs-lookup"><span data-stu-id="8f47b-109">By a computed numeric range.</span></span>  
  
-   <span data-ttu-id="8f47b-110">ブール述語またはその他の式で。</span><span class="sxs-lookup"><span data-stu-id="8f47b-110">By Boolean predicate or other expression.</span></span>  
  
-   <span data-ttu-id="8f47b-111">複合キーで。</span><span class="sxs-lookup"><span data-stu-id="8f47b-111">By a compound key.</span></span>  
  
 <span data-ttu-id="8f47b-112">さらに、最後の 2 つのクエリは、学生の名と姓だけを含む新しい匿名型に結果を射影します。</span><span class="sxs-lookup"><span data-stu-id="8f47b-112">In addition, the last two queries project their results into a new anonymous type that contains only the student's first and last name.</span></span> <span data-ttu-id="8f47b-113">詳しくは、「[group 句](../language-reference/keywords/group-clause.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8f47b-113">For more information, see the [group clause](../language-reference/keywords/group-clause.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f47b-114">例</span><span class="sxs-lookup"><span data-stu-id="8f47b-114">Example</span></span>  
 <span data-ttu-id="8f47b-115">このトピックのすべての例では、次のヘルパー クラスとデータ ソースを使います。</span><span class="sxs-lookup"><span data-stu-id="8f47b-115">All the examples in this topic use the following helper classes and data sources.</span></span>  
  
 <span data-ttu-id="8f47b-116">[!code-cs[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="8f47b-116">[!code-cs[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f47b-117">例</span><span class="sxs-lookup"><span data-stu-id="8f47b-117">Example</span></span>  
 <span data-ttu-id="8f47b-118">次の例では、要素の 1 つのプロパティをグループ化キーとして使って、ソース要素をグループ化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8f47b-118">The following example shows how to group source elements by using a single property of the element as the group key.</span></span> <span data-ttu-id="8f47b-119">この場合、キーは学生の姓である `string` です。</span><span class="sxs-lookup"><span data-stu-id="8f47b-119">In this case the key is a `string`, the student's last name.</span></span> <span data-ttu-id="8f47b-120">また、キーの部分文字列を使うこともできます。</span><span class="sxs-lookup"><span data-stu-id="8f47b-120">It is also possible to use a substring for the key.</span></span> <span data-ttu-id="8f47b-121">グループ化操作では、型の既定の等値比較子を使います。</span><span class="sxs-lookup"><span data-stu-id="8f47b-121">The grouping operation uses the default equality comparer for the type.</span></span>  
  
 <span data-ttu-id="8f47b-122">次のメソッドを `StudentClass` クラスに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="8f47b-122">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="8f47b-123">`Main` メソッドの呼び出しステートメントを `sc.GroupBySingleProperty()` に変更します。</span><span class="sxs-lookup"><span data-stu-id="8f47b-123">Change the calling statement in the `Main` method to `sc.GroupBySingleProperty()`.</span></span>  
  
 <span data-ttu-id="8f47b-124">[!code-cs[csProgGuideLINQ#17](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="8f47b-124">[!code-cs[csProgGuideLINQ#17](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_2.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f47b-125">例</span><span class="sxs-lookup"><span data-stu-id="8f47b-125">Example</span></span>  
 <span data-ttu-id="8f47b-126">次の例では、オブジェクトのプロパティ以外の何かをグループ化キーとして使って、ソース要素をグループ化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8f47b-126">The following example shows how to group source elements by using something other than a property of the object for the group key.</span></span> <span data-ttu-id="8f47b-127">この例では、キーは学生の姓の最初の文字です。</span><span class="sxs-lookup"><span data-stu-id="8f47b-127">In this example, the key is the first letter of the student's last name.</span></span>  
  
 <span data-ttu-id="8f47b-128">次のメソッドを `StudentClass` クラスに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="8f47b-128">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="8f47b-129">`Main` メソッドの呼び出しステートメントを `sc.GroupBySubstring()` に変更します。</span><span class="sxs-lookup"><span data-stu-id="8f47b-129">Change the calling statement in the `Main` method to `sc.GroupBySubstring()`.</span></span>  
  
 <span data-ttu-id="8f47b-130">[!code-cs[csProgGuideLINQ#18](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="8f47b-130">[!code-cs[csProgGuideLINQ#18](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_3.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f47b-131">例</span><span class="sxs-lookup"><span data-stu-id="8f47b-131">Example</span></span>  
 <span data-ttu-id="8f47b-132">次の例では、数値範囲をグループ化キーとして使って、ソース要素をグループ化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8f47b-132">The following example shows how to group source elements by using a numeric range as a group key.</span></span> <span data-ttu-id="8f47b-133">クエリは、名と姓および学生が属しているパーセンタイル範囲のみを含む匿名型に、結果を投影します。</span><span class="sxs-lookup"><span data-stu-id="8f47b-133">The query then projects the results into an anonymous type that contains only the first and last name and the percentile range to which the student belongs.</span></span> <span data-ttu-id="8f47b-134">匿名型を使っているのは、結果を表示するために完全な `Student` オブジェクトを使う必要がないためです。</span><span class="sxs-lookup"><span data-stu-id="8f47b-134">An anonymous type is used because it is not necessary to use the complete `Student` object to display the results.</span></span> <span data-ttu-id="8f47b-135">`GetPercentile` は、学生の平均スコアに基づいてパーセンタイルを計算するヘルパー関数です。</span><span class="sxs-lookup"><span data-stu-id="8f47b-135">`GetPercentile` is a helper function that calculates a percentile based on the student's average score.</span></span> <span data-ttu-id="8f47b-136">メソッドは、0 から 10 の間の整数を返します。</span><span class="sxs-lookup"><span data-stu-id="8f47b-136">The method returns an integer between 0 and 10.</span></span>  
  
 <span data-ttu-id="8f47b-137">[!code-cs[csProgGuideLINQ#50](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="8f47b-137">[!code-cs[csProgGuideLINQ#50](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_4.cs)]</span></span>  
  
 <span data-ttu-id="8f47b-138">次のメソッドを `StudentClass` クラスに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="8f47b-138">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="8f47b-139">`Main` メソッドの呼び出しステートメントを `sc.GroupByRange()` に変更します。</span><span class="sxs-lookup"><span data-stu-id="8f47b-139">Change the calling statement in the `Main` method to `sc.GroupByRange()`.</span></span>  
  
 <span data-ttu-id="8f47b-140">[!code-cs[csProgGuideLINQ#19](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="8f47b-140">[!code-cs[csProgGuideLINQ#19](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_5.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f47b-141">例</span><span class="sxs-lookup"><span data-stu-id="8f47b-141">Example</span></span>  
 <span data-ttu-id="8f47b-142">次の例では、ブール比較式を使って、ソース要素をグループ化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8f47b-142">The following example shows how to group source elements by using a Boolean comparison expression.</span></span> <span data-ttu-id="8f47b-143">この例のブール式は、学生の平均試験スコアが 75 より大きいかどうかをテストします。</span><span class="sxs-lookup"><span data-stu-id="8f47b-143">In this example, the Boolean expression tests whether a student's average exam score is greater than 75.</span></span> <span data-ttu-id="8f47b-144">前の例と同じように、完全なソース要素が必要ないため、結果を匿名型に投影します。</span><span class="sxs-lookup"><span data-stu-id="8f47b-144">As in previous examples, the results are projected into an anonymous type because the complete source element is not needed.</span></span> <span data-ttu-id="8f47b-145">匿名型のプロパティは `Key` メンバーのプロパティになり、クエリ実行時に名前でアクセスできることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="8f47b-145">Note that the properties in the anonymous type become properties on the `Key` member and can be accessed by name when the query is executed.</span></span>  
  
 <span data-ttu-id="8f47b-146">次のメソッドを `StudentClass` クラスに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="8f47b-146">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="8f47b-147">`Main` メソッドの呼び出しステートメントを `sc.GroupByBoolean()` に変更します。</span><span class="sxs-lookup"><span data-stu-id="8f47b-147">Change the calling statement in the `Main` method to `sc.GroupByBoolean()`.</span></span>  
  
 <span data-ttu-id="8f47b-148">[!code-cs[csProgGuideLINQ#20](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="8f47b-148">[!code-cs[csProgGuideLINQ#20](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_6.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f47b-149">例</span><span class="sxs-lookup"><span data-stu-id="8f47b-149">Example</span></span>  
 <span data-ttu-id="8f47b-150">次の例では、匿名型を使って、複数の値を含むキーをカプセル化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8f47b-150">The following example shows how to use an anonymous type to encapsulate a key that contains multiple values.</span></span> <span data-ttu-id="8f47b-151">この例では、最初のキーの値は学生の姓の最初の文字です。</span><span class="sxs-lookup"><span data-stu-id="8f47b-151">In this example, the first key value is the first letter of the student's last name.</span></span> <span data-ttu-id="8f47b-152">2 番目のキーの値は、最初の試験での学生のスコアが 85 より高いかどうかを示すブール値です。</span><span class="sxs-lookup"><span data-stu-id="8f47b-152">The second key value is a Boolean that specifies whether the student scored over 85 on the first exam.</span></span> <span data-ttu-id="8f47b-153">キーの任意のプロパティでグループを並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="8f47b-153">You can order the groups by any property in the key.</span></span>  
  
 <span data-ttu-id="8f47b-154">次のメソッドを `StudentClass` クラスに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="8f47b-154">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="8f47b-155">`Main` メソッドの呼び出しステートメントを `sc.GroupByCompositeKey()` に変更します。</span><span class="sxs-lookup"><span data-stu-id="8f47b-155">Change the calling statement in the `Main` method to `sc.GroupByCompositeKey()`.</span></span>  
  
 <span data-ttu-id="8f47b-156">[!code-cs[csProgGuideLINQ#21](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="8f47b-156">[!code-cs[csProgGuideLINQ#21](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_7.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f47b-157">関連項目</span><span class="sxs-lookup"><span data-stu-id="8f47b-157">See also</span></span>  
 <span data-ttu-id="8f47b-158"><xref:System.Linq.Enumerable.GroupBy%2A></span><span class="sxs-lookup"><span data-stu-id="8f47b-158"><xref:System.Linq.Enumerable.GroupBy%2A></span></span>   
 <span data-ttu-id="8f47b-159"><xref:System.Linq.IGrouping%602></span><span class="sxs-lookup"><span data-stu-id="8f47b-159"><xref:System.Linq.IGrouping%602></span></span>   
 <span data-ttu-id="8f47b-160">[LINQ クエリ式](index.md) </span><span class="sxs-lookup"><span data-stu-id="8f47b-160">[LINQ Query Expressions](index.md) </span></span>  
 <span data-ttu-id="8f47b-161">[group 句](../language-reference/keywords/group-clause.md) </span><span class="sxs-lookup"><span data-stu-id="8f47b-161">[group clause](../language-reference/keywords/group-clause.md) </span></span>  
 <span data-ttu-id="8f47b-162">[匿名型](../programming-guide/classes-and-structs/anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="8f47b-162">[Anonymous Types](../programming-guide/classes-and-structs/anonymous-types.md) </span></span>  
 <span data-ttu-id="8f47b-163">[グループ化操作でのサブクエリの実行](perform-a-subquery-on-a-grouping-operation.md) </span><span class="sxs-lookup"><span data-stu-id="8f47b-163">[Perform a Subquery on a Grouping Operation](perform-a-subquery-on-a-grouping-operation.md) </span></span>  
 <span data-ttu-id="8f47b-164">[入れ子になったグループの作成](create-a-nested-group.md) </span><span class="sxs-lookup"><span data-stu-id="8f47b-164">[Create a Nested Group](create-a-nested-group.md) </span></span>  
 [<span data-ttu-id="8f47b-165">データのグループ化</span><span class="sxs-lookup"><span data-stu-id="8f47b-165">Grouping Data</span></span>](../programming-guide/concepts/linq/grouping-data.md)

