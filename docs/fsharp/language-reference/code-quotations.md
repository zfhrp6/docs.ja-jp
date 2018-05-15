---
title: コード クォート (F#)
description: F# コード クォートを生成して f# のコード式をプログラムで使用することができます、言語の機能を説明します。
ms.date: 05/16/2016
ms.openlocfilehash: a6fab0364cadef1f45276267a59c694140b24a9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="code-quotations"></a><span data-ttu-id="58a68-103">コード クォート</span><span class="sxs-lookup"><span data-stu-id="58a68-103">Code Quotations</span></span>

> [!NOTE]
<span data-ttu-id="58a68-104">API リファレンスのリンクをクリックすると MSDN に移動します。</span><span class="sxs-lookup"><span data-stu-id="58a68-104">The API reference link will take you to MSDN.</span></span>  <span data-ttu-id="58a68-105">docs.microsoft.com API リファレンスは完全ではありません。</span><span class="sxs-lookup"><span data-stu-id="58a68-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="58a68-106">このトピックについて説明*コード クォート*言語の機能を生成し、f# のコード式をプログラムで使用することができます。</span><span class="sxs-lookup"><span data-stu-id="58a68-106">This topic describes *code quotations*, a language feature that enables you to generate and work with F# code expressions programmatically.</span></span> <span data-ttu-id="58a68-107">この機能では、f# コードを表す抽象構文ツリーを生成できます。</span><span class="sxs-lookup"><span data-stu-id="58a68-107">This feature lets you generate an abstract syntax tree that represents F# code.</span></span> <span data-ttu-id="58a68-108">抽象構文ツリーを走査し、アプリケーションのニーズに合わせて処理します。</span><span class="sxs-lookup"><span data-stu-id="58a68-108">The abstract syntax tree can then be traversed and processed according to the needs of your application.</span></span> <span data-ttu-id="58a68-109">たとえば、ツリーを使用して、f# コードを生成するか他の言語でコードを生成することができます。</span><span class="sxs-lookup"><span data-stu-id="58a68-109">For example, you can use the tree to generate F# code or generate code in some other language.</span></span>


## <a name="quoted-expressions"></a><span data-ttu-id="58a68-110">引用符で囲まれた式</span><span class="sxs-lookup"><span data-stu-id="58a68-110">Quoted Expressions</span></span>
<span data-ttu-id="58a68-111">A*式を引用符で囲まれた*は、プログラムの一部としてコンパイルされていない方法で区切られますが、代わりに、f# の式を表すオブジェクトにコンパイルされるコードで f# 式です。</span><span class="sxs-lookup"><span data-stu-id="58a68-111">A *quoted expression* is an F# expression in your code that is delimited in such a way that it is not compiled as part of your program, but instead is compiled into an object that represents an F# expression.</span></span> <span data-ttu-id="58a68-112">2 つの方法のいずれかで、引用符で囲まれた式をマークすることができます。 型情報または型情報がない場合。</span><span class="sxs-lookup"><span data-stu-id="58a68-112">You can mark a quoted expression in one of two ways: either with type information or without type information.</span></span> <span data-ttu-id="58a68-113">記号を使用する型情報を含める場合は、`<@`と`@>`を引用符で囲まれた式を区切るためにします。</span><span class="sxs-lookup"><span data-stu-id="58a68-113">If you want to include type information, you use the symbols `<@` and `@>` to delimit the quoted expression.</span></span> <span data-ttu-id="58a68-114">記号を使用する場合は、型情報を使用する必要はありません、`<@@`と`@@>`です。</span><span class="sxs-lookup"><span data-stu-id="58a68-114">If you do not need type information, you use the symbols `<@@` and `@@>`.</span></span> <span data-ttu-id="58a68-115">次のコードでは、型指定された、型指定されていないクォートを示します。</span><span class="sxs-lookup"><span data-stu-id="58a68-115">The following code shows typed and untyped quotations.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet501.fs)]

<span data-ttu-id="58a68-116">大規模な式ツリーを走査するは、高速は、型情報が含まれていない場合です。</span><span class="sxs-lookup"><span data-stu-id="58a68-116">Traversing a large expression tree is faster if you do not include type information.</span></span> <span data-ttu-id="58a68-117">型指定されたシンボルを含む引用符で囲まれた式の結果として得られる型は`Expr<'T>`、型パラメーターが、f# コンパイラの型推論アルゴリズムによって決定される式の型。</span><span class="sxs-lookup"><span data-stu-id="58a68-117">The resulting type of an expression quoted with the typed symbols is `Expr<'T>`, where the type parameter has the type of the expression as determined by the F# compiler's type inference algorithm.</span></span> <span data-ttu-id="58a68-118">型情報がないコード クォートを使用する場合、引用符で囲まれた式の型は非ジェネリック型に[Expr](https://msdn.microsoft.com/library/ed6a2caf-69d4-45c2-ab97-e9b3be9bce65)です。</span><span class="sxs-lookup"><span data-stu-id="58a68-118">When you use code quotations without type information, the type of the quoted expression is the non-generic type [Expr](https://msdn.microsoft.com/library/ed6a2caf-69d4-45c2-ab97-e9b3be9bce65).</span></span> <span data-ttu-id="58a68-119">呼び出すことができます、 [Raw](https://msdn.microsoft.com/library/47fb94f1-e77f-4c68-aabc-2b0ba40d59c2)プロパティを型指定された`Expr`させることが、型指定されていないクラス`Expr`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="58a68-119">You can call the [Raw](https://msdn.microsoft.com/library/47fb94f1-e77f-4c68-aabc-2b0ba40d59c2) property on the typed `Expr` class to obtain the untyped `Expr` object.</span></span>

<span data-ttu-id="58a68-120">さまざまなオブジェクトを生成する f# 式プログラム的に処理する静的メソッドがある、`Expr`クラスを使用せずには、式が引用符で囲まれています。</span><span class="sxs-lookup"><span data-stu-id="58a68-120">There are a variety of static methods that allow you to generate F# expression objects programmatically in the `Expr` class without using quoted expressions.</span></span>

<span data-ttu-id="58a68-121">コード クォートが完全な式を含める必要がありますに注意してください。</span><span class="sxs-lookup"><span data-stu-id="58a68-121">Note that a code quotation must include a complete expression.</span></span> <span data-ttu-id="58a68-122">`let`バインド、たとえば、する必要がありますバインドの名前と、バインディングを使用する追加の式の両方の定義。</span><span class="sxs-lookup"><span data-stu-id="58a68-122">For a `let` binding, for example, you need both the definition of the bound name and an additional expression that uses the binding.</span></span> <span data-ttu-id="58a68-123">冗語構文は、これは依存する式、`in`キーワード。</span><span class="sxs-lookup"><span data-stu-id="58a68-123">In verbose syntax, this is an expression that follows the `in` keyword.</span></span> <span data-ttu-id="58a68-124">トップ レベルで、モジュールで、これは、モジュールでは、次の式のみが、引用符内で明示的に必要なします。</span><span class="sxs-lookup"><span data-stu-id="58a68-124">At the top-level in a module, this is just the next expression in the module, but in a quotation, it is explicitly required.</span></span>

<span data-ttu-id="58a68-125">したがって、次の式が正しくありません。</span><span class="sxs-lookup"><span data-stu-id="58a68-125">Therefore, the following expression is not valid.</span></span>

```fsharp
// Not valid:
// <@ let f x = x + 1 @>
```

<span data-ttu-id="58a68-126">次の式は無効です。</span><span class="sxs-lookup"><span data-stu-id="58a68-126">But the following expressions are valid.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet502.fs)]

