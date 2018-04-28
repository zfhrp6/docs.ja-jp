---
title: dotnet migrate コマンド - .NET Core CLI
description: dotnet migrate コマンドは、プロジェクトとそのすべての依存関係を移行します。
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 796a241fea2c85fb03729a9cb0ed79682ac0dcee
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-migrate"></a><span data-ttu-id="cb040-103">dotnet の移行</span><span class="sxs-lookup"><span data-stu-id="cb040-103">dotnet migrate</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="cb040-104">name</span><span class="sxs-lookup"><span data-stu-id="cb040-104">Name</span></span>

<span data-ttu-id="cb040-105">`dotnet migrate` - Preview 2 .NET Core プロジェクトを .NET Core SDK 1.0 プロジェクトに移行します。</span><span class="sxs-lookup"><span data-stu-id="cb040-105">`dotnet migrate` - Migrates a Preview 2 .NET Core project to a .NET Core SDK 1.0 project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="cb040-106">構文</span><span class="sxs-lookup"><span data-stu-id="cb040-106">Synopsis</span></span>

`dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file] [-s|--skip-project-references] [-r|--report-file] [--format-report-file-json] [--skip-backup] [-h|--help]`

## <a name="description"></a><span data-ttu-id="cb040-107">説明</span><span class="sxs-lookup"><span data-stu-id="cb040-107">Description</span></span>

<span data-ttu-id="cb040-108">`dotnet migrate` コマンドは、有効な Preview 2 *project.json* ベースのプロジェクトを有効な .NET Core SDK 1.0 *csproj* プロジェクトに移行します。</span><span class="sxs-lookup"><span data-stu-id="cb040-108">The `dotnet migrate` command migrates a valid Preview 2 *project.json*-based project to a valid .NET Core SDK 1.0 *csproj* project.</span></span> 

<span data-ttu-id="cb040-109">既定では、このコマンドは、ルート プロジェクトとルート プロジェクトに含まれるすべてのプロジェクト参照を移行します。</span><span class="sxs-lookup"><span data-stu-id="cb040-109">By default, the command migrates the root project and any project references that the root project contains.</span></span> <span data-ttu-id="cb040-110">この動作は、実行時に `--skip-project-references` オプションを使って、無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="cb040-110">This behavior is disabled using the `--skip-project-references` option at runtime.</span></span> 

<span data-ttu-id="cb040-111">移行は、次のように実行されます。</span><span class="sxs-lookup"><span data-stu-id="cb040-111">Migration is performed on the following:</span></span>

* <span data-ttu-id="cb040-112">1 つのプロジェクト。移行する *project.json* ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="cb040-112">A single project by specifying the *project.json* file to migrate.</span></span>
* <span data-ttu-id="cb040-113">*global.json* ファイルで指定されているすべてのディレクトリ。*global.json* ファイルへのパスを渡します。</span><span class="sxs-lookup"><span data-stu-id="cb040-113">All of the directories specified in the *global.json* file by passing in a path to the *global.json* file.</span></span>
* <span data-ttu-id="cb040-114">*solution.sln* ファイル。ソリューションで参照されているプロジェクトを移行します。</span><span class="sxs-lookup"><span data-stu-id="cb040-114">A *solution.sln* file, where it migrates the projects referenced in the solution.</span></span>
* <span data-ttu-id="cb040-115">特定のディレクトリのすべてのサブディレクトリ (再帰的)。</span><span class="sxs-lookup"><span data-stu-id="cb040-115">On all sub-directories of the given directory recursively.</span></span>

<span data-ttu-id="cb040-116">`dotnet migrate` コマンドは、`backup` ディレクトリ内に移行された *project.json* ファイルを保持します。ディレクトリが存在しない場合は作成されます。</span><span class="sxs-lookup"><span data-stu-id="cb040-116">The `dotnet migrate` command keeps the migrated *project.json* file inside a `backup` directory, which it creates if the directory doesn't exist.</span></span> <span data-ttu-id="cb040-117">この動作は、`--skip-backup` オプションを使ってオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="cb040-117">This behavior is overridden using the `--skip-backup` option.</span></span>

