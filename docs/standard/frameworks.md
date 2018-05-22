---
title: ターゲット フレームワーク
description: .NET Core アプリとライブラリのターゲット フレームワークについて説明します。
author: richlander
ms.author: mairaw
ms.date: 04/16/2018
ms.custom: updateeachrelease
ms.technology: dotnet-standard
ms.openlocfilehash: fa8049c9e33f0f6b2f16fd8572d6500ba1860c2e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="target-frameworks"></a><span data-ttu-id="c88c8-103">ターゲット フレームワーク</span><span class="sxs-lookup"><span data-stu-id="c88c8-103">Target frameworks</span></span>

<span data-ttu-id="c88c8-104">アプリまたはライブラリでフレームワークをターゲットに設定するときは、アプリまたはライブラリで使用できるようにする API のセットを指定します。</span><span class="sxs-lookup"><span data-stu-id="c88c8-104">When you target a framework in an app or library, you're specifying the set of APIs that you'd like to make available to the app or library.</span></span> <span data-ttu-id="c88c8-105">プロジェクト ファイルでターゲット フレームワークを指定するには、ターゲット フレームワーク モニカー (TFM) を使います。</span><span class="sxs-lookup"><span data-stu-id="c88c8-105">You specify the target framework in your project file using Target Framework Monikers (TFMs).</span></span>

<span data-ttu-id="c88c8-106">アプリまたはライブラリでは、[.NET Standard](~/docs/standard/net-standard.md) のバージョンをターゲットにできます。</span><span class="sxs-lookup"><span data-stu-id="c88c8-106">An app or library can target a version of [.NET Standard](~/docs/standard/net-standard.md).</span></span> <span data-ttu-id="c88c8-107">.NET Standard のバージョンは、.NET のすべての実装で標準化された API のセットを表します。</span><span class="sxs-lookup"><span data-stu-id="c88c8-107">.NET Standard versions represent standardized sets of APIs across all .NET implementations.</span></span> <span data-ttu-id="c88c8-108">たとえば、ライブラリは、.NET Standard 1.6 をターゲットにして、.NET Core と .NET Framework で機能する API に同じコードベースを使ってアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="c88c8-108">For example, a library can target .NET Standard 1.6 and gain access to APIs that function across .NET Core and .NET Framework using the same codebase.</span></span>

<span data-ttu-id="c88c8-109">また、アプリまたはライブラリは、.NET の特定の実装をターゲットにして、実装固有の API にアクセスすることもできます。</span><span class="sxs-lookup"><span data-stu-id="c88c8-109">An app or library can also target a specific .NET implementation to gain access to implementation-specific APIs.</span></span> <span data-ttu-id="c88c8-110">たとえば、Xamarin.iOS (たとえば `Xamarin.iOS10`) をターゲットにするアプリは Xamarin が提供する iOS 10 用の iOS API ラッパーにアクセスでき、ユニバーサル Windows プラットフォーム (UWP、`uap10.0`) をターゲットにするアプリは Windows 10 を実行するデバイス用にコンパイルできる API にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="c88c8-110">For example, an app that targets Xamarin.iOS (for example, `Xamarin.iOS10`) gets access to Xamarin-provided iOS API wrappers for iOS 10, or an app that targets the Universal Windows Platform (UWP, `uap10.0`) has access to APIs that compile for devices that run Windows 10.</span></span>

<span data-ttu-id="c88c8-111">一部のターゲット フレームワーク (.NET Framework など) では、API はフレームワークがシステムにインストールするアセンブリによって定義され、アプリケーション フレームワーク API (たとえば ASP.NET) を含む場合があります。</span><span class="sxs-lookup"><span data-stu-id="c88c8-111">For some target frameworks (for example, the .NET Framework), the APIs are defined by the assemblies that the framework installs on a system and may include application framework APIs (for example, ASP.NET).</span></span>

