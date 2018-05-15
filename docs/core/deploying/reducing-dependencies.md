---
title: project.json によるパッケージ依存関係の縮小
description: project.json ベースのライブラリ作成時にパッケージの依存関係を減らします。
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.openlocfilehash: ae314800f789cee363728def8347b5e6990acb0b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="reducing-package-dependencies-with-projectjson"></a><span data-ttu-id="09e88-103">project.json によるパッケージ依存関係の縮小</span><span class="sxs-lookup"><span data-stu-id="09e88-103">Reducing Package Dependencies with project.json</span></span>

<span data-ttu-id="09e88-104">この記事では、`project.json` ライブラリの作成時にパッケージ依存関係を減らすために知っておくべきことについて紹介します。</span><span class="sxs-lookup"><span data-stu-id="09e88-104">This article covers what you need to know about reducing your package dependencies when authoring `project.json` libraries.</span></span> <span data-ttu-id="09e88-105">この記事を最後までお読みいただくと、必要な依存関係だけが使用されるようにライブラリを構築する方法を理解できます。</span><span class="sxs-lookup"><span data-stu-id="09e88-105">By the end of this article, you will learn how to compose your library such that it only uses the dependencies it needs.</span></span> 

## <a name="why-its-important"></a><span data-ttu-id="09e88-106">これが重要な理由</span><span class="sxs-lookup"><span data-stu-id="09e88-106">Why it's Important</span></span>

