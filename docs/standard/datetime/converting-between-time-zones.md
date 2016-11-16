---
title: "タイム ゾーン間での時刻の変換"
description: "タイム ゾーン間での時刻の変換"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: bf8f74e6-e7f2-4c2a-a04c-57db0e28dd36
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 051a4891336470e79bda9d7b9bb1be4e2c9187b8

---

# <a name="converting-times-between-time-zones"></a>タイム ゾーン間での時刻の変換

日時を使用するすべてのアプリケーションで、タイム ゾーン間の違いを処理することの重要性が高まっています。 アプリケーションでは、すべての時刻を現地時刻で表現できることを前提とはしていません。現地時刻は、[System.DateTime](xref:System.DateTime) 構造体から取得できる時刻です。 たとえば、米国東部の現在の時刻を表示する Web ページには、東アジアの顧客に対する信頼性を欠いています。 このトピックでは、時刻をあるタイム ゾーンから別のタイム ゾーンに変換する方法、およびタイム ゾーン対応に制限のある [System.DateTimeOffset](xref:System.DateTimeOffset) 値を変換する方法について説明します。

## <a name="converting-to-coordinated-universal-time"></a>世界協定時刻への変換

世界協定時刻 (UTC) は、高精度の原子時標準です。 世界のタイム ゾーンは、UTC からの正または負のオフセットとして表現されます。 したがって、UTC はタイム ゾーンの影響を受けない、またはタイム ゾーンに依存しない種類の時刻を提供します。 コンピューター間の日時の移植性が重要となる場合には、UTC 時刻の使用が推奨されます。 個別のタイム ゾーンを UTC に変換すると、時間の比較が容易になります。

> [!NOTE]
> また、ある時点を明確に表すように [DateTimeOffset](xref:System.DateTimeOffset) 構造体をシリアル化することもできます。 [DateTimeOffset](xref:System.DateTimeOffset) オブジェクトは日時値を UTC からのオフセットと共に格納するので、特定の時点を常に UTC と関連付けて表します。