<span data-ttu-id="c88c8-112">パッケージ ベースのターゲット フレームワーク (.NET Standard、.NET Core など) では、API はアプリまたはライブラリに含まれるパッケージによって定義されます。</span><span class="sxs-lookup"><span data-stu-id="c88c8-112">For package-based target frameworks (for example, .NET Standard and .NET Core), the APIs are defined by the packages included in the app or library.</span></span> <span data-ttu-id="c88c8-113">"*メタパッケージ*" は、それ独自の内容はなく、依存するもの (他のパッケージ) のリストを保持している NuGet パッケージです。</span><span class="sxs-lookup"><span data-stu-id="c88c8-113">A *metapackage* is a NuGet package that has no content of its own but is a list of dependencies (other packages).</span></span> <span data-ttu-id="c88c8-114">NuGet パッケージ ベースのターゲット フレームワークでは、全体としてフレームワークを構成するすべてのパッケージを参照するメタパッケージが暗黙的に指定されます。</span><span class="sxs-lookup"><span data-stu-id="c88c8-114">A NuGet package-based target framework implicitly specifies a metapackage that references all the packages that together make up the framework.</span></span>

## <a name="latest-target-framework-versions"></a><span data-ttu-id="c88c8-115">最新のターゲット フレームワークのバージョン</span><span class="sxs-lookup"><span data-stu-id="c88c8-115">Latest target framework versions</span></span>

<span data-ttu-id="c88c8-116">次の表では、最も一般的なターゲット フレームワーク、それらの参照方法、およびそれらが実装する [.NET Standard](~/docs/standard/net-standard.md) のバージョンを定義します。</span><span class="sxs-lookup"><span data-stu-id="c88c8-116">The following table defines the most common target frameworks, how they're referenced, and which version of the [.NET Standard](~/docs/standard/net-standard.md) they implement.</span></span> <span data-ttu-id="c88c8-117">これらのターゲット フレームワークのバージョンは、最新の安定したバージョンです。</span><span class="sxs-lookup"><span data-stu-id="c88c8-117">These target framework versions are the latest stable versions.</span></span> <span data-ttu-id="c88c8-118">プレリリース バージョンは記載されていません。</span><span class="sxs-lookup"><span data-stu-id="c88c8-118">Pre-release versions aren't shown.</span></span> <span data-ttu-id="c88c8-119">ターゲット フレームワーク モニカー (TFM) は、.NET アプリまたはライブラリのターゲット フレームワークを指定するための標準化されたトークン形式です。</span><span class="sxs-lookup"><span data-stu-id="c88c8-119">A Target Framework Moniker (TFM) is a standardized token format for specifying the target framework of a .NET app or library.</span></span>

