---
title: "パターン マッチ (F#)"
description: "パターンを f# で使用論理構造とデータを比較し、構成要素にデータを分解または、データから情報を抽出する方法について説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 5562ee98-e2f1-4dcd-8e2f-16ae27baaade
ms.openlocfilehash: 7c7a3110a8f34c0c96c12d4584010a9ac4b485fa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="pattern-matching"></a><span data-ttu-id="3c5fc-104">パターン マッチ</span><span class="sxs-lookup"><span data-stu-id="3c5fc-104">Pattern Matching</span></span>

<span data-ttu-id="3c5fc-105">パターンは、入力データの変換規則です。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-105">Patterns are rules for transforming input data.</span></span> <span data-ttu-id="3c5fc-106">データを論理構造と比較したり、データを構成要素に分解したり、さまざまな方法でデータから情報を抽出したりするために、F# 言語全体で使用されます。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-106">They are used throughout the F# language to compare data with a logical structure or structures, decompose data into constituent parts, or extract information from data in various ways.</span></span>


## <a name="remarks"></a><span data-ttu-id="3c5fc-107">コメント</span><span class="sxs-lookup"><span data-stu-id="3c5fc-107">Remarks</span></span>
<span data-ttu-id="3c5fc-108">パターンは、`match` 式などの多くの言語構成要素で使用されます。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-108">Patterns are used in many language constructs, such as the `match` expression.</span></span> <span data-ttu-id="3c5fc-109">`let` 束縛、ラムダ式、および `try...with` 式に関連付けられている例外ハンドラーで関数の引数を処理する場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-109">They are used when you are processing arguments for functions in `let` bindings, lambda expressions, and in the exception handlers associated with the `try...with` expression.</span></span> <span data-ttu-id="3c5fc-110">詳細については、次を参照してください[Match 式](match-expressions.md)、 [let 束縛](functions/let-bindings.md)、[ラムダ式:、`fun`キーワード](functions/lambda-expressions-the-fun-keyword.md)、および[例外:、 。`try...with`式](exception-handling/the-try-with-expression.md)です。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-110">For more information, see [Match Expressions](match-expressions.md), [let Bindings](functions/let-bindings.md), [Lambda Expressions: The `fun` Keyword](functions/lambda-expressions-the-fun-keyword.md), and [Exceptions: The `try...with` Expression](exception-handling/the-try-with-expression.md).</span></span>

<span data-ttu-id="3c5fc-111">たとえば、`match`式では、*パターン*がパイプ記号の後に続きます。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-111">For example, in the `match` expression, the *pattern* is what follows the pipe symbol.</span></span>

```fsharp
match expression with
| pattern [ when condition ] -> result-expression
...
```

<span data-ttu-id="3c5fc-112">各パターンは、なんらかの方法で入力を変換する際の規則として機能します。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-112">Each pattern acts as a rule for transforming input in some way.</span></span> <span data-ttu-id="3c5fc-113">`match` 式では、各パターンが順に調べられ、入力データにパターンとの互換性があるかどうかが確認されます。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-113">In the `match` expression, each pattern is examined in turn to see if the input data is compatible with the pattern.</span></span> <span data-ttu-id="3c5fc-114">一致が見つかった場合は、結果の式が実行されます。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-114">If a match is found, the result expression is executed.</span></span> <span data-ttu-id="3c5fc-115">一致が見つからなかった場合は、次のパターン規則がテストされます。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-115">If a match is not found, the next pattern rule is tested.</span></span> <span data-ttu-id="3c5fc-116">省略可能な場合に*条件*」で説明されて一部[Match 式](match-expressions.md)です。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-116">The optional when *condition* part is explained in [Match Expressions](match-expressions.md).</span></span>

<span data-ttu-id="3c5fc-117">サポートされているパターンを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-117">Supported patterns are shown in the following table.</span></span> <span data-ttu-id="3c5fc-118">実行時に、表に示されている順序で次の各パターンに対して入力がテストされます。パターンは、コードに示されているとおりに先頭から末尾へ、各行のパターンの左から右へ、再帰的に適用されます。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-118">At run time, the input is tested against each of the following patterns in the order listed in the table, and patterns are applied recursively, from first to last as they appear in your code, and from left to right for the patterns on each line.</span></span>

