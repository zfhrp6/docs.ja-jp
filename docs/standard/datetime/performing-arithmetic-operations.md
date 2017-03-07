---
title: "日付と時刻を使用した算術演算の実行"
description: "日付と時刻を使用した算術演算の実行"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/16/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 589ac5ec-8365-4a0d-bc38-72183718110c
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: b872cc4c2b799ddafc9df263795d860754d1ec17
ms.lasthandoff: 03/02/2017

---

# <a name="performing-arithmetic-operations-with-dates-and-times"></a>日付と時刻を使用した算術演算の実行

[System.DateTime](xref:System.DateTime) 構造体と [System.DateTimeOffset](xref:System.DateTimeOffset) 構造体には、その値に対して算術演算を実行するメンバーが用意されていますが、算術演算の結果は大きく異なります。 この記事では、それらの相違点を検討し、日付と時刻のデータがどの程度タイム ゾーンに対応しているかを明らかにして、日付と時刻のデータを使用してタイム ゾーンに完全に対応した操作を実行する方法について説明します。

## <a name="comparisons-and-arithmetic-operations-with-datetime-values"></a>DateTime 値を使用した比較および算術演算

[System.DateTime](xref:System.DateTime) 値は、制限付きでタイム ゾーンに対応しています。 [DateTime.Kind](xref:System.DateTime.Kind) プロパティでは、[System.DateTimeKind](xref:System.DateTimeKind) 値を日付と時刻に割り当てて、その日付と時刻が現地時刻、世界協定時刻 (UTC)、またはタイム ゾーンが指定されていない時刻のどれを表すかを示すことができます。 ただし、この制限付きのタイム ゾーン情報は、[DateTime](xref:System.DateTime) 値に対して比較操作を行うか、日付と時刻の算術演算を実行するときには無視されます。 次の例では、現在の現地時刻と現在の UTC 時刻を比較することで、この問題を示しています。

```csharp
using System;

public enum TimeComparison
{
   EarlierThan = -1,
   TheSameAs = 0,
   LaterThan = 1
}

public class DateManipulation
{
   public static void Main()
   {
      DateTime localTime = DateTime.Now;
      DateTime utcTime = DateTime.UtcNow;

      Console.WriteLine("Difference between {0} and {1} time: {2}:{3} hours", 
                        localTime.Kind.ToString(), 
                        utcTime.Kind.ToString(), 
                        (localTime - utcTime).Hours, 
                        (localTime - utcTime).Minutes);
      Console.WriteLine("The {0} time is {1} the {2} time.", 
                        localTime.Kind.ToString(), 
                        Enum.GetName(typeof(TimeComparison), localTime.CompareTo(utcTime)), 
                        utcTime.Kind.ToString());  
   }
}
// If run in the U.S. Pacific Standard Time zone, the example displays 
// the following output to the console:
//    Difference between Local and Utc time: -7:0 hours
//    The Local time is EarlierThan the Utc time.
```

```vb
Public Enum TimeComparison As Integer
   EarlierThan = -1
   TheSameAs = 0
   LaterThan = 1
End Enum

Module DateManipulation
   Public Sub Main()
      Dim localTime As Date = Date.Now
      Dim utcTime As Date = Date.UtcNow

      Console.WriteLine("Difference between {0} and {1} time: {2}:{3} hours", _
                        localTime.Kind.ToString(), _
                        utcTime.Kind.ToString(), _
                        (localTime - utcTime).Hours, _
                        (localTime - utcTime).Minutes)
      Console.WriteLine("The {0} time is {1} the {2} time.", _
                        localTime.Kind.ToString(), _ 
                        [Enum].GetName(GetType(TimeComparison), localTime.CompareTo(utcTime)), _
                        utcTime.Kind.ToString())  
      ' If run in the U.S. Pacific Standard Time zone, the example displays 
      ' the following output to the console:
      '    Difference between Local and Utc time: -7:0 hours
      '    The Local time is EarlierThan the Utc time.                                                    
   End Sub
End Module
```

[DateTime.CompareTo(DateTime, DateTime)](xref:System.DateTime.Compare(System.DateTime,System.DateTime)) メソッドは、現地時刻が UTC 時刻より早い (より小さい) という結果を出力しており、減算の操作は、UTC と米国の太平洋標準時ゾーンにあるシステムの現地時刻との差が7 時間であることを示しています。 しかし、これら&2; つの値は、ある特定の時点を異なる表現で示したものであるため、この場合、時間差の原因は、UTC を基準としたローカル タイム ゾーンのオフセットにあることは明らかです。 

