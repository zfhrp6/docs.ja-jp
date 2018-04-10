---
title: C# の新機能 - C# ガイド
description: C# 言語がどのように進化しているか
keywords: C#, 最新の機能, 新機能, Roslyn
author: BillWagner
ms.author: wiwagn
ms.date: 11/13/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 77deec51-a14d-46d4-9bb3-faf449477149
ms.openlocfilehash: 719fbe826b0b115b19067dbaf0d04f14e6534890
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2017
---
# <a name="whats-new-in-c"></a><span data-ttu-id="d504a-104">C# の新機能</span><span class="sxs-lookup"><span data-stu-id="d504a-104">What's new in C#</span></span> #

<span data-ttu-id="d504a-105">このページでは、C# 言語の各メジャー リリースの新機能に関するロードマップを示しています。</span><span class="sxs-lookup"><span data-stu-id="d504a-105">This page provides a roadmap of new features in each major release of the C# language.</span></span> <span data-ttu-id="d504a-106">以下のリンクで、各リリースで追加された主な機能の詳細情報を確認できます。</span><span class="sxs-lookup"><span data-stu-id="d504a-106">The following links provide detailed information on the major features added in each release.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d504a-107">C# 言語のこれらの機能のいくつかは、*標準ライブラリ*の型とメソッドに依存します。</span><span class="sxs-lookup"><span data-stu-id="d504a-107">The C# language relies on types and methods in a *standard library* for some of the features.</span></span> <span data-ttu-id="d504a-108">一例として、例外処理があります。</span><span class="sxs-lookup"><span data-stu-id="d504a-108">One example is exception processing.</span></span> <span data-ttu-id="d504a-109">すべての `throw` ステートメントまたは式は、スローされたオブジェクトが <xref:System.Exception> から派生していることを確認するために、チェックされます。</span><span class="sxs-lookup"><span data-stu-id="d504a-109">Every `throw` statement or expression is checked to ensure the object being thrown is derived from <xref:System.Exception>.</span></span> <span data-ttu-id="d504a-110">同様に、すべての `catch` は、キャッチされた型が <xref:System.Exception> から派生していることを確認するために、チェックされます。</span><span class="sxs-lookup"><span data-stu-id="d504a-110">Similarly, every `catch` is checked to ensure that the type being caught is derived from <xref:System.Exception>.</span></span> <span data-ttu-id="d504a-111">バージョンごとに新しい要件が追加されている場合があります。</span><span class="sxs-lookup"><span data-stu-id="d504a-111">Each version may add new requirements.</span></span> <span data-ttu-id="d504a-112">古い環境で言語の最新機能を使用するには、特定のライブラリをインストールする必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="d504a-112">To use the latest language features in older environments, you may need to install specific libraries.</span></span> <span data-ttu-id="d504a-113">これらの依存関係については、特定のバージョンごとに用意されたページに記載されています。</span><span class="sxs-lookup"><span data-stu-id="d504a-113">These dependencies are documented in the page for each specific version.</span></span> <span data-ttu-id="d504a-114">詳細については、この依存関係のバックグラウンドにある[言語とライブラリ間の関係](relationships-between-language-and-library.md)に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d504a-114">You can learn more about the [relationships between language and library](relationships-between-language-and-library.md) for background on this dependency.</span></span> 