|<span data-ttu-id="3c5fc-119">名前</span><span class="sxs-lookup"><span data-stu-id="3c5fc-119">Name</span></span>|<span data-ttu-id="3c5fc-120">説明</span><span class="sxs-lookup"><span data-stu-id="3c5fc-120">Description</span></span>|<span data-ttu-id="3c5fc-121">例</span><span class="sxs-lookup"><span data-stu-id="3c5fc-121">Example</span></span>|
|----|-----------|-------|
|<span data-ttu-id="3c5fc-122">定数パターン</span><span class="sxs-lookup"><span data-stu-id="3c5fc-122">Constant pattern</span></span>|<span data-ttu-id="3c5fc-123">数値、文字、リテラル文字列、列挙定数、または定義済みのリテラル識別子</span><span class="sxs-lookup"><span data-stu-id="3c5fc-123">Any numeric, character, or string literal, an enumeration constant, or a defined literal identifier</span></span>|<span data-ttu-id="3c5fc-124">`1.0`, `"test"`, `30`, `Color.Red`</span><span class="sxs-lookup"><span data-stu-id="3c5fc-124">`1.0`, `"test"`, `30`, `Color.Red`</span></span>|
|<span data-ttu-id="3c5fc-125">識別子パターン</span><span class="sxs-lookup"><span data-stu-id="3c5fc-125">Identifier pattern</span></span>|<span data-ttu-id="3c5fc-126">判別共用体のケース値、例外ラベル、またはアクティブ パターンのケース</span><span class="sxs-lookup"><span data-stu-id="3c5fc-126">A case value of a discriminated union, an exception label, or an active pattern case</span></span>|`Some(x)`<br /><br />`Failure(msg)`|
|<span data-ttu-id="3c5fc-127">変数パターン</span><span class="sxs-lookup"><span data-stu-id="3c5fc-127">Variable pattern</span></span>|<span data-ttu-id="3c5fc-128">*identifier*</span><span class="sxs-lookup"><span data-stu-id="3c5fc-128">*identifier*</span></span>|`a`|
|<span data-ttu-id="3c5fc-129">`as` パターン</span><span class="sxs-lookup"><span data-stu-id="3c5fc-129">`as` pattern</span></span>|<span data-ttu-id="3c5fc-130">*パターン*として*識別子*</span><span class="sxs-lookup"><span data-stu-id="3c5fc-130">*pattern* as *identifier*</span></span>|`(a, b) as tuple1`|
|<span data-ttu-id="3c5fc-131">OR パターン</span><span class="sxs-lookup"><span data-stu-id="3c5fc-131">OR pattern</span></span>|<span data-ttu-id="3c5fc-132">*pattern1* &#124;です。*pattern2*</span><span class="sxs-lookup"><span data-stu-id="3c5fc-132">*pattern1* &#124; *pattern2*</span></span>|<code>([h] &#124; [h; _])</code>|
|<span data-ttu-id="3c5fc-133">AND パターン</span><span class="sxs-lookup"><span data-stu-id="3c5fc-133">AND pattern</span></span>|<span data-ttu-id="3c5fc-134">*pattern1* &amp; *pattern2*</span><span class="sxs-lookup"><span data-stu-id="3c5fc-134">*pattern1* &amp; *pattern2*</span></span>|`(a, b) & (_, "test")`|
|<span data-ttu-id="3c5fc-135">Cons パターン</span><span class="sxs-lookup"><span data-stu-id="3c5fc-135">Cons pattern</span></span>|<span data-ttu-id="3c5fc-136">*識別子*::*一覧識別子*</span><span class="sxs-lookup"><span data-stu-id="3c5fc-136">*identifier* :: *list-identifier*</span></span>|`h :: t`|
|<span data-ttu-id="3c5fc-137">リスト パターン</span><span class="sxs-lookup"><span data-stu-id="3c5fc-137">List pattern</span></span>|<span data-ttu-id="3c5fc-138">[ *pattern_1*;... です。*pattern_n* ]</span><span class="sxs-lookup"><span data-stu-id="3c5fc-138">[ *pattern_1*; ... ; *pattern_n* ]</span></span>|`[ a; b; c ]`|
|<span data-ttu-id="3c5fc-139">配列パターン</span><span class="sxs-lookup"><span data-stu-id="3c5fc-139">Array pattern</span></span>|<span data-ttu-id="3c5fc-140">[&#124;です。*pattern_1*;.. です。*pattern_n* &#124;です]。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-140">[&#124; *pattern_1*; ..; *pattern_n* &#124;]</span></span>|<code>[&#124; a; b; c &#124;]</code>|
|<span data-ttu-id="3c5fc-141">かっこで囲まれたパターン</span><span class="sxs-lookup"><span data-stu-id="3c5fc-141">Parenthesized pattern</span></span>|<span data-ttu-id="3c5fc-142">(*パターン*)</span><span class="sxs-lookup"><span data-stu-id="3c5fc-142">( *pattern* )</span></span>|`( a )`|
|<span data-ttu-id="3c5fc-143">タプル パターン</span><span class="sxs-lookup"><span data-stu-id="3c5fc-143">Tuple pattern</span></span>|<span data-ttu-id="3c5fc-144">( *pattern_1*,..., *pattern_n* )</span><span class="sxs-lookup"><span data-stu-id="3c5fc-144">( *pattern_1*, ... , *pattern_n* )</span></span>|`( a, b )`|
|<span data-ttu-id="3c5fc-145">レコード パターン</span><span class="sxs-lookup"><span data-stu-id="3c5fc-145">Record pattern</span></span>|<span data-ttu-id="3c5fc-146">{ *identifier1* = *pattern_1*;... です。*identifier_n* = *pattern_n* }</span><span class="sxs-lookup"><span data-stu-id="3c5fc-146">{ *identifier1* = *pattern_1*; ... ; *identifier_n* = *pattern_n* }</span></span>|`{ Name = name; }`|
|<span data-ttu-id="3c5fc-147">ワイルドカード パターン</span><span class="sxs-lookup"><span data-stu-id="3c5fc-147">Wildcard pattern</span></span>|<span data-ttu-id="3c5fc-148">_</span><span class="sxs-lookup"><span data-stu-id="3c5fc-148">_</span></span>|`_`|
|<span data-ttu-id="3c5fc-149">型の注釈が指定されたパターン</span><span class="sxs-lookup"><span data-stu-id="3c5fc-149">Pattern together with type annotation</span></span>|<span data-ttu-id="3c5fc-150">*パターン*:*型*</span><span class="sxs-lookup"><span data-stu-id="3c5fc-150">*pattern* : *type*</span></span>|`a : int`|
|<span data-ttu-id="3c5fc-151">型テスト パターン</span><span class="sxs-lookup"><span data-stu-id="3c5fc-151">Type test pattern</span></span>|<span data-ttu-id="3c5fc-152">:?</span><span class="sxs-lookup"><span data-stu-id="3c5fc-152">:?</span></span> <span data-ttu-id="3c5fc-153">*型*[として*識別子*]</span><span class="sxs-lookup"><span data-stu-id="3c5fc-153">*type* [ as *identifier* ]</span></span>|`:? System.DateTime as dt`|
|<span data-ttu-id="3c5fc-154">null パターン</span><span class="sxs-lookup"><span data-stu-id="3c5fc-154">Null pattern</span></span>|<span data-ttu-id="3c5fc-155">null</span><span class="sxs-lookup"><span data-stu-id="3c5fc-155">null</span></span>|`null`|

## <a name="constant-patterns"></a><span data-ttu-id="3c5fc-156">定数パターン</span><span class="sxs-lookup"><span data-stu-id="3c5fc-156">Constant Patterns</span></span>
<span data-ttu-id="3c5fc-157">定数パターンは、数値、文字、リテラル文字列、列挙定数 (列挙型名が含まれる) です。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-157">Constant patterns are numeric, character, and string literals, enumeration constants (with the enumeration type name included).</span></span> <span data-ttu-id="3c5fc-158">定数パターンのみが含まれる `match` 式は、他の言語の case ステートメントと比較できます。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-158">A `match` expression that has only constant patterns can be compared to a case statement in other languages.</span></span> <span data-ttu-id="3c5fc-159">入力がリテラル値と比較され、値が等しい場合にはパターンが一致します。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-159">The input is compared with the literal value and the pattern matches if the values are equal.</span></span> <span data-ttu-id="3c5fc-160">リテラルの型に、入力の型との互換性があることが必要です。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-160">The type of the literal must be compatible with the type of the input.</span></span>

<span data-ttu-id="3c5fc-161">リテラル パターンの使用例を次に示します。変数パターンと OR パターンも使用します。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-161">The following example demonstrates the use of literal patterns, and also uses a variable pattern and an OR pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4801.fs)]

<span data-ttu-id="3c5fc-162">リテラル パターンにはこの他に、列挙定数に基づくパターンもあります。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-162">Another example of a literal pattern is a pattern based on enumeration constants.</span></span> <span data-ttu-id="3c5fc-163">列挙定数を使用するときは、列挙型名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-163">You must specify the enumeration type name when you use enumeration constants.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4802.fs)]

