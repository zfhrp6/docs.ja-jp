---
title: 概要 - C# ガイド
description: 短期間で C# の概念について学習でき、.NET Core アプリケーションを作成することができるようになるような、短くて簡単なチュートリアルを探します。
keywords: C#, 概要, 取得,インストール
helpviewer_keywords:
- Visual C#, getting started
- getting started, Visual C#
author: rpetrusha
ms.author: ronpet
ms.date: 08/23/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.openlocfilehash: 630815032925e5dac0477147c6265657face44a5
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="get-started-with-c"></a><span data-ttu-id="973be-104">C# の使用を開始する</span><span class="sxs-lookup"><span data-stu-id="973be-104">Get started with C#</span></span> #

<span data-ttu-id="973be-105">このセクションでは、C# と .NET Core を使用して短時間でアプリケーションを構築できる、短いシンプルなチュートリアルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="973be-105">This section provides short, simple tutorials that let you quickly build an application using C# and .NET Core.</span></span> <span data-ttu-id="973be-106">Visual Studio 2017 と Visual Studio Code については、その概要を説明しているトピックがあります。</span><span class="sxs-lookup"><span data-stu-id="973be-106">There are getting started topics for Visual Studio 2017 and Visual Studio Code.</span></span> <span data-ttu-id="973be-107">単純な Hello World アプリケーションをビルドするか、Visual Studio 2017 を持っている場合は、他のアプリケーションで使用できる単純なクラス ライブラリをビルドできます。</span><span class="sxs-lookup"><span data-stu-id="973be-107">You can build either a simple Hello World application or, if you have Visual Studio 2017, a simple class library that can be used by other applications.</span></span>

<span data-ttu-id="973be-108">次のトピックを参照できます。</span><span class="sxs-lookup"><span data-stu-id="973be-108">The following topics are available:</span></span>

