---
title: "型の書式設定"
description: "型の書式設定"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: cf497639-9f91-45cb-836f-998d1cea2f43
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 6c6ddfdbe288fe012adf31fd4d45af1b697d1132

---

# <a name="formatting-types"></a>型の書式設定

書式設定とはクラス、構造体、または列挙値のインスタンスを文字列形式に変換するプロセスのことで、多くの場合、変換した文字列をユーザーに表示したり、逆シリアル化して元のデータ型を復元したりするために行います。 この変換には次のような問題がある場合があります。

* 値の内部での格納方法に、ユーザーが望む表示方法が反映されない場合がある。 たとえば、電話番号が **8009999999** という形式で格納されることがあります。これではユーザーにはわかりにくいため、 代わりに **800-999-9999** と表示する必要があります。 数値をこのように書式指定する例については、「[カスタム書式指定文字列](#custom-format-strings)」を参照してください。 

* オブジェクトから文字列形式への変換が直観的に理解しづらい場合がある。 たとえば、**Temperature** オブジェクトや **Person** オブジェクトの文字列形式がどのようになるのか、明確ではありません。 **Temperature** オブジェクトをさまざまな方法で書式指定する例については、「[標準書式指定文字列](#standard-format-strings)」を参照してください。

* 通常、カルチャ依存の書式指定が必要になる。 たとえば、通貨値を数字で表すアプリケーションでは、数値文字列にカルチャ別の通貨記号、桁区切り記号 (ほとんどのカルチャでは 1000 単位)、および小数点を含める必要があります。 例については、「[書式プロバイダーと IFormatProvider インターフェイスによるカルチャに依存した書式指定](#culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface)」を参照してください。 

* アプリケーションによっては、同じ値をさまざまな方法で表示する必要がある。 たとえば、列挙型のメンバーを表すために、その名前の文字列形式を表示する場合や、基になる値を表示する場合が考えられます。 [DayOfWeek](xref:System.DayOfWeek) 列挙体のメンバーをさまざまな方法で書式指定する例については、「[標準書式指定文字列](#standard-format-strings)」を参照してください。

.NET は書式設定機能が充実しているため、開発者はこうした要件を満たすことができます。 

> [!NOTE]
> 書式設定は型の値を文字列形式に変換します。 解析は書式設定の逆の操作で、 文字列形式からデータ型のインスタンスを作成します。 他のデータ型への文字列の変換については、「[文字列の解析](parsing-strings.md)」を参照してください。

この概要は、次のセクションで構成されています。

* [.NET での書式設定](#formatting-in-net)

* [ToString メソッドを使用した既定の書式設定](#default-formatting-using-the-tostring-method)

* [ToString メソッドのオーバーライド](#overriding-the-tostring-method)

* [ToString メソッドと書式指定文字列](#the-tostring-method-and-format-strings)

    * [標準の書式指定文字列](#standard-format-strings)
    
    * [カスタム書式指定文字列](#custom-format-strings)
    
    * [書式指定文字列と .NET 型](#format-strings-and-net-types)
    
* [書式プロバイダーと IFormatProvider インターフェイスによるカルチャに依存した書式指定](#culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface)

    * [数値のカルチャに依存した書式設定](#culture-sensitive-formatting-of-numeric-values)
    
    * [日付と時刻の値のカルチャに依存した書式設定](#culture-sensitive-formatting-of-date-and-time-values)
    
* [IFormattable インターフェイス](#the-iformattable-interface)

* [複合書式指定](#composite-formatting)

* [ICustomFormatter を使用したカスタム書式設定](#custom-formatting-with-icustomformatter)

* [関連トピック](#related-topics)

* [参照](#reference)

## <a name="formatting-in-net"></a>.NET での書式設定

基本的な書式設定の方式は、[Object.ToString](xref:System.Object.ToString) メソッドによって既定として実装されます。このメソッドについては、このトピックの「[ToString メソッドを使用した既定の書式設定](#default-formatting-using-the-tostring-method)」のセクションを参照してください。 ただし、.NET には、この既定の書式設定機能を変更および拡張する方法がいくつかあります。 次に例を示します。

* [Object.ToString](xref:System.Object.ToString) メソッドをオーバーライドして、オブジェクトの値のカスタム文字列形式を定義する方法。 詳細については、このトピックの「[ToString メソッドのオーバーライド](#overriding-the-tostring-method)」のセクションを参照してください。

* オブジェクトの値の文字列形式に複数の形式を持たせる書式指定子を定義する方法。 たとえば、次のステートメントでは "X" 書式指定子を使用して整数を 16 進値の文字列形式に変換します。

  ```csharp
  int integerValue = 60312;
  Console.WriteLine(integerValue.ToString("X"));   // Displays EB98.
  ```

  ```vb
  Dim integerValue As Integer = 60312
  Console.WriteLine(integerValue.ToString("X"))   ' Displays EB98.
  ```
  
  書式指定子の詳細については、「[ToString メソッドと書式指定文字列](#the-tostring-method-and-format-strings)」のセクションを参照してください。
  
* 書式プロバイダーを使用して、特定のカルチャの書式指定規則を利用する方法。 たとえば、次のステートメントでは en-US カルチャの書式指定規則を使用して通貨値を表示します。 

  ```csharp
  double cost = 1632.54; 
  Console.WriteLine(cost.ToString("C", 
                  new System.Globalization.CultureInfo("en-US")));   
  // The example displays the following output:
  //       $1,632.54
  ```

  ```vb
  Dim cost As Double = 1632.54
  Console.WriteLine(cost.ToString("C", New System.Globalization.CultureInfo("en-US")))
  ' The example displays the following output:
  '       $1,632.54
  ```
  
  書式プロバイダーを使用した書式設定の詳細については、「[書式プロバイダーと IFormatProvider インターフェイスによるカルチャに依存した書式指定](#culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface)」のセクションを参照してください。  
  
* [IFormattable](xref:System.IFormattable) インターフェイスを実装して、[Convert](xref:System.Convert) クラスによる文字列変換と複合書式指定の両方をサポートする方法。 詳細については、「[IFormattable インターフェイス](#the-iformattable-interface)」のセクションを参照してください。

* 複合書式指定を使用して、値の文字列形式を大きな文字列に埋め込む方法。 詳細については、「[複合書式指定](#composite-formatting)」のセクションを参照してください。

* [ICustomFormatter](xref:System.ICustomFormatter) および [IFormatProvider](xref:System.IFormatProvider) を実装して、完全なカスタム書式設定ソリューションを提供する方法。 詳細については、「[ICustomFormatter を使用したカスタム書式設定](#custom-formatting-with-icustomformatter)」のセクションを参照してください。

以降のセクションでは、オブジェクトを文字列形式に変換するこれらの方法について説明します。

## <a name="default-formatting-using-the-tostring-method"></a>ToString メソッドを使用した既定の書式設定

[System.Object](xref:System.Object) から派生したすべての型は、既定で型の名前を返す、パラメーターなしの [ToString](xref:System.Object.ToString) メソッドを自動的に継承します。 既定の [ToString](xref:System.Object.ToString) メソッドの例を次に示します。 このコード例では、実装を持たない `Automobile` という名前のクラスを定義します。 このクラスがインスタンス化され、[ToString](xref:System.Object.ToString) メソッドが呼び出されると、その型の名前が表示されます。 サンプルでは、[ToString](xref:System.Object.ToString) メソッドが明示的に呼び出されないことに注意してください。 [Console.WriteLine(Object)](xref:System.Console.WriteLine(System.Object)) メソッドは引数として渡されたオブジェクトの [ToString](xref:System.Object.ToString) メソッドを暗黙的に呼び出します。 

```csharp
using System;

public class Automobile
{
   // No implementation. All members are inherited from Object.
}

public class Example
{
   public static void Main()
   {
      Automobile firstAuto = new Automobile();
      Console.WriteLine(firstAuto);
   }
}
// The example displays the following output:
//       Automobile
```

```vb 
Public Class Automobile
   ' No implementation. All members are inherited from Object.
End Class

Module Example
   Public Sub Main()
      Dim firstAuto As New Automobile()
      Console.WriteLine(firstAuto)
   End Sub
End Module
' The example displays the following output:
'       Automobile
```

インターフェイス以外の型はすべて [Object](xref:System.Object) から派生するため、この機能はカスタムのクラスまたは構造体に自動的に提供されます。 ただし、既定の [ToString](xref:System.Object.ToString) メソッドによって提供される機能には制限があり、型の識別は行いますが、型のインスタンスに関する情報は提供しません。 それ自体に関する情報を提供するオブジェクトの文字列形式を提供するには、[ToString](xref:System.Object.ToString) メソッドをオーバーライドする必要があります。

> [!NOTE]
> 構造体は、[Object](xref:System.Object) から派生した [ValueType](xref:System.ValueType) を継承します。 [ValueType](xref:System.ValueType) は [Object.ToString](xref:System.Object.ToString) をオーバーライドしますが、その実装は同じです。

## <a name="overriding-the-tostring-method"></a>ToString メソッドのオーバーライド

型の名前の表示は用途が限定され、型のコンシューマー側でインスタンスを別のインスタンスと区別することはできません。 ただし、[ToString](xref:System.Object.ToString) メソッドをオーバーライドして、より役に立つオブジェクトの値の形式を作成することができます。 次の例では `Temperature` オブジェクトを定義し、その [ToString](xref:System.Object.ToString) メソッドをオーバーライドして、温度を摂氏で表示します。

```csharp
using System;

public class Temperature
{
   private decimal temp;

   public Temperature(decimal temperature)
   {
      this.temp = temperature;   
   }

   public override string ToString()
   {
      return this.temp.ToString("N1") + "°C";
   }
}

public class Example
{
   public static void Main()
   {
      Temperature currentTemperature = new Temperature(23.6m);
      Console.WriteLine("The current temperature is " +
                        currentTemperature.ToString());
   }
}
// The example displays the following output:
//       The current temperature is 23.6°C.
```

```vb
Public Class Temperature
   Private temp As Decimal

   Public Sub New(temperature As Decimal)
      Me.temp = temperature
   End Sub

   Public Overrides Function ToString() As String
      Return Me.temp.ToString("N1") + "°C"   
   End Function
End Class

Module Example
   Public Sub Main()
      Dim currentTemperature As New Temperature(23.6d)
      Console.WriteLine("The current temperature is " +
                        currentTemperature.ToString())
   End Sub
End Module
' The example displays the following output:
'       The current temperature is 23.6°C.
```

.NET では、各プリミティブ値型の [ToString](xref:System.Object.ToString) メソッドは名前の代わりにオブジェクトの値を表示するようにオーバーライドされています。 各プリミティブ型のオーバーライドを次の表に示します。 オーバーライドされているメソッドのほとんどは [ToString](xref:System.Object.ToString) メソッドの別のオーバーロードを呼び出し、それにその型の一般書式を定義する "G" 書式指定子と、現在のカルチャを表す [IFormatProvider](xref:System.IFormatProvider) オブジェクトを渡します。

型 | ToString のオーバーライド
---- | -----------------
[Boolean](xref:System.Boolean) | [Boolean.TrueString](xref:System.Boolean.TrueString) または [Boolean.FalseString](xref:System.Boolean.FalseString) のいずれかを返します。
[Byte](xref:System.Byte) | `Byte.ToString("G", NumberFormatInfo.CurrentInfo)` を呼び出して、現在のカルチャに合わせて [Byte](xref:System.Byte) 値の書式設定をします。
[Char](xref:System.Char) | 文字を文字列として返します。
[DateTime](xref:System.DateTime) | `DateTime.ToString("G", DatetimeFormatInfo.CurrentInfo)` を呼び出して、現在のカルチャに合わせて日付と時刻の値の書式設定をします。 
[Decimal](xref:System.Decimal) | `Decimal.ToString("G", NumberFormatInfo.CurrentInfo)` を呼び出して、現在のカルチャに合わせて [Decimal](xref:System.Decimal) 値の書式設定をします。
[Double](xref:System.Double) | `Double.ToString("G", NumberFormatInfo.CurrentInfo)` を呼び出して、現在のカルチャに合わせて [Double](xref:System.Double) 値の書式設定をします。
[Int16](xref:System.Int16) | `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` を呼び出して、現在のカルチャに合わせて [Int16](xref:System.Int16) 値の書式設定をします。
[Int32](xref:System.Int32) | `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` を呼び出して、現在のカルチャに合わせて [Int32](xref:System.Int32) 値の書式設定をします。
[Int64](xref:System.Int64) | `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` を呼び出して、現在のカルチャに合わせて [Int64](xref:System.Int64) 値の書式設定をします。
[SByte](xref:System.SByte) | `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` を呼び出して、現在のカルチャに合わせて[SByte](xref:System.SByte) 値の | 書式設定をします。
[Single](xref:System.Single) | `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` を呼び出して、現在のカルチャに合わせて [Single](xref:System.Single) 値の書式設定をします。
[UInt32](xref:System.UInt32) | `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` を呼び出して、現在のカルチャに合わせて [UInt32](xref:System.UInt32) 値の書式設定をします。
[UInt32](xref:System.UInt32) | `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` を呼び出して、現在のカルチャに合わせて [UInt32](xref:System.UInt32) 値の書式設定をします。
[UInt64](xref:System.UInt64) | `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` を呼び出して、現在のカルチャに合わせて [UInt64](xref:System.UInt64) 値の書式設定をします。

## <a name="the-tostring-method-and-format-strings"></a>ToString メソッドと書式指定文字列

既定の [ToString](xref:System.Object.ToString) メソッドや [ToString](xref:System.Object.ToString) のオーバーライドの使用は、オブジェクトの文字列形式が 1 つの場合に適しています。 しかし、多くの場合オブジェクトの値には複数の形式があります。 たとえば、温度は華氏、摂氏、またはケルビンで表現できます。 また、整数値 10 は 10、10.0、1.0e01、$10.00 などの多くの方法で表すことができます。

.NET では、書式指定文字列を使用することで、1 つの値に複数の文字列形式を持たせることができます。 書式指定文字列とは定義済みの書式指定子を 1 つ以上含む文字列です。書式指定子とは、[ToString](xref:System.Object.ToString) メソッドによるその出力の書式設定方法を定義する 1 文字または文字グループです。 書式指定文字列はパラメーターとしてオブジェクトの [ToString](xref:System.Object.ToString) メソッドに渡され、オブジェクトの値の文字列形式の表示方法を決定します。

.NET では、すべての数値型、日付/時刻型、および列挙型で、定義済みの一連の書式指定子をサポートしています。 書式指定文字列を使用して、アプリケーションで定義されたデータ型の文字列形式を複数定義することもできます。

### <a name="standard-format-strings"></a>標準の書式指定文字列

標準書式指定文字列には、適用先のオブジェクトの文字列形式を定義する英字の単一の書式指定子と、結果文字列に表示される桁数に影響するオプションの精度指定子が含まれます。 精度指定子が省略されるかサポートされていない場合、標準書式指定子は標準書式指定文字列と同じになります。 

.NET では、すべての数値型、すべての日付/時刻型、およびすべての列挙型に対して一連の標準書式指定子が定義されています。 たとえば、それらのカテゴリごとに、対応する型の値の一般的な文字列形式を定義する "G" 標準書式指定子がサポートされています。

列挙型の標準書式指定文字列は、値の文字列形式を直接制御します。 列挙値の [ToString](xref:System.Object.ToString) メソッドに渡された書式指定文字列によって、文字列名 ("G" 書式指定子および "F" 書式指定子)、基になる整数値 ("D" 書式指定子)、または 16 進値 ("X" 書式指定子) のどの形式で値を表示するかが決定します。 次のコード例では、標準書式指定文字列を使用して、[DayOfWeek](xref:System.DayOfWeek) 列挙値の書式を設定する方法を示しています。 

```csharp
DayOfWeek thisDay = DayOfWeek.Monday;
string[] formatStrings = {"G", "F", "D", "X"};

foreach (string formatString in formatStrings)
   Console.WriteLine(thisDay.ToString(formatString));
// The example displays the following output:
//       Monday
//       Monday
//       1
//       00000001
```

```vb
Dim thisDay As DayOfWeek = DayOfWeek.Monday
Dim formatStrings() As String = {"G", "F", "D", "X"}

For Each formatString As String In formatStrings
   Console.WriteLine(thisDay.ToString(formatString))
Next
' The example displays the following output:
'       Monday
'       Monday
'       1
'       00000001
```

列挙型書式指定文字列については、「[列挙型書式指定文字列](enumeration-format.md)」を参照してください。

数値型の標準書式指定文字列は、通常、表示される桁数が 1 つ以上のプロパティ値によって制御される結果文字列を定義します。 たとえば、"C" 書式指定子は数字を通貨値として書式設定します。 唯一のパラメーターとして "C" 書式指定子を渡して [ToString](xref:System.Object.ToString) メソッドを呼び出した場合、現在のカルチャの [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) オブジェクトの次のプロパティ値を使用して数値の文字列形式を定義します。

* [CurrencySymbol](xref:System.Globalization.NumberFormatInfo.CurrencySymbol) プロパティ。現在のカルチャの通貨記号を指定します。

* [CurrencyNegativePattern](xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern) プロパティまたは [CurrencyPositivePattern](xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern) プロパティ。次の情報を特定する整数を返します。 

    * 通貨記号の位置。
    
    * 負の値を表すために、先頭の負の符号、末尾の負の符号、またはかっこのどれを使用するか。
    
    * 数値と通貨記号の間にスペース文字を表示するかどうか。
    
* [CurrencyDecimalDigits](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits) プロパティ。結果文字列の小数点以下の桁数を定義します。

* [CurrencyDecimalSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator) プロパティ。結果文字列の小数点の記号を定義します。

* [CurrencyGroupSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator) プロパティ。桁区切り記号を定義します。

* [CurrencyGroupSizes](xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes) プロパティ。整数部の各グループの桁数を定義します。

* [NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign) プロパティ。かっこを使用せずに負の値を表す場合に結果文字列で使用する負の符号を決定します。

さらに、数値書式指定文字列には、精度指定子が含まれる場合があります。 この指定子の意味は一緒に使用される書式指定文字列によって異なりますが、通常は、結果文字列に表示される合計桁数か小数点以下の桁数を示します。 たとえば、次の例では、"X4" の標準数値文字列と精度指定子を使用して、4 桁の 16 進数から成る文字列値を作成します。

```csharp
byte[] byteValues = { 12, 163, 255 };
foreach (byte byteValue in byteValues)
   Console.WriteLine(byteValue.ToString("X4"));
// The example displays the following output:
//       000C
//       00A3
//       00FF
```

```vb
Dim byteValues() As Byte = { 12, 163, 255 }
For Each byteValue As Byte In byteValues
   Console.WriteLine(byteValue.ToString("X4"))
Next
' The example displays the following output:
'       000C
'       00A3
'       00FF
```

標準の数値書式指定文字列の詳細については、「[標準の数値書式指定文字列](standard-numeric.md)」を参照してください。 

日付と時刻の値の標準書式指定文字列は、特定の [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) クラスに格納されているカスタム書式指定文字列のエイリアスです。 たとえば、"D" 書式指定子を渡して日付と時刻の値の [ToString](xref:System.Object.ToString) メソッドを呼び出すと、現在のカルチャの [DateTimeFormatInfo.LongDatePattern](xref:System.Globalization.DateTimeFormatInfo.LongDatePattern) プロパティに格納されているカスタム書式指定文字列を使用して日付と時刻が表示されます (カスタム書式指定文字列の詳細については、「[カスタム書式指定文字列](#custom-format-strings)」のセクションを参照してください)。この関係を次の例に示します。

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      DateTime date1 = new DateTime(2017, 6, 30);
      Console.WriteLine("D Format Specifier:     {0:D}", date1);
      string longPattern = CultureInfo.CurrentCulture.DateTimeFormat.LongDatePattern;
      Console.WriteLine("'{0}' custom format string:     {1}", 
                        longPattern, date1.ToString(longPattern));
   }
}
// The example displays the following output when run on a system whose
// current culture is en-US:
//    D Format Specifier:     Tuesday, June 30, 2017
//    'dddd, MMMM dd, yyyy' custom format string:     Tuesday, June 30, 2017
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim date1 As Date = #6/30/2009#
      Console.WriteLine("D Format Specifier:     {0:D}", date1)
      Dim longPattern As String = CultureInfo.CurrentCulture.DateTimeFormat.LongDatePattern
      Console.WriteLine("'{0}' custom format string:     {1}", _
                        longPattern, date1.ToString(longPattern))
   End Sub
End Module
' The example displays the following output when run on a system whose
' current culture is en-US:
'    D Format Specifier:     Tuesday, June 30, 2009
'    'dddd, MMMM dd, yyyy' custom format string:     Tuesday, June 30, 2009
```

標準の日時書式指定文字列の詳細については、「[標準の日時書式指定文字列](standard-datetime.md)」を参照してください。

また、標準書式指定文字列を使用して、オブジェクトの `ToString(String)` メソッドによって生成された、アプリケーション定義のオブジェクトの文字列形式を定義することもできます。 オブジェクトでサポートする特定の標準書式指定子を定義したり、それらで大文字と小文字を区別するかしないかを決定したりすることができます。 `ToString(String)` メソッドの実装で、以下がサポートされます。

* オブジェクトの一般的な書式または共通の書式を表す "G" 書式指定子。 オブジェクトの `ToString` メソッドのパラメーターなしのオーバーロードで、その `ToString(String)` オーバーロードを呼び出し、それに "G" 標準書式指定文字列を渡します。

* null 参照に相当する書式指定子。 null 参照に相当する書式指定子は "G" 書式指定子と同等に扱う必要があります。

たとえば、`Temperature` クラスの場合、内部的には温度を摂氏で格納し、書式指定子を使用して `Temperature` オブジェクトの値を摂氏、華氏、およびケルビンで表すことができます。 具体的な例を次に示します。

```csharp
using System;

public class Temperature
{
   private decimal m_Temp;

   public Temperature(decimal temperature)
   {
      this.m_Temp = temperature;
   }

   public decimal Celsius
   {
      get { return this.m_Temp; }
   }

   public decimal Kelvin
   {
      get { return this.m_Temp + 273.15m; }   
   }

   public decimal Fahrenheit
   {
      get { return Math.Round(((decimal) (this.m_Temp * 9 / 5 + 32)), 2); }
   }

   public override string ToString()
   {
      return this.ToString("C");
   }

   public string ToString(string format)
   {  
      // Handle null or empty string.
      if (String.IsNullOrEmpty(format)) format = "C";
      // Remove spaces and convert to uppercase.
      format = format.Trim().ToUpperInvariant();      

      // Convert temperature to Fahrenheit and return string.
      switch (format)
      {
         // Convert temperature to Fahrenheit and return string.
         case "F":
            return this.Fahrenheit.ToString("N2") + " °F";
         // Convert temperature to Kelvin and return string.
         case "K":
            return this.Kelvin.ToString("N2") + " K";
         // return temperature in Celsius.
         case "G":
         case "C":
            return this.Celsius.ToString("N2") + " °C";
         default:
            throw new FormatException(String.Format("The '{0}' format string is not supported.", format));
      }      
   }
}

public class Example
{
   public static void Main()
   {
      Temperature temp1 = new Temperature(0m);
      Console.WriteLine(temp1.ToString());
      Console.WriteLine(temp1.ToString("G"));
      Console.WriteLine(temp1.ToString("C"));
      Console.WriteLine(temp1.ToString("F"));
      Console.WriteLine(temp1.ToString("K"));

      Temperature temp2 = new Temperature(-40m);
      Console.WriteLine(temp2.ToString());
      Console.WriteLine(temp2.ToString("G"));
      Console.WriteLine(temp2.ToString("C"));
      Console.WriteLine(temp2.ToString("F"));
      Console.WriteLine(temp2.ToString("K"));

      Temperature temp3 = new Temperature(16m);
      Console.WriteLine(temp3.ToString());
      Console.WriteLine(temp3.ToString("G"));
      Console.WriteLine(temp3.ToString("C"));
      Console.WriteLine(temp3.ToString("F"));
      Console.WriteLine(temp3.ToString("K"));

      Console.WriteLine(String.Format("The temperature is now {0:F}.", temp3));
   }
}
// The example displays the following output:
//       0.00 °C
//       0.00 °C
//       0.00 °C
//       32.00 °F
//       273.15 K
//       -40.00 °C
//       -40.00 °C
//       -40.00 °C
//       -40.00 °F
//       233.15 K
//       16.00 °C
//       16.00 °C
//       16.00 °C
//       60.80 °F
//       289.15 K
//       The temperature is now 16.00 °C.
```

```vb
Public Class Temperature
   Private m_Temp As Decimal

   Public Sub New(temperature As Decimal)
      Me.m_Temp = temperature
   End Sub

   Public ReadOnly Property Celsius() As Decimal
      Get
         Return Me.m_Temp
      End Get   
   End Property

   Public ReadOnly Property Kelvin() As Decimal
      Get
         Return Me.m_Temp + 273.15d   
      End Get
   End Property

   Public ReadOnly Property Fahrenheit() As Decimal
      Get
         Return Math.Round(CDec(Me.m_Temp * 9 / 5 + 32), 2)
      End Get      
   End Property

   Public Overrides Function ToString() As String
      Return Me.ToString("C")
   End Function

   Public Overloads Function ToString(format As String) As String  
      ' Handle null or empty string.
      If String.IsNullOrEmpty(format) Then format = "C"
      ' Remove spaces and convert to uppercase.
      format = format.Trim().ToUpperInvariant()      

      Select Case format
         Case "F"
           ' Convert temperature to Fahrenheit and return string.
            Return Me.Fahrenheit.ToString("N2") & " °F"
         Case "K"
            ' Convert temperature to Kelvin and return string.
            Return Me.Kelvin.ToString("N2") & " K"
         Case "C", "G"
            ' Return temperature in Celsius.
            Return Me.Celsius.ToString("N2") & " °C"
         Case Else
            Throw New FormatException(String.Format("The '{0}' format string is not supported.", format))
      End Select      
   End Function
End Class

Public Module Example
   Public Sub Main()
      Dim temp1 As New Temperature(0d)
      Console.WriteLine(temp1.ToString())
      Console.WriteLine(temp1.ToString("G"))
      Console.WriteLine(temp1.ToString("C"))
      Console.WriteLine(temp1.ToString("F"))
      Console.WriteLine(temp1.ToString("K"))

      Dim temp2 As New Temperature(-40d)
      Console.WriteLine(temp2.ToString())
      Console.WriteLine(temp2.ToString("G"))
      Console.WriteLine(temp2.ToString("C"))
      Console.WriteLine(temp2.ToString("F"))
      Console.WriteLine(temp2.ToString("K"))

      Dim temp3 As New Temperature(16d)
      Console.WriteLine(temp3.ToString())
      Console.WriteLine(temp3.ToString("G"))
      Console.WriteLine(temp3.ToString("C"))
      Console.WriteLine(temp3.ToString("F"))
      Console.WriteLine(temp3.ToString("K"))

      Console.WriteLine(String.Format("The temperature is now {0:F}.", temp3))
   End Sub
End Module
' The example displays the following output:
'       0.00 °C
'       0.00 °C
'       0.00 °C
'       32.00 °F
'       273.15 K
'       -40.00 °C
'       -40.00 °C
'       -40.00 °C
'       -40.00 °F
'       233.15 K
'       16.00 °C
'       16.00 °C
'       16.00 °C
'       60.80 °F
'       289.15 K
'       The temperature is now 16.00 °C.
```

### <a name="custom-format-strings"></a>カスタム書式指定文字列

.NET では、標準書式指定文字列のほかに、数値および日付と時刻の値の両方のカスタム書式指定文字列が定義されています。 カスタム書式指定文字列は、値の文字列形式を定義する 1 つ以上のカスタム書式指定子で構成されます。 たとえば、"yyyy/mm/dd hh:mm:ss.ffff t zzz" というカスタム日時書式指定文字列の場合、en-US カルチャでは日付が "2008/11/15 07:45:00.0000 P -08:00" という文字列形式に変換されます。 また、"0000" というカスタム書式指定文字列の場合、整数値 12 は "0012" に変換されます。 カスタム書式指定文字列の一覧については、「[カスタム日時書式指定文字列](custom-datetime.md)」および「[カスタム数値書式指定文字列](custom-numeric.md)」を参照してください。

書式指定文字列が単一のカスタム書式指定子で構成される場合は、標準書式指定子と混同しないように、書式指定子の前にパーセント (%) 記号を付ける必要があります。 次の例では、"M" カスタム書式指定子を使用して、特定の日付の月を表す 1 桁または 2 桁の数値を表示します。

```csharp
DateTime date1 = new DateTime(2009, 9, 8);
Console.WriteLine(date1.ToString("%M"));       
// Displays 9
```

```vb
Dim date1 As Date = #09/08/2009#
Console.WriteLine(date1.ToString("%M"))      ' Displays 9
```

日付および時刻の値の標準書式指定文字列の多くは、[DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) オブジェクトのプロパティによって定義されているカスタム書式指定文字列のエイリアスです。 また、カスタム書式指定文字列を使用することで、数値または日付と時刻の値に対して、柔軟にアプリケーション定義の書式を指定できます。 複数のカスタム書式指定子を 1 つのカスタム書式指定文字列に結合することによって、数値および日付と時刻の値の両方に対するカスタムの結果文字列を独自に定義することができます。 次の例では、月の名前、日付、および年の後に、かっこで囲んで曜日を表示するカスタム書式指定文字列を定義しています。

```csharp
string customFormat = "MMMM dd, yyyy (dddd)";
DateTime date1 = new DateTime(2009, 8, 28);
Console.WriteLine(date1.ToString(customFormat));   
// The example displays the following output if run on a system
// whose language is English:
//       August 28, 2009 (Friday) 
```

```vb
Dim customFormat As String = "MMMM dd, yyyy (dddd)"
Dim date1 As Date = #8/28/2009#
Console.WriteLine(date1.ToString(customFormat))   
' The example displays the following output if run on a system
' whose language is English:
'       August 28, 2009 (Friday) 
```

次の例では、[Int64](xref:System.Int64) 値を米国で標準的な 7 桁の電話番号を市外局番と共に表示するカスタム書式指定文字列を定義します。 

```csharp
using System;

public class Example
{
   public static void Main()
   {
      long number = 8009999999;
      string fmt = "000-000-0000";
      Console.WriteLine(number.ToString(fmt));
   }
}
// The example displays the following output:
//        800-999-9999
```

```vb
Module Example
   Public Sub Main()
      Dim number As Long = 8009999999
      Dim fmt As String = "000-000-0000"
      Console.WriteLine(number.ToString(fmt))
   End Sub
End Module
' The example displays the following output:

' The example displays the following output:
'       800-999-9999
```

一般には、アプリケーション定義の型に対する書式設定のほとんどのニーズに標準書式指定文字列を使用して対応できますが、カスタム書式指定子を定義して型の書式を設定することもできます。 

### <a name="format-strings-and-net-types"></a>書式指定文字列と .NET 型

すべての数値型 (つまり、[Byte](xref:System.Byte)、[Decimal](xref:System.Decimal)、[Double](xref:System.Double)、[Int16](xref:System.Int16)、[Int32](xref:System.Int32)、[Int64](xref:System.Int64)、[SByte](xref:System.SByte)、[Single](xref:System.Single)、[UInt16](xref:System.UInt16)、[UInt32](xref:System.UInt32)、[UInt64](xref:System.UInt64)、[BigInteger](xref:System.Numerics.BigInteger) 型)、および [DateTime](xref:System.DateTime)、[DateTimeOffset](xref:System.DateTimeOffset)、[TimeSpan](xref:System.TimeSpan)、[Guid](xref:System.Guid) と、すべての列挙型が書式指定文字列による書式設定に対応しています。 各型でサポートされている特定の書式指定文字列については、次のトピックを参照してください。 

タイトル | 定義
----- | ----------
[標準の数値書式指定文字列](standard-numeric.md) | 数値に対して一般的に使用される文字列形式を作成する標準書式指定文字列について説明します。 
[カスタム数値書式指定文字列](custom-numeric.md) | 数値に対するアプリケーション固有の文字列形式を作成するカスタム書式指定文字列について説明します。
[標準の日時書式指定文字列](standard-datetime.md) | [DateTime](xref:System.DateTime) 値に対して一般的に使用される文字列形式を作成する標準書式指定文字列について説明します。
[カスタム日時書式指定文字列](custom-datetime.md) | [DateTime](xref:System.DateTime) 値に対するアプリケーション固有の文字列形式を作成するカスタム書式指定文字列について説明します。
[標準 TimeSpan 書式指定文字列](standard-timespan.md) | 時間間隔に対して一般的に使用される文字列形式を作成する標準書式指定文字列について説明します。
[カスタム TimeSpan 書式指定文字列](custom-timespan.md) | 時間間隔に対するアプリケーション固有の文字列形式を作成するカスタム書式指定文字列について説明します。
[列挙型書式指定文字列](enumeration-format.md) | 列挙型の文字列形式を作成するために使用される標準書式指定文字列について説明します。
[Guid.ToString(String)](xref:System.Guid.ToString(System.String)) | [Guid](xref:System.Guid) 値の標準的書式指定文字列について説明します。

## <a name="culturesensitive-formatting-with-format-providers-and-the-iformatprovider-interface"></a>書式プロバイダーと IFormatProvider インターフェイスによるカルチャに依存した書式指定

書式指定子を利用することでオブジェクトの書式をカスタマイズできますが、多くの場合、意味のあるオブジェクトの文字列形式を生成するには追加の書式設定情報が必要です。 たとえば、"C" 標準書式指定文字列または "$ #,#.00" などのカスタム書式指定文字列を使用して数字を通貨値として書式設定する場合、少なくとも、正しい通貨記号、桁区切り記号、および小数点記号についての情報を書式設定された文字列に含めることができる必要があります。 .NET では、[IFormatProvider](xref:System.IFormatProvider) インターフェイスによって、この追加の書式設定情報を利用できるようにします。このインターフェイスは、数値型および日付/時刻型の `ToString` メソッドの 1 つ以上のオーバーロードに対するパラメーターとして提供されます。 [IFormatProvider](xref:System.IFormatProvider) の実装は .NET で使用され、カルチャ固有の書式指定をサポートします。 それぞれ異なるカルチャを示す 3 つの [IFormatProvider](xref:System.IFormatProvider) オブジェクトを使用してオブジェクトの書式を設定した場合に、その文字列形式がどのように変化するかを次の例に示します。

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      decimal value = 1603.42m;
      Console.WriteLine(value.ToString("C3", new CultureInfo("en-US")));
      Console.WriteLine(value.ToString("C3", new CultureInfo("fr-FR")));
      Console.WriteLine(value.ToString("C3", new CultureInfo("de-DE")));
   }
}
// The example displays the following output:
//       $1,603.420
//       1 603,420 €
//       1.603,420 €
```

```vb
Imports System.Globalization

Public Module Example
   Public Sub Main()
      Dim value As Decimal = 1603.42d
      Console.WriteLine(value.ToString("C3", New CultureInfo("en-US")))
      Console.WriteLine(value.ToString("C3", New CultureInfo("fr-FR")))
      Console.WriteLine(value.ToString("C3", New CultureInfo("de-DE")))
   End Sub
End Module
' The example displays the following output:
'       $1,603.420
'       1 603,420 €
'       1.603,420 €
```

[IFormatProvider](xref:System.IFormatProvider) インターフェイスには、[GetFormat(Type)](xref:System.IFormatProvider.GetFormat(System.Type)) という 1 つのメソッドが含まれています。このメソッドには、書式設定情報を提供するオブジェクトの型を指定する 1 つのパラメーターがあります。 このメソッドがその型のオブジェクトを提供できる場合は、それが返されます。 それ以外の場合は、null 参照を返します。

[IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) はコールバック メソッドです。 [IFormatProvider](xref:System.IFormatProvider) パラメーターを含む `ToString` メソッド オーバーロードを呼び出すと、その [IFormatProvider](xref:System.IFormatProvider) オブジェクトの [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) メソッドが呼び出されます。 [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) メソッドは、*formatType* パラメーターで指定された、必要な書式設定情報を提供するオブジェクトを `ToString` メソッドに返します。 

数多くの書式指定メソッドや文字列変換メソッドに [IFormatProvider](xref:System.IFormatProvider) 型のパラメーターが含まれていますが、多くの場合、メソッドを呼び出すときはパラメーターの値は無視されます。 [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) メソッドに渡される [Type](xref:System.Type) オブジェクトのパラメーターと型を使用する書式指定メソッドの一部を次の表に示します。 

メソッド | *formatType* パラメーターの型
------ | ------------------------------
数値型の `ToString` メソッド | [System.Globalization.NumberFormatInfo](xref:System.Globalization.NumberFormatInfo)
日付/時刻型の `ToString` メソッド | [System.Globalization.DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo)
[String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) | [System.ICustomFormatter](xref:System.ICustomFormatter)
[StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)) | [System.ICustomFormatter](xref:System.ICustomFormatter)

.NET には、[IFormatProvider](xref:System.IFormatProvider) を実装する次の 3 つのクラスが用意されています。 

* [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo)。このクラスは、特定のカルチャの日付と時刻の値に対する書式設定情報を提供します。 対応する [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) の実装では、それ自身のインスタンスが返されます。

* [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo)。このクラスは、特定のカルチャの数値に対する書式設定情報を提供します。 対応する [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) の実装では、それ自身のインスタンスが返されます。

* [CultureInfo](xref:System.Globalization.CultureInfo)。 対応する [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) の実装では、数値に対する書式設定情報を提供する [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) オブジェクトか、日付と時刻の値に対する書式設定情報を提供する [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) オブジェクトのいずれかが返されます。 

また、これらのクラスのうちのいずれかを置き換える独自の書式プロバイダーを実装できます。 ただし、実装の `GetFormat` メソッドは、書式設定情報を `ToString` メソッドに渡す場合、前の表に示した型のオブジェクトを返す必要があります。

### <a name="culturesensitive-formatting-of-numeric-values"></a>数値のカルチャに依存した書式設定

既定では、数値の書式指定はカルチャに依存します。 書式指定メソッドを呼び出すときにカルチャを指定しない場合は、現在のスレッド カルチャの書式指定規則が使用されます。 次に示す例では、現在のスレッド カルチャを 4 回変更した後に、[Decimal.ToString(String)](xref:System.Decimal.ToString(System.String)) メソッドを呼び出します。 各ケースでは、結果の文字列は、現在のカルチャの書式指定規則を反映します。 これは、各数値型の `ToString` メソッドへの呼び出しを、`ToString(String)` メソッドと `ToString(String, IFormatProvider)` メソッドがラップするためです。 

```csharp
using System;
using System.Globalization;
using System.Threading;

public class Example
{
   public static void Main()
   {
      string[] cultureNames = { "en-US", "fr-FR", "es-MX", "de-DE" };
      Decimal value = 1043.17m;

      foreach (var cultureName in cultureNames) {
         // Change the current thread culture.
         Thread.CurrentThread.CurrentCulture = CultureInfo.CreateSpecificCulture(cultureName);
         Console.WriteLine("The current culture is {0}", 
                           Thread.CurrentThread.CurrentCulture.Name);
         Console.WriteLine(value.ToString("C2"));
         Console.WriteLine();
      }   
   }
}
// The example displays the following output:
//       The current culture is en-US
//       $1,043.17
//       
//       The current culture is fr-FR
//       1 043,17 €
//       
//       The current culture is es-MX
//       $1,043.17
//       
//       The current culture is de-DE
//       1.043,17 €
```

```vb
Imports System.Globalization
Imports System.Threading 

Module Example
   Public Sub Main()
      Dim cultureNames() As String = { "en-US", "fr-FR", "es-MX", "de-DE" }
      Dim value As Decimal = 1043.17d 

      For Each cultureName In cultureNames
         ' Change the current thread culture.
         Thread.CurrentThread.CurrentCulture = CultureInfo.CreateSpecificCulture(cultureName)
         Console.WriteLine("The current culture is {0}", 
                           Thread.CurrentThread.CurrentCulture.Name)
         Console.WriteLine(value.ToString("C2"))
         Console.WriteLine()
      Next                  
   End Sub
End Module
' The example displays the following output:
'       The current culture is en-US
'       $1,043.17
'       
'       The current culture is fr-FR
'       1 043,17 €
'       
'       The current culture is es-MX
'       $1,043.17
'       
'       The current culture is de-DE
'       1.043,17 €
```

また、*provider* パラメーターを持つ `ToString` オーバーロードを呼び出して、次のどちらかを渡すことにより、特定カルチャの数値を書式指定することもできます。 

* 使用される書式指定規則のカルチャを表す [CultureInfo](xref:System.Globalization.CultureInfo) オブジェクト。 その [CultureInfo.GetFormat](xref:System.Globalization.CultureInfo.GetFormat(System.Type)) メソッドは、[CultureInfo.NumberFormat](xref:System.Globalization.CultureInfo.NumberFormat) プロパティの値を返します。このプロパティは、数値にカルチャ固有の書式指定情報を提供する [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) オブジェクトです。

* 使用されるカルチャ固有の書式指定規則を定義する [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) オブジェクト。 その [GetFormat](xref:System.Globalization.NumberFormatInfo.GetFormat(System.Type)) メソッドでは、それ自身のインスタンスが返されます。

次の例では、浮動小数点数を書式指定する際に、英語 (米国) と英語 (英国) のカルチャおよびフランス語とロシア語のニュートラル カルチャを表す [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) オブジェクトを使用します。

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {                                                                                                    
      Double value = 1043.62957;
      string[] cultureNames = { "en-US", "en-GB", "ru", "fr" };

      foreach (var name in cultureNames) {
         NumberFormatInfo nfi = CultureInfo.CreateSpecificCulture(name).NumberFormat;
         Console.WriteLine("{0,-6} {1}", name + ":", value.ToString("N3", nfi));
      }   
   }
}
// The example displays the following output:
//       en-US: 1,043.630
//       en-GB: 1,043.630
//       ru:    1 043,630
//       fr:    1 043,630
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim value As Double = 1043.62957
      Dim cultureNames() As String = { "en-US", "en-GB", "ru", "fr" }

      For Each name In cultureNames
         Dim nfi As NumberFormatInfo = CultureInfo.CreateSpecificCulture(name).NumberFormat
         Console.WriteLine("{0,-6} {1}", name + ":", value.ToString("N3", nfi))
      Next   
   End Sub
End Module
' The example displays the following output:
'       en-US: 1,043.630
'       en-GB: 1,043.630
'       ru:    1 043,630
'       fr:    1 043,630
```

### <a name="culturesensitive-formatting-of-date-and-time-values"></a>日付と時刻の値のカルチャに依存した書式設定

既定では、日時の値の書式指定はカルチャに依存します。 書式指定メソッドを呼び出すときにカルチャを指定しない場合は、現在のスレッド カルチャの書式指定規則が使用されます。 次に示す例では、現在のスレッド カルチャを 4 回変更した後に、[DateTime.ToString(String)](xref:System.DateTime.ToString(System.String)) メソッドを呼び出します。 各ケースでは、結果の文字列は、現在のカルチャの書式指定規則を反映します。 これは、[DateTime.ToString()](xref:System.DateTime.ToString)、[DateTime.ToString(String)](xref:System.DateTime.ToString(System.String))、[DateTimeOffset.ToString()](xref:System.DateTimeOffset.ToString(System.String))、[DateTimeOffset.ToString(String)](xref:System.DateTimeOffset.ToString(System.String)) の各メソッドが、[DateTime.ToString(String, IFormatProvider)](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) メソッドおよび [DateTimeOffset.ToString(String, IFormatProvider)](xref:System.DateTimeOffset.ToString(System.String,System.IFormatProvider)) メソッドへの呼び出しをラップするためです。

```csharp
using System;
using System.Globalization;
using System.Threading;

public class Example
{
   public static void Main()
   {
      string[] cultureNames = { "en-US", "fr-FR", "es-MX", "de-DE" };
      DateTime dateToFormat = new DateTime(2012, 5, 28, 11, 30, 0);

      foreach (var cultureName in cultureNames) {
         // Change the current thread culture.
         Thread.CurrentThread.CurrentCulture = CultureInfo.CreateSpecificCulture(cultureName);
         Console.WriteLine("The current culture is {0}", 
                           Thread.CurrentThread.CurrentCulture.Name);
         Console.WriteLine(dateToFormat.ToString("F"));
         Console.WriteLine();
      }   
   }
}
// The example displays the following output:
//       The current culture is en-US
//       Monday, May 28, 2012 11:30:00 AM
//       
//       The current culture is fr-FR
//       lundi 28 mai 2012 11:30:00
//       
//       The current culture is es-MX
//       lunes, 28 de mayo de 2012 11:30:00 a.m.
//       
//       The current culture is de-DE
//       Montag, 28. Mai 2012 11:30:00
```

```vb
Imports System.Globalization
Imports System.Threading 

Module Example
   Public Sub Main()
      Dim cultureNames() As String = { "en-US", "fr-FR", "es-MX", "de-DE" }
      Dim dateToFormat As Date = #5/28/2012 11:30AM#

      For Each cultureName In cultureNames
         ' Change the current thread culture.
         Thread.CurrentThread.CurrentCulture = CultureInfo.CreateSpecificCulture(cultureName)
         Console.WriteLine("The current culture is {0}", 
                           Thread.CurrentThread.CurrentCulture.Name)
         Console.WriteLine(dateToFormat.ToString("F"))
         Console.WriteLine()
      Next                  
   End Sub
End Module
' The example displays the following output:
'       The current culture is en-US
'       Monday, May 28, 2012 11:30:00 AM
'       
'       The current culture is fr-FR
'       lundi 28 mai 2012 11:30:00
'       
'       The current culture is es-MX
'       lunes, 28 de mayo de 2012 11:30:00 a.m.
'       
'       The current culture is de-DE
'       Montag, 28. Mai 2012 11:30:00
```

provider パラメーターを持つ [DateTime.ToString](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) または [DateTimeOffset.ToString](xref:System.DateTimeOffset.ToString(System.String,System.IFormatProvider)) オーバーロードを呼び出して、次のどちらかを渡すことにより、特定カルチャの日時の値を書式指定することもできます。 

* 使用される書式指定規則のカルチャを表す [CultureInfo](xref:System.Globalization.CultureInfo) オブジェクト。 その [CultureInfo.GetFormat](xref:System.Globalization.CultureInfo.GetFormat(System.Type)) メソッドは、[CultureInfo.NumberFormat](xref:System.Globalization.CultureInfo.NumberFormat) プロパティの値を返します。このプロパティは、数値にカルチャ固有の書式指定情報を提供する [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) オブジェクトです。

* 使用されるカルチャ固有の書式指定規則を定義する [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) オブジェクト。 その [GetFormat](xref:System.Globalization.DateTimeFormatInfo.GetFormat(System.Type)) メソッドでは、それ自身のインスタンスが返されます。

次の例では、日付を書式指定する際に、英語 (米国) と英語 (英国) のカルチャおよびフランス語とロシア語のニュートラル カルチャを表す [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) オブジェクトを使用します。 

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {                                                                                                    
      DateTime dat1 = new DateTime(2012, 5, 28, 11, 30, 0);
      string[] cultureNames = { "en-US", "en-GB", "ru", "fr" };

      foreach (var name in cultureNames) {
         DateTimeFormatInfo dtfi = CultureInfo.CreateSpecificCulture(name).DateTimeFormat;
         Console.WriteLine("{0}: {1}", name, dat1.ToString(dtfi));
      }   
   }
}
// The example displays the following output:
//       en-US: 5/28/2012 11:30:00 AM
//       en-GB: 28/05/2012 11:30:00
//       ru: 28.05.2012 11:30:00
//       fr: 28/05/2012 11:30:00
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim dat1 As Date = #5/28/2012 11:30AM#
      Dim cultureNames() As String = { "en-US", "en-GB", "ru", "fr" }

      For Each name In cultureNames
         Dim dtfi As DateTimeFormatInfo = CultureInfo.CreateSpecificCulture(name).DateTimeFormat
         Console.WriteLine("{0}: {1}", name, dat1.ToString(dtfi))
      Next   
   End Sub
End Module
' The example displays the following output:
'       en-US: 5/28/2012 11:30:00 AM
'       en-GB: 28/05/2012 11:30:00
'       ru: 28.05.2012 11:30:00
'       fr: 28/05/2012 11:30:00
```

## <a name="the-iformattable-interface"></a>IFormattable インターフェイス

通常、書式指定文字列および [IFormatProvider](xref:System.IFormatProvider) パラメーターを使用して `ToString` メソッドをオーバーロードする型は、[IFormattable](xref:System.IFormattable) インターフェイスも実装します。 このインターフェイスには、[IFormattable.ToString(String, IFormatProvider)](xref:System.IFormattable.ToString(System.String,System.IFormatProvider)) という単一のメンバーがあります。このメンバーには、パラメーターとして書式指定文字列と書式プロバイダーの両方が含まれています。

アプリケーション定義のクラスに [IFormattable](xref:System.IFormattable) インターフェイスを実装した場合、2 つの利点があります。 

* [Convert](xref:System.Convert) クラスによる文字列変換がサポートされます。 [Convert.ToString(Object)](xref:System.Convert.ToString(System.Object)) メソッドおよび [Convert.ToString(Object, IFormatProvider)](xref:System.Convert.ToString(System.Object,System.IFormatProvider)) メソッドを呼び出すと、自動的に [IFormattable](xref:System.IFormattable) の実装が呼び出されます。

* 複合書式指定がサポートされます。 書式指定文字列を含む書式指定項目を使用してカスタムの型の書式を設定する場合に、共通言語ランタイムによって自動的に [IFormattable](xref:System.IFormattable) の実装が呼び出され、それに書式指定文字列が渡されます。 `String.Format` メソッドや `Console.WriteLine` メソッドを使用した複合書式指定の詳細については、「[複合書式指定](#composite-formatting)」のセクションを参照してください。

次の例では、[IFormattable](xref:System.IFormattable) インターフェイスを実装する `Temperature` クラスを定義しています。 このクラスでは、温度を摂氏で表示するために "C" 書式指定子または "G" 書式指定子、華氏で表示するために "F" 書式指定子、ケルビンで表示するために "K" 書式指定子をそれぞれサポートしています。

```csharp
using System;
using System.Globalization;

public class Temperature : IFormattable
{
   private decimal m_Temp;

   public Temperature(decimal temperature)
   {
      this.m_Temp = temperature;
   }

   public decimal Celsius
   {
      get { return this.m_Temp; }
   }

   public decimal Kelvin
   {
      get { return this.m_Temp + 273.15m; }   
   }

   public decimal Fahrenheit
   {
      get { return Math.Round((decimal) this.m_Temp * 9 / 5 + 32, 2); }
   }

   public override string ToString()
   {
      return this.ToString("G", null);
   }

   public string ToString(string format)
   {
      return this.ToString(format, null);
   }

   public string ToString(string format, IFormatProvider provider)  
   {
      // Handle null or empty arguments.
      if (String.IsNullOrEmpty(format)) format = "G";
      // Remove any white space and convert to uppercase.
      format = format.Trim().ToUpperInvariant();

      if (provider == null) provider = NumberFormatInfo.CurrentInfo;

      switch (format)
      {
         // Convert temperature to Fahrenheit and return string.
         case "F":
            return this.Fahrenheit.ToString("N2", provider) + "°F";
         // Convert temperature to Kelvin and return string.
         case "K":
            return this.Kelvin.ToString("N2", provider) + "K";
         // Return temperature in Celsius.
         case "C":
         case "G":
            return this.Celsius.ToString("N2", provider) + "°C";
         default:
            throw new FormatException(String.Format("The '{0}' format string is not supported.", format));
      }      
   }
}
```

```vb
Imports System.Globalization

Public Class Temperature : Implements IFormattable
   Private m_Temp As Decimal

   Public Sub New(temperature As Decimal)
      Me.m_Temp = temperature
   End Sub

   Public ReadOnly Property Celsius() As Decimal
      Get
         Return Me.m_Temp
      End Get   
   End Property

   Public ReadOnly Property Kelvin() As Decimal
      Get
         Return Me.m_Temp + 273.15d   
      End Get
   End Property

   Public ReadOnly Property Fahrenheit() As Decimal
      Get
         Return Math.Round(CDec(Me.m_Temp * 9 / 5 + 32), 2)
      End Get      
   End Property

   Public Overrides Function ToString() As String
      Return Me.ToString("G", Nothing)
   End Function

   Public Overloads Function ToString(format As String) As String
      Return Me.ToString(format, Nothing)
   End Function

   Public Overloads Function ToString(format As String, provider As IFormatProvider) As String _  
      Implements IFormattable.ToString

      ' Handle null or empty arguments.
      If String.IsNullOrEmpty(format) Then format = "G"
      ' Remove any white space and convert to uppercase.
      format = format.Trim().ToUpperInvariant()

      If provider Is Nothing Then provider = NumberFormatInfo.CurrentInfo

      Select Case format
         ' Convert temperature to Fahrenheit and return string.
         Case "F"
            Return Me.Fahrenheit.ToString("N2", provider) & "°F"
         ' Convert temperature to Kelvin and return string.
         Case "K"
            Return Me.Kelvin.ToString("N2", provider) & "K"
         ' Return temperature in Celsius.
         Case "C", "G"
            Return Me.Celsius.ToString("N2", provider) & "°C"
         Case Else
            Throw New FormatException(String.Format("The '{0}' format string is not supported.", format))
      End Select      
   End Function
End Class
```

次の例では、`Temperature` オブジェクトをインスタンス化しています。 その後、[ToString](xref:System.Convert.ToString(System.Object,System.IFormatProvider)) メソッドを呼び出し、いくつかの複合書式指定文字列を使用して `Temperature` オブジェクトのさまざまな文字列形式を取得します。 さらに、それらの各メソッド呼び出しで、`Temperature` クラスの [IFormattable](xref:System.IFormattable) 実装を呼び出しています。

```csharp
public class Example
{
   public static void Main()
   {
      Temperature temp1 = new Temperature(22m);
      Console.WriteLine(Convert.ToString(temp1, new CultureInfo("ja-JP")));
      Console.WriteLine("Temperature: {0:K}", temp1);
      Console.WriteLine("Temperature: {0:F}", temp1);
      Console.WriteLine(String.Format(new CultureInfo("fr-FR"), "Temperature: {0:F}", temp1));
   }
}
// The example displays the following output:
//       22.00°C
//       Temperature: 295.15°K
//       Temperature: 71.60°F
//       Temperature: 71,60°F
```

```vb
Public Module Example
   Public Sub Main()
      Dim temp1 As New Temperature(22d)
      Console.WriteLine(Convert.ToString(temp1, New CultureInfo("ja-JP")))
      Console.WriteLine("Temperature: {0:K}", temp1)
      Console.WriteLine("Temperature: {0:F}", temp1)
      Console.WriteLine(String.Format(New CultureInfo("fr-FR"), "Temperature: {0:F}", temp1)) 
   End Sub
End Module
' The example displays the following output:
'       22.00°C
'       Temperature: 295.15°K
'       Temperature: 71.60°F
'       Temperature: 71,60°F
```

## <a name="composite-formatting"></a>複合書式指定

`String.Format` や `StringBuilder.AppendFormat` などの一部のメソッドでは、複合書式指定がサポートされます。 複合書式指定文字列は一種のテンプレートで、0 個以上のオブジェクトの文字列形式が組み込まれた単一の文字列を返します。 各オブジェクトは、インデックス付きの書式指定項目によって、複合書式指定文字列で表現されます。 書式指定項目のインデックスは、それが表すオブジェクトのメソッドのパラメーター リスト内の位置と対応しています。 インデックスは 0 から始まります。 たとえば、`String.Format` メソッドの次のメソッド呼び出しでは、最初の書式指定項目 `{0:D}` は `thatDate` の文字列形式に、2 番目の書式指定項目 `{1}` は `item1` の文字列形式に、3 番目の書式指定項目 `{2:C2}` は `item1.Value` の文字列形式に置き換えられます。

```csharp
result = String.Format("On {0:d}, the inventory of {1} was worth {2:C2}.", 
                       thatDate, item1, item1.Value);
Console.WriteLine(result);                            
// The example displays output like the following if run on a system
// whose current culture is en-US:
//       On 5/1/2009, the inventory of WidgetA was worth $107.44.
```

```vb
result = String.Format("On {0:d}, the inventory of {1} was worth {2:C2}.", _
                       thatDate, item1, item1.Value)
Console.WriteLine(result)                            
' The example displays output like the following if run on a system
' whose current culture is en-US:
'       On 5/1/2009, the inventory of WidgetA was worth $107.44.
```

書式項目をそれに対応するオブジェクトの文字列形式に置換することに加えて、書式項目は以下を制御することもできます。 

* オブジェクトを文字列として表現する特定の方法 (オブジェクトが [IFormattable](xref:System.IFormattable) インターフェイスを実装し、書式文字列をサポートする場合)。 これは、: (コロン) 付きの書式項目のインデックスに、有効な書式文字列を続けることによります。 前の例では、日付の値を "d" (短い日付のパターン) 書式文字列 (`{0:d}` など) を書式設定し、数値を "C2" 書式文字列 (`{2:C2}` など) で書式設定して数値を 2 桁の小数部を含む 10 進数を持つ通貨値で表していました。 

* オブジェクトの文字列形式を含むフィールドの幅、およびそのフィールドの文字列形式の配置。 これは、, (コンマ) 付きの書式項目のインデックスに、フィールドの幅を続けることによります。 フィールドの幅が正の値の場合、文字列はフィールドで右揃えにし、フィールドの幅が負の値の場合、左揃えにします。 次の例では、20 文字のフィールドで日付の値を左揃えにし、11 文字のフィールドで、1 桁の小数部を含む 10 進数値を右揃えにします。 

```csharp
DateTime startDate = new DateTime(2015, 8, 28, 6, 0, 0);
decimal[] temps = { 73.452m, 68.98m, 72.6m, 69.24563m,
                   74.1m, 72.156m, 72.228m };
Console.WriteLine("{0,-20} {1,11}\n", "Date", "Temperature");
for (int ctr = 0; ctr < temps.Length; ctr++)
   Console.WriteLine("{0,-20:g} {1,11:N1}", startDate.AddDays(ctr), temps[ctr]);

// The example displays the following output:
//       Date                 Temperature
//
//       8/28/2015 6:00 AM           73.5
//       8/29/2015 6:00 AM           69.0
//       8/30/2015 6:00 AM           72.6
//       8/31/2015 6:00 AM           69.2
//       9/1/2015 6:00 AM            74.1
//       9/2/2015 6:00 AM            72.2
//       9/3/2015 6:00 AM            72.2
```

```vb
Dim startDate As New Date(2015, 8, 28, 6, 0, 0)
Dim temps() As Decimal = { 73.452, 68.98, 72.6, 69.24563,
                           74.1, 72.156, 72.228 }
Console.WriteLine("{0,-20} {1,11}", "Date", "Temperature")
Console.WriteLine()
For ctr As Integer = 0 To temps.Length - 1
   Console.WriteLine("{0,-20:g} {1,11:N1}", startDate.AddDays(ctr), temps(ctr))
Next
' The example displays the following output:
'       Date                 Temperature
'
'       8/28/2015 6:00 AM           73.5
'       8/29/2015 6:00 AM           69.0
'       8/30/2015 6:00 AM           72.6
'       8/31/2015 6:00 AM           69.2
'       9/1/2015 6:00 AM            74.1
'       9/2/2015 6:00 AM            72.2
'       9/3/2015 6:00 AM            72.2
```

配置文字列コンポーネントと書式文字列コンポーネントの両方が存在する場合、前者は後者の前にきます (たとえば `{0,-20:g}`)。 

複合書式指定の詳細については、「[複合書式指定](composite-format.md)」を参照してください。

## <a name="custom-formatting-with-icustomformatter"></a>ICustomFormatter を使用したカスタム書式設定

[String.Format(IFormatProvider, String, Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object[])) および [StringBuilder.AppendFormat(IFormatProvider, String, Object[])](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)) の 2 つの複合書式指定メソッドには、カスタム書式設定をサポートしている書式プロバイダー パラメーターが含まれています。 これらの書式指定メソッドのいずれかを呼び出すと、書式プロバイダーの `GetFormat` メソッドに [ICustomFormatter](xref:System.ICustomFormatter) インターフェイスを表す [Type](xref:System.Type) オブジェクトが渡されます。 次に、`GetFormat` メソッドによって、カスタム書式設定を提供する [ICustomFormatter](xref:System.ICustomFormatter) の実装が返されます。

[ICustomFormatter](xref:System.ICustomFormatter) インターフェイスには、[Format(String, Object, IFormatProvider)](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) という単一のメソッドがあります。このメソッドは、複合書式指定文字列の書式指定項目ごとに 1 回、複合書式指定メソッドによって自動的に呼び出されます。 [Format(String, Object, IFormatProvider)](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) メソッドには、3 つのパラメーターがあります。書式指定項目の *formatString* 引数を表す書式指定文字列、書式を設定するオブジェクト、および書式指定サービスを提供する [IFormatProvider](xref:System.IFormatProvider) オブジェクトの 3 つです。 通常は、[ICustomFormatter](xref:System.ICustomFormatter) を実装するクラスでは [IFormatProvider](xref:System.IFormatProvider) も実装するため、この最後のパラメーターはカスタム書式指定クラス自体への参照になります。 このメソッドは、書式を設定するオブジェクトのカスタム書式の文字列形式を返します。 オブジェクトの書式を設定できない場合は、null 参照を返します。

整数値を 2 桁の 16 進値とそれに続く 1 つの空白のシーケンスとして表示する、`ByteByByteFormatter` という名前の [ICustomFormatter](xref:System.ICustomFormatter) の実装の例を次に示します。

```csharp
public class ByteByByteFormatter : IFormatProvider, ICustomFormatter
{
   public object GetFormat(Type formatType)
   { 
      if (formatType == typeof(ICustomFormatter))
         return this;
      else
         return null;
   }

   public string Format(string format, object arg, 
                          IFormatProvider formatProvider)
   {   
      if (! formatProvider.Equals(this)) return null;

      // Handle only hexadecimal format string.
      if (! format.StartsWith("X")) return null;

      byte[] bytes;
      string output = null;

      // Handle only integral types.
      if (arg is Byte) 
         bytes = BitConverter.GetBytes((Byte) arg);
      else if (arg is Int16)
         bytes = BitConverter.GetBytes((Int16) arg);
      else if (arg is Int32)
         bytes = BitConverter.GetBytes((Int32) arg);
      else if (arg is Int64)   
         bytes = BitConverter.GetBytes((Int64) arg);
      else if (arg is SByte)
         bytes = BitConverter.GetBytes((SByte) arg);
      else if (arg is UInt16)
         bytes = BitConverter.GetBytes((UInt16) arg);
      else if (arg is UInt32)
         bytes = BitConverter.GetBytes((UInt32) arg);
      else if (arg is UInt64)
         bytes = BitConverter.GetBytes((UInt64) arg);
      else
         return null;

      for (int ctr = bytes.Length - 1; ctr >= 0; ctr--)
         output += String.Format("{0:X2} ", bytes[ctr]);   

      return output.Trim();
   }
}
```

```vb
Public Class ByteByByteFormatter : Implements IFormatProvider, ICustomFormatter
   Public Function GetFormat(formatType As Type) As Object _
                   Implements IFormatProvider.GetFormat
      If formatType Is GetType(ICustomFormatter) Then
         Return Me
      Else
         Return Nothing
      End If
   End Function

   Public Function Format(fmt As String, arg As Object, 
                          formatProvider As IFormatProvider) As String _
                          Implements ICustomFormatter.Format

      If Not formatProvider.Equals(Me) Then Return Nothing

      ' Handle only hexadecimal format string.
      If Not fmt.StartsWith("X") Then 
            Return Nothing
      End If

      ' Handle only integral types.
      If Not typeof arg Is Byte AndAlso
         Not typeof arg Is Int16 AndAlso
         Not typeof arg Is Int32 AndAlso
         Not typeof arg Is Int64 AndAlso
         Not typeof arg Is SByte AndAlso
         Not typeof arg Is UInt16 AndAlso
         Not typeof arg Is UInt32 AndAlso
         Not typeof arg Is UInt64 Then _
            Return Nothing

      Dim bytes() As Byte = BitConverter.GetBytes(arg)
      Dim output As String = Nothing

      For ctr As Integer = bytes.Length - 1 To 0 Step -1
         output += String.Format("{0:X2} ", bytes(ctr))   
      Next

      Return output.Trim()
   End Function
End Class
```

`ByteByByteFormatter` クラスを使用して整数値の書式を設定する例を次に示します。 [ICustomFormatter.Format](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) メソッドが 2 回目の [String.Format(IFormatProvider, String, Object[])](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) メソッド呼び出しで複数回呼び出されることに注意してください。また、`.ByteByByteFormatter.Format` メソッドが "N0" 書式指定文字列を認識せず、null 参照を返すため、3 回目のメソッド呼び出しでは既定の [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) プロバイダーが使用されていることに注意してください。

```csharp
public class Example
{
   public static void Main()
   {
      long value = 3210662321; 
      byte value1 = 214;
      byte value2 = 19;

      Console.WriteLine(String.Format(new ByteByByteFormatter(), "{0:X}", value));
      Console.WriteLine(String.Format(new ByteByByteFormatter(), "{0:X} And {1:X} = {2:X} ({2:000})", 
                                      value1, value2, value1 & value2));                                
      Console.WriteLine(String.Format(new ByteByByteFormatter(), "{0,10:N0}", value));
   }
}
// The example displays the following output:
//       00 00 00 00 BF 5E D1 B1
//       00 D6 And 00 13 = 00 12 (018)
//       3,210,662,321
```

```vb
Public Module Example
   Public Sub Main()
      Dim value As Long = 3210662321 
      Dim value1 As Byte = 214
      Dim value2 As Byte = 19

      Console.WriteLine((String.Format(New ByteByByteFormatter(), "{0:X}", value)))
      Console.WriteLine((String.Format(New ByteByByteFormatter(), "{0:X} And {1:X} = {2:X} ({2:000})", 
                                      value1, value2, value1 And value2)))                                
      Console.WriteLine(String.Format(New ByteByByteFormatter(), "{0,10:N0}", value))
   End Sub
End Module
' The example displays the following output:
'       00 00 00 00 BF 5E D1 B1
'       00 D6 And 00 13 = 00 12 (018)
'       3,210,662,321
```

## <a name="related-topics"></a>関連トピック

タイトル | 定義
----- | ----------
[標準の数値書式指定文字列](standard-numeric.md) | 数値に対して一般的に使用される文字列形式を作成する標準書式指定文字列について説明します。 
[カスタム数値書式指定文字列](custom-numeric.md) | 数値に対するアプリケーション固有の文字列形式を作成するカスタム書式指定文字列について説明します。
[標準の日時書式指定文字列](standard-datetime.md) |  [DateTime](xref:System.DateTime) 値に対して一般的に使用される文字列形式を作成する標準書式指定文字列について説明します。
[カスタム日時書式指定文字列](custom-datetime.md) | [DateTime](xref:System.DateTime) 値に対するアプリケーション固有の文字列形式を作成するカスタム書式指定文字列について説明します。
[標準 TimeSpan 書式指定文字列](standard-timespan.md) | 時間間隔に対して一般的に使用される文字列形式を作成する標準書式指定文字列について説明します。
[カスタム TimeSpan 書式指定文字列](custom-timespan.md) | 時間間隔に対するアプリケーション固有の文字列形式を作成するカスタム書式指定文字列について説明します。
[列挙型書式指定文字列](enumeration-format.md) | 列挙型の文字列形式を作成するために使用される標準書式指定文字列について説明します。
[複合書式指定](composite-format.md) | 文字列に 1 つ以上の書式指定された値を埋め込む方法について説明します。 この文字列は、コンソールに表示したり、ストリームに書き込んだりできます。
[書式設定操作の実行](performing-formatting-operations.md) | 特定の書式設定操作を行うための手順を説明するトピックの一覧を示します。
[文字列の解析](parsing-strings.md) | オブジェクトの文字列表現によって指定された値にオブジェクトを初期化する方法について説明します。 解析は書式設定の逆の操作です。

## <a name="reference"></a>参照

[System.IFormattable](xref:System.IFormattable)

[System.IFormatProvider](xref:System.IFormatProvider)

[System.ICustomFormatter](xref:System.ICustomFormatter)



<!--HONumber=Nov16_HO1-->