## <a name="identifier-patterns"></a><span data-ttu-id="3c5fc-164">識別子パターン</span><span class="sxs-lookup"><span data-stu-id="3c5fc-164">Identifier Patterns</span></span>
<span data-ttu-id="3c5fc-165">パターンが有効な識別子になる文字列の場合は、識別子の形式でパターンの照合方法が決まります。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-165">If the pattern is a string of characters that forms a valid identifier, the form of the identifier determines how the pattern is matched.</span></span> <span data-ttu-id="3c5fc-166">識別子が 2 文字以上で、大文字で始まる場合は、コンパイラが識別子パターンとの照合を試みます。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-166">If the identifier is longer than a single character and starts with an uppercase character, the compiler tries to make a match to the identifier pattern.</span></span> <span data-ttu-id="3c5fc-167">このパターンの識別子は、Literal 属性が指定された値、判別共用体のケース、例外識別子、またはアクティブ パターンのケースです。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-167">The identifier for this pattern could be a value marked with the Literal attribute, a discriminated union case, an exception identifier, or an active pattern case.</span></span> <span data-ttu-id="3c5fc-168">一致する識別子が見つからない場合は、照合が失敗し、次のパターン規則の変数パターンが入力と比較されます。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-168">If no matching identifier is found, the match fails and the next pattern rule, the variable pattern, is compared to the input.</span></span>

