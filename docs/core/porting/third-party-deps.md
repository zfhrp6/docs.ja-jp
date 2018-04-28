---
title: .NET Core への移植 - サードパーティの依存関係を分析する
description: .NET Framework から .NET Core にプロジェクトを移植するために、サードパーティの依存関係を分析する方法を説明します。
author: cartermp
ms.author: mairaw
ms.date: 02/15/2018
ms.topic: conceptual
ms.prod: dotnet-core
ms.workload:
- dotnetcore
ms.openlocfilehash: be8d5a60977c7863136a1661a60e3bf23c0eb93e
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="analyze-your-third-party-dependencies"></a><span data-ttu-id="7ed32-103">サードパーティの依存関係を分析する</span><span class="sxs-lookup"><span data-stu-id="7ed32-103">Analyze your third-party dependencies</span></span>

<span data-ttu-id="7ed32-104">.NET Core または .NET Standard にコードを移植する場合、移植プロセスの最初のステップとして、サードパーティの依存関係を理解します。</span><span class="sxs-lookup"><span data-stu-id="7ed32-104">If you're looking to port your code to .NET Core or .NET Standard, the first step in the porting process is to understand your third-party dependencies.</span></span> <span data-ttu-id="7ed32-105">サードパーティの依存関係は、プロジェクトで参照する [NuGet パッケージ](#analyze-referenced-nuget-packages-on-your-project)または [DLL](#analyze-dependencies-that-arent-nuget-packages) です。</span><span class="sxs-lookup"><span data-stu-id="7ed32-105">Third-party dependencies are either [NuGet packages](#analyze-referenced-nuget-packages-on-your-project) or [DLLs](#analyze-dependencies-that-arent-nuget-packages) you're referencing in your project.</span></span> <span data-ttu-id="7ed32-106">それぞれの依存関係を評価し、.NET Core と互換性のない依存関係に対して代替計画を作成します。</span><span class="sxs-lookup"><span data-stu-id="7ed32-106">Evaluate each dependency and develop a contingency plan for the dependencies that aren't compatible with .NET Core.</span></span> <span data-ttu-id="7ed32-107">この記事では、依存関係が .NET Core と互換性があるかどうかを判別する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="7ed32-107">This article shows you how to determine if the dependency is compatible with .NET Core.</span></span>

## <a name="analyze-referenced-nuget-packages-in-your-project"></a><span data-ttu-id="7ed32-108">プロジェクトで参照される NuGet パッケージを分析する</span><span class="sxs-lookup"><span data-stu-id="7ed32-108">Analyze referenced NuGet packages in your project</span></span>

<span data-ttu-id="7ed32-109">プロジェクトで NuGet パッケージを参照する場合は、.NET Core と互換性があるかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ed32-109">If you're referencing NuGet packages in your project, you need to verify if they're compatible with .NET Core.</span></span>
<span data-ttu-id="7ed32-110">これを行う場合、次の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="7ed32-110">There are two ways to accomplish that:</span></span>