* <span data-ttu-id="d504a-115">[C# 7.2](csharp-7-2.md):</span><span class="sxs-lookup"><span data-stu-id="d504a-115">[C# 7.2](csharp-7-2.md):</span></span>
    - <span data-ttu-id="d504a-116">このページでは C# 言語の最新の機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="d504a-116">This page describes the latest features in the C# language.</span></span> <span data-ttu-id="d504a-117">C# 7.2 は現在 [Visual Studio 2017 バージョン 15.5](https://www.visualstudio.com/vs/whatsnew/) および [.NET Core 2.0 SDK](../../core/whats-new/index.md) で利用可能です。</span><span class="sxs-lookup"><span data-stu-id="d504a-117">C# 7.2 is currently available in [Visual Studio 2017 version 15.5](https://www.visualstudio.com/vs/whatsnew/), and in the [.NET Core 2.0 SDK](../../core/whats-new/index.md).</span></span>

* <span data-ttu-id="d504a-118">[C# 7.1](csharp-7-1.md):</span><span class="sxs-lookup"><span data-stu-id="d504a-118">[C# 7.1](csharp-7-1.md):</span></span>
    - <span data-ttu-id="d504a-119">このページでは、C# 7.1 の機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="d504a-119">This page describes the features in C# 7.1.</span></span> <span data-ttu-id="d504a-120">これらの機能は、[Visual Studio 2017 バージョン 15.3](https://www.visualstudio.com/vs/whatsnew/) および [.NET Core 2.0 SDK](../../core/whats-new/index.md) に追加されています。</span><span class="sxs-lookup"><span data-stu-id="d504a-120">These features were added in [Visual Studio 2017 version 15.3](https://www.visualstudio.com/vs/whatsnew/), and in the [.NET Core 2.0 SDK](../../core/whats-new/index.md).</span></span>

* <span data-ttu-id="d504a-121">[C# 7](csharp-7.md):</span><span class="sxs-lookup"><span data-stu-id="d504a-121">[C# 7](csharp-7.md):</span></span>
    - <span data-ttu-id="d504a-122">このページでは、C# 7 で追加された機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="d504a-122">This page describes the features added in C# 7.</span></span> <span data-ttu-id="d504a-123">これらの機能は [Visual Studio 2017](https://www.visualstudio.com/vs/whatsnew/) および [.NET Core 1.0](../../core/whats-new/index.md) 以降で追加されました。</span><span class="sxs-lookup"><span data-stu-id="d504a-123">These features were added in [Visual Studio 2017](https://www.visualstudio.com/vs/whatsnew/) and [.NET Core 1.0](../../core/whats-new/index.md) and later</span></span>
     
* <span data-ttu-id="d504a-124">[C# 6](csharp-6.md):</span><span class="sxs-lookup"><span data-stu-id="d504a-124">[C# 6](csharp-6.md):</span></span>
    - <span data-ttu-id="d504a-125">このページでは、C# 6 で追加された機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="d504a-125">This page describes the features that were added in C# 6.</span></span> <span data-ttu-id="d504a-126">これらの機能は、Windows 開発者は Visual Studio 2015 で利用でき、macOS および Linux で C# を使用する開発者は .NET Core 1.0 で利用できます。</span><span class="sxs-lookup"><span data-stu-id="d504a-126">These features are available in Visual Studio 2015 for Windows developers, and on .NET Core 1.0 for developers exploring C# on macOS and Linux.</span></span>

<!--* [C# Interactive](../interactive/index.md): 
    - This page describes C# Interactive, an interactive Read Eval Print Loop (REPL) that you can use to explore the C# language. You can use it to write code interactively and see it execute immediately, without any compile or build step.
-->
* <span data-ttu-id="d504a-127">[クロス プラットフォーム サポート](../../core/index.md):</span><span class="sxs-lookup"><span data-stu-id="d504a-127">[Cross Platform Support](../../core/index.md):</span></span>
    - <span data-ttu-id="d504a-128">C# は .NET Core のサポートにより、複数のプラットフォームで実行できます。</span><span class="sxs-lookup"><span data-stu-id="d504a-128">C#, through .NET Core support, runs on multiple platforms.</span></span> <span data-ttu-id="d504a-129">macOS や、Linux をサポートする多くのディストリビューションのいずれかで C# を使用する場合は、.NET Core の詳細を確認してください。</span><span class="sxs-lookup"><span data-stu-id="d504a-129">If you are interested in trying C# on macOS, or on one of the many supported Linux distributions, learn more about .NET Core.</span></span>

<!--
- [.NET Compiler Platform SDK](../roslyn/index.md):
    - The .NET Compiler Platform SDK enables you to write code that performs static analysis on C# code. You can use these APIs to find potential errors, or bad practices, suggest fixes, and even implement those fixes.
-->
  
## <a name="previous-versions"></a><span data-ttu-id="d504a-130">以前のバージョン</span><span class="sxs-lookup"><span data-stu-id="d504a-130">Previous Versions</span></span>
<span data-ttu-id="d504a-131">次の一覧は、C# 言語と Visual Studio .NET の以前のバージョンで導入された主な機能を示しています。</span><span class="sxs-lookup"><span data-stu-id="d504a-131">The following lists key features that were introduced in previous versions of the C# language and Visual Studio .NET.</span></span>  
  
 * <span data-ttu-id="d504a-132">Visual Studio .NET 2013:</span><span class="sxs-lookup"><span data-stu-id="d504a-132">Visual Studio .NET 2013:</span></span> 
     - <span data-ttu-id="d504a-133">このバージョンの Visual Studio には、バグの修正、パフォーマンスの向上、.NET コンパイラ プラットフォーム ("Roslyn") の Technology Preview (後の <!--Link to ../roslyn/index.md-->.NET コンパイラ プラットフォーム SDK) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d504a-133">This version of Visual Studio included bug fixes, performance improvements, and technology previews of .NET Compiler Platform ("Roslyn") which became the .NET Compiler Platform SDK<!--Link to ../roslyn/index.md-->.</span></span>

 * <span data-ttu-id="d504a-134">C# 5、Visual Studio .NET 2012:</span><span class="sxs-lookup"><span data-stu-id="d504a-134">C# 5, Visual Studio .NET 2012:</span></span> 
     - <span data-ttu-id="d504a-135">`Async` / `await`、および[呼び出し元情報](../programming-guide/concepts/caller-information.md)属性。</span><span class="sxs-lookup"><span data-stu-id="d504a-135">`Async` / `await`, and [caller information](../programming-guide/concepts/caller-information.md) attributes.</span></span>

 * <span data-ttu-id="d504a-136">C# 4、Visual Studio .NET 2010:</span><span class="sxs-lookup"><span data-stu-id="d504a-136">C# 4, Visual Studio .NET 2010:</span></span> 
     - <span data-ttu-id="d504a-137">`Dynamic`、[名前付き引数](../programming-guide/classes-and-structs/named-and-optional-arguments.md)、省略可能なパラメーター、ジェネリックの[共変性および反変性](../programming-guide/concepts/covariance-contravariance/index.md)。</span><span class="sxs-lookup"><span data-stu-id="d504a-137">`Dynamic`, [named arguments](../programming-guide/classes-and-structs/named-and-optional-arguments.md), optional parameters, and generic [covariance and contra variance](../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

 * <span data-ttu-id="d504a-138">C# 3、Visual Studio .NET 2008:</span><span class="sxs-lookup"><span data-stu-id="d504a-138">C# 3, Visual Studio .NET 2008:</span></span> 
     - <span data-ttu-id="d504a-139">オブジェクト初期化子とコレクション初期化子、ラムダ式、拡張メソッド、匿名型、自動プロパティ、ローカル `var` 型推論、および[統合言語クエリ (LINQ)](../programming-guide/concepts/linq/index.md)。</span><span class="sxs-lookup"><span data-stu-id="d504a-139">Object and collection initializers, lambda expressions, extension methods, anonymous types, automatic properties, local `var` type inference, and [Language Integrated Query (LINQ)](../programming-guide/concepts/linq/index.md).</span></span>

 * <span data-ttu-id="d504a-140">C# 2、Visual Studio .NET 2005:</span><span class="sxs-lookup"><span data-stu-id="d504a-140">C# 2, Visual Studio .NET 2005:</span></span> 
     - <span data-ttu-id="d504a-141">匿名メソッド、ジェネリック、null 許容型、反復子/yield、`static` クラス、デリゲートの共変性および反変性。</span><span class="sxs-lookup"><span data-stu-id="d504a-141">Anonymous methods, generics, nullable types, iterators/yield, `static` classes, and covariance and contra variance for delegates.</span></span>

 * <span data-ttu-id="d504a-142">C# 1.1、Visual Studio .NET 2003:</span><span class="sxs-lookup"><span data-stu-id="d504a-142">C# 1.1, Visual Studio .NET 2003:</span></span> 
     - <span data-ttu-id="d504a-143">`#line` プラグマと xml ドキュメント コメント。</span><span class="sxs-lookup"><span data-stu-id="d504a-143">`#line` pragma and xml doc comments.</span></span>

 * <span data-ttu-id="d504a-144">C# 1、Visual Studio .NET 2002:</span><span class="sxs-lookup"><span data-stu-id="d504a-144">C# 1, Visual Studio .NET 2002:</span></span> 
     - <span data-ttu-id="d504a-145">[C#](../csharp.md) の最初のリリース。</span><span class="sxs-lookup"><span data-stu-id="d504a-145">The first release of [C#](../csharp.md).</span></span>   
