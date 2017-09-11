---
title: ".NET での数値文字列の解析"
description: ".NET での数値文字列の解析"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/29/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: e393430a-731a-49fa-83de-ff7ed52d5704
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 85cd57d33b03f7a2105ee3f770b2f8bcc0a57ee4
ms.contentlocale: ja-jp
ms.lasthandoff: 03/02/2017

---

# <a name="parsing-numeric-strings-in-net"></a><span data-ttu-id="d5dad-104">.NET での数値文字列の解析</span><span class="sxs-lookup"><span data-stu-id="d5dad-104">Parsing numeric strings in .NET</span></span>

<span data-ttu-id="d5dad-105">すべての数値型には、2 つの静的解析メソッド (`Parse` と `TryParse`) があり、数字の文字列形式を数値型に変換するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="d5dad-105">All numeric types have two static parsing methods, `Parse` and `TryParse`, that you can use to convert the string representation of a number into a numeric type.</span></span> <span data-ttu-id="d5dad-106">これらのメソッドでは、[標準の数値書式指定文字列](standard-numeric.md)と[カスタム数値書式指定文字列](custom-numeric.md)で記述されている書式指定文字列を使用して、生成された文字列を解析できます。</span><span class="sxs-lookup"><span data-stu-id="d5dad-106">These methods enable you to parse strings that were produced by using the format strings documented in [Standard Numeric Format Strings](standard-numeric.md) and [Custom Numeric Format Strings](custom-numeric.md).</span></span> <span data-ttu-id="d5dad-107">既定では、`Parse` と `TryParse` メソッドは、10 進数の整数を含む文字列を整数値のみに正常に変換することができます。</span><span class="sxs-lookup"><span data-stu-id="d5dad-107">By default, the `Parse` and `TryParse` methods can successfully convert strings that contain integral decimal digits only to integer values.</span></span> <span data-ttu-id="d5dad-108">これらのメソッドは、整数部と小数部、グループ区切り、および小数点記号を含む文字列を浮動小数点値に正常に変換できます。</span><span class="sxs-lookup"><span data-stu-id="d5dad-108">They can successfully convert strings that contain integral and fractional decimal digits, group separators, and a decimal separator to floating-point values.</span></span> <span data-ttu-id="d5dad-109">`TryParse` メソッドが `false` を返すのに対して、`Parse` メソッドは操作が失敗した場合に例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="d5dad-109">The `Parse` method throws an exception if the operation fails, whereas the `TryParse` method returns `false`.</span></span>

## <a name="parsing-and-format-providers"></a><span data-ttu-id="d5dad-110">解析と書式プロバイダー</span><span class="sxs-lookup"><span data-stu-id="d5dad-110">Parsing and format providers</span></span>

<span data-ttu-id="d5dad-111">通常、数値の文字列形式はカルチャによって異なります。</span><span class="sxs-lookup"><span data-stu-id="d5dad-111">Typically, the string representations of numeric values differ by culture.</span></span> <span data-ttu-id="d5dad-112">通貨記号、グループ (または千単位) 区切り、および小数点記号などの数値文字列の要素は、カルチャによって大きく異なります。</span><span class="sxs-lookup"><span data-stu-id="d5dad-112">Elements of numeric strings such as currency symbols, group (or thousands) separators, and decimal separators all vary by culture.</span></span> <span data-ttu-id="d5dad-113">暗黙的または明示的のいずれかの解析メソッドでは、これらのカルチャ固有のバリエーションを認識する書式プロバイダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="d5dad-113">Parsing methods either implicitly or explicitly use a format provider that recognizes these culture-specific variations.</span></span> <span data-ttu-id="d5dad-114">書式プロバイダーが `Parse` または `TryParse` メソッドの呼び出しで指定されない場合、現在のスレッド カルチャ ([NumberFormatInfo.CurrentInfo](xref:System.Globalization.NumberFormatInfo.CurrentInfo) プロパティで返された [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) オブジェクト) と関連付けられた書式プロバイダーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="d5dad-114">If no format provider is specified in a call to the `Parse` or `TryParse` method, the format provider associated with the current thread culture (the [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) object returned by the [NumberFormatInfo.CurrentInfo](xref:System.Globalization.NumberFormatInfo.CurrentInfo) property) is used.</span></span> 

