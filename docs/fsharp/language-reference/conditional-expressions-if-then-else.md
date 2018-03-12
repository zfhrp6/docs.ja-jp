---
title: "条件式: if... then...else (F#)"
description: "コードの別の分岐を実行するのには、f# で条件付きの式を記述する方法を説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 16e1871c-4d4d-4691-9ab2-bd2c6f65589a
ms.openlocfilehash: 5823e46cd13053fcd31f94f2d79d1f7470ca5118
ms.sourcegitcommit: d3cfda0943364aaf6ccd574f55f584576c8a4fee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2018
---
# <a name="conditional-expressions-ifthenelse"></a><span data-ttu-id="41474-104">条件式: `if...then...else`</span><span class="sxs-lookup"><span data-stu-id="41474-104">Conditional Expressions: `if...then...else`</span></span>

<span data-ttu-id="41474-105">`if...then...else`式は、コードの別の分岐を実行し、別の値によって指定されるブール式を評価することもできます。</span><span class="sxs-lookup"><span data-stu-id="41474-105">The `if...then...else` expression runs different branches of code and also evaluates to a different value depending on the Boolean expression given.</span></span>


## <a name="syntax"></a><span data-ttu-id="41474-106">構文</span><span class="sxs-lookup"><span data-stu-id="41474-106">Syntax</span></span>

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a><span data-ttu-id="41474-107">コメント</span><span class="sxs-lookup"><span data-stu-id="41474-107">Remarks</span></span>
<span data-ttu-id="41474-108">前の構文で*expression1*ブール式を評価するときに実行`true`、それ以外の*expression2*を実行します。</span><span class="sxs-lookup"><span data-stu-id="41474-108">In the previous syntax, *expression1* runs when the Boolean expression evaluates to `true`; otherwise, *expression2* runs.</span></span>

<span data-ttu-id="41474-109">異なり、他の言語で、`if...then...else`構造は式、ステートメントではなくです。</span><span class="sxs-lookup"><span data-stu-id="41474-109">Unlike in other languages, the `if...then...else` construct is an expression, not a statement.</span></span> <span data-ttu-id="41474-110">つまりを実行する分岐の最後の式の値には、値が生成されます。</span><span class="sxs-lookup"><span data-stu-id="41474-110">That means that it produces a value, which is the value of the last expression in the branch that executes.</span></span> <span data-ttu-id="41474-111">各分岐で生成される値の型が一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="41474-111">The types of the values produced in each branch must match.</span></span> <span data-ttu-id="41474-112">明示的ながある場合`else`分岐では、そのタイプが`unit`です。</span><span class="sxs-lookup"><span data-stu-id="41474-112">If there is no explicit `else` branch, its type is `unit`.</span></span> <span data-ttu-id="41474-113">したがって場合の種類、`then`分岐以外の任意の型は、 `unit`、必要があります、`else`分岐と同じ戻り値の型。</span><span class="sxs-lookup"><span data-stu-id="41474-113">Therefore, if the type of the `then` branch is any type other than `unit`, there must be an `else` branch with the same return type.</span></span> <span data-ttu-id="41474-114">チェーンと`if...then...else`式のキーワードを使用することができます、併せて`elif`の代わりに`else if`; それらが等しい。</span><span class="sxs-lookup"><span data-stu-id="41474-114">When chaining `if...then...else` expressions together, you can use the keyword `elif` instead of `else if`; they are equivalent.</span></span>

## <a name="example"></a><span data-ttu-id="41474-115">例</span><span class="sxs-lookup"><span data-stu-id="41474-115">Example</span></span>
<span data-ttu-id="41474-116">次の例を使用する方法を示しています、`if...then...else`式。</span><span class="sxs-lookup"><span data-stu-id="41474-116">The following example illustrates how to use the `if...then...else` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```
10 is less than 20
What is your name? John
How old are you? 9
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a><span data-ttu-id="41474-117">参照</span><span class="sxs-lookup"><span data-stu-id="41474-117">See Also</span></span>
[<span data-ttu-id="41474-118">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="41474-118">F# Language Reference</span></span>](index.md)

