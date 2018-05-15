---
title: .NET Core のランタイム識別子 (RID) のカタログ
description: ランタイム識別子 (RID) と .NET Core での RID の使用方法について説明します。
author: mairaw
ms.author: mairaw
ms.date: 09/07/2017
ms.openlocfilehash: 81f9e5f65385bbd81c7fdae7f75c62d11b6f6319
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="net-core-rid-catalog"></a><span data-ttu-id="d2c75-103">.NET Core の RID カタログ</span><span class="sxs-lookup"><span data-stu-id="d2c75-103">.NET Core RID Catalog</span></span>

<span data-ttu-id="d2c75-104">RID は*ランタイム識別子*の略です。</span><span class="sxs-lookup"><span data-stu-id="d2c75-104">RID is short for *Runtime IDentifier*.</span></span> <span data-ttu-id="d2c75-105">RID の値は、アプリケーションが実行されている対象プラットフォームの識別に使用されます。</span><span class="sxs-lookup"><span data-stu-id="d2c75-105">RID values are used to identify target platforms where the application runs.</span></span>
<span data-ttu-id="d2c75-106">これは NuGet パッケージのプラットフォーム固有のアセットを表すために、.NET パッケージによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="d2c75-106">They're used by .NET packages to represent platform-specific assets in NuGet packages.</span></span> <span data-ttu-id="d2c75-107">RID は、たとえば `linux-x64`、`ubuntu.14.04-x64`、`win7-x64`、または `osx.10.12-x64` などの値です。</span><span class="sxs-lookup"><span data-stu-id="d2c75-107">The following values are examples of RIDs: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, or `osx.10.12-x64`.</span></span>
<span data-ttu-id="d2c75-108">ネイティブ依存関係のあるパッケージの場合、パッケージを復元できるプラットフォームが RID によって指定されます。</span><span class="sxs-lookup"><span data-stu-id="d2c75-108">For the packages with native dependencies, the RID designates on which platforms the package can be restored.</span></span>

<span data-ttu-id="d2c75-109">プロジェクト ファイルの `<RuntimeIdentifier>` 要素では、1 つの RID を設定できます。</span><span class="sxs-lookup"><span data-stu-id="d2c75-109">A single RID can be set in the `<RuntimeIdentifier>` element of your project file.</span></span> <span data-ttu-id="d2c75-110">複数の RID は、プロジェクト ファイルの `<RuntimeIdentifiers>` 要素でセミコロン区切りのリストとして定義できます。</span><span class="sxs-lookup"><span data-stu-id="d2c75-110">Multiple RIDs can be defined as a semicolon-delimited list in the project file's `<RuntimeIdentifiers>` element.</span></span> <span data-ttu-id="d2c75-111">以下の [.NET Core CLI コマンド](./tools/index.md)の `--runtime` オプションで使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="d2c75-111">They're also used via the `--runtime` option with the following [.NET Core CLI commands](./tools/index.md):</span></span>

- [<span data-ttu-id="d2c75-112">dotnet build</span><span class="sxs-lookup"><span data-stu-id="d2c75-112">dotnet build</span></span>](./tools/dotnet-build.md)
- [<span data-ttu-id="d2c75-113">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="d2c75-113">dotnet clean</span></span>](./tools/dotnet-clean.md)
- [<span data-ttu-id="d2c75-114">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="d2c75-114">dotnet pack</span></span>](./tools/dotnet-pack.md)
- [<span data-ttu-id="d2c75-115">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="d2c75-115">dotnet publish</span></span>](./tools/dotnet-publish.md)
- [<span data-ttu-id="d2c75-116">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="d2c75-116">dotnet restore</span></span>](./tools/dotnet-restore.md)
- [<span data-ttu-id="d2c75-117">dotnet run</span><span class="sxs-lookup"><span data-stu-id="d2c75-117">dotnet run</span></span>](./tools/dotnet-run.md)
- [<span data-ttu-id="d2c75-118">dotnet store</span><span class="sxs-lookup"><span data-stu-id="d2c75-118">dotnet store</span></span>](./tools/dotnet-store.md)

<span data-ttu-id="d2c75-119">具体的なオペレーティング システムを表す RID は通常、`[os].[version]-[architecture]-[additional qualifiers]` のようなパターンになります。それぞれ、次のような意味があります。</span><span class="sxs-lookup"><span data-stu-id="d2c75-119">RIDs that represent concrete operating systems usually follow this pattern: `[os].[version]-[architecture]-[additional qualifiers]` where:</span></span>