<span data-ttu-id="3c5fc-169">判別共用体パターンは、単純な名前付きケースであるか、値またはタプル (複数の値を含む) を含むかのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-169">Discriminated union patterns can be simple named cases or they can have a value, or a tuple containing multiple values.</span></span> <span data-ttu-id="3c5fc-170">値が存在する場合は、値の識別子を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-170">If there is a value, you must specify an identifier for the value.</span></span> <span data-ttu-id="3c5fc-171">タプルの場合は、タプルの各要素の識別子、または 1 つ以上の名前付きの共用体フィールドのフィールド名の識別子、を持つタプル パターンを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-171">In the case of a tuple, you must supply a tuple pattern with an identifier for each element of the tuple or an identifier with a field name for one or more named union fields.</span></span> <span data-ttu-id="3c5fc-172">例については、このセクションのコード例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-172">See the code examples in this section for examples.</span></span>

<span data-ttu-id="3c5fc-173">`option` 型は、`Some` と `None` の 2 つのケースを持つ判別共用体です。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-173">The `option` type is a discriminated union that has two cases, `Some` and `None`.</span></span> <span data-ttu-id="3c5fc-174">一方のケース (`Some`) には値が含まれますが、もう一方のケース (`None`) は単なる名前付きケースです。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-174">One case (`Some`) has a value, but the other (`None`) is just a named case.</span></span> <span data-ttu-id="3c5fc-175">したがって、`Some` には、`Some` ケースに関連付けられた値の変数が必要ですが、`None` は単体で使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-175">Therefore, `Some` needs to have a variable for the value associated with the `Some` case, but `None` must appear by itself.</span></span> <span data-ttu-id="3c5fc-176">次のコードでは、`var1` 変数に、`Some` ケースとの照合で取得された値が指定されます。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-176">In the following code, the variable `var1` is given the value that is obtained by matching to the `Some` case.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4803.fs)]

