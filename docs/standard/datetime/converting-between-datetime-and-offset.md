---
title: "DateTime と DateTimeOffset 間の変換"
description: "DateTime と DateTimeOffset 間の変換"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: fab3af5b-5d0f-4384-a40a-1b5d99b30dd1
translationtype: Human Translation
ms.sourcegitcommit: c40c28da09e8a122b542463c197196c82c81dd19
ms.openlocfilehash: 312ac8cb7e901c4ceeff2e428620c2c4c615ca3d

---

# <a name="converting-between-datetime-and-datetimeoffset"></a>DateTime と DateTimeOffset 間の変換

[System.DateTimeOffset](xref:System.DateTimeOffset) 構造体は、[System.DateTime](xref:System.DateTime) 構造体よりも高度なタイム ゾーン対応を実現しますが、メソッド呼び出しでは [DateTime](xref:System.DateTime) パラメーターがよく使用されます。 このため、[DateTimeOffset](xref:System.DateTimeOffset) 値を [DateTime](xref:System.DateTime) 値に、またはその逆方向に変換する機能が特に重要です。 この記事では、タイム ゾーン情報をできるだけ多く保持するようにこれらの変換を実行する方法を示します。

> [!NOTE]
> [DateTime](xref:System.DateTime) 型と [DateTimeOffset](xref:System.DateTimeOffset) 型は両方とも、タイム ゾーンの時刻を表す場合に制限があります。 [DateTime](xref:System.DateTime) は、その [Kind](xref:System.DateTime.Kind) プロパティによって世界協定時刻 (UTC) とシステムのローカル タイム ゾーンのみを反映できます。 [DateTimeOffset](xref:System.DateTimeOffset) は、UTC からの時間のオフセットを反映しますが、そのオフセットが所属する実際のタイム ゾーンは反映しません。 時刻の値とタイム ゾーンのサポートの詳細については、「[DateTime DateTimeOffset TimeSpan、および TimeZoneInfo の使い分け](choosing-between-datetime.md)」を参照してください。

## <a name="conversions-from-datetime-to-datetimeoffset"></a>DateTime から DateTimeOffset への変換

[DateTimeOffset](xref:System.DateTimeOffset) 構造体は、ほとんどの変換に適した、[DateTime](xref:System.DateTime) から [DateTimeOffset](xref:System.DateTimeOffset) への変換を実行する次の 2 つの相当する方法を提供します。

* [DateTimeOffset(DateTime)](xref:System.DateTimeOffset) コンストラクター。[DateTime](xref:System.DateTime) 値に基づいて新しい [DateTimeOffset](xref:System.DateTimeOffset) オブジェクトを作成します。

* 暗黙的な変換演算子。[DateTime](xref:System.DateTime) 値を [DateTimeOffset](xref:System.DateTimeOffset) オブジェクトに割り当て可能にします。

UTC と現地の [DateTime](xref:System.DateTime) 値について、変換後の [DateTimeOffset](xref:System.DateTimeOffset) 値の [DateTimeOffset.Offset](xref:System.DateTimeOffset.Offset) プロパティは、UTC またはローカル タイム ゾーン オフセットを正確に反映します。 たとえば、次のコードは、UTC 時刻を同等の [DateTimeOffset](xref:System.DateTimeOffset) 値に変換します。 

```csharp
DateTime utcTime1 = new DateTime(2008, 6, 19, 7, 0, 0);
utcTime1 = DateTime.SpecifyKind(utcTime1, DateTimeKind.Utc);
DateTimeOffset utcTime2 = utcTime1;
Console.WriteLine("Converted {0} {1} to a DateTimeOffset value of {2}", 
                  utcTime1, 
                  utcTime1.Kind.ToString(), 
                  utcTime2);
// This example displays the following output to the console:
//    Converted 6/19/2008 7:00:00 AM Utc to a DateTimeOffset value of 6/19/2008 7:00:00 AM +00:00
```

