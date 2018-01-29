---
title: "dotnet コマンド - .NET Core CLI"
description: "dotnet コマンド (.NET Core CLI ツールの一般的なドライバー) とその使用法について説明します。"
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 2eea7d13994bfddc89d8f3513308a6620c53c88c
ms.sourcegitcommit: f28752eab00d2bd97e971542c0f49ce63cfbc239
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2018
---
# <a name="dotnet-command"></a><span data-ttu-id="b5060-103">dotnet コマンド</span><span class="sxs-lookup"><span data-stu-id="b5060-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="b5060-104">name</span><span class="sxs-lookup"><span data-stu-id="b5060-104">Name</span></span>

<span data-ttu-id="b5060-105">`dotnet` - コマンドラインのコマンドを実行するための一般的なドライバーです。</span><span class="sxs-lookup"><span data-stu-id="b5060-105">`dotnet` - General driver for running the command-line commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b5060-106">構文</span><span class="sxs-lookup"><span data-stu-id="b5060-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="b5060-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="b5060-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbose] [--version]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="b5060-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="b5060-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [-v|--verbose] [--version]
```
---

## <a name="description"></a><span data-ttu-id="b5060-109">説明</span><span class="sxs-lookup"><span data-stu-id="b5060-109">Description</span></span>

<span data-ttu-id="b5060-110">`dotnet` は、コマンド ライン インターフェイス (CLI) ツールチェーンの一般的なドライバーです。</span><span class="sxs-lookup"><span data-stu-id="b5060-110">`dotnet` is a generic driver for the Command Line Interface (CLI) toolchain.</span></span> <span data-ttu-id="b5060-111">単独で呼び出され、簡単な使用方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="b5060-111">Invoked on its own, it provides brief usage instructions.</span></span>

<span data-ttu-id="b5060-112">特定の機能がそれぞれコマンドとして実装されます。</span><span class="sxs-lookup"><span data-stu-id="b5060-112">Each specific feature is implemented as a command.</span></span> <span data-ttu-id="b5060-113">機能を使用するには、[`dotnet build`](dotnet-build.md) のように、`dotnet` の後にコマンドを指定します。</span><span class="sxs-lookup"><span data-stu-id="b5060-113">In order to use the feature, the command is specified after `dotnet`, such as [`dotnet build`](dotnet-build.md).</span></span> <span data-ttu-id="b5060-114">コマンドに続く引数はすべて独自の引数です。</span><span class="sxs-lookup"><span data-stu-id="b5060-114">All of the arguments following the command are its own arguments.</span></span>

<span data-ttu-id="b5060-115">`dotnet` が単独でコマンドとして使用されるのは、[フレームワークに依存するアプリ](../deploying/index.md)を実行する場合のみです。</span><span class="sxs-lookup"><span data-stu-id="b5060-115">The only time `dotnet` is used as a command on its own is to run [framework-dependent apps](../deploying/index.md).</span></span> <span data-ttu-id="b5060-116">アプリケーションを実行する場合は、`dotnet` の動詞の後にアプリケーション DLL を指定します (`dotnet myapp.dll` など)。</span><span class="sxs-lookup"><span data-stu-id="b5060-116">Specify an application DLL after the `dotnet` verb to execute the application (for example, `dotnet myapp.dll`).</span></span>

## <a name="options"></a><span data-ttu-id="b5060-117">オプション</span><span class="sxs-lookup"><span data-stu-id="b5060-117">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="b5060-118">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="b5060-118">.NET Core 2.x</span></span>](#tab/netcore2x)

`--additional-deps <PATH>`

<span data-ttu-id="b5060-119">追加の *deps.json* ファイルへのパスです。</span><span class="sxs-lookup"><span data-stu-id="b5060-119">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="b5060-120">プローブ ポリシーとプローブするアセンブリを含むパスです。</span><span class="sxs-lookup"><span data-stu-id="b5060-120">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="b5060-121">診断出力を有効にします。</span><span class="sxs-lookup"><span data-stu-id="b5060-121">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="b5060-122">アプリケーションを実行するために使用するインストール済み .NET Core ランタイムのバージョンです。</span><span class="sxs-lookup"><span data-stu-id="b5060-122">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="b5060-123">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="b5060-123">Prints out a short help for the command.</span></span> <span data-ttu-id="b5060-124">`dotnet` で使用すると、使用可能なコマンドのリストも印刷されます。</span><span class="sxs-lookup"><span data-stu-id="b5060-124">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="b5060-125">現在のオペレーティング システム、バージョンのコミット SHA、およびその他の情報など、CLI ツールと環境の詳細情報を印刷します。</span><span class="sxs-lookup"><span data-stu-id="b5060-125">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="b5060-126">共有フレームワークの候補なしでロールフォワードします。</span><span class="sxs-lookup"><span data-stu-id="b5060-126">Rolls forward on no candidate shared framework.</span></span>

`-v|--verbose`

<span data-ttu-id="b5060-127">詳細出力を有効にします。</span><span class="sxs-lookup"><span data-stu-id="b5060-127">Enables verbose output.</span></span>

`--version`

<span data-ttu-id="b5060-128">使用中の .NET Core SDK のバージョンを印刷します。</span><span class="sxs-lookup"><span data-stu-id="b5060-128">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="b5060-129">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="b5060-129">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="b5060-130">プローブ ポリシーとプローブするアセンブリを含むパスです。</span><span class="sxs-lookup"><span data-stu-id="b5060-130">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="b5060-131">診断出力を有効にします。</span><span class="sxs-lookup"><span data-stu-id="b5060-131">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="b5060-132">アプリケーションを実行するために使用するインストール済み .NET Core ランタイムのバージョンです。</span><span class="sxs-lookup"><span data-stu-id="b5060-132">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="b5060-133">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="b5060-133">Prints out a short help for the command.</span></span> <span data-ttu-id="b5060-134">`dotnet` で使用すると、使用可能なコマンドのリストも印刷されます。</span><span class="sxs-lookup"><span data-stu-id="b5060-134">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="b5060-135">現在のオペレーティング システム、バージョンのコミット SHA、およびその他の情報など、CLI ツールと環境の詳細情報を印刷します。</span><span class="sxs-lookup"><span data-stu-id="b5060-135">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`-v|--verbose`

<span data-ttu-id="b5060-136">詳細出力を有効にします。</span><span class="sxs-lookup"><span data-stu-id="b5060-136">Enables verbose output.</span></span>

`--version`

<span data-ttu-id="b5060-137">使用中の .NET Core SDK のバージョンを印刷します。</span><span class="sxs-lookup"><span data-stu-id="b5060-137">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="b5060-138">dotnet コマンド</span><span class="sxs-lookup"><span data-stu-id="b5060-138">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="b5060-139">全般</span><span class="sxs-lookup"><span data-stu-id="b5060-139">General</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="b5060-140">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="b5060-140">.NET Core 2.x</span></span>](#tab/netcore2x)

| <span data-ttu-id="b5060-141">コマンド</span><span class="sxs-lookup"><span data-stu-id="b5060-141">Command</span></span>                             | <span data-ttu-id="b5060-142">関数</span><span class="sxs-lookup"><span data-stu-id="b5060-142">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="b5060-143">dotnet build</span><span class="sxs-lookup"><span data-stu-id="b5060-143">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="b5060-144">.NET Core アプリケーションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="b5060-144">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="b5060-145">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="b5060-145">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="b5060-146">クリーン ビルド出力です。</span><span class="sxs-lookup"><span data-stu-id="b5060-146">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="b5060-147">dotnet help</span><span class="sxs-lookup"><span data-stu-id="b5060-147">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="b5060-148">コマンドのより詳細なドキュメントをオンラインで表示します。</span><span class="sxs-lookup"><span data-stu-id="b5060-148">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="b5060-149">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="b5060-149">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="b5060-150">有効な Preview 2 プロジェクトを .NET Core SDK 1.0 プロジェクトに移行します。</span><span class="sxs-lookup"><span data-stu-id="b5060-150">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="b5060-151">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="b5060-151">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="b5060-152">MSBuild コマンド ラインへのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="b5060-152">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="b5060-153">dotnet new</span><span class="sxs-lookup"><span data-stu-id="b5060-153">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="b5060-154">指定されたテンプレートの C# または F# プロジェクトを初期化します。</span><span class="sxs-lookup"><span data-stu-id="b5060-154">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="b5060-155">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="b5060-155">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="b5060-156">コードの NuGet パッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="b5060-156">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="b5060-157">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="b5060-157">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="b5060-158">.NET Framework に依存するアプリケーションまたは自己完結型アプリケーションを発行します。</span><span class="sxs-lookup"><span data-stu-id="b5060-158">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="b5060-159">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="b5060-159">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="b5060-160">指定されたアプリケーションの依存関係を復元します。</span><span class="sxs-lookup"><span data-stu-id="b5060-160">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="b5060-161">dotnet run</span><span class="sxs-lookup"><span data-stu-id="b5060-161">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="b5060-162">ソースからアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="b5060-162">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="b5060-163">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="b5060-163">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="b5060-164">ソリューション ファイルのプロジェクトを追加、削除、一覧表示するオプション。</span><span class="sxs-lookup"><span data-stu-id="b5060-164">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="b5060-165">dotnet store</span><span class="sxs-lookup"><span data-stu-id="b5060-165">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="b5060-166">ランタイム パッケージ ストアにアセンブリを格納します。</span><span class="sxs-lookup"><span data-stu-id="b5060-166">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="b5060-167">dotnet test</span><span class="sxs-lookup"><span data-stu-id="b5060-167">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="b5060-168">テスト ランナーを使用してテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="b5060-168">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="b5060-169">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="b5060-169">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="b5060-170">コマンド</span><span class="sxs-lookup"><span data-stu-id="b5060-170">Command</span></span>                             | <span data-ttu-id="b5060-171">関数</span><span class="sxs-lookup"><span data-stu-id="b5060-171">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="b5060-172">dotnet build</span><span class="sxs-lookup"><span data-stu-id="b5060-172">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="b5060-173">.NET Core アプリケーションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="b5060-173">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="b5060-174">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="b5060-174">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="b5060-175">クリーン ビルド出力です。</span><span class="sxs-lookup"><span data-stu-id="b5060-175">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="b5060-176">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="b5060-176">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="b5060-177">有効な Preview 2 プロジェクトを .NET Core SDK 1.0 プロジェクトに移行します。</span><span class="sxs-lookup"><span data-stu-id="b5060-177">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="b5060-178">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="b5060-178">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="b5060-179">MSBuild コマンド ラインへのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="b5060-179">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="b5060-180">dotnet new</span><span class="sxs-lookup"><span data-stu-id="b5060-180">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="b5060-181">指定されたテンプレートの C# または F# プロジェクトを初期化します。</span><span class="sxs-lookup"><span data-stu-id="b5060-181">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="b5060-182">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="b5060-182">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="b5060-183">コードの NuGet パッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="b5060-183">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="b5060-184">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="b5060-184">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="b5060-185">.NET Framework に依存するアプリケーションまたは自己完結型アプリケーションを発行します。</span><span class="sxs-lookup"><span data-stu-id="b5060-185">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="b5060-186">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="b5060-186">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="b5060-187">指定されたアプリケーションの依存関係を復元します。</span><span class="sxs-lookup"><span data-stu-id="b5060-187">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="b5060-188">dotnet run</span><span class="sxs-lookup"><span data-stu-id="b5060-188">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="b5060-189">ソースからアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="b5060-189">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="b5060-190">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="b5060-190">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="b5060-191">ソリューション ファイルのプロジェクトを追加、削除、一覧表示するオプション。</span><span class="sxs-lookup"><span data-stu-id="b5060-191">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="b5060-192">dotnet test</span><span class="sxs-lookup"><span data-stu-id="b5060-192">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="b5060-193">テスト ランナーを使用してテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="b5060-193">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="b5060-194">プロジェクト参照</span><span class="sxs-lookup"><span data-stu-id="b5060-194">Project references</span></span>

<span data-ttu-id="b5060-195">コマンド</span><span class="sxs-lookup"><span data-stu-id="b5060-195">Command</span></span> | <span data-ttu-id="b5060-196">関数</span><span class="sxs-lookup"><span data-stu-id="b5060-196">Function</span></span>
--- | ---
[<span data-ttu-id="b5060-197">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="b5060-197">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="b5060-198">プロジェクト参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="b5060-198">Add a project reference.</span></span>
[<span data-ttu-id="b5060-199">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="b5060-199">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="b5060-200">プロジェクト参照をリストします。</span><span class="sxs-lookup"><span data-stu-id="b5060-200">List project references.</span></span>
[<span data-ttu-id="b5060-201">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="b5060-201">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="b5060-202">プロジェクト参照を削除します。</span><span class="sxs-lookup"><span data-stu-id="b5060-202">Remove a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="b5060-203">NuGet パッケージ</span><span class="sxs-lookup"><span data-stu-id="b5060-203">NuGet packages</span></span>

<span data-ttu-id="b5060-204">コマンド</span><span class="sxs-lookup"><span data-stu-id="b5060-204">Command</span></span> | <span data-ttu-id="b5060-205">関数</span><span class="sxs-lookup"><span data-stu-id="b5060-205">Function</span></span>
--- | ---
[<span data-ttu-id="b5060-206">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="b5060-206">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="b5060-207">NuGet パッケージを追加します。</span><span class="sxs-lookup"><span data-stu-id="b5060-207">Add a NuGet package.</span></span>
[<span data-ttu-id="b5060-208">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="b5060-208">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="b5060-209">NuGet パッケージを削除します。</span><span class="sxs-lookup"><span data-stu-id="b5060-209">Remove a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="b5060-210">NuGet コマンド</span><span class="sxs-lookup"><span data-stu-id="b5060-210">NuGet commands</span></span>

<span data-ttu-id="b5060-211">コマンド</span><span class="sxs-lookup"><span data-stu-id="b5060-211">Command</span></span> | <span data-ttu-id="b5060-212">関数</span><span class="sxs-lookup"><span data-stu-id="b5060-212">Function</span></span>
--- | ---
[<span data-ttu-id="b5060-213">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="b5060-213">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="b5060-214">サーバーからパッケージを削除または一覧から削除します。</span><span class="sxs-lookup"><span data-stu-id="b5060-214">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="b5060-215">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="b5060-215">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="b5060-216">HTTP 要求キャッシュ、一時的なキャッシュ、コンピューター全体のグローバル パッケージ フォルダーなどのローカルの NuGet リソースをクリアまたは一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="b5060-216">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="b5060-217">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="b5060-217">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="b5060-218">パッケージをサーバーにプッシュして発行します。</span><span class="sxs-lookup"><span data-stu-id="b5060-218">Pushes a package to the server and publishes it.</span></span>

## <a name="examples"></a><span data-ttu-id="b5060-219">使用例</span><span class="sxs-lookup"><span data-stu-id="b5060-219">Examples</span></span>

<span data-ttu-id="b5060-220">コンパイルして実行できるサンプルの .NET Core コンソール アプリケーションを初期化します。</span><span class="sxs-lookup"><span data-stu-id="b5060-220">Initialize a sample .NET Core console application that can be compiled and run:</span></span>

`dotnet new console`

<span data-ttu-id="b5060-221">指定されたアプリケーションの依存関係を復元します。</span><span class="sxs-lookup"><span data-stu-id="b5060-221">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="b5060-222">指定されたディレクトリにプロジェクトとその依存関係をビルドします。</span><span class="sxs-lookup"><span data-stu-id="b5060-222">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="b5060-223">`myapp.dll` という名前のフレームワークに依存するアプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="b5060-223">Run a framework-dependent app named `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="b5060-224">環境変数</span><span class="sxs-lookup"><span data-stu-id="b5060-224">Environment variables</span></span>

