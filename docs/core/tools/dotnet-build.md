---
title: "dotnet-build コマンド - .NET Core CLI"
description: "dotnet-build コマンドは、プロジェクトとそのすべての依存関係をします。"
keywords: "dotnet-build, CLI, CLI コマンド, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 5e1a2bc4-a919-4a86-8f33-a9b218b1fcb3
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d2006b15978f384e53e43a0a2562e81d10582abd
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-build"></a><span data-ttu-id="9c1a9-104">dotnet-build</span><span class="sxs-lookup"><span data-stu-id="9c1a9-104">dotnet-build</span></span>

## <a name="name"></a><span data-ttu-id="9c1a9-105">名前</span><span class="sxs-lookup"><span data-stu-id="9c1a9-105">Name</span></span>

<span data-ttu-id="9c1a9-106">`dotnet-build` - プロジェクトとそのすべての依存関係をビルドします。</span><span class="sxs-lookup"><span data-stu-id="9c1a9-106">`dotnet-build` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9c1a9-107">構文</span><span class="sxs-lookup"><span data-stu-id="9c1a9-107">Synopsis</span></span>

`dotnet build [<PROJECT>] [-o|--output] [-f|--framework] [-c|--configuration] [-r|--runtime] [--version-suffix] [--no-incremental] [--no-dependencies] [-v|--verbosity] [-h|--help]`

## <a name="description"></a><span data-ttu-id="9c1a9-108">説明</span><span class="sxs-lookup"><span data-stu-id="9c1a9-108">Description</span></span>

<span data-ttu-id="9c1a9-109">`dotnet build` コマンドは、プロジェクトとその依存関係をバイナリ セットにビルドします。</span><span class="sxs-lookup"><span data-stu-id="9c1a9-109">The `dotnet build` command builds the project and its dependencies into a set of binaries.</span></span> <span data-ttu-id="9c1a9-110">バイナリには、拡張子が *.dll* である中間言語 (IL) ファイルのプロジェクトのコードと、拡張子が *.pdb* でありデバッグに使われるシンボル ファイルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="9c1a9-110">The binaries include the project's code in Intermediate Language (IL) files with a *.dll* extension and symbol files used for debugging with a *.pdb* extension.</span></span> <span data-ttu-id="9c1a9-111">アプリケーションの依存関係を一覧表示する依存関係 JSON ファイル (*\*.deps.json*) が生成されます。</span><span class="sxs-lookup"><span data-stu-id="9c1a9-111">A dependencies JSON file (*\*.deps.json*) is produced that lists the dependencies of the application.</span></span> <span data-ttu-id="9c1a9-112">共有ランタイムと、そのアプリケーションのバージョンを指定する、*\*.runtimeconfig.json* ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="9c1a9-112">A *\*.runtimeconfig.json* file is produced, which specifies the shared runtime and its version for the application.</span></span>

<span data-ttu-id="9c1a9-113">サードパーティ (NuGet のライブラリなど) との依存関係があるプロジェクトの場合、NuGet キャッシュから解決され、プロジェクトのビルドの出力では使うことができません。</span><span class="sxs-lookup"><span data-stu-id="9c1a9-113">If the project has third-party dependencies, such as libraries from NuGet, they're resolved from the NuGet cache and aren't available with the project's built output.</span></span> <span data-ttu-id="9c1a9-114">この点を考慮すると、`dotnet build` の生成物は別のコンピューターに転送して実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="9c1a9-114">With that in mind, the product of `dotnet build` isn't ready to be transferred to another machine to run.</span></span> <span data-ttu-id="9c1a9-115">これは .NET Framework の動作とは対照的です。.NET Framework の場合、実行可能なプロジェクト (アプリケーション) をビルドすると、.NET Framework がインストールされている任意のコンピューター上で実行できる出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="9c1a9-115">This is in contrast to the behavior of the .NET Framework in which building an executable project (an application) produces output that's runnable on any machine where the .NET Framework is installed.</span></span> <span data-ttu-id="9c1a9-116">.NET Core でも同様の動作にするには、[dotnet publish](dotnet-publish.md) コマンドを使います。</span><span class="sxs-lookup"><span data-stu-id="9c1a9-116">To have a similar experience with .NET Core, you use the [dotnet publish](dotnet-publish.md) command.</span></span> <span data-ttu-id="9c1a9-117">詳しくは、「[.NET Core アプリケーション展開](../deploying/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9c1a9-117">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span> 

