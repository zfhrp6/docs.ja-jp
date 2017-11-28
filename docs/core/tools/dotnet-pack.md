---
title: "dotnet pack コマンド - .NET Core CLI"
description: "dotnet pack コマンドでは、.NET Core プロジェクトの NuGet パッケージを作成します。"
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 8594c863d67baf0237b63e61f28ca9ee315eeddf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-pack"></a><span data-ttu-id="95272-103">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="95272-103">dotnet pack</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="95272-104">名前</span><span class="sxs-lookup"><span data-stu-id="95272-104">Name</span></span>

<span data-ttu-id="95272-105">`dotnet pack` - NuGet パッケージにコードをパックします。</span><span class="sxs-lookup"><span data-stu-id="95272-105">`dotnet pack` - Packs the code into a NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="95272-106">構文</span><span class="sxs-lookup"><span data-stu-id="95272-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="95272-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="95272-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet pack [<PROJECT>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--no-build] [--no-dependencies] [--no-restore] [-o|--output] [--runtime] [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="95272-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="95272-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet pack [<PROJECT>] [-c|--configuration] [--include-source] [--include-symbols] [--no-build] [-o|--output] [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="95272-109">説明</span><span class="sxs-lookup"><span data-stu-id="95272-109">Description</span></span>

<span data-ttu-id="95272-110">`dotnet pack` コマンドはプロジェクトをビルドし、NuGet パッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="95272-110">The `dotnet pack` command builds the project and creates NuGet packages.</span></span> <span data-ttu-id="95272-111">このコマンドの結果が NuGet パッケージです。</span><span class="sxs-lookup"><span data-stu-id="95272-111">The result of this command is a NuGet package.</span></span> <span data-ttu-id="95272-112">`--include-symbols` オプションが存在する場合、デバッグ シンボルを含む別のパッケージが作成されます。</span><span class="sxs-lookup"><span data-stu-id="95272-112">If the `--include-symbols` option is present, another package containing the debug symbols is created.</span></span>

<span data-ttu-id="95272-113">パックされるプロジェクトの NuGet 依存関係が *.nuspec* ファイルに追加されるため、パッケージのインストール時に適切に解決されます。</span><span class="sxs-lookup"><span data-stu-id="95272-113">NuGet dependencies of the packed project are added to the *.nuspec* file, so they're properly resolved when the package is installed.</span></span> <span data-ttu-id="95272-114">プロジェクト間参照はプロジェクト内にはパッケージ化されません。</span><span class="sxs-lookup"><span data-stu-id="95272-114">Project-to-project references aren't packaged inside the project.</span></span> <span data-ttu-id="95272-115">現時点では、プロジェクト間の依存関係がある場合は、プロジェクトごとにパッケージが必要になります。</span><span class="sxs-lookup"><span data-stu-id="95272-115">Currently, you must have a package per project if you have project-to-project dependencies.</span></span>

<span data-ttu-id="95272-116">既定では、`dotnet pack` は最初にプロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="95272-116">By default, `dotnet pack` builds the project first.</span></span> <span data-ttu-id="95272-117">この動作を避けたい場合は、`--no-build` オプションを渡します。</span><span class="sxs-lookup"><span data-stu-id="95272-117">If you wish to avoid this behavior, pass the `--no-build` option.</span></span> <span data-ttu-id="95272-118">これは、コードが既にビルドされていることがわかっている場合の継続的インテグレーション (CI) ビルド シナリオで役立つことがよくあります。</span><span class="sxs-lookup"><span data-stu-id="95272-118">This is often useful in Continuous Integration (CI) build scenarios where you know the code was previously built.</span></span>