`DOTNET_PACKAGES`

<span data-ttu-id="b5060-225">プライマリ パッケージのキャッシュです。</span><span class="sxs-lookup"><span data-stu-id="b5060-225">The primary package cache.</span></span> <span data-ttu-id="b5060-226">設定されていない場合は、既定で `$HOME/.nuget/packages` (Unix の場合) または `%HOME%\NuGet\Packages` (Windows の場合) になります。</span><span class="sxs-lookup"><span data-stu-id="b5060-226">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="b5060-227">ランタイムの読み込み時に共有ホストで使用するサービス インデックスの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="b5060-227">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="b5060-228">.NET Core ツールの使用に関するデータを収集し、Microsoft に送信するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b5060-228">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="b5060-229">`true` に設定するとテレメトリ機能が無効になります (指定できる値は `true`、`1`、または `yes` です)。それ以外の場合は `false` に設定します。この場合、テレメトリ機能が有効になります (指定できる値は `false`、`0`、または `no` です)。</span><span class="sxs-lookup"><span data-stu-id="b5060-229">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted); otherwise, set to `false` to opt-in to the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="b5060-230">設定されていない場合、既定で `false` になり、テレメトリ機能はアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="b5060-230">If not set, the defaults is `false`, and the telemetry feature is active.</span></span>
