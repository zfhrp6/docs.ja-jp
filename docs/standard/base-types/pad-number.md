---
title: "方法: 数値に先行するゼロを埋め込む"
description: "数値に先行するゼロを埋め込む方法"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: a517c066-b11e-4815-826b-9262611eac40
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 0a136d88dfbc83d40ff8a204f275537c24f9748b

---

# <a name="how-to-pad-a-number-with-leading-zeros"></a>方法: 数値に先行するゼロを埋め込む

整数値に先行ゼロを追加するには、精度指定子と[標準の数値書式指定文字列](standard-numeric.md) "D" を使用します。 整数値と浮動小数点数値の両方に先行ゼロを追加するには、[カスタム数値書式指定文字列](custom-numeric.md)を使用します。 このトピックでは、この両方の方法で数値に先行ゼロを埋め込む方法を説明します。

## <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a>特定の長さになるまで整数値に先行ゼロを埋め込むには

1. 整数値を表示する際の最小桁数を決定します。 この数には先行桁数も含みます。

2. 整数値を 10 進数値と 16 進数値のどちらで表示するかを決定します。

    * 整数値を 10 進数値として表示するには、`ToString(String)` メソッドを呼び出し、format パラメーターの値として文字列 "D*n*" を渡します。この *n* は、文字列の最小長を表します。
    
    * 整数値を 16 進数値として表示するには、`ToString(String)` メソッドを呼び出し、format パラメーターの値として文字列 "X*n*" を渡します。この *n* は、文字列の最小長を表します。
    
  また、[Console.WriteLine](xref:System.Console.WriteLine) や [String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) など、[複合書式指定](composite-format.md)を使用するメソッドでもこの書式指定文字列を使用できます。  
  
次の例は、書式指定された数値全体の長さが 8 文字以上になるように、先行ゼロを使用してさまざまな数値を書式指定します。

```csharp
byte byteValue = 254;
short shortValue = 10342;
int intValue = 1023983;
long lngValue = 6985321;               
ulong ulngValue = UInt64.MaxValue;

// Display integer values by calling the ToString method.
Console.WriteLine("{0,22} {1,22}", byteValue.ToString("D8"), byteValue.ToString("X8"));
Console.WriteLine("{0,22} {1,22}", shortValue.ToString("D8"), shortValue.ToString("X8"));
Console.WriteLine("{0,22} {1,22}", intValue.ToString("D8"), intValue.ToString("X8"));
Console.WriteLine("{0,22} {1,22}", lngValue.ToString("D8"), lngValue.ToString("X8"));
Console.WriteLine("{0,22} {1,22}", ulngValue.ToString("D8"), ulngValue.ToString("X8"));
Console.WriteLine();

// Display the same integer values by using composite formatting.
Console.WriteLine("{0,22:D8} {0,22:X8}", byteValue);
Console.WriteLine("{0,22:D8} {0,22:X8}", shortValue);
Console.WriteLine("{0,22:D8} {0,22:X8}", intValue);
Console.WriteLine("{0,22:D8} {0,22:X8}", lngValue);
Console.WriteLine("{0,22:D8} {0,22:X8}", ulngValue);
// The example displays the following output:
//                     00000254               000000FE
//                     00010342               00002866
//                     01023983               000F9FEF
//                     06985321               006A9669
//         18446744073709551615       FFFFFFFFFFFFFFFF
//       
//                     00000254               000000FE
//                     00010342               00002866
//                     01023983               000F9FEF
//                     06985321               006A9669
//         18446744073709551615       FFFFFFFFFFFFFFFF
//         18446744073709551615       FFFFFFFFFFFFFFFF
```

