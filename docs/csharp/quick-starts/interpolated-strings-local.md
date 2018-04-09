---
title: 挿入文字列のチュートリアル - C# ローカル クイックスタート
description: この挿入文字列に関するクイックスタートでは、C# コードを記述して、より大きな文字列に式の結果を含めます。
author: rpetrusha
ms.author: ronpet
ms.date: 01/11/2018
ms.topic: get-started-article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 1edd2b9f59d1933547c4152343f226a86ad90216
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/28/2018
---
# <a name="interpolated-strings"></a><span data-ttu-id="4f46c-103">挿入文字列</span><span class="sxs-lookup"><span data-stu-id="4f46c-103">Interpolated strings</span></span>

<span data-ttu-id="4f46c-104">このクイックスタートでは、C# で挿入文字列を使用して、単一の出力文字列に値を挿入する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="4f46c-104">This quickstart teaches you how to use interpolated strings in C# to insert values into a single ouput string.</span></span> <span data-ttu-id="4f46c-105">C# コードを記述し、コードをコンパイルおよび実行して結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="4f46c-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="4f46c-106">クイックスタートには、値を文字列に挿入し、それらの値の書式をさまざまな方法で設定する、一連のレッスンが含まれています。</span><span class="sxs-lookup"><span data-stu-id="4f46c-106">The quickstart contains a series of lessons that insert values into strings, and format those values in different ways.</span></span>

