---
title: ターゲット フレームワーク
description: .NET Core アプリとライブラリのターゲット フレームワークについて説明します。
author: richlander
ms.author: mairaw
ms.date: 05/31/2018
ms.custom: updateeachrelease
ms.technology: dotnet-standard
ms.openlocfilehash: 346eece8fdb391fd62b369db6ef65964fcd6e67a
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34728317"
---
# <a name="target-frameworks"></a><span data-ttu-id="48907-103">ターゲット フレームワーク</span><span class="sxs-lookup"><span data-stu-id="48907-103">Target frameworks</span></span>

<span data-ttu-id="48907-104">アプリまたはライブラリでフレームワークをターゲットに設定するときは、アプリまたはライブラリで使用できるようにする API のセットを指定します。</span><span class="sxs-lookup"><span data-stu-id="48907-104">When you target a framework in an app or library, you're specifying the set of APIs that you'd like to make available to the app or library.</span></span> <span data-ttu-id="48907-105">プロジェクト ファイルでターゲット フレームワークを指定するには、ターゲット フレームワーク モニカー (TFM) を使います。</span><span class="sxs-lookup"><span data-stu-id="48907-105">You specify the target framework in your project file using Target Framework Monikers (TFMs).</span></span>

<span data-ttu-id="48907-106">アプリまたはライブラリでは、[.NET Standard](~/docs/standard/net-standard.md) のバージョンをターゲットにできます。</span><span class="sxs-lookup"><span data-stu-id="48907-106">An app or library can target a version of [.NET Standard](~/docs/standard/net-standard.md).</span></span> <span data-ttu-id="48907-107">.NET Standard のバージョンは、.NET のすべての実装で標準化された API のセットを表します。</span><span class="sxs-lookup"><span data-stu-id="48907-107">.NET Standard versions represent standardized sets of APIs across all .NET implementations.</span></span> <span data-ttu-id="48907-108">たとえば、ライブラリは、.NET Standard 1.6 をターゲットにして、.NET Core と .NET Framework で機能する API に同じコードベースを使ってアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="48907-108">For example, a library can target .NET Standard 1.6 and gain access to APIs that function across .NET Core and .NET Framework using the same codebase.</span></span>

<span data-ttu-id="48907-109">また、アプリまたはライブラリは、.NET の特定の実装をターゲットにして、実装固有の API にアクセスすることもできます。</span><span class="sxs-lookup"><span data-stu-id="48907-109">An app or library can also target a specific .NET implementation to gain access to implementation-specific APIs.</span></span> <span data-ttu-id="48907-110">たとえば、Xamarin.iOS (たとえば `Xamarin.iOS10`) をターゲットにするアプリは Xamarin が提供する iOS 10 用の iOS API ラッパーにアクセスでき、ユニバーサル Windows プラットフォーム (UWP、`uap10.0`) をターゲットにするアプリは Windows 10 を実行するデバイス用にコンパイルできる API にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="48907-110">For example, an app that targets Xamarin.iOS (for example, `Xamarin.iOS10`) gets access to Xamarin-provided iOS API wrappers for iOS 10, or an app that targets the Universal Windows Platform (UWP, `uap10.0`) has access to APIs that compile for devices that run Windows 10.</span></span>

<span data-ttu-id="48907-111">一部のターゲット フレームワーク (.NET Framework など) では、API はフレームワークがシステムにインストールするアセンブリによって定義され、アプリケーション フレームワーク API (たとえば ASP.NET) を含む場合があります。</span><span class="sxs-lookup"><span data-stu-id="48907-111">For some target frameworks (for example, the .NET Framework), the APIs are defined by the assemblies that the framework installs on a system and may include application framework APIs (for example, ASP.NET).</span></span>

