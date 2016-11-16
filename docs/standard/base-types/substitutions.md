---
title: "正規表現での置換"
description: "正規表現での置換"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/29/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 0fded615-1021-4468-a644-b491814305c6
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 3e02d18d6566c67c7fff7003671f340f97b0dfce

---

# <a name="substitutions-in-regular-expressions"></a>正規表現での置換

置換は、置換パターン内でのみ認識される言語要素です。 置換では、正規表現パターンを使用して、入力文字列内の一致するテキストを置換するテキストの全体または一部を定義します。 置換パターンは、1 個以上の置換と、リテラル文字で構成されます。 置換パターンは、*replacement* パラメーターを指定した [Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.String,System.Text.RegularExpressions.RegexOptions)) メソッドのオーバーロードと、[Match.Result](xref:System.Text.RegularExpressions.Match.Result(System.String)) メソッドに用意されています。 メソッドは、一致するパターンを、*replacement* パラメーターで定義されているパターンで置換します。

.NET では、次の表に示す置換要素が定義されています。

代入 | 説明
------------ | ----------- 
**$**_number_ | *number* で識別されるキャプチャ グループに一致する最後の部分文字列を置換文字列に含めます。*number* は 10 進値です。 詳細については、「[番号付きグループの置換](#substituting-a-numbered-group)」を参照してください。
**${**_name_**}** | **(?<**_name_**>)** で指定された名前付きグループに一致する最後の部分文字列を置換文字列に含めます。 詳細については、「[名前付きグループの置換](#substituting-a-named-group)」を参照してください。
**$$** | 置換文字列に 1 つの "$" リテラルを含めます。 詳細については、「["$" 文字の置換](#substituting-a--character)」を参照してください。
**$&** | 一致した文字列全体のコピーを置換文字列に含めます。 詳細については、「[一致した文字列全体の置換](#substituting-the-entire-match)」を参照してください。
**$`** | 一致した場所より前にある入力文字列のテキストすべてを置換文字列に含めます。 詳細については、「[一致した文字列より前にあるテキストの置換](#substituting-the-text-before-the-match)」を参照してください。
**$'** | 一致した場所より後にある入力文字列のテキストすべてを置換文字列に含めます。 詳細については、「[一致した文字列より後にあるテキストの置換](#substituting-the-text-after-the-match)」を参照してください。 
**$+** | 最後にキャプチャされたグループを置換文字列に含めます。 詳細については、「[キャプチャされた最後のグループの置換](#substituting-the-last-captured-group)」を参照してください。
**$_** | 入力文字列全体を置換文字列に含めます。 詳細については、「[入力文字列全体の置換](#substituting-the-entire-input-string)」を参照してください。
 
## <a name="substitution-elements-and-replacement-patterns"></a>置換要素と置換パターン

置換構成体は、置換パターンで認識される特殊な構成体です。 文字エスケープやピリオド (**.**) など、任意の文字に一致する他の正規表現言語要素はいずれもサポートされていません。 同様に、置換言語要素は置換パターン内でのみ認識され、正規表現パターン内では有効ではありません。 

正規表現パターンと置換の両方に使用できる文字は **$** 文字だけですが、この文字の意味はコンテキストによって異なります。 正規表現パターンでは、**$** は文字列の末尾に一致するアンカーです。 置換パターンでは、**$** は置換の先頭を示します。 

> [!NOTE]
> 正規表現の中で置換パターンに似た機能を利用するには、前方参照を使用します。 前方参照の詳細については、「[前方参照構成体](backreference.md)」を参照してください。
 
## <a name="substituting-a-numbered-group"></a>番号付きグループの置換

**$**_number_ 言語要素は、number キャプチャ グループに一致する最後の部分文字列を置換文字列に含めます。*number* は、キャプチャ グループのインデックスです。 たとえば、置換パターン `$1` は、一致した部分文字列がキャプチャされた最初のグループに置き換えられることを示します。 番号付きキャプチャ グループの詳細については、「[正規表現でのグループ化構成体](grouping.md)」を参照してください。

**$** 以降のすべての数字が、number グループに所属すると解釈されます。 そうしたくない場合は、代わりに名前付きグループを使用できます。 たとえば、**$11** の代わりに、置換文字列 **${1}1** を使用して、最初のキャプチャ グループの値と数字 "1" を置換文字列として定義できます。 詳細については、「[名前付きグループの置換](#substituting-a-named-group)」を参照してください。 

**(?<**_name-**>)** 構文を使用して名前が明示的に割り当てられていないキャプチャ グループには、1 から開始する番号が左から右の順に割り当てられます。 名前付きグループにも、最後の名前のないグループのインデックスよりも 1 つ大きい数値から開始する番号が、左から右へと順に割り当てられます。 たとえば、正規表現 `(\w)(?<digit>\d)` では、`digit` という名前付きグループのインデックスは 2 です。

*number* が、正規表現パターンで定義される有効なキャプチャ グループを指定していない場合は、**$**_number_ が、一致した各文字列の置換に使用されるリテラル文字列シーケンスとして解釈されます。

次の例では、**$**_number_ の置換を使用して、10 進値から通貨記号を削除しています。 通貨値の先頭または末尾に見つかった通貨記号を削除し、最も一般的な 2 つの桁区切り記号 ("." および ",") を認識します。 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\p{Sc}*(\s?\d+[.,]?\d*)\p{Sc}*";
      string replacement = "$1";
      string input = "$16.32 12.19 £16.29 €18.29  €18,29";
      string result = Regex.Replace(input, pattern, replacement);
      Console.WriteLine(result);
   }
}
// The example displays the following output:
//       16.32 12.19 16.29 18.29  18,29
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\p{Sc}*(\s?\d+[.,]?\d*)\p{Sc}*"
      Dim replacement As String = "$1"
      Dim input As String = "$16.32 12.19 £16.29 €18.29  €18,29"
      Dim result As String = Regex.Replace(input, pattern, replacement)
      Console.WriteLine(result)
   End Sub
End Module
' The example displays the following output:
'       16.32 12.19 16.29 18.29  18,29
```

正規表現パターン `\p{Sc}*(\s?\d+[.,]?\d*)\p{Sc}*` は、次の表に示すように定義されています。

パターン | 説明
------- | -----------
`\p{Sc}*` | 0 個以上の通貨記号文字と一致します。
`\s?` | 0 個または 1 個の空白文字と一致します。
`\d+` | 1 個以上の 10 進数と一致します。
`[.,]?` | 0 個または 1 個のピリオドまたはコンマと一致します。
`\d*` | 0 個以上の 10 進数と一致します。
`(\s?\d+[.,]?\d*)` | 空白の後に 1 つ以上の 10 進数、0 個または 1 個のピリオドまたはコンマ、さらに 0 個以上の 10 進数が続くパターンに一致します。 これが最初のキャプチャ グループです。 置換パターンは `$1` であるため、[Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.String,System.Text.RegularExpressions.RegexOptions)) メソッドを呼び出すと、一致する部分文字列全体がこのキャプチャされたグループに置き換えられます。 
 
## <a name="substituting-a-named-group"></a>名前付きのグループの置換

**${**_name_**}** 言語要素は、*name* キャプチャ グループに一致する最後の部分文字列を置換します。ここで、*name* は **(?<**_name_**>)** 言語要素で定義されているキャプチャ グループの名前です。 名前付きキャプチャ グループの詳細については、「[正規表現でのグループ化構成体](grouping.md)」を参照してください。

*name* が正規表現パターンで定義されている有効な名前付きキャプチャ グループを指定していないものの、数字で構成されている場合、**${**_name_**}** は番号付きグループとして解釈されます。 

*name* が、正規表現パターンで定義されている有効な名前付きキャプチャ グループも有効な番号付きキャプチャ グループも指定していない場合、**${**_name_**}** は、一致した各文字列の置換に使用されるリテラル文字列シーケンスとして解釈されます。

次の例では、**${**_name_**}** の置換を使用して、10 進値から通貨記号を削除しています。 通貨値の先頭または末尾に見つかった通貨記号を削除し、最も一般的な 2 つの桁区切り記号 ("." および ",") を認識します。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\p{Sc}*(?<amount>\s?\d+[.,]?\d*)\p{Sc}*";
      string replacement = "${amount}";
      string input = "$16.32 12.19 £16.29 €18.29  €18,29";
      string result = Regex.Replace(input, pattern, replacement);
      Console.WriteLine(result);
   }
}
// The example displays the following output:
//       16.32 12.19 16.29 18.29  18,29
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\p{Sc}*(?<amount>\s?\d+[.,]?\d*)\p{Sc}*"
      Dim replacement As String = "${amount}"
      Dim input As String = "$16.32 12.19 £16.29 €18.29  €18,29"
      Dim result As String = Regex.Replace(input, pattern, replacement)
      Console.WriteLine(result)
   End Sub
End Module
' The example displays the following output:
'       16.32 12.19 16.29 18.29  18,29
```

正規表現パターン `\p{Sc}*(?<amount>\s?\d[.,]?\d*)\p{Sc}*` は、次の表に示すように定義されています。 

パターン | 説明
------- | -----------
`\p{Sc}*` | 0 個以上の通貨記号文字と一致します。
`\s?` | 0 個または 1 個の空白文字と一致します。
`\d+` | 1 個以上の 10 進数と一致します。
`[.,]?` | 0 個または 1 個のピリオドまたはコンマと一致します。
`\d*` | 0 個以上の 10 進数と一致します。
`(?<amount>\s?\d[.,]?\d*)` | 空白の後に 1 つ以上の 10 進数、0 個または 1 個のピリオドまたはコンマ、さらに 0 個以上の 10 進数が続くパターンに一致します。 これは、amount という名前のキャプチャ グループです。 置換パターンは `${amount}` であるため、[Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.String,System.Text.RegularExpressions.RegexOptions)) メソッドを呼び出すと、一致する部分文字列全体がこのキャプチャされたグループに置き換えられます。 
 
## <a name="substituting-a-character"></a>$ 文字の置換

**$$** の置換は、リテラル文字 "$" を置換文字列に挿入します。 

次の例では、[NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) オブジェクトを使用して、現在のカルチャの通貨記号と、通貨文字列内でのその配置を決定します。 次に、正規表現パターンと置換パターンの両方を動的に構築します。 現在 en-US カルチャが使用されているコンピューターでこの例を実行すると、`\b(\d+)(\.(\d+))?` という正規表現パターンと `$$ $1$2` という置換パターンが生成されます。 置換パターンは、一致するテキストを、通貨記号と空白に続いて、キャプチャされた最初および 2 番目のグループで置換します。

```csharp
using System;
using System.Globalization;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      // Define array of decimal values.
      string[] values= { "16.35", "19.72", "1234", "0.99"};
      // Determine whether currency precedes (True) or follows (False) number.
      bool precedes = NumberFormatInfo.CurrentInfo.CurrencyPositivePattern % 2 == 0;
      // Get decimal separator.
      string cSeparator = NumberFormatInfo.CurrentInfo.CurrencyDecimalSeparator;
      // Get currency symbol.
      string symbol = NumberFormatInfo.CurrentInfo.CurrencySymbol;
      // If symbol is a "$", add an extra "$".
      if (symbol == "$") symbol = "$$";

      // Define regular expression pattern and replacement string.
      string pattern = @"\b(\d+)(" + cSeparator + @"(\d+))?"; 
      string replacement = "$1$2";
      replacement = precedes ? symbol + " " + replacement : replacement + " " + symbol;
      foreach (string value in values)
         Console.WriteLine("{0} --> {1}", value, Regex.Replace(value, pattern, replacement));
   }
}
// The example displays the following output:
//       16.35 --> $ 16.35
//       19.72 --> $ 19.72
//       1234 --> $ 1234
//       0.99 --> $ 0.99
```

```vb
Imports System.Globalization
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      ' Define array of decimal values.
      Dim values() As String = { "16.35", "19.72", "1234", "0.99"}
      ' Determine whether currency precedes (True) or follows (False) number.
      Dim precedes As Boolean = (NumberFormatInfo.CurrentInfo.CurrencyPositivePattern Mod 2 = 0)
      ' Get decimal separator.
      Dim cSeparator As String = NumberFormatInfo.CurrentInfo.CurrencyDecimalSeparator
      ' Get currency symbol.
      Dim symbol As String = NumberFormatInfo.CurrentInfo.CurrencySymbol
      ' If symbol is a "$", add an extra "$".
      If symbol = "$" Then symbol = "$$"

      ' Define regular expression pattern and replacement string.
      Dim pattern As String = "\b(\d+)(" + cSeparator + "(\d+))?" 
      Dim replacement As String = "$1$2"
      replacement = If(precedes, symbol + " " + replacement, replacement + " " + symbol)
      For Each value In values
         Console.WriteLine("{0} --> {1}", value, Regex.Replace(value, pattern, replacement))
      Next
   End Sub
