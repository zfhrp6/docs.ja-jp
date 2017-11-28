---
title: "エントリ ポイント (F#)"
description: "実行が正式に開始、実行可能ファイルとしてコンパイルされた f# プログラムのエントリ ポイントを設定する方法を説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 91455443-ff9d-4510-a7e9-1560bdcd0bb0
ms.openlocfilehash: 685fd4da67119aa5fcaaffd142a0a17c8f5dc7f6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="entry-point"></a>エントリ ポイント

このトピックでは、f# のプログラムにエントリ ポイントを設定するために使用方法について説明します。


## <a name="syntax"></a>構文

```fsharp
[<EntryPoint>]
let-function-binding
```

## <a name="remarks"></a>コメント
前の構文で*let 関数バインド*内の関数の定義、`let`バインドします。

実行可能ファイルの実行が正式な開始位置としてコンパイルされたプログラムへのエントリ ポイントです。 適用することで、f# アプリケーションへのエントリ ポイントを指定する、`EntryPoint`属性をプログラムの`main`関数。 この関数 (を使用して作成された、`let`バインディング)、前回のコンパイル済みファイルの最後の関数でなければなりません。 最後のコンパイル済みファイルは、プロジェクトの最後のファイルまたはコマンドラインに渡される最後のファイルです。

エントリ ポイント関数が型`string array -> int`です。 コマンドラインで指定された引数に渡される、`main`文字列の配列内の関数。 配列の最初の要素が最初の引数です。他の言語であるために、実行可能ファイルの名前は、配列に含まれていません。 戻り値は、プロセスの終了コードとして使用します。 0 は、成功; 通常ことを示します。0 以外の値は、エラーを表します。 0 以外のリターン コードの特定の意味の規則はありません。これらのリターン コードの意味は、アプリケーション固有です。

次の例では、単純な`main`関数。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/entry-point/snippet501.fs)]

このコードを次のコマンドラインを実行すると`EntryPoint.exe 1 2 3`出力は次のとおりです。

```console
Arguments passed to function : [|"1"; "2"; "3"|]
```

## <a name="implicit-entry-point"></a>暗黙のエントリ ポイント
No があるときに**EntryPoint**を明示的に最上位レベルのバインディングは、最後のファイルをコンパイル、エントリ ポイントを示す属性は、エントリ ポイントとして使用されます。


## <a name="see-also"></a>関連項目
[関数](index.md)

[let バインド](let-bindings.md)
