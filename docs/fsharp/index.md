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
# <a name="f-guide"></a><span data-ttu-id="346f5-103">F# のガイド</span><span class="sxs-lookup"><span data-stu-id="346f5-103">F# Guide</span></span>

<span data-ttu-id="346f5-104">F# では .NET で実行されている機能のプログラミング言語です。</span><span class="sxs-lookup"><span data-stu-id="346f5-104">F# is a functional programming language that runs on .NET.</span></span> <span data-ttu-id="346f5-105">Blend の機能とオブジェクトのプログラミングに関する問題をすべての実用的な解決策をすること、オブジェクトの完全なサポートもあります。</span><span class="sxs-lookup"><span data-stu-id="346f5-105">It also has full support for objects, letting you blend functional and object programming for pragmatic solutions to any problem.</span></span>

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

<span data-ttu-id="346f5-106">F# は、その中心に生産性が向上します。</span><span class="sxs-lookup"><span data-stu-id="346f5-106">F# is about productivity at its heart.</span></span> <span data-ttu-id="346f5-107">F# 用ツール サポートは、広く普及し、高度な機能の完全です。</span><span class="sxs-lookup"><span data-stu-id="346f5-107">The tooling support for F# is ubiquitous and full of advanced features.</span></span>

## <a name="learning-f"></a><span data-ttu-id="346f5-108">F# の学習</span><span class="sxs-lookup"><span data-stu-id="346f5-108">Learning F#</span></span> #