- <span data-ttu-id="d2c75-120">`[os]` はオペレーティング システムまたはプラットフォーム システムのモニカーです。</span><span class="sxs-lookup"><span data-stu-id="d2c75-120">`[os]` is the operating/platform system moniker.</span></span> <span data-ttu-id="d2c75-121">たとえば、`ubuntu` のようにします。</span><span class="sxs-lookup"><span data-stu-id="d2c75-121">For example, `ubuntu`.</span></span>

- <span data-ttu-id="d2c75-122">`[version]` は、オペレーティング システムのバージョンをドット区切りの形式 (`.`) で表したバージョン番号です。</span><span class="sxs-lookup"><span data-stu-id="d2c75-122">`[version]` is the operating system version in the form of a dot-separated (`.`) version number.</span></span> <span data-ttu-id="d2c75-123">たとえば、`15.10` のようにします。</span><span class="sxs-lookup"><span data-stu-id="d2c75-123">For example, `15.10`.</span></span>

  - <span data-ttu-id="d2c75-124">バージョンはマーケティング バージョンに**しないでください**。プラットフォームの API アクセス領域が異なる、オペレーティング システムの複数の別々のバージョンを表すことがあるためです。</span><span class="sxs-lookup"><span data-stu-id="d2c75-124">The version **shouldn't** be marketing versions, as they often represent multiple discrete versions of the operating system with varying platform API surface area.</span></span>

- <span data-ttu-id="d2c75-125">`[architecture]` はプロセッサ アーキテクチャです。</span><span class="sxs-lookup"><span data-stu-id="d2c75-125">`[architecture]` is the processor architecture.</span></span> <span data-ttu-id="d2c75-126">たとえば `x86`、`x64`、`arm` または `arm64` などです。</span><span class="sxs-lookup"><span data-stu-id="d2c75-126">For example: `x86`, `x64`, `arm`, or `arm64`.</span></span>

- <span data-ttu-id="d2c75-127">`[additional qualifiers]` はさまざまなプラットフォームをさらに区別します。</span><span class="sxs-lookup"><span data-stu-id="d2c75-127">`[additional qualifiers]` further differentiate different platforms.</span></span> <span data-ttu-id="d2c75-128">例 : `aot` または `corert`。</span><span class="sxs-lookup"><span data-stu-id="d2c75-128">For example: `aot` or `corert`.</span></span>

## <a name="rid-graph"></a><span data-ttu-id="d2c75-129">RID グラフ</span><span class="sxs-lookup"><span data-stu-id="d2c75-129">RID graph</span></span>

<span data-ttu-id="d2c75-130">RID グラフまたはランタイム フォールバック グラフとは、相互に互換性のある RID の一覧です。</span><span class="sxs-lookup"><span data-stu-id="d2c75-130">The RID graph or runtime fallback graph is a list of RIDs that are compatible with each other.</span></span> <span data-ttu-id="d2c75-131">RID は [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) パッケージで定義されています。</span><span class="sxs-lookup"><span data-stu-id="d2c75-131">The RIDs are defined in the [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) package.</span></span> <span data-ttu-id="d2c75-132">サポートされている RID および RID グラフの一覧は、CoreFX リポジトリにある [*runtime.json*](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) ファイルで確認できます。</span><span class="sxs-lookup"><span data-stu-id="d2c75-132">You can see the list of supported RIDs and the RID graph in the [*runtime.json*](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) file, which is located at the CoreFX repo.</span></span> <span data-ttu-id="d2c75-133">このファイルでは、基本となる RID を除くすべての RID に `"#import"` ステートメントが記述されていることを確認できます。</span><span class="sxs-lookup"><span data-stu-id="d2c75-133">In this file, you can see that all RIDs, except for the base one, contain an `"#import"` statement.</span></span> <span data-ttu-id="d2c75-134">このステートメントは互換性のある RID を示しています。</span><span class="sxs-lookup"><span data-stu-id="d2c75-134">These statements indicate compatible RIDs.</span></span>

<span data-ttu-id="d2c75-135">NuGet はパッケージを復元する際、指定されたランタイムと正確に一致するものを見つけようとします。</span><span class="sxs-lookup"><span data-stu-id="d2c75-135">When NuGet restores packages, it tries to find an exact match for the specified runtime.</span></span>
<span data-ttu-id="d2c75-136">正確に一致するものが見つからない場合、NuGet は、RID グラフに基づいて最も互換性のあるシステムが見つかるまでグラフを遡ります。</span><span class="sxs-lookup"><span data-stu-id="d2c75-136">If an exact match is not found, NuGet walks back the graph until it finds the closest compatible system according to the RID graph.</span></span>

