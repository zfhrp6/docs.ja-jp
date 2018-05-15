---
title: C# の新機能 - C# ガイド
description: C# 言語がどのように進化しているか
ms.date: 11/13/2017
ms.assetid: 77deec51-a14d-46d4-9bb3-faf449477149
ms.openlocfilehash: 3fc42809943b10d09d59780576dd9768d9e16ec4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="whats-new-in-c"></a><span data-ttu-id="570af-103">C# の新機能</span><span class="sxs-lookup"><span data-stu-id="570af-103">What's new in C#</span></span> #

<span data-ttu-id="570af-104">このページでは、C# 言語の各メジャー リリースの新機能に関するロードマップを示しています。</span><span class="sxs-lookup"><span data-stu-id="570af-104">This page provides a roadmap of new features in each major release of the C# language.</span></span> <span data-ttu-id="570af-105">以下のリンクで、各リリースで追加された主な機能の詳細情報を確認できます。</span><span class="sxs-lookup"><span data-stu-id="570af-105">The following links provide detailed information on the major features added in each release.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="570af-106">C# 言語のこれらの機能のいくつかは、*標準ライブラリ*の型とメソッドに依存します。</span><span class="sxs-lookup"><span data-stu-id="570af-106">The C# language relies on types and methods in a *standard library* for some of the features.</span></span> <span data-ttu-id="570af-107">一例として、例外処理があります。</span><span class="sxs-lookup"><span data-stu-id="570af-107">One example is exception processing.</span></span> <span data-ttu-id="570af-108">すべての `throw` ステートメントまたは式は、スローされたオブジェクトが <xref:System.Exception> から派生していることを確認するために、チェックされます。</span><span class="sxs-lookup"><span data-stu-id="570af-108">Every `throw` statement or expression is checked to ensure the object being thrown is derived from <xref:System.Exception>.</span></span> <span data-ttu-id="570af-109">同様に、すべての `catch` は、キャッチされた型が <xref:System.Exception> から派生していることを確認するために、チェックされます。</span><span class="sxs-lookup"><span data-stu-id="570af-109">Similarly, every `catch` is checked to ensure that the type being caught is derived from <xref:System.Exception>.</span></span> <span data-ttu-id="570af-110">バージョンごとに新しい要件が追加されている場合があります。</span><span class="sxs-lookup"><span data-stu-id="570af-110">Each version may add new requirements.</span></span> <span data-ttu-id="570af-111">古い環境で言語の最新機能を使用するには、特定のライブラリをインストールする必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="570af-111">To use the latest language features in older environments, you may need to install specific libraries.</span></span> <span data-ttu-id="570af-112">これらの依存関係については、特定のバージョンごとに用意されたページに記載されています。</span><span class="sxs-lookup"><span data-stu-id="570af-112">These dependencies are documented in the page for each specific version.</span></span> <span data-ttu-id="570af-113">詳細については、この依存関係のバックグラウンドにある[言語とライブラリ間の関係](relationships-between-language-and-library.md)に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="570af-113">You can learn more about the [relationships between language and library](relationships-between-language-and-library.md) for background on this dependency.</span></span> 


