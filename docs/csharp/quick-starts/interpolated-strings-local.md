---
title: 文字列補間のチュートリアル - C# ローカル クイックスタート
description: このクイックスタートでは、C# で文字列補間機能を使用して、大きい文字列で書式設定された計算式の結果を含める方法を示します。
author: rpetrusha
ms.author: ronpet
ms.date: 04/14/2018
ms.custom: mvc
ms.openlocfilehash: 80b7a2c39094f1101e714b47f0e77f0a7c4907f2
ms.sourcegitcommit: 77d9a94dac4c05827ed0663d95e0f9ad35d6682e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/24/2018
ms.locfileid: "34472764"
---
# <a name="string-interpolation"></a><span data-ttu-id="0bb39-103">文字列補間</span><span class="sxs-lookup"><span data-stu-id="0bb39-103">String interpolation</span></span>

<span data-ttu-id="0bb39-104">このクイックスタートでは、C# で[文字列補間](../language-reference/tokens/interpolated.md)を使用して、単一の結果の文字列に値を挿入する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="0bb39-104">This quickstart teaches you how to use C# [string interpolation](../language-reference/tokens/interpolated.md) to insert values into a single result string.</span></span> <span data-ttu-id="0bb39-105">C# コードを記述し、コードをコンパイルおよび実行して結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="0bb39-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="0bb39-106">クイックスタートには、値を文字列に挿入し、それらの値の書式をさまざまな方法で設定する方法を示す、一連のレッスンが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0bb39-106">The quickstart contains a series of lessons that show you how to insert values into a string and format those values in different ways.</span></span>

