---
title: "方法 : ユーザーがあいまいな時刻を解決できるようにする"
description: "方法 : ユーザーがあいまいな時刻を解決できるようにする"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: d6858a5c-02ab-4367-9e08-fa22c051c38d
translationtype: Human Translation
ms.sourcegitcommit: c40c28da09e8a122b542463c197196c82c81dd19
ms.openlocfilehash: c54a3e742ea436c31fd238d5ecb5be98cbc6c6af

---

# <a name="how-to-let-users-resolve-ambiguous-times"></a>方法 : ユーザーがあいまいな時刻を解決できるようにする

あいまいな時刻は複数の世界協定時刻 (UTC) にマップされる時刻です。 これは、あるタイム ゾーンの夏時間から標準時間に移行する際など、時計の時刻を前に戻すときに発生します。 あいまいな時刻を処理する場合は、次のいずれかの操作を行います。

* あいまいな時刻が、ユーザーによって入力されたデータの項目の場合は、あいまいさの解決をユーザーに任せることができます。

* 時刻が UTC にどのようにマップされるかを想定します。 たとえば、あいまいな時刻は常にタイム ゾーンの標準時刻で表されると想定できます。

この記事では、ユーザーにあいまいな時刻を解決させる方法を示します。

## <a name="to-let-a-user-resolve-an-ambiguous-time"></a>ユーザーにあいまいな時刻を解決させるには

1. ユーザーによって入力された日付と時刻を取得します。

2. [IsAmbiguousTime(DateTime)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTime)) または [IsAmbiguousTime(DateTimeOffset)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTimeOffset)) メソッドを呼び出して、時刻があいまいかどうかを判断します。

3. ユーザーに目的のオフセットを選択させます。

4. ローカル時刻からユーザーによって選択されたオフセットを減算して、UTC の日時を取得します。

5. `static` ( Visual Basic では `Shared`) [SpecifyKind](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)) メソッドを呼び出して、UTC の日時値の [Kind](xref:System.DateTime.Kind) プロパティを [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) に設定します。

## <a name="example"></a>例

次の例では、ユーザーに日付と時刻を入力するように求め、それがあいまいである場合は、ユーザーにあいまいな時刻をマップする UTC 時刻を選択させています。 この例では、[DateTime](xref:System.DateTime) オブジェクトを使用しています。必要に応じて、[DateTimeOffset](xref:System.DateTimeOffset) オブジェクトに置き換えることができます。

```csharp
private void GetUserDateInput()
{
   // Get date and time from user
   DateTime inputDate = GetUserDateTime();
   DateTime utcDate;

   // Exit if date has no significant value
   if (inputDate == DateTime.MinValue) return;

   if (TimeZoneInfo.Local.IsAmbiguousTime(inputDate))
   {
      Console.WriteLine("The date you've entered is ambiguous.");
      Console.WriteLine("Please select the correct offset from Universal Coordinated Time:");
      TimeSpan[] offsets = TimeZoneInfo.Local.GetAmbiguousTimeOffsets(inputDate);
      for (int ctr = 0; ctr < offsets.Length; ctr++)
      {
         Console.WriteLine("{0}.) {1} hours, {2} minutes", ctr, offsets[ctr].Hours, offsets[ctr].Minutes);
      }
      Console.Write("> ");
      int selection = Convert.ToInt32(Console.ReadLine());

      // Convert local time to UTC, and set Kind property to DateTimeKind.Utc
      utcDate = DateTime.SpecifyKind(inputDate - offsets[selection], DateTimeKind.Utc);

      Console.WriteLine("{0} local time corresponds to {1} {2}.", inputDate, utcDate, utcDate.Kind.ToString());
   }
   else
   {
      utcDate = inputDate.ToUniversalTime();
      Console.WriteLine("{0} local time corresponds to {1} {2}.", inputDate, utcDate, utcDate.Kind.ToString());    
   }
}

private DateTime GetUserDateTime() 
{
   bool exitFlag = false;             // flag to exit loop if date is valid
   string dateString;  
   DateTime inputDate = DateTime.MinValue;

   Console.Write("Enter a local date and time: ");
   while (! exitFlag)
   {
      dateString = Console.ReadLine();
      if (dateString.ToUpper() == "E")
         exitFlag = true;

      if (DateTime.TryParse(dateString, out inputDate))
         exitFlag = true;
      else
         Console.Write("Enter a valid date and time, or enter 'e' to exit: ");
   }

   return inputDate;        
}
```