| <span data-ttu-id="c88c8-120">[対象とする Framework]</span><span class="sxs-lookup"><span data-stu-id="c88c8-120">Target Framework</span></span>      | <span data-ttu-id="c88c8-121">Latest</span><span class="sxs-lookup"><span data-stu-id="c88c8-121">Latest</span></span> <br/> <span data-ttu-id="c88c8-122">安定バージョン</span><span class="sxs-lookup"><span data-stu-id="c88c8-122">Stable Version</span></span> | <span data-ttu-id="c88c8-123">ターゲット フレームワーク モニカー (TFM)</span><span class="sxs-lookup"><span data-stu-id="c88c8-123">Target Framework Moniker (TFM)</span></span> | <span data-ttu-id="c88c8-124">実装済み</span><span class="sxs-lookup"><span data-stu-id="c88c8-124">Implemented</span></span> <br/> <span data-ttu-id="c88c8-125">.NET Standard バージョン</span><span class="sxs-lookup"><span data-stu-id="c88c8-125">.NET Standard Version</span></span> |
| :-------------------: | :-------------------------: | :----------------------------: | :-------------------------------------: |
| <span data-ttu-id="c88c8-126">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="c88c8-126">.NET Standard</span></span>         | <span data-ttu-id="c88c8-127">2.0</span><span class="sxs-lookup"><span data-stu-id="c88c8-127">2.0</span></span>                         | <span data-ttu-id="c88c8-128">netstandard2.0</span><span class="sxs-lookup"><span data-stu-id="c88c8-128">netstandard2.0</span></span>                 | <span data-ttu-id="c88c8-129">N/A</span><span class="sxs-lookup"><span data-stu-id="c88c8-129">N/A</span></span>                                     |
| <span data-ttu-id="c88c8-130">.NET Core アプリケーション</span><span class="sxs-lookup"><span data-stu-id="c88c8-130">.NET Core Application</span></span> | <span data-ttu-id="c88c8-131">2.0</span><span class="sxs-lookup"><span data-stu-id="c88c8-131">2.0</span></span>                         | <span data-ttu-id="c88c8-132">netcoreapp2.0</span><span class="sxs-lookup"><span data-stu-id="c88c8-132">netcoreapp2.0</span></span>                  | <span data-ttu-id="c88c8-133">2.0</span><span class="sxs-lookup"><span data-stu-id="c88c8-133">2.0</span></span>                                     |
| <span data-ttu-id="c88c8-134">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="c88c8-134">.NET Framework</span></span>        | <span data-ttu-id="c88c8-135">4.7.2</span><span class="sxs-lookup"><span data-stu-id="c88c8-135">4.7.2</span></span>                       | <span data-ttu-id="c88c8-136">net472</span><span class="sxs-lookup"><span data-stu-id="c88c8-136">net472</span></span>                         | <span data-ttu-id="c88c8-137">2.0</span><span class="sxs-lookup"><span data-stu-id="c88c8-137">2.0</span></span>                                     |

## <a name="supported-target-framework-versions"></a><span data-ttu-id="c88c8-138">サポートされるターゲット フレームワークのバージョン</span><span class="sxs-lookup"><span data-stu-id="c88c8-138">Supported target framework versions</span></span>

<span data-ttu-id="c88c8-139">ターゲット フレームワークは、通常、TFM によって参照されます。</span><span class="sxs-lookup"><span data-stu-id="c88c8-139">A target framework is typically referenced by a TFM.</span></span> <span data-ttu-id="c88c8-140">次の表では、.NET Core SDK および NuGet クライアントによってサポートされるターゲット フレームワークを示します。</span><span class="sxs-lookup"><span data-stu-id="c88c8-140">The following table shows the target frameworks supported by the .NET Core SDK and the NuGet client.</span></span> <span data-ttu-id="c88c8-141">同等のものがかっこ内に示されています。</span><span class="sxs-lookup"><span data-stu-id="c88c8-141">Equivalents are shown within brackets.</span></span> <span data-ttu-id="c88c8-142">たとえば、`win81` は `netcore451` と同等の TFM です。</span><span class="sxs-lookup"><span data-stu-id="c88c8-142">For example, `win81` is an equivalent TFM to `netcore451`.</span></span>