```vb
Dim utcTime1 As Date = Date.SpecifyKind(#06/19/2008 7:00AM#, _
                                        DateTimeKind.Utc)
Dim utcTime2 As DateTimeOffset = utcTime1
Console.WriteLine("Converted {0} {1} to a DateTimeOffset value of {2}", _
                  utcTime1, _
                  utcTime1.Kind.ToString(), _
                  utcTime2)
' This example displays the following output to the console:
'    Converted 6/19/2008 7:00:00 AM Utc to a DateTimeOffset value of 6/19/2008 7:00:00 AM  +00:00
```

この場合、`utcTime2` 変数のオフセットは 00:00 です。 同様に、次のコードは、現地時刻を同等の [DateTimeOffset](xref:System.DateTimeOffset) 値に変換します。

```csharp
DateTime localTime1 = new DateTime(2008, 6, 19, 7, 0, 0);
localTime1 = DateTime.SpecifyKind(localTime1, DateTimeKind.Local);
DateTimeOffset localTime2 = localTime1;
Console.WriteLine("Converted {0} {1} to a DateTimeOffset value of {2}", 
                  localTime1, 
                  localTime1.Kind.ToString(), 
                  localTime2);
// This example displays the following output to the console:
//    Converted 6/19/2008 7:00:00 AM Local to a DateTimeOffset value of 6/19/2008 7:00:00 AM -07:00
```

```vb
Dim localTime1 As Date = Date.SpecifyKind(#06/19/2008 7:00AM#, DateTimeKind.Local)
Dim localTime2 As DateTimeOffset = localTime1
Console.WriteLine("Converted {0} {1} to a DateTimeOffset value of {2}", _
                  localTime1, _
                  localTime1.Kind.ToString(), _
                  localTime2)
' This example displays the following output to the console:
'    Converted 6/19/2008 7:00:00 AM Local to a DateTimeOffset value of 6/19/2008 7:00:00 AM -07:00
```

ただし、[Kind](xref:System.DateTime.Kind) プロパティが [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified) である [DateTime](xref:System.DateTime) 値については、これらの 2 つの変換メソッドは、オフセットがローカル タイム ゾーンのオフセットである [DateTimeOffset](xref:System.DateTimeOffset) 値を生成します。 米国の太平洋標準時ゾーンでの実行例を次に示します。

```csharp
DateTime time1 = new DateTime(2008, 6, 19, 7, 0, 0);  // Kind is DateTimeKind.Unspecified
DateTimeOffset time2 = time1;
Console.WriteLine("Converted {0} {1} to a DateTimeOffset value of {2}", 
                  time1, 
                  time1.Kind.ToString(), 
                  time2);
// This example displays the following output to the console:
//    Converted 6/19/2008 7:00:00 AM Unspecified to a DateTimeOffset value of 6/19/2008 7:00:00 AM -07:00
```

```vb
Dim time1 As Date = #06/19/2008 7:00AM#      ' Kind is DateTimeKind.Unspecified
Dim time2 As DateTimeOffset = time1
Console.WriteLine("Converted {0} {1} to a DateTimeOffset value of {2}", _
                  time1, _
                  time1.Kind.ToString(), _
                  time2)
' This example displays the following output to the console:
'    Converted 6/19/2008 7:00:00 AM Unspecified to a DateTimeOffset value of 6/19/2008 7:00:00 AM -07:00
```

[DateTime](xref:System.DateTime) 値がローカル タイム ゾーンまたは UTC 以外の何らかの日時を反映している場合は、オーバーロードされた [DateTimeOffset(DateTime, TimeSpan)](xref:System.DateTimeOffset) コンストラクターを呼び出して、この値を [DateTimeOffset](xref:System.DateTimeOffset) 値に変換し、そのタイム ゾーン情報を保持することができます。 たとえば、次の例では、中部標準時を反映する [DateTimeOffset](xref:System.DateTimeOffset) オブジェクトをインスタンス化します。

