---
title: "dotnet-vstest コマンド"
description: "dotnet-vstest コマンドは、プロジェクトとそのすべての依存関係をビルドします。"
keywords: "dotnet-vstest, CLI, CLI コマンド, .NET Core"
author: guardrex
ms.author: mairaw
ms.date: 03/09/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 0e36c070-2242-41d3-96f1-aea0aca48d4d
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 740e0e002b8fde1c5bfd1eb8e53be54b4113c74d
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-vstest"></a><span data-ttu-id="4d1fe-104">dotnet-vstest</span><span class="sxs-lookup"><span data-stu-id="4d1fe-104">dotnet-vstest</span></span>

## <a name="name"></a><span data-ttu-id="4d1fe-105">名前</span><span class="sxs-lookup"><span data-stu-id="4d1fe-105">Name</span></span>

<span data-ttu-id="4d1fe-106">`dotnet-vstest` - 指定されたファイルからテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="4d1fe-106">`dotnet-vstest` - Runs tests from the specified files.</span></span>

## <a name="synopsis"></a><span data-ttu-id="4d1fe-107">構文</span><span class="sxs-lookup"><span data-stu-id="4d1fe-107">Synopsis</span></span>

`dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]`

## <a name="description"></a><span data-ttu-id="4d1fe-108">説明</span><span class="sxs-lookup"><span data-stu-id="4d1fe-108">Description</span></span>

<span data-ttu-id="4d1fe-109">`dotnet-vstest` コマンドでは、`VSTest.Console` コマンド ライン アプリケーションを実行し、自動化された単体とコード化された UI アプリケーション テストを実行します。</span><span class="sxs-lookup"><span data-stu-id="4d1fe-109">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit and coded UI application tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="4d1fe-110">引数</span><span class="sxs-lookup"><span data-stu-id="4d1fe-110">Arguments</span></span>

`TEST_FILE_NAMES`

<span data-ttu-id="4d1fe-111">指定されたアセンブリからテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="4d1fe-111">Run tests from the specified assemblies.</span></span> <span data-ttu-id="4d1fe-112">複数のテスト アセンブリ名を指定するときは、空白で区切ります。</span><span class="sxs-lookup"><span data-stu-id="4d1fe-112">Separate multiple test assembly names with spaces.</span></span>

