---
title: .NET アーキテクチャ コンポーネント
description: .NET Standard、.NET 実装、.NET ランタイム、ツールなど、.NET アーキテクチャ コンポーネントについて説明します。
author: cartermp
ms.author: mairaw
ms.date: 08/23/2017
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 51e6779d63cdaccc5633c9e81f97471d71099653
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="net-architectural-components"></a><span data-ttu-id="b0c8b-103">.NET アーキテクチャ コンポーネント</span><span class="sxs-lookup"><span data-stu-id="b0c8b-103">.NET architectural components</span></span>

<span data-ttu-id="b0c8b-104">.NET アプリは、1 つまたは複数の *.NET 実装*向けに開発され、実行されます。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-104">A .NET app is developed for and runs in one or more *implementations of .NET*.</span></span>  <span data-ttu-id="b0c8b-105">.NET 実装には、.NET Framework、.NET Core、および Mono が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-105">Implementations of .NET include the .NET Framework, .NET Core, and Mono.</span></span> <span data-ttu-id="b0c8b-106">すべての .NET 実装に共通する API 仕様があり、それを.NET Standard と呼びます。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-106">There is an API specification common to all implementations of .NET that's called the .NET Standard.</span></span> <span data-ttu-id="b0c8b-107">この記事では、それぞれの概念について簡単に説明します。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-107">This article gives a brief introduction to each of these concepts.</span></span>

## <a name="net-standard"></a><span data-ttu-id="b0c8b-108">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="b0c8b-108">.NET Standard</span></span>

<span data-ttu-id="b0c8b-109">.NET Standard は、.NET 実装の基本クラス ライブラリで実装されている API のセットです。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-109">The .NET Standard is a set of APIs that are implemented by the Base Class Library of a .NET implementation.</span></span> <span data-ttu-id="b0c8b-110">さらに厳密に言うと、コードのコンパイル対象である統一されたコントラクトのセットを構成する .NET API の仕様です。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-110">More formally, it's a specification of .NET APIs that make up a uniform set of contracts that you compile your code against.</span></span> <span data-ttu-id="b0c8b-111">これらのコントラクトが各 .NET 実装に実装されています。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-111">These contracts are implemented in each .NET implementation.</span></span> <span data-ttu-id="b0c8b-112">これにより異なる .NET 実装間で移植することができるため、実質的にコードをどこでも実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-112">This enables portability across different .NET implementations, effectively allowing your code to run everywhere.</span></span>