```csharp
DateTime time1 = new DateTime(2008, 6, 19, 7, 0, 0);     // Kind is DateTimeKind.Unspecified
try
{
   DateTimeOffset time2 = new DateTimeOffset(time1, 
                  TimeZoneInfo.FindSystemTimeZoneById("Central Standard Time").GetUtcOffset(time1)); 
   Console.WriteLine("Converted {0} {1} to a DateTime value of {2}", 
                     time1, 
                     time1.Kind.ToString(), 
                     time2);
}
// Handle exception if time zone is not defined in registry
catch (TimeZoneNotFoundException)
{
   Console.WriteLine("Unable to identify target time zone for conversion.");
}
// This example displays the following output to the console:
//    Converted 6/19/2008 7:00:00 AM Unspecified to a DateTime value of 6/19/2008 7:00:00 AM -05:00
```

```vb
Dim time1 As Date = #06/19/2008 7:00AM#      ' Kind is DateTimeKind.Unspecified
Try
   Dim time2 As New DateTimeOffset(time1, _
                    TimeZoneInfo.FindSystemTimeZoneById("Central Standard Time").GetUtcOffset(time1)) 
   Console.WriteLine("Converted {0} {1} to a DateTime value of {2}", _
                     time1, _
                     time1.Kind.ToString(), _
                     time2)
' Handle exception if time zone is not defined in registry
Catch e As TimeZoneNotFoundException
   Console.WriteLine("Unable to identify target time zone for conversion.")
End Try
' This example displays the following output to the console:
'    Converted 6/19/2008 7:00:00 AM Unspecified to a DateTime value of 6/19/2008 7:00:00 AM -05:00
```

このコンストラクター オーバーロードの 2 番目のパラメーターは、UTC からの時刻のオフセットを表す [System.TimeSpan](xref:System.TimeSpan) オブジェクトです。このオブジェクトは、時刻の対応するタイム ゾーンの [TimeZoneInfo.GetUtcOffset(DateTime)](xref:System.TimeZoneInfo) メソッドを呼び出して取得する必要があります。 このメソッドの単一のパラメーターは、変換する日時を表す [DateTime](xref:System.DateTime) 値です。 タイム ゾーンで夏時間がサポートされている場合、このパラメーターにより、このメソッドはその特定の日時に対して適切なオフセットを決定できます。

## <a name="conversions-from-datetimeoffset-to-datetime"></a>DateTimeOffset から DateTime への変換

[DateTimeOffset](xref:System.DateTimeOffset) から [DateTime](xref:System.DateTime) への変換の実行には、[DateTime](xref:System.DateTime) プロパティが最もよく使用されます。 ただし、次の例に示すように、このプロパティは、[Kind](xref:System.DateTime.Kind) プロパティが [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified) である [DateTime](xref:System.DateTime) 値を返します。 

```csharp
DateTime baseTime = new DateTime(2008, 6, 19, 7, 0, 0);
DateTimeOffset sourceTime;
DateTime targetTime;

// Convert UTC to DateTime value
sourceTime = new DateTimeOffset(baseTime, TimeSpan.Zero);
targetTime = sourceTime.DateTime;
Console.WriteLine("{0} converts to {1} {2}", 
                  sourceTime, 
                  targetTime, 
                  targetTime.Kind.ToString());

// Convert local time to DateTime value
sourceTime = new DateTimeOffset(baseTime, 
                                TimeZoneInfo.Local.GetUtcOffset(baseTime));
targetTime = sourceTime.DateTime;
Console.WriteLine("{0} converts to {1} {2}", 
                  sourceTime, 
                  targetTime, 
                  targetTime.Kind.ToString());

// Convert Central Standard Time to a DateTime value
try
{
   TimeSpan offset = TimeZoneInfo.FindSystemTimeZoneById("Central Standard Time").GetUtcOffset(baseTime);
   sourceTime = new DateTimeOffset(baseTime, offset);
   targetTime = sourceTime.DateTime;
   Console.WriteLine("{0} converts to {1} {2}", 
                     sourceTime, 
                     targetTime, 
                     targetTime.Kind.ToString());
}
catch (TimeZoneNotFoundException)
{
   Console.WriteLine("Unable to create DateTimeOffset based on U.S. Central Standard Time.");
} 
// This example displays the following output to the console:
//    6/19/2008 7:00:00 AM +00:00 converts to 6/19/2008 7:00:00 AM Unspecified
//    6/19/2008 7:00:00 AM -07:00 converts to 6/19/2008 7:00:00 AM Unspecified
//    6/19/2008 7:00:00 AM -05:00 converts to 6/19/2008 7:00:00 AM Unspecified 
```

