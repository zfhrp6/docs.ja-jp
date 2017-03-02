---
title: "型変換"
description: "型変換"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/22/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: c9a53222-89cb-47e5-983d-4f0f204e31ba
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 0a774a170b7703b900c2044708b07faeb4e51548
ms.lasthandoff: 03/02/2017

---

# <a name="type-conversion"></a>型変換

すべての値には関連付けられた型があり、その値に割り振られる容量、可能な値の範囲、使用できるメンバーなどの属性を定義しています。 多くの値は複数の型として表現できます。 たとえば、値 `4` は整数または浮動小数点数として表現できます。 型変換を実行すると、変換元の型の値と等価な値が新しい型で作成されますが、それが元のオブジェクトと同一である (値が正確に一致する) とは限りません。

次の変換は、.NET によって自動的にサポートされます。

* 派生クラスから基底クラスへの変換。 これは、たとえば、任意のクラスまたは構造体のインスタンスを[オブジェクト](xref:System.Object) インスタンスに変換できることを意味します。 この変換では、キャスト演算子は必要ありません。

* 基本クラスから元の派生クラスへの変換。 C# の場合、この変換ではキャスト演算子が必要です。 Visual Basic では、`Option Strict` がオンの場合、`CType` 演算子が必要です。 

* インターフェイスを実装する型から、そのインターフェイスを表すインターフェイス オブジェクトへの変換。 この変換では、キャスト演算子は必要ありません。

* インターフェイス オブジェクトから、そのインターフェイスを実装する元の型への変換。 C# の場合、この変換ではキャスト演算子が必要です。 Visual Basic では、`Option Strict` がオンの場合、`CType` 演算子が必要です。 

これらの自動変換に加えて、.NET ではカスタムの型変換をサポートするいくつかの機能を提供しています。 次に例を示します。 

