---
title: "ラムダ式: fun キーワード (F#)"
description: "F# 'fun' キーワードを使用して、匿名関数であるラムダ式を定義する方法を説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e5d3565c-d7cc-433f-a619-886ed92523a7
ms.openlocfilehash: 09f1c1787bbb4b86ec40f9e973e08104919631aa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="lambda-expressions-the-fun-keyword-f"></a><span data-ttu-id="0e360-104">ラムダ式: fun キーワード (F#)</span><span class="sxs-lookup"><span data-stu-id="0e360-104">Lambda Expressions: The fun Keyword (F#)</span></span>

<span data-ttu-id="0e360-105">`fun`キーワードの使用をラムダ式、つまり、匿名関数を定義します。</span><span class="sxs-lookup"><span data-stu-id="0e360-105">The `fun` keyword is used to define a lambda expression, that is, an anonymous function.</span></span>


## <a name="syntax"></a><span data-ttu-id="0e360-106">構文</span><span class="sxs-lookup"><span data-stu-id="0e360-106">Syntax</span></span>

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a><span data-ttu-id="0e360-107">コメント</span><span class="sxs-lookup"><span data-stu-id="0e360-107">Remarks</span></span>
<span data-ttu-id="0e360-108">*パラメーター リスト*通常の名前と、必要に応じて、パラメーターの型で構成されます。</span><span class="sxs-lookup"><span data-stu-id="0e360-108">The *parameter-list* typically consists of names and, optionally, types of parameters.</span></span> <span data-ttu-id="0e360-109">一般的に、*パラメーター リスト*f# パターンで構成されることができます。</span><span class="sxs-lookup"><span data-stu-id="0e360-109">More generally, the *parameter-list* can be composed of any F# patterns.</span></span> <span data-ttu-id="0e360-110">可能なパターンの一覧については、次を参照してください。[パターン マッチ](../pattern-matching.md)です。</span><span class="sxs-lookup"><span data-stu-id="0e360-110">For a full list of possible patterns, see [Pattern Matching](../pattern-matching.md).</span></span> <span data-ttu-id="0e360-111">有効なパラメーターのリストには、次の例が含まれます。</span><span class="sxs-lookup"><span data-stu-id="0e360-111">Lists of valid parameters include the following examples.</span></span>

```fsharp
// Lambda expressions with parameter lists.
fun a b c -> ...
fun (a: int) b c -> ...
fun (a : int) (b : string) (c:float) -> ...

// A lambda expression with a tuple pattern.
fun (a, b) -> …

// A lambda expression with a list pattern.
fun head :: tail -> …
```

<span data-ttu-id="0e360-112">*式*うち、最後の式には、戻り値が生成されます。 関数の本文です。</span><span class="sxs-lookup"><span data-stu-id="0e360-112">The *expression* is the body of the function, the last expression of which generates a return value.</span></span> <span data-ttu-id="0e360-113">有効なラムダ式の例については、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="0e360-113">Examples of valid lambda expressions include the following:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet301.fs)]
    
## <a name="using-lambda-expressions"></a><span data-ttu-id="0e360-114">ラムダ式の使用</span><span class="sxs-lookup"><span data-stu-id="0e360-114">Using Lambda Expressions</span></span>
<span data-ttu-id="0e360-115">ラムダ式は、リストまたはその他のコレクションで操作を実行し、追加の関数を定義する作業を避けたい場合に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="0e360-115">Lambda expressions are especially useful when you want to perform operations on a list or other collection and want to avoid the extra work of defining a function.</span></span> <span data-ttu-id="0e360-116">多数の f# ライブラリ関数は、引数としての関数の値を行い、そのような場合、ラムダ式を使用すると特に便利であることができます。</span><span class="sxs-lookup"><span data-stu-id="0e360-116">Many F# library functions take function values as arguments, and it can be especially convenient to use a lambda expression in those cases.</span></span> <span data-ttu-id="0e360-117">次のコードは、リストの要素をラムダ式を適用します。</span><span class="sxs-lookup"><span data-stu-id="0e360-117">The following code applies a lambda expression to elements of a list.</span></span> <span data-ttu-id="0e360-118">この場合、匿名の関数は、一覧のすべての要素に 1 を追加します。</span><span class="sxs-lookup"><span data-stu-id="0e360-118">In this case, the anonymous function adds 1 to every element of a list.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet302.fs)]
    
## <a name="see-also"></a><span data-ttu-id="0e360-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="0e360-119">See Also</span></span>
[<span data-ttu-id="0e360-120">関数</span><span class="sxs-lookup"><span data-stu-id="0e360-120">Functions</span></span>](index.md)
