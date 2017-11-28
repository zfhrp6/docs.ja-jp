---
title: "クロス プラットフォーム ツールによるライブラリの開発"
description: ".NET Core CLI ツールを使用して .NET ライブラリを作成する方法を説明します。"
keywords: .NET, .NET Core
author: cartermp
ms.author: mairaw
ms.date: 05/01/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 9f6e8679-bd7e-4317-b3f9-7255a260d9cf
ms.openlocfilehash: 21f8a4f4862cabd21ab9017056f3f71706e8e9a1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="developing-libraries-with-cross-platform-tools"></a><span data-ttu-id="8ca1c-104">クロス プラットフォーム ツールによるライブラリの開発</span><span class="sxs-lookup"><span data-stu-id="8ca1c-104">Developing Libraries with Cross Platform Tools</span></span>

<span data-ttu-id="8ca1c-105">この記事では、クロスプラットフォーム CLI ツールを使用して .NET 用ライブラリを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-105">This article covers how to write libraries for .NET using cross-platform CLI tools.</span></span> <span data-ttu-id="8ca1c-106">CLI は、サポートされる任意の OS で動作する効率的で低レベルのエクスペリエンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-106">The CLI provides an efficient and low-level experience that works across any supported OS.</span></span> <span data-ttu-id="8ca1c-107">Visual Studio でライブラリを構築することもできます。Visual Studio で構築する場合は、[Visual Studio ガイドを参照](libraries-with-vs.md)してください。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-107">You can still build libraries with Visual Studio, and if that is your preferred experience [refer to the Visual Studio guide](libraries-with-vs.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8ca1c-108">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="8ca1c-108">Prerequisites</span></span>

