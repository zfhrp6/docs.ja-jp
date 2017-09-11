---
title: ".NET での日付と時刻文字列の解析"
description: ".NET での日付と時刻文字列の解析"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/29/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: e61514cd-5329-4eb8-b122-482fffb54ab7
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: f0131baa0874880b6697458426da5ae9ce1705b7
ms.contentlocale: ja-jp
ms.lasthandoff: 03/02/2017

---

# <a name="parsing-date-and-time-strings-in-net"></a><span data-ttu-id="83d92-104">.NET での日付と時刻文字列の解析</span><span class="sxs-lookup"><span data-stu-id="83d92-104">Parsing date and time strings in .NET</span></span>

<span data-ttu-id="83d92-105">解析メソッドは、日付と時刻の文字列形式を等価の [DateTime](xref:System.DateTime) オブジェクトに変換します。</span><span class="sxs-lookup"><span data-stu-id="83d92-105">Parsing methods convert the string representation of a date and time to an equivalent [DateTime](xref:System.DateTime) object.</span></span> <span data-ttu-id="83d92-106">[Parse](xref:System.DateTime.Parse(System.String)) と [TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) メソッドでは、日付と時刻のいくつかの共通表現のいずれかを変換します。</span><span class="sxs-lookup"><span data-stu-id="83d92-106">The [Parse](xref:System.DateTime.Parse(System.String)) and [TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) methods convert any of several common representations of a date and time.</span></span> <span data-ttu-id="83d92-107">[ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)) と [TryParseExact](xref:System.DateTime.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTime@)) メソッドでは、日付と時刻の書式指定文字列で指定されたパターンに適合する文字列形式を変換します。</span><span class="sxs-lookup"><span data-stu-id="83d92-107">The [ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)) and [TryParseExact](xref:System.DateTime.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTime@)) methods convert a string representation that conforms to the pattern specified by a date and time format string.</span></span> <span data-ttu-id="83d92-108">([標準の日付と時刻の書式指定文字列](standard-datetime.md)と[カスタムの日付と時刻の書式指定文字列](custom-datetime.md)に関するトピックをご覧ください)。</span><span class="sxs-lookup"><span data-stu-id="83d92-108">(See the topics on [standard date and time format strings](standard-datetime.md) and [custom date and time format strings](custom-datetime.md).)</span></span> 

<span data-ttu-id="83d92-109">解析は、日付と時刻の区切り記号、および月、日、および年号の名前に使用される文字列などの情報を提供する書式プロバイダーのプロパティの影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="83d92-109">Parsing is influenced by the properties of a format provider that supplies information such as the strings used for date and time separators, and the names of months, days, and eras.</span></span> <span data-ttu-id="83d92-110">書式プロバイダーは、現在の [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) オブジェクトです。このオブジェクトは、現在のスレッド カルチャによって暗黙的に指定されるか、または解析するメソッドの [IFormatProvider](xref:System.IFormatProvider) パラメーターによって明示的に指定されます。</span><span class="sxs-lookup"><span data-stu-id="83d92-110">The format provider is the current [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) object, which is provided implicitly by the current thread culture or explicitly by the [IFormatProvider](xref:System.IFormatProvider) parameter of a parsing method.</span></span> <span data-ttu-id="83d92-111">[IFormatProvider](xref:System.IFormatProvider) パラメーターには、カルチャ ([DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) オブジェクト) を表す [CultureInfo](xref:System.Globalization.CultureInfo) オブジェクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="83d92-111">For the [IFormatProvider](xref:System.IFormatProvider) parameter, specify a [CultureInfo](xref:System.Globalization.CultureInfo) object, which represents a culture, or a [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) object.</span></span> 

<span data-ttu-id="83d92-112">解析される日付の文字列形式には、月と、少なくとも日付または年を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="83d92-112">The string representation of a date to be parsed must include the month and at least a day or year.</span></span> <span data-ttu-id="83d92-113">時刻の文字列形式は、時間と、少なくとも分または AM/PM 指定子を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="83d92-113">The string representation of a time must include the hour and at least minutes or the AM/PM designator.</span></span> <span data-ttu-id="83d92-114">ただし、可能な場合は、解析により省略されたコンポーネントに既定値が指定されます。</span><span class="sxs-lookup"><span data-stu-id="83d92-114">However, parsing supplies default values for omitted components if possible.</span></span> <span data-ttu-id="83d92-115">欠落している日付には現在の日付が規定で設定され、欠落している年には現在の年が規定で設定され、欠落している月の日付には月の最初の日が規定で設定され、欠落している時刻には午前&0; 時が規定で設定されます。</span><span class="sxs-lookup"><span data-stu-id="83d92-115">A missing date defaults to the current date, a missing year defaults to the current year, a missing day of the month defaults to the first day of the month, and a missing time defaults to midnight.</span></span> 