<span data-ttu-id="d5dad-115">書式プロバイダーは、[IFormatProvider](xref:System.Globalization.NumberFormatInfo.CurrentInfo) 実装によって示されます。</span><span class="sxs-lookup"><span data-stu-id="d5dad-115">A format provider is represented by an [IFormatProvider](xref:System.Globalization.NumberFormatInfo.CurrentInfo) implementation.</span></span> <span data-ttu-id="d5dad-116">このインターフェイスには、1 つのメンバー ([GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) メソッド) があり、その&1; つのパラメーターは、書式設定される型を示す [Type](xref:System.Type) オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="d5dad-116">This interface has a single member, the [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) method, whose single parameter is a [Type](xref:System.Type) object that represents the type to be formatted.</span></span> <span data-ttu-id="d5dad-117">このメソッドは、書式情報を示すオブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="d5dad-117">This method returns the object that provides formatting information.</span></span> <span data-ttu-id="d5dad-118">.NET では、数値文字列を解析するために、次の&2; つの [IFormatProvider](xref:System.Globalization.NumberFormatInfo.CurrentInfo) の実装をサポートします。</span><span class="sxs-lookup"><span data-stu-id="d5dad-118">.NET supports the following two [IFormatProvider](xref:System.Globalization.NumberFormatInfo.CurrentInfo) implementations for parsing numeric strings:</span></span>

* <span data-ttu-id="d5dad-119">[CultureInfo.GetFormat](xref:System.Globalization.CultureInfo.GetFormat(System.Type)) メソッドが、カルチャ固有の書式情報を提供する [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) オブジェクトを返す、[CultureInfo](xref:System.Globalization.CultureInfo) オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="d5dad-119">A [CultureInfo](xref:System.Globalization.CultureInfo) object whose [CultureInfo.GetFormat](xref:System.Globalization.CultureInfo.GetFormat(System.Type)) method returns a [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) object that provides culture-specific formatting information.</span></span>

* <span data-ttu-id="d5dad-120">[NumberFormatInfo.GetFormat](xref:System.Globalization.NumberFormatInfo.GetFormat(System.Type)) メソッドがそれ自体を返す、[NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="d5dad-120">A [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) object whose [NumberFormatInfo.GetFormat](xref:System.Globalization.NumberFormatInfo.GetFormat(System.Type)) method returns itself.</span></span>

<span data-ttu-id="d5dad-121">次の例では、配列内の各文字列を [Double](xref:System.Double) 値に変換しようとします。</span><span class="sxs-lookup"><span data-stu-id="d5dad-121">The following example tries to convert each string in an array to a [Double](xref:System.Double) value.</span></span> <span data-ttu-id="d5dad-122">最初に、英語 (米国) カルチャの規則を反映する書式プロバイダーを使用して、文字列を解析しようとします。</span><span class="sxs-lookup"><span data-stu-id="d5dad-122">It first tries to parse the string by using a format provider that reflects the conventions of the English (United States) culture.</span></span> <span data-ttu-id="d5dad-123">この操作が [FormatException](xref:System.FormatException) をスローする場合、フランス語 (フランス) カルチャの規則を反映する書式プロバイダーを使用して、文字列を解析しようとしています。</span><span class="sxs-lookup"><span data-stu-id="d5dad-123">If this operation throws a [FormatException](xref:System.FormatException), it tries to parse the string by using a format provider that reflects the conventions of the French (France) culture.</span></span>

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      string[] values = { "1,304.16", "$1,456.78", "1,094", "152", 
                          "123,45 €", "1 304,16", "Ae9f" };
      double number;
      CultureInfo culture = null;

      foreach (string value in values) {
         try {
            culture = CultureInfo.CreateSpecificCulture("en-US");
            number = Double.Parse(value, culture);
            Console.WriteLine("{0}: {1} --> {2}", culture.Name, value, number);
         }   
         catch (FormatException) {
            Console.WriteLine("{0}: Unable to parse '{1}'.", 
                              culture.Name, value);
            culture = CultureInfo.CreateSpecificCulture("fr-FR");
            try {
               number = Double.Parse(value, culture);
               Console.WriteLine("{0}: {1} --> {2}", culture.Name, value, number);
            }
            catch (FormatException) {
               Console.WriteLine("{0}: Unable to parse '{1}'.", 
                                 culture.Name, value);
            }
         }
         Console.WriteLine();
      }   
   }
}
// The example displays the following output:
//    en-US: 1,304.16 --> 1304.16
//    
//    en-US: Unable to parse '$1,456.78'.
//    fr-FR: Unable to parse '$1,456.78'.
//    
//    en-US: 1,094 --> 1094
//    
//    en-US: 152 --> 152
//    
//    en-US: Unable to parse '123,45 €'.
//    fr-FR: Unable to parse '123,45 €'.
//    
//    en-US: Unable to parse '1 304,16'.
//    fr-FR: 1 304,16 --> 1304.16
//    
//    en-US: Unable to parse 'Ae9f'.
//    fr-FR: Unable to parse 'Ae9f'.
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim values() As String = { "1,304.16", "$1,456.78", "1,094", "152", 
                                 "123,45 €", "1 304,16", "Ae9f" }
      Dim number As Double
      Dim culture As CultureInfo = Nothing

      For Each value As String In values
         Try
            culture = CultureInfo.CreateSpecificCulture("en-US")
            number = Double.Parse(value, culture)
            Console.WriteLine("{0}: {1} --> {2}", culture.Name, value, number)
         Catch e As FormatException
            Console.WriteLine("{0}: Unable to parse '{1}'.", 
                              culture.Name, value)
            culture = CultureInfo.CreateSpecificCulture("fr-FR")
            Try
               number = Double.Parse(value, culture)
               Console.WriteLine("{0}: {1} --> {2}", culture.Name, value, number)
            Catch ex As FormatException
               Console.WriteLine("{0}: Unable to parse '{1}'.", 
                                 culture.Name, value)
            End Try
         End Try
         Console.WriteLine()
      Next
   End Sub
