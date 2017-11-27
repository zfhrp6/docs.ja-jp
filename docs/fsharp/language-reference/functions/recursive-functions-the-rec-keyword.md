---
title: "再帰関数: rec キーワード (F#)"
description: "再帰関数を定義する 'let' キーワードを使用して f# 'rec' キーワードが使用される方法を説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 1a95639f-9bfe-4f1d-a5e2-246d1d37776e
ms.openlocfilehash: b837d2c0f8e2b1d28980620103097ccc8345c098
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="recursive-functions-the-rec-keyword"></a><span data-ttu-id="8a78d-104">再帰関数: rec キーワード</span><span class="sxs-lookup"><span data-stu-id="8a78d-104">Recursive Functions: The rec Keyword</span></span>

<span data-ttu-id="8a78d-105">`rec`と共にキーワードが使用する、`let`再帰関数を定義するキーワードです。</span><span class="sxs-lookup"><span data-stu-id="8a78d-105">The `rec` keyword is used together with the `let` keyword to define a recursive function.</span></span>


## <a name="syntax"></a><span data-ttu-id="8a78d-106">構文</span><span class="sxs-lookup"><span data-stu-id="8a78d-106">Syntax</span></span>

```fsharp
// Recursive function:
let rec function-nameparameter-list =
function-body

// Mutually recursive functions:
let rec function1-nameparameter-list =
function1-body
and function2-nameparameter-list =
function2-body
...
```

## <a name="remarks"></a><span data-ttu-id="8a78d-107">コメント</span><span class="sxs-lookup"><span data-stu-id="8a78d-107">Remarks</span></span>
<span data-ttu-id="8a78d-108">再帰関数は、自身を呼び出す関数は、f# 言語で明示的に識別されます。</span><span class="sxs-lookup"><span data-stu-id="8a78d-108">Recursive functions, functions that call themselves, are identified explicitly in the F# language.</span></span> <span data-ttu-id="8a78d-109">これにより、関数のスコープで定義されている識別子を使用可能なにします。</span><span class="sxs-lookup"><span data-stu-id="8a78d-109">This makes the identifer that is being defined available in the scope of the function.</span></span>

<span data-ttu-id="8a78d-110">次のコードを計算する再帰関数を示しています、  *n*番目のフィボナッチ数。</span><span class="sxs-lookup"><span data-stu-id="8a78d-110">The following code illustrates a recursive function that computes the *n*th Fibonacci number.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

>[!NOTE]
<span data-ttu-id="8a78d-111">実際には、上記のようなコードは、事前に計算された値の再計算が伴うのでメモリとプロセッサ時間の浪費になります。</span><span class="sxs-lookup"><span data-stu-id="8a78d-111">In practice, code like that above is wasteful of memory and processor time because it involves the recomputation of previously computed values.</span></span>


<span data-ttu-id="8a78d-112">メソッドは、暗黙的に型内で再帰追加する必要はありません、`rec`キーワード。</span><span class="sxs-lookup"><span data-stu-id="8a78d-112">Methods are implicitly recursive within the type; there is no need to add the `rec` keyword.</span></span> <span data-ttu-id="8a78d-113">クラス内の let バインディングは、暗黙的に再帰的ではありません。</span><span class="sxs-lookup"><span data-stu-id="8a78d-113">Let bindings within classes are not implicitly recursive.</span></span>


## <a name="mutually-recursive-functions"></a><span data-ttu-id="8a78d-114">相互再帰関数</span><span class="sxs-lookup"><span data-stu-id="8a78d-114">Mutually Recursive Functions</span></span>
<span data-ttu-id="8a78d-115">関数は、場合によって*相互再帰*呼び出しが、1 つの関数呼び出しを呼び出して、最初の呼び出しの数に別間に、円を描くことを意味します。</span><span class="sxs-lookup"><span data-stu-id="8a78d-115">Sometimes functions are *mutually recursive*, meaning that calls form a circle, where one function calls another which in turn calls the first, with any number of calls in between.</span></span> <span data-ttu-id="8a78d-116">このような関数の定義は、1 つで一緒にする必要があります`let`して、バインド、`and`それらをリンクするキーワードです。</span><span class="sxs-lookup"><span data-stu-id="8a78d-116">You must define such functions together in the one `let` binding, using the `and` keyword to link them together.</span></span>

<span data-ttu-id="8a78d-117">次の例は、2 つを一緒には再帰関数。</span><span class="sxs-lookup"><span data-stu-id="8a78d-117">The following example shows two mutually recursive functions.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a><span data-ttu-id="8a78d-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="8a78d-118">See Also</span></span>
[<span data-ttu-id="8a78d-119">関数</span><span class="sxs-lookup"><span data-stu-id="8a78d-119">Functions</span></span>](index.md)