```vb
Dim byteValue As Byte = 254
Dim shortValue As Short = 10342
Dim intValue As Integer = 1023983
Dim lngValue As Long = 6985321               
Dim ulngValue As ULong = UInt64.MaxValue

' Display integer values by calling the ToString method.
Console.WriteLine("{0,22} {1,22}", byteValue.ToString("D8"), byteValue.ToString("X8"))
Console.WriteLine("{0,22} {1,22}", shortValue.ToString("D8"), shortValue.ToString("X8"))
Console.WriteLine("{0,22} {1,22}", intValue.ToString("D8"), intValue.ToString("X8"))
Console.WriteLine("{0,22} {1,22}", lngValue.ToString("D8"), lngValue.ToString("X8"))
Console.WriteLine("{0,22} {1,22}", ulngValue.ToString("D8"), ulngValue.ToString("X8"))
Console.WriteLine()

' Display the same integer values by using composite formatting.
Console.WriteLine("{0,22:D8} {0,22:X8}", byteValue)
Console.WriteLine("{0,22:D8} {0,22:X8}", shortValue)
Console.WriteLine("{0,22:D8} {0,22:X8}", intValue)
Console.WriteLine("{0,22:D8} {0,22:X8}", lngValue)
Console.WriteLine("{0,22:D8} {0,22:X8}", ulngValue)
' The example displays the following output:
'                     00000254               000000FE
'                     00010342               00002866
'                     01023983               000F9FEF
'                     06985321               006A9669
'         18446744073709551615       FFFFFFFFFFFFFFFF
'       
'                     00000254               000000FE
'                     00010342               00002866
'                     01023983               000F9FEF
'                     06985321               006A9669
'         18446744073709551615       FFFFFFFFFFFFFFFF
```

## <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a>特定の数の先行ゼロを整数値に埋め込むには

1. 整数値に表示する先行ゼロの数を決定します。

2. 整数値を 10 進数値と 16 進数値のどちらで表示するかを決定します。 10 進数値として書式指定する場合には標準書式指定子 "D" を使用する必要があります。16 進数値として書式指定する場合には標準書式指定子 "X" を使用する必要があります。

3. 整数値の `ToString("D").Length` メソッドまたは `ToString("X").Length` メソッドを使用して、先行ゼロが埋め込まれていない数値文字列の長さを決定します。 

4. 書式指定した文字列に埋め込む先行ゼロの数を、埋め込まれていない数値の文字列の長さに加算します。 これにより、埋め込み文字列全体の長さが定義されます。

5. 整数値の `ToString(String)` メソッドを呼び出し、10 進数値文字列の場合は "D*n*"、16 進数値の場合は "X*n*" を渡します。*n* は埋め込み文字列全体の長さを表します。 書式指定文字列 "D*n*" または "X*n*"は、複合書式指定をサポートするメソッドでも使用できます。

次の例は、整数値に 5 つの先行ゼロを埋め込みます。

```csharp
int value = 160934;
int decimalLength = value.ToString("D").Length + 5;
int hexLength = value.ToString("X").Length + 5;
Console.WriteLine(value.ToString("D" + decimalLength.ToString()));
Console.WriteLine(value.ToString("X" + hexLength.ToString()));
// The example displays the following output:
//       00000160934
//       00000274A6
```

```vb
Dim value As Integer = 160934
Dim decimalLength As Integer = value.ToString("D").Length + 5
Dim hexLength As Integer = value.ToString("X").Length + 5
Console.WriteLine(value.ToString("D" + decimalLength.ToString()))
Console.WriteLine(value.ToString("X" + hexLength.ToString()))
' The example displays the following output:
'       00000160934
'       00000274A6 
```

## <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a>特定の長さになるまで数値に先行ゼロを埋め込むには

1. 文字列形式の数値の整数部分の桁数を決定します。 合計桁数には先行ゼロも含みます。

2. ゼロの最小数を表すゼロ プレースホルダー ("0") を使用するカスタム数値書式指定文字列を定義します。

3. 数値の `ToString(String)` メソッドを呼び出し、カスタム書式指定文字列を渡します。 カスタム書式指定文字列は、複合書式指定をサポートしているメソッドでも使用できます。

次の例は、書式指定された数値全体の長さが 8 文字以上の整数になるように、先行ゼロを使用してさまざまな数値を書式指定します。

```csharp
string fmt = "00000000.##";
int intValue = 1053240;
decimal decValue = 103932.52m;
float sngValue = 1549230.10873992f;
double dblValue = 9034521202.93217412;

// Display the numbers using the ToString method.
Console.WriteLine(intValue.ToString(fmt));
Console.WriteLine(decValue.ToString(fmt));           
Console.WriteLine(sngValue.ToString(fmt));
Console.WriteLine(dblValue.ToString(fmt));           
Console.WriteLine();

// Display the numbers using composite formatting.
string formatString = " {0,15:" + fmt + "}";
Console.WriteLine(formatString, intValue);      
Console.WriteLine(formatString, decValue);      
Console.WriteLine(formatString, sngValue);      
Console.WriteLine(formatString, dblValue);      
// The example displays the following output:
//       01053240
//       00103932.52
//       01549230
//       9034521202.93
//       
//               01053240
//            00103932.52
//               01549230
//          9034521202.93  
```

