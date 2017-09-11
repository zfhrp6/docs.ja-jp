---
title: "dotnet-pack コマンド - .NET Core CLI"
description: "dotnet-pack コマンドでは、.NET Core プロジェクトの NuGet パッケージを作成します。"
keywords: "dotnet-pack, CLI, CLI コマンド, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 8dbbb3f7-b817-4161-a6c8-a3489d05e051
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 04b967fdf6578098caae8c21604c5d6160eb6775
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-pack"></a><span data-ttu-id="494b4-104">dotnet-pack</span><span class="sxs-lookup"><span data-stu-id="494b4-104">dotnet-pack</span></span>

## <a name="name"></a><span data-ttu-id="494b4-105">名前</span><span class="sxs-lookup"><span data-stu-id="494b4-105">Name</span></span>

<span data-ttu-id="494b4-106">`dotnet-pack` - NuGet パッケージにコードをパックします。</span><span class="sxs-lookup"><span data-stu-id="494b4-106">`dotnet-pack` - Packs the code into a NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="494b4-107">構文</span><span class="sxs-lookup"><span data-stu-id="494b4-107">Synopsis</span></span>

`dotnet pack [<PROJECT>] [-o|--output] [--no-build] [--include-symbols] [--include-source] [-c|--configuration] [--version-suffix <VERSION_SUFFIX>] [-s|--serviceable] [-v|--verbosity] [-h|--help]`

## <a name="description"></a><span data-ttu-id="494b4-108">説明</span><span class="sxs-lookup"><span data-stu-id="494b4-108">Description</span></span>

<span data-ttu-id="494b4-109">`dotnet pack` コマンドはプロジェクトをビルドし、NuGet パッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="494b4-109">The `dotnet pack` command builds the project and creates NuGet packages.</span></span> <span data-ttu-id="494b4-110">このコマンドの結果が NuGet パッケージです。</span><span class="sxs-lookup"><span data-stu-id="494b4-110">The result of this command is a NuGet package.</span></span> <span data-ttu-id="494b4-111">`--include-symbols` オプションが存在する場合、デバッグ シンボルを含む別のパッケージが作成されます。</span><span class="sxs-lookup"><span data-stu-id="494b4-111">If the `--include-symbols` option is present, another package containing the debug symbols is created.</span></span> 

<span data-ttu-id="494b4-112">パックされるプロジェクトの NuGet 依存関係が *.nuspec* ファイルに追加されるため、パッケージのインストール時に適切に解決されます。</span><span class="sxs-lookup"><span data-stu-id="494b4-112">NuGet dependencies of the packed project are added to the *.nuspec* file, so they're properly resolved when the package is installed.</span></span> <span data-ttu-id="494b4-113">プロジェクト間参照はプロジェクト内にはパッケージ化されません。</span><span class="sxs-lookup"><span data-stu-id="494b4-113">Project-to-project references aren't packaged inside the project.</span></span> <span data-ttu-id="494b4-114">現時点では、プロジェクト間の依存関係がある場合は、プロジェクトごとにパッケージが必要になります。</span><span class="sxs-lookup"><span data-stu-id="494b4-114">Currently, you must have a package per project if you have project-to-project dependencies.</span></span>

<span data-ttu-id="494b4-115">既定では、`dotnet pack` は最初にプロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="494b4-115">By default, `dotnet pack` builds the project first.</span></span> <span data-ttu-id="494b4-116">この動作を避けたい場合は、`--no-build` オプションを渡します。</span><span class="sxs-lookup"><span data-stu-id="494b4-116">If you wish to avoid this behavior, pass the `--no-build` option.</span></span> <span data-ttu-id="494b4-117">これは、コードが既にビルドされていることがわかっている場合の継続的インテグレーション (CI) ビルド シナリオで役立つことがよくあります。</span><span class="sxs-lookup"><span data-stu-id="494b4-117">This is often useful in Continuous Integration (CI) build scenarios where you know the code was previously built.</span></span>

