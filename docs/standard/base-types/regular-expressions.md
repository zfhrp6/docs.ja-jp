---
title: ".NET の正規表現"
description: ".NET の正規表現"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: d1a640cf-09ca-48f7-800c-a627a6d549c9
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: ac26821819b22aa3ea47e6945bb5c8575dcd9807
ms.contentlocale: ja-jp
ms.lasthandoff: 03/02/2017

---

# <a name="regular-expressions-in-net"></a><span data-ttu-id="bb630-104">.NET の正規表現</span><span class="sxs-lookup"><span data-stu-id="bb630-104">Regular expressions in .NET</span></span>

<span data-ttu-id="bb630-105">正規表現を使用すると、強力、柔軟、そして効率的な方法でテキストを処理できます。</span><span class="sxs-lookup"><span data-stu-id="bb630-105">Regular expressions provide a powerful, flexible, and efficient method for processing text.</span></span> <span data-ttu-id="bb630-106">正規表現の広範なパターン一致表記法を使用することで、大量のテキストをすばやく解析して特定の文字パターンを検索したり、決められたパターン (電子メール アドレスなど) と照らしてテキストを検証したりできるほか、テキストの部分文字列を抽出、編集、置換、または削除したり、抽出した文字列をコレクションに追加してレポートを生成したりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="bb630-106">The extensive pattern-matching notation of regular expressions enables you to quickly parse large amounts of text to find specific character patterns; to validate text to ensure that it matches a predefined pattern (such as an e-mail address); to extract, edit, replace, or delete text substrings; and to add the extracted strings to a collection in order to generate a report.</span></span> <span data-ttu-id="bb630-107">文字列処理や大量のテキストを解析する多くのアプリケーションにとって、正規表現は欠くことのできないツールです。</span><span class="sxs-lookup"><span data-stu-id="bb630-107">For many applications that deal with strings or that parse large blocks of text, regular expressions are an indispensable tool.</span></span>

## <a name="how-regular-expressions-work"></a><span data-ttu-id="bb630-108">正規表現の動作</span><span class="sxs-lookup"><span data-stu-id="bb630-108">How Regular Expressions Work</span></span>

<span data-ttu-id="bb630-109">正規表現を使ったテキスト処理の最も重要な部分は、.NET の [System.Text.RegularExpressions.Regex](xref:System.Text.RegularExpressions.Regex) オブジェクトによって表される正規表現エンジンです。</span><span class="sxs-lookup"><span data-stu-id="bb630-109">The centerpiece of text processing with regular expressions is the regular expression engine, which is represented by the [System.Text.RegularExpressions.Regex](xref:System.Text.RegularExpressions.Regex) object in .NET.</span></span> <span data-ttu-id="bb630-110">正規表現を使ったテキスト処理では、正規表現エンジンに対し、最低でも次の&2; つの情報を与える必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb630-110">At a minimum, processing text using regular expressions requires that the regular expression engine be provided with the following two items of information:</span></span>

