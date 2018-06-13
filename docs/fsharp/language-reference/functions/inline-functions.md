---
title: インライン関数 (F#)
description: 呼び出し元のコードに直接組み込まれている f# インライン関数を使用する方法を説明します。
ms.date: 05/16/2016
ms.openlocfilehash: d265f9b4e828946c510bd8e84b14d5236ab511fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563509"
---
# <a name="inline-functions"></a>インライン関数

*インライン関数*関数が呼び出し元のコードに直接統合されています。


## <a name="using-inline-functions"></a>インライン関数を使用します。
静的な型パラメーターを使用して、型パラメーターでパラメーター化されるすべての関数はインラインにする必要があります。 これは、コンパイラがこれらの型パラメーターを解決できることを保証します。 通常のジェネリック型パラメーターを使用するときに、このような制限はありません。

以外のメンバーの制約の使用を有効にすると、インライン関数でコードを最適化することができます。 ただし、過剰に使用するインライン関数には、コードがコンパイラの最適化やライブラリ関数の実装の変更を受けに可能性があります。 このため、他のすべての最適化の手法を試した場合を除き、最適化のインライン関数の使用を避ける必要があります。 関数またはメソッドのインラインを行うことがありますパフォーマンスが向上するは常に大文字と小文字になっていません。 したがって、こと、指定された関数のインラインを行うには実際にが良い影響を確認するのにパフォーマンスの測定を使用することも必要があります。

`inline`修飾子は、最上位レベルに、モジュール レベルで、またはクラスで、メソッド レベルでの関数に適用できます。

次のコード例は、最上位レベル、インライン インスタンス メソッド、およびインラインの静的メソッドで、インライン関数を示しています。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet201.fs)]
    
## <a name="inline-functions-and-type-inference"></a>インライン関数と型の推論
存在する`inline`型の推論に影響します。 これは、非インライン関数ことはできませんが、インライン関数できますが静的に解決されるため、型パラメーター。 次のコード例は、ケースを示しています。 ここで`inline`ため、静的に解決される型パラメーターを持つ関数を使用すると便利です、`float`変換演算子です。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet202.fs)]

なし、`inline`修飾子、型の推論はここでは、特定の種類を実行する関数`int`です。 ただし、`inline`修飾子は、関数が静的に解決される型パラメーターを持つと推論もします。 `inline`次と修飾子は、型が推論されます。

```fsharp
^a -> unit when ^a : (static member op_Explicit : ^a -> float)
```

したがって、関数への変換をサポートする任意の型を受け取る**float**です。


## <a name="see-also"></a>関連項目
[関数](index.md)

[制約](../generics/constraints.md)

[静的に解決される型パラメーター](../generics/statically-resolved-type-parameters.md)
