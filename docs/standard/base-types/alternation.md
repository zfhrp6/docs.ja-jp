---
title: "正規表現での代替構成体"
description: "正規表現での代替構成体"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 59ffac4d-fc6e-461f-8783-d9f8dc88ce2c
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: fa2a880e5bcc36354bd59d3dc032180c89984f1d
ms.lasthandoff: 03/02/2017

---

# <a name="alternation-constructs-in-regular-expressions"></a>正規表現での代替構成体

代替構成体は、択一条件または条件一致を有効にするように正規表現を変更します。 .NET では、次の&3; つの代替構成体がサポートされています。

* **|** を使用したパターン マッチ

* **(?(**_expression_**)**_yes_**|**_no_**)** を使用した条件一致

* 有効なキャプチャ グループに基づく条件一致

## <a name="pattern-matching-with-"></a>| を使用したパターン マッチ

縦棒 (|) 文字を使って、| 文字で各パターンを区切った一連のパターンのいずれかと照合できます。 

肯定的文字クラスと同じように、| 文字を使うと、複数の文字のいずれか&1; 文字と照合できます。 次の例は、肯定的文字クラスと | 文字との択一パターン マッチを使って、文字列から単語 "gray"や "grey" を検索します。 この場合、| 文字を使うと、より詳細な正規表現が生成されます。 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      // Regular expression using character class.
      string pattern1 = @"\bgr[ae]y\b";
      // Regular expression using either/or.
      string pattern2 = @"\bgr(a|e)y\b";

      string input = "The gray wolf blended in among the grey rocks.";
      foreach (Match match in Regex.Matches(input, pattern1))
         Console.WriteLine("'{0}' found at position {1}", 
                           match.Value, match.Index);
      Console.WriteLine();
      foreach (Match match in Regex.Matches(input, pattern2))
         Console.WriteLine("'{0}' found at position {1}", 
                           match.Value, match.Index);
   }
}
// The example displays the following output:
//       'gray' found at position 4
//       'grey' found at position 35
//       
//       'gray' found at position 4
//       'grey' found at position 35           
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      ' Regular expression using character class.
      Dim pattern1 As String = "\bgr[ae]y\b"
      ' Regular expression using either/or.
      Dim pattern2 As String = "\bgr(a|e)y\b"

      Dim input As String = "The gray wolf blended in among the grey rocks."
      For Each match As Match In Regex.Matches(input, pattern1)
         Console.WriteLine("'{0}' found at position {1}", _
                           match.Value, match.Index)
      Next      
      Console.WriteLine()
      For Each match As Match In Regex.Matches(input, pattern2)
         Console.WriteLine("'{0}' found at position {1}", _
                           match.Value, match.Index)
      Next      
   End Sub
End Module
' The example displays the following output:
'       'gray' found at position 4
'       'grey' found at position 35
'       
'       'gray' found at position 4
'       'grey' found at position 35 
```

| 文字を使う正規表現 `\bgr(a|e)y\b,` の解釈を次の表に示します。

パターン | 説明
------- | -----------
`\b` | ワード境界から開始します。
`gr` | 文字 "gr" と一致します。
`(a|e)` | "a" または "e" と一致します。
`y\b` |    ワード境界にある "y" と一致します。


また、| 文字を使って、複数の文字や部分式との択一照合を実行できます。これは、文字リテラルと正規表現言語要素を自由に組み合わせて使うことができます。 (文字クラスにこの機能はありません)。次の例では、| 文字を使って、米国の社会保障番号 (SSN) (*ddd-dd-dddd* という形式の 9 桁の数字)、または米国の雇用者番号 (EIN) (*dd-ddddddd* という形式の 9 桁の数字) のいずれかを抽出します。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b";
      string input = "01-9999999 020-333333 777-88-9999";
      Console.WriteLine("Matches for {0}:", pattern);
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index);
   }
}
// The example displays the following output:
//       Matches for \b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b:
//          01-9999999 at position 0
//          777-88-9999 at position 22
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b"
      Dim input As String = "01-9999999 020-333333 777-88-9999"
      Console.WriteLine("Matches for {0}:", pattern)
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index)
      Next   
   End Sub
End Module
' The example displays the following output:
'       Matches for \b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b:
'          01-9999999 at position 0
'          777-88-9999 at position 22
```

