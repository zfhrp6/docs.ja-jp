---
title: "例外: raise 関数 (F#)"
description: "F# 'raise' 関数が、エラーまたは例外条件が発生したことを示すために使用する方法について説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: b00da469-4789-4cdd-9f77-7a2e29f28637
ms.openlocfilehash: dc524a06d075b982a6aa1fd266769bfc7d883517
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="exceptions-the-raise-function"></a><span data-ttu-id="3184d-104">例外: raise 関数</span><span class="sxs-lookup"><span data-stu-id="3184d-104">Exceptions: the raise Function</span></span>

<span data-ttu-id="3184d-105">`raise`関数は、エラーまたは例外条件が発生したことを示すために使用します。</span><span class="sxs-lookup"><span data-stu-id="3184d-105">The `raise` function is used to indicate that an error or exceptional condition has occurred.</span></span> <span data-ttu-id="3184d-106">エラーに関する情報は、例外オブジェクトでキャプチャされます。</span><span class="sxs-lookup"><span data-stu-id="3184d-106">Information about the error is captured in an exception object.</span></span>


## <a name="syntax"></a><span data-ttu-id="3184d-107">構文</span><span class="sxs-lookup"><span data-stu-id="3184d-107">Syntax</span></span>

```fsharp
raise (expression)
```

## <a name="remarks"></a><span data-ttu-id="3184d-108">コメント</span><span class="sxs-lookup"><span data-stu-id="3184d-108">Remarks</span></span>
<span data-ttu-id="3184d-109">`raise`関数は、例外オブジェクトを生成し、スタック アンワインド プロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="3184d-109">The `raise` function generates an exception object and initiates a stack unwinding process.</span></span> <span data-ttu-id="3184d-110">スタック アンワインド プロセスは、このプロセスの動作は同じはその他の任意の .NET 言語であるため、共通言語ランタイム (CLR) によって管理されます。</span><span class="sxs-lookup"><span data-stu-id="3184d-110">The stack unwinding process is managed by the common language runtime (CLR), so the behavior of this process is the same as it is in any other .NET language.</span></span> <span data-ttu-id="3184d-111">スタック アンワインド プロセスは、生成された例外に一致する例外ハンドラーに対する検索です。</span><span class="sxs-lookup"><span data-stu-id="3184d-111">The stack unwinding process is a search for an exception handler that matches the generated exception.</span></span> <span data-ttu-id="3184d-112">現在の検索が開始`try...with`式、1 つを使用する必要がある場合。</span><span class="sxs-lookup"><span data-stu-id="3184d-112">The search starts in the current `try...with` expression, if there is one.</span></span> <span data-ttu-id="3184d-113">各パターン、`with`の順序でブロックがチェックされます。</span><span class="sxs-lookup"><span data-stu-id="3184d-113">Each pattern in the `with` block is checked, in order.</span></span> <span data-ttu-id="3184d-114">一致する例外ハンドラーが見つかった場合に例外が処理されたと見なされますそれ以外の場合、スタックがアンワインドされますと`with`一致するハンドラーが見つかるまで、呼び出しチェーンのブロックがチェックされます。</span><span class="sxs-lookup"><span data-stu-id="3184d-114">When a matching exception handler is found, the exception is considered handled; otherwise, the stack is unwound and `with` blocks up the call chain are checked until a matching handler is found.</span></span> <span data-ttu-id="3184d-115">どの`finally`呼び出しチェーンに含まれるブロックは順番に実行スタックがアンワインドとして。</span><span class="sxs-lookup"><span data-stu-id="3184d-115">Any `finally` blocks that are encountered in the call chain are also executed in sequence as the stack unwinds.</span></span>

<span data-ttu-id="3184d-116">`raise`関数は、それと同等の`throw`c# または C++ でします。</span><span class="sxs-lookup"><span data-stu-id="3184d-116">The `raise` function is the equivalent of `throw` in C# or C++.</span></span> <span data-ttu-id="3184d-117">使用して`reraise`呼び出しチェーンを同じ例外を反映 catch ハンドラーでします。</span><span class="sxs-lookup"><span data-stu-id="3184d-117">Use `reraise` in a catch handler to propagate the same exception up the call chain.</span></span>

<span data-ttu-id="3184d-118">コード例を次の例を示します、`raise`例外を生成する関数。</span><span class="sxs-lookup"><span data-stu-id="3184d-118">The following code examples illustrate the use of the `raise` function to generate an exception.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5801.fs)]

<span data-ttu-id="3184d-119">`raise`次の例で示すようにも、関数を使用、.NET 例外を発生させることができます。</span><span class="sxs-lookup"><span data-stu-id="3184d-119">The `raise` function can also be used to raise .NET exceptions, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5802.fs)]
    
## <a name="see-also"></a><span data-ttu-id="3184d-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="3184d-120">See Also</span></span>
[<span data-ttu-id="3184d-121">例外処理</span><span class="sxs-lookup"><span data-stu-id="3184d-121">Exception Handling</span></span>](index.md)

[<span data-ttu-id="3184d-122">例外の種類</span><span class="sxs-lookup"><span data-stu-id="3184d-122">Exception Types</span></span>](exception-types.md)

[<span data-ttu-id="3184d-123">例外: `try...with` 式</span><span class="sxs-lookup"><span data-stu-id="3184d-123">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)

[<span data-ttu-id="3184d-124">例外: `try...finally` 式</span><span class="sxs-lookup"><span data-stu-id="3184d-124">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)

[<span data-ttu-id="3184d-125">例外: `failwith` 関数</span><span class="sxs-lookup"><span data-stu-id="3184d-125">Exceptions: The `failwith` Function</span></span>](the-failwith-function.md)

[<span data-ttu-id="3184d-126">例外: `invalidArg` 関数</span><span class="sxs-lookup"><span data-stu-id="3184d-126">Exceptions: The `invalidArg` Function</span></span>](the-invalidArg-function.md)