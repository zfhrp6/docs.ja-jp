---
title: dotnet vstest コマンド - .NET Core CLI
description: dotnet vstest コマンドは、プロジェクトとそのすべての依存関係をビルドします。
author: guardrex
ms.author: mairaw
ms.date: 08/14/2017
ms.openlocfilehash: 981b56aa46afd5ca313ee0be0ca10843ef70e939
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="dotnet-vstest"></a><span data-ttu-id="91937-103">dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="91937-103">dotnet vstest</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="91937-104">name</span><span class="sxs-lookup"><span data-stu-id="91937-104">Name</span></span>

<span data-ttu-id="91937-105">`dotnet-vstest` - 指定されたファイルからテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="91937-105">`dotnet-vstest` - Runs tests from the specified files.</span></span>

## <a name="synopsis"></a><span data-ttu-id="91937-106">構文</span><span class="sxs-lookup"><span data-stu-id="91937-106">Synopsis</span></span>

`dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]`

## <a name="description"></a><span data-ttu-id="91937-107">説明</span><span class="sxs-lookup"><span data-stu-id="91937-107">Description</span></span>

<span data-ttu-id="91937-108">`dotnet-vstest` コマンドでは、`VSTest.Console` コマンド ライン アプリケーションを実行し、自動化された単体とコード化された UI アプリケーション テストを実行します。</span><span class="sxs-lookup"><span data-stu-id="91937-108">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit and coded UI application tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="91937-109">引数</span><span class="sxs-lookup"><span data-stu-id="91937-109">Arguments</span></span>

`TEST_FILE_NAMES`

<span data-ttu-id="91937-110">指定されたアセンブリからテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="91937-110">Run tests from the specified assemblies.</span></span> <span data-ttu-id="91937-111">複数のテスト アセンブリ名を指定するときは、空白で区切ります。</span><span class="sxs-lookup"><span data-stu-id="91937-111">Separate multiple test assembly names with spaces.</span></span>