<span data-ttu-id="48907-112">パッケージ ベースのターゲット フレームワーク (.NET Standard、.NET Core など) では、API はアプリまたはライブラリに含まれるパッケージによって定義されます。</span><span class="sxs-lookup"><span data-stu-id="48907-112">For package-based target frameworks (for example, .NET Standard and .NET Core), the APIs are defined by the packages included in the app or library.</span></span> <span data-ttu-id="48907-113">"*メタパッケージ*" は、それ独自の内容はなく、依存するもの (他のパッケージ) のリストを保持している NuGet パッケージです。</span><span class="sxs-lookup"><span data-stu-id="48907-113">A *metapackage* is a NuGet package that has no content of its own but is a list of dependencies (other packages).</span></span> <span data-ttu-id="48907-114">NuGet パッケージ ベースのターゲット フレームワークでは、全体としてフレームワークを構成するすべてのパッケージを参照するメタパッケージが暗黙的に指定されます。</span><span class="sxs-lookup"><span data-stu-id="48907-114">A NuGet package-based target framework implicitly specifies a metapackage that references all the packages that together make up the framework.</span></span>

## <a name="latest-target-framework-versions"></a><span data-ttu-id="48907-115">最新のターゲット フレームワークのバージョン</span><span class="sxs-lookup"><span data-stu-id="48907-115">Latest target framework versions</span></span>

<span data-ttu-id="48907-116">次の表では、最も一般的なターゲット フレームワーク、それらの参照方法、およびそれらが実装する [.NET Standard](~/docs/standard/net-standard.md) のバージョンを定義します。</span><span class="sxs-lookup"><span data-stu-id="48907-116">The following table defines the most common target frameworks, how they're referenced, and which version of the [.NET Standard](~/docs/standard/net-standard.md) they implement.</span></span> <span data-ttu-id="48907-117">これらのターゲット フレームワークのバージョンは、最新の安定したバージョンです。</span><span class="sxs-lookup"><span data-stu-id="48907-117">These target framework versions are the latest stable versions.</span></span> <span data-ttu-id="48907-118">プレリリース バージョンは記載されていません。</span><span class="sxs-lookup"><span data-stu-id="48907-118">Pre-release versions aren't shown.</span></span> <span data-ttu-id="48907-119">ターゲット フレームワーク モニカー (TFM) は、.NET アプリまたはライブラリのターゲット フレームワークを指定するための標準化されたトークン形式です。</span><span class="sxs-lookup"><span data-stu-id="48907-119">A Target Framework Moniker (TFM) is a standardized token format for specifying the target framework of a .NET app or library.</span></span>

| <span data-ttu-id="48907-120">[対象とする Framework]</span><span class="sxs-lookup"><span data-stu-id="48907-120">Target Framework</span></span>      | <span data-ttu-id="48907-121">Latest</span><span class="sxs-lookup"><span data-stu-id="48907-121">Latest</span></span> <br/> <span data-ttu-id="48907-122">安定バージョン</span><span class="sxs-lookup"><span data-stu-id="48907-122">Stable Version</span></span> | <span data-ttu-id="48907-123">ターゲット フレームワーク モニカー (TFM)</span><span class="sxs-lookup"><span data-stu-id="48907-123">Target Framework Moniker (TFM)</span></span> | <span data-ttu-id="48907-124">実装済み</span><span class="sxs-lookup"><span data-stu-id="48907-124">Implemented</span></span> <br/> <span data-ttu-id="48907-125">.NET Standard バージョン</span><span class="sxs-lookup"><span data-stu-id="48907-125">.NET Standard Version</span></span> |
| :-------------------: | :-------------------------: | :----------------------------: | :-------------------------------------: |
| <span data-ttu-id="48907-126">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="48907-126">.NET Standard</span></span>         | <span data-ttu-id="48907-127">2.0</span><span class="sxs-lookup"><span data-stu-id="48907-127">2.0</span></span>                         | <span data-ttu-id="48907-128">netstandard2.0</span><span class="sxs-lookup"><span data-stu-id="48907-128">netstandard2.0</span></span>                 | <span data-ttu-id="48907-129">N/A</span><span class="sxs-lookup"><span data-stu-id="48907-129">N/A</span></span>                                     |
| <span data-ttu-id="48907-130">.NET Core</span><span class="sxs-lookup"><span data-stu-id="48907-130">.NET Core</span></span>             | <span data-ttu-id="48907-131">2.1</span><span class="sxs-lookup"><span data-stu-id="48907-131">2.1</span></span>                         | <span data-ttu-id="48907-132">netcoreapp2.1</span><span class="sxs-lookup"><span data-stu-id="48907-132">netcoreapp2.1</span></span>                  | <span data-ttu-id="48907-133">2.0</span><span class="sxs-lookup"><span data-stu-id="48907-133">2.0</span></span>                                     |
| <span data-ttu-id="48907-134">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="48907-134">.NET Framework</span></span>        | <span data-ttu-id="48907-135">4.7.2</span><span class="sxs-lookup"><span data-stu-id="48907-135">4.7.2</span></span>                       | <span data-ttu-id="48907-136">net472</span><span class="sxs-lookup"><span data-stu-id="48907-136">net472</span></span>                         | <span data-ttu-id="48907-137">2.0</span><span class="sxs-lookup"><span data-stu-id="48907-137">2.0</span></span>                                     |