<span data-ttu-id="83d92-116">文字列形式で時刻のみを指定する場合、解析は、[Today](xref:System.DateTime.Today) プロパティの対応する値に、その [Year](xref:System.DateTime.Year)、[Month](xref:System.DateTime.Month)、および [Day](xref:System.DateTime.Day) プロパティを設定した [DateTime](xref:System.DateTime) オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="83d92-116">If the string representation specifies only a time, parsing returns a [DateTime](xref:System.DateTime) object with its [Year](xref:System.DateTime.Year), [Month](xref:System.DateTime.Month), and [Day](xref:System.DateTime.Day) properties set to the corresponding values of the [Today](xref:System.DateTime.Today) property.</span></span> <span data-ttu-id="83d92-117">ただし、[DateTimeStyles.NoCurrentDateDefault](xref:System.Globalization.DateTimeStyles.NoCurrentDateDefault) 定数が解析メソッドで指定されている場合、結果の年、月、日付のプロパティの値は 1 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="83d92-117">However, if the [DateTimeStyles.NoCurrentDateDefault](xref:System.Globalization.DateTimeStyles.NoCurrentDateDefault) constant is specified in the parsing method, the resulting year, month, and day properties are set to the value 1.</span></span>

<span data-ttu-id="83d92-118">日付と時刻のコンポーネントだけでなく、日付と時刻の文字列形式には、世界協定時刻 (UTC) と何時間異なるかを示すオフセットを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="83d92-118">In addition to a date and a time component, the string representation of a date and time can include an offset that indicates how much the time differs from Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="83d92-119">たとえば、文字列 "2/14/2007 5:32:00 -7:00" は、UTC より 7 時間早い時刻を定義します。</span><span class="sxs-lookup"><span data-stu-id="83d92-119">For example, the string "2/14/2007 5:32:00 -7:00" defines a time that is seven hours earlier than UTC.</span></span> <span data-ttu-id="83d92-120">オフセットが時刻の文字列形式から省略される場合、解析では、その [Kind](xref:System.DateTime.Kind) プロパティに [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified) を設定して、[DateTime](xref:System.DateTime) オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="83d92-120">If an offset is omitted from the string representation of a time, parsing returns a [DateTime](xref:System.DateTime) object with its [Kind](xref:System.DateTime.Kind) property set to [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified).</span></span> <span data-ttu-id="83d92-121">オフセットが指定されている場合、解析では、その [Kind](xref:System.DateTime.Kind) プロパティに [Local](xref:System.DateTimeKind.Local) を設定した [DateTime](xref:System.DateTime) オブジェクトと、使用しているマシンのローカル タイム ゾーンに調整された値を返します。</span><span class="sxs-lookup"><span data-stu-id="83d92-121">If an offset is specified, parsing returns a [DateTime](xref:System.DateTime) object with its [Kind](xref:System.DateTime.Kind) property set to [Local](xref:System.DateTimeKind.Local) and its value adjusted to the local time zone of your machine.</span></span> <span data-ttu-id="83d92-122">解析メソッドで [DateTimeStyles](xref:System.Globalization.DateTimeStyles) 定数を使用して、この動作を変更できます。</span><span class="sxs-lookup"><span data-stu-id="83d92-122">You can modify this behavior by using a [DateTimeStyles](xref:System.Globalization.DateTimeStyles) constant with the parsing method.</span></span>

<span data-ttu-id="83d92-123">書式プロバイダーは、あいまいな数値の日付を解釈するためにも使用されます。</span><span class="sxs-lookup"><span data-stu-id="83d92-123">The format provider is also used to interpret an ambiguous numeric date.</span></span> <span data-ttu-id="83d92-124">たとえば、文字列 "02/03/04" で示された日付は、どのコンポーネントが月、日、年であるのかが明確ではありません。</span><span class="sxs-lookup"><span data-stu-id="83d92-124">For example, it is not clear which components of the date represented by the string "02/03/04" are the month, day, and year.</span></span> <span data-ttu-id="83d92-125">この場合、コンポーネントは、書式プロバイダーの日付形式と同様の順序で解釈されます。</span><span class="sxs-lookup"><span data-stu-id="83d92-125">In this case, the components are interpreted according to the order of similar date formats in the format provider.</span></span> 

