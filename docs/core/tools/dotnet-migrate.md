---
title: dotnet migrate コマンド - .NET Core CLI
description: dotnet migrate コマンドは、プロジェクトとそのすべての依存関係を移行します。
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 67a845f7604dededd00746fa6b74a320b3e134fa
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34697106"
---
# <a name="dotnet-migrate"></a><span data-ttu-id="f8efb-103">dotnet の移行</span><span class="sxs-lookup"><span data-stu-id="f8efb-103">dotnet migrate</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="f8efb-104">name</span><span class="sxs-lookup"><span data-stu-id="f8efb-104">Name</span></span>

<span data-ttu-id="f8efb-105">`dotnet migrate` - Preview 2 .NET Core プロジェクトを .NET Core SDK 1.0 プロジェクトに移行します。</span><span class="sxs-lookup"><span data-stu-id="f8efb-105">`dotnet migrate` - Migrates a Preview 2 .NET Core project to a .NET Core SDK 1.0 project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f8efb-106">構文</span><span class="sxs-lookup"><span data-stu-id="f8efb-106">Synopsis</span></span>

```
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json] [-r|--report-file] [-s|--skip-project-references] [--skip-backup] [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file]
dotnet migrate [-h|--help]
```

## <a name="description"></a><span data-ttu-id="f8efb-107">説明</span><span class="sxs-lookup"><span data-stu-id="f8efb-107">Description</span></span>

<span data-ttu-id="f8efb-108">`dotnet migrate` コマンドは、有効な Preview 2 *project.json* ベースのプロジェクトを有効な .NET Core SDK 1.0 *csproj* プロジェクトに移行します。</span><span class="sxs-lookup"><span data-stu-id="f8efb-108">The `dotnet migrate` command migrates a valid Preview 2 *project.json*-based project to a valid .NET Core SDK 1.0 *csproj* project.</span></span>

<span data-ttu-id="f8efb-109">既定では、このコマンドは、ルート プロジェクトとルート プロジェクトに含まれるすべてのプロジェクト参照を移行します。</span><span class="sxs-lookup"><span data-stu-id="f8efb-109">By default, the command migrates the root project and any project references that the root project contains.</span></span> <span data-ttu-id="f8efb-110">この動作は、実行時に `--skip-project-references` オプションを使って、無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="f8efb-110">This behavior is disabled using the `--skip-project-references` option at runtime.</span></span>

<span data-ttu-id="f8efb-111">移行は次のアセットで実行できます。</span><span class="sxs-lookup"><span data-stu-id="f8efb-111">Migration can be performed on the following assets:</span></span>

* <span data-ttu-id="f8efb-112">1 つのプロジェクト。移行する *project.json* ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="f8efb-112">A single project by specifying the *project.json* file to migrate.</span></span>
* <span data-ttu-id="f8efb-113">*global.json* ファイルで指定されているすべてのディレクトリ。*global.json* ファイルへのパスを渡します。</span><span class="sxs-lookup"><span data-stu-id="f8efb-113">All of the directories specified in the *global.json* file by passing in a path to the *global.json* file.</span></span>
* <span data-ttu-id="f8efb-114">*solution.sln* ファイル。ソリューションで参照されているプロジェクトを移行します。</span><span class="sxs-lookup"><span data-stu-id="f8efb-114">A *solution.sln* file, where it migrates the projects referenced in the solution.</span></span>
* <span data-ttu-id="f8efb-115">特定のディレクトリのすべてのサブディレクトリ (再帰的)。</span><span class="sxs-lookup"><span data-stu-id="f8efb-115">On all subdirectories of the given directory recursively.</span></span>

<span data-ttu-id="f8efb-116">`dotnet migrate` コマンドは、`backup` ディレクトリ内に移行された *project.json* ファイルを保持します。ディレクトリが存在しない場合は作成されます。</span><span class="sxs-lookup"><span data-stu-id="f8efb-116">The `dotnet migrate` command keeps the migrated *project.json* file inside a `backup` directory, which it creates if the directory doesn't exist.</span></span> <span data-ttu-id="f8efb-117">この動作は、`--skip-backup` オプションを使ってオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="f8efb-117">This behavior is overridden using the `--skip-backup` option.</span></span>