## <a name="supported-target-framework-versions"></a><span data-ttu-id="48907-138">サポートされるターゲット フレームワークのバージョン</span><span class="sxs-lookup"><span data-stu-id="48907-138">Supported target framework versions</span></span>

<span data-ttu-id="48907-139">ターゲット フレームワークは、通常、TFM によって参照されます。</span><span class="sxs-lookup"><span data-stu-id="48907-139">A target framework is typically referenced by a TFM.</span></span> <span data-ttu-id="48907-140">次の表では、.NET Core SDK および NuGet クライアントによってサポートされるターゲット フレームワークを示します。</span><span class="sxs-lookup"><span data-stu-id="48907-140">The following table shows the target frameworks supported by the .NET Core SDK and the NuGet client.</span></span> <span data-ttu-id="48907-141">同等のものがかっこ内に示されています。</span><span class="sxs-lookup"><span data-stu-id="48907-141">Equivalents are shown within brackets.</span></span> <span data-ttu-id="48907-142">たとえば、`win81` は `netcore451` と同等の TFM です。</span><span class="sxs-lookup"><span data-stu-id="48907-142">For example, `win81` is an equivalent TFM to `netcore451`.</span></span>

| <span data-ttu-id="48907-143">[対象とする Framework]</span><span class="sxs-lookup"><span data-stu-id="48907-143">Target Framework</span></span>           | <span data-ttu-id="48907-144">TFM</span><span class="sxs-lookup"><span data-stu-id="48907-144">TFM</span></span> |
| -------------------------- | --- |
| <span data-ttu-id="48907-145">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="48907-145">.NET Standard</span></span>              | <span data-ttu-id="48907-146">netstandard1.0</span><span class="sxs-lookup"><span data-stu-id="48907-146">netstandard1.0</span></span><br><span data-ttu-id="48907-147">netstandard1.1</span><span class="sxs-lookup"><span data-stu-id="48907-147">netstandard1.1</span></span><br><span data-ttu-id="48907-148">netstandard1.2</span><span class="sxs-lookup"><span data-stu-id="48907-148">netstandard1.2</span></span><br><span data-ttu-id="48907-149">netstandard1.3</span><span class="sxs-lookup"><span data-stu-id="48907-149">netstandard1.3</span></span><br><span data-ttu-id="48907-150">netstandard1.4</span><span class="sxs-lookup"><span data-stu-id="48907-150">netstandard1.4</span></span><br><span data-ttu-id="48907-151">netstandard1.5</span><span class="sxs-lookup"><span data-stu-id="48907-151">netstandard1.5</span></span><br><span data-ttu-id="48907-152">netstandard1.6</span><span class="sxs-lookup"><span data-stu-id="48907-152">netstandard1.6</span></span><br><span data-ttu-id="48907-153">netstandard2.0</span><span class="sxs-lookup"><span data-stu-id="48907-153">netstandard2.0</span></span> |
| <span data-ttu-id="48907-154">.NET Core</span><span class="sxs-lookup"><span data-stu-id="48907-154">.NET Core</span></span>                  | <span data-ttu-id="48907-155">netcoreapp1.0</span><span class="sxs-lookup"><span data-stu-id="48907-155">netcoreapp1.0</span></span><br><span data-ttu-id="48907-156">netcoreapp1.1</span><span class="sxs-lookup"><span data-stu-id="48907-156">netcoreapp1.1</span></span><br><span data-ttu-id="48907-157">netcoreapp2.0</span><span class="sxs-lookup"><span data-stu-id="48907-157">netcoreapp2.0</span></span><br><span data-ttu-id="48907-158">netcoreapp2.1</span><span class="sxs-lookup"><span data-stu-id="48907-158">netcoreapp2.1</span></span> |
| <span data-ttu-id="48907-159">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="48907-159">.NET Framework</span></span>             | <span data-ttu-id="48907-160">net11</span><span class="sxs-lookup"><span data-stu-id="48907-160">net11</span></span><br><span data-ttu-id="48907-161">net20</span><span class="sxs-lookup"><span data-stu-id="48907-161">net20</span></span><br><span data-ttu-id="48907-162">net35</span><span class="sxs-lookup"><span data-stu-id="48907-162">net35</span></span><br><span data-ttu-id="48907-163">net40</span><span class="sxs-lookup"><span data-stu-id="48907-163">net40</span></span><br><span data-ttu-id="48907-164">net403</span><span class="sxs-lookup"><span data-stu-id="48907-164">net403</span></span><br><span data-ttu-id="48907-165">net45</span><span class="sxs-lookup"><span data-stu-id="48907-165">net45</span></span><br><span data-ttu-id="48907-166">net451</span><span class="sxs-lookup"><span data-stu-id="48907-166">net451</span></span><br><span data-ttu-id="48907-167">net452</span><span class="sxs-lookup"><span data-stu-id="48907-167">net452</span></span><br><span data-ttu-id="48907-168">net46</span><span class="sxs-lookup"><span data-stu-id="48907-168">net46</span></span><br><span data-ttu-id="48907-169">net461</span><span class="sxs-lookup"><span data-stu-id="48907-169">net461</span></span><br><span data-ttu-id="48907-170">net462</span><span class="sxs-lookup"><span data-stu-id="48907-170">net462</span></span><br><span data-ttu-id="48907-171">net47</span><span class="sxs-lookup"><span data-stu-id="48907-171">net47</span></span><br><span data-ttu-id="48907-172">net471</span><span class="sxs-lookup"><span data-stu-id="48907-172">net471</span></span><br><span data-ttu-id="48907-173">net472</span><span class="sxs-lookup"><span data-stu-id="48907-173">net472</span></span> |
| <span data-ttu-id="48907-174">Windows ストア</span><span class="sxs-lookup"><span data-stu-id="48907-174">Windows Store</span></span>              | <span data-ttu-id="48907-175">netcore [netcore45]</span><span class="sxs-lookup"><span data-stu-id="48907-175">netcore [netcore45]</span></span><br><span data-ttu-id="48907-176">netcore45 [win] [win8]</span><span class="sxs-lookup"><span data-stu-id="48907-176">netcore45 [win] [win8]</span></span><br><span data-ttu-id="48907-177">netcore451 [win81]</span><span class="sxs-lookup"><span data-stu-id="48907-177">netcore451 [win81]</span></span> |
| <span data-ttu-id="48907-178">.NET Micro Framework</span><span class="sxs-lookup"><span data-stu-id="48907-178">.NET Micro Framework</span></span>       | <span data-ttu-id="48907-179">netmf</span><span class="sxs-lookup"><span data-stu-id="48907-179">netmf</span></span> |
| <span data-ttu-id="48907-180">Silverlight</span><span class="sxs-lookup"><span data-stu-id="48907-180">Silverlight</span></span>                | <span data-ttu-id="48907-181">sl4</span><span class="sxs-lookup"><span data-stu-id="48907-181">sl4</span></span><br><span data-ttu-id="48907-182">sl5</span><span class="sxs-lookup"><span data-stu-id="48907-182">sl5</span></span> |
| <span data-ttu-id="48907-183">Windows Phone</span><span class="sxs-lookup"><span data-stu-id="48907-183">Windows Phone</span></span>              | <span data-ttu-id="48907-184">wp [wp7]</span><span class="sxs-lookup"><span data-stu-id="48907-184">wp [wp7]</span></span><br><span data-ttu-id="48907-185">wp7</span><span class="sxs-lookup"><span data-stu-id="48907-185">wp7</span></span><br><span data-ttu-id="48907-186">wp75</span><span class="sxs-lookup"><span data-stu-id="48907-186">wp75</span></span><br><span data-ttu-id="48907-187">wp8</span><span class="sxs-lookup"><span data-stu-id="48907-187">wp8</span></span><br><span data-ttu-id="48907-188">wp81</span><span class="sxs-lookup"><span data-stu-id="48907-188">wp81</span></span><br><span data-ttu-id="48907-189">wpa81</span><span class="sxs-lookup"><span data-stu-id="48907-189">wpa81</span></span> |
| <span data-ttu-id="48907-190">ユニバーサル Windows プラットフォーム</span><span class="sxs-lookup"><span data-stu-id="48907-190">Universal Windows Platform</span></span> | <span data-ttu-id="48907-191">uap [uap10.0]</span><span class="sxs-lookup"><span data-stu-id="48907-191">uap [uap10.0]</span></span><br><span data-ttu-id="48907-192">uap10.0 [win10] [netcore50]</span><span class="sxs-lookup"><span data-stu-id="48907-192">uap10.0 [win10] [netcore50]</span></span> |

