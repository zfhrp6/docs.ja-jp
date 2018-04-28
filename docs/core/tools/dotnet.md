---
title: dotnet コマンド - .NET Core CLI
description: dotnet コマンド (.NET Core CLI ツールの一般的なドライバー) とその使用法について説明します。
author: mairaw
ms.author: mairaw
ms.date: 03/20/2018
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: bf69be7eb8dfe454823236012113fa53ed39f2f4
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-command"></a><span data-ttu-id="fb264-103">dotnet コマンド</span><span class="sxs-lookup"><span data-stu-id="fb264-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="fb264-104">name</span><span class="sxs-lookup"><span data-stu-id="fb264-104">Name</span></span>

<span data-ttu-id="fb264-105">`dotnet` - コマンドラインのコマンドを実行するための一般的なドライバーです。</span><span class="sxs-lookup"><span data-stu-id="fb264-105">`dotnet` - General driver for running the command-line commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="fb264-106">構文</span><span class="sxs-lookup"><span data-stu-id="fb264-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="fb264-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="fb264-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="fb264-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="fb264-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [-v|--verbosity] [--version]
```
---

## <a name="description"></a><span data-ttu-id="fb264-109">説明</span><span class="sxs-lookup"><span data-stu-id="fb264-109">Description</span></span>

<span data-ttu-id="fb264-110">`dotnet` は、コマンド ライン インターフェイス (CLI) ツールチェーンの一般的なドライバーです。</span><span class="sxs-lookup"><span data-stu-id="fb264-110">`dotnet` is a generic driver for the Command Line Interface (CLI) toolchain.</span></span> <span data-ttu-id="fb264-111">単独で呼び出され、簡単な使用方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="fb264-111">Invoked on its own, it provides brief usage instructions.</span></span>

<span data-ttu-id="fb264-112">特定の機能がそれぞれコマンドとして実装されます。</span><span class="sxs-lookup"><span data-stu-id="fb264-112">Each specific feature is implemented as a command.</span></span> <span data-ttu-id="fb264-113">機能を使用するには、[`dotnet build`](dotnet-build.md) のように、`dotnet` の後にコマンドを指定します。</span><span class="sxs-lookup"><span data-stu-id="fb264-113">In order to use the feature, the command is specified after `dotnet`, such as [`dotnet build`](dotnet-build.md).</span></span> <span data-ttu-id="fb264-114">コマンドに続く引数はすべて独自の引数です。</span><span class="sxs-lookup"><span data-stu-id="fb264-114">All of the arguments following the command are its own arguments.</span></span>

<span data-ttu-id="fb264-115">`dotnet` が単独でコマンドとして使用されるのは、[フレームワークに依存するアプリ](../deploying/index.md)を実行する場合のみです。</span><span class="sxs-lookup"><span data-stu-id="fb264-115">The only time `dotnet` is used as a command on its own is to run [framework-dependent apps](../deploying/index.md).</span></span> <span data-ttu-id="fb264-116">アプリケーションを実行する場合は、`dotnet` の動詞の後にアプリケーション DLL を指定します (`dotnet myapp.dll` など)。</span><span class="sxs-lookup"><span data-stu-id="fb264-116">Specify an application DLL after the `dotnet` verb to execute the application (for example, `dotnet myapp.dll`).</span></span>

## <a name="options"></a><span data-ttu-id="fb264-117">オプション</span><span class="sxs-lookup"><span data-stu-id="fb264-117">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="fb264-118">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="fb264-118">.NET Core 2.x</span></span>](#tab/netcore2x)

`--additional-deps <PATH>`

<span data-ttu-id="fb264-119">追加の *deps.json* ファイルへのパスです。</span><span class="sxs-lookup"><span data-stu-id="fb264-119">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="fb264-120">プローブ ポリシーとプローブするアセンブリを含むパスです。</span><span class="sxs-lookup"><span data-stu-id="fb264-120">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="fb264-121">診断出力を有効にします。</span><span class="sxs-lookup"><span data-stu-id="fb264-121">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="fb264-122">アプリケーションを実行するために使用するインストール済み .NET Core ランタイムのバージョンです。</span><span class="sxs-lookup"><span data-stu-id="fb264-122">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="fb264-123">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="fb264-123">Prints out a short help for the command.</span></span> <span data-ttu-id="fb264-124">`dotnet` で使用すると、使用可能なコマンドのリストも印刷されます。</span><span class="sxs-lookup"><span data-stu-id="fb264-124">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="fb264-125">現在のオペレーティング システム、バージョンのコミット SHA、およびその他の情報など、CLI ツールと環境の詳細情報を印刷します。</span><span class="sxs-lookup"><span data-stu-id="fb264-125">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="fb264-126">共有フレームワークの候補なしでロールフォワードします。</span><span class="sxs-lookup"><span data-stu-id="fb264-126">Rolls forward on no candidate shared framework.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="fb264-127">コマンドの詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="fb264-127">Sets the verbosity level of the command.</span></span> <span data-ttu-id="fb264-128">指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。</span><span class="sxs-lookup"><span data-stu-id="fb264-128">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="fb264-129">一部のコマンドではサポートされていません。このオプションが使用可能かどうかを判断するには、対象のコマンドのページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="fb264-129">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="fb264-130">使用中の .NET Core SDK のバージョンを印刷します。</span><span class="sxs-lookup"><span data-stu-id="fb264-130">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="fb264-131">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="fb264-131">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="fb264-132">プローブ ポリシーとプローブするアセンブリを含むパスです。</span><span class="sxs-lookup"><span data-stu-id="fb264-132">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="fb264-133">診断出力を有効にします。</span><span class="sxs-lookup"><span data-stu-id="fb264-133">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="fb264-134">アプリケーションを実行するために使用するインストール済み .NET Core ランタイムのバージョンです。</span><span class="sxs-lookup"><span data-stu-id="fb264-134">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="fb264-135">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="fb264-135">Prints out a short help for the command.</span></span> <span data-ttu-id="fb264-136">`dotnet` で使用すると、使用可能なコマンドのリストも印刷されます。</span><span class="sxs-lookup"><span data-stu-id="fb264-136">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="fb264-137">現在のオペレーティング システム、バージョンのコミット SHA、およびその他の情報など、CLI ツールと環境の詳細情報を印刷します。</span><span class="sxs-lookup"><span data-stu-id="fb264-137">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="fb264-138">コマンドの詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="fb264-138">Sets the verbosity level of the command.</span></span> <span data-ttu-id="fb264-139">指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。</span><span class="sxs-lookup"><span data-stu-id="fb264-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="fb264-140">一部のコマンドではサポートされていません。このオプションが使用可能かどうかを判断するには、対象のコマンドのページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="fb264-140">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="fb264-141">使用中の .NET Core SDK のバージョンを印刷します。</span><span class="sxs-lookup"><span data-stu-id="fb264-141">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="fb264-142">dotnet コマンド</span><span class="sxs-lookup"><span data-stu-id="fb264-142">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="fb264-143">全般</span><span class="sxs-lookup"><span data-stu-id="fb264-143">General</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="fb264-144">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="fb264-144">.NET Core 2.x</span></span>](#tab/netcore2x)

| <span data-ttu-id="fb264-145">コマンド</span><span class="sxs-lookup"><span data-stu-id="fb264-145">Command</span></span>                             | <span data-ttu-id="fb264-146">関数</span><span class="sxs-lookup"><span data-stu-id="fb264-146">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="fb264-147">dotnet build</span><span class="sxs-lookup"><span data-stu-id="fb264-147">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="fb264-148">.NET Core アプリケーションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="fb264-148">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="fb264-149">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="fb264-149">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="fb264-150">クリーン ビルド出力です。</span><span class="sxs-lookup"><span data-stu-id="fb264-150">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="fb264-151">dotnet help</span><span class="sxs-lookup"><span data-stu-id="fb264-151">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="fb264-152">コマンドのより詳細なドキュメントをオンラインで表示します。</span><span class="sxs-lookup"><span data-stu-id="fb264-152">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="fb264-153">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="fb264-153">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="fb264-154">有効な Preview 2 プロジェクトを .NET Core SDK 1.0 プロジェクトに移行します。</span><span class="sxs-lookup"><span data-stu-id="fb264-154">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="fb264-155">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="fb264-155">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="fb264-156">MSBuild コマンド ラインへのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="fb264-156">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="fb264-157">dotnet new</span><span class="sxs-lookup"><span data-stu-id="fb264-157">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="fb264-158">指定されたテンプレートの C# または F# プロジェクトを初期化します。</span><span class="sxs-lookup"><span data-stu-id="fb264-158">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="fb264-159">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="fb264-159">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="fb264-160">コードの NuGet パッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="fb264-160">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="fb264-161">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="fb264-161">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="fb264-162">.NET Framework に依存するアプリケーションまたは自己完結型アプリケーションを発行します。</span><span class="sxs-lookup"><span data-stu-id="fb264-162">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="fb264-163">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="fb264-163">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="fb264-164">指定されたアプリケーションの依存関係を復元します。</span><span class="sxs-lookup"><span data-stu-id="fb264-164">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="fb264-165">dotnet run</span><span class="sxs-lookup"><span data-stu-id="fb264-165">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="fb264-166">ソースからアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="fb264-166">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="fb264-167">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="fb264-167">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="fb264-168">ソリューション ファイルのプロジェクトを追加、削除、一覧表示するオプション。</span><span class="sxs-lookup"><span data-stu-id="fb264-168">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="fb264-169">dotnet store</span><span class="sxs-lookup"><span data-stu-id="fb264-169">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="fb264-170">ランタイム パッケージ ストアにアセンブリを格納します。</span><span class="sxs-lookup"><span data-stu-id="fb264-170">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="fb264-171">dotnet test</span><span class="sxs-lookup"><span data-stu-id="fb264-171">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="fb264-172">テスト ランナーを使用してテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="fb264-172">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="fb264-173">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="fb264-173">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="fb264-174">コマンド</span><span class="sxs-lookup"><span data-stu-id="fb264-174">Command</span></span>                             | <span data-ttu-id="fb264-175">関数</span><span class="sxs-lookup"><span data-stu-id="fb264-175">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="fb264-176">dotnet build</span><span class="sxs-lookup"><span data-stu-id="fb264-176">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="fb264-177">.NET Core アプリケーションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="fb264-177">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="fb264-178">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="fb264-178">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="fb264-179">クリーン ビルド出力です。</span><span class="sxs-lookup"><span data-stu-id="fb264-179">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="fb264-180">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="fb264-180">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="fb264-181">有効な Preview 2 プロジェクトを .NET Core SDK 1.0 プロジェクトに移行します。</span><span class="sxs-lookup"><span data-stu-id="fb264-181">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="fb264-182">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="fb264-182">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="fb264-183">MSBuild コマンド ラインへのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="fb264-183">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="fb264-184">dotnet new</span><span class="sxs-lookup"><span data-stu-id="fb264-184">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="fb264-185">指定されたテンプレートの C# または F# プロジェクトを初期化します。</span><span class="sxs-lookup"><span data-stu-id="fb264-185">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="fb264-186">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="fb264-186">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="fb264-187">コードの NuGet パッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="fb264-187">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="fb264-188">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="fb264-188">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="fb264-189">.NET Framework に依存するアプリケーションまたは自己完結型アプリケーションを発行します。</span><span class="sxs-lookup"><span data-stu-id="fb264-189">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="fb264-190">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="fb264-190">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="fb264-191">指定されたアプリケーションの依存関係を復元します。</span><span class="sxs-lookup"><span data-stu-id="fb264-191">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="fb264-192">dotnet run</span><span class="sxs-lookup"><span data-stu-id="fb264-192">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="fb264-193">ソースからアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="fb264-193">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="fb264-194">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="fb264-194">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="fb264-195">ソリューション ファイルのプロジェクトを追加、削除、一覧表示するオプション。</span><span class="sxs-lookup"><span data-stu-id="fb264-195">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="fb264-196">dotnet test</span><span class="sxs-lookup"><span data-stu-id="fb264-196">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="fb264-197">テスト ランナーを使用してテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="fb264-197">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="fb264-198">プロジェクト参照</span><span class="sxs-lookup"><span data-stu-id="fb264-198">Project references</span></span>

<span data-ttu-id="fb264-199">コマンド</span><span class="sxs-lookup"><span data-stu-id="fb264-199">Command</span></span> | <span data-ttu-id="fb264-200">関数</span><span class="sxs-lookup"><span data-stu-id="fb264-200">Function</span></span>
--- | ---
[<span data-ttu-id="fb264-201">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="fb264-201">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="fb264-202">プロジェクト参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="fb264-202">Add a project reference.</span></span>
[<span data-ttu-id="fb264-203">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="fb264-203">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="fb264-204">プロジェクト参照をリストします。</span><span class="sxs-lookup"><span data-stu-id="fb264-204">List project references.</span></span>
[<span data-ttu-id="fb264-205">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="fb264-205">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="fb264-206">プロジェクト参照を削除します。</span><span class="sxs-lookup"><span data-stu-id="fb264-206">Remove a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="fb264-207">NuGet パッケージ</span><span class="sxs-lookup"><span data-stu-id="fb264-207">NuGet packages</span></span>

<span data-ttu-id="fb264-208">コマンド</span><span class="sxs-lookup"><span data-stu-id="fb264-208">Command</span></span> | <span data-ttu-id="fb264-209">関数</span><span class="sxs-lookup"><span data-stu-id="fb264-209">Function</span></span>
--- | ---
[<span data-ttu-id="fb264-210">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="fb264-210">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="fb264-211">NuGet パッケージを追加します。</span><span class="sxs-lookup"><span data-stu-id="fb264-211">Add a NuGet package.</span></span>
[<span data-ttu-id="fb264-212">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="fb264-212">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="fb264-213">NuGet パッケージを削除します。</span><span class="sxs-lookup"><span data-stu-id="fb264-213">Remove a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="fb264-214">NuGet コマンド</span><span class="sxs-lookup"><span data-stu-id="fb264-214">NuGet commands</span></span>

<span data-ttu-id="fb264-215">コマンド</span><span class="sxs-lookup"><span data-stu-id="fb264-215">Command</span></span> | <span data-ttu-id="fb264-216">関数</span><span class="sxs-lookup"><span data-stu-id="fb264-216">Function</span></span>
--- | ---
[<span data-ttu-id="fb264-217">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="fb264-217">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="fb264-218">サーバーからパッケージを削除または一覧から削除します。</span><span class="sxs-lookup"><span data-stu-id="fb264-218">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="fb264-219">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="fb264-219">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="fb264-220">HTTP 要求キャッシュ、一時的なキャッシュ、コンピューター全体のグローバル パッケージ フォルダーなどのローカルの NuGet リソースをクリアまたは一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="fb264-220">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="fb264-221">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="fb264-221">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="fb264-222">パッケージをサーバーにプッシュして発行します。</span><span class="sxs-lookup"><span data-stu-id="fb264-222">Pushes a package to the server and publishes it.</span></span>

## <a name="examples"></a><span data-ttu-id="fb264-223">使用例</span><span class="sxs-lookup"><span data-stu-id="fb264-223">Examples</span></span>

<span data-ttu-id="fb264-224">コンパイルして実行できるサンプルの .NET Core コンソール アプリケーションを初期化します。</span><span class="sxs-lookup"><span data-stu-id="fb264-224">Initialize a sample .NET Core console application that can be compiled and run:</span></span>

`dotnet new console`

<span data-ttu-id="fb264-225">指定されたアプリケーションの依存関係を復元します。</span><span class="sxs-lookup"><span data-stu-id="fb264-225">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="fb264-226">指定されたディレクトリにプロジェクトとその依存関係をビルドします。</span><span class="sxs-lookup"><span data-stu-id="fb264-226">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="fb264-227">`myapp.dll` という名前のフレームワークに依存するアプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="fb264-227">Run a framework-dependent app named `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="fb264-228">環境変数</span><span class="sxs-lookup"><span data-stu-id="fb264-228">Environment variables</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="fb264-229">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="fb264-229">.NET Core 2.x</span></span>](#tab/netcore2x)

`DOTNET_PACKAGES`

<span data-ttu-id="fb264-230">プライマリ パッケージのキャッシュです。</span><span class="sxs-lookup"><span data-stu-id="fb264-230">The primary package cache.</span></span> <span data-ttu-id="fb264-231">設定されていない場合は、既定で `$HOME/.nuget/packages` (Unix の場合) または `%HOME%\NuGet\Packages` (Windows の場合) になります。</span><span class="sxs-lookup"><span data-stu-id="fb264-231">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="fb264-232">ランタイムの読み込み時に共有ホストで使用するサービス インデックスの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="fb264-232">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="fb264-233">.NET Core ツールの使用に関するデータを収集し、Microsoft に送信するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="fb264-233">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="fb264-234">`true` に設定するとテレメトリ機能が無効になります (指定できる値は `true`、`1`、または `yes` です)。それ以外の場合は `false` に設定します。この場合、テレメトリ機能が有効になります (指定できる値は `false`、`0`、または `no` です)。</span><span class="sxs-lookup"><span data-stu-id="fb264-234">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted); otherwise, set to `false` to opt-in to the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="fb264-235">設定されていない場合、既定で `false` になり、テレメトリ機能はアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="fb264-235">If not set, the defaults is `false`, and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="fb264-236">.NET Core ランタイム、共有フレームワークまたは SDK がグローバルな場所から解決されるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="fb264-236">Specifies whether .NET Core runtime, shared framework or SDK are resolved from the global location.</span></span> <span data-ttu-id="fb264-237">設定されていない場合は、既定で `true` になります。</span><span class="sxs-lookup"><span data-stu-id="fb264-237">If not set, it defaults to `true`.</span></span> <span data-ttu-id="fb264-238">`false` に設定すると、グローバルな場所から解決されず、.NET Core インストールが分離されます (値 `0` または `false` が受け入れられます)。</span><span class="sxs-lookup"><span data-stu-id="fb264-238">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="fb264-239">複数レベルのルックアップの詳細については、「[Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md)」 (複数レベルの SharedFX ルックアップ) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fb264-239">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="fb264-240">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="fb264-240">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="fb264-241">プライマリ パッケージのキャッシュです。</span><span class="sxs-lookup"><span data-stu-id="fb264-241">The primary package cache.</span></span> <span data-ttu-id="fb264-242">設定されていない場合は、既定で `$HOME/.nuget/packages` (Unix の場合) または `%HOME%\NuGet\Packages` (Windows の場合) になります。</span><span class="sxs-lookup"><span data-stu-id="fb264-242">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="fb264-243">ランタイムの読み込み時に共有ホストで使用するサービス インデックスの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="fb264-243">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="fb264-244">.NET Core ツールの使用に関するデータを収集し、Microsoft に送信するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="fb264-244">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="fb264-245">`true` に設定するとテレメトリ機能が無効になります (指定できる値は `true`、`1`、または `yes` です)。それ以外の場合は `false` に設定します。この場合、テレメトリ機能が有効になります (指定できる値は `false`、`0`、または `no` です)。</span><span class="sxs-lookup"><span data-stu-id="fb264-245">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted); otherwise, set to `false` to opt-in to the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="fb264-246">設定されていない場合、既定で `false` になり、テレメトリ機能はアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="fb264-246">If not set, the defaults is `false`, and the telemetry feature is active.</span></span>

---
