---
title: "方法 : TimeZoneInfo オブジェクトをインスタンス化する"
description: "方法 : TimeZoneInfo オブジェクトをインスタンス化する"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: bff137e5-d550-44c3-b460-b3f2dabd4035
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: f2584d446c92d2df2f6d74533ef07fe96888d36a
ms.lasthandoff: 03/02/2017

---

# <a name="how-to-instantiate-a-timezoneinfo-object"></a>方法 : TimeZoneInfo オブジェクトをインスタンス化する

[TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクトをインスタンス化する最も一般的な方法は、オペレーティング システムからオブジェクトに関する情報を取得することです。 このトピックでは、ローカル システムから [TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクトをインスタンス化する方法について説明します。

## <a name="to-instantiate-a-timezoneinfo-object"></a>TimeZoneInfo オブジェクトをインスタンス化するには

1. [TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクトを宣言します。

2. `static` (Visual Basic の場合は `Shared`) [TimeZoneInfo.FindSystemTimeZoneById](xref:System.TimeZoneInfo.FindSystemTimeZoneById(System.String)) メソッドを呼び出します。

3. メソッドによってスローされた例外を処理します。

## <a name="example"></a>例

次のコードでは、東部標準時のタイム ゾーンを表す [TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクトを取得し、現地時刻に対応する東部標準時の時刻を表示します。

```csharp
DateTime timeNow = DateTime.Now;
try
{
   TimeZoneInfo easternZone = TimeZoneInfo.FindSystemTimeZoneById("Eastern Standard Time");
   DateTime easternTimeNow = TimeZoneInfo.ConvertTime(timeNow, TimeZoneInfo.Local, 
                                                   easternZone);
   Console.WriteLine("{0} {1} corresponds to {2} {3}.",
                     timeNow, 
                     TimeZoneInfo.Local.IsDaylightSavingTime(timeNow) ?
                               TimeZoneInfo.Local.DaylightName : 
                               TimeZoneInfo.Local.StandardName,
                     easternTimeNow, 
                     easternZone.IsDaylightSavingTime(easternTimeNow) ?
                                 easternZone.DaylightName : 
                                 easternZone.StandardName);
}
// Handle exception
//
// As an alternative to simply displaying an error message, an alternate Eastern
// Standard Time TimeZoneInfo object could be instantiated here either by restoring
// it from a serialized string or by providing the necessary data to the
// CreateCustomTimeZone method.
catch (InvalidTimeZoneException)
{
   Console.WriteLine("The Eastern Standard Time Zone contains invalid or missing data.");
}
catch (SecurityException)
{
   Console.WriteLine("The application lacks permission to read time zone information from the registry.");
}
catch (OutOfMemoryException)
{
   Console.WriteLine("Not enough memory is available to load information on the Eastern Standard Time zone.");
}
// If we weren't passing FindSystemTimeZoneById a literal string, we also 
// would handle an ArgumentNullException.
```

```vb
Dim timeNow As Date = Date.Now
Try
   Dim easternZone As TimeZoneInfo = TimeZoneInfo.FindSystemTimeZoneById("Eastern Standard Time")
   Dim easternTimeNow As Date = TimeZoneInfo.ConvertTime(timeNow, TimeZoneInfo.Local, easternZone)
   Console.WriteLine("{0} {1} corresponds to {2} {3}.", _
                     timeNow, _
                     IIf(TimeZoneInfo.Local.IsDaylightSavingTime(timeNow), _
                         TimeZoneInfo.Local.DaylightName, TimeZoneInfo.Local.StandardName), _
                     easternTimeNow, _
                     IIf(easternZone.IsDaylightSavingTime(easternTimeNow), _
                         easternZone.DaylightName, easternZone.StandardName))
' Handle exception
'
' As an alternative to simply displaying an error message, an alternate Eastern
' Standard Time TimeZoneInfo object could be instantiated here either by restoring
' it from a serialized string or by providing the necessary data to the
' CreateCustomTimeZone method.
Catch e As InvalidTimeZoneException
   Console.WriteLine("The Eastern Standard Time Zone contains invalid or missing data.")   
Catch e As SecurityException
   Console.WriteLine("The application lacks permission to read time zone information from the registry.")
Catch e As OutOfMemoryException
   Console.WriteLine("Not enough memory is available to load information on the Eastern Standard Time zone.")
' If we weren't passing FindSystemTimeZoneById a literal string, we also 
' would handle an ArgumentNullException.
End
``` 

[TimeZoneInfo.FindSystemTimeZoneById](xref:System.TimeZoneInfo.FindSystemTimeZoneById(System.String)) メソッドの唯一のパラメーターは、取得するタイム ゾーンの識別子です。これは、オブジェクトの [TimeZoneInfo.Id](xref:System.TimeZoneInfo.Id) プロパティに対応します。 タイム ゾーン ID は、タイム ゾーンを一意に識別するキー フィールドです。 ほとんどのキーは比較的短いですが、タイム ゾーン ID はいくぶん長めです。 ほとんどの場合、ID の値は、タイム ゾーンの標準時刻の名前を表すために使用される [TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクトの [StandardName](xref:System.TimeZoneInfo.StandardName) プロパティに対応します。 ただし、例外もあります。 有効な識別子を確実に指定する最良の方法は、システムで使用できるタイム ゾーンを列挙し、対応するタイム ゾーン識別子を記録しておくことです。 例については、「[方法 : コンピューター上に存在するタイム ゾーンを列挙する](enumerate-time-zones.md)」を参照してください。 「[ローカル システムで定義されているタイム ゾーンの検索](finding-the-time-zones-on-local-system.md)」のトピックには、選択したタイム ゾーン ID の一覧も掲載されています。

タイム ゾーンが見つかると、メソッドは [TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクトを返します。 タイム ゾーンが見つかっても、そのデータが破損しているか不完全な場合には、メソッドから [InvalidTimeZoneException](xref:System.InvalidTimeZoneException) がスローされます。 

## <a name="see-also"></a>関連項目

[日付、時刻およびタイム ゾーン](index.md)

[ローカル システムで定義されているタイム ゾーンの検索](finding-the-time-zones-on-local-system.md)