<span data-ttu-id="d2c75-137">次に示す例は、`osx.10.12-x64` の RID として実際に記述されているものです。</span><span class="sxs-lookup"><span data-stu-id="d2c75-137">The following example is the actual entry for the `osx.10.12-x64` RID:</span></span>

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

<span data-ttu-id="d2c75-138">上の RID は `osx.10.12-x64` が `osx.10.11-x64` をインポートすることを指定します。</span><span class="sxs-lookup"><span data-stu-id="d2c75-138">The above RID specifies that `osx.10.12-x64` imports `osx.10.11-x64`.</span></span> <span data-ttu-id="d2c75-139">そのため、NuGet はパッケージを復元する際、`osx.10.12-x64` と正確に一致するものをパッケージから見つけようとします。</span><span class="sxs-lookup"><span data-stu-id="d2c75-139">So, when NuGet restores packages, it tries to find an exact match for  `osx.10.12-x64` in the package.</span></span> <span data-ttu-id="d2c75-140">特定のランタイムが見つからなかった場合、NuGet は、たとえば `osx.10.11-x64` ランタイムを指定しているパッケージを復元できます。</span><span class="sxs-lookup"><span data-stu-id="d2c75-140">If NuGet cannot find the specific runtime, it can restore packages that specify `osx.10.11-x64` runtimes, for example.</span></span>

<span data-ttu-id="d2c75-141">次の例は、*runtime.json* ファイルにも定義されている少し大きめの RID グラフです。</span><span class="sxs-lookup"><span data-stu-id="d2c75-141">The following example shows a slightly bigger RID graph also defined in the *runtime.json*  file:</span></span>

```
    win7-x64    win7-x86
       |   \   /    |
       |   win7     |
       |     |      |
    win-x64  |  win-x86
          \  |  /
            win
             |
            any
```

<span data-ttu-id="d2c75-142">すべての RID は最終的にルート `any` RID にマッピングされます。</span><span class="sxs-lookup"><span data-stu-id="d2c75-142">All RIDs eventually map back to the root `any` RID.</span></span>

<span data-ttu-id="d2c75-143">RID を使用する際に留意しておく必要のある注意事項があります。</span><span class="sxs-lookup"><span data-stu-id="d2c75-143">There are some considerations about RIDs that you have to keep in mind when working with them:</span></span>

- <span data-ttu-id="d2c75-144">RID は**不透明な文字列**であり、ブラック ボックスとして処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2c75-144">RIDs are **opaque strings** and should be treated as black boxes.</span></span>
- <span data-ttu-id="d2c75-145">RID をプログラムによって作成しないでください。</span><span class="sxs-lookup"><span data-stu-id="d2c75-145">Don't build RIDs programmatically.</span></span>
- <span data-ttu-id="d2c75-146">プラットフォームであらかじめ定義されている RID を使用します。</span><span class="sxs-lookup"><span data-stu-id="d2c75-146">Use RIDs that are already defined for the platform.</span></span>
- <span data-ttu-id="d2c75-147">RID は特定の値である必要があるため、実際の値から推測した値にしないでください。</span><span class="sxs-lookup"><span data-stu-id="d2c75-147">The RIDs need to be specific, so don't assume anything from the actual RID value.</span></span>

## <a name="using-rids"></a><span data-ttu-id="d2c75-148">RID の使用</span><span class="sxs-lookup"><span data-stu-id="d2c75-148">Using RIDs</span></span>

<span data-ttu-id="d2c75-149">RID を使用するには、どのような RID があるのか知る必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2c75-149">To be able to use RIDs, you have to know which RIDs exist.</span></span> <span data-ttu-id="d2c75-150">プラットフォームには新しい RID が定期的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="d2c75-150">New values are added regularly to the platform.</span></span>
<span data-ttu-id="d2c75-151">最新の完全バージョンについては、CoreFX リポジトリの [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) ファイルをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d2c75-151">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) file on CoreFX repo.</span></span>

<span data-ttu-id="d2c75-152">.NET Core 2.0 SDK には、ポータブル RID の概念が導入されています。</span><span class="sxs-lookup"><span data-stu-id="d2c75-152">.NET Core 2.0 SDK introduces the concept of portable RIDs.</span></span> <span data-ttu-id="d2c75-153">これは、RID グラフに新しく追加された値であり、特定のバージョンや OS のディストリビューションに関連付けられていません。</span><span class="sxs-lookup"><span data-stu-id="d2c75-153">They are new values added to the RID graph that aren't tied to a specific version or OS distribution.</span></span> <span data-ttu-id="d2c75-154">特に、複数の Linux ディストリビューションを扱うときに便利です。</span><span class="sxs-lookup"><span data-stu-id="d2c75-154">They're particularly useful when dealing with multiple Linux distros.</span></span>

