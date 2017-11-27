---
title: "F# のガイド"
description: "F# プログラミング言語、関数型プログラミングのファースト クラスのサポートを提供する .NET 用のオープン ソース言語について説明します。"
keywords: .NET, .NET Core
author: jackfoxy
ms.author: phcart
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: ea27fb37-dad1-4bd4-a3cc-4f5c70767ae9
ms.openlocfilehash: 4ddd77cef6cf70a63f1af81359d82eda27a01593
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="f-guide"></a><span data-ttu-id="14782-104">F# のガイド</span><span class="sxs-lookup"><span data-stu-id="14782-104">F# Guide</span></span>

<span data-ttu-id="14782-105">F# は、.NET 用のクロス プラットフォームのオープン ソース プログラミング言語であり、オブジェクト指向プログラミングと命令型プログラミングのサポートと共に、関数型プログラミングの優れたサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="14782-105">F# is a cross-platform, open source programming language for .NET which provides first-class support for functional programming, along with support of object-oriented and imperative programming.</span></span>  <span data-ttu-id="14782-106">Visual F# コンパイラとツールは Microsoft による F# プログラミング言語の実装であり、これにより F# は .NET のファースト クラスのメンバーになっています。</span><span class="sxs-lookup"><span data-stu-id="14782-106">The Visual F# compiler and tooling are Microsoft's implementation and tooling for the F# programming language, making F# a first-class member of .NET.</span></span>

## <a name="if-youre-new-to-f"></a><span data-ttu-id="14782-107">F# に慣れていない場合</span><span class="sxs-lookup"><span data-stu-id="14782-107">If You're New to F#</span></span> #

<span data-ttu-id="14782-108">F# を初めて始まります、[ツアーの f#](tour.md)言語の概要を取得します。</span><span class="sxs-lookup"><span data-stu-id="14782-108">If you're new to F#, begin with the [Tour of F#](tour.md) to get an overview of the language.</span></span>

<span data-ttu-id="14782-109">学習することも推奨、[ファースト クラス値として機能](introduction-to-functional-programming/functions-as-first-class-values.md)<!--[Introduction to Functional Progamming](introduction-to-functional-programming/index.md)-->を f# で作業するために不可欠である関数型プログラミングの概念を参照してください。</span><span class="sxs-lookup"><span data-stu-id="14782-109">It's also recommended that you go through the [Functions as First-Class Values](introduction-to-functional-programming/functions-as-first-class-values.md)<!--[Introduction to Functional Progamming](introduction-to-functional-programming/index.md)--> to learn Functional Programming concepts which are essential to working with F#.</span></span>

<span data-ttu-id="14782-110">[チュートリアル](tutorials/getting-started/index.md)には、さまざまなスキル レベルと言語の機能のステップ バイ ステップ ガイドもあります。</span><span class="sxs-lookup"><span data-stu-id="14782-110">The [Tutorials](tutorials/getting-started/index.md) also have step-by-step guides for various skill levels and features of the language.</span></span>

## <a name="if-youre-experienced-with-f"></a><span data-ttu-id="14782-111">F# によるした経験が場合</span><span class="sxs-lookup"><span data-stu-id="14782-111">If You're Experienced with F#</span></span> #

<span data-ttu-id="14782-112">F# の使用方法がわかっている場合、[言語リファレンス](language-reference/index.md)で多くの使用方法を知ることができます。多数のコード サンプルで補足された言語のあらゆる側面を徹底的に解説しています。</span><span class="sxs-lookup"><span data-stu-id="14782-112">If you know your way around F#, you'll find a lot of use in the [Language Reference](language-reference/index.md), which documents each aspect of the language thoroughly, supplemented by numerous code samples.</span></span>  <span data-ttu-id="14782-113">「[F# Core Library Reference](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference)」 (F# コア ライブラリ リファレンス) にも多くの使用方法が記載されています。</span><span class="sxs-lookup"><span data-stu-id="14782-113">You'll also find a lot of use in the [F# Core Library Reference](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference).</span></span>  <span data-ttu-id="14782-114">F# コア ライブラリの参照は、MSDN から離れた場所と、これらの現在のドキュメントに最終的に移動します。</span><span class="sxs-lookup"><span data-stu-id="14782-114">The F# Core Library Reference will eventually move away from MSDN and into these current docs.</span></span>

## <a name="the-f-software-foundation"></a><span data-ttu-id="14782-115">F# ソフトウェアの基礎</span><span class="sxs-lookup"><span data-stu-id="14782-115">The F# Software Foundation</span></span>

