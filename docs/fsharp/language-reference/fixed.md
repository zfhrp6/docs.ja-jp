---
title: Fixed キーワード (f#)
description: スタックにローカルを防ぐため、f# を使用して、コレクションがキーワードを '固定' して 'ピン留めできる' 方法について説明します。
ms.date: 04/24/2017
ms.openlocfilehash: 913ee4d7b0f6b2437793d4788e53556d6be6c4db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="the-fixed-keyword"></a>Fixed キーワード

F# 4.1 が導入されています、`fixed`キーワードで、収集またはガベージ コレクション中に移動されないようにするには、スタックにローカルに「固定」することができます。  低レベルのプログラミング シナリオに使用されます。

## <a name="syntax"></a>構文

```fsharp
use ptr = fixed expression
```

## <a name="remarks"></a>コメント

これは、ポインターを抽出およびを収集したり、ガベージ コレクション中に移動が回避される名にバインドすることを許可する式の構文を拡張します。  

使用して、式からのポインターは固定されて、`fixed`キーワードが使用して、識別子にバインドされて、`use`キーワード。  これのセマンティクスは経由でリソースの管理に似ています、`use`キーワード。  ポインターは、スコープ内にあることと、固定が不要になったスコープ外にしたら、中に固定されています。  `fixed` コンテキストの外部で使用することはできません、`use`バインドします。  名前に、ポインターをバインドする必要があります`use`です。

使用`fixed`関数またはメソッドの式内で発生する必要があります。  スクリプト レベルまたはモジュール レベルのスコープで使用することはできません。

ポインターのすべてのコードのようにこれは安全でない機能であり使用時に警告を生成します。

## <a name="example"></a>例

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

## <a name="see-also"></a>関連項目

[NativePtr モジュール](https://msdn.microsoft.com/visualfsharpdocs/conceptual/nativeinterop.nativeptr-module-%5Bfsharp%5D)
