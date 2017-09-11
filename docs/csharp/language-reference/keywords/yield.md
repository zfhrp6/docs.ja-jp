---
title: "yield (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- yield
- yield_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- yield keyword [C#]
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
caps.latest.revision: 46
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
ms.openlocfilehash: eb55fd5b1ade48316516cda83633935abbf8dcf9
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="yield-c-reference"></a><span data-ttu-id="108be-102">yield (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="108be-102">yield (C# Reference)</span></span>
<span data-ttu-id="108be-103">ステートメントで `yield` キーワードを使用した場合、メソッド、演算子、または `get` アクセサーが反復子であることを示します。</span><span class="sxs-lookup"><span data-stu-id="108be-103">When you use the `yield` keyword in a statement, you indicate that the method, operator, or `get` accessor in which it appears is an iterator.</span></span> <span data-ttu-id="108be-104">`yield` を使用して反復子を定義すると、カスタム コレクション型の <xref:System.Collections.Generic.IEnumerator%601> および <xref:System.Collections.IEnumerable> パターンを実装するときに明示的な余分なクラス (列挙の状態を保持するクラス。たとえば <xref:System.Collections.IEnumerator> を参照) が不要になります。</span><span class="sxs-lookup"><span data-stu-id="108be-104">Using `yield` to define an iterator removes the need for an explicit extra class (the class that holds the state for an enumeration, see <xref:System.Collections.Generic.IEnumerator%601> for an example) when you implement the <xref:System.Collections.IEnumerable> and <xref:System.Collections.IEnumerator> pattern for a custom collection type.</span></span>  
  
 <span data-ttu-id="108be-105">`yield` ステートメントの 2 つの形式を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="108be-105">The following example shows the two forms of the `yield` statement.</span></span>  
  
```csharp  
yield return <expression>;  
yield break;  
```  
  
## <a name="remarks"></a><span data-ttu-id="108be-106">コメント</span><span class="sxs-lookup"><span data-stu-id="108be-106">Remarks</span></span>  
 <span data-ttu-id="108be-107">各要素を 1 つずつ返すには、`yield return` ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="108be-107">You use a `yield return` statement to return each element one at a time.</span></span>  
  
 <span data-ttu-id="108be-108">[foreach](../../../csharp/language-reference/keywords/foreach-in.md) ステートメントまたは LINQ クエリを使用することにより、Iterator メソッドを処理します。</span><span class="sxs-lookup"><span data-stu-id="108be-108">You consume an iterator method by using a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement or LINQ query.</span></span> <span data-ttu-id="108be-109">`foreach` ループの各イテレーションは、Iterator メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="108be-109">Each iteration of the `foreach` loop calls the iterator method.</span></span> <span data-ttu-id="108be-110">`yield return` ステートメントが Iterator メソッドに到達すると、`expression` が返され、コードの現在の位置が保持されます。</span><span class="sxs-lookup"><span data-stu-id="108be-110">When a `yield return` statement is reached in the iterator method, `expression` is returned, and the current location in code is retained.</span></span> <span data-ttu-id="108be-111">次回、Iterator 関数が呼び出されると、この位置から実行が再開されます。</span><span class="sxs-lookup"><span data-stu-id="108be-111">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="108be-112">`yield break` ステートメントを使用すると、反復を終了できます。</span><span class="sxs-lookup"><span data-stu-id="108be-112">You can use a `yield break` statement to end the iteration.</span></span>  
  
 <span data-ttu-id="108be-113">反復子について詳しくは、「[Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="108be-113">For more information about iterators, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
## <a name="iterator-methods-and-get-accessors"></a><span data-ttu-id="108be-114">Iterator メソッドと get アクセサー</span><span class="sxs-lookup"><span data-stu-id="108be-114">Iterator Methods and get Accessors</span></span>  
 <span data-ttu-id="108be-115">反復子の宣言は、次の要件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="108be-115">The declaration of an iterator must meet the following requirements:</span></span>  
  
-   <span data-ttu-id="108be-116">戻り値の型は、<xref:System.Collections.IEnumerable>、<xref:System.Collections.Generic.IEnumerable%601>、<xref:System.Collections.IEnumerator>、または <xref:System.Collections.Generic.IEnumerator%601> であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="108be-116">The return type must be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
-   <span data-ttu-id="108be-117">この宣言には、[ref](../../../csharp/language-reference/keywords/ref.md) パラメーターまたは [out](../../../csharp/language-reference/keywords/out.md) パラメーターを含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="108be-117">The declaration can't have any [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out.md) parameters.</span></span>  
  
 <span data-ttu-id="108be-118">`yield` または <xref:System.Collections.IEnumerable> を返す反復子の <xref:System.Collections.IEnumerator> 型は `object` です。</span><span class="sxs-lookup"><span data-stu-id="108be-118">The `yield` type of an iterator that returns <xref:System.Collections.IEnumerable> or <xref:System.Collections.IEnumerator> is `object`.</span></span>  <span data-ttu-id="108be-119">反復子が <xref:System.Collections.Generic.IEnumerable%601> または <xref:System.Collections.Generic.IEnumerator%601> を返す場合、`yield return` ステートメント内の式の型から、ジェネリック型パラメーターへの暗黙的な変換が存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="108be-119">If the iterator returns <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.Generic.IEnumerator%601>, there must be an implicit conversion from the type of the expression in the `yield return` statement to the generic type parameter .</span></span>  
  
 <span data-ttu-id="108be-120">次の特性を持つメソッドに `yield return` ステートメントまたは `yield break` ステートメントを含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="108be-120">You can't include a `yield return` or `yield break` statement in methods that have the following characteristics:</span></span>  
  
-   <span data-ttu-id="108be-121">匿名メソッド。</span><span class="sxs-lookup"><span data-stu-id="108be-121">Anonymous methods.</span></span> <span data-ttu-id="108be-122">詳しくは、「[匿名メソッド](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="108be-122">For more information, see [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span></span>  
  
-   <span data-ttu-id="108be-123">unsafe ブロックを含むメソッド。</span><span class="sxs-lookup"><span data-stu-id="108be-123">Methods that contain unsafe blocks.</span></span> <span data-ttu-id="108be-124">詳しくは、「[unsafe](../../../csharp/language-reference/keywords/unsafe.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="108be-124">For more information, see [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="108be-125">例外処理</span><span class="sxs-lookup"><span data-stu-id="108be-125">Exception Handling</span></span>  
 <span data-ttu-id="108be-126">`yield return` ステートメントは、try-catch ブロックに配置することはできません。</span><span class="sxs-lookup"><span data-stu-id="108be-126">A `yield return` statement can't be located in a try-catch block.</span></span> <span data-ttu-id="108be-127">`yield return` ステートメントは、try-finally ステートメントの try ブロックに配置できます。</span><span class="sxs-lookup"><span data-stu-id="108be-127">A `yield return` statement can be located in the try block of a try-finally statement.</span></span>  
  
 <span data-ttu-id="108be-128">`yield break` ステートメントは、try ブロックまたは catch ブロックには配置できますが、finally ブロックには配置できません。</span><span class="sxs-lookup"><span data-stu-id="108be-128">A `yield break` statement can be located in a try block or a catch block but not a finally block.</span></span>  
  
 <span data-ttu-id="108be-129">`foreach` 本体 (Iterator メソッドの外部) で例外がスローされた場合、Iterator メソッドの `finally` ブロックが実行されます。</span><span class="sxs-lookup"><span data-stu-id="108be-129">If the `foreach` body (outside of the iterator method) throws an exception, a `finally` block in the iterator method is executed.</span></span>  
  
## <a name="technical-implementation"></a><span data-ttu-id="108be-130">技術的な実装</span><span class="sxs-lookup"><span data-stu-id="108be-130">Technical Implementation</span></span>  
 <span data-ttu-id="108be-131">次のコードは、iterator メソッドから `IEnumerable<string>` を返した後、要素を反復処理します。</span><span class="sxs-lookup"><span data-stu-id="108be-131">The following code returns an `IEnumerable<string>` from an iterator method and then iterates through its elements.</span></span>  
  
```csharp  
IEnumerable<string> elements = MyIteratorMethod();  
foreach (string element in elements)  
{  
   ...  
}  
```  
  
 <span data-ttu-id="108be-132">`MyIteratorMethod` への呼び出しでは、メソッドの本体は実行されません。</span><span class="sxs-lookup"><span data-stu-id="108be-132">The call to `MyIteratorMethod` doesn't execute the body of the method.</span></span> <span data-ttu-id="108be-133">この呼び出しでは、`IEnumerable<string>` が `elements` 変数に返されます。</span><span class="sxs-lookup"><span data-stu-id="108be-133">Instead the call returns an `IEnumerable<string>` into the `elements` variable.</span></span>  
  
 <span data-ttu-id="108be-134">`foreach` ループの反復処理では、<xref:System.Collections.IEnumerator.MoveNext%2A> について `elements` メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="108be-134">On an iteration of the `foreach` loop, the <xref:System.Collections.IEnumerator.MoveNext%2A> method is called for `elements`.</span></span> <span data-ttu-id="108be-135">この呼び出しでは、次の `MyIteratorMethod` ステートメントに到達するまで、`yield return` の本体が実行されます。</span><span class="sxs-lookup"><span data-stu-id="108be-135">This call executes the body of `MyIteratorMethod` until the next `yield return` statement is reached.</span></span> <span data-ttu-id="108be-136">`yield return` ステートメントによって返される式は、ループ本体による処理に対する `element` 変数の値だけでなく、<xref:System.Collections.Generic.IEnumerator%601.Current%2A> である要素の `IEnumerable<string>` プロパティも決定します。</span><span class="sxs-lookup"><span data-stu-id="108be-136">The expression returned by the `yield return` statement determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of elements, which is an `IEnumerable<string>`.</span></span>  
  
 <span data-ttu-id="108be-137">`foreach` ループの以降の各反復処理では、反復子本体の実行が中断した場所から続行し、`yield return` ステートメントに到達したときに再度停止します。</span><span class="sxs-lookup"><span data-stu-id="108be-137">On each subsequent iteration of the `foreach` loop, the execution of the iterator body continues from where it left off, again stopping when it reaches a `yield return` statement.</span></span> <span data-ttu-id="108be-138">iterator メソッドまたは `foreach` ステートメントの最後に到達すると、`yield break` ループは完了します。</span><span class="sxs-lookup"><span data-stu-id="108be-138">The `foreach` loop completes when the end of the iterator method or a `yield break` statement is reached.</span></span>  
  
## <a name="example"></a><span data-ttu-id="108be-139">例</span><span class="sxs-lookup"><span data-stu-id="108be-139">Example</span></span>  
 <span data-ttu-id="108be-140">次の例では、`yield return` ループ内に `for` ステートメントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="108be-140">The following example has a `yield return` statement that's inside a `for` loop.</span></span> <span data-ttu-id="108be-141">`foreach` 内の `Process` ステートメント本体の各反復処理では、`Power` Iterator 関数が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="108be-141">Each iteration of the `foreach` statement body in `Process` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="108be-142">Iterator 関数を呼び出すごとに、`yield return` ステートメントの次の実行に進みます。これは、`for` ループの次の反復処理で行われます。</span><span class="sxs-lookup"><span data-stu-id="108be-142">Each call to the iterator function proceeds to the next execution of the `yield return` statement, which occurs during the next iteration of the `for` loop.</span></span>  
  
 <span data-ttu-id="108be-143">Iterator メソッドの戻り値の型は <xref:System.Collections.IEnumerable> であり、これは反復子インターフェイス型です。</span><span class="sxs-lookup"><span data-stu-id="108be-143">The return type of the iterator method is <xref:System.Collections.IEnumerable>, which is an iterator interface type.</span></span> <span data-ttu-id="108be-144">Iterator メソッドが呼び出されると、数値の累乗を含む列挙可能なオブジェクトが返されます。</span><span class="sxs-lookup"><span data-stu-id="108be-144">When the iterator method is called, it returns an enumerable object that contains the powers of a number.</span></span>  
  
 <span data-ttu-id="108be-145">[!code-cs[csrefKeywordsContextual#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/yield_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="108be-145">[!code-cs[csrefKeywordsContextual#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/yield_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="108be-146">例</span><span class="sxs-lookup"><span data-stu-id="108be-146">Example</span></span>  
 <span data-ttu-id="108be-147">次の例は、反復子である `get` アクセサーを示しています。</span><span class="sxs-lookup"><span data-stu-id="108be-147">The following example demonstrates a `get` accessor that is an iterator.</span></span> <span data-ttu-id="108be-148">この例では、各 `yield return` ステートメントがユーザー定義クラスのインスタンスを返します。</span><span class="sxs-lookup"><span data-stu-id="108be-148">In the example, each `yield return` statement returns an instance of a user-defined class.</span></span>  
  
 <span data-ttu-id="108be-149">[!code-cs[csrefKeywordsContextual#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/yield_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="108be-149">[!code-cs[csrefKeywordsContextual#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/yield_2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="108be-150">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="108be-150">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="108be-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="108be-151">See Also</span></span>  
 <span data-ttu-id="108be-152">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="108be-152">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="108be-153">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="108be-153">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="108be-154">[foreach、in](../../../csharp/language-reference/keywords/foreach-in.md) </span><span class="sxs-lookup"><span data-stu-id="108be-154">[foreach, in](../../../csharp/language-reference/keywords/foreach-in.md) </span></span>  
 [<span data-ttu-id="108be-155">反復子</span><span class="sxs-lookup"><span data-stu-id="108be-155">Iterators</span></span>](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)