End Module
' The example displays the following output:
'       16.35 --> $ 16.35
'       19.72 --> $ 19.72
'       1234 --> $ 1234
'       0.99 --> $ 0.99
```

正規表現パターン `\b(\d+)(\.(\d+))?` は、次の表に示すように定義されています。

パターン | 説明
------- | -----------
`\b` | ワード境界の先頭から照合を開始します。
`(\d+)` | 1 個以上の 10 進数と一致します。 これが最初のキャプチャ グループです。
`\.` | ピリオド (桁区切り記号) と一致します。
`(\d+)` | 1 個以上の 10 進数と一致します。 これが 3 番目のキャプチャ グループです。
`(\.(\d+))?` | ピリオドの後に 1 つ以上の 10 進数が続くパターンの 0 回または 1 回の出現と一致します。 これが 2 番目のキャプチャ グループです。
 
## <a name="substituting-the-entire-match"></a>一致した文字列全体の置換

**$&** の置換は、一致した文字列全体を置換文字列に含めます。 通常は、一致した文字列の先頭または末尾に部分文字列を追加するために使用されます。 たとえば、`($&)` という置換パターンは、一致した各文字列の先頭と末尾にかっこを追加します。 一致する文字列がない場合、**$&** の置換は無効です。

**$&** の置換を使用して、文字列配列に格納されている書籍タイトルの先頭と末尾に引用符を追加する例を次に示します。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"^(\w+\s?)+$";
      string[] titles = { "A Tale of Two Cities", 
                          "The Hound of the Baskervilles", 
                          "The Protestant Ethic and the Spirit of Capitalism", 
                          "The Origin of Species" };
      string replacement = "\"$&\"";
      foreach (string title in titles)
         Console.WriteLine(Regex.Replace(title, pattern, replacement));
   }
}
// The example displays the following output:
//       "A Tale of Two Cities"
//       "The Hound of the Baskervilles"
//       "The Protestant Ethic and the Spirit of Capitalism"
//       "The Origin of Species"
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "^(\w+\s?)+$"
      Dim titles() As String = { "A Tale of Two Cities", _
                                 "The Hound of the Baskervilles", _
                                 "The Protestant Ethic and the Spirit of Capitalism", _
                                 "The Origin of Species" }
      Dim replacement As String = """$&"""
      For Each title As String In titles
         Console.WriteLine(Regex.Replace(title, pattern, replacement))
      Next  
   End Sub
End Module
' The example displays the following output:
'       "A Tale of Two Cities"
'       "The Hound of the Baskervilles"
'       "The Protestant Ethic and the Spirit of Capitalism"
'       "The Origin of Species"
```

