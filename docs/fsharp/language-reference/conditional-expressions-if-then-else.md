---
title: '条件式: if... then...else (F#)'
description: コードの別の分岐を実行するのには、f# で条件付きの式を記述する方法を説明します。
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: bfb985f09be91034894e1d3eba88cebef6bb3fd4
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="conditional-expressions-ifthenelse"></a><span data-ttu-id="363fa-103">条件式: `if...then...else`</span><span class="sxs-lookup"><span data-stu-id="363fa-103">Conditional Expressions: `if...then...else`</span></span>

<span data-ttu-id="363fa-104">`if...then...else`式は、コードの別の分岐を実行し、別の値によって指定されるブール式を評価することもできます。</span><span class="sxs-lookup"><span data-stu-id="363fa-104">The `if...then...else` expression runs different branches of code and also evaluates to a different value depending on the Boolean expression given.</span></span>


## <a name="syntax"></a><span data-ttu-id="363fa-105">構文</span><span class="sxs-lookup"><span data-stu-id="363fa-105">Syntax</span></span>

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a><span data-ttu-id="363fa-106">コメント</span><span class="sxs-lookup"><span data-stu-id="363fa-106">Remarks</span></span>
<span data-ttu-id="363fa-107">前の構文で*expression1*ブール式を評価するときに実行`true`、それ以外の*expression2*を実行します。</span><span class="sxs-lookup"><span data-stu-id="363fa-107">In the previous syntax, *expression1* runs when the Boolean expression evaluates to `true`; otherwise, *expression2* runs.</span></span>

<span data-ttu-id="363fa-108">異なり、他の言語で、`if...then...else`構造は式、ステートメントではなくです。</span><span class="sxs-lookup"><span data-stu-id="363fa-108">Unlike in other languages, the `if...then...else` construct is an expression, not a statement.</span></span> <span data-ttu-id="363fa-109">つまりを実行する分岐の最後の式の値には、値が生成されます。</span><span class="sxs-lookup"><span data-stu-id="363fa-109">That means that it produces a value, which is the value of the last expression in the branch that executes.</span></span> <span data-ttu-id="363fa-110">各分岐で生成される値の型が一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="363fa-110">The types of the values produced in each branch must match.</span></span> <span data-ttu-id="363fa-111">明示的ながある場合`else`分岐では、そのタイプが`unit`です。</span><span class="sxs-lookup"><span data-stu-id="363fa-111">If there is no explicit `else` branch, its type is `unit`.</span></span> <span data-ttu-id="363fa-112">したがって場合の種類、`then`分岐以外の任意の型は、 `unit`、必要があります、`else`分岐と同じ戻り値の型。</span><span class="sxs-lookup"><span data-stu-id="363fa-112">Therefore, if the type of the `then` branch is any type other than `unit`, there must be an `else` branch with the same return type.</span></span> <span data-ttu-id="363fa-113">チェーンと`if...then...else`式のキーワードを使用することができます、併せて`elif`の代わりに`else if`; それらが等しい。</span><span class="sxs-lookup"><span data-stu-id="363fa-113">When chaining `if...then...else` expressions together, you can use the keyword `elif` instead of `else if`; they are equivalent.</span></span>

## <a name="example"></a><span data-ttu-id="363fa-114">例</span><span class="sxs-lookup"><span data-stu-id="363fa-114">Example</span></span>
<span data-ttu-id="363fa-115">次の例を使用する方法を示しています、`if...then...else`式。</span><span class="sxs-lookup"><span data-stu-id="363fa-115">The following example illustrates how to use the `if...then...else` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```
10 is less than 20
What is your name? John
How old are you? 9
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a><span data-ttu-id="363fa-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="363fa-116">See Also</span></span>
[<span data-ttu-id="363fa-117">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="363fa-117">F# Language Reference</span></span>](index.md)

