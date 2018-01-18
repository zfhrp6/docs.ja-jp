---
title: "dotnet run コマンド - .NET Core CLI"
description: "dotnet run コマンドは、ソース コードからアプリケーションを実行する便利なオプションを提供します。"
author: mairaw
ms.author: mairaw
ms.date: 09/24/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: 1f5a3927859f89bef6c50d3d31b73de43cd1cd31
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-run"></a><span data-ttu-id="d4162-103">dotnet run</span><span class="sxs-lookup"><span data-stu-id="d4162-103">dotnet run</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="d4162-104">name</span><span class="sxs-lookup"><span data-stu-id="d4162-104">Name</span></span>

<span data-ttu-id="d4162-105">`dotnet run` -- 明示的なコンパイルや起動コマンドなしで、ソース コードを実行します。</span><span class="sxs-lookup"><span data-stu-id="d4162-105">`dotnet run` - Runs source code without any explicit compile or launch commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d4162-106">構文</span><span class="sxs-lookup"><span data-stu-id="d4162-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="d4162-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="d4162-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies] [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d4162-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="d4162-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet run [-c|--configuration] [-f|--framework] [-p|--project] [[--] [application arguments]]
dotnet run [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="d4162-109">説明</span><span class="sxs-lookup"><span data-stu-id="d4162-109">Description</span></span>

<span data-ttu-id="d4162-110">`dotnet run` コマンドは、1 つのコマンドを使用して、ソース コードからアプリケーションを実行する便利なオプションを提供します。</span><span class="sxs-lookup"><span data-stu-id="d4162-110">The `dotnet run` command provides a convenient option to run your application from the source code with one command.</span></span> <span data-ttu-id="d4162-111">コマンド ラインからの短期間の反復開発に便利です。</span><span class="sxs-lookup"><span data-stu-id="d4162-111">It's useful for fast iterative development from the command line.</span></span> <span data-ttu-id="d4162-112">このコマンドは [`dotnet build`](dotnet-build.md) コマンドに依存し、コードをビルドします。</span><span class="sxs-lookup"><span data-stu-id="d4162-112">The command depends on the [`dotnet build`](dotnet-build.md) command to build the code.</span></span> <span data-ttu-id="d4162-113">そのため、プロジェクトを最初に復元する必要があるなど、ビルドに要件があれば、それが `dotnet run` にも適用されます。</span><span class="sxs-lookup"><span data-stu-id="d4162-113">Any requirements for the build, such as that the project must be restored first, apply to `dotnet run` as well.</span></span> 

<span data-ttu-id="d4162-114">出力ファイルは既定の場所である `bin/<configuration>/<target>` に書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="d4162-114">Output files are written into the default location, which is `bin/<configuration>/<target>`.</span></span> <span data-ttu-id="d4162-115">たとえば、`netcoreapp1.0` というアプリケーションがあり、`dotnet run` を実行する場合、`bin/Debug/netcoreapp1.0` に出力されます。</span><span class="sxs-lookup"><span data-stu-id="d4162-115">For example if you have a `netcoreapp1.0` application and you run `dotnet run`, the output is placed in `bin/Debug/netcoreapp1.0`.</span></span> <span data-ttu-id="d4162-116">必要に応じて、ファイルは上書きされます。</span><span class="sxs-lookup"><span data-stu-id="d4162-116">Files are overwritten as needed.</span></span> <span data-ttu-id="d4162-117">一時ファイルは `obj` ディレクトリに置かれます。</span><span class="sxs-lookup"><span data-stu-id="d4162-117">Temporary files are placed in the `obj` directory.</span></span> 

<span data-ttu-id="d4162-118">フレームワークを複数指定するプロジェクトの場合、`-f|--framework <FRAMEWORK>` オプションを使用してフレームワークを指定しない限り、`dotnet run` を実行するとエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="d4162-118">If the project specifies multiple frameworks, executing `dotnet run` results in an error unless the `-f|--framework <FRAMEWORK>` option is used to specify the framework.</span></span>

<span data-ttu-id="d4162-119">`dotnet run` コマンドは、ビルド済みのアセンブリではなく、プロジェクトのコンテキストで使用されます。</span><span class="sxs-lookup"><span data-stu-id="d4162-119">The `dotnet run` command is used in the context of projects, not built assemblies.</span></span> <span data-ttu-id="d4162-120">代わりにフレームワークに依存するアプリケーション DLL の実行を試みる場合は、コマンドなしで [dotnet](dotnet.md) を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4162-120">If you're trying to run a framework-dependent application DLL instead, you must use [dotnet](dotnet.md) without a command.</span></span> <span data-ttu-id="d4162-121">たとえば、`myapp.dll` を実行する場合は、次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="d4162-121">For example, to run `myapp.dll`, use:</span></span>

```
dotnet myapp.dll
```

<span data-ttu-id="d4162-122">`dotnet` ドライバーの詳細については、「[.NET Core Command Line Tools (CLI)](index.md)」 (.NET Core コマンド ライン ツール (CLI)) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4162-122">For more information on the `dotnet` driver, see the [.NET Core Command Line Tools (CLI)](index.md) topic.</span></span>

<span data-ttu-id="d4162-123">アプリケーションを実行するために、`dotnet run` コマンドは、NuGet キャッシュから共有ランタイムの外にあるアプリケーションの依存関係を解決します。</span><span class="sxs-lookup"><span data-stu-id="d4162-123">In order to run the application, the `dotnet run` command resolves the dependencies of the application that are outside of the shared runtime from the NuGet cache.</span></span> <span data-ttu-id="d4162-124">このコマンドではキャッシュされた依存関係を使用するため、`dotnet run` を使用してアプリケーションを実稼働環境で実行することは推奨されません。</span><span class="sxs-lookup"><span data-stu-id="d4162-124">Because it uses cached dependencies, it's not recommended to use `dotnet run` to run applications in production.</span></span> <span data-ttu-id="d4162-125">代わりに、[`dotnet publish`](dotnet-publish.md) コマンドを使用して[展開を作成](../deploying/index.md)し、発行された出力を展開します。</span><span class="sxs-lookup"><span data-stu-id="d4162-125">Instead, [create a deployment](../deploying/index.md) using the [`dotnet publish`](dotnet-publish.md) command and deploy the published output.</span></span>

## <a name="options"></a><span data-ttu-id="d4162-126">オプション</span><span class="sxs-lookup"><span data-stu-id="d4162-126">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="d4162-127">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="d4162-127">.NET Core 2.x</span></span>](#tab/netcore2x)

`--`

<span data-ttu-id="d4162-128">実行中のアプリケーションの引数と `dotnet run` の引数を区切ります。</span><span class="sxs-lookup"><span data-stu-id="d4162-128">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="d4162-129">この後の引数はすべて実行中のアプリケーションに渡されます。</span><span class="sxs-lookup"><span data-stu-id="d4162-129">All arguments after this one are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="d4162-130">ビルド構成を定義します。</span><span class="sxs-lookup"><span data-stu-id="d4162-130">Defines the build configuration.</span></span> <span data-ttu-id="d4162-131">既定値は `Debug` です。</span><span class="sxs-lookup"><span data-stu-id="d4162-131">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="d4162-132">指定された[フレームワーク](../../standard/frameworks.md)を使用してアプリをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="d4162-132">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="d4162-133">フレームワークはプロジェクト ファイルに指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4162-133">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="d4162-134">最後の復元が成功した場合でも、すべての依存関係が強制的に解決されます。</span><span class="sxs-lookup"><span data-stu-id="d4162-134">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="d4162-135">これは、*project.assets.json* を削除する処理に相当します。</span><span class="sxs-lookup"><span data-stu-id="d4162-135">This is equivalent to deleting *project.assets.json*.</span></span>

`-h|--help`

<span data-ttu-id="d4162-136">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="d4162-136">Prints out a short help for the command.</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="d4162-137">アプリケーションを起動する場合に使用する起動プロファイル (存在する場合) の名前です。</span><span class="sxs-lookup"><span data-stu-id="d4162-137">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="d4162-138">起動プロファイルは *launchSettings.json* ファイル内に定義されており、通常は、`Development`、`Staging`、および `Production` と呼ばれています。</span><span class="sxs-lookup"><span data-stu-id="d4162-138">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging` and `Production`.</span></span> <span data-ttu-id="d4162-139">詳細については、[「Working with multiple environments」](/aspnet/core/fundamentals/environments) (複数の環境での使用) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d4162-139">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="d4162-140">実行前にプロジェクトをビルドしません。</span><span class="sxs-lookup"><span data-stu-id="d4162-140">Doesn't build the project before running.</span></span>

`--no-dependencies`

<span data-ttu-id="d4162-141">プロジェクト間 (P2P) 参照を含むプロジェクトを復元する場合は、参照ではなく、ルート プロジェクトを復元します。</span><span class="sxs-lookup"><span data-stu-id="d4162-141">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="d4162-142">アプリケーションを構成するための *launchSettings.json* の使用を試みません。</span><span class="sxs-lookup"><span data-stu-id="d4162-142">Doesn't attempt to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="d4162-143">コマンドを実行するときに、暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="d4162-143">Doesn't perform an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="d4162-144">実行するプロジェクト ファイルのパスを指定します (フォルダー名または完全なパス)。</span><span class="sxs-lookup"><span data-stu-id="d4162-144">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="d4162-145">指定しない場合は、既定で現在のディレクトリに設定されます。</span><span class="sxs-lookup"><span data-stu-id="d4162-145">It defaults to the current directory if not specified.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="d4162-146">パッケージを復元するターゲット ランタイムを指定します。</span><span class="sxs-lookup"><span data-stu-id="d4162-146">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="d4162-147">ランタイム ID (RID) の一覧については、[RID カタログ](../rid-catalog.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d4162-147">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d4162-148">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="d4162-148">.NET Core 1.x</span></span>](#tab/netcore1x)

`--`

<span data-ttu-id="d4162-149">実行中のアプリケーションの引数と `dotnet run` の引数を区切ります。</span><span class="sxs-lookup"><span data-stu-id="d4162-149">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="d4162-150">この後の引数はすべて実行中のアプリケーションに渡されます。</span><span class="sxs-lookup"><span data-stu-id="d4162-150">All arguments after this one are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="d4162-151">ビルド構成を定義します。</span><span class="sxs-lookup"><span data-stu-id="d4162-151">Defines the build configuration.</span></span> <span data-ttu-id="d4162-152">既定値は `Debug` です。</span><span class="sxs-lookup"><span data-stu-id="d4162-152">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="d4162-153">指定された[フレームワーク](../../standard/frameworks.md)を使用してアプリをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="d4162-153">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="d4162-154">フレームワークはプロジェクト ファイルに指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4162-154">The framework must be specified in the project file.</span></span>

`-h|--help`

<span data-ttu-id="d4162-155">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="d4162-155">Prints out a short help for the command.</span></span>

`-p|--project <PATH/PROJECT.csproj>`

<span data-ttu-id="d4162-156">プロジェクト ファイルのパスと名前を指定します </span><span class="sxs-lookup"><span data-stu-id="d4162-156">Specifies the path and name of the project file.</span></span> <span data-ttu-id="d4162-157">(注を参照)。指定しない場合は、既定で現在のディレクトリに設定されます。</span><span class="sxs-lookup"><span data-stu-id="d4162-157">(See the NOTE.) It defaults to the current directory if not specified.</span></span>

> [!NOTE]
> <span data-ttu-id="d4162-158">`-p|--project` オプションでプロジェクト ファイルのパスと名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="d4162-158">Use the path and name of the project file with the `-p|--project` option.</span></span> <span data-ttu-id="d4162-159">CLI の回帰により、.NET Core 1.x SDK でフォルダー パスを指定できなくなります。</span><span class="sxs-lookup"><span data-stu-id="d4162-159">A regression in the CLI prevents providing a folder path with .NET Core 1.x SDK.</span></span> <span data-ttu-id="d4162-160">この問題の詳細については、[「dotnet run -p, can not start a project (dotnet/cli #5992)」](https://github.com/dotnet/cli/issues/5992) (dotnet run -p でプロジェクトを開始できない (dotnet/cli #5992)) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4162-160">For more information about this issue, see [dotnet run -p, can not start a project (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).</span></span>

---

## <a name="examples"></a><span data-ttu-id="d4162-161">使用例</span><span class="sxs-lookup"><span data-stu-id="d4162-161">Examples</span></span>

<span data-ttu-id="d4162-162">現在のディレクトリのプロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="d4162-162">Run the project in the current directory:</span></span>

`dotnet run`

<span data-ttu-id="d4162-163">指定されたプロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="d4162-163">Run the specified project:</span></span>

`dotnet run --project /projects/proj1/proj1.csproj`

<span data-ttu-id="d4162-164">現在のディレクトリのプロジェクトを実行します (この例では、`--` 引数が使用されているため、`--help` 引数がアプリケーションに渡されます)。</span><span class="sxs-lookup"><span data-stu-id="d4162-164">Run the project in the current directory (the `--help` argument in this example is passed to the application, since the `--` argument is used):</span></span>

`dotnet run --configuration Release -- --help`