一般的に、[DateTimeKind](xref:System.DateTimeKind) プロパティは、[DateTime](xref:System.DateTime) の比較および算術メソッドによって返される結果に影響を与えません (2 つの同じ時点の比較結果が示すとおり)。ただし、その結果の解釈には影響を与えることがあります。 例:

* 算術演算の実行対象となる&2; つの日付と時刻の値の [DateTimeKind](xref:System.DateTimeKind) プロパティが両方とも [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) である場合、実行結果には、2 つの値の実際の時間差が反映されます。 同様に、そのような&2; つの日付と時刻の値を比較した結果には、2 つの時間の関係が正確に反映されます。

* 算術演算または比較操作の実行対象となる&2; つの日付と時刻の値の [DateTimeKind](xref:System.DateTimeKind) プロパティが両方とも [DateTimeKind.Local](xref:System.DateTimeKind.Local) であるか、または&2; つの日付と時刻の値の [DateTimeKind](xref:System.DateTimeKind) プロパティ値が異なる場合、実行結果には、2 つの値の間の時刻差が反映されます。 

* ローカルの日付と時刻の値に対する算術演算または比較操作では、特定の値があいまいであるかや、無効であるかどうかは考慮されず、ローカル タイム ゾーンでの夏時間の開始や終了による調整規則の影響についても考慮されません。

* UTC と現地時刻の差を比較または計算する操作の結果には、UTC を基準としたローカル タイム ゾーンのオフセットに等しい時間差が含まれます。 

* タイム ゾーンが指定されていない時刻と UTC または現地時刻との差を比較または計算する操作では、単純な時刻差が反映されます。 タイム ゾーンの違いは考慮されず、結果にはタイム ゾーン調整規則の適用が反映されません。 

* タイム ゾーンが指定されていない&2; つの時刻の差を比較または計算する操作の結果には、2 つの異なるタイム ゾーンの時刻の差を反映した未知の時間差が含まれる場合があります。

多くの場合、タイム ゾーンの違いは日付と時刻の計算には影響しないか、または日付と時刻のデータのコンテキストによって比較操作や算術演算の意味が規定されます。 これらの詳細については、「[DateTime、DateTimeOffset、TimeSpan、および TimeZoneInfo の使い分け](choosing-between-datetime.md)」をご覧ください。

## <a name="comparisons-and-arithmetic-operations-with-datetimeoffset-values"></a>DateTimeOffset 値を使用した比較および算術演算

[System.DateTimeOffset](xref:System.DateTimeOffset) 値には、日付と時刻だけでなく、UTC を基準としてその日付と時刻を明確に定義するオフセットが含まれています。 このため、[System.DateTime](xref:System.DateTime) 値とはいくらか異なる等価性を規定できるようになります。 [DateTime](xref:System.DateTime) 値が等しくなるのは日付と時刻の値が同じ場合ですが、[DateTimeOffset](xref:System.DateTimeOffset) 値が等しくなるのは、両方の値が同じ時点を表す場合です。 これにより、2 つの日付と時刻の間隔を決定する比較操作やほとんどの算術演算では、[DateTimeOffset](xref:System.DateTimeOffset) 値を使用すると、より正確な結果を得ることができ、結果を正しく解釈する手間を減らすことができます。 次の例では、現地時刻と UTC の DateTime 値を比較した前の例に [DateTimeOffset](xref:System.DateTimeOffset) を使用して、動作の違いを示しています。

```csharp
using System;

public enum TimeComparison
{
   EarlierThan = -1,
   TheSameAs = 0,
   LaterThan = 1
}

public class DateTimeOffsetManipulation
{
   public static void Main()
   {
      DateTimeOffset localTime = DateTimeOffset.Now;
      DateTimeOffset utcTime = DateTimeOffset.UtcNow;

      Console.WriteLine("Difference between local time and UTC: {0}:{1:D2} hours", 
                        (localTime - utcTime).Hours, 
                        (localTime - utcTime).Minutes);
      Console.WriteLine("The local time is {0} UTC.", 
                        Enum.GetName(typeof(TimeComparison), localTime.CompareTo(utcTime)));  
   }
}
// Regardless of the local time zone, the example displays 
// the following output to the console:
//    Difference between local time and UTC: 0:00 hours.
//    The local time is TheSameAs UTC.
```

