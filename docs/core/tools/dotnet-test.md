---
title: "dotnet-test コマンド - .NET Core CLI"
description: "`dotnet test` コマンドは、指定されたプロジェクトで単体テストを実行する場合に使用されます。"
keywords: "dotnet-test, CLI, CLI コマンド, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/25/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 4bf0aef4-148a-41c6-bb95-0a9e1af8762e
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 3308488672df2621c04de40f642c732f81284019
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

#<a name="dotnet-test"></a><span data-ttu-id="b4660-104">dotnet-test</span><span class="sxs-lookup"><span data-stu-id="b4660-104">dotnet-test</span></span>

## <a name="name"></a><span data-ttu-id="b4660-105">名前</span><span class="sxs-lookup"><span data-stu-id="b4660-105">Name</span></span>

<span data-ttu-id="b4660-106">`dotnet-test` - 単体テストを実行するために使用される .NET テスト ドライバー。</span><span class="sxs-lookup"><span data-stu-id="b4660-106">`dotnet-test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b4660-107">構文</span><span class="sxs-lookup"><span data-stu-id="b4660-107">Synopsis</span></span>

`dotnet test [<PROJECT>] [-s|--settings] [-t|--list-tests] [--filter] [-a|--test-adapter-path] [-l|--logger] [-c|--configuration] [-f|--framework] [-o|--output] [-d|--diag] [--no-build] [-v|--verbosity] [-h|--help]`

## <a name="description"></a><span data-ttu-id="b4660-108">説明</span><span class="sxs-lookup"><span data-stu-id="b4660-108">Description</span></span>

<span data-ttu-id="b4660-109">`dotnet test` コマンドは、指定されたプロジェクトで単体テストを実行する場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="b4660-109">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="b4660-110">単体テストは、単体テスト フレームワーク (MSTest、NUnit、xUnit など) および単体テスト フレームワークの dotnet テスト ランナーに対する依存関係があるコンソール アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="b4660-110">Unit tests are console application projects that have dependencies on the unit test framework (for example, MSTest, NUnit, or xUnit) and the dotnet test runner for the unit testing framework.</span></span> <span data-ttu-id="b4660-111">これらは NuGet パッケージとしてパッケージ化され、プロジェクトの通常の依存関係として復元されます。</span><span class="sxs-lookup"><span data-stu-id="b4660-111">These are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="b4660-112">テスト プロジェクトでは、テスト ランナーを指定する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="b4660-112">Test projects also must specify the test runner.</span></span> <span data-ttu-id="b4660-113">これは、通常の `<PackageReference>` 要素を使用して指定されます。次のサンプル プロジェクト ファイルのようになります。</span><span class="sxs-lookup"><span data-stu-id="b4660-113">This is specified using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

<span data-ttu-id="b4660-114">[!code-xml[XUnit 基本テンプレート](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]</span><span class="sxs-lookup"><span data-stu-id="b4660-114">[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]</span></span>

## <a name="options"></a><span data-ttu-id="b4660-115">オプション</span><span class="sxs-lookup"><span data-stu-id="b4660-115">Options</span></span>

`PROJECT`
    
<span data-ttu-id="b4660-116">テスト プロジェクトへのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="b4660-116">Specifies a path to the test project.</span></span> <span data-ttu-id="b4660-117">省略すると、既定で現在のディレクトリに設定されます。</span><span class="sxs-lookup"><span data-stu-id="b4660-117">If omitted, it defaults to current directory.</span></span>

`-h|--help`

<span data-ttu-id="b4660-118">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="b4660-118">Prints out a short help for the command.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="b4660-119">テストの実行時に使用される設定です。</span><span class="sxs-lookup"><span data-stu-id="b4660-119">Settings to use when running tests.</span></span> 

`-t|--list-tests`

<span data-ttu-id="b4660-120">現在のプロジェクトで検出されたすべてのテストを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="b4660-120">List all of the discovered tests in the current project.</span></span> 

`--filter <EXPRESSION>`

<span data-ttu-id="b4660-121">指定された式を使用して、現在のプロジェクト内のテストを除外します。</span><span class="sxs-lookup"><span data-stu-id="b4660-121">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="b4660-122">詳細については、「[フィルター オプションの詳細](#filter-option-details)」セクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b4660-122">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="b4660-123">選択的単体テストのフィルター処理の使用方法に関する詳細と例については、「[Running selective unit tests (選択的単体テストの実行)](../testing/selective-unit-tests.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b4660-123">For additional information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="b4660-124">テスト実行で指定されたパスからカスタムのテスト アダプターを使用します。</span><span class="sxs-lookup"><span data-stu-id="b4660-124">Use the custom test adapters from the specified path in the test run.</span></span> 

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="b4660-125">テスト結果のロガーを指定します。</span><span class="sxs-lookup"><span data-stu-id="b4660-125">Specifies a logger for test results.</span></span> 

`-c|--configuration <CONFIGURATION>`

<span data-ttu-id="b4660-126">ビルドに使用する構成です。</span><span class="sxs-lookup"><span data-stu-id="b4660-126">Configuration under which to build.</span></span> <span data-ttu-id="b4660-127">既定値は `Debug` ですが、プロジェクトの構成がこの既定の SDK 設定に優先する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b4660-127">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="b4660-128">特定の[フレームワーク](../../standard/frameworks.md)のテスト バイナリを検索します。</span><span class="sxs-lookup"><span data-stu-id="b4660-128">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="b4660-129">実行するバイナリを検索するディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="b4660-129">Directory in which to find the binaries to run.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="b4660-130">テスト プラットフォームの診断モードを有効にし、指定したファイルに診断メッセージを出力します。</span><span class="sxs-lookup"><span data-stu-id="b4660-130">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span> 

`--no-build` 

<span data-ttu-id="b4660-131">実行の前にテスト プロジェクトをビルドしません。</span><span class="sxs-lookup"><span data-stu-id="b4660-131">Does not build the test project prior to running it.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="b4660-132">コマンドの詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="b4660-132">Sets the verbosity level of the command.</span></span> <span data-ttu-id="b4660-133">指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。</span><span class="sxs-lookup"><span data-stu-id="b4660-133">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="b4660-134">例</span><span class="sxs-lookup"><span data-stu-id="b4660-134">Examples</span></span>

<span data-ttu-id="b4660-135">現在のディレクトリのプロジェクトでテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="b4660-135">Run the tests in the project in the current directory:</span></span>

`dotnet test` 

<span data-ttu-id="b4660-136">`test1` プロジェクトでテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="b4660-136">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

## <a name="filter-option-details"></a><span data-ttu-id="b4660-137">フィルター オプションの詳細</span><span class="sxs-lookup"><span data-stu-id="b4660-137">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="b4660-138">`<Expression>` の形式は `<property><operator><value>[|&<Expression>]` です。</span><span class="sxs-lookup"><span data-stu-id="b4660-138">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="b4660-139">`<property>` は `Test Case` の属性です。</span><span class="sxs-lookup"><span data-stu-id="b4660-139">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="b4660-140">よく利用される単体テスト フレームワークでサポートされるプロパティは以下の通りです。</span><span class="sxs-lookup"><span data-stu-id="b4660-140">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="b4660-141">テスト フレームワーク</span><span class="sxs-lookup"><span data-stu-id="b4660-141">Test Framework</span></span> | <span data-ttu-id="b4660-142">サポートされるプロパティ</span><span class="sxs-lookup"><span data-stu-id="b4660-142">Supported properties</span></span>                                                                                      |
| :------------: | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="b4660-143">MSTest</span><span class="sxs-lookup"><span data-stu-id="b4660-143">MSTest</span></span>         | <ul><li><span data-ttu-id="b4660-144">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="b4660-144">FullyQualifiedName</span></span></li><li><span data-ttu-id="b4660-145">名前</span><span class="sxs-lookup"><span data-stu-id="b4660-145">Name</span></span></li><li><span data-ttu-id="b4660-146">ClassName</span><span class="sxs-lookup"><span data-stu-id="b4660-146">ClassName</span></span></li><li><span data-ttu-id="b4660-147">優先度</span><span class="sxs-lookup"><span data-stu-id="b4660-147">Priority</span></span></li><li><span data-ttu-id="b4660-148">TestCategory</span><span class="sxs-lookup"><span data-stu-id="b4660-148">TestCategory</span></span></li></ul> |
| <span data-ttu-id="b4660-149">Xunit</span><span class="sxs-lookup"><span data-stu-id="b4660-149">Xunit</span></span>          | <ul><li><span data-ttu-id="b4660-150">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="b4660-150">FullyQualifiedName</span></span></li><li><span data-ttu-id="b4660-151">DisplayName</span><span class="sxs-lookup"><span data-stu-id="b4660-151">DisplayName</span></span></li><li><span data-ttu-id="b4660-152">Traits</span><span class="sxs-lookup"><span data-stu-id="b4660-152">Traits</span></span></li></ul>                                   |

<span data-ttu-id="b4660-153">`<operator>` は、プロパティと値の関係を示します。</span><span class="sxs-lookup"><span data-stu-id="b4660-153">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="b4660-154">演算子</span><span class="sxs-lookup"><span data-stu-id="b4660-154">Operator</span></span> | <span data-ttu-id="b4660-155">関数</span><span class="sxs-lookup"><span data-stu-id="b4660-155">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="b4660-156">完全一致</span><span class="sxs-lookup"><span data-stu-id="b4660-156">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="b4660-157">完全一致ではない</span><span class="sxs-lookup"><span data-stu-id="b4660-157">Not exact match</span></span> |
| `~`      | <span data-ttu-id="b4660-158">内容</span><span class="sxs-lookup"><span data-stu-id="b4660-158">Contains</span></span>        |

<span data-ttu-id="b4660-159">`<value>` は文字列です。</span><span class="sxs-lookup"><span data-stu-id="b4660-159">`<value>` is a string.</span></span> <span data-ttu-id="b4660-160">すべての参照で大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="b4660-160">All the lookups are case insensitive.</span></span>

<span data-ttu-id="b4660-161">`<operator>` を含まない式は、自動的に `FullyQualifiedName` プロパティの `contains` とみなされます (たとえば、`dotnet test --filter xyz` は `dotnet test --filter FullyQualifiedName~xyz` と同じです)。</span><span class="sxs-lookup"><span data-stu-id="b4660-161">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="b4660-162">式は条件演算子を使用して結合できます。</span><span class="sxs-lookup"><span data-stu-id="b4660-162">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="b4660-163">演算子</span><span class="sxs-lookup"><span data-stu-id="b4660-163">Operator</span></span> | <span data-ttu-id="b4660-164">関数</span><span class="sxs-lookup"><span data-stu-id="b4660-164">Function</span></span> |
| :------: | :------: |
| <code>&#124;</code>      | <span data-ttu-id="b4660-165">OR</span><span class="sxs-lookup"><span data-stu-id="b4660-165">OR</span></span>       |
| `&`      | <span data-ttu-id="b4660-166">AND</span><span class="sxs-lookup"><span data-stu-id="b4660-166">AND</span></span>      |

<span data-ttu-id="b4660-167">条件演算子を使用する場合は、式をかっこで囲みます (例: `(Name~TestMethod1) | (Name~TestMethod2)`)。</span><span class="sxs-lookup"><span data-stu-id="b4660-167">You can enclose expressions in paranthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="b4660-168">選択的単体テストのフィルター処理の使用方法に関する詳細と例については、「[Running selective unit tests (選択的単体テストの実行)](../testing/selective-unit-tests.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b4660-168">For additional information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b4660-169">関連項目</span><span class="sxs-lookup"><span data-stu-id="b4660-169">See also</span></span>

<span data-ttu-id="b4660-170">[フレームワークとターゲット](../../standard/frameworks.md) </span><span class="sxs-lookup"><span data-stu-id="b4660-170">[Frameworks and Targets](../../standard/frameworks.md) </span></span>  
[<span data-ttu-id="b4660-171">.NET Core のランタイム識別子 (RID) のカタログ</span><span class="sxs-lookup"><span data-stu-id="b4660-171">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)