## <a name="how-to-specify-target-frameworks"></a><span data-ttu-id="48907-193">ターゲット フレームワークを指定する方法</span><span class="sxs-lookup"><span data-stu-id="48907-193">How to specify target frameworks</span></span>

<span data-ttu-id="48907-194">ターゲット フレームワークはプロジェクト ファイルで指定します。</span><span class="sxs-lookup"><span data-stu-id="48907-194">Target frameworks are specified in your project file.</span></span> <span data-ttu-id="48907-195">単一のターゲット フレームワークを指定するときは、**TargetFramework** 要素を使います。</span><span class="sxs-lookup"><span data-stu-id="48907-195">When a single target framework is specified, use the **TargetFramework** element.</span></span> <span data-ttu-id="48907-196">次のコンソール アプリのプロジェクト ファイルでは、.NET Core 2.0 をターゲットにする方法が示されています。</span><span class="sxs-lookup"><span data-stu-id="48907-196">The following console app project file demonstrates how to target .NET Core 2.0:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.0</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="48907-197">複数のターゲット フレームワークを指定するときは、各ターゲット フレームワークに対するアセンブリを条件付きで参照できます。</span><span class="sxs-lookup"><span data-stu-id="48907-197">When you specify multiple target frameworks, you may conditionally reference assemblies for each target framework.</span></span> <span data-ttu-id="48907-198">コードでは、プリプロセッサ シンボルと *if-then-else* ロジックを使うことで、これらのアセンブリに対して条件付きでコンパイルできます。</span><span class="sxs-lookup"><span data-stu-id="48907-198">In your code, you can conditionally compile against those assemblies by using preprocessor symbols with *if-then-else* logic.</span></span>