* <span data-ttu-id="570af-114">[C# 7.2](csharp-7-2.md):</span><span class="sxs-lookup"><span data-stu-id="570af-114">[C# 7.2](csharp-7-2.md):</span></span>
    - <span data-ttu-id="570af-115">このページでは C# 言語の最新の機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="570af-115">This page describes the latest features in the C# language.</span></span> <span data-ttu-id="570af-116">C# 7.2 は現在 [Visual Studio 2017 バージョン 15.5](https://www.visualstudio.com/vs/whatsnew/) および [.NET Core 2.0 SDK](../../core/whats-new/index.md) で利用可能です。</span><span class="sxs-lookup"><span data-stu-id="570af-116">C# 7.2 is currently available in [Visual Studio 2017 version 15.5](https://www.visualstudio.com/vs/whatsnew/), and in the [.NET Core 2.0 SDK](../../core/whats-new/index.md).</span></span>

* <span data-ttu-id="570af-117">[C# 7.1](csharp-7-1.md):</span><span class="sxs-lookup"><span data-stu-id="570af-117">[C# 7.1](csharp-7-1.md):</span></span>
    - <span data-ttu-id="570af-118">このページでは、C# 7.1 の機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="570af-118">This page describes the features in C# 7.1.</span></span> <span data-ttu-id="570af-119">これらの機能は、[Visual Studio 2017 バージョン 15.3](https://www.visualstudio.com/vs/whatsnew/) および [.NET Core 2.0 SDK](../../core/whats-new/index.md) に追加されています。</span><span class="sxs-lookup"><span data-stu-id="570af-119">These features were added in [Visual Studio 2017 version 15.3](https://www.visualstudio.com/vs/whatsnew/), and in the [.NET Core 2.0 SDK](../../core/whats-new/index.md).</span></span>

* <span data-ttu-id="570af-120">[C# 7.0](csharp-7.md):</span><span class="sxs-lookup"><span data-stu-id="570af-120">[C# 7.0](csharp-7.md):</span></span>
    - <span data-ttu-id="570af-121">このページでは、C# 7.0 で追加された機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="570af-121">This page describes the features added in C# 7.0.</span></span> <span data-ttu-id="570af-122">これらの機能は [Visual Studio 2017](https://www.visualstudio.com/vs/whatsnew/) および [.NET Core 1.0](../../core/whats-new/index.md) 以降で追加されました。</span><span class="sxs-lookup"><span data-stu-id="570af-122">These features were added in [Visual Studio 2017](https://www.visualstudio.com/vs/whatsnew/) and [.NET Core 1.0](../../core/whats-new/index.md) and later</span></span>
     
* <span data-ttu-id="570af-123">[C# 6](csharp-6.md):</span><span class="sxs-lookup"><span data-stu-id="570af-123">[C# 6](csharp-6.md):</span></span>
    - <span data-ttu-id="570af-124">このページでは、C# 6 で追加された機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="570af-124">This page describes the features that were added in C# 6.</span></span> <span data-ttu-id="570af-125">これらの機能は、Windows 開発者は Visual Studio 2015 で利用でき、macOS および Linux で C# を使用する開発者は .NET Core 1.0 で利用できます。</span><span class="sxs-lookup"><span data-stu-id="570af-125">These features are available in Visual Studio 2015 for Windows developers, and on .NET Core 1.0 for developers exploring C# on macOS and Linux.</span></span>

<!--* [C# Interactive](../interactive/index.md): 
    - This page describes C# Interactive, an interactive Read Eval Print Loop (REPL) that you can use to explore the C# language. You can use it to write code interactively and see it execute immediately, without any compile or build step.
-->
* <span data-ttu-id="570af-126">[クロス プラットフォーム サポート](../../core/index.md):</span><span class="sxs-lookup"><span data-stu-id="570af-126">[Cross Platform Support](../../core/index.md):</span></span>
    - <span data-ttu-id="570af-127">C# は .NET Core のサポートにより、複数のプラットフォームで実行できます。</span><span class="sxs-lookup"><span data-stu-id="570af-127">C#, through .NET Core support, runs on multiple platforms.</span></span> <span data-ttu-id="570af-128">macOS や、Linux をサポートする多くのディストリビューションのいずれかで C# を使用する場合は、.NET Core の詳細を確認してください。</span><span class="sxs-lookup"><span data-stu-id="570af-128">If you are interested in trying C# on macOS, or on one of the many supported Linux distributions, learn more about .NET Core.</span></span>

<!--
- [.NET Compiler Platform SDK](../roslyn/index.md):
    - The .NET Compiler Platform SDK enables you to write code that performs static analysis on C# code. You can use these APIs to find potential errors, or bad practices, suggest fixes, and even implement those fixes.
-->
  
## <a name="previous-versions"></a><span data-ttu-id="570af-129">以前のバージョン</span><span class="sxs-lookup"><span data-stu-id="570af-129">Previous Versions</span></span>
<span data-ttu-id="570af-130">次の一覧は、C# 言語と Visual Studio .NET の以前のバージョンで導入された主な機能を示しています。</span><span class="sxs-lookup"><span data-stu-id="570af-130">The following lists key features that were introduced in previous versions of the C# language and Visual Studio .NET.</span></span>  
  
 * <span data-ttu-id="570af-131">Visual Studio .NET 2013:</span><span class="sxs-lookup"><span data-stu-id="570af-131">Visual Studio .NET 2013:</span></span> 
     - <span data-ttu-id="570af-132">このバージョンの Visual Studio には、バグの修正、パフォーマンスの向上、.NET コンパイラ プラットフォーム ("Roslyn") の Technology Preview (後の <!--Link to ../roslyn/index.md-->.NET コンパイラ プラットフォーム SDK) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="570af-132">This version of Visual Studio included bug fixes, performance improvements, and technology previews of .NET Compiler Platform ("Roslyn") which became the .NET Compiler Platform SDK<!--Link to ../roslyn/index.md-->.</span></span>

 * <span data-ttu-id="570af-133">C# 5、Visual Studio .NET 2012:</span><span class="sxs-lookup"><span data-stu-id="570af-133">C# 5, Visual Studio .NET 2012:</span></span> 
     - <span data-ttu-id="570af-134">`Async` / `await`、および[呼び出し元情報](../programming-guide/concepts/caller-information.md)属性。</span><span class="sxs-lookup"><span data-stu-id="570af-134">`Async` / `await`, and [caller information](../programming-guide/concepts/caller-information.md) attributes.</span></span>

 * <span data-ttu-id="570af-135">C# 4、Visual Studio .NET 2010:</span><span class="sxs-lookup"><span data-stu-id="570af-135">C# 4, Visual Studio .NET 2010:</span></span> 
     - <span data-ttu-id="570af-136">`Dynamic`、[名前付き引数](../programming-guide/classes-and-structs/named-and-optional-arguments.md)、省略可能なパラメーター、ジェネリックの[共変性および反変性](../programming-guide/concepts/covariance-contravariance/index.md)。</span><span class="sxs-lookup"><span data-stu-id="570af-136">`Dynamic`, [named arguments](../programming-guide/classes-and-structs/named-and-optional-arguments.md), optional parameters, and generic [covariance and contra variance](../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

 * <span data-ttu-id="570af-137">C# 3、Visual Studio .NET 2008:</span><span class="sxs-lookup"><span data-stu-id="570af-137">C# 3, Visual Studio .NET 2008:</span></span> 
     - <span data-ttu-id="570af-138">オブジェクト初期化子とコレクション初期化子、ラムダ式、拡張メソッド、匿名型、自動プロパティ、ローカル `var` 型推論、および[統合言語クエリ (LINQ)](../programming-guide/concepts/linq/index.md)。</span><span class="sxs-lookup"><span data-stu-id="570af-138">Object and collection initializers, lambda expressions, extension methods, anonymous types, automatic properties, local `var` type inference, and [Language Integrated Query (LINQ)](../programming-guide/concepts/linq/index.md).</span></span>

 * <span data-ttu-id="570af-139">C# 2、Visual Studio .NET 2005:</span><span class="sxs-lookup"><span data-stu-id="570af-139">C# 2, Visual Studio .NET 2005:</span></span> 
     - <span data-ttu-id="570af-140">匿名メソッド、ジェネリック、null 許容型、反復子/yield、`static` クラス、デリゲートの共変性および反変性。</span><span class="sxs-lookup"><span data-stu-id="570af-140">Anonymous methods, generics, nullable types, iterators/yield, `static` classes, and covariance and contra variance for delegates.</span></span>

 * <span data-ttu-id="570af-141">C# 1.1、Visual Studio .NET 2003:</span><span class="sxs-lookup"><span data-stu-id="570af-141">C# 1.1, Visual Studio .NET 2003:</span></span> 
     - <span data-ttu-id="570af-142">`#line` プラグマと xml ドキュメント コメント。</span><span class="sxs-lookup"><span data-stu-id="570af-142">`#line` pragma and xml doc comments.</span></span>

 * <span data-ttu-id="570af-143">C# 1、Visual Studio .NET 2002:</span><span class="sxs-lookup"><span data-stu-id="570af-143">C# 1, Visual Studio .NET 2002:</span></span> 
     - <span data-ttu-id="570af-144">[C#](../csharp.md) の最初のリリース。</span><span class="sxs-lookup"><span data-stu-id="570af-144">The first release of [C#](../csharp.md).</span></span>   