End Module
' The example displays the following output:
'    en-US: 1,304.16 --> 1304.16
'    
'    en-US: Unable to parse '$1,456.78'.
'    fr-FR: Unable to parse '$1,456.78'.
'    
'    en-US: 1,094 --> 1094
'    
'    en-US: 152 --> 152
'    
'    en-US: Unable to parse '123,45 €'.
'    fr-FR: Unable to parse '123,45 €'.
'    
'    en-US: Unable to parse '1 304,16'.
'    fr-FR: 1 304,16 --> 1304.16
'    
'    en-US: Unable to parse 'Ae9f'.
'    fr-FR: Unable to parse 'Ae9f'.
```

## <a name="parsing-and-numberstyles-values"></a><span data-ttu-id="d5dad-124">解析と NumberStyles 値</span><span class="sxs-lookup"><span data-stu-id="d5dad-124">Parsing and NumberStyles values</span></span>

<span data-ttu-id="d5dad-125">解析操作が処理できるスタイル要素 (空白文字、グループ区切り、小数点の記号など) は、[NumberStyles](xref:System.Globalization.NumberStyles) 列挙値によって定義されます。</span><span class="sxs-lookup"><span data-stu-id="d5dad-125">The style elements (such as white space, group separators, and decimal separator) that the parse operation can handle are defined by a [NumberStyles](xref:System.Globalization.NumberStyles) enumeration value.</span></span> <span data-ttu-id="d5dad-126">既定では、整数値を表す文字列は、[NumberStyles.Integer](xref:System.Globalization.NumberStyles.Integer) 値を使用して解析されます。これは、数値、先頭と末尾の空白、および先頭の符号のみを許可します。</span><span class="sxs-lookup"><span data-stu-id="d5dad-126">By default, strings that represent integer values are parsed by using the [NumberStyles.Integer](xref:System.Globalization.NumberStyles.Integer) value, which permits only numeric digits, leading and trailing white space, and a leading sign.</span></span> <span data-ttu-id="d5dad-127">浮動小数点値を表す文字列は、[NumberStyles.Float](xref:System.Globalization.NumberStyles.Float) と [NumberStyles.AllowThousands](xref:System.Globalization.NumberStyles.AllowThousands) 値の組み合わせを使用して解析されます。この複合スタイルは、先頭と末尾の空白、先頭の符号、小数点記号、グループ区切り、および指数と共に&10; 進数を許可します。</span><span class="sxs-lookup"><span data-stu-id="d5dad-127">Strings that represent floating-point values are parsed using a combination of the [NumberStyles.Float](xref:System.Globalization.NumberStyles.Float) and [NumberStyles.AllowThousands](xref:System.Globalization.NumberStyles.AllowThousands) values; this composite style permits decimal digits along with leading and trailing white space, a leading sign, a decimal separator, a group separator, and an exponent.</span></span> <span data-ttu-id="d5dad-128">[NumberStyles](xref:System.Globalization.NumberStyles) 型のパラメーターを含む、`Parse` または `TryParse` メソッドのオーバーロードを呼び出し、1 つ以上の [NumberStyles](xref:System.Globalization.NumberStyles) フラグを設定すると、解析操作が成功するように、文字列で示すことができるスタイル要素を制御することができます。</span><span class="sxs-lookup"><span data-stu-id="d5dad-128">By calling an overload of the `Parse` or `TryParse` method that includes a parameter of type [NumberStyles](xref:System.Globalization.NumberStyles) and setting one or more [NumberStyles](xref:System.Globalization.NumberStyles) flags, you can control the style elements that can be present in the string for the parse operation to succeed.</span></span> 

<span data-ttu-id="d5dad-129">たとえば、グループ区切りを含む文字列は、[Int32.Parse(String)](xref:System.Int32.Parse(System.String)) メソッドを使用して、[Int32](xref:System.Int32) 値に変換することはできません。</span><span class="sxs-lookup"><span data-stu-id="d5dad-129">For example, a string that contains a group separator cannot be converted to an [Int32](xref:System.Int32) value by using the [Int32.Parse(String)](xref:System.Int32.Parse(System.String)) method.</span></span> <span data-ttu-id="d5dad-130">ただし、次の例に示すように、[NumberStyles.AllowThousands](xref:System.Globalization.NumberStyles.AllowThousands) フラグを使用した場合、この変換は成功します。</span><span class="sxs-lookup"><span data-stu-id="d5dad-130">However, the conversion succeeds if you use the [NumberStyles.AllowThousands](xref:System.Globalization.NumberStyles.AllowThousands) flag, as the following example illustrates.</span></span>

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      string value = "1,304";
      int number;
      IFormatProvider provider = CultureInfo.CreateSpecificCulture("en-US");
      if (Int32.TryParse(value, out number))
         Console.WriteLine("{0} --> {1}", value, number);
      else
         Console.WriteLine("Unable to convert '{0}'", value);

      if (Int32.TryParse(value, NumberStyles.Integer | NumberStyles.AllowThousands, 
                        provider, out number))
         Console.WriteLine("{0} --> {1}", value, number);
      else
         Console.WriteLine("Unable to convert '{0}'", value);
   }
}
// The example displays the following output:
//       Unable to convert '1,304'
//       1,304 --> 1304
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim value As String = "1,304"
      Dim number As Integer
      Dim provider As IFormatProvider = CultureInfo.CreateSpecificCulture("en-US")
      If Int32.TryParse(value, number) Then
         Console.WriteLine("{0} --> {1}", value, number)
      Else
         Console.WriteLine("Unable to convert '{0}'", value)
      End If

      If Int32.TryParse(value, NumberStyles.Integer Or NumberStyles.AllowThousands, 
                        provider, number) Then
         Console.WriteLine("{0} --> {1}", value, number)
      Else
         Console.WriteLine("Unable to convert '{0}'", value)
      End If
   End Sub
End Module
' The example displays the following output:
'       Unable to convert '1,304'
'       1,304 --> 1304
```

