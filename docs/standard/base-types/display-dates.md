---
title: "方法: グレゴリオ暦以外の暦の日付を表示する"
description: "方法: グレゴリオ暦以外の暦の日付を表示する"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 93f06e1d-544b-4ccc-a0b2-95cd674852cb
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 69a33b3e162c07a1d8a065a150c6db96f04334f6
ms.lasthandoff: 03/02/2017

---

# <a name="how-to-display-dates-in-non-gregorian-calendars"></a>方法: グレゴリオ暦以外の暦の日付を表示する

[DateTime](xref:System.DateTime) 型と [DateTimeOffset](xref:System.DateTimeOffset) 型は既定の暦としてグレゴリオ暦を使用しています。 つまり、日付と時刻値の `ToString` メソッドを呼び出すと、その日付の時刻が別の暦を使用して作成された場合でも、その日付の時刻はグレゴリオ暦の文字列形式で表示されます。 これを次の例で示します。この例では、2 つの方法を使用してペルシャ暦で日付と時刻の値を作成していますが、[ToString](xref:System.DateTime.ToString) メソッドを呼び出すと、これらの日付と時刻の値はグレゴリオ暦で表示されます。 この例では、一般的に使われているものの、特定の暦で日付を表示するには正しくない&2; つの手法が反映されています。

```csharp
PersianCalendar persianCal = new PersianCalendar();

DateTime persianDate = persianCal.ToDateTime(1387, 3, 18, 12, 0, 0, 0);
Console.WriteLine(persianDate.ToString());

persianDate = new DateTime(1387, 3, 18, persianCal);
Console.WriteLine(persianDate.ToString());
// The example displays the following output to the console:
//       6/7/2008 12:00:00 PM
//       6/7/2008 12:00:00 AM
```

```vb
Dim persianCal As New PersianCalendar()

Dim persianDate As Date = persianCal.ToDateTime(1387, 3, 18, _
                                                12, 0, 0, 0)
Console.WriteLine(persianDate.ToString())

persianDate = New DateTime(1387, 3, 18, persianCal)
Console.WriteLine(persianDate.ToString())
' The example displays the following output to the console:
'       6/7/2008 12:00:00 PM
'       6/7/2008 12:00:00 AM
```

2 つの手法は、特定の暦で日付を表示するために使用できます。 1 番目の手法では、暦は特定のカルチャの既定の暦である必要があります。 2 番目の手法は、任意の暦で使用できます。

## <a name="to-display-the-date-for-a-cultures-default-calendar"></a>カルチャの既定の暦の日付を表示するには

1. 使用する暦を表す [Calendar](xref:System.Globalization.Calendar) クラスから派生した暦オブジェクトをインスタンス化します。

2. 日付を表示するために使用される書式のカルチャを表す [CultureInfo](xref:System.Globalization.CultureInfo) オブジェクトをインスタンス化します。

3. [Array.Exists&lt;T&gt;](xref:System.Array.Exists``1(``0[],System.Predicate{``0})) メソッドを呼び出し、暦オブジェクトが [CultureInfo.OptionalCalendars](xref:System.Globalization.CultureInfo.OptionalCalendars) プロパティによって返される配列のメンバーかどうかを判断します。 これは、暦が [CultureInfo](xref:System.Globalization.CultureInfo) オブジェクトの既定の暦として使用できることを示します。 配列のメンバーでない場合は、「任意の暦で日付を表示するには」セクションの手順に従います。

4. 暦オブジェクトを [CultureInfo.DateTimeFormat](xref:System.Globalization.CultureInfo.DateTimeFormat) プロパティによって返された [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) オブジェクトの [Calendar](xref:System.Globalization.DateTimeFormatInfo.Calendar) プロパティに割り当てます。

  > [!NOTE]
  > [CultureInfo](xref:System.Globalization.CultureInfo) クラスには [Calendar](xref:System.Globalization.CultureInfo.Calendar) プロパティもあります。 ただし、これは読み取り専用で定数のため、[DateTimeFormatInfo.Calendar](xref:System.Globalization.DateTimeFormatInfo.Calendar) プロパティに割り当てられた新しい既定の暦を反映するために変更されることはありません。
  
5. [DateTime.ToString(IFormatProvider)](xref:System.DateTime.ToString(System.IFormatProvider)) または [DateTime.ToString(String,IFormatProvider)](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) のいずれかのメソッドを呼び出して、それを既定の暦が前の手順で変更された [CultureInfo](xref:System.Globalization.CultureInfo) オブジェクトに渡します。

## <a name="to-display-the-date-in-any-calendar"></a>任意の暦で日付を表示するには

1. 使用する暦を表す [Calendar](xref:System.Globalization.Calendar) クラスから派生した暦オブジェクトをインスタンス化します。

