---
title: "dotnet-run コマンド - .NET Core CLI"
description: "dotnet-run コマンドは、ソース コードからアプリケーションを実行する便利なオプションを提供します。"
keywords: "dotnet-run, CLI, CLI コマンド, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/22/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 40d4e60f-9900-4a48-b03c-0bae06792d91
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: f0a6fce4f83808076b7cbcabdaa948badde2cf80
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-run"></a><span data-ttu-id="ed192-104">dotnet-run</span><span class="sxs-lookup"><span data-stu-id="ed192-104">dotnet-run</span></span>

## <a name="name"></a><span data-ttu-id="ed192-105">名前</span><span class="sxs-lookup"><span data-stu-id="ed192-105">Name</span></span> 

<span data-ttu-id="ed192-106">`dotnet-run` -- 明示的なコンパイルや起動コマンドなしで、ソース コードを実行します。</span><span class="sxs-lookup"><span data-stu-id="ed192-106">`dotnet-run` - Runs source code without any explicit compile or launch commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ed192-107">構文</span><span class="sxs-lookup"><span data-stu-id="ed192-107">Synopsis</span></span>

`dotnet run [-c|--configuration] [-f|--framework] [-p|--project] [[--] [application arguments]] [-h|--help]`

## <a name="description"></a><span data-ttu-id="ed192-108">説明</span><span class="sxs-lookup"><span data-stu-id="ed192-108">Description</span></span>

<span data-ttu-id="ed192-109">`dotnet run` コマンドは、1 つのコマンドを使用して、ソース コードからアプリケーションを実行する便利なオプションを提供します。</span><span class="sxs-lookup"><span data-stu-id="ed192-109">The `dotnet run` command provides a convenient option to run your application from the source code with one command.</span></span> <span data-ttu-id="ed192-110">コマンド ラインからの短期間の反復開発に便利です。</span><span class="sxs-lookup"><span data-stu-id="ed192-110">It's useful for fast iterative development from the command line.</span></span> <span data-ttu-id="ed192-111">このコマンドは [`dotnet build`](dotnet-build.md) コマンドに依存し、コードをビルドします。</span><span class="sxs-lookup"><span data-stu-id="ed192-111">The command depends on the [`dotnet build`](dotnet-build.md) command to build the code.</span></span> <span data-ttu-id="ed192-112">そのため、プロジェクトを最初に復元する必要があるなど、ビルドに要件があれば、それが `dotnet run` にも適用されます。</span><span class="sxs-lookup"><span data-stu-id="ed192-112">Any requirements for the build, such as that the project must be restored first, apply to `dotnet run` as well.</span></span> 

<span data-ttu-id="ed192-113">出力ファイルは既定の場所である `bin/<configuration>/<target>` に書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="ed192-113">Output files are written into the default location, which is `bin/<configuration>/<target>`.</span></span> <span data-ttu-id="ed192-114">たとえば、`netcoreapp1.0` というアプリケーションがあり、`dotnet run` を実行する場合、`bin/Debug/netcoreapp1.0` に出力されます。</span><span class="sxs-lookup"><span data-stu-id="ed192-114">For example if you have a `netcoreapp1.0` application and you run `dotnet run`, the output is placed in `bin/Debug/netcoreapp1.0`.</span></span> <span data-ttu-id="ed192-115">必要に応じて、ファイルは上書きされます。</span><span class="sxs-lookup"><span data-stu-id="ed192-115">Files are overwritten as needed.</span></span> <span data-ttu-id="ed192-116">一時ファイルは `obj` ディレクトリに置かれます。</span><span class="sxs-lookup"><span data-stu-id="ed192-116">Temporary files are placed in the `obj` directory.</span></span> 

<span data-ttu-id="ed192-117">フレームワークを複数指定するプロジェクトの場合、`-f|--framework <FRAMEWORK>` オプションを使用してフレームワークを指定しない限り、`dotnet run` を実行するとエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="ed192-117">If the project specifies multiple frameworks, executing `dotnet run` results in an error unless the `-f|--framework <FRAMEWORK>` option is used to specify the framework.</span></span>

<span data-ttu-id="ed192-118">`dotnet run` コマンドは、ビルド済みのアセンブリではなく、プロジェクトのコンテキストで使用されます。</span><span class="sxs-lookup"><span data-stu-id="ed192-118">The `dotnet run` command is used in the context of projects, not built assemblies.</span></span> <span data-ttu-id="ed192-119">代わりにフレームワークに依存するアプリケーション DLL の実行を試みる場合は、コマンドなしで [dotnet](dotnet.md) を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ed192-119">If you're trying to run a framework-dependent application DLL instead, you must use [dotnet](dotnet.md) without a command.</span></span> <span data-ttu-id="ed192-120">たとえば、`myapp.dll` を実行する場合は、次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="ed192-120">For example, to run `myapp.dll`, use:</span></span>
 
```
dotnet myapp.dll
```