> <span data-ttu-id="d5dad-131">**警告**</span><span class="sxs-lookup"><span data-stu-id="d5dad-131">**Warning**</span></span>
>
> <span data-ttu-id="d5dad-132">解析操作は、常に特定のカルチャの書式規則を使用します。</span><span class="sxs-lookup"><span data-stu-id="d5dad-132">The parse operation always uses the formatting conventions of a particular culture.</span></span> <span data-ttu-id="d5dad-133">[CultureInfo](xref:System.Globalization.CultureInfo) または [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) オブジェクトを渡してカルチャを指定しない場合、現在のスレッドに関連付けられているカルチャが使用されます。</span><span class="sxs-lookup"><span data-stu-id="d5dad-133">If you do not specify a culture by passing a [CultureInfo](xref:System.Globalization.CultureInfo) or [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) object, the culture associated with the current thread is used.</span></span>
 
<span data-ttu-id="d5dad-134">次の表では、[NumberStyles](xref:System.Globalization.NumberStyles) 列挙体のメンバーを一覧し、そのメンバーが解析操作に与える影響について説明します。</span><span class="sxs-lookup"><span data-stu-id="d5dad-134">The following table lists the members of the [NumberStyles](xref:System.Globalization.NumberStyles) enumeration and describes the effect that they have on the parsing operation.</span></span>