<span data-ttu-id="cb040-118">既定では、移行操作は、標準出力 (STDOUT) に移行プロセスの状態を出力します。</span><span class="sxs-lookup"><span data-stu-id="cb040-118">By default, the migration operation outputs the state of the migration process to standard output (STDOUT).</span></span> <span data-ttu-id="cb040-119">`--report-file <REPORT_FILE>` オプションを使うと、指定したファイルに出力が保存を指定します。</span><span class="sxs-lookup"><span data-stu-id="cb040-119">If you use the `--report-file <REPORT_FILE>` option, the output is saved to the file specify.</span></span> 

<span data-ttu-id="cb040-120">`dotnet migrate` コマンドは、有効な Preview 2 *project.json* ベースのプロジェクトのみをサポートします。</span><span class="sxs-lookup"><span data-stu-id="cb040-120">The `dotnet migrate` command only supports valid Preview 2 *project.json*-based projects.</span></span> <span data-ttu-id="cb040-121">つまり、DNX または Preview 1 の *project.json* ベースのプロジェクトを MSBuild/csproj プロジェクトに直接移行するためには使えません。</span><span class="sxs-lookup"><span data-stu-id="cb040-121">This means that you cannot use it to migrate DNX or Preview 1 *project.json*-based projects directly to MSBuild/csproj projects.</span></span> <span data-ttu-id="cb040-122">最初にプロジェクトを Preview 2 *project.json* ベースのプロジェクトに手動で移行し、その後で `dotnet migrate` コマンドを使ってプロジェクトを移行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb040-122">You first need to manually migrate the project to a Preview 2 *project.json*-based project and then use the `dotnet migrate` command to migrate the project.</span></span>

## <a name="arguments"></a><span data-ttu-id="cb040-123">引数</span><span class="sxs-lookup"><span data-stu-id="cb040-123">Arguments</span></span>

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

<span data-ttu-id="cb040-124">次のいずれかへのパスです。</span><span class="sxs-lookup"><span data-stu-id="cb040-124">The path to one of the following:</span></span>

* <span data-ttu-id="cb040-125">移行する *project.json* ファイル。</span><span class="sxs-lookup"><span data-stu-id="cb040-125">a *project.json* file to migrate.</span></span>
* <span data-ttu-id="cb040-126">*global.json* ファイル。*global.json* で指定されているフォルダーを移行します。</span><span class="sxs-lookup"><span data-stu-id="cb040-126">a *global.json* file, it will migrate the folders specified in *global.json*.</span></span>
* <span data-ttu-id="cb040-127">*solution.sln* ファイル。ソリューションで参照されているプロジェクトを移行します。</span><span class="sxs-lookup"><span data-stu-id="cb040-127">a *solution.sln* file, it will migrate the projects referenced in the solution.</span></span>
* <span data-ttu-id="cb040-128">移行するディレクトリ。移行する *project.json* ファイルを再帰的に検索します。</span><span class="sxs-lookup"><span data-stu-id="cb040-128">a directory to migrate, it will recursively search for *project.json* files to migrate.</span></span>

<span data-ttu-id="cb040-129">何も指定しない場合の既定値は現在のディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="cb040-129">Defaults to current directory if nothing is specified.</span></span>

## <a name="options"></a><span data-ttu-id="cb040-130">オプション</span><span class="sxs-lookup"><span data-stu-id="cb040-130">Options</span></span>

`-h|--help`

<span data-ttu-id="cb040-131">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="cb040-131">Prints out a short help for the command.</span></span>

`-t|--template-file <TEMPLATE_FILE>`

