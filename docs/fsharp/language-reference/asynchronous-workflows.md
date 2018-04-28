---
title: 非同期ワークフロー (F#)
description: サポートに関する情報、f# のプログラミング言語を非同期的に、計算を実行するその他の作業の実行をブロックせずに実行されます。
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 1521ea3719f906a45b11d19a27256e87c5643e28
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="asynchronous-workflows"></a>非同期ワークフロー

> [!NOTE]
API リファレンスのリンクをクリックすると MSDN に移動します。  docs.microsoft.com API リファレンスは完全ではありません。

このトピックでは、計算を実行する、非同期的には、その他の作業の実行をブロックすることがなく f# でサポートについて説明します。 たとえば、アプリケーションがその他の作業を実行をユーザーに応答性を維持するための Ui があるアプリケーションを作成する非同期計算を使用できます。

## <a name="syntax"></a>構文

```fsharp
async { expression }
```

## <a name="remarks"></a>コメント

前の構文では、によって表される、計算`expression`は、スリープ状態の非同期操作、I/O、およびその他の非同期操作が実行されるときに、計算の現在のスレッドをブロックすることがなく、非同期的に実行するように設定します。 非同期計算を現在のスレッドで実行が続行中に、多くの場合、バック グラウンド スレッドで開始されます。 式の型は`Async<'T>`ここで、`'T`式によって返される型は、ときに、`return`キーワードを使用します。 このような式の中でコードを呼びます、*非同期ブロック*、または*async ブロック*です。

さまざまな非同期プログラミングの方法があると、 [ `Async` ](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7)クラスがいくつかのシナリオをサポートするメソッドを提供します。 一般的な方法は、作成する`Async`トリガーを起動する関数のいずれかを使用して開始し、これらの計算の計算などに、非同期的に実行する計算を表すオブジェクト。 さまざまなトリガーを起動する関数が、非同期計算を実行中のさまざまな方法を提供し、現在のスレッド、バック グラウンド スレッド、または、.NET Framework タスク オブジェクトを使用するかどうかに依存した 1 つを使用して、継続があるかどうか計算の終了時に実行する関数。 たとえば、非同期計算を開始するには、現在のスレッドを行うこともできます[ `Async.StartImmediate`](https://msdn.microsoft.com/library/2f71d1cc-187f-48cf-ac66-e7fda41c46e3)です。 UI スレッドから非同期計算を開始する場合、キーストロークやマウスのアクティビティなどのユーザー アクションを処理するため、アプリケーションが応答する主要なイベント ループはブロックされません。

## <a name="asynchronous-binding-by-using-let"></a>Let を使用して非同期バインドは!

非同期のワークフローでは、一部の式と操作は同期的でし、一部が非同期的に結果を返すよう設計されている長い計算します。 メソッドを呼び出す場合、非同期的に、通常ではなく`let`使用するバインディング、`let!`です。 効果`let!`は計算が実行されている他の計算やスレッドで継続して実行を有効にします。 右側にある後、`let!`バインディングを返します、非同期のワークフローの残りの部分が実行を再開します。

次のコード間の違いを示しています。`let`と`let!`です。 使用するコードの行`let`実行できる後で使用すると、たとえば、オブジェクトとして非同期計算を作成します`Async.StartImmediate`または[ `Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b)です。 使用するコードの行`let!`計算を開始し、スレッドが、結果が入手可能にするポイントの実行を継続するまで中断します。

```fsharp
// let just stores the result as an asynchronous operation.
let (result1 : Async<byte[]>) = stream.AsyncRead(bufferSize)
// let! completes the asynchronous operation and returns the data.
let! (result2 : byte[])  = stream.AsyncRead(bufferSize)
```

加え`let!`、使用することができます`use!`非同期バインドを実行します。 間の違い`let!`と`use!`間の差として同じ`let`と`use`です。 `use!`、現在のスコープの終了時のオブジェクトが破棄されます。 F# 言語の現在のリリースで`use!`いなくても、null に初期化する値を許可しない`use`はします。

## <a name="asynchronous-primitives"></a>非同期プリミティブ

1 つの非同期タスクを実行し、結果を返すメソッドが呼び出された、*非同期プリミティブ*で使用する専用に設計された、これらと`let!`です。 複数の非同期プリミティブは、f# コア ライブラリで定義されます。 Web アプリケーションのような 2 つのメソッドは、モジュールで定義されて[ `Microsoft.FSharp.Control.WebExtensions` ](https://msdn.microsoft.com/library/95ef17bc-ee3f-44ba-8a11-c90fcf4cf003): [ `WebRequest.AsyncGetResponse` ](https://msdn.microsoft.com/library/09a60c31-e6e2-4b5c-ad23-92a86e50060c)と[ `WebClient.AsyncDownloadString`](https://msdn.microsoft.com/library/8a85a9b7-f712-4cac-a0ce-0a797f8ea32a)です。 両方のプリミティブは、指定された URL の Web ページからデータをダウンロードします。 `AsyncGetResponse` 生成、`System.Net.WebResponse`オブジェクト、および`AsyncDownloadString`を Web ページの HTML を表す文字列を生成します。

非同期 I/O 操作のいくつかのプリミティブに含まれる、 [ `Microsoft.FSharp.Control.CommonExtensions` ](https://msdn.microsoft.com/library/2edb67cb-6814-4a30-849f-b6dbdd042396)モジュール。 これらの拡張メソッドの`System.IO.Stream`クラスが[ `Stream.AsyncRead` ](https://msdn.microsoft.com/library/85698aaa-bdda-47e6-abed-3730f59fda5e)と[ `Stream.AsyncWrite`](https://msdn.microsoft.com/library/1b0a2751-e42a-47e1-bd27-020224adc618)です。

使用可能なその他の非同期プリミティブ、 [f# パワー ツール](https://fsprojects.github.io/VisualFSharpPowerTools/)です。 完全な本体を持つが非同期ブロックで囲まれている関数を定義することで、独自の非同期プリミティブを記述することもできます。

返す、f# の関数を作成する f# 非同期プログラミング モデルとその他の非同期モデルのように設計されて .NET Framework での非同期のメソッドを使用する`Async`オブジェクト。 F# ライブラリでは、これを行うには簡単にできるようにする機能が備わっています。

非同期のワークフローを使用しての一例が含まれるです。内にあるその他の多くのメソッドのドキュメント、 [Async クラス](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7)です。

この例では、非同期のワークフローを使用して、並列で計算を実行する方法を示します。

次のコード例で、関数`fetchAsync`Web 要求から返される HTML テキストを取得します。 `fetchAsync`関数には、非同期コードのブロックが含まれています。 ときに、バインドされる非同期のプリミティブの結果をここでは[ `AsyncDownloadString`](https://msdn.microsoft.com/library/8a85a9b7-f712-4cac-a0ce-0a797f8ea32a)できます! let の代わりに使用されます。

関数を使用する[ `Async.RunSynchronously` ](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b)に非同期操作を実行し、その結果を待機します。 例として、することが複数の非同期操作で並列に実行を使用して、 [ `Async.Parallel` ](https://msdn.microsoft.com/library/aa9b0355-2d55-4858-b943-cbe428de9dc4)関数を`Async.RunSynchronously`関数。 `Async.Parallel`関数の一覧には、`Async`オブジェクトをそれぞれのコードを設定`Async`parallel、および返しますを実行するタスク オブジェクト、`Async`並列計算を表すオブジェクト。 1 つの操作と同じ動作を呼び出す`Async.RunSynchronously`実行を開始します。

`runAll`関数は、次の 3 つの非同期ワークフローを並列でを起動し、これらがすべて完了するまで待機します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet8003.fs)]

## <a name="see-also"></a>関連項目

[F# 言語リファレンス](index.md)

[コンピュテーション式](computation-expressions.md)

[Control.Async クラス](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.async-class-%5bfsharp%5d)
