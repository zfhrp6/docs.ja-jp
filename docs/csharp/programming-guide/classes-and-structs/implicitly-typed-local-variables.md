---
title: 暗黙的に型指定されるローカル変数 (C# プログラミング ガイド)
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
ms.openlocfilehash: c6c2bae39764e78fad2510bbc8937b0ac790bef5
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2018
---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a><span data-ttu-id="3f4a3-102">暗黙的に型指定されるローカル変数 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="3f4a3-102">Implicitly Typed Local Variables (C# Programming Guide)</span></span>
<span data-ttu-id="3f4a3-103">ローカル変数は、明示的な型を指定しないで宣言できます。</span><span class="sxs-lookup"><span data-stu-id="3f4a3-103">Local variables can be declared without giving an explicit type.</span></span> <span data-ttu-id="3f4a3-104">`var` キーワードは、初期化ステートメントの右辺にある式から変数の型を推論するようにコンパイラに指示します。</span><span class="sxs-lookup"><span data-stu-id="3f4a3-104">The `var` keyword instructs the compiler to infer the type of the variable from the expression on the right side of the initialization statement.</span></span> <span data-ttu-id="3f4a3-105">推論される型は、組み込み型、匿名型、ユーザー定義型、または .NET Framework クラス ライブラリで定義されている型である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3f4a3-105">The inferred type may be a built-in type, an anonymous type, a user-defined type, or a type defined in the .NET Framework class library.</span></span> <span data-ttu-id="3f4a3-106">`var` で配列を初期化する方法の詳細については、「[暗黙的に型指定される配列](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f4a3-106">For more information about how to initialize arrays with `var`, see [Implicitly Typed Arrays](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).</span></span>  
  
 <span data-ttu-id="3f4a3-107">ローカル変数を `var` で宣言するさまざまな方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="3f4a3-107">The following examples show various ways in which local variables can be declared with `var`:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#43](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_1.cs)]  
  
 <span data-ttu-id="3f4a3-108">`var` キーワードは "バリアント" を意味するのではなく、変数の厳密でない型指定や遅延バインディングを示すものでもないことを理解することが重要です。</span><span class="sxs-lookup"><span data-stu-id="3f4a3-108">It is important to understand that the `var` keyword does not mean "variant" and does not indicate that the variable is loosely typed, or late-bound.</span></span> <span data-ttu-id="3f4a3-109">単に、最も適切な型をコンパイラが決定して割り当てることを意味します。</span><span class="sxs-lookup"><span data-stu-id="3f4a3-109">It just means that the compiler determines and assigns the most appropriate type.</span></span>  
  
 <span data-ttu-id="3f4a3-110">`var` キーワードは、次のコンテキストで使用される場合があります。</span><span class="sxs-lookup"><span data-stu-id="3f4a3-110">The `var` keyword may be used in the following contexts:</span></span>  
  
-   <span data-ttu-id="3f4a3-111">前の例で示したようなローカル変数 (メソッドのスコープで宣言された変数)。</span><span class="sxs-lookup"><span data-stu-id="3f4a3-111">On local variables (variables declared at method scope) as shown in the previous example.</span></span>  
  
-   <span data-ttu-id="3f4a3-112">[for](../../../csharp/language-reference/keywords/for.md) 初期化ステートメント。</span><span class="sxs-lookup"><span data-stu-id="3f4a3-112">In a [for](../../../csharp/language-reference/keywords/for.md) initialization statement.</span></span>  
  
    ```csharp  
    for(var x = 1; x < 10; x++)  
    ```  
  
-   <span data-ttu-id="3f4a3-113">[foreach](../../../csharp/language-reference/keywords/foreach-in.md) 初期化ステートメント。</span><span class="sxs-lookup"><span data-stu-id="3f4a3-113">In a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) initialization statement.</span></span>  
  
    ```csharp  
    foreach(var item in list){...}  
    ```  
  
-   <span data-ttu-id="3f4a3-114">[using](../../../csharp/language-reference/keywords/using-statement.md) ステートメント。</span><span class="sxs-lookup"><span data-stu-id="3f4a3-114">In a [using](../../../csharp/language-reference/keywords/using-statement.md) statement.</span></span>  
  
    ```csharp  
    using (var file = new StreamReader("C:\\myfile.txt")) {...}  
    ```  
  
 <span data-ttu-id="3f4a3-115">詳細については、「[方法: クエリ式で暗黙的に型指定されるローカル変数および配列を使用する](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f4a3-115">For more information, see [How to: Use Implicitly Typed Local Variables and Arrays in a Query Expression](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span></span>  
  
## <a name="var-and-anonymous-types"></a><span data-ttu-id="3f4a3-116">var と匿名型</span><span class="sxs-lookup"><span data-stu-id="3f4a3-116">var and Anonymous Types</span></span>  
 <span data-ttu-id="3f4a3-117">多くの場合、`var` の使用は任意であり、構文上便利なだけです。</span><span class="sxs-lookup"><span data-stu-id="3f4a3-117">In many cases the use of `var` is optional and is just a syntactic convenience.</span></span> <span data-ttu-id="3f4a3-118">ただし、変数が匿名型で初期化される場合、後でオブジェクトのプロパティへのアクセスが必要になったら、変数を `var` として宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f4a3-118">However, when a variable is initialized with an anonymous type you must declare the variable as `var` if you need to access the properties of the object at a later point.</span></span> <span data-ttu-id="3f4a3-119">これは、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリ式では一般的なシナリオです。</span><span class="sxs-lookup"><span data-stu-id="3f4a3-119">This is a common scenario in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="3f4a3-120">詳細については、「[匿名型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f4a3-120">For more information, see [Anonymous Types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>  
  
 <span data-ttu-id="3f4a3-121">ソース コードの観点から見ると、匿名型には名前がありません。</span><span class="sxs-lookup"><span data-stu-id="3f4a3-121">From the perspective of your source code, an anonymous type has no name.</span></span> <span data-ttu-id="3f4a3-122">そのため、クエリ変数が `var` で初期化された場合、返されたオブジェクトのシーケンスのプロパティにアクセスするための唯一の方法は、`foreach` ステートメント内の繰り返し変数の型として `var` を使用することです。</span><span class="sxs-lookup"><span data-stu-id="3f4a3-122">Therefore, if a query variable has been initialized with `var`, then the only way to access the properties in the returned sequence of objects is to use `var` as the type of the iteration variable in the `foreach` statement.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#44](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_2.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="3f4a3-123">コメント</span><span class="sxs-lookup"><span data-stu-id="3f4a3-123">Remarks</span></span>  
 <span data-ttu-id="3f4a3-124">暗黙的に型指定される変数の宣言には、次の制限が適用されます。</span><span class="sxs-lookup"><span data-stu-id="3f4a3-124">The following restrictions apply to implicitly-typed variable declarations:</span></span>  
  
-   <span data-ttu-id="3f4a3-125">`var` を使用できるのは、同じステートメント内でローカル変数の宣言と初期化が行われる場合のみです。この変数は、null、メソッド グループ、または匿名関数に初期化することはできません。</span><span class="sxs-lookup"><span data-stu-id="3f4a3-125">`var` can only be used when a local variable is declared and initialized in the same statement; the variable cannot be initialized to null, or to a method group or an anonymous function.</span></span>  
  
-   <span data-ttu-id="3f4a3-126">`var` は、クラス スコープのフィールドで使用できません。</span><span class="sxs-lookup"><span data-stu-id="3f4a3-126">`var` cannot be used on fields at class scope.</span></span>  
  
-   <span data-ttu-id="3f4a3-127">`var` を使用して宣言された変数は、初期化式では使用できません。</span><span class="sxs-lookup"><span data-stu-id="3f4a3-127">Variables declared by using `var` cannot be used in the initialization expression.</span></span> <span data-ttu-id="3f4a3-128">つまり、`: int i = (i = 20);` という式は有効ですが、`var i = (i = 20);` という式はコンパイル時のエラーを生成します。</span><span class="sxs-lookup"><span data-stu-id="3f4a3-128">In other words, this expression is legal`: int i = (i = 20);` but this expression produces a compile-time error: `var i = (i = 20);`</span></span>  
  
-   <span data-ttu-id="3f4a3-129">暗黙的に型指定された複数の変数を同じステートメント内で初期化することはできません。</span><span class="sxs-lookup"><span data-stu-id="3f4a3-129">Multiple implicitly-typed variables cannot be initialized in the same statement.</span></span>  
  
-   <span data-ttu-id="3f4a3-130">`var` という名前の型がスコープ内にある場合、`var` キーワードはその型名に解決され、暗黙的に型指定されたローカル変数の宣言の一部とは見なされません。</span><span class="sxs-lookup"><span data-stu-id="3f4a3-130">If a type named `var` is in scope, then the `var` keyword will resolve to that type name and will not be treated as part of an implicitly typed local variable declaration.</span></span>  
  
 <span data-ttu-id="3f4a3-131">`var` は、クエリ式と使用する場合に便利なこともあります。クエリ変数の構築された型を厳密に判別することが難しい場合です。</span><span class="sxs-lookup"><span data-stu-id="3f4a3-131">You may find that `var` can also be useful with query expressions in which the exact constructed type of the query variable is difficult to determine.</span></span> <span data-ttu-id="3f4a3-132">このような状況は、グループ化と並べ替えの処理で発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="3f4a3-132">This can occur with grouping and ordering operations.</span></span>  
  
 <span data-ttu-id="3f4a3-133">`var` キーワードは、変数の特定の型をキーボードで入力するのが面倒な場合、その型が明白な場合、型によってコードが読みやすくならない場合にも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="3f4a3-133">The `var` keyword can also be useful when the specific type of the variable is tedious to type on the keyboard, or is obvious, or does not add to the readability of the code.</span></span> <span data-ttu-id="3f4a3-134">このような理由で `var` が有用な例の 1 つとして、グループ化処理で使用されるような入れ子にされたジェネリック型があります。</span><span class="sxs-lookup"><span data-stu-id="3f4a3-134">One example where `var` is helpful in this manner is with nested generic types such as those used with group operations.</span></span> <span data-ttu-id="3f4a3-135">次のクエリでは、クエリ変数の型は `IEnumerable<IGrouping<string, Student>>` です。</span><span class="sxs-lookup"><span data-stu-id="3f4a3-135">In the following query, the type of the query variable is `IEnumerable<IGrouping<string, Student>>`.</span></span> <span data-ttu-id="3f4a3-136">コードの作成者とそのコードを保守する担当者がこの点を理解している限り、簡略化するために暗黙的な型指定を使用しても問題はありません。</span><span class="sxs-lookup"><span data-stu-id="3f4a3-136">As long as you and others who must maintain your code understand this, there is no problem with using implicit typing for convenience and brevity.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicitly-typed-local-variables_3.cs)]  
  
 <span data-ttu-id="3f4a3-137">ただし、`var` を使用すると、他の開発者がコードを理解しづらくなる可能性はあります。</span><span class="sxs-lookup"><span data-stu-id="3f4a3-137">However, the use of `var` does have at least the potential to make your code more difficult to understand for other developers.</span></span> <span data-ttu-id="3f4a3-138">このため、C# のドキュメントでは、通常、必要な場合にだけ `var` を使用しています。</span><span class="sxs-lookup"><span data-stu-id="3f4a3-138">For that reason, the C# documentation generally uses `var` only when it is required.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f4a3-139">参照</span><span class="sxs-lookup"><span data-stu-id="3f4a3-139">See Also</span></span>  
 [<span data-ttu-id="3f4a3-140">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="3f4a3-140">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="3f4a3-141">暗黙的に型指定される配列</span><span class="sxs-lookup"><span data-stu-id="3f4a3-141">Implicitly Typed Arrays</span></span>](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md)  
 [<span data-ttu-id="3f4a3-142">方法: クエリ式で暗黙的に型指定されるローカル変数および配列を使用する</span><span class="sxs-lookup"><span data-stu-id="3f4a3-142">How to: Use Implicitly Typed Local Variables and Arrays in a Query Expression</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)  
 [<span data-ttu-id="3f4a3-143">匿名型</span><span class="sxs-lookup"><span data-stu-id="3f4a3-143">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
 [<span data-ttu-id="3f4a3-144">オブジェクト初期化子とコレクション初期化子</span><span class="sxs-lookup"><span data-stu-id="3f4a3-144">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 [<span data-ttu-id="3f4a3-145">var</span><span class="sxs-lookup"><span data-stu-id="3f4a3-145">var</span></span>](../../../csharp/language-reference/keywords/var.md)  
 [<span data-ttu-id="3f4a3-146">LINQ クエリ式</span><span class="sxs-lookup"><span data-stu-id="3f4a3-146">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="3f4a3-147">統合言語クエリ (LINQ)</span><span class="sxs-lookup"><span data-stu-id="3f4a3-147">LINQ (Language-Integrated Query)</span></span>](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [<span data-ttu-id="3f4a3-148">for</span><span class="sxs-lookup"><span data-stu-id="3f4a3-148">for</span></span>](../../../csharp/language-reference/keywords/for.md)  
 [<span data-ttu-id="3f4a3-149">foreach、in</span><span class="sxs-lookup"><span data-stu-id="3f4a3-149">foreach, in</span></span>](../../../csharp/language-reference/keywords/foreach-in.md)  
 [<span data-ttu-id="3f4a3-150">using ステートメント</span><span class="sxs-lookup"><span data-stu-id="3f4a3-150">using Statement</span></span>](../../../csharp/language-reference/keywords/using-statement.md)