* <span data-ttu-id="bb630-111">テキストを識別する正規表現パターン。</span><span class="sxs-lookup"><span data-stu-id="bb630-111">The regular expression pattern to identify in the text.</span></span> 
  
  <span data-ttu-id="bb630-112">.NET では、正規表現のパターンが特殊な構文または言語で定義されます。この構文または言語には、Perl 5 の正規表現と互換性があるほか、右から左への一致処理など、いくつかの機能が追加されています。</span><span class="sxs-lookup"><span data-stu-id="bb630-112">In .NET, regular expression patterns are defined by a special syntax or language, which is compatible with Perl 5 regular expressions and adds some additional features such as right-to-left matching.</span></span> <span data-ttu-id="bb630-113">詳細については、「[正規表現言語 - クイック リファレンス](quick-ref.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bb630-113">For more information, see [Regular Expression Language - Quick Reference](quick-ref.md).</span></span>
  
* <span data-ttu-id="bb630-114">正規表現パターンの解析対象となるテキスト。</span><span class="sxs-lookup"><span data-stu-id="bb630-114">The text to parse for the regular expression pattern.</span></span>

<span data-ttu-id="bb630-115">[Regex](xref:System.Text.RegularExpressions.Regex) クラスのメソッドを使用すると、次のような処理を実行できます。</span><span class="sxs-lookup"><span data-stu-id="bb630-115">The methods of the [Regex](xref:System.Text.RegularExpressions.Regex) class let you perform the following operations:</span></span>

* <span data-ttu-id="bb630-116">入力されたテキストに特定の正規表現パターンが出現するかどうかを調べるには、[Regex.IsMatch](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String)) メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="bb630-116">Determine whether the regular expression pattern occurs in the input text by calling the [Regex.IsMatch](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String)) method.</span></span> <span data-ttu-id="bb630-117">テキストを検証するために [IsMatch](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String)) メソッドを使用する例については、「[方法: 文字列が有効な電子メール形式であるかどうかを検証する](verify-format.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bb630-117">For an example that uses the [IsMatch](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String)) method for validating text, see [How to: Verify that Strings Are in Valid Email Format](verify-format.md).</span></span>

* <span data-ttu-id="bb630-118">正規表現パターンと一致したテキストを&1; つまたはすべて取得するには、[Regex.Match](xref:System.Text.RegularExpressions.Regex.Match(System.String)) メソッドまたは [Regex.Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String)) メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="bb630-118">Retrieve one or all occurrences of text that matches the regular expression pattern by calling the [Regex.Match](xref:System.Text.RegularExpressions.Regex.Match(System.String)) or [Regex.Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String)) method.</span></span> <span data-ttu-id="bb630-119">前者は、一致したテキストの情報を保持する [System.Text.RegularExpressions.Match](xref:System.Text.RegularExpressions.Match) オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="bb630-119">The former method returns a [System.Text.RegularExpressions.Match](xref:System.Text.RegularExpressions.Match) object that provides information about the matching text.</span></span> <span data-ttu-id="bb630-120">後者は、解析対象のテキストに見つかった各一致につき&1; つの [System.Text.RegularExpressions.Match](xref:System.Text.RegularExpressions.Match) オブジェクトを含む [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="bb630-120">The latter returns a [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) object that contains one [System.Text.RegularExpressions.Match](xref:System.Text.RegularExpressions.Match) object for each match found in the parsed text.</span></span> 

* <span data-ttu-id="bb630-121">正規表現パターンと一致したテキストを置換するには、[Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)) メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="bb630-121">Replace text that matches the regular expression pattern by calling the [Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)) method.</span></span> <span data-ttu-id="bb630-122">[Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)) メソッドを使用して日付形式を変更したり文字列から無効な文字を削除したりする例については、「[方法: 文字列から無効な文字を取り除く](strip-characters.md)」および「[正規表現の例: 日付形式の変更](changing-formats.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bb630-122">For examples that use the [Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)) method to change date formats and remove invalid characters from a string, see [How to: Strip Invalid Characters from a String](strip-characters.md) and [Regular Expression Example: Changing Date Formats](changing-formats.md).</span></span>

<span data-ttu-id="bb630-123">正規表現のオブジェクト モデルの概要については、「[正規表現のオブジェクト モデル](object-model.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bb630-123">For an overview of the regular expression object model, see [The Regular Expression Object Model](object-model.md).</span></span>

<span data-ttu-id="bb630-124">正規表現言語の詳細については、「[正規表現言語 - クイック リファレンス](quick-ref.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bb630-124">For more information about the regular expression language, see [Regular Expression Language - Quick Reference](quick-ref.md).</span></span>

## <a name="regular-expression-examples"></a><span data-ttu-id="bb630-125">正規表現の例</span><span class="sxs-lookup"><span data-stu-id="bb630-125">Regular Expression Examples</span></span>

<span data-ttu-id="bb630-126">[String](xref:System.String) クラスには、より大きな文字列内のリテラル文字列を検索する際に使用できる文字列の検索メソッドと置換メソッドが数多く含まれています。</span><span class="sxs-lookup"><span data-stu-id="bb630-126">The [String](xref:System.String) class includes a number of string search and replacement methods that you can use when you want to locate literal strings in a larger string.</span></span> <span data-ttu-id="bb630-127">正規表現は、次の例に示すように、文字列内の部分文字列のいずれかを検索する場合、または文字列内のパターンを識別する場合に最も役立ちます。</span><span class="sxs-lookup"><span data-stu-id="bb630-127">Regular expressions are most useful either when you want to locate one of several substrings in a larger string, or when you want to identify patterns in a string, as the following examples illustrate.</span></span> 

### <a name="example-1-replacing-substrings"></a><span data-ttu-id="bb630-128">例 1: 部分文字列の置換</span><span class="sxs-lookup"><span data-stu-id="bb630-128">Example 1: Replacing Substrings</span></span>

<span data-ttu-id="bb630-129">氏名に敬称 (Mr.、Mrs.、Miss、または Ms.) が付いている場合がある名前が、宛先リストに含まれるとします。</span><span class="sxs-lookup"><span data-stu-id="bb630-129">Assume that a mailing list contains names that sometimes include a title (Mr., Mrs., Miss, or Ms.) along with a first and last name.</span></span> <span data-ttu-id="bb630-130">そのリストから封筒のラベルを生成する場合に敬称が含まれないようにするには、次の例に示すように、正規表現を使用して敬称を削除します。</span><span class="sxs-lookup"><span data-stu-id="bb630-130">If you do not want to include the titles when you generate envelope labels from the list, you can use a regular expression to remove the titles, as the following example illustrates.</span></span>

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = "(Mr\\.? |Mrs\\.? |Miss |Ms\\.? )";
      string[] names = { "Mr. Henry Hunt", "Ms. Sara Samuels", 
                         "Abraham Adams", "Ms. Nicole Norris" };
      foreach (string name in names)
         Console.WriteLine(Regex.Replace(name, pattern, String.Empty));
   }
}
// The example displays the following output:
//    Henry Hunt
//    Sara Samuels
//    Abraham Adams
//    Nicole Norris
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "(Mr\.? |Mrs\.? |Miss |Ms\.? )"
      Dim names() As String = { "Mr. Henry Hunt", "Ms. Sara Samuels", _
                                "Abraham Adams", "Ms. Nicole Norris" }
      For Each name As String In names
         Console.WriteLine(Regex.Replace(name, pattern, String.Empty))
      Next                                
   End Sub
End Module
' The example displays the following output:
'    Henry Hunt
'    Sara Samuels
'    Abraham Adams
'    Nicole Norris
```

<span data-ttu-id="bb630-131">正規表現パターン `(Mr\.? |Mrs\.? |Miss |Ms\.? )` は、"Mr "、"Mr. "、"Mrs "、"Mrs. "、"Miss "、"Ms"、または "Ms. " の出現と一致します。</span><span class="sxs-lookup"><span data-stu-id="bb630-131">The regular expression pattern `(Mr\.? |Mrs\.? |Miss |Ms\.? )` matches any occurrence of "Mr ", "Mr. ", "Mrs ", "Mrs. ", "Miss ", "Ms or "Ms. ".</span></span> <span data-ttu-id="bb630-132">[Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)) メソッドを呼び出すと、一致する文字列が [String.Empty](xref:System.String.Empty) に置き換えられます。つまり、元の文字列から削除されます。</span><span class="sxs-lookup"><span data-stu-id="bb630-132">The call to the [Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)) method replaces the matched string with [String.Empty](xref:System.String.Empty); in other words, it removes it from the original string.</span></span>

### <a name="example-2-identifying-duplicated-words"></a><span data-ttu-id="bb630-133">例 2: 重複する単語の識別</span><span class="sxs-lookup"><span data-stu-id="bb630-133">Example 2: Identifying Duplicated Words</span></span>

<span data-ttu-id="bb630-134">記述者が単語を誤って重複入力するというエラーがよくあります。</span><span class="sxs-lookup"><span data-stu-id="bb630-134">Accidentally duplicating words is a common error that writers make.</span></span> <span data-ttu-id="bb630-135">次の例に示すように、正規表現を使用して重複する単語を識別できます。</span><span class="sxs-lookup"><span data-stu-id="bb630-135">A regular expression can be used to identify duplicated words, as the following example shows.</span></span>

```csharp
using System;
using System.Text.RegularExpressions;

public class Class1
{
   public static void Main()
   {
      string pattern = @"\b(\w+?)\s\1\b";
      string input = "This this is a nice day. What about this? This tastes good. I saw a a dog.";
      foreach (Match match in Regex.Matches(input, pattern, RegexOptions.IgnoreCase))
         Console.WriteLine("{0} (duplicates '{1}') at position {2}", 
                           match.Value, match.Groups[1].Value, match.Index);
   }
}
// The example displays the following output:
//       This this (duplicates 'This)' at position 0
//       a a (duplicates 'a)' at position 66
```

```vb
Imports System.Text.RegularExpressions

Module modMain
   Public Sub Main()
      Dim pattern As String = "\b(\w+?)\s\1\b"
      Dim input As String = "This this is a nice day. What about this? This tastes good. I saw a a dog."
      For Each match As Match In Regex.Matches(input, pattern, RegexOptions.IgnoreCase)
         Console.WriteLine("{0} (duplicates '{1}') at position {2}", _
                           match.Value, match.Groups(1).Value, match.Index)
      Next
   End Sub
End Module
' The example displays the following output:
'       This this (duplicates 'This)' at position 0
'       a a (duplicates 'a)' at position 66
```

<span data-ttu-id="bb630-136">正規表現パターン `\b(\w+?)\s\1\b` は、次のように解釈できます。</span><span class="sxs-lookup"><span data-stu-id="bb630-136">The regular expression pattern `\b(\w+?)\s\1\b` can be interpreted as follows:</span></span>

<span data-ttu-id="bb630-137">構文</span><span class="sxs-lookup"><span data-stu-id="bb630-137">Syntax</span></span> | <span data-ttu-id="bb630-138">説明</span><span class="sxs-lookup"><span data-stu-id="bb630-138">Meaning</span></span>
------ | -------
`\b` | <span data-ttu-id="bb630-139">ワード境界から開始します。</span><span class="sxs-lookup"><span data-stu-id="bb630-139">Start at a word boundary.</span></span>
`(\w+?)` | <span data-ttu-id="bb630-140">1 つ以上 (ただし、できるだけ少ない文字数) の単語文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="bb630-140">Match one or more word characters, but as few characters as possible.</span></span> <span data-ttu-id="bb630-141">同時に、`\1` というグループを形成します。</span><span class="sxs-lookup"><span data-stu-id="bb630-141">Together, they form a group that can be referred to as `\1`.</span></span>
`\s` | <span data-ttu-id="bb630-142">空白文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="bb630-142">Match a white-space character.</span></span>
`\1` | <span data-ttu-id="bb630-143">`\1` という名前のグループと等しい部分文字列と一致します。</span><span class="sxs-lookup"><span data-stu-id="bb630-143">Match the substring that is equal to the group named `\1`.</span></span>
`\b` | <span data-ttu-id="bb630-144">ワード境界に一致します。</span><span class="sxs-lookup"><span data-stu-id="bb630-144">Match a word boundary.</span></span>

<span data-ttu-id="bb630-145">[Regex.Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) メソッドは、正規表現オプションを [RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase) に設定して呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="bb630-145">The [Regex.Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) method is called with regular expression options set to [RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase).</span></span> <span data-ttu-id="bb630-146">したがって、照合操作では大文字と小文字が区別されず、この例では部分文字列 "This this" が重複として識別されます。</span><span class="sxs-lookup"><span data-stu-id="bb630-146">Therefore, the match operation is case-insensitive, and the example identifies the substring "This this" as a duplication.</span></span>

<span data-ttu-id="bb630-147">入力文字列には部分文字列 "this?</span><span class="sxs-lookup"><span data-stu-id="bb630-147">Note that the input string includes the substring "this?</span></span> <span data-ttu-id="bb630-148">This" が含まれています。</span><span class="sxs-lookup"><span data-stu-id="bb630-148">This".</span></span> <span data-ttu-id="bb630-149">ただし、句読点が介在するので、重複として識別されません。</span><span class="sxs-lookup"><span data-stu-id="bb630-149">However, because of the intervening punctuation mark, it is not identified as a duplication.</span></span>

### <a name="example-3-dynamically-building-a-culture-sensitive-regular-expression"></a><span data-ttu-id="bb630-150">例 3: カルチャに依存した正規表現の動的な構築</span><span class="sxs-lookup"><span data-stu-id="bb630-150">Example 3: Dynamically Building a Culture-Sensitive Regular Expression</span></span>

<span data-ttu-id="bb630-151">ここでは、正規表現による強力なテキスト処理と、.NET の柔軟なグローバリゼーション機能を組み合わせて使用する例を紹介します。</span><span class="sxs-lookup"><span data-stu-id="bb630-151">The following example illustrates the power of regular expressions combined with the flexibility offered by .NET's globalization features.</span></span> <span data-ttu-id="bb630-152">この例では、システムの現在のカルチャで用いられている通貨値の形式を調べるために、[NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) オブジェクトが使用されています。</span><span class="sxs-lookup"><span data-stu-id="bb630-152">It uses the [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) object to determine the format of currency values in the system's current culture.</span></span> <span data-ttu-id="bb630-153">さらに、その情報を基に、テキストから通貨値を抽出する正規表現を動的に構築します。</span><span class="sxs-lookup"><span data-stu-id="bb630-153">It then uses that information to dynamically construct a regular expression that extracts currency values from the text.</span></span> <span data-ttu-id="bb630-154">検出された一致ごとに、数値文字列のみを含んだサブグループを抽出し、[Decimal](xref:System.Decimal) 値に変換して、通算の合計を計算します。</span><span class="sxs-lookup"><span data-stu-id="bb630-154">For each match, it extracts the subgroup that contains the numeric string only, converts it to a [Decimal](xref:System.Decimal) value, and calculates a running total.</span></span> 

```csharp
using System;
using System.Collections.Generic;
using System.Globalization;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      // Define text to be parsed.
      string input = "Office expenses on 2/13/2008:\n" + 
                     "Paper (500 sheets)                      $3.95\n" + 
                     "Pencils (box of 10)                     $1.00\n" + 
                     "Pens (box of 10)                        $4.49\n" + 
                     "Erasers                                 $2.19\n" + 
                     "Ink jet printer                        $69.95\n\n" + 
                     "Total Expenses                        $ 81.58\n"; 

      // Get current culture's NumberFormatInfo object.
      NumberFormatInfo nfi = CultureInfo.CurrentCulture.NumberFormat;
      // Assign needed property values to variables.
      string currencySymbol = nfi.CurrencySymbol;
      bool symbolPrecedesIfPositive = nfi.CurrencyPositivePattern % 2 == 0;
      string groupSeparator = nfi.CurrencyGroupSeparator;
      string decimalSeparator = nfi.CurrencyDecimalSeparator;

      // Form regular expression pattern.
      string pattern = Regex.Escape( symbolPrecedesIfPositive ? currencySymbol : "") + 
                       @"\s*[-+]?" + "([0-9]{0,3}(" + groupSeparator + "[0-9]{3})*(" + 
                       Regex.Escape(decimalSeparator) + "[0-9]+)?)" + 
                       (! symbolPrecedesIfPositive ? currencySymbol : ""); 
      Console.WriteLine( "The regular expression pattern is:");
      Console.WriteLine("   " + pattern);      

      // Get text that matches regular expression pattern.
      MatchCollection matches = Regex.Matches(input, pattern, 
                                              RegexOptions.IgnorePatternWhitespace);               
      Console.WriteLine("Found {0} matches.", matches.Count); 

      // Get numeric string, convert it to a value, and add it to List object.
      List<decimal> expenses = new List<Decimal>();

      foreach (Match match in matches)
         expenses.Add(Decimal.Parse(match.Groups[1].Value));      

      // Determine whether total is present and if present, whether it is correct.
      decimal total = 0;
      foreach (decimal value in expenses)
         total += value;

      if (total / 2 == expenses[expenses.Count - 1]) 
         Console.WriteLine("The expenses total {0:C2}.", expenses[expenses.Count - 1]);
      else
         Console.WriteLine("The expenses total {0:C2}.", total);
   }  
}
// The example displays the following output:
//       The regular expression pattern is:
//          \$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)
//       Found 6 matches.
//       The expenses total $81.58.
```

```vb
Imports System.Collections.Generic
Imports System.Globalization
Imports System.Text.RegularExpressions