2. 日付と時刻の値の文字列形式で表示する日付と時刻の要素を決定します。

3. 表示する日付と時刻の要素ごとに、暦オブジェクトの `Get…` メソッドを呼び出します。 次のメソッドが使用できます。

    * [GetYear](xref:System.Globalization.Calendar.GetYear(System.DateTime)): 適切な暦で年を表示します。
    
    * [GetMonth](xref:System.Globalization.Calendar.GetMonth(System.DateTime)): 適切な暦で月を表示します。 
    
    * [GetDayOfMonth](xref:System.Globalization.Calendar.GetDayOfMonth(System.DateTime)): 適切な暦で月の日付を表示します。
    
    * [GetHour](xref:System.Globalization.Calendar.GetHour(System.DateTime)): 適切な暦で日の時間を表示します。
    
    * [GetMinute](xref:System.Globalization.Calendar.GetMinute(System.DateTime)): 適切な暦で時間の分を表示します。
    
    * [GetSecond](xref:System.Globalization.Calendar.GetSecond(System.DateTime)): 適切な暦で分の秒を表示します。 
    
    * [GetMilliseconds](xref:System.Globalization.Calendar.GetMilliseconds(System.DateTime)): 適切な暦で秒のミリ秒を表示します。
    
## <a name="example"></a>例
    
この例では、2 つの異なる暦を使用して日付を表示します。 ar-JO カルチャの既定の暦としてイスラム暦を定義した後の日付を表示し、その日付を fa-IR カルチャでオプションの暦としてサポートされていないペルシャ暦を使用して表示します。

```csharp
using System;
using System.Globalization;

public class CalendarDates
{
   public static void Main()
   {
      HijriCalendar hijriCal = new HijriCalendar();
      CalendarUtility hijriUtil = new CalendarUtility(hijriCal);
      DateTime dateValue1 = new DateTime(1429, 6, 29, hijriCal);
      DateTimeOffset dateValue2 = new DateTimeOffset(dateValue1, 
                                  TimeZoneInfo.Local.GetUtcOffset(dateValue1));
      CultureInfo jc = CultureInfo.CreateSpecificCulture("ar-JO");

      // Display the date using the Gregorian calendar.
      Console.WriteLine("Using the system default culture: {0}", 
                        dateValue1.ToString("d"));
      // Display the date using the ar-JO culture's original default calendar.
      Console.WriteLine("Using the ar-JO culture's original default calendar: {0}", 
                        dateValue1.ToString("d", jc));
      // Display the date using the Hijri calendar.
      Console.WriteLine("Using the ar-JO culture with Hijri as the default calendar:");
      // Display a Date value.
      Console.WriteLine(hijriUtil.DisplayDate(dateValue1, jc));
      // Display a DateTimeOffset value.
      Console.WriteLine(hijriUtil.DisplayDate(dateValue2, jc));

      Console.WriteLine();

      PersianCalendar persianCal = new PersianCalendar();
      CalendarUtility persianUtil = new CalendarUtility(persianCal);
      CultureInfo ic = CultureInfo.CreateSpecificCulture("fa-IR");

      // Display the date using the ir-FA culture's default calendar.
      Console.WriteLine("Using the ir-FA culture's default calendar: {0}",       
                        dateValue1.ToString("d", ic));
      // Display a Date value.
      Console.WriteLine(persianUtil.DisplayDate(dateValue1, ic));
      // Display a DateTimeOffset value.
      Console.WriteLine(persianUtil.DisplayDate(dateValue2, ic));
   }
}

public class CalendarUtility
{
   private Calendar thisCalendar;
   private CultureInfo targetCulture;

   public CalendarUtility(Calendar cal)
   {
      this.thisCalendar = cal;
   }

   private bool CalendarExists(CultureInfo culture)
   {
      this.targetCulture = culture;
      return Array.Exists(this.targetCulture.OptionalCalendars, 
                          this.HasSameName);
   }

   private bool HasSameName(Calendar cal)
   {
      if (cal.ToString() == thisCalendar.ToString())
         return true;
      else
         return false;
   }

   public string DisplayDate(DateTime dateToDisplay, CultureInfo culture)
   {
      DateTimeOffset displayOffsetDate = dateToDisplay;
      return DisplayDate(displayOffsetDate, culture);
   }

   public string DisplayDate(DateTimeOffset dateToDisplay, 
                             CultureInfo culture)
   {
      string specifier = "yyyy/MM/dd";

      if (this.CalendarExists(culture))
      {
         Console.WriteLine("Displaying date in supported {0} calendar...", 
                           this.thisCalendar.GetType().Name);
         culture.DateTimeFormat.Calendar = this.thisCalendar;
         return dateToDisplay.ToString(specifier, culture);
      }
      else
      {
         Console.WriteLine("Displaying date in unsupported {0} calendar...", 
                           thisCalendar.GetType().Name);

         string separator = targetCulture.DateTimeFormat.DateSeparator;

         return thisCalendar.GetYear(dateToDisplay.DateTime).ToString("0000") +
                separator +
                thisCalendar.GetMonth(dateToDisplay.DateTime).ToString("00") + 
                separator +
                thisCalendar.GetDayOfMonth(dateToDisplay.DateTime).ToString("00"); 
      }
   } 
}
// The example displays the following output to the console:
//       Using the system default culture: 7/3/2008
//       Using the ar-JO culture's original default calendar: 03/07/2008
//       Using the ar-JO culture with Hijri as the default calendar:
//       Displaying date in supported HijriCalendar calendar...
//       1429/06/29
//       Displaying date in supported HijriCalendar calendar...
//       1429/06/29
//       
//       Using the ir-FA culture's default calendar: 7/3/2008
//       Displaying date in unsupported PersianCalendar calendar...
//       1387/04/13
//       Displaying date in unsupported PersianCalendar calendar...
//       1387/04/13
```

