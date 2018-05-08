---
title: F# のガイド
description: このガイドでは、f#、.NET で実行される関数型プログラミング言語のさまざまな学習教材の概要を説明します。
author: jackfoxy
ms.date: 03/19/2018
ms.openlocfilehash: 393214a5da7445d8ee3dced844da8592f4ca6d31
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="f-guide"></a>F# のガイド

F# では .NET で実行されている機能のプログラミング言語です。 Blend の機能とオブジェクトのプログラミングに関する問題をすべての実用的な解決策をすること、オブジェクトの完全なサポートもあります。

```fsharp
open System // Get access to functionality in System namespace.

// Function: takes a name and produces a greeting.
let getGreeting name =
    sprintf "Hello, %s! Isn't F# great?" name

// Use the EntryPoint attribute to run the program.
[<EntryPoint>]
let main args =
    // Define a list of names
    let names = [| "Don"; "Julia"; "Xi" |]
    
    // Print a fun greeting for each name!
    names
    |> Array.map getGreeting
    |> Array.iter (fun greeting -> printfn "%s" greeting)

    0
```

F# は、その中心に生産性が向上します。 F# 用ツール サポートは、広く普及し、高度な機能の完全です。

## <a name="learning-f"></a>F# の学習 #

[F# のツアー](tour.md)多くのコード サンプルの主要な言語機能の概要を示します。 これは推奨している f# に新しい言語のしくみを理解する場合。

[F# では、Visual Studio での概要](get-started/get-started-visual-studio.md)Windows にいるし、Visual Studio IDE (Integraded 開発環境) の完全なエクスペリエンスをするかどうか。

[Mac 用の Visual Studio で f# 概要](get-started/get-started-with-visual-studio-for-mac.md)macos Visual Studio IDE を使用する場合。

[Visual Studio のコードで f# で作業を開始](get-started/get-started-vscode.md)軽量なクロスプラット フォームをするかどうか、および IDE の機能パックが発生します。

[F# では、.NET Core CLI を使用して使ってみる](get-started/get-started-command-line.md)コマンド ライン ツールを使用する場合。

[F# および Xamarin の概要](https://docs.microsoft.com/xamarin/cross-platform/platform/fsharp/)f# とモバイルのプログラミングに関するします。

## <a name="references"></a>参照

[F# 言語リファレンス](language-reference/index.md)の f# 言語のすべての機能の公式、包括的な参照です。 各記事は、構文について説明し、コード サンプルを示します。 目次のフィルター バーを使用するには特定の記事を検索します。

[F# コア ライブラリ リファレンス](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference)f# コア ライブラリの API リファレンスがします。


## <a name="additional-guides"></a>その他のガイド

[F# では、楽しくて利益の](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/)F# で学習するための包括的な非常に詳細なブックします。 その内容と作成者は、f# コミュニティ大好きです。 対象者は、オブジェクト指向プログラミングの経験によって、開発者は、主にです。

[F# のプログラミング Wikibook](https://en.wikibooks.org/wiki/F_Sharp_Programming) f# に関する wikibook がします。 F# community の製品です。 対象者は、f#、若干のオブジェクト指向プログラミングの経験に慣れていないユーザーです。

## <a name="learn-f-through-videos"></a>ビデオを F# で学習します

[YouTube の f# チュートリアル](https://www.youtube.com/watch?v=c7eNDJN758U)は、優れた入門 f# Visual Studio を使用して、1.5 時間の間に多数の優れた例を示しています。 対象者は、f# を初めて Visual Studio の開発者です。

[F# によるプログラミングの概要](https://www.youtube.com/watch?v=Teak30_pXHk&list=PLEoMzSkcN8oNiJ67Hd7oRGgD1d4YBxYGC)はメインのエディターとして Visual Studio のコードを使用する優れたビデオ シリーズです。 ビデオ シリーズでは、何もから開始され、テキスト ベースの RPG ビデオ ゲームの構築を終了します。 対象者は、Visual Studio Code (または軽量 IDE) を優先し、f# に慣れていない開発者です。

[F# の開発者向けの Visual Studio 2017 の新](https://www.linkedin.com/learning/what-s-new-in-visual-studio-2017-for-f-sharp-for-developers)の F# では、Visual Studio 2017 で、新しい機能の一部を表示するビデオのコースがします。 対象者は、f# を初めて Visual Studio の開発者です。

## <a name="other-useful-resources"></a>その他の便利なリソース

[F# スニペット web サイト](http://www.fssnip.net)f#、初級から非常に高度なスニペットまでの範囲にあるあらゆるものを行う方法を示すコード スニペットの大規模なセットが含まれています。

[F# ソフトウェア Foundation Slack](http://fsharp.org/guides/slack/)最適な場所が初心者と似ていますの専門家は、頻度の高いおり、世界中の最適な f# のプログラマのチャットに使用できるいくつか。 参加を強くお勧めします。

## <a name="the-f-software-foundation"></a>F# ソフトウェアの基礎

マイクロソフトでは、f# 言語やそのツールと Visual Studio での主な開発者は、f# も支えられた独立の foundation、f# ソフトウェア Foundation (FSSF)。

F# Software Foundation の使命は、F# プログラミング言語の促進、保護、進歩であり、F# プログラマーの多様なインターナショナル コミュニティをサポートし、成長を促進しています。

詳細およびコミュニティへの参加については、[fsharp.org](http://fsharp.org) を参照してください。参加するには無料で、f# foundation の開発者のネットワークを使用して、見逃したくない点です。