<span data-ttu-id="3c5fc-177">次の例では、`PersonName` 判別共用体に、名前に使用できる形式を表す文字列および文字が混在しています。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-177">In the following example, the `PersonName` discriminated union contains a mixture of strings and characters that represent possible forms of names.</span></span> <span data-ttu-id="3c5fc-178">判別共用体のケースは `FirstOnly`、`LastOnly`、および `FirstLast` です。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-178">The cases of the discriminated union are `FirstOnly`, `LastOnly`, and `FirstLast`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4804.fs)]

<span data-ttu-id="3c5fc-179">名前付きフィールドがある判別共用体の場合、名前付きフィールドの値を抽出するために等号 (=) を使用します。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-179">For discriminated unions that have named fields, you use the equals sign (=) to extract the value of a named field.</span></span> <span data-ttu-id="3c5fc-180">たとえば、次のような宣言を持つ判別共用体について検討します。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-180">For example, consider a discriminated union with a declaration like the following.</span></span>

```fsharp
type Shape =
    | Rectangle of height : float * width : float
    | Circle of radius : float
```

<span data-ttu-id="3c5fc-181">次のようにパターン一致式の中で名前付きフィールドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-181">You can use the named fields in a pattern matching expression as follows.</span></span>

```fsharp
let matchShape shape =
    match shape with
    | Rectangle(height = h) -> printfn "Rectangle with length %f" h
    | Circle(r) -> printfn "Circle with radius %f" r
```

<span data-ttu-id="3c5fc-182">前の例では、名前付きフィールドの使用は省略可能であり、したがって、`Circle(r)` と `Circle(radius = r)` は同じ結果になります。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-182">The use of the named field is optional, so in the previous example, both `Circle(r)` and `Circle(radius = r)` have the same effect.</span></span>

<span data-ttu-id="3c5fc-183">複数のフィールドを指定する場合は、区切り記号としてセミコロン (;) を使用します。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-183">When you specify multiple fields, use the semicolon (;) as a separator.</span></span>

```
match shape with
| Rectangle(height = h; width = w) -> printfn "Rectangle with height %f and width %f" h w
| _ -> ()
```

<span data-ttu-id="3c5fc-184">アクティブ パターンを使用すると、より複雑なカスタム パターン マッチを定義できます。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-184">Active patterns enable you to define more complex custom pattern matching.</span></span> <span data-ttu-id="3c5fc-185">アクティブ パターンの詳細については、次を参照してください。[アクティブ パターン](active-patterns.md)です。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-185">For more information about active patterns, see [Active Patterns](active-patterns.md).</span></span>

<span data-ttu-id="3c5fc-186">識別子が例外であるケースは、例外ハンドラーのコンテキストのパターン マッチで使用されます。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-186">The case in which the identifier is an exception is used in pattern matching in the context of exception handlers.</span></span> <span data-ttu-id="3c5fc-187">例外処理では、照合するパターンについては、次を参照してください。[例外:、`try...with`式](exception-handling/the-try-with-expression.md)です。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-187">For information about pattern matching in exception handling, see [Exceptions: The `try...with` Expression](exception-handling/the-try-with-expression.md).</span></span>


## <a name="variable-patterns"></a><span data-ttu-id="3c5fc-188">変数パターン</span><span class="sxs-lookup"><span data-stu-id="3c5fc-188">Variable Patterns</span></span>
<span data-ttu-id="3c5fc-189">変数パターンでは、照合される値が変数名に割り当てられ、その変数名を、`->` 記号の右側の実行式で使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-189">The variable pattern assigns the value being matched to a variable name, which is then available for use in the execution expression to the right of the `->` symbol.</span></span> <span data-ttu-id="3c5fc-190">変数パターン単体はどの入力にも一致しますが、多くの場合、変数パターンはその他のパターン内で使用されます。このため、タプルや配列などのより複雑な構造体を変数に分解することが可能になります。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-190">A variable pattern alone matches any input, but variable patterns often appear within other patterns, therefore enabling more complex structures such as tuples and arrays to be decomposed into variables.</span></span>

