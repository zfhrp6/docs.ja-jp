---
title: "標準 TimeSpan 書式指定文字列"
description: "標準 TimeSpan 書式指定文字列"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 4e0f02f1-4abd-47b5-8995-5c3ff45b0ce1
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: a31f0da1f5b502d8b983f4d496c4b9a520b0309c

---

# <a name="standard-timespan-format-strings"></a>標準 TimeSpan 書式指定文字列

標準の [TimeSpan](xref:System.TimeSpan) 書式指定文字列は、単一の書式指定子を使用して、書式設定操作によって生成される [TimeSpan](xref:System.TimeSpan) 値のテキスト表現を定義します。 空白を含む複数の文字で構成される書式指定文字列は、カスタムの [TimeSpan](xref:System.TimeSpan) 書式指定文字列として解釈されます。 詳細については、「[カスタム TimeSpan 書式指定文字列](custom-timespan.md)」をご覧ください。

[TimeSpan](xref:System.TimeSpan) 値の文字列形式は、[TimeSpan.ToString](xref:System.TimeSpan.ToString) メソッドのオーバーロードの呼び出しと、[String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) などの複合書式指定をサポートするメソッドによって生成されます。 詳細については、「[型の書式設定](formatting-types.md)」と「[複合書式指定](composite-format.md)」をご覧ください。 次の例では、書式設定操作で標準書式指定文字列を使用する方法を示しています。

```csharp
using System;

public class Example
{
   public static void Main()
   {
      TimeSpan duration = new TimeSpan(1, 12, 23, 62);
      string output = "Time of Travel: " + duration.ToString("c");
      Console.WriteLine(output);

      Console.WriteLine("Time of Travel: {0:c}", duration); 
   }
}
// The example displays the following output:
//       Time of Travel: 1.12:24:02
//       Time of Travel: 1.12:24:02
```

```vb
Module Example
   Public Sub Main()
      Dim duration As New TimeSpan(1, 12, 23, 62)
      Dim output As String = "Time of Travel: " + duration.ToString("c")
      Console.WriteLine(output)

      Console.WriteLine("Time of Travel: {0:c}", duration) 
   End Sub
End Module
' The example displays the following output:
'       Time of Travel: 1.12:24:02
'       Time of Travel: 1.12:24:02
```

標準の [TimeSpan](xref:System.TimeSpan) 書式指定文字列は、解析操作に必要な入力文字列の書式を定義するために [TimeSpan.ParseExact](xref:System.TimeSpan.ParseExact(System.String,System.String,System.IFormatProvider)) メソッドと [TimeSpan.TryParseExact](xref:System.TimeSpan.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.TimeSpanStyles,System.TimeSpan@)) メソッドでも使用されます。 (解析では、特定の値の文字列形式が、その値に変換されます)。次のコード例では、解析操作で標準書式指定文字列を使用する方法を示しています。

```csharp
using System;

public class Example
{
   public static void Main()
   {
      string value = "1.03:14:56.1667";
      TimeSpan interval;
      try {
         interval = TimeSpan.ParseExact(value, "c", null);
         Console.WriteLine("Converted '{0}' to {1}", value, interval);
      }   
      catch (FormatException) {
         Console.WriteLine("{0}: Bad Format", value);
      }   
      catch (OverflowException) {
         Console.WriteLine("{0}: Out of Range", value);
      }

      if (TimeSpan.TryParseExact(value, "c", null, out interval))
         Console.WriteLine("Converted '{0}' to {1}", value, interval);
      else
         Console.WriteLine("Unable to convert {0} to a time interval.", 
                           value);
   }
}
// The example displays the following output:
//       Converted '1.03:14:56.1667' to 1.03:14:56.1667000
//       Converted '1.03:14:56.1667' to 1.03:14:56.1667000
```

```vb
Module Example
   Public Sub Main()
      Dim value As String = "1.03:14:56.1667"
      Dim interval As TimeSpan
      Try
         interval = TimeSpan.ParseExact(value, "c", Nothing)
         Console.WriteLine("Converted '{0}' to {1}", value, interval)
      Catch e As FormatException
         Console.WriteLine("{0}: Bad Format", value)
      Catch e As OverflowException
         Console.WriteLine("{0}: Out of Range", value)
      End Try

      If TimeSpan.TryParseExact(value, "c", Nothing, interval) Then
         Console.WriteLine("Converted '{0}' to {1}", value, interval)
      Else
         Console.WriteLine("Unable to convert {0} to a time interval.", 
                           value)
      End If                
   End Sub
End Module
' The example displays the following output:
'       Converted '1.03:14:56.1667' to 1.03:14:56.1667000
'       Converted '1.03:14:56.1667' to 1.03:14:56.1667000
```

