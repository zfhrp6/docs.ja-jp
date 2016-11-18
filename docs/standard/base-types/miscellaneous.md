---
title: "正規表現でのその他のコンストラクト"
description: "正規表現でのその他のコンストラクト"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/29/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 478901dc-db6c-4d90-9d3b-f5cfdca2cbf5
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 4205d2a318849a7b24ac0f1fd65f7e8a23ec7f55

---

# <a name="miscellaneous-constructs-in-regular-expressions"></a>正規表現でのその他のコンストラクト


.NET の正規表現には、次の 3 つのその他の言語コンストラクトが含まれます。 1 つは、正規表現パターンの途中で特定の一致オプションを有効または無効にすることができます。 残りの 2 つは、正規表現にコメントを含めることができます。

## <a name="inline-options"></a>インライン オプション

この構文を使用して、正規表現の一部の特定のパターン一致オプションを設定または無効にできます。

```
(?imnsx-imnsx)
```

疑問符の後に有効にするオプション、マイナス記号の後に無効にするオプションを指定します。 各オプションの説明を次の表に示します。 各オプションの詳細については、「[正規表現のオプション](options.md)」を参照してください。

オプション | 説明
------ | ----------- 
**i** | 大文字と小文字を区別しない一致。
**m** | 複数行モードを指定します。
**n** | 明示的なキャプチャのみ (かっこはキャプチャ グループとして機能しません)。
**s** | 単一行モード。
**x** | エスケープされていない空白を無視し、x モード コメントを許可します。 
 
**(?imnsx-imnsx)** コンストラクトによって定義された正規表現オプションの変更は、囲んでいるグループの末尾まで有効です。

> [!NOTE]
> **(?imnsx-imnsx**:_subexpression_**)** グループ化コンストラクトは、部分式と同じ機能を提供します。 詳細については、「[正規表現でのグループ化構成体](grouping.md)」を参照してください。
 
次の例では **i**、**n**、および **x** オプションを使用して、大文字と小文字の区別をせず、明示的なキャプチャを有効にして、正規表現の途中の正規表現パターン内の空白を無視します。 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern; 
      string input = "double dare double Double a Drooling dog The Dreaded Deep";

      pattern = @"\b(D\w+)\s(d\w+)\b";
      // Match pattern using default options.
      foreach (Match match in Regex.Matches(input, pattern))
      {
         Console.WriteLine(match.Value);
         if (match.Groups.Count > 1)
            for (int ctr = 1; ctr < match.Groups.Count; ctr++) 
               Console.WriteLine("   Group {0}: {1}", ctr, match.Groups[ctr].Value);
      }
      Console.WriteLine();

      // Change regular expression pattern to include options.
      pattern = @"\b(D\w+)(?ixn) \s (d\w+) \b";
      // Match new pattern with options. 
      foreach (Match match in Regex.Matches(input, pattern))
      {
         Console.WriteLine(match.Value);
         if (match.Groups.Count > 1)
            for (int ctr = 1; ctr < match.Groups.Count; ctr++) 
               Console.WriteLine("   Group {0}: '{1}'", ctr, match.Groups[ctr].Value);
      }
   }
}
// The example displays the following output:
//       Drooling dog
//          Group 1: Drooling
//          Group 2: dog
//       
//       Drooling dog
//          Group 1: 'Drooling'
//       Dreaded Deep
//          Group 1: 'Dreaded'
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String 
      Dim input As String = "double dare double Double a Drooling dog The Dreaded Deep"

      pattern = "\b(D\w+)\s(d\w+)\b"
      ' Match pattern using default options.
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine(match.Value)
         If match.Groups.Count > 1 Then
            For ctr As Integer = 1 To match.Groups.Count - 1 
               Console.WriteLine("   Group {0}: {1}", ctr, match.Groups(ctr).Value)
            Next
         End If
      Next
      Console.WriteLine()

      ' Change regular expression pattern to include options.
      pattern = "\b(D\w+)(?ixn) \s (d\w+) \b"
      ' Match new pattern with options. 
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine(match.Value)
         If match.Groups.Count > 1 Then
            For ctr As Integer = 1 To match.Groups.Count - 1 
               Console.WriteLine("   Group {0}: '{1}'", ctr, match.Groups(ctr).Value)
            Next
         End If
      Next
   End Sub
