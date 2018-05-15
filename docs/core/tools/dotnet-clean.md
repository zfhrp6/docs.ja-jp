---
title: dotnet clean コマンド - .NET Core CLI
description: dotnet clean コマンドは現在のディレクトリを消去します。
author: mairaw
ms.author: mairaw
ms.date: 08/13/2017
ms.openlocfilehash: 412f3aa3a942d2f48cd684af341227d193a6db02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="dotnet-clean"></a><span data-ttu-id="c7097-103">dotnet-clean</span><span class="sxs-lookup"><span data-stu-id="c7097-103">dotnet-clean</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="c7097-104">name</span><span class="sxs-lookup"><span data-stu-id="c7097-104">Name</span></span>

<span data-ttu-id="c7097-105">`dotnet clean` - プロジェクトの出力を消去します。</span><span class="sxs-lookup"><span data-stu-id="c7097-105">`dotnet clean` - Cleans the output of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c7097-106">構文</span><span class="sxs-lookup"><span data-stu-id="c7097-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="c7097-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="c7097-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c7097-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="c7097-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-v|--verbosity]
dotnet clean [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="c7097-109">説明</span><span class="sxs-lookup"><span data-stu-id="c7097-109">Description</span></span>

<span data-ttu-id="c7097-110">`dotnet clean` コマンドは、以前のビルドの出力を消去します。</span><span class="sxs-lookup"><span data-stu-id="c7097-110">The `dotnet clean` command cleans the output of the previous build.</span></span> <span data-ttu-id="c7097-111">[MSBuild ターゲット](/visualstudio/msbuild/msbuild-targets)として実装されます。そのため、コマンドの実行時にプロジェクトが評価されます。</span><span class="sxs-lookup"><span data-stu-id="c7097-111">It's implemented as an [MSBuild target](/visualstudio/msbuild/msbuild-targets), so the project is evaluated when the command is run.</span></span> <span data-ttu-id="c7097-112">ビルド中に作成された出力のみが消去されます。</span><span class="sxs-lookup"><span data-stu-id="c7097-112">Only the outputs created during the build are cleaned.</span></span> <span data-ttu-id="c7097-113">中間 (*obj*) と最終出力 (*bin*) フォルダーの両方が消去されます。</span><span class="sxs-lookup"><span data-stu-id="c7097-113">Both intermediate (*obj*) and final output (*bin*) folders are cleaned.</span></span>

## <a name="arguments"></a><span data-ttu-id="c7097-114">引数</span><span class="sxs-lookup"><span data-stu-id="c7097-114">Arguments</span></span>

`PROJECT`

<span data-ttu-id="c7097-115">消去する MSBuild プロジェクトです。</span><span class="sxs-lookup"><span data-stu-id="c7097-115">The MSBuild project to clean.</span></span> <span data-ttu-id="c7097-116">プロジェクト ファイルを指定しない場合、MSBuild は、現在の作業ディレクトリから *proj* で終わるファイル名拡張子を検索し、そのファイルを使います。</span><span class="sxs-lookup"><span data-stu-id="c7097-116">If a project file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="c7097-117">オプション</span><span class="sxs-lookup"><span data-stu-id="c7097-117">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="c7097-118">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="c7097-118">.NET Core 2.x</span></span>](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="c7097-119">ビルド構成を定義します。</span><span class="sxs-lookup"><span data-stu-id="c7097-119">Defines the build configuration.</span></span> <span data-ttu-id="c7097-120">既定値は `Debug` です。</span><span class="sxs-lookup"><span data-stu-id="c7097-120">The default value is `Debug`.</span></span> <span data-ttu-id="c7097-121">このオプションは、ビルド時に指定した場合にのみ、消去時にも必要です。</span><span class="sxs-lookup"><span data-stu-id="c7097-121">This option is only required when cleaning if you specified it during build time.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="c7097-122">ビルド時に指定された[フレームワーク](../../standard/frameworks.md)です。</span><span class="sxs-lookup"><span data-stu-id="c7097-122">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="c7097-123">フレームワークは、[プロジェクト ファイル](csproj.md)で定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c7097-123">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="c7097-124">ビルド時にフレームワークを指定した場合は、消去時にフレームワークを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c7097-124">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

`-h|--help`

<span data-ttu-id="c7097-125">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="c7097-125">Prints out a short help for the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="c7097-126">ビルド出力が配置されたディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="c7097-126">Directory in which the build outputs are placed.</span></span> <span data-ttu-id="c7097-127">プロジェクトのビルド時にフレームワークを指定した場合、出力ディレクトリ スイッチと共に `-f|--framework <FRAMEWORK>` スイッチを指定します。</span><span class="sxs-lookup"><span data-stu-id="c7097-127">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="c7097-128">指定したランタイムの出力フォルダーをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="c7097-128">Cleans the output folder of the specified runtime.</span></span> <span data-ttu-id="c7097-129">これは、[自己完結型の展開](../deploying/index.md#self-contained-deployments-scd)が作成された場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="c7097-129">This is used when a [self-contained deployment](../deploying/index.md#self-contained-deployments-scd) was created.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="c7097-130">コマンドの詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="c7097-130">Sets the verbosity level of the command.</span></span> <span data-ttu-id="c7097-131">指定できるレベルは、q[uiet]、m[inimal]、n[ormal]、d[etailed]、diag[nostic] です。</span><span class="sxs-lookup"><span data-stu-id="c7097-131">Allowed levels are q[uiet], m[inimal], n[ormal], d[etailed], and diag[nostic].</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c7097-132">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="c7097-132">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="c7097-133">ビルド構成を定義します。</span><span class="sxs-lookup"><span data-stu-id="c7097-133">Defines the build configuration.</span></span> <span data-ttu-id="c7097-134">既定値は `Debug` です。</span><span class="sxs-lookup"><span data-stu-id="c7097-134">The default value is `Debug`.</span></span> <span data-ttu-id="c7097-135">このオプションは、ビルド時に指定した場合にのみ、消去時にも必要です。</span><span class="sxs-lookup"><span data-stu-id="c7097-135">This option is only required when cleaning if you specified it during build time.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="c7097-136">ビルド時に指定された[フレームワーク](../../standard/frameworks.md)です。</span><span class="sxs-lookup"><span data-stu-id="c7097-136">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="c7097-137">フレームワークは、[プロジェクト ファイル](csproj.md)で定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c7097-137">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="c7097-138">ビルド時にフレームワークを指定した場合は、消去時にフレームワークを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c7097-138">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

`-h|--help`

<span data-ttu-id="c7097-139">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="c7097-139">Prints out a short help for the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="c7097-140">ビルド出力が配置されたディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="c7097-140">Directory in which the build outputs are placed.</span></span> <span data-ttu-id="c7097-141">プロジェクトのビルド時にフレームワークを指定した場合、出力ディレクトリ スイッチと共に `-f|--framework <FRAMEWORK>` スイッチを指定します。</span><span class="sxs-lookup"><span data-stu-id="c7097-141">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="c7097-142">コマンドの詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="c7097-142">Sets the verbosity level of the command.</span></span> <span data-ttu-id="c7097-143">指定できるレベルは、q[uiet]、m[inimal]、n[ormal]、d[etailed]、diag[nostic] です。</span><span class="sxs-lookup"><span data-stu-id="c7097-143">Allowed levels are q[uiet], m[inimal], n[ormal], d[etailed], and diag[nostic].</span></span>

---

## <a name="examples"></a><span data-ttu-id="c7097-144">使用例</span><span class="sxs-lookup"><span data-stu-id="c7097-144">Examples</span></span>

<span data-ttu-id="c7097-145">プロジェクトの既定のビルドを消去します。</span><span class="sxs-lookup"><span data-stu-id="c7097-145">Clean a default build of the project:</span></span>

`dotnet clean`

<span data-ttu-id="c7097-146">リリース構成を使用してビルドされたプロジェクトを消去します。</span><span class="sxs-lookup"><span data-stu-id="c7097-146">Clean a project built using the Release configuration:</span></span>

`dotnet clean --configuration Release`