```vb
Imports System.Globalization

Public Class CalendarDates
   Public Shared Sub Main()
      Dim hijriCal As New HijriCalendar()
      Dim hijriUtil As New CalendarUtility(hijriCal)
      Dim dateValue1 As Date = New Date(1429, 6, 29, hijriCal)
      Dim dateValue2 As DateTimeOffset = New DateTimeOffset(dateValue1, _
                                         TimeZoneInfo.Local.GetUtcOffset(dateValue1))
      Dim jc As CultureInfo = CultureInfo.CreateSpecificCulture("ar-JO")

      ' Display the date using the Gregorian calendar.
      Console.WriteLine("Using the system default culture: {0}", _
                        dateValue1.ToString("d"))
      ' Display the date using the ar-JO culture's original default calendar.
      Console.WriteLine("Using the ar-JO culture's original default calendar: {0}", _
                        dateValue1.ToString("d", jc))
      ' Display the date using the Hijri calendar.
      Console.WriteLine("Using the ar-JO culture with Hijri as the default calendar:")
      ' Display a Date value.
      Console.WriteLine(hijriUtil.DisplayDate(dateValue1, jc))
      ' Display a DateTimeOffset value.
      Console.WriteLine(hijriUtil.DisplayDate(dateValue2, jc))

      Console.WriteLine()

      Dim persianCal As New PersianCalendar()
      Dim persianUtil As New CalendarUtility(persianCal)
      Dim ic As CultureInfo = CultureInfo.CreateSpecificCulture("fa-IR")

      ' Display the date using the ir-FA culture's default calendar.
      Console.WriteLine("Using the ir-FA culture's default calendar: {0}", _      
                        dateValue1.ToString("d", ic))
      ' Display a Date value.
      Console.WriteLine(persianUtil.DisplayDate(dateValue1, ic))
      ' Display a DateTimeOffset value.
      Console.WriteLine(persianUtil.DisplayDate(dateValue2, ic))
   End Sub
End Class

Public Class CalendarUtility
   Private thisCalendar As Calendar
   Private targetCulture As CultureInfo

   Public Sub New(cal As Calendar)
      Me.thisCalendar = cal
   End Sub

   Private Function CalendarExists(culture As CultureInfo) As Boolean
      Me.targetCulture = culture
      Return Array.Exists(Me.targetCulture.OptionalCalendars, _
                          AddressOf Me.HasSameName)
   End Function 

   Private Function HasSameName(cal As Calendar) As Boolean
      If cal.ToString() = thisCalendar.ToString() Then
         Return True
      Else
         Return False
      End If
   End Function

   Public Function DisplayDate(dateToDisplay As Date, _
                               culture As CultureInfo) As String
      Dim displayOffsetDate As DateTimeOffset = dateToDisplay
      Return DisplayDate(displayOffsetDate, culture)
   End Function

   Public Function DisplayDate(dateToDisplay As DateTimeOffset, _
                               culture As CultureInfo) As String
      Dim specifier As String = "yyyy/MM/dd"

      If Me.CalendarExists(culture) Then
         Console.WriteLine("Displaying date in supported {0} calendar...", _
                           thisCalendar.GetType().Name)
         culture.DateTimeFormat.Calendar = Me.thisCalendar
         Return dateToDisplay.ToString(specifier, culture)
      Else
         Console.WriteLine("Displaying date in unsupported {0} calendar...", _
                           thisCalendar.GetType().Name)

         Dim separator As String = targetCulture.DateTimeFormat.DateSeparator

         Return thisCalendar.GetYear(dateToDisplay.DateTime).ToString("0000") & separator & _
                thisCalendar.GetMonth(dateToDisplay.DateTime).ToString("00") & separator & _
                thisCalendar.GetDayOfMonth(dateToDisplay.DateTime).ToString("00") 
      End If             
   End Function
End Class
' The example displays the following output to the console:
'       Using the system default culture: 7/3/2008
'       Using the ar-JO culture's original default calendar: 03/07/2008
'       Using the ar-JO culture with Hijri as the default calendar:
'       Displaying date in supported HijriCalendar calendar...
'       1429/06/29
'       Displaying date in supported HijriCalendar calendar...
'       1429/06/29
'       
'       Using the ir-FA culture's default calendar: 7/3/2008
'       Displaying date in unsupported PersianCalendar calendar...
'       1387/04/13
'       Displaying date in unsupported PersianCalendar calendar...
'       1387/04/13
```