```vb
Const baseTime As Date = #06/19/2008 7:00AM#
Dim sourceTime As DateTimeOffset
Dim targetTime As Date

' Convert UTC to DateTime value
sourceTime = New DateTimeOffset(baseTime, TimeSpan.Zero)
targetTime = sourceTime.DateTime
Console.WriteLine("{0} converts to {1} {2}", _
                  sourceTime, _
                  targetTime, _
                  targetTime.Kind.ToString())

' Convert local time to DateTime value
sourceTime = New DateTimeOffset(baseTime, _
                                TimeZoneInfo.Local.GetUtcOffset(baseTime))
targetTime = sourceTime.DateTime
Console.WriteLine("{0} converts to {1} {2}", _
                  sourceTime, _
                  targetTime, _
                  targetTime.Kind.ToString())

' Convert Central Standard Time to a DateTime value
Try
   Dim offset As TimeSpan = TimeZoneInfo.FindSystemTimeZoneById("Central Standard Time").GetUtcOffset(baseTime)
   sourceTime = New DateTimeOffset(baseTime, offset)
   targetTime = sourceTime.DateTime
Console.WriteLine("{0} converts to {1} {2}", _
                  sourceTime, _
                  targetTime, _
                  targetTime.Kind.ToString())
Catch e As TimeZoneNotFoundException
   Console.WriteLine("Unable to create DateTimeOffset based on U.S. Central Standard Time.")
End Try 
' This example displays the following output to the console:
'    6/19/2008 7:00:00 AM +00:00 converts to 6/19/2008 7:00:00 AM Unspecified
'    6/19/2008 7:00:00 AM -07:00 converts to 6/19/2008 7:00:00 AM Unspecified
'    6/19/2008 7:00:00 AM -05:00 converts to 6/19/2008 7:00:00 AM Unspecified 
```

つまり、[DateTime](xref:System.DateTime) プロパティを使用すると、変換によって [DateTimeOffset](xref:System.DateTimeOffset) 値と UTC との関係に関するすべての情報が失われます。 このことは、UTC 時刻またはシステムの現地時刻に対応する [DateTimeOffset](xref:System.DateTimeOffset) 値に影響を与えます。これは、[DateTime](xref:System.DateTime) 構造体が、その [Kind](xref:System.DateTime.Kind) プロパティでこれらの 2 つのタイム ゾーンのみを反映するためです。

[DateTimeOffset](xref:System.DateTimeOffset) を [DateTime](xref:System.DateTime) 値に変換するときにできるだけ多くのタイム ゾーン情報を保持するには、[DateTimeOffset.UtcDateTime](xref:System.DateTimeOffset.UtcDateTime) プロパティと [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) プロパティを使用します。 

## <a name="converting-a-utc-time"></a>UTC 時刻の変換

変換された [DateTime](xref:System.DateTime) 値が UTC 時刻であることを示すには、[DateTimeOffset.UtcDateTime](xref:System.DateTimeOffset.UtcDateTime) プロパティの値を取得します。 このプロパティは、[DateTimeOffset.DateTime](xref:System.DateTimeOffset.DateTime) プロパティと次の 2 つの点で異なります。

* [Kind](xref:System.DateTime.Kind) プロパティが [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) である [DateTime](xref:System.DateTime) 値を返します。

* [DateTimeOffset.Offset](xref:System.DateTimeOffset.Offset) プロパティ値が [TimeSpan.Zero](xref:System.TimeSpan.Zero) と等しくない場合、時刻を UTC に変換します。