* [<span data-ttu-id="973be-109">C# 言語と .NET Framework の概要</span><span class="sxs-lookup"><span data-stu-id="973be-109">Introduction to the C# Language and the .NET Framework</span></span>](introduction-to-the-csharp-language-and-the-net-framework.md)

     <span data-ttu-id="973be-110">C# 言語および .NET の概要を示します。</span><span class="sxs-lookup"><span data-stu-id="973be-110">Provides an overview of the C# language and .NET.</span></span>

* [<span data-ttu-id="973be-111">Visual Studio 2017 での .NET Core を使用した C# Hello World アプリケーションの構築</span><span class="sxs-lookup"><span data-stu-id="973be-111">Building a C# Hello World application with .NET Core in Visual Studio 2017</span></span>](../../core/tutorials/with-visual-studio.md)

   <span data-ttu-id="973be-112">Visual Studio の最新リリースである Visual Studio 2017 では、Windows 統合開発環境で、アプリケーションのコーディング、コンパイル、実行、デバッグ、プロファイル、および発行を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="973be-112">Visual Studio 2017, the latest release of Visual Studio, lets you code, compile, run, debug, profile, and publish your applications from a integrated development environment for Windows.</span></span>

   <span data-ttu-id="973be-113">このトピックでは、単純な Hello World アプリケーションを作成して実行した後、やや対話的な Hello World アプリケーションとして実行するための修正を行います。</span><span class="sxs-lookup"><span data-stu-id="973be-113">The topic lets you create and run a simple Hello World application and then modify it to run a slightly more interactive Hello World application.</span></span> <span data-ttu-id="973be-114">アプリケーションのビルドと実行が完了したら、[デバッグ](../../core/tutorials/debugging-with-visual-studio.md)方法と[発行](../../core/tutorials/publishing-with-visual-studio.md)方法も学習することで、.NET Core でサポートされている任意のプラットフォームでアプリケーションを実行できるようにします。</span><span class="sxs-lookup"><span data-stu-id="973be-114">Once you've finished building and running your application, you can also learn how to [debug it](../../core/tutorials/debugging-with-visual-studio.md) and how to [publish it](../../core/tutorials/publishing-with-visual-studio.md) so that it can be run on any platform supported by .NET Core.</span></span>

* [<span data-ttu-id="973be-115">Visual Studio 2017 での C# と .NET Core を使用したクラス ライブラリの構築</span><span class="sxs-lookup"><span data-stu-id="973be-115">Building a class library with C# and .NET Core in Visual Studio 2017</span></span>](../../core/tutorials/library-with-visual-studio.md)

   <span data-ttu-id="973be-116">クラス ライブラリを使用して、別のアプリケーションから呼び出すことができる型と型のメンバーを定義できます。</span><span class="sxs-lookup"><span data-stu-id="973be-116">A class library lets you define types and type members that can be called from another application.</span></span> <span data-ttu-id="973be-117">このトピックでは、文字列が大文字で始まるかどうかを決定する単一のメソッドがあるクラス ライブラリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="973be-117">This topic lets you create a class library with a single method that determines whether a string begins with an uppercase character.</span></span> <span data-ttu-id="973be-118">ライブラリの構築が完了したら、[単体テスト](../../core/tutorials/testing-library-with-visual-studio.md)を開発して、それが期待どおりに動作することを確認した後、[そのライブラリを使用したいアプリケーション](../../core/tutorials/consuming-library-with-visual-studio.md)で使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="973be-118">Once you've finished building the library, you can develop a [unit test](../../core/tutorials/testing-library-with-visual-studio.md) to ensure that it works as expected, and then you can make it available to [applications that want to consume it](../../core/tutorials/consuming-library-with-visual-studio.md).</span></span>

* [<span data-ttu-id="973be-119">C# および Visual Studio Code の使用を開始する</span><span class="sxs-lookup"><span data-stu-id="973be-119">Get started with C# and Visual Studio Code</span></span>](../../core/tutorials/with-visual-studio-code.md)

   <span data-ttu-id="973be-120">Visual Studio Code は、最新の Web アプリケーションやクラウド アプリケーションのビルドとデバッグ向けに最適化された無料コード エディターです。</span><span class="sxs-lookup"><span data-stu-id="973be-120">Visual Studio Code is a free code editor optimized for building and debugging modern web and cloud applications.</span></span> <span data-ttu-id="973be-121">IntelliSense をサポートしており、Linux、macOS、Windows で使用できます。</span><span class="sxs-lookup"><span data-stu-id="973be-121">It supports IntelliSense and is available for Linux, macOS, and Windows.</span></span>

   <span data-ttu-id="973be-122">このトピックでは、Visual Studio Code と .NET Core を使用して、単純な Hello World アプリケーションを作成して実行する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="973be-122">This topic shows you how to create and run a simple Hello World application with Visual Studio Code and .NET Core.</span></span>

## <a name="related-sections"></a><span data-ttu-id="973be-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="973be-123">Related Sections</span></span>

* [<span data-ttu-id="973be-124">Visual C# 開発環境の使用</span><span class="sxs-lookup"><span data-stu-id="973be-124">Using the Visual Studio Development Environment for C#</span></span>](/visualstudio/csharp-ide/using-the-visual-studio-development-environment-for-csharp)  

    <span data-ttu-id="973be-125">Visual C# 統合開発環境を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="973be-125">Provides a guide to using the Visual C# integrated development environment.</span></span>

* [<span data-ttu-id="973be-126">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="973be-126">C# Programming Guide</span></span>](../../csharp/programming-guide/index.md)

    <span data-ttu-id="973be-127">C# プログラミングの概念に関する情報を提供し、C# でさまざまなタスクを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="973be-127">Provides information about C# programming concepts, and describes how to perform various tasks in C#.</span></span>

* [<span data-ttu-id="973be-128">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="973be-128">C# Reference</span></span>](../../csharp/language-reference/index.md)

    <span data-ttu-id="973be-129">C# のキーワード、演算子、プリプロセッサ ディレクティブ、コンパイラ オプション、およびコンパイラのエラーと警告に関する詳細なリファレンス情報を紹介します。</span><span class="sxs-lookup"><span data-stu-id="973be-129">Provides detailed reference information about C# keywords, operators, preprocessor directives, compiler options, and compiler errors and warnings.</span></span>

* [<span data-ttu-id="973be-130">Visual Studio のサンプル</span><span class="sxs-lookup"><span data-stu-id="973be-130">Visual Studio Samples</span></span>](/visualstudio/ide/visual-studio-samples)

    <span data-ttu-id="973be-131">オンライン サンプルへのアクセス方法に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="973be-131">Provides information about how you can access online samples.</span></span>

* [<span data-ttu-id="973be-132">チュートリアル</span><span class="sxs-lookup"><span data-stu-id="973be-132">Walkthroughs</span></span>](../../csharp/walkthroughs.md)

    <span data-ttu-id="973be-133">C# を使用するプログラミングのチュートリアルと、各チュートリアルに関する簡単な説明へのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="973be-133">Provides links to programming walkthroughs that use C# and a brief description of each walkthrough.</span></span>

## <a name="see-also"></a><span data-ttu-id="973be-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="973be-134">See also</span></span>
 [<span data-ttu-id="973be-135">Visual Studio を使用した Visual C# と Visual Basic の概要</span><span class="sxs-lookup"><span data-stu-id="973be-135">Getting Started with Visual C# and Visual Basic using Visual Studio</span></span>](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)
