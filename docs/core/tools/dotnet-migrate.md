---
title: "dotnet-migrate コマンド - .NET Core CLI"
description: "dotnet-migrate コマンドは、プロジェクトとそのすべての依存関係を移行します。"
keywords: "dotnet-migrate, CLI, CLI コマンド, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 0da07253-5ae1-42e9-9455-bffee9950952
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: e8491d69b2e0df7b3bd2741e34abdb9631777019
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-migrate"></a><span data-ttu-id="8140c-104">dotnet-migrate</span><span class="sxs-lookup"><span data-stu-id="8140c-104">dotnet-migrate</span></span>

## <a name="name"></a><span data-ttu-id="8140c-105">名前</span><span class="sxs-lookup"><span data-stu-id="8140c-105">Name</span></span>

<span data-ttu-id="8140c-106">`dotnet-migrate` - Preview 2 .NET Core プロジェクトを .NET Core SDK 1.0 プロジェクトに移行します。</span><span class="sxs-lookup"><span data-stu-id="8140c-106">`dotnet-migrate` - Migrates a Preview 2 .NET Core project to a .NET Core SDK 1.0 project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="8140c-107">構文</span><span class="sxs-lookup"><span data-stu-id="8140c-107">Synopsis</span></span>

`dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file] [-s|--skip-project-references] [-r|--report-file] [--format-report-file-json] [--skip-backup] [-h|--help]`

## <a name="description"></a><span data-ttu-id="8140c-108">説明</span><span class="sxs-lookup"><span data-stu-id="8140c-108">Description</span></span>

<span data-ttu-id="8140c-109">`dotnet migrate` コマンドは、有効な Preview 2 *project.json* ベースのプロジェクトを有効な .NET Core SDK 1.0 *csproj* プロジェクトに移行します。</span><span class="sxs-lookup"><span data-stu-id="8140c-109">The `dotnet migrate` command migrates a valid Preview 2 *project.json*-based project to a valid .NET Core SDK 1.0 *csproj* project.</span></span> 

<span data-ttu-id="8140c-110">既定では、このコマンドは、ルート プロジェクトとルート プロジェクトに含まれるすべてのプロジェクト参照を移行します。</span><span class="sxs-lookup"><span data-stu-id="8140c-110">By default, the command migrates the root project and any project references that the root project contains.</span></span> <span data-ttu-id="8140c-111">この動作は、実行時に `--skip-project-references` オプションを使って、無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="8140c-111">This behavior is disabled using the `--skip-project-references` option at runtime.</span></span> 

<span data-ttu-id="8140c-112">移行は、次のように実行されます。</span><span class="sxs-lookup"><span data-stu-id="8140c-112">Migration is performed on the following:</span></span>

* <span data-ttu-id="8140c-113">1 つのプロジェクト。移行する *project.json* ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="8140c-113">A single project by specifying the *project.json* file to migrate.</span></span>
* <span data-ttu-id="8140c-114">*global.json* ファイルで指定されているすべてのディレクトリ。*global.json* ファイルへのパスを渡します。</span><span class="sxs-lookup"><span data-stu-id="8140c-114">All of the directories specified in the *global.json* file by passing in a path to the *global.json* file.</span></span>
* <span data-ttu-id="8140c-115">*solution.sln* ファイル。ソリューションで参照されているプロジェクトを移行します。</span><span class="sxs-lookup"><span data-stu-id="8140c-115">A *solution.sln* file, where it migrates the projects referenced in the solution.</span></span>
* <span data-ttu-id="8140c-116">特定のディレクトリのすべてのサブディレクトリ (再帰的)。</span><span class="sxs-lookup"><span data-stu-id="8140c-116">On all sub-directories of the given directory recursively.</span></span>