標準の時間間隔書式指定子を次の表に示します。

書式指定子 | 名前 | 説明 | 例
---------------- | ---- | ----------- | --------
"c" | 固定 (不変) 書式 | この指定子はカルチャに依存しません。 [-][d’.’]hh’:’mm’:’ss[‘.’fffffff] の書式になります。 ("t" と "T" の各書式指定文字列によって生成される結果は同じになります。) | `TimeSpan.Zero -> 00:00:00`; `New TimeSpan(0, 0, 30, 0) -> 00:30:00`; `New TimeSpan(3, 17, 25, 30, 500) -> 3.17:25:30.5000000`
"g" | 一般の短い書式 | この指定子は必要なものだけを出力します。 カルチャに依存し、[-][d’:’]h’:’mm’:’ss[.FFFFFFF] の書式になります。 | `New TimeSpan(1, 3, 16, 50, 500) -> 1:3:16:50.5 (en-US)`; `New TimeSpan(1, 3, 16, 50, 500) -> 1:3:16:50,5 (fr-FR)`; `New TimeSpan(1, 3, 16, 50, 599) -> 1:3:16:50.599 (en-US)`; `New TimeSpan(1, 3, 16, 50, 599) -> 1:3:16:50,599 (fr-FR)`
"G" | 一般の長い書式 | この指定子は、常に日数と 7 桁の小数部を出力します。 カルチャに依存し、[-]d’:’hh’:’mm’:’ss.fffffff の書式になります。 | `New TimeSpan(18, 30, 0) -> 0:18:30:00.0000000 (en-US)`; `New TimeSpan(18, 30, 0) -> 0:18:30:00,0000000 (fr-FR)` 

## <a name="the-constant-c-format-specifier"></a>固定の ("c") 書式指定子

"c" 書式指定子は、次の書式で [TimeSpan](xref:System.TimeSpan) 値の文字列形式を返します。

[-][_d_.]_hh_:_mm_:_ss_[._fffffff_]

角かっこ ([ および ]) 内の要素は省略可能です。 コロン (:) とピリオド (.) は、リテラル文字です。 残りの要素について次の表で説明します。 

要素 | 説明
------- | -----------
- | 負の時間間隔を示す、省略可能なマイナス記号。
*d* | 先行ゼロを付けない、省略可能な日数。
*hh* | "00" ～ "23" の範囲の時間数。
*mm* | "00" ～ "59" の範囲の分数。
*ss* | "0" ～ "59" の範囲の秒数。
*fffffff* | 省略可能な秒の小数部。 "0000001" (1 ティック、つまり 1,000 万分の 1 秒) ～ "9999999" (1,000 万分の 9,999,999 秒、つまり 1 秒より 1 ティック少ない) までの範囲の値が可能です。 

"g" および "G" 書式指定子とは異なり、"c" 書式指定子はカルチャに依存しません。 不変で、かつ .NET Framework 4 より前のすべての .NET Framework バージョンに共通する [TimeSpan](xref:System.TimeSpan) 値の文字列形式を生成します。 "c" は、既定の [TimeSpan](xref:System.TimeSpan) 書式文字列です。[TimeSpan.ToString](xref:System.TimeSpan.ToString) メソッドは、"c" 書式指定文字列を使用して時間間隔値の書式を設定します。

> [!NOTE]
> [TimeSpan](xref:System.TimeSpan) では、動作が "c" 標準書式指定文字列と同じである "t" および "T" の標準書式指定文字列もサポートされます。

次の例では、2 つの [TimeSpan](xref:System.TimeSpan) オブジェクトのインスタンスを作成し、これらを使用して算術演算を実行し、結果を表示します。 いずれの場合も、複合書式指定を使用し、"c" 書式指定子を使用して [TimeSpan](xref:System.TimeSpan) 値を表示します。

```csharp
using System;

public class Example
{
   public static void Main()
   {
      TimeSpan interval1, interval2;
      interval1 = new TimeSpan(7, 45, 16);
      interval2 = new TimeSpan(18, 12, 38);

      Console.WriteLine("{0:c} - {1:c} = {2:c}", interval1, 
                        interval2, interval1 - interval2);
      Console.WriteLine("{0:c} + {1:c} = {2:c}", interval1, 
                        interval2, interval1 + interval2);

      interval1 = new TimeSpan(0, 0, 1, 14, 365);
      interval2 = TimeSpan.FromTicks(2143756);  
      Console.WriteLine("{0:c} + {1:c} = {2:c}", interval1, 
                        interval2, interval1 + interval2);
   }
}
// The example displays the following output:
//       07:45:16 - 18:12:38 = -10:27:22
//       07:45:16 + 18:12:38 = 1.01:57:54
//       00:01:14.3650000 + 00:00:00.2143756 = 00:01:14.5793756
```

