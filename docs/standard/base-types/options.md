---
title: "正規表現のオプション"
description: "正規表現のオプション"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/29/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 2db2c3e6-953e-4913-8168-d707c437f2df
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 21672e28d0e76b98f6dac698096fccb2ce4edd03

---

# <a name="regular-expression-options"></a>正規表現のオプション

正規表現パターンでの入力文字列とリテラル文字列の比較では、大文字と小文字が区別されます。正規表現パターンに含まれる空白は、リテラルの空白文字として解釈されます。正規表現で使用されるキャプチャ グループは、暗黙的に指定される場合と明示的に指定される場合があります。これらはすべて、正規表現の既定の動作です。 正規表現のオプションを指定することで、これらの正規表現の既定の動作とそのいくつかの側面を変更できます。 次の表に示す各オプションは、正規表現パターンの一部としてインラインで記述することも、[System.Text.RegularExpressions.Regex](xref:System.Text.RegularExpressions.Regex) クラス コンストラクターまたは静的パターン一致メソッドに [System.Text.RegularExpressions.RegexOptions](xref:System.Text.RegularExpressions.RegexOptions) 列挙値として渡すこともできます。 

RegexOptions のメンバー | インライン文字 | 効果
------------------- | ---------------- | ------ 
[None](xref:System.Text.RegularExpressions.RegexOptions.None) | 使用できません | 既定の動作を使用します。 詳細については、「[既定のオプション](#default-options)」を参照してください。
[IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase) | **i** | 大文字と小文字を区別しない一致を使用します。 詳細については、「[大文字と小文字を区別しない一致](#case-insensitive-matching)」を参照してください。
[Multiline](xref:System.Text.RegularExpressions.RegexOptions.Multiline) | **m** | 複数行モードを使用します。**^** と **$** は、(入力文字列の先頭および末尾ではなく) 各行の先頭および末尾と一致します。 詳細については、「[複数行モード](#multiline-mode)」を参照してください。
[Singleline](xref:System.Text.RegularExpressions.RegexOptions.Singleline) | **s** | 単一行モードを使用します。ピリオド (**.**) は任意の 1 文字と一致します (**\n** を除くすべての文字の代用)。 詳細については、「[単一行モード](#single-line-mode)」を参照してください。
[ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture) | **n** | 名前のないグループをキャプチャしません。 **(?<**_name_**>** _subexpression_**)** という形式で、明示的に名前または番号が付加されたグループのみを有効なキャプチャ対象とします。 詳細については、「[明示的なキャプチャのみ](#explicit-captures-only)」を参照してください。
[Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) | 使用できません | 正規表現をアセンブリにコンパイルします。 詳細については、「[コンパイルされた正規表現](#compiled-regular-expressions)」を参照してください。
[IgnorePatternWhitespace](xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace) | **x** | エスケープされていない空白をパターンから除外し、シャープ記号 (**#**) の後ろのコメントを有効にします。 詳細については、「[空白を無視](#ignore-white-space)」を参照してください。
[RightToLeft](xref:System.Text.RegularExpressions.RegexOptions.RightToLeft) | 使用できません | 検索の方向を変更します。 左から右ではなく、右から左に検索します。 詳細については、「[右から左モード](#right-to-left-mode)」を参照してください。
[ECMAScript](xref:System.Text.RegularExpressions.RegexOptions.ECMAScript) | 使用できません | 式の ECMAScript 準拠の動作を有効にします。 詳細については、「[ECMAScript 一致の動作](#ecmascript-matching-behavior)」を参照してください。
[CultureInvariant](xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant) | 使用できません | 言語のカルチャの違いを無視します。 詳細については、「[インバリアント カルチャを使用した比較](#comparison-using-the-invariant-culture)」を参照してください。
 
## <a name="specifying-the-options"></a>オプションの指定

正規表現のオプションは、次の 3 種類の方法のいずれかで指定できます。

* [Regex.Regex(String, RegexOptions)](xref:System.Text.RegularExpressions.Regex.%23ctor(System.String,System.Text.RegularExpressions.RegexOptions)) のような [System.Text.RegularExpressions.Regex](xref:System.Text.RegularExpressions.Regex) クラス コンストラクターの *options* パラメーターまたは [Regex.Match(String, String, RegexOptions)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) のような静的 (Visual Basic の共有) パターン一致メソッドで。 *options* パラメーターは [System.Text.RegularExpressions.RegexOptions](xref:System.Text.RegularExpressions.RegexOptions) 列挙値をビットごとの OR で組み合わせたものです。 

  クラス コンストラクターの *options* パラメーターを使用して、オプションが [Regex](xref:System.Text.RegularExpressions.Regex) インスタンスに指定されると、それらのオプションは [System.Text.RegularExpressions.RegexOptions](xref:System.Text.RegularExpressions.RegexOptions) プロパティに割り当てられます。 ただし、[System.Text.RegularExpressions.RegexOptions](xref:System.Text.RegularExpressions.RegexOptions) プロパティは、正規表現パターン自体でのインライン オプションを反映しません。 

  具体的な例を次に示します。 [Regex.Match(String, String, RegexOptions)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) メソッドの *options* パラメーターを使用して、文字 "d" で始まる単語を識別するときに、大文字と小文字を区別しない一致を有効にすると同時に、パターンの空白を無視します。

  ```csharp
  string pattern = @"d \w+ \s";
  string input = "Dogs are decidedly good pets.";
  RegexOptions options = RegexOptions.IgnoreCase | RegexOptions.IgnorePatternWhitespace;
  
  foreach (Match match in Regex.Matches(input, pattern, options))
     Console.WriteLine("'{0}// found at index {1}.", match.Value, match.Index);
  // The example displays the following output:
  //    'Dogs // found at index 0.
  //    'decidedly // found at index 9.      
  ```

  ```vb
  Dim pattern As String = "d \w+ \s"
  Dim input As String = "Dogs are decidedly good pets."
  Dim options As RegexOptions = RegexOptions.IgnoreCase Or RegexOptions.IgnorePatternWhitespace

  For Each match As Match In Regex.Matches(input, pattern, options)
     Console.WriteLine("'{0}' found at index {1}.", match.Value, match.Index)
  Next
  ' The example displays the following output:
  '    'Dogs ' found at index 0.
  '    'decidedly ' found at index 9.  
  ```

* **(?imnsx-imnsx)** という構文で、インライン オプションを正規表現パターンに適用します。 この場合、オプションが定義されているパターンの先頭から、パターンの末尾を含むポイントまで、または別のインライン オプションでオプションが定義されていないポイントまでを範囲として、オプションがパターンに適用されます。 [Regex](xref:System.Text.RegularExpressions.Regex) インスタンスの [System.Text.RegularExpressions.RegexOptions](xref:System.Text.RegularExpressions.RegexOptions) プロパティはこれらのインライン オプションを反映しないことに注意してください。 詳細については、「[正規表現でのその他の構成体](miscellaneous.md)」トピックをご覧ください。

  具体的な例を次に示します。 インライン オプションを使用して、文字 "d" で始まる単語を識別するときに、大文字と小文字を区別しない一致を有効にすると同時に、パターンの空白を無視します。

  ```csharp
  string pattern = @"(?ix) d \w+ \s";
  string input = "Dogs are decidedly good pets.";
  
  foreach (Match match in Regex.Matches(input, pattern))
     Console.WriteLine("'{0}// found at index {1}.", match.Value, match.Index);
  // The example displays the following output:
  //    'Dogs // found at index 0.
  //    'decidedly // found at index 9.      
  ```

  ```vb
  Dim pattern As String = "\b(?ix) d \w+ \s"
  Dim input As String = "Dogs are decidedly good pets."

  For Each match As Match In Regex.Matches(input, pattern)
     Console.WriteLine("'{0}' found at index {1}.", match.Value, match.Index)
  Next
  ' The example displays the following output:
  '    'Dogs ' found at index 0.
  '    'decidedly ' found at index 9.  
  ```

* **(?imnsx-imnsx:**_subexpression_**)** という構文で、特定のグループ化構成体のインライン オプションを正規表現パターンに適用します。 オプション セットの前にマイナス記号を付けないとそのオプション セットはオンになり、マイナス記号を付けるとオフになります  (**?** は言語構成要素の構文の固定部分であり、オプションが有効であるか無効であるかにかかわらず、必要になります)。オプションは、そのグループに対してのみ適用されます。 詳細については、「[正規表現でのグループ化構成体](grouping.md)」を参照してください。

  具体的な例を次に示します。 グループ化構成体のインライン オプションを使用して、文字 "d" で始まる単語を識別するときに、大文字と小文字を区別しない一致を有効にすると同時に、パターンの空白を無視します。

  ```csharp
  string pattern = @"\b(?ix: d \w+)\s";
  string input = "Dogs are decidedly good pets.";
  
  foreach (Match match in Regex.Matches(input, pattern))
     Console.WriteLine("'{0}// found at index {1}.", match.Value, match.Index);
  // The example displays the following output:
  //    'Dogs // found at index 0.
  //    'decidedly // found at index 9.      
  ```

  ```vb
  Dim pattern As String = "\b(?ix: d \w+)\s"
  Dim input As String = "Dogs are decidedly good pets."

  For Each match As Match In Regex.Matches(input, pattern)
     Console.WriteLine("'{0}' found at index {1}.", match.Value, match.Index)
  Next
  ' The example displays the following output:
  '    'Dogs ' found at index 0.
  '    'decidedly ' found at index 9. 
  ```


オプションをインラインで指定した場合は、オプションまたはオプション セットの前にマイナス記号 (-) を付けると、そのオプションはオフになります。 たとえば、インライン構成体 **(?ix-ms)** は [RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase) オプションと [RegexOptions.IgnorePatternWhitespace](xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace) オプションをオンにし、[RegexOptions.Multiline](xref:System.Text.RegularExpressions.RegexOptions.Multiline) オプションと [RegexOptions.Singleline](xref:System.Text.RegularExpressions.RegexOptions.Singleline) オプションをオフにします。 既定では、すべての正規表現のオプションがオフです。

> [!NOTE]
> コンストラクターまたはメソッド呼び出しの options パラメーターで指定した正規表現オプションが正規表現パターンのインラインで指定したオプションと競合した場合は、インラインで指定したオプションが使用されます。
 

次に示す 5 種類の正規表現オプションは、*options* パラメーターとインラインの両方で設定できます。

* [RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase)

* [RegexOptions.Multiline](xref:System.Text.RegularExpressions.RegexOptions.Multiline)

* [RegexOptions.Singleline](xref:System.Text.RegularExpressions.RegexOptions.Singleline)

* [RegexOptions.ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture)

* [RegexOptions.IgnorePatternWhitespace](xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace)

次に示す 5 種類の正規表現オプションは *options* パラメーターを使用して設定することはできますが、インラインで設定することはできません。

* [RegexOptions.None](xref:System.Text.RegularExpressions.RegexOptions.None)

* [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled)

* [RegexOptions.RightToLeft](xref:System.Text.RegularExpressions.RegexOptions.RightToLeft)

* [RegexOptions.CultureInvariant](xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant)

* [RegexOptions.ECMAScript](xref:System.Text.RegularExpressions.RegexOptions.ECMAScript)

## <a name="determining-the-options"></a>オプションの確認

インスタンス化されたときに [Regex](xref:System.Text.RegularExpressions.Regex) オブジェクトに渡されたオプションの種類を確認するには、読み取り専用の [Regex.Options](xref:System.Text.RegularExpressions.Regex.Options) プロパティの値を取得します。

[RegexOptions.None](xref:System.Text.RegularExpressions.RegexOptions.None) を除くオプションが存在するかどうかをテストするには、目的の [Regex.Options](xref:System.Text.RegularExpressions.Regex.Options) プロパティの値と [RegexOptions](xref:System.Text.RegularExpressions.RegexOptions) の値を使用して AND 演算を実行します。 次に、この結果が [RegexOptions](xref:System.Text.RegularExpressions.RegexOptions) の値と等しいかどうかをテストします。 次の例は、[RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase) オプションが設定されているかどうかをテストします。 

```csharp
if ((rgx.Options & RegexOptions.IgnoreCase) == RegexOptions.IgnoreCase)
   Console.WriteLine("Case-insensitive pattern comparison.");
else
   Console.WriteLine("Case-sensitive pattern comparison.");
```

```vb
If (rgx.Options And RegexOptions.IgnoreCase) = RegexOptions.IgnoreCase Then
   Console.WriteLine("Case-insensitive pattern comparison.")
Else
   Console.WriteLine("Case-sensitive pattern comparison.")
End If 
```

[RegexOptions.None](xref:System.Text.RegularExpressions.RegexOptions.None) に関してテストするには、[RegexOptions](xref:System.Text.RegularExpressions.RegexOptions) プロパティの値が次の例のように [RegexOptions.None](xref:System.Text.RegularExpressions.RegexOptions.None) と等しいかどうかを判断します。 

```csharp
if (rgx.Options == RegexOptions.None)
   Console.WriteLine("No options have been set.");
```

```vb
If rgx.Options = RegexOptions.None Then
   Console.WriteLine("No options have been set.")
End If
```

以降のセクションでは、.NET の正規表現でサポートされているオプションについて説明します。 

## <a name="default-options"></a>既定のオプション

[RegexOptions.None](xref:System.Text.RegularExpressions.RegexOptions.None) オプションは、オプションが指定されていないことを示します。正規表現エンジンは、このオプションの既定の動作を使用します。 次に例を示します。

* このパターンは、ECMAScript 正規表現ではなく、標準の形式として解釈されます。

* 正規表現パターンは、左から右に入力文字列と照合されます。

* 比較では大文字と小文字が区別されます。

* **^** 言語要素および **$** 言語要素は、入力文字列の先頭および末尾と一致します。

* **.** 言語要素は、**\n** を除く任意の 1 文字と一致します。

* 正規表現パターンに含まれる空白は、リテラルの空白文字として解釈されます。

* パターンを入力文字列と比較するときに、現在のカルチャの規則が使用されます。 

* 正規表現パターンのキャプチャ グループは、暗黙的に指定される場合と明示的に指定される場合があります。 

> [!NOTE]
> [RegexOptions.None](xref:System.Text.RegularExpressions.RegexOptions.None) オプションには、等価なインライン オプションは存在しません。 正規表現オプションがインラインで適用されたときに、特定のオプションをオフにすると、既定の動作がオプションごとに復元されます。 たとえば、`(?i)` は大文字と小文字を区別しない比較をオンにし、`(?-i)` は既定の動作 (大文字と小文字を区別する比較) を復元します。
 
[RegexOptions.None](xref:System.Text.RegularExpressions.RegexOptions.None) オプションは正規表現エンジンの既定の動作を表しているので、メソッド呼び出しで明示的に指定されることはほとんどありません。 代わりに、options パラメーターを使用せずにコンストラクターまたは静的パターン一致メソッドが呼び出されます。

## <a name="caseinsensitive-matching"></a>大文字と小文字を区別しない一致

[RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase) オプションまたは **i** インライン オプションを指定すると、大文字と小文字を区別しない一致が実行されます。 既定では、現在のカルチャの大文字と小文字の表記規則が使用されます。

次の例では、"the" で始まるすべての単語と一致する正規表現パターン `\bthe\w*\b` を定義します。 Match メソッドの最初の呼び出しでは既定の大文字と小文字を区別する比較を使用しているので、結果の出力から、文の先頭の文字列 "The" は一致として処理されていないことがわかります。 これが一致として処理されるのは、オプションを [IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase) に設定して [Match](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) メソッドが呼び出された場合です。 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\bthe\w*\b";
      string input = "The man then told them about that event.";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("Found {0} at index {1}.", match.Value, match.Index);

      Console.WriteLine();
      foreach (Match match in Regex.Matches(input, pattern, 
                                            RegexOptions.IgnoreCase))
         Console.WriteLine("Found {0} at index {1}.", match.Value, match.Index);
   }
}
// The example displays the following output:
//       Found then at index 8.
//       Found them at index 18.
//       
//       Found The at index 0.
//       Found then at index 8.
//       Found them at index 18.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\bthe\w*\b"
      Dim input As String = "The man then told them about that event."
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("Found {0} at index {1}.", match.Value, match.Index)
      Next
      Console.WriteLine()
      For Each match As Match In Regex.Matches(input, pattern, _
                                               RegexOptions.IgnoreCase)
         Console.WriteLine("Found {0} at index {1}.", match.Value, match.Index)
      Next
   End Sub
End Module
' The example displays the following output:
'       Found then at index 8.
'       Found them at index 18.
'       
'       Found The at index 0.
'       Found then at index 8.
'       Found them at index 18.
```

次の例では、前の例の正規表現パターンを変更し、*options* パラメーターを使用する代わりに、インライン オプションを使用して、大文字と小文字を区別しない比較を行っています。 最初のパターンでは、文字列 "the" の文字 "t" のみに適用されるよう、グループ化構成体の大文字と小文字を区別しないオプションを定義しています。 オプションの構成体がパターンの先頭にあるので、2 番目のパターンでは、大文字と小文字を区別しないオプションが正規表現全体に適用されています。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(?i:t)he\w*\b";
      string input = "The man then told them about that event.";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("Found {0} at index {1}.", match.Value, match.Index);

      Console.WriteLine();
      pattern = @"(?i)\bthe\w*\b";
      foreach (Match match in Regex.Matches(input, pattern, 
                                            RegexOptions.IgnoreCase))
         Console.WriteLine("Found {0} at index {1}.", match.Value, match.Index);
   }
}
// The example displays the following output:
//       Found The at index 0.
//       Found then at index 8.
//       Found them at index 18.
//       
//       Found The at index 0.
//       Found then at index 8.
//       Found them at index 18.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(?i:t)he\w*\b"
      Dim input As String = "The man then told them about that event."
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("Found {0} at index {1}.", match.Value, match.Index)
      Next
      Console.WriteLine()
      pattern = "(?i)\bthe\w*\b"
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("Found {0} at index {1}.", match.Value, match.Index)
      Next
   End Sub
End Module
' The example displays the following output:
'       Found The at index 0.
'       Found then at index 8.
'       Found them at index 18.
'       
'       Found The at index 0.
'       Found then at index 8.
'       Found them at index 18.
```

## <a name="multiline-mode"></a>複数行モード

[RegexOptions.Multiline](xref:System.Text.RegularExpressions.RegexOptions.Multiline) オプションまたは **m** インライン オプションを指定すると、正規表現エンジンでは、複数行で構成される入力文字列の処理が有効になります。 具体的には、**^** 言語要素および **$** 言語要素の解釈を変更して、入力文字列の先頭および末尾ではなく、行の先頭および末尾に一致するものとします。 

既定では、**$** は入力文字列の末尾とのみ一致します。 [RegexOptions.Multiline](xref:System.Text.RegularExpressions.RegexOptions.Multiline) オプションを指定した場合は、改行文字 **(\n)** または入力文字列の末尾と一致します。 ただし、復帰とライン フィード文字の組み合わせとは一致しません。 この組み合わせと正常に一致させるには、**$** を単独で使用する代わりに、部分式 **\r?$** を使用します。 

次の例では、ボウリング参加者の名前とスコアを抽出し、降順に並べ替えて、[SortedList&lt;TKey, TValue&gt;](xref:System.Collections.Generic.SortedList%602) コレクションに追加しています。 [Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String)) メソッドは 2 回呼び出されています。 最初のメソッド呼び出しでは、`^(\w+)\s(\d+)$` という正規表現が使用され、オプションは設定されていません。 出力結果が示すように、正規表現エンジンは入力パターンを入力文字列の先頭および末尾と一致させることができないので、一致は検出されません。 2 番目のメソッド呼び出しでは、正規表現は `^(\w+)\s(\d+)\r?$` に変更されており、オプションは [RegexOptions.Multiline](xref:System.Text.RegularExpressions.RegexOptions.Multiline) に設定されています。 出力結果が示すように、名前とスコアの照合は正常に行われ、スコアは降順で表示されています。

```csharp
using System;
using System.Collections.Generic;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      SortedList<int, string> scores = new SortedList<int, string>(new DescendingComparer<int>());

      string input = "Joe 164\n" + 
                     "Sam 208\n" + 
                     "Allison 211\n" + 
                     "Gwen 171\n"; 
      string pattern = @"^(\w+)\s(\d+)$";
      bool matched = false;

      Console.WriteLine("Without Multiline option:");
      foreach (Match match in Regex.Matches(input, pattern))
      {
         scores.Add(Int32.Parse(match.Groups[2].Value), (string) match.Groups[1].Value);
         matched = true;
      }
      if (! matched)
         Console.WriteLine("   No matches.");
      Console.WriteLine();

      // Redefine pattern to handle multiple lines.
      pattern = @"^(\w+)\s(\d+)\r*$";
      Console.WriteLine("With multiline option:");
      foreach (Match match in Regex.Matches(input, pattern, RegexOptions.Multiline))
         scores.Add(Int32.Parse(match.Groups[2].Value), (string) match.Groups[1].Value);

      // List scores in descending order. 
      foreach (KeyValuePair<int, string> score in scores)
         Console.WriteLine("{0}: {1}", score.Value, score.Key);
   }
}

public class DescendingComparer<T> : IComparer<T>
{
   public int Compare(T x, T y)
   {
      return Comparer<T>.Default.Compare(x, y) * -1;       
   }
}
// The example displays the following output:
//   Without Multiline option:
//      No matches.
//   
//   With multiline option:
//   Allison: 211
//   Sam: 208
//   Gwen: 171
//   Joe: 164
```

```vb
Imports System.Collections.Generic
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim scores As New SortedList(Of Integer, String)(New DescendingComparer(Of Integer)())

      Dim input As String = "Joe 164" + vbCrLf + _
                            "Sam 208" + vbCrLf + _
                            "Allison 211" + vbCrLf + _
                            "Gwen 171" + vbCrLf
      Dim pattern As String = "^(\w+)\s(\d+)$"
      Dim matched As Boolean = False

      Console.WriteLine("Without Multiline option:")
      For Each match As Match In Regex.Matches(input, pattern)
         scores.Add(CInt(match.Groups(2).Value), match.Groups(1).Value)
         matched = True
      Next
      If Not matched Then Console.WriteLine("   No matches.")
      Console.WriteLine()

      ' Redefine pattern to handle multiple lines.
      pattern = "^(\w+)\s(\d+)\r*$"
      Console.WriteLine("With multiline option:")
      For Each match As Match In Regex.Matches(input, pattern, RegexOptions.Multiline)
         scores.Add(CInt(match.Groups(2).Value), match.Groups(1).Value)
      Next
      ' List scores in descending order. 
      For Each score As KeyValuePair(Of Integer, String) In scores
         Console.WriteLine("{0}: {1}", score.Value, score.Key)
      Next
   End Sub
End Module

Public Class DescendingComparer(Of T) : Implements IComparer(Of T)
   Public Function Compare(x As T, y As T) As Integer _
          Implements IComparer(Of T).Compare
      Return Comparer(Of T).Default.Compare(x, y) * -1       
   End Function
End Class
' The example displays the following output:
'    Without Multiline option:
'       No matches.
'    
'    With multiline option:
'    Allison: 211
'    Sam: 208
'    Gwen: 171
'    Joe: 164
```

正規表現パターン `^(\w+)\s(\d+)\r*$` は、次の表に示すように定義されています。

パターン | 説明
------- | ----------- 
`^` | 行の先頭から始まります。
`(\w+)` | 1 つ以上の単語文字に一致します。 これが最初のキャプチャ グループです。
`\s` | 空白文字と一致します。
`(\d+)` | 1 個以上の 10 進数と一致します。 これが 2 番目のキャプチャ グループです。
`\r?` | 0 個または 1 個の復帰文字と一致します。
`$` | 行の末尾で終了します。
 
次の例は、前の例と等価ですが、インライン オプション **(?m)** を使用して複数行オプションを設定している点が異なります。

```csharp
using System;
using System.Collections.Generic;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      SortedList<int, string> scores = new SortedList<int, string>(new DescendingComparer<int>());

      string input = "Joe 164\n" +  
                     "Sam 208\n" +  
                     "Allison 211\n" +  
                     "Gwen 171\n"; 
      string pattern = @"(?m)^(\w+)\s(\d+)\r*$";

      foreach (Match match in Regex.Matches(input, pattern, RegexOptions.Multiline))
         scores.Add(Convert.ToInt32(match.Groups[2].Value), match.Groups[1].Value);

      // List scores in descending order. 
      foreach (KeyValuePair<int, string> score in scores)
         Console.WriteLine("{0}: {1}", score.Value, score.Key);
   }
}

public class DescendingComparer<T> : IComparer<T>
{
   public int Compare(T x, T y) 
   {
      return Comparer<T>.Default.Compare(x, y) * -1;       
   }
}
// The example displays the following output:
//    Allison: 211
//    Sam: 208
//    Gwen: 171
//    Joe: 164
```

```vb
Imports System.Collections.Generic
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim scores As New SortedList(Of Integer, String)(New DescendingComparer(Of Integer)())

      Dim input As String = "Joe 164" + vbCrLf + _
                            "Sam 208" + vbCrLf + _
                            "Allison 211" + vbCrLf + _
                            "Gwen 171" + vbCrLf
      Dim pattern As String = "(?m)^(\w+)\s(\d+)\r*$"

      For Each match As Match In Regex.Matches(input, pattern, RegexOptions.Multiline)
         scores.Add(CInt(match.Groups(2).Value), match.Groups(1).Value)
      Next
      ' List scores in descending order. 
      For Each score As KeyValuePair(Of Integer, String) In scores
         Console.WriteLine("{0}: {1}", score.Value, score.Key)
      Next
   End Sub
End Module

Public Class DescendingComparer(Of T) : Implements IComparer(Of T)
   Public Function Compare(x As T, y As T) As Integer _
          Implements IComparer(Of T).Compare
      Return Comparer(Of T).Default.Compare(x, y) * -1       
   End Function
End Class
' The example displays the following output:
'    Allison: 211
'    Sam: 208
'    Gwen: 171
'    Joe: 164
```

## <a name="singleline-mode"></a>単一行モード

[RegexOptions.Singleline](xref:System.Text.RegularExpressions.RegexOptions.Singleline) オプションまたは s インライン オプションを指定すると、正規表現エンジンでは、入力文字列が単一行で構成されているかのように処理されます。 具体的には、ピリオド (**.**) 言語要素の動作を変更して、改行文字 (**\n** または \u000A) を除く任意の文字ではなく、改行文字を含む任意の 1 文字と一致するようにします。

以下の例には、動作が図示されています。 言語要素は [RegexOptions.Singleline](xref:System.Text.RegularExpressions.RegexOptions.Singleline) オプションの使用時に変わります。 正規表現 `^.+` は文字列の先頭から開始し、すべての文字と一致します。 既定では、照合は 1 行目の末尾で終了します。正規表現パターンは復帰文字 **\r** (\u000D) と一致しますが、**\n** とは一致しません。 [RegexOptions.Singleline](xref:System.Text.RegularExpressions.RegexOptions.Singleline) オプションは入力文字列全体を単一行として解釈するので、**\n** を含む入力文字列内のすべての文字と一致します。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = "^.+";
      string input = "This is one line and" + Environment.NewLine + "this is the second.";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine(Regex.Escape(match.Value));

      Console.WriteLine();
      foreach (Match match in Regex.Matches(input, pattern, RegexOptions.Singleline))
         Console.WriteLine(Regex.Escape(match.Value));
   }
}
// The example displays the following output:
//       This\ is\ one\ line\ and\r
//       
//       This\ is\ one\ line\ and\r\nthis\ is\ the\ second\.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "^.+"
      Dim input As String = "This is one line and" + vbCrLf + "this is the second."
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine(Regex.Escape(match.Value))
      Next
      Console.WriteLine()
      For Each match As Match In Regex.Matches(input, pattern, RegexOptions.SingleLine)
         Console.WriteLine(Regex.Escape(match.Value))
      Next
   End Sub
End Module
' The example displays the following output:
'       This\ is\ one\ line\ and\r
'       
'       This\ is\ one\ line\ and\r\nthis\ is\ the\ second\.
```

次の例は、前の例と等価ですが、インライン オプション **(?s)** を使用して単一行モードを有効にしている点が異なります。 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {      
      string pattern = "(?s)^.+";
      string input = "This is one line and" + Environment.NewLine + "this is the second.";

      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine(Regex.Escape(match.Value));
   }
}
// The example displays the following output:
//       This\ is\ one\ line\ and\r\nthis\ is\ the\ second\.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "(?s)^.+"
      Dim input As String = "This is one line and" + vbCrLf + "this is the second."

      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine(Regex.Escape(match.Value))
      Next
   End Sub
End Module
' The example displays the following output:
'       This\ is\ one\ line\ and\r\nthis\ is\ the\ second\.
```

## <a name="explicit-captures-only"></a>明示的なキャプチャのみ

既定では、キャプチャ グループは正規表現パターンでかっこを使用することで定義されます。 名前付きのグループには **(?<**_name_**>** _subexpression_**)** 言語オプションで名前または番号が与えられるのに対して、名前のないグループにはインデックスでアクセスできます。 [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) オブジェクトでは、名前のないグループが名前付きのグループよりも優先されます。 

グループ化構成体は通常、複数の言語要素に量指定子を適用する場合にのみ使用され、キャプチャされた部分文字列は対象になりません。 たとえば、次の正規表現について考えます。

```
\b\(?((\w+),?\s?)+[\.!?]\)?
```

この正規表現は、ドキュメントから文末がピリオド、感嘆符、または疑問符である文を抽出することのみを目的とし、結果の文 ([Match](xref:System.Text.RegularExpressions.Match) オブジェクトで表される) のみを対象としています。 コレクション内の個々の単語は対象ではありません。 

正規表現エンジンで [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) コレクション オブジェクトと [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) コレクション オブジェクトの両方を設定する必要があるので、キャプチャ グループが以後、使用されない場合は、この設定の処理が無駄になる可能性があります。 別の方法としては、[RegexOptions.ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture) オプションまたは **n** インライン オプションを使用して、**(?<**_name_**>** _subexpression_**)** 構成体によって指定された明示的な名前または番号付きのグループのみを有効なキャプチャ対象として指定する方法が挙げられます。 

次の例は、`\b\(?((\w+),?\s?)+[\.!?]\)?` 正規表現パターンによって返された一致に関する情報を示しています ([Match](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.Int32)) メソッドが [RegexOptions.ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture) オプションを使用して呼び出された場合、および使用せずに呼び出された場合)。 最初のメソッド呼び出しの出力結果が示すように、正規表現エンジンでは、キャプチャした部分文字列に関する情報に基づいて、[GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) コレクション オブジェクトおよび [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) コレクション オブジェクトが完全に設定されています。 2 番目のメソッドは、options を [RegexOptions.ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture) に設定して呼び出されているので、グループに関する情報をキャプチャしません。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "This is the first sentence. Is it the beginning " + 
                     "of a literary masterpiece? I think not. Instead, " + 
                     "it is a nonsensical paragraph.";
      string pattern = @"\b\(?((?>\w+),?\s?)+[\.!?]\)?";
      Console.WriteLine("With implicit captures:");
      foreach (Match match in Regex.Matches(input, pattern))
      {
         Console.WriteLine("The match: {0}", match.Value);
         int groupCtr = 0;
         foreach (Group group in match.Groups)
         {
            Console.WriteLine("   Group {0}: {1}", groupCtr, group.Value);
            groupCtr++;
            int captureCtr = 0;
            foreach (Capture capture in group.Captures)
            {
               Console.WriteLine("      Capture {0}: {1}", captureCtr, capture.Value);
               captureCtr++;
            }
         }
      }
      Console.WriteLine();
      Console.WriteLine("With explicit captures only:");
      foreach (Match match in Regex.Matches(input, pattern, RegexOptions.ExplicitCapture))
      {
         Console.WriteLine("The match: {0}", match.Value);
         int groupCtr = 0;
         foreach (Group group in match.Groups)
         {
            Console.WriteLine("   Group {0}: {1}", groupCtr, group.Value);
            groupCtr++;
            int captureCtr = 0;
            foreach (Capture capture in group.Captures)
            {
               Console.WriteLine("      Capture {0}: {1}", captureCtr, capture.Value);
               captureCtr++;
            }
         }
      }
   }
}
// The example displays the following output:
//    With implicit captures:
//    The match: This is the first sentence.
//       Group 0: This is the first sentence.
//          Capture 0: This is the first sentence.
//       Group 1: sentence
//          Capture 0: This
//          Capture 1: is
//          Capture 2: the
//          Capture 3: first
//          Capture 4: sentence
//       Group 2: sentence
//          Capture 0: This
//          Capture 1: is
//          Capture 2: the
//          Capture 3: first
//          Capture 4: sentence
//    The match: Is it the beginning of a literary masterpiece?
//       Group 0: Is it the beginning of a literary masterpiece?
//          Capture 0: Is it the beginning of a literary masterpiece?
//       Group 1: masterpiece
//          Capture 0: Is
//          Capture 1: it
//          Capture 2: the
//          Capture 3: beginning
//          Capture 4: of
//          Capture 5: a
//          Capture 6: literary
//          Capture 7: masterpiece
//       Group 2: masterpiece
//          Capture 0: Is
//          Capture 1: it
//          Capture 2: the
//          Capture 3: beginning
//          Capture 4: of
//          Capture 5: a
//          Capture 6: literary
//          Capture 7: masterpiece
//    The match: I think not.
//       Group 0: I think not.
//          Capture 0: I think not.
//       Group 1: not
//          Capture 0: I
//          Capture 1: think
//          Capture 2: not
//       Group 2: not
//          Capture 0: I
//          Capture 1: think
//          Capture 2: not
//    The match: Instead, it is a nonsensical paragraph.
//       Group 0: Instead, it is a nonsensical paragraph.
//          Capture 0: Instead, it is a nonsensical paragraph.
//       Group 1: paragraph
//          Capture 0: Instead,
//          Capture 1: it
//          Capture 2: is
//          Capture 3: a
//          Capture 4: nonsensical
//          Capture 5: paragraph
//       Group 2: paragraph
//          Capture 0: Instead
//          Capture 1: it
//          Capture 2: is
//          Capture 3: a
//          Capture 4: nonsensical
//          Capture 5: paragraph
//    
//    With explicit captures only:
//    The match: This is the first sentence.
//       Group 0: This is the first sentence.
//          Capture 0: This is the first sentence.
//    The match: Is it the beginning of a literary masterpiece?
//       Group 0: Is it the beginning of a literary masterpiece?
//          Capture 0: Is it the beginning of a literary masterpiece?
//    The match: I think not.
//       Group 0: I think not.
//          Capture 0: I think not.
//    The match: Instead, it is a nonsensical paragraph.
//       Group 0: Instead, it is a nonsensical paragraph.
//          Capture 0: Instead, it is a nonsensical paragraph.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "This is the first sentence. Is it the beginning " + _
                            "of a literary masterpiece? I think not. Instead, " + _
                            "it is a nonsensical paragraph."
      Dim pattern As String = "\b\(?((?>\w+),?\s?)+[\.!?]\)?"
      Console.WriteLine("With implicit captures:")
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("The match: {0}", match.Value)
         Dim groupCtr As Integer = 0
         For Each group As Group In match.Groups
            Console.WriteLine("   Group {0}: {1}", groupCtr, group.Value)
            groupCtr += 1
            Dim captureCtr As Integer = 0
            For Each capture As Capture In group.Captures
               Console.WriteLine("      Capture {0}: {1}", captureCtr, capture.Value)
               captureCtr += 1
            Next
         Next
      Next
      Console.WriteLine()
      Console.WriteLine("With explicit captures only:")
      For Each match As Match In Regex.Matches(input, pattern, RegexOptions.ExplicitCapture)
         Console.WriteLine("The match: {0}", match.Value)
         Dim groupCtr As Integer = 0
         For Each group As Group In match.Groups
            Console.WriteLine("   Group {0}: {1}", groupCtr, group.Value)
            groupCtr += 1
            Dim captureCtr As Integer = 0
            For Each capture As Capture In group.Captures
               Console.WriteLine("      Capture {0}: {1}", captureCtr, capture.Value)
               captureCtr += 1
            Next
         Next
      Next
   End Sub
End Module
' The example displays the following output:
'    With implicit captures:
'    The match: This is the first sentence.
'       Group 0: This is the first sentence.
'          Capture 0: This is the first sentence.
'       Group 1: sentence
'          Capture 0: This
'          Capture 1: is
'          Capture 2: the
'          Capture 3: first
'          Capture 4: sentence
'       Group 2: sentence
'          Capture 0: This
'          Capture 1: is
'          Capture 2: the
'          Capture 3: first
'          Capture 4: sentence
'    The match: Is it the beginning of a literary masterpiece?
'       Group 0: Is it the beginning of a literary masterpiece?
'          Capture 0: Is it the beginning of a literary masterpiece?
'       Group 1: masterpiece
'          Capture 0: Is
'          Capture 1: it
'          Capture 2: the
'          Capture 3: beginning
'          Capture 4: of
'          Capture 5: a
'          Capture 6: literary
'          Capture 7: masterpiece
'       Group 2: masterpiece
'          Capture 0: Is
'          Capture 1: it
'          Capture 2: the
'          Capture 3: beginning
'          Capture 4: of
'          Capture 5: a
'          Capture 6: literary
'          Capture 7: masterpiece
'    The match: I think not.
'       Group 0: I think not.
'          Capture 0: I think not.
'       Group 1: not
'          Capture 0: I
'          Capture 1: think
'          Capture 2: not
'       Group 2: not
'          Capture 0: I
'          Capture 1: think
'          Capture 2: not
'    The match: Instead, it is a nonsensical paragraph.
'       Group 0: Instead, it is a nonsensical paragraph.
'          Capture 0: Instead, it is a nonsensical paragraph.
'       Group 1: paragraph
'          Capture 0: Instead,
'          Capture 1: it
'          Capture 2: is
'          Capture 3: a
'          Capture 4: nonsensical
'          Capture 5: paragraph
'       Group 2: paragraph
'          Capture 0: Instead
'          Capture 1: it
'          Capture 2: is
'          Capture 3: a
'          Capture 4: nonsensical
'          Capture 5: paragraph
'    
'    With explicit captures only:
'    The match: This is the first sentence.
'       Group 0: This is the first sentence.
'          Capture 0: This is the first sentence.
'    The match: Is it the beginning of a literary masterpiece?
'       Group 0: Is it the beginning of a literary masterpiece?
'          Capture 0: Is it the beginning of a literary masterpiece?
'    The match: I think not.
'       Group 0: I think not.
'          Capture 0: I think not.
'    The match: Instead, it is a nonsensical paragraph.
'       Group 0: Instead, it is a nonsensical paragraph.
'          Capture 0: Instead, it is a nonsensical paragraph.
```

正規表現パターン `\b\(?((?>\w+),?\s?)+[\.!?]\)?` は、次の表に示すように定義されています。

パターン | 説明
------- | ----------- 
`\b` | ワード境界から始まります。
`\(?` | 左かっこ ("(") の 0 回または 1 回の繰り返しと一致します。
`(?>\w+),?` | 1 個以上の単語文字の後に 0 個または 1 個のコンマが続くパターンと一致します。 単語文字の照合中にバックトラックは実行されません。
`\s?` | 0 個または 1 個の空白文字と一致します。
`((\w+),?\s?)+` | 1 個以上の単語文字、0 個または 1 個のコンマ、および 0 個または 1 個の空白文字が 1 回以上続くパターンと一致します。
`[\.!?]\)?` | 3 種類の区切り記号のいずれかの後に 0 個または 1 個の右かっこ (")") が続くパターンと一致します。
 
**(?n)** インライン要素を使用して、自動的なキャプチャを抑制することもできます。 次の例では、前の例の正規表現パターンを変更して、**(?n)** インライン要素を [RegexOptions.ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture) オプションの代わりに使用しています。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "This is the first sentence. Is it the beginning " + 
                     "of a literary masterpiece? I think not. Instead, " + 
                     "it is a nonsensical paragraph.";
      string pattern = @"(?n)\b\(?((?>\w+),?\s?)+[\.!?]\)?";

      foreach (Match match in Regex.Matches(input, pattern))
      {
         Console.WriteLine("The match: {0}", match.Value);
         int groupCtr = 0;
         foreach (Group group in match.Groups)
         {
            Console.WriteLine("   Group {0}: {1}", groupCtr, group.Value);
            groupCtr++;
            int captureCtr = 0;
            foreach (Capture capture in group.Captures)
            {
               Console.WriteLine("      Capture {0}: {1}", captureCtr, capture.Value);
               captureCtr++;
            }
         }
      }
   }
}
// The example displays the following output:
//       The match: This is the first sentence.
//          Group 0: This is the first sentence.
//             Capture 0: This is the first sentence.
//       The match: Is it the beginning of a literary masterpiece?
//          Group 0: Is it the beginning of a literary masterpiece?
//             Capture 0: Is it the beginning of a literary masterpiece?
//       The match: I think not.
//          Group 0: I think not.
//             Capture 0: I think not.
//       The match: Instead, it is a nonsensical paragraph.
//          Group 0: Instead, it is a nonsensical paragraph.
//             Capture 0: Instead, it is a nonsensical paragraph.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "This is the first sentence. Is it the beginning " + _
                            "of a literary masterpiece? I think not. Instead, " + _
                            "it is a nonsensical paragraph."
      Dim pattern As String = "(?n)\b\(?((?>\w+),?\s?)+[\.!?]\)?"

      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("The match: {0}", match.Value)
         Dim groupCtr As Integer = 0
         For Each group As Group In match.Groups
            Console.WriteLine("   Group {0}: {1}", groupCtr, group.Value)
            groupCtr += 1
            Dim captureCtr As Integer = 0
            For Each capture As Capture In group.Captures
               Console.WriteLine("      Capture {0}: {1}", captureCtr, capture.Value)
               captureCtr += 1
            Next
         Next
      Next
   End Sub
End Module
' The example displays the following output:
'       The match: This is the first sentence.
'          Group 0: This is the first sentence.
'             Capture 0: This is the first sentence.
'       The match: Is it the beginning of a literary masterpiece?
'          Group 0: Is it the beginning of a literary masterpiece?
'             Capture 0: Is it the beginning of a literary masterpiece?
'       The match: I think not.
'          Group 0: I think not.
'             Capture 0: I think not.
'       The match: Instead, it is a nonsensical paragraph.
'          Group 0: Instead, it is a nonsensical paragraph.
'             Capture 0: Instead, it is a nonsensical paragraph.
```

最後に、インライン グループ要素 **(?n:)** を使用して、グループごとに自動的なキャプチャを抑制することもできます。 次の例では、前のパターンを変更して、外部グループ `((?>\w+),?\s?)` で名前のないキャプチャを抑制しています。 この処理では、内部グループでの名前のないキャプチャも抑制されることに注意してください。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "This is the first sentence. Is it the beginning " + 
                     "of a literary masterpiece? I think not. Instead, " + 
                     "it is a nonsensical paragraph.";
      string pattern = @"\b\(?(?n:(?>\w+),?\s?)+[\.!?]\)?";

      foreach (Match match in Regex.Matches(input, pattern))
      {
         Console.WriteLine("The match: {0}", match.Value);
         int groupCtr = 0;
         foreach (Group group in match.Groups)
         {
            Console.WriteLine("   Group {0}: {1}", groupCtr, group.Value);
            groupCtr++;
            int captureCtr = 0;
            foreach (Capture capture in group.Captures)
            {
               Console.WriteLine("      Capture {0}: {1}", captureCtr, capture.Value);
               captureCtr++;
            }
         }
      }
   }
}
// The example displays the following output:
//       The match: This is the first sentence.
//          Group 0: This is the first sentence.
//             Capture 0: This is the first sentence.
//       The match: Is it the beginning of a literary masterpiece?
//          Group 0: Is it the beginning of a literary masterpiece?
//             Capture 0: Is it the beginning of a literary masterpiece?
//       The match: I think not.
//          Group 0: I think not.
//             Capture 0: I think not.
//       The match: Instead, it is a nonsensical paragraph.
//          Group 0: Instead, it is a nonsensical paragraph.
//             Capture 0: Instead, it is a nonsensical paragraph.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "This is the first sentence. Is it the beginning " + _
                            "of a literary masterpiece? I think not. Instead, " + _
                            "it is a nonsensical paragraph."
      Dim pattern As String = "\b\(?(?n:(?>\w+),?\s?)+[\.!?]\)?"

      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("The match: {0}", match.Value)
         Dim groupCtr As Integer = 0
         For Each group As Group In match.Groups
            Console.WriteLine("   Group {0}: {1}", groupCtr, group.Value)
            groupCtr += 1
            Dim captureCtr As Integer = 0
            For Each capture As Capture In group.Captures
               Console.WriteLine("      Capture {0}: {1}", captureCtr, capture.Value)
               captureCtr += 1
            Next
         Next
      Next
   End Sub