<span data-ttu-id="b0c8b-113">.NET Standard は、[ターゲット フレームワーク](glossary.md#target-framework)でもあります。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-113">The .NET Standard is also a [target framework](glossary.md#target-framework).</span></span> <span data-ttu-id="b0c8b-114">コードが .NET Standard のバージョンをターゲットにする場合、.NET Standard のそのバージョンをサポートするすべての .NET 実装でそのコードを実行できます。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-114">If your code targets a version of the .NET Standard, it can run on any .NET implementation which supports that version of the .NET Standard.</span></span>

<span data-ttu-id="b0c8b-115">.NET Standard とそのターゲットの設定方法については、「[.NET Standard](net-standard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-115">To learn more about the .NET Standard and how to target it, see the [.NET Standard](net-standard.md) topic.</span></span>

## <a name="net-implementations"></a><span data-ttu-id="b0c8b-116">.NET 実装</span><span class="sxs-lookup"><span data-stu-id="b0c8b-116">.NET implementations</span></span>

<span data-ttu-id="b0c8b-117">各 .NET 実装には、次のコンポーネントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-117">Each implementation of .NET includes the following components:</span></span>

- <span data-ttu-id="b0c8b-118">1 つまたは複数のランタイム。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-118">One or more runtimes.</span></span> <span data-ttu-id="b0c8b-119">たとえば、CLR for .NET Framework、CoreCLR、CoreRT for .NET Core などです。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-119">Examples: CLR for .NET Framework, CoreCLR and CoreRT for .NET Core.</span></span>
- <span data-ttu-id="b0c8b-120">.NET Standard を実装し、他の API も実装する可能性があるクラス ライブラリ。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-120">A class library that implements the .NET Standard and may implement additional APIs.</span></span> <span data-ttu-id="b0c8b-121">たとえば、.NET Framework 基本クラス ライブラリや .NET Core 基本クラス ライブラリなどです。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-121">Examples: .NET Framework Base Class Library, .NET Core Base Class Library.</span></span>
- <span data-ttu-id="b0c8b-122">必要に応じて、1 つまたは複数のアプリケーション フレームワーク。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-122">Optionally, one or more application frameworks.</span></span> <span data-ttu-id="b0c8b-123">たとえば、.NET Framework には、[ASP.NET](https://www.asp.net/)、[Windows フォーム](../framework/winforms/windows-forms-overview.md)、[Windows Presentation Foundation (WPF)](../framework/wpf/index.md) などです。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-123">Examples: [ASP.NET](https://www.asp.net/), [Windows Forms](../framework/winforms/windows-forms-overview.md), and [Windows Presentation Foundation (WPF)](../framework/wpf/index.md) are included in the .NET Framework.</span></span>
- <span data-ttu-id="b0c8b-124">必要に応じて、開発ツール。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-124">Optionally, development tools.</span></span> <span data-ttu-id="b0c8b-125">一部の開発ツールは、複数の実装間で共有されます。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-125">Some development tools are shared among multiple implementations.</span></span>

<span data-ttu-id="b0c8b-126">Microsoft が積極的に開発し保守している主要な .NET 実装としては、.NET Core、.NET Framework、Mono、UWP の 4 つがあります。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-126">There are four primary .NET implementations that Microsoft actively develops and maintains: .NET Core, .NET Framework, Mono, and UWP.</span></span>

### <a name="net-core"></a><span data-ttu-id="b0c8b-127">.NET Core</span><span class="sxs-lookup"><span data-stu-id="b0c8b-127">.NET Core</span></span>

<span data-ttu-id="b0c8b-128">.NET Core は .NET のクラスプラットフォーム実装であり、サーバーとクラウドのワークロードをその規模に応じて処理するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-128">.NET Core is a cross-platform implementation of .NET and designed to handle server and cloud workloads at scale.</span></span> <span data-ttu-id="b0c8b-129">Windows、macOS および Linux で実行されます。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-129">It runs on Windows, macOS and Linux.</span></span> <span data-ttu-id="b0c8b-130">.NET Standard を実装しているので、.NET Standard をターゲットとするすべてのコードを .NET Core 上で実行できます。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-130">It implements the .NET Standard, so code that targets the .NET Standard can run on .NET Core.</span></span> <span data-ttu-id="b0c8b-131">ASP.NET Core は、.NET Core 上で実行されます。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-131">ASP.NET Core runs on .NET Core.</span></span> 

<span data-ttu-id="b0c8b-132">.NET Core の詳細については、「[.NET Core](../core/index.md)」および「[サーバー アプリ用 .NET Core と .NET Framework の選択](choosing-core-framework-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-132">To learn more about .NET Core, see the [.NET Core Guide](../core/index.md) and [Choosing between .NET Core and .NET Framework for server apps](choosing-core-framework-server.md).</span></span>

### <a name="net-framework"></a><span data-ttu-id="b0c8b-133">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="b0c8b-133">.NET Framework</span></span>

<span data-ttu-id="b0c8b-134">.Net Framework は、2002 年からリリースされている元の .NET 実装です。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-134">The.NET Framework is the original .NET implementation that has existed since 2002.</span></span> <span data-ttu-id="b0c8b-135">既存の .NET 開発者が常に使用してきたものと同じ .NET Framework です。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-135">It's the same .NET Framework that existing .NET developers have always used.</span></span> <span data-ttu-id="b0c8b-136">バージョン 4.5 以降では .NET Standard を実装しているので、.NET Standard をターゲットとするすべてのコードが .NET Framework 4.5 以降で実行できます。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-136">Versions 4.5 and later implement the .NET Standard, so code that targets the .NET Standard can run on those versions of the .NET Framework.</span></span> <span data-ttu-id="b0c8b-137">Windows フォームと WPF での Windows デスクトップ開発用 API など、追加の Windows 固有 API が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-137">It contains additional Windows-specific APIs, such as APIs for Windows desktop development with Windows Forms and WPF.</span></span> <span data-ttu-id="b0c8b-138">.NET Framework は、Windows デスクトップ アプリケーション開発用に最適化されています。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-138">The .NET Framework is optimized for building Windows desktop applications.</span></span>

<span data-ttu-id="b0c8b-139">.NET Framework について詳しくは、「[.NET Framework](../framework/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-139">To learn more about the .NET Framework, see the [.NET Framework Guide](../framework/index.md).</span></span>

### <a name="mono"></a><span data-ttu-id="b0c8b-140">Mono</span><span class="sxs-lookup"><span data-stu-id="b0c8b-140">Mono</span></span>

<span data-ttu-id="b0c8b-141">Mono は、主に小規模なランタイムが必要な場合に使用される .NET 実装です。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-141">Mono is a .NET implementation that is mainly used when a small runtime is required.</span></span> <span data-ttu-id="b0c8b-142">Android、Mac、iOS、tvOS、および watchOS 上の Xamarin アプリケーションで利用されるランタイムで、フットプリントが小さいことに重点を置いています。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-142">It is the runtime that powers Xamarin applications on Android, Mac, iOS, tvOS and watchOS and is focused primarily on a small footprint.</span></span> <span data-ttu-id="b0c8b-143">Mono は、Unity エンジンを使用して構築されたゲームでも利用されます。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-143">Mono also powers games built using the Unity engine.</span></span>

<span data-ttu-id="b0c8b-144">現在公開されているすべての .NET Standard バージョンをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-144">It supports all of the currently published .NET Standard versions.</span></span>

<span data-ttu-id="b0c8b-145">これまで Mono は .NET Framework の多数の API を実装し、Unix で人気の高い機能の一部をエミュレートしていました。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-145">Historically, Mono implemented the larger API of the .NET Framework and emulated some of the most popular capabilities on Unix.</span></span> <span data-ttu-id="b0c8b-146">また、Unix のそのような機能に依存する .NET アプリケーションを実行するために使用されることもあります。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-146">It is sometimes used to run .NET applications that rely on those capabilities on Unix.</span></span>

<span data-ttu-id="b0c8b-147">一般的に Mono は、Just-In-Time コンパイラと共に使用されますが、iOS のようなプラットフォームに使用される完全な静的コンパイラ (Ahead Of Time コンパイル) としても機能します。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-147">Mono is typically used with a just-in-time compiler, but it also features a full static compiler (ahead-of-time compilation) that is used on platforms like iOS.</span></span>

<span data-ttu-id="b0c8b-148">Mono について詳しくは、[Mono のドキュメント](https://www.mono-project.com/docs/)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-148">To learn more about Mono, see the [Mono documentation](https://www.mono-project.com/docs/).</span></span>

### <a name="universal-windows-platform-uwp"></a><span data-ttu-id="b0c8b-149">ユニバーサル Windows プラットフォーム (UWP)</span><span class="sxs-lookup"><span data-stu-id="b0c8b-149">Universal Windows Platform (UWP)</span></span>

<span data-ttu-id="b0c8b-150">UWP は、モノのインターネット (IoT) 用に最新のタッチ対応の Windows アプリケーションとソフトウェアを構築するために使われる .NET 実装です。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-150">UWP is an implementation of .NET that is used for building modern, touch-enabled Windows applications and software for the Internet of Things (IoT).</span></span> <span data-ttu-id="b0c8b-151">PC、タブレット、ファブレット、携帯電話、Xbox など、ターゲットにする可能性があるさまざまな種類のデバイスを統一するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-151">It's designed to unify the different types of devices that you may want to target, including PCs, tablets, phablets, phones, and even the Xbox.</span></span> <span data-ttu-id="b0c8b-152">UWP は、一元的なアプリ ストア、実行環境 (AppContainer)、Win32 の代わりに使う Windows API のセット (WinRT) など、多くのサービスを提供します。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-152">UWP provides many services, such as a centralized app store, an execution environment (AppContainer), and a set of Windows APIs to use instead of Win32 (WinRT).</span></span> <span data-ttu-id="b0c8b-153">アプリは、C++、C#、VB.NET、および JavaScript で記述することができます。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-153">Apps can be written in C++, C#, VB.NET, and JavaScript.</span></span> <span data-ttu-id="b0c8b-154">C# と VB.NET を使うときは、.NET Core によって .NET API が提供されます。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-154">When using C# and VB.NET, the .NET APIs are provided by .NET Core.</span></span>

<span data-ttu-id="b0c8b-155">UWP の詳細については、「[ユニバーサル Windows プラットフォームの紹介](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-155">To learn more about UWP, see [Intro to the Universal Windows Platform](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide).</span></span>

## <a name="net-runtimes"></a><span data-ttu-id="b0c8b-156">.NET ランタイム</span><span class="sxs-lookup"><span data-stu-id="b0c8b-156">.NET runtimes</span></span>

<span data-ttu-id="b0c8b-157">ランタイムは、マネージ プログラムの実行環境です。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-157">A runtime is the execution environment for a managed program.</span></span> <span data-ttu-id="b0c8b-158">OS は、ランタイム環境の一部ですが、.NET ランタイムの一部ではありません。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-158">The OS is part of the runtime environment but is not part of the .NET runtime.</span></span> <span data-ttu-id="b0c8b-159">.NET ランタイムの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-159">Here are some examples of .NET runtimes:</span></span>
 
 - <span data-ttu-id="b0c8b-160">.NET Framework 用共通言語ランタイム (CLR)</span><span class="sxs-lookup"><span data-stu-id="b0c8b-160">Common Language Runtime (CLR) for the .NET Framework</span></span>
 - <span data-ttu-id="b0c8b-161">.NET Core 用共通言語ランタイム (CoreCLR)</span><span class="sxs-lookup"><span data-stu-id="b0c8b-161">Core Common Language Runtime (CoreCLR) for .NET Core</span></span>
 - <span data-ttu-id="b0c8b-162">ユニバーサル Windows プラットフォーム用 .NET Native</span><span class="sxs-lookup"><span data-stu-id="b0c8b-162">.NET Native for Universal Windows Platform</span></span> 
 - <span data-ttu-id="b0c8b-163">Xamarin.iOS、Xamarin.Android、Xamarin.Mac、Mono デスクトップ フレームワーク用ランタイム</span><span class="sxs-lookup"><span data-stu-id="b0c8b-163">The Mono runtime for Xamarin.iOS, Xamarin.Android, Xamarin.Mac, and the Mono desktop framework</span></span>

## <a name="net-tooling-and-common-infrastructure"></a><span data-ttu-id="b0c8b-164">.NET のツールと共通インフラストラクチャ</span><span class="sxs-lookup"><span data-stu-id="b0c8b-164">.NET tooling and common infrastructure</span></span>

<span data-ttu-id="b0c8b-165">すべての .NET 実装と連携する多様なツールやインフラストラクチャ コンポーネントにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-165">You have access to an extensive set of tools and infrastructure components that work with every implementation of .NET.</span></span> <span data-ttu-id="b0c8b-166">その一部を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b0c8b-166">These include, but are not limited to the following:</span></span>

- <span data-ttu-id="b0c8b-167">.NET 言語とコンパイラ</span><span class="sxs-lookup"><span data-stu-id="b0c8b-167">The .NET languages and their compilers</span></span>
- <span data-ttu-id="b0c8b-168">.NET プロジェクト システム (*.csproj*、*.vbproj*、および *.fsproj* ファイルに基づく)</span><span class="sxs-lookup"><span data-stu-id="b0c8b-168">The .NET project system (based on *.csproj*, *.vbproj*, and *.fsproj* files)</span></span>
- <span data-ttu-id="b0c8b-169">[MSBuild](/visualstudio/msbuild/msbuild) (プロジェクトのビルドに使用されるビルド エンジン)</span><span class="sxs-lookup"><span data-stu-id="b0c8b-169">[MSBuild](/visualstudio/msbuild/msbuild), the build engine used to build projects</span></span>
- <span data-ttu-id="b0c8b-170">[NuGet](/nuget/) (Microsoft の .NET 用パッケージ マネージャー)</span><span class="sxs-lookup"><span data-stu-id="b0c8b-170">[NuGet](/nuget/), Microsoft's package manager for .NET</span></span>
- <span data-ttu-id="b0c8b-171">オープン ソースのビルド オーケストレーション ツール ([CAKE](https://cakebuild.net/)、[FAKE](https://fake.build/) など)</span><span class="sxs-lookup"><span data-stu-id="b0c8b-171">Open-source build orchestration tools, such as [CAKE](https://cakebuild.net/) and [FAKE](https://fake.build/)</span></span>

## <a name="see-also"></a><span data-ttu-id="b0c8b-172">関連項目</span><span class="sxs-lookup"><span data-stu-id="b0c8b-172">See also</span></span>
<span data-ttu-id="b0c8b-173">[サーバー アプリ用 .NET Core と .NET Framework の選択](choosing-core-framework-server.md) </span><span class="sxs-lookup"><span data-stu-id="b0c8b-173">[Choosing between .NET Core and .NET Framework for server apps](choosing-core-framework-server.md) </span></span>  
[<span data-ttu-id="b0c8b-174">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="b0c8b-174">.NET Standard</span></span>](net-standard.md)  
[<span data-ttu-id="b0c8b-175">.NET Core のガイド</span><span class="sxs-lookup"><span data-stu-id="b0c8b-175">.NET Core Guide</span></span>](../core/index.md)  
[<span data-ttu-id="b0c8b-176">.NET Framework ガイド</span><span class="sxs-lookup"><span data-stu-id="b0c8b-176">.NET Framework Guide</span></span>](../framework/index.md)  
[<span data-ttu-id="b0c8b-177">C# のガイド</span><span class="sxs-lookup"><span data-stu-id="b0c8b-177">C# Guide</span></span>](../csharp/index.md)  
[<span data-ttu-id="b0c8b-178">F# のガイド</span><span class="sxs-lookup"><span data-stu-id="b0c8b-178">F# Guide</span></span>](../fsharp/index.md)  
[<span data-ttu-id="b0c8b-179">VB.NET ガイド</span><span class="sxs-lookup"><span data-stu-id="b0c8b-179">VB.NET Guide</span></span>](../visual-basic/index.md)  

