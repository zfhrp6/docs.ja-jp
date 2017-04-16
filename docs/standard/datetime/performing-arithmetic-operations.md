---
title: "日付と時刻を使用した算術演算の実行 | Microsoft Docs"
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
  - "算術演算 [.NET Framework], 日付と時刻"
  - "日付 [.NET Framework], 算術演算"
  - "日付 [.NET Framework], 比較"
  - "DateTime 構造体, 算術演算"
  - "DateTimeOffset 構造体, 算術演算"
  - "タイム ゾーン [.NET Framework], 算術演算"
  - "時刻 [.NET Framework], 算術演算"
ms.assetid: 87c7ddf2-f15e-48af-8602-b3642237e6d0
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# 日付と時刻を使用した算術演算の実行
<xref:System.DateTime> 構造体と <xref:System.DateTimeOffset> 構造体はいずれも、構造体の値に対して算術演算を実行するメンバーを提供しますが、演算の結果は大きく異なります。  ここでは、その相違点について考察し、日付と時刻のデータにおけるタイム ゾーンへの対応の程度について詳述します。さらに、日付と時刻のデータを使用して、タイム ゾーンに完全に対応した操作を実行する方法について解説します。  
  
## DateTime 値を使用した比較演算と算術演算  
 .NET Framework Version 2.0 以降では、<xref:System.DateTime> 値でのタイム ゾーンへの対応は限られたものになっています。  <xref:System.DateTime.Kind%2A?displayProperty=fullName> プロパティを使用すると、<xref:System.DateTimeKind> 値を日付と時刻に割り当てて、それが表す内容が現地時刻、世界協定時刻 \(UTC: Coordinated Universal Time\)、タイム ゾーンが指定されていない時刻のいずれであるかを示すことができます。  ただし、<xref:System.DateTime> 値で日付と時刻の比較演算や算術演算が実行されるときには、このタイム ゾーンについての制限された情報は無視されます。  この例を次に示します。例では、現在の現地時刻を現在の UTC 時刻と比較します。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual2.cs#2)]
 [!code-vb[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual2.vb#2)]  
  
 <xref:System.DateTime.CompareTo%28System.DateTime%29> のメソッドは米国の太平洋標準時タイム ゾーンのシステムの UTC と現地時間の違いを 7 時間であることを現地時間 \(または未満\) は UTC 時刻よりも早い\)、および減算演算は次のことを報告します。  しかし、これらの 2 つの値では時刻の表現方法が異なるため、この例では明らかに、時間間隔は UTC からのローカル タイム ゾーンのオフセットに完全に帰属します。  
  
 より一般的な例としては、<xref:System.DateTime.Kind%2A?displayProperty=fullName> プロパティは <xref:System.DateTime> 比較演算および算術演算によって返される結果には影響しないことが挙げられます \(同じ 2 つの時刻の比較が行われるため\)。ただし、結果の解釈には影響することがあります。  たとえば、次のようになります。  
  
-   2 つの日付と時刻の値 \(<xref:System.DateTime.Kind%2A?displayProperty=fullName> プロパティはいずれも <xref:System.DateTimeKind> に設定されている\) に対して実行した算術演算の結果には、2 つの値の間の実際の時間間隔が反映されます。  同様に、このような 2 つの日付と時刻の値を比較すると、時刻間の関係が正確に反映されます。  
  
-   2 つの日付と時刻の値 \(<xref:System.DateTime.Kind%2A?displayProperty=fullName> プロパティがいずれも <xref:System.DateTimeKind> に設定されているか、2 つの日付と時刻の値にはそれぞれ異なる <xref:System.DateTime.Kind%2A?displayProperty=fullName> プロパティ値が設定されている\) に対して実行した算術演算または比較演算の結果には、2 つの値の間のクロック時間の差異が反映されます。  
  
-   ローカルの日付と時刻の値に対して実行される算術演算と比較演算では、特定の値が不明確または無効であるかは考慮されません。また、ローカル タイム ゾーンの夏時間への移行または夏時間からの移行によって生じる調整規則の影響についても考慮されません。  
  
-   UTC 時刻と現地時刻との差異を比較または算出する演算には、時間間隔が含まれます。この時間間隔は、結果として求められる UTC からのローカル タイム ゾーンのオフセットに等しくなります。  
  
-   タイム ゾーンが指定されていない時刻と UTC 時刻または現地時刻との差異を比較または算出する演算には、単にクロック時間が反映されます。  タイム ゾーン間の差異は考慮されず、結果にはタイム ゾーン調整規則のアプリケーションは反映されません。  
  
-   タイム ゾーンが指定されていない 2 つの時刻間での差異を比較または算出する演算には、未知の間隔が含まれます。この時間間隔には、2 つの異なるタイム ゾーンにおける時差が反映されます。  
  
 タイム ゾーンの相違が日付と時刻の計算に影響しないシナリオ \(詳細については、「[DateTime、DateTimeOffset、TimeSpan、および TimeZoneInfo の使い分け](../../../docs/standard/datetime/choosing-between-datetime.md)」を参照\) や、日付と時刻のデータのコンテキストによって比較演算と算術演算の意味を定義するシナリオなど、さまざまなシナリオがあります。  
  
## DateTimeOffset 値を使用した比較演算と算術演算  
 <xref:System.DateTimeOffset> 値には、日付と時刻だけでなく、UTC に対する日付と時刻を明確に定義するオフセットも定義されます。  これにより、<xref:System.DateTime> 値とはいくぶん異なる等値性を定義できるようになります。  <xref:System.DateTime> 値は日付と時刻の値が同じである場合に等しくなりますが、<xref:System.DateTimeOffset> 値は同じ時刻を参照している場合に等しくなります。  これによって <xref:System.DateTimeOffset> 値の精度が高まり、2 つの日付と時刻の間隔を判定する比較演算や大部分の算術演算で使用するときに解釈を行う必要性が低くなります。  次の例では、現地時刻および UTC 時刻の <xref:System.DateTime> 値を比較した前述の例と同じ <xref:System.DateTimeOffset> を使用して、その動作の違いを示します。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual3.cs#3)]
 [!code-vb[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual3.vb#3)]  
  
 この例では、<xref:System.DateTimeOffset.CompareTo%2A> メソッドにより、現在の現地時刻と現在の UTC 時刻が等しいことが示されます。また、<xref:System.DateTimeOffset> 値の減算により、2 つの時刻の差が <xref:System.TimeSpan.Zero?displayProperty=fullName> であることが示されます。  
  
 日付と時刻の算術演算で <xref:System.DateTimeOffset> 値を使用するときの主な制限事項は、<xref:System.DateTimeOffset> 値はタイム ゾーンに対応しているものの、それが完全ではないことです。  <xref:System.DateTimeOffset> 変数に最初に値が割り当てられ、タイム ゾーンとの関連付けが解除されたときに、<xref:System.DateTimeOffset> 値のオフセットに UTC からのローカル タイム ゾーンのオフセットが反映されます。  識別できる時間に直接関連付けられていないため、日付と時刻の間隔の加算と減算では、タイム ゾーンの調整規則は考慮されません。  
  
 実際の例では、米国の中部標準時ゾーンの夏時間への移行が 2008 \(3 年 12 月 9 日の午前 2:00 で発生します。  これは、2 種類を追加したことを意味し、2008 年 1 月 3 日 9 時に午前 1:30 の中部標準時に 30 分の間隔は 2008 \(3 年 12 月 9 日の午前 5:00 の日時を生成します。  ただし、次の例に示すように、追加の結果が 2008 \(3 年 12 月 9 日の午前 4:00 です。  この時刻は目的のタイム ゾーンの時刻ではありませんが \(予期したタイム ゾーン オフセットではありませんが\)、演算の結果は正しい時刻を表していることに留意してください。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual4.cs#4)]
 [!code-vb[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual4.vb#4)]  
  
## タイム ゾーンの時刻を使用した算術演算  
 <xref:System.TimeZoneInfo> クラスには、タイム ゾーン間で時刻を変換するときに自動的に調整を適用する変換メソッドが数多く含まれています。  次に例を示します。  
  
-   <xref:System.TimeZoneInfo.ConvertTime%2A> メソッドと <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A> メソッド。任意の 2 つのタイム ゾーン間で時刻を変換します。  
  
-   <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A> メソッドと <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> メソッド。特定のタイム ゾーンの時刻から UTC、または UTC から特定のタイム ゾーンの時刻に変換します。  
  
 詳細については、「[タイム ゾーン間での時刻の変換](../../../docs/standard/datetime/converting-between-time-zones.md)」を参照してください。  
  
 <xref:System.TimeZoneInfo> クラスでは、日付と時刻の算術演算を実行するとき、調整規則を自動的に適用するメソッドは提供されません。  ただし、タイム ゾーンの時刻を UTC 時刻に変換し、算術演算を実行して、UTC 時刻からタイム ゾーンの時刻に戻すことで、この処理を実行できます。  詳細については、「[方法 : 日付と時刻の演算でタイム ゾーンを使用する](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)」を参照してください。  
  
 たとえば、次のコードでは、2008 年 1 月 3 日 9 時追加した前のコードと似ています。に午前 2:00 に 2.5 時間かかります。  ここでは、日付と時刻の算術演算を実行して UTC 時刻から中部標準時に結果を変換する前に、中部標準時が UTC 時刻に変換されるため、結果の時刻には中部標準時ゾーンの夏時間への移行が反映されます。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual5.cs#5)]
 [!code-vb[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual5.vb#5)]  
  
## 参照  
 [日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)   
 [方法 : 日付と時刻の演算でタイム ゾーンを使用する](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)