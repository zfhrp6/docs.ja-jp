---
title: "F# のガイド"
description: "F# で、.NET で実行される関数型プログラミング言語について説明します。"
keywords: .NET, .NET Core
author: jackfoxy
ms.author: phcart
ms.date: 12/01/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: ea27fb37-dad1-4bd4-a3cc-4f5c70767ae9
ms.openlocfilehash: 45f5d2ca794ccea7a35cf6c0bf9d58a3e6500453
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="f-guide"></a><span data-ttu-id="f5016-104">F# のガイド</span><span class="sxs-lookup"><span data-stu-id="f5016-104">F# Guide</span></span>

<span data-ttu-id="f5016-105">F# は、.NET で実行される関数型プログラミング言語です。</span><span class="sxs-lookup"><span data-stu-id="f5016-105">F# is a functional programming language which runs on .NET.</span></span>  <span data-ttu-id="f5016-106">サポートする関数型プログラミング構成要素だけでなくオブジェクトのプログラミング機能もあります。</span><span class="sxs-lookup"><span data-stu-id="f5016-106">In addition to supporting functional programming constructs, it also has object programming capabilities.</span></span>  <span data-ttu-id="f5016-107">このハイブリッド オブジェクト指向の機能を備えた関数型プログラミングは、F# でいずれかのタスクを実行するための実践的な言語です。</span><span class="sxs-lookup"><span data-stu-id="f5016-107">This hybrid of functional programming with object-oriented capabilities makes F# a pragmatic language for accomplishing any task.</span></span>

## <a name="if-youre-new-to-f"></a><span data-ttu-id="f5016-108">F# に慣れていない場合</span><span class="sxs-lookup"><span data-stu-id="f5016-108">If You're New to F#</span></span> #

<span data-ttu-id="f5016-109">F# を初めて始まります、[ツアーの f#](tour.md)言語の概要とそのプログラミングの概念の一部を取得します。</span><span class="sxs-lookup"><span data-stu-id="f5016-109">If you're new to F#, begin with the [Tour of F#](tour.md) to get an overview of the language and some of its programming concepts.</span></span>  <span data-ttu-id="f5016-110">Visual Studio を使用している場合、チュートリアルのプロジェクト テンプレートには、同じコンテンツが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f5016-110">If you're using Visual Studio, the Tutorial project template contains the same content.</span></span>

## <a name="if-youre-experienced-with-f"></a><span data-ttu-id="f5016-111">F# によるした経験が場合</span><span class="sxs-lookup"><span data-stu-id="f5016-111">If You're Experienced with F#</span></span> #

<span data-ttu-id="f5016-112">F# では、対処方法を知っているかの詳細については、特定の言語コンストラクトを表示、[言語リファレンス](language-reference/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="f5016-112">If you know your way around F#, or want to learn more about a specific language construct, see the [Language Reference](language-reference/index.md).</span></span>  <span data-ttu-id="f5016-113">F# 言語のすべての機能の詳細なガイドでは。</span><span class="sxs-lookup"><span data-stu-id="f5016-113">It's a thorough guide of all F# language capabilities.</span></span>