## <a name="options"></a><span data-ttu-id="91937-112">オプション</span><span class="sxs-lookup"><span data-stu-id="91937-112">Options</span></span>

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="91937-113">テストの実行時に使用される設定です。</span><span class="sxs-lookup"><span data-stu-id="91937-113">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="91937-114">指定した値に一致する名前のテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="91937-114">Run tests with names that match the provided values.</span></span> <span data-ttu-id="91937-115">複数の値を指定するときは、コンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="91937-115">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="91937-116">テストの実行では、指定されたパス (存在する場合) からカスタム テスト アダプターを使用します。</span><span class="sxs-lookup"><span data-stu-id="91937-116">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="91937-117">テストの実行に使用する対象のプラットフォーム アーキテクチャです。</span><span class="sxs-lookup"><span data-stu-id="91937-117">Target platform architecture used for test execution.</span></span> <span data-ttu-id="91937-118">有効な値は `x86`、`x64`、`ARM` です。</span><span class="sxs-lookup"><span data-stu-id="91937-118">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="91937-119">テストの実行に使用する対象の .NET Framework バージョンです。</span><span class="sxs-lookup"><span data-stu-id="91937-119">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="91937-120">有効な値の例としては、`.NETFramework,Version=v4.6`、`.NETCoreApp,Version=v1.0` などがあります。サポートされるその他の値は、`Framework35`、`Framework40`、`Framework45`、および `FrameworkCore10` です。</span><span class="sxs-lookup"><span data-stu-id="91937-120">Examples of valid values are `.NETFramework,Version=v4.6`, `.NETCoreApp,Version=v1.0`, etc. Other supported values are `Framework35`, `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="91937-121">テストを並列で実行します。</span><span class="sxs-lookup"><span data-stu-id="91937-121">Execute tests in parallel.</span></span> <span data-ttu-id="91937-122">既定では、コンピューター上のすべての使用可能なコアを使用できます。</span><span class="sxs-lookup"><span data-stu-id="91937-122">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="91937-123">設定ファイルを使用して、明示的なコア数を設定します。</span><span class="sxs-lookup"><span data-stu-id="91937-123">Set an explicit number of cores with a settings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="91937-124">指定した式に一致するテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="91937-124">Run tests that match the given expression.</span></span> <span data-ttu-id="91937-125">`<Expression>` の形式は `<property>Operator<value>[|&<Expression>]` です。この場合の演算子は `=`、`!=`、または `~` のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="91937-125">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span>  <span data-ttu-id="91937-126">演算子 `~` は 'contains' セマンティクスを持ち、`DisplayName` などの文字列プロパティに適用できます。</span><span class="sxs-lookup"><span data-stu-id="91937-126">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="91937-127">かっこ `()` はサブ式をグループ化するために使用します。</span><span class="sxs-lookup"><span data-stu-id="91937-127">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="91937-128">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="91937-128">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="91937-129">テスト結果のロガーを指定します。</span><span class="sxs-lookup"><span data-stu-id="91937-129">Specify a logger for test results.</span></span>  

* <span data-ttu-id="91937-130">Team Foundation Server にテスト結果を発行するには、次のように `TfsPublisher` ロガー プロバイダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="91937-130">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="91937-131">Visual Studio テスト結果ファイル (TRX) に結果のログを書き込むには、`trx` ロガー プロバイダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="91937-131">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="91937-132">このように切り替えることで、テスト結果ディレクトリに指定のログ ファイル名でファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="91937-132">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="91937-133">`LogFileName` が指定されていない場合は、テスト結果を保持するために一意のファイル名が作成されます。</span><span class="sxs-lookup"><span data-stu-id="91937-133">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="91937-134">指定されたテスト コンテナーから探索されたテストを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="91937-134">Lists discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="91937-135">現在のプロセスを起動する親プロセスのプロセス ID です。</span><span class="sxs-lookup"><span data-stu-id="91937-135">Process Id of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="91937-136">ソケット接続およびイベント メッセージの受信用のポートを指定します。</span><span class="sxs-lookup"><span data-stu-id="91937-136">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="91937-137">テスト プラットフォームの詳細ログを有効にします。</span><span class="sxs-lookup"><span data-stu-id="91937-137">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="91937-138">指定されたファイルにログが書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="91937-138">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="91937-139">アダプターに渡す追加の引数を指定します。</span><span class="sxs-lookup"><span data-stu-id="91937-139">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="91937-140">引数は `<n>=<v>` 形式の名前と値のペアとして指定されます。この場合の `<n>` は引数名、`<v>` は引数値です。</span><span class="sxs-lookup"><span data-stu-id="91937-140">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="91937-141">複数の引数を指定する場合は、空白で区切ります。</span><span class="sxs-lookup"><span data-stu-id="91937-141">Use a space to separate multiple arguments.</span></span>

## <a name="examples"></a><span data-ttu-id="91937-142">使用例</span><span class="sxs-lookup"><span data-stu-id="91937-142">Examples</span></span>

<span data-ttu-id="91937-143">`mytestproject.dll` でテストを実行する:</span><span class="sxs-lookup"><span data-stu-id="91937-143">Run tests in `mytestproject.dll`:</span></span>

`dotnet vstest mytestproject.dll`

<span data-ttu-id="91937-144">`mytestproject.dll` でテストを実行し、カスタム名を持つカスタム フォルダーにエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="91937-144">Run tests in `mytestproject.dll`, exporting to custom folder with custom name:</span></span>

`dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path`

<span data-ttu-id="91937-145">`mytestproject.dll` と `myothertestproject.exe` でテストを実行する:</span><span class="sxs-lookup"><span data-stu-id="91937-145">Run tests in `mytestproject.dll` and `myothertestproject.exe`:</span></span>

`dotnet vstest mytestproject.dll myothertestproject.exe`

<span data-ttu-id="91937-146">`TestMethod1` テストを実行する:</span><span class="sxs-lookup"><span data-stu-id="91937-146">Run `TestMethod1` tests:</span></span>

`dotnet vstest /Tests:TestMethod1`

<span data-ttu-id="91937-147">`TestMethod1` および `TestMethod2` テストを実行する:</span><span class="sxs-lookup"><span data-stu-id="91937-147">Run `TestMethod1` and `TestMethod2` tests:</span></span>

`dotnet vstest /Tests:TestMethod1,TestMethod2`