| <span data-ttu-id="c88c8-143">[対象とする Framework]</span><span class="sxs-lookup"><span data-stu-id="c88c8-143">Target Framework</span></span>           | <span data-ttu-id="c88c8-144">TFM</span><span class="sxs-lookup"><span data-stu-id="c88c8-144">TFM</span></span> |
| -------------------------- | --- |
| <span data-ttu-id="c88c8-145">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="c88c8-145">.NET Standard</span></span>              | <span data-ttu-id="c88c8-146">netstandard1.0</span><span class="sxs-lookup"><span data-stu-id="c88c8-146">netstandard1.0</span></span><br><span data-ttu-id="c88c8-147">netstandard1.1</span><span class="sxs-lookup"><span data-stu-id="c88c8-147">netstandard1.1</span></span><br><span data-ttu-id="c88c8-148">netstandard1.2</span><span class="sxs-lookup"><span data-stu-id="c88c8-148">netstandard1.2</span></span><br><span data-ttu-id="c88c8-149">netstandard1.3</span><span class="sxs-lookup"><span data-stu-id="c88c8-149">netstandard1.3</span></span><br><span data-ttu-id="c88c8-150">netstandard1.4</span><span class="sxs-lookup"><span data-stu-id="c88c8-150">netstandard1.4</span></span><br><span data-ttu-id="c88c8-151">netstandard1.5</span><span class="sxs-lookup"><span data-stu-id="c88c8-151">netstandard1.5</span></span><br><span data-ttu-id="c88c8-152">netstandard1.6</span><span class="sxs-lookup"><span data-stu-id="c88c8-152">netstandard1.6</span></span><br><span data-ttu-id="c88c8-153">netstandard2.0</span><span class="sxs-lookup"><span data-stu-id="c88c8-153">netstandard2.0</span></span> |
| <span data-ttu-id="c88c8-154">.NET Core</span><span class="sxs-lookup"><span data-stu-id="c88c8-154">.NET Core</span></span>                  | <span data-ttu-id="c88c8-155">netcoreapp1.0</span><span class="sxs-lookup"><span data-stu-id="c88c8-155">netcoreapp1.0</span></span><br><span data-ttu-id="c88c8-156">netcoreapp1.1</span><span class="sxs-lookup"><span data-stu-id="c88c8-156">netcoreapp1.1</span></span><br><span data-ttu-id="c88c8-157">netcoreapp2.0</span><span class="sxs-lookup"><span data-stu-id="c88c8-157">netcoreapp2.0</span></span><br><span data-ttu-id="c88c8-158">netcoreapp2.1</span><span class="sxs-lookup"><span data-stu-id="c88c8-158">netcoreapp2.1</span></span> |
| <span data-ttu-id="c88c8-159">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="c88c8-159">.NET Framework</span></span>             | <span data-ttu-id="c88c8-160">net11</span><span class="sxs-lookup"><span data-stu-id="c88c8-160">net11</span></span><br><span data-ttu-id="c88c8-161">net20</span><span class="sxs-lookup"><span data-stu-id="c88c8-161">net20</span></span><br><span data-ttu-id="c88c8-162">net35</span><span class="sxs-lookup"><span data-stu-id="c88c8-162">net35</span></span><br><span data-ttu-id="c88c8-163">net40</span><span class="sxs-lookup"><span data-stu-id="c88c8-163">net40</span></span><br><span data-ttu-id="c88c8-164">net403</span><span class="sxs-lookup"><span data-stu-id="c88c8-164">net403</span></span><br><span data-ttu-id="c88c8-165">net45</span><span class="sxs-lookup"><span data-stu-id="c88c8-165">net45</span></span><br><span data-ttu-id="c88c8-166">net451</span><span class="sxs-lookup"><span data-stu-id="c88c8-166">net451</span></span><br><span data-ttu-id="c88c8-167">net452</span><span class="sxs-lookup"><span data-stu-id="c88c8-167">net452</span></span><br><span data-ttu-id="c88c8-168">net46</span><span class="sxs-lookup"><span data-stu-id="c88c8-168">net46</span></span><br><span data-ttu-id="c88c8-169">net461</span><span class="sxs-lookup"><span data-stu-id="c88c8-169">net461</span></span><br><span data-ttu-id="c88c8-170">net462</span><span class="sxs-lookup"><span data-stu-id="c88c8-170">net462</span></span><br><span data-ttu-id="c88c8-171">net47</span><span class="sxs-lookup"><span data-stu-id="c88c8-171">net47</span></span><br><span data-ttu-id="c88c8-172">net471</span><span class="sxs-lookup"><span data-stu-id="c88c8-172">net471</span></span><br><span data-ttu-id="c88c8-173">net472</span><span class="sxs-lookup"><span data-stu-id="c88c8-173">net472</span></span> |
| <span data-ttu-id="c88c8-174">Windows ストア</span><span class="sxs-lookup"><span data-stu-id="c88c8-174">Windows Store</span></span>              | <span data-ttu-id="c88c8-175">netcore [netcore45]</span><span class="sxs-lookup"><span data-stu-id="c88c8-175">netcore [netcore45]</span></span><br><span data-ttu-id="c88c8-176">netcore45 [win] [win8]</span><span class="sxs-lookup"><span data-stu-id="c88c8-176">netcore45 [win] [win8]</span></span><br><span data-ttu-id="c88c8-177">netcore451 [win81]</span><span class="sxs-lookup"><span data-stu-id="c88c8-177">netcore451 [win81]</span></span> |
| <span data-ttu-id="c88c8-178">.NET Micro Framework</span><span class="sxs-lookup"><span data-stu-id="c88c8-178">.NET Micro Framework</span></span>       | <span data-ttu-id="c88c8-179">netmf</span><span class="sxs-lookup"><span data-stu-id="c88c8-179">netmf</span></span> |
| <span data-ttu-id="c88c8-180">Silverlight</span><span class="sxs-lookup"><span data-stu-id="c88c8-180">Silverlight</span></span>                | <span data-ttu-id="c88c8-181">sl4</span><span class="sxs-lookup"><span data-stu-id="c88c8-181">sl4</span></span><br><span data-ttu-id="c88c8-182">sl5</span><span class="sxs-lookup"><span data-stu-id="c88c8-182">sl5</span></span> |
| <span data-ttu-id="c88c8-183">Windows Phone</span><span class="sxs-lookup"><span data-stu-id="c88c8-183">Windows Phone</span></span>              | <span data-ttu-id="c88c8-184">wp [wp7]</span><span class="sxs-lookup"><span data-stu-id="c88c8-184">wp [wp7]</span></span><br><span data-ttu-id="c88c8-185">wp7</span><span class="sxs-lookup"><span data-stu-id="c88c8-185">wp7</span></span><br><span data-ttu-id="c88c8-186">wp75</span><span class="sxs-lookup"><span data-stu-id="c88c8-186">wp75</span></span><br><span data-ttu-id="c88c8-187">wp8</span><span class="sxs-lookup"><span data-stu-id="c88c8-187">wp8</span></span><br><span data-ttu-id="c88c8-188">wp81</span><span class="sxs-lookup"><span data-stu-id="c88c8-188">wp81</span></span><br><span data-ttu-id="c88c8-189">wpa81</span><span class="sxs-lookup"><span data-stu-id="c88c8-189">wpa81</span></span> |
| <span data-ttu-id="c88c8-190">ユニバーサル Windows プラットフォーム</span><span class="sxs-lookup"><span data-stu-id="c88c8-190">Universal Windows Platform</span></span> | <span data-ttu-id="c88c8-191">uap [uap10.0]</span><span class="sxs-lookup"><span data-stu-id="c88c8-191">uap [uap10.0]</span></span><br><span data-ttu-id="c88c8-192">uap10.0 [win10] [netcore50]</span><span class="sxs-lookup"><span data-stu-id="c88c8-192">uap10.0 [win10] [netcore50]</span></span> |

