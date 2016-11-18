---
title: ".NET での日付と時刻文字列の解析"
description: ".NET での日付と時刻文字列の解析"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/29/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: e61514cd-5329-4eb8-b122-482fffb54ab7
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 8b0c5a64db50163d196017ebb410e454eb5a6af9

---

# <a name="parsing-date-and-time-strings-in-net"></a>.NET での日付と時刻文字列の解析

解析メソッドは、日付と時刻の文字列形式を等価の [DateTime](xref:System.DateTime) オブジェクトに変換します。 [Parse](xref:System.DateTime.Parse(System.String)) と [TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) メソッドでは、日付と時刻のいくつかの共通表現のいずれかを変換します。 [ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)) と [TryParseExact](xref:System.DateTime.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTime@)) メソッドでは、日付と時刻の書式指定文字列で指定されたパターンに適合する文字列形式を変換します。 ([標準の日付と時刻の書式指定文字列](standard-datetime.md)と[カスタムの日付と時刻の書式指定文字列](custom-datetime.md)に関するトピックをご覧ください)。 

解析は、日付と時刻の区切り記号、および月、日、および年号の名前に使用される文字列などの情報を提供する書式プロバイダーのプロパティの影響を受けます。 書式プロバイダーは、現在の [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) オブジェクトです。このオブジェクトは、現在のスレッド カルチャによって暗黙的に指定されるか、または解析するメソッドの [IFormatProvider](xref:System.IFormatProvider) パラメーターによって明示的に指定されます。 [IFormatProvider](xref:System.IFormatProvider) パラメーターには、カルチャ ([DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) オブジェクト) を表す [CultureInfo](xref:System.Globalization.CultureInfo) オブジェクトを指定します。 

解析される日付の文字列形式には、月と、少なくとも日付または年を含める必要があります。 時刻の文字列形式は、時間と、少なくとも分または AM/PM 指定子を含める必要があります。 ただし、可能な場合は、解析により省略されたコンポーネントに既定値が指定されます。 欠落している日付には現在の日付が規定で設定され、欠落している年には現在の年が規定で設定され、欠落している月の日付には月の最初の日が規定で設定され、欠落している時刻には午前 0 時が規定で設定されます。 

文字列形式で時刻のみを指定する場合、解析は、[Today](xref:System.DateTime.Today) プロパティの対応する値に、その [Year](xref:System.DateTime.Year)、[Month](xref:System.DateTime.Month)、および [Day](xref:System.DateTime.Day) プロパティを設定した [DateTime](xref:System.DateTime) オブジェクトを返します。 ただし、[DateTimeStyles.NoCurrentDateDefault](xref:System.Globalization.DateTimeStyles.NoCurrentDateDefault) 定数が解析メソッドで指定されている場合、結果の年、月、日付のプロパティの値は 1 に設定されます。

日付と時刻のコンポーネントだけでなく、日付と時刻の文字列形式には、世界協定時刻 (UTC) と何時間異なるかを示すオフセットを含めることができます。 たとえば、文字列 "2/14/2007 5:32:00 -7:00" は、UTC より 7 時間早い時刻を定義します。 オフセットが時刻の文字列形式から省略される場合、解析では、その [Kind](xref:System.DateTime.Kind) プロパティに [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified) を設定して、[DateTime](xref:System.DateTime) オブジェクトを返します。 オフセットが指定されている場合、解析では、その [Kind](xref:System.DateTime.Kind) プロパティに [Local](xref:System.DateTimeKind.Local) を設定した [DateTime](xref:System.DateTime) オブジェクトと、使用しているマシンのローカル タイム ゾーンに調整された値を返します。 解析メソッドで [DateTimeStyles](xref:System.Globalization.DateTimeStyles) 定数を使用して、この動作を変更できます。

書式プロバイダーは、あいまいな数値の日付を解釈するためにも使用されます。 たとえば、文字列 "02/03/04" で示された日付は、どのコンポーネントが月、日、年であるのかが明確ではありません。 この場合、コンポーネントは、書式プロバイダーの日付形式と同様の順序で解釈されます。 

## <a name="parse"></a>Parse

次のコード例では、文字列を `DateTime` に変換するために、`Parse` メソッドを使用する方法を示します。 この例では、現在のスレッドに関連付けられているカルチャを使用して、解析が実行されます。 現在のカルチャに関連付けられている [CultureInfo](xref:System.Globalization.CultureInfo) で入力文字列を解析できない場合は、[FormatException](xref:System.FormatException) がスローされます。

```csharp
string MyString = "Jan 1, 2009";
DateTime MyDateTime = DateTime.Parse(MyString);
Console.WriteLine(MyDateTime);
// Displays the following output on a system whose culture is en-US:
//       1/1/2009 12:00:00 AM
```

```vb
Dim MyString As String = "Jan 1, 2009"
Dim MyDateTime As DateTime = DateTime.Parse(MyString)
Console.WriteLine(MyDateTime)
' Displays the following output on a system whose culture is en-US:
'       1/1/2009 12:00:00 AM
```

