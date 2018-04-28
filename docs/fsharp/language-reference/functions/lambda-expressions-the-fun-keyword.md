---
title: 'ラムダ式: fun キーワード (F#)'
description: F# 'fun' キーワードを使用して、匿名関数であるラムダ式を定義する方法を説明します。
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: f2f15a1b482ce3971d0b3d5ffc4f6dcc9ccf1569
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="lambda-expressions-the-fun-keyword-f"></a>ラムダ式: fun キーワード (F#)

`fun`キーワードの使用をラムダ式、つまり、匿名関数を定義します。


## <a name="syntax"></a>構文

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a>コメント
*パラメーター リスト*通常の名前と、必要に応じて、パラメーターの型で構成されます。 一般的に、*パラメーター リスト*f# パターンで構成されることができます。 可能なパターンの一覧については、次を参照してください。[パターン マッチ](../pattern-matching.md)です。 有効なパラメーターのリストには、次の例が含まれます。

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

*式*うち、最後の式には、戻り値が生成されます。 関数の本文です。 有効なラムダ式の例については、次のとおりです。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet301.fs)]
    
## <a name="using-lambda-expressions"></a>ラムダ式の使用
ラムダ式は、リストまたはその他のコレクションで操作を実行し、追加の関数を定義する作業を避けたい場合に特に便利です。 多数の f# ライブラリ関数は、引数としての関数の値を行い、そのような場合、ラムダ式を使用すると特に便利であることができます。 次のコードは、リストの要素をラムダ式を適用します。 この場合、匿名の関数は、一覧のすべての要素に 1 を追加します。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet302.fs)]
    
## <a name="see-also"></a>関連項目
[関数](index.md)