```vb
Dim fmt As String = "00000000.##"
Dim intValue As Integer = 1053240
Dim decValue As Decimal = 103932.52d
Dim sngValue As Single = 1549230.10873992
Dim dblValue As Double = 9034521202.93217412

' Display the numbers using the ToString method.
Console.WriteLine(intValue.ToString(fmt))
Console.WriteLine(decValue.ToString(fmt))            
Console.WriteLine(sngValue.ToString(fmt))
Console.WriteLine(dblValue.ToString(fmt))            
Console.WriteLine()

' Display the numbers using composite formatting.
Dim formatString As String = " {0,15:" + fmt + "}"
Console.WriteLine(formatString, intValue)      
Console.WriteLine(formatString, decValue)      
Console.WriteLine(formatString, sngValue)      
Console.WriteLine(formatString, dblValue)      
' The example displays the following output:
'       01053240
'       00103932.52
'       01549230
'       9034521202.93
'       
'               01053240
'            00103932.52
'               01549230
'          9034521202.93
```

## <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a>特定の数の先行ゼロを数値に埋め込むには

1. 数値に埋め込む先行ゼロの数を決定します。

2. 埋め込みのない数値文字列での整数部の桁数を決定します。 この操作を行うには、次の手順を実行します。

    a.  文字列形式の数値に小数点が含まれるかどうかを決定します。
    
    b.  小数点記号を含める場合は、整数部分の文字数を決定します。       
    
    または
       
    小数点記号を含めない場合は、文字列の長さを決定します。 
       
3. 文字列に表示する各先行ゼロの位置にゼロ プレースホルダー ("0") を使用し、既定の文字列の各桁の位置にゼロ プレースホルダーまたは桁プレースホルダー ("#") を使用するカスタム書式指定文字列を作成します。 

4. 数値の ToString(String) メソッド、または複合書式指定をサポートするメソッドのパラメーターとして、カスタム書式指定文字列を指定します。

次の例は、2 つの [Double](xref:System.Double) 値を 5 つの先行ゼロで埋め込みます。

```csharp
double[] dblValues = { 9034521202.93217412, 9034521202 };
foreach (double dblValue in dblValues)
{
   string decSeparator = System.Globalization.NumberFormatInfo.CurrentInfo.NumberDecimalSeparator;
   string fmt, formatString;

   if (dblValue.ToString().Contains(decSeparator))
   {
      int digits = dblValue.ToString().IndexOf(decSeparator);
      fmt = new String('0', 5) + new String('#', digits) + ".##";
   }
   else
   {
      fmt = new String('0', dblValue.ToString().Length);   
   }
   formatString = "{0,20:" + fmt + "}";

   Console.WriteLine(dblValue.ToString(fmt));
   Console.WriteLine(formatString, dblValue);
}
// The example displays the following output:
//       000009034521202.93
//         000009034521202.93
//       9034521202
//                 9034521202 
```

```vb
Dim dblValues() As Double = { 9034521202.93217412, 9034521202 }
For Each dblValue As Double In dblValues
   Dim decSeparator As String = System.Globalization.NumberFormatInfo.CurrentInfo.NumberDecimalSeparator
   Dim fmt, formatString As String

   If dblValue.ToString.Contains(decSeparator) Then
      Dim digits As Integer = dblValue.ToString().IndexOf(decSeparator)
      fmt = New String("0"c, 5) + New String("#"c, digits) + ".##"
   Else
      fmt = New String("0"c, dblValue.ToString.Length)   
   End If
   formatString = "{0,20:" + fmt + "}"

   Console.WriteLine(dblValue.ToString(fmt))
   Console.WriteLine(formatString, dblValue)
Next
' The example displays the following output:
'       000009034521202.93
'         000009034521202.93
'       9034521202
'                 9034521202
```

## <a name="see-also"></a>関連項目

[標準の数値書式指定文字列](standard-numeric.md)

[カスタム数値書式指定文字列](custom-numeric.md)

[複合書式指定](composite-format.md)




<!--HONumber=Nov16_HO3-->