<span data-ttu-id="ed192-121">`dotnet` ドライバーの詳細については、「[.NET Core Command Line Tools (CLI)](index.md)」 (.NET Core コマンド ライン ツール (CLI)) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ed192-121">For more information on the `dotnet` driver, see the [.NET Core Command Line Tools (CLI)](index.md) topic.</span></span>

<span data-ttu-id="ed192-122">アプリケーションを実行するために、`dotnet run` コマンドは、NuGet キャッシュから共有ランタイムの外にあるアプリケーションの依存関係を解決します。</span><span class="sxs-lookup"><span data-stu-id="ed192-122">In order to run the application, the `dotnet run` command resolves the dependencies of the application that are outside of the shared runtime from the NuGet cache.</span></span> <span data-ttu-id="ed192-123">このコマンドではキャッシュされた依存関係を使用するため、`dotnet run` を使用してアプリケーションを実稼働環境で実行することは推奨されません。</span><span class="sxs-lookup"><span data-stu-id="ed192-123">Because it uses cached dependencies, it's not recommended to use `dotnet run` to run applications in production.</span></span> <span data-ttu-id="ed192-124">代わりに、[`dotnet publish`](dotnet-publish.md) コマンドを使用して[展開を作成](../deploying/index.md)し、発行された出力を展開します。</span><span class="sxs-lookup"><span data-stu-id="ed192-124">Instead, [create a deployment](../deploying/index.md) using the [`dotnet publish`](dotnet-publish.md) command and deploy the published output.</span></span> 

## <a name="options"></a><span data-ttu-id="ed192-125">オプション</span><span class="sxs-lookup"><span data-stu-id="ed192-125">Options</span></span>

`--`

<span data-ttu-id="ed192-126">実行中のアプリケーションの引数と `dotnet run` の引数を区切ります。</span><span class="sxs-lookup"><span data-stu-id="ed192-126">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="ed192-127">この後の引数はすべて実行中のアプリケーションに渡されます。</span><span class="sxs-lookup"><span data-stu-id="ed192-127">All arguments after this one are passed to the application run.</span></span> 

`-h|--help`

<span data-ttu-id="ed192-128">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="ed192-128">Prints out a short help for the command.</span></span>

`-c|--configuration <CONFIGURATION>`

<span data-ttu-id="ed192-129">プロジェクトのビルド時に使用する構成です。</span><span class="sxs-lookup"><span data-stu-id="ed192-129">Configuration to use for building the project.</span></span> <span data-ttu-id="ed192-130">既定値は `Debug` です。</span><span class="sxs-lookup"><span data-stu-id="ed192-130">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="ed192-131">指定された[フレームワーク](../../standard/frameworks.md)を使用してアプリをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="ed192-131">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="ed192-132">フレームワークはプロジェクト ファイルに指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ed192-132">The framework must be specified in the project file.</span></span>

`-p|--project <PATH/PROJECT.csproj>`

<span data-ttu-id="ed192-133">プロジェクト ファイルのパスと名前を指定します </span><span class="sxs-lookup"><span data-stu-id="ed192-133">Specifies the path and name of the project file.</span></span> <span data-ttu-id="ed192-134">(注を参照)。指定しない場合は、既定で現在のディレクトリに設定されます。</span><span class="sxs-lookup"><span data-stu-id="ed192-134">(See the NOTE.) It defaults to the current directory if not specified.</span></span>

> [!NOTE]
> <span data-ttu-id="ed192-135">`-p|--project` オプションでプロジェクト ファイルのパスと名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="ed192-135">Use the path and name of the project file with the `-p|--project` option.</span></span> <span data-ttu-id="ed192-136">CLI の回帰により、この時点でフォルダー パスを指定できなくなります。</span><span class="sxs-lookup"><span data-stu-id="ed192-136">A regression in the CLI prevents providing a folder path at this time.</span></span> <span data-ttu-id="ed192-137">詳細およびこの問題の追跡については、「[dotnet run -p, can not start a project (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992)」 (dotnet run -p でプロジェクトを開始できない (dotnet/cli #5992)) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ed192-137">For more information and to track this issue, see [dotnet run -p, can not start a project (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).</span></span>

## <a name="examples"></a><span data-ttu-id="ed192-138">例</span><span class="sxs-lookup"><span data-stu-id="ed192-138">Examples</span></span>

<span data-ttu-id="ed192-139">現在のディレクトリのプロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="ed192-139">Run the project in the current directory:</span></span>

`dotnet run` 

<span data-ttu-id="ed192-140">指定されたプロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="ed192-140">Run the specified project:</span></span>

`dotnet run --project /projects/proj1/proj1.csproj`

<span data-ttu-id="ed192-141">現在のディレクトリのプロジェクトを実行します (この例では、`--` 引数が使用されているため、`--help` 引数がアプリケーションに渡されます)。</span><span class="sxs-lookup"><span data-stu-id="ed192-141">Run the project in the current directory (the `--help` argument in this example is passed to the application, since the `--` argument is used):</span></span>

`dotnet run --configuration Release -- --help`

