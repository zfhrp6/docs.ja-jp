---
title: "dotnet-publish コマンド - .NET Core CLI"
description: "dotnet-publish コマンドは、.NET Core プロジェクトをディレクトリに発行します。"
keywords: "dotnet-publish, CLI, CLI コマンド, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: f2ef275a-7c5e-430a-8c30-65f52af62771
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a8a37b1eacab13682d4f4a2bea2f9ea248cdd9eb
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-publish"></a><span data-ttu-id="205a6-104">dotnet-publish</span><span class="sxs-lookup"><span data-stu-id="205a6-104">dotnet-publish</span></span>

## <a name="name"></a><span data-ttu-id="205a6-105">名前</span><span class="sxs-lookup"><span data-stu-id="205a6-105">Name</span></span>

<span data-ttu-id="205a6-106">`dotnet-publish` - ホスティング システムへの展開のため、アプリケーションとその依存関係をフォルダーにパックします。</span><span class="sxs-lookup"><span data-stu-id="205a6-106">`dotnet-publish` - Packs the application and its dependencies into a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="205a6-107">構文</span><span class="sxs-lookup"><span data-stu-id="205a6-107">Synopsis</span></span>

`dotnet publish [<PROJECT>] [-f|--framework] [-r|--runtime] [-o|--output] [-c|--configuration] [--version-suffix] [-v|--verbosity] [-h|--help]`

## <a name="description"></a><span data-ttu-id="205a6-108">説明</span><span class="sxs-lookup"><span data-stu-id="205a6-108">Description</span></span>

<span data-ttu-id="205a6-109">`dotnet publish` はアプリケーションをコンパイルし、プロジェクト ファイルに指定されたその依存関係を読み取り、結果のファイル セットをディレクトリに発行します。</span><span class="sxs-lookup"><span data-stu-id="205a6-109">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="205a6-110">出力の内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="205a6-110">The output will contain the following:</span></span>

* <span data-ttu-id="205a6-111">アセンブリの中間言語 (IL) コード (拡張子 `*.dll`)。</span><span class="sxs-lookup"><span data-stu-id="205a6-111">Intermediate Language (IL) code in an assembly with a `*.dll` extension.</span></span>
* <span data-ttu-id="205a6-112">*\*.deps.json* ファイル。プロジェクトのすべての依存関係が含まれます。</span><span class="sxs-lookup"><span data-stu-id="205a6-112">*\*.deps.json* file that contains all of the dependencies of the project.</span></span>
* <span data-ttu-id="205a6-113">*\*.runtime.config.json* ファイル。アプリケーションが想定する共有ランタイムと、ランタイムの他の構成オプション (ガベージ コレクションの種類など) を指定します。</span><span class="sxs-lookup"><span data-stu-id="205a6-113">*\*.runtime.config.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
* <span data-ttu-id="205a6-114">アプリケーションの依存関係。</span><span class="sxs-lookup"><span data-stu-id="205a6-114">The application's dependencies.</span></span> <span data-ttu-id="205a6-115">これらは NuGet キャッシュから出力フォルダーにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="205a6-115">These are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="205a6-116">`dotnet publish` コマンドの出力は、ホスティング システム (サーバー、PC、Mac、ラップトップなど) に展開して実行できる状態になっており、展開用にアプリケーションを準備するための正式にサポートされる唯一の方法です。</span><span class="sxs-lookup"><span data-stu-id="205a6-116">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution and is the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="205a6-117">プロジェクトに指定されている展開の種類によっては、ホスティング システムに .NET Core 共有ランタイムがインストールされている場合とされていない場合があります。</span><span class="sxs-lookup"><span data-stu-id="205a6-117">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="205a6-118">詳しくは、「[.NET Core アプリケーション展開](../deploying/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="205a6-118">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span> <span data-ttu-id="205a6-119">発行されるアプリケーションのディレクトリ構造については、「[Directory structure](/aspnet/core/hosting/directory-structure)」 (ディレクトリ構造) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="205a6-119">For the directory structure of a published application, see [Directory structure](/aspnet/core/hosting/directory-structure).</span></span>

## <a name="arguments"></a><span data-ttu-id="205a6-120">引数</span><span class="sxs-lookup"><span data-stu-id="205a6-120">Arguments</span></span>

`PROJECT` 

<span data-ttu-id="205a6-121">発行するプロジェクトです。指定されていない場合は、既定で現在のディレクトリに設定されます。</span><span class="sxs-lookup"><span data-stu-id="205a6-121">The project to publish, which defaults to the current directory if not specified.</span></span> 

