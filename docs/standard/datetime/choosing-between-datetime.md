---
title: "DateTime、DateTimeOffset、TimeSpan、および TimeZoneInfo の使い分け"
description: "DateTime、DateTimeOffset、TimeSpan、および TimeZoneInfo の使い分け"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 08/11/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 2dd84ee8-9f0f-4054-9537-155857a460cd
translationtype: Human Translation
ms.sourcegitcommit: c40c28da09e8a122b542463c197196c82c81dd19
ms.openlocfilehash: e5b709cb82c680edf454d0a8fc9ff27e6d26c138

---

# <a name="choosing-between-datetime-datetimeoffset-timespan-and-timezoneinfo"></a>DateTime、DateTimeOffset、TimeSpan、および TimeZoneInfo の使い分け

日時情報を使用する .NET アプリケーションは非常に多様であり、その情報をさまざまな方法で使用できます。 より一般的な日時情報の用途には、次の 1 つ以上が含まれます。

* 日付のみを反映する (時刻情報は重要ではない)。

* 時刻のみを反映する (日付情報は重要ではない)。

* 特定の時刻と場所に関連付けられていない抽象日時を反映する (たとえば、国際的チェーンのほとんどのストアは週中の午前 9:00 にオープンする)。

* .NET アプリケーションの外部ソースから日時情報を取得する (通常、日時情報は単純なデータ型に格納される)。

* 単一の時点を一意かつ明確に識別する。 ホスト システムでのみ日付と時刻を明確にする必要があるアプリケーションもあれば、システム全体で明確にする必要があるアプリケーションもあります (つまり、1 つのシステムでシリアル化される日付は有意に逆シリアル化し、世界中のどの場所においても別のシステムで使用できます)。 

* 関連する複数の時刻を保持する (要求元の現地時刻やサーバーの Web 要求受信時刻など)。

* 日付と時刻の演算を実行する (これにより、おそらく単一時点が一意かつ明確に識別される)。 

.NET には、[System.DateTime](xref:System.DateTime)、[System.DateTimeOffset](xref:System.DateTimeOffset)、[System.TimeSpan](xref:System.TimeSpan)、[System.TimeZoneInfo](xref:System.TimeZoneInfo) の各型が含まれます。このすべては、日付と時刻を使用するアプリケーションを構築するために使用できます。 

> [!NOTE]
> このトピックでは古い `TimeZone` 型については説明されません。その機能は、[System.TimeZoneInfo](xref:System.TimeZoneInfo) クラスにほぼ完全に組み込まれているからです。 開発者は可能な限り、`TimeZone` クラスの代わりに [System.TimeZoneInfo](xref:System.TimeZoneInfo) クラスを使用する必要があります。


## <a name="the-datetime-structure"></a>DateTime 構造体

[System.DateTime](xref:System.DateTime) 値は、特定の日付と時刻を定義します。 これには日付と時刻が属するタイム ゾーンに関する限られた情報を提供する [Kind](xref:System.DateTime.Kind) プロパティが含まれています。 [Kind](xref:System.DateTime.Kind) プロパティによって返される [DateTimeKind](xref:System.DateTimeKind) 値は、[DateTime](xref:System.DateTime) 値が現地時刻 ([DateTimeKind.Local](xref:System.DateTimeKind.Local))、世界協定時刻 (UTC) ([DateTimeKind.Utc](xref:System.DateTimeKind.Utc))、指定されていない時刻 ([DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified)) のうちのどれを表すかを示します。

[DateTime](xref:System.DateTime) 構造体は、次の操作を実行するアプリケーションに適しています。 

* 日付のみを使用するアプリケーション。

* 時刻のみを使用するアプリケーション。

* 抽象日時を使用するアプリケーション。

* タイム ゾーン情報がない日時を使用するアプリケーション。 

* UTC 日時のみを使用するアプリケーション。 

* SQL データベースなど、.NET Framework の外部ソースから日時情報を取得します。 通常、これらのソースは、[DateTime](xref:System.DateTime) 構造体と互換性のある単純な形式で日時情報を格納します。

* 日付と時刻の演算を実行しますが、これは一般的な結果に関するものです。 たとえば、6 カ月を特定の日付と時刻に加算する加算演算では、多くの場合、結果を夏時間に合わせて調整するかどうかは重要ではありません。