<span data-ttu-id="4f46c-107">このクイックスタートでは、開発用に使用できるマシンがあることを想定しています。</span><span class="sxs-lookup"><span data-stu-id="4f46c-107">This quickstart expects that you have a machine you can use for development.</span></span> <span data-ttu-id="4f46c-108">Mac、PC、または Linux 上でローカルの開発環境を設定する手順については、.NET の [10 分でわかる概要](https://www.microsoft.com/net/core)に関するトピックに記載されています。</span><span class="sxs-lookup"><span data-stu-id="4f46c-108">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="4f46c-109">使用するコマンドの概要を手短に確認するには、[ローカルでのクイックスタートの概要](local-environment.md)と詳細へのリンクをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4f46c-109">A quick overview of the commands you'll use is in the [introduction to the local quickstarts](local-environment.md) with links to more details.</span></span> 

## <a name="create-an-interpolated-string"></a><span data-ttu-id="4f46c-110">挿入文字列を作成する</span><span class="sxs-lookup"><span data-stu-id="4f46c-110">Create an interpolated string</span></span>

<span data-ttu-id="4f46c-111">**interpolated-quickstart** という名前のディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="4f46c-111">Create a directory named **interpolated-quickstart**.</span></span> <span data-ttu-id="4f46c-112">それを現在のディレクトリにして、コンソール ウィンドウから次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="4f46c-112">Make it the current directory and run the following command from a console window:</span></span>

```console
dotnet new console -n interpolated -o .
```

<span data-ttu-id="4f46c-113">このコマンドによって、現在のディレクトリに新しい .NET Core コンソール アプリケーションが作成されます。</span><span class="sxs-lookup"><span data-stu-id="4f46c-113">This command creates a new .NET Core console application in the current directory.</span></span>

<span data-ttu-id="4f46c-114">お好みのエディターで **Program.cs** を開き、`Console.WriteLine("Hello World!");` の行を次のコードで置き換えます。`<name>` は自分の名前に置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="4f46c-114">Open **Program.cs** in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code, where you replace `<name>` with your name:</span></span>

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```
<span data-ttu-id="4f46c-115">コンソール ウィンドウで「`dotnet run`」と入力し、このコードを試します。</span><span class="sxs-lookup"><span data-stu-id="4f46c-115">Try this code by typing `dotnet run` in your console window.</span></span> <span data-ttu-id="4f46c-116">プログラムを実行すると、あいさつ文に自分の名前を含む単一の文字列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4f46c-116">When you run the program, it displays a single string that includes your name in the greeting.</span></span> <span data-ttu-id="4f46c-117"><xref:System.Console.WriteLine%2A> メソッド呼び出しに含まれる文字列は、*挿入文字列*です。</span><span class="sxs-lookup"><span data-stu-id="4f46c-117">The string included in the <xref:System.Console.WriteLine%2A> method call is an *interpolated string*.</span></span> <span data-ttu-id="4f46c-118">これは、埋め込みコードを含む文字列から (*結果文字列*という) 単一の文字列を構築できる一種のテンプレートです。</span><span class="sxs-lookup"><span data-stu-id="4f46c-118">It's a kind of template that lets you construct a single string (called the *result string*) from a string that includes embedded code.</span></span> <span data-ttu-id="4f46c-119">挿入文字列は、文字列に値を挿入したり、文字列を (結合) 連結したりする場合に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="4f46c-119">Interpolated strings are particularly useful for inserting values into a string or concatenating (joining together) strings.</span></span> 
    
<span data-ttu-id="4f46c-120">この簡単な例には、すべての挿入文字列に含める必要がある次の 2 つの要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="4f46c-120">This simple example contains the two elements that every interpolated string must have:</span></span> 

- <span data-ttu-id="4f46c-121">始まりの引用符文字の前の `$` で始まる文字列リテラル。</span><span class="sxs-lookup"><span data-stu-id="4f46c-121">A string literal that begins with the `$` character before its opening quotation mark character.</span></span> <span data-ttu-id="4f46c-122">`$` シンボルと引用符文字の間にスペースを挿入することはできません </span><span class="sxs-lookup"><span data-stu-id="4f46c-122">There can't be any spaces between the `$` symbol and the quotation mark character.</span></span> <span data-ttu-id="4f46c-123">(スペースが含まれている場合の動作を確認したい場合は、`$` 文字の後にスペースを挿入し、ファイルを保存してから、コンソール ウィンドウで「`dotnet run`」と入力してプログラムを再実行します。</span><span class="sxs-lookup"><span data-stu-id="4f46c-123">(If you'd like to see what happens if you include one, insert a space after the `$` character, save the file, and run the program again by typing `dotnet run` in the console window.</span></span> <span data-ttu-id="4f46c-124">C# コンパイラには、"エラー CS1056: 予期しない文字 '$' です" というエラー メッセージが表示されます)。</span><span class="sxs-lookup"><span data-stu-id="4f46c-124">The C# compiler displays an error message, "error CS1056: Unexpected character '$'".)</span></span> 

- <span data-ttu-id="4f46c-125">1 つ以上の*挿入式*。</span><span class="sxs-lookup"><span data-stu-id="4f46c-125">One or more *interpolated expressions*.</span></span> <span data-ttu-id="4f46c-126">挿入式は、始めかっこと終わりかっこ (`{` と `}`) で示されます。</span><span class="sxs-lookup"><span data-stu-id="4f46c-126">An interpolated expression is indicated by an opening and closing brace (`{` and `}`).</span></span> <span data-ttu-id="4f46c-127">かっこ内に (`null` を含む) 値を返す C# 式を配置できます。</span><span class="sxs-lookup"><span data-stu-id="4f46c-127">You can put any C# expression that returns a value (including `null`) inside the braces.</span></span> 

<span data-ttu-id="4f46c-128">その他のいくつかのデータ型を持つ挿入文字列の例をさらにいくつか試してみましょう。</span><span class="sxs-lookup"><span data-stu-id="4f46c-128">Let's try a few more interpolated string examples with some other data types.</span></span>
    
## <a name="include-different-data-types"></a><span data-ttu-id="4f46c-129">さまざまなデータ型を含める</span><span class="sxs-lookup"><span data-stu-id="4f46c-129">Include different data types</span></span>

<span data-ttu-id="4f46c-130">前のセクションでは、挿入文字列を使用して、1 つの文字列内に別の文字列を挿入しましたが、</span><span class="sxs-lookup"><span data-stu-id="4f46c-130">In the previous section, you used an interpolated string to insert one string inside of another.</span></span> <span data-ttu-id="4f46c-131">挿入文字列式を任意のデータ型にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="4f46c-131">An interpolated string expression can be any data type, though.</span></span> <span data-ttu-id="4f46c-132">複数のデータ型の値を持つ挿入文字列を試してみましょう。</span><span class="sxs-lookup"><span data-stu-id="4f46c-132">Let's try an interpolated string that has values of multiple data types.</span></span> 
    
<span data-ttu-id="4f46c-133">次の例には、`Vegetable` オブジェクト、`Unit` 列挙型のメンバー、<xref:System.DateTime> 値、<xref:System.Decimal> 値を持つ挿入式が含まれています。</span><span class="sxs-lookup"><span data-stu-id="4f46c-133">The following example includes interpolated expressions with a `Vegetable` object, a member of the `Unit` enumeration, a <xref:System.DateTime> value, and a <xref:System.Decimal> value.</span></span> <span data-ttu-id="4f46c-134">エディターのすべての C# コードを以下のコードに置き換えてから、`console run` コマンドを使用して実行します。</span><span class="sxs-lookup"><span data-stu-id="4f46c-134">Replace all of the C# code in your editor with the following code, and then use the `console run` command to run it:</span></span>

```csharp
using System;

public class Vegetable
{
   public Vegetable(string name) => Name = name;
   
   public string Name { get; }
   
   public override string ToString() => Name;
}

public class Example
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
    
<span data-ttu-id="4f46c-135">2 つ目の挿入式には、コンソールに表示される結果文字列の `item` オブジェクトが含まれており、この場合、"eggplant" という文字列が結果文字列に挿入されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4f46c-135">Note that the second interpolated expression includes the `item` object in the result string that's displayed to the console, and in this case the string "eggplant" is inserted into the result string.</span></span> <span data-ttu-id="4f46c-136">これは、挿入式の型が文字列でない場合、C# コンパイラでは次の処理が行われるためです。</span><span class="sxs-lookup"><span data-stu-id="4f46c-136">That's because, when the type of an interpolated expression is not a string, the C# compiler does the following:</span></span>

- <span data-ttu-id="4f46c-137">挿入式が `null` の場合、挿入式は空の文字列 (""、または <xref:System.String.Empty?displayProperty=nameWithType>) を返します。</span><span class="sxs-lookup"><span data-stu-id="4f46c-137">If the interpolated expression is `null`, the interpolated expression returns an empty string ("", or <xref:System.String.Empty?displayProperty=nameWithType>).</span></span>

- <span data-ttu-id="4f46c-138">挿入式が `null` でない場合、挿入式の型の `ToString` メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="4f46c-138">If the interpolated expression is not `null`, the `ToString` method of the type of the interpolated expression is called.</span></span> <span data-ttu-id="4f46c-139">コメント シンボル (`//`) を前に配置して、例の `Vegetable.ToString` メソッドの定義をコメント アウトすることで、これをテストできます。</span><span class="sxs-lookup"><span data-stu-id="4f46c-139">You can test this by commenting out the definition of the `Vegetable.ToString` method in the example by putting a comment symbol (`//`) in front of it.</span></span> <span data-ttu-id="4f46c-140">出力では、"eggplant" という文字列が "Vegetable" という型名に置き換えられます。これは、<xref:System.Object.ToString?displayProperty=nameWithType> メソッドの既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="4f46c-140">In the output, the string "eggplant" is replaced by the type name, "Vegetable", which is the default behavior of the <xref:System.Object.ToString?displayProperty=nameWithType> method.</span></span>   

<span data-ttu-id="4f46c-141">この例の出力では、日付の精度が高すぎ (エッグプラントの価格が 2 つ目の値により変化しない)、価格の値は通貨の単位を示していません。</span><span class="sxs-lookup"><span data-stu-id="4f46c-141">In the output from this example, the date is too precise (the price of eggplant does not vary by the second), and the price value doesn't indicate a unit of currency.</span></span> <span data-ttu-id="4f46c-142">次のセクションでは、挿入式によって返される文字列の書式を制御することで、こうした問題を修正する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4f46c-142">In the next section, you'll learn how to fix those issues by controlling the format of strings returned by interpolated expressions.</span></span>

## <a name="control-the-formatting-of-interpolated-expressions"></a><span data-ttu-id="4f46c-143">挿入式の書式設定を制御する</span><span class="sxs-lookup"><span data-stu-id="4f46c-143">Control the formatting of interpolated expressions</span></span>

<span data-ttu-id="4f46c-144">前のセクションでは、適切に書式設定されていない 2 つの文字列が結果文字列に挿入されました。</span><span class="sxs-lookup"><span data-stu-id="4f46c-144">In the previous section, two poorly formatted strings were inserted into the result string.</span></span> <span data-ttu-id="4f46c-145">1 つは、日付のみが適切な日時の値でした。</span><span class="sxs-lookup"><span data-stu-id="4f46c-145">One was a date and time value for which only the date was appropriate.</span></span> <span data-ttu-id="4f46c-146">もう 1 つは、通貨単位を示さない価格でした。</span><span class="sxs-lookup"><span data-stu-id="4f46c-146">The second was a price that did not indicate its unit of currency.</span></span> <span data-ttu-id="4f46c-147">両方の問題には簡単に対処することができます。</span><span class="sxs-lookup"><span data-stu-id="4f46c-147">Both issues are easy to address.</span></span> <span data-ttu-id="4f46c-148">挿入式に、特定の型の書式設定を制御する*書式指定文字列*を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="4f46c-148">Interpolated expressions can include *format strings* that control the formatting of particular types.</span></span> <span data-ttu-id="4f46c-149">前の例の `Console.WriteLine` 呼び出しを変更し、次の行に示すように、日付と価格のフィールドの書式指定子を含めます。</span><span class="sxs-lookup"><span data-stu-id="4f46c-149">Modify the call to `Console.WriteLine` from the previous example to include the format specifier for the date and price fields as shown in the following line:</span></span>

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```
    
<span data-ttu-id="4f46c-150">コロンと書式指定文字列を持つ挿入式に従って、書式指定文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="4f46c-150">You specify a format string by following the interpolated expression with a colon and the format string.</span></span> <span data-ttu-id="4f46c-151">"d" は、短い日付形式を表す[標準の日時書式設定文字列](../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier)です。</span><span class="sxs-lookup"><span data-stu-id="4f46c-151">"d" is a [standard date and time format string](../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) that represents the short date format.</span></span> <span data-ttu-id="4f46c-152">"C2" は、小数点以下が 2 桁の通貨値として数値を表す[標準の数値書式指定文字列](../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier)です。</span><span class="sxs-lookup"><span data-stu-id="4f46c-152">"C2" is a  [standard numeric format string](../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) that represents a number as a currency value with two digits after the decimal point.</span></span>

<span data-ttu-id="4f46c-153">.NET Standard ライブラリの多くの型で、定義済みの書式指定文字列セットがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="4f46c-153">A number of types in the .NET Standard libraries support a predefined set of format strings.</span></span> <span data-ttu-id="4f46c-154">これらには、数値型と日時型がすべて含まれます。</span><span class="sxs-lookup"><span data-stu-id="4f46c-154">These include all the numeric types and the date and time types.</span></span> <span data-ttu-id="4f46c-155">書式指定文字列をサポートする型の完全なリストについては、「[.Net 型の書式設定](../../standard/base-types/formatting-types.md)」記事の「[.NET クラス ライブラリの型および書式指定文字列](../../standard/base-types/formatting-types.md#stringRef)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f46c-155">For a complete list of types that support format strings, see [Format Strings and .NET Class Library Types](../../standard/base-types/formatting-types.md#stringRef) in the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) article.</span></span> <span data-ttu-id="4f46c-156">どの型でも書式指定文字列セットをサポートすることができ、既存の型のカスタム書式指定を提供するカスタム書式指定拡張機能を開発することもできます。</span><span class="sxs-lookup"><span data-stu-id="4f46c-156">Any type can support a set of format strings, and you can also develop custom formatting extensions that provide custom formatting for existing types.</span></span> <span data-ttu-id="4f46c-157"><xref:System.ICustomFormatter> 実装を提供することによるカスタム書式指定については、「[.Net 型の書式設定](../../standard/base-types/formatting-types.md)」記事の「[ICustomFormatter を使用したカスタム書式設定](../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f46c-157">For information on custom formatting by providing an <xref:System.ICustomFormatter> implementation, see [Custom Formatting with ICustomFormatter](../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter) in the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) article.</span></span>

<span data-ttu-id="4f46c-158">テキスト エディターで書式指定文字列を変更してみて、変更するたびにプログラムを再実行し、変更が日時と数値の書式設定にどのように影響するかを確認します。</span><span class="sxs-lookup"><span data-stu-id="4f46c-158">Try modifying the format strings in your text editor and, each time you make a change, rerun the program to see how the changes affect the formatting of the date and time and the numeric value.</span></span> <span data-ttu-id="4f46c-159">`{date:d}` の "d" を "t" (短い時刻形式を表示する)、"y" (年と月を表示する)、"yyyy" (4 桁の数字として年を表示する) に変更します。</span><span class="sxs-lookup"><span data-stu-id="4f46c-159">Change the "d" in `{date:d}` to "t" (to display the short time format), "y" (to display the year and month), and "yyyy" (to display the year as a four-digit number).</span></span> <span data-ttu-id="4f46c-160">`{price:C2}` "C2" を "e" (指数表記の場合) と "F3" (小数点以下が 3 桁の数値の場合) に変更します。</span><span class="sxs-lookup"><span data-stu-id="4f46c-160">Change the "C2" in `{price:C2}` to "e" (for exponential notation) and "F3" (for a numeric value with three digits after the decimal point).</span></span>

<span data-ttu-id="4f46c-161">書式設定を制御するだけでなく、挿入式によって返される文字列のフィールドの幅と配置を制御することもできます。</span><span class="sxs-lookup"><span data-stu-id="4f46c-161">In addition to controlling formatting, you can also control the field width and alignment of the strings returned by an interpolated expression.</span></span> <span data-ttu-id="4f46c-162">次のセクションでは、この方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="4f46c-162">In the next section, you'll learn how to do this.</span></span>

## <a name="control-the-field-width-and-alignment-of-interpolated-expressions"></a><span data-ttu-id="4f46c-163">挿入式のフィールドの幅と配置を制御する</span><span class="sxs-lookup"><span data-stu-id="4f46c-163">Control the field width and alignment of interpolated expressions</span></span>

<span data-ttu-id="4f46c-164">通常、挿入式によって返される文字列が結果文字列に含まれている場合、先頭スペースも末尾スペースもありません。</span><span class="sxs-lookup"><span data-stu-id="4f46c-164">Ordinarily, when the string returned by an interpolated expression is included in a result string, it has no leading or trailing spaces.</span></span> <span data-ttu-id="4f46c-165">特にデータ セットを処理する場合、挿入式ではフィールドの幅とその配置を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="4f46c-165">Particularly for instances in which you are working with a set of data, interpolated expressions let you specify a field width and its alignment.</span></span> <span data-ttu-id="4f46c-166">そのためには、テキスト エディターのすべてのコードを次のコードに置き換えてから、「`console run`」と入力してプログラムを実行します。</span><span class="sxs-lookup"><span data-stu-id="4f46c-166">To see this, replace all the code in your text editor with the following code, then type `console run` to execute the program:</span></span>
    
```csharp
using System;
using System.Collections.Generic;

public class Example
{
   public static void Main()
   {
      var titles = new Dictionary<string, string>();
      titles.Add("Doyle, Arthur Conan", "Hound of the Baskervilles, The");
      titles.Add("London, Jack", "Call of the Wild, The");
      titles.Add("Shakespeare, William", "Tempest, The");

      Console.WriteLine("Author and Title List");
      Console.WriteLine($"\n{"Author",-25}    {"Title",30}\n");
      foreach (var title in titles)
         Console.WriteLine($"{title.Key,-25}     {title.Value,30}");
   }
}
```
    
<span data-ttu-id="4f46c-167">作成者の名前は左揃えになり、書き込まれたタイトルは右揃えになります。</span><span class="sxs-lookup"><span data-stu-id="4f46c-167">The names of authors are left-aligned, and the titles they wrote are right-aligned.</span></span> <span data-ttu-id="4f46c-168">式の後にコンマ (",") を追加し、フィールドの幅を指定して、配置を指定します。</span><span class="sxs-lookup"><span data-stu-id="4f46c-168">You specify the alignment by adding a comma (",") after the expression and designating the field width.</span></span> <span data-ttu-id="4f46c-169">次のようにフィールドの幅が正数の場合、フィールドは右揃えになります。</span><span class="sxs-lookup"><span data-stu-id="4f46c-169">If the field width is a positive number, the field is right-aligned:</span></span>

```text
{expression, width}
```

<span data-ttu-id="4f46c-170">次のようにフィールドの幅が負数の場合、フィールドは左揃えになります。</span><span class="sxs-lookup"><span data-stu-id="4f46c-170">If the field width is a negative number, the field is left-aligned:</span></span>

```text
{expression, -width}
```

<span data-ttu-id="4f46c-171">`{"Author",-25}` と `{title.Key,-25}` の挿入式から負号を削除してみて、次のコードのように、例を再実行します。</span><span class="sxs-lookup"><span data-stu-id="4f46c-171">Try removing the negative signs from the `{"Author",-25}` and `{title.Key,-25}` interpolated expressions and run the example again, as the following code does:</span></span>

```csharp
Console.WriteLine($"\n{"Author",25}    {"Title",30}\n");
foreach (var title in titles)
   Console.WriteLine($"{title.Key,25}     {title.Value,30}");
```

<span data-ttu-id="4f46c-172">この場合、作成者情報は右揃えになります。</span><span class="sxs-lookup"><span data-stu-id="4f46c-172">This time, the author information is right-aligned.</span></span>

<span data-ttu-id="4f46c-173">フィールドの幅と書式指定文字列を組み合わせて単一の挿入式にまとめることができます。</span><span class="sxs-lookup"><span data-stu-id="4f46c-173">You can combine a field width and a format string in a single interpolated expression.</span></span> <span data-ttu-id="4f46c-174">最初にフィールドの幅が配置され、その後にコロンと書式指定文字列が続きます。</span><span class="sxs-lookup"><span data-stu-id="4f46c-174">The field width comes first, followed by a colon and the format string.</span></span> <span data-ttu-id="4f46c-175">`Main` メソッド内のすべてのコードを次のコードに置き換えると、フィールド幅が定義された 3 つの書式指定された文字列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4f46c-175">Replace all of the code inside the `Main` method with the following code, which displays three formatted strings with defined field widths.</span></span> <span data-ttu-id="4f46c-176">次に、`dotnet run` コマンドを入力してプログラムを実行します。</span><span class="sxs-lookup"><span data-stu-id="4f46c-176">Then run the program by entering the `dotnet run` command.</span></span>

```csharp
Console.WriteLine($"{DateTime.Now,-20:d} Hour {DateTime.Now,-10:HH} {1063.342,15:N2} feet");
```
<span data-ttu-id="4f46c-177">出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="4f46c-177">The output looks something like the following:</span></span>

```console
1/11/2018            Hour 09                1,063.34 feet
```

<span data-ttu-id="4f46c-178">挿入文字列のクイックスタートはこれで終了です。</span><span class="sxs-lookup"><span data-stu-id="4f46c-178">You've completed the interpolated strings quickstart.</span></span> 
    
<span data-ttu-id="4f46c-179">続けて独自の開発環境で[配列とコレクション](arrays-and-collections.md)のクイックスタートに進むことができます。</span><span class="sxs-lookup"><span data-stu-id="4f46c-179">You can continue with the [Arrays and collections](arrays-and-collections.md) quickstart in your own development environment.</span></span>

<span data-ttu-id="4f46c-180">挿入文字列の詳細については、C# リファレンスの「[文字列補間](../language-reference/tokens/interpolated.md)」トピックで学習できます。</span><span class="sxs-lookup"><span data-stu-id="4f46c-180">You can learn more about interpolated strings in the [String interpolation](../language-reference/tokens/interpolated.md) topic in the C# Reference.</span></span>