<span data-ttu-id="d2c75-155">次の一覧に、各 OS に使用される最も一般的な RID を示します。</span><span class="sxs-lookup"><span data-stu-id="d2c75-155">The following list shows the most common RIDs used for each OS.</span></span> <span data-ttu-id="d2c75-156">`arm` と `corert` の値は対象外です。</span><span class="sxs-lookup"><span data-stu-id="d2c75-156">It doesn't cover `arm` or `corert` values.</span></span>

## <a name="windows-rids"></a><span data-ttu-id="d2c75-157">Windows RID</span><span class="sxs-lookup"><span data-stu-id="d2c75-157">Windows RIDs</span></span>

- <span data-ttu-id="d2c75-158">ポータブル</span><span class="sxs-lookup"><span data-stu-id="d2c75-158">Portable</span></span>
  - `win-x86`
  - `win-x64`
- <span data-ttu-id="d2c75-159">Windows 7 / Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="d2c75-159">Windows 7 / Windows Server 2008 R2</span></span>
  - `win7-x64`
  - `win7-x86`
- <span data-ttu-id="d2c75-160">Windows 8 / Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="d2c75-160">Windows 8 / Windows Server 2012</span></span>
  - `win8-x64`
  - `win8-x86`
  - `win8-arm`
- <span data-ttu-id="d2c75-161">Windows 8.1 / Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="d2c75-161">Windows 8.1 / Windows Server 2012 R2</span></span>
  - `win81-x64`
  - `win81-x86`
  - `win81-arm`
- <span data-ttu-id="d2c75-162">Windows 10 / Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="d2c75-162">Windows 10 / Windows Server 2016</span></span>
  - `win10-x64`
  - `win10-x86`
  - `win10-arm`
  - `win10-arm64`