正規表現パターン `^(\w+\s?)+$` は、次の表に示すように定義されています。

パターン | 説明
------- | -----------
`^` | 入力文字列の先頭から照合を開始します。
`(\w+\s?)+` | 1 つ以上の単語文字の後に 0 個または 1 個の空白文字が 1 回以上続くパターンに一致します。 
`$` | 入力文字列の末尾と一致します。

`"$&"` という置換パターンは、各一致文字列の先頭と末尾にリテラルの一重引用符を追加します。

## <a name="substituting-the-text-before-the-match"></a>一致した文字列より前にあるテキストの置換

**$`** substitution replaces the matched string with the entire input string before the match. That is, it duplicates the input string up to the match while removing the matched text. Any text that follows the matched text is unchanged in the result string. If there are multiple matches in an input string, the replacement text is derived from the original input string, rather than from the string in which text has been replaced by earlier matches. (The example provides an illustration.) If there is no match, the **$`** の置換は無効です。

次の例では、正規表現パターン `\d+` を使用して、入力文字列内の 1 つ以上の 10 進数のシーケンスを照合します。 置換文字列 **$`** は、これらの数字を、一致文字列より前にあるテキストで置換します。 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "aa1bb2cc3dd4ee5";
      string pattern = @"\d+";
      string substitution = "$`";
      Console.WriteLine("Matches:");
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index);

      Console.WriteLine("Input string:  {0}", input);
      Console.WriteLine("Output string: " + 
                        Regex.Replace(input, pattern, substitution));
   }
}
// The example displays the following output:
//    Matches:
//       1 at position 2
//       2 at position 5
//       3 at position 8
//       4 at position 11
//       5 at position 14
//    Input string:  aa1bb2cc3dd4ee5
//    Output string: aaaabbaa1bbccaa1bb2ccddaa1bb2cc3ddeeaa1bb2cc3dd4ee
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "aa1bb2cc3dd4ee5"
      Dim pattern As String = "\d+"
      Dim substitution As String = "$`"
      Console.WriteLine("Matches:")
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index)
      Next   
      Console.WriteLine("Input string:  {0}", input)
      Console.WriteLine("Output string: " + _
                        Regex.Replace(input, pattern, substitution))
   End Sub