<span data-ttu-id="f8efb-118">既定では、移行操作は、標準出力 (STDOUT) に移行プロセスの状態を出力します。</span><span class="sxs-lookup"><span data-stu-id="f8efb-118">By default, the migration operation outputs the state of the migration process to standard output (STDOUT).</span></span> <span data-ttu-id="f8efb-119">`--report-file <REPORT_FILE>` オプションを使うと、指定したファイルに出力が保存を指定します。</span><span class="sxs-lookup"><span data-stu-id="f8efb-119">If you use the `--report-file <REPORT_FILE>` option, the output is saved to the file specify.</span></span>

<span data-ttu-id="f8efb-120">`dotnet migrate` コマンドは、有効な Preview 2 *project.json* ベースのプロジェクトのみをサポートします。</span><span class="sxs-lookup"><span data-stu-id="f8efb-120">The `dotnet migrate` command only supports valid Preview 2 *project.json*-based projects.</span></span> <span data-ttu-id="f8efb-121">つまり、DNX または Preview 1 の *project.json* ベースのプロジェクトを MSBuild/csproj プロジェクトに直接移行するためには使えません。</span><span class="sxs-lookup"><span data-stu-id="f8efb-121">This means that you cannot use it to migrate DNX or Preview 1 *project.json*-based projects directly to MSBuild/csproj projects.</span></span> <span data-ttu-id="f8efb-122">最初にプロジェクトを Preview 2 *project.json* ベースのプロジェクトに手動で移行し、その後で `dotnet migrate` コマンドを使ってプロジェクトを移行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f8efb-122">You first need to manually migrate the project to a Preview 2 *project.json*-based project and then use the `dotnet migrate` command to migrate the project.</span></span>

## <a name="arguments"></a><span data-ttu-id="f8efb-123">引数</span><span class="sxs-lookup"><span data-stu-id="f8efb-123">Arguments</span></span>

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

<span data-ttu-id="f8efb-124">次のいずれかへのパスです。</span><span class="sxs-lookup"><span data-stu-id="f8efb-124">The path to one of the following:</span></span>

* <span data-ttu-id="f8efb-125">移行する *project.json* ファイル。</span><span class="sxs-lookup"><span data-stu-id="f8efb-125">a *project.json* file to migrate.</span></span>
* <span data-ttu-id="f8efb-126">*global.json* ファイル: *global.json* で指定されているフォルダーを移行します。</span><span class="sxs-lookup"><span data-stu-id="f8efb-126">a *global.json* file: the folders specified in *global.json* are migrated.</span></span>
* <span data-ttu-id="f8efb-127">*solution.sln* ファイル: ソリューションで参照されているプロジェクトを移行します。</span><span class="sxs-lookup"><span data-stu-id="f8efb-127">a *solution.sln* file: the projects referenced in the solution are migrated.</span></span>
* <span data-ttu-id="f8efb-128">移行するディレクトリ: 移行する *project.json* ファイルを再帰的に検索して、指定したディレクトリ内に移行します。</span><span class="sxs-lookup"><span data-stu-id="f8efb-128">a directory to migrate: recursively searches for *project.json* files to migrate inside the specified directory.</span></span>

<span data-ttu-id="f8efb-129">何も指定しない場合の既定値は現在のディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="f8efb-129">Defaults to current directory if nothing is specified.</span></span>

## <a name="options"></a><span data-ttu-id="f8efb-130">オプション</span><span class="sxs-lookup"><span data-stu-id="f8efb-130">Options</span></span>

`--format-report-file-json <REPORT_FILE>`

<span data-ttu-id="f8efb-131">ユーザー メッセージではなく、JSON として移行レポート ファイルを出力します。</span><span class="sxs-lookup"><span data-stu-id="f8efb-131">Output migration report file as JSON rather than user messages.</span></span>