<span data-ttu-id="8140c-117">`dotnet migrate` コマンドは、`backup` ディレクトリ内に移行された *project.json* ファイルを保持します。ディレクトリが存在しない場合は作成されます。</span><span class="sxs-lookup"><span data-stu-id="8140c-117">The `dotnet migrate` command keeps the migrated *project.json* file inside a `backup` directory, which it creates if the directory doesn't exist.</span></span> <span data-ttu-id="8140c-118">この動作は、`--skip-backup` オプションを使ってオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="8140c-118">This behavior is overriden using the `--skip-backup` option.</span></span> 

<span data-ttu-id="8140c-119">既定では、移行操作は、標準出力 (STDOUT) に移行プロセスの状態を出力します。</span><span class="sxs-lookup"><span data-stu-id="8140c-119">By default, the migration operation outputs the state of the migration process to standard output (STDOUT).</span></span> <span data-ttu-id="8140c-120">`--report-file <REPORT_FILE>` オプションを使うと、指定したファイルに出力が保存を指定します。</span><span class="sxs-lookup"><span data-stu-id="8140c-120">If you use the `--report-file <REPORT_FILE>` option, the output is saved to the file specify.</span></span> 

<span data-ttu-id="8140c-121">`dotnet migrate` コマンドは、有効な Preview 2 *project.json* ベースのプロジェクトのみをサポートします。</span><span class="sxs-lookup"><span data-stu-id="8140c-121">The `dotnet migrate` command only supports valid Preview 2 *project.json*-based projects.</span></span> <span data-ttu-id="8140c-122">つまり、DNX または Preview 1 の *project.json* ベースのプロジェクトを MSBuild/csproj プロジェクトに直接移行するためには使えません。</span><span class="sxs-lookup"><span data-stu-id="8140c-122">This means that you cannot use it to migrate DNX or Preview 1 *project.json*-based projects directly to MSBuild/csproj projects.</span></span> <span data-ttu-id="8140c-123">最初にプロジェクトを Preview 2 *project.json* ベースのプロジェクトに手動で移行し、その後で `dotnet migrate` コマンドを使ってプロジェクトを移行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8140c-123">You first need to manually migrate the project to a Preview 2 *project.json*-based project and then use the `dotnet migrate` command to migrate the project.</span></span>

## <a name="arguments"></a><span data-ttu-id="8140c-124">引数</span><span class="sxs-lookup"><span data-stu-id="8140c-124">Arguments</span></span>

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

<span data-ttu-id="8140c-125">次のいずれかへのパスです。</span><span class="sxs-lookup"><span data-stu-id="8140c-125">The path to one of the following:</span></span>

* <span data-ttu-id="8140c-126">移行する *project.json* ファイル。</span><span class="sxs-lookup"><span data-stu-id="8140c-126">a *project.json* file to migrate.</span></span>
* <span data-ttu-id="8140c-127">*global.json* ファイル。*global.json* で指定されているフォルダーを移行します。</span><span class="sxs-lookup"><span data-stu-id="8140c-127">a *global.json* file, it will migrate the folders specified in *global.json*.</span></span>
* <span data-ttu-id="8140c-128">*solution.sln* ファイル。ソリューションで参照されているプロジェクトを移行します。</span><span class="sxs-lookup"><span data-stu-id="8140c-128">a *solution.sln* file, it will migrate the projects referenced in the solution.</span></span>
* <span data-ttu-id="8140c-129">移行するディレクトリ。移行する *project.json* ファイルを再帰的に検索します。</span><span class="sxs-lookup"><span data-stu-id="8140c-129">a directory to migrate, it will recursively search for *project.json* files to migrate.</span></span>

<span data-ttu-id="8140c-130">何も指定しない場合の既定値は現在のディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="8140c-130">Defaults to current directory if nothing is specified.</span></span>

## <a name="options"></a><span data-ttu-id="8140c-131">オプション</span><span class="sxs-lookup"><span data-stu-id="8140c-131">Options</span></span>

`-h|--help`

<span data-ttu-id="8140c-132">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="8140c-132">Prints out a short help for the command.</span></span>  

`-t|--template-file <TEMPLATE_FILE>`