## <a name="how-to-specify-target-frameworks"></a><span data-ttu-id="c88c8-193">ターゲット フレームワークを指定する方法</span><span class="sxs-lookup"><span data-stu-id="c88c8-193">How to specify target frameworks</span></span>

<span data-ttu-id="c88c8-194">ターゲット フレームワークはプロジェクト ファイルで指定します。</span><span class="sxs-lookup"><span data-stu-id="c88c8-194">Target frameworks are specified in your project file.</span></span> <span data-ttu-id="c88c8-195">単一のターゲット フレームワークを指定するときは、**TargetFramework** 要素を使います。</span><span class="sxs-lookup"><span data-stu-id="c88c8-195">When a single target framework is specified, use the **TargetFramework** element.</span></span> <span data-ttu-id="c88c8-196">次のコンソール アプリのプロジェクト ファイルでは、.NET Core 2.0 をターゲットにする方法が示されています。</span><span class="sxs-lookup"><span data-stu-id="c88c8-196">The following console app project file demonstrates how to target .NET Core 2.0:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.0</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="c88c8-197">複数のターゲット フレームワークを指定するときは、各ターゲット フレームワークに対するアセンブリを条件付きで参照できます。</span><span class="sxs-lookup"><span data-stu-id="c88c8-197">When you specify multiple target frameworks, you may conditionally reference assemblies for each target framework.</span></span> <span data-ttu-id="c88c8-198">コードでは、プリプロセッサ シンボルと *if-then-else* ロジックを使うことで、これらのアセンブリに対して条件付きでコンパイルできます。</span><span class="sxs-lookup"><span data-stu-id="c88c8-198">In your code, you can conditionally compile against those assemblies by using preprocessor symbols with *if-then-else* logic.</span></span>

