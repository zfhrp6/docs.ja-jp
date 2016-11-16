---
title: ".NET の正規表現"
description: ".NET の正規表現"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: d1a640cf-09ca-48f7-800c-a627a6d549c9
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: e9ae9cb47955fb926507be32afb875efd3260ce3

---

# <a name="regular-expressions-in-net"></a>.NET の正規表現

正規表現を使用すると、強力、柔軟、そして効率的な方法でテキストを処理できます。 正規表現の広範なパターン一致表記法を使用することで、大量のテキストをすばやく解析して特定の文字パターンを検索したり、決められたパターン (電子メール アドレスなど) と照らしてテキストを検証したりできるほか、テキストの部分文字列を抽出、編集、置換、または削除したり、抽出した文字列をコレクションに追加してレポートを生成したりすることもできます。 文字列処理や大量のテキストを解析する多くのアプリケーションにとって、正規表現は欠くことのできないツールです。

## <a name="how-regular-expressions-work"></a>正規表現の動作

正規表現を使ったテキスト処理の最も重要な部分は、.NET の [System.Text.RegularExpressions.Regex](xref:System.Text.RegularExpressions.Regex) オブジェクトによって表される正規表現エンジンです。 正規表現を使ったテキスト処理では、正規表現エンジンに対し、最低でも次の 2 つの情報を与える必要があります。

* テキストを識別する正規表現パターン。 
  
  .NET では、正規表現のパターンが特殊な構文または言語で定義されます。この構文または言語には、Perl 5 の正規表現と互換性があるほか、右から左への一致処理など、いくつかの機能が追加されています。 詳細については、「[正規表現言語 - クイック リファレンス](quick-ref.md)」をご覧ください。
  
* 正規表現パターンの解析対象となるテキスト。

[Regex](xref:System.Text.RegularExpressions.Regex) クラスのメソッドを使用すると、次のような処理を実行できます。

* 入力されたテキストに特定の正規表現パターンが出現するかどうかを調べるには、[Regex.IsMatch](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String)) メソッドを呼び出します。 テキストを検証するために [IsMatch](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String)) メソッドを使用する例については、「[方法: 文字列が有効な電子メール形式であるかどうかを検証する](verify-format.md)」をご覧ください。

* 正規表現パターンと一致したテキストを 1 つまたはすべて取得するには、[Regex.Match](xref:System.Text.RegularExpressions.Regex.Match(System.String)) メソッドまたは [Regex.Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String)) メソッドを呼び出します。 前者は、一致したテキストの情報を保持する [System.Text.RegularExpressions.Match](xref:System.Text.RegularExpressions.Match) オブジェクトを返します。 後者は、解析対象のテキストに見つかった各一致につき 1 つの [System.Text.RegularExpressions.Match](xref:System.Text.RegularExpressions.Match) オブジェクトを含む [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) オブジェクトを返します。 

* 正規表現パターンと一致したテキストを置換するには、[Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)) メソッドを呼び出します。 [Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)) メソッドを使用して日付形式を変更したり文字列から無効な文字を削除したりする例については、「[方法: 文字列から無効な文字を取り除く](strip-characters.md)」および「[正規表現の例: 日付形式の変更](changing-formats.md)」をご覧ください。

正規表現のオブジェクト モデルの概要については、「[正規表現のオブジェクト モデル](object-model.md)」をご覧ください。

正規表現言語の詳細については、「[正規表現言語 - クイック リファレンス](quick-ref.md)」をご覧ください。

## <a name="regular-expression-examples"></a>正規表現の例

[String](xref:System.String) クラスには、より大きな文字列内のリテラル文字列を検索する際に使用できる文字列の検索メソッドと置換メソッドが数多く含まれています。 正規表現は、次の例に示すように、文字列内の部分文字列のいずれかを検索する場合、または文字列内のパターンを識別する場合に最も役立ちます。 

### <a name="example-1-replacing-substrings"></a>例 1: 部分文字列の置換

氏名に敬称 (Mr.、Mrs.、Miss、または Ms.) が付いている場合がある名前が、宛先リストに含まれるとします。 そのリストから封筒のラベルを生成する場合に敬称が含まれないようにするには、次の例に示すように、正規表現を使用して敬称を削除します。

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

正規表現パターン `(Mr\.? |Mrs\.? |Miss |Ms\.? )` は、"Mr "、"Mr. "、"Mrs "、"Mrs. "、"Miss "、"Ms"、または "Ms. " の出現と一致します。 [Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)) メソッドを呼び出すと、一致する文字列が [String.Empty](xref:System.String.Empty) に置き換えられます。つまり、元の文字列から削除されます。

