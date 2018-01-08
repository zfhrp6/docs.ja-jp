---
title: "dotnet pack コマンド - .NET Core CLI"
description: "dotnet pack コマンドでは、.NET Core プロジェクトの NuGet パッケージを作成します。"
author: mairaw
ms.author: mairaw
ms.date: 12/13/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: 28cd05db0643097a7271fd0488354846598ba493
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-pack"></a><span data-ttu-id="b5d67-103">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="b5d67-103">dotnet pack</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="b5d67-104">name</span><span class="sxs-lookup"><span data-stu-id="b5d67-104">Name</span></span>

<span data-ttu-id="b5d67-105">`dotnet pack` - NuGet パッケージにコードをパックします。</span><span class="sxs-lookup"><span data-stu-id="b5d67-105">`dotnet pack` - Packs the code into a NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b5d67-106">構文</span><span class="sxs-lookup"><span data-stu-id="b5d67-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="b5d67-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="b5d67-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet pack [<PROJECT>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--no-build] [--no-dependencies] [--no-restore] [-o|--output] [--runtime] [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="b5d67-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="b5d67-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet pack [<PROJECT>] [-c|--configuration] [--include-source] [--include-symbols] [--no-build] [-o|--output] [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="b5d67-109">説明</span><span class="sxs-lookup"><span data-stu-id="b5d67-109">Description</span></span>

<span data-ttu-id="b5d67-110">`dotnet pack` コマンドはプロジェクトをビルドし、NuGet パッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="b5d67-110">The `dotnet pack` command builds the project and creates NuGet packages.</span></span> <span data-ttu-id="b5d67-111">このコマンドの結果が NuGet パッケージです。</span><span class="sxs-lookup"><span data-stu-id="b5d67-111">The result of this command is a NuGet package.</span></span> <span data-ttu-id="b5d67-112">`--include-symbols` オプションが存在する場合、デバッグ シンボルを含む別のパッケージが作成されます。</span><span class="sxs-lookup"><span data-stu-id="b5d67-112">If the `--include-symbols` option is present, another package containing the debug symbols is created.</span></span>

<span data-ttu-id="b5d67-113">パックされるプロジェクトの NuGet 依存関係が *.nuspec* ファイルに追加されるため、パッケージのインストール時に適切に解決されます。</span><span class="sxs-lookup"><span data-stu-id="b5d67-113">NuGet dependencies of the packed project are added to the *.nuspec* file, so they're properly resolved when the package is installed.</span></span> <span data-ttu-id="b5d67-114">プロジェクト間参照はプロジェクト内にはパッケージ化されません。</span><span class="sxs-lookup"><span data-stu-id="b5d67-114">Project-to-project references aren't packaged inside the project.</span></span> <span data-ttu-id="b5d67-115">現時点では、プロジェクト間の依存関係がある場合は、プロジェクトごとにパッケージが必要になります。</span><span class="sxs-lookup"><span data-stu-id="b5d67-115">Currently, you must have a package per project if you have project-to-project dependencies.</span></span>

<span data-ttu-id="b5d67-116">既定では、`dotnet pack` は最初にプロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="b5d67-116">By default, `dotnet pack` builds the project first.</span></span> <span data-ttu-id="b5d67-117">この動作を避けたい場合は、`--no-build` オプションを渡します。</span><span class="sxs-lookup"><span data-stu-id="b5d67-117">If you wish to avoid this behavior, pass the `--no-build` option.</span></span> <span data-ttu-id="b5d67-118">これは、コードが既にビルドされていることがわかっている場合の継続的インテグレーション (CI) ビルド シナリオで役立つことがよくあります。</span><span class="sxs-lookup"><span data-stu-id="b5d67-118">This is often useful in Continuous Integration (CI) build scenarios where you know the code was previously built.</span></span>

<span data-ttu-id="b5d67-119">パッキング プロセスのために `dotnet pack` コマンドに MSBuild のプロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b5d67-119">You can provide MSBuild properties to the `dotnet pack` command for the packing process.</span></span> <span data-ttu-id="b5d67-120">詳細については、「[NuGet メタデータ プロパティ](csproj.md#nuget-metadata-properties)」と「[MSBuild コマンド ライン リファレンス](/visualstudio/msbuild/msbuild-command-line-reference)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b5d67-120">For more information, see [NuGet metadata properties](csproj.md#nuget-metadata-properties) and the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="b5d67-121">「[例](#examples)」のセクションでは、MSBuild の /p スイッチを使用する方法について、2 つの異なるシナリオで説明します。</span><span class="sxs-lookup"><span data-stu-id="b5d67-121">The [Examples](#examples) section shows how to use the MSBuild /p switch for a couple of different scenarios.</span></span>

## <a name="arguments"></a><span data-ttu-id="b5d67-122">引数</span><span class="sxs-lookup"><span data-stu-id="b5d67-122">Arguments</span></span>

`PROJECT`

<span data-ttu-id="b5d67-123">パックするプロジェクトです。</span><span class="sxs-lookup"><span data-stu-id="b5d67-123">The project to pack.</span></span> <span data-ttu-id="b5d67-124">[csproj ファイル](csproj.md)またはディレクトリのいずれかへのパスです。</span><span class="sxs-lookup"><span data-stu-id="b5d67-124">It's either a path to a [csproj file](csproj.md) or to a directory.</span></span> <span data-ttu-id="b5d67-125">省略すると、既定で現在のディレクトリに設定されます。</span><span class="sxs-lookup"><span data-stu-id="b5d67-125">If omitted, it defaults to the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="b5d67-126">オプション</span><span class="sxs-lookup"><span data-stu-id="b5d67-126">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="b5d67-127">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="b5d67-127">.NET Core 2.x</span></span>](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="b5d67-128">ビルド構成を定義します。</span><span class="sxs-lookup"><span data-stu-id="b5d67-128">Defines the build configuration.</span></span> <span data-ttu-id="b5d67-129">既定値は `Debug` です。</span><span class="sxs-lookup"><span data-stu-id="b5d67-129">The default value is `Debug`.</span></span>

<span data-ttu-id="b5d67-130">`--force` 最後の復元が成功した場合でも、すべての依存関係が強制的に解決されます。</span><span class="sxs-lookup"><span data-stu-id="b5d67-130">`--force` Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="b5d67-131">これは、*project.assets.json* ファイルを削除する処理に相当します。</span><span class="sxs-lookup"><span data-stu-id="b5d67-131">This is equivalent to deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="b5d67-132">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="b5d67-132">Prints out a short help for the command.</span></span>

`--include-source`

<span data-ttu-id="b5d67-133">NuGet パッケージにソース ファイルを含めます。</span><span class="sxs-lookup"><span data-stu-id="b5d67-133">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="b5d67-134">ソース ファイルは、`nupkg` 内の `src` フォルダーに含まれます。</span><span class="sxs-lookup"><span data-stu-id="b5d67-134">The sources files are included in the `src` folder within the `nupkg`.</span></span>

`--include-symbols`

<span data-ttu-id="b5d67-135">シンボルの `nupkg` を生成します。</span><span class="sxs-lookup"><span data-stu-id="b5d67-135">Generates the symbols `nupkg`.</span></span>

`--no-build`

<span data-ttu-id="b5d67-136">パッキングの前にプロジェクトをビルドしません。</span><span class="sxs-lookup"><span data-stu-id="b5d67-136">Doesn't build the project before packing.</span></span>

`--no-dependencies`

<span data-ttu-id="b5d67-137">プロジェクト間参照を無視し、ルート プロジェクトのみを復元します。</span><span class="sxs-lookup"><span data-stu-id="b5d67-137">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="b5d67-138">コマンドを実行するときに、暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="b5d67-138">Doesn't perform an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="b5d67-139">指定したディレクトリにビルド済みパッケージを配置します。</span><span class="sxs-lookup"><span data-stu-id="b5d67-139">Places the built packages in the directory specified.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="b5d67-140">パッケージを復元するターゲット ランタイムを指定します。</span><span class="sxs-lookup"><span data-stu-id="b5d67-140">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="b5d67-141">ランタイム ID (RID) の一覧については、[RID カタログ](../rid-catalog.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b5d67-141">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-s|--serviceable`

<span data-ttu-id="b5d67-142">パッケージに処理可能フラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="b5d67-142">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="b5d67-143">詳しくは、「[.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing)」(.NET ブログ: .NET 4.5.1 は .NET NuGet ライブラリに対する Microsoft セキュリティ更新プログラムをサポートする) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b5d67-143">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="b5d67-144">プロジェクトの `$(VersionSuffix)` MSBuild プロパティの値を定義します。</span><span class="sxs-lookup"><span data-stu-id="b5d67-144">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="b5d67-145">コマンドの詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="b5d67-145">Sets the verbosity level of the command.</span></span> <span data-ttu-id="b5d67-146">指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。</span><span class="sxs-lookup"><span data-stu-id="b5d67-146">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="b5d67-147">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="b5d67-147">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="b5d67-148">ビルド構成を定義します。</span><span class="sxs-lookup"><span data-stu-id="b5d67-148">Defines the build configuration.</span></span> <span data-ttu-id="b5d67-149">既定値は `Debug` です。</span><span class="sxs-lookup"><span data-stu-id="b5d67-149">The default value is `Debug`.</span></span>

`-h|--help`

<span data-ttu-id="b5d67-150">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="b5d67-150">Prints out a short help for the command.</span></span>

`--include-source`

<span data-ttu-id="b5d67-151">NuGet パッケージにソース ファイルを含めます。</span><span class="sxs-lookup"><span data-stu-id="b5d67-151">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="b5d67-152">ソース ファイルは、`nupkg` 内の `src` フォルダーに含まれます。</span><span class="sxs-lookup"><span data-stu-id="b5d67-152">The sources files are included in the `src` folder within the `nupkg`.</span></span>

`--include-symbols`

<span data-ttu-id="b5d67-153">シンボルの `nupkg` を生成します。</span><span class="sxs-lookup"><span data-stu-id="b5d67-153">Generates the symbols `nupkg`.</span></span>

`--no-build`

<span data-ttu-id="b5d67-154">パッキングの前にプロジェクトをビルドしません。</span><span class="sxs-lookup"><span data-stu-id="b5d67-154">Doesn't build the project before packing.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="b5d67-155">指定したディレクトリにビルド済みパッケージを配置します。</span><span class="sxs-lookup"><span data-stu-id="b5d67-155">Places the built packages in the directory specified.</span></span>

`-s|--serviceable`

<span data-ttu-id="b5d67-156">パッケージに処理可能フラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="b5d67-156">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="b5d67-157">詳しくは、「[.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing)」(.NET ブログ: .NET 4.5.1 は .NET NuGet ライブラリに対する Microsoft セキュリティ更新プログラムをサポートする) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b5d67-157">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="b5d67-158">プロジェクトの `$(VersionSuffix)` MSBuild プロパティの値を定義します。</span><span class="sxs-lookup"><span data-stu-id="b5d67-158">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="b5d67-159">コマンドの詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="b5d67-159">Sets the verbosity level of the command.</span></span> <span data-ttu-id="b5d67-160">指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。</span><span class="sxs-lookup"><span data-stu-id="b5d67-160">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="b5d67-161">使用例</span><span class="sxs-lookup"><span data-stu-id="b5d67-161">Examples</span></span>

<span data-ttu-id="b5d67-162">現在のディレクトリのプロジェクトをパックします。</span><span class="sxs-lookup"><span data-stu-id="b5d67-162">Pack the project in the current directory:</span></span>

`dotnet pack`

<span data-ttu-id="b5d67-163">`app1` プロジェクトをパックします。</span><span class="sxs-lookup"><span data-stu-id="b5d67-163">Pack the `app1` project:</span></span>

`dotnet pack ~/projects/app1/project.csproj`
    
<span data-ttu-id="b5d67-164">プロジェクトを現在のディレクトリにパックし、`nupkgs` フォルダーに生成されたパッケージを配置します。</span><span class="sxs-lookup"><span data-stu-id="b5d67-164">Pack the project in the current directory and place the resulting packages into the `nupkgs` folder:</span></span>

`dotnet pack --output nupkgs`

<span data-ttu-id="b5d67-165">現在のディレクトリのプロジェクトを `nupkgs` フォルダーにパックし、ビルド ステップをスキップします。</span><span class="sxs-lookup"><span data-stu-id="b5d67-165">Pack the project in the current directory into the `nupkgs` folder and skip the build step:</span></span>

`dotnet pack --no-build --output nupkgs`

<span data-ttu-id="b5d67-166">*.csproj* ファイルで `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` として構成されているプロジェクトのバージョン サフィックスで、現在のプロジェクトをパックし、結果のパッケージ バージョンを指定されたサフィックスで更新します。</span><span class="sxs-lookup"><span data-stu-id="b5d67-166">With the project's version suffix configured as `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` in the *.csproj* file, pack the current project and update the resulting package version with the given suffix:</span></span>

`dotnet pack --version-suffix "ci-1234"`

<span data-ttu-id="b5d67-167">`PackageVersion` MSBuild プロパティで `2.1.0` にパッケージ バージョンを設定します。</span><span class="sxs-lookup"><span data-stu-id="b5d67-167">Set the package version to `2.1.0` with the `PackageVersion` MSBuild property:</span></span>

`dotnet pack /p:PackageVersion=2.1.0`

<span data-ttu-id="b5d67-168">プロジェクトを特定の[ターゲット フレームワーク](../../standard/frameworks.md)用にパックします。</span><span class="sxs-lookup"><span data-stu-id="b5d67-168">Pack the project for a specific [target framework](../../standard/frameworks.md):</span></span>

`dotnet pack /p:TargetFrameworks=net45`