時刻を UTC に変換する最も簡単な方法としては、`static` (Visual Basic では `Shared`) [TimeZoneInfo.ConvertTimeToUtc(DateTime)](https://msdn.microsoft.com/en-us/library/bb381744(v=vs.110).aspx) メソッドを呼び出します。 

> [!IMPORTANT]
> `TimeZoneInfo.ConvertTimeToUtc(DateTime)` メソッドは現在 .NET Core で使用できません。 

次の表に示すように、このメソッドによって実行される実際の変換は、`DateTime` パラメーターの [Kind](xref:System.DateTime.Kind) プロパティの値によって異なります。

[DateTime.Kind](xref:System.DateTimeKind) プロパティ | 変換
---------------------------------------------------------------------------------------------- | ----------
[DateTimeKind.Local](xref:System.DateTimeKind.Local) | 現地時刻を UTC に変換します。
[DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified) | `DateTime` パラメーターが現地時刻であることを前提とし、現地時刻を UTC に変換します。
[DateTimeKind.Utc](xref:System.DateTimeKind.Utc) | `DateTime` パラメーターを変更せずに返します。

次のコードは、現在の現地時刻を UTC に変換し、コンソールに結果を表示します。

```csharp
DateTime dateNow = DateTime.Now;
Console.WriteLine("The date and time are {0} UTC.", 
                   TimeZoneInfo.ConvertTimeToUtc(dateNow));
```

```vb
Dim dateNow As Date = Date.Now      
Console.WriteLine("The date and time are {0} UTC.", _
                  TimeZoneInfo.ConvertTimeToUtc(dateNow))
```

> [!NOTE]
>[TimeZoneInfo.ConvertTimeToUtc(DateTime)](https://msdn.microsoft.com/en-us/library/bb381744(v=vs.110).aspx) メソッドは、[TimeZone.ToUniversalTime](https://msdn.microsoft.com/en-us/library/System.TimeZone.ToUniversalTime(v=vs.110).aspx) メソッドおよび [DateTime.ToUniversalTime](xref:System.DateTime.ToUniversalTime) メソッドと同じ結果を必ずしも生成するとは限りません。 ホスト システムのローカル タイム ゾーンに複数の調整規則が含まれる場合、[TimeZoneInfo.ConvertTimeToUtc(DateTime)](https://msdn.microsoft.com/en-us/library/System.TimeZone.ConvertTimeToUtc(v=vs.110).aspx) は特定の日時に適切な規則を適用します。 他の 2 つのメソッドは、常に最新の調整規則を適用します。

日時値が現地時刻と UTC のどちらかを表さない場合、[ToUniversalTime](https://msdn.microsoft.com/en-us/library/System.TimeZone.ToUniversalTime(v=vs.110).aspx) メソッドは不正な結果を返す可能性があります。 ただし、[TimeZoneInfo.ConvertTimeToUtc](https://msdn.microsoft.com/en-us/library/bb381744(v=vs.110).aspx) メソッドを使用して、指定したタイム ゾーンから日時を変換できます (変換先のタイム ゾーンを表す TimeZoneInfo オブジェクトを取得する方法の詳細については、「[ローカル システムで定義されているタイム ゾーンの検索](finding-the-time-zones-on-local-system.md)」を参照してください)。 次のコードは、[TimeZoneInfo.ConvertTimeToUtc](https://msdn.microsoft.com/en-us/library/bb381744(v=vs.110).aspx) メソッドを使用して東部標準時を UTC に変換します。

```csharp
DateTime easternTime = new DateTime(2007, 01, 02, 12, 16, 00);
string easternZoneId = "Eastern Standard Time";
try
{
   TimeZoneInfo easternZone = TimeZoneInfo.FindSystemTimeZoneById(easternZoneId);
   Console.WriteLine("The date and time are {0} UTC.", 
                     TimeZoneInfo.ConvertTimeToUtc(easternTime, easternZone));
}
catch (TimeZoneNotFoundException)
{
   Console.WriteLine("Unable to find the {0} zone in the registry.", 
                     easternZoneId);
}                           
catch (InvalidTimeZoneException)
{
   Console.WriteLine("Registry data on the {0} zone has been corrupted.", 
                     easternZoneId);
}
```

```vb
Dim easternTime As New Date(2007, 01, 02, 12, 16, 00)
Dim easternZoneId As String = "Eastern Standard Time"
Try
   Dim easternZone As TimeZoneInfo = TimeZoneInfo.FindSystemTimeZoneById(easternZoneId)
   Console.WriteLine("The date and time are {0} UTC.", _ 
                     TimeZoneInfo.ConvertTimeToUtc(easternTime, easternZone))
Catch e As TimeZoneNotFoundException
   Console.WriteLine("Unable to find the {0} zone in the registry.", _
                     easternZoneId)
Catch e As InvalidTimeZoneException
   Console.WriteLine("Registry data on the {0} zone has been corrupted.", _ 
                     easternZoneId)
End Try    
```

[DateTime](xref:System.DateTime) オブジェクトの [Kind](xref:System.DateTimeKind) プロパティとタイム ゾーンが一致しない場合、このメソッドは [ArgumentException](xref:System.ArgumentException) をスローします。 Kind プロパティが [DateTimeKind.Local](xref:System.DateTimeKind.Local) であるが [TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクトがローカル タイム ゾーンを表さない場合、または Kind プロパティが [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) であるが [TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクトが [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) と等しくない場合に、不一致が発生します。

これらすべてのメソッドは、パラメーターとして [DateTime](xref:System.DateTime) 値を受け取り、[DateTime](xref:System.DateTime) 値を返します。 [DateTimeOffset](xref:System.DateTimeOffset) 値について、[DateTimeOffset](xref:System.DateTimeOffset) 構造体には、現在のインスタンスの日時を UTC に変換する [ToUniversalTime](xref:System.DateTimeOffset.ToUniversalTime) インスタンス メソッドが含まれます。 次の例では、[ToUniversalTime](xref:System.DateTimeOffset.ToUniversalTime) メソッドを呼び出して、現地時刻およびその他のいくつかの時刻を世界協定時刻 (UTC) に変換します。

```csharp
DateTimeOffset localTime, otherTime, universalTime;

// Define local time in local time zone
localTime = new DateTimeOffset(new DateTime(2007, 6, 15, 12, 0, 0));
Console.WriteLine("Local time: {0}", localTime);
Console.WriteLine();

// Convert local time to offset 0 and assign to otherTime
otherTime = localTime.ToOffset(TimeSpan.Zero);
Console.WriteLine("Other time: {0}", otherTime);
Console.WriteLine("{0} = {1}: {2}", 
                  localTime, otherTime, 
                  localTime.Equals(otherTime));
Console.WriteLine("{0} exactly equals {1}: {2}", 
                  localTime, otherTime, 
                  localTime.EqualsExact(otherTime));
Console.WriteLine();

// Convert other time to UTC
universalTime = localTime.ToUniversalTime(); 
Console.WriteLine("Universal time: {0}", universalTime);
Console.WriteLine("{0} = {1}: {2}", 
                  otherTime, universalTime, 
                  universalTime.Equals(otherTime));
Console.WriteLine("{0} exactly equals {1}: {2}", 
                  otherTime, universalTime, 
                  universalTime.EqualsExact(otherTime));
Console.WriteLine();
// The example produces the following output to the console:
//    Local time: 6/15/2007 12:00:00 PM -07:00
//    
//    Other time: 6/15/2007 7:00:00 PM +00:00
//    6/15/2007 12:00:00 PM -07:00 = 6/15/2007 7:00:00 PM +00:00: True
//    6/15/2007 12:00:00 PM -07:00 exactly equals 6/15/2007 7:00:00 PM +00:00: False
//    
//    Universal time: 6/15/2007 7:00:00 PM +00:00
//    6/15/2007 7:00:00 PM +00:00 = 6/15/2007 7:00:00 PM +00:00: True
//    6/15/2007 7:00:00 PM +00:00 exactly equals 6/15/2007 7:00:00 PM +00:00: True 
```

```vb
Dim localTime, otherTime, universalTime As DateTimeOffset

' Define local time in local time zone
localTime = New DateTimeOffset(#6/15/2007 12:00:00PM#)
Console.WriteLine("Local time: {0}", localTime)
Console.WriteLine()

' Convert local time to offset 0 and assign to otherTime
otherTime = localTime.ToOffset(TimeSpan.Zero)
Console.WriteLine("Other time: {0}", otherTime)
Console.WriteLine("{0} = {1}: {2}", _
                  localTime, otherTime, _
                  localTime.Equals(otherTime))
Console.WriteLine("{0} exactly equals {1}: {2}", _ 
                  localTime, otherTime, _
                  localTime.EqualsExact(otherTime))
Console.WriteLine()

' Convert other time to UTC
universalTime = localTime.ToUniversalTime() 
Console.WriteLine("Universal time: {0}", universalTime)
Console.WriteLine("{0} = {1}: {2}", _
                  otherTime, universalTime, _ 
                  universalTime.Equals(otherTime))
Console.WriteLine("{0} exactly equals {1}: {2}", _ 
                  otherTime, universalTime, _
                  universalTime.EqualsExact(otherTime))
Console.WriteLine()
' The example produces the following output to the console:
'    Local time: 6/15/2007 12:00:00 PM -07:00
'    
'    Other time: 6/15/2007 7:00:00 PM +00:00
'    6/15/2007 12:00:00 PM -07:00 = 6/15/2007 7:00:00 PM +00:00: True
'    6/15/2007 12:00:00 PM -07:00 exactly equals 6/15/2007 7:00:00 PM +00:00: False
'    
'    Universal time: 6/15/2007 7:00:00 PM +00:00
'    6/15/2007 7:00:00 PM +00:00 = 6/15/2007 7:00:00 PM +00:00: True
'    6/15/2007 7:00:00 PM +00:00 exactly equals 6/15/2007 7:00:00 PM +00:00: True 
```

## <a name="converting-utc-to-a-designated-time-zone"></a>UTC から指定したタイム ゾーンへの変換

UTC を現地時刻に変換するには、後の「[UTC から現地時刻への変換](#converting-utc-to-local-time)」セクションを参照してください。 

UTC を、指定した任意のタイム ゾーンの時刻に変換するには、[ConvertTimeFromUtc](https://msdn.microsoft.com/en-us/library/System.TimeZoneInfo.converttimefromutc(v=vs.110).aspx) メソッドを呼び出します。 

> [!IMPORTANT]
> .NET Core では、`TimeZoneInfo.ConvertTimeFromUtc' メソッドは現在使用できません。 

このメソッドは、次の 2 つのパラメーターを受け取ります。

* 変換対象の UTC。 これは、[Kind](xref:System.DateTime.Kind) にプロパティが [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) または [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified) に設定されている [DateTime](xref:System.DateTime) 値でなければなりません。 

* UTC の変換先のタイム ゾーン。 

次のコードは、UTC を中部標準時に変換します。

```csharp
DateTime timeUtc = DateTime.UtcNow;
try
{
   TimeZoneInfo cstZone = TimeZoneInfo.FindSystemTimeZoneById("Central Standard Time");
   DateTime cstTime = TimeZoneInfo.ConvertTimeFromUtc(timeUtc, cstZone);
   Console.WriteLine("The date and time are {0} {1}.", 
                     cstTime, 
                     cstZone.IsDaylightSavingTime(cstTime) ?
                             cstZone.DaylightName : cstZone.StandardName);
}
catch (TimeZoneNotFoundException)
{
   Console.WriteLine("The registry does not define the Central Standard Time zone.");
}                           
catch (InvalidTimeZoneException)
{
   Console.WriteLine("Registry data on the Central Standard Time zone has been corrupted.");
}
```

```vb
Dim timeUtc As Date = Date.UtcNow
Try
   Dim cstZone As TimeZoneInfo = TimeZoneInfo.FindSystemTimeZoneById("Central Standard Time")
   Dim cstTime As Date = TimeZoneInfo.ConvertTimeFromUtc(timeUtc, cstZone)
   Console.WriteLine("The date and time are {0} {1}.", _
                     cstTime, _
                     IIf(cstZone.IsDaylightSavingTime(cstTime), _
                         cstZone.DaylightName, cstZone.StandardName))
Catch e As TimeZoneNotFoundException
   Console.WriteLine("The registry does not define the Central Standard Time zone.")
Catch e As InvalidTimeZoneException
   Console.WriteLine("Registry data on the Central Standard Time zone has been corrupted.")
End Try
``` 

## <a name="converting-utc-to-local-time"></a>UTC から現地時刻への変換

UTC を現地時刻に変換するには、時刻を変換する対象の [DateTime](xref:System.DateTime) オブジェクトの [DateTime.ToLocalTime](xref:System.DateTime) メソッドを呼び出します。 次の表に示すように、このメソッドの実際の動作は、オブジェクトの [Kind](xref:System.DateTime.Kind) プロパティの値によって異なります。

[DateTime.Kind](xref:System.DateTimeKind) プロパティ | 変換
---------------------------------------------------------------------------------------------- | ----------
[DateTimeKind.Local](xref:System.DateTimeKind.Local) | [DateTime](xref:System.DateTime) 値を変更せずに返します。
[DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified) | [DateTime](xref:System.DateTime) 値が UTC であることを前提とし、UTC を現地時刻に変換します。
[DateTimeKind.Utc](xref:System.DateTimeKind.Utc) | [DateTime](xref:System.DateTime) 値を現地時刻に変換します。

## <a name="converting-between-any-two-time-zones"></a>任意の 2 つのタイム ゾーン間での変換

静的な [TimeZoneInfo.ConvertTime](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo)) メソッドを使用すると、任意の 2 つのタイム ゾーン間で変換を行うことができます。 このメソッドのパラメーターは、変換対象の [DateTime](xref:System.DateTime) 値、日時値のタイム ゾーンを表す [TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクト、および日時値の変換先のタイム ゾーンを表す [TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクトです。

このメソッドでは、変換対象の日時値の [Kind](xref:System.DateTime.Kind) プロパティと、タイム ゾーンを表す [TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクトまたはタイム ゾーン識別子とが、相互に対応する必要があります。 それ以外の場合は、[ArgumentException](xref:System.ArgumentException) がスローされます。 たとえば、日時値の [Kind](xref:System.DateTime.Kind) プロパティが [DateTimeKind.Local](xref:System.DateTimeKind.Local) である場合に、このメソッドにパラメーターとして渡された [TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクトが [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) と等しくなければ、例外がスローされます。 また、このメソッドにパラメーターとして渡された識別子が [TimeZoneInfo.Id](xref:System.TimeZoneInfo.Id) と等しくない場合にも、例外がスローされます。

次の例では、[ConvertTime](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo)) メソッドを使用してハワイ標準時を現地時刻に変換します。

```csharp
DateTime hwTime = new DateTime(2007, 02, 01, 08, 00, 00);
try
{
   TimeZoneInfo hwZone = TimeZoneInfo.FindSystemTimeZoneById("Hawaiian Standard Time");
   Console.WriteLine("{0} {1} is {2} local time.", 
           hwTime, 
           hwZone.IsDaylightSavingTime(hwTime) ? hwZone.DaylightName : hwZone.StandardName, 
           TimeZoneInfo.ConvertTime(hwTime, hwZone, TimeZoneInfo.Local));
}
catch (TimeZoneNotFoundException)
{
   Console.WriteLine("The registry does not define the Hawaiian Standard Time zone.");
}                           
catch (InvalidTimeZoneException)
{
   Console.WriteLine("Registry data on the Hawaiian STandard Time zone has been corrupted.");
}
```

```vb
Dim hwTime As Date = #2/01/2007 8:00:00 AM#
Try
   Dim hwZone As TimeZoneInfo = TimeZoneInfo.FindSystemTimeZoneById("Hawaiian Standard Time")
   Console.WriteLine("{0} {1} is {2} local time.", _
                     hwTime, _
                     IIf(hwZone.IsDaylightSavingTime(hwTime), hwZone.DaylightName, hwZone.StandardName), _
                     TimeZoneInfo.ConvertTime(hwTime, hwZone, TimeZoneInfo.Local))
Catch e As TimeZoneNotFoundException
   Console.WriteLine("The registry does not define the Hawaiian Standard Time zone.")
Catch e As InvalidTimeZoneException
   Console.WriteLine("Registry data on the Hawaiian Standard Time zone has been corrupted.")
End Try
```

## <a name="converting-datetimeoffset-values"></a>DateTimeOffset 値の変換

[System.DateTimeOffset](xref:System.DateTimeOffset) オブジェクトによって表される日時値は、完全にはタイム ゾーン対応ではありません。これは、オブジェクトがインスタンス化された時点でそのタイム ゾーンとの関連付けが解除されるためです。 ただし、アプリケーションでは多くの場合、特定のタイム ゾーンの時刻ではなく、単に UTC からの 2 つの異なるオフセットに基づいて日時を変換する必要があります。 この変換を実行するには、現在のインスタンスの [ToOffset](xref:System.DateTimeOffset.ToOffset(System.TimeSpan)) メソッドを呼び出します。 このメソッドの単一のパラメーターは、メソッドが返す新しい日時値のオフセットを表す [TimeSpan](xref:System.TimeSpan) です。  

たとえば、Web ページに対するユーザー要求の日時が既知であり、MM/dd/yyyy hh:mm:ss zzzz の形式で文字列としてシリアル化される場合、次の `ReturnTimeOnServer` メソッドは、この日時値を Web サーバー上の日時に変換します。

```csharp
public DateTimeOffset ReturnTimeOnServer(string clientString)
{
   string format = @"M/d/yyyy H:m:s zzz";
   TimeSpan serverOffset = TimeZoneInfo.Local.GetUtcOffset(DateTimeOffset.Now);

   try
   {      
      DateTimeOffset clientTime = DateTimeOffset.ParseExact(clientString, format, CultureInfo.InvariantCulture);
      DateTimeOffset serverTime = clientTime.ToOffset(serverOffset);
      return serverTime;
   }
   catch (FormatException)
   {
      return DateTimeOffset.MinValue;
   }
}
```

```vb
Public Function ReturnTimeOnServer(clientString As String) As DateTimeOffset
   Dim format As String = "M/d/yyyy H:m:s zzz"
   Dim serverOffset As TimeSpan = TimeZoneInfo.Local.GetUtcOffset(DateTimeOffset.Now)

   Try      
      Dim clientTime As DateTimeOffset = DateTimeOffset.ParseExact(clientString, format, CultureInfo.InvariantCulture)
      Dim serverTime As DateTimeOffset = clientTime.ToOffset(serverOffset)
      Return serverTime
   Catch e As FormatException
      Return DateTimeOffset.MinValue
   End Try    
End Function
```

このメソッドが、UTC よりも 5 時間遅いタイム ゾーンの日時を表す文字列 "9/1/2007 5:32:07 -05:00" を渡された場合、米国の太平洋標準時ゾーンにあるサーバー用に 9/1/2007 3:32:07 AM -07:00 を返します。

[TimeZoneInfo](xref:System.TimeZoneInfo) クラスには、[System.DateTimeOffset](xref:System.DateTimeOffset) 値によるタイム ゾーン変換を実行する、オーバーロードされた [TimeZoneInfo.ConvertTime (DateTimeOffset、TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTimeOffset,System.TimeZoneInfo)) メソッドも含まれます。 このメソッドのパラメーターは、[System.DateTimeOffset](xref:System.DateTimeOffset) 値と、時刻の変換先となるタイム ゾーンへの参照です。 このメソッド呼び出しは、[System.DateTimeOffset](xref:System.DateTimeOffset) 値を返します。 たとえば、前の例の `ReturnTimeOnServer` メソッドを次のように書き換えて、[ConvertTime(DateTimeOffset, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTimeOffset,System.TimeZoneInfo)) メソッドを呼び出すことができます。

```csharp
public DateTimeOffset ReturnTimeOnServer(string clientString)
{
   string format = @"M/d/yyyy H:m:s zzz";

   try
   {      
      DateTimeOffset clientTime = DateTimeOffset.ParseExact(clientString, format, 
                                  CultureInfo.InvariantCulture);
      DateTimeOffset serverTime = TimeZoneInfo.ConvertTime(clientTime, 
                                  TimeZoneInfo.Local);
      return serverTime;
   }
   catch (FormatException)
   {
      return DateTimeOffset.MinValue;
   }
}
```

```vb
Public Function ReturnTimeOnServer(clientString As String) As DateTimeOffset
   Dim format As String = "M/d/yyyy H:m:s zzz"

   Try      
      Dim clientTime As DateTimeOffset = DateTimeOffset.ParseExact(clientString, format, CultureInfo.InvariantCulture)
      Dim serverTime As DateTimeOffset = TimeZoneInfo.ConvertTime(clientTime, TimeZoneInfo.Local)
      Return serverTime
   Catch e As FormatException
      Return DateTimeOffset.MinValue
   End Try    
End Function
```

## <a name="see-also"></a>関連項目

[TimeZoneInfo](xref:System.TimeZoneInfo)

[日付、時刻およびタイム ゾーン](index.md)

[ローカル システムで定義されているタイム ゾーンの検索](finding-the-time-zones-on-local-system.md)





<!--HONumber=Nov16_HO1-->