<span data-ttu-id="d5dad-135">NumberStyles 値</span><span class="sxs-lookup"><span data-stu-id="d5dad-135">NumberStyles value</span></span> | <span data-ttu-id="d5dad-136">解析する文字列への影響</span><span class="sxs-lookup"><span data-stu-id="d5dad-136">Effect on the string to be parsed</span></span>
------------------ | --------------------------------- 
[<span data-ttu-id="d5dad-137">NumberStyles.None</span><span class="sxs-lookup"><span data-stu-id="d5dad-137">NumberStyles.None</span></span>](xref:System.Globalization.NumberStyles.None) | <span data-ttu-id="d5dad-138">数字のみが許可されます。</span><span class="sxs-lookup"><span data-stu-id="d5dad-138">Only numeric digits are permitted.</span></span>
[<span data-ttu-id="d5dad-139">NumberStyles.AllowDecimalPoint</span><span class="sxs-lookup"><span data-stu-id="d5dad-139">NumberStyles.AllowDecimalPoint</span></span>](xref:System.Globalization.NumberStyles.AllowDecimalPoint) | <span data-ttu-id="d5dad-140">小数点の記号と桁数が許可されます。</span><span class="sxs-lookup"><span data-stu-id="d5dad-140">The decimal separator and fractional digits are permitted.</span></span> <span data-ttu-id="d5dad-141">整数値の場合、0 のみが小数点の桁数として許可されます。</span><span class="sxs-lookup"><span data-stu-id="d5dad-141">For integer values, only zero is permitted as a fractional digit.</span></span> <span data-ttu-id="d5dad-142">有効な小数点記号は、[NumberFormatInfo.NumberDecimalSeparator](xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator) または [NumberFormatInfo.CurrencyDecimalSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator) プロパティによって決定されます。</span><span class="sxs-lookup"><span data-stu-id="d5dad-142">Valid decimal separators are determined by the [NumberFormatInfo.NumberDecimalSeparator](xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator) or [NumberFormatInfo.CurrencyDecimalSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator) property.</span></span>
[<span data-ttu-id="d5dad-143">NumberStyles.AllowExponent</span><span class="sxs-lookup"><span data-stu-id="d5dad-143">NumberStyles.AllowExponent</span></span>](xref:System.Globalization.NumberStyles.AllowExponent) | <span data-ttu-id="d5dad-144">"e" または "E" の文字は、指数表記を示すために使用できます。</span><span class="sxs-lookup"><span data-stu-id="d5dad-144">The "e" or "E" character can be used to indicate exponential notation.</span></span>
[<span data-ttu-id="d5dad-145">NumberStyles.AllowLeadingWhite</span><span class="sxs-lookup"><span data-stu-id="d5dad-145">NumberStyles.AllowLeadingWhite</span></span>](xref:System.Globalization.NumberStyles.AllowLeadingWhite) | <span data-ttu-id="d5dad-146">先頭の空白が許可されます。</span><span class="sxs-lookup"><span data-stu-id="d5dad-146">Leading white space is permitted.</span></span>
[<span data-ttu-id="d5dad-147">NumberStyles.AllowTrailingWhite</span><span class="sxs-lookup"><span data-stu-id="d5dad-147">NumberStyles.AllowTrailingWhite</span></span>](xref:System.Globalization.NumberStyles.AllowTrailingWhite) | <span data-ttu-id="d5dad-148">末尾の空白が許可されます。</span><span class="sxs-lookup"><span data-stu-id="d5dad-148">Trailing white space is permitted.</span></span>
[<span data-ttu-id="d5dad-149">NumberStyles.AllowLeadingSign</span><span class="sxs-lookup"><span data-stu-id="d5dad-149">NumberStyles.AllowLeadingSign</span></span>](xref:System.Globalization.NumberStyles.AllowLeadingSign) | <span data-ttu-id="d5dad-150">正または負の符号には、数字の先頭に追加できます。</span><span class="sxs-lookup"><span data-stu-id="d5dad-150">A positive or negative sign can precede numeric digits.</span></span>
[<span data-ttu-id="d5dad-151">NumberStyles.AllowTrailingSign</span><span class="sxs-lookup"><span data-stu-id="d5dad-151">NumberStyles.AllowTrailingSign</span></span>](xref:System.Globalization.NumberStyles.AllowTrailingSign) | <span data-ttu-id="d5dad-152">正または負の符号は、数字の後に続けることができます。</span><span class="sxs-lookup"><span data-stu-id="d5dad-152">A positive or negative sign can follow numeric digits.</span></span>
[<span data-ttu-id="d5dad-153">NumberStyles.AllowParentheses</span><span class="sxs-lookup"><span data-stu-id="d5dad-153">NumberStyles.AllowParentheses</span></span>](xref:System.Globalization.NumberStyles.AllowParentheses) | <span data-ttu-id="d5dad-154">かっこは、負の符号を示すために使用できます。</span><span class="sxs-lookup"><span data-stu-id="d5dad-154">Parentheses can be used to indicate negative values.</span></span>
[<span data-ttu-id="d5dad-155">NumberStyles.AllowThousands</span><span class="sxs-lookup"><span data-stu-id="d5dad-155">NumberStyles.AllowThousands</span></span>](xref:System.Globalization.NumberStyles.AllowThousands) | <span data-ttu-id="d5dad-156">グループ区切りが許可されます。</span><span class="sxs-lookup"><span data-stu-id="d5dad-156">The group separator is permitted.</span></span> <span data-ttu-id="d5dad-157">グループ区切りは、[NumberFormatInfo.NumberGroupSeparator](xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator) または [NumberFormatInfo.CurrencyGroupSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator) プロパティによって決定されます。</span><span class="sxs-lookup"><span data-stu-id="d5dad-157">The group separator character is determined by the [NumberFormatInfo.NumberGroupSeparator](xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator) or [NumberFormatInfo.CurrencyGroupSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator) property.</span></span>
[<span data-ttu-id="d5dad-158">NumberStyles.AllowCurrencySymbol</span><span class="sxs-lookup"><span data-stu-id="d5dad-158">NumberStyles.AllowCurrencySymbol</span></span>](xref:System.Globalization.NumberStyles.AllowCurrencySymbol) | <span data-ttu-id="d5dad-159">通貨記号が許可されます。</span><span class="sxs-lookup"><span data-stu-id="d5dad-159">The currency symbol is permitted.</span></span> <span data-ttu-id="d5dad-160">通貨記号は、[NumberFormatInfo.CurrencySymbol](xref:System.Globalization.NumberFormatInfo.CurrencySymbol) プロパティによって定義されます。</span><span class="sxs-lookup"><span data-stu-id="d5dad-160">The currency symbol is defined by the [NumberFormatInfo.CurrencySymbol](xref:System.Globalization.NumberFormatInfo.CurrencySymbol) property.</span></span>
[<span data-ttu-id="d5dad-161">NumberStyles.AllowHexSpecifier</span><span class="sxs-lookup"><span data-stu-id="d5dad-161">NumberStyles.AllowHexSpecifier</span></span>](xref:System.Globalization.NumberStyles.AllowHexSpecifier) | <span data-ttu-id="d5dad-162">解析する文字列は、16 進数として解釈されます。</span><span class="sxs-lookup"><span data-stu-id="d5dad-162">The string to be parsed is interpreted as a hexadecimal number.</span></span> <span data-ttu-id="d5dad-163">これには、16 進数の値の 0 ～ 9、A ～ F、a ～ f を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="d5dad-163">It can include the hexadecimal digits 0-9, A-F, and a-f.</span></span> <span data-ttu-id="d5dad-164">このフラグは、整数値を解析するためにだけに使用できます。</span><span class="sxs-lookup"><span data-stu-id="d5dad-164">This flag can be used only to parse integer values.</span></span>
 