<span data-ttu-id="14782-116">マイクロソフトでは、F# 言語および Visual F# ツールの主な開発者ですが、F# は、F# Software Foundation (FSSF) という独立した団体によってもサポートされています。</span><span class="sxs-lookup"><span data-stu-id="14782-116">Although Microsoft is the primary developer of the F# language and Visual F# Tooling, F# is also backed by an independent foundation, the F# Software Foundation (FSSF).</span></span>

<span data-ttu-id="14782-117">F# Software Foundation の使命は、F# プログラミング言語の促進、保護、進歩であり、F# プログラマーの多様なインターナショナル コミュニティをサポートし、成長を促進しています。</span><span class="sxs-lookup"><span data-stu-id="14782-117">The mission of the F# Software Foundation is to promote, protect, and advance the F# programming language, and to support and facilitate the growth of a diverse and international community of F# programmers.</span></span>

<span data-ttu-id="14782-118">詳細およびコミュニティへの参加については、[fsharp.org](http://fsharp.org) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="14782-118">To learn more and get involved, check out [fsharp.org](http://fsharp.org).</span></span>

## <a name="documentation"></a><span data-ttu-id="14782-119">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="14782-119">Documentation</span></span>

* [<span data-ttu-id="14782-120">チュートリアル</span><span class="sxs-lookup"><span data-stu-id="14782-120">Tutorials</span></span>](tutorials/getting-started/index.md)
* <span data-ttu-id="14782-121">[ファースト クラス値としての関数](introduction-to-functional-programming/functions-as-first-class-values.md)<!--[Introduction to Functional Programming](introduction-to-functional-programming/index.md)--></span><span class="sxs-lookup"><span data-stu-id="14782-121">[Functions as First-Class Values](introduction-to-functional-programming/functions-as-first-class-values.md)<!--[Introduction to Functional Programming](introduction-to-functional-programming/index.md)--></span></span>
* [<span data-ttu-id="14782-122">言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="14782-122">Language Reference</span></span>](language-reference/index.md)
* [<span data-ttu-id="14782-123">F# コア ライブラリ リファレンス</span><span class="sxs-lookup"><span data-stu-id="14782-123">F# Core Library Reference</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference)

## <a name="online-reading-resources"></a><span data-ttu-id="14782-124">オンライン リソース</span><span class="sxs-lookup"><span data-stu-id="14782-124">Online Reading Resources</span></span>

* [<span data-ttu-id="14782-125">F# の楽しみとメリット Gitbook</span><span class="sxs-lookup"><span data-stu-id="14782-125">F# for Fun and Profit Gitbook</span></span>](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/) 
* [<span data-ttu-id="14782-126">F# プログラミング Wikibook</span><span class="sxs-lookup"><span data-stu-id="14782-126">F# Programming Wikibook</span></span>](https://en.wikibooks.org/wiki/F_Sharp_Programming)

## <a name="video-learning-resources"></a><span data-ttu-id="14782-127">ビデオ学習リソース</span><span class="sxs-lookup"><span data-stu-id="14782-127">Video Learning Resources</span></span>

* [<span data-ttu-id="14782-128">YouTube の F# でのプログラミングの概要シリーズ</span><span class="sxs-lookup"><span data-stu-id="14782-128">Introduction to Programming with F# series on YouTube</span></span>](https://www.youtube.com/watch?v=Teak30_pXHk&list=PLEoMzSkcN8oNiJ67Hd7oRGgD1d4YBxYGC)
* [<span data-ttu-id="14782-129">FSharpTV の F# の概要シリーズ</span><span class="sxs-lookup"><span data-stu-id="14782-129">Introduction to F# series on FSharpTV</span></span>](https://fsharp.tv/courses/fsharp-programming-intro/)

## <a name="further-resources"></a><span data-ttu-id="14782-130">他のリソース</span><span class="sxs-lookup"><span data-stu-id="14782-130">Further Resources</span></span>

* [<span data-ttu-id="14782-131">F# series の F# 学習リソース</span><span class="sxs-lookup"><span data-stu-id="14782-131">F# Learning Resources on fsharp.org</span></span>](http://fsharp.org/learn.html)
* [<span data-ttu-id="14782-132">F# スニペットの Web サイト</span><span class="sxs-lookup"><span data-stu-id="14782-132">F# Snippets Website</span></span>](http://www.fssnip.net)
* [<span data-ttu-id="14782-133">F# ソフトウェアの基礎</span><span class="sxs-lookup"><span data-stu-id="14782-133">F# Software Foundation</span></span>](http://fsharp.org)
