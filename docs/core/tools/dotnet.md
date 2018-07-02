---
title: dotnet コマンド - .NET Core CLI
description: dotnet コマンド (.NET Core CLI ツールの一般的なドライバー) とその使用法について説明します。
author: mairaw
ms.author: mairaw
ms.date: 06/04/2018
ms.openlocfilehash: 788dc746705f9328683019ab3ad9836204a1ea63
ms.sourcegitcommit: fc70fcb9c789b6a4aefcdace46f3643fd076450f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2018
ms.locfileid: "34805660"
---
# <a name="dotnet-command"></a><span data-ttu-id="08d49-103">dotnet コマンド</span><span class="sxs-lookup"><span data-stu-id="08d49-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="08d49-104">name</span><span class="sxs-lookup"><span data-stu-id="08d49-104">Name</span></span>

<span data-ttu-id="08d49-105">`dotnet` - コマンドラインのコマンドを実行するための一般的なドライバーです。</span><span class="sxs-lookup"><span data-stu-id="08d49-105">`dotnet` - General driver for running the command-line commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="08d49-106">構文</span><span class="sxs-lookup"><span data-stu-id="08d49-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="08d49-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="08d49-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="08d49-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="08d49-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="08d49-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="08d49-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [-v|--verbosity] [--version]
```
---

## <a name="description"></a><span data-ttu-id="08d49-110">説明</span><span class="sxs-lookup"><span data-stu-id="08d49-110">Description</span></span>

<span data-ttu-id="08d49-111">`dotnet` は、コマンド ライン インターフェイス (CLI) ツールチェーンの一般的なドライバーです。</span><span class="sxs-lookup"><span data-stu-id="08d49-111">`dotnet` is a generic driver for the Command Line Interface (CLI) toolchain.</span></span> <span data-ttu-id="08d49-112">単独で呼び出され、簡単な使用方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="08d49-112">Invoked on its own, it provides brief usage instructions.</span></span>

<span data-ttu-id="08d49-113">特定の機能がそれぞれコマンドとして実装されます。</span><span class="sxs-lookup"><span data-stu-id="08d49-113">Each specific feature is implemented as a command.</span></span> <span data-ttu-id="08d49-114">機能を使用するには、[`dotnet build`](dotnet-build.md) のように、`dotnet` の後にコマンドを指定します。</span><span class="sxs-lookup"><span data-stu-id="08d49-114">To use the feature, the command is specified after `dotnet`, such as [`dotnet build`](dotnet-build.md).</span></span> <span data-ttu-id="08d49-115">コマンドに続く引数はすべて独自の引数です。</span><span class="sxs-lookup"><span data-stu-id="08d49-115">All of the arguments following the command are its own arguments.</span></span>

<span data-ttu-id="08d49-116">`dotnet` が単独でコマンドとして使用されるのは、[フレームワークに依存するアプリ](../deploying/index.md)を実行する場合のみです。</span><span class="sxs-lookup"><span data-stu-id="08d49-116">The only time `dotnet` is used as a command on its own is to run [framework-dependent apps](../deploying/index.md).</span></span> <span data-ttu-id="08d49-117">アプリケーションを実行する場合は、`dotnet` の動詞の後にアプリケーション DLL を指定します (`dotnet myapp.dll` など)。</span><span class="sxs-lookup"><span data-stu-id="08d49-117">Specify an application DLL after the `dotnet` verb to execute the application (for example, `dotnet myapp.dll`).</span></span>

## <a name="options"></a><span data-ttu-id="08d49-118">オプション</span><span class="sxs-lookup"><span data-stu-id="08d49-118">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="08d49-119">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="08d49-119">.NET Core 2.1</span></span>](#tab/netcore21)

`--additional-deps <PATH>`

<span data-ttu-id="08d49-120">追加の *deps.json* ファイルへのパスです。</span><span class="sxs-lookup"><span data-stu-id="08d49-120">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="08d49-121">プローブ ポリシーとプローブするアセンブリを含むパスです。</span><span class="sxs-lookup"><span data-stu-id="08d49-121">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="08d49-122">診断出力を有効にします。</span><span class="sxs-lookup"><span data-stu-id="08d49-122">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="08d49-123">アプリケーションを実行するために使用するインストール済み .NET Core ランタイムのバージョンです。</span><span class="sxs-lookup"><span data-stu-id="08d49-123">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="08d49-124">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="08d49-124">Prints out a short help for the command.</span></span> <span data-ttu-id="08d49-125">`dotnet` で使用すると、使用可能なコマンドのリストも印刷されます。</span><span class="sxs-lookup"><span data-stu-id="08d49-125">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="08d49-126">現在のオペレーティング システム、バージョンのコミット SHA、およびその他の情報など、CLI ツールと環境の詳細情報を印刷します。</span><span class="sxs-lookup"><span data-stu-id="08d49-126">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`--list-runtimes`

<span data-ttu-id="08d49-127">インストールされている .NET Core ランタイムを表示します。</span><span class="sxs-lookup"><span data-stu-id="08d49-127">Displays the installed .NET Core runtimes.</span></span>

`--list-sdks`

<span data-ttu-id="08d49-128">インストールされている .NET Core SDK を表示します。</span><span class="sxs-lookup"><span data-stu-id="08d49-128">Displays the installed .NET Core SDKs.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="08d49-129">共有フレームワークの候補なしでロールフォワードします。</span><span class="sxs-lookup"><span data-stu-id="08d49-129">Rolls forward on no candidate shared framework.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="08d49-130">コマンドの詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="08d49-130">Sets the verbosity level of the command.</span></span> <span data-ttu-id="08d49-131">指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。</span><span class="sxs-lookup"><span data-stu-id="08d49-131">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="08d49-132">一部のコマンドではサポートされていません。このオプションが使用可能かどうかを判断するには、対象のコマンドのページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="08d49-132">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="08d49-133">使用中の .NET Core SDK のバージョンを印刷します。</span><span class="sxs-lookup"><span data-stu-id="08d49-133">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="08d49-134">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="08d49-134">.NET Core 2.0</span></span>](#tab/netcore20)

`--additional-deps <PATH>`

<span data-ttu-id="08d49-135">追加の *deps.json* ファイルへのパスです。</span><span class="sxs-lookup"><span data-stu-id="08d49-135">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="08d49-136">プローブ ポリシーとプローブするアセンブリを含むパスです。</span><span class="sxs-lookup"><span data-stu-id="08d49-136">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="08d49-137">診断出力を有効にします。</span><span class="sxs-lookup"><span data-stu-id="08d49-137">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="08d49-138">アプリケーションを実行するために使用するインストール済み .NET Core ランタイムのバージョンです。</span><span class="sxs-lookup"><span data-stu-id="08d49-138">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="08d49-139">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="08d49-139">Prints out a short help for the command.</span></span> <span data-ttu-id="08d49-140">`dotnet` で使用すると、使用可能なコマンドのリストも印刷されます。</span><span class="sxs-lookup"><span data-stu-id="08d49-140">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="08d49-141">現在のオペレーティング システム、バージョンのコミット SHA、およびその他の情報など、CLI ツールと環境の詳細情報を印刷します。</span><span class="sxs-lookup"><span data-stu-id="08d49-141">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="08d49-142">共有フレームワークの候補なしでロールフォワードします。</span><span class="sxs-lookup"><span data-stu-id="08d49-142">Rolls forward on no candidate shared framework.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="08d49-143">コマンドの詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="08d49-143">Sets the verbosity level of the command.</span></span> <span data-ttu-id="08d49-144">指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。</span><span class="sxs-lookup"><span data-stu-id="08d49-144">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="08d49-145">一部のコマンドではサポートされていません。このオプションが使用可能かどうかを判断するには、対象のコマンドのページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="08d49-145">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="08d49-146">使用中の .NET Core SDK のバージョンを印刷します。</span><span class="sxs-lookup"><span data-stu-id="08d49-146">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="08d49-147">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="08d49-147">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="08d49-148">プローブ ポリシーとプローブするアセンブリを含むパスです。</span><span class="sxs-lookup"><span data-stu-id="08d49-148">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="08d49-149">診断出力を有効にします。</span><span class="sxs-lookup"><span data-stu-id="08d49-149">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="08d49-150">アプリケーションを実行するために使用するインストール済み .NET Core ランタイムのバージョンです。</span><span class="sxs-lookup"><span data-stu-id="08d49-150">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="08d49-151">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="08d49-151">Prints out a short help for the command.</span></span> <span data-ttu-id="08d49-152">`dotnet` で使用すると、使用可能なコマンドのリストも印刷されます。</span><span class="sxs-lookup"><span data-stu-id="08d49-152">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="08d49-153">現在のオペレーティング システム、バージョンのコミット SHA、およびその他の情報など、CLI ツールと環境の詳細情報を印刷します。</span><span class="sxs-lookup"><span data-stu-id="08d49-153">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="08d49-154">コマンドの詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="08d49-154">Sets the verbosity level of the command.</span></span> <span data-ttu-id="08d49-155">指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。</span><span class="sxs-lookup"><span data-stu-id="08d49-155">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="08d49-156">一部のコマンドではサポートされていません。このオプションが使用可能かどうかを判断するには、対象のコマンドのページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="08d49-156">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="08d49-157">使用中の .NET Core SDK のバージョンを印刷します。</span><span class="sxs-lookup"><span data-stu-id="08d49-157">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="08d49-158">dotnet コマンド</span><span class="sxs-lookup"><span data-stu-id="08d49-158">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="08d49-159">全般</span><span class="sxs-lookup"><span data-stu-id="08d49-159">General</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="08d49-160">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="08d49-160">.NET Core 2.1</span></span>](#tab/netcore21)

| <span data-ttu-id="08d49-161">コマンド</span><span class="sxs-lookup"><span data-stu-id="08d49-161">Command</span></span>                                       | <span data-ttu-id="08d49-162">関数</span><span class="sxs-lookup"><span data-stu-id="08d49-162">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="08d49-163">dotnet build</span><span class="sxs-lookup"><span data-stu-id="08d49-163">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="08d49-164">.NET Core アプリケーションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="08d49-164">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="08d49-165">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="08d49-165">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="08d49-166">ビルドによって起動されたサーバーとやり取りします。</span><span class="sxs-lookup"><span data-stu-id="08d49-166">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="08d49-167">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="08d49-167">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="08d49-168">クリーン ビルド出力です。</span><span class="sxs-lookup"><span data-stu-id="08d49-168">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="08d49-169">dotnet help</span><span class="sxs-lookup"><span data-stu-id="08d49-169">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="08d49-170">コマンドのより詳細なドキュメントをオンラインで表示します。</span><span class="sxs-lookup"><span data-stu-id="08d49-170">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="08d49-171">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="08d49-171">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="08d49-172">有効な Preview 2 プロジェクトを .NET Core SDK 1.0 プロジェクトに移行します。</span><span class="sxs-lookup"><span data-stu-id="08d49-172">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="08d49-173">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="08d49-173">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="08d49-174">MSBuild コマンド ラインへのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="08d49-174">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="08d49-175">dotnet new</span><span class="sxs-lookup"><span data-stu-id="08d49-175">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="08d49-176">指定されたテンプレートの C# または F# プロジェクトを初期化します。</span><span class="sxs-lookup"><span data-stu-id="08d49-176">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="08d49-177">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="08d49-177">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="08d49-178">コードの NuGet パッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="08d49-178">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="08d49-179">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="08d49-179">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="08d49-180">.NET Framework に依存するアプリケーションまたは自己完結型アプリケーションを発行します。</span><span class="sxs-lookup"><span data-stu-id="08d49-180">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="08d49-181">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="08d49-181">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="08d49-182">指定されたアプリケーションの依存関係を復元します。</span><span class="sxs-lookup"><span data-stu-id="08d49-182">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="08d49-183">dotnet run</span><span class="sxs-lookup"><span data-stu-id="08d49-183">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="08d49-184">ソースからアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="08d49-184">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="08d49-185">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="08d49-185">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="08d49-186">ソリューション ファイルのプロジェクトを追加、削除、一覧表示するオプション。</span><span class="sxs-lookup"><span data-stu-id="08d49-186">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="08d49-187">dotnet store</span><span class="sxs-lookup"><span data-stu-id="08d49-187">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="08d49-188">ランタイム パッケージ ストアにアセンブリを格納します。</span><span class="sxs-lookup"><span data-stu-id="08d49-188">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="08d49-189">dotnet test</span><span class="sxs-lookup"><span data-stu-id="08d49-189">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="08d49-190">テスト ランナーを使用してテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="08d49-190">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="08d49-191">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="08d49-191">.NET Core 2.0</span></span>](#tab/netcore20)

| <span data-ttu-id="08d49-192">コマンド</span><span class="sxs-lookup"><span data-stu-id="08d49-192">Command</span></span>                             | <span data-ttu-id="08d49-193">関数</span><span class="sxs-lookup"><span data-stu-id="08d49-193">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="08d49-194">dotnet build</span><span class="sxs-lookup"><span data-stu-id="08d49-194">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="08d49-195">.NET Core アプリケーションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="08d49-195">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="08d49-196">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="08d49-196">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="08d49-197">クリーン ビルド出力です。</span><span class="sxs-lookup"><span data-stu-id="08d49-197">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="08d49-198">dotnet help</span><span class="sxs-lookup"><span data-stu-id="08d49-198">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="08d49-199">コマンドのより詳細なドキュメントをオンラインで表示します。</span><span class="sxs-lookup"><span data-stu-id="08d49-199">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="08d49-200">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="08d49-200">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="08d49-201">有効な Preview 2 プロジェクトを .NET Core SDK 1.0 プロジェクトに移行します。</span><span class="sxs-lookup"><span data-stu-id="08d49-201">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="08d49-202">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="08d49-202">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="08d49-203">MSBuild コマンド ラインへのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="08d49-203">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="08d49-204">dotnet new</span><span class="sxs-lookup"><span data-stu-id="08d49-204">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="08d49-205">指定されたテンプレートの C# または F# プロジェクトを初期化します。</span><span class="sxs-lookup"><span data-stu-id="08d49-205">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="08d49-206">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="08d49-206">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="08d49-207">コードの NuGet パッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="08d49-207">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="08d49-208">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="08d49-208">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="08d49-209">.NET Framework に依存するアプリケーションまたは自己完結型アプリケーションを発行します。</span><span class="sxs-lookup"><span data-stu-id="08d49-209">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="08d49-210">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="08d49-210">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="08d49-211">指定されたアプリケーションの依存関係を復元します。</span><span class="sxs-lookup"><span data-stu-id="08d49-211">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="08d49-212">dotnet run</span><span class="sxs-lookup"><span data-stu-id="08d49-212">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="08d49-213">ソースからアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="08d49-213">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="08d49-214">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="08d49-214">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="08d49-215">ソリューション ファイルのプロジェクトを追加、削除、一覧表示するオプション。</span><span class="sxs-lookup"><span data-stu-id="08d49-215">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="08d49-216">dotnet store</span><span class="sxs-lookup"><span data-stu-id="08d49-216">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="08d49-217">ランタイム パッケージ ストアにアセンブリを格納します。</span><span class="sxs-lookup"><span data-stu-id="08d49-217">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="08d49-218">dotnet test</span><span class="sxs-lookup"><span data-stu-id="08d49-218">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="08d49-219">テスト ランナーを使用してテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="08d49-219">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="08d49-220">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="08d49-220">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="08d49-221">コマンド</span><span class="sxs-lookup"><span data-stu-id="08d49-221">Command</span></span>                             | <span data-ttu-id="08d49-222">関数</span><span class="sxs-lookup"><span data-stu-id="08d49-222">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="08d49-223">dotnet build</span><span class="sxs-lookup"><span data-stu-id="08d49-223">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="08d49-224">.NET Core アプリケーションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="08d49-224">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="08d49-225">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="08d49-225">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="08d49-226">クリーン ビルド出力です。</span><span class="sxs-lookup"><span data-stu-id="08d49-226">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="08d49-227">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="08d49-227">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="08d49-228">有効な Preview 2 プロジェクトを .NET Core SDK 1.0 プロジェクトに移行します。</span><span class="sxs-lookup"><span data-stu-id="08d49-228">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="08d49-229">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="08d49-229">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="08d49-230">MSBuild コマンド ラインへのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="08d49-230">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="08d49-231">dotnet new</span><span class="sxs-lookup"><span data-stu-id="08d49-231">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="08d49-232">指定されたテンプレートの C# または F# プロジェクトを初期化します。</span><span class="sxs-lookup"><span data-stu-id="08d49-232">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="08d49-233">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="08d49-233">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="08d49-234">コードの NuGet パッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="08d49-234">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="08d49-235">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="08d49-235">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="08d49-236">.NET Framework に依存するアプリケーションまたは自己完結型アプリケーションを発行します。</span><span class="sxs-lookup"><span data-stu-id="08d49-236">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="08d49-237">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="08d49-237">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="08d49-238">指定されたアプリケーションの依存関係を復元します。</span><span class="sxs-lookup"><span data-stu-id="08d49-238">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="08d49-239">dotnet run</span><span class="sxs-lookup"><span data-stu-id="08d49-239">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="08d49-240">ソースからアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="08d49-240">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="08d49-241">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="08d49-241">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="08d49-242">ソリューション ファイルのプロジェクトを追加、削除、一覧表示するオプション。</span><span class="sxs-lookup"><span data-stu-id="08d49-242">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="08d49-243">dotnet test</span><span class="sxs-lookup"><span data-stu-id="08d49-243">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="08d49-244">テスト ランナーを使用してテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="08d49-244">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="08d49-245">プロジェクト参照</span><span class="sxs-lookup"><span data-stu-id="08d49-245">Project references</span></span>

<span data-ttu-id="08d49-246">コマンド</span><span class="sxs-lookup"><span data-stu-id="08d49-246">Command</span></span> | <span data-ttu-id="08d49-247">関数</span><span class="sxs-lookup"><span data-stu-id="08d49-247">Function</span></span>
--- | ---
[<span data-ttu-id="08d49-248">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="08d49-248">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="08d49-249">プロジェクト参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="08d49-249">Adds a project reference.</span></span>
[<span data-ttu-id="08d49-250">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="08d49-250">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="08d49-251">プロジェクト参照をリストします。</span><span class="sxs-lookup"><span data-stu-id="08d49-251">Lists project references.</span></span>
[<span data-ttu-id="08d49-252">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="08d49-252">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="08d49-253">プロジェクト参照を削除します。</span><span class="sxs-lookup"><span data-stu-id="08d49-253">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="08d49-254">NuGet パッケージ</span><span class="sxs-lookup"><span data-stu-id="08d49-254">NuGet packages</span></span>

<span data-ttu-id="08d49-255">コマンド</span><span class="sxs-lookup"><span data-stu-id="08d49-255">Command</span></span> | <span data-ttu-id="08d49-256">関数</span><span class="sxs-lookup"><span data-stu-id="08d49-256">Function</span></span>
--- | ---
[<span data-ttu-id="08d49-257">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="08d49-257">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="08d49-258">NuGet パッケージを追加します。</span><span class="sxs-lookup"><span data-stu-id="08d49-258">Adds a NuGet package.</span></span>
[<span data-ttu-id="08d49-259">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="08d49-259">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="08d49-260">NuGet パッケージを削除します。</span><span class="sxs-lookup"><span data-stu-id="08d49-260">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="08d49-261">NuGet コマンド</span><span class="sxs-lookup"><span data-stu-id="08d49-261">NuGet commands</span></span>

<span data-ttu-id="08d49-262">コマンド</span><span class="sxs-lookup"><span data-stu-id="08d49-262">Command</span></span> | <span data-ttu-id="08d49-263">関数</span><span class="sxs-lookup"><span data-stu-id="08d49-263">Function</span></span>
--- | ---
[<span data-ttu-id="08d49-264">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="08d49-264">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="08d49-265">サーバーからパッケージを削除または一覧から削除します。</span><span class="sxs-lookup"><span data-stu-id="08d49-265">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="08d49-266">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="08d49-266">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="08d49-267">HTTP 要求キャッシュ、一時的なキャッシュ、コンピューター全体のグローバル パッケージ フォルダーなどのローカルの NuGet リソースをクリアまたは一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="08d49-267">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="08d49-268">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="08d49-268">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="08d49-269">パッケージをサーバーにプッシュして発行します。</span><span class="sxs-lookup"><span data-stu-id="08d49-269">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tools-commands"></a><span data-ttu-id="08d49-270">グローバル ツール コマンド</span><span class="sxs-lookup"><span data-stu-id="08d49-270">Global Tools commands</span></span>

<span data-ttu-id="08d49-271">[.NET Core グローバル ツール](global-tools.md)は .NET Core SDK 2.1.300 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="08d49-271">[.NET Core Global Tools](global-tools.md) are available starting with .NET Core SDK 2.1.300:</span></span>

<span data-ttu-id="08d49-272">コマンド</span><span class="sxs-lookup"><span data-stu-id="08d49-272">Command</span></span> | <span data-ttu-id="08d49-273">関数</span><span class="sxs-lookup"><span data-stu-id="08d49-273">Function</span></span>
--- | ---
[<span data-ttu-id="08d49-274">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="08d49-274">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="08d49-275">グローバル ツールをマシンにインストールします。</span><span class="sxs-lookup"><span data-stu-id="08d49-275">Installs a Global Tool on your machine.</span></span>
[<span data-ttu-id="08d49-276">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="08d49-276">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="08d49-277">マシン上の既定のディレクトリまたは指定したパスに現在インストールされているすべてのグローバル ツールを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="08d49-277">Lists all Global Tools currently installed in the default directory on your machine or in the specified path.</span></span>
[<span data-ttu-id="08d49-278">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="08d49-278">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="08d49-279">グローバル ツールをマシンからアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="08d49-279">Uninstalls a Global Tool from your machine.</span></span>
[<span data-ttu-id="08d49-280">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="08d49-280">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="08d49-281">マシン上のグローバル ツールを更新します。</span><span class="sxs-lookup"><span data-stu-id="08d49-281">Updates a Global Tool on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="08d49-282">その他のツール</span><span class="sxs-lookup"><span data-stu-id="08d49-282">Additional tools</span></span>

<span data-ttu-id="08d49-283">.NET Core SDK 2.1.300 以降では、`DotnetCliToolReference` を使用してプロジェクト単位でのみ入手可能であった複数のツールを .NET Core SDK の一部として入手できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="08d49-283">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="08d49-284">それらのツールを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="08d49-284">These tools include:</span></span>

| <span data-ttu-id="08d49-285">ツール</span><span class="sxs-lookup"><span data-stu-id="08d49-285">Tool</span></span>                                              | <span data-ttu-id="08d49-286">関数</span><span class="sxs-lookup"><span data-stu-id="08d49-286">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="08d49-287">dev-certs</span><span class="sxs-lookup"><span data-stu-id="08d49-287">dev-certs</span></span>                                         | <span data-ttu-id="08d49-288">開発証明書を作成および管理します。</span><span class="sxs-lookup"><span data-stu-id="08d49-288">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="08d49-289">ef</span><span class="sxs-lookup"><span data-stu-id="08d49-289">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="08d49-290">Entity Framework Core コマンドライン ツールです。</span><span class="sxs-lookup"><span data-stu-id="08d49-290">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="08d49-291">sql-cache</span><span class="sxs-lookup"><span data-stu-id="08d49-291">sql-cache</span></span>                                         | <span data-ttu-id="08d49-292">SQL Server キャッシュ コマンドライン ツールです。</span><span class="sxs-lookup"><span data-stu-id="08d49-292">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="08d49-293">user-secrets</span><span class="sxs-lookup"><span data-stu-id="08d49-293">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="08d49-294">開発ユーザーのシークレットを管理します。</span><span class="sxs-lookup"><span data-stu-id="08d49-294">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="08d49-295">watch</span><span class="sxs-lookup"><span data-stu-id="08d49-295">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="08d49-296">ファイルが変化するとコマンドを実行するファイル ウォッチャーを起動します。</span><span class="sxs-lookup"><span data-stu-id="08d49-296">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="08d49-297">各ツールの詳細については、`dotnet <tool-name> --help` を実行してください。</span><span class="sxs-lookup"><span data-stu-id="08d49-297">For more information about each tool, execute `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="08d49-298">使用例</span><span class="sxs-lookup"><span data-stu-id="08d49-298">Examples</span></span>

