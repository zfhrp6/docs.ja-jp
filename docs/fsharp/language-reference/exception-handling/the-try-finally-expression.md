---
title: '例外: try...finally 式 (F#)'
description: 学習方法、f# 'try… 最後に' 式では、コード ブロックの例外をスローする場合でも、クリーンアップ コードを実行することができます。
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 588e4edb4d25c6d25ef103ba724613db997f68d7
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="exceptions-the-tryfinally-expression"></a>例外: try...finally 式

`try...finally`式では、コード ブロックの例外をスローする場合でも、クリーンアップ コードを実行することができます。


## <a name="syntax"></a>構文

```fsharp
try
    expression1
finally
    expression2
```

## <a name="remarks"></a>コメント
`try...finally`でコードを実行する式を使用できます*expression2*の実行中に例外を生成するかどうかに関係なく上記の構文で*expression1*です。

型*expression2* ; 式全体の値には含まれません、例外が発生していないときに返される型の最後の値は、 *expression1*です。 例外が発生した場合、値は返されません、コール スタックを [次へ] の一致する例外ハンドラーに制御フローを転送します。 例外ハンドラーが見つからない場合、プログラムが終了します。 プログラムは終了し、コードまたは一致するハンドラーのコードが実行される前に、`finally`分岐が実行されます。

次の例では、使用、`try...finally`式。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5701.fs)]

コンソールへの出力は次のとおりです。

```
Closing stream
Exception handled.
```

出力からわかるように、ストリームが閉じられた外側の例外が処理された、およびファイル`test.txt`テキストを含む`test1`バッファーがフラッシュされ、場合でも、例外の転送をディスクに書き込まれることを示します外側の例外ハンドラーに制御します。

なお、`try...with`コンストラクトでは、個別の`try...finally`を構築します。 そのため、コードでは、両方が必要な場合、`with`ブロックと`finally`ブロックを次のコード例のように、2 つの構造を入れ子にする必要があります。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5702.fs)]

コンピュテーション式のコンテキストでシーケンス式と非同期のワークフローを含む**try… finally**式は、カスタム実装を持つことができます。 詳細については、次を参照してください。[コンピュテーション式](../computation-expressions.md)です。


## <a name="see-also"></a>関連項目
[例外処理](index.md)

[例外: `try...with` 式](the-try-with-expression.md)
