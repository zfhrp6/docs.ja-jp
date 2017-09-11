---
title: "dotnet コマンド - .NET Core CLI"
description: "dotnet コマンド (.NET Core CLI ツールの一般的なドライバー) とその使用法について説明します。"
keywords: "dotnet, CLI, CLI コマンド, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/20/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 256e468e-eaaa-4715-b5fb-8cbddcf80e69
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1f377ea55278ae382f56a0dc0cbcf1bb99f49eca
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-command"></a><span data-ttu-id="0945a-104">dotnet コマンド</span><span class="sxs-lookup"><span data-stu-id="0945a-104">dotnet command</span></span>

## <a name="name"></a><span data-ttu-id="0945a-105">名前</span><span class="sxs-lookup"><span data-stu-id="0945a-105">Name</span></span>

<span data-ttu-id="0945a-106">`dotnet` - コマンドラインのコマンドを実行するための一般的なドライバーです。</span><span class="sxs-lookup"><span data-stu-id="0945a-106">`dotnet` - General driver for running the command-line commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0945a-107">構文</span><span class="sxs-lookup"><span data-stu-id="0945a-107">Synopsis</span></span>

`dotnet [command] [arguments] [--version] [--info] [-d|--diagnostics] [-v|--verbose] [--fx-version] [--additionalprobingpath] [-h|--help]`

## <a name="description"></a><span data-ttu-id="0945a-108">説明</span><span class="sxs-lookup"><span data-stu-id="0945a-108">Description</span></span>

<span data-ttu-id="0945a-109">`dotnet` は、コマンド ライン インターフェイス (CLI) ツールチェーンの一般的なドライバーです。</span><span class="sxs-lookup"><span data-stu-id="0945a-109">`dotnet` is a generic driver for the Command Line Interface (CLI) toolchain.</span></span> <span data-ttu-id="0945a-110">単独で呼び出され、簡単な使用方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="0945a-110">Invoked on its own, it provides brief usage instructions.</span></span>

<span data-ttu-id="0945a-111">特定の機能がそれぞれコマンドとして実装されます。</span><span class="sxs-lookup"><span data-stu-id="0945a-111">Each specific feature is implemented as a command.</span></span> <span data-ttu-id="0945a-112">機能を使用するには、[`dotnet build`](dotnet-build.md) のように、`dotnet` の後にコマンドを指定します。</span><span class="sxs-lookup"><span data-stu-id="0945a-112">In order to use the feature, the command is specified after `dotnet`, such as [`dotnet build`](dotnet-build.md).</span></span> <span data-ttu-id="0945a-113">コマンドに続く引数はすべて独自の引数です。</span><span class="sxs-lookup"><span data-stu-id="0945a-113">All of the arguments following the command are its own arguments.</span></span>

<span data-ttu-id="0945a-114">`dotnet` が単独でコマンドとして使用されるのは、[フレームワークに依存するアプリ](../deploying/index.md)を実行する場合のみです。</span><span class="sxs-lookup"><span data-stu-id="0945a-114">The only time `dotnet` is used as a command on its own is to run [framework-dependent apps](../deploying/index.md).</span></span> <span data-ttu-id="0945a-115">アプリケーションを実行する場合は、`dotnet` の動詞の後にアプリケーション DLL を指定します (`dotnet myapp.dll` など)。</span><span class="sxs-lookup"><span data-stu-id="0945a-115">Specify an application DLL after the `dotnet` verb to execute the application (for example, `dotnet myapp.dll`).</span></span>

## <a name="options"></a><span data-ttu-id="0945a-116">オプション</span><span class="sxs-lookup"><span data-stu-id="0945a-116">Options</span></span>

`-v|--verbose`

<span data-ttu-id="0945a-117">詳細出力を有効にします。</span><span class="sxs-lookup"><span data-stu-id="0945a-117">Enables verbose output.</span></span>

`-d|--diagnostics`