Public Module Example
   Public Sub Main()
      ' Define text to be parsed.
      Dim input As String = "Office expenses on 2/13/2008:" + vbCrLf + _
                            "Paper (500 sheets)                      $3.95" + vbCrLf + _
                            "Pencils (box of 10)                     $1.00" + vbCrLf + _
                            "Pens (box of 10)                        $4.49" + vbCrLf + _
                            "Erasers                                 $2.19" + vbCrLf + _
                            "Ink jet printer                        $69.95" + vbCrLf + vbCrLf + _
                            "Total Expenses                        $ 81.58" + vbCrLf
      ' Get current culture's NumberFormatInfo object.
      Dim nfi As NumberFormatInfo = CultureInfo.CurrentCulture.NumberFormat
      ' Assign needed property values to variables.
      Dim currencySymbol As String = nfi.CurrencySymbol
      Dim symbolPrecedesIfPositive As Boolean = CBool(nfi.CurrencyPositivePattern Mod 2 = 0)
      Dim groupSeparator As String = nfi.CurrencyGroupSeparator
      Dim decimalSeparator As String = nfi.CurrencyDecimalSeparator

      ' Form regular expression pattern.
      Dim pattern As String = Regex.Escape(CStr(IIf(symbolPrecedesIfPositive, currencySymbol, ""))) + _
                              "\s*[-+]?" + "([0-9]{0,3}(" + groupSeparator + "[0-9]{3})*(" + _
                              Regex.Escape(decimalSeparator) + "[0-9]+)?)" + _
                              CStr(IIf(Not symbolPrecedesIfPositive, currencySymbol, "")) 
      Console.WriteLine("The regular expression pattern is: ")
      Console.WriteLine("   " + pattern)      

      ' Get text that matches regular expression pattern.
      Dim matches As MatchCollection = Regex.Matches(input, pattern, RegexOptions.IgnorePatternWhitespace)               
      Console.WriteLine("Found {0} matches. ", matches.Count)

      ' Get numeric string, convert it to a value, and add it to List object.
      Dim expenses As New List(Of Decimal)

      For Each match As Match In matches
         expenses.Add(Decimal.Parse(match.Groups.Item(1).Value))      
      Next

      ' Determine whether total is present and if present, whether it is correct.
      Dim total As Decimal
      For Each value As Decimal In expenses
         total += value
      Next

      If total / 2 = expenses(expenses.Count - 1) Then
         Console.WriteLine("The expenses total {0:C2}.", expenses(expenses.Count - 1))
      Else
         Console.WriteLine("The expenses total {0:C2}.", total)
      End If   
   End Sub