End Module
' The example displays the following output:
'    Matches:
'       1 at position 2
'       2 at position 5
'       3 at position 8
'       4 at position 11
'       5 at position 14
'    Input string:  aa1bb2cc3dd4ee5
'    Output string: aaaabbaa1bbccaa1bb2ccddaa1bb2cc3ddeeaa1bb2cc3dd4ee
```

この例では、入力文字列 `"aa1bb2cc3dd4ee5"` に 5 つの一致が含まれています。 $` の置換によって、正規表現エンジンが入力文字列の各一致文字列をどのように置換するかを、次の表に示します。 挿入されたテキストは結果文字列の列に太字で示されています。

一致したもの | 位置 | 一致した場所より前にある文字列 | 結果文字列
----- | -------- | ------------------- | -------------
1 | 2 | aa | aa**aa**bb2cc3dd4ee5
2 | 5 | aa1bb | aaaabb**aa1bb**cc3dd4ee5
3 | 8 | aa1bb2cc | aaaabbaa1bbcc**aa1bb2cc**dd4ee5
4 | 11 | aa1bb2cc3dd | aaaabbaa1bbccaa1bb2ccdd**aa1bb2cc3dd**ee5
5 | 14 | aa1bb2cc3dd4ee | aaaabbaa1bbccaa1bb2ccddaa1bb2cc3ddee **aa1bb2cc3dd4ee**
 
