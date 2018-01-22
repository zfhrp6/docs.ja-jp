---
title: "Fixed キーワード (f#)"
description: "スタックにローカルを防ぐため、f# を使用して、コレクションがキーワードを '固定' して 'ピン留めできる' 方法について説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 04/24/2017
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 5795ce1f-11bf-4798-9f1f-6e44ffa1477e
ms.openlocfilehash: 1605603bc35941e21c798600140036fb678869b5
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="the-fixed-keyword"></a><span data-ttu-id="1ee41-104">Fixed キーワード</span><span class="sxs-lookup"><span data-stu-id="1ee41-104">The Fixed Keyword</span></span>

<span data-ttu-id="1ee41-105">F# 4.1 が導入されています、`fixed`キーワードで、収集またはガベージ コレクション中に移動されないようにするには、スタックにローカルに「固定」することができます。</span><span class="sxs-lookup"><span data-stu-id="1ee41-105">F# 4.1 introduces the `fixed` keyword, which allows you to "pin" a local onto the stack to prevent it from being collected or moved during garbage-collection.</span></span>  <span data-ttu-id="1ee41-106">低レベルのプログラミング シナリオに使用されます。</span><span class="sxs-lookup"><span data-stu-id="1ee41-106">It is used for low-level programming scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="1ee41-107">構文</span><span class="sxs-lookup"><span data-stu-id="1ee41-107">Syntax</span></span>

```fsharp
use ptr = fixed expression
```

## <a name="remarks"></a><span data-ttu-id="1ee41-108">コメント</span><span class="sxs-lookup"><span data-stu-id="1ee41-108">Remarks</span></span>

<span data-ttu-id="1ee41-109">これは、ポインターを抽出およびを収集したり、ガベージ コレクション中に移動が回避される名にバインドすることを許可する式の構文を拡張します。</span><span class="sxs-lookup"><span data-stu-id="1ee41-109">This extends the syntax of expressions to allow extracting a pointer and binding it to a name which is prevented from being collected or moved during garbage-collection.</span></span>  

<span data-ttu-id="1ee41-110">使用して、式からのポインターは固定されて、`fixed`キーワードが使用して、識別子にバインドされて、`use`キーワード。</span><span class="sxs-lookup"><span data-stu-id="1ee41-110">A pointer from an expression is fixed via the `fixed` keyword is bound to an identifier via the `use` keyword.</span></span>  <span data-ttu-id="1ee41-111">これのセマンティクスは経由でリソースの管理に似ています、`use`キーワード。</span><span class="sxs-lookup"><span data-stu-id="1ee41-111">The semantics of this are similar to resource management via the `use` keyword.</span></span>  <span data-ttu-id="1ee41-112">ポインターは、スコープ内にあることと、固定が不要になったスコープ外にしたら、中に固定されています。</span><span class="sxs-lookup"><span data-stu-id="1ee41-112">The pointer is fixed while it is in scope, and once it is out of scope, it is no longer fixed.</span></span>  <span data-ttu-id="1ee41-113">`fixed`コンテキストの外部で使用することはできません、`use`バインドします。</span><span class="sxs-lookup"><span data-stu-id="1ee41-113">`fixed` cannot be used outside the context of a `use` binding.</span></span>  <span data-ttu-id="1ee41-114">名前に、ポインターをバインドする必要があります`use`です。</span><span class="sxs-lookup"><span data-stu-id="1ee41-114">You must bind the pointer to a name with `use`.</span></span>

<span data-ttu-id="1ee41-115">使用`fixed`関数またはメソッドの式内で発生する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1ee41-115">Use of `fixed` must occur within an expression in a function or a method.</span></span>  <span data-ttu-id="1ee41-116">スクリプト レベルまたはモジュール レベルのスコープで使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="1ee41-116">It cannot be used at a script-level or module-level scope.</span></span>

<span data-ttu-id="1ee41-117">ポインターのすべてのコードのようにこれは安全でない機能であり使用時に警告を生成します。</span><span class="sxs-lookup"><span data-stu-id="1ee41-117">Like all pointer code, this is an unsafe feature and will emit a warning when used.</span></span>

## <a name="example"></a><span data-ttu-id="1ee41-118">例</span><span class="sxs-lookup"><span data-stu-id="1ee41-118">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="1ee41-119">参照</span><span class="sxs-lookup"><span data-stu-id="1ee41-119">See Also</span></span>

[<span data-ttu-id="1ee41-120">NativePtr モジュール</span><span class="sxs-lookup"><span data-stu-id="1ee41-120">NativePtr Module</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/nativeinterop.nativeptr-module-%5Bfsharp%5D)