この正規表現 `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` の解釈を次の表に示します。

パターン | 説明
------- | -----------
`\b` | ワード境界から開始します。
`(\d{2}-\d{7}|;\d{3}-\d{2}-\d{4})` | 「2 桁と&7; 桁の&10; 進数がハイフンでつながれた文字列」または「3 桁、2 桁、4 桁の&10; 進数がそれぞれハイフンでつながれた文字列」のいずれかと一致します。 
`\d` | ワード境界で照合を終了します。
                                         
## <a name="conditional-matching-with-an-expression"></a>式を使用した条件一致

この言語要素では、最初のパターンに一致するかどうかに応じて、2 つのパターンのいずれかの照合を実行します。 構文は次のとおりです。

**(?(**_expression_**)**_yes_**|**_no_**)**

ここで、*expression* は照合する最初のパターン、*yes* は expression が一致した場合に照合するパターン、*no* は *expression* が一致しなかった場合に照合するパターン (省略可能) です。 *expression* は正規表現エンジンによってゼロ幅アサーションとして処理されるので、*expression* が評価された後、正規表現エンジンによる入力ストリーム内の評価位置は前に進みません。 そのため、この構成体は次の構成体と同じです。

**(?(?**=_expression_**)**_yes_**|**_no_**)**

ここで、**(?**=_expression_**)** はゼロ幅アサーションの構成体として解釈されます (詳細については、「[正規表現でのグループ化構成体](grouping.md)」をご覧ください)。正規表現エンジンによって *expression* はアンカー (ゼロ幅アサーション) として解釈されるので、*expression* は、ゼロ幅アサーション (詳細については、「[正規表現のアンカー](anchors.md)」を参照) または *yes* にも含まれている部分式のどちらかである必要があります。 それ以外の場合、*yes* パターンには一致しません。 

> [!NOTE]
> *expression* が名前付きキャプチャ グループや番号付きキャプチャ グループである場合、代替構成体はキャプチャ テストとして解釈されます。詳しくは、次のセクション「[有効なキャプチャ グループに基づく条件一致](#conditional-matching-based-on-a-valid-captured-group)」をご覧ください。 つまり、正規表現エンジンは、キャプチャした部分文字列を照合しようとはせず、代わりにグループが存在するかどうかをテストします。
 

次の例は、前のセクションで説明した例を少し変更したものです。 条件一致を使用して、ワード境界の後の最初の&3; 文字が「2 桁の数字の後にハイフン」であるかどうかを判定します。 一致した場合は、米国の雇用者番号 (EIN) との照合を試みます。 一致しない場合は、米国の社会保険番号 (SSN) との照合を試みます。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b";
      string input = "01-9999999 020-333333 777-88-9999";
      Console.WriteLine("Matches for {0}:", pattern);
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index);
   }
}
// The example displays the following output:
//       Matches for \b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b:
//          01-9999999 at position 0
//          777-88-9999 at position 22
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b"
      Dim input As String = "01-9999999 020-333333 777-88-9999"
      Console.WriteLine("Matches for {0}:", pattern)
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index)
      Next   
   End Sub