## <a name="substituting-the-text-after-the-match"></a>一致した文字列より後にあるテキストの置換

**$'** の置換は、一致した場所より後にある入力文字列全体で一致した文字列を置換します。 つまり、一致した場所より後にある入力文字列を複製し、一致したテキストを削除します。 結果文字列では、一致したテキストより前にあるテキストは変更されません。 一致する文字列がない場合、**$'** の置換は無効です。

次の例では、正規表現パターン `\d+` を使用して、入力文字列内の 1 つ以上の 10 進数のシーケンスを照合します。 置換文字列 **$'** は、これらの数字を、一致文字列に続くテキストで置換します。 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "aa1bb2cc3dd4ee5";
      string pattern = @"\d+";
      string substitution = "$'";
      Console.WriteLine("Matches:");
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index);
      Console.WriteLine("Input string:  {0}", input);
      Console.WriteLine("Output string: " + 
                        Regex.Replace(input, pattern, substitution));
   }
}
// The example displays the following output:
//    Matches:
//       1 at position 2
//       2 at position 5
//       3 at position 8
//       4 at position 11
//       5 at position 14
//    Input string:  aa1bb2cc3dd4ee5
//    Output string: aaaabbaa1bbccaa1bb2ccddaa1bb2cc3ddeeaa1bb2cc3dd4ee
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "aa1bb2cc3dd4ee5"
      Dim pattern As String = "\d+"
      Dim substitution As String = "$'"
      Console.WriteLine("Matches:")
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index)
      Next   
      Console.WriteLine("Input string:  {0}", input)
      Console.WriteLine("Output string: " + _
                        Regex.Replace(input, pattern, substitution))
   End Sub