<span data-ttu-id="8140c-133">移行に使用するテンプレートの csproj ファイル。</span><span class="sxs-lookup"><span data-stu-id="8140c-133">Template csproj file to use for migration.</span></span> <span data-ttu-id="8140c-134">既定では、`dotnet new console` によってドロップされるテンプレートと同じテンプレートが使用されます。</span><span class="sxs-lookup"><span data-stu-id="8140c-134">By default, the same template as the one dropped by `dotnet new console` is used.</span></span> 

`-v|--sdk-package-version <VERSION>`

<span data-ttu-id="8140c-135">移行されたアプリで参照される sdk パッケージのバージョンです。</span><span class="sxs-lookup"><span data-stu-id="8140c-135">The version of the sdk package that's referenced in the migrated app.</span></span> <span data-ttu-id="8140c-136">既定値は、`dotnet new` 内の SDK のバージョンです。</span><span class="sxs-lookup"><span data-stu-id="8140c-136">The default is the version of the SDK in `dotnet new`.</span></span>

`-x|--xproj-file <FILE>`

<span data-ttu-id="8140c-137">使用する xproj ファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="8140c-137">The path to the xproj file to use.</span></span> <span data-ttu-id="8140c-138">プロジェクト ディレクトリに複数の xproj がある場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="8140c-138">Required when there is more than one xproj in a project directory.</span></span>

`-s|--skip-project-references [Debug|Release]`

<span data-ttu-id="8140c-139">プロジェクト参照の移行をスキップします。</span><span class="sxs-lookup"><span data-stu-id="8140c-139">Skip migrating project references.</span></span> <span data-ttu-id="8140c-140">既定では、プロジェクト参照は再帰的に移行されます。</span><span class="sxs-lookup"><span data-stu-id="8140c-140">By default, project references are migrated recursively.</span></span>

`-r|--report-file <REPORT_FILE>`

<span data-ttu-id="8140c-141">移行レポートをコンソールだけでなく、ファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="8140c-141">Output migration report to a file in addition to the console.</span></span>

`--format-report-file-json <REPORT_FILE>`

<span data-ttu-id="8140c-142">ユーザー メッセージではなく、JSON として移行レポート ファイルを出力します。</span><span class="sxs-lookup"><span data-stu-id="8140c-142">Output migration report file as JSON rather than user messages.</span></span>

`--skip-backup`

<span data-ttu-id="8140c-143">移行が成功した後、*project.json*、*global.json*、および *\*.xproj* の `backup` ディレクトリへの移動をスキップします。</span><span class="sxs-lookup"><span data-stu-id="8140c-143">Skip moving *project.json*, *global.json*, and *\*.xproj* to a `backup` directory after successful migration.</span></span>

## <a name="examples"></a><span data-ttu-id="8140c-144">例</span><span class="sxs-lookup"><span data-stu-id="8140c-144">Examples</span></span>

<span data-ttu-id="8140c-145">現在のディレクトリのプロジェクトとそのプロジェクト間の依存関係をすべて移行します。</span><span class="sxs-lookup"><span data-stu-id="8140c-145">Migrate a project in the current directory and all of its project-to-project dependencies:</span></span>

`dotnet migrate`

<span data-ttu-id="8140c-146">*global.json* ファイルに含まれるすべてのプロジェクトを移行します。</span><span class="sxs-lookup"><span data-stu-id="8140c-146">Migrate all projects that *global.json* file includes:</span></span>

`dotnet migrate path/to/global.json`

<span data-ttu-id="8140c-147">現在のプロジェクトのみを移行し、プロジェクト間 (P2P) の依存関係は移行しません。</span><span class="sxs-lookup"><span data-stu-id="8140c-147">Migrate only the current project and no project-to-project (P2P) dependencies.</span></span> <span data-ttu-id="8140c-148">また、特定の SDK バージョンを使います。</span><span class="sxs-lookup"><span data-stu-id="8140c-148">Also, use a specific SDK version:</span></span>

`dotnet migrate -s -v 1.0.0-preview4`

