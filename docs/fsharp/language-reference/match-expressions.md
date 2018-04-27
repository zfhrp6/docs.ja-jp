---
title: Match 式 (f#)
description: F# 一致式が式のパターンのセットとの比較に基づいている分岐のコントロールがどのように提供する方法について説明します。
author: cartermp
ms.author: phcart
ms.date: 04/19/2018
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.openlocfilehash: f843e6fde98eae8a10235dd5cae38ffc10a4fb9f
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="match-expressions"></a><span data-ttu-id="0e09d-103">Match 式</span><span class="sxs-lookup"><span data-stu-id="0e09d-103">Match expressions</span></span>

<span data-ttu-id="0e09d-104">`match`式が式のパターンのセットとの比較に基づいている分岐のコントロールを提供します。</span><span class="sxs-lookup"><span data-stu-id="0e09d-104">The `match` expression provides branching control that is based on the comparison of an expression with a set of patterns.</span></span>

## <a name="syntax"></a><span data-ttu-id="0e09d-105">構文</span><span class="sxs-lookup"><span data-stu-id="0e09d-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="0e09d-106">コメント</span><span class="sxs-lookup"><span data-stu-id="0e09d-106">Remarks</span></span>

<span data-ttu-id="0e09d-107">パターン一致式では、複雑なパターンのセットとテスト式の比較に基づく、分岐できます。</span><span class="sxs-lookup"><span data-stu-id="0e09d-107">The pattern matching expressions allow for complex branching based on the comparison of a test expression with a set of patterns.</span></span> <span data-ttu-id="0e09d-108">`match` 、式、*テスト式*、逆を使用して、対応する一致が見つかったが、各パターンと比較*結果式*が評価されると、結果として得られる値は一致する式の値として返されます。</span><span class="sxs-lookup"><span data-stu-id="0e09d-108">In the `match` expression, the *test-expression* is compared with each pattern in turn, and when a match is found, the corresponding *result-expression* is evaluated and the resulting value is returned as the value of the match expression.</span></span>

<span data-ttu-id="0e09d-109">パターン一致の前の構文に示す関数は、ラムダ式、パターン マッチが行わ直ちに引数です。</span><span class="sxs-lookup"><span data-stu-id="0e09d-109">The pattern matching function shown in the previous syntax is a lambda expression in which pattern matching is performed immediately on the argument.</span></span> <span data-ttu-id="0e09d-110">パターン一致の前の構文に示す関数は、次のと同じです。</span><span class="sxs-lookup"><span data-stu-id="0e09d-110">The pattern matching function shown in the previous syntax is equivalent to the following.</span></span>

```fsharp
fun arg ->
    match arg with
    | pattern1 [ when condition ] -> result-expression1
    | pattern2 [ when condition ] -> result-expression2
    | ...
```

<span data-ttu-id="0e09d-111">ラムダ式の詳細については、次を参照してください。[ラムダ式:、`fun`キーワード](functions/lambda-expressions-the-fun-keyword.md)です。</span><span class="sxs-lookup"><span data-stu-id="0e09d-111">For more information about lambda expressions, see [Lambda Expressions: The `fun` Keyword](functions/lambda-expressions-the-fun-keyword.md).</span></span>

<span data-ttu-id="0e09d-112">パターンのセット全体では、入力変数のすべての一致候補を取り扱う必要があります。</span><span class="sxs-lookup"><span data-stu-id="0e09d-112">The whole set of patterns should cover all the possible matches of the input variable.</span></span> <span data-ttu-id="0e09d-113">ワイルドカード パターンを使用する多くの場合、(`_`)、以前に一致しない入力の値に一致する最後のパターンとして。</span><span class="sxs-lookup"><span data-stu-id="0e09d-113">Frequently, you use the wildcard pattern (`_`) as the last pattern to match any previously unmatched input values.</span></span>

<span data-ttu-id="0e09d-114">次のコードを示すための方法の一部、`match`式を使用します。</span><span class="sxs-lookup"><span data-stu-id="0e09d-114">The following code illustrates some of the ways in which the `match` expression is used.</span></span> <span data-ttu-id="0e09d-115">参照と使用できるすべての可能なパターンの例では、次を参照してください。[パターン マッチ](pattern-matching.md)です。</span><span class="sxs-lookup"><span data-stu-id="0e09d-115">For a reference and examples of all the possible patterns that can be used, see [Pattern Matching](pattern-matching.md).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4601.fs)]