<span data-ttu-id="9c1a9-118">ビルドには *project.assets.json* ファイルが必要です。このファイルには、アプリケーションの依存関係が一覧表示されています。</span><span class="sxs-lookup"><span data-stu-id="9c1a9-118">Building requires the *project.assets.json* file, which lists the dependencies of your application.</span></span> <span data-ttu-id="9c1a9-119">このファイルは、プロジェクトをビルドする前に [`dotnet restore`](dotnet-restore.md) を実行すると作成されます。</span><span class="sxs-lookup"><span data-stu-id="9c1a9-119">The file is created when you execute [`dotnet restore`](dotnet-restore.md) before building the project.</span></span> <span data-ttu-id="9c1a9-120">アセット ファイルがないと、ツールは参照アセンブリを解決できないため、エラーになります。</span><span class="sxs-lookup"><span data-stu-id="9c1a9-120">Without the assets file in place, the tooling cannot resolve reference assemblies, which will result in errors.</span></span>

<span data-ttu-id="9c1a9-121">`dotnet build` は MSBuild を使ってプロジェクトをビルドするので、並行ビルドとインクリメンタル ビルドの両方をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="9c1a9-121">`dotnet build` uses MSBuild to build the project; thus, it supports both parallel and incremental builds.</span></span> <span data-ttu-id="9c1a9-122">詳しくは、「[インクリメンタル ビルド](/visualstudio/msbuild/incremental-builds)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9c1a9-122">Refer to [Incremental Builds](/visualstudio/msbuild/incremental-builds) for more information.</span></span> 

<span data-ttu-id="9c1a9-123">このオプションに加え、`dotnet build` コマンドは、プロパティを設定する `/p` やロガーを定義する `/l` などの MSBuild オプションも受け入れます。</span><span class="sxs-lookup"><span data-stu-id="9c1a9-123">In addition to its options, the `dotnet build` command accepts MSBuild options, such as `/p` for setting properties or `/l` to define a logger.</span></span> <span data-ttu-id="9c1a9-124">これらのオプションについて詳しくは、「[MSBuild コマンド ライン リファレンス](/visualstudio/msbuild/msbuild-command-line-reference)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9c1a9-124">Learn more about these options in the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> 

<span data-ttu-id="9c1a9-125">プロジェクトを実行できるかどうかは、プロジェクト ファイルの `<OutputType>` プロパティで決まります。</span><span class="sxs-lookup"><span data-stu-id="9c1a9-125">Whether the project is executable or not is determined by the `<OutputType>` property in the project file.</span></span> <span data-ttu-id="9c1a9-126">次の例は、実行可能なコードを生成するプロジェクトを示しています。</span><span class="sxs-lookup"><span data-stu-id="9c1a9-126">The following example shows a project that will produce executable code:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="9c1a9-127">ライブラリを生成するには、`<OutputType>` プロパティを省略してください。</span><span class="sxs-lookup"><span data-stu-id="9c1a9-127">In order to produce a library, omit the `<OutputType>` property.</span></span> <span data-ttu-id="9c1a9-128">ビルドされる出力の主な違いは、ライブラリの IL DLL にはエントリ ポイントが含まれず、実行できないことです。</span><span class="sxs-lookup"><span data-stu-id="9c1a9-128">The main difference in built output is that the IL DLL for a library doesn't contain entry points and can't be executed.</span></span> 

## <a name="arguments"></a><span data-ttu-id="9c1a9-129">引数</span><span class="sxs-lookup"><span data-stu-id="9c1a9-129">Arguments</span></span>

`PROJECT`

<span data-ttu-id="9c1a9-130">ビルドするプロジェクト ファイル。</span><span class="sxs-lookup"><span data-stu-id="9c1a9-130">The project file to build.</span></span> <span data-ttu-id="9c1a9-131">プロジェクト ファイルを指定しない場合、MSBuild は、現在の作業ディレクトリから *proj* で終わるファイル名拡張子を検索し、そのファイルを使います。</span><span class="sxs-lookup"><span data-stu-id="9c1a9-131">If a project file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="9c1a9-132">オプション</span><span class="sxs-lookup"><span data-stu-id="9c1a9-132">Options</span></span>

`-h|--help`

