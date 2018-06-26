---
title: dotnet pack コマンド - .NET Core CLI
description: dotnet pack コマンドでは、.NET Core プロジェクトの NuGet パッケージを作成します。
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 8c2569ec7598b21fe9b673176143d0e54b9eb065
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696820"
---
# <a name="dotnet-pack"></a><span data-ttu-id="91ccd-103">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="91ccd-103">dotnet pack</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="91ccd-104">name</span><span class="sxs-lookup"><span data-stu-id="91ccd-104">Name</span></span>

<span data-ttu-id="91ccd-105">`dotnet pack` - NuGet パッケージにコードをパックします。</span><span class="sxs-lookup"><span data-stu-id="91ccd-105">`dotnet pack` - Packs the code into a NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="91ccd-106">構文</span><span class="sxs-lookup"><span data-stu-id="91ccd-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="91ccd-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="91ccd-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet pack [<PROJECT>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [--runtime] [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="91ccd-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="91ccd-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet pack [<PROJECT>] [-c|--configuration] [--include-source] [--include-symbols] [--no-build] [-o|--output]
    [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="91ccd-109">説明</span><span class="sxs-lookup"><span data-stu-id="91ccd-109">Description</span></span>

<span data-ttu-id="91ccd-110">`dotnet pack` コマンドはプロジェクトをビルドし、NuGet パッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="91ccd-110">The `dotnet pack` command builds the project and creates NuGet packages.</span></span> <span data-ttu-id="91ccd-111">このコマンドの結果が NuGet パッケージです。</span><span class="sxs-lookup"><span data-stu-id="91ccd-111">The result of this command is a NuGet package.</span></span> <span data-ttu-id="91ccd-112">`--include-symbols` オプションが存在する場合、デバッグ シンボルを含む別のパッケージが作成されます。</span><span class="sxs-lookup"><span data-stu-id="91ccd-112">If the `--include-symbols` option is present, another package containing the debug symbols is created.</span></span>

<span data-ttu-id="91ccd-113">パックされるプロジェクトの NuGet 依存関係が *.nuspec* ファイルに追加されるため、パッケージのインストール時に適切に解決されます。</span><span class="sxs-lookup"><span data-stu-id="91ccd-113">NuGet dependencies of the packed project are added to the *.nuspec* file, so they're properly resolved when the package is installed.</span></span> <span data-ttu-id="91ccd-114">プロジェクト間参照はプロジェクト内にはパッケージ化されません。</span><span class="sxs-lookup"><span data-stu-id="91ccd-114">Project-to-project references aren't packaged inside the project.</span></span> <span data-ttu-id="91ccd-115">現時点では、プロジェクト間の依存関係がある場合は、プロジェクトごとにパッケージが必要になります。</span><span class="sxs-lookup"><span data-stu-id="91ccd-115">Currently, you must have a package per project if you have project-to-project dependencies.</span></span>

<span data-ttu-id="91ccd-116">既定では、`dotnet pack` は最初にプロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="91ccd-116">By default, `dotnet pack` builds the project first.</span></span> <span data-ttu-id="91ccd-117">この動作を避けたい場合は、`--no-build` オプションを渡します。</span><span class="sxs-lookup"><span data-stu-id="91ccd-117">If you wish to avoid this behavior, pass the `--no-build` option.</span></span> <span data-ttu-id="91ccd-118">このオプションは、コードが既にビルドされていることがわかっている場合の継続的インテグレーション (CI) ビルド シナリオで役立つことがよくあります。</span><span class="sxs-lookup"><span data-stu-id="91ccd-118">This option is often useful in Continuous Integration (CI) build scenarios where you know the code was previously built.</span></span>

<span data-ttu-id="91ccd-119">パッキング プロセスのために `dotnet pack` コマンドに MSBuild のプロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="91ccd-119">You can provide MSBuild properties to the `dotnet pack` command for the packing process.</span></span> <span data-ttu-id="91ccd-120">詳細については、「[NuGet メタデータ プロパティ](csproj.md#nuget-metadata-properties)」と「[MSBuild コマンド ライン リファレンス](/visualstudio/msbuild/msbuild-command-line-reference)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91ccd-120">For more information, see [NuGet metadata properties](csproj.md#nuget-metadata-properties) and the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="91ccd-121">「[例](#examples)」のセクションでは、MSBuild の /p スイッチを使用する方法について、2 つの異なるシナリオで説明します。</span><span class="sxs-lookup"><span data-stu-id="91ccd-121">The [Examples](#examples) section shows how to use the MSBuild /p switch for a couple of different scenarios.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="91ccd-122">引数</span><span class="sxs-lookup"><span data-stu-id="91ccd-122">Arguments</span></span>

`PROJECT`

<span data-ttu-id="91ccd-123">パックするプロジェクトです。</span><span class="sxs-lookup"><span data-stu-id="91ccd-123">The project to pack.</span></span> <span data-ttu-id="91ccd-124">[csproj ファイル](csproj.md)またはディレクトリのいずれかへのパスです。</span><span class="sxs-lookup"><span data-stu-id="91ccd-124">It's either a path to a [csproj file](csproj.md) or to a directory.</span></span> <span data-ttu-id="91ccd-125">指定しない場合は、既定で現在のディレクトリに設定されます。</span><span class="sxs-lookup"><span data-stu-id="91ccd-125">If not specified, it defaults to the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="91ccd-126">オプション</span><span class="sxs-lookup"><span data-stu-id="91ccd-126">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="91ccd-127">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="91ccd-127">.NET Core 2.x</span></span>](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="91ccd-128">ビルド構成を定義します。</span><span class="sxs-lookup"><span data-stu-id="91ccd-128">Defines the build configuration.</span></span> <span data-ttu-id="91ccd-129">既定値は `Debug` です。</span><span class="sxs-lookup"><span data-stu-id="91ccd-129">The default value is `Debug`.</span></span>

`--force`

<span data-ttu-id="91ccd-130">最後の復元が成功した場合でも、すべての依存関係が強制的に解決されます。</span><span class="sxs-lookup"><span data-stu-id="91ccd-130">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="91ccd-131">このフラグを指定することは、*project.assets.json* ファイルを削除することと同じです。</span><span class="sxs-lookup"><span data-stu-id="91ccd-131">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="91ccd-132">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="91ccd-132">Prints out a short help for the command.</span></span>

`--include-source`

<span data-ttu-id="91ccd-133">NuGet パッケージにソース ファイルを含めます。</span><span class="sxs-lookup"><span data-stu-id="91ccd-133">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="91ccd-134">ソース ファイルは、`nupkg` 内の `src` フォルダーに含まれます。</span><span class="sxs-lookup"><span data-stu-id="91ccd-134">The sources files are included in the `src` folder within the `nupkg`.</span></span>

`--include-symbols`

<span data-ttu-id="91ccd-135">シンボルの `nupkg` を生成します。</span><span class="sxs-lookup"><span data-stu-id="91ccd-135">Generates the symbols `nupkg`.</span></span>

`--no-build`

<span data-ttu-id="91ccd-136">パッキングの前にプロジェクトをビルドしません。</span><span class="sxs-lookup"><span data-stu-id="91ccd-136">Doesn't build the project before packing.</span></span> <span data-ttu-id="91ccd-137">また、`--no-restore` フラグが暗黙的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="91ccd-137">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="91ccd-138">プロジェクト間参照を無視し、ルート プロジェクトのみを復元します。</span><span class="sxs-lookup"><span data-stu-id="91ccd-138">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="91ccd-139">コマンドを実行するときに、暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="91ccd-139">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="91ccd-140">指定したディレクトリにビルド済みパッケージを配置します。</span><span class="sxs-lookup"><span data-stu-id="91ccd-140">Places the built packages in the directory specified.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="91ccd-141">パッケージを復元するターゲット ランタイムを指定します。</span><span class="sxs-lookup"><span data-stu-id="91ccd-141">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="91ccd-142">ランタイム ID (RID) の一覧については、[RID カタログ](../rid-catalog.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="91ccd-142">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-s|--serviceable`

<span data-ttu-id="91ccd-143">パッケージに処理可能フラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="91ccd-143">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="91ccd-144">詳しくは、「[.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing)」(.NET ブログ: .NET 4.5.1 は .NET NuGet ライブラリに対する Microsoft セキュリティ更新プログラムをサポートする) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="91ccd-144">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="91ccd-145">プロジェクトの `$(VersionSuffix)` MSBuild プロパティの値を定義します。</span><span class="sxs-lookup"><span data-stu-id="91ccd-145">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="91ccd-146">コマンドの詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="91ccd-146">Sets the verbosity level of the command.</span></span> <span data-ttu-id="91ccd-147">指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。</span><span class="sxs-lookup"><span data-stu-id="91ccd-147">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="91ccd-148">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="91ccd-148">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="91ccd-149">ビルド構成を定義します。</span><span class="sxs-lookup"><span data-stu-id="91ccd-149">Defines the build configuration.</span></span> <span data-ttu-id="91ccd-150">既定値は `Debug` です。</span><span class="sxs-lookup"><span data-stu-id="91ccd-150">The default value is `Debug`.</span></span>

`-h|--help`

<span data-ttu-id="91ccd-151">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="91ccd-151">Prints out a short help for the command.</span></span>

`--include-source`

<span data-ttu-id="91ccd-152">NuGet パッケージにソース ファイルを含めます。</span><span class="sxs-lookup"><span data-stu-id="91ccd-152">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="91ccd-153">ソース ファイルは、`nupkg` 内の `src` フォルダーに含まれます。</span><span class="sxs-lookup"><span data-stu-id="91ccd-153">The sources files are included in the `src` folder within the `nupkg`.</span></span>

`--include-symbols`

<span data-ttu-id="91ccd-154">シンボルの `nupkg` を生成します。</span><span class="sxs-lookup"><span data-stu-id="91ccd-154">Generates the symbols `nupkg`.</span></span>

`--no-build`

<span data-ttu-id="91ccd-155">パッキングの前にプロジェクトをビルドしません。</span><span class="sxs-lookup"><span data-stu-id="91ccd-155">Doesn't build the project before packing.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="91ccd-156">指定したディレクトリにビルド済みパッケージを配置します。</span><span class="sxs-lookup"><span data-stu-id="91ccd-156">Places the built packages in the directory specified.</span></span>

`-s|--serviceable`

<span data-ttu-id="91ccd-157">パッケージに処理可能フラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="91ccd-157">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="91ccd-158">詳しくは、「[.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing)」(.NET ブログ: .NET 4.5.1 は .NET NuGet ライブラリに対する Microsoft セキュリティ更新プログラムをサポートする) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="91ccd-158">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="91ccd-159">プロジェクトの `$(VersionSuffix)` MSBuild プロパティの値を定義します。</span><span class="sxs-lookup"><span data-stu-id="91ccd-159">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="91ccd-160">コマンドの詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="91ccd-160">Sets the verbosity level of the command.</span></span> <span data-ttu-id="91ccd-161">指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。</span><span class="sxs-lookup"><span data-stu-id="91ccd-161">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="91ccd-162">使用例</span><span class="sxs-lookup"><span data-stu-id="91ccd-162">Examples</span></span>

<span data-ttu-id="91ccd-163">現在のディレクトリのプロジェクトをパックします。</span><span class="sxs-lookup"><span data-stu-id="91ccd-163">Pack the project in the current directory:</span></span>

`dotnet pack`

<span data-ttu-id="91ccd-164">`app1` プロジェクトをパックします。</span><span class="sxs-lookup"><span data-stu-id="91ccd-164">Pack the `app1` project:</span></span>

`dotnet pack ~/projects/app1/project.csproj`

<span data-ttu-id="91ccd-165">プロジェクトを現在のディレクトリにパックし、`nupkgs` フォルダーに生成されたパッケージを配置します。</span><span class="sxs-lookup"><span data-stu-id="91ccd-165">Pack the project in the current directory and place the resulting packages into the `nupkgs` folder:</span></span>

`dotnet pack --output nupkgs`

<span data-ttu-id="91ccd-166">現在のディレクトリのプロジェクトを `nupkgs` フォルダーにパックし、ビルド ステップをスキップします。</span><span class="sxs-lookup"><span data-stu-id="91ccd-166">Pack the project in the current directory into the `nupkgs` folder and skip the build step:</span></span>

`dotnet pack --no-build --output nupkgs`

<span data-ttu-id="91ccd-167">*.csproj* ファイルで `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` として構成されているプロジェクトのバージョン サフィックスで、現在のプロジェクトをパックし、結果のパッケージ バージョンを指定されたサフィックスで更新します。</span><span class="sxs-lookup"><span data-stu-id="91ccd-167">With the project's version suffix configured as `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` in the *.csproj* file, pack the current project and update the resulting package version with the given suffix:</span></span>

`dotnet pack --version-suffix "ci-1234"`

<span data-ttu-id="91ccd-168">`PackageVersion` MSBuild プロパティで `2.1.0` にパッケージ バージョンを設定します。</span><span class="sxs-lookup"><span data-stu-id="91ccd-168">Set the package version to `2.1.0` with the `PackageVersion` MSBuild property:</span></span>

`dotnet pack /p:PackageVersion=2.1.0`

<span data-ttu-id="91ccd-169">プロジェクトを特定の[ターゲット フレームワーク](../../standard/frameworks.md)用にパックします。</span><span class="sxs-lookup"><span data-stu-id="91ccd-169">Pack the project for a specific [target framework](../../standard/frameworks.md):</span></span>

`dotnet pack /p:TargetFrameworks=net45`

<span data-ttu-id="91ccd-170">プロジェクトをパックして、復元操作の特定のランタイム (Windows 10) を使用します(.NET Core SDK 2.0 以降のバージョン)。</span><span class="sxs-lookup"><span data-stu-id="91ccd-170">Pack the project and use a specific runtime (Windows 10) for the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet pack --runtime win10-x64`