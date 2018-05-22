---
title: C# 7.1 の新機能
description: C# 7.1 の新機能の概要。
ms.date: 08/16/2017
ms.openlocfilehash: 00baec45d7582d3ac12c7b0865241f5cd8159246
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="whats-new-in-c-71"></a><span data-ttu-id="b7d6c-103">C# 7.1 の新機能</span><span class="sxs-lookup"><span data-stu-id="b7d6c-103">What's new in C# 7.1</span></span>

<span data-ttu-id="b7d6c-104">C# 7.1 は C# 言語の最初のポイント リリースです。</span><span class="sxs-lookup"><span data-stu-id="b7d6c-104">C# 7.1 is the first point release to the C# language.</span></span> <span data-ttu-id="b7d6c-105">この言語のリリース サイクルが増えたことになります。</span><span class="sxs-lookup"><span data-stu-id="b7d6c-105">It marks an increased release cadence for the language.</span></span> <span data-ttu-id="b7d6c-106">新機能は間もなく使用できます。理論的には、各々の新機能が用意できたときに使用できます。</span><span class="sxs-lookup"><span data-stu-id="b7d6c-106">You can use the new features sooner, ideally when each new feature is ready.</span></span> <span data-ttu-id="b7d6c-107">C# 7.1 では、特定のバージョンの言語に合わせるようにコンパイラを構成する機能が追加されます。</span><span class="sxs-lookup"><span data-stu-id="b7d6c-107">C# 7.1 adds the ability to configure the compiler to match a specified version of the language.</span></span> <span data-ttu-id="b7d6c-108">ツールをアップグレードする決定と言語バージョンをアップグレードする決定を分けることができます。</span><span class="sxs-lookup"><span data-stu-id="b7d6c-108">That enables you to separate the decision to upgrade tools from the decision to upgrade language versions.</span></span>

<span data-ttu-id="b7d6c-109">C# 7.1 では、[言語バージョン選択](#language-version-selection)構成要素、3 つの新しい言語機能、新しいコンパイラ動作が追加されます。</span><span class="sxs-lookup"><span data-stu-id="b7d6c-109">C# 7.1 adds the [language version selection](#language-version-selection) configuration element, three new language features and new compiler behavior.</span></span>

<span data-ttu-id="b7d6c-110">このリリースの新しい言語機能は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b7d6c-110">The new language features in this release are:</span></span>