<span data-ttu-id="9c1a9-133">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="9c1a9-133">Prints out a short help for the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="9c1a9-134">ビルド済みバイナリを配置するディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="9c1a9-134">Directory in which to place the built binaries.</span></span> <span data-ttu-id="9c1a9-135">このオプションを指定する場合は、`--framework` を定義する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="9c1a9-135">You also need to define `--framework` when you specify this option.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="9c1a9-136">特定の[フレームワーク](../../standard/frameworks.md)用にコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="9c1a9-136">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="9c1a9-137">フレームワークは、[プロジェクト ファイル](csproj.md)で定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c1a9-137">The framework must be defined in the [project file](csproj.md).</span></span>

`-c|--configuration <CONFIGURATION>`

<span data-ttu-id="9c1a9-138">ビルド構成を定義します。</span><span class="sxs-lookup"><span data-stu-id="9c1a9-138">Defines the build configuration.</span></span> <span data-ttu-id="9c1a9-139">省略すると、ビルド構成は既定で `Debug` になります。</span><span class="sxs-lookup"><span data-stu-id="9c1a9-139">If omitted, the build configuration defaults to `Debug`.</span></span> <span data-ttu-id="9c1a9-140">リリース構成をビルドするには `Release` を使います。</span><span class="sxs-lookup"><span data-stu-id="9c1a9-140">Use `Release` build a Release configuration.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="9c1a9-141">ターゲットのランタイムを指定します。</span><span class="sxs-lookup"><span data-stu-id="9c1a9-141">Specifies the target runtime.</span></span> <span data-ttu-id="9c1a9-142">ランタイム ID (RID) の一覧については、[RID カタログ](../rid-catalog.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9c1a9-142">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="9c1a9-143">プロジェクト ファイルのバージョン フィールドでアスタリスク (`*`) のバージョン サフィックスを定義します。</span><span class="sxs-lookup"><span data-stu-id="9c1a9-143">Defines the version suffix for an asterisk (`*`) in the version field of the project file.</span></span> <span data-ttu-id="9c1a9-144">形式は NuGet のバージョン ガイドラインに従います。</span><span class="sxs-lookup"><span data-stu-id="9c1a9-144">The format follows NuGet's version guidelines.</span></span>

`--no-incremental`

<span data-ttu-id="9c1a9-145">インクリメンタル ビルドとして安全でないビルドをマークします。</span><span class="sxs-lookup"><span data-stu-id="9c1a9-145">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="9c1a9-146">これにより、インクリメンタル コンパイルは無効になり、プロジェクトの依存関係グラフのクリーン再ビルドが強制的に行われます。</span><span class="sxs-lookup"><span data-stu-id="9c1a9-146">This turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

`--no-dependencies`

<span data-ttu-id="9c1a9-147">プロジェクト間 (P2P) 参照を無視し、ビルド対象として指定されたルート プロジェクトのみをビルドします。</span><span class="sxs-lookup"><span data-stu-id="9c1a9-147">Ignores project-to-project (P2P) references and only builds the root project specified to build.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="9c1a9-148">コマンドの詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="9c1a9-148">Sets the verbosity level of the command.</span></span> <span data-ttu-id="9c1a9-149">指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。</span><span class="sxs-lookup"><span data-stu-id="9c1a9-149">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="9c1a9-150">例</span><span class="sxs-lookup"><span data-stu-id="9c1a9-150">Examples</span></span>

<span data-ttu-id="9c1a9-151">プロジェクトとその依存関係をビルドします。</span><span class="sxs-lookup"><span data-stu-id="9c1a9-151">Build a project and its dependencies:</span></span>

`dotnet build`

<span data-ttu-id="9c1a9-152">リリース構成を使用して、プロジェクトとその依存関係をビルドします。</span><span class="sxs-lookup"><span data-stu-id="9c1a9-152">Build a project and its dependencies using Release configuration:</span></span>

`dotnet build --configuration Release`

<span data-ttu-id="9c1a9-153">特定のランタイム (この例では、Ubuntu 16.04) 用にプロジェクトとその依存関係をビルドします。</span><span class="sxs-lookup"><span data-stu-id="9c1a9-153">Build a project and its dependencies for a specific runtime (in this example, Ubuntu 16.04):</span></span>

`dotnet build --runtime ubuntu.16.04-x64`