<span data-ttu-id="8ca1c-109">[.NET Core SDK と CLI](https://www.microsoft.com/net/core) がコンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-109">You need [the .NET Core SDK and CLI](https://www.microsoft.com/net/core) installed on your machine.</span></span>

<span data-ttu-id="8ca1c-110">このドキュメントで [.NET Framework](http://getdotnet.azurewebsites.net/) バージョンについて扱うセクションでは、.NET Framework が Windows コンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-110">For the sections of this document dealing with .NET Framework versions, you need the [.NET Framework](http://getdotnet.azurewebsites.net/) installed on a Windows machine.</span></span>

<span data-ttu-id="8ca1c-111">また、古い .NET Framework ターゲットをサポートする場合、[.NET ターゲット プラットフォーム ページ](http://getdotnet.azurewebsites.net/target-dotnet-platforms.html)から古い .NET Framework バージョンの Targeting/Developer Pack をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-111">Additionally, if you wish to support older .NET Framework targets, you need to install targeting/developer packs for older framework versions from the [.NET target platforms page](http://getdotnet.azurewebsites.net/target-dotnet-platforms.html).</span></span> <span data-ttu-id="8ca1c-112">次の表を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-112">Refer to this table:</span></span>

| <span data-ttu-id="8ca1c-113">.NET Framework のバージョン</span><span class="sxs-lookup"><span data-stu-id="8ca1c-113">.NET Framework Version</span></span> | <span data-ttu-id="8ca1c-114">ダウンロードするもの</span><span class="sxs-lookup"><span data-stu-id="8ca1c-114">What to download</span></span>                                       |
| ---------------------- | ------------------------------------------------------ |
| <span data-ttu-id="8ca1c-115">4.6.1</span><span class="sxs-lookup"><span data-stu-id="8ca1c-115">4.6.1</span></span>                  | <span data-ttu-id="8ca1c-116">.NET Framework 4.6.1 Targeting Pack</span><span class="sxs-lookup"><span data-stu-id="8ca1c-116">.NET Framework 4.6.1 Targeting Pack</span></span>                    |
| <span data-ttu-id="8ca1c-117">4.6</span><span class="sxs-lookup"><span data-stu-id="8ca1c-117">4.6</span></span>                    | <span data-ttu-id="8ca1c-118">.NET Framework 4.6 Targeting Pack</span><span class="sxs-lookup"><span data-stu-id="8ca1c-118">.NET Framework 4.6 Targeting Pack</span></span>                      |
| <span data-ttu-id="8ca1c-119">4.5.2</span><span class="sxs-lookup"><span data-stu-id="8ca1c-119">4.5.2</span></span>                  | <span data-ttu-id="8ca1c-120">.NET Framework 4.5.2 Developer Pack</span><span class="sxs-lookup"><span data-stu-id="8ca1c-120">.NET Framework 4.5.2 Developer Pack</span></span>                    |
| <span data-ttu-id="8ca1c-121">4.5.1</span><span class="sxs-lookup"><span data-stu-id="8ca1c-121">4.5.1</span></span>                  | <span data-ttu-id="8ca1c-122">.NET Framework 4.5.1 Developer Pack</span><span class="sxs-lookup"><span data-stu-id="8ca1c-122">.NET Framework 4.5.1 Developer Pack</span></span>                    |
| <span data-ttu-id="8ca1c-123">4.5</span><span class="sxs-lookup"><span data-stu-id="8ca1c-123">4.5</span></span>                    | <span data-ttu-id="8ca1c-124">Windows 8 用 Windows ソフトウェア開発キット</span><span class="sxs-lookup"><span data-stu-id="8ca1c-124">Windows Software Development Kit for Windows 8</span></span>         |
| <span data-ttu-id="8ca1c-125">4.0</span><span class="sxs-lookup"><span data-stu-id="8ca1c-125">4.0</span></span>                    | <span data-ttu-id="8ca1c-126">Windows SDK for Windows 7 および .NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="8ca1c-126">Windows SDK for Windows 7 and .NET Framework 4</span></span>         |
| <span data-ttu-id="8ca1c-127">2.0、3.0、および 3.5</span><span class="sxs-lookup"><span data-stu-id="8ca1c-127">2.0, 3.0, and 3.5</span></span>      | <span data-ttu-id="8ca1c-128">.NET Framework 3.5 SP1 Runtime (または Windows 8 以降のバージョン)</span><span class="sxs-lookup"><span data-stu-id="8ca1c-128">.NET Framework 3.5 SP1 Runtime (or Windows 8+ version)</span></span> |

## <a name="how-to-target-the-net-standard"></a><span data-ttu-id="8ca1c-129">.NET Standard をターゲット設定する方法</span><span class="sxs-lookup"><span data-stu-id="8ca1c-129">How to target the .NET Standard</span></span>

<span data-ttu-id="8ca1c-130">.NET Standard にあまりなじみがない場合、詳細については、「[.NET Standard](../../standard/net-standard.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-130">If you're not quite familiar with the .NET Standard, refer to the [.NET Standard](../../standard/net-standard.md) to learn more.</span></span>

<span data-ttu-id="8ca1c-131">この記事には、.NET Standard バージョンを多様な実装にマップする表が掲載されています。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-131">In that article, there is a table which maps .NET Standard versions to various implementations:</span></span>

[!INCLUDE [net-standard-table](~/includes/net-standard-table.md)]

<span data-ttu-id="8ca1c-132">ライブラリを作成する目的でこの表の意味について説明します。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-132">Here's what this table means for the purposes of creating a library:</span></span>

<span data-ttu-id="8ca1c-133">選択する .NET Standard のバージョンは、最新の API にアクセスできることと、より多くの .NET 実装と .NET Standard バージョンをターゲット設定できることのトレードオフで決まります。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-133">The version of the .NET Standard you pick will be a tradeoff between access to the newest APIs and the ability to target more .NET implementations and .NET Standard versions.</span></span> <span data-ttu-id="8ca1c-134">ターゲット設定可能なプラットフォームとバージョンの範囲は、`netstandardX.X` のバージョンを選択し (`X.X` はバージョン番号です)、プロジェクト ファイル (`.csproj` または `.fsproj`) に追加することで制御します。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-134">You control the range of targetable platforms and versions by picking a version of `netstandardX.X` (Where `X.X` is a version number) and adding it to your project file (`.csproj` or `.fsproj`).</span></span>

<span data-ttu-id="8ca1c-135">.NET Standard をターゲット設定する場合、ニーズに応じて主に 3 つのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-135">You have three primary options when targeting the .NET Standard, depending on your needs.</span></span>

1. <span data-ttu-id="8ca1c-136">テンプレートに指定されている既定のバージョンの .NET Standard (`netstandard1.4`) を使用できます。これで .NET Standard 上のほとんどの API にアクセスできますが、UWP、.NET Framework 4.6.1、近日公開される .NET Standard 2.0 との互換性もあります。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-136">You can use the default version of the .NET Standard supplied by templates - `netstandard1.4` - which gives you access to most APIs on .NET Standard while still being compatible with UWP, .NET Framework 4.6.1, and the forthcoming .NET Standard 2.0.</span></span>

    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <TargetFramework>netstandard1.4</TargetFramework>
      </PropertyGroup>
    </Project>
    ```

2. <span data-ttu-id="8ca1c-137">プロジェクト ファイルの `TargetFramework` ノードの値を変更することで、.NET Standard の下位または上位バージョンを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-137">You can use a lower or higher version of the .NET Standard by modifying the value in the `TargetFramework` node of your project file.</span></span>
    
    <span data-ttu-id="8ca1c-138">.NET Standard バージョンは下位互換性があります。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-138">.NET Standard versions are backward compatible.</span></span> <span data-ttu-id="8ca1c-139">つまり、`netstandard1.0` ライブラリは、`netstandard1.1` プラットフォーム以降で実行されます。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-139">That means that `netstandard1.0` libraries run on `netstandard1.1` platforms and higher.</span></span> <span data-ttu-id="8ca1c-140">ただし、上位互換性はないため、古い .NET Standard プラットフォームは新しいプラットフォームを参照できません。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-140">However, there is no forward compatibility - lower .NET Standard platforms cannot reference higher ones.</span></span> <span data-ttu-id="8ca1c-141">つまり、`netstandard1.0` ライブラリは、`netstandard1.1` 以降をターゲットとするライブラリを参照できません。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-141">This means that `netstandard1.0` libraries cannot reference libraries targeting `netstandard1.1` or higher.</span></span> <span data-ttu-id="8ca1c-142">API とプラットフォームを適切に組み合わせ、ニーズに対応できる Standard バージョンを選択してください。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-142">Select the Standard version that has the right mix of APIs and platform support for your needs.</span></span> <span data-ttu-id="8ca1c-143">現時点では `netstandard1.4` が推奨されます。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-143">We recommend `netstandard1.4` for now.</span></span>
    
3. <span data-ttu-id="8ca1c-144">.NET Framework バージョン 4.0 以前をターゲットにする場合、または .NET Framework では利用できて .NET Standard では利用できない API (`System.Drawing` など) を使用する場合は、マルチターゲットの方法について次のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-144">If you want to target the .NET Framework versions 4.0 or below, or you wish to use an API available in the .NET Framework but not in the .NET Standard (for example, `System.Drawing`), read the following sections and learn how to multitarget.</span></span>

## <a name="how-to-target-the-net-framework"></a><span data-ttu-id="8ca1c-145">.NET Framework をターゲット設定する方法</span><span class="sxs-lookup"><span data-stu-id="8ca1c-145">How to target the .NET Framework</span></span>

> [!NOTE]
> <span data-ttu-id="8ca1c-146">次の手順では、.NET Framework がコンピューターにインストールされていると想定しています。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-146">These instructions assume you have the .NET Framework installed on your machine.</span></span> <span data-ttu-id="8ca1c-147">依存関係のインストールについては、「[前提条件](#prerequisites)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-147">Refer to the [Prerequisites](#prerequisites) to get dependencies installed.</span></span>

<span data-ttu-id="8ca1c-148">ここで使用されている .NET Framework バージョンには、現在サポートされていないものもあります。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-148">Keep in mind that some of the .NET Framework versions used here are no longer in support.</span></span> <span data-ttu-id="8ca1c-149">サポートされないバージョンについては、「[.NET Framework Support Lifecycle Policy FAQ](https://support.microsoft.com/gp/framework_faq/en-us)」(.NET Framework のサポート ライフサイクル ポリシーについてよく寄せられる質問) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-149">Refer to the [.NET Framework Support Lifecycle Policy FAQ](https://support.microsoft.com/gp/framework_faq/en-us) about unsupported versions.</span></span>

<span data-ttu-id="8ca1c-150">最大数の開発者とプロジェクトを対象にしたい場合、基準となるターゲットは .NET Framework 4.0 です。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-150">If you want to reach the maximum number of developers and projects, use the .NET Framework 4.0 as your baseline target.</span></span> <span data-ttu-id="8ca1c-151">.NET Framework をターゲット設定するには、まず、サポートしたい .NET Framework バージョンに対応する正しいターゲット フレームワーク モニカー (TFM) を使用します。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-151">To target the .NET Framework, you will need to begin by using the correct Target Framework Moniker (TFM) that corresponds to the .NET Framework version you wish to support.</span></span>

```
.NET Framework 2.0   --> net20
.NET Framework 3.0   --> net30
.NET Framework 3.5   --> net35
.NET Framework 4.0   --> net40
.NET Framework 4.5   --> net45
.NET Framework 4.5.1 --> net451
.NET Framework 4.5.2 --> net452
.NET Framework 4.6   --> net46
.NET Framework 4.6.1 --> net461
.NET Framework 4.6.2 --> net462
.NET Framework 4.7   --> net47
```

<span data-ttu-id="8ca1c-152">この TFM をプロジェクト ファイルの `TargetFramework` セクションに挿入します。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-152">You then insert this TFM into the `TargetFramework` section of your project file.</span></span> <span data-ttu-id="8ca1c-153">.NET Framework 4.0 をターゲットとするライブラリを作成する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-153">For example, here's how you would write a library which targets the .NET Framework 4.0:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net40</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="8ca1c-154">以上です。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-154">And that's it!</span></span> <span data-ttu-id="8ca1c-155">これは .NET Framework 4 向けにのみコンパイルされていますが、新しいバージョンの .NET Framework のライブラリを使用できます。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-155">Although this compiled only for the .NET Framework 4, you can use the library on newer versions of the .NET Framework.</span></span>

## <a name="how-to-multitarget"></a><span data-ttu-id="8ca1c-156">マルチターゲットを設定する方法</span><span class="sxs-lookup"><span data-stu-id="8ca1c-156">How to Multitarget</span></span>

> [!NOTE]
> <span data-ttu-id="8ca1c-157">次の手順では、.NET Framework がコンピューターにインストールされている想定です。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-157">The following instructions assume you have the .NET Framework installed on your machine.</span></span> <span data-ttu-id="8ca1c-158">インストールする必要がある依存関係と、そのダウンロードできる場所については、「[前提条件](#prerequisites)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-158">Refer to the [Prerequisites](#prerequisites) section to learn which dependencies you need to install and where to download them from.</span></span>

<span data-ttu-id="8ca1c-159">プロジェクトが .NET Framework と .NET Core の両方をサポートしている場合、状況によっては古いバージョンの .NET Framework をターゲットにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-159">You may need to target older versions of the .NET Framework when your project supports both the .NET Framework and .NET Core.</span></span> <span data-ttu-id="8ca1c-160">このシナリオで、新しい API と新しいターゲット向けの言語構成を使用する場合、コードで `#if` ディレクティブを使用します。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-160">In this scenario, if you want to use newer APIs and language constructs for the newer targets, use `#if` directives in your code.</span></span> <span data-ttu-id="8ca1c-161">また、必要に応じて、ターゲットにする各プラットフォームに応じて異なるパッケージと依存関係追加して、それぞれに異なる必要な API を含めます。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-161">You also might need to add different packages and dependencies for each platform you're targeting to include the different APIs needed for each case.</span></span>

<span data-ttu-id="8ca1c-162">たとえば、HTTP 上でネットワークキング操作を行うライブラリがあるとします。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-162">For example, let's say you have a library that performs networking operations over HTTP.</span></span> <span data-ttu-id="8ca1c-163">.NET Standard と .NET Framework バージョン 4.5 以降の場合、`System.Net.Http` 名前空間の `HttpClient` クラスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-163">For .NET Standard and the .NET Framework versions 4.5 or higher, you can use the `HttpClient` class from the `System.Net.Http` namespace.</span></span> <span data-ttu-id="8ca1c-164">ただし、それより前のバージョンの .NET Framework に `HttpClient` クラスはないので、代わりに `System.Net` 名前空間の `WebClient` クラスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-164">However, earlier versions of the .NET Framework don't have the `HttpClient` class, so you could use the `WebClient` class from the `System.Net` namespace for those instead.</span></span>

<span data-ttu-id="8ca1c-165">プロジェクト ファイルは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-165">Your project file could look like this:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netstandard1.4;net40;net45</TargetFrameworks>
  </PropertyGroup>

  <!-- Need to conditionally bring in references for the .NET Framework 4.0 target -->
  <ItemGroup Condition="'$(TargetFramework)' == 'net40'">
    <Reference Include="System.Net" />
  </ItemGroup>

  <!-- Need to conditionally bring in references for the .NET Framework 4.5 target -->
  <ItemGroup Condition="'$(TargetFramework)' == 'net45'">
    <Reference Include="System.Net.Http" />
    <Reference Include="System.Threading.Tasks" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="8ca1c-166">主な変更点が 3 つあります。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-166">You'll notice three major changes here:</span></span>

1. <span data-ttu-id="8ca1c-167">`TargetFramework` ノードは `TargetFrameworks` で置き換えられ、3 つの TFM が内部に表現されています。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-167">The `TargetFramework` node has been replaced by `TargetFrameworks`, and three TFMs are expressed inside.</span></span>
1. <span data-ttu-id="8ca1c-168">1 つの .NET Framework 参照を取り込む `net40 ` ターゲットの `<ItemGroup>` ノードがあります。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-168">There is an `<ItemGroup>` node for the `net40 ` target pulling in one .NET Framework reference.</span></span>
1. <span data-ttu-id="8ca1c-169">.NET Framework の参照 2 に取り込む `net45` ターゲットの `<ItemGroup>` ノードがあります。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-169">There is an `<ItemGroup>` node for the `net45` target pulling in two .NET Framework references.</span></span>

<span data-ttu-id="8ca1c-170">ビルド システムは `#if` ディレクティブで使用される次のプリプロセッサ シンボルを認識します。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-170">The build system is aware of the following preprocessor symbols used in `#if` directives:</span></span>

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

<span data-ttu-id="8ca1c-171">次に、ターゲットごとに条件付きコンパイルを利用する例を示します。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-171">Here is an example making use of conditional compilation per-target:</span></span>

```csharp
using System;
using System.Text.RegularExpressions;
#if NET40
// This only compiles for the .NET Framework 4 targets
using System.Net;
#else
 // This compiles for all other targets
using System.Net.Http;
using System.Threading.Tasks;
#endif

namespace MultitargetLib
{
    public class Library
    {
#if NET40
        private readonly WebClient _client = new WebClient();
        private readonly object _locker = new object();
#else
        private readonly HttpClient _client = new HttpClient();
#endif

#if NET40
        // .NET Framework 4.0 does not have async/await
        public string GetDotNetCount()
        {
            string url = "http://www.dotnetfoundation.org/";

            var uri = new Uri(url);

            string result = "";

            // Lock here to provide thread-safety.
            lock(_locker)
            {
                result = _client.DownloadString(uri);
            }

            int dotNetCount = Regex.Matches(result, ".NET").Count;

            return $"Dotnet Foundation mentions .NET {dotNetCount} times!";
        }
#else
        // .NET 4.5+ can use async/await!
        public async Task<string> GetDotNetCountAsync()
        {
            string url = "http://www.dotnetfoundation.org/";

            // HttpClient is thread-safe, so no need to explicitly lock here
            var result = await _client.GetStringAsync(url);

            int dotNetCount = Regex.Matches(result, ".NET").Count;

            return $"dotnetfoundation.org mentions .NET {dotNetCount} times in its HTML!";
        }
#endif
    }
}
```

<span data-ttu-id="8ca1c-172">`dotnet build` を使用してこのプロジェクトをビルドすると、`bin/` フォルダー以下に 3 つのディレクトリがあることがわかります。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-172">If you build this project with `dotnet build`, you'll notice three directories under the `bin/` folder:</span></span>

```
net40/
net45/
netstandard1.4/
```

<span data-ttu-id="8ca1c-173">各ディレクトリには、各ターゲットの `.dll` ファイルがあります。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-173">Each of these contain the `.dll` files for each target.</span></span>

## <a name="how-to-test-libraries-on-net-core"></a><span data-ttu-id="8ca1c-174">.NET Core でライブラリをテストする方法</span><span class="sxs-lookup"><span data-stu-id="8ca1c-174">How to test libraries on .NET Core</span></span>

<span data-ttu-id="8ca1c-175">プラットフォーム全体でテストできることが重要です。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-175">It's important to be able to test across platforms.</span></span> <span data-ttu-id="8ca1c-176">[xUnit](http://xunit.github.io/) または MSTest はそのまま利用できます。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-176">You can use either [xUnit](http://xunit.github.io/) or MSTest out of the box.</span></span> <span data-ttu-id="8ca1c-177">どちらも、.NET Core 上のライブラリの単体テストに最適です。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-177">Both are perfectly suitable for unit testing your library on .NET Core.</span></span> <span data-ttu-id="8ca1c-178">テスト プロジェクトでソリューションをセットアップする方法は、[ソリューションの構造](#structuring-a-solution)によって異なります。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-178">How you set up your solution with test projects will depend on the [structure of your solution](#structuring-a-solution).</span></span> <span data-ttu-id="8ca1c-179">次の例は、テスト ディレクトリとソース ディレクトリが同じ最上位ディレクトリにある場合です。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-179">The following example assumes that the test and source directories live in the same top-level directory.</span></span>

> [!NOTE]
> <span data-ttu-id="8ca1c-180">この例ではいくつかの [.NET CLI コマンド](../tools/index.md)を使用しています。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-180">This uses some [.NET Core CLI commands](../tools/index.md).</span></span> <span data-ttu-id="8ca1c-181">詳細については、「[dotnet new](../tools/dotnet-new.md)」と「[dotnet sln](../tools/dotnet-sln.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-181">See [dotnet new](../tools/dotnet-new.md) and [dotnet sln](../tools/dotnet-sln.md) for more information.</span></span>

1. <span data-ttu-id="8ca1c-182">ソリューションを設定します。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-182">Set up your solution.</span></span> <span data-ttu-id="8ca1c-183">次のコマンドで実行することができます。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-183">You can do so with the following commands:</span></span>

   ```bash
   mkdir SolutionWithSrcAndTest
   cd SolutionWithSrcAndTest
   dotnet new sln
   dotnet new classlib -o MyProject
   dotnet new xunit -o MyProject.Test
   dotnet sln add MyProject/MyProject.csproj
   dotnet sln add MyProject.Test/MyProject.Test.csproj
   ```

   <span data-ttu-id="8ca1c-184">これでプロジェクトが作成され、ソリューション内のプロジェクトがリンクされます。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-184">This will create projects and link them together in a solution.</span></span> <span data-ttu-id="8ca1c-185">`SolutionWithSrcAndTest` のディレクトリは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-185">Your directory for `SolutionWithSrcAndTest` should look like this:</span></span>

   ```
   /SolutionWithSrcAndTest
   |__SolutionWithSrcAndTest.sln
   |__MyProject/
   |__MyProject.Test/
   ```

1. <span data-ttu-id="8ca1c-186">テスト プロジェクトのディレクトリに移動し、`MyProject` から `MyProject.Test` への参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-186">Navigate to the test project's directory and add a reference to `MyProject.Test` from `MyProject`.</span></span>

   ```bash
   cd MyProject.Test
   dotnet add reference ../MyProject/MyProject.csproj
   ```

1. <span data-ttu-id="8ca1c-187">パッケージを復元し、プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-187">Restore packages and build projects:</span></span>

   ```bash
   dotnet restore
   dotnet build
   ```

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

1. <span data-ttu-id="8ca1c-188">`dotnet test` コマンドを実行して、xUnit が実行されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-188">Verify that xUnit runs by executing the `dotnet test` command.</span></span> <span data-ttu-id="8ca1c-189">MSTest を使用する場合は、MSTest コンソール実行ツールが実行されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-189">If you chose to use MSTest, then the MSTest console runner should run instead.</span></span>
    
<span data-ttu-id="8ca1c-190">以上です。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-190">And that's it!</span></span> <span data-ttu-id="8ca1c-191">コマンド ライン ツールを使用して、すべてのプラットフォームでライブラリをテストできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-191">You can now test your library across all platforms using command line tools.</span></span> <span data-ttu-id="8ca1c-192">すべてをセットアップしてテストに進む場合、ライブラリのテストはとても単純です。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-192">To continue testing now that you have everything set up, testing your library is very simple:</span></span>

1. <span data-ttu-id="8ca1c-193">ライブラリに変更を加えます。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-193">Make changes to your library.</span></span>
1. <span data-ttu-id="8ca1c-194">コマンド ラインから、`dotnet test` コマンドを使用してテスト ディレクトリでテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-194">Run tests from the command line, in your test directory, with `dotnet test` command.</span></span>

<span data-ttu-id="8ca1c-195">`dotnet test` コマンドを呼び出すと、コードは自動的にリビルドされます。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-195">Your code will be automatically rebuilt when you invoke `dotnet test` command.</span></span>

## <a name="how-to-use-multiple-projects"></a><span data-ttu-id="8ca1c-196">複数のプロジェクトを使用する方法</span><span class="sxs-lookup"><span data-stu-id="8ca1c-196">How to use multiple projects</span></span>

<span data-ttu-id="8ca1c-197">大規模なライブラリで一般的なニーズは、複数のプロジェクトに機能を配置することです。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-197">A common need for larger libraries is to place functionality in different projects.</span></span>

<span data-ttu-id="8ca1c-198">たとえば、慣用的な C# や F# で使用できるライブラリをビルドするとします。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-198">Imagine you wished to build a library which could be consumed in idiomatic C# and F#.</span></span> <span data-ttu-id="8ca1c-199">これは、ライブラリのユーザーは、C# または F# に対して自然な方法で使用することを意味します。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-199">That would mean that consumers of your library consume them in ways which are natural to C# or F#.</span></span> <span data-ttu-id="8ca1c-200">たとえば、C# の場合、次のようにライブラリを使用できます。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-200">For example, in C# you might consume the library like this:</span></span>

```csharp
using AwesomeLibrary.CSharp;

public Task DoThings(Data data)
{
    var convertResult = await AwesomeLibrary.ConvertAsync(data);
    var result = AwesomeLibrary.Process(convertResult);
    // do something with result
}
```

<span data-ttu-id="8ca1c-201">F# の場合は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-201">In F#, it might look like this:</span></span>

```fsharp
open AwesomeLibrary.FSharp

let doWork data = async {
    let! result = AwesomeLibrary.AsyncConvert data // Uses an F# async function rather than C# async method
    // do something with result
}
```

<span data-ttu-id="8ca1c-202">このような使用シナリオは、アクセスされる API が C# と F# 用に異なる構造を持つ必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-202">Consumption scenarios like this mean that the APIs being accessed have to have a different structure for C# and F#.</span></span>  <span data-ttu-id="8ca1c-203">これを実現する一般的なアプローチとして、ライブラリのすべてのロジックをコア プロジェクトに取り入れ、C# および F# プロジェクトでコア プロジェクトに呼び出す API レイヤーを定義する方法があります。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-203">A common approach to accomplishing this is to factor all of the logic of a library into a core project, with C# and F# projects defining the API layers that call into that core project.</span></span>  <span data-ttu-id="8ca1c-204">以降のセクションでは、次の名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-204">The rest of the section will use the following names:</span></span>

* <span data-ttu-id="8ca1c-205">**AwesomeLibrary.Core** - ライブラリのすべてのロジックを含むコア プロジェクト</span><span class="sxs-lookup"><span data-stu-id="8ca1c-205">**AwesomeLibrary.Core** - A core project which contains all logic for the library</span></span>
* <span data-ttu-id="8ca1c-206">**AwesomeLibrary.CSharp** - C# で使用するためのパブリック API を含むプロジェクト</span><span class="sxs-lookup"><span data-stu-id="8ca1c-206">**AwesomeLibrary.CSharp** - A project with public APIs intended for consumption in C#</span></span>
* <span data-ttu-id="8ca1c-207">**AwesomeLibrary.FSharp** - F# で使用するためのパブリック API を含むプロジェクト</span><span class="sxs-lookup"><span data-stu-id="8ca1c-207">**AwesomeLibrary.FSharp** - A project with public APIs intended for consumption in F#</span></span>

<span data-ttu-id="8ca1c-208">自分の端末で次のコマンドを実行し、このガイドと同じ構造を作成することができます。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-208">You can run the following commands in your terminal to produce the same structure as this guide:</span></span>

```console
mkdir AwesomeLibrary && cd AwesomeLibrary
dotnet new sln
mkdir AwesomeLibrary.Core && cd AwesomeLibrary.Core && dotnet new classlib
cd ..
mkdir AwesomeLibrary.CSharp && cd AwesomeLibrary.CSharp && dotnet new classlib
cd ..
mkdir AwesomeLibrary.FSharp && cd AwesomeLibrary.FSharp && dotnet new classlib -lang F#
cd ..
dotnet sln add AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
dotnet sln add AwesomeLibrary.CSharp/AwesomeLibrary.CSharp.csproj
dotnet sln add AwesomeLibrary.FSharp/AwesomeLibrary.FSharp.fsproj
```

<span data-ttu-id="8ca1c-209">これで上記の 3 つのプロジェクトと、プロジェクトをリンクするソリューション ファイルが追加されます。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-209">This will add the three projects above and a solution file which links them together.</span></span> <span data-ttu-id="8ca1c-210">ソリューション ファイルとリンクするプロジェクトを作成すると、最上位レベルからプロジェクトを復元し、ビルドできるようになります。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-210">Creating the solution file and linking projects will allow you to restore and build projects from a top-level.</span></span>

### <a name="project-to-project-referencing"></a><span data-ttu-id="8ca1c-211">プロジェクト間参照</span><span class="sxs-lookup"><span data-stu-id="8ca1c-211">Project-to-project referencing</span></span>

<span data-ttu-id="8ca1c-212">プロジェクトを参照するには、.NET Core CLI を使用してプロジェクト参照を追加することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-212">The best way to reference a project is to use the .NET Core CLI to add a project reference.</span></span> <span data-ttu-id="8ca1c-213">**AwesomeLibrary.CSharp** と **AwesomeLibrary.FSharp** のプロジェクト ディレクトリから、次のコマンドを実行できます。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-213">From the **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** project directories, you can run the following command:</span></span>

```console
$ dotnet add reference ../AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
```

<span data-ttu-id="8ca1c-214">**AwesomeLibrary.CSharp** と **AwesomeLibrary.FSharp** の両方のプロジェクト ファイルは、`ProjectReference` ターゲットとして **AwesomeLibrary.Core** を参照するようになります。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-214">The project files for both **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** will now reference **AwesomeLibrary.Core** as a `ProjectReference` target.</span></span>  <span data-ttu-id="8ca1c-215">この参照を確認するには、プロジェクト ファイルに以下の行があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-215">You can verify this by inspecting the project files and seeing the following in them:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\AwesomeLibrary.Core\AwesomeLibrary.Core.csproj" />
</ItemGroup>
```

<span data-ttu-id="8ca1c-216">この .NET Core CLI を使用しない場合は、このセクションを各プロジェクト ファイルに手動で追加します。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-216">You can add this section to each project file manually if you prefer not to use the .NET Core CLI.</span></span>

### <a name="structuring-a-solution"></a><span data-ttu-id="8ca1c-217">ソリューションの構築</span><span class="sxs-lookup"><span data-stu-id="8ca1c-217">Structuring a solution</span></span>

<span data-ttu-id="8ca1c-218">マルチプロジェクト ソリューションのもう 1 つの重要な側面は、全体のプロジェクト構造を適切に構築することです。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-218">Another important aspect of multi-project solutions is establishing a good overall project structure.</span></span> <span data-ttu-id="8ca1c-219">ただし、`dotnet sln add` でソリューション ファイルに各プロジェクト ファイルがリンクされ、ソリューション レベルで `dotnet restore` と `dotnet build` を実行できる限り、好みに応じてコードを整理することができます。</span><span class="sxs-lookup"><span data-stu-id="8ca1c-219">You can organize code however you like, and as long as you link each project to your solution file with `dotnet sln add`, you will be able to run `dotnet restore` and `dotnet build` at the solution level.</span></span>