各 [CultureInfo](xref:System.Globalization.CultureInfo) オブジェクトは、[OptionalCalendars](xref:System.Globalization.CultureInfo.OptionalCalendars) プロパティに示されている&1; つ以上の暦をサポートできます。 これらのいずれかがカルチャの既定の暦として指定され、読み取り専用の [CultureInfo.Calendar](xref:System.Globalization.CultureInfo.Calendar) プロパティによって返されます。 オプションの暦のもう&1; つは、その暦を表す [Calendar](xref:System.Globalization.Calendar) オブジェクトを [CultureInfo.DateTimeFormat](xref:System.Globalization.CultureInfo.DateTimeFormat) プロパティによって返された [DateTimeFormatInfo.Calendar](xref:System.Globalization.DateTimeFormatInfo.Calendar) プロパティに割り当てることで、既定値として指定することができます。 ただし、[PersianCalendar](xref:System.Globalization.PersianCalendar) クラスによって表されるペルシャ暦などの一部の暦は、どのカルチャのオプションの暦としても機能しません。   

例では、特定の暦を使用して日付の文字列形式を生成する詳細の多くを処理するため、再利用可能な暦ユーティリティ クラス `CalendarUtility` を定義しています。 `CalendarUtility` クラスには次のメンバーがあります。 

* パラメーター化されたコンストラクター。その単一のパラメーターが [Calendar](xref:System.Globalization.Calendar) オブジェクトで、この中で日付が表示されます。 これは、クラスのプライベート フィールドに割り当てられます。

* `CalendarExists` は、`CalendarUtility` オブジェクトによって表される暦が、パラメーターとしてメソッドに渡される [CultureInfo](xref:System.Globalization.CultureInfo) オブジェクトによってサポートされているかどうかを示すブール値を返すプライベート メソッドです。 このメソッドは、[CultureInfo.OptionalCalendars](xref:System.Globalization.CultureInfo.OptionalCalendars) 配列を渡す [Array.Exists&lt;T&gt;](xref:System.Array.Exists``1(``0[],System.Predicate{``0})) メソッドへの呼び出しをラップします。

* `HasSameName` は、パラメーターとして [Array.Exists&lt;T&gt;](xref:System.Array.Exists``1(``0[],System.Predicate{``0})) メソッドに渡される [Predicate&lt;T&gt;](xref:System.Predicate%601) デリゲートに割り当てられるプライベート メソッドです。 メソッドが `true` を返すまで、配列の各メンバーがメソッドに渡されます。 このメソッドは、オプションの暦の名前が `CalendarUtility` オブジェクトによって表される暦と同じかどうかを判断します。

* `DisplayDate` は、2 つのパラメーターに渡されるオーバーロードされたパブリック メソッドです。[DateTime](xref:System.DateTime) または [DateTimeOffset](xref:System.DateTimeOffset) のいずれかの値を `CalendarUtility` オブジェクトによって表される暦で表し、カルチャの書式指定規則が使用されます。 日付の文字列表現を返す際の動作は、ターゲットの暦が、使用される書式指定規則のカルチャでサポートされているかどうかによって異なります。

この例では、[DateTime](xref:System.DateTime) または [DateTimeOffset](xref:System.DateTimeOffset) 値を作成するために使用する暦に関係なく、その値は通常、グレゴリオ暦の日付として表現されます。 これは、[DateTime](xref:System.DateTime) と [DateTimeOffset](xref:System.DateTimeOffset) 型は、どの暦情報も保持しないからです。 これらは内部的に 0001 年 1 月 1 日の午前 0 時から経過したタイマー刻みの数として表されます。 その数の解釈は、暦に依存します。 ほとんどのカルチャでは、既定の暦はグレゴリオ暦です。 

## <a name="see-also"></a>関連項目

[書式設定操作の実行](performing-formatting-operations.md)

