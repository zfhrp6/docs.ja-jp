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
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 0a774a170b7703b900c2044708b07faeb4e51548
ms.contentlocale: ja-jp
ms.lasthandoff: 03/02/2017

---

# <a name="type-conversion"></a><span data-ttu-id="ce0a7-104">型変換</span><span class="sxs-lookup"><span data-stu-id="ce0a7-104">Type conversion</span></span>

<span data-ttu-id="ce0a7-105">すべての値には関連付けられた型があり、その値に割り振られる容量、可能な値の範囲、使用できるメンバーなどの属性を定義しています。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-105">Every value has an associated type, which defines attributes such as the amount of space allocated to the value, the range of possible values it can have, and the members that it makes available.</span></span> <span data-ttu-id="ce0a7-106">多くの値は複数の型として表現できます。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-106">Many values can be expressed as more than one type.</span></span> <span data-ttu-id="ce0a7-107">たとえば、値 `4` は整数または浮動小数点数として表現できます。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-107">For example, the value `4` can be expressed as an integer or a floating-point value.</span></span> <span data-ttu-id="ce0a7-108">型変換を実行すると、変換元の型の値と等価な値が新しい型で作成されますが、それが元のオブジェクトと同一である (値が正確に一致する) とは限りません。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-108">Type conversion creates a value in a new type that is equivalent to the value of an old type, but does not necessarily preserve the identity (or exact value) of the original object.</span></span>

<span data-ttu-id="ce0a7-109">次の変換は、.NET によって自動的にサポートされます。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-109">.NET automatically supports the following conversions:</span></span>

* <span data-ttu-id="ce0a7-110">派生クラスから基底クラスへの変換。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-110">Conversion from a derived class to a base class.</span></span> <span data-ttu-id="ce0a7-111">これは、たとえば、任意のクラスまたは構造体のインスタンスを[オブジェクト](xref:System.Object) インスタンスに変換できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-111">This means, for example, that an instance of any class or structure can be converted to an [Object](xref:System.Object) instance.</span></span> <span data-ttu-id="ce0a7-112">この変換では、キャスト演算子は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-112">This conversion does not require a casting operator.</span></span>

* <span data-ttu-id="ce0a7-113">基本クラスから元の派生クラスへの変換。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-113">Conversion from a base class back to the original derived class.</span></span> <span data-ttu-id="ce0a7-114">C# の場合、この変換ではキャスト演算子が必要です。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-114">In C#, this conversion requires a casting operator.</span></span> <span data-ttu-id="ce0a7-115">Visual Basic では、`Option Strict` がオンの場合、`CType` 演算子が必要です。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-115">In Visual Basic, it requires the `CType` operator if `Option Strict` is on.</span></span> 

* <span data-ttu-id="ce0a7-116">インターフェイスを実装する型から、そのインターフェイスを表すインターフェイス オブジェクトへの変換。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-116">Conversion from a type that implements an interface to an interface object that represents that interface.</span></span> <span data-ttu-id="ce0a7-117">この変換では、キャスト演算子は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-117">This conversion does not require a casting operator.</span></span>

* <span data-ttu-id="ce0a7-118">インターフェイス オブジェクトから、そのインターフェイスを実装する元の型への変換。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-118">Conversion from an interface object back to the original type that implements that interface.</span></span> <span data-ttu-id="ce0a7-119">C# の場合、この変換ではキャスト演算子が必要です。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-119">In C#, this conversion requires a casting operator.</span></span> <span data-ttu-id="ce0a7-120">Visual Basic では、`Option Strict` がオンの場合、`CType` 演算子が必要です。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-120">In Visual Basic, it requires the `CType` operator if `Option Strict` is on.</span></span> 

<span data-ttu-id="ce0a7-121">これらの自動変換に加えて、.NET ではカスタムの型変換をサポートするいくつかの機能を提供しています。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-121">In addition to these automatic conversions, .NET provides several features that support custom type conversion.</span></span> <span data-ttu-id="ce0a7-122">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-122">These include the following:</span></span> 

