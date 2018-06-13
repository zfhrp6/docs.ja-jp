---
title: 'ラムダ式: fun キーワード (F#)'
description: F# 'fun' キーワードを使用して、匿名関数であるラムダ式を定義する方法を説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 433451fb9bf89bfabdcd8e71560105317771d251
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563851"
---
# <a name="lambda-expressions-the-fun-keyword-f"></a><span data-ttu-id="63f1f-103">ラムダ式: fun キーワード (F#)</span><span class="sxs-lookup"><span data-stu-id="63f1f-103">Lambda Expressions: The fun Keyword (F#)</span></span>

<span data-ttu-id="63f1f-104">`fun`キーワードの使用をラムダ式、つまり、匿名関数を定義します。</span><span class="sxs-lookup"><span data-stu-id="63f1f-104">The `fun` keyword is used to define a lambda expression, that is, an anonymous function.</span></span>


## <a name="syntax"></a><span data-ttu-id="63f1f-105">構文</span><span class="sxs-lookup"><span data-stu-id="63f1f-105">Syntax</span></span>

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a><span data-ttu-id="63f1f-106">コメント</span><span class="sxs-lookup"><span data-stu-id="63f1f-106">Remarks</span></span>
<span data-ttu-id="63f1f-107">*パラメーター リスト*通常の名前と、必要に応じて、パラメーターの型で構成されます。</span><span class="sxs-lookup"><span data-stu-id="63f1f-107">The *parameter-list* typically consists of names and, optionally, types of parameters.</span></span> <span data-ttu-id="63f1f-108">一般的に、*パラメーター リスト*f# パターンで構成されることができます。</span><span class="sxs-lookup"><span data-stu-id="63f1f-108">More generally, the *parameter-list* can be composed of any F# patterns.</span></span> <span data-ttu-id="63f1f-109">可能なパターンの一覧については、次を参照してください。[パターン マッチ](../pattern-matching.md)です。</span><span class="sxs-lookup"><span data-stu-id="63f1f-109">For a full list of possible patterns, see [Pattern Matching](../pattern-matching.md).</span></span> <span data-ttu-id="63f1f-110">有効なパラメーターのリストには、次の例が含まれます。</span><span class="sxs-lookup"><span data-stu-id="63f1f-110">Lists of valid parameters include the following examples.</span></span>

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

<span data-ttu-id="63f1f-111">*式*うち、最後の式には、戻り値が生成されます。 関数の本文です。</span><span class="sxs-lookup"><span data-stu-id="63f1f-111">The *expression* is the body of the function, the last expression of which generates a return value.</span></span> <span data-ttu-id="63f1f-112">有効なラムダ式の例については、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="63f1f-112">Examples of valid lambda expressions include the following:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet301.fs)]
    
## <a name="using-lambda-expressions"></a><span data-ttu-id="63f1f-113">ラムダ式の使用</span><span class="sxs-lookup"><span data-stu-id="63f1f-113">Using Lambda Expressions</span></span>
<span data-ttu-id="63f1f-114">ラムダ式は、リストまたはその他のコレクションで操作を実行し、追加の関数を定義する作業を避けたい場合に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="63f1f-114">Lambda expressions are especially useful when you want to perform operations on a list or other collection and want to avoid the extra work of defining a function.</span></span> <span data-ttu-id="63f1f-115">多数の f# ライブラリ関数は、引数としての関数の値を行い、そのような場合、ラムダ式を使用すると特に便利であることができます。</span><span class="sxs-lookup"><span data-stu-id="63f1f-115">Many F# library functions take function values as arguments, and it can be especially convenient to use a lambda expression in those cases.</span></span> <span data-ttu-id="63f1f-116">次のコードは、リストの要素をラムダ式を適用します。</span><span class="sxs-lookup"><span data-stu-id="63f1f-116">The following code applies a lambda expression to elements of a list.</span></span> <span data-ttu-id="63f1f-117">この場合、匿名の関数は、一覧のすべての要素に 1 を追加します。</span><span class="sxs-lookup"><span data-stu-id="63f1f-117">In this case, the anonymous function adds 1 to every element of a list.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet302.fs)]
    
## <a name="see-also"></a><span data-ttu-id="63f1f-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="63f1f-118">See Also</span></span>
[<span data-ttu-id="63f1f-119">関数</span><span class="sxs-lookup"><span data-stu-id="63f1f-119">Functions</span></span>](index.md)