<span data-ttu-id="346f5-109">[F# のツアー](tour.md)多くのコード サンプルの主要な言語機能の概要を示します。</span><span class="sxs-lookup"><span data-stu-id="346f5-109">[Tour of F#](tour.md) gives an overview of major language features with lots of code samples.</span></span> <span data-ttu-id="346f5-110">これは推奨している f# に新しい言語のしくみを理解する場合。</span><span class="sxs-lookup"><span data-stu-id="346f5-110">This is recommended if you are new to F# and want to get a feel for how the language works.</span></span>

<span data-ttu-id="346f5-111">[F# では、Visual Studio での概要](get-started/get-started-visual-studio.md)Windows にいるし、Visual Studio IDE (Integraded 開発環境) の完全なエクスペリエンスをするかどうか。</span><span class="sxs-lookup"><span data-stu-id="346f5-111">[Get started with F# in Visual Studio](get-started/get-started-visual-studio.md) if you're on Windows and want the full Visual Studio IDE (Integraded Development Environment) experience.</span></span>

<span data-ttu-id="346f5-112">[Mac 用の Visual Studio で f# 概要](get-started/get-started-with-visual-studio-for-mac.md)macos Visual Studio IDE を使用する場合。</span><span class="sxs-lookup"><span data-stu-id="346f5-112">[Get started with F# in Visual Studio for Mac](get-started/get-started-with-visual-studio-for-mac.md) if you're on macOS and want to use a Visual Studio IDE.</span></span>

<span data-ttu-id="346f5-113">[Visual Studio のコードで f# で作業を開始](get-started/get-started-vscode.md)軽量なクロスプラット フォームをするかどうか、および IDE の機能パックが発生します。</span><span class="sxs-lookup"><span data-stu-id="346f5-113">[Get Started with F# in Visual Studio Code](get-started/get-started-vscode.md) if you want a lightweight, cross-platform, and feature-packed IDE experience.</span></span>

<span data-ttu-id="346f5-114">[F# では、.NET Core CLI を使用して使ってみる](get-started/get-started-command-line.md)コマンド ライン ツールを使用する場合。</span><span class="sxs-lookup"><span data-stu-id="346f5-114">[Get started with F# with the .NET Core CLI](get-started/get-started-command-line.md) if you want to use command-line tools.</span></span>

<span data-ttu-id="346f5-115">[F# および Xamarin の概要](https://docs.microsoft.com/xamarin/cross-platform/platform/fsharp/)f# とモバイルのプログラミングに関するします。</span><span class="sxs-lookup"><span data-stu-id="346f5-115">[Get started with F# and Xamarin](https://docs.microsoft.com/xamarin/cross-platform/platform/fsharp/) for mobile programming with F#.</span></span>

## <a name="references"></a><span data-ttu-id="346f5-116">参照</span><span class="sxs-lookup"><span data-stu-id="346f5-116">References</span></span>

<span data-ttu-id="346f5-117">[F# 言語リファレンス](language-reference/index.md)の f# 言語のすべての機能の公式、包括的な参照です。</span><span class="sxs-lookup"><span data-stu-id="346f5-117">[F# Language Reference](language-reference/index.md) is the official, comprehensive reference for all F# language features.</span></span> <span data-ttu-id="346f5-118">各記事は、構文について説明し、コード サンプルを示します。</span><span class="sxs-lookup"><span data-stu-id="346f5-118">Each article explains the syntax and shows code samples.</span></span> <span data-ttu-id="346f5-119">目次のフィルター バーを使用するには特定の記事を検索します。</span><span class="sxs-lookup"><span data-stu-id="346f5-119">You can use the filter bar in the table of contents to find specific articles.</span></span>

<span data-ttu-id="346f5-120">[F# コア ライブラリ リファレンス](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference)f# コア ライブラリの API リファレンスがします。</span><span class="sxs-lookup"><span data-stu-id="346f5-120">[F# Core Library Reference](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference) is the API reference for the F# Core Library.</span></span>


## <a name="additional-guides"></a><span data-ttu-id="346f5-121">その他のガイド</span><span class="sxs-lookup"><span data-stu-id="346f5-121">Additional guides</span></span>

<span data-ttu-id="346f5-122">[F# では、楽しくて利益の](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/)F# で学習するための包括的な非常に詳細なブックします。</span><span class="sxs-lookup"><span data-stu-id="346f5-122">[F# for Fun and Profit](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/) is a comprehensive and very detailed book on learning F#.</span></span> <span data-ttu-id="346f5-123">その内容と作成者は、f# コミュニティ大好きです。</span><span class="sxs-lookup"><span data-stu-id="346f5-123">Its contents and author are beloved by the F# community.</span></span> <span data-ttu-id="346f5-124">対象者は、オブジェクト指向プログラミングの経験によって、開発者は、主にです。</span><span class="sxs-lookup"><span data-stu-id="346f5-124">The target audience is primarily developers with an object oriented programming background.</span></span>

<span data-ttu-id="346f5-125">[F# のプログラミング Wikibook](https://en.wikibooks.org/wiki/F_Sharp_Programming) f# に関する wikibook がします。</span><span class="sxs-lookup"><span data-stu-id="346f5-125">[F# Programming Wikibook](https://en.wikibooks.org/wiki/F_Sharp_Programming) is a wikibook about learning F#.</span></span> <span data-ttu-id="346f5-126">F# community の製品です。</span><span class="sxs-lookup"><span data-stu-id="346f5-126">It is also a product of the F# community.</span></span> <span data-ttu-id="346f5-127">対象者は、f#、若干のオブジェクト指向プログラミングの経験に慣れていないユーザーです。</span><span class="sxs-lookup"><span data-stu-id="346f5-127">The target audience is people who are new to F#, with a little bit of object oriented programming background.</span></span>

## <a name="learn-f-through-videos"></a><span data-ttu-id="346f5-128">ビデオを F# で学習します</span><span class="sxs-lookup"><span data-stu-id="346f5-128">Learn F# through videos</span></span>

<span data-ttu-id="346f5-129">[YouTube の f# チュートリアル](https://www.youtube.com/watch?v=c7eNDJN758U)は、優れた入門 f# Visual Studio を使用して、1.5 時間の間に多数の優れた例を示しています。</span><span class="sxs-lookup"><span data-stu-id="346f5-129">[F# tutorial on YouTube](https://www.youtube.com/watch?v=c7eNDJN758U) is a great introduction to F# using Visual Studio, showing lots of great examples over the course of 1.5 hours.</span></span> <span data-ttu-id="346f5-130">対象者は、f# を初めて Visual Studio の開発者です。</span><span class="sxs-lookup"><span data-stu-id="346f5-130">The target audience is Visual Studio developers who are new to F#.</span></span>

<span data-ttu-id="346f5-131">[F# によるプログラミングの概要](https://www.youtube.com/watch?v=Teak30_pXHk&list=PLEoMzSkcN8oNiJ67Hd7oRGgD1d4YBxYGC)はメインのエディターとして Visual Studio のコードを使用する優れたビデオ シリーズです。</span><span class="sxs-lookup"><span data-stu-id="346f5-131">[Introduction to Programming with F#](https://www.youtube.com/watch?v=Teak30_pXHk&list=PLEoMzSkcN8oNiJ67Hd7oRGgD1d4YBxYGC) is a great video series that uses Visual Studio Code as the main editor.</span></span> <span data-ttu-id="346f5-132">ビデオ シリーズでは、何もから開始され、テキスト ベースの RPG ビデオ ゲームの構築を終了します。</span><span class="sxs-lookup"><span data-stu-id="346f5-132">The video series starts from nothing and ends with building a text-based RPG video game.</span></span> <span data-ttu-id="346f5-133">対象者は、Visual Studio Code (または軽量 IDE) を優先し、f# に慣れていない開発者です。</span><span class="sxs-lookup"><span data-stu-id="346f5-133">The target audience is developers who prefer Visual Studio Code (or a lightweight IDE) and are new to F#.</span></span>

<span data-ttu-id="346f5-134">[F# の開発者向けの Visual Studio 2017 の新](https://www.linkedin.com/learning/what-s-new-in-visual-studio-2017-for-f-sharp-for-developers)の F# では、Visual Studio 2017 で、新しい機能の一部を表示するビデオのコースがします。</span><span class="sxs-lookup"><span data-stu-id="346f5-134">[What's New in Visual Studio 2017 for F# For Developers](https://www.linkedin.com/learning/what-s-new-in-visual-studio-2017-for-f-sharp-for-developers) is a video course that shows some of the newer features for F# in Visual Studio 2017.</span></span> <span data-ttu-id="346f5-135">対象者は、f# を初めて Visual Studio の開発者です。</span><span class="sxs-lookup"><span data-stu-id="346f5-135">The target audience is Visual Studio developers who are new to F#.</span></span>

## <a name="other-useful-resources"></a><span data-ttu-id="346f5-136">その他の便利なリソース</span><span class="sxs-lookup"><span data-stu-id="346f5-136">Other useful resources</span></span>

<span data-ttu-id="346f5-137">[F# スニペット web サイト](http://www.fssnip.net)f#、初級から非常に高度なスニペットまでの範囲にあるあらゆるものを行う方法を示すコード スニペットの大規模なセットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="346f5-137">The [F# Snippets Website](http://www.fssnip.net) contains a massive set of code snippets showing how to do just about anything in F#, ranging from absolute beginner to highly advanced snippets.</span></span>

<span data-ttu-id="346f5-138">[F# ソフトウェア Foundation Slack](http://fsharp.org/guides/slack/)最適な場所が初心者と似ていますの専門家は、頻度の高いおり、世界中の最適な f# のプログラマのチャットに使用できるいくつか。</span><span class="sxs-lookup"><span data-stu-id="346f5-138">The [F# Software Foundation Slack](http://fsharp.org/guides/slack/) is a great place for beginners and experts alike, is highly active, and has some of world's best F# programmers available for a chat.</span></span> <span data-ttu-id="346f5-139">参加を強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="346f5-139">We highly recommend joining.</span></span>

## <a name="the-f-software-foundation"></a><span data-ttu-id="346f5-140">F# ソフトウェアの基礎</span><span class="sxs-lookup"><span data-stu-id="346f5-140">The F# Software Foundation</span></span>

<span data-ttu-id="346f5-141">マイクロソフトでは、f# 言語やそのツールと Visual Studio での主な開発者は、f# も支えられた独立の foundation、f# ソフトウェア Foundation (FSSF)。</span><span class="sxs-lookup"><span data-stu-id="346f5-141">Although Microsoft is the primary developer of the F# language and its tools in Visual Studio, F# is also backed by an independent foundation, the F# Software Foundation (FSSF).</span></span>

<span data-ttu-id="346f5-142">F# Software Foundation の使命は、F# プログラミング言語の促進、保護、進歩であり、F# プログラマーの多様なインターナショナル コミュニティをサポートし、成長を促進しています。</span><span class="sxs-lookup"><span data-stu-id="346f5-142">The mission of the F# Software Foundation is to promote, protect, and advance the F# programming language, and to support and facilitate the growth of a diverse and international community of F# programmers.</span></span>

<span data-ttu-id="346f5-143">詳細およびコミュニティへの参加については、[fsharp.org](http://fsharp.org) を参照してください。参加するには無料で、f# foundation の開発者のネットワークを使用して、見逃したくない点です。</span><span class="sxs-lookup"><span data-stu-id="346f5-143">To learn more and get involved, check out [fsharp.org](http://fsharp.org). It's free to join, and the network of F# developers in the foundation is something you don't want to miss out on!</span></span>
