---
title: "正規表現での前方参照構成体"
description: "正規表現での前方参照構成体"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: c453ed78-650f-4c3c-9ab4-9d89d250bf88
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 757c8c4e71bbafb12c8add925723daf1a24e06d1

---

# <a name="backreference-constructs-in-regular-expressions"></a>正規表現での前方参照構成体

前方参照は、文字列内の繰り返しの文字または部分文字列を識別するために便利な方法を提供します。 たとえば、入力文字列に複数回出現する任意の部分文字列が含まれている場合は、キャプチャ グループを使用して最初の一致を検出し、前方参照を使用して部分文字列の後続の出現箇所を見つけます。 

> [!NOTE]
> 別の構文を使用して、置換文字列内の名前付きおよび番号付きのキャプチャ グループを参照します。 詳細については、「[正規表現での置換](substitutions.md)」を参照してください。
 
.NET では、番号付きおよび名前付きのキャプチャ グループを参照する個別の言語要素が定義されています。 キャプチャ グループの詳細については、「[正規表現でのグループ化構成体](grouping.md)」を参照してください。

## <a name="numbered-backreferences"></a>番号付き前方参照

番号付き前方参照は、次の構文を使用します。

**\**_number_

ここで、*number* は、正規表現でのキャプチャ グループの位置を表す序数です。 たとえば、`\4` は 4 番目のキャプチャ グループの内容と一致します。 *number* が正規表現パターンで定義されていない場合は、解析エラーが発生し、正規表現エンジンが [ArgumentException](xref:System.ArgumentException) をスローします。 たとえば、正規表現 `\b(\w+)\s\1` は有効です (`(\w+)` が式の中の最初で唯一のキャプチャ グループであるため)。 これに対して、`\b(\w+)\s\2` は無効であり、引数の例外がスローされます (`\2` という番号のキャプチャ グループは存在しないため)。

同じ表記法を使用した、8 進数のエスケープ コード (`\16` など) と **\**_number_ 前方参照との間には、あいまいさがあることに注意してください。 このあいまいさは、次のように解決されます。

* `\1` から `\9` までの式は、8 進数コードとしてではなく、常に前方参照として解釈されます。

* 複数桁の式の最初の桁が 8 または 9 (`\80`や `\91`) の場合、式はリテラルとして解釈されます。

* `\10` 以降の式は、その番号に対応する前方参照がある場合、前方参照として解釈されます。それ以外の場合は、8 進数のコードとして解釈されます。

* 正規表現に未定義のグループ番号への前方参照が含まれる場合、解析エラーが発生し、正規表現エンジンが [ArgumentException](xref:System.ArgumentException) をスローします。

あいまいさが問題になる場合は、**\k<**_name_**>** という表記を使用できます。この表記はあいまいではなく、8 進数の文字コードと混同することはありません。 同様に、`\xdd` などの 16 進数コードはあいまいではなく、前方参照と混同することはありません。

次の例では、文字列内の単語に使用される重複した文字を検索します。 例で定義している正規表現 `(\w)\1,` は、次の要素で構成されています。

要素 | 説明
------- | -----------
`(\w)` | 単語文字を検出し、最初のキャプチャ グループに割り当てます。
`\1` | 最初のキャプチャ グループの値と同じ次の文字を検出します。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"(\w)\1";
      string input = "trellis llama webbing dresser swagger";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("Found '{0}' at position {1}.", 
                           match.Value, match.Index);
   }
}
// The example displays the following output:
//       Found 'll' at position 3.
//       Found 'll' at position 8.
//       Found 'bb' at position 16.
//       Found 'ss' at position 25.
//       Found 'gg' at position 33.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "(\w)\1"
      Dim input As String = "trellis llama webbing dresser swagger"
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("Found '{0}' at position {1}.", _
                           match.Value, match.Index)
      Next   
   End Sub
