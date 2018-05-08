---
title: '例外: raise 関数 (F#)'
description: F# 'raise' 関数が、エラーまたは例外条件が発生したことを示すために使用する方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: bad18bfbccd738a12e16a0e026ade22e96d4cfcb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="exceptions-the-raise-function"></a>例外: raise 関数

`raise`関数は、エラーまたは例外条件が発生したことを示すために使用します。 エラーに関する情報は、例外オブジェクトでキャプチャされます。


## <a name="syntax"></a>構文

```fsharp
raise (expression)
```

## <a name="remarks"></a>コメント
`raise`関数は、例外オブジェクトを生成し、スタック アンワインド プロセスを開始します。 スタック アンワインド プロセスは、このプロセスの動作は同じはその他の任意の .NET 言語であるため、共通言語ランタイム (CLR) によって管理されます。 スタック アンワインド プロセスは、生成された例外に一致する例外ハンドラーに対する検索です。 現在の検索が開始`try...with`式、1 つを使用する必要がある場合。 各パターン、`with`の順序でブロックがチェックされます。 一致する例外ハンドラーが見つかった場合に例外が処理されたと見なされますそれ以外の場合、スタックがアンワインドされますと`with`一致するハンドラーが見つかるまで、呼び出しチェーンのブロックがチェックされます。 どの`finally`呼び出しチェーンに含まれるブロックは順番に実行スタックがアンワインドとして。

`raise`関数は、それと同等の`throw`c# または C++ でします。 使用して`reraise`呼び出しチェーンを同じ例外を反映 catch ハンドラーでします。

コード例を次の例を示します、`raise`例外を生成する関数。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5801.fs)]

`raise`次の例で示すようにも、関数を使用、.NET 例外を発生させることができます。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5802.fs)]
    
## <a name="see-also"></a>関連項目
[例外処理](index.md)

[例外の種類](exception-types.md)

[例外: `try...with` 式](the-try-with-expression.md)

[例外: `try...finally` 式](the-try-finally-expression.md)

[例外: `failwith` 関数](the-failwith-function.md)

[例外: `invalidArg` 関数](the-invalidArg-function.md)