End Module
' The example displays the following output:
'       The match: This is the first sentence.
'          Group 0: This is the first sentence.
'             Capture 0: This is the first sentence.
'       The match: Is it the beginning of a literary masterpiece?
'          Group 0: Is it the beginning of a literary masterpiece?
'             Capture 0: Is it the beginning of a literary masterpiece?
'       The match: I think not.
'          Group 0: I think not.
'             Capture 0: I think not.
'       The match: Instead, it is a nonsensical paragraph.
'          Group 0: Instead, it is a nonsensical paragraph.
'             Capture 0: Instead, it is a nonsensical paragraph.
```

## <a name="compiled-regular-expressions"></a>コンパイルされた正規表現

既定では、.NET の正規表現は解釈の対象になります。 [Regex](xref:System.Text.RegularExpressions.Regex) オブジェクトがインスタンス化されるか、静的 [Regex](xref:System.Text.RegularExpressions.Regex) メソッドが呼び出されたときに、正規表現パターンはカスタム オペコードのセットに解析され、インタープリターがこのオペコードに基づいて正規表現を実行します。 この場合、正規表現エンジンの初期化処理を優先すると、実行時のパフォーマンスが低下するというトレードオフが伴います。

正規表現を逐次解釈する代わりに、[RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) オプションを使用してコンパイルされた正規表現を使用できます。 この場合、パターンは正規表現エンジンに渡され、オペコードのセットに解析されてから、Microsoft Intermediate Language (MSIL) に変換されます。変換されたコードは、共通言語ランタイムに直接渡すことができます。 コンパイルされた正規表現を使用すると、初期化処理に時間を要しますが、実行時のパフォーマンスは向上します。

> [!NOTE]
> 正規表現をコンパイルするには、[RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) 値を [Regex](xref:System.Text.RegularExpressions.Regex) クラス コンストラクターまたは静的パターン一致メソッドの options パラメーターに渡す必要があります。 インライン オプションとしては使用できません。 
 

コンパイルされた正規表現は、静的正規表現とインスタンス正規表現の両方の呼び出しに使用できます。 静的正規表現では、[RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) オプションは正規表現パターン一致メソッドの options パラメーターに渡されます。 インスタンス正規表現では、[Regex](xref:System.Text.RegularExpressions.Regex) クラス コンストラクターの options パラメーターに渡されます。 どちらの場合も、パフォーマンスが向上します。 

ただし、パフォーマンスが向上するのは、次の条件を満たしている場合に限定されます。

* 特定の正規表現を表す [Regex](xref:System.Text.RegularExpressions.Regex) オブジェクトが正規表現パターン一致メソッドの複数の呼び出しで使用されている。

* [Regex](xref:System.Text.RegularExpressions.Regex) オブジェクトがスコープの外に出ることが許可されておらず、再利用できる。

* 静的正規表現が正規表現パターン一致メソッドの複数の呼び出しで使用されている (静的メソッド呼び出しで使用した正規表現は正規表現エンジンによってキャッシュされるので、パフォーマンスの向上が可能になります)。 

## <a name="ignore-white-space"></a>空白を無視

既定では、正規表現パターンに含まれる空白には重要な意味があり、正規表現エンジンでは、入力文字列内の空白文字との照合が強制されます。 この結果、正規表現 `"\b\w+\s"` および `"\b\w+ "` は、ほぼ等価な正規表現であると言えます。 さらに、シャープ記号 (**#**) が正規表現パターンに含まれている場合は、照合する対象のリテラル文字として解釈されます。

[RegexOptions.IgnorePatternWhitespace](xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace) オプションまたは **x** インライン オプションはこの既定の動作を次のように変えます。

* 正規表現パターンでエスケープされていない空白は無視されます。 空白文字を正規表現パターンの一部に含めるには、エスケープする必要があります (たとえば、**\s** や "**\**")。

* シャープ記号 (**#**) は、リテラル文字ではなく、コメントの先頭として解釈されます。 **#** 記号から文字列の末尾まで、正規表現パターンに含まれるすべてのテキストは、コメントとして解釈されます。

ただし次に説明する状況では、[RegexOptions.IgnorePatternWhitespace](xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace) オプションを使用している場合でも、正規表現の空白文字は無視されません。 

* 文字クラス内の空白は常に、空白として解釈されます。 たとえば、正規表現パターン `[ .,;:]` は、空白文字、ピリオド、コンマ、セミコロン、またはコロンの任意の 1 文字と一致します。 

* かっこで囲まれた量指定子 (**{**_n_**}**、**{**_n_**,}**、**{**_n_**,**_m_**}** など) には空白を使用できません。 たとえば、正規表現パターン **\d{1. 3}** は、空白文字が含まれているため、1 ～ 3 桁の数値のどのシーケンスにも一致しません。 

* 言語要素を導入する文字シーケンス内では空白を使用できません。 例: 

    * 言語要素 **(?:**_subexpression_**)** は非キャプチャ グループを表し、要素の **(?:** 部分には空白を埋め込むことはできません。 パターン **(? :**_subexpression_**)** は、正規表現エンジンで解析できないため実行時に [ArgumentException](xref:System.ArgumentException) をスローします。パターン **(? :**_subexpression_**)** は *subexpression* に一致しません。

    * Unicode カテゴリまたは名前付きブロックを表す言語要素 **\p{**_name_**}** の **\p{** 部分には、空白を埋め込むことはできません。 空白を追加すると、この要素は実行時に [ArgumentException](xref:System.ArgumentException) をスローします。 

このオプションを有効にすると、多くの場合、解析や理解が困難な正規表現を簡略化できます。 正規表現が読みやすくなり、説明も記述できます。 

次の例では、正規表現パターンを定義しています。

`\b \(? ( (?>\w+) ,?\s? )+ [\.!?] \)? # Matches an entire sentence`。