> [!NOTE]
> アプリケーションで、[DateTime](xref:System.DateTime) 値によってある時点を明確に識別する必要がある場合、[DateTimeOffset](xref:System.DateTimeOffset) から [DateTime](xref:System.DateTime) へのすべての変換を処理するために、[DateTimeOffset.UtcDateTime](xref:System.DateTimeOffset.UtcDateTime) プロパティの使用を検討してください。

次のコードは、[UtcDateTime](xref:System.DateTimeOffset.UtcDateTime) プロパティを使用して、オフセットが [TimeSpan.Zero](xref:System.TimeSpan.Zero) と等しい [DateTimeOffset](xref:System.DateTimeOffset) 値を [DateTime](xref:System.DateTime) 値に変換します。

```csharp
DateTimeOffset utcTime1 = new DateTimeOffset(2008, 6, 19, 7, 0, 0, TimeSpan.Zero);
DateTime utcTime2 = utcTime1.UtcDateTime;
Console.WriteLine("{0} converted to {1} {2}", 
                  utcTime1, 
                  utcTime2, 
                  utcTime2.Kind.ToString());
// The example displays the following output to the console:
//   6/19/2008 7:00:00 AM +00:00 converted to 6/19/2008 7:00:00 AM Utc
```

```vb
Dim utcTime1 As New DateTimeOffset(#06/19/2008 7:00AM#, TimeSpan.Zero)
Dim utcTime2 As Date = utcTime1.UtcDateTime
Console.WriteLine("{0} converted to {1} {2}", _
                  utcTime1, _
                  utcTime2, _
                  utcTime2.Kind.ToString())
' The example displays the following output to the console:
'   6/19/2008 7:00:00 AM +00:00 converted to 6/19/2008 7:00:00 AM Utc
```

次のコードは、UtcDateTime プロパティを使用して、[DateTimeOffset](xref:System.DateTimeOffset) 値に対してタイム ゾーン変換と型変換の両方を実行します。

```csharp
DateTimeOffset originalTime = new DateTimeOffset(2008, 6, 19, 7, 0, 0, new TimeSpan(5, 0, 0));
DateTime utcTime = originalTime.UtcDateTime;
Console.WriteLine("{0} converted to {1} {2}", 
                  originalTime, 
                  utcTime, 
                  utcTime.Kind.ToString());
// The example displays the following output to the console:
//       6/19/2008 7:00:00 AM +05:00 converted to 6/19/2008 2:00:00 AM Utc
```

```vb
Dim originalTime As New DateTimeOffset(#6/19/2008 7:00AM#, _
                                       New TimeSpan(5, 0, 0))
Dim utcTime As Date = originalTime.UtcDateTime
Console.WriteLine("{0} converted to {1} {2}", _ 
                  originalTime, _
                  utcTime, _
                  utcTime.Kind.ToString())
' The example displays the following output to the console:
'       6/19/2008 7:00:00 AM +05:00 converted to 6/19/2008 2:00:00 AM Utc
```

## <a name="converting-a-local-time"></a>現地時刻の変換

[DateTimeOffset](xref:System.DateTimeOffset) 値が現地時刻を表すことを示すには、[DateTimeOffset.DateTime](xref:System.DateTimeOffset.DateTime) プロパティによって返される [DateTime](xref:System.DateTime) 値を静的な [DateTime.SpecifyKind(DateTime, DateTimeKind)](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)) メソッドに渡します。 このメソッドは、その最初のパラメーターとして渡された日時を返しますが、[Kind](xref:System.DateTime.Kind) プロパティを、その 2 番目のパラメーターによって指定された値に設定します。 次のコードは、オフセットがローカル タイム ゾーンのオフセットに対応する [DateTimeOffset](xref:System.DateTimeOffset) 値を変換する際に、[SpecifyKind(DateTime, DateTimeKind)](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)) メソッドを使用します。