* <span data-ttu-id="ce0a7-123">`Implicit` 演算子。型の間で使用できる拡大変換を定義します。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-123">The `Implicit` operator, which defines the available widening conversions between types.</span></span> <span data-ttu-id="ce0a7-124">詳細については、「[Implicit 演算子を使用する暗黙的な変換](#implicit-conversion-with-the-implicit-operator)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-124">For more information, see the [Implicit conversion with the Implicit operator](#implicit-conversion-with-the-implicit-operator) section.</span></span>

* <span data-ttu-id="ce0a7-125">`Explicit` 演算子。型の間で使用できる縮小変換を定義します。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-125">The `Explicit` operator, which defines the available narrowing conversions between types.</span></span> <span data-ttu-id="ce0a7-126">詳細については、「[Explicit 演算子を使用する明示的な変換](#explicit-conversion-with-the-explicit-operator)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-126">For more information, see the [Explicit conversion with the Explicit operator](#explicit-conversion-with-the-explicit-operator) section.</span></span>

* <span data-ttu-id="ce0a7-127">[IConvertible](xref:System.IConvertible) インターフェイス。.NET の各基本データ型への変換を定義します。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-127">The [IConvertible](xref:System.IConvertible) interface, which defines conversions to each of the base .NET data types.</span></span> <span data-ttu-id="ce0a7-128">詳細については、「[IConvertible インターフェイス](#the-iconvertible-interface)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-128">For more information, see the [The IConvertible interface](#the-iconvertible-interface) section.</span></span>

* <span data-ttu-id="ce0a7-129">[Convert](xref:System.Convert) クラス。`IConvertible` インターフェイスにメソッドを実装する一連のメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-129">The [Convert](xref:System.Convert) class, which provides a set of methods that implement the methods in the `IConvertible` interface.</span></span> <span data-ttu-id="ce0a7-130">詳細については、「[Convert クラス](#the-convert-class)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-130">For more information, see the [The Convert class](#the-convert-class) section.</span></span>

* <span data-ttu-id="ce0a7-131">[TypeConverter](xref:System.ComponentModel.TypeConverter) クラス。指定された型から他の型への変換をサポートするように拡張できる基本クラスです。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-131">The [TypeConverter](xref:System.ComponentModel.TypeConverter) class, which is a base class that can be extended to support the conversion of a specified type to any other type.</span></span> <span data-ttu-id="ce0a7-132">詳細については、「[TypeConverter クラス](#the-typeconverter-class)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-132">For more information, see the [The TypeConverter class](#the-typeconverter-class) section.</span></span>

## <a name="implicit-conversion-with-the-implicit-operator"></a><span data-ttu-id="ce0a7-133">Implicit 演算子を使用する暗黙的な変換</span><span class="sxs-lookup"><span data-stu-id="ce0a7-133">Implicit conversion with the Implicit operator</span></span>

<span data-ttu-id="ce0a7-134">拡大変換では、変換後の型より範囲の制限が厳しい既存の型またはメンバー リストが制限されている既存の型の値から新しい値が作成されます。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-134">Widening conversions involve the creation of a new value from the value of an existing type that has either a more restrictive range or a more restricted member list than the target type.</span></span> <span data-ttu-id="ce0a7-135">拡大変換でデータ損失が発生することはありません (ただし、精度が失われることはあります)。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-135">Widening conversions cannot result in data loss (although they may result in a loss of precision).</span></span> <span data-ttu-id="ce0a7-136">データが失われないため、コンパイラは明示的な変換メソッドまたはキャスト演算子を使用するように要求する必要がなく、暗黙的または透過的に変換を処理できます。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-136">Because data cannot be lost, compilers can handle the conversion implicitly or transparently, without requiring the use of an explicit conversion method or a casting operator.</span></span>

> [!NOTE]
> <span data-ttu-id="ce0a7-137">暗黙的な変換を実行するコードで変換メソッドを呼び出したり、キャスト演算子を使用したりすることはできますが、暗黙的な変換がサポートされるコンパイラでは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-137">Although code that performs an implicit conversion can call a conversion method or use a casting operator, their use is not required by compilers that support implicit conversions.</span></span>

<span data-ttu-id="ce0a7-138">たとえば、[Decimal](xref:System.Decimal) 型では、[Byte](xref:System.Byte)、[Char](xref:System.Char)、[Int16](xref:System.Int16)、[Int32](xref:System.Int32)、[Int64](xref:System.Int64)、[SByte](xref:System.SByte)、[UInt16](xref:System.UInt16)、[UInt32](xref:System.UInt32)、および [UInt64](xref:System.UInt64) の各値からの暗黙的な変換がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-138">For example, the [Decimal](xref:System.Decimal) type supports implicit conversions from [Byte](xref:System.Byte), [Char](xref:System.Char), [Int16](xref:System.Int16), [Int32](xref:System.Int32), [Int64](xref:System.Int64), [SByte](xref:System.SByte), [UInt16](xref:System.UInt16), [UInt32](xref:System.UInt32), and [UInt64](xref:System.UInt64) values.</span></span> <span data-ttu-id="ce0a7-139">`Decimal` 変数への値の代入時に、これらの暗黙的な変換の一部が実行される例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-139">The following example illustrates some of these implicit conversions in assigning values to a `Decimal` variable.</span></span>

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

<span data-ttu-id="ce0a7-140">特定の言語のコンパイラがカスタム演算子をサポートする場合、独自のカスタム型でも暗黙的な変換を定義できます。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-140">If a particular language compiler supports custom operators, you can also define implicit conversions in your own custom types.</span></span> <span data-ttu-id="ce0a7-141">`ByteWithSign` という名前が付けられた、符号および絶対値による表現を使用する符号付きバイト データ型の実装の一部を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-141">The following example provides a partial implementation of a signed byte data type named `ByteWithSign` that uses sign-and-magnitude representation.</span></span> <span data-ttu-id="ce0a7-142">この実装では、[Byte](xref:System.Byte) 値および [SByte](xref:System.SByte) 値から `ByteWithSign` 値への暗黙的な変換がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-142">It supports implicit conversion of [Byte](xref:System.Byte) and [SByte](xref:System.SByte) values to `ByteWithSign` values.</span></span>

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

<span data-ttu-id="ce0a7-143">これにより、明示的な変換を実行したり、キャスト演算子を使用したりすることなく、クライアント コードで `ByteWithSign` 変数を宣言し、この変数に [Byte](xref:System.Byte) 値および [SByte](xref:System.SByte) 値を代入できます。この例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-143">Client code can then declare a `ByteWithSign` variable and assign it [Byte](xref:System.Byte) and [SByte](xref:System.SByte) values without performing any explicit conversions or using any casting operators, as the following example shows.</span></span>

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

## <a name="explicit-conversion-with-the-explicit-operator"></a><span data-ttu-id="ce0a7-144">Explicit 演算子を使用する明示的な変換</span><span class="sxs-lookup"><span data-stu-id="ce0a7-144">Explicit conversion with the Explicit operator</span></span>

<span data-ttu-id="ce0a7-145">縮小変換では、変換後の型より範囲が広い既存の型またはメンバー リストが多い既存の型の値から新しい値が作成されます。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-145">Narrowing conversions involve the creation of a new value from the value of an existing type that has either a greater range or a larger member list than the target type.</span></span> <span data-ttu-id="ce0a7-146">縮小変換ではデータ損失が発生する可能性があるため、コンパイラでは多くの場合、変換メソッドの呼び出しまたはキャスト演算子を通じて変換を明示的に行うことが要求されます。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-146">Because a narrowing conversion can result in a loss of data, compilers often require that the conversion be made explicit through a call to a conversion method or a casting operator.</span></span> <span data-ttu-id="ce0a7-147">つまり、変換は、開発者のコード内で明示的に処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-147">That is, the conversion must be handled explicitly in developer code.</span></span> 

> [!NOTE]
> <span data-ttu-id="ce0a7-148">縮小変換で変換メソッドまたはキャスト演算子を必須とする主な目的は、コード内で処理できるように、データ損失の可能性または [OverflowException](xref:System.OverflowException) について開発者に認識してもらうことにあります。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-148">The major purpose of requiring a conversion method or casting operator for narrowing conversions is to make the developer aware of the possibility of data loss or an [OverflowException](xref:System.OverflowException) so that it can be handled in code.</span></span> <span data-ttu-id="ce0a7-149">ただし、一部のコンパイラでは、この要件が緩和されている場合もあります。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-149">However, some compilers can relax this requirement.</span></span> <span data-ttu-id="ce0a7-150">たとえば、Visual Basic で `Option Strict` がオフの場合 (既定の設定)、Visual Basic コンパイラは縮小変換を暗黙的に実行します。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-150">For example, in Visual Basic, if `Option Strict` is off (its default setting), the Visual Basic compiler tries to perform narrowing conversions implicitly.</span></span>

<span data-ttu-id="ce0a7-151">たとえば、[UInt32](xref:System.UInt32)、[Int64](xref:System.Int64)、および [UInt64](xref:System.UInt64) の各データ型の範囲は、次の表に示すように、[Int32](xref:System.Int32) データ型より広くなっています。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-151">For example, the [UInt32](xref:System.UInt32), [Int64](xref:System.Int64), and [UInt64](xref:System.UInt64) data types have ranges that exceed that the [Int32](xref:System.Int32) data type, as the following table shows.</span></span>

<span data-ttu-id="ce0a7-152">型</span><span class="sxs-lookup"><span data-stu-id="ce0a7-152">Type</span></span> | <span data-ttu-id="ce0a7-153">Int32 の範囲との比較</span><span class="sxs-lookup"><span data-stu-id="ce0a7-153">Comparison with range of Int32</span></span>
---- | ------------------------------
[<span data-ttu-id="ce0a7-154">Int64</span><span class="sxs-lookup"><span data-stu-id="ce0a7-154">Int64</span></span>](xref:System.Int64) | <span data-ttu-id="ce0a7-155">[Int64.MaxValue](xref:System.Int64.MaxValue) が [Int32.MaxValue](xref:System.Int32#System_Int32_MaxValue) より大きく、[Int64.MinValue](xref:System.Int64.MinValue) が [Int32.MinValue](xref:System.Int32#System_Int32_MinValue) より小さく (負の値の範囲が広く) なっています。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-155">[Int64.MaxValue](xref:System.Int64.MaxValue) is greater than [Int32.MaxValue](xref:System.Int32#System_Int32_MaxValue), and [Int64.MinValue](xref:System.Int64.MinValue) is less than (has a greater negative range than) [Int32.MinValue](xref:System.Int32#System_Int32_MinValue).</span></span>
[<span data-ttu-id="ce0a7-156">UInt32</span><span class="sxs-lookup"><span data-stu-id="ce0a7-156">UInt32</span></span>](xref:System.UInt32) | <span data-ttu-id="ce0a7-157">[UInt32.MaxValue](xref:System.UInt32.MaxValue) が [Int32.MaxValue](xref:System.Int32.MaxValue) より大きくなっています。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-157">[UInt32.MaxValue](xref:System.UInt32.MaxValue) is greater than [Int32.MaxValue](xref:System.Int32.MaxValue).</span></span>
[<span data-ttu-id="ce0a7-158">UInt64</span><span class="sxs-lookup"><span data-stu-id="ce0a7-158">UInt64</span></span>](xref:System.UInt64) | <span data-ttu-id="ce0a7-159">[UInt64.MaxValue](xref:System.UInt64.MaxValue) が [Int32.MaxValue](xref:System.Int32.MaxValue) より大きくなっています。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-159">[UInt64.MaxValue](xref:System.UInt64.MaxValue) is greater than [Int32.MaxValue](xref:System.Int32.MaxValue).</span></span>

<span data-ttu-id="ce0a7-160">このような縮小変換を処理するため、.NET では、型で `Explicit` 演算子を定義できます。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-160">To handle such narrowing conversions, .NET allows types to define an `Explicit` operator.</span></span> <span data-ttu-id="ce0a7-161">これにより、個別の言語コンパイラで独自の構文を使用してこの演算子を実装するか、または [Convert](xref:System.Convert) クラスのメンバーを呼び出して変換を実行できます </span><span class="sxs-lookup"><span data-stu-id="ce0a7-161">Individual language compilers can then implement this operator using their own syntax, or a member of the [Convert](xref:System.Convert) class can be called to perform the conversion.</span></span> <span data-ttu-id="ce0a7-162">(`Convert` クラスの詳細については、このトピックの下記の「[Convert クラス](#the-convert-class)」を参照してください)。これらの範囲外の可能性がある整数値を [Int32](xref:System.Int32) 値に明示的に変換する処理を実行する言語機能の使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-162">(For more information about the `Convert` class, see [The Convert class](#the-convert-class) later in this topic.) The following example illustrates the use of language features to handle the explicit conversion of these potentially out-of-range integer values to [Int32](xref:System.Int32) values.</span></span> 

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

<span data-ttu-id="ce0a7-163">明示的な変換で生成される結果は言語によって異なることがあり、これらの結果は対応する [Convert](xref:System.Convert) メソッドによって返される値とは異なる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-163">Explicit conversions can produce different results in different languages, and these results can differ from the value returned by the corresponding [Convert](xref:System.Convert) method.</span></span> <span data-ttu-id="ce0a7-164">たとえば、[Double](xref:System.Double) の値 **12.63251** を [Int32](xref:System.Int32) に変換する場合、.NET [Convert.ToInt32(Double)](xref:System.Convert.ToInt32(System.Double)) と Visual Basic `CInt` メソッドは両方とも [Double](xref:System.Double) を丸めて値 **13** を返しますが、C# の `(int)` 演算子は [Double](xref:System.Double) を切り捨てて値 **12** を返します。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-164">For example, if the [Double](xref:System.Double) value **12.63251** is converted to an [Int32](xref:System.Int32), both the .NET [Convert.ToInt32(Double)](xref:System.Convert.ToInt32(System.Double)) and the Visual Basic `CInt` method method rounds the [Double](xref:System.Double) to return a value of **13**, but the C# `(int)` operator truncates the [Double](xref:System.Double) to return a value of **12**.</span></span> <span data-ttu-id="ce0a7-165">同様に、C# の `(int)` 演算子はブール型から整数型への変換をサポートしませんが、Visual Basic の `CInt` メソッドは値 `true` を **-1** に変換します。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-165">Similarly, the C# `(int)` operator does not support Boolean-to-integer conversion, but the Visual Basic `CInt` method converts a value of `true` to **-1**.</span></span> <span data-ttu-id="ce0a7-166">一方、[Convert.ToInt32(Boolean)](xref:System.Convert.ToInt32(System.Boolean)) メソッドは値 `true` を **1** に変換します。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-166">On the other hand, the [Convert.ToInt32(Boolean)](xref:System.Convert.ToInt32(System.Boolean)) method converts a value of `true` to **1**.</span></span>

<span data-ttu-id="ce0a7-167">ほとんどのコンパイラでは、チェックを行う形でも行わない形でも明示的な変換を実行できます。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-167">Most compilers allow explicit conversions to be performed in a checked or unchecked manner.</span></span> <span data-ttu-id="ce0a7-168">チェックを行う変換を実行すると、変換する型の値が変換先の型の範囲外になる場合に [OverflowException](xref:System.OverflowException) がスローされます。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-168">When a checked conversion is performed, an [OverflowException](xref:System.OverflowException) is thrown when the value of the type to be converted is outside the range of the target type.</span></span> <span data-ttu-id="ce0a7-169">チェックを行わない変換を同じ条件で実行した場合、例外がスローされることがなくても、実際の動作は不定となり、結果が正しくない値になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-169">When an unchecked conversion is performed under the same conditions, the conversion might not throw an exception, but the exact behavior becomes undefined and an incorrect value might result.</span></span>

> [!NOTE]
> <span data-ttu-id="ce0a7-170">C# では、キャスト演算子と共に `checked` キーワードを使用するか、または `/checked+` コンパイラ オプションを指定することで、チェックを行う変換を実行できます。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-170">In C#, checked conversions can be performed by using the `checked` keyword together with a casting operator, or by specifying the `/checked+` compiler option.</span></span> <span data-ttu-id="ce0a7-171">反対に、チェックを行わない変換を実行する場合は、キャスト演算子と共に `unchecked` キーワードを使用するか、または `/checked-` コンパイラ オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-171">Conversely, unchecked conversions can be performed by using the `unchecked` keyword together with the casting operator, or by specifying the `/checked-` compiler option.</span></span> <span data-ttu-id="ce0a7-172">既定では、明示的な変換はチェックされません。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-172">By default, explicit conversions are unchecked.</span></span> <span data-ttu-id="ce0a7-173">Visual basic では、`/removeintchecks-` コンパイラ オプションを指定することで、チェックを行う変換を実行できます。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-173">In Visual Basic, checked conversions can be performed by specifying the `/removeintchecks-` compiler option.</span></span> <span data-ttu-id="ce0a7-174">反対に、チェックを行わない変換を実行する場合は、`/removeintchecks+` コンパイラ オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-174">Conversely, unchecked conversions can be performed by specifying the `/removeintchecks+` compiler option.</span></span> <span data-ttu-id="ce0a7-175">既定では、明示的な変換のチェックが行われます。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-175">By default, explicit conversions are checked.</span></span>

<span data-ttu-id="ce0a7-176">次の C# の例では、`checked` キーワードと `unchecked` キーワードを使用して、[Byte](xref:System.Byte) の範囲外の値を `Byte` に変換したときの動作の違いを示しています。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-176">The following C# example uses the `checked` and `unchecked` keywords to illustrate the difference in behavior when a value outside the range of a [Byte](xref:System.Byte) is converted to a `Byte`.</span></span> <span data-ttu-id="ce0a7-177">チェックを行う変換では例外がスローされますが、チェックを行わない変換では [Byte.MaxValue](xref:System.Byte.MaxValue) 変数に `Byte` が代入されます。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-177">The checked conversion throws an exception, but the unchecked conversion assigns [Byte.MaxValue](xref:System.Byte.MaxValue) to the `Byte` variable.</span></span>

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

<span data-ttu-id="ce0a7-178">特定の言語のコンパイラで演算子のカスタム オーバーロードがサポートされている場合は、独自に作成したカスタム型の明示的な変換も定義できます。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-178">If a particular language compiler supports custom overloaded operators, you can also define explicit conversions in your own custom types.</span></span> <span data-ttu-id="ce0a7-179">`ByteWithSign` という名前が付けられた、符号および絶対値による表現を使用する符号付きバイト データ型の実装の一部を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-179">The following example provides a partial implementation of a signed byte data type named `ByteWithSign` that uses sign-and-magnitude representation.</span></span> <span data-ttu-id="ce0a7-180">この実装では、[Int32](xref:System.Int32) 値および [UInt32](xref:System.UInt32) 値から `ByteWithSign` 値への明示的な変換がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-180">It supports explicit conversion of [Int32](xref:System.Int32) and [UInt32](xref:System.UInt32) values to `ByteWithSign` values.</span></span>

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

<span data-ttu-id="ce0a7-181">これにより、代入処理にキャスト演算子が含まれている場合は、クライアント コードで `ByteWithSign` 変数を宣言し、この変数に [Int32](xref:System.Int32) 値および [UInt32](xref:System.UInt32) 値を代入できます。この例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-181">Client code can then declare a `ByteWithSign` variable and assign it [Int32](xref:System.Int32) and [UInt32](xref:System.UInt32) values if the assignments include a casting operator, as the following example shows.</span></span>

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

## <a name="the-iconvertible-interface"></a><span data-ttu-id="ce0a7-182">IConvertible インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ce0a7-182">The IConvertible interface</span></span>

<span data-ttu-id="ce0a7-183">任意の型から共通言語ランタイムの基本型への変換をサポートするため、.NET には [IConvertible](xref:System.IConvertible) インターフェイスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-183">To support the conversion of any type to a common language runtime base type, .NET provides the [IConvertible](xref:System.IConvertible) interface.</span></span> <span data-ttu-id="ce0a7-184">実装する型には、次のメソッドが必要です。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-184">The implementing type is required to provide the following:</span></span>

* <span data-ttu-id="ce0a7-185">実装する型の [TypeCode](xref:System.TypeCode) を返すメソッド。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-185">A method that returns the [TypeCode](xref:System.TypeCode) of the implementing type.</span></span>

* <span data-ttu-id="ce0a7-186">実装する型を共通言語ランタイムの各基本型 ([Boolean](xref:System.Boolean)、[Byte](xref:System.Byte)、[DateTime](xref:System.DateTime)、[Decimal](xref:System.Decimal)、[Double](xref:System.Double) など) へ変換するメソッド。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-186">Methods to convert the implementing type to each common language runtime base type ([Boolean](xref:System.Boolean), [Byte](xref:System.Byte), [DateTime](xref:System.DateTime), [Decimal](xref:System.Decimal), [Double](xref:System.Double), and so on).</span></span>

* <span data-ttu-id="ce0a7-187">実装する型のインスタンスを他の特定の型へ変換する汎用的な変換メソッド。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-187">A generalized conversion method to convert an instance of the implementing type to another specified type.</span></span> <span data-ttu-id="ce0a7-188">サポートされていない変換では、[InvalidCastException](xref:System.InvalidCastException) をスローする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-188">Conversions that are not supported should throw an [InvalidCastException](xref:System.InvalidCastException).</span></span>

<span data-ttu-id="ce0a7-189">共通言語ランタイムの各基本型 (つまり、[Boolean](xref:System.Boolean)、[Byte](xref:System.Byte)、[Char](xref:System.Char)、[DateTime](xref:System.DateTime)、[Decimal](xref:System.Decimal)、[Double](xref:System.Double)、[Int16](xref:System.Int16)、[Int32](xref:System.Int32)、[Int64](xref:System.Int64)、[SByte](xref:System.SByte)、[Single](xref:System.Single)、[String](xref:System.String)、[UInt16](xref:System.UInt16)、[UInt32](xref:System.UInt32)、および [UInt64](xref:System.UInt64)) と、[DBNull](xref:System.DBNull) 型および [Enum](xref:System.Enum) 型では、[IConvertible](xref:System.IConvertible) インターフェイスが実装されます。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-189">Each common language runtime base type (that is, the [Boolean](xref:System.Boolean), [Byte](xref:System.Byte), [Char](xref:System.Char), [DateTime](xref:System.DateTime), [Decimal](xref:System.Decimal), [Double](xref:System.Double), [Int16](xref:System.Int16), [Int32](xref:System.Int32), [Int64](xref:System.Int64), [SByte](xref:System.SByte), [Single](xref:System.Single), [String](xref:System.String), [UInt16](xref:System.UInt16), [UInt32](xref:System.UInt32), and [UInt64](xref:System.UInt64), as well as the [DBNull](xref:System.DBNull) and [Enum](xref:System.Enum) types, implement the [IConvertible](xref:System.IConvertible) interface.</span></span> <span data-ttu-id="ce0a7-190">ただし、これらは明示的なインターフェイスの実装です。次の例に示すように、変換メソッドは、[IConvertible](xref:System.IConvertible) インターフェイス変数を介してのみ呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-190">However, these are explicit interface implementations; the conversion method can be called only through an [IConvertible](xref:System.IConvertible) interface variable, as the following example shows.</span></span> <span data-ttu-id="ce0a7-191">この例では、[Int32](xref:System.Int32) 値が対応する [Char](xref:System.Char) 値に変換されます。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-191">This example converts an [Int32](xref:System.Int32) value to its equivalent [Char](xref:System.Char) value.</span></span>

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

<span data-ttu-id="ce0a7-192">実装する型ではなく、そのインターフェイス上で変換メソッドを呼び出すという要件があるため、明示的なインターフェイスの実装の負荷は相対的に大きくなります。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-192">The requirement to call the conversion method on its interface rather than on the implementing type makes explicit interface implementations relatively expensive.</span></span> <span data-ttu-id="ce0a7-193">代わりに、[Convert](xref:System.Convert) クラスの適切なメンバーを呼び出して共通言語ランタイムの基本型間の変換を行うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-193">Instead, we recommend that you call the appropriate member of the [Convert](xref:System.Convert) class to convert between common language runtime base types.</span></span> <span data-ttu-id="ce0a7-194">詳細については、次のセクションの「[Convert クラス](#the-convert-class)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-194">For more information, see the next section, [The Convert class](#the-convert-class).</span></span> 

> [!NOTE]
> <span data-ttu-id="ce0a7-195">.NET で提供される [IConvertible](xref:System.IConvertible) インターフェイスおよび [Convert](xref:System.Convert) クラスに加えて、各言語独自の変換方法が提供されている場合もあります。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-195">In addition to the [IConvertible](xref:System.IConvertible) interface and the [Convert](xref:System.Convert) class provided by .NET, individual languages may also provide ways to perform conversions.</span></span> <span data-ttu-id="ce0a7-196">たとえば C# ではキャスト演算子が使用され、Visual Basic ではコンパイラで実装された `CType`、`CInt`、`DirectCast` などの変換関数が使用されます。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-196">For example, C# uses casting operators; Visual Basic uses compiler-implemented conversion functions such as `CType`, `CInt`, and `DirectCast`.</span></span>

<span data-ttu-id="ce0a7-197">一般に、[IConvertible](xref:System.IConvertible) インターフェイスは、.NET の基本型間の変換をサポートするために設計されています。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-197">For the most part, the [IConvertible](xref:System.IConvertible) interface is designed to support conversion between the base types in .NET.</span></span> <span data-ttu-id="ce0a7-198">ただし、このインターフェイスをカスタム型に実装して、その型から他のカスタム型への変換をサポートすることもできます。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-198">However, the interface can also be implemented by a custom type to support conversion of that type to other custom types.</span></span> <span data-ttu-id="ce0a7-199">詳細については、このトピックの下記の「[ChangeType メソッドを使用するカスタム変換](#custom-conversions-with-the-changetype-method)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-199">For more information, see the section [Custom conversions with the ChangeType method](#custom-conversions-with-the-changetype-method) later in this topic.</span></span>

## <a name="the-convert-class"></a><span data-ttu-id="ce0a7-200">Convert クラス</span><span class="sxs-lookup"><span data-stu-id="ce0a7-200">The Convert class</span></span>

<span data-ttu-id="ce0a7-201">型変換を実行するために各基本型の [IConvertible](xref:System.IConvertible) インターフェイス実装を呼び出すこともできますが、ある基本型から他の基本型への変換では、言語に依存しない方法である [System.Convert](xref:System.Convert) クラスのメソッドの呼び出しを推奨します。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-201">Although each base type's [IConvertible](xref:System.IConvertible) interface implementation can be called to perform a type conversion, calling the methods of the [System.Convert](xref:System.Convert) class is the recommended language-neutral way to convert from one base type to another.</span></span> <span data-ttu-id="ce0a7-202">また、[Convert.ChangeType(Object, Type, IFormatProvider)](xref:System.Convert.ChangeType(System.Object,System.Type,System.IFormatProvider)) メソッドは、特定のカスタム型から他のカスタム型への変換にも使用できます。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-202">In addition, the [Convert.ChangeType(Object, Type, IFormatProvider)](xref:System.Convert.ChangeType(System.Object,System.Type,System.IFormatProvider)) method can be used to convert from a specified custom type to another type.</span></span> 

### <a name="conversions-between-base-types"></a><span data-ttu-id="ce0a7-203">基本型どうしの変換</span><span class="sxs-lookup"><span data-stu-id="ce0a7-203">Conversions between base types</span></span>

<span data-ttu-id="ce0a7-204">[Convert](xref:System.Convert) クラスは、言語に依存しない方法で基本型どうしの変換を実行し、共通言語ランタイムに対応するすべての言語で使用できます。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-204">The [Convert](xref:System.Convert) class provides a language-neutral way to perform conversions between base types and is available to all languages that target the common language runtime.</span></span> <span data-ttu-id="ce0a7-205">このクラスには、拡大と縮小の両方の変換のための一連のメソッドがすべて用意されています。また、サポートされない変換 ([DateTime](xref:System.DateTime) 値から整数値への変換など) に対しては [InvalidCastException](xref:System.InvalidCastException) がスローされます。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-205">It provides a complete set of methods for both widening and narrowing conversions, and throws an [InvalidCastException](xref:System.InvalidCastException) for conversions that are not supported (such as the conversion of a [DateTime](xref:System.DateTime) value to an integer value).</span></span> <span data-ttu-id="ce0a7-206">縮小変換は checked コンテキストで実行され、変換が失敗すると [OverflowException](xref:System.OverflowException) がスローされます。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-206">Narrowing conversions are performed in a checked context, and an [OverflowException](xref:System.OverflowException) is thrown if the conversion fails.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ce0a7-207">[Convert](xref:System.Convert) クラスには各基本型どうしの変換を実行するメソッドが含まれているため、各基本型の明示的な [IConvertible](xref:System.IConvertible) インターフェイス実装を呼び出す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-207">Because the [Convert](xref:System.Convert) class includes methods to convert to and from each base type, it eliminates the need to call each base type's [IConvertible](xref:System.IConvertible) explicit interface implementation.</span></span>

<span data-ttu-id="ce0a7-208">[System.Convert](xref:System.Convert) クラスを使用して .NET 基本型どうしの拡大変換および縮小変換を実行する例をいくつか以下に示します。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-208">The following example illustrates the use of the [System.Convert](xref:System.Convert) class to perform several widening and narrowing conversions between .NET base types.</span></span>

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

<span data-ttu-id="ce0a7-209">特に浮動小数点値間の変換の場合など、変換によって精度が低下することがありますが、[OverflowException](xref:System.OverflowException) はスローされません。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-209">In some cases, particularly when converting to and from floating-point values, a conversion may involve a loss of precision, even though it does not throw an [OverflowException](xref:System.OverflowException).</span></span> <span data-ttu-id="ce0a7-210">このように精度が低下する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-210">The following example illustrates this loss of precision.</span></span> <span data-ttu-id="ce0a7-211">最初の例では、[Decimal](xref:System.Decimal) 値を [Double](xref:System.Double) に変換したときに精度が低く (有効桁数が少なく) なります。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-211">In the first case, a [Decimal](xref:System.Decimal) value has less precision (fewer significant digits) when it is converted to a [Double](xref:System.Double).</span></span> <span data-ttu-id="ce0a7-212">2 番目の例では、変換を完了させるために、[Double](xref:System.Double) 値の **42.72** が **43** に丸められています。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-212">In the second case, a [Double](xref:System.Double) value is rounded from **42.72** to **43** in order to complete the conversion.</span></span>

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

<span data-ttu-id="ce0a7-213">[Convert](xref:System.Convert) クラスでサポートされる拡大と縮小の両方の変換の一覧表については、「[型変換の表](conversion-tables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-213">For a table that lists both the widening and narrowing conversions supported by the [Convert](xref:System.Convert) class, see [Type conversion tables](conversion-tables.md).</span></span>

### <a name="custom-conversions-with-the-changetype-method"></a><span data-ttu-id="ce0a7-214">ChangeType メソッドを使用するカスタム変換</span><span class="sxs-lookup"><span data-stu-id="ce0a7-214">Custom conversions with the ChangeType method</span></span>

<span data-ttu-id="ce0a7-215">[Convert](xref:System.Convert) クラスは、各基本型どうしの変換をサポートするだけでなく、カスタム型を&1; つ以上の定義済みの型に変換できます。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-215">In addition to supporting conversions to each of the base types, the [Convert](xref:System.Convert) class can be used to convert a custom type to one or more predefined types.</span></span> <span data-ttu-id="ce0a7-216">この変換は [Convert.ChangeType(Object, Type, IFormatProvider)](xref:System.Convert.ChangeType(System.Object,System.Type,System.IFormatProvider)) メソッドによって実行されます。さらに、このメソッドが、値パラメーターの [IConvertible.ToType](xref:System.IConvertible.ToType(System.Type,System.IFormatProvider)) メソッドに対する呼び出しをラップします。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-216">This conversion is performed by the [Convert.ChangeType(Object, Type, IFormatProvider)](xref:System.Convert.ChangeType(System.Object,System.Type,System.IFormatProvider)) method, which in turn wraps a call to the [IConvertible.ToType](xref:System.IConvertible.ToType(System.Type,System.IFormatProvider)) method of the value parameter.</span></span> <span data-ttu-id="ce0a7-217">したがって、値パラメーターで表されるオブジェクトで、[IConvertible](xref:System.IConvertible) インターフェイスの実装を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-217">This means that the object represented by the value parameter must provide an implementation of the [IConvertible](xref:System.IConvertible) interface.</span></span>

> [!NOTE]
> <span data-ttu-id="ce0a7-218">[Convert.ChangeType(Object, Type)](xref:System.Convert.ChangeType(System.Object,System.Type)) メソッドと [Convert.ChangeType(Object, Type, IFormatProvider)](xref:System.Convert.ChangeType(System.Object,System.Type,System.IFormatProvider)) メソッドは [Type](xref:System.Type) オブジェクトを使用して値の変換後の型を指定するため、コンパイル時には型がわからないオブジェクトへの動的な変換に使用することができます。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-218">Because the [Convert.ChangeType(Object, Type)](xref:System.Convert.ChangeType(System.Object,System.Type)) and [Convert.ChangeType(Object, Type, IFormatProvider)](xref:System.Convert.ChangeType(System.Object,System.Type,System.IFormatProvider)) methods use a [Type](xref:System.Type) object to specify the target type to which value is converted, they can be used to perform a dynamic conversion to an object whose type is not known at compile time.</span></span> <span data-ttu-id="ce0a7-219">ただし、値の [IConvertible](xref:System.IConvertible) の実装も、この変換をサポートする必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-219">However, note that the [IConvertible](xref:System.IConvertible) implementation of value must still support this conversion.</span></span> 

<span data-ttu-id="ce0a7-220">`TemperatureCelsius` オブジェクトから `TemperatureFahrenheit` オブジェクトへの変換およびその逆の変換を実行できる [IConvertible](xref:System.IConvertible) インターフェイスとして考えられる実装を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-220">The following example illustrates a possible implementation of the [IConvertible](xref:System.IConvertible) interface that allows a `TemperatureCelsius` object to be converted to a `TemperatureFahrenheit` object and vice versa.</span></span> <span data-ttu-id="ce0a7-221">この例では、[IConvertible](xref:System.IConvertible) インターフェイスを実装し、[Object.ToString](xref:System.Object.ToString) メソッドをオーバーライドする基本クラス `Temperature` を定義します。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-221">The example defines a base class, `Temperature`, that implements the [IConvertible](xref:System.IConvertible) interface and overrides the [Object.ToString](xref:System.Object.ToString) method.</span></span> <span data-ttu-id="ce0a7-222">派生クラスの `TemperatureCelsius` および `TemperatureFahrenheit` クラスが、基本クラスの `ToType` メソッドおよび `ToString` メソッドをそれぞれオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-222">The derived `TemperatureCelsius` and `TemperatureFahrenheit` classes each override the `ToType` and the `ToString` methods of the base class.</span></span> 

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

<span data-ttu-id="ce0a7-223">これらの [IConvertible](xref:System.IConvertible) 実装を呼び出して `TemperatureCelsius` オブジェクトから `TemperatureFahrenheit` オブジェクトへの変換またはその逆の変換を実行する例をいくつか以下に示します。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-223">The following example illustrates several calls to these [IConvertible](xref:System.IConvertible) implementations to convert `TemperatureCelsius` objects to `TemperatureFahrenheit` objects and vice versa.</span></span>

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

## <a name="the-typeconverter-class"></a><span data-ttu-id="ce0a7-224">TypeConverter クラス</span><span class="sxs-lookup"><span data-stu-id="ce0a7-224">The TypeConverter class</span></span>

<span data-ttu-id="ce0a7-225">.NET では、[System.ComponentModel.TypeConverter](xref:System.ComponentModel.TypeConverter) クラスを拡張し、[System.ComponentModel.TypeConverterAttribute](xref:System.ComponentModel.TypeConverterAttribute) 属性を使用して型コンバーターを型に関連付けることによって、カスタム型の型コンバーターも定義できます。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-225">.NET also allows you to define a type converter for a custom type by extending the [System.ComponentModel.TypeConverter](xref:System.ComponentModel.TypeConverter) class and associating the type converter with the type through a [System.ComponentModel.TypeConverterAttribute](xref:System.ComponentModel.TypeConverterAttribute) attribute.</span></span> <span data-ttu-id="ce0a7-226">次の表に、この方法と、カスタム型に対して [IConvertible](xref:System.IConvertible) インターフェイスを実装する方法の相違点をまとめます。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-226">The following table highlights the differences between this approach and implementing the [IConvertible](xref:System.IConvertible) interface for a custom type.</span></span>

> [!NOTE]
> <span data-ttu-id="ce0a7-227">カスタム型に対してデザイン時サポートが有効になるのは、そのカスタム型の型コンバーターが定義されている場合だけです。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-227">Design-time support can be provided for a custom type only if it has a type converter defined for it.</span></span>

<span data-ttu-id="ce0a7-228">TypeConverter を使用した変換</span><span class="sxs-lookup"><span data-stu-id="ce0a7-228">Conversion using TypeConverter</span></span> | <span data-ttu-id="ce0a7-229">IConvertible を使用した変換</span><span class="sxs-lookup"><span data-stu-id="ce0a7-229">Conversion using IConvertible</span></span>
------------------------------ | -----------------------------
<span data-ttu-id="ce0a7-230">[TypeConverter](xref:System.ComponentModel.TypeConverter) から独立したクラスを派生させることにより、カスタム型に実装されます。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-230">Is implemented for a custom type by deriving a separate class from [TypeConverter](xref:System.ComponentModel.TypeConverter).</span></span> <span data-ttu-id="ce0a7-231">この派生クラスは、[TypeConverterAttribute](xref:System.ComponentModel.TypeConverterAttribute) 属性を適用することにより、カスタム型と関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-231">This derived class is associated with the custom type by applying a [TypeConverterAttribute](xref:System.ComponentModel.TypeConverterAttribute) attribute.</span></span> | <span data-ttu-id="ce0a7-232">変換を実行するためにカスタム型によって実装されます。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-232">Is implemented by a custom type to perform conversion.</span></span> <span data-ttu-id="ce0a7-233">その型を使用するときに、その型に対して [IConvertible](xref:System.IConvertible) 変換メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-233">A user of the type invokes an [IConvertible](xref:System.IConvertible) conversion method on the type.</span></span>
<span data-ttu-id="ce0a7-234">デザイン時と実行時に使用できます。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-234">Can be used both at design time and at run time.</span></span> | <span data-ttu-id="ce0a7-235">実行時だけ使用できます。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-235">Can be used only at run time.</span></span>
<span data-ttu-id="ce0a7-236">リフレクションを使用するため、[IConvertible](xref:System.IConvertible) での変換よりも処理に時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-236">Uses reflection; therefore, is slower than conversion enabled by [IConvertible](xref:System.IConvertible).</span></span> | <span data-ttu-id="ce0a7-237">リフレクションを使用しません。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-237">Does not use reflection.</span></span>
<span data-ttu-id="ce0a7-238">カスタム型から他のデータ型への変換と、他のデータ型からカスタム型への変換という双方向の変換を実行できます。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-238">Allows two-way type conversions from the custom type to other data types, and from other data types to the custom type.</span></span> <span data-ttu-id="ce0a7-239">たとえば、`MyType` に対して定義される [TypeConverter](xref:System.ComponentModel.TypeConverter) を使用することによって、`MyType` から [String](xref:System.String) への変換および [String](xref:System.String) から `MyType` への変換を実行できます。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-239">For example, a [TypeConverter](xref:System.ComponentModel.TypeConverter) defined for `MyType` allows conversions from `MyType` to [String](xref:System.String), and from [String](xref:System.String) to `MyType`.</span></span> | <span data-ttu-id="ce0a7-240">カスタム型から他のデータ型への変換は実行できますが、他のデータ型からカスタム型への変換は実行できません。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-240">Allows conversion from a custom type to other data types, but not from other data types to the custom type.</span></span>

<span data-ttu-id="ce0a7-241">型コンバーターを使用した変換の詳細については、[System.ComponentModel.TypeConverter](xref:System.ComponentModel.TypeConverter) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ce0a7-241">For more information about using type converters to perform conversions, see [System.ComponentModel.TypeConverter](xref:System.ComponentModel.TypeConverter).</span></span>

## <a name="see-also"></a><span data-ttu-id="ce0a7-242">関連項目</span><span class="sxs-lookup"><span data-stu-id="ce0a7-242">See also</span></span>

[<span data-ttu-id="ce0a7-243">System.Convert</span><span class="sxs-lookup"><span data-stu-id="ce0a7-243">System.Convert</span></span>](xref:System.Convert)

[<span data-ttu-id="ce0a7-244">IConvertible</span><span class="sxs-lookup"><span data-stu-id="ce0a7-244">IConvertible</span></span>](xref:System.IConvertible)

[<span data-ttu-id="ce0a7-245">型変換の表</span><span class="sxs-lookup"><span data-stu-id="ce0a7-245">Type conversion tables</span></span>](conversion-tables.md)
