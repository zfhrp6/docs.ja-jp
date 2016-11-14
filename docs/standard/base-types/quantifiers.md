---
title: "正規表現での量指定子"
description: "正規表現での量指定子"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/29/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 8e5124c4-20b5-4c57-ab68-301d1d7311c4
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 016ee9a4f05fdf36982c5b369780526296b53a7d

---

# <a name="quantifiers-in-regular-expressions"></a>正規表現での量指定子

量指定子は、一致と見なされるために入力中に存在する必要がある文字、グループ、または文字クラスの出現数を指定します。 次の表に、.NET でサポートされている量指定子の一覧を示します。

最長一致の量指定子 | 最短一致の量指定子 | 説明
----------------- | --------------- | ----------- 
**\*** | **\*?** | 0 回以上の繰り返しに一致します。
**+** | **+?** | 1 回以上の繰り返しに一致します。
**?** | **??** | 0 回または 1 回の繰り返しに一致します。
**{**_n_**}** | **{**_n_**}?** | n 回の繰り返しに一致します。
**{**_n_**,}** | **{**_n_**,}?** | n 回以上の繰り返しに一致します。
**{**_n_**,**_m_**}** | **{**_n_**,**_m_**}?** | n 回から m 回の繰り返しに一致します。
 
量 *n* および *m* は整数の定数です。 通常、量指定子は最長一致です。最長一致の場合、正規表現エンジンでは、特定のパターンの繰り返しができるだけ多くなるように照合が行われます。 量指定子に `?` 文字を付けると最短一致になります。最短一致の場合、正規表現エンジンでは、特定のパターンの繰り返しができるだけ少なくなるように照合が行われます。 最長一致と最短一致の量指定子の違いの詳細については、このトピックの「[最長一致と最短一致の量指定子](#greedy-and-lazy-quantifiers)」のセクションをご覧ください。

> [!IMPORTANT]
> 量指定子を入れ子にすると (たとえば、正規表現パターン `(a*)*` など)、入力文字列の文字数に応じて指数関数的に、正規表現エンジンで実行する必要がある比較の回数が増加する可能性があります。 この動作と回避方法の詳細については、「[正規表現におけるバックトラッキング](backtracking.md)」を参照してください。

## <a name="regular-expression-quantifiers"></a>正規表現の量指定子

以降のセクションでは、.NET の正規表現でサポートされている量指定子について説明します。 

> [!NOTE]
> 正規表現エンジンでは、正規表現パターンで \*, +, ?, {, および } の各文字を検出すると、[文字クラス](classes.md)に含まれているもの以外は量指定子または量指定子コンストラクトの一部として解釈します。 文字クラスの外側でこれらをリテラル文字として解釈するには、文字の前に円記号を付けてエスケープする必要があります。 たとえば、正規表現パターン内の `\*` という文字列は、リテラルのアスタリスク ("*") 文字と解釈されます。

### <a name="match-zero-or-more-times-"></a>0 回以上の繰り返しに一致: \*

\* 量指定子は、直前の要素の 0 回以上の繰り返しに一致します。 これは **{0,}** 量指定子と同じです。 **\*** は最長一致の量指定子であり、最短一致でこれに対応するのは **\*?** です。

次の例は、この正規表現を示しています。 入力文字列の 9 個の数字のうち、5 個がパターンに一致し、4 個 (`95`、`929`、`9129`、および `9919`) が一致しません。

```csharp
string pattern = @"\b91*9*\b";   
string input = "99 95 919 929 9119 9219 999 9919 91119";
foreach (Match match in Regex.Matches(input, pattern))
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);

// The example displays the following output:   
//       '99' found at position 0.
//       '919' found at position 6.
//       '9119' found at position 14.
//       '999' found at position 24.
//       '91119' found at position 33.
```

```vb
Dim pattern As String = "\b91*9*\b"   
Dim input As String = "99 95 919 929 9119 9219 999 9919 91119"
For Each match As Match In Regex.Matches(input, pattern)
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)
Next     
' The example displays the following output:   
'       '99' found at position 0.
'       '919' found at position 6.
'       '9119' found at position 14.
'       '999' found at position 24.
'       '91119' found at position 33.
```

正規表現パターンは、次の表に示すように定義されています。

パターン | 説明
------- | ----------- 
`\b` | ワード境界から開始します。
`91*` | "9" の後に文字 "1" が 0 個以上続くパターンに一致します。
`9*` | 0 個以上の文字 "9" に一致します。
`\b` | ワード境界で終了します。
 
### <a name="match-one-or-more-times-"></a>1 回以上の繰り返しに一致: +

**+** 量指定子は、直前の要素の 1 回以上の繰り返しに一致します。 これは **{1,}** と同じです。 **+** は最長一致の量指定子であり、最短一致でこれに対応するのは **+?** です。

たとえば、正規表現 `\ban+\w*?\b` は、文字 `a` で始まり、文字 `n` が 1 回以上繰り返されるすべての単語に一致を試みます。 次の例は、この正規表現を示しています。 この正規表現は、単語 `an`、`annual`、`announcement`、および `antique` に一致し、`autumn` と `all` では不一致となります。

```csharp
string pattern = @"\ban+\w*?\b";

string input = "Autumn is a great time for an annual announcement to all antique collectors.";
foreach (Match match in Regex.Matches(input, pattern, RegexOptions.IgnoreCase))
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);

// The example displays the following output:   
//       'an' found at position 27.
//       'annual' found at position 30.
//       'announcement' found at position 37.
//       'antique' found at position 57.      
```

```vb
Dim pattern As String = "\ban+\w*?\b"

Dim input As String = "Autumn is a great time for an annual announcement to all antique collectors."
For Each match As Match In Regex.Matches(input, pattern, RegexOptions.IgnoreCase)
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)
Next   
' The example displays the following output:   
'       'an' found at position 27.
'       'annual' found at position 30.
'       'announcement' found at position 37.
'       'antique' found at position 57. 
```

正規表現パターンは、次の表に示すように定義されています。

パターン | 説明
------- | ----------- 
`\b` | ワード境界から開始します。
`an+` | "a" の後に文字 "n" が 1 個以上続くパターンに一致します。 
`\w*?` | 単語に含まれる文字の 0 回以上の繰り返しのうち、最も少ない繰り返しに一致します。
`\b` | ワード境界で終了します。
 
### <a name="match-zero-or-one-time-"></a>0 回または 1 回の繰り返しに一致: ?

**?** 量指定子は、直前の要素の 0 回または 1 回の繰り返しに一致します。 これは **{0,1}** と同じです。 **?** は最長一致の量指定子であり、最短一致でこれに対応するのは **??** です。

たとえば、正規表現 `\ban?\b` は、文字 `a` で始まり、文字 `n` が 0 回または 1 回繰り返されるすべての単語に一致を試みます。 つまり、単語 `a` と `an` に一致を試みます。 次の例は、この正規表現を示しています。

```csharp
string pattern = @"\ban?\b";
string input = "An amiable animal with a large snount and an animated nose.";
foreach (Match match in Regex.Matches(input, pattern, RegexOptions.IgnoreCase))
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);

// The example displays the following output:   
//        'An' found at position 0.
//        'a' found at position 23.
//        'an' found at position 42.
```

```vb
Dim pattern As String = "\ban?\b"
Dim input As String = "An amiable animal with a large snount and an animated nose."
For Each match As Match In Regex.Matches(input, pattern, RegexOptions.IgnoreCase)
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)
Next  
' The example displays the following output:   
'       'An' found at position 0.
'       'a' found at position 23.
'       'an' found at position 42.
```

正規表現パターンは、次の表に示すように定義されています。

パターン | 説明
------- | ----------- 
`\b` | ワード境界から開始します。
`an?` | "a" の後に文字 "n" が 0 個または 1 個続くパターンに一致します。 
`\b` | ワード境界で終了します。
 
### <a name="match-exactly-n-times-n"></a>n 回の繰り返しに一致: {n}

**{**_n_**}** 量指定子は、直前の要素の *n* 回の繰り返しに一致します。ここで、*n* は任意の整数です。 **{**_n_**}** は最長一致の量指定子であり、最短一致でこれに対応するのは **{**_n_**}?** です。

たとえば、正規表現 `\b\d+\,\d{3}\b` は、ワード境界、1 個以上の 10 進数、3 個の 10 進数、ワード境界の順に続く文字に一致を試みます。 次の例は、この正規表現を示しています。 

```csharp
string pattern = @"\b\d+\,\d{3}\b";
string input = "Sales totaled 103,524 million in January, " + 
                      "106,971 million in February, but only " + 
                      "943 million in March.";
foreach (Match match in Regex.Matches(input, pattern))
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);

//  The example displays the following output:   
//        '103,524' found at position 14.
//        '106,971' found at position 45.
```

```vb
Dim pattern As String = "\b\d+\,\d{3}\b"
Dim input As String = "Sales totaled 103,524 million in January, " + _
                      "106,971 million in February, but only " + _
                      "943 million in March."
For Each match As Match In Regex.Matches(input, pattern)
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)
Next     
' The example displays the following output:   
'       '103,524' found at position 14.
'       '106,971' found at position 45.
```

正規表現パターンは、次の表に示すように定義されています。

パターン | 説明
------- | ----------- 
`\b` | ワード境界から開始します。
`\d+` | 1 個以上の 10 進数と一致します。 
`\,` | コンマ文字と一致します。
`\d{3}` | 3 個の 10 進数と一致します。
`\b` | ワード境界で終了します。
 
### <a name="match-at-least-n-times-n"></a>n 回以上の繰り返しに一致: {n,}

**{**_n_**,}** 量指定子は、直前の要素の *n* 回以上の繰り返しに一致します。ここで、*n* は任意の整数です。 **{**_n_**,}** は最長一致の量指定子であり、最短一致でこれに対応するのは **{**_n_**}?** です。

たとえば、正規表現 `\b\d{2,}\b\D+` は、ワード境界、2 個以上の 10 進数、ワード境界、数字以外の文字の順に続く文字に一致を試みます。 次の例は、この正規表現を示しています。 この正規表現は "7 days" という語句には一致しません。これは、10 進数が 1 個しか含まれていないためです。しかし、"10 weeks and 300 years" という語句には正常に一致します。

```csharp
string pattern = @"\b\d{2,}\b\D+";   
string input = "7 days, 10 weeks, 300 years";
foreach (Match match in Regex.Matches(input, pattern))
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);

//  The example displays the following output:
//        '10 weeks, ' found at position 8.
// 
``` 

```vb
Dim pattern As String = "\b\d{2,}\b\D+"  
 Dim input As String = "7 days, 10 weeks, 300 years"
For Each match As Match In Regex.Matches(input, pattern)
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)
Next 
' The example displays the following output:
'       '10 weeks, ' found at position 8.
'       '300 years' found at position 18.
      '300 years' found at position 18.
```

正規表現パターンは、次の表に示すように定義されています。

パターン | 説明
------- | ----------- 
`\b` | ワード境界から開始します。
`\d{2,}` | 2 個以上の 10 進数と一致します。 
`\b` | ワード境界に一致します。
`\D+` | 1 個以上の 10 進数以外の数字と一致します。
 
### <a name="match-between-n-and-m-times-nm"></a>n 回から m 回までの繰り返しに一致: {n,m}

**{**_n_**,**_m_**}** 量指定子は、直前の要素の *n* 回以上、*m* 回以下の繰り返しに一致します。ここで、*n* と *m* は整数です。 **{**_n_**,**_m_**}** は最長一致の量指定子であり、最短一致でこれに対応するのは **{**_n_**,**_m_**}?** です。

次の例では、正規表現 `(00\s){2,4}` は、2 個の 0 と 1 個のスペースが、2 回以上 4 回以下だけ現れる文字列に一致を試みます。 入力文字列の最後の部分には、このパターンが最大の 4 回ではなく 5 回含まれていることに注意してください。 この部分文字列の最初の部分 (スペースと 5 つ目の 0 のペアまで) だけが正規表現パターンに一致します。

```csharp
string pattern = @"(00\s){2,4}";
string input = "0x00 FF 00 00 18 17 FF 00 00 00 21 00 00 00 00 00";
foreach (Match match in Regex.Matches(input, pattern))
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);

//  The example displays the following output:
//        '00 00 ' found at position 8.
//        '00 00 00 ' found at position 23.
//        '00 00 00 00 ' found at position 35.
```

```vb
Dim pattern As String = "(00\s){2,4}"
Dim input As String = "0x00 FF 00 00 18 17 FF 00 00 00 21 00 00 00 00 00"
For Each match As Match In Regex.Matches(input, pattern)
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)
Next 
' The example displays the following output:
'       '00 00 ' found at position 8.
'       '00 00 00 ' found at position 23.
'       '00 00 00 00 ' found at position 35.
```

### <a name="match-zero-or-more-times-lazy-match-"></a>0 回以上の繰り返しに一致 (最短一致): \*?

**\*?** 量指定子は、直前の要素の 0 回以上の繰り返しのうち、最も少ない繰り返しに一致します。 これは、最長一致の量指定子 **\*** に対応する、最短一致の量指定子です。

次の例では、正規表現 `\b\w*?oo\w*?\b` は、文字列 `oo` を含むすべての単語に一致します。 

```csharp
 string pattern = @"\b\w*?oo\w*?\b";
 string input = "woof root root rob oof woo woe";
 foreach (Match match in Regex.Matches(input, pattern, RegexOptions.IgnoreCase))
    Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);

 //  The example displays the following output:
//        'woof' found at position 0.
//        'root' found at position 5.
//        'root' found at position 10.
//        'oof' found at position 19.
//        'woo' found at position 23.
```

```vb
Dim pattern As String = "\b\w*?oo\w*?\b"
 Dim input As String = "woof root root rob oof woo woe"
 For Each match As Match In Regex.Matches(input, pattern, RegexOptions.IgnoreCase)
    Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)
 Next 
 ' The example displays the following output:
'       'woof' found at position 0.
'       'root' found at position 5.
'       'root' found at position 10.
'       'oof' found at position 19.
'       'woo' found at position 23.
```

正規表現パターンは、次の表に示すように定義されています。

パターン | 説明
------- | ----------- 
`\b` | ワード境界から開始します。
`\w*?` | 単語に含まれる 0 個以上の文字のうち、最も少ない文字に一致します。 
`oo` | 文字列 "oo" と一致します。
`\w*?` | 単語に含まれる 0 個以上の文字のうち、最も少ない文字に一致します。
`\b` | ワード境界で終了します。
 
### <a name="match-one-or-more-times-lazy-match-"></a>1 回以上の繰り返しに一致 (最短一致): +?

**+?** 量指定子は、直前の要素の 1 回以上の繰り返しのうち、最も少ない繰り返しに一致します。 これは、最長一致の量指定子 **+** に対応する、最短一致の量指定子です。

たとえば、正規表現 `\b\w+?\b` は、ワード境界で区切られた 1 つ以上の文字に一致します。 次の例は、この正規表現を示しています。

```csharp
string pattern = @"\b\w+?\b";
string input = "Aa Bb Cc Dd Ee Ff";
foreach (Match match in Regex.Matches(input, pattern))
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);

//  The example displays the following output:
//        'Aa' found at position 0.
//        'Bb' found at position 3.
//        'Cc' found at position 6.
//        'Dd' found at position 9.
//        'Ee' found at position 12.
//        'Ff' found at position 15.
```

```vb
Dim pattern As String = "\b\w+?\b"
 Dim input As String = "Aa Bb Cc Dd Ee Ff"
For Each match As Match In Regex.Matches(input, pattern)
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)
Next 
' The example displays the following output:
'       'Aa' found at position 0.
'       'Bb' found at position 3.
'       'Cc' found at position 6.
'       'Dd' found at position 9.
'       'Ee' found at position 12.
'       'Ff' found at position 15.
```

### <a name="match-zero-or-one-time-lazy-match-"></a>0 回または 1 回の繰り返しに一致 (最短一致): ??

**??** 量指定子は、直前の要素の 0 回または 1 回の繰り返しのうち、最も少ない繰り返しに一致します。 これは、最長一致の量指定子 **?** に対応する、最短一致の量指定子です。

たとえば、正規表現 `^\s*(System.)??Console.Write(Line)??\(??` は、文字列 "Console.Write" または "Console.WriteLine" に一致を試みます。 文字列には、"Console" の前に "System." が含まれていてもよく、最後に左かっこがあってもかまいません。 文字列は行の先頭にある必要がありますが、文字列の前に空白があってもかまいません。 次の例は、この正規表現を示しています。

```csharp
string pattern = @"^\s*(System.)??Console.Write(Line)??\(??";
string input = "System.Console.WriteLine(\"Hello!\")\n" + 
                      "Console.Write(\"Hello!\")\n" + 
                      "Console.WriteLine(\"Hello!\")\n" + 
                      "Console.ReadLine()\n" + 
                      "   Console.WriteLine";
foreach (Match match in Regex.Matches(input, pattern, 
                                      RegexOptions.IgnorePatternWhitespace | 
                                      RegexOptions.IgnoreCase | 
                                      RegexOptions.Multiline))
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);

//  The example displays the following output:
//        'System.Console.Write' found at position 0.
//        'Console.Write' found at position 36.
//        'Console.Write' found at position 61.
//        '   Console.Write' found at position 110.
```

```vb
Dim pattern As String = "^\s*(System.)??Console.Write(Line)??\(??"
Dim input As String = "System.Console.WriteLine(""Hello!"")" + vbCrLf + _
                      "Console.Write(""Hello!"")" + vbCrLf + _
                      "Console.WriteLine(""Hello!"")" + vbCrLf + _
                      "Console.ReadLine()" + vbCrLf + _
                      "   Console.WriteLine"
For Each match As Match In Regex.Matches(input, pattern, _
                                         RegexOptions.IgnorePatternWhitespace Or RegexOptions.IgnoreCase Or RegexOptions.MultiLine)
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)
Next 
' The example displays the following output:
'       'System.Console.Write' found at position 0.
'       'Console.Write' found at position 36.
'       'Console.Write' found at position 61.
'       '   Console.Write' found at position 110.
```

正規表現パターンは、次の表に示すように定義されています。

パターン | 説明
------- | ----------- 
`^` | 入力ストリームの先頭と一致します。
`\s*` | 0 個以上の空白文字と一致します。
`(System.)??` | 文字列 "System." の 0 回または 1 回の繰り返しに一致します。
`Console.Write` | 文字列 "Console.Write" と一致します。
`(Line)??` | 文字列 "Line" の 0 回または 1 回の繰り返しに一致します。
`\(??` | 左かっこの 0 回または 1 回の繰り返しに一致します。
 
### <a name="match-exactly-n-times-lazy-match-n"></a>n 回の繰り返しに一致 (最短一致): {n}?

**{**_n_**}?** 量指定子は、直前の要素の *n* 回の繰り返しに一致します。ここで、*n* は任意の整数です。 これは、最長一致の量指定子 **{**_n_**}+** に対応する、最短一致の量指定子です。

次の例では、正規表現 `\b(\w{3,}?\.){2}?\w{3,}?\b` を使用して Web サイトのアドレスを識別します。 "www.microsoft.com" と "msdn.microsoft.com" には一致しますが、"mywebsite" や "mycompany.com" には一致しない点に注意してください。

```csharp
string pattern = @"\b(\w{3,}?\.){2}?\w{3,}?\b";
string input = "www.microsoft.com msdn.microsoft.com mywebsite mycompany.com";
foreach (Match match in Regex.Matches(input, pattern))
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);

//  The example displays the following output:
//        'www.microsoft.com' found at position 0.
//        'msdn.microsoft.com' found at position 18.
```

```vb
Dim pattern As String = "\b(\w{3,}?\.){2}?\w{3,}?\b"
 Dim input As String = "www.microsoft.com msdn.microsoft.com mywebsite mycompany.com"
For Each match As Match In Regex.Matches(input, pattern)
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)
Next     
' The example displays the following output:
'       'www.microsoft.com' found at position 0.
'       'msdn.microsoft.com' found at position 18.
```

正規表現パターンは、次の表に示すように定義されています。

パターン | 説明
------- | -----------
`\b` | ワード境界から開始します。
`(\w{3,}?\.)` | 単語に含まれる 3 個以上の文字のうち、最も少ない文字の後に、ドット (ピリオド) 文字が続くパターンに一致します。 これが最初のキャプチャ グループです。
`(\w{3,}?\.){2}?` | 最初のグループのパターンの 2 回の繰り返しのうち、最も少ない繰り返しに一致します。
`\b` | ワード境界で照合を終了します。
 
### <a name="match-at-least-n-times-lazy-match-n"></a>n 回以上の繰り返しに一致 (最短一致): {n,}?

**{**_n_**,}?** 量指定子は、直前の要素の *n* 回以上の繰り返しのうち、最も少ない繰り返しに一致します。ここで、*n* は任意の整数です。 これは、最長一致の量指定子 **{**_n_**,}** に対応する、最短一致の量指定子です。

実例として、前のセクションの **{**_n_**}?** 量指定子の例を参照してください。 この例の正規表現は、3 文字以上の後にピリオドが続く文字列に一致させるために **{**_n_**,}** 量指定子を使用しています。

### <a name="match-between-n-and-m-times-lazy-match-nm"></a>n 回から m 回までの繰り返しに一致 (最短一致): {n,m}?

**{**_n_**,**_m_**}?** 量指定子は、直前の要素の *n* 回から *m* 回までの繰り返しのうち、最も少ない繰り返しに一致します。ここで、*n* と *m* は整数です。 これは、最長一致の量指定子 **{**_n_**,**_m_**}** に対応する、最短一致の量指定子です。

次の例では、正規表現 `\b[A-Z](\w*\s+){1,10}?[.!?]` は、1 個以上 10 個以下の単語が含まれる文に一致します。 18 個の単語が含まれている 1 つの文を除き、入力文字列中のすべての文に一致します。

```csharp
string pattern = @"\b[A-Z](\w*?\s*?){1,10}[.!?]";
string input = "Hi. I am writing a short note. Its purpose is " + 
                      "to test a regular expression that attempts to find " + 
                      "sentences with ten or fewer words. Most sentences " + 
                      "in this note are short.";
foreach (Match match in Regex.Matches(input, pattern))
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);

//  The example displays the following output:
//        'Hi.' found at position 0.
//        'I am writing a short note.' found at position 4.
//        'Most sentences in this note are short.' found at position 132.
```

```vb
Dim pattern As String = "\b[A-Z](\w*\s?){1,10}?[.!?]"
Dim input As String = "Hi. I am writing a short note. Its purpose is " + _
                      "to test a regular expression that attempts to find " + _
                      "sentences with ten or fewer words. Most sentences " + _
                      "in this note are short."
For Each match As Match In Regex.Matches(input, pattern)
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)
Next 
' The example displays the following output:
'       'Hi.' found at position 0.
'       'I am writing a short note.' found at position 4.
'       'Most sentences in this note are short.' found at position 132.
```

正規表現パターンは、次の表に示すように定義されています。

パターン | 説明
------- | -----------
`\b` | ワード境界から開始します。
`[A-Z]` | A から Z の大文字と一致します。
`(\w*\s+)` | 単語に含まれる 0 個以上の文字の後に空白文字が 1 個以上続くパターンと一致します。 これが最初のキャプチャ グループです。
`{1,10}?` | 前のパターンの 1 回以上 10 回以下の繰り返しのうち、最も少ない繰り返しに一致します。
`[.!?]` | 区切り文字 "."、"!"、"?" のいずれか 1 文字と一致します。
 
## <a name="greedy-and-lazy-quantifiers"></a>最長一致と最短一致の量指定子

いくつかの量指定子には次の 2 つのバージョンがあります。 

* 最長一致バージョン。 

  最長一致の量指定子は、要素をできるだけ多く一致させようとします。 


* •最短一致バージョン。 

 最短一致の量指定子は、要素をできるだけ少なく一致させようとします。 最長一致の量指定子に **?** を追加するだけで最短一致の量指定子にすることができます。

クレジット カード番号などの数値の列から最後の 4 桁の数字を取り出す、単純な正規表現について考えてみます。 最長一致の **\*** 量指定子を使用するバージョンの正規表現は、`\b.*([0-9]{4})\b` です。 しかし、2 個の数値が含まれている文字列の場合、この正規表現は、次の例に示すように 2 番目の数値の最後の 4 桁の数字だけに一致します。

```csharp
string greedyPattern = @"\b.*([0-9]{4})\b";
string input1 = "1112223333 3992991999";
foreach (Match match in Regex.Matches(input1, greedyPattern))
   Console.WriteLine("Account ending in ******{0}.", match.Groups[1].Value);

// The example displays the following output:
//       Account ending in ******1999.
```

```vb
Dim greedyPattern As String = "\b.*([0-9]{4})\b"
Dim input1 As String = "1112223333 3992991999"
For Each match As Match In Regex.Matches(input1, greedypattern)
   Console.WriteLine("Account ending in ******{0}.", match.Groups(1).Value)
Next
' The example displays the following output:
'       Account ending in ******1999.
```

この正規表現は最初の数値の一致に失敗します。**\*** 量指定子では、直前の要素をできるだけ多く繰り返して文字列全体に一致させようとして、文字列の最後まで一致と見なされるためです。

これは期待した動作ではありません。 この場合は、次の例に示すように、代わりに最短一致の **\*?** 量指定子を使用すると、両方の数値から数字を抽出できます。

```csharp
string lazyPattern = @"\b.*?([0-9]{4})\b";
string input2 = "1112223333 3992991999";
foreach (Match match in Regex.Matches(input2, lazyPattern))
   Console.WriteLine("Account ending in ******{0}.", match.Groups[1].Value);

// The example displays the following output:
//       Account ending in ******3333.
//       Account ending in ******1999.
```

```vb
Dim lazyPattern As String = "\b.*?([0-9]{4})\b"
Dim input2 As String = "1112223333 3992991999"
For Each match As Match In Regex.Matches(input2, lazypattern)
   Console.WriteLine("Account ending in ******{0}.", match.Groups(1).Value)
Next     
' The example displays the following output:
'       Account ending in ******3333.
'       Account ending in ******1999.
```

多くの場合、最長一致と最短一致の量指定子を使用した正規表現は、同じ一致結果を返します。 異なる結果を返すことが最も多いのは、任意の文字に一致するワイルドカード (**.**) のメタ文字を使用した場合です。 

## <a name="quantifiers-and-empty-matches"></a>量指定子と空一致

量指定子 **\***、**+**、および **{**_n_**,**_m_**}** と、これらに対応する最短一致の量指定子は、最小回数のキャプチャが見つかった場合、空一致の後には繰り返されません。 この規則により、可能なグループ キャプチャの最大回数が無限またはほぼ無限のときに、量指定子が空の部分式一致の無限ループに入ることを回避できます。

たとえば、次のコードは、0 個または 1 個の文字 "a" と 0 回以上一致する正規表現パターン `(a?)*,` を指定して [Regex.Match](xref:System.Text.RegularExpressions.Regex.Match(System.String)) メソッドを呼び出した結果を表示します。 単一のキャプチャ グループによって各 "a" と [String.Empty](xref:System.String.Empty) がキャプチャされますが、2 番目の空一致はないことに注意してください。これは、最初の空一致により量指定子が繰り返しを停止するためです。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = "(a?)*";
      string input = "aaabbb";
      Match match = Regex.Match(input, pattern);
      Console.WriteLine("Match: '{0}' at index {1}", 
                        match.Value, match.Index);
      if (match.Groups.Count > 1) {
         GroupCollection groups = match.Groups;
         for (int grpCtr = 1; grpCtr <= groups.Count - 1; grpCtr++) {
            Console.WriteLine("   Group {0}: '{1}' at index {2}", 
                              grpCtr, 
                              groups[grpCtr].Value,
                              groups[grpCtr].Index);
            int captureCtr = 0;
            foreach (Capture capture in groups[grpCtr].Captures) {
               captureCtr++;
               Console.WriteLine("      Capture {0}: '{1}' at index {2}", 
                                 captureCtr, capture.Value, capture.Index);
            }
         } 
      }   
   }
}
// The example displays the following output:
//       Match: 'aaa' at index 0
//          Group 1: '' at index 3
//             Capture 1: 'a' at index 0
//             Capture 2: 'a' at index 1
//             Capture 3: 'a' at index 2
//             Capture 4: '' at index 3
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "(a?)*"
      Dim input As String = "aaabbb"
      Dim match As Match = Regex.Match(input, pattern)
      Console.WriteLine("Match: '{0}' at index {1}", 
                        match.Value, match.Index)
      If match.Groups.Count > 1 Then
         Dim groups As GroupCollection = match.Groups
         For grpCtr As Integer = 1 To groups.Count - 1
            Console.WriteLine("   Group {0}: '{1}' at index {2}", 
                              grpCtr, 
                              groups(grpCtr).Value,
                              groups(grpCtr).Index)
            Dim captureCtr As Integer = 0
            For Each capture As Capture In groups(grpCtr).Captures
               captureCtr += 1
               Console.WriteLine("      Capture {0}: '{1}' at index {2}", 
                                 captureCtr, capture.Value, capture.Index)
            Next
         Next 
      End If   
   End Sub