このパターンは、「[明示的なキャプチャのみ](#explicit-captures-only)」セクションで定義したパターンと似ています。ただし、[RegexOptions.IgnorePatternWhitespace](xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace) オプションを使用して、パターンの空白を無視している点が異なります。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "This is the first sentence. Is it the beginning " + 
                     "of a literary masterpiece? I think not. Instead, " + 
                     "it is a nonsensical paragraph.";
      string pattern = @"\b\(?((?>\w+),?\s?)+[\.!?]\)?";

      foreach (Match match in Regex.Matches(input, pattern, RegexOptions.IgnorePatternWhitespace))
         Console.WriteLine(match.Value);
   }
}
// The example displays the following output:
//       This is the first sentence.
//       Is it the beginning of a literary masterpiece?
//       I think not.
//       Instead, it is a nonsensical paragraph.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "This is the first sentence. Is it the beginning " + _
                            "of a literary masterpiece? I think not. Instead, " + _
                            "it is a nonsensical paragraph."
      Dim pattern As String = "\b \(? ( (?>\w+) ,?\s? )+  [\.!?] \)? # Matches an entire sentence."

      For Each match As Match In Regex.Matches(input, pattern, RegexOptions.IgnorePatternWhitespace)
         Console.WriteLine(match.Value)
      Next
   End Sub