```vb
Module Example
   Public Sub Main()
      Dim interval1, interval2 As TimeSpan
      interval1 = New TimeSpan(7, 45, 16)
      interval2 = New TimeSpan(18, 12, 38)

      Console.WriteLine("{0:c} - {1:c} = {2:c}", interval1, 
                        interval2, interval1 - interval2)
      Console.WriteLine("{0:c} + {1:c} = {2:c}", interval1, 
                        interval2, interval1 + interval2)

      interval1 = New TimeSpan(0, 0, 1, 14, 365)
      interval2 = TimeSpan.FromTicks(2143756)      
      Console.WriteLine("{0:c} + {1:c} = {2:c}", interval1, 
                        interval2, interval1 + interval2)
   End Sub
End Module
' The example displays the following output:
'       07:45:16 - 18:12:38 = -10:27:22
'       07:45:16 + 18:12:38 = 1.01:57:54
'       00:01:14.3650000 + 00:00:00.2143756 = 00:01:14.5793756
```

## <a name="the-general-short-g-format-specifier"></a>一般の短い ("g") 書式指定子

"g" [TimeSpan](xref:System.TimeSpan) 書式指定子は、必要な要素のみを含めることによって、コンパクトな形式で [TimeSpan](xref:System.TimeSpan) 値の文字列形式を返します。 次の書式を使用します。

[-][_d_:]_h_:_mm_:_ss_[._FFFFFFF_]

角かっこ ([ および ]) 内の要素は省略可能です。 コロン (:) は、リテラル文字です。 残りの要素について次の表で説明します。

要素 | 説明
------- | -----------
- | 負の時間間隔を示す、省略可能なマイナス記号。
*d* | 先行ゼロを付けない、省略可能な日数。
*hh* | 先行ゼロを付けない、"0" ～ "23" の範囲の時間数。 
*mm* | "00" ～ "59" の範囲の分数。
*ss* | "0" ～ "59" の範囲の秒数。
」を参照してください。 | 秒の小数部の区切り記号。
*FFFFFFF* | 秒の小数部。 可能な限り少ない桁数が表示されます。

"G" 書式指定子と同様に、"g" 書式指定子はローカライズされます。 その秒の小数部の区切り記号は、現在のカルチャに基づきます。

次の例では、2 つの [TimeSpan](xref:System.TimeSpan) オブジェクトのインスタンスを作成し、これらを使用して算術演算を実行し、結果を表示します。 いずれの場合も、複合書式指定を使用し、"g" 書式指定子を使用して [TimeSpan](xref:System.TimeSpan) 値を表示します。 また、現在のシステム カルチャ (この場合は、英語 - 米国 (en-US)) とフランス語 - フランス (fr-FR) カルチャの書式指定規則を使用して、[TimeSpan](xref:System.TimeSpan) 値の書式を設定します。

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      TimeSpan interval1, interval2;
      interval1 = new TimeSpan(7, 45, 16);
      interval2 = new TimeSpan(18, 12, 38);

      Console.WriteLine("{0:g} - {1:g} = {2:g}", interval1, 
                        interval2, interval1 - interval2);
      Console.WriteLine(String.Format(new CultureInfo("fr-FR"), 
                        "{0:g} + {1:g} = {2:g}", interval1, 
                        interval2, interval1 + interval2));

      interval1 = new TimeSpan(0, 0, 1, 14, 36);
      interval2 = TimeSpan.FromTicks(2143756);      
      Console.WriteLine("{0:g} + {1:g} = {2:g}", interval1, 
                        interval2, interval1 + interval2);
   }
}
// The example displays the following output:
//       7:45:16 - 18:12:38 = -10:27:22
//       7:45:16 + 18:12:38 = 1:1:57:54
//       0:01:14.036 + 0:00:00.2143756 = 0:01:14.2503756
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim interval1, interval2 As TimeSpan
      interval1 = New TimeSpan(7, 45, 16)
      interval2 = New TimeSpan(18, 12, 38)

      Console.WriteLine("{0:g} - {1:g} = {2:g}", interval1, 
                        interval2, interval1 - interval2)
      Console.WriteLine(String.Format(New CultureInfo("fr-FR"), 
                        "{0:g} + {1:g} = {2:g}", interval1, 
                        interval2, interval1 + interval2))

      interval1 = New TimeSpan(0, 0, 1, 14, 36)
      interval2 = TimeSpan.FromTicks(2143756)      
      Console.WriteLine("{0:g} + {1:g} = {2:g}", interval1, 
                        interval2, interval1 + interval2)
   End Sub