```vb
Private Sub GetUserDateInput()
   ' Get date and time from user
   Dim inputDate As Date = GetUserDateTime()
   Dim utcDate As Date

   ' Exit if date has no significant value
   If inputDate = Date.MinValue Then Exit Sub

   If TimeZoneInfo.Local.IsAmbiguousTime(inputDate) Then
      Console.WriteLine("The date you've entered is ambiguous.")
      Console.WriteLine("Please select the correct offset from Universal Coordinated Time:")
      Dim offsets() As TimeSpan = TimeZoneInfo.Local.GetAmbiguousTimeOffsets(inputDate)
      For ctr As Integer = 0 to offsets.Length - 1
         Dim zoneDescription As String
         If offsets(ctr).Equals(TimeZoneInfo.Local.BaseUtcOffset) Then 
            zoneDescription = TimeZoneInfo.Local.StandardName
         Else
            zoneDescription = TimeZoneInfo.Local.DaylightName
         End If
         Console.WriteLine("{0}.) {1} hours, {2} minutes ({3})", _
                           ctr, offsets(ctr).Hours, offsets(ctr).Minutes, zoneDescription)
      Next         
      Console.Write("> ")
      Dim selection As Integer = CInt(Console.ReadLine())

      ' Convert local time to UTC, and set Kind property to DateTimeKind.Utc
      utcDate = Date.SpecifyKind(inputDate - offsets(selection), DateTimeKind.Utc)

      Console.WriteLine("{0} local time corresponds to {1} {2}.", inputDate, utcDate, utcDate.Kind.ToString())
   Else
      utcDate = inputDate.ToUniversalTime()
      Console.WriteLine("{0} local time corresponds to {1} {2}.", inputDate, utcDate, utcDate.Kind.ToString())    
   End If
End Sub

Private Function GetUserDateTime() As Date
   Dim exitFlag As Boolean = False            ' flag to exit loop if date is valid
   Dim dateString As String 
   Dim inputDate As Date = Date.MinValue

   Console.Write("Enter a local date and time: ")
   Do While Not exitFlag
      dateString = Console.ReadLine()
      If dateString.ToUpper = "E" Then exitFlag = True
      If Date.TryParse(dateString, inputDate) Then
         exitFlag = true
      Else   
         Console.Write("Enter a valid date and time, or enter 'e' to exit: ")
      End If
   Loop

   Return inputDate        
End Function
```

このコード例の核心は、[TimeSpan](xref:System.TimeSpan) オブジェクトの配列を使用して、UTC からのあいまいな時刻の可能性のあるオフセットを示すことです。 ただし、これらのオフセットは、ユーザーにとって意味がない可能性があります。 オフセットの意味を明確にするには、コードで、オフセットがローカル タイム ゾーンの標準時刻を表すか、または夏時間を表すかに注意します。 コードで標準時間と夏時間を判断するには、そのオフセットと [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset) プロパティの値を比較します。 このプロパティは、UTC とタイム ゾーンの標準時間の差を示します。

この例では、ローカル タイム ゾーンへのすべての参照は [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) プロパティによって行われます。ローカル タイム ゾーンが、オブジェクト変数に割り当てられることはありません。 これは、別の呼び出しがキャッシ データをクリアして、ローカル タイム ゾーンが割り当てられているオブジェクトが無効にされる可能性があるために、推奨される方法です。

## <a name="see-also"></a>関連項目

[日付、時刻およびタイム ゾーン](index.md)

[方法: あいまいな時刻を解決する](resolve-ambiguous-times.md)




<!--HONumber=Nov16_HO3-->