End Module
' The example displays the following output:
'       Found 'll' at position 3.
'       Found 'll' at position 8.
'       Found 'bb' at position 16.
'       Found 'ss' at position 25.
'       Found 'gg' at position 33.
```

## <a name="named-backreferences"></a>名前付き前方参照

名前付き前方参照は、次の構文を使用して定義します。

**\k<**_name_**>**

または

**\k'**_name_**'**

ここで、*name* は正規表現パターンで定義されたキャプチャ グループの名前です。 *name* が正規表現パターンで定義されていない場合は、解析エラーが発生し、正規表現エンジンが [ArgumentException](xref:System.ArgumentException) をスローします。

次の例では、文字列内の単語に使用される重複した文字を検索します。 例で定義している正規表現 `(?<char>\w)\k<char>` は、次の要素で構成されています。

要素 | 説明
------- | -----------
`(?<char>\w)` | 単語文字を検出し、char という名前のキャプチャ グループに割り当てます。
`\k<char>` | char キャプチャ グループの値と同じ次の文字を検出します。
 
```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"(?<char>\w)\k<char>";
      string input = "trellis llama webbing dresser swagger";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("Found '{0}' at position {1}.", 
                           match.Value, match.Index);
   }
}
// The example displays the following output:
//       Found 'll' at position 3.
//       Found 'll' at position 8.
//       Found 'bb' at position 16.
//       Found 'ss' at position 25.
//       Found 'gg' at position 33.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "(?<char>\w)\k<char>"
      Dim input As String = "trellis llama webbing dresser swagger"
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("Found '{0}' at position {1}.", _
                           match.Value, match.Index)
      Next   
   End Sub
End Module
' The example displays the following output:
'       Found 'll' at position 3.
'       Found 'll' at position 8.
'       Found 'bb' at position 16.
'       Found 'ss' at position 25.
'       Found 'gg' at position 33.
```

*name* は数字の文字列表現とすることもできます。 たとえば、次の例では正規表現 `(?<2>\w)\k<2>` を使用して、文字列内の単語の重複した文字を検索します。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"(?<2>\w)\k<2>";
      string input = "trellis llama webbing dresser swagger";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("Found '{0}' at position {1}.", 
                           match.Value, match.Index);
   }
}
// The example displays the following output:
//       Found 'll' at position 3.
//       Found 'll' at position 8.
//       Found 'bb' at position 16.
//       Found 'ss' at position 25.
//       Found 'gg' at position 33.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "(?<2>\w)\k<2>"
      Dim input As String = "trellis llama webbing dresser swagger"
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("Found '{0}' at position {1}.", _
                           match.Value, match.Index)
      Next   
   End Sub
End Module
' The example displays the following output:
'       Found 'll' at position 3.
'       Found 'll' at position 8.
'       Found 'bb' at position 16.
'       Found 'ss' at position 25.
'       Found 'gg' at position 33.
```

## <a name="what-backreferences-match"></a>前方参照と一致する内容

前方参照は、グループの最新の定義 (左から右に検出する場合は、すぐ左にある定義) を参照します。 1 つのグループで複数のキャプチャが発生した場合、前方参照は最新のキャプチャを参照します。 

次の例には、正規表現パターン `(?<1>a)(?<1>\1b)*` が含まれています。このパターンは \1 の名前付きグループを再定義します。 正規表現の各パターンは、次の表に示すように定義されています。 

パターン | 説明
------- | -----------
`(?<1>a)` | 文字 "a" を検出し、結果を 1 という名前のキャプチャ グループに割り当てます。
`(?<1>\1b)*` |1 という名前のグループの 0 個または 1 個の出現箇所を "b" と共に検出し、結果を 1 という名前のキャプチャ グループに割り当てます。 
 
```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"(?<1>a)(?<1>\1b)*";
      string input = "aababb";
      foreach (Match match in Regex.Matches(input, pattern))
      {
         Console.WriteLine("Match: " + match.Value);
         foreach (Group group in match.Groups)
            Console.WriteLine("   Group: " + group.Value);
      }
   }
}
// The example displays the following output:
//          Group: aababb
//          Group: abb
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "(?<1>a)(?<1>\1b)*"
      Dim input As String = "aababb"
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("Match: " + match.Value)
         For Each group As Group In match.Groups
            Console.WriteLIne("   Group: " + group.Value)
         Next
      Next
   End Sub
End Module
' The example display the following output:
'          Group: aababb
'          Group: abb
```