また、そのオブジェクトで定義されているカルチャのいずれかに設定される `CultureInfo` を指定するか、または [CultureInfo.DateTimeFormat](xref:System.Globalization.CultureInfo.DateTimeFormat) プロパティによって返される標準の [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) オブジェクトのいずれかを指定することもできます。 次のコード例は、書式プロバイダーを使用して、ドイツ語の文字列を `DateTime` に解析します。 この特定の文字列を正常に解析できるように、de-DE カルチャを示す `CultureInfo` が定義され、解析されている文字列と共に渡されます。 これによって、`CurrentThread` の `CurrentCulture` がどのように設定されていても除外されます。

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      CultureInfo MyCultureInfo = new CultureInfo("de-DE");
      string MyString = "12 Juni 2008";
      DateTime MyDateTime = DateTime.Parse(MyString, MyCultureInfo);
      Console.WriteLine(MyDateTime);
   }
}
// The example displays the following output:
//       6/12/2008 12:00:00 AM
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim MyCultureInfo As CultureInfo = new CultureInfo("de-DE")
      Dim MyString As String = "12 Juni 2008"
      Dim MyDateTime As DateTime = DateTime.Parse(MyString, MyCultureInfo)
      Console.WriteLine(MyDateTime)
   End Sub
End Module
' The example displays the following output:
'       6/12/2008 12:00:00 AM
```

ただし、[Parse](xref:System.DateTime.Parse(System.String)) メソッドのオーバーロードを使用して、カスタム書式プロバイダーを指定することができますが、このメソッドでは非標準の書式プロバイダーの使用をサポートしていません。 非標準の書式設定で示された日付と時刻を解析するには、代わりに [ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)) メソッドを使用します。

次のコード例では、[DateTimeStyles](xref:System.Globalization.DateTimeStyles) 列挙体を使用して、現在の日付と時刻の情報を、文字列で定義しないフィールドの `DateTime` に追加しないことを指定します。

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      CultureInfo MyCultureInfo = new CultureInfo("de-DE");
      string MyString = "12 Juni 2008";
      DateTime MyDateTime = DateTime.Parse(MyString, MyCultureInfo, 
                                           DateTimeStyles.NoCurrentDateDefault);
      Console.WriteLine(MyDateTime);
   }
}
// The example displays the following output if the current culture is en-US:
//      6/12/2008 12:00:00 AM
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim MyCultureInfo As CultureInfo = new CultureInfo("de-DE")
      Dim MyString As String = "12 Juni 2008"
      Dim MyDateTime As DateTime = DateTime.Parse(MyString, MyCultureInfo)
      Console.WriteLine(MyDateTime)
   End Sub
End Module
' The example displays the following output:
'       6/12/2008 12:00:00 AM
```

## <a name="parseexact"></a>ParseExact

[DateTime.ParseExact]((xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)) メソッドは、指定された文字列パターンに適合する文字列を `DateTime` オブジェクトに変換します。 指定された形式ではない文字列がこのメソッドに渡された場合、[FormatException](xref:System.FormatException) がスローされます。 標準の日付と時刻の書式指定子のいずれか、またはカスタムの日付と時刻の書式指定子の制限された組み合わせを指定することができます。 カスタムの書式指定子を使用すると、カスタムの認識文字列を構成することができます。 (指定子の詳細については、[標準の日付と時刻の書式指定文字列](standard-datetime.md)と[カスタムの日付と時刻の書式指定文字列](custom-datetime.md)に関するトピックをご覧ください)。 

[ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)) メソッドのオーバーロードごとに、通常は文字列の書式設定に関するカルチャ固有の情報を指定する [IFormatProvider](xref:System.IFormatProvider) パラメーターもあります。 通常、この [IFormatProvider](xref:System.IFormatProvider) オブジェクトは、標準カルチャを表す [CultureInfo](xref:System.Globalization.CultureInfo) オブジェクト、または [CultureInfo.DateTimeFormat](xref:System.Globalization.CultureInfo.DateTimeFormat) プロパティによって返される [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) オブジェクトです。 ただし、その他の日付と時刻の解析関数とは異なり、このメソッドでは、非標準の日付と時刻の書式を定義する [IFormatProvider](xref:System.IFormatProvider) もサポートしています。 

次のコード例では、`ParseExact` メソッドに解析する文字列オブジェクト、書式指定子、`CultureInfo` オブジェクトが順に渡されます。 この `ParseExact` メソッドでは、en-US カルチャで長い形式の日付パターンを示す文字列のみを解析できます。

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      CultureInfo MyCultureInfo = new CultureInfo("en-US");
      string[] MyString = {" Friday, April 10, 2009", "Friday, April 10, 2009"};
      foreach (string dateString in MyString)
      {
         try {
            DateTime MyDateTime = DateTime.ParseExact(dateString, "D", MyCultureInfo);
            Console.WriteLine(MyDateTime);
         }
         catch (FormatException) {
            Console.WriteLine("Unable to parse '{0}'", dateString);
         }
      }
   }
}
// The example displays the following output:
//       Unable to parse ' Friday, April 10, 2009'
//       4/10/2009 12:00:00 AM
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim MyCultureInfo As CultureInfo = new CultureInfo("en-US")
      Dim MyString() As String = {" Friday, April 10, 2009", "Friday, April 10, 2009"}
      For Each dateString As String In MyString
         Try
            Dim MyDateTime As DateTime = DateTime.ParseExact(dateString, "D", _
                                                             MyCultureInfo)
            Console.WriteLine(MyDateTime)
         Catch e As FormatException
            Console.WriteLine("Unable to parse '{0}'", dateString)
         End Try
      Next
   End Sub
End Module
' The example displays the following output:
'       Unable to parse ' Friday, April 10, 2009'
'       4/10/2009 12:00:00 AM
```

## <a name="see-also"></a>関連項目

[.NET での文字列の解析](parsing-strings.md)

[.NET での型の書式設定](formatting-types.md)

[.NET での型変換](type-conversion.md)




<!--HONumber=Nov16_HO3-->