`-h|--help`

<span data-ttu-id="f8efb-132">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="f8efb-132">Prints out a short help for the command.</span></span>

`-r|--report-file <REPORT_FILE>`

<span data-ttu-id="f8efb-133">移行レポートをコンソールだけでなく、ファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="f8efb-133">Output migration report to a file in addition to the console.</span></span>

`-s|--skip-project-references [Debug|Release]`

<span data-ttu-id="f8efb-134">プロジェクト参照の移行をスキップします。</span><span class="sxs-lookup"><span data-stu-id="f8efb-134">Skip migrating project references.</span></span> <span data-ttu-id="f8efb-135">既定では、プロジェクト参照は再帰的に移行されます。</span><span class="sxs-lookup"><span data-stu-id="f8efb-135">By default, project references are migrated recursively.</span></span>

`--skip-backup`

<span data-ttu-id="f8efb-136">移行が成功した後、*project.json*、*global.json*、および *\*.xproj* の `backup` ディレクトリへの移動をスキップします。</span><span class="sxs-lookup"><span data-stu-id="f8efb-136">Skip moving *project.json*, *global.json*, and *\*.xproj* to a `backup` directory after successful migration.</span></span>

`-t|--template-file <TEMPLATE_FILE>`

<span data-ttu-id="f8efb-137">移行に使用するテンプレートの csproj ファイル。</span><span class="sxs-lookup"><span data-stu-id="f8efb-137">Template csproj file to use for migration.</span></span> <span data-ttu-id="f8efb-138">既定では、`dotnet new console` によってドロップされるテンプレートと同じテンプレートが使用されます。</span><span class="sxs-lookup"><span data-stu-id="f8efb-138">By default, the same template as the one dropped by `dotnet new console` is used.</span></span>

`-v|--sdk-package-version <VERSION>`

<span data-ttu-id="f8efb-139">移行されたアプリで参照される sdk パッケージのバージョンです。</span><span class="sxs-lookup"><span data-stu-id="f8efb-139">The version of the sdk package that's referenced in the migrated app.</span></span> <span data-ttu-id="f8efb-140">既定値は、`dotnet new` 内の SDK のバージョンです。</span><span class="sxs-lookup"><span data-stu-id="f8efb-140">The default is the version of the SDK in `dotnet new`.</span></span>

`-x|--xproj-file <FILE>`

<span data-ttu-id="f8efb-141">使用する xproj ファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="f8efb-141">The path to the xproj file to use.</span></span> <span data-ttu-id="f8efb-142">プロジェクト ディレクトリに複数の xproj がある場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="f8efb-142">Required when there is more than one xproj in a project directory.</span></span>

## <a name="examples"></a><span data-ttu-id="f8efb-143">使用例</span><span class="sxs-lookup"><span data-stu-id="f8efb-143">Examples</span></span>

<span data-ttu-id="f8efb-144">現在のディレクトリのプロジェクトとそのプロジェクト間の依存関係をすべて移行します。</span><span class="sxs-lookup"><span data-stu-id="f8efb-144">Migrate a project in the current directory and all of its project-to-project dependencies:</span></span>

`dotnet migrate`

<span data-ttu-id="f8efb-145">*global.json* ファイルに含まれるすべてのプロジェクトを移行します。</span><span class="sxs-lookup"><span data-stu-id="f8efb-145">Migrate all projects that *global.json* file includes:</span></span>

`dotnet migrate path/to/global.json`

<span data-ttu-id="f8efb-146">現在のプロジェクトのみを移行し、プロジェクト間 (P2P) の依存関係は移行しません。</span><span class="sxs-lookup"><span data-stu-id="f8efb-146">Migrate only the current project and no project-to-project (P2P) dependencies.</span></span> <span data-ttu-id="f8efb-147">また、特定の SDK バージョンを使います。</span><span class="sxs-lookup"><span data-stu-id="f8efb-147">Also, use a specific SDK version:</span></span>

`dotnet migrate -s -v 1.0.0-preview4`