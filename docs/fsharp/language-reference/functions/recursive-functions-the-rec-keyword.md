---
title: '再帰関数: rec キーワード (F#)'
description: 再帰関数を定義する 'let' キーワードを使用して f# 'rec' キーワードが使用される方法を説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 6039a48eae2b16aa1d82617176460d727a878d87
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="recursive-functions-the-rec-keyword"></a>再帰関数: rec キーワード

`rec`と共にキーワードが使用する、`let`再帰関数を定義するキーワードです。


## <a name="syntax"></a>構文

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

## <a name="remarks"></a>コメント
再帰関数は、自身を呼び出す関数は、f# 言語で明示的に識別されます。 これにより、関数のスコープで定義されている識別子を使用可能なにします。

次のコードを計算する再帰関数を示しています、 *n*番目のフィボナッチ数。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

>[!NOTE]
実際には、上記のようなコードは、事前に計算された値の再計算が伴うのでメモリとプロセッサ時間の浪費になります。


メソッドは、暗黙的に型内で再帰追加する必要はありません、`rec`キーワード。 クラス内の let バインディングは、暗黙的に再帰的ではありません。


## <a name="mutually-recursive-functions"></a>相互再帰関数
関数は、場合によって*相互再帰*呼び出しが、1 つの関数呼び出しを呼び出して、最初の呼び出しの数に別間に、円を描くことを意味します。 このような関数の定義は、1 つで一緒にする必要があります`let`して、バインド、`and`それらをリンクするキーワードです。

次の例は、2 つを一緒には再帰関数。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a>関連項目
[関数](index.md)
