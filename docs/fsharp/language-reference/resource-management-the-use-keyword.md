---
title: "リソースの管理: use キーワード (F#)"
description: "F# キーワード 'use' と 'を使用して' の関数は、初期化とリソースの解放を制御できますについて説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 00c3040e-859f-4dad-a7b5-7b8d44dc232c
ms.openlocfilehash: d4e8626f07f1c77e52e8fabd5ccc07dbf1fa8ddd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="resource-management-the-use-keyword"></a>リソースの管理: use キーワード

このトピックは、キーワードをについて説明`use`と`using`関数で、初期化とリソースの解放を制御できます。

## <a name="resources"></a>リソース
用語*リソース*は複数の方法で使用します。 [はい]、リソースがこのコンテキストでは文字列、画像、および、like など、アプリケーションで使用されるデータを指定できます*リソース*グラフィックス デバイス コンテキスト、ファイル ハンドル、ネットワークなど、ソフトウェアやオペレーティング システムのリソースへの参照データベースの接続、待機ハンドルなどの同時実行オブジェクト。 アプリケーションでこれらのリソースを使用するには、オペレーティング システムまたはその他のアプリケーションに提供できるようにプールに、リソースの以降のリリースを続けて、その他のリソース プロバイダーからリソースの取得が含まれます。 問題は、アプリケーションが共通のプールに戻してリソースを解放しない場合に発生します。

## <a name="managing-resources"></a>リソースの管理
確実かつ効率的にリソースを管理するアプリケーションで、迅速にし、予測可能な方法でリソースを解放する必要があります。 .NET Framework では、このことで実行できます。、`System.IDisposable`インターフェイスです。 実装する型`System.IDisposable`が、`System.IDisposable.Dispose`メソッドで、正しくリソースを解放します。 適切に記述されたアプリケーションを確実に`System.IDisposable.Dispose`迅速に制限されているリソースを保持する任意のオブジェクトが不要になったときに呼び出されます。 しかし、ほとんどの .NET 言語が、簡単に作成するサポートを提供し、f# 例外ではありません。 Dispose パターンをサポートする 2 つの有用な言語構成要素がある:`use`バインディング、および`using`関数。

## <a name="use-binding"></a>バインディングを使用します。
`use`キーワードがフォームに似ている`let`バインド。

使用して*値* = *式*

同じ機能を提供、`let`バインドしますが、への呼び出しを追加`Dispose`値がスコープ外に出るときの値にします。 コンパイラによって挿入される値では、null チェックする場合、値はメモ`null`への呼び出し`Dispose`は行われません。

次の例を使用してファイルを自動的に終了する方法を示しています、`use`キーワード。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6301.fs)]

>[!NOTE]
使用することができます`use`コンピュテーション式で、カスタマイズされたバージョンの場合、`use`式を使用します。 詳細については、次を参照してください。[シーケンス](sequences.md)、[非同期ワークフロー](asynchronous-workflows.md)、および[コンピュテーション式](computation-expressions.md)です。


## <a name="using-function"></a>関数を使用してください。
`using`関数は、次の形式。

`using`(*expression1*)*関数またはラムダ*

`using`式、 *expression1*破棄する必要があるオブジェクトを作成します。 結果*expression1* (にあるオブジェクトを破棄する必要があります) では、引数になります*値*を*関数またはラムダ*、これは、1 つを期待している関数残りの値に一致する型の引数によって生成される*expression1*、またはその型の引数を受け取るラムダ式。 ランタイムが呼び出す関数の実行の最後に、`Dispose`リソースを解放し、(値がない限り、 `null`、後者 Dispose の呼び出しは行われません)。

次の例で、`using`ラムダ式を持つ式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6302.fs)]

[次へ]、例に示す、`using`式、関数を使用します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6303.fs)]

関数が既に適用されるいくつかの引数を持つ関数がある場合に注意してください。 次のコード例を示します。 文字列を含むファイルが作成されます`XYZ`です。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6304.fs)]

`using`関数および`use`バインディングは、同じことを実現するほぼ同等の方法です。 `using`キーワードにより、タイミングをより細かく制御`Dispose`と呼びます。 使用すると`using`、`Dispose`を使用するときに、関数、またはラムダ式の最後に呼び出される、`use`キーワード、`Dispose`要素を含むコード ブロックの最後に呼び出されます。 一般に、使用する優先する必要があります`use`の代わりに、`using`関数。


## <a name="see-also"></a>関連項目
[F# 言語リファレンス](index.md)