<span data-ttu-id="f5016-114">さらに、 [f# コア ライブラリ リファレンス](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference)は FSharp.Core、f# の一部では、コア ライブラリの学習に役立つ優れたリソースです。</span><span class="sxs-lookup"><span data-stu-id="f5016-114">Additionally, the [F# Core Library Reference](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference) is a great resource for learning about FSharp.Core, the core library which is a part of F#.</span></span>

## <a name="the-f-software-foundation"></a><span data-ttu-id="f5016-115">F# ソフトウェアの基礎</span><span class="sxs-lookup"><span data-stu-id="f5016-115">The F# Software Foundation</span></span>

<span data-ttu-id="f5016-116">Microsoft は、f# 言語およびそのツールの主な開発者が、f# もでバックアップ、独立した foundation、f# ソフトウェア Foundation (FSSF)。</span><span class="sxs-lookup"><span data-stu-id="f5016-116">Although Microsoft is the primary developer of the F# language and its tooling, F# is also backed by an independent foundation, the F# Software Foundation (FSSF).</span></span>

<span data-ttu-id="f5016-117">F# Software Foundation の使命は、F# プログラミング言語の促進、保護、進歩であり、F# プログラマーの多様なインターナショナル コミュニティをサポートし、成長を促進しています。</span><span class="sxs-lookup"><span data-stu-id="f5016-117">The mission of the F# Software Foundation is to promote, protect, and advance the F# programming language, and to support and facilitate the growth of a diverse and international community of F# programmers.</span></span>

<span data-ttu-id="f5016-118">詳細およびコミュニティへの参加については、[fsharp.org](http://fsharp.org) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5016-118">To learn more and get involved, check out [fsharp.org](http://fsharp.org).</span></span>

## <a name="documentation"></a><span data-ttu-id="f5016-119">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="f5016-119">Documentation</span></span>

* [<span data-ttu-id="f5016-120">チュートリアル</span><span class="sxs-lookup"><span data-stu-id="f5016-120">Tutorials</span></span>](tutorials/getting-started/index.md)
* <span data-ttu-id="f5016-121">[ファースト クラス値としての関数](introduction-to-functional-programming/functions-as-first-class-values.md)<!--[Introduction to Functional Programming](introduction-to-functional-programming/index.md)--></span><span class="sxs-lookup"><span data-stu-id="f5016-121">[Functions as First-Class Values](introduction-to-functional-programming/functions-as-first-class-values.md)<!--[Introduction to Functional Programming](introduction-to-functional-programming/index.md)--></span></span>
* [<span data-ttu-id="f5016-122">言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="f5016-122">Language Reference</span></span>](language-reference/index.md)
* [<span data-ttu-id="f5016-123">F# コア ライブラリ リファレンス</span><span class="sxs-lookup"><span data-stu-id="f5016-123">F# Core Library Reference</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference)

## <a name="online-reading-resources"></a><span data-ttu-id="f5016-124">オンライン リソース</span><span class="sxs-lookup"><span data-stu-id="f5016-124">Online Reading Resources</span></span>

* [<span data-ttu-id="f5016-125">F# の楽しみとメリット Gitbook</span><span class="sxs-lookup"><span data-stu-id="f5016-125">F# for Fun and Profit Gitbook</span></span>](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/) 
* [<span data-ttu-id="f5016-126">F# プログラミング Wikibook</span><span class="sxs-lookup"><span data-stu-id="f5016-126">F# Programming Wikibook</span></span>](https://en.wikibooks.org/wiki/F_Sharp_Programming)

## <a name="video-learning-resources"></a><span data-ttu-id="f5016-127">ビデオ学習リソース</span><span class="sxs-lookup"><span data-stu-id="f5016-127">Video Learning Resources</span></span>

* [<span data-ttu-id="f5016-128">YouTube の F# でのプログラミングの概要シリーズ</span><span class="sxs-lookup"><span data-stu-id="f5016-128">Introduction to Programming with F# series on YouTube</span></span>](https://www.youtube.com/watch?v=Teak30_pXHk&list=PLEoMzSkcN8oNiJ67Hd7oRGgD1d4YBxYGC)
* [<span data-ttu-id="f5016-129">FSharpTV の F# の概要シリーズ</span><span class="sxs-lookup"><span data-stu-id="f5016-129">Introduction to F# series on FSharpTV</span></span>](https://fsharp.tv/courses/fsharp-programming-intro/)

## <a name="further-resources"></a><span data-ttu-id="f5016-130">他のリソース</span><span class="sxs-lookup"><span data-stu-id="f5016-130">Further Resources</span></span>

* [<span data-ttu-id="f5016-131">F# series の F# 学習リソース</span><span class="sxs-lookup"><span data-stu-id="f5016-131">F# Learning Resources on fsharp.org</span></span>](http://fsharp.org/learn.html)
* [<span data-ttu-id="f5016-132">F# スニペットの Web サイト</span><span class="sxs-lookup"><span data-stu-id="f5016-132">F# Snippets Website</span></span>](http://www.fssnip.net)
* [<span data-ttu-id="f5016-133">F# ソフトウェアの基礎</span><span class="sxs-lookup"><span data-stu-id="f5016-133">F# Software Foundation</span></span>](http://fsharp.org)