<span data-ttu-id="48907-199">次のライブラリ プロジェクト ファイルは、.NET Standard (`netstandard1.4`) の API と、.NET Framework (`net40` および `net45`) の API をターゲットにしています。</span><span class="sxs-lookup"><span data-stu-id="48907-199">The following library project file targets APIs of .NET Standard (`netstandard1.4`) and APIs of the .NET Framework (`net40` and `net45`).</span></span> <span data-ttu-id="48907-200">ターゲット フレームワークが複数あるときは、複数形の **TargetFrameworks** 要素を使います。</span><span class="sxs-lookup"><span data-stu-id="48907-200">Use the plural **TargetFrameworks** element with multiple target frameworks.</span></span> <span data-ttu-id="48907-201">ライブラリが 2 つの .NET Framework TFM に対してコンパイルされるときに `Condition` 属性で実装固有のパッケージを指定する方法に注意してください。</span><span class="sxs-lookup"><span data-stu-id="48907-201">Note how the `Condition` attributes include implementation-specific packages when the library is compiled for the two .NET Framework TFMs:</span></span>

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

<span data-ttu-id="48907-202">ライブラリまたはアプリ内では、各ターゲット フレームワーク用にコンパイルするための条件付きコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="48907-202">Within your library or app, you write conditional code to compile for each target framework:</span></span>

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