End Module
' The example displays the following output:
'       Drooling dog
'          Group 1: Drooling
'          Group 2: dog
'       
'       Drooling dog
'          Group 1: 'Drooling'
'       Dreaded Deep
'          Group 1: 'Dreaded'
```

この例では、2 つの正規表現を定義しています。 最初の `\b(D\w+)\s(d\w+)\b` は、大文字の "D" と小文字の "d" で始まる 2 つの連続した単語に一致します。 2 つ目の正規表現 `\b(D\w+)(?ixn) \s (d\w+) \b` は、次の表に示すように、インライン オプションを使用して、このパターンを変更します。 結果の比較で、`(?ixn)` コンストラクトの効果を確認します。

パターン | 説明
------- | ----------- 
`\b` | ワード境界から開始します。
`(D\w+)` | 大文字 "D" の後に 1 つ以上の単語の文字が続くパターンに一致します。 これが最初のキャプチャ グループです。
`(?ixn)` | この時点から、大文字と小文字を区別しない比較を行い、明示的なキャプチャのみを行って、正規表現パターン内の空白を無視します。
`\s` | 空白文字と一致します。
`(d\w+)` | 大文字または小文字 "d" の後に 1 つ以上の単語の文字が続くパターンに一致します。 n (明示的なキャプチャ) オプションが有効になっているため、このグループはキャプチャされません。
`\b` | ワード境界に一致します。
 
## <a name="inline-comment"></a>インライン コメント

**(?#** _comment_**)** コンストラクトを使用して、正規表現にインライン コメントを含めることができます。 [Regex.ToString](xref:System.Text.RegularExpressions.Regex.Unescape(System.String)) メソッドによって返される文字列にコメントが含まれますが、正規表現エンジンは、パターン マッチングでコメントのどの部分も使用しません。 コメントは、最初の閉じかっこで終了します。

次の例では、前のセクションの例の最初の正規表現パターンを繰り返しています。 比較で大文字小文字を区別するかどうかを示す 2 つのインライン コメントを正規表現に追加しています。 正規表現パターン `\b((?# case-sensitive comparison)D\w+)\s((?#case-insensitive comparison)d\w+)\b` は、次のように定義されます。

パターン | 説明
------- | ----------- 
`\b` | ワード境界から開始します。
`(?# case-sensitive comparison)` | コメント。 これは、パターンマッチング動作に影響を与えません。
`(D\w+)` | 大文字 "D" の後に 1 つ以上の単語の文字が続くパターンに一致します。 これが最初のキャプチャ グループです。
`\s` | 空白文字と一致します。
`(?ixn)` |この時点から、大文字と小文字を区別しない比較を行い、明示的なキャプチャのみを行って、正規表現パターン内の空白を無視します。
`(?#case-insensitive comparison)` | コメント。 これは、パターンマッチング動作に影響を与えません。 
`(d\w+)` | 大文字または小文字 "d" の後に 1 つ以上の単語の文字が続くパターンに一致します。 これが 2 番目のキャプチャ グループです。
`\b` | ワード境界に一致します。
 
```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b((?# case sensitive comparison)D\w+)\s(?ixn)((?#case insensitive comparison)d\w+)\b";
      Regex rgx = new Regex(pattern);
      string input = "double dare double Double a Drooling dog The Dreaded Deep";

      Console.WriteLine("Pattern: " + pattern.ToString());
      // Match pattern using default options.
      foreach (Match match in rgx.Matches(input))
      {
         Console.WriteLine(match.Value);
         if (match.Groups.Count > 1)
         {
            for (int ctr = 1; ctr <match.Groups.Count; ctr++) 
               Console.WriteLine("   Group {0}: {1}", ctr, match.Groups[ctr].Value);
         }
      }
   }
}
// The example displays the following output:
//    Pattern: \b((?# case sensitive comparison)D\w+)\s(?ixn)((?#case insensitive comp
//    arison)d\w+)\b
//    Drooling dog
//       Group 1: Drooling
//    Dreaded Deep
//       Group 1: Dreaded
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b((?# case sensitive comparison)D\w+)\s(?ixn)((?#case insensitive comparison)d\w+)\b"
      Dim rgx As New Regex(pattern)
      Dim input As String = "double dare double Double a Drooling dog The Dreaded Deep"

      Console.WriteLine("Pattern: " + pattern.ToString())
      ' Match pattern using default options.
      For Each match As Match In rgx.Matches(input)
         Console.WriteLine(match.Value)
         If match.Groups.Count > 1 Then
            For ctr As Integer = 1 To match.Groups.Count - 1 
               Console.WriteLine("   Group {0}: {1}", ctr, match.Groups(ctr).Value)
            Next
         End If
      Next
   End Sub
End Module
' The example displays the following output:
'    Pattern: \b((?# case sensitive comparison)D\w+)\s(?ixn)((?#case insensitive comp
'    arison)d\w+)\b
'    Drooling dog
'       Group 1: Drooling
'    Dreaded Deep
'       Group 1: Dreaded
```

## <a name="endofline-comment"></a>行末のコメント

シャープ記号 (**#**) は、正規表現パターンの末尾のエスケープ解除された # 文字から始まり、行の末尾まで続く x モード コメントをマークします。 このコンストラクトを使用するには、[Regex](xref:System.Text.RegularExpressions.Regex) オブジェクトをインスタンス化したり、静的 [Regex](xref:System.Text.RegularExpressions.Regex) メソッドを呼び出したりする際に、**x** オプションを有効にする (インライン オプションによって) か、または *option* パラメーターに [RegexOptions.IgnorePatternWhitespace](xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace) 値を指定する必要があります。 

次の例は、行末のコメント コンストラクトを示しています。 これは、1 つ以上の書式指定項目を含む複合書式文字列かどうかを判断します。 次の表に、正規表現パターン内のコンストラクトを説明しています。 

`\{\d+(,-*\d+)*(\:\w{1,4}?)*\}(?x) # Looks for a composite format item`。 

パターン | 説明
------- | ----------- 
`\{` | 左中かっこと一致します。
`\d+` | 1 個以上の 10 進数と一致します。
`(,-*\d+)*` | 0 個または 1 つのコンマの後にオプションのマイナス記号が続き、その後に 1 つ以上の 10 進数が続くパターンと一致します。
`(\:\w{1,4}?)*` | 0 個または 1 つのコロンの後に 1 ～ 4 個の、ただし可能な限り少ない空白文字が続くパターンと一致します。
`(?#case insensitive comparison)` | インライン コメント。 これは、パターンマッチング動作に影響を与えません。
`\}` | 右中かっこと一致します。
`(?x)` | 行末のコメントが認識されるように、パターンの空白を無視するオプションを有効にします。
`# Looks for a composite format item.` | 行末のコメント。
 
```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\{\d+(,-*\d+)*(\:\w{1,4}?)*\}(?x) # Looks for a composite format item.";
      string input = "{0,-3:F}";
      Console.WriteLine("'{0}':", input);
      if (Regex.IsMatch(input, pattern))
         Console.WriteLine("   contains a composite format item.");
      else
         Console.WriteLine("   does not contain a composite format item.");
   }
}
// The example displays the following output:
//       '{0,-3:F}':
//          contains a composite format item.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\{\d+(,-*\d+)*(\:\w{1,4}?)*\}(?x) # Looks for a composite format item."
      Dim input As String = "{0,-3:F}"
      Console.WriteLine("'{0}':", input)
      If Regex.IsMatch(input, pattern) Then
         Console.WriteLine("   contains a composite format item.")
      Else
         Console.WriteLine("   does not contain a composite format item.")
      End If
   End Sub
End Module
' The example displays the following output:
'       '{0,-3:F}':
'          contains a composite format item.
```

正規表現で `(?x)` コンストラクトを指定する代わりに、[Regex.IsMatch(String, String, RegexOptions)](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) メソッドを呼び出し、それに [RegexOptions.IgnorePatternWhitespace](xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace) 列挙値を渡して、コメントを認識させることもできることに注意してください。

## <a name="see-also"></a>関連項目

[正規表現言語 - クイック リファレンス](quick-ref.md)




<!--HONumber=Nov16_HO3-->


