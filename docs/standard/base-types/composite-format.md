---
title: "複合書式指定"
description: "複合書式指定"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/25/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: a01efc8f-c242-4535-bd32-acd0032d9590
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 15c549f5df0b6de8164e05f50855006996a47fac

---

# <a name="composite-formatting"></a>複合書式指定

.NET の複合書式指定機能は、オブジェクトのリストおよび複合書式指定文字列を入力として使用します。 複合書式指定文字列は、固定テキストに、書式指定項目と呼ばれるインデックス化されたプレースホルダーが混合されて構成されます。このプレースホルダーはリスト内のオブジェクトに対応します。 書式設定操作によって生成される結果の文字列は、元の固定テキストに文字列で表されたリスト内のオブジェクトが混合されて構成されます。 

複合書式指定機能をサポートするメソッドには、次のようなものがあります。 

* [String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object))。書式設定された結果文字列を返します。 

* [StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider, System.String, System.Object)。書式設定された結果文字列を [StringBuilder](xref:System.Text.StringBuilder) オブジェクトに追加します。

* [Console](xref:System.Console) `WriteLine` メソッドの一部のオーバーロード。書式設定された結果文字列をコンソールに表示します。  

* [TextWriter](xref:System.IO.TextWriter) `WriteLine` メソッドの一部のオーバーロード。書式設定された結果文字列をストリームまたはファイルに書き込みます。 [TextWriter](xref:System.IO.TextWriter) から派生したクラス ([StreamWriter](xref:System.IO.StreamWriter) など) も、この機能を共有します。

* [Debug.WriteLine(String, Object[])](xref:System.Diagnostics.Debug.WriteLine(System.String,System.Object[]))。書式設定されたメッセージをトレース リスナーに出力します。 

* [Trace.TraceError(String, Object[])](xref:System.Diagnostics.Trace.TraceError(System.String,System.Object[]))、[Trace.TraceInformation(String, Object[])](xref:System.Diagnostics.Trace.TraceInformation(System.String,System.Object[]))、および [Trace.TraceWarning(String, Object[])](xref:System.Diagnostics.Trace.TraceWarning(System.String,System.Object[])) メソッド。書式設定されたメッセージをトレース リスナーに出力します。 

* [TraceSource.TraceInformation(String, Object[])](xref:System.Diagnostics.TraceSource.TraceInformation(System.String,System.Object[])) メソッド。情報提供メソッドをトレース リスナーに書き込みます。 

## <a name="composite-format-string"></a>複合書式指定文字列

複合書式指定文字列とオブジェクト リストは、複合書式指定機能をサポートするメソッドの引数として使用されます。 複合書式指定文字列は、1 つ以上の書式指定項目が混合された 0 個以上の固定テキストで構成されます。 固定テキストはユーザーが任意に選択した文字列で、各書式指定項目はリスト内のオブジェクトまたはボックス化された構造体に対応します。 複合書式指定機能は、各書式指定項目がリスト内の対応するオブジェクトの文字列表現で置換された新しい文字列を返します。