```csharp
DateTime sourceDate = new DateTime(2008, 6, 19, 7, 0, 0);
DateTimeOffset utcTime1 = new DateTimeOffset(sourceDate, 
                          TimeZoneInfo.Local.GetUtcOffset(sourceDate));
DateTime utcTime2 = utcTime1.DateTime;
if (utcTime1.Offset.Equals(TimeZoneInfo.Local.GetUtcOffset(utcTime1.DateTime))) 
   utcTime2 = DateTime.SpecifyKind(utcTime2, DateTimeKind.Local);

Console.WriteLine("{0} converted to {1} {2}", 
                  utcTime1, 
                  utcTime2, 
                  utcTime2.Kind.ToString());
// The example displays the following output to the console:
//   6/19/2008 7:00:00 AM -07:00 converted to 6/19/2008 7:00:00 AM Local
```

```vb
Dim sourceDate As Date = #06/19/2008 7:00AM#
Dim utcTime1 As New DateTimeOffset(sourceDate, _
                                   TimeZoneInfo.Local.GetUtcOffset(sourceDate))
Dim utcTime2 As Date = utcTime1.DateTime
If utcTime1.Offset.Equals(TimeZoneInfo.Local.GetUtcOffset(utcTime1.DateTime)) Then
   utcTime2 = DateTime.SpecifyKind(utcTime2, DateTimeKind.Local)
End If   
Console.WriteLine("{0} converted to {1} {2}", _
                  utcTime1, _
                  utcTime2, _
                  utcTime2.Kind.ToString())
' The example displays the following output to the console:
'   6/19/2008 7:00:00 AM -07:00 converted to 6/19/2008 7:00:00 AM Local
```

[DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) プロパティを使用して、[DateTimeOffset](xref:System.DateTimeOffset) 値をローカルの [DateTime](xref:System.DateTime) 値に変換することもできます。 返される [DateTime](xref:System.DateTime) 値の [Kind](xref:System.DateTime.Kind) プロパティは、[DateTimeKind.Local](xref:System.DateTimeKind.Local) です。 次のコードは、オフセットがローカル タイム ゾーンのオフセットに対応する [DateTimeOffset](xref:System.DateTimeOffset) 値を変換する際に、[DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) プロパティを使用します。

```csharp
DateTime sourceDate = new DateTime(2008, 6, 19, 7, 0, 0);
DateTimeOffset localTime1 = new DateTimeOffset(sourceDate, 
                          TimeZoneInfo.Local.GetUtcOffset(sourceDate));
DateTime localTime2 = localTime1.LocalDateTime;

Console.WriteLine("{0} converted to {1} {2}", 
                  localTime1, 
                  localTime2, 
                  localTime2.Kind.ToString());
// The example displays the following output to the console:
//   6/19/2008 7:00:00 AM -07:00 converted to 6/19/2008 7:00:00 AM Local
```

```vb
Dim sourceDate As Date = #06/19/2008 7:00AM#
Dim localTime1 As New DateTimeOffset(sourceDate, _
                                   TimeZoneInfo.Local.GetUtcOffset(sourceDate))
Dim localTime2 As Date = localTime1.LocalDateTime
Console.WriteLine("{0} converted to {1} {2}", _
                  localTime1, _
                  localTime2, _
                  localTime2.Kind.ToString())
' The example displays the following output to the console:
'   6/19/2008 7:00:00 AM -07:00 converted to 6/19/2008 7:00:00 AM Local 
```

[DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) プロパティを使用して [DateTime](xref:System.DateTime) 値を取得する場合、このプロパティの `get` アクセサーは、最初に [DateTimeOffset](xref:System.DateTimeOffset) 値を UTC に変換してから、[DateTimeOffset.ToLocalTime](xref:System.DateTimeOffset) メソッドを呼び出して現地時刻に変換します。 つまり、[DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) プロパティから値を取得して、型変換を実行するのと同時にタイム ゾーン変換を実行できます。 また、変換の実行にローカル タイム ゾーンの調整規則が適用されることも意味します。 次のコードは、[DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) プロパティを使用して型変換とタイム ゾーン変換の両方を実行する例を示しています。