<span data-ttu-id="d5dad-165">さらに、[NumberStyles](xref:System.Globalization.NumberStyles) 列挙体は、複数の [NumberStyles](xref:System.Globalization.NumberStyles) フラグを含む、次の複合スタイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="d5dad-165">In addition, the [NumberStyles](xref:System.Globalization.NumberStyles) enumeration provides the following composite styles, which include multiple [NumberStyles](xref:System.Globalization.NumberStyles) flags.</span></span> 

<span data-ttu-id="d5dad-166">複合 NumberStyles 値</span><span class="sxs-lookup"><span data-stu-id="d5dad-166">Composite NumberStyles value</span></span> | <span data-ttu-id="d5dad-167">数値を含む</span><span class="sxs-lookup"><span data-stu-id="d5dad-167">Includes members</span></span>
---------------------------- | ---------------- 
[<span data-ttu-id="d5dad-168">NumberStyles.Integer</span><span class="sxs-lookup"><span data-stu-id="d5dad-168">NumberStyles.Integer</span></span>](xref:System.Globalization.NumberStyles.Integer) | <span data-ttu-id="d5dad-169">[NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite)、[NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite)、および [NumberStyles.AllowLeadingSign](xref:System.Globalization.NumberStyles.AllowLeadingSign) のスタイルを含みます。</span><span class="sxs-lookup"><span data-stu-id="d5dad-169">Includes the [NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite), [NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite), and [NumberStyles.AllowLeadingSign](xref:System.Globalization.NumberStyles.AllowLeadingSign) styles.</span></span> <span data-ttu-id="d5dad-170">これは、整数値を解析するために使用される既定のスタイルです。</span><span class="sxs-lookup"><span data-stu-id="d5dad-170">This is the default style used to parse integer values.</span></span>
[<span data-ttu-id="d5dad-171">NumberStyles.Number</span><span class="sxs-lookup"><span data-stu-id="d5dad-171">NumberStyles.Number</span></span>](xref:System.Globalization.NumberStyles.Number) | <span data-ttu-id="d5dad-172">[NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite)、[NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite)、[NumberStyles.AllowLeadingSign](xref:System.Globalization.NumberStyles.AllowLeadingSign)、[NumberStyles.AllowTrailingSign](xref:System.Globalization.NumberStyles.AllowTrailingSign)、[NumberStyles.AllowDecimalPoint](xref:System.Globalization.NumberStyles.AllowDecimalPoint)、および [NumberStyles.AllowThousands](xref:System.Globalization.NumberStyles.AllowThousands) のスタイルを含みます。</span><span class="sxs-lookup"><span data-stu-id="d5dad-172">Includes the [NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite), [NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite), [NumberStyles.AllowLeadingSign](xref:System.Globalization.NumberStyles.AllowLeadingSign), [NumberStyles.AllowTrailingSign](xref:System.Globalization.NumberStyles.AllowTrailingSign), [NumberStyles.AllowDecimalPoint](xref:System.Globalization.NumberStyles.AllowDecimalPoint), and [NumberStyles.AllowThousands](xref:System.Globalization.NumberStyles.AllowThousands) styles.</span></span>
[<span data-ttu-id="d5dad-173">NumberStyles.Float</span><span class="sxs-lookup"><span data-stu-id="d5dad-173">NumberStyles.Float</span></span>](xref:System.Globalization.NumberStyles.Float) | <span data-ttu-id="d5dad-174">[NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite)、[NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite)、[NumberStyles.AllowLeadingSign](xref:System.Globalization.NumberStyles.AllowLeadingSign)、[NumberStyles.AllowDecimalPoint](xref:System.Globalization.NumberStyles.AllowDecimalPoint)、および [NumberStyles.AllowExponent](xref:System.Globalization.NumberStyles.AllowExponent) のスタイルを含みます。</span><span class="sxs-lookup"><span data-stu-id="d5dad-174">Includes the [NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite), [NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite), [NumberStyles.AllowLeadingSign](xref:System.Globalization.NumberStyles.AllowLeadingSign), [NumberStyles.AllowDecimalPoint](xref:System.Globalization.NumberStyles.AllowDecimalPoint), and [NumberStyles.AllowExponent](xref:System.Globalization.NumberStyles.AllowExponent) styles.</span></span>
[<span data-ttu-id="d5dad-175">NumberStyles.Currency</span><span class="sxs-lookup"><span data-stu-id="d5dad-175">NumberStyles.Currency</span></span>](xref:System.Globalization.NumberStyles.Currency) | <span data-ttu-id="d5dad-176">[NumberStyles.AllowExponent](xref:System.Globalization.NumberStyles.AllowExponent) および [NumberStyles.AllowHexSpecifier](xref:System.Globalization.NumberStyles.AllowHexSpecifier) を除く、すべてのスタイルを含みます。</span><span class="sxs-lookup"><span data-stu-id="d5dad-176">Includes all styles except [NumberStyles.AllowExponent](xref:System.Globalization.NumberStyles.AllowExponent) and [NumberStyles.AllowHexSpecifier](xref:System.Globalization.NumberStyles.AllowHexSpecifier).</span></span>
[<span data-ttu-id="d5dad-177">NumberStyles.Any</span><span class="sxs-lookup"><span data-stu-id="d5dad-177">NumberStyles.Any</span></span>](xref:System.Globalization.NumberStyles.Any) | <span data-ttu-id="d5dad-178">[NumberStyles.AllowHexSpecifier](xref:System.Globalization.NumberStyles.AllowHexSpecifier) を除く、すべてのスタイルを含みます。</span><span class="sxs-lookup"><span data-stu-id="d5dad-178">Includes all styles except [NumberStyles.AllowHexSpecifier](xref:System.Globalization.NumberStyles.AllowHexSpecifier).</span></span>
[<span data-ttu-id="d5dad-179">NumberStyles.HexNumber</span><span class="sxs-lookup"><span data-stu-id="d5dad-179">NumberStyles.HexNumber</span></span>](xref:System.Globalization.NumberStyles.HexNumber) | <span data-ttu-id="d5dad-180">[NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite)、[NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite)、および [NumberStyles.AllowHexSpecifier](xref:System.Globalization.NumberStyles.AllowHexSpecifier) のスタイルを含みます。</span><span class="sxs-lookup"><span data-stu-id="d5dad-180">Includes the [NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite), [NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite), and [NumberStyles.AllowHexSpecifier](xref:System.Globalization.NumberStyles.AllowHexSpecifier) styles.</span></span>
 
