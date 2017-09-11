---
title: "join 句 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- join
- join_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- join clause [C#]
- join keyword [C#]
ms.assetid: 76e9df84-092c-41a6-9537-c3f1cbd7f0fb
caps.latest.revision: 29
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
ms.openlocfilehash: 3368ba14101eda38ed8e3ee2bdc81bcab74a9b82
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="join-clause-c-reference"></a><span data-ttu-id="bf81b-102">join 句 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="bf81b-102">join clause (C# Reference)</span></span>
<span data-ttu-id="bf81b-103">`join` 句は、オブジェクト モデル内での直接リレーションシップがない、さまざまなソース シーケンスの要素を関連付ける際に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="bf81b-103">The `join` clause is useful for associating elements from different source sequences that have no direct relationship in the object model.</span></span> <span data-ttu-id="bf81b-104">唯一の要件は、等価性を比較できるいくつかの値が各ソース内の要素間で共有されていることです。</span><span class="sxs-lookup"><span data-stu-id="bf81b-104">The only requirement is that the elements in each source share some value that can be compared for equality.</span></span> <span data-ttu-id="bf81b-105">たとえば、食品販売会社には特定の商品についての供給元のリストと購入者のリストがあります。</span><span class="sxs-lookup"><span data-stu-id="bf81b-105">For example, a food distributor might have a list of suppliers of a certain product, and a list of buyers.</span></span> <span data-ttu-id="bf81b-106">`join` 句は、たとえば指定された地域のすべての供給元および購入者のリストを作成するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="bf81b-106">A `join` clause can be used, for example, to create a list of the suppliers and buyers of that product who are all in the same specified region.</span></span>  
  
 <span data-ttu-id="bf81b-107">`join` 句では、2 つのソース シーケンスを入力として受け取ります。</span><span class="sxs-lookup"><span data-stu-id="bf81b-107">A `join` clause takes two source sequences as input.</span></span> <span data-ttu-id="bf81b-108">各シーケンスの要素は、もう一方のシーケンスの対応するプロパティと比較できるプロパティであるか、そのプロパティを含む要素であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="bf81b-108">The elements in each sequence must either be or contain a property that can be compared to a corresponding property in the other sequence.</span></span> <span data-ttu-id="bf81b-109">`join` 句では、特殊な `equals` キーワードを使用して、指定されたキーの等価性が比較されます。</span><span class="sxs-lookup"><span data-stu-id="bf81b-109">The `join` clause compares the specified keys for equality by using the special `equals` keyword.</span></span> <span data-ttu-id="bf81b-110">`join` 句によって実行される結合はすべてが等結合です。</span><span class="sxs-lookup"><span data-stu-id="bf81b-110">All joins performed by the `join` clause are equijoins.</span></span> <span data-ttu-id="bf81b-111">`join` 句の出力形式は、実行する結合の種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="bf81b-111">The shape of the output of a `join` clause depends on the specific type of join you are performing.</span></span> <span data-ttu-id="bf81b-112">最も一般的な 3 種類の結合を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="bf81b-112">The following are three most common join types:</span></span>  
  
-   <span data-ttu-id="bf81b-113">内部結合</span><span class="sxs-lookup"><span data-stu-id="bf81b-113">Inner join</span></span>  
  
-   <span data-ttu-id="bf81b-114">グループ結合</span><span class="sxs-lookup"><span data-stu-id="bf81b-114">Group join</span></span>  
  
-   <span data-ttu-id="bf81b-115">左外部結合</span><span class="sxs-lookup"><span data-stu-id="bf81b-115">Left outer join</span></span>  
  
## <a name="inner-join"></a><span data-ttu-id="bf81b-116">内部結合</span><span class="sxs-lookup"><span data-stu-id="bf81b-116">Inner Join</span></span>  
 <span data-ttu-id="bf81b-117">次の例は、単純な内部等結合を示しています。</span><span class="sxs-lookup"><span data-stu-id="bf81b-117">The following example shows a simple inner equijoin.</span></span> <span data-ttu-id="bf81b-118">このクエリによって "商品名/カテゴリ" のペアからなるフラットなシーケンスが生成されます。</span><span class="sxs-lookup"><span data-stu-id="bf81b-118">This query produces a flat sequence of "product name / category" pairs.</span></span> <span data-ttu-id="bf81b-119">複数の要素に同じカテゴリ文字列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="bf81b-119">The same category string will appear in multiple elements.</span></span> <span data-ttu-id="bf81b-120">`categories` の要素に一致する `products` がない場合、そのカテゴリは結果に含まれません。</span><span class="sxs-lookup"><span data-stu-id="bf81b-120">If an element from `categories` has no matching `products`, that category will not appear in the results.</span></span>  
  
 <span data-ttu-id="bf81b-121">[!code-cs[cscsrefQueryKeywords#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="bf81b-121">[!code-cs[cscsrefQueryKeywords#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_1.cs)]</span></span>  
  
 <span data-ttu-id="bf81b-122">詳細については、「[方法: 内部結合を実行する](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bf81b-122">For more information, see [How to: Perform Inner Joins](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md).</span></span>  
  
## <a name="group-join"></a><span data-ttu-id="bf81b-123">Group Join</span><span class="sxs-lookup"><span data-stu-id="bf81b-123">Group Join</span></span>  
 <span data-ttu-id="bf81b-124">`into` 式を使用した `join` 句はグループ結合と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="bf81b-124">A `join` clause with an `into` expression is called a group join.</span></span>  
  
 <span data-ttu-id="bf81b-125">[!code-cs[cscsrefQueryKeywords#25](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="bf81b-125">[!code-cs[cscsrefQueryKeywords#25](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_2.cs)]</span></span>  
  
 <span data-ttu-id="bf81b-126">グループ結合によって生成される階層形式の結果シーケンスでは、左側のソース シーケンスの要素と一致する右側のソース シーケンスの 1 つ以上の要素が関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="bf81b-126">A group join produces a hierarchical result sequence, which associates elements in the left source sequence with one or more matching elements in the right side source sequence.</span></span> <span data-ttu-id="bf81b-127">リレーショナル データベースにおいてグループ結合に相当する用語はありません。グループ結合とは、本質的にはオブジェクト配列のシーケンスです。</span><span class="sxs-lookup"><span data-stu-id="bf81b-127">A group join has no equivalent in relational terms; it is essentially a sequence of object arrays.</span></span>  
  
 <span data-ttu-id="bf81b-128">右側のソース シーケンスの要素に左側のソースの要素と一致するものが見つからない場合は、その項目に対して `join` 句によって空の配列が生成されます。</span><span class="sxs-lookup"><span data-stu-id="bf81b-128">If no elements from the right source sequence are found to match an element in the left source, the `join` clause will produce an empty array for that item.</span></span> <span data-ttu-id="bf81b-129">つまりグループ結合は、結果シーケンスがグループに整理されることを除けば、基本的には内部等結合です。</span><span class="sxs-lookup"><span data-stu-id="bf81b-129">Therefore, the group join is still basically an inner-equijoin except that the result sequence is organized into groups.</span></span>  
  
 <span data-ttu-id="bf81b-130">グループ結合の結果を選択しただけでは、項目にアクセスすることはできでも、その照合に使用するキーを特定することはできません。</span><span class="sxs-lookup"><span data-stu-id="bf81b-130">If you just select the results of a group join, you can access the items, but you cannot identify the key that they match on.</span></span> <span data-ttu-id="bf81b-131">そのため、通常はグループ結合の結果を選択し、前の例に示したようなキー名を含む新しい型にするとさらに便利になります。</span><span class="sxs-lookup"><span data-stu-id="bf81b-131">Therefore, it is generally more useful to select the results of the group join into a new type that also has the key name, as shown in the previous example.</span></span>  
  
 <span data-ttu-id="bf81b-132">また、当然ながらグループ結合の結果を別のサブクエリのジェネレーターとして使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="bf81b-132">You can also, of course, use the result of a group join as the generator of another subquery:</span></span>  
  
 <span data-ttu-id="bf81b-133">[!code-cs[cscsrefQueryKeywords#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="bf81b-133">[!code-cs[cscsrefQueryKeywords#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_3.cs)]</span></span>  
  
 <span data-ttu-id="bf81b-134">詳細については、「[方法: グループ化結合を実行する](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bf81b-134">For more information, see [How to: Perform Grouped Joins](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md).</span></span>  
  
## <a name="left-outer-join"></a><span data-ttu-id="bf81b-135">左外部結合</span><span class="sxs-lookup"><span data-stu-id="bf81b-135">Left Outer Join</span></span>  
 <span data-ttu-id="bf81b-136">左外部結合では、右側のシーケンスに一致する要素がなくても、左側のソース シーケンスのすべての要素が返されます。</span><span class="sxs-lookup"><span data-stu-id="bf81b-136">In a left outer join, all the elements in the left source sequence are returned, even if no matching elements are in the right sequence.</span></span> <span data-ttu-id="bf81b-137">[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] で左外部結合を実行するには、`DefaultIfEmpty` メソッドとグループ結合を組み合わせて使用し、左側の要素に一致するものがない場合に既定の右側の要素を生成するように指定します。</span><span class="sxs-lookup"><span data-stu-id="bf81b-137">To perform a left outer join in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], use the `DefaultIfEmpty` method in combination with a group join to specify a default right-side element to produce if a left-side element has no matches.</span></span> <span data-ttu-id="bf81b-138">参照型用の既定値として `null` を使用するか、ユーザー定義の既定の型を指定できます。</span><span class="sxs-lookup"><span data-stu-id="bf81b-138">You can use `null` as the default value for any reference type, or you can specify a user-defined default type.</span></span> <span data-ttu-id="bf81b-139">次の例では、ユーザー定義の既定の型を示しています。</span><span class="sxs-lookup"><span data-stu-id="bf81b-139">In the following example, a user-defined default type is shown:</span></span>  
  
 <span data-ttu-id="bf81b-140">[!code-cs[cscsrefQueryKeywords#27](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="bf81b-140">[!code-cs[cscsrefQueryKeywords#27](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_4.cs)]</span></span>  
  
 <span data-ttu-id="bf81b-141">詳細については、「[方法: 左外部結合を実行する](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bf81b-141">For more information, see [How to: Perform Left Outer Joins](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md).</span></span>  
  
## <a name="the-equals-operator"></a><span data-ttu-id="bf81b-142">等値演算子</span><span class="sxs-lookup"><span data-stu-id="bf81b-142">The equals operator</span></span>  
 <span data-ttu-id="bf81b-143">`join` 句は等結合を実行します。</span><span class="sxs-lookup"><span data-stu-id="bf81b-143">A `join` clause performs an equijoin.</span></span> <span data-ttu-id="bf81b-144">つまり、基準にできるのは 2 つのキーの等価性に関する照合のみです。</span><span class="sxs-lookup"><span data-stu-id="bf81b-144">In other words, you can only base matches on the equality of two keys.</span></span> <span data-ttu-id="bf81b-145">"～より大きい" や "等しくない" など、他の種類の比較はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="bf81b-145">Other types of comparisons such as "greater than" or "not equals" are not supported.</span></span> <span data-ttu-id="bf81b-146">すべての結合が等結合であることを明確化するために、`join` 句では `==` 演算子ではなく `equals` キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="bf81b-146">To make clear that all joins are equijoins, the `join` clause uses the `equals` keyword instead of the `==` operator.</span></span> <span data-ttu-id="bf81b-147">`equals` キーワードは `join` 句でしか使用できず、また `==` 演算子とは 1 つの重要な点で異なります。</span><span class="sxs-lookup"><span data-stu-id="bf81b-147">The `equals` keyword can only be used in a `join` clause and it differs from the `==` operator in one important way.</span></span> <span data-ttu-id="bf81b-148">`equals` を指定すると、左側のキーでは外部のソース シーケンス、右側のキーでは内部のソースが使用されます。</span><span class="sxs-lookup"><span data-stu-id="bf81b-148">With `equals`, the left key consumes the outer source sequence, and the right key consumes the inner source.</span></span> <span data-ttu-id="bf81b-149">外部のソースは `equals` の左側のスコープ内、内部のソース シーケンスは右側のスコープ内でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="bf81b-149">The outer source is only in scope on the left side of `equals` and the inner source sequence is only in scope on the right side.</span></span>  
  
## <a name="non-equijoins"></a><span data-ttu-id="bf81b-150">非等結合</span><span class="sxs-lookup"><span data-stu-id="bf81b-150">Non-Equijoins</span></span>  
 <span data-ttu-id="bf81b-151">複数の `from` 句を使用して新しいシーケンスをクエリに個別に導入することで、非等結合、クロス結合、およびその他のカスタム結合操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="bf81b-151">You can perform non-equijoins, cross joins, and other custom join operations by using multiple `from` clauses to introduce new sequences independently into a query.</span></span> <span data-ttu-id="bf81b-152">詳細については、「[方法: カスタム結合操作を実行する](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-custom-join-operations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bf81b-152">For more information, see [How to: Perform Custom Join Operations](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-custom-join-operations.md).</span></span>  
  
## <a name="joins-on-object-collections-vs-relational-tables"></a><span data-ttu-id="bf81b-153">オブジェクト コレクションとリレーショナル テーブルでの結合の比較</span><span class="sxs-lookup"><span data-stu-id="bf81b-153">Joins on object collections vs. relational tables</span></span>  
 <span data-ttu-id="bf81b-154">[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリ式での結合操作は、オブジェクト コレクションに対して実行されます。</span><span class="sxs-lookup"><span data-stu-id="bf81b-154">In a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression, join operations are performed on object collections.</span></span> <span data-ttu-id="bf81b-155">2 つのリレーショナル テーブルの "結合" とまったく同じ方法でオブジェクト コレクションを結合することはできません。</span><span class="sxs-lookup"><span data-stu-id="bf81b-155">Object collections cannot be "joined" in exactly the same way as two relational tables.</span></span> <span data-ttu-id="bf81b-156">[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] では、2 つのソース シーケンスがリレーションシップによって関連付けられていない場合にのみ明示的な `join` 句が必要になります。</span><span class="sxs-lookup"><span data-stu-id="bf81b-156">In [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], explicit `join` clauses are only required when two source sequences are not tied by any relationship.</span></span> <span data-ttu-id="bf81b-157">[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] を使用する場合、外部キー テーブルはオブジェクト モデル内でプライマリ テーブルのプロパティとして表されます。</span><span class="sxs-lookup"><span data-stu-id="bf81b-157">When working with [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], foreign key tables are represented in the object model as properties of the primary table.</span></span> <span data-ttu-id="bf81b-158">たとえば Northwind データベースでは、Customer テーブルに Orders テーブルとの外部キー リレーションシップがあります。</span><span class="sxs-lookup"><span data-stu-id="bf81b-158">For example, in the Northwind database, the Customer table has a foreign key relationship with the Orders table.</span></span> <span data-ttu-id="bf81b-159">テーブルをオブジェクト モデルに割り当てると、Customer クラスには、その Customer に関連付けられた Orders のコレクションを含む Orders プロパティが含まれます。</span><span class="sxs-lookup"><span data-stu-id="bf81b-159">When you map the tables to the object model, the Customer class has an Orders property that contains the collection of Orders associated with that Customer.</span></span> <span data-ttu-id="bf81b-160">実質的には、既に結合が実行されていることになります。</span><span class="sxs-lookup"><span data-stu-id="bf81b-160">In effect, the join has already been done for you.</span></span>  
  
 <span data-ttu-id="bf81b-161">[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] を使用した関連テーブル間でのクエリの詳細については、「[方法: データベース リレーションシップを割り当てる](../../../framework/data/adonet/sql/linq/how-to-map-database-relationships.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bf81b-161">For more information about querying across related tables in the context of [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], see [How to: Map Database Relationships](../../../framework/data/adonet/sql/linq/how-to-map-database-relationships.md).</span></span>  
  
## <a name="composite-keys"></a><span data-ttu-id="bf81b-162">複合キー</span><span class="sxs-lookup"><span data-stu-id="bf81b-162">Composite Keys</span></span>  
 <span data-ttu-id="bf81b-163">複合キーを使用すると、複数の値の等価性をテストできます。</span><span class="sxs-lookup"><span data-stu-id="bf81b-163">You can test for equality of multiple values by using a composite key.</span></span> <span data-ttu-id="bf81b-164">詳細については、「[方法: 複合キーを使用して結合する](../../../csharp/programming-guide/linq-query-expressions/how-to-join-by-using-composite-keys.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bf81b-164">For more information, see [How to: Join by Using Composite Keys](../../../csharp/programming-guide/linq-query-expressions/how-to-join-by-using-composite-keys.md).</span></span> <span data-ttu-id="bf81b-165">複合キーは、`group` 句でも使用できます。</span><span class="sxs-lookup"><span data-stu-id="bf81b-165">Composite keys can be also used in a `group` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf81b-166">例</span><span class="sxs-lookup"><span data-stu-id="bf81b-166">Example</span></span>  
 <span data-ttu-id="bf81b-167">次の例では、同じ照合キーを使用し、同じデータ ソースでの内部結合、グループ結合、左外部結合の結果を比較しています。</span><span class="sxs-lookup"><span data-stu-id="bf81b-167">The following example compares the results of an inner join, a group join, and a left outer join on the same data sources by using the same matching keys.</span></span> <span data-ttu-id="bf81b-168">これらの例には、結果をコンソールにわかりやすく表示するためのコードがいくつか追加されています。</span><span class="sxs-lookup"><span data-stu-id="bf81b-168">Some extra code is added to these examples to clarify the results in the console display.</span></span>  
  
 <span data-ttu-id="bf81b-169">[!code-cs[cscsrefQueryKeywords#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="bf81b-169">[!code-cs[cscsrefQueryKeywords#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_5.cs)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf81b-170">コメント</span><span class="sxs-lookup"><span data-stu-id="bf81b-170">Remarks</span></span>  
 <span data-ttu-id="bf81b-171">`join` 句の後に `into` がない場合は、<xref:System.Linq.Enumerable.Join%2A> メソッド呼び出しに変換されます。</span><span class="sxs-lookup"><span data-stu-id="bf81b-171">A `join` clause that is not followed by `into` is translated into a <xref:System.Linq.Enumerable.Join%2A> method call.</span></span> <span data-ttu-id="bf81b-172">`join` 句の後に `into` がある場合は、<xref:System.Linq.Enumerable.GroupJoin%2A> メソッド呼び出しに変換されます。</span><span class="sxs-lookup"><span data-stu-id="bf81b-172">A `join` clause that is followed by `into` is translated to a <xref:System.Linq.Enumerable.GroupJoin%2A> method call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf81b-173">関連項目</span><span class="sxs-lookup"><span data-stu-id="bf81b-173">See Also</span></span>  
 <span data-ttu-id="bf81b-174">[クエリ キーワード (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="bf81b-174">[Query Keywords (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md) </span></span>  
 <span data-ttu-id="bf81b-175">[LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md) </span><span class="sxs-lookup"><span data-stu-id="bf81b-175">[LINQ Query Expressions](../../../csharp/programming-guide/linq-query-expressions/index.md) </span></span>  
 <span data-ttu-id="bf81b-176">[結合操作](http://msdn.microsoft.com/library/442d176d-028c-4beb-8d22-407d4ef89107) </span><span class="sxs-lookup"><span data-stu-id="bf81b-176">[Join Operations](http://msdn.microsoft.com/library/442d176d-028c-4beb-8d22-407d4ef89107) </span></span>  
 <span data-ttu-id="bf81b-177">[group 句](../../../csharp/language-reference/keywords/group-clause.md) </span><span class="sxs-lookup"><span data-stu-id="bf81b-177">[group clause](../../../csharp/language-reference/keywords/group-clause.md) </span></span>  
 <span data-ttu-id="bf81b-178">[方法: 左外部結合を実行する](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md) </span><span class="sxs-lookup"><span data-stu-id="bf81b-178">[How to: Perform Left Outer Joins](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md) </span></span>  
 <span data-ttu-id="bf81b-179">[方法: 内部結合を実行する](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md) </span><span class="sxs-lookup"><span data-stu-id="bf81b-179">[How to: Perform Inner Joins](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md) </span></span>  
 <span data-ttu-id="bf81b-180">[方法: グループ化結合を実行する](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md) </span><span class="sxs-lookup"><span data-stu-id="bf81b-180">[How to: Perform Grouped Joins](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md) </span></span>  
 <span data-ttu-id="bf81b-181">[方法: join 句の結果の順序を指定する](../../../csharp/programming-guide/linq-query-expressions/how-to-order-the-results-of-a-join-clause.md) </span><span class="sxs-lookup"><span data-stu-id="bf81b-181">[How to: Order the Results of a Join Clause](../../../csharp/programming-guide/linq-query-expressions/how-to-order-the-results-of-a-join-clause.md) </span></span>  
 <span data-ttu-id="bf81b-182">[方法: 複合キーを使用して結合する](../../../csharp/programming-guide/linq-query-expressions/how-to-join-by-using-composite-keys.md) </span><span class="sxs-lookup"><span data-stu-id="bf81b-182">[How to: Join by Using Composite Keys](../../../csharp/programming-guide/linq-query-expressions/how-to-join-by-using-composite-keys.md) </span></span>  
 [<span data-ttu-id="bf81b-183">方法 : サンプル データベースをインストールする</span><span class="sxs-lookup"><span data-stu-id="bf81b-183">How to: Install Sample Databases</span></span>](http://msdn.microsoft.com/library/ed1291f6-604c-4972-ae22-0345c6dea12e)