* `Implicit` 演算子。型の間で使用できる拡大変換を定義します。 詳細については、「[Implicit 演算子を使用する暗黙的な変換](#implicit-conversion-with-the-implicit-operator)」を参照してください。

* `Explicit` 演算子。型の間で使用できる縮小変換を定義します。 詳細については、「[Explicit 演算子を使用する明示的な変換](#explicit-conversion-with-the-explicit-operator)」を参照してください。

* [IConvertible](xref:System.IConvertible) インターフェイス。.NET の各基本データ型への変換を定義します。 詳細については、「[IConvertible インターフェイス](#the-iconvertible-interface)」を参照してください。

* [Convert](xref:System.Convert) クラス。`IConvertible` インターフェイスにメソッドを実装する一連のメソッドを提供します。 詳細については、「[Convert クラス](#the-convert-class)」を参照してください。

* [TypeConverter](xref:System.ComponentModel.TypeConverter) クラス。指定された型から他の型への変換をサポートするように拡張できる基本クラスです。 詳細については、「[TypeConverter クラス](#the-typeconverter-class)」を参照してください。

## <a name="implicit-conversion-with-the-implicit-operator"></a>Implicit 演算子を使用する暗黙的な変換

拡大変換では、変換後の型より範囲の制限が厳しい既存の型またはメンバー リストが制限されている既存の型の値から新しい値が作成されます。 拡大変換でデータ損失が発生することはありません (ただし、精度が失われることはあります)。 データが失われないため、コンパイラは明示的な変換メソッドまたはキャスト演算子を使用するように要求する必要がなく、暗黙的または透過的に変換を処理できます。

> [!NOTE]
> 暗黙的な変換を実行するコードで変換メソッドを呼び出したり、キャスト演算子を使用したりすることはできますが、暗黙的な変換がサポートされるコンパイラでは必要ありません。

たとえば、[Decimal](xref:System.Decimal) 型では、[Byte](xref:System.Byte)、[Char](xref:System.Char)、[Int16](xref:System.Int16)、[Int32](xref:System.Int32)、[Int64](xref:System.Int64)、[SByte](xref:System.SByte)、[UInt16](xref:System.UInt16)、[UInt32](xref:System.UInt32)、および [UInt64](xref:System.UInt64) の各値からの暗黙的な変換がサポートされます。 `Decimal` 変数への値の代入時に、これらの暗黙的な変換の一部が実行される例を次に示します。

```csharp
byte byteValue = 16;
short shortValue = -1024;
int intValue = -1034000;
long longValue = 1152921504606846976;
ulong ulongValue = UInt64.MaxValue;

decimal decimalValue;

decimalValue = byteValue;
Console.WriteLine("After assigning a {0} value, the Decimal value is {1}.", 
                  byteValue.GetType().Name, decimalValue); 

decimalValue = shortValue;
Console.WriteLine("After assigning a {0} value, the Decimal value is {1}.", 
                  shortValue.GetType().Name, decimalValue); 

decimalValue = intValue;
Console.WriteLine("After assigning a {0} value, the Decimal value is {1}.", 
                  intValue.GetType().Name, decimalValue); 

decimalValue = longValue;
Console.WriteLine("After assigning a {0} value, the Decimal value is {1}.", 
                  longValue.GetType().Name, decimalValue); 

decimalValue = ulongValue;
Console.WriteLine("After assigning a {0} value, the Decimal value is {1}.", 
                  longValue.GetType().Name, decimalValue); 
// The example displays the following output:
//    After assigning a Byte value, the Decimal value is 16.
//    After assigning a Int16 value, the Decimal value is -1024.
//    After assigning a Int32 value, the Decimal value is -1034000.
//    After assigning a Int64 value, the Decimal value is 1152921504606846976.
//    After assigning a Int64 value, the Decimal value is 18446744073709551615.
```

```vb
Dim byteValue As Byte = 16
Dim shortValue As Short = -1024
Dim intValue As Integer = -1034000
Dim longValue As Long = CLng(1024^6)
Dim ulongValue As ULong = ULong.MaxValue

Dim decimalValue As Decimal

decimalValue = byteValue
Console.WriteLine("After assigning a {0} value, the Decimal value is {1}.",
                  byteValue.GetType().Name, decimalValue) 

decimalValue = shortValue
Console.WriteLine("After assigning a {0} value, the Decimal value is {1}.",
                  shortValue.GetType().Name, decimalValue) 

decimalValue = intValue
Console.WriteLine("After assigning a {0} value, the Decimal value is {1}.",
                  intValue.GetType().Name, decimalValue) 

decimalValue = longValue
Console.WriteLine("After assigning a {0} value, the Decimal value is {1}.",
                  longValue.GetType().Name, decimalValue) 

decimalValue = ulongValue
Console.WriteLine("After assigning a {0} value, the Decimal value is {1}.",
                  longValue.GetType().Name, decimalValue) 
' The example displays the following output:
'    After assigning a Byte value, the Decimal value is 16.
'    After assigning a Int16 value, the Decimal value is -1024.
'    After assigning a Int32 value, the Decimal value is -1034000.
'    After assigning a Int64 value, the Decimal value is 1152921504606846976.
'    After assigning a Int64 value, the Decimal value is 18446744073709551615.
```

特定の言語のコンパイラがカスタム演算子をサポートする場合、独自のカスタム型でも暗黙的な変換を定義できます。 `ByteWithSign` という名前が付けられた、符号および絶対値による表現を使用する符号付きバイト データ型の実装の一部を次の例に示します。 この実装では、[Byte](xref:System.Byte) 値および [SByte](xref:System.SByte) 値から `ByteWithSign` 値への暗黙的な変換がサポートされます。

```csharp
public struct ByteWithSign
{
   private SByte signValue; 
   private Byte value;

   public static implicit operator ByteWithSign(SByte value) 
   {
      ByteWithSign newValue;
      newValue.signValue = (SByte) Math.Sign(value);
      newValue.value = (byte) Math.Abs(value);
      return newValue;
   }  

   public static implicit operator ByteWithSign(Byte value)
   {
      ByteWithSign  newValue;
      newValue.signValue = 1;
      newValue.value = value;
      return newValue;
   }

   public override string ToString()
   { 
      return (signValue * value).ToString();
   }
}
```

```vb
Public Structure ByteWithSign
   Private signValue As SByte 
   Private value As Byte

   Public Overloads Shared Widening Operator CType(value As SByte) As ByteWithSign
      Dim newValue As ByteWithSign
      newValue.signValue = CSByte(Math.Sign(value))
      newValue.value = CByte(Math.Abs(value))
      Return newValue
   End Operator  

   Public Overloads Shared Widening Operator CType(value As Byte) As ByteWithSign
      Dim NewValue As ByteWithSign
      newValue.signValue = 1
      newValue.value = value
      Return newValue
   End Operator

   Public Overrides Function ToString() As String 
      Return (signValue * value).ToString()
   End Function
End Structure
```

これにより、明示的な変換を実行したり、キャスト演算子を使用したりすることなく、クライアント コードで `ByteWithSign` 変数を宣言し、この変数に [Byte](xref:System.Byte) 値および [SByte](xref:System.SByte) 値を代入できます。この例を次に示します。

```csharp
SByte sbyteValue = -120;
ByteWithSign value = sbyteValue;
Console.WriteLine(value);
value = Byte.MaxValue;
Console.WriteLine(value);
// The example displays the following output:
//       -120
//       255
```

```vb
Dim sbyteValue As SByte = -120
Dim value As ByteWithSign = sbyteValue
Console.WriteLine(value.ToString()) 
value = Byte.MaxValue
Console.WriteLine(value.ToString()) 
' The example displays the following output:
'       -120
'       255
```

## <a name="explicit-conversion-with-the-explicit-operator"></a>Explicit 演算子を使用する明示的な変換

縮小変換では、変換後の型より範囲が広い既存の型またはメンバー リストが多い既存の型の値から新しい値が作成されます。 縮小変換ではデータ損失が発生する可能性があるため、コンパイラでは多くの場合、変換メソッドの呼び出しまたはキャスト演算子を通じて変換を明示的に行うことが要求されます。 つまり、変換は、開発者のコード内で明示的に処理する必要があります。 

> [!NOTE]
> 縮小変換で変換メソッドまたはキャスト演算子を必須とする主な目的は、コード内で処理できるように、データ損失の可能性または [OverflowException](xref:System.OverflowException) について開発者に認識してもらうことにあります。 ただし、一部のコンパイラでは、この要件が緩和されている場合もあります。 たとえば、Visual Basic で `Option Strict` がオフの場合 (既定の設定)、Visual Basic コンパイラは縮小変換を暗黙的に実行します。

たとえば、[UInt32](xref:System.UInt32)、[Int64](xref:System.Int64)、および [UInt64](xref:System.UInt64) の各データ型の範囲は、次の表に示すように、[Int32](xref:System.Int32) データ型より広くなっています。

型 | Int32 の範囲との比較
---- | ------------------------------
[Int64](xref:System.Int64) | [Int64.MaxValue](xref:System.Int64.MaxValue) が [Int32.MaxValue](xref:System.Int32#System_Int32_MaxValue) より大きく、[Int64.MinValue](xref:System.Int64.MinValue) が [Int32.MinValue](xref:System.Int32#System_Int32_MinValue) より小さく (負の値の範囲が広く) なっています。
[UInt32](xref:System.UInt32) | [UInt32.MaxValue](xref:System.UInt32.MaxValue) が [Int32.MaxValue](xref:System.Int32.MaxValue) より大きくなっています。
[UInt64](xref:System.UInt64) | [UInt64.MaxValue](xref:System.UInt64.MaxValue) が [Int32.MaxValue](xref:System.Int32.MaxValue) より大きくなっています。

このような縮小変換を処理するため、.NET では、型で `Explicit` 演算子を定義できます。 これにより、個別の言語コンパイラで独自の構文を使用してこの演算子を実装するか、または [Convert](xref:System.Convert) クラスのメンバーを呼び出して変換を実行できます  (`Convert` クラスの詳細については、このトピックの下記の「[Convert クラス](#the-convert-class)」を参照してください)。これらの範囲外の可能性がある整数値を [Int32](xref:System.Int32) 値に明示的に変換する処理を実行する言語機能の使用例を次に示します。 

```csharp
long number1 = int.MaxValue + 20L;
uint number2 = int.MaxValue - 1000;
ulong number3 = int.MaxValue;

int intNumber;

try {
   intNumber = checked((int) number1);
   Console.WriteLine("After assigning a {0} value, the Integer value is {1}.", 
                     number1.GetType().Name, intNumber); 
}
catch (OverflowException) {
   if (number1 > int.MaxValue)
      Console.WriteLine("Conversion failed: {0} exceeds {1}.", 
                        number1, int.MaxValue);
   else
      Console.WriteLine("Conversion failed: {0} is less than {1}.", 
                        number1, int.MinValue);
}

try {
   intNumber = checked((int) number2);
   Console.WriteLine("After assigning a {0} value, the Integer value is {1}.", 
                     number2.GetType().Name, intNumber); 
}
catch (OverflowException) {
   Console.WriteLine("Conversion failed: {0} exceeds {1}.", 
                     number2, int.MaxValue);
}

try {
   intNumber = checked((int) number3);
   Console.WriteLine("After assigning a {0} value, the Integer value is {1}.", 
                     number3.GetType().Name, intNumber); 
}
catch (OverflowException) {
   Console.WriteLine("Conversion failed: {0} exceeds {1}.", 
                     number1, int.MaxValue);
}

// The example displays the following output:
//    Conversion failed: 2147483667 exceeds 2147483647.
//    After assigning a UInt32 value, the Integer value is 2147482647.
//    After assigning a UInt64 value, the Integer value is 2147483647.
```

```vb
Dim number1 As Long = Integer.MaxValue + 20L
Dim number2 As UInteger = Integer.MaxValue - 1000
Dim number3 As ULong = Integer.MaxValue

Dim intNumber As Integer

Try
   intNumber = CInt(number1)
   Console.WriteLine("After assigning a {0} value, the Integer value is {1}.", 
                       number1.GetType().Name, intNumber)
Catch e As OverflowException
   If number1 > Integer.MaxValue Then
      Console.WriteLine("Conversion failed: {0} exceeds {1}.", 
                                        number1, Integer.MaxValue)
   Else
      Console.WriteLine("Conversion failed: {0} is less than {1}.\n", 
                                        number1, Integer.MinValue)
   End If
End Try

Try
   intNumber = CInt(number2)
   Console.WriteLine("After assigning a {0} value, the Integer value is {1}.", 
                       number2.GetType().Name, intNumber)
Catch e As OverflowException
   Console.WriteLine("Conversion failed: {0} exceeds {1}.", 
                                     number2, Integer.MaxValue)
End Try

Try
   intNumber = CInt(number3)
   Console.WriteLine("After assigning a {0} value, the Integer value is {1}.", 
                       number3.GetType().Name, intNumber)
Catch e As OverflowException
   Console.WriteLine("Conversion failed: {0} exceeds {1}.",
                                     number1, Integer.MaxValue)
End Try
' The example displays the following output:
'    Conversion failed: 2147483667 exceeds 2147483647.
'    After assigning a UInt32 value, the Integer value is 2147482647.
'    After assigning a UInt64 value, the Integer value is 2147483647.
```

明示的な変換で生成される結果は言語によって異なることがあり、これらの結果は対応する [Convert](xref:System.Convert) メソッドによって返される値とは異なる可能性があります。 たとえば、[Double](xref:System.Double) の値 **12.63251** を [Int32](xref:System.Int32) に変換する場合、.NET [Convert.ToInt32(Double)](xref:System.Convert.ToInt32(System.Double)) と Visual Basic `CInt` メソッドは両方とも [Double](xref:System.Double) を丸めて値 **13** を返しますが、C# の `(int)` 演算子は [Double](xref:System.Double) を切り捨てて値 **12** を返します。 同様に、C# の `(int)` 演算子はブール型から整数型への変換をサポートしませんが、Visual Basic の `CInt` メソッドは値 `true` を **-1** に変換します。 一方、[Convert.ToInt32(Boolean)](xref:System.Convert.ToInt32(System.Boolean)) メソッドは値 `true` を **1** に変換します。

ほとんどのコンパイラでは、チェックを行う形でも行わない形でも明示的な変換を実行できます。 チェックを行う変換を実行すると、変換する型の値が変換先の型の範囲外になる場合に [OverflowException](xref:System.OverflowException) がスローされます。 チェックを行わない変換を同じ条件で実行した場合、例外がスローされることがなくても、実際の動作は不定となり、結果が正しくない値になる可能性があります。

> [!NOTE]
> C# では、キャスト演算子と共に `checked` キーワードを使用するか、または `/checked+` コンパイラ オプションを指定することで、チェックを行う変換を実行できます。 反対に、チェックを行わない変換を実行する場合は、キャスト演算子と共に `unchecked` キーワードを使用するか、または `/checked-` コンパイラ オプションを指定します。 既定では、明示的な変換はチェックされません。 Visual basic では、`/removeintchecks-` コンパイラ オプションを指定することで、チェックを行う変換を実行できます。 反対に、チェックを行わない変換を実行する場合は、`/removeintchecks+` コンパイラ オプションを指定します。 既定では、明示的な変換のチェックが行われます。

次の C# の例では、`checked` キーワードと `unchecked` キーワードを使用して、[Byte](xref:System.Byte) の範囲外の値を `Byte` に変換したときの動作の違いを示しています。 チェックを行う変換では例外がスローされますが、チェックを行わない変換では [Byte.MaxValue](xref:System.Byte.MaxValue) 変数に `Byte` が代入されます。

```csharp
int largeValue = Int32.MaxValue;
byte newValue;

try {
   newValue = unchecked((byte) largeValue);
   Console.WriteLine("Converted the {0} value {1} to the {2} value {3}.", 
                     largeValue.GetType().Name, largeValue,
                     newValue.GetType().Name, newValue);
}
catch (OverflowException) {
   Console.WriteLine("{0} is outside the range of the Byte data type.", 
                     largeValue);
}

try {
   newValue = checked((byte) largeValue);
   Console.WriteLine("Converted the {0} value {1} to the {2} value {3}.", 
                     largeValue.GetType().Name, largeValue,
                     newValue.GetType().Name, newValue);
}
catch (OverflowException) {
   Console.WriteLine("{0} is outside the range of the Byte data type.", 
                     largeValue);
}
// The example displays the following output:
//    Converted the Int32 value 2147483647 to the Byte value 255.
//    2147483647 is outside the range of the Byte data type.
```

特定の言語のコンパイラで演算子のカスタム オーバーロードがサポートされている場合は、独自に作成したカスタム型の明示的な変換も定義できます。 `ByteWithSign` という名前が付けられた、符号および絶対値による表現を使用する符号付きバイト データ型の実装の一部を次の例に示します。 この実装では、[Int32](xref:System.Int32) 値および [UInt32](xref:System.UInt32) 値から `ByteWithSign` 値への明示的な変換がサポートされます。

```csharp
public struct ByteWithSign
{
   private SByte signValue; 
   private Byte value;

   private const byte MaxValue = byte.MaxValue;
   private const int MinValue = -1 * byte.MaxValue;

   public static explicit operator ByteWithSign(int value) 
   {
      // Check for overflow.
      if (value > ByteWithSign.MaxValue || value < ByteWithSign.MinValue)
         throw new OverflowException(String.Format("'{0}' is out of range of the ByteWithSign 
                                                   data type.", 
                                                   value));

      ByteWithSign newValue;
      newValue.signValue = (SByte) Math.Sign(value);
      newValue.value = (byte) Math.Abs(value);
      return newValue;
   }  

   public static explicit operator ByteWithSign(uint value)
   {
      if (value > ByteWithSign.MaxValue) 
         throw new OverflowException(String.Format("'{0}' is out of range of the ByteWithSign 
                                                   data type.", 
                                                   value));

      ByteWithSign newValue;
      newValue.signValue = 1;
      newValue.value = (byte) value;
      return newValue;
   }

   public override string ToString()
   { 
      return (signValue * value).ToString();
   }
}
```

```vb
Public Structure ByteWithSign
   Private signValue As SByte 
   Private value As Byte

   Private Const MaxValue As Byte = Byte.MaxValue
   Private Const MinValue As Integer = -1 * Byte.MaxValue

   Public Overloads Shared Narrowing Operator CType(value As Integer) As ByteWithSign
      ' Check for overflow.
      If value > ByteWithSign.MaxValue Or value < ByteWithSign.MinValue Then
         Throw New OverflowException(String.Format("'{0}' is out of range of the ByteWithSign 
                                                   data type.", value))
      End If

      Dim newValue As ByteWithSign

      newValue.signValue = CSByte(Math.Sign(value))
      newValue.value = CByte(Math.Abs(value))
      Return newValue
   End Operator

   Public Overloads Shared Narrowing Operator CType(value As UInteger) As ByteWithSign
      If value > ByteWithSign.MaxValue Then 
         Throw New OverflowException(String.Format("'{0}' is out of range of the ByteWithSign 
                                                   data type.", value))
      End If

      Dim NewValue As ByteWithSign

      newValue.signValue = 1
      newValue.value = CByte(value)
      Return newValue
   End Operator

   Public Overrides Function ToString() As String 
      Return (signValue * value).ToString()
   End Function
End Structure
```

これにより、代入処理にキャスト演算子が含まれている場合は、クライアント コードで `ByteWithSign` 変数を宣言し、この変数に [Int32](xref:System.Int32) 値および [UInt32](xref:System.UInt32) 値を代入できます。この例を次に示します。

```csharp
ByteWithSign value;

try {
   int intValue = -120;
   value = (ByteWithSign) intValue;
   Console.WriteLine(value);
}
catch (OverflowException e) {
   Console.WriteLine(e.Message);
}

try {
   uint uintValue = 1024;
   value = (ByteWithSign) uintValue;
   Console.WriteLine(value);
}
catch (OverflowException e) {
    Console.WriteLine(e.Message);
}
// The example displays the following output:
//       -120
//       '1024' is out of range of the ByteWithSign data type.
```

```vb
Dim value As ByteWithSign

Try  
   Dim intValue As Integer = -120
   value = CType(intValue, ByteWithSign)
   Console.WriteLine(value) 
Catch e As OverflowException
   Console.WriteLine(e.Message)
End Try

Try
   Dim uintValue As UInteger = 1024
   value = CType(uintValue, ByteWithSign)
   Console.WriteLine(value) 
Catch e As OverflowException
   Console.WriteLine(e.Message)
End Try
' The example displays the following output:
'       -120
'       '1024' is out of range of the ByteWithSign data type.
```

## <a name="the-iconvertible-interface"></a>IConvertible インターフェイス

任意の型から共通言語ランタイムの基本型への変換をサポートするため、.NET には [IConvertible](xref:System.IConvertible) インターフェイスが用意されています。 実装する型には、次のメソッドが必要です。

* 実装する型の [TypeCode](xref:System.TypeCode) を返すメソッド。

* 実装する型を共通言語ランタイムの各基本型 ([Boolean](xref:System.Boolean)、[Byte](xref:System.Byte)、[DateTime](xref:System.DateTime)、[Decimal](xref:System.Decimal)、[Double](xref:System.Double) など) へ変換するメソッド。

* 実装する型のインスタンスを他の特定の型へ変換する汎用的な変換メソッド。 サポートされていない変換では、[InvalidCastException](xref:System.InvalidCastException) をスローする必要があります。

共通言語ランタイムの各基本型 (つまり、[Boolean](xref:System.Boolean)、[Byte](xref:System.Byte)、[Char](xref:System.Char)、[DateTime](xref:System.DateTime)、[Decimal](xref:System.Decimal)、[Double](xref:System.Double)、[Int16](xref:System.Int16)、[Int32](xref:System.Int32)、[Int64](xref:System.Int64)、[SByte](xref:System.SByte)、[Single](xref:System.Single)、[String](xref:System.String)、[UInt16](xref:System.UInt16)、[UInt32](xref:System.UInt32)、および [UInt64](xref:System.UInt64)) と、[DBNull](xref:System.DBNull) 型および [Enum](xref:System.Enum) 型では、[IConvertible](xref:System.IConvertible) インターフェイスが実装されます。 ただし、これらは明示的なインターフェイスの実装です。次の例に示すように、変換メソッドは、[IConvertible](xref:System.IConvertible) インターフェイス変数を介してのみ呼び出すことができます。 この例では、[Int32](xref:System.Int32) 値が対応する [Char](xref:System.Char) 値に変換されます。

```csharp
int codePoint = 1067;
IConvertible iConv = codePoint;
char ch = iConv.ToChar(null);
Console.WriteLine("Converted {0} to {1}.", codePoint, ch);
```

```vb
Dim codePoint As Integer = 1067
Dim iConv As IConvertible = codePoint
Dim ch As Char = iConv.ToChar(Nothing)
Console.WriteLine("Converted {0} to {1}.", codePoint, ch)
```

実装する型ではなく、そのインターフェイス上で変換メソッドを呼び出すという要件があるため、明示的なインターフェイスの実装の負荷は相対的に大きくなります。 代わりに、[Convert](xref:System.Convert) クラスの適切なメンバーを呼び出して共通言語ランタイムの基本型間の変換を行うことをお勧めします。 詳細については、次のセクションの「[Convert クラス](#the-convert-class)」を参照してください。 

> [!NOTE]
> .NET で提供される [IConvertible](xref:System.IConvertible) インターフェイスおよび [Convert](xref:System.Convert) クラスに加えて、各言語独自の変換方法が提供されている場合もあります。 たとえば C# ではキャスト演算子が使用され、Visual Basic ではコンパイラで実装された `CType`、`CInt`、`DirectCast` などの変換関数が使用されます。

一般に、[IConvertible](xref:System.IConvertible) インターフェイスは、.NET の基本型間の変換をサポートするために設計されています。 ただし、このインターフェイスをカスタム型に実装して、その型から他のカスタム型への変換をサポートすることもできます。 詳細については、このトピックの下記の「[ChangeType メソッドを使用するカスタム変換](#custom-conversions-with-the-changetype-method)」を参照してください。

## <a name="the-convert-class"></a>Convert クラス

型変換を実行するために各基本型の [IConvertible](xref:System.IConvertible) インターフェイス実装を呼び出すこともできますが、ある基本型から他の基本型への変換では、言語に依存しない方法である [System.Convert](xref:System.Convert) クラスのメソッドの呼び出しを推奨します。 また、[Convert.ChangeType(Object, Type, IFormatProvider)](xref:System.Convert.ChangeType(System.Object,System.Type,System.IFormatProvider)) メソッドは、特定のカスタム型から他のカスタム型への変換にも使用できます。 

### <a name="conversions-between-base-types"></a>基本型どうしの変換

[Convert](xref:System.Convert) クラスは、言語に依存しない方法で基本型どうしの変換を実行し、共通言語ランタイムに対応するすべての言語で使用できます。 このクラスには、拡大と縮小の両方の変換のための一連のメソッドがすべて用意されています。また、サポートされない変換 ([DateTime](xref:System.DateTime) 値から整数値への変換など) に対しては [InvalidCastException](xref:System.InvalidCastException) がスローされます。 縮小変換は checked コンテキストで実行され、変換が失敗すると [OverflowException](xref:System.OverflowException) がスローされます。

> [!IMPORTANT]
> [Convert](xref:System.Convert) クラスには各基本型どうしの変換を実行するメソッドが含まれているため、各基本型の明示的な [IConvertible](xref:System.IConvertible) インターフェイス実装を呼び出す必要はありません。

[System.Convert](xref:System.Convert) クラスを使用して .NET 基本型どうしの拡大変換および縮小変換を実行する例をいくつか以下に示します。

```csharp
// Convert an Int32 value to a Decimal (a widening conversion).
int integralValue = 12534;
decimal decimalValue = Convert.ToDecimal(integralValue);
Console.WriteLine("Converted the {0} value {1} to " +  
                                  "the {2} value {3:N2}.", 
                                  integralValue.GetType().Name, 
                                  integralValue, 
                                  decimalValue.GetType().Name, 
                                  decimalValue);
// Convert a Byte value to an Int32 value (a widening conversion).
byte byteValue = Byte.MaxValue;
int integralValue2 = Convert.ToInt32(byteValue);                                  
Console.WriteLine("Converted the {0} value {1} to " +  
                                  "the {2} value {3:G}.", 
                                  byteValue.GetType().Name, 
                                  byteValue, 
                                  integralValue2.GetType().Name, 
                                  integralValue2);

// Convert a Double value to an Int32 value (a narrowing conversion).
double doubleValue = 16.32513e12;
try {
   long longValue = Convert.ToInt64(doubleValue);
   Console.WriteLine("Converted the {0} value {1:E} to " +  
                                     "the {2} value {3:N0}.", 
                                     doubleValue.GetType().Name, 
                                     doubleValue, 
                                     longValue.GetType().Name, 
                                     longValue);
}
catch (OverflowException) {
   Console.WriteLine("Unable to convert the {0:E} value {1}.", 
                                     doubleValue.GetType().Name, doubleValue);
}

// Convert a signed byte to a byte (a narrowing conversion).     
sbyte sbyteValue = -16;
try {
   byte byteValue2 = Convert.ToByte(sbyteValue);
   Console.WriteLine("Converted the {0} value {1} to " +  
                                     "the {2} value {3:G}.", 
                                     sbyteValue.GetType().Name, 
                                     sbyteValue, 
                                     byteValue2.GetType().Name, 
                                     byteValue2);
}
catch (OverflowException) {
   Console.WriteLine("Unable to convert the {0} value {1}.", 
                                     sbyteValue.GetType().Name, sbyteValue);
}                                         
// The example displays the following output:
//       Converted the Int32 value 12534 to the Decimal value 12,534.00.
//       Converted the Byte value 255 to the Int32 value 255.
//       Converted the Double value 1.632513E+013 to the Int64 value 16,325,130,000,000.
//       Unable to convert the SByte value -16.
```

```vb
' Convert an Int32 value to a Decimal (a widening conversion).
Dim integralValue As Integer = 12534
Dim decimalValue As Decimal = Convert.ToDecimal(integralValue)
Console.WriteLine("Converted the {0} value {1} to the {2} value {3:N2}.", 
                  integralValue.GetType().Name,
                  integralValue,
                  decimalValue.GetType().Name,
                  decimalValue)

' Convert a Byte value to an Int32 value (a widening conversion).
Dim byteValue As Byte = Byte.MaxValue
Dim integralValue2 As Integer = Convert.ToInt32(byteValue)                                  
Console.WriteLine("Converted the {0} value {1} to " + 
                                  "the {2} value {3:G}.",
                                  byteValue.GetType().Name,
                                  byteValue,
                                  integralValue2.GetType().Name,
                                  integralValue2)

' Convert a Double value to an Int32 value (a narrowing conversion).
Dim doubleValue As Double = 16.32513e12
Try
   Dim longValue As Long = Convert.ToInt64(doubleValue)
   Console.WriteLine("Converted the {0} value {1:E} to " + 
                                     "the {2} value {3:N0}.",
                                     doubleValue.GetType().Name,
                                     doubleValue,
                                     longValue.GetType().Name,
                                     longValue)
Catch e As OverflowException
   Console.WriteLine("Unable to convert the {0:E} value {1}.",
                                     doubleValue.GetType().Name, doubleValue)
End Try                                                             

' Convert a signed byte to a byte (a narrowing conversion).     
Dim sbyteValue As SByte = -16
Try
   Dim byteValue2 As Byte = Convert.ToByte(sbyteValue)
   Console.WriteLine("Converted the {0} value {1} to " + 
                                     "the {2} value {3:G}.",
                                     sbyteValue.GetType().Name,
                                     sbyteValue,
                                     byteValue2.GetType().Name,
                                     byteValue2)
Catch e As OverflowException
   Console.WriteLine("Unable to convert the {0} value {1}.",
                                     sbyteValue.GetType().Name, sbyteValue)
End Try 
' The example displays the following output:
'       Converted the Int32 value 12534 to the Decimal value 12,534.00.
'       Converted the Byte value 255 to the Int32 value 255.
'       Converted the Double value 1.632513E+013 to the Int64 value 16,325,130,000,000.
'       Unable to convert the SByte value -16.
```

特に浮動小数点値間の変換の場合など、変換によって精度が低下することがありますが、[OverflowException](xref:System.OverflowException) はスローされません。 このように精度が低下する例を次に示します。 最初の例では、[Decimal](xref:System.Decimal) 値を [Double](xref:System.Double) に変換したときに精度が低く (有効桁数が少なく) なります。 2 番目の例では、変換を完了させるために、[Double](xref:System.Double) 値の **42.72** が **43** に丸められています。

```csharp
double doubleValue; 

// Convert a Double to a Decimal.
decimal decimalValue = 13956810.96702888123451471211m;
doubleValue = Convert.ToDouble(decimalValue);
Console.WriteLine("{0} converted to {1}.", decimalValue, doubleValue);

doubleValue = 42.72;
try {
   int integerValue = Convert.ToInt32(doubleValue);
   Console.WriteLine("{0} converted to {1}.", 
                                     doubleValue, integerValue);
}
catch (OverflowException) {      
   Console.WriteLine("Unable to convert {0} to an integer.", 
                                     doubleValue);
}   
// The example displays the following output:
//       13956810.96702888123451471211 converted to 13956810.9670289.
//       42.72 converted to 43.
```

```vb
Dim doubleValue As Double 

' Convert a Double to a Decimal.
Dim decimalValue As Decimal = 13956810.96702888123451471211d
doubleValue = Convert.ToDouble(decimalValue)
Console.WriteLine("{0} converted to {1}.", decimalValue, doubleValue)

doubleValue = 42.72
Try
   Dim integerValue As Integer = Convert.ToInt32(doubleValue)
   Console.WriteLine("{0} converted to {1}.",
                                     doubleValue, integerValue)
Catch e As OverflowException
   Console.WriteLine("Unable to convert {0} to an integer.",
                                     doubleValue)
End Try   
' The example displays the following output:
'       13956810.96702888123451471211 converted to 13956810.9670289.
'       42.72 converted to 43.
```

[Convert](xref:System.Convert) クラスでサポートされる拡大と縮小の両方の変換の一覧表については、「[型変換の表](conversion-tables.md)」を参照してください。

### <a name="custom-conversions-with-the-changetype-method"></a>ChangeType メソッドを使用するカスタム変換

[Convert](xref:System.Convert) クラスは、各基本型どうしの変換をサポートするだけでなく、カスタム型を&1; つ以上の定義済みの型に変換できます。 この変換は [Convert.ChangeType(Object, Type, IFormatProvider)](xref:System.Convert.ChangeType(System.Object,System.Type,System.IFormatProvider)) メソッドによって実行されます。さらに、このメソッドが、値パラメーターの [IConvertible.ToType](xref:System.IConvertible.ToType(System.Type,System.IFormatProvider)) メソッドに対する呼び出しをラップします。 したがって、値パラメーターで表されるオブジェクトで、[IConvertible](xref:System.IConvertible) インターフェイスの実装を提供する必要があります。

> [!NOTE]
> [Convert.ChangeType(Object, Type)](xref:System.Convert.ChangeType(System.Object,System.Type)) メソッドと [Convert.ChangeType(Object, Type, IFormatProvider)](xref:System.Convert.ChangeType(System.Object,System.Type,System.IFormatProvider)) メソッドは [Type](xref:System.Type) オブジェクトを使用して値の変換後の型を指定するため、コンパイル時には型がわからないオブジェクトへの動的な変換に使用することができます。 ただし、値の [IConvertible](xref:System.IConvertible) の実装も、この変換をサポートする必要があることに注意してください。 

`TemperatureCelsius` オブジェクトから `TemperatureFahrenheit` オブジェクトへの変換およびその逆の変換を実行できる [IConvertible](xref:System.IConvertible) インターフェイスとして考えられる実装を次の例に示します。 この例では、[IConvertible](xref:System.IConvertible) インターフェイスを実装し、[Object.ToString](xref:System.Object.ToString) メソッドをオーバーライドする基本クラス `Temperature` を定義します。 派生クラスの `TemperatureCelsius` および `TemperatureFahrenheit` クラスが、基本クラスの `ToType` メソッドおよび `ToString` メソッドをそれぞれオーバーライドします。 

```csharp
using System;

public abstract class Temperature : IConvertible
{
   protected decimal temp;

   public Temperature(decimal temperature)
   {
      this.temp = temperature;
   }

   public decimal Value
   { 
      get { return this.temp; } 
      set { this.temp = Value; }        
   }

   public override string ToString()
   {
      return temp.ToString(null as IFormatProvider) + "º";
   }

   // IConvertible implementations.
   public TypeCode GetTypeCode() { 
      return TypeCode.Object;
   }   

   public bool ToBoolean(IFormatProvider provider) {
      throw new InvalidCastException(String.Format("Temperature-to-Boolean conversion is not supported."));
   }

   public byte ToByte(IFormatProvider provider) {
      if (temp < Byte.MinValue || temp > Byte.MaxValue)
         throw new OverflowException(String.Format("{0} is out of range of the Byte data type.", temp));
      else
         return (byte) temp;
   }

   public char ToChar(IFormatProvider provider) {
      throw new InvalidCastException("Temperature-to-Char conversion is not supported.");
   }

   public DateTime ToDateTime(IFormatProvider provider) {
      throw new InvalidCastException("Temperature-to-DateTime conversion is not supported.");
   }

   public decimal ToDecimal(IFormatProvider provider) {
      return temp;
   }

   public double ToDouble(IFormatProvider provider) {
      return (double) temp;
   }

   public short ToInt16(IFormatProvider provider) {
      if (temp < Int16.MinValue || temp > Int16.MaxValue)
         throw new OverflowException(String.Format("{0} is out of range of the Int16 data type.", temp));
      else
         return (short) Math.Round(temp);
   }

   public int ToInt32(IFormatProvider provider) {
      if (temp < Int32.MinValue || temp > Int32.MaxValue)
         throw new OverflowException(String.Format("{0} is out of range of the Int32 data type.", temp));
      else
         return (int) Math.Round(temp);
   }

   public long ToInt64(IFormatProvider provider) {
      if (temp < Int64.MinValue || temp > Int64.MaxValue)
         throw new OverflowException(String.Format("{0} is out of range of the Int64 data type.", temp));
      else
         return (long) Math.Round(temp);
   }

   public sbyte ToSByte(IFormatProvider provider) {
      if (temp < SByte.MinValue || temp > SByte.MaxValue)
         throw new OverflowException(String.Format("{0} is out of range of the SByte data type.", temp));
      else
         return (sbyte) temp;
   }

   public float ToSingle(IFormatProvider provider) {
      return (float) temp;
   }

   public virtual string ToString(IFormatProvider provider) {
      return temp.ToString(provider) + "°";
   }

   // If conversionType is implemented by another IConvertible method, call it.
   public virtual object ToType(Type conversionType, IFormatProvider provider) {
      switch (Type.GetTypeCode(conversionType))
      {
         case TypeCode.Boolean:
            return this.ToBoolean(provider);
         case TypeCode.Byte:
            return this.ToByte(provider);
         case TypeCode.Char:
            return this.ToChar(provider);
         case TypeCode.DateTime:
            return this.ToDateTime(provider);
         case TypeCode.Decimal:
            return this.ToDecimal(provider);
         case TypeCode.Double:
            return this.ToDouble(provider);
         case TypeCode.Empty:
            throw new NullReferenceException("The target type is null.");
         case TypeCode.Int16:
            return this.ToInt16(provider);
         case TypeCode.Int32:
            return this.ToInt32(provider);
         case TypeCode.Int64:
            return this.ToInt64(provider);
         case TypeCode.Object:
            // Leave conversion of non-base types to derived classes.
            throw new InvalidCastException(String.Format("Cannot convert from Temperature to {0}.", 
                                           conversionType.Name));
         case TypeCode.SByte:
            return this.ToSByte(provider);
         case TypeCode.Single:
            return this.ToSingle(provider);
         case TypeCode.String:
            IConvertible iconv = this;
            return iconv.ToString(provider);
         case TypeCode.UInt16:
            return this.ToUInt16(provider);
         case TypeCode.UInt32:
            return this.ToUInt32(provider);
         case TypeCode.UInt64:
            return this.ToUInt64(provider);
         default:
            throw new InvalidCastException("Conversion not supported.");
      }
   }

   public ushort ToUInt16(IFormatProvider provider) {
      if (temp < UInt16.MinValue || temp > UInt16.MaxValue)
         throw new OverflowException(String.Format("{0} is out of range of the UInt16 data type.", temp));
      else
         return (ushort) Math.Round(temp);
   }

   public uint ToUInt32(IFormatProvider provider) {
      if (temp < UInt32.MinValue || temp > UInt32.MaxValue)
         throw new OverflowException(String.Format("{0} is out of range of the UInt32 data type.", temp));
      else
         return (uint) Math.Round(temp);
   }

   public ulong ToUInt64(IFormatProvider provider) {
      if (temp < UInt64.MinValue || temp > UInt64.MaxValue)
         throw new OverflowException(String.Format("{0} is out of range of the UInt64 data type.", temp));
      else
         return (ulong) Math.Round(temp);
   }
}

public class TemperatureCelsius : Temperature, IConvertible
{
   public TemperatureCelsius(decimal value) : base(value)
   {
   }

   // Override ToString methods.
   public override string ToString()
   {
      return this.ToString(null);
   }

   public override string ToString(IFormatProvider provider)
   {
      return temp.ToString(provider) + "°C"; 
   }

   // If conversionType is a implemented by another IConvertible method, call it.
   public override object ToType(Type conversionType, IFormatProvider provider) {
      // For non-objects, call base method.
      if (Type.GetTypeCode(conversionType) != TypeCode.Object) {
         return base.ToType(conversionType, provider);
      }   
      else
      {   
         if (conversionType.Equals(typeof(TemperatureCelsius)))
            return this;
         else if (conversionType.Equals(typeof(TemperatureFahrenheit)))
            return new TemperatureFahrenheit((decimal) this.temp * 9 / 5 + 32);
         else
            throw new InvalidCastException(String.Format("Cannot convert from Temperature to {0}.", 
                                           conversionType.Name));
      }
   }
}

public class TemperatureFahrenheit : Temperature, IConvertible 
{
   public TemperatureFahrenheit(decimal value) : base(value)
   {
   }

   // Override ToString methods.
   public override string ToString()
   {
      return this.ToString(null);
   }

   public override string ToString(IFormatProvider provider)
   {
      return temp.ToString(provider) + "°F"; 
   }

   public override object ToType(Type conversionType, IFormatProvider provider)
   { 
      // For non-objects, call base methood.
      if (Type.GetTypeCode(conversionType) != TypeCode.Object) {
         return base.ToType(conversionType, provider);
      }   
      else
      {   
         // Handle conversion between derived classes.
         if (conversionType.Equals(typeof(TemperatureFahrenheit))) 
            return this;
         else if (conversionType.Equals(typeof(TemperatureCelsius)))
            return new TemperatureCelsius((decimal) (this.temp - 32) * 5 / 9);
         // Unspecified object type: throw an InvalidCastException.
         else
            throw new InvalidCastException(String.Format("Cannot convert from Temperature to {0}.", 
                                           conversionType.Name));
      }                                 
   }
}
```

```vb
Public MustInherit Class Temperature
   Implements IConvertible

   Protected temp As Decimal

   Public Sub New(temperature As Decimal)
      Me.temp = temperature
   End Sub

   Public Property Value As Decimal
      Get 
         Return Me.temp
      End Get
      Set
         Me.temp = Value
      End Set   
   End Property

   Public Overrides Function ToString() As String
      Return temp.ToString() & "º"
   End Function

   ' IConvertible implementations.
   Public Function GetTypeCode() As TypeCode Implements IConvertible.GetTypeCode
      Return TypeCode.Object
   End Function   

   Public Function ToBoolean(provider As IFormatProvider) As Boolean Implements IConvertible.ToBoolean
      Throw New InvalidCastException(String.Format("Temperature-to-Boolean conversion is not supported."))
   End Function

   Public Function ToByte(provider As IFormatProvider) As Byte Implements IConvertible.ToByte
      If temp < Byte.MinValue Or temp > Byte.MaxValue Then
         Throw New OverflowException(String.Format("{0} is out of range of the Byte data type.", temp))
      Else
         Return CByte(temp)
      End If    
   End Function

   Public Function ToChar(provider As IFormatProvider) As Char Implements IConvertible.ToChar
      Throw New InvalidCastException("Temperature-to-Char conversion is not supported.")
   End Function

   Public Function ToDateTime(provider As IFormatProvider) As DateTime Implements IConvertible.ToDateTime
      Throw New InvalidCastException("Temperature-to-DateTime conversion is not supported.")
   End Function

   Public Function ToDecimal(provider As IFormatProvider) As Decimal Implements IConvertible.ToDecimal
      Return temp
   End Function

   Public Function ToDouble(provider As IFormatProvider) As Double Implements IConvertible.ToDouble
      Return CDbl(temp)
   End Function

   Public Function ToInt16(provider As IFormatProvider) As Int16 Implements IConvertible.ToInt16
      If temp < Int16.MinValue Or temp > Int16.MaxValue Then
         Throw New OverflowException(String.Format("{0} is out of range of the Int16 data type.", temp))
      End If
      Return CShort(Math.Round(temp))
   End Function

   Public Function ToInt32(provider As IFormatProvider) As Int32 Implements IConvertible.ToInt32
      If temp < Int32.MinValue Or temp > Int32.MaxValue Then
         Throw New OverflowException(String.Format("{0} is out of range of the Int32 data type.", temp))
      End If
      Return CInt(Math.Round(temp))
   End Function

   Public Function ToInt64(provider As IFormatProvider) As Int64 Implements IConvertible.ToInt64
      If temp < Int64.MinValue Or temp > Int64.MaxValue Then
         Throw New OverflowException(String.Format("{0} is out of range of the Int64 data type.", temp))
      End If
      Return CLng(Math.Round(temp))
   End Function

   Public Function ToSByte(provider As IFormatProvider) As SByte Implements IConvertible.ToSByte
      If temp < SByte.MinValue Or temp > SByte.MaxValue Then
         Throw New OverflowException(String.Format("{0} is out of range of the SByte data type.", temp))
      Else
         Return CSByte(temp)
      End If    
   End Function

   Public Function ToSingle(provider As IFormatProvider) As Single Implements IConvertible.ToSingle
      Return CSng(temp)
   End Function

   Public Overridable Overloads Function ToString(provider As IFormatProvider) As String Implements IConvertible.ToString
      Return temp.ToString(provider) & " °C"
   End Function

   ' If conversionType is a implemented by another IConvertible method, call it.
   Public Overridable Function ToType(conversionType As Type, provider As IFormatProvider) As Object Implements IConvertible.ToType
      Select Case Type.GetTypeCode(conversionType)
         Case TypeCode.Boolean
            Return Me.ToBoolean(provider)
         Case TypeCode.Byte
            Return Me.ToByte(provider)
         Case TypeCode.Char
            Return Me.ToChar(provider)   
         Case TypeCode.DateTime
            Return Me.ToDateTime(provider)
         Case TypeCode.Decimal
            Return Me.ToDecimal(provider)
         Case TypeCode.Double
            Return Me.ToDouble(provider)
         Case TypeCode.Empty
            Throw New NullReferenceException("The target type is null.")
         Case TypeCode.Int16
            Return Me.ToInt16(provider)
         Case TypeCode.Int32
            Return Me.ToInt32(provider)
         Case TypeCode.Int64
            Return Me.ToInt64(provider)
         Case TypeCode.Object
            ' Leave conversion of non-base types to derived classes.
            Throw New InvalidCastException(String.Format("Cannot convert from Temperature to {0}.", _
                                           conversionType.Name))
         Case TypeCode.SByte
            Return Me.ToSByte(provider)
         Case TypeCode.Single
            Return Me.ToSingle(provider)
         Case TypeCode.String
            Return Me.ToString(provider)
         Case TypeCode.UInt16
            Return Me.ToUInt16(provider)
         Case TypeCode.UInt32
            Return Me.ToUInt32(provider)
         Case TypeCode.UInt64
            Return Me.ToUInt64(provider)
         Case Else
            Throw New InvalidCastException("Conversion not supported.")   
      End Select
   End Function

   Public Function ToUInt16(provider As IFormatProvider) As UInt16 Implements IConvertible.ToUInt16
      If temp < UInt16.MinValue Or temp > UInt16.MaxValue Then
         Throw New OverflowException(String.Format("{0} is out of range of the UInt16 data type.", temp))
      End If
      Return CUShort(Math.Round(temp))
   End Function

   Public Function ToUInt32(provider As IFormatProvider) As UInt32 Implements IConvertible.ToUInt32
      If temp < UInt32.MinValue Or temp > UInt32.MaxValue Then
         Throw New OverflowException(String.Format("{0} is out of range of the UInt32 data type.", temp))
      End If
      Return CUInt(Math.Round(temp))
   End Function

   Public Function ToUInt64(provider As IFormatProvider) As UInt64 Implements IConvertible.ToUInt64
      If temp < UInt64.MinValue Or temp > UInt64.MaxValue Then
         Throw New OverflowException(String.Format("{0} is out of range of the UInt64 data type.", temp))
      End If
      Return CULng(Math.Round(temp))
   End Function
End Class

Public Class TemperatureCelsius : Inherits Temperature : Implements IConvertible
   Public Sub New(value As Decimal)
      MyBase.New(value)
   End Sub

   ' Override ToString methods.
   Public Overrides Function ToString() As String
      Return Me.ToString(Nothing)
   End Function

   Public Overrides Function ToString(provider As IFormatProvider ) As String
      Return temp.ToString(provider) + "°C" 
   End Function

  ' If conversionType is a implemented by another IConvertible method, call it.
   Public Overrides Function ToType(conversionType As Type, provider As IFormatProvider) As Object
      ' For non-objects, call base method.
      If Type.GetTypeCode(conversionType) <> TypeCode.Object Then
         Return MyBase.ToType(conversionType, provider)
      Else   
         If conversionType.Equals(GetType(TemperatureCelsius)) Then
            Return Me
         ElseIf conversionType.Equals(GetType(TemperatureFahrenheit))
            Return New TemperatureFahrenheit(CDec(Me.temp * 9 / 5 + 32))
         ' Unspecified object type: throw an InvalidCastException.
         Else
            Throw New InvalidCastException(String.Format("Cannot convert from Temperature to {0}.", _ 
                                           conversionType.Name))
         End If
      End If                                  
   End Function
End Class

Public Class TemperatureFahrenheit : Inherits Temperature : Implements IConvertible
   Public Sub New(value As Decimal)
      MyBase.New(value)
   End Sub

   ' Override ToString methods.
   Public Overrides Function ToString() As String
      Return Me.ToString(Nothing)
   End Function

   Public Overrides Function ToString(provider As IFormatProvider ) As String
      Return temp.ToString(provider) + "°F" 
   End Function

   Public Overrides Function ToType(conversionType As Type, provider As IFormatProvider) As Object
      ' For non-objects, call base methood.
      If Type.GetTypeCode(conversionType) <> TypeCode.Object Then
         Return MyBase.ToType(conversionType, provider)
      Else   
         ' Handle conversion between derived classes.
         If conversionType.Equals(GetType(TemperatureFahrenheit)) Then 
            Return Me
         ElseIf conversionType.Equals(GetType(TemperatureCelsius))
            Return New TemperatureCelsius(CDec((MyBase.temp - 32) * 5 / 9))
         ' Unspecified object type: throw an InvalidCastException.
         Else
            Throw New InvalidCastException(String.Format("Cannot convert from Temperature to {0}.", _
                                           conversionType.Name))
         End If
      End If                                  
   End Function
End Class
```

これらの [IConvertible](xref:System.IConvertible) 実装を呼び出して `TemperatureCelsius` オブジェクトから `TemperatureFahrenheit` オブジェクトへの変換またはその逆の変換を実行する例をいくつか以下に示します。

```csharp
TemperatureCelsius tempC1 = new TemperatureCelsius(0);
TemperatureFahrenheit tempF1 = (TemperatureFahrenheit) Convert.ChangeType(tempC1, typeof(TemperatureFahrenheit), null);
Console.WriteLine("{0} equals {1}.", tempC1, tempF1);
TemperatureCelsius tempC2 = (TemperatureCelsius) Convert.ChangeType(tempC1, typeof(TemperatureCelsius), null);
Console.WriteLine("{0} equals {1}.", tempC1, tempC2);
TemperatureFahrenheit tempF2 = new TemperatureFahrenheit(212);
TemperatureCelsius tempC3 = (TemperatureCelsius) Convert.ChangeType(tempF2, typeof(TemperatureCelsius), null);
Console.WriteLine("{0} equals {1}.", tempF2, tempC3);
TemperatureFahrenheit tempF3 = (TemperatureFahrenheit) Convert.ChangeType(tempF2, typeof(TemperatureFahrenheit), null);
Console.WriteLine("{0} equals {1}.", tempF2, tempF3);
// The example displays the following output:
//       0°C equals 32°F.
//       0°C equals 0°C.
//       212°F equals 100°C.
//       212°F equals 212°F.
```

```vb
Dim tempC1 As New TemperatureCelsius(0)
Dim tempF1 As TemperatureFahrenheit = CType(Convert.ChangeType(tempC1, GetType(TemperatureFahrenheit), Nothing), TemperatureFahrenheit)
Console.WriteLine("{0} equals {1}.", tempC1, tempF1) 
Dim tempC2 As TemperatureCelsius = CType(Convert.ChangeType(tempC1, GetType(TemperatureCelsius), Nothing), TemperatureCelsius)
Console.WriteLine("{0} equals {1}.", tempC1, tempC2) 
Dim tempF2 As New TemperatureFahrenheit(212)
Dim tempC3 As TEmperatureCelsius = CType(Convert.ChangeType(tempF2, GEtType(TemperatureCelsius), Nothing), TemperatureCelsius)
Console.WriteLine("{0} equals {1}.", tempF2, tempC3) 
Dim tempF3 As TemperatureFahrenheit = CType(Convert.ChangeType(tempF2, GetType(TemperatureFahrenheit), Nothing), TemperatureFahrenheit)
Console.WriteLine("{0} equals {1}.", tempF2, tempF3)
' The example displays the following output:
'       0°C equals 32°F.
'       0°C equals 0°C.
'       212°F equals 100°C.
'       212°F equals 212°F.
```

## <a name="the-typeconverter-class"></a>TypeConverter クラス

.NET では、[System.ComponentModel.TypeConverter](xref:System.ComponentModel.TypeConverter) クラスを拡張し、[System.ComponentModel.TypeConverterAttribute](xref:System.ComponentModel.TypeConverterAttribute) 属性を使用して型コンバーターを型に関連付けることによって、カスタム型の型コンバーターも定義できます。 次の表に、この方法と、カスタム型に対して [IConvertible](xref:System.IConvertible) インターフェイスを実装する方法の相違点をまとめます。

> [!NOTE]
> カスタム型に対してデザイン時サポートが有効になるのは、そのカスタム型の型コンバーターが定義されている場合だけです。

TypeConverter を使用した変換 | IConvertible を使用した変換
------------------------------ | -----------------------------
[TypeConverter](xref:System.ComponentModel.TypeConverter) から独立したクラスを派生させることにより、カスタム型に実装されます。 この派生クラスは、[TypeConverterAttribute](xref:System.ComponentModel.TypeConverterAttribute) 属性を適用することにより、カスタム型と関連付けられます。 | 変換を実行するためにカスタム型によって実装されます。 その型を使用するときに、その型に対して [IConvertible](xref:System.IConvertible) 変換メソッドを呼び出します。
デザイン時と実行時に使用できます。 | 実行時だけ使用できます。
リフレクションを使用するため、[IConvertible](xref:System.IConvertible) での変換よりも処理に時間がかかります。 | リフレクションを使用しません。
カスタム型から他のデータ型への変換と、他のデータ型からカスタム型への変換という双方向の変換を実行できます。 たとえば、`MyType` に対して定義される [TypeConverter](xref:System.ComponentModel.TypeConverter) を使用することによって、`MyType` から [String](xref:System.String) への変換および [String](xref:System.String) から `MyType` への変換を実行できます。 | カスタム型から他のデータ型への変換は実行できますが、他のデータ型からカスタム型への変換は実行できません。

型コンバーターを使用した変換の詳細については、[System.ComponentModel.TypeConverter](xref:System.ComponentModel.TypeConverter) を参照してください。

## <a name="see-also"></a>関連項目

[System.Convert](xref:System.Convert)

[IConvertible](xref:System.IConvertible)

[型変換の表](conversion-tables.md)