<span data-ttu-id="0945a-118">診断出力を有効にします。</span><span class="sxs-lookup"><span data-stu-id="0945a-118">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="0945a-119">アプリケーションを実行するために使用するインストール済みの Shared Framework のバージョンです。</span><span class="sxs-lookup"><span data-stu-id="0945a-119">Version of the installed Shared Framework to use to run the application.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="0945a-120">プローブ ポリシーとプローブするアセンブリを含むパスです。</span><span class="sxs-lookup"><span data-stu-id="0945a-120">Path containing probing policy and assemblies to probe.</span></span>

`--version`

<span data-ttu-id="0945a-121">CLI ツールのバージョンを印刷します。</span><span class="sxs-lookup"><span data-stu-id="0945a-121">Prints out the version of the CLI tooling.</span></span>

`--info`

<span data-ttu-id="0945a-122">現在のオペレーティング システム、バージョンのコミット SHA、およびその他の情報など、CLI ツールと環境の詳細情報を印刷します。</span><span class="sxs-lookup"><span data-stu-id="0945a-122">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`-h|--help`

<span data-ttu-id="0945a-123">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="0945a-123">Prints out a short help for the command.</span></span> <span data-ttu-id="0945a-124">`dotnet` で使用すると、使用可能なコマンドのリストも印刷されます。</span><span class="sxs-lookup"><span data-stu-id="0945a-124">If using with `dotnet`, it also prints a list of the available commands.</span></span>

## <a name="dotnet-commands"></a><span data-ttu-id="0945a-125">dotnet コマンド</span><span class="sxs-lookup"><span data-stu-id="0945a-125">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="0945a-126">全般</span><span class="sxs-lookup"><span data-stu-id="0945a-126">General</span></span>