<span data-ttu-id="cb040-132">移行に使用するテンプレートの csproj ファイル。</span><span class="sxs-lookup"><span data-stu-id="cb040-132">Template csproj file to use for migration.</span></span> <span data-ttu-id="cb040-133">既定では、`dotnet new console` によってドロップされるテンプレートと同じテンプレートが使用されます。</span><span class="sxs-lookup"><span data-stu-id="cb040-133">By default, the same template as the one dropped by `dotnet new console` is used.</span></span>

`-v|--sdk-package-version <VERSION>`

<span data-ttu-id="cb040-134">移行されたアプリで参照される sdk パッケージのバージョンです。</span><span class="sxs-lookup"><span data-stu-id="cb040-134">The version of the sdk package that's referenced in the migrated app.</span></span> <span data-ttu-id="cb040-135">既定値は、`dotnet new` 内の SDK のバージョンです。</span><span class="sxs-lookup"><span data-stu-id="cb040-135">The default is the version of the SDK in `dotnet new`.</span></span>

`-x|--xproj-file <FILE>`

<span data-ttu-id="cb040-136">使用する xproj ファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="cb040-136">The path to the xproj file to use.</span></span> <span data-ttu-id="cb040-137">プロジェクト ディレクトリに複数の xproj がある場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="cb040-137">Required when there is more than one xproj in a project directory.</span></span>

`-s|--skip-project-references [Debug|Release]`

<span data-ttu-id="cb040-138">プロジェクト参照の移行をスキップします。</span><span class="sxs-lookup"><span data-stu-id="cb040-138">Skip migrating project references.</span></span> <span data-ttu-id="cb040-139">既定では、プロジェクト参照は再帰的に移行されます。</span><span class="sxs-lookup"><span data-stu-id="cb040-139">By default, project references are migrated recursively.</span></span>

`-r|--report-file <REPORT_FILE>`

<span data-ttu-id="cb040-140">移行レポートをコンソールだけでなく、ファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="cb040-140">Output migration report to a file in addition to the console.</span></span>

`--format-report-file-json <REPORT_FILE>`

<span data-ttu-id="cb040-141">ユーザー メッセージではなく、JSON として移行レポート ファイルを出力します。</span><span class="sxs-lookup"><span data-stu-id="cb040-141">Output migration report file as JSON rather than user messages.</span></span>

`--skip-backup`

<span data-ttu-id="cb040-142">移行が成功した後、*project.json*、*global.json*、および *\*.xproj* の `backup` ディレクトリへの移動をスキップします。</span><span class="sxs-lookup"><span data-stu-id="cb040-142">Skip moving *project.json*, *global.json*, and *\*.xproj* to a `backup` directory after successful migration.</span></span>

## <a name="examples"></a><span data-ttu-id="cb040-143">使用例</span><span class="sxs-lookup"><span data-stu-id="cb040-143">Examples</span></span>

<span data-ttu-id="cb040-144">現在のディレクトリのプロジェクトとそのプロジェクト間の依存関係をすべて移行します。</span><span class="sxs-lookup"><span data-stu-id="cb040-144">Migrate a project in the current directory and all of its project-to-project dependencies:</span></span>

`dotnet migrate`

<span data-ttu-id="cb040-145">*global.json* ファイルに含まれるすべてのプロジェクトを移行します。</span><span class="sxs-lookup"><span data-stu-id="cb040-145">Migrate all projects that *global.json* file includes:</span></span>

`dotnet migrate path/to/global.json`

<span data-ttu-id="cb040-146">現在のプロジェクトのみを移行し、プロジェクト間 (P2P) の依存関係は移行しません。</span><span class="sxs-lookup"><span data-stu-id="cb040-146">Migrate only the current project and no project-to-project (P2P) dependencies.</span></span> <span data-ttu-id="cb040-147">また、特定の SDK バージョンを使います。</span><span class="sxs-lookup"><span data-stu-id="cb040-147">Also, use a specific SDK version:</span></span>

`dotnet migrate -s -v 1.0.0-preview4`
