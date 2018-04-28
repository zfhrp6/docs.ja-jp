---
title: Fixed キーワード (f#)
description: スタックにローカルを防ぐため、f# を使用して、コレクションがキーワードを '固定' して 'ピン留めできる' 方法について説明します。
author: cartermp
ms.author: phcart
ms.date: 04/24/2017
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 8c1d486ec754335dfbaeec439b1eb949494e4241
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="the-fixed-keyword"></a><span data-ttu-id="ace04-103">Fixed キーワード</span><span class="sxs-lookup"><span data-stu-id="ace04-103">The Fixed Keyword</span></span>

<span data-ttu-id="ace04-104">F# 4.1 が導入されています、`fixed`キーワードで、収集またはガベージ コレクション中に移動されないようにするには、スタックにローカルに「固定」することができます。</span><span class="sxs-lookup"><span data-stu-id="ace04-104">F# 4.1 introduces the `fixed` keyword, which allows you to "pin" a local onto the stack to prevent it from being collected or moved during garbage-collection.</span></span>  <span data-ttu-id="ace04-105">低レベルのプログラミング シナリオに使用されます。</span><span class="sxs-lookup"><span data-stu-id="ace04-105">It is used for low-level programming scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="ace04-106">構文</span><span class="sxs-lookup"><span data-stu-id="ace04-106">Syntax</span></span>

```fsharp
use ptr = fixed expression
```

## <a name="remarks"></a><span data-ttu-id="ace04-107">コメント</span><span class="sxs-lookup"><span data-stu-id="ace04-107">Remarks</span></span>

<span data-ttu-id="ace04-108">これは、ポインターを抽出およびを収集したり、ガベージ コレクション中に移動が回避される名にバインドすることを許可する式の構文を拡張します。</span><span class="sxs-lookup"><span data-stu-id="ace04-108">This extends the syntax of expressions to allow extracting a pointer and binding it to a name which is prevented from being collected or moved during garbage-collection.</span></span>  

<span data-ttu-id="ace04-109">使用して、式からのポインターは固定されて、`fixed`キーワードが使用して、識別子にバインドされて、`use`キーワード。</span><span class="sxs-lookup"><span data-stu-id="ace04-109">A pointer from an expression is fixed via the `fixed` keyword is bound to an identifier via the `use` keyword.</span></span>  <span data-ttu-id="ace04-110">これのセマンティクスは経由でリソースの管理に似ています、`use`キーワード。</span><span class="sxs-lookup"><span data-stu-id="ace04-110">The semantics of this are similar to resource management via the `use` keyword.</span></span>  <span data-ttu-id="ace04-111">ポインターは、スコープ内にあることと、固定が不要になったスコープ外にしたら、中に固定されています。</span><span class="sxs-lookup"><span data-stu-id="ace04-111">The pointer is fixed while it is in scope, and once it is out of scope, it is no longer fixed.</span></span>  <span data-ttu-id="ace04-112">`fixed` コンテキストの外部で使用することはできません、`use`バインドします。</span><span class="sxs-lookup"><span data-stu-id="ace04-112">`fixed` cannot be used outside the context of a `use` binding.</span></span>  <span data-ttu-id="ace04-113">名前に、ポインターをバインドする必要があります`use`です。</span><span class="sxs-lookup"><span data-stu-id="ace04-113">You must bind the pointer to a name with `use`.</span></span>

<span data-ttu-id="ace04-114">使用`fixed`関数またはメソッドの式内で発生する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ace04-114">Use of `fixed` must occur within an expression in a function or a method.</span></span>  <span data-ttu-id="ace04-115">スクリプト レベルまたはモジュール レベルのスコープで使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="ace04-115">It cannot be used at a script-level or module-level scope.</span></span>

<span data-ttu-id="ace04-116">ポインターのすべてのコードのようにこれは安全でない機能であり使用時に警告を生成します。</span><span class="sxs-lookup"><span data-stu-id="ace04-116">Like all pointer code, this is an unsafe feature and will emit a warning when used.</span></span>

## <a name="example"></a><span data-ttu-id="ace04-117">例</span><span class="sxs-lookup"><span data-stu-id="ace04-117">Example</span></span>

```fsharp
open Microsoft.FSharp.NativeInterop

type Point = { mutable X: int; mutable Y: int}

let squareWithPointer (p: nativeptr<int>) =
    // Dereference the pointer at the 0th address.
    let mutable value = NativePtr.get p 0

    // Perform some work
    value <- value * value

    // Set the value in the pointer at the 0th address.
    NativePtr.set p 0 value

let pnt = { X = 1; Y = 2 }
printfn "pnt before - X: %d Y: %d" pnt.X pnt.Y // prints 1 and 2

// Note that the use of 'fixed' is inside a function.
// You cannot fix a pointer at a script-level or module-level scope.
let doPointerWork() =
    use ptr = fixed &pnt.Y

    // Square the Y value
    squareWithPointer ptr
    printfn "pnt after - X: %d Y: %d" pnt.X pnt.Y // prints 1 and 4

doPointerWork()
```

## <a name="see-also"></a><span data-ttu-id="ace04-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="ace04-118">See Also</span></span>

[<span data-ttu-id="ace04-119">NativePtr モジュール</span><span class="sxs-lookup"><span data-stu-id="ace04-119">NativePtr Module</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/nativeinterop.nativeptr-module-%5Bfsharp%5D)
