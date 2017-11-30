---
title: "7.1 c# の新機能"
description: "7.1 c# の新機能の概要。"
keywords: "C# 言語のデザイン、7.1、Visual Studio 2017、"
author: billwagner
ms.author: wiwagn
ms.date: 08/16/2017
ms.topic: article
ms.prod: .net
ms.devlang: devlang-csharp
ms.openlocfilehash: 02f1f8fc8f0a3221e00e2a3c43ce06423ca43672
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="whats-new-in-c-71"></a><span data-ttu-id="ddc34-104">7.1 c# の新機能</span><span class="sxs-lookup"><span data-stu-id="ddc34-104">What's new in C# 7.1</span></span>

<span data-ttu-id="ddc34-105">C# 7.1 は、c# 言語に最初のポイント リリースです。</span><span class="sxs-lookup"><span data-stu-id="ddc34-105">C# 7.1 is the first point release to the C# language.</span></span> <span data-ttu-id="ddc34-106">言語の増加のリリース パターンをマークします。</span><span class="sxs-lookup"><span data-stu-id="ddc34-106">It marks an increased release cadence for the language.</span></span> <span data-ttu-id="ddc34-107">使用できますの新機能、理想的には各新機能の準備ができたとき。</span><span class="sxs-lookup"><span data-stu-id="ddc34-107">You can use the new features sooner, ideally when each new feature is ready.</span></span> <span data-ttu-id="ddc34-108">C# 7.1 は、コンパイラ、言語の指定したバージョンと一致するを構成する機能を追加します。</span><span class="sxs-lookup"><span data-stu-id="ddc34-108">C# 7.1 adds the ability to configure the compiler to match a specified version of the language.</span></span> <span data-ttu-id="ddc34-109">言語バージョンにアップグレードする意思決定からツールをアップグレードするかどうかを分離することができます。</span><span class="sxs-lookup"><span data-stu-id="ddc34-109">That enables you to separate the decision to upgrade tools from the decision to upgrade language versions.</span></span>

<span data-ttu-id="ddc34-110">C# 7.1 を追加、[バージョンの言語の選択](#language-version-selection)、3 つの新しい言語機能および新しいコンパイラの動作の構成要素。</span><span class="sxs-lookup"><span data-stu-id="ddc34-110">C# 7.1 adds the [language version selection](#language-version-selection) configuration element, three new language features and new compiler behavior.</span></span>

<span data-ttu-id="ddc34-111">このリリースの新しい言語機能は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ddc34-111">The new language features in this release are:</span></span>

