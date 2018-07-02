---
title: dotnet restore コマンド - .NET Core CLI
description: dotnet restore コマンドを使用して、依存関係とプロジェクト固有のツールを復元する方法について説明します。
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 0eaab1aa1bc52bd5b3c51a6ed2dd7a59c35a4aa5
ms.sourcegitcommit: 736ec4d3e2c74895b47a0d36126657b95da383c9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/30/2018
ms.locfileid: "37140256"
---
# <a name="dotnet-restore"></a><span data-ttu-id="4eb95-103">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="4eb95-103">dotnet restore</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="4eb95-104">name</span><span class="sxs-lookup"><span data-stu-id="4eb95-104">Name</span></span>

<span data-ttu-id="4eb95-105">`dotnet restore` - プロジェクトの依存関係とツールを復元します。</span><span class="sxs-lookup"><span data-stu-id="4eb95-105">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="4eb95-106">構文</span><span class="sxs-lookup"><span data-stu-id="4eb95-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="4eb95-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="4eb95-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--force] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="4eb95-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="4eb95-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="4eb95-109">説明</span><span class="sxs-lookup"><span data-stu-id="4eb95-109">Description</span></span>

<span data-ttu-id="4eb95-110">`dotnet restore` コマンドでは NuGet を使用して、依存関係と、プロジェクト ファイルに指定されているプロジェクト固有のツールを復元します。</span><span class="sxs-lookup"><span data-stu-id="4eb95-110">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span> <span data-ttu-id="4eb95-111">既定では、依存関係とツールの復元は並列に実行されます。</span><span class="sxs-lookup"><span data-stu-id="4eb95-111">By default, the restoration of dependencies and tools are executed in parallel.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="4eb95-112">依存関係を復元するには、NuGet で、パッケージを配置するフィードが必要になります。</span><span class="sxs-lookup"><span data-stu-id="4eb95-112">To restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="4eb95-113">フィードは、通常、*NuGet.config* 構成ファイルを通じて提供されます。</span><span class="sxs-lookup"><span data-stu-id="4eb95-113">Feeds are usually provided via the *NuGet.config* configuration file.</span></span> <span data-ttu-id="4eb95-114">既定の構成ファイルは、CLI ツールがインストールされている場合に提供されます。</span><span class="sxs-lookup"><span data-stu-id="4eb95-114">A default configuration file is provided when the CLI tools are installed.</span></span> <span data-ttu-id="4eb95-115">プロジェクト ディレクトリに独自の *NuGet.config* ファイルを作成して、さらにフィードを指定します。</span><span class="sxs-lookup"><span data-stu-id="4eb95-115">You specify additional feeds by creating your own *NuGet.config* file in the project directory.</span></span> <span data-ttu-id="4eb95-116">コマンド プロンプトで呼び出すごとにフィードをさらに指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="4eb95-116">You also specify additional feeds per invocation at a command prompt.</span></span>

<span data-ttu-id="4eb95-117">依存関係については、`--packages` 引数を使用して、復元操作中に復元されたパッケージの配置場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="4eb95-117">For dependencies, you specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="4eb95-118">指定されていない場合は、既定の NuGet パッケージ キャッシュが使用されます。これは、すべてのオペレーティング システムのユーザーのホーム ディレクトリ内の `.nuget/packages` ディレクトリにあります。</span><span class="sxs-lookup"><span data-stu-id="4eb95-118">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems.</span></span> <span data-ttu-id="4eb95-119">たとえば、Linux の場合は */home/user1*、Windows の場合は *C:\Users\user1* です。</span><span class="sxs-lookup"><span data-stu-id="4eb95-119">For example, */home/user1* on Linux or *C:\Users\user1* on Windows.</span></span>

<span data-ttu-id="4eb95-120">プロジェクト固有のツールについては、`dotnet restore` はまず、ツールがパックされているパッケージを復元し、プロジェクト ファイルに指定されているツールの依存関係の復元に進みます。</span><span class="sxs-lookup"><span data-stu-id="4eb95-120">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

<span data-ttu-id="4eb95-121">*Nuget.Config* がある場合、`dotnet restore` コマンドの動作はその設定の一部に影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="4eb95-121">The behavior of the `dotnet restore` command is affected by some of the settings in the *Nuget.Config* file, if present.</span></span> <span data-ttu-id="4eb95-122">たとえば、*NuGet.Config* に `globalPackagesFolder` を設定すると、指定されたフォルダーに NuGet パッケージが復元されます。</span><span class="sxs-lookup"><span data-stu-id="4eb95-122">For example, setting the `globalPackagesFolder` in *NuGet.Config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="4eb95-123">これは `dotnet restore` コマンドで `--packages` オプションを指定する操作の代替方法です。</span><span class="sxs-lookup"><span data-stu-id="4eb95-123">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="4eb95-124">詳細については、「[NuGet.Config reference](/nuget/schema/nuget-config-file)」(NuGet.Config リファレンス) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4eb95-124">For more information, see the [NuGet.Config reference](/nuget/schema/nuget-config-file).</span></span>