* [<span data-ttu-id="b7d6c-111">`async` `Main` メソッド</span><span class="sxs-lookup"><span data-stu-id="b7d6c-111">`async` `Main` method</span></span>](#async-main)
  - <span data-ttu-id="b7d6c-112">アプリケーションのエントリ ポイントに `async` 修飾子を設定できます。</span><span class="sxs-lookup"><span data-stu-id="b7d6c-112">The entry point for an application can have the `async` modifier.</span></span>
* [<span data-ttu-id="b7d6c-113">`default` リテラル式</span><span class="sxs-lookup"><span data-stu-id="b7d6c-113">`default` literal expressions</span></span>](#default-literal-expressions)
  - <span data-ttu-id="b7d6c-114">ターゲットの種類を推論できるとき、既定の値式で既定のリテラル式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="b7d6c-114">You can use default literal expressions in default value expressions when the target type can be inferred.</span></span>
* [<span data-ttu-id="b7d6c-115">推論されたタプル要素の名前</span><span class="sxs-lookup"><span data-stu-id="b7d6c-115">Inferred tuple element names</span></span>](#inferred-tuple-element-names)
  - <span data-ttu-id="b7d6c-116">タプル要素の名前は、多くの場合、タプル初期化から推論できます。</span><span class="sxs-lookup"><span data-stu-id="b7d6c-116">The names of tuple elements can be inferred from tuple initialization in many cases.</span></span>

<span data-ttu-id="b7d6c-117">最後に、コンパイラには、[参照アセンブリ生成](#reference-assembly-generation)を制御する 2 つのオプション、`/refout` と `/refonly` があります。</span><span class="sxs-lookup"><span data-stu-id="b7d6c-117">Finally, the compiler has two options `/refout` and `/refonly` that control [reference assembly generation](#reference-assembly-generation).</span></span>

## <a name="language-version-selection"></a><span data-ttu-id="b7d6c-118">言語バージョン選択</span><span class="sxs-lookup"><span data-stu-id="b7d6c-118">Language version selection</span></span>

<span data-ttu-id="b7d6c-119">C# コンパイラは、Visual Studio 2017 バージョン 15.3 または .NET Core SDK 2.0 以降で C# 7.1 をサポートします。</span><span class="sxs-lookup"><span data-stu-id="b7d6c-119">The C# compiler supports C# 7.1 starting with Visual Studio 2017 version 15.3, or the .NET Core SDK 2.0.</span></span> <span data-ttu-id="b7d6c-120">ただし、7.1 機能は既定でオフになっています。</span><span class="sxs-lookup"><span data-stu-id="b7d6c-120">However, the 7.1 features are turned off by default.</span></span> <span data-ttu-id="b7d6c-121">7.1 機能を有効にするには、プロジェクトの言語バージョン設定を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b7d6c-121">To enable the 7.1 features, you need to change the language version setting for your project.</span></span>

<span data-ttu-id="b7d6c-122">Visual Studio で、ソリューション エクスプローラー内でプロジェクトを右クリックし、**[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="b7d6c-122">In Visual Studio, right-click on the project node in Solution Explorer and select **Properties**.</span></span> <span data-ttu-id="b7d6c-123">**[ビルド]** タブを選択し、**[詳細設定]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="b7d6c-123">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="b7d6c-124">ドロップダウンで、下の画像のように、**C# 最新マイナー バージョン (最新)** を選択するか、特定バージョンの **C# 7.1** を選択します。</span><span class="sxs-lookup"><span data-stu-id="b7d6c-124">In the dropdown, select **C# latest minor version (latest)**, or the specific version **C# 7.1** as shown in the image following.</span></span> <span data-ttu-id="b7d6c-125">`latest` という値は、現在のコンピューターに最新のマイナー バージョンを使用することを意味します。</span><span class="sxs-lookup"><span data-stu-id="b7d6c-125">The `latest` value means you want to use the latest minor version on the current machine.</span></span> <span data-ttu-id="b7d6c-126">`C# 7.1` は、最新のマイナー バージョンがリリースされた後でも、C# 7.1 を使用することを意味します。</span><span class="sxs-lookup"><span data-stu-id="b7d6c-126">The `C# 7.1` means that you want to use C# 7.1, even after newer minor versions are released.</span></span>

![言語バージョンの設定](./media/csharp-7-1/advanced-build-settings.png)

<span data-ttu-id="b7d6c-128">あるいは、"csproj" ファイルを編集し、次の行を追加するか、編集できます。</span><span class="sxs-lookup"><span data-stu-id="b7d6c-128">Alternatively, you can edit the "csproj" file and add or modify the following lines:</span></span>

```xml
<PropertyGroup>
  <LangVersion>latest</LangVersion>
</PropertyGroup>
```

> [!NOTE]
> <span data-ttu-id="b7d6c-129">Visual Studio IDE を使用して csproj ファイルを更新する場合、IDE によって、ビルド構成ごとにノードが作成されます。</span><span class="sxs-lookup"><span data-stu-id="b7d6c-129">If you use the Visual Studio IDE to update your csproj files, the IDE creates separate nodes for each build configuration.</span></span> <span data-ttu-id="b7d6c-130">一般的に、すべてのビルド構成で同じように値を設定しますが、ビルド構成ごとに明示的に設定する必要があります。あるいは、この設定を変更するとき、"すべての構成" を選択します。</span><span class="sxs-lookup"><span data-stu-id="b7d6c-130">You'll typically set the value the same in all build configurations, but you need to set it explicitly for each build configuration, or select "All Configurations" when you modify this setting.</span></span> <span data-ttu-id="b7d6c-131">csproj ファイルに次が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b7d6c-131">You'll see the following in your csproj file:</span></span>

```xml
<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|AnyCPU'">
  <LangVersion>latest</LangVersion>
</PropertyGroup>

<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|AnyCPU'">
  <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="b7d6c-132">`LangVersion` 要素の有効な設定:</span><span class="sxs-lookup"><span data-stu-id="b7d6c-132">Valid settings for the `LangVersion` element are:</span></span>

* `ISO-1`
* `ISO-2`
* `3`
* `4`
* `5`
* `6`
* `7`
* `7.1`
* `default`
* `latest`

<span data-ttu-id="b7d6c-133">特殊文字列の `default` と `latest` はそれぞれ、ビルド コンピューターにインストールされている最新のメジャー言語バージョンとマイナー言語バージョンに解決されます。</span><span class="sxs-lookup"><span data-stu-id="b7d6c-133">The special strings `default` and `latest` resolve to the latest major and minor language versions installed on the build machine, respectively.</span></span>

<span data-ttu-id="b7d6c-134">この設定によって、開発環境に新しいバージョンの SDK とツールをインストールすることと新しい言語機能をプロジェクトに組み込む選択が別になります。</span><span class="sxs-lookup"><span data-stu-id="b7d6c-134">This setting decouples installing new versions of the SDK and tools in your development environment from choosing to incorporate new language features in a project.</span></span> <span data-ttu-id="b7d6c-135">ビルド コンピューターに最新の SDK とツールをインストールできます。</span><span class="sxs-lookup"><span data-stu-id="b7d6c-135">You can install the latest SDK and tools on your build machine.</span></span> <span data-ttu-id="b7d6c-136">特定バージョンの言語をビルドに使用するように各プロジェクトを構成できます。</span><span class="sxs-lookup"><span data-stu-id="b7d6c-136">Each project can be configured to use a specific version of the language for its build.</span></span>

## <a name="async-main"></a><span data-ttu-id="b7d6c-137">async main</span><span class="sxs-lookup"><span data-stu-id="b7d6c-137">Async main</span></span>

<span data-ttu-id="b7d6c-138">*async main* メソッドにより、`Main` メソッドで `await` を使用できます。</span><span class="sxs-lookup"><span data-stu-id="b7d6c-138">An *async main* method enables you to use `await` in your `Main` method.</span></span>
<span data-ttu-id="b7d6c-139">以前は次のように記述する必要がありました。</span><span class="sxs-lookup"><span data-stu-id="b7d6c-139">Previously you would need to write:</span></span>

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

<span data-ttu-id="b7d6c-140">それが次のように記述できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="b7d6c-140">You can now write:</span></span>

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

<span data-ttu-id="b7d6c-141">プログラムによって終了コードが返されない場合、<xref:System.Threading.Tasks.Task> を返す `Main` メソッドを宣言できます。</span><span class="sxs-lookup"><span data-stu-id="b7d6c-141">If your program doesn't return an exit code, you can declare a `Main` method that returns a <xref:System.Threading.Tasks.Task>:</span></span>

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

<span data-ttu-id="b7d6c-142">プログラミング ガイドの [async main](../programming-guide/main-and-command-args/index.md) トピックに詳細があります。</span><span class="sxs-lookup"><span data-stu-id="b7d6c-142">You can read more about the details in the [async main](../programming-guide/main-and-command-args/index.md) topic in the programming guide.</span></span>

## <a name="default-literal-expressions"></a><span data-ttu-id="b7d6c-143">既定のリテラル式</span><span class="sxs-lookup"><span data-stu-id="b7d6c-143">Default literal expressions</span></span>

<span data-ttu-id="b7d6c-144">既定のリテラル式は既定の値式の拡張版です。</span><span class="sxs-lookup"><span data-stu-id="b7d6c-144">Default literal expressions are an enhancement to default value expressions.</span></span>
<span data-ttu-id="b7d6c-145">これらの式によって変数が初期化され、既定値になります。</span><span class="sxs-lookup"><span data-stu-id="b7d6c-145">These expressions initialize a variable to the default value.</span></span> <span data-ttu-id="b7d6c-146">以前は次のように記述していました。</span><span class="sxs-lookup"><span data-stu-id="b7d6c-146">Where you previously would write:</span></span>

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

<span data-ttu-id="b7d6c-147">それが今では、初期化の右項で種類を省略できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="b7d6c-147">You can now omit the type on the right-hand side of the initialization:</span></span>

```csharp
Func<string, bool> whereClause = default;
```

<span data-ttu-id="b7d6c-148">この拡張の詳細は、C# プログラミング ガイドの[既定の値式](../programming-guide/statements-expressions-operators/default-value-expressions.md)に関するトピックにあります。</span><span class="sxs-lookup"><span data-stu-id="b7d6c-148">You can learn more about this enhancement in the C# Programming Guide topic on [default value expressions](../programming-guide/statements-expressions-operators/default-value-expressions.md).</span></span>

<span data-ttu-id="b7d6c-149">この拡張では、[既定のキーワード](../language-reference/keywords/default.md)の解析ルールも一部変更されています。</span><span class="sxs-lookup"><span data-stu-id="b7d6c-149">This enhancement also changes some of the parsing rules for the [default keyword](../language-reference/keywords/default.md).</span></span>

## <a name="inferred-tuple-element-names"></a><span data-ttu-id="b7d6c-150">推論されたタプル要素の名前</span><span class="sxs-lookup"><span data-stu-id="b7d6c-150">Inferred tuple element names</span></span>

<span data-ttu-id="b7d6c-151">この機能は、C# 7.0 で導入されたタプル機能の小規模拡張です。</span><span class="sxs-lookup"><span data-stu-id="b7d6c-151">This feature is a small enhancement to the tuples feature introduced in C# 7.0.</span></span> <span data-ttu-id="b7d6c-152">タプルを何度初期化しても、代入の右項に使用される変数は、タプル要素に使用するものと同じ名前になります。</span><span class="sxs-lookup"><span data-stu-id="b7d6c-152">Many times when you initialize a tuple, the variables used for the right side of the assignment are the same as the names you'd like for the tuple elements:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

<span data-ttu-id="b7d6c-153">タプル要素の名前は、C# 7.1 でタプルの初期化に使用される変数から推測できます。</span><span class="sxs-lookup"><span data-stu-id="b7d6c-153">The names of tuple elements can be inferred from the variables used to initialize the tuple in C# 7.1:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

<span data-ttu-id="b7d6c-154">この機能の詳細については、[タプル](../tuples.md)に関するトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7d6c-154">You can learn more about this feature in the [Tuples](../tuples.md) topic.</span></span>

## <a name="reference-assembly-generation"></a><span data-ttu-id="b7d6c-155">参照アセンブリ生成</span><span class="sxs-lookup"><span data-stu-id="b7d6c-155">Reference assembly generation</span></span>

<span data-ttu-id="b7d6c-156">*参照専用アセンブリ*を生成する新しい 2 つのコンパイラ オプション [/refout](../language-reference/compiler-options/refout-compiler-option.md) と [/refonly](../language-reference/compiler-options/refonly-compiler-option.md) があります。</span><span class="sxs-lookup"><span data-stu-id="b7d6c-156">There are two new compiler options that generate *reference-only assemblies*: [/refout](../language-reference/compiler-options/refout-compiler-option.md) and [/refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span></span>
<span data-ttu-id="b7d6c-157">リンク先のトピックには、オプションと参照アセンブリに関する詳細があります。</span><span class="sxs-lookup"><span data-stu-id="b7d6c-157">The linked topics explain these options and reference assemblies in more detail.</span></span>