End Module
' The example displays the following output:
'       This is the first sentence.
'       Is it the beginning of a literary masterpiece?
'       I think not.
'       Instead, it is a nonsensical paragraph.
```

次の例では、**(?x)** インライン オプションを使用して、パターンの空白を無視しています。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "This is the first sentence. Is it the beginning " + 
                     "of a literary masterpiece? I think not. Instead, " + 
                     "it is a nonsensical paragraph.";
      string pattern = @"(?x)\b \(? ( (?>\w+) ,?\s? )+  [\.!?] \)? # Matches an entire sentence.";

      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine(match.Value);
   }
}
// The example displays the following output:
//       This is the first sentence.
//       Is it the beginning of a literary masterpiece?
//       I think not.
//       Instead, it is a nonsensical paragraph.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "This is the first sentence. Is it the beginning " + _
                            "of a literary masterpiece? I think not. Instead, " + _
                            "it is a nonsensical paragraph."
      Dim pattern As String = "(?x)\b \(? ( (?>\w+) ,?\s? )+  [\.!?] \)? # Matches an entire sentence."

      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine(match.Value)
      Next
   End Sub
End Module
' The example displays the following output:
'       This is the first sentence.
'       Is it the beginning of a literary masterpiece?
'       I think not.
'       Instead, it is a nonsensical paragraph.
```

