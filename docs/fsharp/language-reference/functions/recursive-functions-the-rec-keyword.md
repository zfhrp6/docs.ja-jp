---
title: '再帰関数: rec キーワード (F#)'
description: 再帰関数を定義する 'let' キーワードを使用して f# 'rec' キーワードが使用される方法を説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 6039a48eae2b16aa1d82617176460d727a878d87
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562922"
---
# <a name="recursive-functions-the-rec-keyword"></a><span data-ttu-id="be99f-103">再帰関数: rec キーワード</span><span class="sxs-lookup"><span data-stu-id="be99f-103">Recursive Functions: The rec Keyword</span></span>

<span data-ttu-id="be99f-104">`rec`と共にキーワードが使用する、`let`再帰関数を定義するキーワードです。</span><span class="sxs-lookup"><span data-stu-id="be99f-104">The `rec` keyword is used together with the `let` keyword to define a recursive function.</span></span>


## <a name="syntax"></a><span data-ttu-id="be99f-105">構文</span><span class="sxs-lookup"><span data-stu-id="be99f-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="be99f-106">コメント</span><span class="sxs-lookup"><span data-stu-id="be99f-106">Remarks</span></span>
<span data-ttu-id="be99f-107">再帰関数は、自身を呼び出す関数は、f# 言語で明示的に識別されます。</span><span class="sxs-lookup"><span data-stu-id="be99f-107">Recursive functions, functions that call themselves, are identified explicitly in the F# language.</span></span> <span data-ttu-id="be99f-108">これにより、関数のスコープで定義されている識別子を使用可能なにします。</span><span class="sxs-lookup"><span data-stu-id="be99f-108">This makes the identifer that is being defined available in the scope of the function.</span></span>

<span data-ttu-id="be99f-109">次のコードを計算する再帰関数を示しています、 *n*番目のフィボナッチ数。</span><span class="sxs-lookup"><span data-stu-id="be99f-109">The following code illustrates a recursive function that computes the *n*th Fibonacci number.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

>[!NOTE]
<span data-ttu-id="be99f-110">実際には、上記のようなコードは、事前に計算された値の再計算が伴うのでメモリとプロセッサ時間の浪費になります。</span><span class="sxs-lookup"><span data-stu-id="be99f-110">In practice, code like that above is wasteful of memory and processor time because it involves the recomputation of previously computed values.</span></span>


<span data-ttu-id="be99f-111">メソッドは、暗黙的に型内で再帰追加する必要はありません、`rec`キーワード。</span><span class="sxs-lookup"><span data-stu-id="be99f-111">Methods are implicitly recursive within the type; there is no need to add the `rec` keyword.</span></span> <span data-ttu-id="be99f-112">クラス内の let バインディングは、暗黙的に再帰的ではありません。</span><span class="sxs-lookup"><span data-stu-id="be99f-112">Let bindings within classes are not implicitly recursive.</span></span>


## <a name="mutually-recursive-functions"></a><span data-ttu-id="be99f-113">相互再帰関数</span><span class="sxs-lookup"><span data-stu-id="be99f-113">Mutually Recursive Functions</span></span>
<span data-ttu-id="be99f-114">関数は、場合によって*相互再帰*呼び出しが、1 つの関数呼び出しを呼び出して、最初の呼び出しの数に別間に、円を描くことを意味します。</span><span class="sxs-lookup"><span data-stu-id="be99f-114">Sometimes functions are *mutually recursive*, meaning that calls form a circle, where one function calls another which in turn calls the first, with any number of calls in between.</span></span> <span data-ttu-id="be99f-115">このような関数の定義は、1 つで一緒にする必要があります`let`して、バインド、`and`それらをリンクするキーワードです。</span><span class="sxs-lookup"><span data-stu-id="be99f-115">You must define such functions together in the one `let` binding, using the `and` keyword to link them together.</span></span>

<span data-ttu-id="be99f-116">次の例は、2 つを一緒には再帰関数。</span><span class="sxs-lookup"><span data-stu-id="be99f-116">The following example shows two mutually recursive functions.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a><span data-ttu-id="be99f-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="be99f-117">See Also</span></span>
[<span data-ttu-id="be99f-118">関数</span><span class="sxs-lookup"><span data-stu-id="be99f-118">Functions</span></span>](index.md)