<span data-ttu-id="58a68-127">コード クォートを使用するのには、インポート宣言を追加する必要があります (を使用して、`open`キーワード) を開く、 [Microsoft.FSharp.Quotations](https://msdn.microsoft.com/library/e9ce8a3a-e00c-4190-bad5-cce52ee089b2)名前空間。</span><span class="sxs-lookup"><span data-stu-id="58a68-127">To use code quotations, you must add an import declaration (by using the `open` keyword) that opens the [Microsoft.FSharp.Quotations](https://msdn.microsoft.com/library/e9ce8a3a-e00c-4190-bad5-cce52ee089b2) namespace.</span></span>

<span data-ttu-id="58a68-128">F# PowerPack は、評価および f# 式オブジェクトを実行するためのサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="58a68-128">The F# PowerPack provides support for evaluating and executing F# expression objects.</span></span>


## <a name="expr-type"></a><span data-ttu-id="58a68-129">Expr 型</span><span class="sxs-lookup"><span data-stu-id="58a68-129">Expr Type</span></span>
<span data-ttu-id="58a68-130">インスタンス、`Expr`型が f# の式を表します。</span><span class="sxs-lookup"><span data-stu-id="58a68-130">An instance of the `Expr` type represents an F# expression.</span></span> <span data-ttu-id="58a68-131">ジェネリックと非ジェネリック`Expr`型が f# ライブラリのドキュメントに記載されています。</span><span class="sxs-lookup"><span data-stu-id="58a68-131">Both the generic and the non-generic `Expr` types are documented in the F# library documentation.</span></span> <span data-ttu-id="58a68-132">詳細については、次を参照してください。 [Microsoft.FSharp.Quotations Namespace](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.quotations-namespace-%5bfsharp%5d)と[Quotations.Expr クラス](https://msdn.microsoft.com/visualfsharpdocs/conceptual/quotations.expr-class-%5bfsharp%5d)です。</span><span class="sxs-lookup"><span data-stu-id="58a68-132">For more information, see [Microsoft.FSharp.Quotations Namespace](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.quotations-namespace-%5bfsharp%5d) and [Quotations.Expr Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/quotations.expr-class-%5bfsharp%5d).</span></span>


## <a name="splicing-operators"></a><span data-ttu-id="58a68-133">スプライス演算子</span><span class="sxs-lookup"><span data-stu-id="58a68-133">Splicing Operators</span></span>
<span data-ttu-id="58a68-134">中にスプライスするには、プログラムから、または別のコード クォートから作成した式を持つリテラル コード クォートを結合することができます。</span><span class="sxs-lookup"><span data-stu-id="58a68-134">Splicing enables you to combine literal code quotations with expressions that you have created programmatically or from another code quotation.</span></span> <span data-ttu-id="58a68-135">`%`と`%%`演算子を使用すると、コード クォートに f# の式のオブジェクトを追加します。</span><span class="sxs-lookup"><span data-stu-id="58a68-135">The `%` and `%%` operators enable you to add an F# expression object into a code quotation.</span></span> <span data-ttu-id="58a68-136">使用する、`%`型指定された引用符に型指定された式のオブジェクトを挿入する演算子です。 使用する、`%%`演算子は型指定されていないクォートに式の型指定されていないオブジェクトを挿入します。</span><span class="sxs-lookup"><span data-stu-id="58a68-136">You use the `%` operator to insert a typed expression object into a typed quotation; you use the `%%` operator to insert an untyped expression object into an untyped quotation.</span></span> <span data-ttu-id="58a68-137">両方の演算子は、単項プレフィックス演算子です。</span><span class="sxs-lookup"><span data-stu-id="58a68-137">Both operators are unary prefix operators.</span></span> <span data-ttu-id="58a68-138">したがって場合`expr`型指定されていない式のデータ型は、 `Expr`、次のコードは無効です。</span><span class="sxs-lookup"><span data-stu-id="58a68-138">Thus if `expr` is an untyped expression of type `Expr`, the following code is valid.</span></span>

```fsharp
<@@ 1 + %%expr @@>
```

<span data-ttu-id="58a68-139">場合`expr`型の型指定された引用符は、 `Expr<int>`、次のコードは無効です。</span><span class="sxs-lookup"><span data-stu-id="58a68-139">And if `expr` is a typed quotation of type `Expr<int>`, the following code is valid.</span></span>

```fsharp
<@ 1 + %expr @>
```

## <a name="example"></a><span data-ttu-id="58a68-140">例</span><span class="sxs-lookup"><span data-stu-id="58a68-140">Example</span></span>

### <a name="description"></a><span data-ttu-id="58a68-141">説明</span><span class="sxs-lookup"><span data-stu-id="58a68-141">Description</span></span>
<span data-ttu-id="58a68-142">次の例では、式オブジェクトに f# コードを配置し、式を表す f# コードを印刷するコード クォートの使用を示します。</span><span class="sxs-lookup"><span data-stu-id="58a68-142">The following example illustrates the use of code quotations to put F# code into an expression object and then print the F# code that represents the expression.</span></span> <span data-ttu-id="58a68-143">関数`println`が定義されている再帰関数を含む`print`f# の式のオブジェクトを表示する (型の`Expr`) わかりやすい形式でします。</span><span class="sxs-lookup"><span data-stu-id="58a68-143">A function `println` is defined that contains a recursive function `print` that displays an F# expression object (of type `Expr`) in a friendly format.</span></span> <span data-ttu-id="58a68-144">複数のアクティブなパターンがある、 [Microsoft.FSharp.Quotations.Patterns](https://msdn.microsoft.com/library/093944a9-c752-403a-8983-5fcd5dbf92a4)と[Microsoft.FSharp.Quotations.DerivedPatterns](https://msdn.microsoft.com/library/d2434a6e-ae7b-4f3d-b567-c162938bc9cd)モジュール式のオブジェクトを分析するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="58a68-144">There are several active patterns in the [Microsoft.FSharp.Quotations.Patterns](https://msdn.microsoft.com/library/093944a9-c752-403a-8983-5fcd5dbf92a4) and [Microsoft.FSharp.Quotations.DerivedPatterns](https://msdn.microsoft.com/library/d2434a6e-ae7b-4f3d-b567-c162938bc9cd) modules that can be used to analyze expression objects.</span></span> <span data-ttu-id="58a68-145">この例では、f# の式で表示されるすべての可能なパターンは含まれません。</span><span class="sxs-lookup"><span data-stu-id="58a68-145">This example does not include all the possible patterns that might appear in an F# expression.</span></span> <span data-ttu-id="58a68-146">パターン トリガー ワイルドカードのパターンに一致するいずれかの認識できない (`_`) を使用して表示されると、`ToString`メソッドでありで、`Expr`入力と、一致する式を追加するアクティブ パターンを確認できます。</span><span class="sxs-lookup"><span data-stu-id="58a68-146">Any unrecognized pattern triggers a match to the wildcard pattern (`_`) and is rendered by using the `ToString` method, which, on the `Expr` type, lets you know the active pattern to add to your match expression.</span></span>


### <a name="code"></a><span data-ttu-id="58a68-147">コード</span><span class="sxs-lookup"><span data-stu-id="58a68-147">Code</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet601.fs)]
    
### <a name="output"></a><span data-ttu-id="58a68-148">出力</span><span class="sxs-lookup"><span data-stu-id="58a68-148">Output</span></span>

```fsharp
fun (x:System.Int32) -> x + 1
a + 1
let f = fun (x:System.Int32) -> x + 10 in f 10
```

## <a name="example"></a><span data-ttu-id="58a68-149">例</span><span class="sxs-lookup"><span data-stu-id="58a68-149">Example</span></span>

### <a name="description"></a><span data-ttu-id="58a68-150">説明</span><span class="sxs-lookup"><span data-stu-id="58a68-150">Description</span></span>
<span data-ttu-id="58a68-151">次の 3 つのアクティブなパターンを使用することも、 [ExprShape モジュール](https://msdn.microsoft.com/library/7685150e-2432-4d39-9338-57292eff18de)少ないアクティブ パターンの式ツリーを走査します。</span><span class="sxs-lookup"><span data-stu-id="58a68-151">You can also use the three active patterns in the [ExprShape module](https://msdn.microsoft.com/library/7685150e-2432-4d39-9338-57292eff18de) to traverse expression trees with fewer active patterns.</span></span> <span data-ttu-id="58a68-152">これらのアクティブ パターンは、ツリーを走査したいが、ほとんどのノード内のすべての情報が必要ない場合に役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="58a68-152">These active patterns can be useful when you want to traverse a tree but you do not need all the information in most of the nodes.</span></span> <span data-ttu-id="58a68-153">これらのパターンを使用する場合は次の 3 つのパターンのいずれかの任意の f# 式と一致する:`ShapeVar`式が、変数の場合`ShapeLambda`場合は、式は、ラムダ式、または`ShapeCombination`式がそれ以外の場合。</span><span class="sxs-lookup"><span data-stu-id="58a68-153">When you use these patterns, any F# expression matches one of the following three patterns: `ShapeVar` if the expression is a variable, `ShapeLambda` if the expression is a lambda expression, or `ShapeCombination` if the expression is anything else.</span></span> <span data-ttu-id="58a68-154">前のコード例のようにアクティブ パターンを使用して式ツリーを走査する場合はすべて可能な f# の式の型を処理する多数の複数のパターンを使用する必要し、コードが複雑になります。</span><span class="sxs-lookup"><span data-stu-id="58a68-154">If you traverse an expression tree by using the active patterns as in the previous code example, you have to use many more patterns to handle all possible F# expression types, and your code will be more complex.</span></span> <span data-ttu-id="58a68-155">詳細については、次を参照してください。 [ExprShape.ShapeVar&#124;ShapeLambda&#124;ShapeCombination アクティブ パターン](https://msdn.microsoft.com/visualfsharpdocs/conceptual/exprshape.shapevarhshapelambdahshapecombination-active-pattern-%5bfsharp%5d)です。</span><span class="sxs-lookup"><span data-stu-id="58a68-155">For more information, see [ExprShape.ShapeVar&#124;ShapeLambda&#124;ShapeCombination Active Pattern](https://msdn.microsoft.com/visualfsharpdocs/conceptual/exprshape.shapevarhshapelambdahshapecombination-active-pattern-%5bfsharp%5d).</span></span>

<span data-ttu-id="58a68-156">次のコード例より複雑な走査の基礎として使用できます。</span><span class="sxs-lookup"><span data-stu-id="58a68-156">The following code example can be used as a basis for more complex traversals.</span></span> <span data-ttu-id="58a68-157">このコードを関数呼び出しを含む式を式ツリーを作成`add`です。</span><span class="sxs-lookup"><span data-stu-id="58a68-157">In this code, an expression tree is created for an expression that involves a function call, `add`.</span></span> <span data-ttu-id="58a68-158">[SpecificCall](https://msdn.microsoft.com/library/05a77b21-20fe-4b9a-8e07-aa999538198d)アクティブ パターンが任意の呼び出しを検出するために使用される`add`式ツリーでします。</span><span class="sxs-lookup"><span data-stu-id="58a68-158">The [SpecificCall](https://msdn.microsoft.com/library/05a77b21-20fe-4b9a-8e07-aa999538198d) active pattern is used to detect any call to `add` in the expression tree.</span></span> <span data-ttu-id="58a68-159">このアクティブ パターンへの呼び出しの引数の代入、`exprList`値。</span><span class="sxs-lookup"><span data-stu-id="58a68-159">This active pattern assigns the arguments of the call to the `exprList` value.</span></span> <span data-ttu-id="58a68-160">ここでは、ある 2 つだけこれらが引き出されているため、関数の呼び出しの引数に対して再帰的にします。</span><span class="sxs-lookup"><span data-stu-id="58a68-160">In this case, there are only two, so these are pulled out and the function is called recursively on the arguments.</span></span> <span data-ttu-id="58a68-161">呼び出しを表すコード クォートに結果が挿入されます`mul`スプライス演算子を使用して (`%%`)。</span><span class="sxs-lookup"><span data-stu-id="58a68-161">The results are inserted into a code quotation that represents a call to `mul` by using the splice operator (`%%`).</span></span> <span data-ttu-id="58a68-162">`println`前の例の関数を使用して、結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="58a68-162">The `println` function from the previous example is used to display the results.</span></span>

<span data-ttu-id="58a68-163">その他のアクティブ パターンの分岐で、コードだけを再生成は同じ式ツリーのため結果の式でのみ変更がから変更`add`に`mul`です。</span><span class="sxs-lookup"><span data-stu-id="58a68-163">The code in the other active pattern branches just regenerates the same expression tree, so the only change in the resulting expression is the change from `add` to `mul`.</span></span>


### <a name="code"></a><span data-ttu-id="58a68-164">コード</span><span class="sxs-lookup"><span data-stu-id="58a68-164">Code</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet701.fs)]
    
### <a name="output"></a><span data-ttu-id="58a68-165">出力</span><span class="sxs-lookup"><span data-stu-id="58a68-165">Output</span></span>

```fsharp
1 + Module1.add(2,Module1.add(3,4))
1 + Module1.mul(2,Module1.mul(3,4))
```

## <a name="see-also"></a><span data-ttu-id="58a68-166">関連項目</span><span class="sxs-lookup"><span data-stu-id="58a68-166">See Also</span></span>
[<span data-ttu-id="58a68-167">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="58a68-167">F# Language Reference</span></span>](index.md)