## <a name="options"></a><span data-ttu-id="205a6-122">オプション</span><span class="sxs-lookup"><span data-stu-id="205a6-122">Options</span></span>

`-h|--help`

<span data-ttu-id="205a6-123">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="205a6-123">Prints out a short help for the command.</span></span>  

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="205a6-124">指定した[ターゲット フレームワーク](../../standard/frameworks.md)のアプリケーションを発行します。</span><span class="sxs-lookup"><span data-stu-id="205a6-124">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="205a6-125">ターゲット フレームワークはプロジェクト ファイルで指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="205a6-125">You must specify the target framework in the project file.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="205a6-126">指定されたランタイムのアプリケーションを発行します。</span><span class="sxs-lookup"><span data-stu-id="205a6-126">Publishes the application for a given runtime.</span></span> <span data-ttu-id="205a6-127">これは、[自己完結型の展開 (SCD)](../deploying/index.md#self-contained-deployments-scd) を作成するときに使われます。</span><span class="sxs-lookup"><span data-stu-id="205a6-127">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="205a6-128">ランタイム ID (RID) の一覧については、[RID カタログ](../rid-catalog.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="205a6-128">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="205a6-129">既定では、[フレームワークに依存する展開 (FDD)](../deploying/index.md#framework-dependent-deployments-fdd) が発行されます。</span><span class="sxs-lookup"><span data-stu-id="205a6-129">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="205a6-130">出力ディレクトリのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="205a6-130">Specifies the path for the output directory.</span></span> <span data-ttu-id="205a6-131">指定しないと、既定で、フレームワークに依存する展開の場合は *./bin/[configuration]/[framework]/* に、自己完結型の展開の場合は *./bin/[configuration]/[framework]/[runtime]* に設定されます。</span><span class="sxs-lookup"><span data-stu-id="205a6-131">If not specified, it defaults to *./bin/[configuration]/[framework]/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]* for a self-contained deployment.</span></span>

`-c|--configuration <CONFIGURATION>`

<span data-ttu-id="205a6-132">プロジェクトのビルド時に使用する構成です。</span><span class="sxs-lookup"><span data-stu-id="205a6-132">Configuration to use when building the project.</span></span> <span data-ttu-id="205a6-133">既定値は `Debug` です。</span><span class="sxs-lookup"><span data-stu-id="205a6-133">The default value is `Debug`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="205a6-134">プロジェクト ファイルのバージョン フィールドでアスタリスク (`*`) を置き換えるバージョン サフィックスを定義します。</span><span class="sxs-lookup"><span data-stu-id="205a6-134">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="205a6-135">コマンドの詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="205a6-135">Sets the verbosity level of the command.</span></span> <span data-ttu-id="205a6-136">指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。</span><span class="sxs-lookup"><span data-stu-id="205a6-136">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="205a6-137">例</span><span class="sxs-lookup"><span data-stu-id="205a6-137">Examples</span></span>

<span data-ttu-id="205a6-138">現在のディレクトリのプロジェクトを発行します。</span><span class="sxs-lookup"><span data-stu-id="205a6-138">Publish the project in the current directory:</span></span>

`dotnet publish`

<span data-ttu-id="205a6-139">指定されたプロジェクト ファイルを使用して、アプリケーションを発行します。</span><span class="sxs-lookup"><span data-stu-id="205a6-139">Publish the application using the specified project file:</span></span>

`dotnet publish ~/projects/app1/app1.csproj`
    
<span data-ttu-id="205a6-140">`netcoreapp1.1` フレームワークを使って現在のディレクトリ内のプロジェクトを発行します。</span><span class="sxs-lookup"><span data-stu-id="205a6-140">Publish the project in the current directory using the `netcoreapp1.1` framework:</span></span>

`dotnet publish --framework netcoreapp1.1`
    
<span data-ttu-id="205a6-141">`netcoreapp1.1` フレームワークと `OS X 10.10` のランタイム (この RID はプロジェクト ファイルに列挙しておく必要があります) を使って、現在のアプリケーションを発行します。</span><span class="sxs-lookup"><span data-stu-id="205a6-141">Publish the current application using the `netcoreapp1.1` framework and the runtime for `OS X 10.10` (you must list this RID in the project file).</span></span>

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

## <a name="see-also"></a><span data-ttu-id="205a6-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="205a6-142">See also</span></span>

* [<span data-ttu-id="205a6-143">ターゲット フレームワーク</span><span class="sxs-lookup"><span data-stu-id="205a6-143">Target frameworks</span></span>](../../standard/frameworks.md)
* [<span data-ttu-id="205a6-144">ランタイム識別子 (RID) のカタログ</span><span class="sxs-lookup"><span data-stu-id="205a6-144">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)