```vb
Public Enum TimeComparison As Integer
   EarlierThan = -1
   TheSameAs = 0
   LaterThan = 1
End Enum

Module DateTimeOffsetManipulation
   Public Sub Main()
      Dim localTime As DateTimeOffset = DateTimeOffset.Now
      Dim utcTime As DateTimeOffset = DateTimeOffset.UtcNow

      Console.WriteLine("Difference between local time and UTC: {0}:{1:D2} hours.", _
                        (localTime - utcTime).Hours, _
                        (localTime - utcTime).Minutes)
      Console.WriteLine("The local time is {0} UTC.", _
                        [Enum].GetName(GetType(TimeComparison), localTime.CompareTo(utcTime)))  
   End Sub
End Module
' Regardless of the local time zone, the example displays 
' the following output to the console:
'    Difference between local time and UTC: 0:00 hours.
'    The local time is TheSameAs UTC.
'          Console.WriteLine(e.GetType().Name)
```

この例では、[DateTimeOffset.CompareTo](xref:System.DateTimeOffset.CompareTo(System.DateTimeOffset)) メソッドが、現在の現地時刻と現在の UTC 時刻が等しいことを示しており、[DateTimeOffset](xref:System.DateTimeOffset) 値を減算することで、2 つの時刻の差が [TimeSpan.Zero](xref:System.TimeSpan.Zero) であることを示しています。 

日付と時刻の算術演算に [DateTimeOffset](xref:System.DateTimeOffset) 値を使用する際の主な制限は、[DateTimeOffset](xref:System.DateTimeOffset) 値はタイム ゾーンに一部対応していますが、完全対応しているわけではないことです。 [DateTimeOffset](xref:System.DateTimeOffset) 値のオフセットには、[DateTimeOffset](xref:System.DateTimeOffset) 変数に最初に値が割り当てられたときに UTC を基準としたタイム ゾーンのオフセットが反映されますが、その後は、タイム ゾーンと関連付けられなくなります。 特定可能な時刻との直接の関連付けは失われるため、日付と時刻の間隔に対して加算や減算を行っても、タイム ゾーンの調整規則は考慮されません。 

たとえば、米国の中部標準時のタイム ゾーンが夏時間に移行するのは、 2008 年 3 月 9 日の午前 2 時です。 つまり、中部標準時の 2008 年 3 月 9 日の午前 1 時 30 分に 2 時間 30 分の間隔を加算すると、日付と時刻は 2008 年 3 月 9 日の 午前 5 時になります。 しかし、次の例に示すように、加算の結果は 2008 年 3 月 9 日の 午前 4 時です。 この操作の結果は正しい時点を表していますが、目的のタイム ゾーンの時刻ではありません (つまり、予想されるタイム ゾーンのオフセットが適用されていません)。

```csharp
using System;

public class IntervalArithmetic
{
   public static void Main()
   {
      DateTime generalTime = new DateTime(2008, 3, 9, 1, 30, 0);
      const string tzName = "Central Standard Time";
      TimeSpan twoAndAHalfHours = new TimeSpan(2, 30, 0);

      // Instantiate DateTimeOffset value to have correct CST offset
      try
      {
         DateTimeOffset centralTime1 = new DateTimeOffset(generalTime, 
                    TimeZoneInfo.FindSystemTimeZoneById(tzName).GetUtcOffset(generalTime));

         // Add two and a half hours      
         DateTimeOffset centralTime2 = centralTime1.Add(twoAndAHalfHours);
         // Display result
         Console.WriteLine("{0} + {1} hours = {2}", centralTime1, 
                                                    twoAndAHalfHours.ToString(), 
                                                    centralTime2);  
      }
      catch (TimeZoneNotFoundException)
      {
         Console.WriteLine("Unable to retrieve Central Standard Time zone information.");
      }
   }
}
// The example displays the following output to the console:
//    3/9/2008 1:30:00 AM -06:00 + 02:30:00 hours = 3/9/2008 4:00:00 AM -06:00
```

```vb
Module IntervalArithmetic
   Public Sub Main()
      Dim generalTime As Date = #03/09/2008 1:30AM#
      Const tzName As String = "Central Standard Time"
      Dim twoAndAHalfHours As New TimeSpan(2, 30, 0)

      ' Instantiate DateTimeOffset value to have correct CST offset
      Try
         Dim centralTime1 As New DateTimeOffset(generalTime, _
                    TimeZoneInfo.FindSystemTimeZoneById(tzName).GetUtcOffset(generalTime))

         ' Add two and a half hours      
         Dim centralTime2 As DateTimeOffset = centralTime1.Add(twoAndAHalfHours)
         ' Display result
         Console.WriteLine("{0} + {1} hours = {2}", centralTime1, _
                                                    twoAndAHalfHours.ToString(), _
                                                    centralTime2)   
      Catch e As TimeZoneNotFoundException
         Console.WriteLine("Unable to retrieve Central Standard Time zone information.")
      End Try
   End Sub
End Module
' The example displays the following output to the console:
'    3/9/2008 1:30:00 AM -06:00 + 02:30:00 hours = 3/9/2008 4:00:00 AM -06:00
```