## <a name="righttoleft-mode"></a>右から左モード

既定では、正規表現エンジンは左から右の方向に検索します。 この検索の方向を反転するには、[RegexOptions.RightToLeft](xref:System.Text.RegularExpressions.RegexOptions.RightToLeft) オプションを使用します。 検索は、文字列の最後の文字位置から自動的に開始されます。 [Regex.Match(String, Int32)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.Int32)) など、開始位置のパラメーターを含むパターン一致メソッドの場合は、検索の開始位置である右端の文字位置のインデックスが開始位置になります。 

> [!NOTE]
> 右から左モードを使用するには、[RegexOptions.RightToLeft](xref:System.Text.RegularExpressions.RegexOptions.RightToLeft) 値を [Regex](xref:System.Text.RegularExpressions.Regex) クラス コンストラクターまたは静的パターン一致メソッドの options パラメーターに渡す必要があります。 インライン オプションとしては使用できません。 
 

[RegexOptions.RightToLeft](xref:System.Text.RegularExpressions.RegexOptions.RightToLeft) オプションは、検索の方向のみを変更します。このオプションを指定すると、正規表現パターンが右から左に解釈されるわけではありません。 たとえば、正規表現 `\bb\w+\s` は、文字 "b" で始まる単語とそれに続く空白文字と一致します。 次の例では、入力文字列は、1 文字以上の "b" を含む 3 つの単語で構成されています。 最初の単語は "b" で始まり、2 番目の単語は "b" で終わり、3 番目の単語は語内に 2 文字の "b" を含んでいます。 この例の出力結果が示すように、最初の単語のみが正規表現パターンと一致しています。 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\bb\w+\s";
      string input = "builder rob rabble";
      foreach (Match match in Regex.Matches(input, pattern, RegexOptions.RightToLeft))
         Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);     
   }
}
// The example displays the following output:
//       'builder ' found at position 0.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\bb\w+\s"
      Dim input As String = "builder rob rabble"
      For Each match As Match In Regex.Matches(input, pattern, RegexOptions.RightToLeft)
         Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)     
      Next
   End Sub