正規表現を入力文字列 ("aababb") と比較する際、正規表現エンジンは次の操作を実行します。

1. 文字列の先頭から開始し、式 `(?<1>a)` で "a" を検出します。 グループ 1 の値が "a" になります。

2. 次の文字に進み、式 `\1b` で文字列 "ab" を検出します。 次に、その結果 "ab" を `\1` に割り当てます。

3. これにより 4 番目の文字に進みます。 式 `(?<1>\1b)` を 0 回以上照合し、式 `\1b` で文字列 "abb" を検出します。 その結果 "abb" を `\1` に割り当てます。

この例では、\* はループ量指定子であり、正規表現エンジンが定義したパターンを照合できなくなるまで、繰り返し評価されます。 ループ量指定子によってグループの定義はクリアされません。

グループで部分文字列がキャプチャされなかった場合、そのグループへの前方参照は未定義になり、一致することはありません。 次のように定義されている正規表現パターン `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b,` を例として示します。

パターン | 説明
------- | -----------
`\b` | ワード境界から照合を開始します。
`(\p{Lu}{2})` | 2 つの大文字と一致します。 これが最初のキャプチャ グループです。
`(\d{2})?` | 2 桁の 10 進数の 0 回または 1 回の出現と一致します。 これが 2 番目のキャプチャ グループです。
`(\p{Lu}{2})` | 2 つの大文字と一致します。 これが 3 番目のキャプチャ グループです。
`\b` | ワード境界で照合を終了します。

2 番目のキャプチャ グループによって定義されている 2 桁の 10 進数が存在しない場合でも、入力文字列はこの正規表現を照合できます。 次の例では、一致が見つかった場合でも、成功した 2 つのキャプチャ グループの間に空のキャプチャ グループが検出されます。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b";
      string[] inputs = { "AA22ZZ", "AABB" };
      foreach (string input in inputs)
      {
         Match match = Regex.Match(input, pattern);
         if (match.Success)
         {
            Console.WriteLine("Match in {0}: {1}", input, match.Value);
            if (match.Groups.Count > 1)
            {
               for (int ctr = 1; ctr <= match.Groups.Count - 1; ctr++)
               {
                  if (match.Groups[ctr].Success)
                     Console.WriteLine("Group {0}: {1}", 
                                       ctr, match.Groups[ctr].Value);
                  else
                     Console.WriteLine("Group {0}: <no match>", ctr);
               }
            }
         }
         Console.WriteLine();
      }      
   }
}
// The example displays the following output:
//       Match in AA22ZZ: AA22ZZ
//       Group 1: AA
//       Group 2: 22
//       Group 3: ZZ
//       
//       Match in AABB: AABB
//       Group 1: AA
//       Group 2: <no match>
//       Group 3: BB
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b"
      Dim inputs() As String = { "AA22ZZ", "AABB" }
      For Each input As String In inputs
         Dim match As Match = Regex.Match(input, pattern)
         If match.Success Then
            Console.WriteLine("Match in {0}: {1}", input, match.Value)
            If match.Groups.Count > 1 Then
               For ctr As Integer = 1 To match.Groups.Count - 1
                  If match.Groups(ctr).Success Then
                     Console.WriteLine("Group {0}: {1}", _
                                       ctr, match.Groups(ctr).Value)
                  Else
                     Console.WriteLine("Group {0}: <no match>", ctr)
                  End If      
               Next
            End If
         End If
         Console.WriteLine()
      Next      
   End Sub
End Module
' The example displays the following output:
'       Match in AA22ZZ: AA22ZZ
'       Group 1: AA
'       Group 2: 22
'       Group 3: ZZ
'       
'       Match in AABB: AABB
'       Group 1: AA
'       Group 2: <no match>
'       Group 3: BB
```

## <a name="see-also"></a>関連項目

[正規表現言語 - クイック リファレンス](quick-ref.md)




<!--HONumber=Nov16_HO3-->