<span data-ttu-id="c88c8-199">次のライブラリ プロジェクト ファイルは、.NET Standard (`netstandard1.4`) の API と、.NET Framework (`net40` および `net45`) の API をターゲットにしています。</span><span class="sxs-lookup"><span data-stu-id="c88c8-199">The following library project file targets APIs of .NET Standard (`netstandard1.4`) and APIs of the .NET Framework (`net40` and `net45`).</span></span> <span data-ttu-id="c88c8-200">ターゲット フレームワークが複数あるときは、複数形の **TargetFrameworks** 要素を使います。</span><span class="sxs-lookup"><span data-stu-id="c88c8-200">Use the plural **TargetFrameworks** element with multiple target frameworks.</span></span> <span data-ttu-id="c88c8-201">ライブラリが 2 つの .NET Framework TFM に対してコンパイルされるときに `Condition` 属性で実装固有のパッケージを指定する方法に注意してください。</span><span class="sxs-lookup"><span data-stu-id="c88c8-201">Note how the `Condition` attributes include implementation-specific packages when the library is compiled for the two .NET Framework TFMs:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFrameworks>netstandard1.4;net40;net45</TargetFrameworks>
  </PropertyGroup>

  <!-- Conditionally obtain references for the .NET Framework 4.0 target -->
  <ItemGroup Condition=" '$(TargetFramework)' == 'net40' ">
    <Reference Include="System.Net" />
  </ItemGroup>

  <!-- Conditionally obtain references for the .NET Framework 4.5 target -->
  <ItemGroup Condition=" '$(TargetFramework)' == 'net45' ">
    <Reference Include="System.Net.Http" />
    <Reference Include="System.Threading.Tasks" />
  </ItemGroup>

