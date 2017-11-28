---
title: "文字列補間 - C"
description: "C# 6 の文字列補間の動作について"
keywords: ".NET、.NET Core、C#、文字列"
author: mgroves
ms.author: wiwagn
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: f8806f6b-3ac7-4ee6-9b3e-c524d5301ae9
ms.openlocfilehash: ac19d4208da4f8ee6dd3e071ab70dbc41a0cd065
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="string-interpolation-in-c"></a><span data-ttu-id="ada80-104">C# における文字列補間</span><span class="sxs-lookup"><span data-stu-id="ada80-104">String Interpolation in C#</span></span> #

<span data-ttu-id="ada80-105">文字列補間は、文字列内のプレースホルダーを文字列変数の値によって置き換える方法です。</span><span class="sxs-lookup"><span data-stu-id="ada80-105">String Interpolation is the way that placeholders in a string are replaced by the value of a string variable.</span></span> <span data-ttu-id="ada80-106">C# 6 より前は、これは `System.String.Format` を使用して行われました。</span><span class="sxs-lookup"><span data-stu-id="ada80-106">Before C# 6, the way to do this is with `System.String.Format`.</span></span> <span data-ttu-id="ada80-107">それでも動作しますが、番号付きのプレースホルダーを使用するため読みにくく冗長になります。</span><span class="sxs-lookup"><span data-stu-id="ada80-107">This works okay, but since it uses numbered placeholders, it can be harder to read and more verbose.</span></span>

<span data-ttu-id="ada80-108">他のプログラミング言語ではすでに、文字列補間の機能を組み込んでいました。</span><span class="sxs-lookup"><span data-stu-id="ada80-108">Other programming languages have had string interpolation built into the language for a while.</span></span> <span data-ttu-id="ada80-109">たとえば PHP では次のようになります。</span><span class="sxs-lookup"><span data-stu-id="ada80-109">For instance, in PHP:</span></span>

```php
$name = "Jonas";
echo "My name is $name.";
// This will output "My name is Jonas."
```