特定の [DateTime](xref:System.DateTime) 値が UTC を表さない場合、通常、その日付と時刻の値は、あいまいであるか、その移植性に限定されます。 たとえば、[DateTime](xref:System.DateTime) 値が現地時刻を表す場合、そのローカル タイム ゾーン内で移植することができます (つまり、同じタイム ゾーンにある別のシステムで値が逆シリアル化されると、その値は明確に単一時点を識別します)。 ローカル タイム ゾーン外では、その [DateTime](xref:System.DateTime) 値は複数の意味を持つ場合があります。 値の [Kind](xref:System.DateTime.Kind) プロパティが [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified) の場合、移植性は低くなります。同じタイム ゾーン内であいまいになり、最初にシリアル化したのと同じシステムにおいてさえもあいまいになる可能性があります。 [DateTime](xref:System.DateTime) 値が UTC を表す場合のみ、値が使用されるシステムまたはタイム ゾーンに関係なく、その値は明確に単一時点を識別します。

> [!IMPORTANT]
> [DateTime](xref:System.DateTime) データを保存または共有する際、UTC を使用する必要があり、[DateTime](xref:System.DateTime) 値の [Kind](xref:System.DateTime.Kind) プロパティを [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) に設定する必要があります。

## <a name="the-datetimeoffset-structure"></a>DateTimeOffset 構造体

[System.DateTimeOffset](xref:System.DateTimeOffset) 構造体は、日付と時刻の値、およびその値と UTC との差異を示すオフセットを表します。 そのため、値は常に明確に単一時点を識別します。 

[DateTimeOffset](xref:System.DateTimeOffset) 型には、[DateTime](xref:System.DateTime) 型のすべての機能に加え、タイム ゾーンの処理機能が含まれます。 そのため、次の操作を実行するアプリケーションに適しています。 

* 単一の時点を一意かつ明確に識別する。 [DateTimeOffset](xref:System.DateTimeOffset) 型を使用して、「現在」の意味を明確に定義し、トランザクションの時刻を記録し、システム イベントまたはアプリケーション イベントの時刻を記録し、ファイル作成時刻とファイル変更時刻を記録することができます。 

* 一般的な日付と時刻の演算を実行する。

* その時刻が 2 つの別々の値または構造体の 2 つのメンバーである場合、関連する複数の時刻を保持する。

> [!NOTE]
> [DateTimeOffset](xref:System.DateTimeOffset) 値のこの用途は、[DateTime](xref:System.DateTime) 値の用途と比べてはるかに一般的です。 その結果、[DateTimeOffset](xref:System.DateTimeOffset) はアプリケーション開発の既定の日付時刻型と見なされます。

[DateTimeOffset](xref:System.DateTimeOffset) 値は特定のタイム ゾーンと関連付けられていませんが、さまざまなタイム ゾーンから派生することができます。 これを説明するために、いくつかの [DateTimeOffset](xref:System.DateTimeOffset) 値 (ローカルの太平洋標準時を含む) が属することができるタイム ゾーンの一覧を次の例に示します。

```csharp
using System;
using System.Collections.ObjectModel;

public class TimeOffsets
{
   public static void Main()
   {
      DateTime thisDate = new DateTime(2007, 3, 10, 0, 0, 0);
      DateTime dstDate = new DateTime(2007, 6, 10, 0, 0, 0);
      DateTimeOffset thisTime;

      thisTime = new DateTimeOffset(dstDate, new TimeSpan(-7, 0, 0));
      ShowPossibleTimeZones(thisTime);

      thisTime = new DateTimeOffset(thisDate, new TimeSpan(-6, 0, 0));  
      ShowPossibleTimeZones(thisTime);

      thisTime = new DateTimeOffset(thisDate, new TimeSpan(+1, 0, 0));
      ShowPossibleTimeZones(thisTime);
   }

   private static void ShowPossibleTimeZones(DateTimeOffset offsetTime)
   {
      TimeSpan offset = offsetTime.Offset;
      ReadOnlyCollection<TimeZoneInfo> timeZones;

      Console.WriteLine("{0} could belong to the following time zones:", 
                        offsetTime.ToString());
      // Get all time zones defined on local system
      timeZones = TimeZoneInfo.GetSystemTimeZones();     
      // Iterate time zones 
      foreach (TimeZoneInfo timeZone in timeZones)
      {
         // Compare offset with offset for that date in that time zone
         if (timeZone.GetUtcOffset(offsetTime.DateTime).Equals(offset))
            Console.WriteLine("   {0}", timeZone.DisplayName);
      }
      Console.WriteLine();
   } 
}
// This example displays the following output to the console:
//       6/10/2007 12:00:00 AM -07:00 could belong to the following time zones:
//          (GMT-07:00) Arizona
//          (GMT-08:00) Pacific Time (US & Canada)
//          (GMT-08:00) Tijuana, Baja California
//       
//       3/10/2007 12:00:00 AM -06:00 could belong to the following time zones:
//          (GMT-06:00) Central America
//          (GMT-06:00) Central Time (US & Canada)
//          (GMT-06:00) Guadalajara, Mexico City, Monterrey - New
//          (GMT-06:00) Guadalajara, Mexico City, Monterrey - Old
//          (GMT-06:00) Saskatchewan
//       
//       3/10/2007 12:00:00 AM +01:00 could belong to the following time zones:
//          (GMT+01:00) Amsterdam, Berlin, Bern, Rome, Stockholm, Vienna
//          (GMT+01:00) Belgrade, Bratislava, Budapest, Ljubljana, Prague
//          (GMT+01:00) Brussels, Copenhagen, Madrid, Paris
//          (GMT+01:00) Sarajevo, Skopje, Warsaw, Zagreb
//          (GMT+01:00) West Central Africa
```

