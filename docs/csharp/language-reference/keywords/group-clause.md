---
title: "group 句 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- group
- group_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- group keyword [C#]
- group clause [C#]
ms.assetid: c817242e-b12c-4baa-a57e-73ee138f34d1
caps.latest.revision: 24
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: afd32358a406b2797059cf2b8d85d897c8737222
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="group-clause-c-reference"></a><span data-ttu-id="59bb1-102">group 句 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="59bb1-102">group clause (C# Reference)</span></span>
<span data-ttu-id="59bb1-103">`group` 句は、グループのキー値に一致する 0 個以上の項目を含む <xref:System.Linq.IGrouping%602> オブジェクトのシーケンスを返します。</span><span class="sxs-lookup"><span data-stu-id="59bb1-103">The `group` clause returns a sequence of <xref:System.Linq.IGrouping%602> objects that contain zero or more items that match the key value for the group.</span></span> <span data-ttu-id="59bb1-104">たとえば、各文字列の最初の文字に基づいて文字列のシーケンスをグループ化することができます。</span><span class="sxs-lookup"><span data-stu-id="59bb1-104">For example, you can group a sequence of strings according to the first letter in each string.</span></span> <span data-ttu-id="59bb1-105">この場合、最初の文字がキーで、型は [char](../../../csharp/language-reference/keywords/char.md) であり、各 <xref:System.Linq.IGrouping%602> オブジェクトの `Key` プロパティに格納されています。</span><span class="sxs-lookup"><span data-stu-id="59bb1-105">In this case, the first letter is the key and has a type [char](../../../csharp/language-reference/keywords/char.md), and is stored in the `Key` property of each <xref:System.Linq.IGrouping%602> object.</span></span> <span data-ttu-id="59bb1-106">コンパイラは、キーの型を推論します。</span><span class="sxs-lookup"><span data-stu-id="59bb1-106">The compiler infers the type of the key.</span></span>  
  
 <span data-ttu-id="59bb1-107">次の例で示すように、クエリ式は `group` 句で終了できます。</span><span class="sxs-lookup"><span data-stu-id="59bb1-107">You can end a query expression with a `group` clause, as shown in the following example:</span></span>  
  
 <span data-ttu-id="59bb1-108">[!code-cs[cscsrefQueryKeywords#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="59bb1-108">[!code-cs[cscsrefQueryKeywords#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_1.cs)]</span></span>  
  
 <span data-ttu-id="59bb1-109">各グループで追加のクエリ操作を実行する場合、[into](../../../csharp/language-reference/keywords/into.md) コンテキスト キーワードを使用して一時的な識別子を指定できます。</span><span class="sxs-lookup"><span data-stu-id="59bb1-109">If you want to perform additional query operations on each group, you can specify a temporary identifier by using the [into](../../../csharp/language-reference/keywords/into.md) contextual keyword.</span></span> <span data-ttu-id="59bb1-110">`into` を使用する場合、次の抜粋に示すように、クエリを続行し、最終的には `select` ステートメントまたは別の `group` 句でそれを終了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="59bb1-110">When you use `into`, you must continue with the query, and eventually end it with either a `select` statement or another `group` clause, as shown in the following excerpt:</span></span>  
  
 <span data-ttu-id="59bb1-111">[!code-cs[cscsrefQueryKeywords#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="59bb1-111">[!code-cs[cscsrefQueryKeywords#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_2.cs)]</span></span>  
  
 <span data-ttu-id="59bb1-112">このトピックの「例」のセクションでは、`into` を含む場合と含まない場合の `group` の使用方法の完全な例があります。</span><span class="sxs-lookup"><span data-stu-id="59bb1-112">More complete examples of the use of `group` with and without `into` are provided in the Example section of this topic.</span></span>  
  
## <a name="enumerating-the-results-of-a-group-query"></a><span data-ttu-id="59bb1-113">グループ クエリの結果を列挙する</span><span class="sxs-lookup"><span data-stu-id="59bb1-113">Enumerating the Results of a Group Query</span></span>  
 <span data-ttu-id="59bb1-114">`group` クエリによって生成される <xref:System.Linq.IGrouping%602> オブジェクトは基本的には、リストのリストであるため、各グループのアイテムにアクセスするには、入れ子になった [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ループを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="59bb1-114">Because the <xref:System.Linq.IGrouping%602> objects produced by a `group` query are essentially a list of lists, you must use a nested [foreach](../../../csharp/language-reference/keywords/foreach-in.md) loop to access the items in each group.</span></span> <span data-ttu-id="59bb1-115">外側のループがグループ キーを反復処理し、内側のループがグループ自体の各項目を反復処理します。</span><span class="sxs-lookup"><span data-stu-id="59bb1-115">The outer loop iterates over the group keys, and the inner loop iterates over each item in the group itself.</span></span> <span data-ttu-id="59bb1-116">グループには、キーがある場合はありますが、要素はありません。</span><span class="sxs-lookup"><span data-stu-id="59bb1-116">A group may have a key but no elements.</span></span> <span data-ttu-id="59bb1-117">次に、前のコード例でクエリを実行する `foreach` ループを示します。</span><span class="sxs-lookup"><span data-stu-id="59bb1-117">The following is the `foreach` loop that executes the query in the previous code examples:</span></span>  
  
 <span data-ttu-id="59bb1-118">[!code-cs[cscsrefQueryKeywords#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="59bb1-118">[!code-cs[cscsrefQueryKeywords#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_3.cs)]</span></span>  
  
## <a name="key-types"></a><span data-ttu-id="59bb1-119">キーの種類</span><span class="sxs-lookup"><span data-stu-id="59bb1-119">Key Types</span></span>  
 <span data-ttu-id="59bb1-120">グループ キーは、文字列、組み込みの数値型、またはユーザー定義の名前付きの型または匿名型など、任意の型にすることができます。</span><span class="sxs-lookup"><span data-stu-id="59bb1-120">Group keys can be any type, such as a string, a built-in numeric type, or a user-defined named type or anonymous type.</span></span>  
  
### <a name="grouping-by-string"></a><span data-ttu-id="59bb1-121">文字列でグループ化する</span><span class="sxs-lookup"><span data-stu-id="59bb1-121">Grouping by string</span></span>  
 <span data-ttu-id="59bb1-122">前のコード例では、`char` を使用していました。</span><span class="sxs-lookup"><span data-stu-id="59bb1-122">The previous code examples used a `char`.</span></span> <span data-ttu-id="59bb1-123">姓を完全に指定するなど、簡単に代わりに文字列のキーを指定できます。</span><span class="sxs-lookup"><span data-stu-id="59bb1-123">A string key could easily have been specified instead, for example the complete last name:</span></span>  
  
 <span data-ttu-id="59bb1-124">[!code-cs[cscsrefQueryKeywords#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="59bb1-124">[!code-cs[cscsrefQueryKeywords#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_4.cs)]</span></span>  
  
### <a name="grouping-by-bool"></a><span data-ttu-id="59bb1-125">ブールでグループ化する</span><span class="sxs-lookup"><span data-stu-id="59bb1-125">Grouping by bool</span></span>  
 <span data-ttu-id="59bb1-126">次の例では、結果を 2 つのグループに分割するためのキー用のブール値の用途を示します。</span><span class="sxs-lookup"><span data-stu-id="59bb1-126">The following example shows the use of a bool value for a key to divide the results into two groups.</span></span> <span data-ttu-id="59bb1-127">値は `group` 句のサブ式で生成されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="59bb1-127">Note that the value is produced by a sub-expression in the `group` clause.</span></span>  
  
 <span data-ttu-id="59bb1-128">[!code-cs[cscsrefQueryKeywords#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="59bb1-128">[!code-cs[cscsrefQueryKeywords#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_5.cs)]</span></span>  
  
### <a name="grouping-by-numeric-range"></a><span data-ttu-id="59bb1-129">数値の範囲でグループ化する</span><span class="sxs-lookup"><span data-stu-id="59bb1-129">Grouping by numeric range</span></span>  
 <span data-ttu-id="59bb1-130">次の例では、パーセンタイルの範囲を示す数値のグループ キーを作成する式を使用しています。</span><span class="sxs-lookup"><span data-stu-id="59bb1-130">The next example uses an expression to create numeric group keys that represent a percentile range.</span></span> <span data-ttu-id="59bb1-131">`group` 句でメソッドを 2 度呼び出さなくて済むように、メソッド呼び出しの結果を格納する便利な場所として [let](../../../csharp/language-reference/keywords/let-clause.md) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="59bb1-131">Note the use of [let](../../../csharp/language-reference/keywords/let-clause.md) as a convenient location to store a method call result, so that you do not have to call the method two times in the `group` clause.</span></span> <span data-ttu-id="59bb1-132">また、0 除算の例外を避けるために、受講者の平均が 0 でないことがコードの `group` 句で確認されています。</span><span class="sxs-lookup"><span data-stu-id="59bb1-132">Note also in the `group` clause that to avoid a "divide by zero" exception the code checks to make sure that the student does not have an average of zero.</span></span> <span data-ttu-id="59bb1-133">クエリ式でメソッドを安全に使用する方法の詳細については、「[方法: クエリ式の例外を処理する](../../../csharp/programming-guide/linq-query-expressions/how-to-handle-exceptions-in-query-expressions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59bb1-133">For more information about how to safely use methods in query expressions, see [How to: Handle Exceptions in Query Expressions](../../../csharp/programming-guide/linq-query-expressions/how-to-handle-exceptions-in-query-expressions.md).</span></span>  
  
 <span data-ttu-id="59bb1-134">[!code-cs[cscsrefQueryKeywords#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="59bb1-134">[!code-cs[cscsrefQueryKeywords#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_6.cs)]</span></span>  
  
### <a name="grouping-by-composite-keys"></a><span data-ttu-id="59bb1-135">複合キーでグループ化する</span><span class="sxs-lookup"><span data-stu-id="59bb1-135">Grouping by Composite Keys</span></span>  
 <span data-ttu-id="59bb1-136">1 つ以上のキーを使用して要素をグループ化するには、複合キーを使用します。</span><span class="sxs-lookup"><span data-stu-id="59bb1-136">Use a composite key when you want to group elements according to more than one key.</span></span> <span data-ttu-id="59bb1-137">複合キーは、キー要素を保持する、匿名型または名前付きの型を使用して作成できます。</span><span class="sxs-lookup"><span data-stu-id="59bb1-137">You create a composite key by using an anonymous type or a named type to hold the key element.</span></span> <span data-ttu-id="59bb1-138">次の例では、クラス `Person` が、`surname` と `city` という名前のメンバーで宣言されていると想定しています。</span><span class="sxs-lookup"><span data-stu-id="59bb1-138">In the following example, assume that a class `Person` has been declared with members named `surname` and `city`.</span></span> <span data-ttu-id="59bb1-139">`group` 句により、同じ名前と同じ市の人物のセットごとに、別のグループが作成されます。</span><span class="sxs-lookup"><span data-stu-id="59bb1-139">The `group` clause causes a separate group to be created for each set of persons with the same last name and the same city.</span></span>  
  
```csharp  
group person by new {name = person.surname, city = person.city};  
```  
  
 <span data-ttu-id="59bb1-140">クエリ変数を別のメソッドに渡す場合には、名前付きの型を使用します。</span><span class="sxs-lookup"><span data-stu-id="59bb1-140">Use a named type if you must pass the query variable to another method.</span></span> <span data-ttu-id="59bb1-141">キーの自動実装プロパティを使用して特殊クラスを作成し、<xref:System.Object.Equals%2A> メソッドと <xref:System.Object.GetHashCode%2A> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="59bb1-141">Create a special class using auto-implemented properties for the keys, and then override the <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> methods.</span></span> <span data-ttu-id="59bb1-142">これらのメソッドを厳密にオーバーライドする必要がない構造体を使用することも可能です。</span><span class="sxs-lookup"><span data-stu-id="59bb1-142">You can also use a struct, in which case you do not strictly have to override those methods.</span></span> <span data-ttu-id="59bb1-143">詳細については、「[方法 : 自動実装するプロパティを使用して簡易クラスを実装する](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md)」と「[Query for Duplicate Files in a Directory Tree](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)」 (方法: ディレクトリ ツリーで重複するファイルを問い合わせる) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59bb1-143">For more information see [How to: Implement a Lightweight Class with Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) and [How to: Query for Duplicate Files in a Directory Tree](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md).</span></span> <span data-ttu-id="59bb1-144">後述のトピックには、名前付きの型を複合キーで使用する方法のコード例があります。</span><span class="sxs-lookup"><span data-stu-id="59bb1-144">The latter topic has a code example that demonstrates how to use a composite key with a named type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59bb1-145">例</span><span class="sxs-lookup"><span data-stu-id="59bb1-145">Example</span></span>  
 <span data-ttu-id="59bb1-146">次の例では、グループにその他のクエリ ロジックが適用されていない場合、ソース データをグループに並べる標準的なパターンを示します。</span><span class="sxs-lookup"><span data-stu-id="59bb1-146">The following example shows the standard pattern for ordering source data into groups when no additional query logic is applied to the groups.</span></span> <span data-ttu-id="59bb1-147">これは連結なしのグループ化と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="59bb1-147">This is called a grouping without a continuation.</span></span> <span data-ttu-id="59bb1-148">文字列の配列の要素は、最初の文字でグループ化されます。</span><span class="sxs-lookup"><span data-stu-id="59bb1-148">The elements in an array of strings are grouped according to their first letter.</span></span> <span data-ttu-id="59bb1-149">クエリの結果は、型 `char` のパブリック `Key` プロパティを含む <xref:System.Linq.IGrouping%602> 型とグループに各項目を含む <xref:System.Collections.Generic.IEnumerable%601> コレクションです。</span><span class="sxs-lookup"><span data-stu-id="59bb1-149">The result of the query is an <xref:System.Linq.IGrouping%602> type that contains a public `Key` property of type `char` and an <xref:System.Collections.Generic.IEnumerable%601> collection that contains each item in the grouping.</span></span>  
  
 <span data-ttu-id="59bb1-150">`group` 句の結果は、シーケンスのシーケンスです。</span><span class="sxs-lookup"><span data-stu-id="59bb1-150">The result of a `group` clause is a sequence of sequences.</span></span> <span data-ttu-id="59bb1-151">そのため、返される各グループ内の各要素にアクセスするには、次の例のように、グループ キーを反復処理するループ内で入れ子になった `foreach` ループを使用します。</span><span class="sxs-lookup"><span data-stu-id="59bb1-151">Therefore, to access the individual elements within each returned group, use a nested `foreach` loop inside the loop that iterates the group keys, as shown in the following example.</span></span>  
  
 <span data-ttu-id="59bb1-152">[!code-cs[cscsrefQueryKeywords#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="59bb1-152">[!code-cs[cscsrefQueryKeywords#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_7.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="59bb1-153">例</span><span class="sxs-lookup"><span data-stu-id="59bb1-153">Example</span></span>  
 <span data-ttu-id="59bb1-154">この例では、作成後に、`into` と共に *continuation* を使用し、グループに追加のロジックを実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="59bb1-154">This example shows how to perform additional logic on the groups after you have created them, by using a *continuation* with `into`.</span></span> <span data-ttu-id="59bb1-155">詳しくは、「[into](../../../csharp/language-reference/keywords/into.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="59bb1-155">For more information, see [into](../../../csharp/language-reference/keywords/into.md).</span></span> <span data-ttu-id="59bb1-156">次の例では、キー値が母音であるものだけを選択するために各グループに問い合せを行います。</span><span class="sxs-lookup"><span data-stu-id="59bb1-156">The following example queries each group to select only those whose key value is a vowel.</span></span>  
  
 <span data-ttu-id="59bb1-157">[!code-cs[cscsrefQueryKeywords#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_8.cs)]</span><span class="sxs-lookup"><span data-stu-id="59bb1-157">[!code-cs[cscsrefQueryKeywords#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_8.cs)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59bb1-158">コメント</span><span class="sxs-lookup"><span data-stu-id="59bb1-158">Remarks</span></span>  
 <span data-ttu-id="59bb1-159">コンパイル時に `group` 句が <xref:System.Linq.Enumerable.GroupBy%2A> メソッドの呼び出しに変換されます。</span><span class="sxs-lookup"><span data-stu-id="59bb1-159">At compile time, `group` clauses are translated into calls to the <xref:System.Linq.Enumerable.GroupBy%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59bb1-160">関連項目</span><span class="sxs-lookup"><span data-stu-id="59bb1-160">See Also</span></span>  
 <span data-ttu-id="59bb1-161"><xref:System.Linq.IGrouping%602></span><span class="sxs-lookup"><span data-stu-id="59bb1-161"><xref:System.Linq.IGrouping%602></span></span>   
 <span data-ttu-id="59bb1-162"><xref:System.Linq.Enumerable.GroupBy%2A></span><span class="sxs-lookup"><span data-stu-id="59bb1-162"><xref:System.Linq.Enumerable.GroupBy%2A></span></span>   
 <span data-ttu-id="59bb1-163"><xref:System.Linq.Enumerable.ThenBy%2A></span><span class="sxs-lookup"><span data-stu-id="59bb1-163"><xref:System.Linq.Enumerable.ThenBy%2A></span></span>   
 <span data-ttu-id="59bb1-164"><xref:System.Linq.Enumerable.ThenByDescending%2A></span><span class="sxs-lookup"><span data-stu-id="59bb1-164"><xref:System.Linq.Enumerable.ThenByDescending%2A></span></span>   
 <span data-ttu-id="59bb1-165">[クエリ キーワード (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="59bb1-165">[Query Keywords (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md) </span></span>  
 <span data-ttu-id="59bb1-166">[LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md) </span><span class="sxs-lookup"><span data-stu-id="59bb1-166">[LINQ Query Expressions](../../../csharp/programming-guide/linq-query-expressions/index.md) </span></span>  
 <span data-ttu-id="59bb1-167">[方法: 入れ子になったグループを作成する](../../../csharp/programming-guide/linq-query-expressions/how-to-create-a-nested-group.md) </span><span class="sxs-lookup"><span data-stu-id="59bb1-167">[How to: Create a Nested Group](../../../csharp/programming-guide/linq-query-expressions/how-to-create-a-nested-group.md) </span></span>  
 <span data-ttu-id="59bb1-168">[方法: クエリ結果をグループ化する](../../../csharp/programming-guide/linq-query-expressions/how-to-group-query-results.md) </span><span class="sxs-lookup"><span data-stu-id="59bb1-168">[How to: Group Query Results](../../../csharp/programming-guide/linq-query-expressions/how-to-group-query-results.md) </span></span>  
 [<span data-ttu-id="59bb1-169">方法: グループ化操作でサブクエリを実行する</span><span class="sxs-lookup"><span data-stu-id="59bb1-169">How to: Perform a Subquery on a Grouping Operation</span></span>](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md)