## <a name="implicit-dotnet-restore"></a><span data-ttu-id="4eb95-125">暗黙的 `dotnet restore`</span><span class="sxs-lookup"><span data-stu-id="4eb95-125">Implicit `dotnet restore`</span></span>

<span data-ttu-id="4eb95-126">.NET Core 2.0 より、次のコマンドの発行時に必要な場合、`dotnet restore` が暗黙的に実行されます。</span><span class="sxs-lookup"><span data-stu-id="4eb95-126">Starting with .NET Core 2.0, `dotnet restore` is run implicitly if necessary when you issue the following commands:</span></span>

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

<span data-ttu-id="4eb95-127">ほとんどの場合、`dotnet restore` コマンドを明示的に使用する必要がなくなりました。</span><span class="sxs-lookup"><span data-stu-id="4eb95-127">In most cases, you no longer need to explicitly use the `dotnet restore` command.</span></span>

<span data-ttu-id="4eb95-128">ときには、`dotnet restore` を暗黙的に実行するのが不便な場合があります。</span><span class="sxs-lookup"><span data-stu-id="4eb95-128">Sometimes, it might be inconvenient to run `dotnet restore` implicitly.</span></span> <span data-ttu-id="4eb95-129">たとえば、ビルド システムなど、一部の自動化されているシステムでは、ネットワーク使用状況を制御できるように、`dotnet restore` を明示的に呼び出し、復元のタイミングを制御する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4eb95-129">For example, some automated systems, such as build systems, need to call `dotnet restore` explicitly to control when the restore occurs so that they can control network usage.</span></span> <span data-ttu-id="4eb95-130">`dotnet restore` の暗黙的実行を防ぐために、`--no-restore` フラグと共にこれらのコマンドのいずれかを使用し、暗黙的復元を無効にできます。</span><span class="sxs-lookup"><span data-stu-id="4eb95-130">To prevent `dotnet restore` from running implicitly, you can use the `--no-restore` flag with any of these commands to disable implicit restore.</span></span>

## <a name="arguments"></a><span data-ttu-id="4eb95-131">引数</span><span class="sxs-lookup"><span data-stu-id="4eb95-131">Arguments</span></span>

`ROOT`