End Module
' The example displays the following output:
'       'builder ' found at position 0.
```

先読みアサーション (**(?**=_subexpression_**)** 言語要素) と後読みアサーション (**(?<**=_subexpression_**)** 言語要素) では、方向が変更されないことにも注意してください。 先読みアサーションでは右方向へ、後読みアサーションでは左方向へ参照が行われます。 たとえば、正規表現 `(?<=\d{1,2}\s)\w+,?\s\d{4}` は後読みアサーションを使用して、月の名前の前にある日付をテストします。 次に、この正規表現は、月と年を照合しています。 先読みアサーションと後読みアサーションの詳細については、「[正規表現でのグループ化構成体](grouping.md)」を参照してください。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string[] inputs = { "1 May 1917", "June 16, 2003" };
      string pattern = @"(?<=\d{1,2}\s)\w+,?\s\d{4}";

      foreach (string input in inputs)
      {
         Match match = Regex.Match(input, pattern, RegexOptions.RightToLeft);
         if (match.Success)
            Console.WriteLine("The date occurs in {0}.", match.Value);
         else
            Console.WriteLine("{0} does not match.", input);
      }
   }
}
// The example displays the following output:
//       The date occurs in May 1917.
//       June 16, 2003 does not match.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim inputs() As String = { "1 May 1917", "June 16, 2003" }
      Dim pattern As String = "(?<=\d{1,2}\s)\w+,?\s\d{4}"

      For Each input As String In inputs
         Dim match As Match = Regex.Match(input, pattern, RegexOptions.RightToLeft)
         If match.Success Then
            Console.WriteLine("The date occurs in {0}.", match.Value)
         Else
            Console.WriteLine("{0} does not match.", input)
         End If
      Next
   End Sub
End Module
' The example displays the following output:
'       The date occurs in May 1917.
'       June 16, 2003 does not match.
```