<span data-ttu-id="09e88-107">.NET Core は NuGet パッケージで構成される製品です。</span><span class="sxs-lookup"><span data-stu-id="09e88-107">.NET Core is a product made up of NuGet packages.</span></span>  <span data-ttu-id="09e88-108">必要不可欠なパッケージが [.NETStandard.Library メタパッケージ](https://www.nuget.org/packages/NETStandard.Library)です。これは他のパッケージから構成される NuGet パッケージです。</span><span class="sxs-lookup"><span data-stu-id="09e88-108">An essential package is the [.NETStandard.Library metapackage](https://www.nuget.org/packages/NETStandard.Library), which is a NuGet package composed of other packages.</span></span>  <span data-ttu-id="09e88-109">一連のパッケージが提供されますが、それらは .NET Framework、.NET Core、Xamarin/Mono など、複数の .NET 実装で動作することが確認されています。</span><span class="sxs-lookup"><span data-stu-id="09e88-109">It provides you with the set of packages that are guaranteed to work on multiple .NET implementations, such as .NET Framework, .NET Core and Xamarin/Mono.</span></span>

<span data-ttu-id="09e88-110">しかしながら、お使いのライブラリではすべてのパッケージが使用されるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="09e88-110">However, there's a good chance that your library won't use every single package it contains.</span></span>  <span data-ttu-id="09e88-111">ライブラリを作成し、NuGet 経由で配信するときは、実際に使用するパッケージにのみ依存関係を "減らす" ことが推奨されます。</span><span class="sxs-lookup"><span data-stu-id="09e88-111">When authoring a library and distributing it over NuGet, it's a best practice to "trim" your dependencies down to only the packages you actually use.</span></span>  <span data-ttu-id="09e88-112">結果的に、NuGet パッケージの全体的フットプリントが少なくなります。</span><span class="sxs-lookup"><span data-stu-id="09e88-112">This results in a smaller overall footprint for NuGet packages.</span></span>

## <a name="how-to-do-it"></a><span data-ttu-id="09e88-113">その方法</span><span class="sxs-lookup"><span data-stu-id="09e88-113">How to do it</span></span>

<span data-ttu-id="09e88-114">現在のところ、パッケージ参照を減らす正式な `dotnet` コマンドはありません。</span><span class="sxs-lookup"><span data-stu-id="09e88-114">Currently, there is no official `dotnet` command which trims package references.</span></span>  <span data-ttu-id="09e88-115">代わりに、手動で行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="09e88-115">Instead, you'll have to do it manually.</span></span>  <span data-ttu-id="09e88-116">一般的なプロセスは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="09e88-116">The general process looks like the following:</span></span>

1. <span data-ttu-id="09e88-117">お使いの `project.json` の `dependencies` セクションにある `NETStandard.Library` バージョン `1.6.0` を参照します。</span><span class="sxs-lookup"><span data-stu-id="09e88-117">Reference `NETStandard.Library` version `1.6.0` in a `dependencies` section of your `project.json`.</span></span>
2. <span data-ttu-id="09e88-118">コマンド ラインから `dotnet restore` でパッケージを復元します ([注記参照](#dotnet-restore-note))。</span><span class="sxs-lookup"><span data-stu-id="09e88-118">Restore packages with `dotnet restore` ([see note](#dotnet-restore-note)) from the command line.</span></span>
3. <span data-ttu-id="09e88-119">`project.lock.json` ファイルを調べ、`NETSTandard.Library` というセクションを探します。</span><span class="sxs-lookup"><span data-stu-id="09e88-119">Inspect the `project.lock.json` file and find the `NETSTandard.Library` section.</span></span>  <span data-ttu-id="09e88-120">ファイルの始まりの近くにあります。</span><span class="sxs-lookup"><span data-stu-id="09e88-120">It's near the beginning of the file.</span></span>
4. <span data-ttu-id="09e88-121">`dependencies` の下にあるパッケージをすべてコピーします。</span><span class="sxs-lookup"><span data-stu-id="09e88-121">Copy all of the listed packages under `dependencies`.</span></span>
5. <span data-ttu-id="09e88-122">`.NETStandard.Library` 参照を削除し、コピーしたパッケージで置き換えます。</span><span class="sxs-lookup"><span data-stu-id="09e88-122">Remove the `.NETStandard.Library` reference and replace it with the copied packages.</span></span>
6. <span data-ttu-id="09e88-123">不要なパッケージ参照を削除します。</span><span class="sxs-lookup"><span data-stu-id="09e88-123">Remove references to packages you don't need.</span></span>


<span data-ttu-id="09e88-124">不要なパッケージは次の方法で確認できます。</span><span class="sxs-lookup"><span data-stu-id="09e88-124">You can find out which packages you don't need by one of the following ways:</span></span>

1. <span data-ttu-id="09e88-125">試用とエラー。</span><span class="sxs-lookup"><span data-stu-id="09e88-125">Trial and error.</span></span>  <span data-ttu-id="09e88-126">パッケージを削除したり、復元したり、ライブラリがまだコンパイルするか確認したり、このプロセスを繰り返したりなどの操作が含まれます。</span><span class="sxs-lookup"><span data-stu-id="09e88-126">This involves removing a package, restoring, seeing if your library still compiles, and repeating this process.</span></span>
2. <span data-ttu-id="09e88-127">[ILSpy](http://ilspy.net) や [.NET Reflector](http://www.red-gate.com/products/dotnet-development/reflector) などのツールを利用し、コードで実際に利用されている参照を確認します。</span><span class="sxs-lookup"><span data-stu-id="09e88-127">Using a tool such as [ILSpy](http://ilspy.net) or [.NET Reflector](http://www.red-gate.com/products/dotnet-development/reflector) to peek at references to see what your code is actually using.</span></span>  <span data-ttu-id="09e88-128">その後、利用している種類に該当しないパッケージを削除できます。</span><span class="sxs-lookup"><span data-stu-id="09e88-128">You can then remove packages which don't correspond to types you're using.</span></span>

## <a name="example"></a><span data-ttu-id="09e88-129">例</span><span class="sxs-lookup"><span data-stu-id="09e88-129">Example</span></span> 

<span data-ttu-id="09e88-130">追加機能を汎用コレクション タイプに提供するライブラリを記述したとします。</span><span class="sxs-lookup"><span data-stu-id="09e88-130">Imagine that you wrote a library which provided additional functionality to generic collection types.</span></span>  <span data-ttu-id="09e88-131">そのようなライブラリは `System.Collections` のようなパッケージに依存しなければなりませんが、`System.Net.Http` のようなパッケージにはまったく依存しないことがあります。</span><span class="sxs-lookup"><span data-stu-id="09e88-131">Such a library would need to depend on packages such as `System.Collections`, but may not at all depend on packages such as `System.Net.Http`.</span></span>  <span data-ttu-id="09e88-132">そのため、このライブラリが必要とするものだけにパッケージ依存関係を減らすと効果的です。</span><span class="sxs-lookup"><span data-stu-id="09e88-132">As such, it would be good to trim package dependencies down to only what this library required!</span></span>

<span data-ttu-id="09e88-133">このライブラリから余計なものを減らすには、最初に `project.json` ファイルから始め、`NETStandard.Library` バージョン `1.6.0` の参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="09e88-133">To trim this library, you start with the `project.json` file and add a reference to `NETStandard.Library` version `1.6.0`.</span></span>

```json
{
    "version":"1.0.0",
    "dependencies":{
        "NETStandard.Library":"1.6.0"
    },
    "frameworks": {
        "netstandard1.0": {}
     }
}
```

<span data-ttu-id="09e88-134">次に、`dotnet restore` でパッケージを復元し ([注記参照](#dotnet-restore-note))、`project.lock.json` ファイルを調べ、`NETSTandard.Library` に対して復元されたすべてのパッケージを探します。</span><span class="sxs-lookup"><span data-stu-id="09e88-134">Next, you restore packages with `dotnet restore` ([see note](#dotnet-restore-note)), inspect the `project.lock.json` file, and find all the packages restored for `NETSTandard.Library`.</span></span>

<span data-ttu-id="09e88-135">`netstandard1.0` をターゲットにするとき、`project.lock.json` ファイルの関連セクションは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="09e88-135">Here's what the relevant section in the `project.lock.json` file looks like when targeting `netstandard1.0`:</span></span>

```json
"NETStandard.Library/1.6.0":{
    "type": "package",
    "dependencies": {
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Diagnostics.Debug": "4.0.11",
        "System.Diagnostics.Tools": "4.0.1",
        "System.Globalization": "4.0.11",
        "System.IO": "4.1.0",
        "System.Linq": "4.1.0",
        "System.Net.Primitives": "4.0.11",
        "System.ObjectModel": "4.0.12",
        "System.Reflection": "4.1.0",
        "System.Reflection.Extensions": "4.0.1",
        "System.Reflection.Primitives": "4.0.1",
        "System.Resources.ResourceManager": "4.0.1",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Text.Encoding": "4.0.11",
        "System.Text.Encoding.Extensions": "4.0.11",
        "System.Text.RegularExpressions": "4.1.0",
        "System.Threading": "4.0.11",
        "System.Threading.Tasks": "4.0.11",
        "System.Xml.ReaderWriter": "4.0.11",
        "System.Xml.XDocument": "4.0.11"
    }
}
```

<span data-ttu-id="09e88-136">次に、ライブラリの `project.json` ファイルの `dependencies` セクションにパッケージ参照をコピーします。`NETStandard.Library` 参照を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="09e88-136">Next, copy over the package references into the `dependencies` section of the library's `project.json` file, replacing the `NETStandard.Library` reference:</span></span>

```json
{
    "version":"1.0.0",
    "dependencies":{
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Diagnostics.Debug": "4.0.11",
        "System.Diagnostics.Tools": "4.0.1",
        "System.Globalization": "4.0.11",
        "System.IO": "4.1.0",
        "System.Linq": "4.1.0",
        "System.Net.Primitives": "4.0.11",
        "System.ObjectModel": "4.0.12",
        "System.Reflection": "4.1.0",
        "System.Reflection.Extensions": "4.0.1",
        "System.Reflection.Primitives": "4.0.1",
        "System.Resources.ResourceManager": "4.0.1",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Text.Encoding": "4.0.11",
        "System.Text.Encoding.Extensions": "4.0.11",
        "System.Text.RegularExpressions": "4.1.0",
        "System.Threading": "4.0.11",
        "System.Threading.Tasks": "4.0.11",
        "System.Xml.ReaderWriter": "4.0.11",
        "System.Xml.XDocument": "4.0.11"
    },
    "frameworks":{
        "netstandard1.0": {}
    }
}
```

<span data-ttu-id="09e88-137">パッケージがたくさんあります。コレクション タイプを拡張するとき、この多くが実際には必要ありません。</span><span class="sxs-lookup"><span data-stu-id="09e88-137">That's quite a lot of packages, many of which which certainly aren't necessary for extending collection types.</span></span>  <span data-ttu-id="09e88-138">手動でパッケージを削除するか、[ILSpy](http://ilspy.net) や [.NET Reflector](http://www.red-gate.com/products/dotnet-development/reflector) のようなツールを利用し、コードで実際に使用されるパッケージを特定できます。</span><span class="sxs-lookup"><span data-stu-id="09e88-138">You can either remove packages manually or use a tool such as [ILSpy](http://ilspy.net) or [.NET Reflector](http://www.red-gate.com/products/dotnet-development/reflector) to identify which packages your code actually uses.</span></span>

<span data-ttu-id="09e88-139">余計なものを減らしたパッケージは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="09e88-139">Here's what a trimmed package could look like:</span></span>

```json
{
    "dependencies":{
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Linq": "4.1.0",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Runtime.Handles": "4.0.1",
        "System.Runtime.InteropServices": "4.1.0",
        "System.Runtime.InteropServices.RuntimeInformation": "4.0.0",
        "System.Threading.Tasks": "4.0.11"
    },
    "frameworks":{
        "netstandard1.0": {}
     }
}
```

<span data-ttu-id="09e88-140">これで、`NETStandard.Library` メタパッケージに依存する場合より、フットプリントが少なくなります。</span><span class="sxs-lookup"><span data-stu-id="09e88-140">Now, it has a smaller footprint than if it had depended on the `NETStandard.Library` metapackage.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]