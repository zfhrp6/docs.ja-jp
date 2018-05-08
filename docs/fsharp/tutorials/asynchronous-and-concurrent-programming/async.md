---
title: F# で非同期のプログラミング
description: 言語レベルのプログラミング モデルを使いやすく、自然言語を使用して非同期 f# のプログラミングを実現する方法について説明します。
ms.date: 06/20/2016
ms.openlocfilehash: 93ecd05efc493489435214dcd7ae78fffcccec1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="async-programming-in-f"></a>F# で非同期のプログラミング #

> [!NOTE]
> この記事には、いくつかに関する誤りの修正が検出されました。  これが書き込まれています。  参照してください[問題 #666](https://github.com/dotnet/docs/issues/666)への変更点について説明します。

言語レベルのプログラミング モデルが使いやすく、自然言語にするように設計では、非同期 f# のプログラミングを実現できます。

非同期プログラミングの f# のコアは`Async<'T>`、バック グラウンドで実行する起動可能な作業の表現を`'T`特別なを介して、いずれかの型が返されます`return`キーワードまたは`unit`非同期ワークフローがあるない場合返される結果。

主要概念を理解するは非同期式の種類がある`Async<'T>`、これはだけで、_仕様_の非同期のコンテキストで実行する作業をします。 開始の関数のいずれかに明示的に開始されるまでは実行されません (など`Async.RunSynchronously`)。 作業を行って考えたの別の方法ですが、実際には非常にシンプルされていることを終了します。

たとえば、メイン スレッドをブロックすることがなく dotnetfoundation.org から HTML をダウンロードしたいとします。 次のように、これを行うことができます。

```fsharp
open System
open System.Net

let fetchHtmlAsync url = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()

        // Execution of fetchHtmlAsync won't continue until the result
        // of AsyncDownloadString is bound.
        let! html = webClient.AsyncDownloadString(uri)
        return html
    }

let html = "https://dotnetfoundation.org" |> fetchHtmlAsync |> Async.RunSynchronously
printfn "%s" html
```

以上です。 使用する場合を除いて`async`、 `let!`、および`return`、これは、単に通常の f# コード。

注目すべきである、いくつかの構文構造があります。

*   `let!` (を実行する別のコンテキストで) 非同期式の結果にバインドします。
*   `use!` 同様に動作します`let!`がスコープ外になったときにバインドされているリソースを破棄します。
*   `do!` 何も返さない非同期ワークフローが待機されます。
*   `return` 単に非同期式から結果を返します。
*   `return!` 別の非同期ワークフローを実行し、その戻り値をその結果を返します。

さらに、通常`let`、 `use`、および`do`キーワードは、通常の関数と同様、非同期バージョンと共に使用できます。

## <a name="how-to-start-async-code-in-f"></a>F# で非同期コードを起動する方法 #

前述のように、非同期コードは、明示的に開始する必要がある別のコンテキストで実行する作業の仕様です。 これを実現する 2 つの主な方法を次に示します。

1.  `Async.RunSynchronously` 別のスレッドで非同期ワークフローを開始し、その結果を待機します。

```fsharp
open System
open System.Net

let fetchHtmlAsync url = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        let! html = webClient.AsyncDownloadString(uri)
        return html
    }

 // Execution will pause until fetchHtmlAsync finishes
 let html = "https://dotnetfoundation.org" |> fetchHtmlAsync |> Async.RunSynchronously

 // you actually have the result from fetchHtmlAsync now!
 printfn "%s" html
 ```

2.  `Async.Start` 別のスレッドで非同期ワークフローの開始し、は、**いない**結果を待機します。

```fsharp
open System
open System.Net
  
let uploadDataAsync url data = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        webClient.UploadStringAsync(uri, data)
    }

let workflow = uploadDataAsync "https://url-to-upload-to.com" "hello, world!"

// Execution will continue after calling this!
Async.Start(workflow)

printfn "%s" "uploadDataAsync is running in the background..."
 ```

具体的なシナリオに使用できる非同期ワークフローを開始するには、その他の方法はあります。 詳細については[Async リファレンス](https://msdn.microsoft.com/library/ee370232.aspx)です。

### <a name="a-note-on-threads"></a>スレッドに関する注意事項

"に別のスレッド"という語句が上記ことを知っておく重要な**非同期のワークフローがのファサードであるわけではないマルチ スレッド**です。 ワークフロー実際に「移動」を実際の作業を行うには時間の少量の借用して、スレッド間でします。 非同期ワークフロー待っているときに効果的に""(この例では、値を返すためのネットワーク呼び出しの待機)、他のオブジェクトに有効な作業を移動しないでくださいまで時点で借りてが、任意のスレッドは解放されます。 これにより、非同期のワークフローで、できるだけ効率的に実行されるシステムを利用され、大量の I/O シナリオで特に強力なをようになります。

## <a name="how-to-add-parallelism-to-async-code"></a>非同期コードを並列処理を追加する方法

場合があります可能性があり、必要とする並列で複数の非同期ジョブを実行する、その結果を収集する何らかの方法で解釈します。 `Async.Parallel` これが行われます。 強制的に変換する必要があるタスク並列ライブラリを使用することなく実行できる`Task<'T>`と`Async<'T>`型です。

次の例を使用して`Async.Parallel`ダウンロードする HTML 並列で 4 つの人気のあるサイトからこれらのタスクを完了するまで待機し、ダウンロードされた、HTML を印刷します。

```fsharp
open System
open System.Net

let urlList = 
    [ "https://www.microsoft.com"
      "https://www.google.com"
      "https://www.amazon.com"
      "https://www.facebook.com" ]

let fetchHtmlAsync url = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        let! html = webClient.AsyncDownloadString(uri)
        return html
    }

let getHtmlList urls =
    urls
    |> Seq.map fetchHtmlAsync   // Build an Async<'T> for each site
    |> Async.Parallel           // Returns an Async<'T []>
    |> Async.RunSynchronously   // Wait for the result of the parallel work

let htmlList = getHtmlList urlList

// We now have the downloaded HTML for each site!
for html in htmlList do
    printfn "%s" html
```

## <a name="important-info-and-advice"></a>重要な情報とアドバイス

*   すべての関数の使用を最後に"Async"を追加します。

 これは、名前付け規則だけが、これは API の探索可能性などやすくするためです。 同じルーチンの同期および非同期のバージョンがある場合に特には、これは、名前を使用して非同期を明示的に記述することをお勧めします。

*   コンパイラにリッスンします。

 # のコンパイラは非常に厳格な処理を行うことがほぼ不可能になります troubling と同様に実行"async"コード同期的にします。 警告に遭遇した場合はそれを検討する方法にコードが実行されない記号です。 コンパイラを満足することができますと、ほとんどの場合に、コードは、期待どおりに実行されます。

## <a name="for-the-cvb-programmer-looking-into-f"></a>F# に C #/vb プログラマにとって #

このセクションでは、c# での非同期モデルに慣れているものと/vb です。 いない場合、 [c# での非同期プログラミング](../../../csharp/async.md)開始ポイントです。

C #/vb の非同期モデルと f# の非同期モデルの間の基本的な違いがあります。

返す関数を呼び出すときに、`Task`または`Task<'T>`、そのジョブがすでに実行を開始します。 返されたハンドルは、既に実行中の非同期ジョブを表します。 これに対し、f# で非同期関数を呼び出す場合、`Async<'a>`返されるとなるジョブを表す**生成**いくつかの時点です。 F# で非同期のジョブを連結できるために強力ですが、このモデルを理解することが容易に条件付きで実行され、細かくコントロールの使用を開始します。

その他のいくつかの類似点と相違点も注目すべきがあります。

### <a name="similarities"></a>類似点

*   `let!`、 `use!`、および`do!`に似ています`await`内から非同期ジョブを呼び出すときに、`async{ }`ブロックします。

 次の 3 つのキーワードは内でのみ使用できます、`async { }`ブロック、方法と似ています`await`内のみ呼び出すことができます、`async`メソッドです。 つまり、`let!`をキャプチャして、結果を使用する場合は`use!`同じが、何かのリソースが使用すると、後にクリーンアップする必要がありますと`do!`非同期のワークフローが終了する戻り値はありませんが待機する場合に続行する前にします。

*   F# で同様の方法でデータを並列化をサポートしています。

 まったく違う方法で動作が`Async.Parallel`に対応する`Task.WhenAll`シナリオでは、すべてが完了したときに、一連の非同期ジョブの結果をしたいのです。

### <a name="differences"></a>相違点

*   入れ子になった`let!`は使用できませんとは異なり、入れ子になった `await`

 異なり`await`が無期限に、入れ子にすることができます`let!`ことはできませんし、その結果を別の内部で使用する前にバインドされている必要があります`let!`、 `do!`、または`use!`です。

*   キャンセルのサポートは単純な f# と c#/vb です。

 C #/vb を実行して、タスクの中間にあるの取り消しをサポートする場合は、チェックする必要があります、`IsCancellationRequested`プロパティまたは呼び出す`ThrowIfCancellationRequested()`上、`CancellationToken`は async メソッドに渡されるオブジェクト。

これに対し、F# で非同期ワークフローより自然取り消し可能になりません。 キャンセルは、単純な 3 段階のプロセスです。

1.  新規の `CancellationTokenSource` を作成します。
2.  開始の関数に渡します。
3.  呼び出す`Cancel`トークンにします。

例:

```fsharp
open System
open System.Net

let uploadDataAsync url data = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        webClient.UploadStringAsync(uri, data)
    }

let workflow = uploadDataAsync "https://url-to-upload-to.com" "hello, world!"

let token = new CancellationTokenSource()
Async.Start (workflow, token)

// Immediately cancel uploadDataAsync after it's been started.
token.Cancel()
```

以上です。

## <a name="further-resources"></a>他のリソースについて:

*   [MSDN の非同期ワークフロー](https://msdn.microsoft.com/library/dd233250.aspx)
*   [F# の非同期のシーケンス](https://fsprojects.github.io/FSharp.Control.AsyncSeq/library/AsyncSeq.html)
*   [F# データ HTTP ユーティリティ](https://fsharp.github.io/FSharp.Data/library/Http.html)
