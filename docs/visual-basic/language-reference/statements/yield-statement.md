---
title: "Yield ステートメント (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Yield
helpviewer_keywords:
- iterators, Yield statement [Visual Basic]
- iterators [Visual Basic]
- Yield statement [Visual Basic]
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 99f5129d5cb43cddfb17731f337a72fae22d3626
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="yield-statement-visual-basic"></a><span data-ttu-id="ff64e-102">Yield ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ff64e-102">Yield Statement (Visual Basic)</span></span>
<span data-ttu-id="ff64e-103">コレクションの次の要素を送信、`For Each...Next`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="ff64e-103">Sends the next element of a collection to a `For Each...Next` statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff64e-104">構文</span><span class="sxs-lookup"><span data-stu-id="ff64e-104">Syntax</span></span>  
  
```  
Yield expression  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ff64e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff64e-105">Parameters</span></span>  
  
|<span data-ttu-id="ff64e-106">用語</span><span class="sxs-lookup"><span data-stu-id="ff64e-106">Term</span></span>|<span data-ttu-id="ff64e-107">定義</span><span class="sxs-lookup"><span data-stu-id="ff64e-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="ff64e-108">必須です。</span><span class="sxs-lookup"><span data-stu-id="ff64e-108">Required.</span></span> <span data-ttu-id="ff64e-109">反復子関数の型に暗黙的に変換される式または`Get`アクセサーが含まれている`Yield`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="ff64e-109">An expression that is implicitly convertible to the type of the iterator function or `Get` accessor that contains the `Yield` statement.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff64e-110">コメント</span><span class="sxs-lookup"><span data-stu-id="ff64e-110">Remarks</span></span>  
 <span data-ttu-id="ff64e-111">`Yield`ステートメントは、一度にコレクションの 1 つの要素を返します。</span><span class="sxs-lookup"><span data-stu-id="ff64e-111">The `Yield` statement returns one element of a collection at a time.</span></span> <span data-ttu-id="ff64e-112">`Yield`ステートメントが iterator 関数に含まれるまたは`Get`アクセサーをコレクションに対するカスタム イテレーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="ff64e-112">The `Yield` statement is included in an iterator function or `Get` accessor, which perform custom iterations over a collection.</span></span>  
  
 <span data-ttu-id="ff64e-113">使用して反復子関数を使用する、[ごとにしています.次のステートメントの](../../../visual-basic/language-reference/statements/for-each-next-statement.md)または LINQ クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="ff64e-113">You consume an iterator function by using a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md) or a LINQ query.</span></span> <span data-ttu-id="ff64e-114">各反復処理、`For Each`ループが反復子関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="ff64e-114">Each iteration of the `For Each` loop calls the iterator function.</span></span> <span data-ttu-id="ff64e-115">ときに、`Yield`ステートメントが iterator 関数に到達`expression`が返されたコードの現在の場所が保持されます。</span><span class="sxs-lookup"><span data-stu-id="ff64e-115">When a `Yield` statement is reached in the iterator function, `expression` is returned, and the current location in code is retained.</span></span> <span data-ttu-id="ff64e-116">次回、Iterator 関数が呼び出されると、この位置から実行が再開されます。</span><span class="sxs-lookup"><span data-stu-id="ff64e-116">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="ff64e-117">型からの暗黙的な変換が存在する必要があります`expression`で、`Yield`ステートメント、反復子の戻り値の型をします。</span><span class="sxs-lookup"><span data-stu-id="ff64e-117">An implicit conversion must exist from the type of `expression` in the `Yield` statement to the return type of the iterator.</span></span>  
  
 <span data-ttu-id="ff64e-118">使用することができます、`Exit Function`または`Return`ステートメント、反復を終了します。</span><span class="sxs-lookup"><span data-stu-id="ff64e-118">You can use an `Exit Function` or `Return` statement to end the iteration.</span></span>  
  
 <span data-ttu-id="ff64e-119">「生成」予約語ではないあり、特別な意味で使用されている場合にのみ、`Iterator`関数または`Get`アクセサー。</span><span class="sxs-lookup"><span data-stu-id="ff64e-119">"Yield" is not a reserved word and has special meaning only when it is used in an `Iterator` function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="ff64e-120">反復子関数の詳細については、`Get`アクセサーを参照してください[反復子](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)です。</span><span class="sxs-lookup"><span data-stu-id="ff64e-120">For more information about iterator functions and `Get` accessors, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
## <a name="iterator-functions-and-get-accessors"></a><span data-ttu-id="ff64e-121">反復子関数と Get アクセサー</span><span class="sxs-lookup"><span data-stu-id="ff64e-121">Iterator Functions and Get Accessors</span></span>  
 <span data-ttu-id="ff64e-122">反復子関数の宣言または`Get`アクセサーは、次の要件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="ff64e-122">The declaration of an iterator function or `Get` accessor must meet the following requirements:</span></span>  
  
-   <span data-ttu-id="ff64e-123">含める必要があります、[反復子](../../../visual-basic/language-reference/modifiers/iterator.md)修飾子です。</span><span class="sxs-lookup"><span data-stu-id="ff64e-123">It must include an [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md) modifier.</span></span>  
  
-   <span data-ttu-id="ff64e-124">戻り値の型は、<xref:System.Collections.IEnumerable>、<xref:System.Collections.Generic.IEnumerable%601>、<xref:System.Collections.IEnumerator>、または <xref:System.Collections.Generic.IEnumerator%601> であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="ff64e-124">The return type must be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
-   <span data-ttu-id="ff64e-125">これには指定できません`ByRef`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="ff64e-125">It cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="ff64e-126">Iterator 関数は、イベント、コンス トラクター、静的コンス トラクターまたは静的のデストラクターで発生することはできません。</span><span class="sxs-lookup"><span data-stu-id="ff64e-126">An iterator function cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="ff64e-127">Iterator 関数では、匿名の関数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ff64e-127">An iterator function can be an anonymous function.</span></span> <span data-ttu-id="ff64e-128">詳細については、「[反復子](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ff64e-128">For more information, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="ff64e-129">例外処理</span><span class="sxs-lookup"><span data-stu-id="ff64e-129">Exception Handling</span></span>  
 <span data-ttu-id="ff64e-130">A`Yield`内のステートメントに含めることができます、`Try`のブロック、[を再試行してください.キャッチしてください.Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="ff64e-130">A `Yield` statement can be inside a `Try` block of a [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span> <span data-ttu-id="ff64e-131">A`Try`を持つブロック、`Yield`ステートメントが持つことができます`Catch`をブロックしてができます、`Finally`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="ff64e-131">A `Try` block that has a `Yield` statement can have `Catch` blocks, and can have a `Finally` block.</span></span>  
  
 <span data-ttu-id="ff64e-132">A`Yield`ステートメント内で使用できない、`Catch`ブロックまたは`Finally`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="ff64e-132">A `Yield` statement cannot be inside a `Catch` block or a `Finally` block.</span></span>  
  
 <span data-ttu-id="ff64e-133">場合、`For Each`本体 (関数の外側で、反復子)、例外がスロー、 `Catch` iterator 関数内のブロックが実行されていないが、 `Finally` iterator 関数内のブロックを実行します。</span><span class="sxs-lookup"><span data-stu-id="ff64e-133">If the `For Each` body (outside of the iterator function) throws an exception, a `Catch` block in the iterator function is not executed, but a `Finally` block in the iterator function is executed.</span></span> <span data-ttu-id="ff64e-134">A`Catch`反復子関数の内側のブロックは、iterator 関数内で発生する例外のみをキャッチします。</span><span class="sxs-lookup"><span data-stu-id="ff64e-134">A `Catch` block inside an iterator function catches only exceptions that occur inside the iterator function.</span></span>  
  
## <a name="technical-implementation"></a><span data-ttu-id="ff64e-135">技術的な実装</span><span class="sxs-lookup"><span data-stu-id="ff64e-135">Technical Implementation</span></span>  
 <span data-ttu-id="ff64e-136">次のコードを返します、 `IEnumerable (Of String)` iterator 関数からの要素を反復処理し、`IEnumerable (Of String)`です。</span><span class="sxs-lookup"><span data-stu-id="ff64e-136">The following code returns an `IEnumerable (Of String)` from an iterator function and then iterates through the elements of the `IEnumerable (Of String)`.</span></span>  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 <span data-ttu-id="ff64e-137">呼び出し`MyIteratorFunction`関数の本体は実行されません。</span><span class="sxs-lookup"><span data-stu-id="ff64e-137">The call to `MyIteratorFunction` doesn't execute the body of the function.</span></span> <span data-ttu-id="ff64e-138">この呼び出しでは、`IEnumerable(Of String)` が `elements` 変数に返されます。</span><span class="sxs-lookup"><span data-stu-id="ff64e-138">Instead the call returns an `IEnumerable(Of String)` into the `elements` variable.</span></span>  
  
 <span data-ttu-id="ff64e-139">`For Each` ループの反復処理では、<xref:System.Collections.IEnumerator.MoveNext%2A> について `elements` メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="ff64e-139">On an iteration of the `For Each` loop, the <xref:System.Collections.IEnumerator.MoveNext%2A> method is called for `elements`.</span></span> <span data-ttu-id="ff64e-140">この呼び出しでは、次の `MyIteratorFunction` ステートメントに到達するまで、`Yield` の本体が実行されます。</span><span class="sxs-lookup"><span data-stu-id="ff64e-140">This call executes the body of `MyIteratorFunction` until the next `Yield` statement is reached.</span></span> <span data-ttu-id="ff64e-141">`Yield`ステートメントの値だけでなくを決定する式が返されます、`element`ループの本体によって消費の変数も、<xref:System.Collections.Generic.IEnumerator%601.Current%2A>要素のプロパティは、`IEnumerable (Of String)`です。</span><span class="sxs-lookup"><span data-stu-id="ff64e-141">The `Yield` statement returns an expression that determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of elements, which is an `IEnumerable (Of String)`.</span></span>  
  
 <span data-ttu-id="ff64e-142">`For Each` ループの以降の各反復処理では、反復子本体の実行が中断した場所から続行し、`Yield` ステートメントに到達したときに再度停止します。</span><span class="sxs-lookup"><span data-stu-id="ff64e-142">On each subsequent iteration of the `For Each` loop, the execution of the iterator body continues from where it left off, again stopping when it reaches a `Yield` statement.</span></span> <span data-ttu-id="ff64e-143">`For Each`ループが完了するときに、反復子関数の末尾または`Return`または`Exit Function`ステートメントが到達します。</span><span class="sxs-lookup"><span data-stu-id="ff64e-143">The `For Each` loop completes when the end of the iterator function or a `Return` or `Exit Function` statement is reached.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff64e-144">例</span><span class="sxs-lookup"><span data-stu-id="ff64e-144">Example</span></span>  
 <span data-ttu-id="ff64e-145">次の例は、`Yield`内にあるステートメント、[をしています.[次へ]](../../../visual-basic/language-reference/statements/for-next-statement.md)ループします。</span><span class="sxs-lookup"><span data-stu-id="ff64e-145">The following example has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="ff64e-146">各反復処理、[各](../../../visual-basic/language-reference/statements/for-each-next-statement.md)ステートメント本体で`Main`への呼び出しを作成、 `Power` iterator 関数。</span><span class="sxs-lookup"><span data-stu-id="ff64e-146">Each iteration of the [For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="ff64e-147">Iterator 関数を呼び出すごとに、`Yield` ステートメントの次の実行に進みます。これは、`For…Next` ループの次の反復処理で行われます。</span><span class="sxs-lookup"><span data-stu-id="ff64e-147">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 <span data-ttu-id="ff64e-148">Iterator メソッドの戻り値の型は<xref:System.Collections.Generic.IEnumerable%601>、反復子インターフェイス型です。</span><span class="sxs-lookup"><span data-stu-id="ff64e-148">The return type of the iterator method is <xref:System.Collections.Generic.IEnumerable%601>, an iterator interface type.</span></span> <span data-ttu-id="ff64e-149">Iterator メソッドが呼び出されると、数値の累乗を含む列挙可能なオブジェクトが返されます。</span><span class="sxs-lookup"><span data-stu-id="ff64e-149">When the iterator method is called, it returns an enumerable object that contains the powers of a number.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/yield-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="ff64e-150">例</span><span class="sxs-lookup"><span data-stu-id="ff64e-150">Example</span></span>  
 <span data-ttu-id="ff64e-151">次の例は、反復子である `Get` アクセサーを示しています。</span><span class="sxs-lookup"><span data-stu-id="ff64e-151">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="ff64e-152">プロパティ宣言が含まれる、`Iterator`修飾子です。</span><span class="sxs-lookup"><span data-stu-id="ff64e-152">The property declaration includes an `Iterator` modifier.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/yield-statement_2.vb)]  
  
 <span data-ttu-id="ff64e-153">その他の例では、次を参照してください。[反復子](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)です。</span><span class="sxs-lookup"><span data-stu-id="ff64e-153">For additional examples, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff64e-154">関連項目</span><span class="sxs-lookup"><span data-stu-id="ff64e-154">See Also</span></span>  
 [<span data-ttu-id="ff64e-155">反復子</span><span class="sxs-lookup"><span data-stu-id="ff64e-155">Iterators</span></span>](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)  
 [<span data-ttu-id="ff64e-156">ステートメント</span><span class="sxs-lookup"><span data-stu-id="ff64e-156">Statements</span></span>](../../../visual-basic/language-reference/statements/index.md)