End Module
' The example displays the following output:
'       Match: 'aaa' at index 0
'          Group 1: '' at index 3
'             Capture 1: 'a' at index 0
'             Capture 2: 'a' at index 1
'             Capture 3: 'a' at index 2
'             Capture 4: '' at index 3
```

最小回数と最大回数のキャプチャを定義するキャプチャ グループと固定回数のキャプチャを定義するキャプチャ グループとの間の実際の違いを確認するために、正規表現パターンの `(a\1|(?(1)\1)){0,2}` と `(a\1|(?(1)\1)){2}` について検討します。 どちらの正規表現も、次の表に示すように定義される単一のキャプチャ グループで構成されています。 

パターン | 説明
------- | -----------
`(a\1` | "a" と最初のキャプチャ グループの値に一致します …
`&#124;(?(1)` | … または、最初のキャプチャ グループが定義されているかどうかをテストします。 (**(?(1)** 構成要素ではキャプチャ グループは定義されないことに注意してください。)
`\1))` | 最初のキャプチャ グループが存在する場合、その値と一致します。 グループが存在しない場合、そのグループは [String.Empty](xref:System.String.Empty) と一致します。 
 
最初の正規表現では 0 ～ 2 回、このパターンとの照合が行われます。2 番目の正規表現では、厳密に 2 回です。 最初のパターンは [String.Empty](xref:System.String.Empty) の最初のキャプチャでキャプチャの最小回数に達するため、`a\1;` との照合は繰り返されません。`{0,2}` 量指定子では、最後の繰り返しでの空一致だけが許可されます。 一方、2 番目の正規表現では、2 回目の `a\1` が評価されるため、"a" に一致します。繰り返しの最小回数は 2 で、空一致の後でエンジンが繰り返さなければならない回数になります。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern, input;

      pattern = @"(a\1|(?(1)\1)){0,2}";
      input = "aaabbb"; 

      Console.WriteLine("Regex pattern: {0}", pattern);
      Match match = Regex.Match(input, pattern);
      Console.WriteLine("Match: '{0}' at position {1}.", 
                        match.Value, match.Index);
      if (match.Groups.Count > 1) {
         for (int groupCtr = 1; groupCtr <= match.Groups.Count - 1; groupCtr++)
         {
            Group group = match.Groups[groupCtr];         
            Console.WriteLine("   Group: {0}: '{1}' at position {2}.", 
                              groupCtr, group.Value, group.Index);
            int captureCtr = 0;
            foreach (Capture capture in group.Captures) {
               captureCtr++;
               Console.WriteLine("      Capture: {0}: '{1}' at position {2}.", 
                                 captureCtr, capture.Value, capture.Index);
            }   
         }
      }
      Console.WriteLine();

      pattern = @"(a\1|(?(1)\1)){2}";
      Console.WriteLine("Regex pattern: {0}", pattern);
      match = Regex.Match(input, pattern);
         Console.WriteLine("Matched '{0}' at position {1}.", 
                           match.Value, match.Index);
      if (match.Groups.Count > 1) {
         for (int groupCtr = 1; groupCtr <= match.Groups.Count - 1; groupCtr++)
         {
            Group group = match.Groups[groupCtr];         
            Console.WriteLine("   Group: {0}: '{1}' at position {2}.", 
                              groupCtr, group.Value, group.Index);
            int captureCtr = 0;
            foreach (Capture capture in group.Captures) {
               captureCtr++;
               Console.WriteLine("      Capture: {0}: '{1}' at position {2}.", 
                                 captureCtr, capture.Value, capture.Index);
            }   
         }
      }
   }
}
// The example displays the following output:
//       Regex pattern: (a\1|(?(1)\1)){0,2}
//       Match: '' at position 0.
//          Group: 1: '' at position 0.
//             Capture: 1: '' at position 0.
//       
//       Regex pattern: (a\1|(?(1)\1)){2}
//       Matched 'a' at position 0.
//          Group: 1: 'a' at position 0.
//             Capture: 1: '' at position 0.
//             Capture: 2: 'a' at position 0.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern, input As String

      pattern = "(a\1|(?(1)\1)){0,2}"
      input = "aaabbb" 

      Console.WriteLine("Regex pattern: {0}", pattern)
      Dim match As Match = Regex.Match(input, pattern)
      Console.WriteLine("Match: '{0}' at position {1}.", 
                        match.Value, match.Index)
      If match.Groups.Count > 1 Then
         For groupCtr As Integer = 1 To match.Groups.Count - 1
            Dim group As Group = match.Groups(groupCtr)         
            Console.WriteLine("   Group: {0}: '{1}' at position {2}.", 
                              groupCtr, group.Value, group.Index)
            Dim captureCtr As Integer = 0
            For Each capture As Capture In group.Captures
               captureCtr += 1
               Console.WriteLine("      Capture: {0}: '{1}' at position {2}.", 
                                 captureCtr, capture.Value, capture.Index)
            Next   
         Next
      End If
      Console.WriteLine()

      pattern = "(a\1|(?(1)\1)){2}"
      Console.WriteLine("Regex pattern: {0}", pattern)
      match = Regex.Match(input, pattern)
         Console.WriteLine("Matched '{0}' at position {1}.", 
                           match.Value, match.Index)
      If match.Groups.Count > 1 Then
         For groupCtr As Integer = 1 To match.Groups.Count - 1
            Dim group As Group = match.Groups(groupCtr)         
            Console.WriteLine("   Group: {0}: '{1}' at position {2}.", 
                              groupCtr, group.Value, group.Index)
            Dim captureCtr As Integer = 0
            For Each capture As Capture In group.Captures
               captureCtr += 1
               Console.WriteLine("      Capture: {0}: '{1}' at position {2}.", 
                                 captureCtr, capture.Value, capture.Index)
            Next   
         Next
      End If
   End Sub
End Module
' The example displays the following output:
'       Regex pattern: (a\1|(?(1)\1)){0,2}
'       Match: '' at position 0.
'          Group: 1: '' at position 0.
'             Capture: 1: '' at position 0.
'       
'       Regex pattern: (a\1|(?(1)\1)){2}
'       Matched 'a' at position 0.
'          Group: 1: 'a' at position 0.
'             Capture: 1: '' at position 0.
'             Capture: 2: 'a' at position 0.
```

## <a name="see-also"></a>関連項目

[正規表現言語 - クイック リファレンス](quick-ref.md)

[正規表現におけるバックトラッキング](backtracking.md)




<!--HONumber=Nov16_HO1-->