<span data-ttu-id="0bb39-107">このクイックスタートでは、開発用に使用できるマシンがあることを想定しています。</span><span class="sxs-lookup"><span data-stu-id="0bb39-107">This quickstart expects that you have a machine you can use for development.</span></span> <span data-ttu-id="0bb39-108">Mac、PC、または Linux 上でローカルの開発環境を設定する手順については、.NET の [10 分でわかる概要](https://www.microsoft.com/net/core)に関するトピックに記載されています。</span><span class="sxs-lookup"><span data-stu-id="0bb39-108">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="0bb39-109">使用するコマンドの概要を手短に確認するには、[ローカルでのクイックスタートの概要](local-environment.md)と詳細へのリンクをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0bb39-109">A quick overview of the commands you'll use is in the [introduction to the local quickstarts](local-environment.md) with links to more details.</span></span> <span data-ttu-id="0bb39-110">また、使用しているブラウザーでこのクイックスタートの[対話型バージョン](interpolated-strings.yml)を完了することもできます。</span><span class="sxs-lookup"><span data-stu-id="0bb39-110">You also can complete the [interactive version](interpolated-strings.yml) of this quickstart in your browser.</span></span>

## <a name="create-an-interpolated-string"></a><span data-ttu-id="0bb39-111">挿入文字列を作成する</span><span class="sxs-lookup"><span data-stu-id="0bb39-111">Create an interpolated string</span></span>

<span data-ttu-id="0bb39-112">**interpolated** という名前のディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="0bb39-112">Create a directory named **interpolated**.</span></span> <span data-ttu-id="0bb39-113">それを現在のディレクトリにして、コンソール ウィンドウから次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="0bb39-113">Make it the current directory and run the following command from a console window:</span></span>

```console
dotnet new console
```

<span data-ttu-id="0bb39-114">このコマンドによって、現在のディレクトリに新しい .NET Core コンソール アプリケーションが作成されます。</span><span class="sxs-lookup"><span data-stu-id="0bb39-114">This command creates a new .NET Core console application in the current directory.</span></span>

<span data-ttu-id="0bb39-115">お好みのエディターで **Program.cs** を開き、`Console.WriteLine("Hello World!");` の行を次のコードで置き換えます。`<name>` は自分の名前に置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="0bb39-115">Open **Program.cs** in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code, where you replace `<name>` with your name:</span></span>

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```

<span data-ttu-id="0bb39-116">コンソール ウィンドウで「`dotnet run`」と入力し、このコードを試します。</span><span class="sxs-lookup"><span data-stu-id="0bb39-116">Try this code by typing `dotnet run` in your console window.</span></span> <span data-ttu-id="0bb39-117">プログラムを実行すると、あいさつ文に自分の名前を含む単一の文字列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0bb39-117">When you run the program, it displays a single string that includes your name in the greeting.</span></span> <span data-ttu-id="0bb39-118"><xref:System.Console.WriteLine%2A> メソッド呼び出しに含まれる文字列は、*挿入文字列*です。</span><span class="sxs-lookup"><span data-stu-id="0bb39-118">The string included in the <xref:System.Console.WriteLine%2A> method call is an *interpolated string*.</span></span> <span data-ttu-id="0bb39-119">これは、埋め込みコードを含む文字列から (*結果文字列*という) 単一の文字列を構築できる一種のテンプレートです。</span><span class="sxs-lookup"><span data-stu-id="0bb39-119">It's a kind of template that lets you construct a single string (called the *result string*) from a string that includes embedded code.</span></span> <span data-ttu-id="0bb39-120">挿入文字列は、文字列に値を挿入したり、文字列を (結合) 連結したりする場合に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="0bb39-120">Interpolated strings are particularly useful for inserting values into a string or concatenating (joining together) strings.</span></span>

<span data-ttu-id="0bb39-121">この簡単な例には、すべての挿入文字列に含める必要がある次の 2 つの要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="0bb39-121">This simple example contains the two elements that every interpolated string must have:</span></span>

- <span data-ttu-id="0bb39-122">始まりの引用符文字の前の `$` で始まる文字列リテラル。</span><span class="sxs-lookup"><span data-stu-id="0bb39-122">A string literal that begins with the `$` character before its opening quotation mark character.</span></span> <span data-ttu-id="0bb39-123">`$` シンボルと引用符文字の間にスペースを挿入することはできません </span><span class="sxs-lookup"><span data-stu-id="0bb39-123">There can't be any spaces between the `$` symbol and the quotation mark character.</span></span> <span data-ttu-id="0bb39-124">(スペースが含まれている場合の動作を確認したい場合は、`$` 文字の後にスペースを挿入し、ファイルを保存してから、コンソール ウィンドウで「`dotnet run`」と入力してプログラムを再実行します。</span><span class="sxs-lookup"><span data-stu-id="0bb39-124">(If you'd like to see what happens if you include one, insert a space after the `$` character, save the file, and run the program again by typing `dotnet run` in the console window.</span></span> <span data-ttu-id="0bb39-125">C# コンパイラには、"エラー CS1056: 予期しない文字 '$' です" というエラー メッセージが表示されます)。</span><span class="sxs-lookup"><span data-stu-id="0bb39-125">The C# compiler displays an error message, "error CS1056: Unexpected character '$'".)</span></span>

- <span data-ttu-id="0bb39-126">1 つ以上の*挿入式*。</span><span class="sxs-lookup"><span data-stu-id="0bb39-126">One or more *interpolated expressions*.</span></span> <span data-ttu-id="0bb39-127">挿入式は、始めかっこと終わりかっこ (`{` と `}`) で示されます。</span><span class="sxs-lookup"><span data-stu-id="0bb39-127">An interpolated expression is indicated by an opening and closing brace (`{` and `}`).</span></span> <span data-ttu-id="0bb39-128">かっこ内に (`null` を含む) 値を返す C# 式を配置できます。</span><span class="sxs-lookup"><span data-stu-id="0bb39-128">You can put any C# expression that returns a value (including `null`) inside the braces.</span></span>

<span data-ttu-id="0bb39-129">その他のいくつかのデータ型を持つ文字列補間の例をさらにいくつか試してみましょう。</span><span class="sxs-lookup"><span data-stu-id="0bb39-129">Let's try a few more string interpolation examples with some other data types.</span></span>

## <a name="include-different-data-types"></a><span data-ttu-id="0bb39-130">さまざまなデータ型を含める</span><span class="sxs-lookup"><span data-stu-id="0bb39-130">Include different data types</span></span>

<span data-ttu-id="0bb39-131">前のセクションでは、文字列補間を使用して、1 つの文字列内に別の文字列を挿入しましたが、</span><span class="sxs-lookup"><span data-stu-id="0bb39-131">In the previous section, you used string interpolation to insert one string inside of another.</span></span> <span data-ttu-id="0bb39-132">挿入式の結果を任意のデータ型にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="0bb39-132">The result of an interpolated expression can be of any data type, though.</span></span> <span data-ttu-id="0bb39-133">挿入文字列にさまざまなデータ型の値を含めてみましょう。</span><span class="sxs-lookup"><span data-stu-id="0bb39-133">Let's include values of various data types in an interpolated string.</span></span>

<span data-ttu-id="0bb39-134">次の例では、最初に、`Name` [プロパティ](../properties.md)と `ToString` [メソッド](../methods.md)を持つ[クラス](../programming-guide/classes-and-structs/classes.md) データ型 `Vegetable` を定義します。このメソッドは、<xref:System.Object.ToString?displayProperty=nameWithType> メソッドの動作を[オーバーライド](../language-reference/keywords/override.md)します。</span><span class="sxs-lookup"><span data-stu-id="0bb39-134">In the following example, first, we define a [class](../programming-guide/classes-and-structs/classes.md) data type `Vegetable` that has the `Name` [property](../properties.md) and the `ToString` [method](../methods.md), which [overrides](../language-reference/keywords/override.md) the behavior of the <xref:System.Object.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0bb39-135">[`public` アクセス修飾子](../language-reference/keywords/public.md)により、そのメソッドは、すべてのクライアント コードで `Vegetable` インスタンスの文字列表現を取得するために使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="0bb39-135">The [`public` access modifier](../language-reference/keywords/public.md) makes that method available to any client code to get the string representation of a `Vegetable` instance.</span></span> <span data-ttu-id="0bb39-136">この例の `Vegetable.ToString` メソッドでは、`Vegetable` [コンストラクター](../programming-guide/classes-and-structs/constructors.md)で初期化される `Name` プロパティの値を返します。</span><span class="sxs-lookup"><span data-stu-id="0bb39-136">In the example the `Vegetable.ToString` method returns the value of the `Name` property that is initialized at the `Vegetable` [constructor](../programming-guide/classes-and-structs/constructors.md):</span></span>

```csharp
public Vegetable(string name) => Name = name;
```

<span data-ttu-id="0bb39-137">次に、[`new` キーワード](../language-reference/keywords/new-operator.md)を使用して、コンストラクター `Vegetable` の name パラメーターを指定し、`Vegetable` クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="0bb39-137">Then we create an instance of the `Vegetable` class by using [`new` keyword](../language-reference/keywords/new-operator.md) and providing a name parameter for the constructor `Vegetable`:</span></span>

```csharp
var item = new Vegetable("eggplant");
```

<span data-ttu-id="0bb39-138">最後に、`item` 変数を挿入文字列に含めます。ここには、<xref:System.DateTime> 値、<xref:System.Decimal> 値、`Unit` [列挙](../programming-guide/enumeration-types.md)値も含まれます。</span><span class="sxs-lookup"><span data-stu-id="0bb39-138">Finally, we include the `item` variable into an interpolated string that also contains a <xref:System.DateTime> value, a <xref:System.Decimal> value, and a `Unit` [enumeration](../programming-guide/enumeration-types.md) value.</span></span> <span data-ttu-id="0bb39-139">エディターのすべての C# コードを以下のコードに置き換えてから、`dotnet run` コマンドを使用して実行します。</span><span class="sxs-lookup"><span data-stu-id="0bb39-139">Replace all of the C# code in your editor with the following code, and then use the `dotnet run` command to run it:</span></span>

```csharp
using System;

public class Vegetable
{
   public Vegetable(string name) => Name = name;
   
   public string Name { get; }
   
   public override string ToString() => Name;
}

public class Program
{
   public enum Unit { item, pound, ounce, dozen };

   public static void Main()
   {
      var item = new Vegetable("eggplant");
      var date = DateTime.Now;
      var price = 1.99m;
      var unit = Unit.item;
      Console.WriteLine($"On {date}, the price of {item} was {price} per {unit}.");
   }
}
```

<span data-ttu-id="0bb39-140">挿入文字列の挿入式 `item` は、結果の文字列のテキスト "eggplant" に解決されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="0bb39-140">Note that the interpolated expression `item` in the interpolated string resolves to the text "eggplant" in the result string.</span></span> <span data-ttu-id="0bb39-141">これは、式の結果の型が文字列でない場合に、結果が次の方法で文字列に解決されるためです。</span><span class="sxs-lookup"><span data-stu-id="0bb39-141">That's because, when the type of the expression result is not a string, the result is resolved to a string in the following way:</span></span>

- <span data-ttu-id="0bb39-142">挿入式が `null` の場合、空の文字列 (""、または <xref:System.String.Empty?displayProperty=nameWithType>) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="0bb39-142">If the interpolated expression evaluates to `null`, an empty string ("", or <xref:System.String.Empty?displayProperty=nameWithType>) is used.</span></span>

- <span data-ttu-id="0bb39-143">挿入式が `null` でない場合、通常、結果の型の `ToString` メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="0bb39-143">If the interpolated expression doesn't evaluate to `null`, typically the `ToString` method of the result type is called.</span></span> <span data-ttu-id="0bb39-144">`Vegetable.ToString` メソッドの実装を更新して、これをテストすることができます。</span><span class="sxs-lookup"><span data-stu-id="0bb39-144">You can test this by updating the implementation of the `Vegetable.ToString` method.</span></span> <span data-ttu-id="0bb39-145">すべての型にこのメソッドの実装が含まれるため、`ToString` メソッドを実装する必要なない場合があります。</span><span class="sxs-lookup"><span data-stu-id="0bb39-145">You might not even need to implement the `ToString` method since every type has some implementation of this method.</span></span> <span data-ttu-id="0bb39-146">これをテストするには、例の `Vegetable.ToString` メソッドの定義をコメント アウトします (この操作を行うには、コメント シンボル `//` を前に配置します)。</span><span class="sxs-lookup"><span data-stu-id="0bb39-146">To test this, comment out the definition of the `Vegetable.ToString` method in the example (to do that, put a comment symbol, `//`, in front of it).</span></span> <span data-ttu-id="0bb39-147">出力では、"eggplant" という文字列が完全修飾型名 (この例では "Vegetable") に置き換えられます。これは、<xref:System.Object.ToString?displayProperty=nameWithType> メソッドの既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="0bb39-147">In the output, the string "eggplant" is replaced by the fully qualified type name ("Vegetable" in this example), which is the default behavior of the <xref:System.Object.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0bb39-148">列挙値の `ToString` メソッドの既定の動作は、値の文字列表現を返すことです。</span><span class="sxs-lookup"><span data-stu-id="0bb39-148">The default behavior of the `ToString` method for an enumeration value is to return the string representation of the value.</span></span>

<span data-ttu-id="0bb39-149">この例の出力では、日付の精度が高すぎ ("eggplant" の価格は毎秒変更されることはありません)、価格の値は通貨の単位を示していません。</span><span class="sxs-lookup"><span data-stu-id="0bb39-149">In the output from this example, the date is too precise (the price of eggplant doesn't change every second), and the price value doesn't indicate a unit of currency.</span></span> <span data-ttu-id="0bb39-150">次のセクションでは、式の結果における文字列表現の書式を制御することで、こうした問題を修正する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0bb39-150">In the next section, you'll learn how to fix those issues by controlling the format of string representations of the expression results.</span></span>

## <a name="control-the-formatting-of-interpolated-expressions"></a><span data-ttu-id="0bb39-151">挿入式の書式設定を制御する</span><span class="sxs-lookup"><span data-stu-id="0bb39-151">Control the formatting of interpolated expressions</span></span>

<span data-ttu-id="0bb39-152">前のセクションでは、適切に書式設定されていない 2 つの文字列が結果文字列に挿入されました。</span><span class="sxs-lookup"><span data-stu-id="0bb39-152">In the previous section, two poorly formatted strings were inserted into the result string.</span></span> <span data-ttu-id="0bb39-153">1 つは、日付のみが適切な日時の値でした。</span><span class="sxs-lookup"><span data-stu-id="0bb39-153">One was a date and time value for which only the date was appropriate.</span></span> <span data-ttu-id="0bb39-154">もう 1 つは、通貨単位を示さない価格でした。</span><span class="sxs-lookup"><span data-stu-id="0bb39-154">The second was a price that didn't indicate its unit of currency.</span></span> <span data-ttu-id="0bb39-155">両方の問題には簡単に対処することができます。</span><span class="sxs-lookup"><span data-stu-id="0bb39-155">Both issues are easy to address.</span></span> <span data-ttu-id="0bb39-156">文字列補間では、特定の型の書式設定を制御する*書式指定文字列*を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="0bb39-156">String interpolation lets you specify *format strings* that control the formatting of particular types.</span></span> <span data-ttu-id="0bb39-157">前の例の `Console.WriteLine` 呼び出しを変更し、次の行に示すように、日付と価格の式の書式指定文字列を含めます。</span><span class="sxs-lookup"><span data-stu-id="0bb39-157">Modify the call to `Console.WriteLine` from the previous example to include the format strings for the date and price expressions as shown in the following line:</span></span>

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```

<span data-ttu-id="0bb39-158">コロン (":") と書式指定文字列を持つ挿入式に従って、書式指定文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="0bb39-158">You specify a format string by following the interpolated expression with a colon (":") and the format string.</span></span> <span data-ttu-id="0bb39-159">"d" は、短い日付形式を表す[標準の日時書式設定文字列](../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier)です。</span><span class="sxs-lookup"><span data-stu-id="0bb39-159">"d" is a [standard date and time format string](../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) that represents the short date format.</span></span> <span data-ttu-id="0bb39-160">"C2" は、小数点以下が 2 桁の通貨値として数値を表す[標準の数値書式指定文字列](../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier)です。</span><span class="sxs-lookup"><span data-stu-id="0bb39-160">"C2" is a  [standard numeric format string](../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) that represents a number as a currency value with two digits after the decimal point.</span></span>

<span data-ttu-id="0bb39-161">.NET ライブラリの多くの型で、定義済みの書式指定文字列セットがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="0bb39-161">A number of types in the .NET libraries support a predefined set of format strings.</span></span> <span data-ttu-id="0bb39-162">これらには、数値型と日時型がすべて含まれます。</span><span class="sxs-lookup"><span data-stu-id="0bb39-162">These include all the numeric types and the date and time types.</span></span> <span data-ttu-id="0bb39-163">書式指定文字列をサポートする型の完全なリストについては、「[.Net 型の書式設定](../../standard/base-types/formatting-types.md)」記事の「[.NET クラス ライブラリの型および書式指定文字列](../../standard/base-types/formatting-types.md#stringRef)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0bb39-163">For a complete list of types that support format strings, see [Format Strings and .NET Class Library Types](../../standard/base-types/formatting-types.md#stringRef) in the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) article.</span></span>

<span data-ttu-id="0bb39-164">テキスト エディターで書式指定文字列を変更してみて、変更するたびにプログラムを再実行し、変更が日時と数値の書式設定にどのように影響するかを確認します。</span><span class="sxs-lookup"><span data-stu-id="0bb39-164">Try modifying the format strings in your text editor and, each time you make a change, rerun the program to see how the changes affect the formatting of the date and time and the numeric value.</span></span> <span data-ttu-id="0bb39-165">`{date:d}` の "d" を "t" (短い時刻形式を表示する)、"y" (年と月を表示する)、"yyyy" (4 桁の数字として年を表示する) に変更します。</span><span class="sxs-lookup"><span data-stu-id="0bb39-165">Change the "d" in `{date:d}` to "t" (to display the short time format), "y" (to display the year and month), and "yyyy" (to display the year as a four-digit number).</span></span> <span data-ttu-id="0bb39-166">`{price:C2}` "C2" を "e" (指数表記の場合) と "F3" (小数点以下が 3 桁の数値の場合) に変更します。</span><span class="sxs-lookup"><span data-stu-id="0bb39-166">Change the "C2" in `{price:C2}` to "e" (for exponential notation) and "F3" (for a numeric value with three digits after the decimal point).</span></span>

<span data-ttu-id="0bb39-167">書式設定を制御するだけでなく、結果の文字列に含まれる書式指定された文字列のフィールドの幅と配置を制御することもできます。</span><span class="sxs-lookup"><span data-stu-id="0bb39-167">In addition to controlling formatting, you can also control the field width and alignment of the formatted strings that are included in the result string.</span></span> <span data-ttu-id="0bb39-168">次のセクションでは、この方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="0bb39-168">In the next section, you'll learn how to do this.</span></span>

## <a name="control-the-field-width-and-alignment-of-interpolated-expressions"></a><span data-ttu-id="0bb39-169">挿入式のフィールドの幅と配置を制御する</span><span class="sxs-lookup"><span data-stu-id="0bb39-169">Control the field width and alignment of interpolated expressions</span></span>

<span data-ttu-id="0bb39-170">通常、挿入式の結果が文字列に書式設定される場合、文字列は先頭スペースおよび末尾スペースなしで結果文字列に含まれます。</span><span class="sxs-lookup"><span data-stu-id="0bb39-170">Ordinarily, when the result of an interpolated expression is formatted to string, that string is included in a result string without leading or trailing spaces.</span></span> <span data-ttu-id="0bb39-171">通常、データのセットを操作する場合、フィールドの幅とテキストの配置を制御できることで、読みやすい出力を生成できます。</span><span class="sxs-lookup"><span data-stu-id="0bb39-171">Particularly when you work with a set of data, being able to control a field width and text alignment helps to produce a more readable output.</span></span> <span data-ttu-id="0bb39-172">そのためには、テキスト エディターのすべてのコードを次のコードに置き換えてから、「`dotnet run`」と入力してプログラムを実行します。</span><span class="sxs-lookup"><span data-stu-id="0bb39-172">To see this, replace all the code in your text editor with the following code, then type `dotnet run` to execute the program:</span></span>

```csharp
using System;
using System.Collections.Generic;

public class Example
{
   public static void Main()
   {
      var titles = new Dictionary<string, string>()
      {
          ["Doyle, Arthur Conan"] = "Hound of the Baskervilles, The",
          ["London, Jack"] = "Call of the Wild, The",
          ["Shakespeare, William"] = "Tempest, The"
      };

      Console.WriteLine("Author and Title List");
      Console.WriteLine();
      Console.WriteLine($"|{"Author",-25}|{"Title",30}|");
      foreach (var title in titles)
         Console.WriteLine($"|{title.Key,-25}|{title.Value,30}|");
   }
}
```

<span data-ttu-id="0bb39-173">作成者の名前は左揃えになり、書き込まれたタイトルは右揃えになります。</span><span class="sxs-lookup"><span data-stu-id="0bb39-173">The names of authors are left-aligned, and the titles they wrote are right-aligned.</span></span> <span data-ttu-id="0bb39-174">挿入式の後にコンマ (",") を追加し、*最小*のフィールド幅を指定して、配置を指定します。</span><span class="sxs-lookup"><span data-stu-id="0bb39-174">You specify the alignment by adding a comma (",") after an interpolated expression and designating the *minimum* field width.</span></span> <span data-ttu-id="0bb39-175">指定された値が正数の場合、フィールドは右揃えになります。</span><span class="sxs-lookup"><span data-stu-id="0bb39-175">If the specified value is a positive number, the field is right-aligned.</span></span> <span data-ttu-id="0bb39-176">負数の場合、フィールドは左揃えになります。</span><span class="sxs-lookup"><span data-stu-id="0bb39-176">If it is a negative number, the field is left-aligned.</span></span>

<span data-ttu-id="0bb39-177">`{"Author",-25}` と `{title.Key,-25}` のコードから負号を削除してみて、次のコードのように、例を再実行します。</span><span class="sxs-lookup"><span data-stu-id="0bb39-177">Try removing the negative signs from the `{"Author",-25}` and `{title.Key,-25}` code and run the example again, as the following code does:</span></span>

```csharp
Console.WriteLine($"|{"Author",25}|{"Title",30}|");
foreach (var title in titles)
   Console.WriteLine($"|{title.Key,25}|{title.Value,30}|");
```

<span data-ttu-id="0bb39-178">この場合、作成者情報は右揃えになります。</span><span class="sxs-lookup"><span data-stu-id="0bb39-178">This time, the author information is right-aligned.</span></span>

<span data-ttu-id="0bb39-179">単一の挿入式にアラインメント指定子と書式指定文字列を組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="0bb39-179">You can combine an alignment specifier and a format string for a single interpolated expression.</span></span> <span data-ttu-id="0bb39-180">この操作を行うには、最初に配置を指定して、その後にコロンと書式指定文字列を続けます。</span><span class="sxs-lookup"><span data-stu-id="0bb39-180">To do that, specify the alignment first, followed by a colon and the format string.</span></span> <span data-ttu-id="0bb39-181">`Main` メソッド内のすべてのコードを次のコードに置き換えると、フィールド幅が定義された 3 つの書式指定された文字列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0bb39-181">Replace all of the code inside the `Main` method with the following code, which displays three formatted strings with defined field widths.</span></span> <span data-ttu-id="0bb39-182">次に、`dotnet run` コマンドを入力してプログラムを実行します。</span><span class="sxs-lookup"><span data-stu-id="0bb39-182">Then run the program by entering the `dotnet run` command.</span></span>

```csharp
Console.WriteLine($"[{DateTime.Now,-20:d}] Hour [{DateTime.Now,-10:HH}] [{1063.342,15:N2}] feet");
```

<span data-ttu-id="0bb39-183">出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="0bb39-183">The output looks something like the following:</span></span>

```console
[04/14/2018          ] Hour [16        ] [       1,063.34] feet
```

<span data-ttu-id="0bb39-184">文字列補間のクイックスタートはこれで終了です。</span><span class="sxs-lookup"><span data-stu-id="0bb39-184">You've completed the string interpolation quickstart.</span></span>

<span data-ttu-id="0bb39-185">[リスト コレクション](arrays-and-collections.md)のクイックスタートを、ご自身の開発環境でも使い続けることができます。</span><span class="sxs-lookup"><span data-stu-id="0bb39-185">You can continue with the [List collection](arrays-and-collections.md) quickstart in your own development environment.</span></span>

<span data-ttu-id="0bb39-186">詳細については、[文字列補間](../language-reference/tokens/interpolated.md)に関するトピックと「[C# における文字列補間](../tutorials/string-interpolation.md)」チュートリアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="0bb39-186">For more information, see the [String interpolation](../language-reference/tokens/interpolated.md) topic and the [String interpolation in C#](../tutorials/string-interpolation.md) tutorial.</span></span>
