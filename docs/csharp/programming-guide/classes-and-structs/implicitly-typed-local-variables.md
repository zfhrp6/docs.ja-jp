---
title: "暗黙的に型指定されるローカル変数 (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
caps.latest.revision: 23
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
ms.openlocfilehash: cc02c0f7ef5fbbbf3c60188426a8027f6a60fb89
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a><span data-ttu-id="9a093-102">暗黙的に型指定されるローカル変数 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="9a093-102">Implicitly Typed Local Variables (C# Programming Guide)</span></span>
<span data-ttu-id="9a093-103">ローカル変数は、明示的な型を指定しないで宣言できます。</span><span class="sxs-lookup"><span data-stu-id="9a093-103">Local variables can be declared without giving an explicit type.</span></span> <span data-ttu-id="9a093-104">`var` キーワードは、初期化ステートメントの右辺にある式から変数の型を推論するようにコンパイラに指示します。</span><span class="sxs-lookup"><span data-stu-id="9a093-104">The `var` keyword instructs the compiler to infer the type of the variable from the expression on the right side of the initialization statement.</span></span> <span data-ttu-id="9a093-105">推論される型は、組み込み型、匿名型、ユーザー定義型、または .NET Framework クラス ライブラリで定義されている型である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9a093-105">The inferred type may be a built-in type, an anonymous type, a user-defined type, or a type defined in the .NET Framework class library.</span></span> <span data-ttu-id="9a093-106">`var` で配列を初期化する方法の詳細については、「[暗黙的に型指定される配列](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a093-106">For more information about how to initialize arrays with `var`, see [Implicitly Typed Arrays](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).</span></span>  
  
 <span data-ttu-id="9a093-107">ローカル変数を `var` で宣言するさまざまな方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="9a093-107">The following examples show various ways in which local variables can be declared with `var`:</span></span>  
  
 <span data-ttu-id="9a093-108">[!code-cs[csProgGuideLINQ#43](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="9a093-108">[!code-cs[csProgGuideLINQ#43](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_1.cs)]</span></span>  
  
 <span data-ttu-id="9a093-109">`var` キーワードは "バリアント" を意味するのではなく、変数の厳密でない型指定や遅延バインディングを示すものでもないことを理解することが重要です。</span><span class="sxs-lookup"><span data-stu-id="9a093-109">It is important to understand that the `var` keyword does not mean "variant" and does not indicate that the variable is loosely typed, or late-bound.</span></span> <span data-ttu-id="9a093-110">単に、最も適切な型をコンパイラが決定して割り当てることを意味します。</span><span class="sxs-lookup"><span data-stu-id="9a093-110">It just means that the compiler determines and assigns the most appropriate type.</span></span>  
  
 <span data-ttu-id="9a093-111">`var` キーワードは、次のコンテキストで使用される場合があります。</span><span class="sxs-lookup"><span data-stu-id="9a093-111">The `var` keyword may be used in the following contexts:</span></span>  
  
-   <span data-ttu-id="9a093-112">前の例で示したようなローカル変数 (メソッドのスコープで宣言された変数)。</span><span class="sxs-lookup"><span data-stu-id="9a093-112">On local variables (variables declared at method scope) as shown in the previous example.</span></span>  
  
-   <span data-ttu-id="9a093-113">[for](../../../csharp/language-reference/keywords/for.md) 初期化ステートメント。</span><span class="sxs-lookup"><span data-stu-id="9a093-113">In a [for](../../../csharp/language-reference/keywords/for.md) initialization statement.</span></span>  
  
    ```  
    for(var x = 1; x < 10; x++)  
    ```  
  
-   <span data-ttu-id="9a093-114">[foreach](../../../csharp/language-reference/keywords/foreach-in.md) 初期化ステートメント。</span><span class="sxs-lookup"><span data-stu-id="9a093-114">In a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) initialization statement.</span></span>  
  
    ```  
    foreach(var item in list){...}  
    ```  
  
-   <span data-ttu-id="9a093-115">[using](../../../csharp/language-reference/keywords/using-statement.md) ステートメント。</span><span class="sxs-lookup"><span data-stu-id="9a093-115">In a [using](../../../csharp/language-reference/keywords/using-statement.md) statement.</span></span>  
  
    ```  
    using (var file = new StreamReader("C:\\myfile.txt")) {...}  
    ```  
  
 <span data-ttu-id="9a093-116">詳細については、「[方法: クエリ式で暗黙的に型指定されるローカル変数および配列を使用する](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a093-116">For more information, see [How to: Use Implicitly Typed Local Variables and Arrays in a Query Expression](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span></span>  
  
## <a name="var-and-anonymous-types"></a><span data-ttu-id="9a093-117">var と匿名型</span><span class="sxs-lookup"><span data-stu-id="9a093-117">var and Anonymous Types</span></span>  
 <span data-ttu-id="9a093-118">多くの場合、`var` の使用は任意であり、構文上便利なだけです。</span><span class="sxs-lookup"><span data-stu-id="9a093-118">In many cases the use of `var` is optional and is just a syntactic convenience.</span></span> <span data-ttu-id="9a093-119">ただし、変数が匿名型で初期化される場合、後でオブジェクトのプロパティへのアクセスが必要になったら、変数を `var` として宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9a093-119">However, when a variable is initialized with an anonymous type you must declare the variable as `var` if you need to access the properties of the object at a later point.</span></span> <span data-ttu-id="9a093-120">これは、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリ式では一般的なシナリオです。</span><span class="sxs-lookup"><span data-stu-id="9a093-120">This is a common scenario in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="9a093-121">詳細については、「[匿名型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a093-121">For more information, see [Anonymous Types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>  
  
 <span data-ttu-id="9a093-122">ソース コードの観点から見ると、匿名型には名前がありません。</span><span class="sxs-lookup"><span data-stu-id="9a093-122">From the perspective of your source code, an anonymous type has no name.</span></span> <span data-ttu-id="9a093-123">そのため、クエリ変数が `var` で初期化された場合、返されたオブジェクトのシーケンスのプロパティにアクセスするための唯一の方法は、`foreach` ステートメント内の繰り返し変数の型として `var` を使用することです。</span><span class="sxs-lookup"><span data-stu-id="9a093-123">Therefore, if a query variable has been initialized with `var`, then the only way to access the properties in the returned sequence of objects is to use `var` as the type of the iteration variable in the `foreach` statement.</span></span>  
  
 <span data-ttu-id="9a093-124">[!code-cs[csProgGuideLINQ#44](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="9a093-124">[!code-cs[csProgGuideLINQ#44](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_2.cs)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a093-125">コメント</span><span class="sxs-lookup"><span data-stu-id="9a093-125">Remarks</span></span>  
 <span data-ttu-id="9a093-126">暗黙的に型指定される変数の宣言には、次の制限が適用されます。</span><span class="sxs-lookup"><span data-stu-id="9a093-126">The following restrictions apply to implicitly-typed variable declarations:</span></span>  
  
-   <span data-ttu-id="9a093-127">`var` を使用できるのは、同じステートメント内でローカル変数の宣言と初期化が行われる場合のみです。この変数は、null、メソッド グループ、または匿名関数に初期化することはできません。</span><span class="sxs-lookup"><span data-stu-id="9a093-127">`var` can only be used when a local variable is declared and initialized in the same statement; the variable cannot be initialized to null, or to a method group or an anonymous function.</span></span>  
  
-   <span data-ttu-id="9a093-128">`var` は、クラス スコープのフィールドで使用できません。</span><span class="sxs-lookup"><span data-stu-id="9a093-128">`var` cannot be used on fields at class scope.</span></span>  
  
-   <span data-ttu-id="9a093-129">`var` を使用して宣言された変数は、初期化式では使用できません。</span><span class="sxs-lookup"><span data-stu-id="9a093-129">Variables declared by using `var` cannot be used in the initialization expression.</span></span> <span data-ttu-id="9a093-130">つまり、`: int i = (i = 20);` という式は有効ですが、`var i = (i = 20);` という式はコンパイル時のエラーを生成します。</span><span class="sxs-lookup"><span data-stu-id="9a093-130">In other words, this expression is legal`: int i = (i = 20);` but this expression produces a compile-time error: `var i = (i = 20);`</span></span>  
  
-   <span data-ttu-id="9a093-131">暗黙的に型指定された複数の変数を同じステートメント内で初期化することはできません。</span><span class="sxs-lookup"><span data-stu-id="9a093-131">Multiple implicitly-typed variables cannot be initialized in the same statement.</span></span>  
  
-   <span data-ttu-id="9a093-132">`var` という名前の型がスコープ内にある場合、`var` キーワードはその型名に解決され、暗黙的に型指定されたローカル変数の宣言の一部とは見なされません。</span><span class="sxs-lookup"><span data-stu-id="9a093-132">If a type named `var` is in scope, then the `var` keyword will resolve to that type name and will not be treated as part of an implicitly typed local variable declaration.</span></span>  
  
 <span data-ttu-id="9a093-133">`var` は、クエリ式と使用する場合に便利なこともあります。クエリ変数の構築された型を厳密に判別することが難しい場合です。</span><span class="sxs-lookup"><span data-stu-id="9a093-133">You may find that `var` can also be useful with query expressions in which the exact constructed type of the query variable is difficult to determine.</span></span> <span data-ttu-id="9a093-134">このような状況は、グループ化と並べ替えの処理で発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="9a093-134">This can occur with grouping and ordering operations.</span></span>  
  
 <span data-ttu-id="9a093-135">`var` キーワードは、変数の特定の型をキーボードで入力するのが面倒な場合、その型が明白な場合、型によってコードが読みやすくならない場合にも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="9a093-135">The `var` keyword can also be useful when the specific type of the variable is tedious to type on the keyboard, or is obvious, or does not add to the readability of the code.</span></span> <span data-ttu-id="9a093-136">このような理由で `var` が有用な例の 1 つとして、グループ化処理で使用されるような入れ子にされたジェネリック型があります。</span><span class="sxs-lookup"><span data-stu-id="9a093-136">One example where `var` is helpful in this manner is with nested generic types such as those used with group operations.</span></span> <span data-ttu-id="9a093-137">次のクエリでは、クエリ変数の型は `IEnumerable<IGrouping<string, Student>>` です。</span><span class="sxs-lookup"><span data-stu-id="9a093-137">In the following query, the type of the query variable is `IEnumerable<IGrouping<string, Student>>`.</span></span> <span data-ttu-id="9a093-138">コードの作成者とそのコードを保守する担当者がこの点を理解している限り、簡略化するために暗黙的な型指定を使用しても問題はありません。</span><span class="sxs-lookup"><span data-stu-id="9a093-138">As long as you and others who must maintain your code understand this, there is no problem with using implicit typing for convenience and brevity.</span></span>  
  
 <span data-ttu-id="9a093-139">[!code-cs[cscsrefQueryKeywords#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicitly-typed-local-variables_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="9a093-139">[!code-cs[cscsrefQueryKeywords#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicitly-typed-local-variables_3.cs)]</span></span>  
  
 <span data-ttu-id="9a093-140">ただし、`var` を使用すると、他の開発者がコードを理解しづらくなる可能性はあります。</span><span class="sxs-lookup"><span data-stu-id="9a093-140">However, the use of `var` does have at least the potential to make your code more difficult to understand for other developers.</span></span> <span data-ttu-id="9a093-141">このため、C# のドキュメントでは、通常、必要な場合にだけ `var` を使用しています。</span><span class="sxs-lookup"><span data-stu-id="9a093-141">For that reason, the C# documentation generally uses `var` only when it is required.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a093-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="9a093-142">See Also</span></span>  
 <span data-ttu-id="9a093-143">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="9a093-143">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="9a093-144">[暗黙的に型指定される配列](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="9a093-144">[Implicitly Typed Arrays](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md) </span></span>  
 <span data-ttu-id="9a093-145">[方法: クエリ式で暗黙的に型指定されるローカル変数および配列を使用する](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md) </span><span class="sxs-lookup"><span data-stu-id="9a093-145">[How to: Use Implicitly Typed Local Variables and Arrays in a Query Expression](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md) </span></span>  
 <span data-ttu-id="9a093-146">[匿名型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="9a093-146">[Anonymous Types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md) </span></span>  
 <span data-ttu-id="9a093-147">[オブジェクト初期化子とコレクション初期化子](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md) </span><span class="sxs-lookup"><span data-stu-id="9a093-147">[Object and Collection Initializers](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md) </span></span>  
 <span data-ttu-id="9a093-148">[var](../../../csharp/language-reference/keywords/var.md) </span><span class="sxs-lookup"><span data-stu-id="9a093-148">[var](../../../csharp/language-reference/keywords/var.md) </span></span>  
 <span data-ttu-id="9a093-149">[LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md) </span><span class="sxs-lookup"><span data-stu-id="9a093-149">[LINQ Query Expressions](../../../csharp/programming-guide/linq-query-expressions/index.md) </span></span>  
 <span data-ttu-id="9a093-150">[LINQ (統合言語クエリ)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) </span><span class="sxs-lookup"><span data-stu-id="9a093-150">[LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) </span></span>  
 <span data-ttu-id="9a093-151">[for](../../../csharp/language-reference/keywords/for.md) </span><span class="sxs-lookup"><span data-stu-id="9a093-151">[for](../../../csharp/language-reference/keywords/for.md) </span></span>  
 <span data-ttu-id="9a093-152">[foreach、in](../../../csharp/language-reference/keywords/foreach-in.md) </span><span class="sxs-lookup"><span data-stu-id="9a093-152">[foreach, in](../../../csharp/language-reference/keywords/foreach-in.md) </span></span>  
 [<span data-ttu-id="9a093-153">using ステートメント</span><span class="sxs-lookup"><span data-stu-id="9a093-153">using Statement</span></span>](../../../csharp/language-reference/keywords/using-statement.md)

