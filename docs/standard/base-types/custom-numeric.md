---
title: "カスタム数値書式指定文字列"
description: "カスタム数値書式指定文字列"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/25/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 7b1c16ee-956f-4e9c-8502-c3dd6598c51d
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: e36c0117f6f011589299fa59a8abd139870c2257

---

# <a name="custom-numeric-format-strings"></a>カスタム数値書式指定文字列

1 つ以上のカスタム数値指定子で構成されるカスタム数値書式指定文字列を作成して、数値データの書式設定方法を定義できます。 カスタム数値書式指定文字列は、[標準の数値書式指定文字列](standard-numeric.md)ではない任意の書式指定文字列です。 

カスタム数値書式指定文字列は、すべての数値型の `ToString` メソッドの一部のオーバーロードでサポートされています。 たとえば、[Int32](xref:System.Int32) 型の [ToString(String)](xref:System.Int32.ToString(System.String)) メソッドおよび [ToString(String, IFormatProvider)](xref:System.Int32.ToString(System.String,System.IFormatProvider)) メソッドに数値書式指定文字列を指定できます。 カスタム数値書式指定文字列は、.NET Framework の[複合書式指定](composite-format.md)機能でもサポートされています。この機能を使用するメソッドには、[Console](xref:System.Console) クラスおよび [StreamWriter](xref:System.IO.StreamWriter) クラスの一部の `Write` メソッドと `WriteLine` メソッド、[String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) メソッド、および [StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)) メソッドがあります。