End Module
' The example displays the following output:
'       The regular expression pattern is:
'          \$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)
'       Found 6 matches.
'       The expenses total $81.58.
```

<span data-ttu-id="bb630-155">現在 "英語 - 米国" (en-US) カルチャが使用されているコンピューターでは、`\$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)` という正規表現が動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="bb630-155">On a computer whose current culture is English - United States (en-US), the example dynamically builds the regular expression `\$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`.</span></span> <span data-ttu-id="bb630-156">この正規表現パターンは、次のように解釈できます。</span><span class="sxs-lookup"><span data-stu-id="bb630-156">This regular expression pattern can be interpreted as follows:</span></span>

<span data-ttu-id="bb630-157">構文</span><span class="sxs-lookup"><span data-stu-id="bb630-157">Syntax</span></span> | <span data-ttu-id="bb630-158">説明</span><span class="sxs-lookup"><span data-stu-id="bb630-158">Meaning</span></span>
------ | -------
`\$` | <span data-ttu-id="bb630-159">入力文字列に含まれる単一のドル記号 ($) を検索します。</span><span class="sxs-lookup"><span data-stu-id="bb630-159">Look for a single occurrence of the dollar symbol ($) in the input string.</span></span> <span data-ttu-id="bb630-160">この正規表現パターン文字列に使用されている円記号は、ドル記号を正規表現のアンカーではなく、文字として扱うことを意味します。</span><span class="sxs-lookup"><span data-stu-id="bb630-160">The regular expression pattern string includes a backslash to indicate that the dollar symbol is to be interpreted literally rather than as a regular expression anchor.</span></span> <span data-ttu-id="bb630-161">ドル記号 ($) を単独で指定した場合、正規表現エンジンは、比較の開始位置を文字列の終端に設定します。現在のカルチャの通貨記号が正規表現記号として解釈されるのを防ぐため、この例では、[Escape](xref:System.Text.RegularExpressions.Regex.Escape(System.String)) メソッドを呼び出して文字をエスケープしています。</span><span class="sxs-lookup"><span data-stu-id="bb630-161">(The $ symbol alone would indicate that the regular expression engine should try to begin its match at the end of a string.) To ensure that the current culture's currency symbol is not misinterpreted as a regular expression symbol, the example calls the [Escape](xref:System.Text.RegularExpressions.Regex.Escape(System.String)) method to escape the character.</span></span>
`\s*` | <span data-ttu-id="bb630-162">空白文字の&0; 回以上の繰り返しを検索します。</span><span class="sxs-lookup"><span data-stu-id="bb630-162">Look for zero or more occurrences of a white-space character.</span></span>
`[-+]?` | <span data-ttu-id="bb630-163">正の符号または負の符号の&0; 回または&1; 回の繰り返しを検索します。</span><span class="sxs-lookup"><span data-stu-id="bb630-163">Look for zero or one occurrence of either a positive sign or a negative sign.</span></span>
`([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)` | <span data-ttu-id="bb630-164">外側の丸かっこで囲まれている表現は、キャプチャ グループまたは部分式として定義されます。</span><span class="sxs-lookup"><span data-stu-id="bb630-164">The outer parentheses around this expression define it as a capturing group or a subexpression.</span></span> <span data-ttu-id="bb630-165">一致が見つかった場合、一致文字列のその部分に関する情報を、[Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) プロパティから返された [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) オブジェクトの&2; つ目の [Group](xref:System.Text.RegularExpressions.Group) オブジェクトから取得できます。</span><span class="sxs-lookup"><span data-stu-id="bb630-165">If a match is found, information about this part of the matching string can be retrieved from the second [Group](xref:System.Text.RegularExpressions.Group) object in the [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) object returned by the [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) property.</span></span> <span data-ttu-id="bb630-166">(コレクションの&1; つ目の要素は、一致した文字列全体を表します)。</span><span class="sxs-lookup"><span data-stu-id="bb630-166">(The first element in the collection represents the entire match.)</span></span>
`[0-9]{0,3}` | <span data-ttu-id="bb630-167">10 進数字 (0 ～ 9) の 0 回以上、3 回以下の繰り返しを検索します。</span><span class="sxs-lookup"><span data-stu-id="bb630-167">Look for zero to three occurrences of the decimal digits 0 through 9.</span></span>
`(,[0-9]{3})*` | <span data-ttu-id="bb630-168">桁区切り記号と&3; 桁の&10; 進数字の&0; 回以上の繰り返しを検索します。</span><span class="sxs-lookup"><span data-stu-id="bb630-168">Look for zero or more occurrences of a group separator followed by three decimal digits.</span></span>
`\.` | <span data-ttu-id="bb630-169">単一の小数点を検索します。</span><span class="sxs-lookup"><span data-stu-id="bb630-169">Look for a single occurrence of the decimal separator.</span></span>
`[0-9]+` | <span data-ttu-id="bb630-170">10 進数字の&1; 回以上の繰り返しを検索します。</span><span class="sxs-lookup"><span data-stu-id="bb630-170">Look for one or more decimal digits.</span></span>
`(\.[0-9]+)?` | <span data-ttu-id="bb630-171">小数点と&1; 桁以上の数字の&0; 回または&1; 回の繰り返しを検索します。</span><span class="sxs-lookup"><span data-stu-id="bb630-171">Look for zero or one occurrence of the decimal separator followed by at least one decimal digit.</span></span>

## <a name="related-topics"></a><span data-ttu-id="bb630-172">関連トピック</span><span class="sxs-lookup"><span data-stu-id="bb630-172">Related Topics</span></span>

<span data-ttu-id="bb630-173">タイトル</span><span class="sxs-lookup"><span data-stu-id="bb630-173">Title</span></span> | <span data-ttu-id="bb630-174">説明</span><span class="sxs-lookup"><span data-stu-id="bb630-174">Description</span></span>
----- | -----------
[<span data-ttu-id="bb630-175">正規表現言語 - クイック リファレンス</span><span class="sxs-lookup"><span data-stu-id="bb630-175">Regular expression language - quick reference</span></span>](quick-ref.md) | <span data-ttu-id="bb630-176">正規表現を定義するために使う一連の文字、演算子、および構成体について説明します。</span><span class="sxs-lookup"><span data-stu-id="bb630-176">Provides information on the set of characters, operators, and constructs that you can use to define regular expressions.</span></span>
[<span data-ttu-id="bb630-177">正規表現のオブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="bb630-177">The regular expression object model</span></span>](object-model.md) | <span data-ttu-id="bb630-178">正規表現クラスの使用方法について詳しく説明し、コード例を示します。</span><span class="sxs-lookup"><span data-stu-id="bb630-178">Provides information and code examples that illustrate how to use the regular expression classes.</span></span>
[<span data-ttu-id="bb630-179">正規表現の動作の詳細</span><span class="sxs-lookup"><span data-stu-id="bb630-179">Details of regular expression behavior</span></span>](regex-behavior.md) | <span data-ttu-id="bb630-180">.NET の正規表現の機能と動作について説明します。</span><span class="sxs-lookup"><span data-stu-id="bb630-180">Provides information about the capabilities and behavior of .NETregular expressions.</span></span>
[<span data-ttu-id="bb630-181">正規表現の例</span><span class="sxs-lookup"><span data-stu-id="bb630-181">Regular expression examples</span></span>](regex-examples.md) | <span data-ttu-id="bb630-182">正規表現の一般的な使用方法を示すコード例が用意されています。</span><span class="sxs-lookup"><span data-stu-id="bb630-182">Provides code examples that illustrate typical uses of regular expressions.</span></span>


## <a name="reference"></a><span data-ttu-id="bb630-183">参照</span><span class="sxs-lookup"><span data-stu-id="bb630-183">Reference</span></span>

[<span data-ttu-id="bb630-184">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="bb630-184">System.Text.RegularExpressions</span></span>](xref:System.Text.RegularExpressions)

[<span data-ttu-id="bb630-185">System.Text.RegularExpressions.Regex</span><span class="sxs-lookup"><span data-stu-id="bb630-185">System.Text.RegularExpressions.Regex</span></span>](xref:System.Text.RegularExpressions.Regex)