## <a name="arithmetic-operations-with-times-in-time-zones"></a>タイム ゾーンの時刻を使用した算術演算

[System.TimeZoneInfo](xref:System.TimeZoneInfo) クラスには、日付と時刻の算術演算を実行するときに調整規則を自動的に適用するメソッドは用意されていません。 ただし、あるタイム ゾーンの時刻を UTC に変換してから算術演算を実行し、その後 UTC から元のタイム ゾーンの時刻に再変換することで、調整規則を適用したときと同じ結果を得ることができます。 詳細については、「[方法 : 日付と時刻の演算でタイム ゾーンを使用する](use-time-zones-in-arithmetic.md)」をご覧ください。

たとえば、次のコードは、2008 年 3 月 9 日の午前 2 時に 2 時間 30 分を加算する 前のコードと似ています。 ただし、中部標準時を UTC に変換した後に日付と時刻の算術演算を実行し、その結果を UTC から中部標準時に変換するため、得られた時刻は中部標準時タイム ゾーンの夏時間への移行を反映しています。

```csharp
using System;

public class TimeZoneAwareArithmetic
{
   public static void Main()
   {
      const string tzName = "Central Standard Time";

      DateTime generalTime = new DateTime(2008, 3, 9, 1, 30, 0);
      TimeZoneInfo cst = TimeZoneInfo.FindSystemTimeZoneById(tzName);
      TimeSpan twoAndAHalfHours = new TimeSpan(2, 30, 0);

      // Instantiate DateTimeOffset value to have correct CST offset
      try
      {
         DateTimeOffset centralTime1 = new DateTimeOffset(generalTime, 
                                       cst.GetUtcOffset(generalTime));

         // Add two and a half hours
         DateTimeOffset utcTime = centralTime1.ToUniversalTime();
         utcTime += twoAndAHalfHours;

         DateTimeOffset centralTime2 = TimeZoneInfo.ConvertTime(utcTime, cst);
         // Display result
         Console.WriteLine("{0} + {1} hours = {2}", centralTime1, 
                                                    twoAndAHalfHours.ToString(), 
                                                    centralTime2);  
      }
      catch (TimeZoneNotFoundException)
      {
         Console.WriteLine("Unable to retrieve Central Standard Time zone information.");
      }
   }
}
// The example displays the following output to the console:
//    3/9/2008 1:30:00 AM -06:00 + 02:30:00 hours = 3/9/2008 5:00:00 AM -05:00
```

```vb
Module TimeZoneAwareArithmetic
   Public Sub Main()
      Const tzName As String = "Central Standard Time"

      Dim generalTime As Date = #03/09/2008 1:30AM#
      Dim cst As TimeZoneInfo = TimeZoneInfo.FindSystemTimeZoneById(tzName) 
      Dim twoAndAHalfHours As New TimeSpan(2, 30, 0)

      ' Instantiate DateTimeOffset value to have correct CST offset
      Try
         Dim centralTime1 As New DateTimeOffset(generalTime, _
                    cst.GetUtcOffset(generalTime))

         ' Add two and a half hours 
         Dim utcTime As DateTimeOffset = centralTime1.ToUniversalTime()
         utcTime += twoAndAHalfHours

         Dim centralTime2 As DateTimeOffset = TimeZoneInfo.ConvertTime(utcTime, cst)
         ' Display result
         Console.WriteLine("{0} + {1} hours = {2}", centralTime1, _
                                                    twoAndAHalfHours.ToString(), _
                                                    centralTime2)   
      Catch e As TimeZoneNotFoundException
         Console.WriteLine("Unable to retrieve Central Standard Time zone information.")
      End Try
   End Sub
End Module
' The example displays the following output to the console:
'    3/9/2008 1:30:00 AM -06:00 + 02:30:00 hours = 3/9/2008 5:00:00 AM -05:00
```

## <a name="see-also"></a>関連項目

[日付、時刻およびタイム ゾーン](index.md)

[方法: 日付と時刻の演算でタイム ゾーンを使用する](use-time-zones-in-arithmetic.md)