## <a name="parsing-and-unicode-digits"></a><span data-ttu-id="d5dad-181">解析と Unicode 数字</span><span class="sxs-lookup"><span data-stu-id="d5dad-181">Parsing and Unicode digits</span></span>

<span data-ttu-id="d5dad-182">Unicode 標準では、さまざまな書記体系で数字のコード ポイントを定義します。</span><span class="sxs-lookup"><span data-stu-id="d5dad-182">The Unicode standard defines code points for digits in various writing systems.</span></span> <span data-ttu-id="d5dad-183">たとえば、U+0030 ～ U+0039 のコード ポイントは、0 ～ 9 の基本ラテンの数字を示し、U+09E6 ～ U+09EF のコード ポイントは、0 ～ 9 の数字のバングラ語の数字を示し、U+FF10 ～ U+FF19 のコード ポイントは、0 ～ 9 の全角の数字を示します。</span><span class="sxs-lookup"><span data-stu-id="d5dad-183">For example, code points from U+0030 to U+0039 represent the basic Latin digits 0 through 9, code points from U+09E6 to U+09EF represent the Bangla digits 0 through 9, and code points from U+FF10 to U+FF19 represent the Fullwidth digits 0 through 9.</span></span> <span data-ttu-id="d5dad-184">ただし、解析メソッドで認識される数字は、U+0030 ～ U+0039 のコード ポイントの基本ラテンの数字 0 ～ 9 のみです。</span><span class="sxs-lookup"><span data-stu-id="d5dad-184">However, the only numeric digits recognized by parsing methods are the basic Latin digits 0-9 with code points from U+0030 to U+0039.</span></span> <span data-ttu-id="d5dad-185">数値解析メソッドがその他の数字を含む文字列を渡す場合、メソッドは [FormatException](xref:System.FormatException) をスローします。</span><span class="sxs-lookup"><span data-stu-id="d5dad-185">If a numeric parsing method is passed a string that contains any other digits, the method throws a [FormatException](xref:System.FormatException).</span></span>