<span data-ttu-id="3c5fc-191">タプル パターン内で変数パターンを使用する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-191">The following example demonstrates a variable pattern within a tuple pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4805.fs)]

## <a name="as-pattern"></a><span data-ttu-id="3c5fc-192">as パターン</span><span class="sxs-lookup"><span data-stu-id="3c5fc-192">as Pattern</span></span>
<span data-ttu-id="3c5fc-193">`as` パターンは、`as` 句が追加されたパターンです。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-193">The `as` pattern is a pattern that has an `as` clause appended to it.</span></span> <span data-ttu-id="3c5fc-194">`as` 句は、照合する値を `match` 式の実行式で使用できる名前に束縛します。または、このパターンが `let` 束縛で使用される場合は、名前が束縛としてローカル スコープに追加されます。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-194">The `as` clause binds the matched value to a name that can be used in the execution expression of a `match` expression, or, in the case where this pattern is used in a `let` binding, the name is added as a binding to the local scope.</span></span>

<span data-ttu-id="3c5fc-195">`as` パターンの使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-195">The following example uses an `as` pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4806.fs)]

## <a name="or-pattern"></a><span data-ttu-id="3c5fc-196">OR パターン</span><span class="sxs-lookup"><span data-stu-id="3c5fc-196">OR Pattern</span></span>
<span data-ttu-id="3c5fc-197">OR パターンは、入力データが複数のパターンと一致する場合に、同じコードを結果として実行するときに使用します。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-197">The OR pattern is used when input data can match multiple patterns, and you want to execute the same code as a result.</span></span> <span data-ttu-id="3c5fc-198">OR パターンの両側の型に互換性があることが必要です。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-198">The types of both sides of the OR pattern must be compatible.</span></span>

<span data-ttu-id="3c5fc-199">OR パターンの使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-199">The following example demonstrates the OR pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4807.fs)]

## <a name="and-pattern"></a><span data-ttu-id="3c5fc-200">AND パターン</span><span class="sxs-lookup"><span data-stu-id="3c5fc-200">AND Pattern</span></span>
<span data-ttu-id="3c5fc-201">AND パターンでは、入力が 2 つのパターンと一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-201">The AND pattern requires that the input match two patterns.</span></span> <span data-ttu-id="3c5fc-202">AND パターンの両側の型に互換性があることが必要です。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-202">The types of both sides of the AND pattern must be compatible.</span></span>

<span data-ttu-id="3c5fc-203">例を次のような`detectZeroTuple`に示すように、[タプル パターン](https://msdn.microsoft.com/library/#tuple)このトピックでは、ここでは、両方はで後述する「`var1`と`var2`AND パターンを使用して、値として取得されます。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-203">The following example is like `detectZeroTuple` shown in the [Tuple Pattern](https://msdn.microsoft.com/library/#tuple) section later in this topic, but here both `var1` and `var2` are obtained as values by using the AND pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4808.fs)]

## <a name="cons-pattern"></a><span data-ttu-id="3c5fc-204">Cons パターン</span><span class="sxs-lookup"><span data-stu-id="3c5fc-204">Cons Pattern</span></span>
<span data-ttu-id="3c5fc-205">Cons パターンは、リストに最初の要素に分解するために使用、*ヘッド*、残りの要素を含む一覧と、*末尾*です。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-205">The cons pattern is used to decompose a list into the first element, the *head*, and a list that contains the remaining elements, the *tail*.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4809.fs)]

## <a name="list-pattern"></a><span data-ttu-id="3c5fc-206">リスト パターン</span><span class="sxs-lookup"><span data-stu-id="3c5fc-206">List Pattern</span></span>
<span data-ttu-id="3c5fc-207">リスト パターンでは、リストをいくつかの要素に分解できます。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-207">The list pattern enables lists to be decomposed into a number of elements.</span></span> <span data-ttu-id="3c5fc-208">リスト パターン自体は、特定の数の要素を含むリストとだけ一致します。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-208">The list pattern itself can match only lists of a specific number of elements.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4810.fs)]

