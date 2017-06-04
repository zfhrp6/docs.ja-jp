---
title: "タイム ゾーン間での時刻の変換 | Microsoft Docs"
ms.custom: ""
ms.date: "04/10/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "変換 (時間を)"
  - "ローカル タイムの変換"
  - "タイム ゾーン [.NET Framework], 変換"
  - "時刻 [.NET Framework], 変換"
  - "UTC 時刻, 変換"
ms.assetid: a51e1a3b-c983-4320-b31a-1f9fa3cf824a
caps.latest.revision: 19
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 19
---
# タイム ゾーン間での時刻の変換
タイム ゾーン間での日時の違いを処理するアプリケーションの重要性が増しています。  アプリケーションは、<xref:System.DateTime> 構造体にある現地時刻ですべての時刻を表現するだけで良いとは想定できなくなりました。  たとえば、米国東部の現在時刻を表示する Web ページは、東アジアの顧客にとっては妥当なものではありません。  このトピックでは、あるタイム ゾーンから別のタイム ゾーンに時刻を変換する方法、およびタイム ゾーンの取り扱いが不適切な <xref:System.DateTimeOffset> 値を変換する方法について説明します。  
  
## 世界協定時刻への変換  
 世界協定時刻 \(UTC\) は、高精度で、原子時計に基づく時刻基準です。  世界のタイム ゾーンは、UTC からの正または負のオフセットとして表されます。  したがって、UTC は、タイム ゾーンの影響を受けない時刻、またはどのタイム ゾーンからも中立の時刻を提供します。  コンピューター間での日時の統一性が重要な場合は、UTC 時刻を使用することをお勧めします。\(日付と時刻を使用して詳細および他のベスト プラクティスについては、"参照して [.NET Framework の DateTime を使用してコーディング Best Practices](http://go.microsoft.com/fwlink/?LinkId=92342)ください。個別のタイム ゾーンを UTC に変換すると、時刻の比較が容易になります。  
  
> [!NOTE]
>  <xref:System.DateTimeOffset> 構造体をシリアル化して、ある時刻を明確に表すこともできます。  <xref:System.DateTimeOffset> オブジェクトは UTC からのオフセットで日時の値を格納するので、常に UTC に対する相対値で特定の時刻を表します。  
  
 時刻を UTC に変換する最も簡単な方法は、`static` \(Visual Basic では `Shared`\) の <xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=fullName> メソッドを呼び出す方法です。  メソッドで実行される具体的な変換は、次の表に示すように、`dateTime` パラメーターの <xref:System.DateTime.Kind%2A> プロパティの値によって決まります。  
  
|DateTime.Kind プロパティ|変換|  
|-------------------------|--------|  
|<xref:System.DateTimeKind?displayProperty=fullName>|現地時刻を UTC に変換します。|  
|<xref:System.DateTimeKind?displayProperty=fullName>|`dateTime` パラメーターが現地時刻だと想定し、現地時刻を UTC に変換します。|  
|<xref:System.DateTimeKind?displayProperty=fullName>|`dateTime` パラメーターを変更しないで返します。|  
  
 次に示すコードは、現在の現地時刻を UTC に変換し、結果をコンソールに表示します。  
  
 [!code-csharp[System.TimeZone2.Concepts#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#6)]
 [!code-vb[System.TimeZone2.Concepts#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#6)]  
  
> [!NOTE]
>  <xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=fullName> メソッドでは、<xref:System.TimeZone.ToUniversalTime%2A?displayProperty=fullName> メソッドおよび <xref:System.DateTime.ToUniversalTime%2A?displayProperty=fullName> メソッドと同一の結果が生成されるとは限りません。  ホスト システムのローカル タイム ゾーンに複数の調整規則が含まれる場合、<xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=fullName> は、適切な規則を特定の日付および時刻に適用します。  他の 2 つのメソッドは、最新の調整規則を常に適用します。  
  
 日時値が現地時刻または UTC のどちらも表していない場合、<xref:System.DateTime.ToUniversalTime%2A> メソッドは正しくない結果を返す可能性があります。  ただし、<xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=fullName> メソッドを使用すると、指定したターム ゾーンから日時を変換できます。目的のタイム ゾーンを表す <xref:System.TimeZoneInfo> オブジェクトを取得する方法の詳細については、「[ローカル システムで定義されているタイム ゾーンの検索](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)」を参照してください。次に示すコードでは、<xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=fullName> メソッドを使用して、米国東部標準時を UTC に変換しています。  
  
 [!code-csharp[System.TimeZone2.Concepts#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#7)]
 [!code-vb[System.TimeZone2.Concepts#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#7)]  
  
 <xref:System.DateTime> オブジェクトの <xref:System.DateTime.Kind%2A> プロパティとタイム ゾーンが一致してない場合、このメソッドは <xref:System.ArgumentException> をスローします。  不一致が発生するのは、<xref:System.DateTime.Kind%2A> プロパティが <xref:System.DateTimeKind?displayProperty=fullName> であるのに <xref:System.TimeZoneInfo> オブジェクトがローカル タイム ゾーンを表していない場合、または <xref:System.DateTime.Kind%2A> プロパティが <xref:System.DateTimeKind?displayProperty=fullName> であるのに <xref:System.TimeZoneInfo> オブジェクトが <xref:System.DateTimeKind?displayProperty=fullName> と等しくない場合です。  
  
 これらのメソッドはすべて、<xref:System.DateTime> 値をパラメーターとして受け取り、<xref:System.DateTime> 値を返します。  <xref:System.DateTimeOffset> 値の場合、<xref:System.DateTimeOffset> 構造体には、現在のインスタンスの日時を UTC に変換する <xref:System.DateTimeOffset.ToUniversalTime%2A> インスタンス メソッドがあります。次に示す例では、<xref:System.DateTimeOffset.ToUniversalTime%2A> メソッドを呼び出して、現地時刻と他のいくつかの時刻を UTC に変換しています。  
  
 [!code-csharp[System.DateTimeOffset.Methods#16](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/cs/Methods.cs#16)]
 [!code-vb[System.DateTimeOffset.Methods#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/vb/Methods.vb#16)]  
  
## 指定したタイム ゾーンへの UTC の変換  
 UTC から現地時刻への変換については、後の「UTC から現地時刻への変換」を参照してください。  任意のタイム ゾーンを指定して、UTC をそのタイム ゾーンの時刻に変換するには、<xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A> メソッドを呼び出します。  このメソッドは、次の 2 つのパラメーターを受け取ります。  
  
-   変換対象の UTC。  このパラメーターは、<xref:System.DateTime.Kind%2A> プロパティが <xref:System.DateTimeKind?displayProperty=fullName> または <xref:System.DateTimeKind?displayProperty=fullName> に設定された <xref:System.DateTime> 値である必要があります。  
  
-   UTC の変換先となるタイム ゾーン。  
  
 次に示すコードでは、UTC を米国中部標準時に変換しています。  
  
 [!code-csharp[System.TimeZone2.Concepts#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#8)]
 [!code-vb[System.TimeZone2.Concepts#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#8)]  
  
## UTC から現地時刻への変換  
 UTC を現地時刻に変換するには、変換する時刻を表す <xref:System.DateTime> オブジェクトの <xref:System.DateTime.ToLocalTime%2A> メソッドを呼び出します。  メソッドの具体的な動作は、次の表に示すように、オブジェクトの <xref:System.DateTime.Kind%2A> プロパティの値によって異なります。  
  
|`DateTime.Kind` プロパティ|変換|  
|---------------------------|--------|  
|`DateTimeKind.Local`|<xref:System.DateTime> の値を変更しないで返します。|  
|`DateTimeKind.Unspecified`|<xref:System.DateTime> の値を UTC と想定し、UTC を現地時刻に変換します。|  
|`DateTimeKind.Utc`|<xref:System.DateTime> の値を現地時刻に変換します。|  
  
 **メモ** <xref:System.TimeZone.ToLocalTime%2A?displayProperty=fullName> メソッドの動作は、`DateTime.ToLocalTime` メソッドと同じです。受け取るパラメーターは、変換する日時の値 1 つだけです。  
  
 `static` \(Visual Basic では `Shared`\) <xref:System.TimeZoneInfo.ConvertTime%2A?displayProperty=fullName> メソッドを使用すると、任意のタイム ゾーンの時刻を指定して、現地時刻に変換することもできます。  この方法については、次のセクションで説明します。  
  
## 任意の 2 つのタイム ゾーン間での時刻の変換  
 次に示す <xref:System.TimeZoneInfo> クラスの 2 つの `static` \(Visual Basic では `Shared`\) メソッドを使用すると、任意の 2 つのタイム ゾーン間で時刻を変換できます。  
  
-   <xref:System.TimeZoneInfo.ConvertTime%2A>  
  
     このメソッドのパラメーターは、変換する日時値、その日時値のタイム ゾーンを表す `TimeZoneInfo` オブジェクト、および変換後のタイム ゾーンを表す `TimeZoneInfo` オブジェクトです。  
  
-   <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>  
  
     このメソッドのパラメーターは、変換する日時値、その日時値のタイム ゾーンの識別子、および変換後のタイム ゾーンの識別子です。  
  
 どちらのメソッドでも、変換する日時値の <xref:System.DateTime.Kind%2A> プロパティと、もう 1 つの日時値に対応するタイム ゾーンを表す <xref:System.TimeZoneInfo> オブジェクトまたはタイム ゾーン識別子が必要です。  それ以外の場合は、<xref:System.ArgumentException> がスローされます。  たとえば、日時値の `Kind` プロパティが `DateTimeKind.Local` の場合、メソッドにパラメーターとして渡される `TimeZoneInfo` オブジェクトが `TimeZoneInfo.Local` ではないと、例外がスローされます。  また、メソッドにパラメーターとして渡される識別子が `TimeZoneInfo.Local.Id` に等しくない場合にも、例外がスローされます。  
  
 <xref:System.TimeZoneInfo.ConvertTime%2A> メソッドを使用してハワイ標準時を現地時刻に変換する例を次に示します。  
  
 [!code-csharp[System.TimeZone2.Concepts#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#9)]
 [!code-vb[System.TimeZone2.Concepts#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#9)]  
  
## DateTimeOffset 値の変換  
 <xref:System.DateTimeOffset> オブジェクトはインスタンス化されるときにタイム ゾーンとの関連付けを解除されるので、このオブジェクトによって表される日時値は、完全なタイム ゾーン対応ではありません。  ただし、多くの場合、アプリケーションで必要になるのは、特定のタイム ゾーンでの時刻ではなく、UTC に対する 2 つの異なるオフセットに基づいて日時を変換することだけです。  この変換は、現在のインスタンスの <xref:System.DateTimeOffset.ToOffset%2A> メソッドを呼び出すことで実行できます。  このメソッドの唯一のパラメーターは、メソッドから返される新しい日時値のオフセットです。  
  
 たとえば、Web ページに対するユーザー要求の日時がわかっていて、MM\/dd\/yyyy hh:mm:ss zzzz の形式で文字列としてシリアル化されている場合、次の `ReturnTimeOnServer` メソッドは、この日時値を Web サーバーでの日時に変換します。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/TimeConversions.cs#1)]
 [!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions.vb#1)]  
  
 メソッドが文字列に「9\/1\/5:32 の場合: 07 \-05:00」、タイム ゾーンの時刻を UTC より 5 時間早い表す、9\/1\/3:32:を返します米国の太平洋標準時タイム ゾーンにあるサーバーの 07 年の場合は \-07:00。  
  
 <xref:System.TimeZoneInfo> クラスには、複数の <xref:System.DateTimeOffset> 値を使用してタイム ゾーンの変換を実行する <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=fullName> メソッドのオーバーロードも含まれます。  このメソッドのパラメーターは、<xref:System.DateTimeOffset> 値と、変換後のタイム ゾーンへの参照です。  このメソッドを呼び出すと、<xref:System.DateTimeOffset> 値が返ります。  たとえば、前の例の `ReturnTimeOnServer` メソッドは、<xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29> メソッドの呼び出しを使用して、次のように書き換えることができます。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/timeconversions2.cs#2)]
 [!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions2.vb#2)]  
  
## 参照  
 <xref:System.TimeZoneInfo>   
 [日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)   
 [ローカル システムで定義されているタイム ゾーンの検索](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)