End Module
' The example displays the following output:
'    Matches:
'       1 at position 2
'       2 at position 5
'       3 at position 8
'       4 at position 11
'       5 at position 14
'    Input string:  aa1bb2cc3dd4ee5
'    Output string: aaaabbaa1bbccaa1bb2ccddaa1bb2cc3ddeeaa1bb2cc3dd4ee
```

この例では、入力文字列 `"aa1bb2cc3dd4ee5"` に 5 つの一致が含まれています。 **$'** の置換によって、正規表現エンジンが入力文字列の各一致文字列をどのように置換するかを、次の表に示します。 挿入されたテキストは結果文字列の列に太字で示されています。

一致したもの | 位置 | 一致した場所より前にある文字列 | 結果文字列
----- | -------- | ------------------- | -------------
1 | 2 | bb2cc3dd4ee5 | aa**bb2cc3dd4ee5**bb2cc3dd4ee5
2 | 5 | cc3dd4ee5 | aabb2cc3dd4ee5bb**cc3dd4ee5**cc3dd4ee5
3 | 8 | dd4ee5 | aabb2cc3dd4ee5bbcc3dd4ee5cc**dd4ee5**dd4ee5
4 | 11 | ee5 | aabb2cc3dd4ee5bbcc3dd4ee5ccdd4ee5dd**ee5**ee5
5 | 14 | [String.Empty](xref:System.String.Empty) | aabb2cc3dd4ee5bbcc3dd4ee5ccdd4ee5ddee5ee
 
## <a name="substituting-the-last-captured-group"></a>キャプチャされた最後のグループの置換

**$+** の置換は、キャプチャされた最後のグループで一致した文字列を置換します。 キャプチャされたグループがない場合、またはキャプチャされた最後のグループの値が [String.Empty](xref:System.String.Empty) の場合、**$+** の置換は無効です。

次の例では、文字列内の重複する単語を識別し、**$+** の置換を使用して、これらの単語をその単語 1 つに置換します。 [RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase) オプションを使用すると、大文字と小文字の違いを除いて同一である単語が重複と見なされるようになります。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(\w+)\s\1\b";
      string substitution = "$+";
      string input = "The the dog jumped over the fence fence.";
      Console.WriteLine(Regex.Replace(input, pattern, substitution, 
                        RegexOptions.IgnoreCase));
   }
}
// The example displays the following output:
//      The dog jumped over the fence.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(\w+)\s\1\b"
      Dim substitution As String = "$+"
      Dim input As String = "The the dog jumped over the fence fence."
      Console.WriteLine(Regex.Replace(input, pattern, substitution, _
                                      RegexOptions.IgnoreCase))
   End Sub
End Module
' The example displays the following output:
'      The dog jumped over the fence.
```

正規表現パターン `\b(\w+)\s\1\b` は、次の表に示すように定義されています。

パターン | 説明
------- | ----------- 
`\b` | ワード境界から照合を開始します。
`(\w+)` | 1 つ以上の単語文字に一致します。 これが最初のキャプチャ グループです。
`\s` | 空白文字と一致します。
`\1` | キャプチャされた最初のグループと一致します。
`\b` | ワード境界で照合を終了します。
 
## <a name="substituting-the-entire-input-string"></a>入力文字列全体の置換

**$_** の置換は、一致した文字列を入力文字列全体で置換します。 つまり、一致したテキストを削除し、一致したテキストを含む文字列全体でそのテキストを置換します。

次の例では、入力文字列の 1 つ以上の 10 進数を照合します。 **$_** の置換を使用して、これらを入力文字列全体で置換します。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "ABC123DEF456";
      string pattern = @"\d+";
      string substitution = "$_";
      Console.WriteLine("Original string:          {0}", input);
      Console.WriteLine("String with substitution: {0}", 
                        Regex.Replace(input, pattern, substitution));      
   }
}
// The example displays the following output:
//       Original string:          ABC123DEF456
//       String with substitution: ABCABC123DEF456DEFABC123DEF456
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "ABC123DEF456"
      Dim pattern As String = "\d+"
      Dim substitution As String = "$_"
      Console.WriteLine("Original string:          {0}", input)
      Console.WriteLine("String with substitution: {0}", _
                        Regex.Replace(input, pattern, substitution))      
   End Sub
End Module
' The example displays the following output:
'       Original string:          ABC123DEF456
'       String with substitution: ABCABC123DEF456DEFABC123DEF456
```

この例では、入力文字列 `"ABC123DEF456"` に 2 つの一致が含まれています。 **$_** の置換によって、正規表現エンジンが入力文字列の各一致文字列をどのように置換するかを、次の表に示します。 挿入されたテキストは結果文字列の列に太字で示されています。

一致したもの | 位置 | 一致した場所より前にある文字列 | 結果文字列
----- | -------- | ------------------- | -------------
1 | 3 | 123 | ABC**ABC123DEF456**DEF456
2 | 5 | 456 | ABCABC123DEF456DEF**ABC123DEF456**
 
## <a name="see-also"></a>関連項目

[正規表現言語 - クイック リファレンス](quick-ref.md)




<!--HONumber=Nov16_HO1-->