正規表現パターンは、次の表に示すように定義されています。

パターン | 説明
------- | ----------- 
`(?<=\d{1,2}\s)` | 一致の先頭の前には、1 桁または 2 桁の 10 進数とそれに続く空白が必要です。
`\w+` | 1 つ以上の単語文字に一致します。
`,?` | 0 個または 1 個のコンマと一致します。
`\s` | 空白文字と一致します。
`\d{4}` | 4 桁の 10 進数と一致します。
 
## <a name="ecmascript-matching-behavior"></a>ECMAScript 一致の動作

既定では、正規表現パターンを入力テキストに照合するときに、正規表現エンジンは標準の動作を使用します。 ただし、[RegexOptions.ECMAScript](xref:System.Text.RegularExpressions.RegexOptions.ECMAScript) オプションを使用することで、ECMAScript 一致の動作を使用するように正規表現エンジンに指示できます。 

> [!NOTE]
> ECMAScript 準拠の動作を使用するには、[RegexOptions.ECMAScript](xref:System.Text.RegularExpressions.RegexOptions.ECMAScript) 値を [Regex](xref:System.Text.RegularExpressions.Regex) クラス コンストラクターまたは静的パターン一致メソッドの options パラメーターに渡す必要があります。 インライン オプションとしては使用できません。 
 
[RegexOptions.ECMAScript](xref:System.Text.RegularExpressions.RegexOptions.ECMAScript) オプションは、[RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase) オプションか [RegexOptions.Multiline](xref:System.Text.RegularExpressions.RegexOptions.Multiline) オプションとのみ組み合わせることができます。 これ以外のオプションと同時に正規表現で使用すると、[ArgumentOutOfRangeException](xref:System.ArgumentOutOfRangeException) が発生します。

ECMAScript と標準正規表現は、文字クラスの構文、自己参照キャプチャ グループ、および 8 進数と前方参照の解釈という 3 つの点で動作が異なります。 

* 文字クラスの構文。 標準正規表現が Unicode をサポートしているのに対して、ECMAScript は Unicode をサポートしていないので、ECMAScript の文字クラスの構文には制限が多く、文字クラスの言語要素によっては意味が異なります。 たとえば、ECMAScript は、Unicode カテゴリやブロック要素 (*\p* および **\P**) などの言語要素をサポートしていません。 同様に、単語文字と一致する **\w** 要素は、ECMAScript を使用した場合は **[a-zA-Z_0-9]** 文字クラスと等価になり、標準の動作を使用した場合は **[\p{Ll}\p{Lu}\p{Lt}\p{Lo}\p{Nd}\p{Pc}\p{Lm}]** と等価になります。 詳細については、「[正規表現の文字クラス](classes.md)」を参照してください。

  次の例は、標準パターン一致と ECMAScript パターン一致の違いを示しています。 この例では、単語とそれに続く空白文字と一致する正規表現 `\b(\w+\s*)+` を定義しています。 入力は 2 つの文字列で構成され、一方の文字列ではラテン語文字セットが使用され、もう一方の文字列ではキリル文字セットが使用されています。 出力結果が示すように、ECMAScript 一致を使用した [Regex.IsMatch(String, String, RegexOptions)](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) メソッドの呼び出しではキリル文字の単語が照合されないのに対して、標準一致を使用したメソッドの呼び出しではキリル文字の単語が照合されています。 

  ```csharp
  using System;
  using System.Text.RegularExpressions;
  
  public class Example
  {
     public static void Main()
     {
        string[] values = { "целый мир", "the whole world" };
        string pattern = @"\b(\w+\s*)+";
        foreach (var value in values)
        {
           Console.Write("Canonical matching: ");
           if (Regex.IsMatch(value, pattern))
              Console.WriteLine("'{0}' matches the pattern.", value);
           else
              Console.WriteLine("{0} does not match the pattern.", value);
  
           Console.Write("ECMAScript matching: ");
           if (Regex.IsMatch(value, pattern, RegexOptions.ECMAScript))
              Console.WriteLine("'{0}' matches the pattern.", value);
           else
              Console.WriteLine("{0} does not match the pattern.", value);
           Console.WriteLine();
        }
     }
  }
  // The example displays the following output:
  //       Canonical matching: 'целый мир' matches the pattern.
  //       ECMAScript matching: целый мир does not match the pattern.
  //       
  //       Canonical matching: 'the whole world' matches the pattern.
  //       ECMAScript matching: 'the whole world' matches the pattern.
  ```

  ```vb
  Imports System.Text.RegularExpressions

  Module Example
     Public Sub Main()
        Dim values() As String = { "целый мир", "the whole world" }
        Dim pattern As String = "\b(\w+\s*)+"
        For Each value In values
           Console.Write("Canonical matching: ")
           If Regex.IsMatch(value, pattern)
              Console.WriteLine("'{0}' matches the pattern.", value)
           Else
              Console.WriteLine("{0} does not match the pattern.", value)
           End If

           Console.Write("ECMAScript matching: ")
           If Regex.IsMatch(value, pattern, RegexOptions.ECMAScript)
              Console.WriteLine("'{0}' matches the pattern.", value)
           Else
              Console.WriteLine("{0} does not match the pattern.", value)
           End If
           Console.WriteLine()
        Next
     End Sub
  End Module
  ' The example displays the following output:
  '       Canonical matching: 'целый мир' matches the pattern.
  '       ECMAScript matching: целый мир does not match the pattern.
  '       
  '       Canonical matching: 'the whole world' matches the pattern.
  '       ECMAScript matching: 'the whole world' matches the pattern.
  ```