<span data-ttu-id="ada80-110">C# 6 でついに、この形式の文字列補間ができるようになりました。</span><span class="sxs-lookup"><span data-stu-id="ada80-110">In C# 6, we finally have that style of string interpolation.</span></span> <span data-ttu-id="ada80-111">文字列の前に `$` を使用して、それらの値の変数または式に置き換えると示すことができます。</span><span class="sxs-lookup"><span data-stu-id="ada80-111">You can use a `$` before a string to indicate that it should substitute variables/expressions for their values.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ada80-112">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="ada80-112">Prerequisites</span></span>
<span data-ttu-id="ada80-113">お使いのコンピューターを、.NET Core が実行されるように設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ada80-113">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="ada80-114">インストールの指示については、[.NET Core](https://www.microsoft.com/net/core) のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ada80-114">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span>
<span data-ttu-id="ada80-115">このアプリケーションは、Windows、Ubuntu Linux、macOS または Docker コンテナーで実行できます。</span><span class="sxs-lookup"><span data-stu-id="ada80-115">You can run this application on Windows, Ubuntu Linux, macOS or in a Docker container.</span></span> <span data-ttu-id="ada80-116">お好みのコード エディターをインストールしてください。</span><span class="sxs-lookup"><span data-stu-id="ada80-116">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="ada80-117">次の説明では、オープン ソースのクロス プラットフォーム エディターである [Visual Studio Code](https://code.visualstudio.com/) を使用しています。</span><span class="sxs-lookup"><span data-stu-id="ada80-117">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="ada80-118">しかし、他の使い慣れたツールを使用しても構いません。</span><span class="sxs-lookup"><span data-stu-id="ada80-118">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="ada80-119">アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="ada80-119">Create the Application</span></span>

<span data-ttu-id="ada80-120">すべてのツールをインストールしたら、新しい .NET Core アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="ada80-120">Now that you've installed all the tools, create a new .NET Core application.</span></span> <span data-ttu-id="ada80-121">コマンド ライン ジェネレーターを使用するには、`interpolated` などプロジェクトのディレクトリを作成し、好みのシェルで次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="ada80-121">To use the command line generator, create a directory for your project, such as `interpolated`, and execute the following command in your favorite shell:</span></span>

```
dotnet new console
```

<span data-ttu-id="ada80-122">このコマンドで、プロジェクト ファイル *interpolated.csproj* およびソース コード ファイル *Program.cs* とともに、必要最低限の .NET Core プロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="ada80-122">This command will create a barebones .NET core project with a project file, *interpolated.csproj*, and a source code file, *Program.cs*.</span></span> <span data-ttu-id="ada80-123">`dotnet restore` を実行して、このプロジェクトのコンパイルに必要な依存関係を復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ada80-123">You will need to execute `dotnet restore` to restore the dependencies needed to compile this project.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="ada80-124">プログラムを実行するには `dotnet run` を使用します。</span><span class="sxs-lookup"><span data-stu-id="ada80-124">To execute the program, use `dotnet run`.</span></span> <span data-ttu-id="ada80-125">コンソールに "Hello, World" という出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ada80-125">You should see "Hello, World" output to the console.</span></span>



## <a name="intro-to-string-interpolation"></a><span data-ttu-id="ada80-126">文字列補間の概要</span><span class="sxs-lookup"><span data-stu-id="ada80-126">Intro to String Interpolation</span></span>

<span data-ttu-id="ada80-127">`System.String.Format` を使用して、文字列で、その文字列に続くパラメーターで置き換えられる "プレースホルダー" を指定します。</span><span class="sxs-lookup"><span data-stu-id="ada80-127">With `System.String.Format`, you specify "placeholders" in a string that are replaced by the parameters following the string.</span></span> <span data-ttu-id="ada80-128">たとえば、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="ada80-128">For instance:</span></span>

[!code-csharp[String.Format example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#StringFormatExample)]  

<span data-ttu-id="ada80-129">これにより "My name is Matt Groves" と出力されます。</span><span class="sxs-lookup"><span data-stu-id="ada80-129">That will output "My name is Matt Groves".</span></span>

<span data-ttu-id="ada80-130">C# 6 では `String.Format` を使用する代わりに `$` 記号とともに付加して文字列で直接変数を使用することにより、補間文字列を定義します。</span><span class="sxs-lookup"><span data-stu-id="ada80-130">In C# 6, instead of using `String.Format`, you define an interpolated string by prepending it with the `$` symbol, and then using the variables directly in the string.</span></span> <span data-ttu-id="ada80-131">たとえば、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="ada80-131">For instance:</span></span>

[!code-csharp[Interpolation example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationExample)]  

<span data-ttu-id="ada80-132">使用するのは変数のみとは限りません。</span><span class="sxs-lookup"><span data-stu-id="ada80-132">You don't have to use just variables.</span></span> <span data-ttu-id="ada80-133">角かっこ内で任意の式を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="ada80-133">You can use any expression within the brackets.</span></span> <span data-ttu-id="ada80-134">たとえば、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="ada80-134">For instance:</span></span>

[!code-csharp[Interpolation expression example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationExpressionExample)]  

<span data-ttu-id="ada80-135">この出力は以下のようになります。</span><span class="sxs-lookup"><span data-stu-id="ada80-135">Which would output:</span></span>

```
This is line number 1
This is line number 2
This is line number 3
This is line number 4
This is line number 5
```

## <a name="how-string-interpolation-works"></a><span data-ttu-id="ada80-136">文字列補間の動作</span><span class="sxs-lookup"><span data-stu-id="ada80-136">How string interpolation works</span></span>

<span data-ttu-id="ada80-137">背後では、この文字列補間の構文はコンパイラによって String.Format に変換されます。</span><span class="sxs-lookup"><span data-stu-id="ada80-137">Behind the scenes, this string interpolation syntax is translated into String.Format by the compiler.</span></span> <span data-ttu-id="ada80-138">そのため、[前に String.Format で実行したのと同様のこと](https://msdn.microsoft.com/en-us/library/dwhawy9k(v=vs.110).aspx)ができます。</span><span class="sxs-lookup"><span data-stu-id="ada80-138">So, you can do the [same type of stuff you've done before with String.Format](https://msdn.microsoft.com/en-us/library/dwhawy9k(v=vs.110).aspx).</span></span>

<span data-ttu-id="ada80-139">たとえば、パディングと数値の書式設定を追加できます。</span><span class="sxs-lookup"><span data-stu-id="ada80-139">For instance, you can add padding and numeric formatting:</span></span>

[!code-csharp[Interpolation formatting example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationFormattingExample)]  

<span data-ttu-id="ada80-140">上記はこのような出力となります。</span><span class="sxs-lookup"><span data-stu-id="ada80-140">The above would output something like:</span></span>

```
998        5,177.67
999        6,719.30
1000       9,910.61
1001       529.34
1002       1,349.86
1003       2,660.82
1004       6,227.77
```

<span data-ttu-id="ada80-141">変数名が見つからない場合、コンパイル時エラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="ada80-141">If a variable name is not found, then a compile time error will be generated.</span></span>

<span data-ttu-id="ada80-142">たとえば、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="ada80-142">For instance:</span></span>

```csharp
var animal = "fox";
var localizeMe = $"The {adj} brown {animal} jumped over the lazy {otheranimal}";
var adj = "quick";
Console.WriteLine(localizeMe);
```

<span data-ttu-id="ada80-143">これをコンパイルすると、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="ada80-143">If you compile this, you'll get errors:</span></span>
 
* <span data-ttu-id="ada80-144">`Cannot use local variable 'adj' before it is declared` - 変数 `adj` が補間された文字列の*後までに*宣言されなかった。</span><span class="sxs-lookup"><span data-stu-id="ada80-144">`Cannot use local variable 'adj' before it is declared` - the `adj` variable wasn't declared until *after* the interpolated string.</span></span>
* <span data-ttu-id="ada80-145">`The name 'otheranimal' does not exist in the current context` - `otheranimal` と呼ばれる変数が宣言すらされていない。</span><span class="sxs-lookup"><span data-stu-id="ada80-145">`The name 'otheranimal' does not exist in the current context` - a variable called `otheranimal` was never even declared</span></span>

## <a name="localization-and-internationalization"></a><span data-ttu-id="ada80-146">ローカリゼーションと国際化</span><span class="sxs-lookup"><span data-stu-id="ada80-146">Localization and Internationalization</span></span>

<span data-ttu-id="ada80-147">補間された文字列は `IFormattable` と `FormattableString` をサポートしており、国際化するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="ada80-147">An interpolated string supports `IFormattable` and `FormattableString`, which can be useful for internationalization.</span></span>

<span data-ttu-id="ada80-148">既定では、補間された文字列は現在のカルチャを使用します。</span><span class="sxs-lookup"><span data-stu-id="ada80-148">By default, an interpolated string uses the current culture.</span></span> <span data-ttu-id="ada80-149">別のカルチャを使用するには、`IFormattable` としてキャストします。</span><span class="sxs-lookup"><span data-stu-id="ada80-149">To use a different culture, you could cast it as `IFormattable`</span></span>

<span data-ttu-id="ada80-150">たとえば、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="ada80-150">For instance:</span></span>

[!code-csharp[Interpolation internationalization example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationInternationalizationExample)]  

## <a name="conclusion"></a><span data-ttu-id="ada80-151">まとめ</span><span class="sxs-lookup"><span data-stu-id="ada80-151">Conclusion</span></span> 

<span data-ttu-id="ada80-152">このチュートリアルでは、C# 6 の文字列補間機能の使用方法について説明しました。</span><span class="sxs-lookup"><span data-stu-id="ada80-152">In this tutorial, you learned how to use string interpolation features of C# 6.</span></span> <span data-ttu-id="ada80-153">これは基本的に、シンプルな `String.Format` ステートメントを書く簡潔な方法で、より高度な使い方をするには注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="ada80-153">It's basically a more concise way of writing simple `String.Format` statements, with some caveats for more advanced uses of it.</span></span>