```vb
Imports System.Collections.ObjectModel

Module TimeOffsets
   Public Sub Main()
      Dim thisTime As DateTimeOffset 

      thisTime = New DateTimeOffset(#06/10/2007#, New TimeSpan(-7, 0, 0))
      ShowPossibleTimeZones(thisTime) 

      thisTime = New DateTimeOffset(#03/10/2007#, New TimeSpan(-6, 0, 0))  
      ShowPossibleTimeZones(thisTime)

      thisTime = New DateTimeOffset(#03/10/2007#, New TimeSpan(+1, 0, 0))
      ShowPossibleTimeZones(thisTime)
   End Sub

   Private Sub ShowPossibleTimeZones(offsetTime As DateTimeOffset)
      Dim offset As TimeSpan = offsetTime.Offset
      Dim timeZones As ReadOnlyCollection(Of TimeZoneInfo)

      Console.WriteLine("{0} could belong to the following time zones:", _
                        offsetTime.ToString())
      ' Get all time zones defined on local system
      timeZones = TimeZoneInfo.GetSystemTimeZones()     
      ' Iterate time zones
      For Each timeZone As TimeZoneInfo In timeZones
         ' Compare offset with offset for that date in that time zone
         If timeZone.GetUtcOffset(offsetTime.DateTime).Equals(offset) Then
            Console.WriteLine("   {0}", timeZone.DisplayName)
         End If   
      Next
      Console.WriteLine()
   End Sub
End Module
' This example displays the following output to the console:
'       6/10/2007 12:00:00 AM -07:00 could belong to the following time zones:
'          (GMT-07:00) Arizona
'          (GMT-08:00) Pacific Time (US & Canada)
'          (GMT-08:00) Tijuana, Baja California
'       
'       3/10/2007 12:00:00 AM -06:00 could belong to the following time zones:
'          (GMT-06:00) Central America
'          (GMT-06:00) Central Time (US & Canada)
'          (GMT-06:00) Guadalajara, Mexico City, Monterrey - New
'          (GMT-06:00) Guadalajara, Mexico City, Monterrey - Old
'          (GMT-06:00) Saskatchewan
'       
'       3/10/2007 12:00:00 AM +01:00 could belong to the following time zones:
'          (GMT+01:00) Amsterdam, Berlin, Bern, Rome, Stockholm, Vienna
'          (GMT+01:00) Belgrade, Bratislava, Budapest, Ljubljana, Prague
'          (GMT+01:00) Brussels, Copenhagen, Madrid, Paris
'          (GMT+01:00) Sarajevo, Skopje, Warsaw, Zagreb
'          (GMT+01:00) West Central Africa
```