[Format](xref:System.String.Format(System.String.Format(System.IFormatProvider,System.String,System.Object)) コード フラグメントの例を次に示します。

```csharp
string name = "Fred";
String.Format("Name = {0}, hours = {1:hh}", name, DateTime.Now);
```

```vb
Dim name As String = "Fred"
String.Format("Name = {0}, hours = {1:hh}", name, DateTime.Now)
```

固定テキストは、`"Name = "` および `", hours = "` です。 書式指定項目の 1 つは、インデックスが 0 である `"{0}"` であり、オブジェクト `name` に対応します。もう 1 つはインデックスが 1 である `"{1:hh}"` であり、オブジェクト `DateTime.Now` に対応します。

## <a name="format-item-syntax"></a>書式指定項目の構文

各書式指定項目は、次の形式を使用し、次のコンポーネントで構成されます。

__{__*index*[,*alignment*][:*formatString*]__}__

対になった中かっこ ("{" と "}") が必要です。 
 
### <a name="index-component"></a>Index コンポーネント

必須の *index* コンポーネントは、パラメーター指定子とも呼ばれ、オブジェクトのリスト内で対応する項目を識別するための 0 から始まる数値です。 つまり、パラメーター指定子が 0 である書式指定項目はリスト内の最初のオブジェクトを書式設定し、パラメーター指定子が 1 である書式指定項目はリスト内の 2 番目のオブジェクトを書式設定します。 次の例には、10 未満の素数を表す 4 つのパラメーター指定子 (0 ～ 3 の番号が付けられている) が含まれています。 

```csharp
string primes;
primes = String.Format("Prime numbers less than 10: {0}, {1}, {2}, {3}",
                       2, 3, 5, 7 );
Console.WriteLine(primes);
// The example displays the following output:
//      Prime numbers less than 10: 2, 3, 5, 7
```

```vb
Dim primes As String
primes = String.Format("Prime numbers less than 10: {0}, {1}, {2}, {3}",
                       2, 3, 5, 7 )
Console.WriteLine(primes)
' The example displays the following output:
'      Prime numbers less than 10: 2, 3, 5, 7
```

同じパラメーター指定子を指定することによって、複数の書式指定項目でオブジェクトのリスト内の同じ要素を参照できます。 たとえば、複合書式指定文字列で "0x{0:X} {0:E} {0:N}" のように指定することによって、1 つの数値を 16 進形式、指数形式、および数値形式で書式設定できます。以下に例を示します。 

```csharp
string multiple = String.Format("0x{0:X} {0:E} {0:N}",
                                Int64.MaxValue);
Console.WriteLine(multiple);
// The example displays the following output:
//      0x7FFFFFFFFFFFFFFF 9.223372E+018 9,223,372,036,854,775,807.00
```

```vb
Dim multiple As String = String.Format("0x{0:X} {0:E} {0:N}",
                                       Int64.MaxValue)
Console.WriteLine(multiple)
' The example displays the following output:
'      0x7FFFFFFFFFFFFFFF 9.223372E+018 9,223,372,036,854,775,807.00
```

各書式指定項目は、リスト内のどのオブジェクトでも参照できます。 たとえば、3 つのオブジェクトが存在する場合、2 番目、1 番目、3 番目のオブジェクトを書式設定するには、"{1} {0} {2}" のような複合書式指定文字列を指定します。 書式指定項目で参照されないオブジェクトは無視されます。 パラメーター指定子がオブジェクトのリストの範囲外の項目を指定する場合は、ランタイムに [FormatException](xref:System.FormatException) がスローされます。

### <a name="alignment-component"></a>Alignment コンポーネント

省略可能な *alignment* コンポーネントは、書式設定フィールドの幅を指定する符号付き整数です。 *alignment* の値が書式設定する文字列の長さよりも小さい場合、*alignment* は無視され、書式設定する文字列の長さがフィールドの幅として使用されます。 フィールド内の書式設定されたデータは、*alignment* が正の場合は右揃え、*alignment* が負の場合は左揃えされます。 埋め込みが必要な場合は、空白が使用されます。 *alignment* を指定する場合は、コンマが必要です。

次の例では、2 つの配列を定義します。1 つの配列には従業員の名前が含まれていて、もう 1 つの配列には従業員が 2 週間にわたって作業した時間数が含まれています。 複合書式指定文字列では、名前が 20 文字のフィールドに左揃えに指定され、時間数が 5 文字のフィールドに右揃えに指定されます。 "N1" 標準書式指定文字列も、時間を 1 桁の小数部で書式設定するために使用されることに注意してください。 

```csharp
using System;

public class Example
{
   public static void Main()
   {
      string[] names = { "Adam", "Bridgette", "Carla", "Daniel",
                         "Ebenezer", "Francine", "George" };
      decimal[] hours = { 40, 6.667m, 40.39m, 82, 40.333m, 80,
                                 16.75m };

      Console.WriteLine("{0,-20} {1,5}\n", "Name", "Hours");
      for (int ctr = 0; ctr < names.Length; ctr++)
         Console.WriteLine("{0,-20} {1,5:N1}", names[ctr], hours[ctr]);

   }
}
// The example displays the following output:
//       Name                 Hours
//
//       Adam                  40.0
//       Bridgette              6.7
//       Carla                 40.4
//       Daniel                82.0
//       Ebenezer              40.3
//       Francine              80.0
//       George                16.8
```

```vb
Module Example
   Public Sub Main()
      Dim names() As String = { "Adam", "Bridgette", "Carla", "Daniel",
                                "Ebenezer", "Francine", "George" }
      Dim hours() As Decimal = { 40, 6.667d, 40.39d, 82, 40.333d, 80,
                                 16.75d }

      Console.WriteLine("{0,-20} {1,5}", "Name", "Hours")
      Console.WriteLine()
      For ctr As Integer = 0 To names.Length - 1
         Console.WriteLine("{0,-20} {1,5:N1}", names(ctr), hours(ctr))
      Next
   End Sub
End Module
' The example displays the following output:
'       Name                 Hours
'
'       Adam                  40.0
'       Bridgette              6.7
'       Carla                 40.4
'       Daniel                82.0
'       Ebenezer              40.3
'       Francine              80.0
'       George                16.8
```

### <a name="format-string-component"></a>Format String コンポーネント

オプションの *formatString* コンポーネントは、書式設定されるオブジェクトの種類に適した書式指定文字列です。 対応するオブジェクトが数値の場合は標準またはカスタムの数値書式指定文字列を指定し、対応するオブジェクトが [DateTime](xref:System.DateTime) オブジェクトの場合は標準またはカスタムの日時書式指定文字列を指定し、対応するオブジェクトが列挙値の場合は[列挙型書式指定文字列](enumeration-format.md)を指定します。 *formatString* が指定されない場合は、数値、日付と時刻、または列挙型の汎用 ("G") 書式指定子が使用されます。 *formatString* を指定する場合はコロンが必要です。

次の表は、定義済みの一連の書式指定文字列をサポートする .NET Framework クラス ライブラリ内の型または型のカテゴリの一覧です。サポートされている書式指定文字列が示されているトピックへのリンクも含まれています。 文字列の書式設定とは拡張可能な機構で、既存のすべての型に対する新しい書式指定文字列を定義できるだけでなく、アプリケーション定義の型でサポートされる一連の書式指定文字列も定義できます。 詳細については、[IFormattable](xref:System.IFormattable) インターフェイスと [ICustomFormatter](xref:System.ICustomFormatter) インターフェイスに関するトピックを参照してください。 

型または型のカテゴリ | 参照トピック
--------------------- | ---
日付/時刻型 ([DateTime](xref:System.DateTime)、[DateTimeOffset](xref:System.DateTimeOffset)) | [標準の日時書式指定文字列](standard-datetime.md)、[カスタム日時書式指定文字列](custom-datetime.md)
列挙型 ([System.Enum](xref:System.Enum) から派生したすべての型) | [列挙型書式指定文字列](enumeration-format.md)
数値型 ([BigInteger](xref:System.Numerics.BigInteger)、[Byte](xref:System.Byte)、[Decimal](xref:System.Decimal)、[Double](xref:System.Double)、[Int16](xref:System.Int16)、[Int32](xref:System.Int32)、[Int64](xref:System.Int64)、[SByte](xref:System.SByte)、[Single](xref:System.Single)、[UInt16](xref:System.UInt16)、[UInt32](xref:System.UInt32)、[UInt64](xref:System.UInt64)) | [標準の数値書式指定文字列](standard-numeric.md)、[カスタム数値書式指定文字列](custom-numeric.md)
[Guid](xref:System.Guid) | [Guid.ToString(String)](xref:System.Guid.ToString(System.String))
[TimeSpan](xref:System.TimeSpan) | [標準の TimeSpan 書式指定文字列](standard-timespan.md)、[カスタム TimeSpan 書式指定文字列](custom-timespan.md)

### <a name="escaping-braces"></a>エスケープ中かっこ ({})

左中かっこ ({) および右中かっこ (}) は、書式指定項目の開始および終了として解釈されます。 したがって、左中かっこおよび右中かっこを文字として表示するためには、エスケープ シーケンスを使用する必要があります。 左中かっこを 1 つ ("{") 表示するには、左中かっこ 2 つ ("{{") を固定テキストに指定します。また、右中かっこを 1 つ ("}") 表示するには、右中かっこ 2 つ ("}}") を指定します。 書式指定項目に使用されている中かっこは、指定されている順序に従って解釈されます。 入れ子になった中かっこを解釈する機能はサポートされていません。 

エスケープされた中かっこの解釈によっては、予測しない結果になる場合があります。 たとえば、"{{{0:D}}}" という書式指定項目について考えます。この書式指定項目は、左中かっこ、10 進数として書式設定された数値、および右中かっこを表示することを意図しています。 しかし、この書式指定項目は、実際には、次のように解釈されます。 

1. 最初の 2 つの左中かっこ ("{{") がエスケープされ、左中かっこ 1 つが作成されます。 

2. 次の 3 文字 ("{0:") は、書式指定項目の開始として解釈されます。

3. 次の文字 ("D") は、Decimal 標準数値書式指定子として解釈できますが、エスケープされた次の 2 つの右中かっこ ("}}") からは単一の中かっこが作成されます。 結果として作成される文字列 ("D}") は、標準数値書式指定子ではないため、リテラル文字列 "D}" の表示を意味するカスタム書式指定文字列として解釈されます。 

4. 最後の中かっこ ("}") は、書式指定項目の終わりとして解釈されます。 

5. 最終的には、"{D}" というリテラル文字列が表示されます。 書式設定対象だった数値は、表示されません。

エスケープした中かっこと書式指定項目とが誤って解釈されないコードを記述するためには、中かっこと書式指定項目を別々に書式設定するという方法があります。 つまり、最初の書式設定操作でリテラルの開く中かっこを表示し、次の書式設定操作で書式指定項目の結果を表示し、最後の操作でリテラルの閉じる中かっこを表示します。 このアプローチの例を次に示します。

```csharp
int value = 6324;
string output = string.Format("{0}{1:D}{2}", 
                             "{", value, "}");
Console.WriteLine(output);
// The example displays the following output:
//       {6324} 
```

```vb
Dim value As Integer = 6324
Dim output As String = String.Format("{0}{1:D}{2}", _
                                     "{", value, "}")
Console.WriteLine(output)   
' The example displays the following output:
'       {6324}
```

### <a name="processing-order"></a>処理の順序

複合書式指定メソッドの呼び出しに、値が null でない [IFormatProvider](xref:System.IFormatProvider) 引数が含まれている場合、ランタイムはその [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) メソッドを呼び出して、[ICustomFormatter](xref:System.ICustomFormatter) 実装を要求します。 このメソッドが [ICustomFormatter](xref:System.ICustomFormatter) 実装を返すことができる場合、実装は後で使用できるようにキャッシュされます。 

書式指定項目に対応するパラメーター リストのそれぞれの値は、次の手順を実行することで文字列に変換されます。 最初の 3 つの手順の条件のいずれかに該当する場合は、その手順で値の文字列形式が返され、後続の手順は実行されません。

1. 書式設定する値が `null` の場合は、空の文字列 ("") が返されます。 

2. [ICustomFormatter](xref:System.ICustomFormatter) 実装が利用できる場合、ランタイムはその [Format](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) メソッドを呼び出します。 メソッドには書式指定項目の *formatString* 値 (ある場合) または `null` (ない場合) と、[IFormatProvider](xref:System.IFormatProvider) 実装が渡されます。 

3. 値が [IFormattable](xref:System.IFormattable) インターフェイスを実装している場合は、インターフェイスの [ToString(String,IFormatProvider)](xref:System.IFormattable.ToString(System.String,System.IFormatProvider)) メソッドが呼び出されます。 メソッドは、*formatString* 値 (書式指定項目内に値がある場合) または `null` (ない場合) を受け取ります。 [IFormatProvider](xref:System.IFormatProvider) 引数は、次のように判断されます。

    *   数値の場合、null 以外の [IFormatProvider](xref:System.IFormatProvider) 引数を持つ複合書式指定メソッドが呼び出されると、ランタイムは [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) メソッドから [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) オブジェクトを要求します。 オブジェクトを 1 つも取得できないか、引数の値が `null` であるか、または複合書式指定メソッドに [IFormatProvider](xref:System.IFormatProvider) パラメーターがない場合は、現在のスレッド カルチャの [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo オブジェクトが使用されます。 
    
    * 日付と時刻の値の場合、null 以外の [IFormatProvider](xref:System.IFormatProvider) 引数を持つ複合書式指定メソッドが呼び出されると、ランタイムは [IFormatProvider.GetFormat](xref:System.IFormatProvider._GetFormat(System.Type) メソッドから [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) オブジェクトを要求します。 オブジェクトを 1 つも取得できないか、引数の値が `null` であるか、または複合書式指定メソッドに [IFormatProvider](xref:System.IFormatProvider) パラメーターがない場合は、現在のスレッド カルチャの [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) オブジェクトが使用されます。 
    
    * 他の型のオブジェクトの場合、[IFormatProvider](xref:System.IFormatProvider) 引数を持つ複合書式指定が呼び出されると、その値 ([IFormatProvider](xref:System.IFormatProvider) オブジェクトが指定されない場合の `null` を含む) は [IFormattable.ToString](xref:System.IFormattable.ToString(System.String,System.IFormatProvider)) 実装に直接渡されます。 それ以外の場合は、現在のスレッド カルチャを表す [CultureInfo](xref:System.Globalization.CultureInfo) オブジェクトが [IFormattable.ToString](xref:System.IFormattable.ToString(System.String,System.IFormatProvider)) 実装に渡されます。 
    
4. [Object.ToString()](xref:System.Object.ToString) をオーバーライドするか、基底クラスの動作を継承する、型のパラメーターなしの `ToString` メソッドが呼び出されます。 この場合、書式指定項目の *formatString* コンポーネントで指定されている書式指定文字列は、存在していても無視されます。

前の手順が実行された後、アラインメントが適用されます。 

## <a name="code-examples"></a>コード例

複合書式指定を使用して文字列を作成する方法と、オブジェクトの `ToString` メソッドを使用して文字列を作成する方法を示すコード例を次に示します。 この 2 つの書式設定方法では、等価の文字列が作成されます。 

```csharp
string FormatString1 = String.Format("{0:dddd MMMM}", DateTime.Now);
string FormatString2 = DateTime.Now.ToString("dddd MMMM");
```

```vb
Dim FormatString1 As String = String.Format("{0:dddd MMMM}", DateTime.Now)
Dim FormatString2 As String = DateTime.Now.ToString("dddd MMMM")
```

現在の曜日が木曜日であり、月が 5 月であり、現在のカルチャが英語 (U.S.) の場合、上記のコード例で作成される 2 つの文字列の値はどちらも `Thursday May`です。

[Console.WriteLine](xref:System.Console.WriteLine) は、[String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) と同じ機能を公開します。 これら 2 つのメソッドの唯一の違いは、[String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) が結果を文字列で返すのに対し、[Console.WriteLine](xref:System.Console.WriteLine) は、[Console](xref:System.Console) オブジェクトに関連付けられた出力ストリームに結果を書き出す点です。 [Console.WriteLine](xref:System.Console.WriteLine) メソッドを使用して値 `MyInt` を通貨値として書式設定するコード例を次に示します。

```csharp
int MyInt = 100;
Console.WriteLine("{0:C}", MyInt);
// The example displays the following output 
// if en-US is the current culture:
//        $100.00
```

```vb
Dim MyInt As Integer = 100
Console.WriteLine("{0:C}", MyInt)
' The example displays the following output
' if en-US is the current culture:
'        $100.00
```

1 つのオブジェクトを 2 つの方法で書式設定する例を含め、複数のオブジェクトを書式設定する例を次に示します。

```csharp
string myName = "Fred";
Console.WriteLine(String.Format("Name = {0}, hours = {1:hh}, minutes = {1:mm}",
      myName, DateTime.Now));
// Depending on the current time, the example displays output like the following:
//    Name = Fred, hours = 11, minutes = 30                 
```

```vb
Dim myName As String = "Fred"
Console.WriteLine(String.Format("Name = {0}, hours = {1:hh}, minutes = {1:mm}", _
                  myName, DateTime.Now))
' Depending on the current time, the example displays output like the following:
'    Name = Fred, hours = 11, minutes = 30
```

書式設定でアラインメントを使用する方法を示す例を次に示します。 アラインメント結果を強調表示するため、書式が設定される引数を縦棒 (|) で囲んでいます。

```csharp
string myFName = "Fred";
string myLName = "Opals";
int myInt = 100;
string FormatFName = String.Format("First Name = |{0,10}|", myFName);
string FormatLName = String.Format("Last Name = |{0,10}|", myLName);
string FormatPrice = String.Format("Price = |{0,10:C}|", myInt); 
Console.WriteLine(FormatFName);
Console.WriteLine(FormatLName);
Console.WriteLine(FormatPrice);
Console.WriteLine();

FormatFName = String.Format("First Name = |{0,-10}|", myFName);
FormatLName = String.Format("Last Name = |{0,-10}|", myLName);
FormatPrice = String.Format("Price = |{0,-10:C}|", myInt);
Console.WriteLine(FormatFName);
Console.WriteLine(FormatLName);
Console.WriteLine(FormatPrice);
// The example displays the following output on a system whose current
// culture is en-US:
//          First Name = |      Fred|
//          Last Name = |     Opals|
//          Price = |   $100.00|
//
//          First Name = |Fred      |
//          Last Name = |Opals     |
//          Price = |$100.00   |
```

```vb
Dim myFName As String = "Fred"
Dim myLName As String = "Opals"

Dim myInt As Integer = 100
Dim FormatFName As String = String.Format("First Name = |{0,10}|", myFName)
Dim FormatLName As String = String.Format("Last Name = |{0,10}|", myLName)
Dim FormatPrice As String = String.Format("Price = |{0,10:C}|", myInt)
Console.WriteLine(FormatFName)
Console.WriteLine(FormatLName)
Console.WriteLine(FormatPrice)
Console.WriteLine()

FormatFName = String.Format("First Name = |{0,-10}|", myFName)
FormatLName = String.Format("Last Name = |{0,-10}|", myLName)
FormatPrice = String.Format("Price = |{0,-10:C}|", myInt)
Console.WriteLine(FormatFName)
Console.WriteLine(FormatLName)
Console.WriteLine(FormatPrice)
' The example displays the following output on a system whose current
' culture is en-US:
'          First Name = |      Fred|
'          Last Name = |     Opals|
'          Price = |   $100.00|
'
'          First Name = |Fred      |
'          Last Name = |Opals     |
'          Price = |$100.00   |
```

## <a name="see-also"></a>関連項目

[Console.WriteLine](xref:System.Console.WriteLine)

[String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object))

[型の書式設定](formatting-types.md)

[標準の日時書式指定文字列](standard-datetime.md)

[カスタム日時書式指定文字列](custom-datetime.md)

[列挙型書式指定文字列](enumeration-format.md)

[標準の数値書式指定文字列](standard-numeric.md)

[カスタム数値書式指定文字列](custom-numeric.md)

[標準 TimeSpan 書式指定文字列](standard-timespan.md)

[カスタム TimeSpan 書式指定文字列](custom-timespan.md)



<!--HONumber=Nov16_HO3-->