## <a name="array-pattern"></a><span data-ttu-id="3c5fc-209">配列パターン</span><span class="sxs-lookup"><span data-stu-id="3c5fc-209">Array Pattern</span></span>
<span data-ttu-id="3c5fc-210">配列パターンはリスト パターンに似ており、特定の長さの配列を分解するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-210">The array pattern resembles the list pattern and can be used to decompose arrays of a specific length.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4811.fs)]

## <a name="parenthesized-pattern"></a><span data-ttu-id="3c5fc-211">かっこで囲まれたパターン</span><span class="sxs-lookup"><span data-stu-id="3c5fc-211">Parenthesized Pattern</span></span>
<span data-ttu-id="3c5fc-212">かっこでパターンを囲んで、目的の結合規則を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-212">Parentheses can be grouped around patterns to achieve the desired associativity.</span></span> <span data-ttu-id="3c5fc-213">次の例では、かっこを使用して、AND パターンと Cons パターンの間の結合規則を制御します。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-213">In the following example, parentheses are used to control associativity between an AND pattern and a cons pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4812.fs)]

## <a name="tuple-pattern"></a><span data-ttu-id="3c5fc-214">タプル パターン</span><span class="sxs-lookup"><span data-stu-id="3c5fc-214">Tuple Pattern</span></span>
<span data-ttu-id="3c5fc-215">タプル パターンはタプル形式の入力と一致します。このパターンでは、タプル内の位置ごとにパターン マッチ変数を使用して、タプルを構成要素に分解できます。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-215">The tuple pattern matches input in tuple form and enables the tuple to be decomposed into its constituent elements by using pattern matching variables for each position in the tuple.</span></span>

<span data-ttu-id="3c5fc-216">タプル パターンの使用例を次に示します。リテラル パターン、変数パターン、およびワイルドカード パターンも使用します。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-216">The following example demonstrates the tuple pattern and also uses literal patterns, variable patterns, and the wildcard pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4813.fs)]

## <a name="record-pattern"></a><span data-ttu-id="3c5fc-217">レコード パターン</span><span class="sxs-lookup"><span data-stu-id="3c5fc-217">Record Pattern</span></span>
<span data-ttu-id="3c5fc-218">レコード パターンは、レコードを分解してフィールドの値を抽出するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-218">The record pattern is used to decompose records to extract the values of fields.</span></span> <span data-ttu-id="3c5fc-219">パターンがレコードのすべてのフィールドを参照する必要はありません。省略されたフィールドは照合に使用されないため、抽出されません。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-219">The pattern does not have to reference all fields of the record; any omitted fields just do not participate in matching and are not extracted.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4814.fs)]

## <a name="wildcard-pattern"></a><span data-ttu-id="3c5fc-220">ワイルドカード パターン</span><span class="sxs-lookup"><span data-stu-id="3c5fc-220">Wildcard Pattern</span></span>
<span data-ttu-id="3c5fc-221">ワイルドカード パターンは、アンダースコア (`_`) 文字で表され、変数パターンと同様にどの入力にも一致しますが、入力が変数に割り当てられるのではなく、破棄される点が異なります。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-221">The wildcard pattern is represented by the underscore (`_`) character and matches any input, just like the variable pattern, except that the input is discarded instead of assigned to a variable.</span></span> <span data-ttu-id="3c5fc-222">多くの場合、ワイルドカード パターンは、その他のパターン内で `->` 記号の右側の式で不要な値のプレースホルダーとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-222">The wildcard pattern is often used within other patterns as a placeholder for values that are not needed in the expression to the right of the `->` symbol.</span></span> <span data-ttu-id="3c5fc-223">また、一致しなかった入力に対応するために、パターン リストの最後にワイルドカード パターンが使用されることもよくあります。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-223">The wildcard pattern is also frequently used at the end of a list of patterns to match any unmatched input.</span></span> <span data-ttu-id="3c5fc-224">ワイルドカード パターンは、このトピックの多くのコード例で示されています。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-224">The wildcard pattern is demonstrated in many code examples in this topic.</span></span> <span data-ttu-id="3c5fc-225">一例として、上記のコードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-225">See the preceding code for one example.</span></span>