次の表に、カスタム数値書式指定子の説明および書式指定子ごとのサンプル出力を示します。 カスタム数値書式指定文字列の使用方法については、「[メモ](#notes)」を参照してください。それらを使用する包括的な例については、「[例](#example)」を参照してください。

書式指定子 | 名前 | 説明 | 例
---------------- | ---- | ----------- | --------
"0" | ゼロ プレースホルダー | 対応する数字でゼロを置き換えます。置き換えが行われるのは、対応する数字が存在する場合です。それ以外の場合は、結果の文字列にはゼロが表示されます。 | `1234.5678 ("00000") -> 01235`; `0.45678 ("0.00", en-US) -> 0.46`; `0.45678 ("0.00", fr-FR) -> 0,46`
"#" | 桁プレースホルダー | 対応する数字で "#" 記号を置き換えます。置き換えが行われるのは、対応する数字が存在する場合です。それ以外の場合は、結果の文字列に数字は表示されません。 入力文字列の対応する数字が意味を持たない 0 の場合、結果の文字列に数字は表示されません。 たとえば、0003 ("####") -> 3 です。 | `1234.5678 ("#####") -> 1235`; `0.45678 ("#.##", en-US) -> .46`; `0.45678 ("#.##", fr-FR) -> ,46`
"." | 小数点 | 結果の文字列の小数点位置を決定します。 | `0.45678 ("0.00", en-US) -> 0.46`; `0.45678 ("0.00", fr-FR) -> 0,46`
"," | 桁区切り記号および数値の位取り | 桁区切り記号および数値位取り指定子の両方として機能します。 桁区切り記号としては、各グループの間に、ローカライズされた桁区切り記号文字を挿入します。 数値位取り指定子としては、指定されたコンマごとに、数値を 1000 で除算します。 | 桁区切り記号: `2147483647 ("##,#", en-US) -> 2,147,483,647`; `2147483647 ("##,#", es-ES) -> 2.147.483.647` 位取り指定子: `2147483647 ("#,#,,", en-US) -> 2,147`; `2147483647 ("#,#,,", es-ES) -> 2.147`
"%" | パーセント プレースホルダー | 数値に 100 を乗算し、結果の文字列に、ローカライズされたパーセント記号を挿入します。 | `0.3697 ("%#0.00", en-US) -> %36.97`; `0.3697 ("%#0.00", el-GR) -> %36,97`; `0.3697 ("##.0 %", en-US) -> 37.0 %`; `0.3697 ("##.0 %", el-GR) -> 37,0 %`
"‰" | パーミル プレースホルダー | 数値に 1000 を乗算し、結果の文字列にローカライズされたパーミル記号を挿入します。 | `0.03697 ("#0.00‰", en-US) -> 36.97‰`; `0.03697 ("#0.00‰", ru-RU) -> 36,97‰`
"E0"、"E+0"、"E-0"、"e0"、"e+0"、"e-0" | 指数表記 | 後に 0 (ゼロ) が 1 つ以上続く場合に、指数表記を使用して結果の書式を設定します。 大文字 "E" と小文字 "e" は、結果の文字列の指数記号を大文字にするか小文字にするかを示します。 "E" 文字または "e" 文字の後に続くゼロの数によって、指数部の最小桁数が決まります。 正符号 (+) は、符号文字が指数部の前に常に挿入されることを示します。 負符号 (-) は、指数部が負の値の場合にだけその前に符号文字が挿入されることを示します。 | `987654 ("#0.0e0") -> 98.8e4`; `1503.92311 ("0.0##e+00") -> 1.504e+03`; `1.8901385E-16 ("0.0e+00") -> 1.9e-16`
\ | エスケープ文字 | この文字の次の文字はカスタム書式指定子ではなくリテラルとして解釈されます。 | `987654 ("\###00\#") -> #987654#`
'string'、"string" | リテラル文字列区切り記号 | 囲まれた文字列が結果の文字列にそのままコピーされることを示します。 | `68 ("# ' degrees'") -> 68 degrees`
; | セクション区切り記号 | 正の数値、負の数値、およびゼロの数値に対して、別々の書式指定文字列を使用してセクションを定義します。 | `12.345 ("#0.0#;(#0.0#);-\0-") -> 12.35`; `0 ("#0.0#;(#0.0#);-\0-") -> -0-`; `-12.345 ("#0.0#;(#0.0#);-\0-") -> (12.35)`; `12.345 ("#0.0#;(#0.0#)") -> 12.35`; `0 ("#0.0#;(#0.0#)") -> 0.0 ; -12.345 ("#0.0#;(#0.0#)") -> (12.35)`
その他 | 上記以外のすべての文字 | 文字が結果の文字列にそのままコピーされます。 | `68 ("# °") -> 68 °`

以降では、それぞれのカスタム数値書式指定子について詳しく説明します。

## <a name="the-0-custom-specifier"></a>"0" カスタム指定子

"0" カスタム書式指定子は、ゼロ プレースホルダー記号として機能します。 書式が設定される値で、書式指定文字列のゼロに対応する位置に数字がある場合には、この数字が結果の文字列にコピーされます。それ以外の場合は、結果の文字列にゼロが表示されます。 整数部の左端のゼロの位置と、小数部の右端のゼロの位置によって、常に結果の文字列に示される桁数が決まります。 

指定子が "00" の場合、値は一の位で丸められ、小数点以下のゼロは常に切り捨てられます。 たとえば、"00" を指定して 34.5 を書式設定すると、結果の値は 35 になります。

次の例では、ゼロ プレースホルダーを含むカスタム書式指定文字列を使って書式設定された複数の値を表示します。

```csharp
double value;

value = 123;
Console.WriteLine(value.ToString("00000"));
Console.WriteLine(String.Format("{0:00000}", value));
// Displays 00123

value = 1.2;
Console.WriteLine(value.ToString("0.00", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                "{0:0.00}", value));
// Displays 1.20

Console.WriteLine(value.ToString("00.00", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:00.00}", value));
// Displays 01.20

CultureInfo daDK = CultureInfo.CreateSpecificCulture("da-DK");
Console.WriteLine(value.ToString("00.00", daDK)); 
Console.WriteLine(String.Format(daDK, "{0:00.00}", value));
// Displays 01,20

value = .56;
Console.WriteLine(value.ToString("0.0", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0.0}", value));
// Displays 0.6

value = 1234567890;
Console.WriteLine(value.ToString("0,0", CultureInfo.InvariantCulture)); 
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0,0}", value)); 
// Displays 1,234,567,890      

CultureInfo elGR = CultureInfo.CreateSpecificCulture("el-GR");
Console.WriteLine(value.ToString("0,0", elGR)); 
Console.WriteLine(String.Format(elGR, "{0:0,0}", value));   
// Displays 1.234.567.890

value = 1234567890.123456;
Console.WriteLine(value.ToString("0,0.0", CultureInfo.InvariantCulture));   
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0,0.0}", value));   
// Displays 1,234,567,890.1  

value = 1234.567890;
Console.WriteLine(value.ToString("0,0.00", CultureInfo.InvariantCulture));  
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0,0.00}", value));  
// Displays 1,234.57
```

```vb
Dim value As Double

value = 123
Console.WriteLine(value.ToString("00000"))
Console.WriteLine(String.Format("{0:00000}", value))
' Displays 00123

value = 1.2
Console.Writeline(value.ToString("0.00", CultureInfo.InvariantCulture))
Console.Writeline(String.Format(CultureInfo.InvariantCulture, 
                  "{0:0.00}", value))
' Displays 1.20
Console.WriteLine(value.ToString("00.00", CultureInfo.InvariantCulture))
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:00.00}", value))
' Displays 01.20
Dim daDK As CultureInfo = CultureInfo.CreateSpecificCulture("da-DK")
Console.WriteLine(value.ToString("00.00", daDK))
Console.WriteLine(String.Format(daDK, "{0:00.00}", value))
' Displays 01,20

value = .56
Console.WriteLine(value.ToString("0.0", CultureInfo.InvariantCulture))
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0.0}", value))
' Displays 0.6

value = 1234567890
Console.WriteLine(value.ToString("0,0", CultureInfo.InvariantCulture))  
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0,0}", value))  
' Displays 1,234,567,890      
Dim elGR As CultureInfo = CultureInfo.CreateSpecificCulture("el-GR")
Console.WriteLine(value.ToString("0,0", elGR))
Console.WriteLine(String.Format(elGR, "{0:0,0}", value))    
' Displays 1.234.567.890

value = 1234567890.123456
Console.WriteLine(value.ToString("0,0.0", CultureInfo.InvariantCulture))    
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0,0.0}", value))    
' Displays 1,234,567,890.1  

value = 1234.567890
Console.WriteLine(value.ToString("0,0.00", CultureInfo.InvariantCulture))   
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0,0.00}", value))   
' Displays 1,234.57
```

## <a name="the-custom-specifier"></a>"#" カスタム指定子

"#" カスタム書式指定子は、桁プレースホルダー記号として機能します。 書式が指定される値で、書式指定文字列の "#" 記号に対応する位置に数字がある場合には、この数字が結果の文字列にコピーされます。 それ以外の場合は、結果の文字列のこの位置には何も格納されません。 

この指定子では、文字列の唯一の桁の値がゼロであっても、この桁が有効桁でない場合には、ゼロは表示されません。 表示される数値の有効桁である場合にのみゼロが表示されます。 

書式指定文字列が "##" の場合は、値は一の位で丸められ、小数点以下のゼロは常に切り捨てられます。 たとえば、"##" を指定して 34.5 を書式設定すると、結果の値は 35 になります。

次の例では、桁プレースホルダーを含むカスタム書式指定文字列を使って書式設定された複数の値を表示します。

```csharp
double value;

value = 1.2;
Console.WriteLine(value.ToString("#.##", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#.##}", value));
// Displays 1.2

value = 123;
Console.WriteLine(value.ToString("#####"));
Console.WriteLine(String.Format("{0:#####}", value));
// Displays 123

value = 123456;
Console.WriteLine(value.ToString("[##-##-##]"));      
Console.WriteLine(String.Format("{0:[##-##-##]}", value));      
// Displays [12-34-56]

value = 1234567890;
Console.WriteLine(value.ToString("#"));
Console.WriteLine(String.Format("{0:#}", value));
// Displays 1234567890

Console.WriteLine(value.ToString("(###) ###-####"));
Console.WriteLine(String.Format("{0:(###) ###-####}", value));
// Displays (123) 456-7890
```

```vb
Dim value As Double

value = 1.2
Console.WriteLine(value.ToString("#.##", CultureInfo.InvariantCulture))
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#.##}", value))
' Displays 1.2

value = 123
Console.WriteLine(value.ToString("#####"))
Console.WriteLine(String.Format("{0:#####}", value))
' Displays 123

value = 123456
Console.WriteLine(value.ToString("[##-##-##]"))      
Console.WriteLine(String.Format("{0:[##-##-##]}", value))      
' Displays [12-34-56]

value = 1234567890
Console.WriteLine(value.ToString("#"))
Console.WriteLine(String.Format("{0:#}", value))
' Displays 1234567890

Console.WriteLine(value.ToString("(###) ###-####"))
Console.WriteLine(String.Format("{0:(###) ###-####}", value))
' Displays (123) 456-7890
```

欠落している数字や先頭のゼロをスペースに置き換える結果の文字列を戻すには、次の例に示すように、[複合書式指定](composite-format.md)機能を使用して、フィールド幅を指定します。

```csharp
using System;

public class Example
{
   public static void Main()
   {
      Double value = .324;
      Console.WriteLine("The value is: '{0,5:#.###}'", value);
   }
}
// The example displays the following output if the current culture
// is en-US:
//      The value is: ' .324'
```

```vb
Module Example
   Public Sub Main()
      Dim value As Double = .324
      Console.WriteLine("The value is: '{0,5:#.###}'", value)
   End Sub
End Module
' The example displays the following output if the current culture
' is en-US:
'      The value is: ' .324'
```

## <a name="the-custom-specifier"></a>"." カスタム指定子

"." カスタム書式指定子は、ローカライズされた小数点を結果の文字列に挿入します。 書式指定文字列の 1 番目のピリオドによって、書式設定後の値での小数点の位置が決定します。指定されている他のピリオドは無視されます。 

結果の文字列の中で小数点として使用される文字は、ピリオドであるとは限りません。書式設定を制御する [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) オブジェクトの [NumberDecimalSeparator](xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator) プロパティによって決定されます。

次の例では、結果として得られるさまざまな文字列の小数点位置を、"." 書式指定子を使って定義しています。

```csharp
double value;

value = 1.2;
Console.WriteLine(value.ToString("0.00", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0.00}", value));
// Displays 1.20

Console.WriteLine(value.ToString("00.00", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:00.00}", value));
// Displays 01.20

Console.WriteLine(value.ToString("00.00", 
                CultureInfo.CreateSpecificCulture("da-DK")));
Console.WriteLine(String.Format(CultureInfo.CreateSpecificCulture("da-DK"),
                "{0:00.00}", value));
// Displays 01,20

value = .086;
Console.WriteLine(value.ToString("#0.##%", CultureInfo.InvariantCulture)); 
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#0.##%}", value)); 
// Displays 8.6%

value = 86000;
Console.WriteLine(value.ToString("0.###E+0", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                "{0:0.###E+0}", value));
// Displays 8.6E+4
```

```vb
Dim value As Double

  value = 1.2
  Console.Writeline(value.ToString("0.00", CultureInfo.InvariantCulture))
  Console.Writeline(String.Format(CultureInfo.InvariantCulture, 
                                  "{0:0.00}", value))
  ' Displays 1.20

  Console.WriteLine(value.ToString("00.00", CultureInfo.InvariantCulture))
  Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                  "{0:00.00}", value))
  ' Displays 01.20

  Console.WriteLine(value.ToString("00.00", _
                    CultureInfo.CreateSpecificCulture("da-DK")))
  Console.WriteLine(String.Format(CultureInfo.CreateSpecificCulture("da-DK"),
                    "{0:00.00}", value))
  ' Displays 01,20

  value = .086
  Console.WriteLine(value.ToString("#0.##%", CultureInfo.InvariantCulture)) 
  Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                  "{0:#0.##%}", value)) 
  ' Displays 8.6%

  value = 86000
  Console.WriteLine(value.ToString("0.###E+0", CultureInfo.InvariantCulture))
  Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                    "{0:0.###E+0}", value))
' Displays 8.6E+4
```

## <a name="the-custom-specifier"></a>"," カスタム指定子

"," 文字は、桁区切り記号および数値位取り指定子の両方として機能します。 

* 桁区切り記号: 数値の整数部の桁を書式設定する 2 つの桁プレースホルダー (0 または #) の間に 1 つ以上のコンマが指定されている場合は、出力の整数部分で各数値グループの間に桁区切り記号文字が挿入されます。 

  現在の [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) オブジェクトの [NumberGroupSeparator](xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator) プロパティと [NumberGroupSizes](xref:System.Globalization.NumberFormatInfo.NumberGroupSizes) プロパティによって、桁区切り記号として使用される文字および各数値グループのサイズが決まります。 たとえば、文字列 "#,#" およびインバリアント カルチャを使用して数値 1000 が書式設定される場合は、出力が "1,000" となります。
  
* 数値位取り指定子: 明示的または暗黙的な小数点のすぐ左側に 1 つ以上のコンマが指定されている場合は、コンマごとに書式設定対象の数値が 1000 で除算されます。 たとえば、"0,," 文字列を使用して数値 1 億が書式設定された場合、出力は "100" となります。 

桁区切り記号および数値位取り指定子は、同じ書式指定文字列で使用できます。 たとえば、"#,0,," 文字列およびインバリアント カルチャを使用して 10 億の数値を書式設定した場合、出力は "1,000" となります。 

桁区切り記号としてコンマを使用する例を次に示します。

```csharp
double value = 1234567890;
Console.WriteLine(value.ToString("#,#", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#,#}", value));
// Displays 1,234,567,890      

Console.WriteLine(value.ToString("#,##0,,", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#,##0,,}", value));
// Displays 1,235
```

```vb
Dim value As Double = 1234567890
Console.WriteLine(value.ToString("#,#", CultureInfo.InvariantCulture))
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#,#}", value))
' Displays 1,234,567,890      

Console.WriteLine(value.ToString("#,##0,,", CultureInfo.InvariantCulture))
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#,##0,,}", value))
' Displays 1,235
```

数値の位取り指定子としてコンマを使用する例を次に示します。

```csharp
double value = 1234567890;
Console.WriteLine(value.ToString("#,,", CultureInfo.InvariantCulture)); 
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#,,}", value)); 
// Displays 1235   

Console.WriteLine(value.ToString("#,,,", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#,,,}", value));
// Displays 1  

Console.WriteLine(value.ToString("#,##0,,", CultureInfo.InvariantCulture));       
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#,##0,,}", value));       
// Displays 1,235
```  

```vb
Dim value As Double = 1234567890
  Console.WriteLine(value.ToString("#,,", CultureInfo.InvariantCulture))    
  Console.WriteLine(String.Format(CultureInfo.InvariantCulture, "{0:#,,}", value))  
  ' Displays 1235   

  Console.WriteLine(value.ToString("#,,,", CultureInfo.InvariantCulture))
  Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                  "{0:#,,,}", value))
' Displays 1  

  Console.WriteLine(value.ToString("#,##0,,", CultureInfo.InvariantCulture))       
  Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                  "{0:#,##0,,}", value))       
' Displays 1,235
```

## <a name="the-custom-specifier"></a>"%" カスタム指定子

書式指定文字列にパーセント記号 (%) があると、書式設定前に数値に 100 が乗算されます。 数値では、書式指定文字列の % に対応する位置にローカライズされたパーセント記号が挿入されます。 使用されるパーセント記号は、現在の [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) オブジェクトの [PercentSymbol](xref:System.Globalization.NumberFormatInfo.PercentSymbol) プロパティによって定義されます。

次の例では、"%" カスタム指定子を含むさまざまなカスタム書式指定文字列を定義します。

```csharp
double value = .086;
Console.WriteLine(value.ToString("#0.##%", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#0.##%}", value));
// Displays 8.6%     
```

```vb
Dim value As Double = .086
Console.WriteLine(value.ToString("#0.##%", CultureInfo.InvariantCulture))
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#0.##%}", value))
' Displays 8.6% 
```

## <a name="the-custom-specifier"></a>"‰" カスタム指定子

書式指定文字列にパーミル文字 (‰ または \u2030) があると、書式設定前に数値に 1000 が乗算されます。 返される文字列では、書式指定文字列の ‰ に対応する位置に適切なパーミル記号が挿入されます。 使用されるパーミル文字は、カルチャ固有の書式設定情報を指定するオブジェクトの [NumberFormatInfo.PerMilleSymbol](xref:System.Globalization.NumberFormatInfo.PerMilleSymbol) プロパティによって定義されます。

次の例では、"‰" カスタム指定子を含むカスタム書式指定文字列を定義します。

```csharp
double value = .00354;
string perMilleFmt = "#0.## " + '\u2030';
Console.WriteLine(value.ToString(perMilleFmt, CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:" + perMilleFmt + "}", value));
// Displays 3.54‰   
```

```vb
Dim value As Double = .00354
Dim perMilleFmt As String = "#0.## " & ChrW(&h2030)
Console.WriteLine(value.ToString(perMilleFmt, CultureInfo.InvariantCulture))
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:" + perMilleFmt + "}", value))
' Displays 3.54 ‰
```

## <a name="the-e-and-e-custom-specifiers"></a>"E" カスタム指定子と "e" カスタム指定子

書式指定文字列に "E"、"E+"、"E-"、"e"、"e+"、または "e-" が含まれており、これらの文字の直後にゼロが 1 つ以上続く場合には、指数表記を使用して数値の書式が設定されます。また、数値と指数の間に "E" または "e" が挿入されます。 指数表記インジケーターの後に続くゼロの数によって、出力の指数部の最小桁数が決まります。 書式 "E+" または "e+" は、正符号または負符号が指数部の前に常に挿入されることを示します。 書式 "E"、"E-"、"e"、または "e-" は、指数部が負の値の場合にだけその前に符号文字が挿入されることを示します。

次の例では、指数表記の指定子を使用して、さまざまな数値の書式を設定します。

```csharp
double value = 86000;
Console.WriteLine(value.ToString("0.###E+0", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0.###E+0}", value));
// Displays 8.6E+4

Console.WriteLine(value.ToString("0.###E+000", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0.###E+000}", value));
// Displays 8.6E+004

Console.WriteLine(value.ToString("0.###E-000", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0.###E-000}", value));
// Displays 8.6E004
```

```vb
Dim value As Double = 86000
Console.WriteLine(value.ToString("0.###E+0", CultureInfo.InvariantCulture))
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0.###E+0}", value))
' Displays 8.6E+4

Console.WriteLine(value.ToString("0.###E+000", CultureInfo.InvariantCulture))
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0.###E+000}", value))
' Displays 8.6E+004

Console.WriteLine(value.ToString("0.###E-000", CultureInfo.InvariantCulture))
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0.###E-000}", value))
' Displays 8.6E004
```

## <a name="the-escape-character"></a>"\"" エスケープ文字

書式指定文字列内の "#"、"0"、"."、","、"%"、"‰" の各記号は、リテラル文字ではなく書式指定子として解釈されます。 カスタム書式指定文字列内での位置によっては、大文字および小文字の "E"、および + 記号と - 記号も書式指定子として解釈されます。 

文字が書式指定子として解釈されないようにするには、その文字の前に、エスケープ文字の円記号を付けます。 エスケープ文字は、その後に続く文字が、そのまま結果の文字列に含める必要がある文字リテラルであることを示します。

結果の文字列に円記号を含める場合は、円記号をもう 1 つ付加して、円記号自体をエスケープする必要があります (\\)。 

> [!NOTE]
> C# コンパイラなど、一部のコンパイラでは、同様に、1 つの円記号がエスケープ文字として解釈されることがあります。 書式設定時に文字列が正しく解釈されるようにするには、C# では、逐語的文字列リテラル文字 (@ 文字) を文字列の前に使用します。また、各円記号の前にもう 1 つ円記号を付ける方法もあります。 両方の方法を次の C# の例に示します。

次の例では、エスケープ文字を使用して、書式設定操作で "#"、"0"、"\"" の各文字がエスケープ文字としても書式指定子としても解釈されないようにします。 この例では、円記号をもう 1 つ付けて、円記号がリテラル文字として解釈されるようにしています。

```csharp
int value = 123;
Console.WriteLine(value.ToString("\\#\\#\\# ##0 dollars and \\0\\0 cents \\#\\#\\#"));
Console.WriteLine(String.Format("{0:\\#\\#\\# ##0 dollars and \\0\\0 cents \\#\\#\\#}",
                                value));
// Displays ### 123 dollars and 00 cents ###

Console.WriteLine(value.ToString(xref:"\#\#\# ##0 dollars and \0\0 cents \#\#\#"));
Console.WriteLine(String.Format(xref:"{0:\#\#\# ##0 dollars and \0\0 cents \#\#\#}",
                                value));
// Displays ### 123 dollars and 00 cents ###

Console.WriteLine(value.ToString("\\\\\\\\\\\\ ##0 dollars and \\0\\0 cents \\\\\\\\\\\\"));
Console.WriteLine(String.Format("{0:\\\\\\\\\\\\ ##0 dollars and \\0\\0 cents \\\\\\\\\\\\}",
                                value));
// Displays \\\ 123 dollars and 00 cents \\\

Console.WriteLine(value.ToString(xref:"\\\\\\ ##0 dollars and \0\0 cents \\\\\\"));
Console.WriteLine(String.Format(xref:"{0:\\\\\\ ##0 dollars and \0\0 cents \\\\\\}",
                                value));
// Displays \\\ 123 dollars and 00 cents \\\
```

```vb
Dim value As Integer = 123
Console.WriteLine(value.ToString("\#\#\# ##0 dollars and \0\0 cents \#\#\#"))
Console.WriteLine(String.Format("{0:\#\#\# ##0 dollars and \0\0 cents \#\#\#}", 
                                value))
' Displays ### 123 dollars and 00 cents ###

Console.WriteLine(value.ToString("\\\\\\ ##0 dollars and \0\0 cents \\\\\\"))
Console.WriteLine(String.Format("{0:\\\\\\ ##0 dollars and \0\0 cents \\\\\\}", 
                                value))
' Displays \\\ 123 dollars and 00 cents \\\
```

## <a name="the-section-separator"></a>";" セクション区切り記号

セミコロン (;) は、値が正、負、ゼロのいずれであるかに応じて異なる書式設定を数値に適用する条件付き書式指定子です。 このように数値の内容によって適用する書式を変更するには、カスタム書式指定文字列に、セミコロンで区切ったセクションを最大 3 つまで作成します。 これらのセクションの説明を次に示します。 

セクションの数 | 説明
------------------ | -----------
1 つ | 書式指定文字列はすべての値に適用されます。
2 つ | 最初のセクションが正の値とゼロに適用され、2 番目のセクションが負の値に適用されます。 書式設定対象の数値が負の数値であるが、2 番目のセクションの書式指定に従って丸めた結果ゼロになる場合には、1 番目のセクションの書式に従ってこのゼロが書式設定されます。
3 つ | 最初のセクションが正の値、2 番目のセクションが負の値、3 番目のセクションがゼロに適用されます。 ゼロ以外の値すべてに 1 番目のセクションが適用される場合には、2 番目のセクションが空になる (セミコロンの間に何も表示されない) ことがあります。 書式設定対象の数値がゼロ以外の負の数値であるが、1 番目または 2 番目のセクションの書式に従って丸めた結果ゼロになる場合には、3 番目のセクションの書式に従ってこのゼロが書式設定されます。

セクション区切り記号は、最後の値が書式設定されるときに、数値に関連付けられた既存の書式設定をすべて無視します。 たとえば、セクション区切り記号を使用する場合、負の値はマイナス記号を付けずに表示されます。 最終的に書式設定された値にマイナス記号を付ける場合は、カスタム書式指定子の中に明示的にマイナス記号を含める必要があります。 

次の例では、";" 書式指定子を使用して、正数、負数、ゼロの各部分に対し、それぞれ異なる書式を設定します。

```csharp
double posValue = 1234;
double negValue = -1234;
double zeroValue = 0;

string fmt2 = "##;(##)";
string fmt3 = "##;(##);**Zero**";

Console.WriteLine(posValue.ToString(fmt2));  
Console.WriteLine(String.Format("{0:" + fmt2 + "}", posValue));    
// Displays 1234

Console.WriteLine(negValue.ToString(fmt2));  
Console.WriteLine(String.Format("{0:" + fmt2 + "}", negValue));    
// Displays (1234)

Console.WriteLine(zeroValue.ToString(fmt3)); 
Console.WriteLine(String.Format("{0:" + fmt3 + "}", zeroValue));
// Displays **Zero**
```

```vb
Dim posValue As Double = 1234
Dim negValue As Double = -1234
Dim zeroValue As Double = 0

Dim fmt2 As String = "##;(##)"
Dim fmt3 As String = "##;(##);**Zero**"

Console.WriteLine(posValue.ToString(fmt2))   
Console.WriteLine(String.Format("{0:" + fmt2 + "}", posValue))    
' Displays 1234

Console.WriteLine(negValue.ToString(fmt2))   
Console.WriteLine(String.Format("{0:" + fmt2 + "}", negValue))    
' Displays (1234)

Console.WriteLine(zeroValue.ToString(fmt3))  
Console.WriteLine(String.Format("{0:" + fmt3 + "}", zeroValue))
' Displays **Zero**
```

## <a name="notes"></a>ノート

### <a name="floatingpoint-infinities-and-nan"></a>浮動小数点の無限大値と NaN (非数) 値

[Single](xref:System.Single) の浮動小数点型または [Double](xref:System.Double) の浮動小数点型が正の無限大、負の無限大、または NaN (非数) である場合は、書式指定文字列とは関係なく、現在適用可能な [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) オブジェクトによって指定される [PositiveInfinitySymbol](xref:System.Globalization.NumberFormatInfo.PositiveInfinitySymbol)、[NegativeInfinitySymbol](xref:System.Globalization.NumberFormatInfo.NegativeInfinitySymbol)、または [NaNSymbol](xref:System.Globalization.NumberFormatInfo.NaNSymbol) の各プロパティの値は、書式設定された文字列となります。 

### <a name="rounding-and-fixedpoint-format-strings"></a>丸めと固定小数点の書式指定文字列

固定小数点の書式指定文字列 (つまり指数表記の書式指定文字を含まない書式指定文字列) の場合は、小数点以下の桁数が小数点の右側にある桁プレースホルダーの数と同じである数値に丸められます。 書式指定文字列に小数点が含まれていない場合には、最も近い整数に丸められます。 数値の桁数が、整数部の桁プレースホルダーの数よりも大きい場合には、桁プレースホルダーに収まらない桁が、結果の文字列の 1 番目の桁プレースホルダーの直前にコピーされます。

## <a name="example"></a>例

2 つのカスタム数値書式指定文字列の例を次に示します。 どちらの場合も、桁プレースホルダー (#) によって数値データが表示され、それ以外の文字はすべて結果の文字列にコピーされます。

```csharp
double number1 = 1234567890;
string value1 = number1.ToString("(###) ###-####");
Console.WriteLine(value1);

int number2 = 42;
string value2 = number2.ToString("My Number = #");
Console.WriteLine(value2);
// The example displays the following output:
//       (123) 456-7890
//       My Number = 42
```

```vb
Dim number1 As Double = 1234567890
Dim value1 As String = number1.ToString("(###) ###-####")
Console.WriteLine(value1)

Dim number2 As Integer = 42
Dim value2 As String = number2.ToString("My Number = #")
Console.WriteLine(value2)
' The example displays the following output:
'       (123) 456-7890
'       My Number = 42
```

## <a name="see-also"></a>関連項目

[System.Globalization.NumberFormatInfo](xref:System.Globalization.NumberFormatInfo)

[型の書式設定](formatting-types.md)

[標準の数値書式指定文字列](standard-numeric.md)

[方法: 先行するゼロを数値に埋め込む](pad-number.md)

[複合書式指定](composite-format.md)




<!--HONumber=Nov16_HO1-->