<span data-ttu-id="d2c75-163">詳細については、「[Windows における .NET Core の前提条件](windows-prerequisites.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2c75-163">See [Prerequisites for .NET Core on Windows](windows-prerequisites.md) for more information.</span></span>

## <a name="linux-rids"></a><span data-ttu-id="d2c75-164">Linux RID</span><span class="sxs-lookup"><span data-stu-id="d2c75-164">Linux RIDs</span></span>

- <span data-ttu-id="d2c75-165">ポータブル</span><span class="sxs-lookup"><span data-stu-id="d2c75-165">Portable</span></span>
  - `linux-x64`
- <span data-ttu-id="d2c75-166">CentOS</span><span class="sxs-lookup"><span data-stu-id="d2c75-166">CentOS</span></span>
  - `centos-x64`
  - `centos.7-x64`
- <span data-ttu-id="d2c75-167">Debian</span><span class="sxs-lookup"><span data-stu-id="d2c75-167">Debian</span></span>
  - `debian-x64`
  - `debian.8-x64`
- <span data-ttu-id="d2c75-168">Fedora</span><span class="sxs-lookup"><span data-stu-id="d2c75-168">Fedora</span></span>
  - `fedora-x64`
  - `fedora.24-x64`
  - <span data-ttu-id="d2c75-169">`fedora.25-x64` (.NET Core 2.0 以降)</span><span class="sxs-lookup"><span data-stu-id="d2c75-169">`fedora.25-x64` (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="d2c75-170">`fedora.26-x64` (.NET Core 2.0 以降)</span><span class="sxs-lookup"><span data-stu-id="d2c75-170">`fedora.26-x64` (.NET Core 2.0 or later versions)</span></span>
- <span data-ttu-id="d2c75-171">Gentoo (.NET Core 2.0 以降)</span><span class="sxs-lookup"><span data-stu-id="d2c75-171">Gentoo (.NET Core 2.0 or later versions)</span></span>
  - `gentoo-x64`
- <span data-ttu-id="d2c75-172">openSUSE</span><span class="sxs-lookup"><span data-stu-id="d2c75-172">openSUSE</span></span>
  - `opensuse-x64`
  - `opensuse.42.1-x64`
- <span data-ttu-id="d2c75-173">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="d2c75-173">Oracle Linux</span></span>
  - `ol-x64`
  - `ol.7-x64`
  - `ol.7.0-x64`
  - `ol.7.1-x64`
  - `ol.7.2-x64`
- <span data-ttu-id="d2c75-174">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="d2c75-174">Red Hat Enterprise Linux</span></span>
  - `rhel-x64`
  - <span data-ttu-id="d2c75-175">`rhel.6-x64` (.NET Core 2.0 以降)</span><span class="sxs-lookup"><span data-stu-id="d2c75-175">`rhel.6-x64` (.NET Core 2.0 or later versions)</span></span>
  - `rhel.7-x64`
  - `rhel.7.1-x64`
  - `rhel.7.2-x64`
  - <span data-ttu-id="d2c75-176">`rhel.7.3-x64` (.NET Core 2.0 以降)</span><span class="sxs-lookup"><span data-stu-id="d2c75-176">`rhel.7.3-x64` (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="d2c75-177">`rhel.7.4-x64` (.NET Core 2.0 以降)</span><span class="sxs-lookup"><span data-stu-id="d2c75-177">`rhel.7.4-x64` (.NET Core 2.0 or later versions)</span></span>
- <span data-ttu-id="d2c75-178">Tizen (.NET Core 2.0 以降)</span><span class="sxs-lookup"><span data-stu-id="d2c75-178">Tizen (.NET Core 2.0 or later versions)</span></span>
  - `tizen`
- <span data-ttu-id="d2c75-179">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="d2c75-179">Ubuntu</span></span>
  - `ubuntu-x64`
  - `ubuntu.14.04-x64`
  - `ubuntu.14.10-x64`
  - `ubuntu.15.04-x64`
  - `ubuntu.15.10-x64`
  - `ubuntu.16.04-x64`
  - `ubuntu.16.10-x64`
- <span data-ttu-id="d2c75-180">Ubuntu の派生ディストリビューション</span><span class="sxs-lookup"><span data-stu-id="d2c75-180">Ubuntu derivatives</span></span>
  - `linuxmint.17-x64`
  - `linuxmint.17.1-x64`
  - `linuxmint.17.2-x64`
  - `linuxmint.17.3-x64`
  - `linuxmint.18-x64`
  - <span data-ttu-id="d2c75-181">`linuxmint.18.1-x64` (.NET Core 2.0 以降)</span><span class="sxs-lookup"><span data-stu-id="d2c75-181">`linuxmint.18.1-x64` (.NET Core 2.0 or later versions)</span></span>

<span data-ttu-id="d2c75-182">詳細については、「[Linux における .NET Core の前提条件](linux-prerequisites.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2c75-182">See [Prerequisites for .NET Core on Linux](linux-prerequisites.md) for more information.</span></span>

## <a name="macos-rids"></a><span data-ttu-id="d2c75-183">macOS RID</span><span class="sxs-lookup"><span data-stu-id="d2c75-183">macOS RIDs</span></span>

<span data-ttu-id="d2c75-184">macOS RID では、以前の "OSX" ブランドが使用されています。</span><span class="sxs-lookup"><span data-stu-id="d2c75-184">macOS RIDs use the older "OSX" branding.</span></span>

- <span data-ttu-id="d2c75-185">`osx-x64` (.NET Core 2.0 以降のバージョン、最小バージョンは `osx.10.12-x64`)</span><span class="sxs-lookup"><span data-stu-id="d2c75-185">`osx-x64` (.NET Core 2.0 or later versions, minimum version is `osx.10.12-x64`)</span></span>
- `osx.10.10-x64`
- `osx.10.11-x64`
- <span data-ttu-id="d2c75-186">`osx.10.12-x64` (.NET Core 1.1 以降)</span><span class="sxs-lookup"><span data-stu-id="d2c75-186">`osx.10.12-x64` (.NET Core 1.1 or later versions)</span></span>
- `osx.10.13-x64`

<span data-ttu-id="d2c75-187">詳細については、「[macOS における .NET Core の前提条件](macos-prerequisites.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2c75-187">See [Prerequisites for .NET Core on macOS](macos-prerequisites.md) for more information.</span></span>

## <a name="android-rids-net-core-20-or-later-versions"></a><span data-ttu-id="d2c75-188">Android RID (.NET Core 2.0 以降)</span><span class="sxs-lookup"><span data-stu-id="d2c75-188">Android RIDs (.NET Core 2.0 or later versions)</span></span>

- `android`
- `android.21`

## <a name="see-also"></a><span data-ttu-id="d2c75-189">関連項目</span><span class="sxs-lookup"><span data-stu-id="d2c75-189">See also</span></span>

[<span data-ttu-id="d2c75-190">ランタイム ID</span><span class="sxs-lookup"><span data-stu-id="d2c75-190">Runtime IDs</span></span>](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/readme.md)