<span data-ttu-id="48907-203">ビルド システムは、「[サポートされるターゲット フレームワークのバージョン](#supported-target-framework-versions)」の表で示されているターゲット フレームワークを表すプリプロセッサ シンボルを認識します。</span><span class="sxs-lookup"><span data-stu-id="48907-203">The build system is aware of preprocessor symbols representing the target frameworks shown in the [Supported target framework versions](#supported-target-framework-versions) table.</span></span> <span data-ttu-id="48907-204">.NET Standard または .NET Core の TFM を表すシンボルを使うときは、ドットをアンダースコアに置き換え、小文字を大文字に変更します (たとえば、`netstandard1.4` のシンボルは `NETSTANDARD1_4` です)。</span><span class="sxs-lookup"><span data-stu-id="48907-204">When using a symbol that represents a .NET Standard or .NET Core TFM, replace the dot with an underscore and change lowercase letters to uppercase (for example, the symbol for `netstandard1.4` is `NETSTANDARD1_4`).</span></span>

<span data-ttu-id="48907-205">.NET Core ターゲット フレームワークのプリプロセッサ シンボルの完全な一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="48907-205">The complete list of preprocessor symbols for .NET Core target frameworks is:</span></span>

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

## <a name="deprecated-target-frameworks"></a><span data-ttu-id="48907-206">非推奨のターゲット フレームワーク</span><span class="sxs-lookup"><span data-stu-id="48907-206">Deprecated target frameworks</span></span>

<span data-ttu-id="48907-207">次のターゲット フレームワークは非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="48907-207">The following target frameworks are deprecated.</span></span> <span data-ttu-id="48907-208">これらのターゲット フレームワークをターゲットにするパッケージは、指定されている代替フレームワークに移行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48907-208">Packages targeting these target frameworks should migrate to the indicated replacements.</span></span>

| <span data-ttu-id="48907-209">非推奨の TFM</span><span class="sxs-lookup"><span data-stu-id="48907-209">Deprecated TFM</span></span>                                                                             | <span data-ttu-id="48907-210">Replacement</span><span class="sxs-lookup"><span data-stu-id="48907-210">Replacement</span></span> |
| ------------------------------------------------------------------------------------------ | ----------- |
| <span data-ttu-id="48907-211">aspnet50</span><span class="sxs-lookup"><span data-stu-id="48907-211">aspnet50</span></span><br><span data-ttu-id="48907-212">aspnetcore50</span><span class="sxs-lookup"><span data-stu-id="48907-212">aspnetcore50</span></span><br><span data-ttu-id="48907-213">dnxcore50</span><span class="sxs-lookup"><span data-stu-id="48907-213">dnxcore50</span></span><br><span data-ttu-id="48907-214">dnx</span><span class="sxs-lookup"><span data-stu-id="48907-214">dnx</span></span><br><span data-ttu-id="48907-215">dnx45</span><span class="sxs-lookup"><span data-stu-id="48907-215">dnx45</span></span><br><span data-ttu-id="48907-216">dnx451</span><span class="sxs-lookup"><span data-stu-id="48907-216">dnx451</span></span><br><span data-ttu-id="48907-217">dnx452</span><span class="sxs-lookup"><span data-stu-id="48907-217">dnx452</span></span>                  | <span data-ttu-id="48907-218">netcoreapp</span><span class="sxs-lookup"><span data-stu-id="48907-218">netcoreapp</span></span>  |
| <span data-ttu-id="48907-219">dotnet</span><span class="sxs-lookup"><span data-stu-id="48907-219">dotnet</span></span><br><span data-ttu-id="48907-220">dotnet50</span><span class="sxs-lookup"><span data-stu-id="48907-220">dotnet50</span></span><br><span data-ttu-id="48907-221">dotnet51</span><span class="sxs-lookup"><span data-stu-id="48907-221">dotnet51</span></span><br><span data-ttu-id="48907-222">dotnet52</span><span class="sxs-lookup"><span data-stu-id="48907-222">dotnet52</span></span><br><span data-ttu-id="48907-223">dotnet53</span><span class="sxs-lookup"><span data-stu-id="48907-223">dotnet53</span></span><br><span data-ttu-id="48907-224">dotnet54</span><span class="sxs-lookup"><span data-stu-id="48907-224">dotnet54</span></span><br><span data-ttu-id="48907-225">dotnet55</span><span class="sxs-lookup"><span data-stu-id="48907-225">dotnet55</span></span><br><span data-ttu-id="48907-226">dotnet56</span><span class="sxs-lookup"><span data-stu-id="48907-226">dotnet56</span></span> | <span data-ttu-id="48907-227">netstandard</span><span class="sxs-lookup"><span data-stu-id="48907-227">netstandard</span></span> |
| <span data-ttu-id="48907-228">netcore50</span><span class="sxs-lookup"><span data-stu-id="48907-228">netcore50</span></span>                                                                                  | <span data-ttu-id="48907-229">uap10.0</span><span class="sxs-lookup"><span data-stu-id="48907-229">uap10.0</span></span>     |
| <span data-ttu-id="48907-230">win</span><span class="sxs-lookup"><span data-stu-id="48907-230">win</span></span>                                                                                        | <span data-ttu-id="48907-231">netcore45</span><span class="sxs-lookup"><span data-stu-id="48907-231">netcore45</span></span>   |
| <span data-ttu-id="48907-232">win8</span><span class="sxs-lookup"><span data-stu-id="48907-232">win8</span></span>                                                                                       | <span data-ttu-id="48907-233">netcore45</span><span class="sxs-lookup"><span data-stu-id="48907-233">netcore45</span></span>   |
| <span data-ttu-id="48907-234">win81</span><span class="sxs-lookup"><span data-stu-id="48907-234">win81</span></span>                                                                                      | <span data-ttu-id="48907-235">netcore451</span><span class="sxs-lookup"><span data-stu-id="48907-235">netcore451</span></span>  |
| <span data-ttu-id="48907-236">win10</span><span class="sxs-lookup"><span data-stu-id="48907-236">win10</span></span>                                                                                      | <span data-ttu-id="48907-237">uap10.0</span><span class="sxs-lookup"><span data-stu-id="48907-237">uap10.0</span></span>     |
| <span data-ttu-id="48907-238">winrt</span><span class="sxs-lookup"><span data-stu-id="48907-238">winrt</span></span>                                                                                      | <span data-ttu-id="48907-239">netcore45</span><span class="sxs-lookup"><span data-stu-id="48907-239">netcore45</span></span>   |

## <a name="see-also"></a><span data-ttu-id="48907-240">関連項目</span><span class="sxs-lookup"><span data-stu-id="48907-240">See also</span></span>

[<span data-ttu-id="48907-241">パッケージ、メタパッケージ、フレームワーク</span><span class="sxs-lookup"><span data-stu-id="48907-241">Packages, Metapackages and Frameworks</span></span>](../core/packages.md)  
[<span data-ttu-id="48907-242">クロス プラットフォーム ツールによるライブラリの開発</span><span class="sxs-lookup"><span data-stu-id="48907-242">Developing Libraries with Cross Platform Tools</span></span>](../core/tutorials/libraries.md)  
[<span data-ttu-id="48907-243">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="48907-243">.NET Standard</span></span>](net-standard.md)  
[<span data-ttu-id="48907-244">.NET Core バージョン管理</span><span class="sxs-lookup"><span data-stu-id="48907-244">.NET Core Versioning</span></span>](../core/versions/index.md)  
[<span data-ttu-id="48907-245">dotnet/standard GitHub リポジトリ</span><span class="sxs-lookup"><span data-stu-id="48907-245">dotnet/standard GitHub repository</span></span>](https://github.com/dotnet/standard)  
[<span data-ttu-id="48907-246">NuGet Tools GitHub リポジトリ</span><span class="sxs-lookup"><span data-stu-id="48907-246">NuGet Tools GitHub Repository</span></span>](https://github.com/joelverhagen/NuGetTools)  
[<span data-ttu-id="48907-247">.NET のフレームワーク プロファイル</span><span class="sxs-lookup"><span data-stu-id="48907-247">Framework Profiles in .NET</span></span>](https://blog.stephencleary.com/2012/05/framework-profiles-in-net.html)