<span data-ttu-id="08d49-299">新しい .NET Core コンソール アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="08d49-299">Creates a new .NET Core console application:</span></span>

`dotnet new console`

<span data-ttu-id="08d49-300">指定されたアプリケーションの依存関係を復元します。</span><span class="sxs-lookup"><span data-stu-id="08d49-300">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="08d49-301">指定されたディレクトリにプロジェクトとその依存関係をビルドします。</span><span class="sxs-lookup"><span data-stu-id="08d49-301">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="08d49-302">`myapp.dll` という名前のフレームワークに依存するアプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="08d49-302">Run a framework-dependent app named `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="08d49-303">環境変数</span><span class="sxs-lookup"><span data-stu-id="08d49-303">Environment variables</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="08d49-304">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="08d49-304">.NET Core 2.1</span></span>](#tab/netcore21)

`DOTNET_PACKAGES`

<span data-ttu-id="08d49-305">プライマリ パッケージのキャッシュです。</span><span class="sxs-lookup"><span data-stu-id="08d49-305">The primary package cache.</span></span> <span data-ttu-id="08d49-306">設定されていない場合は、既定で `$HOME/.nuget/packages` (Unix の場合) または `%HOME%\NuGet\Packages` (Windows の場合) になります。</span><span class="sxs-lookup"><span data-stu-id="08d49-306">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="08d49-307">ランタイムの読み込み時に共有ホストで使用するサービス インデックスの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="08d49-307">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="08d49-308">.NET Core ツールの使用に関するデータを収集し、Microsoft に送信するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="08d49-308">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="08d49-309">`true` に設定するとテレメトリ機能が無効になります (指定できる値は `true`、`1`、または `yes` です)。</span><span class="sxs-lookup"><span data-stu-id="08d49-309">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="08d49-310">それ以外の場合は `false` に設定します。この場合、テレメトリ機能が有効になります (指定できる値は `false`、`0`、または `no` です)。</span><span class="sxs-lookup"><span data-stu-id="08d49-310">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="08d49-311">設定されていない場合、既定で `false` になり、テレメトリ機能はアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="08d49-311">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="08d49-312">.NET Core ランタイム、共有フレームワーク、または SDK がグローバルな場所から解決されるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="08d49-312">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="08d49-313">設定されていない場合は、既定で `true` になります。</span><span class="sxs-lookup"><span data-stu-id="08d49-313">If not set, it defaults to `true`.</span></span> <span data-ttu-id="08d49-314">`false` に設定すると、グローバルな場所から解決されず、.NET Core インストールが分離されます (値 `0` または `false` が受け入れられます)。</span><span class="sxs-lookup"><span data-stu-id="08d49-314">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="08d49-315">複数レベルのルックアップの詳細については、「[Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md)」 (複数レベルの SharedFX ルックアップ) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08d49-315">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

<span data-ttu-id="08d49-316">マイナー バージョンのロールフォワードを無効にします。</span><span class="sxs-lookup"><span data-stu-id="08d49-316">Disables minor version roll forward.</span></span> <span data-ttu-id="08d49-317">詳細については、「[Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward)」(ロールフォワード) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08d49-317">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="08d49-318">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="08d49-318">.NET Core 2.0</span></span>](#tab/netcore20)

`DOTNET_PACKAGES`

<span data-ttu-id="08d49-319">プライマリ パッケージのキャッシュです。</span><span class="sxs-lookup"><span data-stu-id="08d49-319">The primary package cache.</span></span> <span data-ttu-id="08d49-320">設定されていない場合は、既定で `$HOME/.nuget/packages` (Unix の場合) または `%HOME%\NuGet\Packages` (Windows の場合) になります。</span><span class="sxs-lookup"><span data-stu-id="08d49-320">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="08d49-321">ランタイムの読み込み時に共有ホストで使用するサービス インデックスの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="08d49-321">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="08d49-322">.NET Core ツールの使用に関するデータを収集し、Microsoft に送信するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="08d49-322">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="08d49-323">`true` に設定するとテレメトリ機能が無効になります (指定できる値は `true`、`1`、または `yes` です)。</span><span class="sxs-lookup"><span data-stu-id="08d49-323">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="08d49-324">それ以外の場合は `false` に設定します。この場合、テレメトリ機能が有効になります (指定できる値は `false`、`0`、または `no` です)。</span><span class="sxs-lookup"><span data-stu-id="08d49-324">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="08d49-325">設定されていない場合、既定で `false` になり、テレメトリ機能はアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="08d49-325">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="08d49-326">.NET Core ランタイム、共有フレームワーク、または SDK がグローバルな場所から解決されるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="08d49-326">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="08d49-327">設定されていない場合は、既定で `true` になります。</span><span class="sxs-lookup"><span data-stu-id="08d49-327">If not set, it defaults to `true`.</span></span> <span data-ttu-id="08d49-328">`false` に設定すると、グローバルな場所から解決されず、.NET Core インストールが分離されます (値 `0` または `false` が受け入れられます)。</span><span class="sxs-lookup"><span data-stu-id="08d49-328">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="08d49-329">複数レベルのルックアップの詳細については、「[Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md)」 (複数レベルの SharedFX ルックアップ) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08d49-329">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="08d49-330">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="08d49-330">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="08d49-331">プライマリ パッケージのキャッシュです。</span><span class="sxs-lookup"><span data-stu-id="08d49-331">The primary package cache.</span></span> <span data-ttu-id="08d49-332">設定されていない場合は、既定で `$HOME/.nuget/packages` (Unix の場合) または `%HOME%\NuGet\Packages` (Windows の場合) になります。</span><span class="sxs-lookup"><span data-stu-id="08d49-332">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="08d49-333">ランタイムの読み込み時に共有ホストで使用するサービス インデックスの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="08d49-333">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="08d49-334">.NET Core ツールの使用に関するデータを収集し、Microsoft に送信するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="08d49-334">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="08d49-335">`true` に設定するとテレメトリ機能が無効になります (指定できる値は `true`、`1`、または `yes` です)。</span><span class="sxs-lookup"><span data-stu-id="08d49-335">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="08d49-336">それ以外の場合は `false` に設定します。この場合、テレメトリ機能が有効になります (指定できる値は `false`、`0`、または `no` です)。</span><span class="sxs-lookup"><span data-stu-id="08d49-336">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="08d49-337">設定されていない場合、既定で `false` になり、テレメトリ機能はアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="08d49-337">If not set, the default is `false` and the telemetry feature is active.</span></span>

---