<span data-ttu-id="0945a-127">コマンド</span><span class="sxs-lookup"><span data-stu-id="0945a-127">Command</span></span> | <span data-ttu-id="0945a-128">関数</span><span class="sxs-lookup"><span data-stu-id="0945a-128">Function</span></span>
--- | ---
[<span data-ttu-id="0945a-129">dotnet-build</span><span class="sxs-lookup"><span data-stu-id="0945a-129">dotnet-build</span></span>](dotnet-build.md) | <span data-ttu-id="0945a-130">.NET Core アプリケーションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="0945a-130">Builds a .NET Core application.</span></span>
[<span data-ttu-id="0945a-131">dotnet-clean</span><span class="sxs-lookup"><span data-stu-id="0945a-131">dotnet-clean</span></span>](dotnet-clean.md) | <span data-ttu-id="0945a-132">クリーン ビルド出力。</span><span class="sxs-lookup"><span data-stu-id="0945a-132">Clean build output(s).</span></span>
[<span data-ttu-id="0945a-133">dotnet-migrate</span><span class="sxs-lookup"><span data-stu-id="0945a-133">dotnet-migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="0945a-134">有効な Preview 2 プロジェクトを .NET Core SDK 1.0 プロジェクトに移行します。</span><span class="sxs-lookup"><span data-stu-id="0945a-134">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>
[<span data-ttu-id="0945a-135">dotnet-msbuild</span><span class="sxs-lookup"><span data-stu-id="0945a-135">dotnet-msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="0945a-136">MSBuild コマンド ラインへのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="0945a-136">Provides access to the MSBuild command line.</span></span>
[<span data-ttu-id="0945a-137">dotnet-new</span><span class="sxs-lookup"><span data-stu-id="0945a-137">dotnet-new</span></span>](dotnet-new.md) | <span data-ttu-id="0945a-138">指定されたテンプレートの C# または F# プロジェクトを初期化します。</span><span class="sxs-lookup"><span data-stu-id="0945a-138">Initializes a C# or F# project for a given template.</span></span>
[<span data-ttu-id="0945a-139">dotnet-pack</span><span class="sxs-lookup"><span data-stu-id="0945a-139">dotnet-pack</span></span>](dotnet-pack.md) | <span data-ttu-id="0945a-140">コードの NuGet パッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="0945a-140">Creates a NuGet package of your code.</span></span>
[<span data-ttu-id="0945a-141">dotnet-publish</span><span class="sxs-lookup"><span data-stu-id="0945a-141">dotnet-publish</span></span>](dotnet-publish.md) | <span data-ttu-id="0945a-142">.NET Framework に依存するアプリケーションまたは自己完結型アプリケーションを発行します。</span><span class="sxs-lookup"><span data-stu-id="0945a-142">Publishes a .NET framework-dependent or self-contained application.</span></span>
[<span data-ttu-id="0945a-143">dotnet-restore</span><span class="sxs-lookup"><span data-stu-id="0945a-143">dotnet-restore</span></span>](dotnet-restore.md) | <span data-ttu-id="0945a-144">指定されたアプリケーションの依存関係を復元します。</span><span class="sxs-lookup"><span data-stu-id="0945a-144">Restores the dependencies for a given application.</span></span>
[<span data-ttu-id="0945a-145">dotnet-run</span><span class="sxs-lookup"><span data-stu-id="0945a-145">dotnet-run</span></span>](dotnet-run.md) | <span data-ttu-id="0945a-146">ソースからアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="0945a-146">Runs the application from source.</span></span>
[<span data-ttu-id="0945a-147">dotnet-sln</span><span class="sxs-lookup"><span data-stu-id="0945a-147">dotnet-sln</span></span>](dotnet-sln.md) | <span data-ttu-id="0945a-148">ソリューション ファイルのプロジェクトを追加、削除、一覧表示するオプション。</span><span class="sxs-lookup"><span data-stu-id="0945a-148">Options to add, remove, and list projects in a solution file.</span></span>
[<span data-ttu-id="0945a-149">dotnet-test</span><span class="sxs-lookup"><span data-stu-id="0945a-149">dotnet-test</span></span>](dotnet-test.md) | <span data-ttu-id="0945a-150">テスト ランナーを使用してテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="0945a-150">Runs tests using a test runner.</span></span>

### <a name="project-references"></a><span data-ttu-id="0945a-151">プロジェクト参照</span><span class="sxs-lookup"><span data-stu-id="0945a-151">Project references</span></span>

<span data-ttu-id="0945a-152">コマンド</span><span class="sxs-lookup"><span data-stu-id="0945a-152">Command</span></span> | <span data-ttu-id="0945a-153">関数</span><span class="sxs-lookup"><span data-stu-id="0945a-153">Function</span></span>
--- | ---
[<span data-ttu-id="0945a-154">dotnet-add 参照</span><span class="sxs-lookup"><span data-stu-id="0945a-154">dotnet-add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="0945a-155">プロジェクト参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="0945a-155">Add a project reference.</span></span>
[<span data-ttu-id="0945a-156">dotnet-list 参照</span><span class="sxs-lookup"><span data-stu-id="0945a-156">dotnet-list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="0945a-157">プロジェクト参照をリストします。</span><span class="sxs-lookup"><span data-stu-id="0945a-157">List project references.</span></span>
[<span data-ttu-id="0945a-158">dotnet-remove 参照</span><span class="sxs-lookup"><span data-stu-id="0945a-158">dotnet-remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="0945a-159">プロジェクト参照を削除します。</span><span class="sxs-lookup"><span data-stu-id="0945a-159">Remove a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="0945a-160">NuGet パッケージ</span><span class="sxs-lookup"><span data-stu-id="0945a-160">NuGet packages</span></span>

<span data-ttu-id="0945a-161">コマンド</span><span class="sxs-lookup"><span data-stu-id="0945a-161">Command</span></span> | <span data-ttu-id="0945a-162">関数</span><span class="sxs-lookup"><span data-stu-id="0945a-162">Function</span></span>
--- | ---
[<span data-ttu-id="0945a-163">dotnet-add パッケージ</span><span class="sxs-lookup"><span data-stu-id="0945a-163">dotnet-add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="0945a-164">NuGet パッケージを追加します。</span><span class="sxs-lookup"><span data-stu-id="0945a-164">Add a NuGet package.</span></span>
[<span data-ttu-id="0945a-165">dotnet-remove パッケージ</span><span class="sxs-lookup"><span data-stu-id="0945a-165">dotnet-remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="0945a-166">NuGet パッケージを削除します。</span><span class="sxs-lookup"><span data-stu-id="0945a-166">Remove a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="0945a-167">NuGet コマンド</span><span class="sxs-lookup"><span data-stu-id="0945a-167">NuGet commands</span></span>

<span data-ttu-id="0945a-168">コマンド</span><span class="sxs-lookup"><span data-stu-id="0945a-168">Command</span></span> | <span data-ttu-id="0945a-169">関数</span><span class="sxs-lookup"><span data-stu-id="0945a-169">Function</span></span>
--- | ---
[<span data-ttu-id="0945a-170">dotnet-nuget delete</span><span class="sxs-lookup"><span data-stu-id="0945a-170">dotnet-nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="0945a-171">サーバーからパッケージを削除または一覧から削除します。</span><span class="sxs-lookup"><span data-stu-id="0945a-171">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="0945a-172">dotnet-nuget locals</span><span class="sxs-lookup"><span data-stu-id="0945a-172">dotnet-nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="0945a-173">HTTP 要求キャッシュ、一時的なキャッシュ、コンピューター全体のグローバル パッケージ フォルダーなどのローカルの NuGet リソースをクリアまたは一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="0945a-173">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="0945a-174">dotnet-nuget push</span><span class="sxs-lookup"><span data-stu-id="0945a-174">dotnet-nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="0945a-175">パッケージをサーバーにプッシュして発行します。</span><span class="sxs-lookup"><span data-stu-id="0945a-175">Pushes a package to the server and publishes it.</span></span>

## <a name="examples"></a><span data-ttu-id="0945a-176">例</span><span class="sxs-lookup"><span data-stu-id="0945a-176">Examples</span></span>

<span data-ttu-id="0945a-177">コンパイルして実行できるサンプルの .NET Core コンソール アプリケーションを初期化します。</span><span class="sxs-lookup"><span data-stu-id="0945a-177">Initialize a sample .NET Core console application that can be compiled and run:</span></span>

`dotnet new console`

<span data-ttu-id="0945a-178">指定されたアプリケーションの依存関係を復元します。</span><span class="sxs-lookup"><span data-stu-id="0945a-178">Restore dependencies for a given application:</span></span>

`dotnet restore`

<span data-ttu-id="0945a-179">指定されたディレクトリにプロジェクトとその依存関係をビルドします。</span><span class="sxs-lookup"><span data-stu-id="0945a-179">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="0945a-180">`myapp.dll` という名前のフレームワークに依存するアプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="0945a-180">Run a framework-dependent app named `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="0945a-181">環境変数</span><span class="sxs-lookup"><span data-stu-id="0945a-181">Environment variables</span></span>

`DOTNET_PACKAGES`

<span data-ttu-id="0945a-182">プライマリ パッケージのキャッシュです。</span><span class="sxs-lookup"><span data-stu-id="0945a-182">The primary package cache.</span></span> <span data-ttu-id="0945a-183">設定されていない場合は、既定で `$HOME/.nuget/packages` (Unix の場合) または `%HOME%\NuGet\Packages` (Windows の場合) になります。</span><span class="sxs-lookup"><span data-stu-id="0945a-183">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="0945a-184">ランタイムの読み込み時に共有ホストで使用するサービス インデックスの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="0945a-184">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="0945a-185">.NET Core ツールの使用に関するデータを収集し、Microsoft に送信するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="0945a-185">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="0945a-186">`true` に設定するとテレメトリ機能が無効になります (指定できる値は `true`、`1`、または `yes` です)。それ以外の場合は `false` に設定します。この場合、テレメトリ機能が有効になります (指定できる値は `false`、`0`、または `no` です)。</span><span class="sxs-lookup"><span data-stu-id="0945a-186">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted); otherwise, set to `false` to opt-in to the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="0945a-187">設定されていない場合、既定で `false` になり、テレメトリ機能はアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="0945a-187">If not set, the defaults is `false`, and the telemetry feature is active.</span></span>