* <span data-ttu-id="7ed32-111">[NuGet パッケージ エクスプローラー アプリの使用](#analyze-nuget-packages-using-nuget-package-explorer) (最も信頼性の高い方法)。</span><span class="sxs-lookup"><span data-stu-id="7ed32-111">[Using the NuGet Package Explorer app](#analyze-nuget-packages-using-nuget-package-explorer) (the most reliable method).</span></span>
* <span data-ttu-id="7ed32-112">[nuget.org サイトの使用](#analyze-nuget-packages-using-nugetorg)。</span><span class="sxs-lookup"><span data-stu-id="7ed32-112">[Using the nuget.org site](#analyze-nuget-packages-using-nugetorg).</span></span>

<span data-ttu-id="7ed32-113">パッケージの分析後、NET Core と互換性がなく、.NET Framework のみをターゲットとする場合は、[.NET Framework 互換モード](#net-framework-compatibility-mode)が移植プロセスに役立つかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="7ed32-113">After analyzing the packages, if they're not compatible with .NET Core and only target .NET Framework, you can check if the [.NET Framework compatibility mode](#net-framework-compatibility-mode) can help with your porting process.</span></span>

### <a name="analyze-nuget-packages-using-nuget-package-explorer"></a><span data-ttu-id="7ed32-114">NuGet パッケージ エクスプローラーを使用して NuGet パッケージを分析する</span><span class="sxs-lookup"><span data-stu-id="7ed32-114">Analyze NuGet packages using NuGet Package Explorer</span></span>

<span data-ttu-id="7ed32-115">NuGet パッケージ自体はフォルダーのセットであり、プラットフォーム固有のアセンブリが含まれます。</span><span class="sxs-lookup"><span data-stu-id="7ed32-115">A NuGet package is itself a set of folders that contain platform-specific assemblies.</span></span> <span data-ttu-id="7ed32-116">したがって、パッケージ内に互換性のあるアセンブリを含むフォルダーがあるかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ed32-116">So you need to check if there's a folder that contains a compatible assembly inside the package.</span></span>

<span data-ttu-id="7ed32-117">NuGet パッケージ フォルダーを調べる最も簡単な方法は、[NuGet パッケージ エクスプローラー](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) ツールを使用することです。</span><span class="sxs-lookup"><span data-stu-id="7ed32-117">The easiest way to inspect NuGet Package folders is to use the [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) tool.</span></span> <span data-ttu-id="7ed32-118">これをインストールした後、次の手順を使用してフォルダー名を確認します。</span><span class="sxs-lookup"><span data-stu-id="7ed32-118">After installing it, use the following steps to see the folder names:</span></span>

1. <span data-ttu-id="7ed32-119">NuGet パッケージ エクスプローラーを開きます。</span><span class="sxs-lookup"><span data-stu-id="7ed32-119">Open the NuGet Package Explorer.</span></span>
2. <span data-ttu-id="7ed32-120">**[Open package from online feed]\(オンライン フィードからパッケージを開く\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7ed32-120">Click **Open package from online feed**.</span></span>
3. <span data-ttu-id="7ed32-121">パッケージの名前を検索します。</span><span class="sxs-lookup"><span data-stu-id="7ed32-121">Search for the name of the package.</span></span>
4. <span data-ttu-id="7ed32-122">検索結果からパッケージ名を選択し、**[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7ed32-122">Select the package name from the search results and click **open**.</span></span>
5. <span data-ttu-id="7ed32-123">右側にある *lib* フォルダーを展開し、フォルダー名を確認します。</span><span class="sxs-lookup"><span data-stu-id="7ed32-123">Expand the *lib* folder on the right-hand side and look at folder names.</span></span>

<span data-ttu-id="7ed32-124">次のいずれかの名前のフォルダーを探します。</span><span class="sxs-lookup"><span data-stu-id="7ed32-124">Look for a folder with any of the following names:</span></span>

```
netstandard1.0
netstandard1.1
netstandard1.2
netstandard1.3
netstandard1.4
netstandard1.5
netstandard1.6
netstandard2.0
netcoreapp1.0
netcoreapp1.1
netcoreapp2.0
portable-net45-win8
portable-win8-wpa8
portable-net451-win81
portable-net45-win8-wpa8-wpa81
```

<span data-ttu-id="7ed32-125">これらの値は[ターゲット フレームワーク モニカー (TFM)](../../standard/frameworks.md) であり、[.NET Standard](../../standard/net-standard.md)、.NET Core、および .NET Core と互換性がある従来のポータブル クラス ライブラリ (PCL) プロファイルのバージョンにマップされます。</span><span class="sxs-lookup"><span data-stu-id="7ed32-125">These values are the [Target Framework Monikers (TFMs)](../../standard/frameworks.md) that map to versions of the [.NET Standard](../../standard/net-standard.md), .NET Core, and traditional Portable Class Library (PCL) profiles that are compatible with .NET Core.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7ed32-126">パッケージでサポートされる TFM を見ると、`netcoreapp*` に互換性はあるものの、.NET Core プロジェクトのみを対象としており、.NET Standard プロジェクトを対象としていないことがわかります。</span><span class="sxs-lookup"><span data-stu-id="7ed32-126">When looking at the TFMs that a package supports, note that `netcoreapp*`, while compatible, is for .NET Core projects only and not for .NET Standard projects.</span></span>
> <span data-ttu-id="7ed32-127">他の .NET Core アプリで使用できるのは、`netstandard*` ではなく、`netcoreapp*` のみをターゲットとするライブラリだけです。</span><span class="sxs-lookup"><span data-stu-id="7ed32-127">A library that only targets `netcoreapp*` and not `netstandard*` can only be consumed by other .NET Core apps.</span></span>

<span data-ttu-id="7ed32-128">また、プレリリース版の .NET Core で使用されるレガシ TFM にも、互換性のあるものがあります。</span><span class="sxs-lookup"><span data-stu-id="7ed32-128">There are also some legacy TFMs used in pre-release versions of .NET Core that may also be compatible:</span></span>

```
dnxcore50
dotnet5.0
dotnet5.1
dotnet5.2
dotnet5.3
dotnet5.4
dotnet5.5
```

<span data-ttu-id="7ed32-129">これらの TFM がコードで動作する可能性はありますが、互換性は保証されていません。</span><span class="sxs-lookup"><span data-stu-id="7ed32-129">While these TFMs likely work with your code, there is no guarantee of compatibility.</span></span> <span data-ttu-id="7ed32-130">このような TFM を含むパッケージは、プレリリース版の .NET Core パッケージで構築されています。</span><span class="sxs-lookup"><span data-stu-id="7ed32-130">Packages with these TFMs were built with pre-release .NET Core packages.</span></span> <span data-ttu-id="7ed32-131">これらの TFM を使用するパッケージが .NET Standard ベースに更新されるか、また、更新される場合はいつ行われるかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="7ed32-131">Take note of when (or if) packages using these TFMs are updated to be .NET Standard-based.</span></span>

> [!NOTE]
> <span data-ttu-id="7ed32-132">従来の PCL またはプレリリースの .NET Core ターゲットを対象とするパッケージを使用するには、プロジェクト ファイルで `PackageTargetFallback` MSBuild 要素を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ed32-132">To use a package targeting a traditional PCL or pre-release .NET Core target, you must use the `PackageTargetFallback` MSBuild element in your project file.</span></span>
> <span data-ttu-id="7ed32-133">MSBuild 要素の詳細については、「[`PackageTargetFallback`](../tools/csproj.md#packagetargetfallback)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ed32-133">For more information about this MSBuild element, see [`PackageTargetFallback`](../tools/csproj.md#packagetargetfallback).</span></span>

### <a name="analyze-nuget-packages-using-nugetorg"></a><span data-ttu-id="7ed32-134">nuget.org を使用して NuGet パッケージを分析する</span><span class="sxs-lookup"><span data-stu-id="7ed32-134">Analyze NuGet packages using nuget.org</span></span>

<span data-ttu-id="7ed32-135">[nuget.org](https://www.nuget.org/) のパッケージ ページの **[Dependencies]\(依存関係\)** セクションで、各パッケージでサポートされる TFM を確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="7ed32-135">Alternatively, you can see the TFMs that each package supports on [nuget.org](https://www.nuget.org/) under the **Dependencies** section of the package page.</span></span>

<span data-ttu-id="7ed32-136">サイトを使用するのが互換性を確認するより簡単な方法ですが、**依存関係**情報はすべてのパッケージのサイトで利用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="7ed32-136">Although using the site is an easier method to verify the compatibility, **Dependencies** information is not available on the site for all packages.</span></span>

### <a name="net-framework-compatibility-mode"></a><span data-ttu-id="7ed32-137">.NET Framework 互換モード</span><span class="sxs-lookup"><span data-stu-id="7ed32-137">.NET Framework compatibility mode</span></span>

<span data-ttu-id="7ed32-138">NuGet パッケージの分析後、ほとんどの NuGet パッケージと同様に、.NET Framework のみがターゲットであることがわかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="7ed32-138">After analyzing the NuGet packages, you might find that they only target the .NET Framework, as most NuGet packages do.</span></span>

<span data-ttu-id="7ed32-139">.NET Standard 2.0 以降、.NET Framework 互換モードが導入されました。</span><span class="sxs-lookup"><span data-stu-id="7ed32-139">Starting with .NET Standard 2.0, the .NET Framework compatibility mode was introduced.</span></span> <span data-ttu-id="7ed32-140">この互換モードにより、.NET Standard および .NET Core プロジェクトは .NET Framework ライブラリを参照できます。</span><span class="sxs-lookup"><span data-stu-id="7ed32-140">This compatibility mode allows .NET Standard and .NET Core projects to reference .NET Framework libraries.</span></span> <span data-ttu-id="7ed32-141">.NET Framework ライブラリの参照はすべてのプロジェクトで機能するわけではありません (例えばライブラリで Windows Presentation Foundation (WPF) API を使用していても、多くの移植シナリオがブロック解除される場合など)。</span><span class="sxs-lookup"><span data-stu-id="7ed32-141">Referencing .NET Framework libraries doesn't work for all projects, such as if the library uses Windows Presentation Foundation (WPF) APIs, but it does unblock many porting scenarios.</span></span>

<span data-ttu-id="7ed32-142">[Huitian.PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections) など、プロジェクトで .NET Framework をターゲットとする NuGet パッケージを参照すると、次の例のようなパッケージ フォールバック警告 ([NU1701](/nuget/reference/errors-and-warnings#nu1701)) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7ed32-142">When you reference NuGet packages that target the .NET Framework in your project, such as [Huitian.PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections), you get a package fallback warning ([NU1701](/nuget/reference/errors-and-warnings#nu1701)) similar to the following example:</span></span>

`NU1701: Package ‘Huitian.PowerCollections 1.0.0’ was restored using ‘.NETFramework,Version=v4.6.1’ instead of the project target framework ‘.NETStandard,Version=v2.0’. This package may not be fully compatible with your project.`

<span data-ttu-id="7ed32-143">この警告は、パッケージを追加したとき、およびプロジェクトでそのパッケージを確実にテストするためにビルドするたびに表示されます。</span><span class="sxs-lookup"><span data-stu-id="7ed32-143">That warning is displayed when you add the package and every time you build to make sure you test that package with your project.</span></span> <span data-ttu-id="7ed32-144">プロジェクトが予期したとおりに動作している場合は、Visual Studio でパッケージ プロパティを編集するか、任意のコード エディターでプロジェクト ファイルを手動で編集して、この警告を非表示にすることができます。</span><span class="sxs-lookup"><span data-stu-id="7ed32-144">If your project is working as expected, you can suppress that warning by editing the package properties in Visual Studio or by manually editing the project file in your favorite code editor.</span></span>

<span data-ttu-id="7ed32-145">プロジェクト ファイルを編集して警告を非表示にするには、警告を非表示にするパッケージの `PackageReference` エントリを見つけて、`NoWarn` 属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="7ed32-145">To suppress the warning by editing the project file, find the `PackageReference` entry for the package you want to suppress the warning for and add the `NoWarn` attribute.</span></span> <span data-ttu-id="7ed32-146">`NoWarn` 属性では、すべての警告 ID のコンマ区切りリストを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="7ed32-146">The `NoWarn` attribute accepts a comma-separated list of all the warning IDs.</span></span> <span data-ttu-id="7ed32-147">次の例は、プロジェクト ファイルを手動で編集して、`Huitian.PowerCollections` パッケージの `NU1701` 警告を非表示にする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="7ed32-147">The following example shows how to suppress the `NU1701` warning for the `Huitian.PowerCollections` package by editing your project file manually:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Huitian.PowerCollections" Version="1.0.0" NoWarn="NU1701" />
</ItemGroup>
```

<span data-ttu-id="7ed32-148">Visual Studio でコンパイラ警告を非表示にする方法の詳細については、「[NuGet パッケージの警告を非表示にする](/visualstudio/ide/how-to-suppress-compiler-warnings#suppressing-warnings-for-nuget-packages)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ed32-148">For more information on how to suppress compiler warnings in Visual Studio, see [Suppressing warnings for NuGet packages](/visualstudio/ide/how-to-suppress-compiler-warnings#suppressing-warnings-for-nuget-packages).</span></span>

### <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a><span data-ttu-id="7ed32-149">NuGet パッケージの依存関係が .NET Core で動作しない場合の対処方法</span><span class="sxs-lookup"><span data-stu-id="7ed32-149">What to do when your NuGet package dependency doesn't run on .NET Core</span></span>

<span data-ttu-id="7ed32-150">依存している NuGet パッケージが .NET Core で動作しない場合の対処方法はいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="7ed32-150">There are a few things you can do if a NuGet package you depend on doesn't run on .NET Core:</span></span>

1. <span data-ttu-id="7ed32-151">プロジェクトがオープン ソースで、GitHub のような場所にホストされている場合、直接開発者に連絡することができます。</span><span class="sxs-lookup"><span data-stu-id="7ed32-151">If the project is open source and hosted somewhere like GitHub, you can engage the developers directly.</span></span>
2. <span data-ttu-id="7ed32-152">[nuget.org](https://www.nuget.org/) で直接作成者に連絡することができます。パッケージを検索し、パッケージのページの左側にある **[Contact Owners]\(所有者に問い合わせる\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7ed32-152">You can contact the author directly on [nuget.org](https://www.nuget.org/). Search for the package and click **Contact Owners** on the left-hand side of the package's page.</span></span>
3. <span data-ttu-id="7ed32-153">使用していたパッケージと同じタスクを実行する、.NET Core で実行される別のパッケージを検索することができます。</span><span class="sxs-lookup"><span data-stu-id="7ed32-153">You can search for another package that runs on .NET Core that accomplishes the same task as the package you were using.</span></span>
4. <span data-ttu-id="7ed32-154">パッケージが行っていたコードを自分で記述できます。</span><span class="sxs-lookup"><span data-stu-id="7ed32-154">You can attempt to write the code the package was doing yourself.</span></span>
5. <span data-ttu-id="7ed32-155">少なくともパッケージの互換バージョンが利用可能になるまでは、アプリの機能を変更することで、パッケージの依存関係を削除することができます。</span><span class="sxs-lookup"><span data-stu-id="7ed32-155">You could eliminate the dependency on the package by changing the functionality of your app, at least until a compatible version of the package becomes available.</span></span>

<span data-ttu-id="7ed32-156">オープン ソース プロジェクトの保守管理者および NuGet パッケージの発行者の多くは、ボランティアであることを忘れないでください。</span><span class="sxs-lookup"><span data-stu-id="7ed32-156">Remember that open-source project maintainers and NuGet package publishers are often volunteers.</span></span> <span data-ttu-id="7ed32-157">彼らは、その分野に関心があるために無償で作業を行っており、多くの場合、日中に別の仕事を抱えています。</span><span class="sxs-lookup"><span data-stu-id="7ed32-157">They contribute because they care about a given domain, do it for free, and often have a different daytime job.</span></span> <span data-ttu-id="7ed32-158">したがって、.NET Core のサポートを求めるために連絡する際には、この点を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="7ed32-158">So be mindful of that when contacting them to ask for .NET Core support.</span></span>

<span data-ttu-id="7ed32-159">上記のいずれでも問題を解決できない場合、後日 .NET Core に移植しなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="7ed32-159">If you can't resolve your issue with any of the above, you may have to port to .NET Core at a later date.</span></span>

<span data-ttu-id="7ed32-160">.NET チームは .NET Core のサポートでどのライブラリが最も重要かを知りたいと考えています。</span><span class="sxs-lookup"><span data-stu-id="7ed32-160">The .NET Team would like to know which libraries are the most important to support with .NET Core.</span></span> <span data-ttu-id="7ed32-161">使用したいライブラリについて、dotnet@microsoft.com にメールを送ることができます。</span><span class="sxs-lookup"><span data-stu-id="7ed32-161">You can send an email to dotnet@microsoft.com about the libraries you'd like to use.</span></span>

## <a name="analyze-dependencies-that-arent-nuget-packages"></a><span data-ttu-id="7ed32-162">NuGet パッケージではない依存関係を分析する</span><span class="sxs-lookup"><span data-stu-id="7ed32-162">Analyze dependencies that aren't NuGet packages</span></span>

<span data-ttu-id="7ed32-163">ファイル システム内の DLL など、NuGet パッケージではない依存関係がある場合もあります。</span><span class="sxs-lookup"><span data-stu-id="7ed32-163">You may have a dependency that isn't a NuGet package, such as a DLL in the file system.</span></span> <span data-ttu-id="7ed32-164">その依存関係の移植性を調べる唯一の方法が、[.NET Portability Analyzer](https://github.com/Microsoft/dotnet-apiport) ツールを実行することです。</span><span class="sxs-lookup"><span data-stu-id="7ed32-164">The only way to determine the portability of that dependency is to run the [.NET Portability Analyzer](https://github.com/Microsoft/dotnet-apiport) tool.</span></span> <span data-ttu-id="7ed32-165">このツールでは、.NET Framework をターゲットとするアセンブリを分析し、.NET Core などの他の .NET プラットフォームに移植できない API を特定できます。</span><span class="sxs-lookup"><span data-stu-id="7ed32-165">The tool can analyze assemblies that target the .NET Framework and identify APIs that aren't portable to other .NET platforms such as .NET Core.</span></span> <span data-ttu-id="7ed32-166">このツールはコンソール アプリケーションまたは [Visual Studio 拡張機能](../../standard/analyzers/portability-analyzer.md)として実行できます。</span><span class="sxs-lookup"><span data-stu-id="7ed32-166">You can run the tool as a console application or as a [Visual Studio extension](../../standard/analyzers/portability-analyzer.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="7ed32-167">次の手順</span><span class="sxs-lookup"><span data-stu-id="7ed32-167">Next steps</span></span>

<span data-ttu-id="7ed32-168">ライブラリを移植している場合は、「[Porting your Libraries](libraries.md)」(ライブラリへの移植) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ed32-168">If you're porting a library, check out [Porting your Libraries](libraries.md).</span></span>
