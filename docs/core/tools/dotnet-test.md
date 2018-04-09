---
title: dotnet test コマンド - .NET Core CLI
description: dotnet test コマンドは、指定されたプロジェクトで単体テストを実行する場合に使用されます。
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 6102281c4daf149f31e65ef8360831fe9e0ef4f6
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/28/2018
---
# <a name="dotnet-test"></a><span data-ttu-id="09d89-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="09d89-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="09d89-104">name</span><span class="sxs-lookup"><span data-stu-id="09d89-104">Name</span></span>

<span data-ttu-id="09d89-105">`dotnet test` - 単体テストを実行するために使用される .NET テスト ドライバー。</span><span class="sxs-lookup"><span data-stu-id="09d89-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="09d89-106">構文</span><span class="sxs-lookup"><span data-stu-id="09d89-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="09d89-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="09d89-107">.NET Core 2.x</span></span>](#tab/netcore2x)


```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="09d89-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="09d89-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]
dotnet test [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="09d89-109">説明</span><span class="sxs-lookup"><span data-stu-id="09d89-109">Description</span></span>

<span data-ttu-id="09d89-110">`dotnet test` コマンドは、指定されたプロジェクトで単体テストを実行する場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="09d89-110">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="09d89-111">`dotnet test` コマンドは、プロジェクト用に指定されたテスト ランナーのコンソール アプリケーションを起動します。</span><span class="sxs-lookup"><span data-stu-id="09d89-111">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="09d89-112">テスト ランナーでは、単体テスト フレームワーク (MSTest、NUnit、xUnit など) 用に定義されたテストを実行し、各テストの成功または失敗をレポートします。</span><span class="sxs-lookup"><span data-stu-id="09d89-112">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="09d89-113">テスト ランナーと単体テスト ライブラリは、NuGet パッケージとしてパッケージ化され、プロジェクトの通常の依存関係として復元されます。</span><span class="sxs-lookup"><span data-stu-id="09d89-113">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="09d89-114">テスト プロジェクトでは、通常の `<PackageReference>` 要素を使用してテスト ランナーを指定します。次のサンプル プロジェクト ファイルのようになります。</span><span class="sxs-lookup"><span data-stu-id="09d89-114">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="09d89-115">引数</span><span class="sxs-lookup"><span data-stu-id="09d89-115">Arguments</span></span>

`PROJECT`

<span data-ttu-id="09d89-116">テスト プロジェクトへのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="09d89-116">Specifies a path to the test project.</span></span> <span data-ttu-id="09d89-117">省略すると、既定で現在のディレクトリに設定されます。</span><span class="sxs-lookup"><span data-stu-id="09d89-117">If omitted, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="09d89-118">オプション</span><span class="sxs-lookup"><span data-stu-id="09d89-118">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="09d89-119">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="09d89-119">.NET Core 2.x</span></span>](#tab/netcore2x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="09d89-120">テスト実行で指定されたパスからカスタムのテスト アダプターを使用します。</span><span class="sxs-lookup"><span data-stu-id="09d89-120">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="09d89-121">ビルド構成を定義します。</span><span class="sxs-lookup"><span data-stu-id="09d89-121">Defines the build configuration.</span></span> <span data-ttu-id="09d89-122">既定値は `Debug` ですが、プロジェクトの構成がこの既定の SDK 設定に優先する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="09d89-122">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="09d89-123">テストの実行のためのデータ コレクターを有効にします。</span><span class="sxs-lookup"><span data-stu-id="09d89-123">Enables data collector for the test run.</span></span> <span data-ttu-id="09d89-124">詳細については、[「Monitor and analyze test run」](https://aka.ms/vstest-collect) (テストの実行のモニターと分析) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="09d89-124">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="09d89-125">テスト プラットフォームの診断モードを有効にし、指定したファイルに診断メッセージを出力します。</span><span class="sxs-lookup"><span data-stu-id="09d89-125">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="09d89-126">特定の[フレームワーク](../../standard/frameworks.md)のテスト バイナリを検索します。</span><span class="sxs-lookup"><span data-stu-id="09d89-126">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="09d89-127">指定された式を使用して、現在のプロジェクト内のテストを除外します。</span><span class="sxs-lookup"><span data-stu-id="09d89-127">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="09d89-128">詳細については、「[フィルター オプションの詳細](#filter-option-details)」セクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="09d89-128">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="09d89-129">選択的単体テストのフィルター処理の使用方法に関する詳細と例については、「[Running selective unit tests (選択的単体テストの実行)](../testing/selective-unit-tests.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="09d89-129">For additional information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="09d89-130">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="09d89-130">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="09d89-131">テスト結果のロガーを指定します。</span><span class="sxs-lookup"><span data-stu-id="09d89-131">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="09d89-132">実行の前にテスト プロジェクトをビルドしません。</span><span class="sxs-lookup"><span data-stu-id="09d89-132">Does not build the test project prior to running it.</span></span>

`--no-restore`

<span data-ttu-id="09d89-133">コマンドを実行するときに、暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="09d89-133">Doesn't perform an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="09d89-134">実行するバイナリを検索するディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="09d89-134">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="09d89-135">テスト結果が配置されるディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="09d89-135">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="09d89-136">存在しない場合は、指定のディレクトリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="09d89-136">The specified directory will be created if it doesn't exist.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="09d89-137">テストの実行時に使用される設定です。</span><span class="sxs-lookup"><span data-stu-id="09d89-137">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="09d89-138">現在のプロジェクトで検出されたすべてのテストを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="09d89-138">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="09d89-139">コマンドの詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="09d89-139">Sets the verbosity level of the command.</span></span> <span data-ttu-id="09d89-140">指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。</span><span class="sxs-lookup"><span data-stu-id="09d89-140">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="09d89-141">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="09d89-141">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="09d89-142">テスト実行で指定されたパスからカスタムのテスト アダプターを使用します。</span><span class="sxs-lookup"><span data-stu-id="09d89-142">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="09d89-143">ビルド構成を定義します。</span><span class="sxs-lookup"><span data-stu-id="09d89-143">Defines the build configuration.</span></span> <span data-ttu-id="09d89-144">既定値は `Debug` ですが、プロジェクトの構成がこの既定の SDK 設定に優先する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="09d89-144">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="09d89-145">テスト プラットフォームの診断モードを有効にし、指定したファイルに診断メッセージを出力します。</span><span class="sxs-lookup"><span data-stu-id="09d89-145">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="09d89-146">特定の[フレームワーク](../../standard/frameworks.md)のテスト バイナリを検索します。</span><span class="sxs-lookup"><span data-stu-id="09d89-146">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="09d89-147">指定された式を使用して、現在のプロジェクト内のテストを除外します。</span><span class="sxs-lookup"><span data-stu-id="09d89-147">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="09d89-148">詳細については、「[フィルター オプションの詳細](#filter-option-details)」セクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="09d89-148">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="09d89-149">選択的単体テストのフィルター処理の使用方法に関する詳細と例については、「[Running selective unit tests (選択的単体テストの実行)](../testing/selective-unit-tests.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="09d89-149">For additional information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="09d89-150">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="09d89-150">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="09d89-151">テスト結果のロガーを指定します。</span><span class="sxs-lookup"><span data-stu-id="09d89-151">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="09d89-152">実行の前にテスト プロジェクトをビルドしません。</span><span class="sxs-lookup"><span data-stu-id="09d89-152">Does not build the test project prior to running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="09d89-153">実行するバイナリを検索するディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="09d89-153">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="09d89-154">テストの実行時に使用される設定です。</span><span class="sxs-lookup"><span data-stu-id="09d89-154">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="09d89-155">現在のプロジェクトで検出されたすべてのテストを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="09d89-155">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="09d89-156">コマンドの詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="09d89-156">Sets the verbosity level of the command.</span></span> <span data-ttu-id="09d89-157">指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。</span><span class="sxs-lookup"><span data-stu-id="09d89-157">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="09d89-158">使用例</span><span class="sxs-lookup"><span data-stu-id="09d89-158">Examples</span></span>

<span data-ttu-id="09d89-159">現在のディレクトリのプロジェクトでテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="09d89-159">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="09d89-160">`test1` プロジェクトでテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="09d89-160">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

## <a name="filter-option-details"></a><span data-ttu-id="09d89-161">フィルター オプションの詳細</span><span class="sxs-lookup"><span data-stu-id="09d89-161">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="09d89-162">`<Expression>` の形式は `<property><operator><value>[|&<Expression>]` です。</span><span class="sxs-lookup"><span data-stu-id="09d89-162">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="09d89-163">`<property>` は `Test Case` の属性です。</span><span class="sxs-lookup"><span data-stu-id="09d89-163">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="09d89-164">よく利用される単体テスト フレームワークでサポートされるプロパティは以下の通りです。</span><span class="sxs-lookup"><span data-stu-id="09d89-164">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="09d89-165">テスト フレームワーク</span><span class="sxs-lookup"><span data-stu-id="09d89-165">Test Framework</span></span> | <span data-ttu-id="09d89-166">サポートされるプロパティ</span><span class="sxs-lookup"><span data-stu-id="09d89-166">Supported properties</span></span>                                                                                      |
| :------------: | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="09d89-167">MSTest</span><span class="sxs-lookup"><span data-stu-id="09d89-167">MSTest</span></span>         | <ul><li><span data-ttu-id="09d89-168">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="09d89-168">FullyQualifiedName</span></span></li><li><span data-ttu-id="09d89-169">name</span><span class="sxs-lookup"><span data-stu-id="09d89-169">Name</span></span></li><li><span data-ttu-id="09d89-170">ClassName</span><span class="sxs-lookup"><span data-stu-id="09d89-170">ClassName</span></span></li><li><span data-ttu-id="09d89-171">優先度</span><span class="sxs-lookup"><span data-stu-id="09d89-171">Priority</span></span></li><li><span data-ttu-id="09d89-172">TestCategory</span><span class="sxs-lookup"><span data-stu-id="09d89-172">TestCategory</span></span></li></ul> |
| <span data-ttu-id="09d89-173">Xunit</span><span class="sxs-lookup"><span data-stu-id="09d89-173">Xunit</span></span>          | <ul><li><span data-ttu-id="09d89-174">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="09d89-174">FullyQualifiedName</span></span></li><li><span data-ttu-id="09d89-175">DisplayName</span><span class="sxs-lookup"><span data-stu-id="09d89-175">DisplayName</span></span></li><li><span data-ttu-id="09d89-176">Traits</span><span class="sxs-lookup"><span data-stu-id="09d89-176">Traits</span></span></li></ul>                                   |

<span data-ttu-id="09d89-177">`<operator>` は、プロパティと値の関係を示します。</span><span class="sxs-lookup"><span data-stu-id="09d89-177">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="09d89-178">演算子</span><span class="sxs-lookup"><span data-stu-id="09d89-178">Operator</span></span> | <span data-ttu-id="09d89-179">関数</span><span class="sxs-lookup"><span data-stu-id="09d89-179">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="09d89-180">完全一致</span><span class="sxs-lookup"><span data-stu-id="09d89-180">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="09d89-181">完全一致ではない</span><span class="sxs-lookup"><span data-stu-id="09d89-181">Not exact match</span></span> |
| `~`      | <span data-ttu-id="09d89-182">内容</span><span class="sxs-lookup"><span data-stu-id="09d89-182">Contains</span></span>        |

<span data-ttu-id="09d89-183">`<value>` は文字列です。</span><span class="sxs-lookup"><span data-stu-id="09d89-183">`<value>` is a string.</span></span> <span data-ttu-id="09d89-184">すべての参照で大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="09d89-184">All the lookups are case insensitive.</span></span>

<span data-ttu-id="09d89-185">`<operator>` を含まない式は、自動的に `FullyQualifiedName` プロパティの `contains` とみなされます (たとえば、`dotnet test --filter xyz` は `dotnet test --filter FullyQualifiedName~xyz` と同じです)。</span><span class="sxs-lookup"><span data-stu-id="09d89-185">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="09d89-186">式は条件演算子を使用して結合できます。</span><span class="sxs-lookup"><span data-stu-id="09d89-186">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="09d89-187">演算子</span><span class="sxs-lookup"><span data-stu-id="09d89-187">Operator</span></span> | <span data-ttu-id="09d89-188">関数</span><span class="sxs-lookup"><span data-stu-id="09d89-188">Function</span></span> |
| :------: | :------: |
| <code>&#124;</code>      | <span data-ttu-id="09d89-189">OR</span><span class="sxs-lookup"><span data-stu-id="09d89-189">OR</span></span>       |
| `&`      | <span data-ttu-id="09d89-190">AND</span><span class="sxs-lookup"><span data-stu-id="09d89-190">AND</span></span>      |

<span data-ttu-id="09d89-191">条件演算子を使用する場合は、式をかっこで囲みます (例: `(Name~TestMethod1) | (Name~TestMethod2)`)。</span><span class="sxs-lookup"><span data-stu-id="09d89-191">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="09d89-192">選択的単体テストのフィルター処理の使用方法に関する詳細と例については、「[Running selective unit tests (選択的単体テストの実行)](../testing/selective-unit-tests.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="09d89-192">For additional information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="09d89-193">関連項目</span><span class="sxs-lookup"><span data-stu-id="09d89-193">See also</span></span>

 [<span data-ttu-id="09d89-194">フレームワークとターゲット</span><span class="sxs-lookup"><span data-stu-id="09d89-194">Frameworks and Targets</span></span>](../../standard/frameworks.md)  
 [<span data-ttu-id="09d89-195">.NET Core のランタイム識別子 (RID) のカタログ</span><span class="sxs-lookup"><span data-stu-id="09d89-195">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