* 自己参照キャプチャ グループ。 正規表現キャプチャ クラスが、それ自体への前方参照を持っている場合は、キャプチャの反復処理のたびに更新する必要があります。 次の例に示すように、この機能では、正規表現 `((a+)(\1) ?)+` による入力文字列 " aa aaaa aaaaaa "との照合は、ECMAScript を使用した場合は有効になり、標準一致を使用した場合は無効になります。 

  ```csharp
  using System;
  using System.Text.RegularExpressions;

  public class Example
  {
     static string pattern;
  
     public static void Main()
     {
        string input = "aa aaaa aaaaaa "; 
        pattern = @"((a+)(\1) ?)+";
  
        // Match input using canonical matching.
        AnalyzeMatch(Regex.Match(input, pattern));

        // Match input using ECMAScript.
        AnalyzeMatch(Regex.Match(input, pattern, RegexOptions.ECMAScript));
     }   

     private static void AnalyzeMatch(Match m)
     {
        if (m.Success)
        {
           Console.WriteLine("'{0}' matches {1} at position {2}.",  
                             pattern, m.Value, m.Index);
           int grpCtr = 0;
           foreach (Group grp in m.Groups)
           {
              Console.WriteLine("   {0}: '{1}'", grpCtr, grp.Value);
              grpCtr++;
              int capCtr = 0;
              foreach (Capture cap in grp.Captures)
              {
                 Console.WriteLine("      {0}: '{1}'", capCtr, cap.Value);
                 capCtr++;
              }
           }
        }
        else
        {
           Console.WriteLine("No match found.");
        }   
        Console.WriteLine();
     }
  }
  // The example displays the following output:
  //    No match found.
  //    
  //    '((a+)(\1) ?)+' matches aa aaaa aaaaaa  at position 0.
  //       0: 'aa aaaa aaaaaa '
  //          0: 'aa aaaa aaaaaa '
  //       1: 'aaaaaa '
  //          0: 'aa '
  //          1: 'aaaa '
  //          2: 'aaaaaa '
  //       2: 'aa'
  //          0: 'aa'
  //          1: 'aa'
  //          2: 'aa'
  //       3: 'aaaa '
  //          0: ''
  //          1: 'aa '
  //          2: 'aaaa '
  ```

  ```vb
  Imports System.Text.RegularExpressions

  Module Example
     Dim pattern As String

     Public Sub Main()
        Dim input As String = "aa aaaa aaaaaa " 
        pattern = "((a+)(\1) ?)+"
  
        ' Match input using canonical matching.
        AnalyzeMatch(Regex.Match(input, pattern))

        ' Match input using ECMAScript.
        AnalyzeMatch(Regex.Match(input, pattern, RegexOptions.ECMAScript))
     End Sub   

     Private Sub AnalyzeMatch(m As Match)
        If m.Success
           Console.WriteLine("'{0}' matches {1} at position {2}.", _ 
                             pattern, m.Value, m.Index)
           Dim grpCtr As Integer = 0
           For Each grp As Group In m.Groups
              Console.WriteLine("   {0}: '{1}'", grpCtr, grp.Value)
              grpCtr += 1
              Dim capCtr As Integer = 0
              For Each cap As Capture In grp.Captures
                 Console.WriteLine("      {0}: '{1}'", capCtr, cap.Value)
                 capCtr += 1
              Next
           Next
        Else
           Console.WriteLine("No match found.")
        End If   
        Console.WriteLine()
     End Sub
  End Module
  ' The example displays the following output:
  '    No match found.
  '    
  '    '((a+)(\1) ?)+' matches aa aaaa aaaaaa  at position 0.
  '       0: 'aa aaaa aaaaaa '
  '          0: 'aa aaaa aaaaaa '
  '       1: 'aaaaaa '
  '          0: 'aa '
  '          1: 'aaaa '  
  '          2: 'aaaaaa '
  '       2: 'aa'
  '          0: 'aa'
  '          1: 'aa'
  '          2: 'aa'
  '       3: 'aaaa '
  '          0: ''
  '          1: 'aa '
  '          2: 'aaaa '
  ``

  The regular expression is defined as shown in the following table.

Pattern | Description
------- | ----------- 
`(a+)` | Match the letter "a" one or more times. This is the second capturing group.
`(\1)` | Match the substring captured by the first capturing group. This is the third capturing group.
`?` | Match zero or one space characters.
`((a+)(\1) ?)+` | Match the pattern of one or more "a" characters followed by a string that matches the first capturing group followed by zero or one space characters one or more times. This is the first capturing group.
  
* Resolution of ambiguities between octal escapes and backreferences. The following table summarizes the differences in octal versus backreference interpretation by canonical and ECMAScript regular expressions.

Regular expression | Canonical behavior | ECMAScript behavior
------------------ | ------------------ | ------------------- 
`\0` followed by 0 to 2 octal digits | Interpret as an octal. For example, `\044` is always interpreted as an octal value and means "**$**". | Same behavior.
**\** followed by a digit from 1 to 9, followed by no additional decimal digits | Interpret as a backreference. For example, \9 always means backreference 9, even if a ninth capturing group does not exist. If the capturing group does not exist, the regular expression parser throws an [ArgumentException](xref:System.ArgumentException). | If a single decimal digit capturing group exists, backreference to that digit. Otherwise, interpret the value as a literal.
**\** followed by a digit from 1 to 9, followed by additional decimal digits | Interpret the digits as a decimal value. If that capturing group exists, interpret the expression as a backreference. Otherwise, interpret the leading octal digits up to octal 377; that is, consider only the low 8 bits of the value. Interpret the remaining digits as literals. For example, in the expression `\3000`, if capturing group 300 exists, interpret as backreference 300; if capturing group 300 does not exist, interpret as octal 300 followed by 0. | Interpret as a backreference by converting as many digits as possible to a decimal value that can refer to a capture. If no digits can be converted, interpret as an octal by using the leading octal digits up to octal 377; interpret the remaining digits as literals.
 
## Comparison using the invariant culture

By default, when the regular expression engine performs case-insensitive comparisons, it uses the casing conventions of the current culture to determine equivalent uppercase and lowercase characters. 

However, this behavior is undesirable for some types of comparisons, particularly when comparing user input to the names of system resources, such as passwords, files, or URLs. The following example illustrates such as scenario. The code is intended to block access to any resource whose URL is prefaced with **FILE://**. The regular expression attempts a case-insensitive match with the string by using the regular expression `$FILE://`. However, when the current system culture is tr-TR (Turkish-Turkey), "I" is not the uppercase equivalent of "i". As a result, the call to the [Regex.IsMatch](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String)) method returns `false`, and access to the file is allowed. 

```csharp
CultureInfo defaultCulture = Thread.CurrentThread.CurrentCulture;
Thread.CurrentThread.CurrentCulture = new CultureInfo("tr-TR");

string input = "file://c:/Documents.MyReport.doc";
string pattern = "FILE://";

Console.WriteLine("Culture-sensitive matching ({0} culture)...", 
                  Thread.CurrentThread.CurrentCulture.Name);
if (Regex.IsMatch(input, pattern, RegexOptions.IgnoreCase))
   Console.WriteLine("URLs that access files are not allowed.");      
else
   Console.WriteLine("Access to {0} is allowed.", input);

Thread.CurrentThread.CurrentCulture = defaultCulture;
// The example displays the following output:
//       Culture-sensitive matching (tr-TR culture)...
//       Access to file://c:/Documents.MyReport.doc is allowed.
```

```vb
Dim defaultCulture As CultureInfo = Thread.CurrentThread.CurrentCulture
Thread.CurrentThread.CurrentCulture = New CultureInfo("tr-TR")

Dim input As String = "file://c:/Documents.MyReport.doc"
Dim pattern As String = "$FILE://"

Console.WriteLine("Culture-sensitive matching ({0} culture)...", _
                  Thread.CurrentThread.CurrentCulture.Name)
If Regex.IsMatch(input, pattern, RegexOptions.IgnoreCase) Then
   Console.WriteLine("URLs that access files are not allowed.")      
Else
   Console.WriteLine("Access to {0} is allowed.", input)
End If

Thread.CurrentThread.CurrentCulture = defaultCulture
' The example displays the following output:
'       Culture-sensitive matching (tr-TR culture)...
'       Access to file://c:/Documents.MyReport.doc is allowed.
```

> [!NOTE]
>   大文字と小文字を区別する文字列比較とインバリアント カルチャを使用する文字列比較の詳細については、「[文字列を使用するためのベスト プラクティス](best-practices.md)」を参照してください。
 
現在のカルチャで大文字と小文字を区別しない比較を行う代わりに、[RegexOptions.CultureInvariant](xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant) オプションを指定すると、言語のカルチャの違いを無視して、インバリアント カルチャの規則を使用できます。

> [!NOTE]
> インバリアント カルチャを使用して比較を行うには、[RegexOptions.CultureInvariant](xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant) 値を [Regex](xref:System.Text.RegularExpressions.Regex) クラス コンストラクターまたは静的パターン一致メソッドの options パラメーターに渡す必要があります。 インライン オプションとしては使用できません。 
 
次の例は前の例と同じものですが、[RegexOptions.CultureInvariant](xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant) を含むオプションを指定して、静的メソッド [Regex.IsMatch(String, String, RegexOptions)](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) が呼び出されている点が異なります。 現在のカルチャがトルコ語 (トルコ) に設定されている場合でも、正規表現エンジンでは "FILE" と "file" が正常に一致し、ファイル リソースへのアクセスが拒否されます。 

```csharp
CultureInfo defaultCulture = Thread.CurrentThread.CurrentCulture;
Thread.CurrentThread.CurrentCulture = new CultureInfo("tr-TR");

string input = "file://c:/Documents.MyReport.doc";
string pattern = "FILE://";

Console.WriteLine("Culture-insensitive matching...");
if (Regex.IsMatch(input, pattern, 
                  RegexOptions.IgnoreCase | RegexOptions.CultureInvariant)) 
   Console.WriteLine("URLs that access files are not allowed.");
else
   Console.WriteLine("Access to {0} is allowed.", input);

Thread.CurrentThread.CurrentCulture = defaultCulture;
// The example displays the following output:
//       Culture-insensitive matching...
//       URLs that access files are not allowed.
```

```vb
Dim defaultCulture As CultureInfo = Thread.CurrentThread.CurrentCulture
Thread.CurrentThread.CurrentCulture = New CultureInfo("tr-TR")

Dim input As String = "file://c:/Documents.MyReport.doc"
Dim pattern As String = "$FILE://"

Console.WriteLine("Culture-insensitive matching...")
If Regex.IsMatch(input, pattern, _
               RegexOptions.IgnoreCase Or RegexOptions.CultureInvariant) Then
   Console.WriteLine("URLs that access files are not allowed.")      
Else
   Console.WriteLine("Access to {0} is allowed.", input)
End If
Thread.CurrentThread.CurrentCulture = defaultCulture
' The example displays the following output:
'        Culture-insensitive matching...
'        URLs that access files are not allowed.
```

## <a name="see-also"></a>関連項目

[正規表現言語 - クイック リファレンス](quick-ref.md)




<!--HONumber=Nov16_HO1-->