## <a name="guards-on-patterns"></a><span data-ttu-id="0e09d-116">パターンのガード</span><span class="sxs-lookup"><span data-stu-id="0e09d-116">Guards on patterns</span></span>

<span data-ttu-id="0e09d-117">使用することができます、`when`句をパターンに一致する変数が満たす必要がある追加の条件を指定します。</span><span class="sxs-lookup"><span data-stu-id="0e09d-117">You can use a `when` clause to specify an additional condition that the variable must satisfy to match a pattern.</span></span> <span data-ttu-id="0e09d-118">このような句と呼ばれます、*ガード*です。</span><span class="sxs-lookup"><span data-stu-id="0e09d-118">Such a clause is referred to as a *guard*.</span></span> <span data-ttu-id="0e09d-119">式以下、`when`そのガードに関連付けられているパターンに一致するものが加えられる場合を除き、キーワードは評価されません。</span><span class="sxs-lookup"><span data-stu-id="0e09d-119">The expression following the `when` keyword is not evaluated unless a match is made to the pattern associated with that guard.</span></span>

<span data-ttu-id="0e09d-120">次の例では、変数パターンの数値の範囲を指定する保護の使用を示します。</span><span class="sxs-lookup"><span data-stu-id="0e09d-120">The following example illustrates the use of a guard to specify a numeric range for a variable pattern.</span></span> <span data-ttu-id="0e09d-121">ブール演算子を使用して複数の条件を組み合わせることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="0e09d-121">Note that multiple conditions are combined by using Boolean operators.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4602.fs)]

<span data-ttu-id="0e09d-122">リテラル以外の値は、パターンでは使用できません、ためにを付けることに注意してください、`when`句の値に対する入力の一部を比較する必要がある場合に指定します。</span><span class="sxs-lookup"><span data-stu-id="0e09d-122">Note that because values other than literals cannot be used in the pattern, you must use a `when` clause if you have to compare some part of the input against a value.</span></span> <span data-ttu-id="0e09d-123">これは、次のコードで示されます。</span><span class="sxs-lookup"><span data-stu-id="0e09d-123">This is shown in the following code:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4603.fs)]

<span data-ttu-id="0e09d-124">共用体パターンはガード覆われて、ときに、保護の対象に適用されることに注意してください**すべて**の最後の 1 つだけでなく、パターンのです。</span><span class="sxs-lookup"><span data-stu-id="0e09d-124">Note that when a union pattern is covered by a guard, the guard applies to **all** of the patterns, not just the last one.</span></span> <span data-ttu-id="0e09d-125">たとえば、次のコードでは、ガードを与える`when a > 12`両方に適用される`A a`と`B a`:</span><span class="sxs-lookup"><span data-stu-id="0e09d-125">For example, given the following code, the guard `when a > 12` applies to both `A a` and `B a`:</span></span>

```fsharp
type Union =
    | A of int
    | B of int

let foo() =
    let test = A 42
    match test with
    | A a
    | B a when a > 41 -> a // the guard applies to both patterns
    | _ -> 1

foo() // returns 42
```

## <a name="see-also"></a><span data-ttu-id="0e09d-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="0e09d-126">See also</span></span>

[<span data-ttu-id="0e09d-127">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="0e09d-127">F# Language Reference</span></span>](index.md)  
[<span data-ttu-id="0e09d-128">アクティブ パターン</span><span class="sxs-lookup"><span data-stu-id="0e09d-128">Active Patterns</span></span>](active-patterns.md)  
[<span data-ttu-id="0e09d-129">パターン一致</span><span class="sxs-lookup"><span data-stu-id="0e09d-129">Pattern Matching</span></span>](pattern-matching.md)  