## <a name="parse"></a><span data-ttu-id="83d92-126">Parse</span><span class="sxs-lookup"><span data-stu-id="83d92-126">Parse</span></span>

<span data-ttu-id="83d92-127">次のコード例では、文字列を `DateTime` に変換するために、`Parse` メソッドを使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="83d92-127">The following code example illustrates the use of the `Parse` method to convert a string into a `DateTime`.</span></span> <span data-ttu-id="83d92-128">この例では、現在のスレッドに関連付けられているカルチャを使用して、解析が実行されます。</span><span class="sxs-lookup"><span data-stu-id="83d92-128">This example uses the culture associated with the current thread to perform the parse.</span></span> <span data-ttu-id="83d92-129">現在のカルチャに関連付けられている [CultureInfo](xref:System.Globalization.CultureInfo) で入力文字列を解析できない場合は、[FormatException](xref:System.FormatException) がスローされます。</span><span class="sxs-lookup"><span data-stu-id="83d92-129">If the [CultureInfo](xref:System.Globalization.CultureInfo) associated with the current culture cannot parse the input string, a [FormatException](xref:System.FormatException) is thrown.</span></span>

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

<span data-ttu-id="83d92-130">また、そのオブジェクトで定義されているカルチャのいずれかに設定される `CultureInfo` を指定するか、または [CultureInfo.DateTimeFormat](xref:System.Globalization.CultureInfo.DateTimeFormat) プロパティによって返される標準の [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) オブジェクトのいずれかを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="83d92-130">You can also specify a `CultureInfo` set to one of the cultures defined by that object, or you can specify one of the standard [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) objects returned by the [CultureInfo.DateTimeFormat](xref:System.Globalization.CultureInfo.DateTimeFormat) property.</span></span> <span data-ttu-id="83d92-131">次のコード例は、書式プロバイダーを使用して、ドイツ語の文字列を `DateTime` に解析します。</span><span class="sxs-lookup"><span data-stu-id="83d92-131">The following code example uses a format provider to parse a German string into a `DateTime`.</span></span> <span data-ttu-id="83d92-132">この特定の文字列を正常に解析できるように、de-DE カルチャを示す `CultureInfo` が定義され、解析されている文字列と共に渡されます。</span><span class="sxs-lookup"><span data-stu-id="83d92-132">A `CultureInfo` representing the de-DE culture is defined and passed with the string being parsed to ensure successful parsing of this particular string.</span></span> <span data-ttu-id="83d92-133">これによって、`CurrentThread` の `CurrentCulture` がどのように設定されていても除外されます。</span><span class="sxs-lookup"><span data-stu-id="83d92-133">This precludes whatever setting is in the `CurrentCulture` of the `CurrentThread`.</span></span>

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

<span data-ttu-id="83d92-134">ただし、[Parse](xref:System.DateTime.Parse(System.String)) メソッドのオーバーロードを使用して、カスタム書式プロバイダーを指定することができますが、このメソッドでは非標準の書式プロバイダーの使用をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="83d92-134">However, although you can use overloads of the [Parse](xref:System.DateTime.Parse(System.String)) method to specify custom format providers, the method does not support the use of non-standard format providers.</span></span> <span data-ttu-id="83d92-135">非標準の書式設定で示された日付と時刻を解析するには、代わりに [ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)) メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="83d92-135">To parse a date and time expressed in a non-standard format, use the [ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)) method instead.</span></span>

<span data-ttu-id="83d92-136">次のコード例では、[DateTimeStyles](xref:System.Globalization.DateTimeStyles) 列挙体を使用して、現在の日付と時刻の情報を、文字列で定義しないフィールドの `DateTime` に追加しないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="83d92-136">The following code example uses the [DateTimeStyles](xref:System.Globalization.DateTimeStyles) enumeration to specify that the current date and time information should not be added to the `DateTime` for fields that the string does not define.</span></span>

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

## <a name="parseexact"></a><span data-ttu-id="83d92-137">ParseExact</span><span class="sxs-lookup"><span data-stu-id="83d92-137">ParseExact</span></span>

