---
title: "dotnet restore コマンド - .NET Core CLI"
description: "dotnet restore コマンドを使用して、依存関係とプロジェクト固有のツールを復元する方法について説明します。"
keywords: "dotnet-restore, CLI, CLI コマンド, .NET Core"
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.translationtype: HT
ms.sourcegitcommit: 019461964ba63d874ce86511474aa37b4342bbc4
ms.openlocfilehash: 86de979257d4e1be3a29d8876494b7f4966e5b1c
ms.contentlocale: ja-jp
ms.lasthandoff: 08/29/2017

---
# <a name="dotnet-restore"></a><span data-ttu-id="3c818-104">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="3c818-104">dotnet restore</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="3c818-105">名前</span><span class="sxs-lookup"><span data-stu-id="3c818-105">Name</span></span>

<span data-ttu-id="3c818-106">`dotnet restore` - プロジェクトの依存関係とツールを復元します。</span><span class="sxs-lookup"><span data-stu-id="3c818-106">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="3c818-107">構文</span><span class="sxs-lookup"><span data-stu-id="3c818-107">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="3c818-108">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="3c818-108">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--force] [--ignore-failed-sources] [--no-cache] [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="3c818-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="3c818-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--ignore-failed-sources] [--no-cache] [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="3c818-110">説明</span><span class="sxs-lookup"><span data-stu-id="3c818-110">Description</span></span>

<span data-ttu-id="3c818-111">`dotnet restore` コマンドでは NuGet を使用して、依存関係と、プロジェクト ファイルに指定されているプロジェクト固有のツールを復元します。</span><span class="sxs-lookup"><span data-stu-id="3c818-111">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span> <span data-ttu-id="3c818-112">既定では、依存関係とツールの復元は並列に実行されます。</span><span class="sxs-lookup"><span data-stu-id="3c818-112">By default, the restoration of dependencies and tools are performed in parallel.</span></span>

<span data-ttu-id="3c818-113">依存関係を復元するには、NuGet で、パッケージを配置するフィードが必要になります。</span><span class="sxs-lookup"><span data-stu-id="3c818-113">In order to restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="3c818-114">フィードは、通常、*NuGet.config* 構成ファイルを通じて提供されます。</span><span class="sxs-lookup"><span data-stu-id="3c818-114">Feeds are usually provided via the *NuGet.config* configuration file.</span></span> <span data-ttu-id="3c818-115">既定の構成ファイルは、CLI ツールがインストールされている場合に提供されます。</span><span class="sxs-lookup"><span data-stu-id="3c818-115">A default configuration file is provided when the CLI tools are installed.</span></span> <span data-ttu-id="3c818-116">プロジェクト ディレクトリに独自の *NuGet.config* ファイルを作成して、さらにフィードを指定します。</span><span class="sxs-lookup"><span data-stu-id="3c818-116">You specify additional feeds by creating your own *NuGet.config* file in the project directory.</span></span> <span data-ttu-id="3c818-117">コマンド プロンプトで呼び出すごとにフィードをさらに指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="3c818-117">You also specify additional feeds per invocation at a command prompt.</span></span>

<span data-ttu-id="3c818-118">依存関係については、`--packages` 引数を使用して、復元操作中に復元されたパッケージの配置場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="3c818-118">For dependencies, you specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="3c818-119">指定されていない場合は、既定の NuGet パッケージ キャッシュが使用されます。これは、すべてのオペレーティング システムのユーザーのホーム ディレクトリ内の `.nuget/packages` ディレクトリにあります (たとえば、Linux の場合は */home/user1*、Windows の場合は *C:\Users\user1*)。</span><span class="sxs-lookup"><span data-stu-id="3c818-119">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems (for example, */home/user1* on Linux or *C:\Users\user1* on Windows).</span></span>

<span data-ttu-id="3c818-120">プロジェクト固有のツールについては、`dotnet restore` はまず、ツールがパックされているパッケージを復元し、プロジェクト ファイルに指定されているツールの依存関係の復元に進みます。</span><span class="sxs-lookup"><span data-stu-id="3c818-120">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

<span data-ttu-id="3c818-121">*Nuget.Config* がある場合、`dotnet restore` コマンドの動作はその設定の一部に影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="3c818-121">The behavior of the `dotnet restore` command is affected by some of the settings in the *Nuget.Config* file, if present.</span></span> <span data-ttu-id="3c818-122">たとえば、*NuGet.Config* に `globalPackagesFolder` を設定すると、指定されたフォルダーに NuGet パッケージが復元されます。</span><span class="sxs-lookup"><span data-stu-id="3c818-122">For example, setting the `globalPackagesFolder` in *NuGet.Config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="3c818-123">これは `dotnet restore` コマンドで `--packages` オプションを指定する操作の代替方法です。</span><span class="sxs-lookup"><span data-stu-id="3c818-123">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="3c818-124">詳細については、「[NuGet.Config reference](/nuget/schema/nuget-config-file)」(NuGet.Config リファレンス) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c818-124">For more information, see the [NuGet.Config reference](/nuget/schema/nuget-config-file).</span></span>

## <a name="arguments"></a><span data-ttu-id="3c818-125">引数</span><span class="sxs-lookup"><span data-stu-id="3c818-125">Arguments</span></span>

`ROOT`

<span data-ttu-id="3c818-126">復元するプロジェクト ファイルへのオプションのパスです。</span><span class="sxs-lookup"><span data-stu-id="3c818-126">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="3c818-127">オプション</span><span class="sxs-lookup"><span data-stu-id="3c818-127">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="3c818-128">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="3c818-128">.NET Core 2.x</span></span>](#tab/netcore2x)

`--configfile <FILE>`

<span data-ttu-id="3c818-129">復元操作で使用する NuGet 構成ファイル (*NuGet.config*) です。</span><span class="sxs-lookup"><span data-stu-id="3c818-129">The NuGet configuration file (*NuGet.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="3c818-130">複数プロジェクトの並行復元を無効にします。</span><span class="sxs-lookup"><span data-stu-id="3c818-130">Disables restoring multiple projects in parallel.</span></span>

`--force`

<span data-ttu-id="3c818-131">最後の復元が成功した場合でも、すべての依存関係が強制的に解決されます。</span><span class="sxs-lookup"><span data-stu-id="3c818-131">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="3c818-132">これは、*project.assets.json* ファイルを削除する処理に相当します。</span><span class="sxs-lookup"><span data-stu-id="3c818-132">This is equivalent to deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="3c818-133">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="3c818-133">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="3c818-134">バージョン要件を満たしているパッケージがある場合は、失敗したソースに関する警告のみです。</span><span class="sxs-lookup"><span data-stu-id="3c818-134">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="3c818-135">パッケージとの HTTP 要求をキャッシュしないように指定します。</span><span class="sxs-lookup"><span data-stu-id="3c818-135">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="3c818-136">プロジェクト間 (P2P) 参照を含むプロジェクトを復元する場合は、参照ではなく、ルート プロジェクトを復元します。</span><span class="sxs-lookup"><span data-stu-id="3c818-136">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="3c818-137">復元されるパッケージのディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="3c818-137">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="3c818-138">パッケージの復元用のランタイムを指定します。</span><span class="sxs-lookup"><span data-stu-id="3c818-138">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="3c818-139">これは、*.csproj* ファイルの `<RuntimeIdentifiers>` タグに明示的にリストされていないランタイムのパッケージを復元するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="3c818-139">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="3c818-140">ランタイム ID (RID) の一覧については、[RID カタログ](../rid-catalog.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3c818-140">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="3c818-141">このオプションを複数回指定して、複数の RID を指定します。</span><span class="sxs-lookup"><span data-stu-id="3c818-141">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="3c818-142">復元操作時に使用する NuGet パッケージのソースを指定します。</span><span class="sxs-lookup"><span data-stu-id="3c818-142">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="3c818-143">これにより、*NuGet.config* ファイルに指定されているすべてのソースがオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="3c818-143">This overrides all of the sources specified in the *NuGet.config* file(s).</span></span> <span data-ttu-id="3c818-144">このオプションを複数回指定することによって、複数のソースを指定できます。</span><span class="sxs-lookup"><span data-stu-id="3c818-144">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="3c818-145">コマンドの詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="3c818-145">Sets the verbosity level of the command.</span></span> <span data-ttu-id="3c818-146">指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。</span><span class="sxs-lookup"><span data-stu-id="3c818-146">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="3c818-147">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="3c818-147">.NET Core 1.x</span></span>](#tab/netcore1x)

`--configfile <FILE>`

<span data-ttu-id="3c818-148">復元操作で使用する NuGet 構成ファイル (*NuGet.config*) です。</span><span class="sxs-lookup"><span data-stu-id="3c818-148">The NuGet configuration file (*NuGet.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="3c818-149">複数プロジェクトの並行復元を無効にします。</span><span class="sxs-lookup"><span data-stu-id="3c818-149">Disables restoring multiple projects in parallel.</span></span>

`-h|--help`

<span data-ttu-id="3c818-150">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="3c818-150">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="3c818-151">バージョン要件を満たしているパッケージがある場合は、失敗したソースに関する警告のみです。</span><span class="sxs-lookup"><span data-stu-id="3c818-151">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="3c818-152">パッケージとの HTTP 要求をキャッシュしないように指定します。</span><span class="sxs-lookup"><span data-stu-id="3c818-152">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="3c818-153">プロジェクト間 (P2P) 参照を含むプロジェクトを復元する場合は、参照ではなく、ルート プロジェクトを復元します。</span><span class="sxs-lookup"><span data-stu-id="3c818-153">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="3c818-154">復元されるパッケージのディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="3c818-154">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="3c818-155">パッケージの復元用のランタイムを指定します。</span><span class="sxs-lookup"><span data-stu-id="3c818-155">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="3c818-156">これは、*.csproj* ファイルの `<RuntimeIdentifiers>` タグに明示的にリストされていないランタイムのパッケージを復元するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="3c818-156">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="3c818-157">ランタイム ID (RID) の一覧については、[RID カタログ](../rid-catalog.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3c818-157">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="3c818-158">このオプションを複数回指定して、複数の RID を指定します。</span><span class="sxs-lookup"><span data-stu-id="3c818-158">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="3c818-159">復元操作時に使用する NuGet パッケージのソースを指定します。</span><span class="sxs-lookup"><span data-stu-id="3c818-159">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="3c818-160">これにより、*NuGet.config* ファイルに指定されているすべてのソースがオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="3c818-160">This overrides all of the sources specified in the *NuGet.config* file(s).</span></span> <span data-ttu-id="3c818-161">このオプションを複数回指定することによって、複数のソースを指定できます。</span><span class="sxs-lookup"><span data-stu-id="3c818-161">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="3c818-162">コマンドの詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="3c818-162">Sets the verbosity level of the command.</span></span> <span data-ttu-id="3c818-163">指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。</span><span class="sxs-lookup"><span data-stu-id="3c818-163">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="3c818-164">例</span><span class="sxs-lookup"><span data-stu-id="3c818-164">Examples</span></span>

<span data-ttu-id="3c818-165">現在のディレクトリでプロジェクトの依存関係とツールを復元します。</span><span class="sxs-lookup"><span data-stu-id="3c818-165">Restore dependencies and tools for the project in the current directory:</span></span>

`dotnet restore`

<span data-ttu-id="3c818-166">指定されたパスで見つかった `app1` プロジェクトの依存関係とツールを復元します。</span><span class="sxs-lookup"><span data-stu-id="3c818-166">Restore dependencies and tools for the `app1` project found in the given path:</span></span>

`dotnet restore ~/projects/app1/app1.csproj`

<span data-ttu-id="3c818-167">ソースとして指定されたファイル パスを使用して、現在のディレクトリでプロジェクトの依存関係とツールを復元します。</span><span class="sxs-lookup"><span data-stu-id="3c818-167">Restore the dependencies and tools for the project in the current directory using the file path provided as the source:</span></span>

`dotnet restore -s c:\packages\mypackages`

<span data-ttu-id="3c818-168">ソースとして指定された 2 つのファイル パスを使用して、現在のディレクトリでプロジェクトの依存関係とツールを復元します。</span><span class="sxs-lookup"><span data-stu-id="3c818-168">Restore the dependencies and tools for the project in the current directory using the two file paths provided as sources:</span></span>

`dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages`

<span data-ttu-id="3c818-169">現在のディレクトリでプロジェクトの依存関係とツールを復元し、最小限の出力のみを表示します。</span><span class="sxs-lookup"><span data-stu-id="3c818-169">Restore dependencies and tools for the project in the current directory and shows only minimal output:</span></span>

`dotnet restore --verbosity minimal`