</Project>
```

<span data-ttu-id="c88c8-202">ライブラリまたはアプリ内では、各ターゲット フレームワーク用にコンパイルするための条件付きコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="c88c8-202">Within your library or app, you write conditional code to compile for each target framework:</span></span>

```csharp
public class MyClass
{
    static void Main()
    {
#if NET40
        Console.WriteLine("Target framework: .NET Framework 4.0");
#elif NET45  
        Console.WriteLine("Target framework: .NET Framework 4.5");
#else
        Console.WriteLine("Target framework: .NET Standard 1.4");
#endif
    }
}
```

<span data-ttu-id="c88c8-203">ビルド システムは、「[サポートされるターゲット フレームワークのバージョン](#supported-target-framework-versions)」の表で示されているターゲット フレームワークを表すプリプロセッサ シンボルを認識します。</span><span class="sxs-lookup"><span data-stu-id="c88c8-203">The build system is aware of preprocessor symbols representing the target frameworks shown in the [Supported target framework versions](#supported-target-framework-versions) table.</span></span> <span data-ttu-id="c88c8-204">.NET Standard または .NET Core の TFM を表すシンボルを使うときは、ドットをアンダースコアに置き換え、小文字を大文字に変更します (たとえば、`netstandard1.4` のシンボルは `NETSTANDARD1_4` です)。</span><span class="sxs-lookup"><span data-stu-id="c88c8-204">When using a symbol that represents a .NET Standard or .NET Core TFM, replace the dot with an underscore and change lowercase letters to uppercase (for example, the symbol for `netstandard1.4` is `NETSTANDARD1_4`).</span></span>

<span data-ttu-id="c88c8-205">.NET Core ターゲット フレームワークのプリプロセッサ シンボルの完全な一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c88c8-205">The complete list of preprocessor symbols for .NET Core target frameworks is:</span></span>

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

## <a name="deprecated-target-frameworks"></a><span data-ttu-id="c88c8-206">非推奨のターゲット フレームワーク</span><span class="sxs-lookup"><span data-stu-id="c88c8-206">Deprecated target frameworks</span></span>

<span data-ttu-id="c88c8-207">次のターゲット フレームワークは非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="c88c8-207">The following target frameworks are deprecated.</span></span> <span data-ttu-id="c88c8-208">これらのターゲット フレームワークをターゲットにするパッケージは、指定されている代替フレームワークに移行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c88c8-208">Packages targeting these target frameworks should migrate to the indicated replacements.</span></span>

| <span data-ttu-id="c88c8-209">非推奨の TFM</span><span class="sxs-lookup"><span data-stu-id="c88c8-209">Deprecated TFM</span></span>                                                                             | <span data-ttu-id="c88c8-210">Replacement</span><span class="sxs-lookup"><span data-stu-id="c88c8-210">Replacement</span></span> |
| ------------------------------------------------------------------------------------------ | ----------- |
| <span data-ttu-id="c88c8-211">aspnet50</span><span class="sxs-lookup"><span data-stu-id="c88c8-211">aspnet50</span></span><br><span data-ttu-id="c88c8-212">aspnetcore50</span><span class="sxs-lookup"><span data-stu-id="c88c8-212">aspnetcore50</span></span><br><span data-ttu-id="c88c8-213">dnxcore50</span><span class="sxs-lookup"><span data-stu-id="c88c8-213">dnxcore50</span></span><br><span data-ttu-id="c88c8-214">dnx</span><span class="sxs-lookup"><span data-stu-id="c88c8-214">dnx</span></span><br><span data-ttu-id="c88c8-215">dnx45</span><span class="sxs-lookup"><span data-stu-id="c88c8-215">dnx45</span></span><br><span data-ttu-id="c88c8-216">dnx451</span><span class="sxs-lookup"><span data-stu-id="c88c8-216">dnx451</span></span><br><span data-ttu-id="c88c8-217">dnx452</span><span class="sxs-lookup"><span data-stu-id="c88c8-217">dnx452</span></span>                  | <span data-ttu-id="c88c8-218">netcoreapp</span><span class="sxs-lookup"><span data-stu-id="c88c8-218">netcoreapp</span></span>  |
| <span data-ttu-id="c88c8-219">dotnet</span><span class="sxs-lookup"><span data-stu-id="c88c8-219">dotnet</span></span><br><span data-ttu-id="c88c8-220">dotnet50</span><span class="sxs-lookup"><span data-stu-id="c88c8-220">dotnet50</span></span><br><span data-ttu-id="c88c8-221">dotnet51</span><span class="sxs-lookup"><span data-stu-id="c88c8-221">dotnet51</span></span><br><span data-ttu-id="c88c8-222">dotnet52</span><span class="sxs-lookup"><span data-stu-id="c88c8-222">dotnet52</span></span><br><span data-ttu-id="c88c8-223">dotnet53</span><span class="sxs-lookup"><span data-stu-id="c88c8-223">dotnet53</span></span><br><span data-ttu-id="c88c8-224">dotnet54</span><span class="sxs-lookup"><span data-stu-id="c88c8-224">dotnet54</span></span><br><span data-ttu-id="c88c8-225">dotnet55</span><span class="sxs-lookup"><span data-stu-id="c88c8-225">dotnet55</span></span><br><span data-ttu-id="c88c8-226">dotnet56</span><span class="sxs-lookup"><span data-stu-id="c88c8-226">dotnet56</span></span> | <span data-ttu-id="c88c8-227">netstandard</span><span class="sxs-lookup"><span data-stu-id="c88c8-227">netstandard</span></span> |
| <span data-ttu-id="c88c8-228">netcore50</span><span class="sxs-lookup"><span data-stu-id="c88c8-228">netcore50</span></span>                                                                                  | <span data-ttu-id="c88c8-229">uap10.0</span><span class="sxs-lookup"><span data-stu-id="c88c8-229">uap10.0</span></span>     |
| <span data-ttu-id="c88c8-230">win</span><span class="sxs-lookup"><span data-stu-id="c88c8-230">win</span></span>                                                                                        | <span data-ttu-id="c88c8-231">netcore45</span><span class="sxs-lookup"><span data-stu-id="c88c8-231">netcore45</span></span>   |
| <span data-ttu-id="c88c8-232">win8</span><span class="sxs-lookup"><span data-stu-id="c88c8-232">win8</span></span>                                                                                       | <span data-ttu-id="c88c8-233">netcore45</span><span class="sxs-lookup"><span data-stu-id="c88c8-233">netcore45</span></span>   |
| <span data-ttu-id="c88c8-234">win81</span><span class="sxs-lookup"><span data-stu-id="c88c8-234">win81</span></span>                                                                                      | <span data-ttu-id="c88c8-235">netcore451</span><span class="sxs-lookup"><span data-stu-id="c88c8-235">netcore451</span></span>  |
| <span data-ttu-id="c88c8-236">win10</span><span class="sxs-lookup"><span data-stu-id="c88c8-236">win10</span></span>                                                                                      | <span data-ttu-id="c88c8-237">uap10.0</span><span class="sxs-lookup"><span data-stu-id="c88c8-237">uap10.0</span></span>     |
| <span data-ttu-id="c88c8-238">winrt</span><span class="sxs-lookup"><span data-stu-id="c88c8-238">winrt</span></span>                                                                                      | <span data-ttu-id="c88c8-239">netcore45</span><span class="sxs-lookup"><span data-stu-id="c88c8-239">netcore45</span></span>   |

## <a name="see-also"></a><span data-ttu-id="c88c8-240">関連項目</span><span class="sxs-lookup"><span data-stu-id="c88c8-240">See also</span></span>

[<span data-ttu-id="c88c8-241">パッケージ、メタパッケージ、フレームワーク</span><span class="sxs-lookup"><span data-stu-id="c88c8-241">Packages, Metapackages and Frameworks</span></span>](../core/packages.md)  
[<span data-ttu-id="c88c8-242">クロス プラットフォーム ツールによるライブラリの開発</span><span class="sxs-lookup"><span data-stu-id="c88c8-242">Developing Libraries with Cross Platform Tools</span></span>](../core/tutorials/libraries.md)  
[<span data-ttu-id="c88c8-243">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="c88c8-243">.NET Standard</span></span>](net-standard.md)  
[<span data-ttu-id="c88c8-244">.NET Core バージョン管理</span><span class="sxs-lookup"><span data-stu-id="c88c8-244">.NET Core Versioning</span></span>](../core/versions/index.md)  
[<span data-ttu-id="c88c8-245">dotnet/standard GitHub リポジトリ</span><span class="sxs-lookup"><span data-stu-id="c88c8-245">dotnet/standard GitHub repository</span></span>](https://github.com/dotnet/standard)  
[<span data-ttu-id="c88c8-246">NuGet Tools GitHub リポジトリ</span><span class="sxs-lookup"><span data-stu-id="c88c8-246">NuGet Tools GitHub Repository</span></span>](https://github.com/joelverhagen/NuGetTools)  
[<span data-ttu-id="c88c8-247">.NET のフレームワーク プロファイル</span><span class="sxs-lookup"><span data-stu-id="c88c8-247">Framework Profiles in .NET</span></span>](https://blog.stephencleary.com/2012/05/framework-profiles-in-net.html)
