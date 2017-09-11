---
title: "dotnet-clean コマンド - .NET Core CLI"
description: "dotnet-clean コマンドは現在のディレクトリを消去します。"
keywords: "dotnet-clean, CLI, CLI コマンド, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: eff65fa1-bab4-4421-8260-d0a284b690b2
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 10222781d5bff596d1b7883bc73097758e878235
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-clean"></a><span data-ttu-id="746dd-104">dotnet-clean</span><span class="sxs-lookup"><span data-stu-id="746dd-104">dotnet-clean</span></span>

## <a name="name"></a><span data-ttu-id="746dd-105">名前</span><span class="sxs-lookup"><span data-stu-id="746dd-105">Name</span></span>

<span data-ttu-id="746dd-106">`dotnet-clean` - プロジェクトの出力を消去します。</span><span class="sxs-lookup"><span data-stu-id="746dd-106">`dotnet-clean` - Cleans the output of a project.</span></span> 

## <a name="synopsis"></a><span data-ttu-id="746dd-107">構文</span><span class="sxs-lookup"><span data-stu-id="746dd-107">Synopsis</span></span>

`dotnet clean [<PROJECT>] [-o|--output] [-f|--framework] [-c|--configuration] [-v|--verbosity] [-h|--help]`

## <a name="description"></a><span data-ttu-id="746dd-108">説明</span><span class="sxs-lookup"><span data-stu-id="746dd-108">Description</span></span>

<span data-ttu-id="746dd-109">`dotnet clean` コマンドは、以前のビルドの出力を消去します。</span><span class="sxs-lookup"><span data-stu-id="746dd-109">The `dotnet clean` command cleans the output of the previous build.</span></span> <span data-ttu-id="746dd-110">[MSBuild ターゲット](/visualstudio/msbuild/msbuild-targets)として実装されます。そのため、コマンドの実行時にプロジェクトが評価されます。</span><span class="sxs-lookup"><span data-stu-id="746dd-110">It's implemented as an [MSBuild target](/visualstudio/msbuild/msbuild-targets), so the project is evaluated when the command is run.</span></span> <span data-ttu-id="746dd-111">ビルド中に作成された出力のみが消去されます。</span><span class="sxs-lookup"><span data-stu-id="746dd-111">Only the outputs created during the build are cleaned.</span></span> <span data-ttu-id="746dd-112">中間 (*obj*) と最終出力 (*bin*) フォルダーの両方が消去されます。</span><span class="sxs-lookup"><span data-stu-id="746dd-112">Both intermediate (*obj*) and final output (*bin*) folders are cleaned.</span></span>

## <a name="arguments"></a><span data-ttu-id="746dd-113">引数</span><span class="sxs-lookup"><span data-stu-id="746dd-113">Arguments</span></span>

`PROJECT`

<span data-ttu-id="746dd-114">消去する MSBuild プロジェクトです。</span><span class="sxs-lookup"><span data-stu-id="746dd-114">The MSBuild project to clean.</span></span> <span data-ttu-id="746dd-115">プロジェクト ファイルを指定しない場合、MSBuild は、現在の作業ディレクトリから *proj* で終わるファイル名拡張子を検索し、そのファイルを使います。</span><span class="sxs-lookup"><span data-stu-id="746dd-115">If a project file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="746dd-116">オプション</span><span class="sxs-lookup"><span data-stu-id="746dd-116">Options</span></span>

`-h|--help`

<span data-ttu-id="746dd-117">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="746dd-117">Prints out a short help for the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="746dd-118">ビルド出力が配置されたディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="746dd-118">Directory in which the build outputs are placed.</span></span> <span data-ttu-id="746dd-119">プロジェクトのビルド時にフレームワークを指定した場合、出力ディレクトリ スイッチと共に `-f|--framework <FRAMEWORK>` スイッチを指定します。</span><span class="sxs-lookup"><span data-stu-id="746dd-119">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="746dd-120">ビルド時に指定された[フレームワーク](../../standard/frameworks.md)です。</span><span class="sxs-lookup"><span data-stu-id="746dd-120">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="746dd-121">フレームワークは、[プロジェクト ファイル](csproj.md)で定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="746dd-121">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="746dd-122">ビルド時にフレームワークを指定した場合は、消去時にフレームワークを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="746dd-122">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

`-c|--configuration <CONFIGURATION>`

<span data-ttu-id="746dd-123">構成を定義します。</span><span class="sxs-lookup"><span data-stu-id="746dd-123">Defines the configuration.</span></span> <span data-ttu-id="746dd-124">省略した場合は、既定で `Debug` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="746dd-124">If omitted, it defaults to `Debug`.</span></span> <span data-ttu-id="746dd-125">このプロパティは、ビルド時に指定した場合にのみ、消去時にも必要です。</span><span class="sxs-lookup"><span data-stu-id="746dd-125">This property is only required when cleaning if you specified it during build time.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="746dd-126">コマンドの詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="746dd-126">Sets the verbosity level of the command.</span></span> <span data-ttu-id="746dd-127">指定できるレベルは、q[uiet]、m[inimal]、n[ormal]、d[etailed]、diag[nostic] です。</span><span class="sxs-lookup"><span data-stu-id="746dd-127">Allowed levels are q[uiet], m[inimal], n[ormal], d[etailed], and diag[nostic].</span></span>

## <a name="examples"></a><span data-ttu-id="746dd-128">例</span><span class="sxs-lookup"><span data-stu-id="746dd-128">Examples</span></span>

<span data-ttu-id="746dd-129">プロジェクトの既定のビルドを消去します。</span><span class="sxs-lookup"><span data-stu-id="746dd-129">Clean a default build of the project:</span></span>

`dotnet clean`

<span data-ttu-id="746dd-130">リリース構成を使用してビルドされたプロジェクトを消去します。</span><span class="sxs-lookup"><span data-stu-id="746dd-130">Clean a project built using the Release configuration:</span></span>

`dotnet clean --configuration Release`