<span data-ttu-id="d5dad-186">次の例では、[Int32.Parse](xref:System.Int32.Parse(System.String)) メソッドを使用して、異なる書記体系の数字で構成される文字列を解析します。</span><span class="sxs-lookup"><span data-stu-id="d5dad-186">The following example uses the [Int32.Parse](xref:System.Int32.Parse(System.String)) method to parse strings that consist of digits in different writing systems.</span></span> <span data-ttu-id="d5dad-187">例の出力に示されているように、基本ラテンの数字を解析する試行は成功しますが、全角、アラビア インド、バングラ語の数字を解析する試行は失敗します。</span><span class="sxs-lookup"><span data-stu-id="d5dad-187">As the output from the example shows, the attempt to parse the basic Latin digits succeeds, but the attempt to parse the Fullwidth, Arabic-Indic, and Bangla digits fails.</span></span>

```csharp
using System;

public class Example
{
   public static void Main()
   {
      string value;
      // Define a string of basic Latin digits 1-5.
      value = "\u0031\u0032\u0033\u0034\u0035";
      ParseDigits(value);

      // Define a string of Fullwidth digits 1-5.
      value = "\uFF11\uFF12\uFF13\uFF14\uFF15";
      ParseDigits(value);

      // Define a string of Arabic-Indic digits 1-5.
      value = "\u0661\u0662\u0663\u0664\u0665";
      ParseDigits(value);

      // Define a string of Bangla digits 1-5.
      value = "\u09e7\u09e8\u09e9\u09ea\u09eb";
      ParseDigits(value);
   }

   static void ParseDigits(string value)
   {
      try {
         int number = Int32.Parse(value);
         Console.WriteLine("'{0}' --> {1}", value, number);
      }   
      catch (FormatException) {
         Console.WriteLine("Unable to parse '{0}'.", value);      
      }     
   }
}
// The example displays the following output:
//       '12345' --> 12345
//       Unable to parse '１２３４５'.
//       Unable to parse '١٢٣٤٥'.
//       Unable to parse '১২৩৪৫'.
```

```vb
Module Example
   Public Sub Main()
      Dim value As String
      ' Define a string of basic Latin digits 1-5.
      value = ChrW(&h31) + ChrW(&h32) + ChrW(&h33) + ChrW(&h34) + ChrW(&h35)
      ParseDigits(value)

      ' Define a string of Fullwidth digits 1-5.
      value = ChrW(&hff11) + ChrW(&hff12) + ChrW(&hff13) + ChrW(&hff14) + ChrW(&hff15)
      ParseDigits(value)

      ' Define a string of Arabic-Indic digits 1-5.
      value = ChrW(&h661) + ChrW(&h662) + ChrW(&h663) + ChrW(&h664) + ChrW(&h665)
      ParseDigits(value)

      ' Define a string of Bangla digits 1-5.
      value = ChrW(&h09e7) + ChrW(&h09e8) + ChrW(&h09e9) + ChrW(&h09ea) + ChrW(&h09eb)
      ParseDigits(value)
   End Sub

   Sub ParseDigits(value As String)
      Try
         Dim number As Integer = Int32.Parse(value)
         Console.WriteLine("'{0}' --> {1}", value, number)
      Catch e As FormatException
         Console.WriteLine("Unable to parse '{0}'.", value)      
      End Try     
   End Sub
End Module
' The example displays the following output:
'       '12345' --> 12345
'       Unable to parse '１２３４５'.
'       Unable to parse '١٢٣٤٥'.
'       Unable to parse '১২৩৪৫'.
```

## <a name="see-also"></a><span data-ttu-id="d5dad-188">関連項目</span><span class="sxs-lookup"><span data-stu-id="d5dad-188">See also</span></span>

[<span data-ttu-id="d5dad-189">System.Globalization.NumberStyles</span><span class="sxs-lookup"><span data-stu-id="d5dad-189">System.Globalization.NumberStyles</span></span>](xref:System.Globalization.NumberStyles)

[<span data-ttu-id="d5dad-190">.NET での文字列の解析</span><span class="sxs-lookup"><span data-stu-id="d5dad-190">Parsing strings in .NET</span></span>](parsing-strings.md)

[<span data-ttu-id="d5dad-191">.NET での型の書式設定</span><span class="sxs-lookup"><span data-stu-id="d5dad-191">Formatting types in .NET</span></span>](formatting-types.md)


