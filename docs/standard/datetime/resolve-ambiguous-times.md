---
title: "方法: あいまいな時刻を解決する"
description: "あいまいな時刻を解決する方法"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 08/16/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: e86050c6-d16d-405e-8bba-7205945c9a81
translationtype: Human Translation
ms.sourcegitcommit: c40c28da09e8a122b542463c197196c82c81dd19
ms.openlocfilehash: b31ea18cd7a7e32863f384cb279dc715fd62b3df

---

# <a name="how-to-resolve-ambiguous-times"></a>方法: あいまいな時刻を解決する

あいまいな時刻とは、複数の世界協定時刻 (UTC) にマップされる時刻です。 これは、あるタイム ゾーンの夏時間から標準時間に移行する際など、時計の時刻を前に戻すときに発生します。 あいまいな時刻を処理する場合は、次のいずれかの操作を行います。

* 時刻が UTC にどのようにマップされるかを想定します。 たとえば、あいまいな時刻は常にタイム ゾーンの標準時刻で表されると想定できます。

* あいまいな時刻が、ユーザーによって入力されたデータ項目である場合は、あいまいさの解決をユーザーに任せることができます。

この記事では、タイム ゾーンの標準時刻を表すと想定して、あいまいな時刻を解決する方法を示します。

## <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a>あいまいな時刻をタイム ゾーンの標準時刻にマップするには

1. [System.TimeZoneInfo.IsAmbiguousTime(DateTime)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTime)) または [System.TimeZoneInfo.IsAmbiguousTime(DateTimeOffset)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTimeOffset)) メソッドを呼び出して、時刻があいまいかどうかを判断します。

2. 時刻があいまいな場合は、タイム ゾーンの [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset) プロパティによって返される [TimeSpan](xref:System.TimeSpan) オブジェクトから時刻を減算します。

3. `static` (Visual Basic では `Shared`) [SpecifyKind](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)) メソッドを呼び出して、UTC の日付と時刻の値の [Kind](xref:System.DateTime.Kind) プロパティを [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) に設定します。

## <a name="example"></a>例

次の例では、あいまいな時刻がローカル タイム ゾーンの標準時刻を表すと想定して、あいまいな [DateTime](xref:System.DateTime) を UTC に変換する方法を示しています。 

```csharp
private DateTime ResolveAmbiguousTime(DateTime ambiguousTime)
{
   // Time is not ambiguous
   if (! TimeZoneInfo.Local.IsAmbiguousTime(ambiguousTime))
   { 
      return ambiguousTime; 
   }
   // Time is ambiguous
   else
   {
      DateTime utcTime = DateTime.SpecifyKind(ambiguousTime - TimeZoneInfo.Local.BaseUtcOffset, 
                                              DateTimeKind.Utc);      
      Console.WriteLine("{0} local time corresponds to {1} {2}.", 
                        ambiguousTime, utcTime, utcTime.Kind.ToString());
      return utcTime;            
   }   
}
```

```vb
Private Function ResolveAmbiguousTime(ambiguousTime As Date) As Date
   ' Time is not ambiguous
   If Not TimeZoneInfo.Local.IsAmbiguousTime(ambiguousTime) Then 
      Return TimeZoneInfo.ConvertTimeToUtc(ambiguousTime) 
   ' Time is ambiguous
   Else
      Dim utcTime As Date = DateTime.SpecifyKind(ambiguousTime - TimeZoneInfo.Local.BaseUtcOffset, DateTimeKind.Utc)      
      Console.WriteLine("{0} local time corresponds to {1} {2}.", ambiguousTime, utcTime, utcTime.Kind.ToString())
      Return utcTime            
   End If   
End Function
```

この例は、渡された [DateTime](xref:System.DateTime) 値があいまいかどうかを判定する `ResolveAmbiguousTime` という名前のメソッドで構成されます。 値があいまいな場合、メソッドは対応する UTC 時刻を表す [DateTime](xref:System.DateTime) 値を返します。 このメソッドは、ローカル タイム ゾーンの [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset) プロパティの値をローカル時刻から減算して、この変換を行います。 

通常、あいまいな時刻の処理では、[GetAmbiguousTimeOffsets](xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets(System.DateTime)) メソッドを呼び出し、あいまいな時刻に対して考えられる UTC オフセットが格納されている [TimeSpan](xref:System.TimeSpan) オブジェクトの配列を取得します。 しかし、この例は、あいまいな時刻は常にタイム ゾーンの標準時刻にマップされるという想定に基づいています。 [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset) プロパティは、UTC とタイム ゾーンの標準時刻の間のオフセットを返します。

## <a name="see-also"></a>関連項目

[日付、時刻およびタイム ゾーン](index.md)

[方法: ユーザーがあいまいな時刻を解決できるようにする](let-users-resolve-ambiguous-times.md)




<!--HONumber=Nov16_HO3-->