### <a name="example-2-identifying-duplicated-words"></a>例 2: 重複する単語の識別

記述者が単語を誤って重複入力するというエラーがよくあります。 次の例に示すように、正規表現を使用して重複する単語を識別できます。

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

正規表現パターン `\b(\w+?)\s\1\b` は、次のように解釈できます。

構文 | 説明
------ | -------
`\b` | ワード境界から開始します。
`(\w+?)` | 1 つ以上 (ただし、できるだけ少ない文字数) の単語文字と一致します。 同時に、`\1` というグループを形成します。
`\s` | 空白文字と一致します。
`\1` | `\1` という名前のグループと等しい部分文字列と一致します。
`\b` | ワード境界に一致します。

[Regex.Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) メソッドは、正規表現オプションを [RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase) に設定して呼び出されます。 したがって、照合操作では大文字と小文字が区別されず、この例では部分文字列 "This this" が重複として識別されます。

入力文字列には部分文字列 "this? This" が含まれています。 ただし、句読点が介在するので、重複として識別されません。

### <a name="example-3-dynamically-building-a-culturesensitive-regular-expression"></a>例 3: カルチャに依存した正規表現の動的な構築

ここでは、正規表現による強力なテキスト処理と、.NET の柔軟なグローバリゼーション機能を組み合わせて使用する例を紹介します。 この例では、システムの現在のカルチャで用いられている通貨値の形式を調べるために、[NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) オブジェクトが使用されています。 さらに、その情報を基に、テキストから通貨値を抽出する正規表現を動的に構築します。 検出された一致ごとに、数値文字列のみを含んだサブグループを抽出し、[Decimal](xref:System.Decimal) 値に変換して、通算の合計を計算します。 

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

現在 "英語 - 米国" (en-US) カルチャが使用されているコンピューターでは、`\$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)` という正規表現が動的に作成されます。 この正規表現パターンは、次のように解釈できます。

構文 | 説明
------ | -------
`\$` | 入力文字列に含まれる単一のドル記号 ($) を検索します。 この正規表現パターン文字列に使用されている円記号は、ドル記号を正規表現のアンカーではなく、文字として扱うことを意味します。 ドル記号 ($) を単独で指定した場合、正規表現エンジンは、比較の開始位置を文字列の終端に設定します。現在のカルチャの通貨記号が正規表現記号として解釈されるのを防ぐため、この例では、[Escape](xref:System.Text.RegularExpressions.Regex.Escape(System.String)) メソッドを呼び出して文字をエスケープしています。
`\s*` | 空白文字の 0 回以上の繰り返しを検索します。
`[-+]?` | 正の符号または負の符号の 0 回または 1 回の繰り返しを検索します。
`([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)` | 外側の丸かっこで囲まれている表現は、キャプチャ グループまたは部分式として定義されます。 一致が見つかった場合、一致文字列のその部分に関する情報を、[Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) プロパティから返された [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) オブジェクトの 2 つ目の [Group](xref:System.Text.RegularExpressions.Group) オブジェクトから取得できます。 (コレクションの 1 つ目の要素は、一致した文字列全体を表します)。
`[0-9]{0,3}` | 10 進数字 (0 ～ 9) の 0 回以上、3 回以下の繰り返しを検索します。
`(,[0-9]{3})*` | 桁区切り記号と 3 桁の 10 進数字の 0 回以上の繰り返しを検索します。
`\.` | 単一の小数点を検索します。
`[0-9]+` | 10 進数字の 1 回以上の繰り返しを検索します。
`(\.[0-9]+)?` | 小数点と 1 桁以上の数字の 0 回または 1 回の繰り返しを検索します。

## <a name="related-topics"></a>関連トピック

タイトル | 説明
----- | -----------
[正規表現言語 - クイック リファレンス](quick-ref.md) | 正規表現を定義するために使う一連の文字、演算子、および構成体について説明します。
[正規表現のオブジェクト モデル](object-model.md) | 正規表現クラスの使用方法について詳しく説明し、コード例を示します。
[正規表現の動作の詳細](regex-behavior.md) | .NET の正規表現の機能と動作について説明します。
[正規表現の例](regex-examples.md) | 正規表現の一般的な使用方法を示すコード例が用意されています。


## <a name="reference"></a>参照

[System.Text.RegularExpressions](xref:System.Text.RegularExpressions)

[System.Text.RegularExpressions.Regex](xref:System.Text.RegularExpressions.Regex)




<!--HONumber=Nov16_HO1-->


