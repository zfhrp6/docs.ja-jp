---
title: LINQ クエリの基本操作 (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- orderby clause [LINQ in C#]
- ordering data [LINQ in C#]
- selecting data [LINQ in C#]
- queries [LINQ in C#], basic operations
- grouping data [LINQ in C#]
- data sources [LINQ in C#]
- sorting data [LINQ in C#]
- projections [LINQ in C#]
- filtering data [LINQ in C#]
- joining data [LINQ in C#]
- select clause [LINQ in C#]
- LINQ [C#], basic query operations
- join clause [LINQ in C#]
- group clause [LINQ in C#]
ms.assetid: a7ea3421-1cf4-4df7-832a-aa22fe6379e9
ms.openlocfilehash: 2825b79c9638fff050522da43184a8d95a3fe02f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333041"
---
# <a name="basic-linq-query-operations-c"></a><span data-ttu-id="73163-102">LINQ クエリの基本操作 (C#)</span><span class="sxs-lookup"><span data-stu-id="73163-102">Basic LINQ Query Operations (C#)</span></span>
<span data-ttu-id="73163-103">このトピックでは、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリ式とクエリで実行する一般的な操作について、簡単に説明します。</span><span class="sxs-lookup"><span data-stu-id="73163-103">This topic gives a brief introduction to [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions and some of the typical kinds of operations that you perform in a query.</span></span> <span data-ttu-id="73163-104">詳細については、以下のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="73163-104">More detailed information is in the following topics:</span></span>  
  
 [<span data-ttu-id="73163-105">LINQ クエリ式</span><span class="sxs-lookup"><span data-stu-id="73163-105">LINQ Query Expressions</span></span>](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
  
 [<span data-ttu-id="73163-106">標準クエリ演算子の概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="73163-106">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
  
 [<span data-ttu-id="73163-107">チュートリアル: C# でのクエリの作成</span><span class="sxs-lookup"><span data-stu-id="73163-107">Walkthrough: Writing Queries in C#</span></span>](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)  
  
> [!NOTE]
>  <span data-ttu-id="73163-108">既に SQL や XQuery などのクエリ言語に精通している場合は、このトピックの大部分を省略できます。</span><span class="sxs-lookup"><span data-stu-id="73163-108">If you already are familiar with a query language such as SQL or XQuery, you can skip most of this topic.</span></span> <span data-ttu-id="73163-109">[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリ式における句の順序について理解するには、次のセクションの "`from` 句" を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73163-109">Read about the "`from` clause" in the next section to learn about the order of clauses in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span>  
  
## <a name="obtaining-a-data-source"></a><span data-ttu-id="73163-110">データ ソースの取得</span><span class="sxs-lookup"><span data-stu-id="73163-110">Obtaining a Data Source</span></span>  
 <span data-ttu-id="73163-111">[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリで必要な最初の手順は、データ ソースを指定することです。</span><span class="sxs-lookup"><span data-stu-id="73163-111">In a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, the first step is to specify the data source.</span></span> <span data-ttu-id="73163-112">ほとんどのプログラミング言語と同じように、C# でも、変数を使用する前に宣言しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="73163-112">In C# as in most programming languages a variable must be declared before it can be used.</span></span> <span data-ttu-id="73163-113">[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリでは、データ ソース (`customers`) および*範囲変数*(`cust`)を導入するために `from` 句が最初に使用されます。</span><span class="sxs-lookup"><span data-stu-id="73163-113">In a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, the `from` clause comes first in order to introduce the data source (`customers`) and the *range variable* (`cust`).</span></span>  
  
 [!code-csharp[csLINQGettingStarted#23](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_1.cs)]  
  
 <span data-ttu-id="73163-114">範囲変数は、`foreach`ループの反復変数と似ていますが、クエリ式では実際の反復は発生しません。</span><span class="sxs-lookup"><span data-stu-id="73163-114">The range variable is like the iteration variable in a `foreach` loop except that no actual iteration occurs in a query expression.</span></span> <span data-ttu-id="73163-115">クエリが実行されると、範囲変数は `customers` の連続する各要素への参照として機能します。</span><span class="sxs-lookup"><span data-stu-id="73163-115">When the query is executed, the range variable will serve as a reference to each successive element in `customers`.</span></span> <span data-ttu-id="73163-116">`cust` の型はコンパイラで推論できるため、明示的に指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="73163-116">Because the compiler can infer the type of `cust`, you do not have to specify it explicitly.</span></span> <span data-ttu-id="73163-117">追加の範囲変数は、`let` 句で導入できます。</span><span class="sxs-lookup"><span data-stu-id="73163-117">Additional range variables can be introduced by a `let` clause.</span></span> <span data-ttu-id="73163-118">詳しくは、「[let 句](../../../../csharp/language-reference/keywords/let-clause.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="73163-118">For more information, see [let clause](../../../../csharp/language-reference/keywords/let-clause.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="73163-119"><xref:System.Collections.ArrayList> などの非ジェネリック データ ソースの場合は、範囲変数を明示的に型指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="73163-119">For non-generic data sources such as <xref:System.Collections.ArrayList>, the range variable must be explicitly typed.</span></span> <span data-ttu-id="73163-120">詳細については、「[方法: LINQ を使用して ArrayList を照会する (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)」および「[from 句](../../../../csharp/language-reference/keywords/from-clause.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73163-120">For more information, see [How to: Query an ArrayList with LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md) and [from clause](../../../../csharp/language-reference/keywords/from-clause.md).</span></span>  
  
## <a name="filtering"></a><span data-ttu-id="73163-121">フィルター処理</span><span class="sxs-lookup"><span data-stu-id="73163-121">Filtering</span></span>  
 <span data-ttu-id="73163-122">最も一般的なクエリ操作は、ブール式の形式でフィルターを適用することです。</span><span class="sxs-lookup"><span data-stu-id="73163-122">Probably the most common query operation is to apply a filter in the form of a Boolean expression.</span></span> <span data-ttu-id="73163-123">クエリにフィルターを使用すると、式の条件に該当する要素だけがクエリから返されます。</span><span class="sxs-lookup"><span data-stu-id="73163-123">The filter causes the query to return only those elements for which the expression is true.</span></span> <span data-ttu-id="73163-124">結果は、`where` 句を使って生成されます。</span><span class="sxs-lookup"><span data-stu-id="73163-124">The result is produced by using the `where` clause.</span></span> <span data-ttu-id="73163-125">フィルターは、実質的にはソース シーケンスから除外する要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="73163-125">The filter in effect specifies which elements to exclude from the source sequence.</span></span> <span data-ttu-id="73163-126">次の例では、住所がロンドンにある `customers` だけが返されます。</span><span class="sxs-lookup"><span data-stu-id="73163-126">In the following example, only those `customers` who have an address in London are returned.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#24](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_2.cs)]  
  
 <span data-ttu-id="73163-127">使い慣れた C# 論理 `AND` 演算子と論理 `OR` 演算子を使用すると、必要なだけのフィルター式を `where` 句に適用できます。</span><span class="sxs-lookup"><span data-stu-id="73163-127">You can use the familiar C# logical `AND` and `OR` operators to apply as many filter expressions as necessary in the `where` clause.</span></span> <span data-ttu-id="73163-128">たとえば、住所が "London" にあり、かつ (`AND`) 名前が "Devon" の顧客だけを返すには、次のコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="73163-128">For example, to return only customers from "London" `AND` whose name is "Devon" you would write the following code:</span></span>  
  
 [!code-csharp[csLINQGettingStarted#25](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_3.cs)]  
  
 <span data-ttu-id="73163-129">住所がロンドンまたはパリにある顧客を返すには、次のコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="73163-129">To return customers from London or Paris, you would write the following code:</span></span>  
  
 [!code-csharp[csLINQGettingStarted#26](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_4.cs)]  
  
 <span data-ttu-id="73163-130">詳しくは、「[where 句](../../../../csharp/language-reference/keywords/where-clause.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="73163-130">For more information, see [where clause](../../../../csharp/language-reference/keywords/where-clause.md).</span></span>  
  
## <a name="ordering"></a><span data-ttu-id="73163-131">順序</span><span class="sxs-lookup"><span data-stu-id="73163-131">Ordering</span></span>  
 <span data-ttu-id="73163-132">返されたデータを並べ替えると便利なことがよくあります。</span><span class="sxs-lookup"><span data-stu-id="73163-132">Often it is convenient to sort the returned data.</span></span> <span data-ttu-id="73163-133">`orderby` 句を使用すると、並べ替える型の既定の比較子に従って、返されたシーケンスの要素が並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="73163-133">The `orderby` clause will cause the elements in the returned sequence to be sorted according to the default comparer for the type being sorted.</span></span> <span data-ttu-id="73163-134">たとえば、次のクエリは `Name` プロパティに基づいて結果を並び替えるように拡張できます。</span><span class="sxs-lookup"><span data-stu-id="73163-134">For example, the following query can be extended to sort the results based on the `Name` property.</span></span> <span data-ttu-id="73163-135">`Name` は文字列であるため、既定の比較子によって、アルファベット順 (A から Z) で並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="73163-135">Because `Name` is a string, the default comparer performs an alphabetical sort from A to Z.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#27](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_5.cs)]  
  
 <span data-ttu-id="73163-136">結果を逆の順序 (Z から A) で並び替えるには、`orderby…descending` 句を使用します。</span><span class="sxs-lookup"><span data-stu-id="73163-136">To order the results in reverse order, from Z to A, use the `orderby…descending` clause.</span></span>  
  
 <span data-ttu-id="73163-137">詳細については、「[orderby 句](../../../../csharp/language-reference/keywords/orderby-clause.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73163-137">For more information, see [orderby clause](../../../../csharp/language-reference/keywords/orderby-clause.md).</span></span>  
  
## <a name="grouping"></a><span data-ttu-id="73163-138">グループ化</span><span class="sxs-lookup"><span data-stu-id="73163-138">Grouping</span></span>  
 <span data-ttu-id="73163-139">指定したキーに基づいて結果をグループ化するには、`group` 句を使用します。</span><span class="sxs-lookup"><span data-stu-id="73163-139">The `group` clause enables you to group your results based on a key that you specify.</span></span> <span data-ttu-id="73163-140">たとえば、結果を `City` 別にグループ化するように指定して、住所がロンドンまたはパリにあるすべての顧客を個々のグループに分けることができます。</span><span class="sxs-lookup"><span data-stu-id="73163-140">For example you could specify that the results should be grouped by the `City` so that all customers from London or Paris are in individual groups.</span></span> <span data-ttu-id="73163-141">この場合は、`cust.City` がキーになります。</span><span class="sxs-lookup"><span data-stu-id="73163-141">In this case, `cust.City` is the key.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#28](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_6.cs)]  
  
 <span data-ttu-id="73163-142">`group` 句を使用したクエリが終了すると、結果は複数リストのリストという形式になります。</span><span class="sxs-lookup"><span data-stu-id="73163-142">When you end a query with a `group` clause, your results take the form of a list of lists.</span></span> <span data-ttu-id="73163-143">リストの各要素はオブジェクトであり、そのオブジェクトには、`Key` メンバーとそのキーに基づいてグループ化された要素のリストが含まれます。</span><span class="sxs-lookup"><span data-stu-id="73163-143">Each element in the list is an object that has a `Key` member and a list of elements that are grouped under that key.</span></span> <span data-ttu-id="73163-144">グループのシーケンスを生成するクエリを反復処理する場合は、入れ子になった `foreach` ループを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="73163-144">When you iterate over a query that produces a sequence of groups, you must use a nested `foreach` loop.</span></span> <span data-ttu-id="73163-145">外側のループは各グループを反復処理し、内側のループは各グループのメンバーを反復処理します。</span><span class="sxs-lookup"><span data-stu-id="73163-145">The outer loop iterates over each group, and the inner loop iterates over each group's members.</span></span>  
  
 <span data-ttu-id="73163-146">グループ操作の結果を参照する必要がある場合は、`into` キーワードを使用して、さらに照会可能な識別子を作成します。</span><span class="sxs-lookup"><span data-stu-id="73163-146">If you must refer to the results of a group operation, you can use the `into` keyword to create an identifier that can be queried further.</span></span> <span data-ttu-id="73163-147">次のクエリでは、顧客が 2 人より多いグループだけが返されます。</span><span class="sxs-lookup"><span data-stu-id="73163-147">The following query returns only those groups that contain more than two customers:</span></span>  
  
 [!code-csharp[csLINQGettingStarted#29](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_7.cs)]  
  
 <span data-ttu-id="73163-148">詳しくは、「[group 句](../../../../csharp/language-reference/keywords/group-clause.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="73163-148">For more information, see [group clause](../../../../csharp/language-reference/keywords/group-clause.md).</span></span>  
  
## <a name="joining"></a><span data-ttu-id="73163-149">結合</span><span class="sxs-lookup"><span data-stu-id="73163-149">Joining</span></span>  
 <span data-ttu-id="73163-150">結合操作は、データ ソースで明示的にモデル化されていないシーケンス間に関連付けを作成します。</span><span class="sxs-lookup"><span data-stu-id="73163-150">Join operations create associations between sequences that are not explicitly modeled in the data sources.</span></span> <span data-ttu-id="73163-151">たとえば、結合を実行して、住所地が同じすべての顧客と販売業者を検索することができます。</span><span class="sxs-lookup"><span data-stu-id="73163-151">For example you can perform a join to find all the customers and distributors who have the same location.</span></span> <span data-ttu-id="73163-152">[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] では、`join` 句はデータベース テーブルを直接の対象とするのではなく、オブジェクトのコレクションを対象として機能します。</span><span class="sxs-lookup"><span data-stu-id="73163-152">In [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] the `join` clause always works against object collections instead of database tables directly.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#36](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_8.cs)]  
  
 <span data-ttu-id="73163-153">[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] では、SQL ほど頻繁に `join` を使用する必要はありません。これは、オブジェクト モデルでは、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] の外部キーが項目のコレクションを保持するプロパティとして表されるためです。</span><span class="sxs-lookup"><span data-stu-id="73163-153">In [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] you do not have to use `join` as often as you do in SQL because foreign keys in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] are represented in the object model as properties that hold a collection of items.</span></span> <span data-ttu-id="73163-154">たとえば、`Customer` オブジェクトには `Order` オブジェクトのコレクションが含まれます。</span><span class="sxs-lookup"><span data-stu-id="73163-154">For example, a `Customer` object contains a collection of `Order` objects.</span></span> <span data-ttu-id="73163-155">結合を実行しなくても、ドット表記を使用して注文にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="73163-155">Rather than performing a join, you access the orders by using dot notation:</span></span>  
  
```  
from order in Customer.Orders...  
```  
  
 <span data-ttu-id="73163-156">詳細については、「[join 句](../../../../csharp/language-reference/keywords/join-clause.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73163-156">For more information, see [join clause](../../../../csharp/language-reference/keywords/join-clause.md).</span></span>  
  
## <a name="selecting-projections"></a><span data-ttu-id="73163-157">選択 (投影)</span><span class="sxs-lookup"><span data-stu-id="73163-157">Selecting (Projections)</span></span>  
 <span data-ttu-id="73163-158">`select` 句はクエリの結果を生成し、返される各要素の "シェイプ" つまり型を指定します。</span><span class="sxs-lookup"><span data-stu-id="73163-158">The `select` clause produces the results of the query and specifies the "shape" or type of each returned element.</span></span> <span data-ttu-id="73163-159">たとえば、完全な `Customer` オブジェクト、１ つのメンバーのみ、メンバーのサブセット、または計算や新しいオブジェクトの作成に基づいた、まったく異なる種類の結果のいずれで結果が構成されるかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="73163-159">For example, you can specify whether your results will consist of complete `Customer` objects, just one member, a subset of members, or some completely different result type based on a computation or new object creation.</span></span> <span data-ttu-id="73163-160">`select` 句でソース要素のコピー以外のものを生成する場合、その操作は*投影*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="73163-160">When the `select` clause produces something other than a copy of the source element, the operation is called a *projection*.</span></span> <span data-ttu-id="73163-161">投影を使用したデータの変換は、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリ式の強力な機能です。</span><span class="sxs-lookup"><span data-stu-id="73163-161">The use of projections to transform data is a powerful capability of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="73163-162">詳細については、「[LINQ によるデータ変換 (C#)](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)」と「[select 句](../../../../csharp/language-reference/keywords/select-clause.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73163-162">For more information, see [Data Transformations with LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md) and [select clause](../../../../csharp/language-reference/keywords/select-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73163-163">参照</span><span class="sxs-lookup"><span data-stu-id="73163-163">See Also</span></span>  
 [<span data-ttu-id="73163-164">C# の LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="73163-164">Getting Started with LINQ in C#</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [<span data-ttu-id="73163-165">LINQ クエリ式</span><span class="sxs-lookup"><span data-stu-id="73163-165">LINQ Query Expressions</span></span>](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="73163-166">チュートリアル: C# でのクエリの作成</span><span class="sxs-lookup"><span data-stu-id="73163-166">Walkthrough: Writing Queries in C#</span></span>](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)  
 [<span data-ttu-id="73163-167">クエリ キーワード (LINQ)</span><span class="sxs-lookup"><span data-stu-id="73163-167">Query Keywords (LINQ)</span></span>](../../../../csharp/language-reference/keywords/query-keywords.md)  
 [<span data-ttu-id="73163-168">匿名型</span><span class="sxs-lookup"><span data-stu-id="73163-168">Anonymous Types</span></span>](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