<span data-ttu-id="95272-119">パッキング プロセスのために `dotnet pack` コマンドに MSBuild のプロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="95272-119">You can provide MSBuild properties to the `dotnet pack` command for the packing process.</span></span> <span data-ttu-id="95272-120">詳細については、「[NuGet メタデータ プロパティ](csproj.md#nuget-metadata-properties)」と「[MSBuild コマンド ライン リファレンス](/visualstudio/msbuild/msbuild-command-line-reference)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="95272-120">For more information, see [NuGet metadata properties](csproj.md#nuget-metadata-properties) and the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

## <a name="arguments"></a><span data-ttu-id="95272-121">引数</span><span class="sxs-lookup"><span data-stu-id="95272-121">Arguments</span></span>

`PROJECT`

<span data-ttu-id="95272-122">パックするプロジェクトです。</span><span class="sxs-lookup"><span data-stu-id="95272-122">The project to pack.</span></span> <span data-ttu-id="95272-123">[csproj ファイル](csproj.md)またはディレクトリのいずれかへのパスです。</span><span class="sxs-lookup"><span data-stu-id="95272-123">It's either a path to a [csproj file](csproj.md) or to a directory.</span></span> <span data-ttu-id="95272-124">省略すると、既定で現在のディレクトリに設定されます。</span><span class="sxs-lookup"><span data-stu-id="95272-124">If omitted, it defaults to the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="95272-125">オプション</span><span class="sxs-lookup"><span data-stu-id="95272-125">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="95272-126">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="95272-126">.NET Core 2.x</span></span>](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="95272-127">ビルド構成を定義します。</span><span class="sxs-lookup"><span data-stu-id="95272-127">Defines the build configuration.</span></span> <span data-ttu-id="95272-128">既定値は `Debug` です。</span><span class="sxs-lookup"><span data-stu-id="95272-128">The default value is `Debug`.</span></span>

<span data-ttu-id="95272-129">`--force` 最後の復元が成功した場合でも、すべての依存関係が強制的に解決されます。</span><span class="sxs-lookup"><span data-stu-id="95272-129">`--force` Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="95272-130">これは、*project.assets.json* ファイルを削除する処理に相当します。</span><span class="sxs-lookup"><span data-stu-id="95272-130">This is equivalent to deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="95272-131">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="95272-131">Prints out a short help for the command.</span></span>

`--include-source`

<span data-ttu-id="95272-132">NuGet パッケージにソース ファイルを含めます。</span><span class="sxs-lookup"><span data-stu-id="95272-132">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="95272-133">ソース ファイルは、`nupkg` 内の `src` フォルダーに含まれます。</span><span class="sxs-lookup"><span data-stu-id="95272-133">The sources files are included in the `src` folder within the `nupkg`.</span></span>

`--include-symbols`

<span data-ttu-id="95272-134">シンボルの `nupkg` を生成します。</span><span class="sxs-lookup"><span data-stu-id="95272-134">Generates the symbols `nupkg`.</span></span>

`--no-build`

<span data-ttu-id="95272-135">パッキングの前にプロジェクトをビルドしません。</span><span class="sxs-lookup"><span data-stu-id="95272-135">Doesn't build the project before packing.</span></span>

`--no-dependencies`

<span data-ttu-id="95272-136">プロジェクト間参照を無視し、ルート プロジェクトのみを復元します。</span><span class="sxs-lookup"><span data-stu-id="95272-136">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="95272-137">コマンドを実行するときに、暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="95272-137">Doesn't perform an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="95272-138">指定したディレクトリにビルド済みパッケージを配置します。</span><span class="sxs-lookup"><span data-stu-id="95272-138">Places the built packages in the directory specified.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="95272-139">パッケージを復元するターゲット ランタイムを指定します。</span><span class="sxs-lookup"><span data-stu-id="95272-139">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="95272-140">ランタイム ID (RID) の一覧については、[RID カタログ](../rid-catalog.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="95272-140">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-s|--serviceable`

<span data-ttu-id="95272-141">パッケージに処理可能フラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="95272-141">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="95272-142">詳しくは、「[.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing)」(.NET ブログ: .NET 4.5.1 は .NET NuGet ライブラリに対する Microsoft セキュリティ更新プログラムをサポートする) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="95272-142">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="95272-143">プロジェクトの `$(VersionSuffix)` MSBuild プロパティの値を定義します。</span><span class="sxs-lookup"><span data-stu-id="95272-143">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="95272-144">コマンドの詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="95272-144">Sets the verbosity level of the command.</span></span> <span data-ttu-id="95272-145">指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。</span><span class="sxs-lookup"><span data-stu-id="95272-145">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="95272-146">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="95272-146">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="95272-147">ビルド構成を定義します。</span><span class="sxs-lookup"><span data-stu-id="95272-147">Defines the build configuration.</span></span> <span data-ttu-id="95272-148">既定値は `Debug` です。</span><span class="sxs-lookup"><span data-stu-id="95272-148">The default value is `Debug`.</span></span>

`-h|--help`

<span data-ttu-id="95272-149">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="95272-149">Prints out a short help for the command.</span></span>

`--include-source`

<span data-ttu-id="95272-150">NuGet パッケージにソース ファイルを含めます。</span><span class="sxs-lookup"><span data-stu-id="95272-150">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="95272-151">ソース ファイルは、`nupkg` 内の `src` フォルダーに含まれます。</span><span class="sxs-lookup"><span data-stu-id="95272-151">The sources files are included in the `src` folder within the `nupkg`.</span></span>

`--include-symbols`

<span data-ttu-id="95272-152">シンボルの `nupkg` を生成します。</span><span class="sxs-lookup"><span data-stu-id="95272-152">Generates the symbols `nupkg`.</span></span>

`--no-build`

<span data-ttu-id="95272-153">パッキングの前にプロジェクトをビルドしません。</span><span class="sxs-lookup"><span data-stu-id="95272-153">Doesn't build the project before packing.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="95272-154">指定したディレクトリにビルド済みパッケージを配置します。</span><span class="sxs-lookup"><span data-stu-id="95272-154">Places the built packages in the directory specified.</span></span>

`-s|--serviceable`

<span data-ttu-id="95272-155">パッケージに処理可能フラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="95272-155">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="95272-156">詳しくは、「[.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing)」(.NET ブログ: .NET 4.5.1 は .NET NuGet ライブラリに対する Microsoft セキュリティ更新プログラムをサポートする) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="95272-156">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="95272-157">プロジェクトの `$(VersionSuffix)` MSBuild プロパティの値を定義します。</span><span class="sxs-lookup"><span data-stu-id="95272-157">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="95272-158">コマンドの詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="95272-158">Sets the verbosity level of the command.</span></span> <span data-ttu-id="95272-159">指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。</span><span class="sxs-lookup"><span data-stu-id="95272-159">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="95272-160">例</span><span class="sxs-lookup"><span data-stu-id="95272-160">Examples</span></span>

<span data-ttu-id="95272-161">現在のディレクトリのプロジェクトをパックします。</span><span class="sxs-lookup"><span data-stu-id="95272-161">Pack the project in the current directory:</span></span>

`dotnet pack`

<span data-ttu-id="95272-162">`app1` プロジェクトをパックします。</span><span class="sxs-lookup"><span data-stu-id="95272-162">Pack the `app1` project:</span></span>

`dotnet pack ~/projects/app1/project.csproj`
    
<span data-ttu-id="95272-163">プロジェクトを現在のディレクトリにパックし、`nupkgs` フォルダーに生成されたパッケージを配置します。</span><span class="sxs-lookup"><span data-stu-id="95272-163">Pack the project in the current directory and place the resulting packages into the `nupkgs` folder:</span></span>

`dotnet pack --output nupkgs`

<span data-ttu-id="95272-164">現在のディレクトリのプロジェクトを `nupkgs` フォルダーにパックし、ビルド ステップをスキップします。</span><span class="sxs-lookup"><span data-stu-id="95272-164">Pack the project in the current directory into the `nupkgs` folder and skip the build step:</span></span>

`dotnet pack --no-build --output nupkgs`

<span data-ttu-id="95272-165">*.csproj* ファイルで `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` として構成されているプロジェクトのバージョン サフィックスで、現在のプロジェクトをパックし、結果のパッケージ バージョンを指定されたサフィックスで更新します。</span><span class="sxs-lookup"><span data-stu-id="95272-165">With the project's version suffix configured as `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` in the *.csproj* file, pack the current project and update the resulting package version with the given suffix:</span></span>

`dotnet pack --version-suffix "ci-1234"`

<span data-ttu-id="95272-166">`PackageVersion` MSBuild プロパティで `2.1.0` にパッケージ バージョンを設定します。</span><span class="sxs-lookup"><span data-stu-id="95272-166">Set the package version to `2.1.0` with the `PackageVersion` MSBuild property:</span></span>

`dotnet pack /p:PackageVersion=2.1.0`