<span data-ttu-id="4eb95-132">復元するプロジェクト ファイルへのオプションのパスです。</span><span class="sxs-lookup"><span data-stu-id="4eb95-132">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="4eb95-133">オプション</span><span class="sxs-lookup"><span data-stu-id="4eb95-133">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="4eb95-134">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="4eb95-134">.NET Core 2.x</span></span>](#tab/netcore2x)

`--configfile <FILE>`

<span data-ttu-id="4eb95-135">復元操作で使用する NuGet 構成ファイル (*NuGet.config*) です。</span><span class="sxs-lookup"><span data-stu-id="4eb95-135">The NuGet configuration file (*NuGet.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="4eb95-136">複数プロジェクトの並行復元を無効にします。</span><span class="sxs-lookup"><span data-stu-id="4eb95-136">Disables restoring multiple projects in parallel.</span></span>

`--force`

<span data-ttu-id="4eb95-137">最後の復元が成功した場合でも、すべての依存関係が強制的に解決されます。</span><span class="sxs-lookup"><span data-stu-id="4eb95-137">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="4eb95-138">このフラグを指定することは、*project.assets.json* ファイルを削除することと同じです。</span><span class="sxs-lookup"><span data-stu-id="4eb95-138">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="4eb95-139">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="4eb95-139">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="4eb95-140">バージョン要件を満たしているパッケージがある場合は、失敗したソースに関する警告のみです。</span><span class="sxs-lookup"><span data-stu-id="4eb95-140">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="4eb95-141">パッケージとの HTTP 要求をキャッシュしないように指定します。</span><span class="sxs-lookup"><span data-stu-id="4eb95-141">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="4eb95-142">プロジェクト間 (P2P) 参照を含むプロジェクトを復元する場合は、参照ではなく、ルート プロジェクトを復元します。</span><span class="sxs-lookup"><span data-stu-id="4eb95-142">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="4eb95-143">復元されるパッケージのディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="4eb95-143">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="4eb95-144">パッケージの復元用のランタイムを指定します。</span><span class="sxs-lookup"><span data-stu-id="4eb95-144">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="4eb95-145">これは、*.csproj* ファイルの `<RuntimeIdentifiers>` タグに明示的にリストされていないランタイムのパッケージを復元するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="4eb95-145">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="4eb95-146">ランタイム ID (RID) の一覧については、[RID カタログ](../rid-catalog.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4eb95-146">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="4eb95-147">このオプションを複数回指定して、複数の RID を指定します。</span><span class="sxs-lookup"><span data-stu-id="4eb95-147">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="4eb95-148">復元操作時に使用する NuGet パッケージのソースを指定します。</span><span class="sxs-lookup"><span data-stu-id="4eb95-148">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="4eb95-149">この設定により、*NuGet.config* ファイルに指定されているすべてのソースがオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="4eb95-149">This setting overrides all of the sources specified in the *NuGet.config* files.</span></span> <span data-ttu-id="4eb95-150">このオプションを複数回指定することによって、複数のソースを指定できます。</span><span class="sxs-lookup"><span data-stu-id="4eb95-150">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="4eb95-151">コマンドの詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="4eb95-151">Sets the verbosity level of the command.</span></span> <span data-ttu-id="4eb95-152">指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。</span><span class="sxs-lookup"><span data-stu-id="4eb95-152">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="4eb95-153">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="4eb95-153">.NET Core 1.x</span></span>](#tab/netcore1x)

`--configfile <FILE>`

<span data-ttu-id="4eb95-154">復元操作で使用する NuGet 構成ファイル (*NuGet.config*) です。</span><span class="sxs-lookup"><span data-stu-id="4eb95-154">The NuGet configuration file (*NuGet.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="4eb95-155">複数プロジェクトの並行復元を無効にします。</span><span class="sxs-lookup"><span data-stu-id="4eb95-155">Disables restoring multiple projects in parallel.</span></span>

`-h|--help`

<span data-ttu-id="4eb95-156">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="4eb95-156">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="4eb95-157">バージョン要件を満たしているパッケージがある場合は、失敗したソースに関する警告のみです。</span><span class="sxs-lookup"><span data-stu-id="4eb95-157">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="4eb95-158">パッケージとの HTTP 要求をキャッシュしないように指定します。</span><span class="sxs-lookup"><span data-stu-id="4eb95-158">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="4eb95-159">プロジェクト間 (P2P) 参照を含むプロジェクトを復元する場合は、参照ではなく、ルート プロジェクトを復元します。</span><span class="sxs-lookup"><span data-stu-id="4eb95-159">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="4eb95-160">復元されるパッケージのディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="4eb95-160">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="4eb95-161">パッケージの復元用のランタイムを指定します。</span><span class="sxs-lookup"><span data-stu-id="4eb95-161">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="4eb95-162">これは、*.csproj* ファイルの `<RuntimeIdentifiers>` タグに明示的にリストされていないランタイムのパッケージを復元するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="4eb95-162">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="4eb95-163">ランタイム ID (RID) の一覧については、[RID カタログ](../rid-catalog.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4eb95-163">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="4eb95-164">このオプションを複数回指定して、複数の RID を指定します。</span><span class="sxs-lookup"><span data-stu-id="4eb95-164">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="4eb95-165">復元操作時に使用する NuGet パッケージのソースを指定します。</span><span class="sxs-lookup"><span data-stu-id="4eb95-165">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="4eb95-166">これにより、*NuGet.config* ファイルに指定されているすべてのソースがオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="4eb95-166">This overrides all of the sources specified in the *NuGet.config* files.</span></span> <span data-ttu-id="4eb95-167">このオプションを複数回指定することによって、複数のソースを指定できます。</span><span class="sxs-lookup"><span data-stu-id="4eb95-167">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="4eb95-168">コマンドの詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="4eb95-168">Sets the verbosity level of the command.</span></span> <span data-ttu-id="4eb95-169">指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。</span><span class="sxs-lookup"><span data-stu-id="4eb95-169">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="4eb95-170">使用例</span><span class="sxs-lookup"><span data-stu-id="4eb95-170">Examples</span></span>

<span data-ttu-id="4eb95-171">現在のディレクトリでプロジェクトの依存関係とツールを復元します。</span><span class="sxs-lookup"><span data-stu-id="4eb95-171">Restore dependencies and tools for the project in the current directory:</span></span>

`dotnet restore`

<span data-ttu-id="4eb95-172">指定されたパスで見つかった `app1` プロジェクトの依存関係とツールを復元します。</span><span class="sxs-lookup"><span data-stu-id="4eb95-172">Restore dependencies and tools for the `app1` project found in the given path:</span></span>

`dotnet restore ~/projects/app1/app1.csproj`

<span data-ttu-id="4eb95-173">ソースとして指定されたファイル パスを使用して、現在のディレクトリでプロジェクトの依存関係とツールを復元します。</span><span class="sxs-lookup"><span data-stu-id="4eb95-173">Restore the dependencies and tools for the project in the current directory using the file path provided as the source:</span></span>

`dotnet restore -s c:\packages\mypackages`

<span data-ttu-id="4eb95-174">ソースとして指定された 2 つのファイル パスを使用して、現在のディレクトリでプロジェクトの依存関係とツールを復元します。</span><span class="sxs-lookup"><span data-stu-id="4eb95-174">Restore the dependencies and tools for the project in the current directory using the two file paths provided as sources:</span></span>

`dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages`

<span data-ttu-id="4eb95-175">現在のディレクトリでプロジェクトの依存関係とツールを復元し、最小限の出力のみを表示します。</span><span class="sxs-lookup"><span data-stu-id="4eb95-175">Restore dependencies and tools for the project in the current directory and shows only minimal output:</span></span>

`dotnet restore --verbosity minimal`