<span data-ttu-id="83d92-138">[DateTime.ParseExact]((xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)) メソッドは、指定された文字列パターンに適合する文字列を `DateTime` オブジェクトに変換します。</span><span class="sxs-lookup"><span data-stu-id="83d92-138">The [DateTime.ParseExact]((xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)) method converts a string that conforms to a specified string pattern to a `DateTime` object.</span></span> <span data-ttu-id="83d92-139">指定された形式ではない文字列がこのメソッドに渡された場合、[FormatException](xref:System.FormatException) がスローされます。</span><span class="sxs-lookup"><span data-stu-id="83d92-139">When a string that is not of the form specified is passed to this method, a [FormatException](xref:System.FormatException) is thrown.</span></span> <span data-ttu-id="83d92-140">標準の日付と時刻の書式指定子のいずれか、またはカスタムの日付と時刻の書式指定子の制限された組み合わせを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="83d92-140">You can specify one of the standard date and time format specifiers or a limited combination of the custom date and time format specifiers.</span></span> <span data-ttu-id="83d92-141">カスタムの書式指定子を使用すると、カスタムの認識文字列を構成することができます。</span><span class="sxs-lookup"><span data-stu-id="83d92-141">Using the custom format specifiers, it is possible for you to construct a custom recognition string.</span></span> <span data-ttu-id="83d92-142">(指定子の詳細については、[標準の日付と時刻の書式指定文字列](standard-datetime.md)と[カスタムの日付と時刻の書式指定文字列](custom-datetime.md)に関するトピックをご覧ください)。</span><span class="sxs-lookup"><span data-stu-id="83d92-142">For an explanation of the specifiers, see the topics on [standard date and time format strings](standard-datetime.md) and [custom date and time format strings](custom-datetime.md).</span></span> 

<span data-ttu-id="83d92-143">[ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)) メソッドのオーバーロードごとに、通常は文字列の書式設定に関するカルチャ固有の情報を指定する [IFormatProvider](xref:System.IFormatProvider) パラメーターもあります。</span><span class="sxs-lookup"><span data-stu-id="83d92-143">Each overload of the [ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)) method also has an [IFormatProvider](xref:System.IFormatProvider) parameter that typically provides culture-specific information about the formatting of the string.</span></span> <span data-ttu-id="83d92-144">通常、この [IFormatProvider](xref:System.IFormatProvider) オブジェクトは、標準カルチャを表す [CultureInfo](xref:System.Globalization.CultureInfo) オブジェクト、または [CultureInfo.DateTimeFormat](xref:System.Globalization.CultureInfo.DateTimeFormat) プロパティによって返される [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="83d92-144">Typically, this [IFormatProvider](xref:System.IFormatProvider) object is a [CultureInfo](xref:System.Globalization.CultureInfo) object that represents a standard culture or a [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) object that is returned by the [CultureInfo.DateTimeFormat](xref:System.Globalization.CultureInfo.DateTimeFormat) property.</span></span> <span data-ttu-id="83d92-145">ただし、その他の日付と時刻の解析関数とは異なり、このメソッドでは、非標準の日付と時刻の書式を定義する [IFormatProvider](xref:System.IFormatProvider) もサポートしています。</span><span class="sxs-lookup"><span data-stu-id="83d92-145">However, unlike the other date and time parsing functions, this method also supports an [IFormatProvider](xref:System.IFormatProvider) that defines a non-standard date and time format.</span></span> 

<span data-ttu-id="83d92-146">次のコード例では、`ParseExact` メソッドに解析する文字列オブジェクト、書式指定子、`CultureInfo` オブジェクトが順に渡されます。</span><span class="sxs-lookup"><span data-stu-id="83d92-146">In the following code example, the `ParseExact` method is passed a string object to parse, followed by a format specifier, followed by a `CultureInfo` object.</span></span> <span data-ttu-id="83d92-147">この `ParseExact` メソッドでは、en-US カルチャで長い形式の日付パターンを示す文字列のみを解析できます。</span><span class="sxs-lookup"><span data-stu-id="83d92-147">This `ParseExact` method can only parse strings that exhibit the long date pattern in the en-US culture.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="83d92-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="83d92-148">See Also</span></span>

[<span data-ttu-id="83d92-149">.NET での文字列の解析</span><span class="sxs-lookup"><span data-stu-id="83d92-149">Parsing strings in .NET</span></span>](parsing-strings.md)

[<span data-ttu-id="83d92-150">.NET での型の書式設定</span><span class="sxs-lookup"><span data-stu-id="83d92-150">Formatting types in .NET</span></span>](formatting-types.md)

[<span data-ttu-id="83d92-151">.NET での型変換</span><span class="sxs-lookup"><span data-stu-id="83d92-151">Type conversion in .NET</span></span>](type-conversion.md)