End Module
' The example displays the following output:
'       7:45:16 - 18:12:38 = -10:27:22
'       7:45:16 + 18:12:38 = 1:1:57:54
'       0:01:14.036 + 0:00:00.2143756 = 0:01:14.2503756
```

## <a name="the-general-long-g-format-specifier"></a>一般の長い ("G") 書式指定子

"G" [TimeSpan](xref:System.TimeSpan) 書式指定子は、常に日数と秒の小数部の両方を含む長い形式で、[TimeSpan](xref:System.TimeSpan) 値の文字列形式を返します。 "G" 標準書式指定子によって生成される文字列は、次の書式になります。

[-]*d*:*hh*:*mm*:*ss*.*fffffff*

角かっこ ([ および ]) 内の要素は省略可能です。 コロン (:) は、リテラル文字です。 残りの要素について次の表で説明します。

要素 | 説明
------- | -----------
- | 負の時間間隔を示す、省略可能なマイナス記号。
*d* | 先行ゼロを付けない、省略可能な日数。
*hh* | "0" ～ "23" の範囲の時間数。 
*mm* | "00" ～ "59" の範囲の分数。
*ss* | "0" ～ "59" の範囲の秒数。
」を参照してください。 | 秒の小数部の区切り記号。
*fffffff* | 秒の小数部。

"G" 書式指定子と同様に、"g" 書式指定子はローカライズされます。 その秒の小数部の区切り記号は、現在のカルチャに基づきます。

次の例では、2 つの [TimeSpan](xref:System.TimeSpan) オブジェクトのインスタンスを作成し、これらを使用して算術演算を実行し、結果を表示します。 いずれの場合も、複合書式指定を使用し、"G" 書式指定子を使用して [TimeSpan](xref:System.TimeSpan) 値を表示します。 また、現在のシステム カルチャ (この場合は、英語 - 米国 (en-US)) とフランス語 - フランス (fr-FR) カルチャの書式指定規則を使用して、[TimeSpan](xref:System.TimeSpan) 値の書式を設定します。 

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      TimeSpan interval1, interval2;
      interval1 = new TimeSpan(7, 45, 16);
      interval2 = new TimeSpan(18, 12, 38);

      Console.WriteLine("{0:G} - {1:G} = {2:G}", interval1, 
                        interval2, interval1 - interval2);
      Console.WriteLine(String.Format(new CultureInfo("fr-FR"), 
                        "{0:G} + {1:G} = {2:G}", interval1, 
                        interval2, interval1 + interval2));

      interval1 = new TimeSpan(0, 0, 1, 14, 36);
      interval2 = TimeSpan.FromTicks(2143756);      
      Console.WriteLine("{0:G} + {1:G} = {2:G}", interval1, 
                        interval2, interval1 + interval2);
   }
}
// The example displays the following output:
//       0:07:45:16.0000000 - 0:18:12:38.0000000 = -0:10:27:22.0000000
//       0:07:45:16,0000000 + 0:18:12:38,0000000 = 1:01:57:54,0000000
//       0:00:01:14.0360000 + 0:00:00:00.2143756 = 0:00:01:14.2503756
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim interval1, interval2 As TimeSpan
      interval1 = New TimeSpan(7, 45, 16)
      interval2 = New TimeSpan(18, 12, 38)

      Console.WriteLine("{0:G} - {1:G} = {2:G}", interval1, 
                        interval2, interval1 - interval2)
      Console.WriteLine(String.Format(New CultureInfo("fr-FR"), 
                        "{0:G} + {1:G} = {2:G}", interval1, 
                        interval2, interval1 + interval2))

      interval1 = New TimeSpan(0, 0, 1, 14, 36)
      interval2 = TimeSpan.FromTicks(2143756)      
      Console.WriteLine("{0:G} + {1:G} = {2:G}", interval1, 
                        interval2, interval1 + interval2)
   End Sub
End Module
' The example displays the following output:
'       0:07:45:16.0000000 - 0:18:12:38.0000000 = -0:10:27:22.0000000
'       0:07:45:16,0000000 + 0:18:12:38,0000000 = 1:01:57:54,0000000
'       0:00:01:14.0360000 + 0:00:00:00.2143756 = 0:00:01:14.2503756
```

## <a name="see-also"></a>関連項目

[型の書式設定](formatting-types.md)

[複合書式指定](composite-format.md)

[文字列の解析](parsing-strings.md)




<!--HONumber=Nov16_HO1-->