この例の日付と時刻の値はそれぞれ少なくとも 3 つの異なるタイム ゾーンに属することができることを出力は示しています。 [DateTimeOffset](xref:System.DateTimeOffset) 値の 6/10/2007 は、日付と時刻の値が夏時間を表す場合、UTC のそのオフセットは必ずしも元のタイム ゾーンの基本 UTC オフセット、またはその表示名から見つかる UTC のオフセットと一致しないことを示しています。 これは、単一の [DateTimeOffset](xref:System.DateTimeOffset) 値はそのタイム ゾーンと密接に関連していないために夏時間との間のタイム ゾーンの遷移を反映することができないことを意味しています。 これは特に、日付と時刻の演算を使用して [DateTimeOffset](xref:System.DateTimeOffset) 値を操作する際に問題となる可能性があります。 タイム ゾーンの調整規則を考慮に入れた日付と時刻の演算を実行する方法については、「[日付と時刻を使用した算術演算の実行](performing-arithmetic-operations.md)」を参照してください。

## <a name="the-timespan-structure"></a>TimeSpan 構造体

[System.TimeSpan](xref:System.TimeSpan) 構造体は、時間間隔を表します。 その 2 つの一般的な用途は、次のとおりです。 

* 2 つの日付と時刻の値の間の時間を反映する。 たとえば、ある値から [DateTime](xref:System.DateTime) 値を減算すると、[TimeSpan](xref:System.TimeSpan) 値が返されます。 

* 経過時間を測定する。 たとえば、[Stopwatch.Elapsed](xref:System.Diagnostics.Stopwatch.Elapsed) プロパティは、経過時間の測定を開始する [System.Diagnostics.Stopwatch](xref:System.Diagnostics.Stopwatch) メソッドの 1 つを呼び出してから経過した時間間隔を反映する [TimeSpan](xref:System.TimeSpan) 値を返します。

値が特定時刻への参照がない値が時間を反映する際、[DateTime](xref:System.DateTime) 値の代わりに [TimeSpan](xref:System.TimeSpan) 値を使用することもできます。 この用途は [DateTime.TimeOfDay](xref:System.DateTime.TimeOfDay) および [DateTimeOffset.TimeOfDay](xref:System.DateTimeOffset.TimeOfDay) プロパティと似ています。これらのプロパティは、日付への参照なしの時間を表す [TimeSpan](xref:System.TimeSpan) 値を返します。 たとえば、[TimeSpan](xref:System.TimeSpan) 構造体を使用して、ストアの開店時刻または閉店時刻を反映したり、標準イベントが発生したときの時刻を表したりするために使用できます。