## <a name="patterns-that-have-type-annotations"></a><span data-ttu-id="3c5fc-226">型の注釈が付けられたパターン</span><span class="sxs-lookup"><span data-stu-id="3c5fc-226">Patterns That Have Type Annotations</span></span>
<span data-ttu-id="3c5fc-227">パターンには型の注釈を付けることができます。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-227">Patterns can have type annotations.</span></span> <span data-ttu-id="3c5fc-228">このコメントはその他の型の注釈と同様に動作し、その他の型の注釈と同様に推論を導きます。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-228">These behave like other type annotations and guide inference like other type annotations.</span></span> <span data-ttu-id="3c5fc-229">パターンの型の注釈はかっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-229">Parentheses are required around type annotations in patterns.</span></span> <span data-ttu-id="3c5fc-230">型の注釈が付けられたパターンを次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-230">The following code shows a pattern that has a type annotation.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4815.fs)]

## <a name="type-test-pattern"></a><span data-ttu-id="3c5fc-231">型テスト パターン</span><span class="sxs-lookup"><span data-stu-id="3c5fc-231">Type Test Pattern</span></span>
<span data-ttu-id="3c5fc-232">型テスト パターンは、入力を型と照合するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-232">The type test pattern is used to match the input against a type.</span></span> <span data-ttu-id="3c5fc-233">入力型がパターンで指定された型と一致する場合、またはその型の派生型である場合は、一致と見なされます。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-233">If the input type is a match to (or a derived type of) the type specified in the pattern, the match succeeds.</span></span>

<span data-ttu-id="3c5fc-234">型テスト パターンの使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-234">The following example demonstrates the type test pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4816.fs)]

## <a name="null-pattern"></a><span data-ttu-id="3c5fc-235">null パターン</span><span class="sxs-lookup"><span data-stu-id="3c5fc-235">Null Pattern</span></span>
<span data-ttu-id="3c5fc-236">null パターンは null 値と一致します。null 値は、null 値を許可する型を使用しているときに示される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-236">The null pattern matches the null value that can appear when you are working with types that allow a null value.</span></span> <span data-ttu-id="3c5fc-237">Null パターンは、.NET Framework コードで相互運用するときに頻繁に使用されます。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-237">Null patterns are frequently used when interoperating with .NET Framework code.</span></span> <span data-ttu-id="3c5fc-238">たとえば、.NET API の戻り値が `match` 式への入力である場合が考えられます。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-238">For example, the return value of a .NET API might be the input to a `match` expression.</span></span> <span data-ttu-id="3c5fc-239">プログラム フローは、戻り値が null であるかどうかと、戻り値のその他の特性に基づいて制御できます。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-239">You can control program flow based on whether the return value is null, and also on other characteristics of the returned value.</span></span> <span data-ttu-id="3c5fc-240">null パターンを使用すると、null 値が残りのプログラムに反映されるのを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-240">You can use the null pattern to prevent null values from propagating to the rest of your program.</span></span>

<span data-ttu-id="3c5fc-241">null パターンと変数パターンの使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3c5fc-241">The following example uses the null pattern and the variable pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4817.fs)]

## <a name="see-also"></a><span data-ttu-id="3c5fc-242">関連項目</span><span class="sxs-lookup"><span data-stu-id="3c5fc-242">See Also</span></span>
[<span data-ttu-id="3c5fc-243">match 式</span><span class="sxs-lookup"><span data-stu-id="3c5fc-243">Match Expressions</span></span>](match-expressions.md)

[<span data-ttu-id="3c5fc-244">アクティブ パターン</span><span class="sxs-lookup"><span data-stu-id="3c5fc-244">Active Patterns</span></span>](active-patterns.md)

[<span data-ttu-id="3c5fc-245">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="3c5fc-245">F# Language Reference</span></span>](index.md)
