---
title: "match 式 (F#)"
description: "F# 一致式が式のパターンのセットとの比較に基づいている分岐のコントロールがどのように提供する方法について説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 8854b713-255a-408d-942a-e80ab52fd2a4
ms.openlocfilehash: c8b9be744cfa7bc76f0d663b12abd66f8757fc56
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="match-expressions"></a><span data-ttu-id="a3cf1-104">match 式</span><span class="sxs-lookup"><span data-stu-id="a3cf1-104">Match Expressions</span></span>

<span data-ttu-id="a3cf1-105">`match`式が式のパターンのセットとの比較に基づいている分岐のコントロールを提供します。</span><span class="sxs-lookup"><span data-stu-id="a3cf1-105">The `match` expression provides branching control that is based on the comparison of an expression with a set of patterns.</span></span>

## <a name="syntax"></a><span data-ttu-id="a3cf1-106">構文</span><span class="sxs-lookup"><span data-stu-id="a3cf1-106">Syntax</span></span>

```fsharp
// Match expression.
match test-expression with
| pattern1 [ when condition ] -> result-expression1
| pattern2 [ when condition ] -> result-expression2
| ...

// Pattern matching function.
function
| pattern1 [ when condition ] -> result-expression1
| pattern2 [ when condition ] -> result-expression2
| ...
```

## <a name="remarks"></a><span data-ttu-id="a3cf1-107">コメント</span><span class="sxs-lookup"><span data-stu-id="a3cf1-107">Remarks</span></span>

<span data-ttu-id="a3cf1-108">パターン一致式では、複雑なパターンのセットとテスト式の比較に基づく、分岐できます。</span><span class="sxs-lookup"><span data-stu-id="a3cf1-108">The pattern matching expressions allow for complex branching based on the comparison of a test expression with a set of patterns.</span></span> <span data-ttu-id="a3cf1-109">`match` 、式、*テスト式*、逆を使用して、対応する一致が見つかったが、各パターンと比較*結果式*が評価されると、結果として得られる値は一致する式の値として返されます。</span><span class="sxs-lookup"><span data-stu-id="a3cf1-109">In the `match` expression, the *test-expression* is compared with each pattern in turn, and when a match is found, the corresponding *result-expression* is evaluated and the resulting value is returned as the value of the match expression.</span></span>

<span data-ttu-id="a3cf1-110">パターン一致の前の構文に示す関数は、ラムダ式、パターン マッチが行わ直ちに引数です。</span><span class="sxs-lookup"><span data-stu-id="a3cf1-110">The pattern matching function shown in the previous syntax is a lambda expression in which pattern matching is performed immediately on the argument.</span></span> <span data-ttu-id="a3cf1-111">パターン一致の前の構文に示す関数は、次のと同じです。</span><span class="sxs-lookup"><span data-stu-id="a3cf1-111">The pattern matching function shown in the previous syntax is equivalent to the following.</span></span>

```fsharp
fun arg ->
    match arg with
    | pattern1 [ when condition ] -> result-expression1
    | pattern2 [ when condition ] -> result-expression2
    | ...
```    

<span data-ttu-id="a3cf1-112">ラムダ式の詳細については、次を参照してください。[ラムダ式:、`fun`キーワード](functions/lambda-expressions-the-fun-keyword.md)です。</span><span class="sxs-lookup"><span data-stu-id="a3cf1-112">For more information about lambda expressions, see [Lambda Expressions: The `fun` Keyword](functions/lambda-expressions-the-fun-keyword.md).</span></span>

<span data-ttu-id="a3cf1-113">パターンのセット全体では、入力変数のすべての一致候補を取り扱う必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3cf1-113">The whole set of patterns should cover all the possible matches of the input variable.</span></span> <span data-ttu-id="a3cf1-114">ワイルドカード パターンを使用する多くの場合、(`_`)、以前に一致しない入力の値に一致する最後のパターンとして。</span><span class="sxs-lookup"><span data-stu-id="a3cf1-114">Frequently, you use the wildcard pattern (`_`) as the last pattern to match any previously unmatched input values.</span></span>

<span data-ttu-id="a3cf1-115">次のコードを示すための方法の一部、`match`式を使用します。</span><span class="sxs-lookup"><span data-stu-id="a3cf1-115">The following code illustrates some of the ways in which the `match` expression is used.</span></span> <span data-ttu-id="a3cf1-116">参照と使用できるすべての可能なパターンの例では、次を参照してください。[パターン マッチ](pattern-matching.md)です。</span><span class="sxs-lookup"><span data-stu-id="a3cf1-116">For a reference and examples of all the possible patterns that can be used, see [Pattern Matching](pattern-matching.md).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4601.fs)]

## <a name="guards-on-patterns"></a><span data-ttu-id="a3cf1-117">パターンのガード</span><span class="sxs-lookup"><span data-stu-id="a3cf1-117">Guards on Patterns</span></span>

<span data-ttu-id="a3cf1-118">使用することができます、`when`句をパターンに一致する変数が満たす必要がある追加の条件を指定します。</span><span class="sxs-lookup"><span data-stu-id="a3cf1-118">You can use a `when` clause to specify an additional condition that the variable must satisfy to match a pattern.</span></span> <span data-ttu-id="a3cf1-119">このような句と呼ばれます、*ガード*です。</span><span class="sxs-lookup"><span data-stu-id="a3cf1-119">Such a clause is referred to as a *guard*.</span></span> <span data-ttu-id="a3cf1-120">式以下、`when`そのガードに関連付けられているパターンに一致するものが加えられる場合を除き、キーワードは評価されません。</span><span class="sxs-lookup"><span data-stu-id="a3cf1-120">The expression following the `when` keyword is not evaluated unless a match is made to the pattern associated with that guard.</span></span>

<span data-ttu-id="a3cf1-121">次の例では、変数パターンの数値の範囲を指定する保護の使用を示します。</span><span class="sxs-lookup"><span data-stu-id="a3cf1-121">The following example illustrates the use of a guard to specify a numeric range for a variable pattern.</span></span> <span data-ttu-id="a3cf1-122">ブール演算子を使用して複数の条件を組み合わせることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a3cf1-122">Note that multiple conditions are combined by using Boolean operators.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4602.fs)]

<span data-ttu-id="a3cf1-123">リテラル以外の値は、パターンでは使用できません、ためにを付けることに注意してください、`when`句の値に対する入力の一部を比較する必要がある場合に指定します。</span><span class="sxs-lookup"><span data-stu-id="a3cf1-123">Note that because values other than literals cannot be used in the pattern, you must use a `when` clause if you have to compare some part of the input against a value.</span></span> <span data-ttu-id="a3cf1-124">これを次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="a3cf1-124">This is shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4603.fs)]

## <a name="see-also"></a><span data-ttu-id="a3cf1-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="a3cf1-125">See Also</span></span>

[<span data-ttu-id="a3cf1-126">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="a3cf1-126">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="a3cf1-127">アクティブ パターン</span><span class="sxs-lookup"><span data-stu-id="a3cf1-127">Active Patterns</span></span>](active-patterns.md)

[<span data-ttu-id="a3cf1-128">パターン一致</span><span class="sxs-lookup"><span data-stu-id="a3cf1-128">Pattern Matching</span></span>](pattern-matching.md)
