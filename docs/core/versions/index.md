---
title: .NET Core バージョン管理
description: .NET Core でのバージョン管理のしくみについて説明します。
author: bleroy
ms.author: mairaw
ms.date: 02/13/2018
ms.openlocfilehash: 0cfd620d2b6e6e60531b0e2aa938c1ed64b6af23
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33219015"
---
# <a name="net-core-versioning"></a><span data-ttu-id="315e4-103">.NET Core バージョン管理</span><span class="sxs-lookup"><span data-stu-id="315e4-103">.NET Core versioning</span></span>

<span data-ttu-id="315e4-104">.NET Core は、ユニットとして配布される [NuGet パッケージ](../packages.md)、ツール、フレームワークで構成されます。</span><span class="sxs-lookup"><span data-stu-id="315e4-104">.NET Core is made of [NuGet packages](../packages.md), tools, and frameworks that are distributed as a unit.</span></span> <span data-ttu-id="315e4-105">これらのプラットフォームの各レイヤーは、製品のアジリティ向上のため、個別にバージョン管理できます。</span><span class="sxs-lookup"><span data-stu-id="315e4-105">Each of these platform layers can be versioned separately, enabling better agility.</span></span> <span data-ttu-id="315e4-106">バージョン管理には大きな柔軟性がありますが、製品を理解しやすいように、プラットフォームをユニットとしてバージョン管理することも望まれています。</span><span class="sxs-lookup"><span data-stu-id="315e4-106">While there is significant versioning flexibility in that regard, there's also a desire to version the platform as a unit to make the product easier to understand.</span></span>

<span data-ttu-id="315e4-107">この記事では、.NET Core SDK とランタイムのバージョン管理方法を明確にすることを目的としています。</span><span class="sxs-lookup"><span data-stu-id="315e4-107">This article aims at clarifying how the .NET Core SDK and runtime are versioned.</span></span>