* [<span data-ttu-id="ddc34-112">`async``Main`メソッド</span><span class="sxs-lookup"><span data-stu-id="ddc34-112">`async` `Main` method</span></span>](#async-main)
  - <span data-ttu-id="ddc34-113">アプリケーションのエントリ ポイントを持つことができます、`async`修飾子です。</span><span class="sxs-lookup"><span data-stu-id="ddc34-113">The entry point for an application can have the `async` modifier.</span></span>
* [<span data-ttu-id="ddc34-114">`default`リテラル式</span><span class="sxs-lookup"><span data-stu-id="ddc34-114">`default` literal expressions</span></span>](#default-literal-expressions)
  - <span data-ttu-id="ddc34-115">対象の型を推論できる場合は、既定値の式の既定のリテラル式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ddc34-115">You can use default literal expressions in default value expressions when the target type can be inferred.</span></span>
* [<span data-ttu-id="ddc34-116">推論されたタプル要素の名前</span><span class="sxs-lookup"><span data-stu-id="ddc34-116">Inferred tuple element names</span></span>](#inferred-tuple-element-names)
  - <span data-ttu-id="ddc34-117">タプル要素の名前は、多くの場合の組の初期化から推論することができます。</span><span class="sxs-lookup"><span data-stu-id="ddc34-117">The names of tuple elements can be inferred from tuple initialization in many cases.</span></span>

<span data-ttu-id="ddc34-118">コンパイラが 2 つのオプションには、最後に、`/refout`と`/refonly`を制御する[参照アセンブリの生成](#reference-assembly-generation)です。</span><span class="sxs-lookup"><span data-stu-id="ddc34-118">Finally, the compiler has two options `/refout` and `/refonly` that control [reference assembly generation](#reference-assembly-generation).</span></span>

## <a name="language-version-selection"></a><span data-ttu-id="ddc34-119">バージョンの言語の選択</span><span class="sxs-lookup"><span data-stu-id="ddc34-119">Language version selection</span></span>

<span data-ttu-id="ddc34-120">C# コンパイラでは、c# 7.1 以降では、Visual Studio 2017 バージョン 15.3、または .NET Core SDK 2.0 をサポートします。</span><span class="sxs-lookup"><span data-stu-id="ddc34-120">The C# compiler supports C# 7.1 starting with Visual Studio 2017 version 15.3, or the .NET Core SDK 2.0.</span></span> <span data-ttu-id="ddc34-121">ただし、7.1 機能は、既定でオフにされます。</span><span class="sxs-lookup"><span data-stu-id="ddc34-121">However, the 7.1 features are turned off by default.</span></span> <span data-ttu-id="ddc34-122">7.1 機能を有効にするには、プロジェクトの言語バージョンの設定を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ddc34-122">To enable the 7.1 features, you need to change the language version setting for your project.</span></span>

<span data-ttu-id="ddc34-123">Visual Studio で、ソリューション エクスプ ローラーでプロジェクト ノードを右クリックし、選択**プロパティ**です。</span><span class="sxs-lookup"><span data-stu-id="ddc34-123">In Visual Studio, right-click on the project node in Solution Explorer and select **Properties**.</span></span> <span data-ttu-id="ddc34-124">選択、**ビルド** タブを選択、**詳細**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ddc34-124">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="ddc34-125">ドロップダウンで、次のように選択します。 **c# 最新のマイナー バージョン (最新)**、または特定のバージョン**c# 7.1**イメージ次に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="ddc34-125">In the dropdown, select **C# latest minor version (latest)**, or the specific version **C# 7.1** as shown in the image following.</span></span> <span data-ttu-id="ddc34-126">`latest`値は、現在のコンピューターに最新のマイナー バージョンを使用することを意味します。</span><span class="sxs-lookup"><span data-stu-id="ddc34-126">The `latest` value means you want to use the latest minor version on the current machine.</span></span> <span data-ttu-id="ddc34-127">`C# 7.1`は最新のマイナー バージョンがリリースされた後でも、c# 7.1 を使用することを意味します。</span><span class="sxs-lookup"><span data-stu-id="ddc34-127">The `C# 7.1` means that you want to use C# 7.1, even after newer minor versions are released.</span></span>

![言語バージョンを設定](./media/csharp-7-1/advanced-build-settings.png)

<span data-ttu-id="ddc34-129">代わりに、"csproj"ファイルを編集し、追加または次の行を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="ddc34-129">Alternatively, you can edit the "csproj" file and add or modify the following lines:</span></span>

```xml
<PropertyGroup>
  <LangVersion>latest</LangVersion>
</PropertyGroup>
```

> [!NOTE]
> <span data-ttu-id="ddc34-130">Visual Studio IDE を使用して、csproj ファイルを更新する場合は、各ビルド構成に対して別々 のノードが作成されます。</span><span class="sxs-lookup"><span data-stu-id="ddc34-130">If you use the Visual Studio IDE to update your csproj files, the IDE creates separate nodes for each build configuration.</span></span> <span data-ttu-id="ddc34-131">通常値を設定する同じすべてのビルド構成が、各ビルド構成に対して明示的に設定またはこの設定を変更するときに、「すべての構成」を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ddc34-131">You'll typically set the value the same in all build configurations, but you need to set it explicitly for each build configuration, or select "All Configurations" when you modify this setting.</span></span> <span data-ttu-id="ddc34-132">Csproj ファイルで、次が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ddc34-132">You'll see the following in your csproj file:</span></span>

```xml
<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|AnyCPU'">
  <LangVersion>latest</LangVersion>
</PropertyGroup>

<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|AnyCPU'">
  <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="ddc34-133">有効な設定、`LangVersion`要素は。</span><span class="sxs-lookup"><span data-stu-id="ddc34-133">Valid settings for the `LangVersion` element are:</span></span>

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

<span data-ttu-id="ddc34-134">特殊な文字列`default`と`latest`それぞれ、ビルド コンピューターにインストールされている最新のメジャーおよびマイナーの言語バージョンに解決します。</span><span class="sxs-lookup"><span data-stu-id="ddc34-134">The special strings `default` and `latest` resolve to the latest major and minor language versions installed on the build machine, respectively.</span></span>

<span data-ttu-id="ddc34-135">この設定は、プロジェクトの新しい言語機能を組み込むを選択することから、開発環境で新しいバージョンの SDK とツールのインストールを切り離します。</span><span class="sxs-lookup"><span data-stu-id="ddc34-135">This setting decouples installing new versions of the SDK and tools in your development environment from choosing to incorporate new language features in a project.</span></span> <span data-ttu-id="ddc34-136">ビルド コンピューターには、最新の SDK とツールをインストールできます。</span><span class="sxs-lookup"><span data-stu-id="ddc34-136">You can install the latest SDK and tools on your build machine.</span></span> <span data-ttu-id="ddc34-137">各プロジェクトは、言語の特定バージョンのビルドを使用して構成できます。</span><span class="sxs-lookup"><span data-stu-id="ddc34-137">Each project can be configured to use a specific version of the language for its build.</span></span>

## <a name="async-main"></a><span data-ttu-id="ddc34-138">非同期のメイン</span><span class="sxs-lookup"><span data-stu-id="ddc34-138">Async main</span></span>

<span data-ttu-id="ddc34-139">*Async メイン*メソッドでは、使用することができます`await`で、`Main`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="ddc34-139">An *async main* method enables you to use `await` in your `Main` method.</span></span>
<span data-ttu-id="ddc34-140">以前を記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ddc34-140">Previously you would need to write:</span></span>

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

<span data-ttu-id="ddc34-141">今すぐに記述できます。</span><span class="sxs-lookup"><span data-stu-id="ddc34-141">You can now write:</span></span>

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

<span data-ttu-id="ddc34-142">宣言するかどうか、プログラムは終了コードを返さない、`Main`を返すメソッド、 <xref:System.Threading.Tasks.Task>:</span><span class="sxs-lookup"><span data-stu-id="ddc34-142">If your program doesn't return an exit code, you can declare a `Main` method that returns a <xref:System.Threading.Tasks.Task>:</span></span>

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

<span data-ttu-id="ddc34-143">詳細を読み取ることができますの詳細について、 [async メイン](../programming-guide/main-and-command-args/index.md)プログラミング ガイドの「します。</span><span class="sxs-lookup"><span data-stu-id="ddc34-143">You can read more about the details in the [async main](../programming-guide/main-and-command-args/index.md) topic in the programming guide.</span></span>

## <a name="default-literal-expressions"></a><span data-ttu-id="ddc34-144">既定のリテラル式</span><span class="sxs-lookup"><span data-stu-id="ddc34-144">Default literal expressions</span></span>

<span data-ttu-id="ddc34-145">既定のリテラル式は、既定値の式の拡張版です。</span><span class="sxs-lookup"><span data-stu-id="ddc34-145">Default literal expressions are an enhancement to default value expressions.</span></span>
<span data-ttu-id="ddc34-146">これらの式は、既定値に変数を初期化します。</span><span class="sxs-lookup"><span data-stu-id="ddc34-146">These expressions initialize a variable to the default value.</span></span> <span data-ttu-id="ddc34-147">ここで以前記述できます。</span><span class="sxs-lookup"><span data-stu-id="ddc34-147">Where you previously would write:</span></span>

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

<span data-ttu-id="ddc34-148">これで、初期化の右側にある型を省略できます。</span><span class="sxs-lookup"><span data-stu-id="ddc34-148">You can now omit the type on the right-hand side of the initialization:</span></span>

```csharp
Func<string, bool> whereClause = default;
```

<span data-ttu-id="ddc34-149">C# プログラミング ガイドのトピックでこの機能強化について詳細にについては、[値式の既定](../programming-guide/statements-expressions-operators/default-value-expressions.md)です。</span><span class="sxs-lookup"><span data-stu-id="ddc34-149">You can learn more about this enhancement in the C# Programming Guide topic on [default value expressions](../programming-guide/statements-expressions-operators/default-value-expressions.md).</span></span>

<span data-ttu-id="ddc34-150">この機能強化にもいくつかの解析規則の変更、 [default キーワード](../language-reference/keywords/default.md)です。</span><span class="sxs-lookup"><span data-stu-id="ddc34-150">This enhancement also changes some of the parsing rules for the [default keyword](../language-reference/keywords/default.md).</span></span>

## <a name="inferred-tuple-element-names"></a><span data-ttu-id="ddc34-151">推論されたタプル要素の名前</span><span class="sxs-lookup"><span data-stu-id="ddc34-151">Inferred tuple element names</span></span>

<span data-ttu-id="ddc34-152">この機能は、c# 7.0 で導入された組の機能の小さい拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="ddc34-152">This feature is a small enhancement to the tuples feature introduced in C# 7.0.</span></span> <span data-ttu-id="ddc34-153">何度も組を初期化するときに、代入の右側にあるに使用される変数は、タプル要素の名前と同じ。</span><span class="sxs-lookup"><span data-stu-id="ddc34-153">Many times when you initialize a tuple, the variables used for the right side of the assignment are the same as the names you'd like for the tuple elements:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

<span data-ttu-id="ddc34-154">タプル要素の名前は、c# 7.1 内の組を初期化するために使用される変数から推論することができます。</span><span class="sxs-lookup"><span data-stu-id="ddc34-154">The names of tuple elements can be inferred from the variables used to initialize the tuple in C# 7.1:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

<span data-ttu-id="ddc34-155">この機能についての詳細については、[組](../tuples.md)トピックです。</span><span class="sxs-lookup"><span data-stu-id="ddc34-155">You can learn more about this feature in the [Tuples](../tuples.md) topic.</span></span>

## <a name="reference-assembly-generation"></a><span data-ttu-id="ddc34-156">参照アセンブリの生成</span><span class="sxs-lookup"><span data-stu-id="ddc34-156">Reference assembly generation</span></span>

<span data-ttu-id="ddc34-157">生成する 2 つのコンパイラ オプションがある*参照専用のアセンブリ*: [/refout](../language-reference/compiler-options/refout-compiler-option.md)と[/refonly](../language-reference/compiler-options/refonly-compiler-option.md)です。</span><span class="sxs-lookup"><span data-stu-id="ddc34-157">There are two new compiler options that generate *reference-only assemblies*: [/refout](../language-reference/compiler-options/refout-compiler-option.md) and [/refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span></span>
<span data-ttu-id="ddc34-158">リンク先のトピックでは、これらのオプションと詳細の参照アセンブリを説明します。</span><span class="sxs-lookup"><span data-stu-id="ddc34-158">The linked topics explain these options and reference assemblies in more detail.</span></span>