以下の例では、開店時刻と閉店時刻用の [TimeSpan](xref:System.TimeSpan) オブジェクト、およびストアのタイム ゾーンを表す [TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクトを含む `StoreInfo` 構造体を定義します。 構造体には、`IsOpenNow`、`IsOpenAt` という 2 つのメソッドも含まれます。これは、ローカル タイム ゾーンにいると想定されるユーザーによって指定された時刻にストアがオープンするかどうかを示します。  

```csharp
using System;

public struct StoreInfo
{
   public String store;
   public TimeZoneInfo tz;
   public TimeSpan open;
   public TimeSpan close;

   public bool IsOpenNow()
   {
      return IsOpenAt(DateTime.TimeOfDay);
   }

   public bool IsOpenAt(TimeSpan time)
   {
      TimeZoneInfo local = TimeZoneInfo.Local;
      TimeSpan offset = TimeZoneInfo.BaseUtcOffset;

      // Is the store in the same time zone?
      if (tz.Equals(local)) {
         return time >= open & time <= close;
      }
   }
}
```

```vb
Public Structure StoreInfo
   Dim store As String
   Dim tz As TimeZoneInfo
   Dim open As TimeSpan
   Dim close As TimeSpan

   Public Function IsOpenNow() As Boolean
      Return IsOpenAt(Date.Now.TimeOfDay)
   End Function

   Public Function IsOpenAt(time As TimeSpan) As Boolean
      Dim local As TimeZoneInfo = TimeZoneInfo.Local
      Dim offset As TimeSpan = TimeZoneInfo.Local.BaseUtcOffset

      ' Is the store in the same time zone?
      If tz.Equals(local) Then
         Return time >= open And time <= close
      Else
         Dim delta As TimeSpan = TimeSpan.Zero
         Dim storeDelta As TimeSpan = TimeSpan.Zero

         ' Is it daylight saving time in either time zone?
         If local.IsDaylightSavingTime(Date.Now.Date + time) Then
            delta = local.GetAdjustmentRules(local.GetAdjustmentRules().Length - 1).DaylightDelta
         End If
         If tz.IsDaylightSavingTime(TimeZoneInfo.ConvertTime(Date.Now.Date + time, local, tz))
            storeDelta = tz.GetAdjustmentRules(local.GetAdjustmentRules().Length - 1).DaylightDelta
         End If
         Dim comparisonTime As TimeSpan = time + (offset - tz.BaseUtcOffset).Negate() + (delta - storeDelta).Negate
         Return (comparisonTime >= open And comparisonTime <= close)
      End If
   End Function
End Structure
```

`StoreInfo` 構造体をクライアント コードで次のように使用できます。 

```csharp
public class Example
{
   public static void Main()
   {
      // Instantiate a StoreInfo object.
      var store103 = new StoreInfo();
      store103.store = "Store #103";
      store103.tz = TimeZoneInfo.FindSystemTimeZoneById("Eastern Standard Time");
      // Store opens at 8:00.
      store103.open = new TimeSpan(8, 0, 0);
      // Store closes at 9:30.
      store103.close = new TimeSpan(21, 30, 0);

      Console.WriteLine("Store is open now at {0}: {1}",
                        DateTime.TimeOfDay, store103.IsOpenNow());
      TimeSpan[] times = { new TimeSpan(8, 0, 0), new TimeSpan(21, 0, 0),
                           new TimeSpan(4, 59, 0), new TimeSpan(18, 31, 0) };
      foreach (var time in times)
         Console.WriteLine("Store is open at {0}: {1}",
                           time, store103.IsOpenAt(time));
   }
}
// The example displays the following output:
//       Store is open now at 15:29:01.6129911: True
//       Store is open at 08:00:00: True
//       Store is open at 21:00:00: False
//       Store is open at 04:59:00: False
//       Store is open at 18:31:00: False
```

```vb
Module Example
   Public Sub Main()
      ' Instantiate a StoreInfo object.
      Dim store103 As New StoreInfo()
      store103.store = "Store #103"
      store103.tz = TimeZoneInfo.FindSystemTimeZoneById("Eastern Standard Time")
      ' Store opens at 8:00.
      store103.open = new TimeSpan(8, 0, 0)
      ' Store closes at 9:30.
      store103.close = new TimeSpan(21, 30, 0)

      Console.WriteLine("Store is open now at {0}: {1}",
                        Date.Now.TimeOfDay, store103.IsOpenNow())
      Dim times() As TimeSpan = { New TimeSpan(8, 0, 0),
                                  New TimeSpan(21, 0, 0),
                                  New TimeSpan(4, 59, 0),
                                  New TimeSpan(18, 31, 0) }
      For Each time In times
         Console.WriteLine("Store is open at {0}: {1}",
                           time, store103.IsOpenAt(time))
      Next
   End Sub
End Module
' The example displays the following output:
'       Store is open now at 15:29:01.6129911: True
'       Store is open at 08:00:00: True
'       Store is open at 21:00:00: False
'       Store is open at 04:59:00: False
'       Store is open at 18:31:00: False
```

## <a name="the-timezoneinfo-class"></a>TimeZoneInfo クラス

[System.TimeZoneInfo](xref:System.TimeZoneInfo) クラスは地球のタイム ゾーンを表し、1 つのタイム ゾーンの日付と時刻の値を、別のタイム ゾーンの日付と時刻の値に変換できるようにします。 [TimeZoneInfo](xref:System.TimeZoneInfo) クラスにより、日付と時刻を使用して、どの日付と時刻の値も明確に単一時点を識別できるようにすることができます。

場合によっては、[TimeZoneInfo](xref:System.TimeZoneInfo) クラスをフル活用するために、開発作業をさらに実行する必要が生じることもあります。 日付と時刻の値は、それが属するタイム ゾーンに密接に関連付けられていません。 結果として、アプリケーションが日付と時刻をその関連タイム ゾーンとリンクするメカニズムを提供していない場合、特定の日付と時刻の値とそのタイム ゾーンの関連付けは簡単に解除されます。 この情報をリンクする 1 つの方法は、日付と時刻の値とその関連タイム ゾーン オブジェクトの両方を含むクラスまたは構造体を定義するという方法です。

日付と時刻のオブジェクトをインスタンスするときにその日付と時刻の値が属するタイム ゾーンがわかっている場合のみ、.NET でタイム ゾーンのサポートを利用できます。 特に Web またはネットワーク アプリケーションでは、これは該当しません。

## <a name="see-also"></a>関連項目

[日付、時刻およびタイム ゾーン](index.md)


<!--HONumber=Nov16_HO1-->