```csharp
DateTimeOffset originalDate;
DateTime localDate;

// Convert time originating in a different time zone
originalDate = new DateTimeOffset(2008, 6, 18, 7, 0, 0, 
                                  new TimeSpan(-5, 0, 0));
localDate = originalDate.LocalDateTime;
Console.WriteLine("{0} converted to {1} {2}", 
                  originalDate, 
                  localDate, 
                  localDate.Kind.ToString());
// Convert time originating in a different time zone 
// so local time zone's adjustment rules are applied
originalDate = new DateTimeOffset(2007, 11, 4, 4, 0, 0, 
                                  new TimeSpan(-5, 0, 0));
localDate = originalDate.LocalDateTime;
Console.WriteLine("{0} converted to {1} {2}", 
                  originalDate, 
                  localDate, 
                  localDate.Kind.ToString());
// The example displays the following output to the console:
//       6/19/2008 7:00:00 AM -05:00 converted to 6/19/2008 5:00:00 AM Local
//       11/4/2007 4:00:00 AM -05:00 converted to 11/4/2007 1:00:00 AM Local
```

```vb
Dim originalDate As DateTimeOffset
Dim localDate As Date

' Convert time originating in a different time zone
originalDate = New DateTimeOffset(#06/19/2008 7:00AM#, _
                                  New TimeSpan(-5, 0, 0))
localDate = originalDate.LocalDateTime
Console.WriteLine("{0} converted to {1} {2}", _
                  originalDate, _
                  localDate, _
                  localDate.Kind.ToString())
' Convert time originating in a different time zone 
' so local time zone's adjustment rules are applied
originalDate = New DateTimeOffset(#11/04/2007 4:00AM#, _
                                  New TimeSpan(-5, 0, 0))
localDate = originalDate.LocalDateTime
Console.WriteLine("{0} converted to {1} {2}", _
                  originalDate, _
                  localDate, _
                  localDate.Kind.ToString())
' The example displays the following output to the console:
'       6/19/2008 7:00:00 AM -05:00 converted to 6/19/2008 5:00:00 AM Local
'       11/4/2007 4:00:00 AM -05:00 converted to 11/4/2007 1:00:00 AM Local
```

## <a name="a-generalpurpose-conversion-method"></a>汎用変換メソッド

次の例では、[DateTimeOffset](xref:System.DateTimeOffset) 値を [DateTime](xref:System.DateTime) 値に変換する `ConvertFromDateTimeOffset` という名前のメソッドを定義します。 オフセットに基づき、[DateTimeOffset](xref:System.DateTimeOffset) 値が UTC 時刻、現地時刻、またはその他の時刻であるかどうかを判断し、その結果に応じて、返される日時値の [Kind](xref:System.DateTime.Kind) プロパティを定義します。 

```csharp
static DateTime ConvertFromDateTimeOffset(DateTimeOffset dateTime)
{
   if (dateTime.Offset.Equals(TimeSpan.Zero))
      return dateTime.UtcDateTime;
   else if (dateTime.Offset.Equals(TimeZoneInfo.Local.GetUtcOffset(dateTime.DateTime)))
      return DateTime.SpecifyKind(dateTime.DateTime, DateTimeKind.Local);
   else
      return dateTime.DateTime;   
}
```

```vb
Function ConvertFromDateTimeOffset(dateTime As DateTimeOffset) As Date
   If dateTime.Offset.Equals(TimeSpan.Zero) Then
      Return dateTime.UtcDateTime
   ElseIf dateTime.Offset.Equals(TimeZoneInfo.Local.GetUtcOffset(dateTime.DateTime))
      Return Date.SpecifyKind(dateTime.DateTime, DateTimeKind.Local)
   Else
      Return dateTime.DateTime   
   End If
```

次の例では、`ConvertFromDateTimeOffset` メソッドを呼び出して、UTC 時刻、現地時刻、および米国の中部標準時ゾーンの時刻を表す [DateTimeOffset](xref:System.DateTimeOffset) 値を変換します。