## <a name="options"></a><span data-ttu-id="4d1fe-113">オプション</span><span class="sxs-lookup"><span data-stu-id="4d1fe-113">Options</span></span>

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="4d1fe-114">テストの実行時に使用される設定です。</span><span class="sxs-lookup"><span data-stu-id="4d1fe-114">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="4d1fe-115">指定した値に一致する名前のテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="4d1fe-115">Run tests with names that match the provided values.</span></span> <span data-ttu-id="4d1fe-116">複数の値を指定するときは、コンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="4d1fe-116">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="4d1fe-117">テストの実行では、指定されたパス (存在する場合) からカスタム テスト アダプターを使用します。</span><span class="sxs-lookup"><span data-stu-id="4d1fe-117">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="4d1fe-118">テストの実行に使用する対象のプラットフォーム アーキテクチャです。</span><span class="sxs-lookup"><span data-stu-id="4d1fe-118">Target platform architecture used for test execution.</span></span> <span data-ttu-id="4d1fe-119">有効な値は `x86`、`x64`、`ARM` です。</span><span class="sxs-lookup"><span data-stu-id="4d1fe-119">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="4d1fe-120">テストの実行に使用する対象の .NET Framework バージョンです。</span><span class="sxs-lookup"><span data-stu-id="4d1fe-120">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="4d1fe-121">有効な値の例としては、`.NETFramework,Version=v4.6`、`.NETCoreApp,Version=v1.0` などがあります。サポートされるその他の値は、`Framework35`、`Framework40`、`Framework45`、および `FrameworkCore10` です。</span><span class="sxs-lookup"><span data-stu-id="4d1fe-121">Examples of valid values are `.NETFramework,Version=v4.6`, `.NETCoreApp,Version=v1.0`, etc. Other supported values are `Framework35`, `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="4d1fe-122">テストを並列で実行します。</span><span class="sxs-lookup"><span data-stu-id="4d1fe-122">Execute tests in parallel.</span></span> <span data-ttu-id="4d1fe-123">既定では、コンピューター上のすべての使用可能なコアを使用できます。</span><span class="sxs-lookup"><span data-stu-id="4d1fe-123">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="4d1fe-124">設定ファイルを使用して、明示的なコア数を設定します。</span><span class="sxs-lookup"><span data-stu-id="4d1fe-124">Set an explicit number of cores with a settings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="4d1fe-125">指定した式に一致するテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="4d1fe-125">Run tests that match the given expression.</span></span> <span data-ttu-id="4d1fe-126">`<Expression>` の形式は `<property>Operator<value>[|&<Expression>]` です。この場合の演算子は `=`、`!=`、または `~` のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="4d1fe-126">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span>  <span data-ttu-id="4d1fe-127">演算子 `~` は 'contains' セマンティクスを持ち、`DisplayName` などの文字列プロパティに適用できます。</span><span class="sxs-lookup"><span data-stu-id="4d1fe-127">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="4d1fe-128">かっこ `()` はサブ式をグループ化するために使用します。</span><span class="sxs-lookup"><span data-stu-id="4d1fe-128">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="4d1fe-129">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="4d1fe-129">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="4d1fe-130">テスト結果のロガーを指定します。</span><span class="sxs-lookup"><span data-stu-id="4d1fe-130">Specify a logger for test results.</span></span>  

* <span data-ttu-id="4d1fe-131">Team Foundation Server にテスト結果を発行するには、次のように `TfsPublisher` ロガー プロバイダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="4d1fe-131">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="4d1fe-132">Visual Studio テスト結果ファイル (TRX) に結果のログを書き込むには、`trx` ロガー プロバイダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="4d1fe-132">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="4d1fe-133">このように切り替えることで、テスト結果ディレクトリに指定のログ ファイル名でファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="4d1fe-133">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="4d1fe-134">`LogFileName` が指定されていない場合は、テスト結果を保持するために一意のファイル名が作成されます。</span><span class="sxs-lookup"><span data-stu-id="4d1fe-134">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="4d1fe-135">指定されたテスト コンテナーから探索されたテストを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="4d1fe-135">Lists discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="4d1fe-136">現在のプロセスを起動する親プロセスのプロセス ID です。</span><span class="sxs-lookup"><span data-stu-id="4d1fe-136">Process Id of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="4d1fe-137">ソケット接続およびイベント メッセージの受信用のポートを指定します。</span><span class="sxs-lookup"><span data-stu-id="4d1fe-137">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="4d1fe-138">テスト プラットフォームの詳細ログを有効にします。</span><span class="sxs-lookup"><span data-stu-id="4d1fe-138">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="4d1fe-139">指定されたファイルにログが書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="4d1fe-139">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="4d1fe-140">アダプターに渡す追加の引数を指定します。</span><span class="sxs-lookup"><span data-stu-id="4d1fe-140">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="4d1fe-141">引数は `<n>=<v>` 形式の名前と値のペアとして指定されます。この場合の `<n>` は引数名、`<v>` は引数値です。</span><span class="sxs-lookup"><span data-stu-id="4d1fe-141">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="4d1fe-142">複数の引数を指定する場合は、空白で区切ります。</span><span class="sxs-lookup"><span data-stu-id="4d1fe-142">Use a space to separate multiple arguments.</span></span>

## <a name="examples"></a><span data-ttu-id="4d1fe-143">例</span><span class="sxs-lookup"><span data-stu-id="4d1fe-143">Examples</span></span>

<span data-ttu-id="4d1fe-144">`mytestproject.dll` でテストを実行する:</span><span class="sxs-lookup"><span data-stu-id="4d1fe-144">Run tests in `mytestproject.dll`:</span></span>

`dotnet vstest mytestproject.dll`

<span data-ttu-id="4d1fe-145">`mytestproject.dll` と `myothertestproject.exe` でテストを実行する:</span><span class="sxs-lookup"><span data-stu-id="4d1fe-145">Run tests in `mytestproject.dll` and `myothertestproject.exe`:</span></span>

`dotnet vstest mytestproject.dll myothertestproject.exe`

<span data-ttu-id="4d1fe-146">`TestMethod1` テストを実行する:</span><span class="sxs-lookup"><span data-stu-id="4d1fe-146">Run `TestMethod1` tests:</span></span>

`dotnet vstest /Tests:TestMethod1`

<span data-ttu-id="4d1fe-147">`TestMethod1` および `TestMethod2` テストを実行する:</span><span class="sxs-lookup"><span data-stu-id="4d1fe-147">Run `TestMethod1` and `TestMethod2` tests:</span></span>

`dotnet vstest /Tests:TestMethod1,TestMethod2`