End Module
' The example displays the following output:
'       Matches for \b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b:
'          01-9999999 at position 0
'          777-88-9999 at position 22
```

この正規表現パターン `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` の解釈を次の表に示します。

パターン | 説明
------- | -----------
`\b` | ワード境界から開始します。
`(?(\d{2}-)` | 次の&3; 文字が「2 桁の数字の後にハイフン」で構成されているかどうかを判定します。
`\d{2}-\d{7}` | 前のパターンに一致する場合は、「2 桁の数字の後にハイフン、その後に&7; 桁の数字」を照合します。
`\d{3}-\d{2}-\d{4}` | 前のパターンに一致しない場合は、「3 桁の&10; 進数、ハイフン、2 桁の&10; 進数、もう&1; つのハイフン、および&4; 桁の&10; 進数」を照合します。 
`\b` | ワード境界に一致します。
 
## <a name="conditional-matching-based-on-a-valid-captured-group"></a>有効なキャプチャ グループに基づく条件一致

この言語要素では、指定されたキャプチャ グループに一致するかどうかに応じて、2 つのパターンのいずれかを照合します。 構文は次のとおりです。

**(?(**_name_**)**_yes_**|**_no_**)**

または

**(?(**_number_**)**_yes_**|**_no_**)**

ここで、*name* はキャプチャ グループの名前、*number* はキャプチャ グループの番号です。*yes* は、name または number が一致する場合に照合する式です。*no* は、一致しない場合に照合する式 (省略可能) です。

*name* が正規表現パターンで使用されているキャプチャ グループの名前に一致しない場合、その代替構成体は式のテスト (前のセクションで説明したもの) として解釈されます。 通常、これは expression が `false` に評価されることを意味します。 `number` が正規表現パターンで使用されている番号付きキャプチャ グループに対応しない場合は、正規表現エンジンが [ArgumentException](xref:System.ArgumentException) をスローします。

次の例は、前のセクションで説明した例を少し変更したものです。 「2 桁の数字の後にハイフン」で構成される `n2` という名前付きキャプチャ グループを使用しています。 代替構成体により、このキャプチャ グループが入力文字列に一致したかどうかテストされます。 一致した場合は、場合に、米国の&9; 桁の雇用者番号 (EIN) との照合を試みます。 一致しなかった場合は、米国の&9; 桁の社会保険番号 (SSN) との照合を試みます。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(?<n2>\d{2}-)*(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b";
      string input = "01-9999999 020-333333 777-88-9999";
      Console.WriteLine("Matches for {0}:", pattern);
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index);
   }
}
// The example displays the following output:
//       Matches for \b(?<n2>\d{2}-)*(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b:
//          01-9999999 at position 0
//          777-88-9999 at position 22
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(?<n2>\d{2}-)*(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b"
      Dim input As String = "01-9999999 020-333333 777-88-9999"
      Console.WriteLine("Matches for {0}:", pattern)
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index)
      Next   
   End Sub
End Module
```

この正規表現パターン `\b(?<n2>\d{2}-)*(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` の解釈を次の表に示します。

パターン | 説明
------- | -----------
`\b` | ワード境界から開始します。
`(?<n2>\d{2}-)*` | 「2 桁の数字の後にハイフン」の&0; 個または&1; 個の出現と照合します。 このキャプチャ グループに `n2` という名前を付けます。
`(?(n2)` | `n2` への一致が入力文字列内に見つかるかどうかテストします。 
`)\d{7}` | `n2` が一致した場合は、7 桁の&10; 進数を照合します。
`|;\d{3}-\d{2}-\d{4}` | `n2` が一致しなかった場合は、「3 桁の&10; 進数、ハイフン、2 桁の&10; 進数、もう&1; つのハイフン、および&4; 桁の&10; 進数」を照合します。 
`\b` | ワード境界に一致します。
 
この例を少し変更して、名前付きグループではなく番号付きグループを使用する例を次に示します。 正規表現パターンは `\b(\d{2}-)*(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b` です。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(\d{2}-)*(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b";
      string input = "01-9999999 020-333333 777-88-9999";
      Console.WriteLine("Matches for {0}:", pattern);
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index);
   }
}
// The example display the following output:
//       Matches for \b(\d{2}-)*(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b:
//          01-9999999 at position 0
//          777-88-9999 at position 22
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(\d{2}-)*(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b"
      Dim input As String = "01-9999999 020-333333 777-88-9999"
      Console.WriteLine("Matches for {0}:", pattern)
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index)
      Next   
   End Sub
End Module
' The example displays the following output:
'       Matches for \b(\d{2}-)*(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b:
'          01-9999999 at position 0
'          777-88-9999 at position 22
```

関連項目

[正規表現言語 - クイック リファレンス](quick-ref.md)