<span data-ttu-id="315e4-108">.NET Core には個別にバージョン管理される多くの移動するパーツがあります。</span><span class="sxs-lookup"><span data-stu-id="315e4-108">There are lots of moving parts that version independently in .NET Core.</span></span> <span data-ttu-id="315e4-109">ただし、.NET Core 2.0 以降では、すべてのユーザーが ".NET Core" 全体のバージョンとして理解する簡単に理解できる最上位*レベ*ルのバージョンがあります。</span><span class="sxs-lookup"><span data-stu-id="315e4-109">However, starting with .NET Core 2.0, there is an easy to understand top-level version number that everybody understands to be *the* version of ".NET Core" as a whole.</span></span> <span data-ttu-id="315e4-110">このドキュメントの残りの部分は、これらすべてのパーツのバージョン管理の詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="315e4-110">The rest of this document goes into the details of the versioning of all those parts.</span></span> <span data-ttu-id="315e4-111">たとえばパッケージ マネージャーの場合は、これらの詳細が重要になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="315e4-111">These details can be important if you're a package manager, for example.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="315e4-112">このトピックで説明されているバージョン管理の詳細は、.NET Core SDK ランタイムの現在のバージョンには適用されません。</span><span class="sxs-lookup"><span data-stu-id="315e4-112">The versioning details explained on this topic don't apply to the current version of the .NET Core SDK and runtime.</span></span>
> <span data-ttu-id="315e4-113">バージョン スキームは将来のリリースで変更されます。</span><span class="sxs-lookup"><span data-stu-id="315e4-113">The version scheme is changing in future releases.</span></span> <span data-ttu-id="315e4-114">[dotnet/designs](https://github.com/dotnet/designs/pull/29) リポジトリで現在の提案を表示できます。</span><span class="sxs-lookup"><span data-stu-id="315e4-114">You can see the current proposal at the [dotnet/designs](https://github.com/dotnet/designs/pull/29) repository.</span></span>

## <a name="versioning-details"></a><span data-ttu-id="315e4-115">バージョン管理の詳細</span><span class="sxs-lookup"><span data-stu-id="315e4-115">Versioning details</span></span>

<span data-ttu-id="315e4-116">.NET Core 2.0 では、ダウンロードは、ファイル名に 1 つのバージョン番号が表示されます。</span><span class="sxs-lookup"><span data-stu-id="315e4-116">With .NET Core 2.0, downloads show a single version number in their file name.</span></span> <span data-ttu-id="315e4-117">次のバージョン番号が統合されました。</span><span class="sxs-lookup"><span data-stu-id="315e4-117">The following version numbers were unified:</span></span>

* <span data-ttu-id="315e4-118">共有のフレームワークおよび関連付けられているランタイム。</span><span class="sxs-lookup"><span data-stu-id="315e4-118">The shared framework and associated runtime.</span></span>
* <span data-ttu-id="315e4-119">.NET Core SDK および関連付けられた .NET Core CLI。</span><span class="sxs-lookup"><span data-stu-id="315e4-119">The .NET Core SDK and associated .NET Core CLI.</span></span>
* <span data-ttu-id="315e4-120">`Microsoft.NETCore.App` メタパッケージ。</span><span class="sxs-lookup"><span data-stu-id="315e4-120">The `Microsoft.NETCore.App` metapackage.</span></span>

<span data-ttu-id="315e4-121">1 つのバージョン番号を使用すると、ユーザーが自分のデバイス マシンにインストールする SDK のバージョン、および運用環境にプロビジョニングするときの共有フレームワークの対応するバージョンを簡単に知ることができるようになります。</span><span class="sxs-lookup"><span data-stu-id="315e4-121">The use of a single version number makes it easier for users to know what version of the SDK to install on their dev machines, and what the corresponding version of the shared framework should be when time comes to provision a production environment.</span></span> <span data-ttu-id="315e4-122">SDK またはランタイムをダウンロードするときに、表示されるバージョン番号は同じです。</span><span class="sxs-lookup"><span data-stu-id="315e4-122">When downloading an SDK or runtime, the version number you see is going to be the same.</span></span>

### <a name="installers"></a><span data-ttu-id="315e4-123">インストーラー</span><span class="sxs-lookup"><span data-stu-id="315e4-123">Installers</span></span>

<span data-ttu-id="315e4-124">.NET Core 2.0 では、[日次のビルド](https://github.com/dotnet/core-setup#daily-builds)と[リリース](https://www.microsoft.com/net/download/core)は、理解しやすい新しい名前付けスキームに従います。</span><span class="sxs-lookup"><span data-stu-id="315e4-124">With .NET Core 2.0, downloads for the [daily builds](https://github.com/dotnet/core-setup#daily-builds) and [releases](https://www.microsoft.com/net/download/core) adhere to a new naming scheme that is easier to understand.</span></span>
<span data-ttu-id="315e4-125">これらのダウンロードのインストーラー UI も、インストールされているコンポーネントの名前とバージョンを明確に表示するように変更されました。</span><span class="sxs-lookup"><span data-stu-id="315e4-125">The installer UI in those downloads was also modified to clearly present the names and versions of the components being installed.</span></span> <span data-ttu-id="315e4-126">具体的には、タイトルは、ダウンロードのファイル名に含まれるものと同じバージョン番号を表示するようになりました。</span><span class="sxs-lookup"><span data-stu-id="315e4-126">In particular, titles now show the same version number that is in the download's file name.</span></span>

#### <a name="file-name-format"></a><span data-ttu-id="315e4-127">ファイル名の形式</span><span class="sxs-lookup"><span data-stu-id="315e4-127">File name format</span></span>

`[product]-[component]-[major].[minor].[patch]-[previewN]-[optional build #]-[rid].[file ext]`

<span data-ttu-id="315e4-128">この形式のいくつかの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="315e4-128">Here are some examples of this format:</span></span>

```
dotnet-runtime-2.0.4-macos.10.12-x64.pkg            # Mac runtime installer
dotnet-sdk-2.0.4-win10-x64.exe                      # Windows SDK installer
dotnet-sdk-2.0.4-fedora.24-x64.tar.gz               # Fedora 24 binary archive

#Ubuntu file set needed for the SDK
dotnet-host-2.0.4-ubuntu.16.04-x64.deb              # Host / muxer and host policy
dotnet-runtime-2.0.4-ubuntu.16.04-x64.deb           # runtime
dotnet-sdk-2.0.4-ubuntu.16.04-x64.deb               # SDK tools
```

<span data-ttu-id="315e4-129">形式は読み取り可能であり、ダウンロードしている内容、そのバージョン、それらを使用できる場所を明確に示します。</span><span class="sxs-lookup"><span data-stu-id="315e4-129">The format is readable and clearly shows what you're downloading, what version it is, and where you can use it.</span></span> <span data-ttu-id="315e4-130">ランタイム パッケージ名には、`runtime` が含まれ、SDK には `SDK` が含まれます。</span><span class="sxs-lookup"><span data-stu-id="315e4-130">The runtime package name includes `runtime`, and the SDK includes `SDK`.</span></span>

#### <a name="ui-string-format"></a><span data-ttu-id="315e4-131">UI の文字列形式</span><span class="sxs-lookup"><span data-stu-id="315e4-131">UI string format</span></span>

<span data-ttu-id="315e4-132">すべての Web サイトの説明と、インストーラーの UI 文字列では一貫性、正確さ、簡潔さが維持されています。</span><span class="sxs-lookup"><span data-stu-id="315e4-132">All web site descriptions and UI strings in the installers are kept consistent, accurate, and simple.</span></span> <span data-ttu-id="315e4-133">次の表に例を示します。</span><span class="sxs-lookup"><span data-stu-id="315e4-133">The following table shows some examples:</span></span>

| <span data-ttu-id="315e4-134">Installer</span><span class="sxs-lookup"><span data-stu-id="315e4-134">Installer</span></span> | <span data-ttu-id="315e4-135">ウィンドウ タイトル</span><span class="sxs-lookup"><span data-stu-id="315e4-135">Window Title</span></span>                          | <span data-ttu-id="315e4-136">インストーラーの他のコンテンツ</span><span class="sxs-lookup"><span data-stu-id="315e4-136">Other content in installer</span></span> | <span data-ttu-id="315e4-137">インストールされる内容</span><span class="sxs-lookup"><span data-stu-id="315e4-137">What is installed</span></span>                               |
| :--       | :--                                   | :--                        | :--                                             |
| <span data-ttu-id="315e4-138">SDK</span><span class="sxs-lookup"><span data-stu-id="315e4-138">SDK</span></span>       | <span data-ttu-id="315e4-139">.NET Core 2.0 (x64) SDK インストーラー</span><span class="sxs-lookup"><span data-stu-id="315e4-139">.NET Core 2.0 SDK (x64) Installer</span></span>     | <span data-ttu-id="315e4-140">.NET Core 2.0.4 SDK</span><span class="sxs-lookup"><span data-stu-id="315e4-140">.NET Core 2.0.4 SDK</span></span>        | <span data-ttu-id="315e4-141">.NET Core 2.0.4 ツール + .NET Core 2.0.4 ランタイム</span><span class="sxs-lookup"><span data-stu-id="315e4-141">.NET Core 2.0.4 Tools + .NET Core 2.0.4 Runtime</span></span> |
| <span data-ttu-id="315e4-142">ランタイム</span><span class="sxs-lookup"><span data-stu-id="315e4-142">Runtime</span></span>   | <span data-ttu-id="315e4-143">.NET Core 2.0 ランタイム (x64) インストーラー</span><span class="sxs-lookup"><span data-stu-id="315e4-143">.NET Core 2.0 Runtime (x64) Installer</span></span> | <span data-ttu-id="315e4-144">.NET Core 2.0.4 ランタイム</span><span class="sxs-lookup"><span data-stu-id="315e4-144">.NET Core 2.0.4 Runtime</span></span>    | <span data-ttu-id="315e4-145">.NET Core 2.0.4 ランタイム</span><span class="sxs-lookup"><span data-stu-id="315e4-145">.NET Core 2.0.4 Runtime</span></span>                         |

<span data-ttu-id="315e4-146">プレビュー リリースはわずかに異なります。</span><span class="sxs-lookup"><span data-stu-id="315e4-146">Preview releases differ only slightly:</span></span>

| <span data-ttu-id="315e4-147">Installer</span><span class="sxs-lookup"><span data-stu-id="315e4-147">Installer</span></span> | <span data-ttu-id="315e4-148">ウィンドウ タイトル</span><span class="sxs-lookup"><span data-stu-id="315e4-148">Window Title</span></span>                                    | <span data-ttu-id="315e4-149">インストーラーの他のコンテンツ</span><span class="sxs-lookup"><span data-stu-id="315e4-149">Other content in installer</span></span>        | <span data-ttu-id="315e4-150">インストールされる内容</span><span class="sxs-lookup"><span data-stu-id="315e4-150">What is installed</span></span>                                                   |
| :--       | :--                                             | :--                               | :--                                                                 |
| <span data-ttu-id="315e4-151">SDK</span><span class="sxs-lookup"><span data-stu-id="315e4-151">SDK</span></span>       | <span data-ttu-id="315e4-152">.NET Core 2.0 Preview 1 SDK (x 64) インストーラー</span><span class="sxs-lookup"><span data-stu-id="315e4-152">.NET Core 2.0 Preview 1 SDK (x64) Installer</span></span>     | <span data-ttu-id="315e4-153">.NET Core 2.0.0 Preview 1 SDK</span><span class="sxs-lookup"><span data-stu-id="315e4-153">.NET Core 2.0.0 Preview 1 SDK</span></span>     | <span data-ttu-id="315e4-154">.NET Core 2.0.0 Preview 1 ツール + .NET Core 2.0.0 Preview 1 ランタイム</span><span class="sxs-lookup"><span data-stu-id="315e4-154">.NET Core 2.0.0 Preview 1 Tools + .NET Core 2.0.0 Preview 1 Runtime</span></span> |
| <span data-ttu-id="315e4-155">ランタイム</span><span class="sxs-lookup"><span data-stu-id="315e4-155">Runtime</span></span>   | <span data-ttu-id="315e4-156">.NET Core 2.0 Preview 1 ランタイム (x64) インストーラー</span><span class="sxs-lookup"><span data-stu-id="315e4-156">.NET Core 2.0 Preview 1 Runtime (x64) Installer</span></span> | <span data-ttu-id="315e4-157">.NET Core 2.0.0 Preview 1 ランタイム</span><span class="sxs-lookup"><span data-stu-id="315e4-157">.NET Core 2.0.0 Preview 1 Runtime</span></span> | <span data-ttu-id="315e4-158">.NET Core 2.0.0 Preview 1 ランタイム</span><span class="sxs-lookup"><span data-stu-id="315e4-158">.NET Core 2.0.0 Preview 1 Runtime</span></span>                                   |

<span data-ttu-id="315e4-159">1 つの SDK リリースに複数のランタイムのバージョンが含まれている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="315e4-159">It may happen that an SDK release contains more than one version of the runtime.</span></span> <span data-ttu-id="315e4-160">その場合、インストーラー UI は次のようになります (SDK のバージョンのみが表示され、インストールされるランタイムのバージョンは、Windows および Mac でのインストール処理の最後にある概要ページに表示されます)。</span><span class="sxs-lookup"><span data-stu-id="315e4-160">When that happens, the installer UX looks like the following (only the SDK version is shown and the installed Runtime versions are shown on a summary page at the end of the installation process on Windows and Mac):</span></span>

| <span data-ttu-id="315e4-161">Installer</span><span class="sxs-lookup"><span data-stu-id="315e4-161">Installer</span></span> | <span data-ttu-id="315e4-162">ウィンドウ タイトル</span><span class="sxs-lookup"><span data-stu-id="315e4-162">Window Title</span></span>                      | <span data-ttu-id="315e4-163">インストーラーの他のコンテンツ</span><span class="sxs-lookup"><span data-stu-id="315e4-163">Other content in installer</span></span>                                   | <span data-ttu-id="315e4-164">インストールされる内容</span><span class="sxs-lookup"><span data-stu-id="315e4-164">What is installed</span></span>                                                         |
| :--       | :--                               | :--                                                          | :--                                                                       |
| <span data-ttu-id="315e4-165">SDK</span><span class="sxs-lookup"><span data-stu-id="315e4-165">SDK</span></span>       | <span data-ttu-id="315e4-166">.NET Core 2.1 SDK (x64) インストーラー</span><span class="sxs-lookup"><span data-stu-id="315e4-166">.NET Core 2.1 SDK (x64) Installer</span></span> | <span data-ttu-id="315e4-167">.NET Core 2.1.1 SDK</span><span class="sxs-lookup"><span data-stu-id="315e4-167">.NET Core 2.1.1 SDK</span></span> <br> <span data-ttu-id="315e4-168">.NET Core 2.1.1 ランタイム</span><span class="sxs-lookup"><span data-stu-id="315e4-168">.NET Core 2.1.1 Runtime</span></span> <br> <span data-ttu-id="315e4-169">.NET Core 2.0.6 ランタイム</span><span class="sxs-lookup"><span data-stu-id="315e4-169">.NET Core 2.0.6 Runtime</span></span> | <span data-ttu-id="315e4-170">.NET Core 2.1.1 ツール + .NET Core 2.1.1 ランタイム + .NET Core 2.0.6 ランタイム</span><span class="sxs-lookup"><span data-stu-id="315e4-170">.NET Core 2.1.1 Tools + .NET Core 2.1.1 Runtime + .NET Core 2.0.6 Runtime</span></span> |

<span data-ttu-id="315e4-171">ランタイムを変更せずに、.NET Core ツールを更新する必要がある場合もあります。</span><span class="sxs-lookup"><span data-stu-id="315e4-171">It's also possible that .NET Core Tools need to be updated, without runtime changes.</span></span> <span data-ttu-id="315e4-172">この場合、SDK のバージョンが増加し (たとえば 2.1.2 になり)、ランタイムは次回の配布時に更新されます (たとえば、ランタイムと SDK の両方が次回に 2.1.3 として配布されます)。</span><span class="sxs-lookup"><span data-stu-id="315e4-172">In that case, the SDK version is increased (for example, to 2.1.2) and then the Runtime catches up the next time it ships (for example, both the Runtime and SDK ship the next time as 2.1.3).</span></span>

### <a name="package-managers"></a><span data-ttu-id="315e4-173">パッケージ マネージャー</span><span class="sxs-lookup"><span data-stu-id="315e4-173">Package managers</span></span>

<span data-ttu-id="315e4-174">.NET Core は、Microsoft 以外のエンティティによって配布される場合があります。</span><span class="sxs-lookup"><span data-stu-id="315e4-174">.NET Core can be distributed by other entities than Microsoft.</span></span> <span data-ttu-id="315e4-175">具体的には、Linux ディストリビューションの所有者とパッケージ管理者は、自社のパッケージ マネージャーに .NET Core パッケージを追加する場合があります。</span><span class="sxs-lookup"><span data-stu-id="315e4-175">In particular, Linux distribution owners and package maintainers may add .NET Core packages to their package managers.</span></span> <span data-ttu-id="315e4-176">これらのパッケージの命名方法に関する推奨事項については、「[.NET Core distribution packaging](../build/distribution-packaging.md)」(.NET Core の配布パッケージ) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="315e4-176">For recommendations on how those packages should be named and versioned, see [.NET Core distribution packaging](../build/distribution-packaging.md).</span></span>

#### <a name="minimum-package-set"></a><span data-ttu-id="315e4-177">最小パッケージ セット</span><span class="sxs-lookup"><span data-stu-id="315e4-177">Minimum package set</span></span>

* <span data-ttu-id="315e4-178">`dotnet-runtime-[major].[minor]`: 指定したバージョンのランタイム (パッケージ マネージャーでは、指定したメジャーとマイナーの組み合わせからなる最新パッチ バージョンのみ使用可能)。</span><span class="sxs-lookup"><span data-stu-id="315e4-178">`dotnet-runtime-[major].[minor]`: a runtime with the specified version (only the latest patch version for a given major+minor combination should be available in the package manager).</span></span> <span data-ttu-id="315e4-179">新しいパッチ バージョンでパッケージを更新しますが、新しいマイナーまたはメジャー バージョンは別のパッケージとなります。</span><span class="sxs-lookup"><span data-stu-id="315e4-179">New patch versions update the package, but new minor or major versions are separate packages.</span></span>

  <span data-ttu-id="315e4-180">**依存関係**: `dotnet-host`</span><span class="sxs-lookup"><span data-stu-id="315e4-180">**Dependencies**: `dotnet-host`</span></span>

* <span data-ttu-id="315e4-181">`dotnet-sdk`: 最新の SDK</span><span class="sxs-lookup"><span data-stu-id="315e4-181">`dotnet-sdk`: the latest SDK.</span></span> <span data-ttu-id="315e4-182">`update` がメジャー、マイナー、およびパッチ バージョンをロール フォワードします。</span><span class="sxs-lookup"><span data-stu-id="315e4-182">`update` rolls forward major, minor, and patch versions.</span></span>

  <span data-ttu-id="315e4-183">**依存関係**: 最新の `dotnet-sdk-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="315e4-183">**Dependencies**: the latest `dotnet-sdk-[major].[minor]`.</span></span>

* <span data-ttu-id="315e4-184">`dotnet-sdk-[major].[minor]`: 指定したバージョンの SDK</span><span class="sxs-lookup"><span data-stu-id="315e4-184">`dotnet-sdk-[major].[minor]`: the SDK with the specified version.</span></span> <span data-ttu-id="315e4-185">指定するバージョンは、ユーザーが共有フレームワークに SDK を簡単に関連付けられるように、同梱する共有フレームワークの中で最も高いバージョンを含むものにします。</span><span class="sxs-lookup"><span data-stu-id="315e4-185">The version specified is the highest included version of included shared frameworks, so that users can easily relate an SDK to a shared framework.</span></span> <span data-ttu-id="315e4-186">新しいパッチ バージョンでパッケージを更新しますが、新しいマイナーまたはメジャー バージョンは別のパッケージとなります。</span><span class="sxs-lookup"><span data-stu-id="315e4-186">New patch versions update the package, but new minor or major versions are separate packages.</span></span>

  <span data-ttu-id="315e4-187">**依存関係**: `dotnet-host`、1 つまたは複数の `dotnet-runtime-[major].[minor]` (そのうちの 1 つは SDK コード自体で使用され、それ以外はユーザーの構築および実行のためにこの場所にあります)。</span><span class="sxs-lookup"><span data-stu-id="315e4-187">**Dependencies**: `dotnet-host`, one or more `dotnet-runtime-[major].[minor]` (one of those is used by the SDK code itself, the others are here for users to build and run against).</span></span>

* <span data-ttu-id="315e4-188">`dotnet-host`: 最新のホスト</span><span class="sxs-lookup"><span data-stu-id="315e4-188">`dotnet-host`: the latest host.</span></span>

##### <a name="preview-versions"></a><span data-ttu-id="315e4-189">プレビュー バージョン</span><span class="sxs-lookup"><span data-stu-id="315e4-189">Preview versions</span></span>

<span data-ttu-id="315e4-190">パッケージ管理者は、ランタイムと SDK のプレビュー バージョンを含めるという選択もできます。</span><span class="sxs-lookup"><span data-stu-id="315e4-190">Package maintainers may decide to include preview versions of the runtime and SDK.</span></span> <span data-ttu-id="315e4-191">それらのプレビュー バージョンはバージョン管理されない `dotnet-sdk` パッケージに含めないでください。ただし、名前のメジャーおよびマイナー バージョン セクションにプレビュー マーカーを追加して、バージョン管理されたパッケージとしてリリースできます。</span><span class="sxs-lookup"><span data-stu-id="315e4-191">Don't include those preview versions in the unversioned `dotnet-sdk` package, but you can release them as versioned packages with an additional preview marker appended to the major and minor version sections of the name.</span></span> <span data-ttu-id="315e4-192">たとえば、`dotnet-sdk-2.0-preview1-final` のようなパッケージが可能です。</span><span class="sxs-lookup"><span data-stu-id="315e4-192">For example, there may be a `dotnet-sdk-2.0-preview1-final` package.</span></span>

### <a name="docker"></a><span data-ttu-id="315e4-193">Docker</span><span class="sxs-lookup"><span data-stu-id="315e4-193">Docker</span></span>

<span data-ttu-id="315e4-194">一般的な Docker タグの名前付け規則では、コンポーネント名の前にバージョン番号を配置します。</span><span class="sxs-lookup"><span data-stu-id="315e4-194">A general Docker tag naming convention is to place the version number before the component name.</span></span> <span data-ttu-id="315e4-195">この規則は、引き続き利用できます。</span><span class="sxs-lookup"><span data-stu-id="315e4-195">This convention may continue to be utilized.</span></span> <span data-ttu-id="315e4-196">現在のタグには、次のようにランタイムのバージョンのみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="315e4-196">The current tags include only the Runtime version as follows.</span></span>

* <span data-ttu-id="315e4-197">1.0.8-runtime</span><span class="sxs-lookup"><span data-stu-id="315e4-197">1.0.8-runtime</span></span>
* <span data-ttu-id="315e4-198">1.0.8-sdk</span><span class="sxs-lookup"><span data-stu-id="315e4-198">1.0.8-sdk</span></span>
* <span data-ttu-id="315e4-199">2.0.4-runtime</span><span class="sxs-lookup"><span data-stu-id="315e4-199">2.0.4-runtime</span></span>
* <span data-ttu-id="315e4-200">2.0.4-sdk</span><span class="sxs-lookup"><span data-stu-id="315e4-200">2.0.4-sdk</span></span>
* <span data-ttu-id="315e4-201">2.1.1-runtime</span><span class="sxs-lookup"><span data-stu-id="315e4-201">2.1.1-runtime</span></span>
* <span data-ttu-id="315e4-202">2.1.1-sdk</span><span class="sxs-lookup"><span data-stu-id="315e4-202">2.1.1-sdk</span></span>

<span data-ttu-id="315e4-203">ランタイムではなく、SDK のバージョンを表すように SDK のタグを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="315e4-203">The SDK tags should be updated to represent the SDK version rather than Runtime.</span></span>

<span data-ttu-id="315e4-204">.NET Core CLI ツール (SDK に含まれる) が修正される可能性がありますが、既存のランタイムとともに再出荷されます。</span><span class="sxs-lookup"><span data-stu-id="315e4-204">It's also possible that the .NET Core CLI tools (included in the SDK) are fixed but reship with an existing runtime.</span></span> <span data-ttu-id="315e4-205">この場合、SDK のバージョンが増加し (たとえば 2.1.2 になり)、ランタイムは次回の配布時に更新されます (たとえば、ランタイムと SDK の両方が次回に 2.1.3 として配布されます)。</span><span class="sxs-lookup"><span data-stu-id="315e4-205">In that case, the SDK version is increased (for example, to 2.1.2), and then the Runtime catches up the next time it ships (for example, both the Runtime and SDK ship the following time as 2.1.3).</span></span>

## <a name="semantic-versioning"></a><span data-ttu-id="315e4-206">セマンティック バージョン管理</span><span class="sxs-lookup"><span data-stu-id="315e4-206">Semantic Versioning</span></span>

<span data-ttu-id="315e4-207">.NET Core は、[セマンティック バージョン管理 (SemVer)](http://semver.org/) を使用して、`MAJOR.MINOR.PATCH` バージョン管理を採用し、バージョン番号のさまざまな部分を使用して変更の度合いと種類を記述します。</span><span class="sxs-lookup"><span data-stu-id="315e4-207">.NET Core uses [Semantic Versioning (SemVer)](http://semver.org/), adopting the use of `MAJOR.MINOR.PATCH` versioning, using the various parts of the version number to describe the degree and type of change.</span></span>

```
MAJOR.MINOR.PATCH[-PRERELEASE-BUILDNUMBER]
```

<span data-ttu-id="315e4-208">省略可能な `PRERELEASE` と `BUILDNUMBER` の部分はサポートされるリリースに含まれることはなく、ソース ターゲットからローカルでビルドされた夜間のビルドおよびサポートされていないプレビュー リリースにのみ存在します。</span><span class="sxs-lookup"><span data-stu-id="315e4-208">The optional `PRERELEASE` and `BUILDNUMBER` parts are never part of supported releases and only exist on nightly builds, local builds from source targets, and unsupported preview releases.</span></span>

### <a name="how-version-numbers-are-incremented"></a><span data-ttu-id="315e4-209">バージョン番号はどのように増分されますか?</span><span class="sxs-lookup"><span data-stu-id="315e4-209">How version numbers are incremented?</span></span>

<span data-ttu-id="315e4-210">`MAJOR` は次のときに増分されます。</span><span class="sxs-lookup"><span data-stu-id="315e4-210">`MAJOR` is incremented when:</span></span>

- <span data-ttu-id="315e4-211">古いバージョンがサポート対象から除外された。</span><span class="sxs-lookup"><span data-stu-id="315e4-211">An old version is no longer supported.</span></span>
- <span data-ttu-id="315e4-212">既存の依存関係の新しい `MAJOR` バージョンが採用された。</span><span class="sxs-lookup"><span data-stu-id="315e4-212">A newer `MAJOR` version of an existing dependency is adopted.</span></span>
- <span data-ttu-id="315e4-213">互換性特性の既定の設定が "オフ" に変更された。</span><span class="sxs-lookup"><span data-stu-id="315e4-213">The default setting of a compatibility quirk is changed to "off."</span></span>

<span data-ttu-id="315e4-214">`MINOR` は次のときに増分されます。</span><span class="sxs-lookup"><span data-stu-id="315e4-214">`MINOR` is incremented when:</span></span>

- <span data-ttu-id="315e4-215">パブリック API アクセス領域が追加された。</span><span class="sxs-lookup"><span data-stu-id="315e4-215">Public API surface area is added.</span></span>
- <span data-ttu-id="315e4-216">新しい動作が追加された。</span><span class="sxs-lookup"><span data-stu-id="315e4-216">A new behavior is added.</span></span>
- <span data-ttu-id="315e4-217">既存の依存関係の新しい `MINOR` バージョンが採用された。</span><span class="sxs-lookup"><span data-stu-id="315e4-217">A newer `MINOR` version of an existing dependency is adopted.</span></span>
- <span data-ttu-id="315e4-218">新しい依存関係が導入された。</span><span class="sxs-lookup"><span data-stu-id="315e4-218">A new dependency is introduced.</span></span>

<span data-ttu-id="315e4-219">`PATCH` は次のときに増分されます。</span><span class="sxs-lookup"><span data-stu-id="315e4-219">`PATCH` is incremented when:</span></span>

- <span data-ttu-id="315e4-220">バグの修正が行われた。</span><span class="sxs-lookup"><span data-stu-id="315e4-220">Bug fixes are made.</span></span>
- <span data-ttu-id="315e4-221">より新しいプラットフォームのサポートが追加された。</span><span class="sxs-lookup"><span data-stu-id="315e4-221">Support for a newer platform is added.</span></span>
- <span data-ttu-id="315e4-222">既存の依存関係の新しい `PATCH` バージョンが採用された。</span><span class="sxs-lookup"><span data-stu-id="315e4-222">A newer `PATCH` version of an existing dependency is adopted.</span></span>
- <span data-ttu-id="315e4-223">前のケースのいずれかに一致しない他の変更。</span><span class="sxs-lookup"><span data-stu-id="315e4-223">Any other change doesn't fit one of the previous cases.</span></span>

<span data-ttu-id="315e4-224">複数の変更が存在する場合、個々の変更によって影響を受ける最高位置の要素が増分され、それに続く要素はゼロにリセットされます。</span><span class="sxs-lookup"><span data-stu-id="315e4-224">When there are multiple changes, the highest element affected by individual changes is incremented, and the following ones are reset to zero.</span></span> <span data-ttu-id="315e4-225">たとえば、`MAJOR` が増分され、`MINOR` と `PATCH` はゼロにリセットされます。</span><span class="sxs-lookup"><span data-stu-id="315e4-225">For example, when `MAJOR` is incremented, `MINOR` and `PATCH` are reset to zero.</span></span> <span data-ttu-id="315e4-226">`MINOR` が増分されるときには、`PATCH` はゼロにリセットされますが、`MAJOR` は変更されません。</span><span class="sxs-lookup"><span data-stu-id="315e4-226">When `MINOR` is incremented, `PATCH` is reset to zero while `MAJOR` is left untouched.</span></span>

### <a name="preview-versions"></a><span data-ttu-id="315e4-227">プレビュー バージョン</span><span class="sxs-lookup"><span data-stu-id="315e4-227">Preview versions</span></span>

<span data-ttu-id="315e4-228">プレビュー バージョンには、`-preview[number]-([build]|"final")` がバージョンに追加されます。</span><span class="sxs-lookup"><span data-stu-id="315e4-228">Preview versions have a `-preview[number]-([build]|"final")` appended to the version.</span></span> <span data-ttu-id="315e4-229">たとえば、`2.0.0-preview1-final` のようにします。</span><span class="sxs-lookup"><span data-stu-id="315e4-229">For example, `2.0.0-preview1-final`.</span></span>

### <a name="servicing-versions"></a><span data-ttu-id="315e4-230">サービスのバージョン</span><span class="sxs-lookup"><span data-stu-id="315e4-230">Servicing versions</span></span>

<span data-ttu-id="315e4-231">リリースされると、通常はリリース ブランチが毎日のビルドの生成を停止し、代わりにサービスのビルドの生成を開始します。</span><span class="sxs-lookup"><span data-stu-id="315e4-231">After a release goes out, the release branches generally stop producing daily builds and instead start producing servicing builds.</span></span> <span data-ttu-id="315e4-232">サービスのバージョンには、`-servicing-[number]` がバージョンに追加されます。</span><span class="sxs-lookup"><span data-stu-id="315e4-232">Servicing versions have a `-servicing-[number]` appended to the version.</span></span> <span data-ttu-id="315e4-233">たとえば、`2.0.1-servicing-006924` のようにします。</span><span class="sxs-lookup"><span data-stu-id="315e4-233">For example, `2.0.1-servicing-006924`.</span></span>

### <a name="lts-vs-current"></a><span data-ttu-id="315e4-234">LTS と Current</span><span class="sxs-lookup"><span data-stu-id="315e4-234">LTS vs. current</span></span>

<span data-ttu-id="315e4-235">.NET Core のリリースには、Long Term Support (LTS) と Current という 2 つのリリース トレーニングがあります。</span><span class="sxs-lookup"><span data-stu-id="315e4-235">There are two trains of releases for .NET Core: Long Term Support (LTS) and Current.</span></span> <span data-ttu-id="315e4-236">これにより、ユーザーは、引き続きサポートされているときに、安定性のレベルと必要な新機能を選択することができます。</span><span class="sxs-lookup"><span data-stu-id="315e4-236">That enables users to pick the level of stability and new features they want, while still being supported.</span></span>

- <span data-ttu-id="315e4-237">LTS は、新機能を受け取る頻度が低くとも、より完成度の高いプラットフォームを利用できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="315e4-237">LTS means you get new features less frequently, but you have a more mature platform.</span></span> <span data-ttu-id="315e4-238">LTS では、長期間のサポートもあります。</span><span class="sxs-lookup"><span data-stu-id="315e4-238">LTS also has a longer period of support.</span></span>
- <span data-ttu-id="315e4-239">Current は、新機能と API をより頻繁に取得しますが、更新プログラムをインストールするための期間が短く、それらの更新がより頻繁に発生するという欠点があります。</span><span class="sxs-lookup"><span data-stu-id="315e4-239">Current means you get new features and APIs more frequently, but the disadvantage is that you have a shorter window of time to install updates, and those updates happen more frequently.</span></span> <span data-ttu-id="315e4-240">Current も完全にサポートされていますが、サポート期間が LTS よりも短くなっています。</span><span class="sxs-lookup"><span data-stu-id="315e4-240">Current is also fully supported but the support period is shorter than LTS.</span></span>

<span data-ttu-id="315e4-241">"Current" バージョンは LTS に昇格される場合があります。</span><span class="sxs-lookup"><span data-stu-id="315e4-241">A "Current" version may get promoted to LTS.</span></span>

<span data-ttu-id="315e4-242">"LTS" と "Current" は、関連付けられているレベルのサポートに関するステートメントを指定するために特定のリリースに付けるラベルと見なす必要があります。</span><span class="sxs-lookup"><span data-stu-id="315e4-242">"LTS" and "Current" should be considered as labels that we put on specific releases to make a statement about the associated level of support.</span></span>

<span data-ttu-id="315e4-243">詳細については、[.NET Core サポート ライフサイクル ファクト シート](https://www.microsoft.com/net/core/support)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="315e4-243">For more information, see [.NET Core Support Lifecycle Fact Sheet](https://www.microsoft.com/net/core/support).</span></span>

## <a name="versioning-scheme-details"></a><span data-ttu-id="315e4-244">バージョン管理スキームの詳細</span><span class="sxs-lookup"><span data-stu-id="315e4-244">Versioning scheme details</span></span>

<span data-ttu-id="315e4-245">.NET Core は、次の部分で構成されます。</span><span class="sxs-lookup"><span data-stu-id="315e4-245">.NET Core is made of the following parts:</span></span>

- <span data-ttu-id="315e4-246">ホスト: フレームワークに依存するアプリケーション用の *dotnet.exe*、または自己完結型アプリケーション用の *\<appname > .exe* です。</span><span class="sxs-lookup"><span data-stu-id="315e4-246">A host: either *dotnet.exe* for framework-dependent applications, or *\<appname>.exe* for self-contained applications.</span></span>
- <span data-ttu-id="315e4-247">SDK (実稼働環境ではなく開発者のマシンに必要な一連のツール)。</span><span class="sxs-lookup"><span data-stu-id="315e4-247">An SDK (the set of tools necessary on a developer's machine, but not in production).</span></span>
- <span data-ttu-id="315e4-248">ランタイム。</span><span class="sxs-lookup"><span data-stu-id="315e4-248">A runtime.</span></span>
- <span data-ttu-id="315e4-249">パッケージとして配布される共有フレームワークの実装。</span><span class="sxs-lookup"><span data-stu-id="315e4-249">A shared framework implementation, distributed as packages.</span></span> <span data-ttu-id="315e4-250">特に修正プログラムのバージョン管理において、各パッケージは個別にバージョン管理されます。</span><span class="sxs-lookup"><span data-stu-id="315e4-250">Each package is versioned independently, particularly for patch versioning.</span></span>
- <span data-ttu-id="315e4-251">または、バージョン管理されたユニットとして詳細なパッケージを参照する[メタパッケージ](../packages.md)のセット。</span><span class="sxs-lookup"><span data-stu-id="315e4-251">Optionally, a set of [metapackages](../packages.md) that reference fine-grained packages as a versioned unit.</span></span> <span data-ttu-id="315e4-252">メタパッケージは、パッケージとは別個にバージョン管理できます。</span><span class="sxs-lookup"><span data-stu-id="315e4-252">Metapackages can be versioned separately from packages.</span></span>

<span data-ttu-id="315e4-253">.NET Core には、ターゲット フレームワークのセットも含まれています (たとえば、`netstandard` または `netcoreapp`)。これはバージョン番号の増分と共に徐々に大きくなる API セットを表します。</span><span class="sxs-lookup"><span data-stu-id="315e4-253">.NET Core also includes a set of target frameworks (for example, `netstandard` or `netcoreapp`) that represent a progressively larger API set, as version numbers are incremented.</span></span>

### <a name="net-standard"></a><span data-ttu-id="315e4-254">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="315e4-254">.NET Standard</span></span>

<span data-ttu-id="315e4-255">.NET Standard では、`MAJOR.MINOR` バージョン管理スキームを使用しています。</span><span class="sxs-lookup"><span data-stu-id="315e4-255">.NET Standard has been using a `MAJOR.MINOR` versioning scheme.</span></span> <span data-ttu-id="315e4-256">`PATCH` レベルは、.NET Standard では使用できません。これは、あまり頻繁に反復処理されないコントラクトのセットを表し、実際の実装と同じバージョン管理の要件を表さないためです。</span><span class="sxs-lookup"><span data-stu-id="315e4-256">`PATCH` level isn't useful for .NET Standard because it expresses a set of contracts that are iterated on less often and doesn't present the same requirements for versioning as an actual implementation.</span></span>

<span data-ttu-id="315e4-257">.NET Standard バージョンと .NET Core のバージョンの間に実際の結合はありません。 .NET Core 2.0 は .NET Standard 2.0 を実装する場合がありますが、.NET Core の将来のバージョンが同じ .NET Standard のバージョンにマッピングされるという保証はありません。</span><span class="sxs-lookup"><span data-stu-id="315e4-257">There is no real coupling between .NET Standard versions and .NET Core versions: .NET Core 2.0 happens to implement .NET Standard 2.0, but there is no guarantee that future versions of .NET Core will map to the same .NET Standard version.</span></span> <span data-ttu-id="315e4-258">.NET Core は、.NET Standard で定義されていない API を配布することができるので、新しい .NET Standard を必要とせずに新しバージョンを配布する場合があります。</span><span class="sxs-lookup"><span data-stu-id="315e4-258">.NET Core can ship APIs that aren't defined by .NET Standard, and, as such, may ship new versions without requiring a new .NET Standard.</span></span> <span data-ttu-id="315e4-259">.NET Standard は、たとえその始まりが .NET Core と同時に起こったとしても、.NET Framework や Mono などの他のターゲットに適用される概念でもあります。</span><span class="sxs-lookup"><span data-stu-id="315e4-259">.NET Standard is also a concept that applies to other targets, such as .NET Framework or Mono, even if its inception happened to coincide with that of .NET Core.</span></span>

### <a name="packages"></a><span data-ttu-id="315e4-260">パッケージ</span><span class="sxs-lookup"><span data-stu-id="315e4-260">Packages</span></span>

<span data-ttu-id="315e4-261">ライブラリ パッケージは独立して進化し、バージョン管理されます。</span><span class="sxs-lookup"><span data-stu-id="315e4-261">Library packages evolve and version independently.</span></span> <span data-ttu-id="315e4-262">.NET Framework System.\* アセンブリと重複するパッケージは、通常は 4.x バージョンを使用し、.NET Framework 4.x のバージョン管理 (履歴選択) に適合します。</span><span class="sxs-lookup"><span data-stu-id="315e4-262">Packages that overlap with .NET Framework System.\* assemblies typically use 4.x versions, aligning with the .NET Framework 4.x versioning (a historical choice).</span></span> <span data-ttu-id="315e4-263">.NET Framework ライブラリと重複しないパッケージ (たとえば、[`System.Reflection.Metadata`](https://www.nuget.org/packages/System.Reflection.Metadata)) は、通常は 1.0 から開始し、増分していきます。</span><span class="sxs-lookup"><span data-stu-id="315e4-263">Packages that do not overlap with the .NET Framework libraries (for example, [`System.Reflection.Metadata`](https://www.nuget.org/packages/System.Reflection.Metadata)) typically start at 1.0 and increment from there.</span></span>

<span data-ttu-id="315e4-264">[`NETStandard.Library`](https://www.nuget.org/packages/NETStandard.Library) によって記述されるパッケージは、プラットフォームのベースに位置するので、特別に扱われます。</span><span class="sxs-lookup"><span data-stu-id="315e4-264">The packages described by [`NETStandard.Library`](https://www.nuget.org/packages/NETStandard.Library) are treated specially due to being at the base of the platform.</span></span>

<span data-ttu-id="315e4-265">`NETStandard.Library` パッケージは、それらの間に実装レベルの依存関係があるため、通常はセットとしてバージョン管理されます。</span><span class="sxs-lookup"><span data-stu-id="315e4-265">`NETStandard.Library` packages will typically version as a set, since they have implementation-level dependencies between them.</span></span>

### <a name="metapackages"></a><span data-ttu-id="315e4-266">メタパッケージ</span><span class="sxs-lookup"><span data-stu-id="315e4-266">Metapackages</span></span>

<span data-ttu-id="315e4-267">.NET Core メタパッケージのバージョン管理は、それが含まれている .NET Core バージョンに基づいています。</span><span class="sxs-lookup"><span data-stu-id="315e4-267">Versioning for .NET Core metapackages is based on the .NET Core version they are a part of.</span></span>

<span data-ttu-id="315e4-268">たとえば、.NET Core 2.1.3 のメタパッケージの `MAJOR` と `MINOR` のバージョン番号はすべて 2.1 になります。</span><span class="sxs-lookup"><span data-stu-id="315e4-268">For instance, the metapackages in .NET Core 2.1.3 should all have 2.1 as their `MAJOR` and `MINOR` version numbers.</span></span>

<span data-ttu-id="315e4-269">メタパッケージの修正プログラムのバージョンは、参照されるパッケージが更新されるたびに増分されます。</span><span class="sxs-lookup"><span data-stu-id="315e4-269">The patch version for the metapackage is incremented every time any referenced package is updated.</span></span> <span data-ttu-id="315e4-270">修正プログラムのバージョンには、更新されたフレームワークのバージョンは含まれません。</span><span class="sxs-lookup"><span data-stu-id="315e4-270">Patch versions don't include an updated framework version.</span></span> <span data-ttu-id="315e4-271">したがって、メタパッケージは、厳密には SemVer 準拠であると言えません。そのバージョン管理スキームが、基になるパッケージでの変更の度合いを表さず、主に API レベルであるためです。</span><span class="sxs-lookup"><span data-stu-id="315e4-271">As a result, the metapackages aren't strictly SemVer-compliant because their versioning scheme doesn't represent the degree of change in the underlying packages, but primarily of the API level.</span></span>

<span data-ttu-id="315e4-272">.NET Core には、現在、次の 2 の主なメタパッケージがあります。</span><span class="sxs-lookup"><span data-stu-id="315e4-272">There are currently two primary metapackages for .NET Core:</span></span>

<span data-ttu-id="315e4-273">**Microsoft.NETCore.App**</span><span class="sxs-lookup"><span data-stu-id="315e4-273">**Microsoft.NETCore.App**</span></span>

- <span data-ttu-id="315e4-274">.NET Core 1.0 の場合は v1.0 (これらのバージョンは一致します)。</span><span class="sxs-lookup"><span data-stu-id="315e4-274">v1.0 as of .NET Core 1.0 (these versions match).</span></span>
- <span data-ttu-id="315e4-275">`netcoreapp` フレームワークにマップされます。</span><span class="sxs-lookup"><span data-stu-id="315e4-275">Maps to the `netcoreapp` framework.</span></span>
- <span data-ttu-id="315e4-276">.NET Core 配布に含まれるパッケージを記述します。</span><span class="sxs-lookup"><span data-stu-id="315e4-276">Describes the packages in the .NET Core distribution.</span></span>

<span data-ttu-id="315e4-277">注: [ `Microsoft.NETCore.Portable.Compatibility` ](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) は、NET Standard の前の .NET の実装との互換性を可能にするために存在する .NET Core メタパッケージです。</span><span class="sxs-lookup"><span data-stu-id="315e4-277">Note: [`Microsoft.NETCore.Portable.Compatibility`](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) is another .NET Core metapackage that exists to enable compatibility with pre-.NET Standard implementation of .NET.</span></span> <span data-ttu-id="315e4-278">特定のフレームワークにマップされないため、パッケージのようにバージョン管理されます。</span><span class="sxs-lookup"><span data-stu-id="315e4-278">It doesn't map to a particular framework, so it versions like a package.</span></span>

<span data-ttu-id="315e4-279">**NETStandard.Library**</span><span class="sxs-lookup"><span data-stu-id="315e4-279">**NETStandard.Library**</span></span>

<span data-ttu-id="315e4-280">[`NETStandard.Library`](https://www.nuget.org/packages/NETStandard.Library) は [.NET Standard](../../standard/library.md) に含まれるライブラリを記述したものです。</span><span class="sxs-lookup"><span data-stu-id="315e4-280">[`NETStandard.Library`](https://www.nuget.org/packages/NETStandard.Library) describes the libraries that are part of the [.NET Standard](../../standard/library.md).</span></span> <span data-ttu-id="315e4-281">.NET Standard をサポートするすべての .NET 実装 (.NET Framework、.NET Core、Mono など) に適用されます。</span><span class="sxs-lookup"><span data-stu-id="315e4-281">Applies to all .NET implementations that support .NET Standard, such as .NET Framework, .NET Core, and Mono.</span></span>

### <a name="target-frameworks"></a><span data-ttu-id="315e4-282">ターゲット フレームワーク</span><span class="sxs-lookup"><span data-stu-id="315e4-282">Target frameworks</span></span>

<span data-ttu-id="315e4-283">ターゲット フレームワーク バージョンは、新しい API が追加されると更新されます。</span><span class="sxs-lookup"><span data-stu-id="315e4-283">Target framework versions are updated when new APIs are added.</span></span> <span data-ttu-id="315e4-284">これらは API のシェイプを表し、実装には関係しないので、修正プログラム バージョンの概念はありません。</span><span class="sxs-lookup"><span data-stu-id="315e4-284">They have no concept of patch version, since they represent API shape and not implementation concerns.</span></span> <span data-ttu-id="315e4-285">メジャーおよびマイナーのバージョン管理は、前に指定した SemVer 規則に従い、それらを実装する .NET Core ディストリビューションの `MAJOR` および `MINOR` の番号と一致します。</span><span class="sxs-lookup"><span data-stu-id="315e4-285">Major and minor versioning follows the SemVer rules specified earlier, and coincides with the `MAJOR` and `MINOR` numbers of the .NET Core distributions that implement them.</span></span>

## <a name="versioning-in-practice"></a><span data-ttu-id="315e4-286">実際のバージョン管理</span><span class="sxs-lookup"><span data-stu-id="315e4-286">Versioning in practice</span></span>

<span data-ttu-id="315e4-287">.NET Core をダウンロードするときには、たとえば `dotnet-sdk-2.0.4-win10-x64.exe` のように、ダウンロードするファイルの名前にバージョンが指定されます。</span><span class="sxs-lookup"><span data-stu-id="315e4-287">When you download .NET Core, the name of the downloaded file carries the version, for example, `dotnet-sdk-2.0.4-win10-x64.exe`.</span></span>

<span data-ttu-id="315e4-288">GitHub の .NET Core リポジトリでは、コミットおよびプル要求が毎日発生し、多くのライブラリの新しいビルドが生成されます。</span><span class="sxs-lookup"><span data-stu-id="315e4-288">There are commits and pull requests on .NET Core repos on GitHub on a daily basis, resulting in new builds of many libraries.</span></span> <span data-ttu-id="315e4-289">変更が行われるたびに、.NET Core の新しいパブリック バージョンを作成するのは実用的ではありません。</span><span class="sxs-lookup"><span data-stu-id="315e4-289">It isn't practical to create new public versions of .NET Core for every change.</span></span> <span data-ttu-id="315e4-290">代わりに、.NET Core の新しいパブリック安定バージョンを作成する前に、未確定の期間 (たとえば、数週間や数か月) にわたって、変更が集計されます。</span><span class="sxs-lookup"><span data-stu-id="315e4-290">Instead, changes are aggregated over an undetermined period of time (for example, weeks or months) before making a new public stable .NET Core version.</span></span>

<span data-ttu-id="315e4-291">.NET Core の新しいバージョンは、次の複数の意味を持ちます。</span><span class="sxs-lookup"><span data-stu-id="315e4-291">A new version of .NET Core could mean several things:</span></span>

- <span data-ttu-id="315e4-292">パッケージおよびメタパッケージの新しいバージョン。</span><span class="sxs-lookup"><span data-stu-id="315e4-292">New versions of packages and metapackages.</span></span>
- <span data-ttu-id="315e4-293">新しい API の追加を仮定した場合の、さまざまなフレームワークの新しいバージョン。</span><span class="sxs-lookup"><span data-stu-id="315e4-293">New versions of various frameworks, assuming the addition of new APIs.</span></span>
- <span data-ttu-id="315e4-294">.NET Core 配布の新しいバージョン。</span><span class="sxs-lookup"><span data-stu-id="315e4-294">New version of the .NET Core distribution.</span></span>

### <a name="shipping-a-patch-release"></a><span data-ttu-id="315e4-295">修正プログラム リリースの配布</span><span class="sxs-lookup"><span data-stu-id="315e4-295">Shipping a patch release</span></span>

<span data-ttu-id="315e4-296">バージョン 2.0.0 などの .NET Core のメジャー リリースを配布した後は、バグを修正してパフォーマンスと信頼性を高めるために、.NET Core ライブラリに対して修正プログラム レベルの変更が行われます。</span><span class="sxs-lookup"><span data-stu-id="315e4-296">After shipping a major release of .NET Core, such as version 2.0.0, patch-level changes are made to .NET Core libraries to fix bugs and improve performance and reliability.</span></span> <span data-ttu-id="315e4-297">つまり、新しい API は導入されません。</span><span class="sxs-lookup"><span data-stu-id="315e4-297">That means that no new APIs are introduced.</span></span> <span data-ttu-id="315e4-298">更新された .NET Core ライブラリ パッケージを参照するように、さまざまなメタパッケージが更新されます。</span><span class="sxs-lookup"><span data-stu-id="315e4-298">The various metapackages are updated to reference the updated .NET Core library packages.</span></span> <span data-ttu-id="315e4-299">メタパッケージは、修正プログラムの更新 (`MAJOR.MINOR.PATCH`) としてバージョン管理されます。</span><span class="sxs-lookup"><span data-stu-id="315e4-299">The metapackages are versioned as patch updates (`MAJOR.MINOR.PATCH`).</span></span> <span data-ttu-id="315e4-300">ターゲット フレームワークは修正プログラムのリリースの一部として更新されません。</span><span class="sxs-lookup"><span data-stu-id="315e4-300">Target frameworks are never updated as part of patch releases.</span></span> <span data-ttu-id="315e4-301">新しい .NET Core 配布は、`Microsoft.NETCore.App` メタパッケージと一致するバージョン番号でリリースされます。</span><span class="sxs-lookup"><span data-stu-id="315e4-301">A new .NET Core distribution is released with a version number that matches that of the `Microsoft.NETCore.App` metapackage.</span></span>

### <a name="shipping-a-minor-release"></a><span data-ttu-id="315e4-302">マイナー リリースの配布</span><span class="sxs-lookup"><span data-stu-id="315e4-302">Shipping a minor release</span></span>

<span data-ttu-id="315e4-303">増分された `MAJOR` バージョン番号の .NET Core バージョンを配布した後は、新しいシナリオを有効にするために .NET Core ライブラリに新しい API が追加されます。</span><span class="sxs-lookup"><span data-stu-id="315e4-303">After shipping a .NET Core version with an incremented `MAJOR` version number, new APIs are added to .NET Core libraries to enable new scenarios.</span></span> <span data-ttu-id="315e4-304">更新された .NET Core ライブラリ パッケージを参照するように、さまざまなメタパッケージが更新されます。</span><span class="sxs-lookup"><span data-stu-id="315e4-304">The various metapackages are updated to reference the updated .NET Core library packages.</span></span> <span data-ttu-id="315e4-305">メタパッケージは、新しいフレームワークのバージョンと一致する `MAJOR` および `MINOR` のバージョン番号で、修正プログラムの更新としてバージョン管理されます。</span><span class="sxs-lookup"><span data-stu-id="315e4-305">The metapackages are versioned as patch updates with `MAJOR` and `MINOR` version numbers matching the new framework version.</span></span> <span data-ttu-id="315e4-306">新しい `MAJOR.MINOR` バージョンの新しいターゲット フレームワーク名 (たとえば、`netcoreapp2.1`) が、新しい API を記述するために追加されます。</span><span class="sxs-lookup"><span data-stu-id="315e4-306">New target framework names with the new `MAJOR.MINOR` version are added to describe the new APIs (for example, `netcoreapp2.1`).</span></span> <span data-ttu-id="315e4-307">新しい .NET Core 配布は、`Microsoft.NETCore.App` メタパッケージと一致するバージョン番号でリリースされます。</span><span class="sxs-lookup"><span data-stu-id="315e4-307">A new .NET Core distribution is released with a matching version number to the `Microsoft.NETCore.App` metapackage.</span></span>

### <a name="shipping-a-major-release"></a><span data-ttu-id="315e4-308">メジャー リリースの配布</span><span class="sxs-lookup"><span data-stu-id="315e4-308">Shipping a major release</span></span>

<span data-ttu-id="315e4-309">.NET Core の新しいメジャー バージョンが配布されるたびに、`MAJOR` バージョン番号が増分され、`MINOR` バージョン番号が 0 にリセットされます。</span><span class="sxs-lookup"><span data-stu-id="315e4-309">Every time a new major version of .NET Core ships, the `MAJOR` version number gets incremented, and the `MINOR` version number gets reset to zero.</span></span> <span data-ttu-id="315e4-310">新しいメジャー バージョンには、少なくとも前のメジャー バージョン以降にマイナー リリースで追加されたすべての API が含まれています。</span><span class="sxs-lookup"><span data-stu-id="315e4-310">The new major version contains at least all the APIs that were added by minor releases after the previous major version.</span></span> <span data-ttu-id="315e4-311">新しいメジャー バージョンは重要な新しいシナリオを有効にする必要があり、また古いプラットフォームのサポートを終了する場合があります。</span><span class="sxs-lookup"><span data-stu-id="315e4-311">A new major version should enable important new scenarios, and it may also drop support for an older platform.</span></span>

<span data-ttu-id="315e4-312">更新された .NET Core ライブラリ パッケージを参照するように、さまざまなメタパッケージが更新されます。</span><span class="sxs-lookup"><span data-stu-id="315e4-312">The various metapackages are updated to reference the updated .NET Core library packages.</span></span> <span data-ttu-id="315e4-313">[ `Microsoft.NETCore.App` ](https://www.nuget.org/packages/Microsoft.NETCore.App) メタパッケージおよび `netcore` ターゲット フレームワークは、新しいリリースの `MAJOR` バージョン番号と一致するメジャー更新プログラムとしてバージョン管理されます。</span><span class="sxs-lookup"><span data-stu-id="315e4-313">The [`Microsoft.NETCore.App`](https://www.nuget.org/packages/Microsoft.NETCore.App) metapackage and the `netcore` target framework are versioned as a major update matching the `MAJOR` version number of the new release.</span></span>

## <a name="see-also"></a><span data-ttu-id="315e4-314">関連項目</span><span class="sxs-lookup"><span data-stu-id="315e4-314">See also</span></span>

[<span data-ttu-id="315e4-315">ターゲット フレームワーク</span><span class="sxs-lookup"><span data-stu-id="315e4-315">Target frameworks</span></span>](../../standard/frameworks.md)  
[<span data-ttu-id="315e4-316">.NET Core の配布パッケージ</span><span class="sxs-lookup"><span data-stu-id="315e4-316">.NET Core distribution packaging</span></span>](../build/distribution-packaging.md)  
[<span data-ttu-id="315e4-317">.NET Core サポート ライフサイクルのファクト シート</span><span class="sxs-lookup"><span data-stu-id="315e4-317">.NET Core Support Lifecycle Fact Sheet</span></span>](https://www.microsoft.com/net/core/support)  
[<span data-ttu-id="315e4-318">.NET core 2 + バージョン バインディング</span><span class="sxs-lookup"><span data-stu-id="315e4-318">.NET Core 2+ Version Binding</span></span>](https://github.com/dotnet/designs/issues/3)  