```csharp
DateTime timeComponent = new DateTime(2008, 6, 19, 7, 0, 0);
DateTime returnedDate; 

// Convert UTC time
DateTimeOffset utcTime = new DateTimeOffset(timeComponent, TimeSpan.Zero);
returnedDate = ConvertFromDateTimeOffset(utcTime); 
Console.WriteLine("{0} converted to {1} {2}", 
                  utcTime, 
                  returnedDate, 
                  returnedDate.Kind.ToString());

// Convert local time
DateTimeOffset localTime = new DateTimeOffset(timeComponent, 
                           TimeZoneInfo.Local.GetUtcOffset(timeComponent)); 
returnedDate = ConvertFromDateTimeOffset(localTime);                                          
Console.WriteLine("{0} converted to {1} {2}", 
                  localTime, 
                  returnedDate, 
                  returnedDate.Kind.ToString());

// Convert Central Standard Time
DateTimeOffset cstTime = new DateTimeOffset(timeComponent, 
               TimeZoneInfo.FindSystemTimeZoneById("Central Standard Time").GetUtcOffset(timeComponent));
returnedDate = ConvertFromDateTimeOffset(cstTime);
Console.WriteLine("{0} converted to {1} {2}", 
                  cstTime, 
                  returnedDate, 
                  returnedDate.Kind.ToString());
// The example displays the following output to the console:
//    6/19/2008 7:00:00 AM +00:00 converted to 6/19/2008 7:00:00 AM Utc
//    6/19/2008 7:00:00 AM -07:00 converted to 6/19/2008 7:00:00 AM Local
//    6/19/2008 7:00:00 AM -05:00 converted to 6/19/2008 7:00:00 AM Unspecified
```

```vb
Dim timeComponent As Date = #06/19/2008 7:00AM#
Dim returnedDate As Date 

' Convert UTC time
Dim utcTime As New DateTimeOffset(timeComponent, TimeSpan.Zero)
returnedDate = ConvertFromDateTimeOffset(utcTime) 
Console.WriteLine("{0} converted to {1} {2}", _
                  utcTime, _
                  returnedDate, _
                  returnedDate.Kind.ToString())

' Convert local time
Dim localTime As New DateTimeOffset(timeComponent, _
                                    TimeZoneInfo.Local.GetUtcOffset(timeComponent)) 
returnedDate = ConvertFromDateTimeOffset(localTime)                                                                  
Console.WriteLine("{0} converted to {1} {2}", _
                  localTime, _
                  returnedDate, _
                  returnedDate.Kind.ToString())

' Convert Central Standard Time
Dim cstTime As New DateTimeOffset(timeComponent, _
               TimeZoneInfo.FindSystemTimeZoneById("Central Standard Time").GetUtcOffset(timeComponent))
returnedDate = ConvertFromDateTimeOffset(cstTime)                                                                  
Console.WriteLine("{0} converted to {1} {2}", _
                  cstTime, _
                  returnedDate, _
                  returnedDate.Kind.ToString())
' The example displays the following output to the console:
'    6/19/2008 7:00:00 AM +00:00 converted to 6/19/2008 7:00:00 AM Utc
'    6/19/2008 7:00:00 AM -07:00 converted to 6/19/2008 7:00:00 AM Local
'    6/19/2008 7:00:00 AM -05:00 converted to 6/19/2008 7:00:00 AM Unspecified
```

このコードは次の 2 つのことを前提としますが、アプリケーションおよびその日時値のソースによっては常に有効とは限らないことに注意してください。

* オフセットが [TimeSpan.Zero](xref:System.TimeSpan.Zero) である日時値が UTC を表すことを前提とします。 実際には、UTC は特定のタイム ゾーンの時刻ではなく、世界のタイム ゾーンの時刻を標準化する際に基準となる時刻です。 タイム ゾーンのオフセットが [Zero](xref:System.TimeSpan.Zero) である場合もあります。

* オフセットがローカル タイム ゾーンのオフセットと等しい日時が、ローカル タイム ゾーンを表すことを前提とします。 日時値は元のタイム ゾーンとの関連付けが解除されているので、これは該当しない場合があります。日時は、同じオフセットを持つ別のタイム ゾーンに由来する可能性があります。

## <a name="see-also"></a>関連項目

[日付、時刻およびタイム ゾーン](index.md)







<!--HONumber=Nov16_HO1-->


