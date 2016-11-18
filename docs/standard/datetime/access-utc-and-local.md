---
title: "方法: 定義済みの UTC オブジェクトおよびローカル タイム ゾーン オブジェクトにアクセスする"
description: "方法: 定義済みの UTC オブジェクトおよびローカル タイム ゾーン オブジェクトにアクセスする"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 08/11/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 13454d47-d957-421b-9ecd-940058b8835e
translationtype: Human Translation
ms.sourcegitcommit: c40c28da09e8a122b542463c197196c82c81dd19
ms.openlocfilehash: ab419cf365b61399ea41e99c15e276584ad0db31

---

# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a>方法: 定義済みの UTC オブジェクトおよびローカル タイム ゾーン オブジェクトにアクセスする

[System.TimeZoneInfo](xref:System.TimeZoneInfo) クラスに用意されている 2 つのプロパティ、`Utc` および `Local` を使用すると、コードから定義済みのタイム ゾーン オブジェクトにアクセスできます。 このトピックでは、これらのプロパティから返される `TimeZoneInfo` オブジェクトにアクセスする方法について説明します。

## <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a>世界協定時刻 (UTC) の TimeZoneInfo オブジェクトにアクセスするには

1. **static** (Visual Basic では **Shared**) [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) プロパティを使用して、世界協定時刻にアクセスします。

2. プロパティから返された [TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクトをオブジェクト変数に割り当てるのではなく、そのまま [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) プロパティを使用して世界協定時刻にアクセスします。


## <a name="to-access-the-local-time-zone"></a>ローカル タイム ゾーンにアクセスするには

1. **static** (Visual Basic では **Shared**) [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) プロパティを使用して、ローカル タイム ゾーンにアクセスします。

2. プロパティから返された [TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクトをオブジェクト変数に割り当てるのではなく、そのまま [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) プロパティを使用してローカル タイム ゾーンにアクセスします。

## <a name="example"></a>例

次のコードでは、[TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) プロパティと [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) プロパティを使用して、米国およびカナダ東部標準時タイム ゾーンの時刻を変換し、コンソールにタイム ゾーンの名前を表示します。

```csharp
// Create Eastern Standard Time value and TimeZoneInfo object      
DateTime estTime = new DateTime(2007, 1, 1, 00, 00, 00);
string timeZoneName = "Eastern Standard Time";
try
{
   TimeZoneInfo est = TimeZoneInfo.FindSystemTimeZoneById(timeZoneName);

   // Convert EST to local time
   DateTime localTime = TimeZoneInfo.ConvertTime(estTime, est, TimeZoneInfo.Local);
   Console.WriteLine("At {0} {1}, the local time is {2} {3}.", 
           estTime, 
           est, 
           localTime, 
           TimeZoneInfo.Local.IsDaylightSavingTime(localTime) ?
                     TimeZoneInfo.Local.DaylightName : 
                     TimeZoneInfo.Local.StandardName);

   // Convert EST to UTC
   DateTime utcTime = TimeZoneInfo.ConvertTime(estTime, est, TimeZoneInfo.Utc);
   Console.WriteLine("At {0} {1}, the time is {2} {3}.", 
           estTime, 
           est, 
           utcTime, 
           TimeZoneInfo.Utc.StandardName);
}
catch (TimeZoneNotFoundException)
{
   Console.WriteLine("The {0} zone cannot be found in the registry.", 
                     timeZoneName);
}
catch (InvalidTimeZoneException)
{
   Console.WriteLine("The registry contains invalid data for the {0} zone.", 
                     timeZoneName);
}
```

```vb
' Create Eastern Standard Time value and TimeZoneInfo object      
Dim estTime As Date = #01/01/2007 00:00:00#
Dim timeZoneName As String = "Eastern Standard Time"
Try
   Dim est As TimeZoneInfo = TimeZoneInfo.FindSystemTimeZoneById(timeZoneName)

   ' Convert EST to local time
   Dim localTime As Date = TimeZoneInfo.ConvertTime(estTime, est, TimeZoneInfo.Local)
   Console.WriteLine("At {0} {1}, the local time is {2} {3}.", _
           estTime, _
           est, _
           localTime, _
           IIf(TimeZoneInfo.Local.IsDaylightSavingTime(localTime), _
               TimeZoneInfo.Local.DaylightName, _
               TimeZoneInfo.Local.StandardName))

   ' Convert EST to UTC
   Dim utcTime As Date = TimeZoneInfo.ConvertTime(estTime, est, TimeZoneInfo.Utc)
   Console.WriteLine("At {0} {1}, the time is {2} {3}.", _
           estTime, _
           est, _
           utcTime, _
           TimeZoneInfo.Utc.StandardName)
Catch e As TimeZoneNotFoundException
   Console.WriteLine("The {0} zone cannot be found in the registry.", _
                     timeZoneName)
Catch e As InvalidTimeZoneException
   Console.WriteLine("The registry contains invalid data for the {0} zone.", _
                     timeZoneName)
End Try
```

ローカル タイム ゾーンにアクセスする場合は、ローカル タイム ゾーンを [TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクト変数に割り当てることはせず、常に [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) プロパティを使用してください。 同様に、世界協定時刻にアクセスする場合は、UTC ゾーンを [TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクト変数に割り当てることはせず、常に [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) プロパティを使用してください。 これにより、[TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクト変数が外部メソッドによって無効になるのを防ぐことができます。


## <a name="see-also"></a>関連項目

[日付、時刻およびタイム ゾーン](index.md)

[ローカル システムで定義されているタイム ゾーンの検索](finding-the-time-zones-on-local-system.md)



<!--HONumber=Nov16_HO3-->