<span data-ttu-id="494b4-118">パッキング プロセスのために `dotnet pack` コマンドに MSBuild のプロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="494b4-118">You can provide MSBuild properties to the `dotnet pack` command for the packing process.</span></span> <span data-ttu-id="494b4-119">詳細については、「[NuGet メタデータ プロパティ](csproj.md#nuget-metadata-properties)」と「[MSBuild コマンド ライン リファレンス](/visualstudio/msbuild/msbuild-command-line-reference)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="494b4-119">For more information, see [NuGet metadata properties](csproj.md#nuget-metadata-properties) and the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

## <a name="arguments"></a><span data-ttu-id="494b4-120">引数</span><span class="sxs-lookup"><span data-stu-id="494b4-120">Arguments</span></span>

`PROJECT` 
    
<span data-ttu-id="494b4-121">パックするプロジェクトです。</span><span class="sxs-lookup"><span data-stu-id="494b4-121">The project to pack.</span></span> <span data-ttu-id="494b4-122">[csproj ファイル](csproj.md)またはディレクトリのいずれかへのパスです。</span><span class="sxs-lookup"><span data-stu-id="494b4-122">It's either a path to a [csproj file](csproj.md) or to a directory.</span></span> <span data-ttu-id="494b4-123">省略すると、既定で現在のディレクトリに設定されます。</span><span class="sxs-lookup"><span data-stu-id="494b4-123">If omitted, it defaults to the current directory.</span></span> 

## <a name="options"></a><span data-ttu-id="494b4-124">オプション</span><span class="sxs-lookup"><span data-stu-id="494b4-124">Options</span></span>

`-h|--help`

<span data-ttu-id="494b4-125">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="494b4-125">Prints out a short help for the command.</span></span>  

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="494b4-126">指定したディレクトリにビルド済みパッケージを配置します。</span><span class="sxs-lookup"><span data-stu-id="494b4-126">Places the built packages in the directory specified.</span></span> 

`--no-build`

<span data-ttu-id="494b4-127">パッキングの前にプロジェクトをビルドしません。</span><span class="sxs-lookup"><span data-stu-id="494b4-127">Don't build the project before packing.</span></span> 

`--include-symbols`

<span data-ttu-id="494b4-128">シンボルの `nupkg` を生成します。</span><span class="sxs-lookup"><span data-stu-id="494b4-128">Generates the symbols `nupkg`.</span></span> 

`--include-source`

<span data-ttu-id="494b4-129">NuGet パッケージにソース ファイルを含めます。</span><span class="sxs-lookup"><span data-stu-id="494b4-129">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="494b4-130">ソース ファイルは、`nupkg` 内の `src` フォルダーに含まれます。</span><span class="sxs-lookup"><span data-stu-id="494b4-130">The sources files are included in the `src` folder within the `nupkg`.</span></span> 

`-c|--configuration <CONFIGURATION>`

<span data-ttu-id="494b4-131">プロジェクトのビルド時に使用する構成です。</span><span class="sxs-lookup"><span data-stu-id="494b4-131">Configuration to use when building the project.</span></span> <span data-ttu-id="494b4-132">指定しないと、構成は既定で `Debug` になります。</span><span class="sxs-lookup"><span data-stu-id="494b4-132">If not specified, configuration defaults to `Debug`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="494b4-133">プロジェクトの `$(VersionSuffix)` MSBuild プロパティの値を定義します。</span><span class="sxs-lookup"><span data-stu-id="494b4-133">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

`-s|--serviceable`

<span data-ttu-id="494b4-134">パッケージに処理可能フラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="494b4-134">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="494b4-135">詳しくは、「[.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing)」(.NET ブログ: .NET 4.5.1 は .NET NuGet ライブラリに対する Microsoft セキュリティ更新プログラムをサポートする) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="494b4-135">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="494b4-136">コマンドの詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="494b4-136">Sets the verbosity level of the command.</span></span> <span data-ttu-id="494b4-137">指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。</span><span class="sxs-lookup"><span data-stu-id="494b4-137">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="494b4-138">例</span><span class="sxs-lookup"><span data-stu-id="494b4-138">Examples</span></span>

<span data-ttu-id="494b4-139">現在のディレクトリのプロジェクトをパックします。</span><span class="sxs-lookup"><span data-stu-id="494b4-139">Pack the project in the current directory:</span></span>

`dotnet pack`

<span data-ttu-id="494b4-140">`app1` プロジェクトをパックします。</span><span class="sxs-lookup"><span data-stu-id="494b4-140">Pack the `app1` project:</span></span>

`dotnet pack ~/projects/app1/project.csproj`
    
<span data-ttu-id="494b4-141">プロジェクトを現在のディレクトリにパックし、`nupkgs` フォルダーに生成されたパッケージを配置します。</span><span class="sxs-lookup"><span data-stu-id="494b4-141">Pack the project in the current directory and place the resulting packages into the `nupkgs` folder:</span></span>

`dotnet pack --output nupkgs`

<span data-ttu-id="494b4-142">現在のディレクトリのプロジェクトを `nupkgs` フォルダーにパックし、ビルド ステップをスキップします。</span><span class="sxs-lookup"><span data-stu-id="494b4-142">Pack the project in the current directory into the `nupkgs` folder and skip the build step:</span></span>

`dotnet pack --no-build --output nupkgs`

<span data-ttu-id="494b4-143">*.csproj* ファイルで `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` として構成されているプロジェクトのバージョン サフィックスで、現在のプロジェクトをパックし、結果のパッケージ バージョンを指定されたサフィックスで更新します。</span><span class="sxs-lookup"><span data-stu-id="494b4-143">With the project's version suffix configured as `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` in the *.csproj* file, pack the current project and update the resulting package version with the given suffix:</span></span>

`dotnet pack --version-suffix "ci-1234"`

<span data-ttu-id="494b4-144">`PackageVersion` MSBuild プロパティで `2.1.0` にパッケージ バージョンを設定します。</span><span class="sxs-lookup"><span data-stu-id="494b4-144">Set the package version to `2.1.0` with the `PackageVersion` MSBuild property:</span></span>

`dotnet pack /p:PackageVersion=2.1.0`

