---
title: "方法 : 調整規則のあるタイム ゾーンを作成する | Microsoft Docs"
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
  - "調整規則 [.NET Framework]"
  - "タイム ゾーン [.NET Framework], および調整規則"
  - "タイム ゾーン [.NET Framework], 作成"
ms.assetid: c52ef192-13a9-435f-8015-3b12eae8c47c
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : 調整規則のあるタイム ゾーンを作成する
アプリケーションで必要な正確なタイム ゾーン情報が、次のような理由で特定のシステムに存在しない場合があります。  
  
-   ローカル システムのレジストリでタイム ゾーンが定義されていない。  
  
-   タイム ゾーンに関するデータがレジストリで変更または削除されている。  
  
-   タイム ゾーンに、過去の特定の期間のタイム ゾーン調整に関する正確な情報がない。  
  
 このような場合は、<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> メソッドを呼び出して、アプリケーションで必要なタイム ゾーンを定義できます。  このメソッドのオーバーロードを使用すると、調整規則のあるタイム ゾーンまたは調整規則のないタイム ゾーンを作成できます。  タイム ゾーンが夏時間をサポートする場合は、固定調整規則または浮動調整規則の調整を定義できます。これらの用語の定義については、「[タイム ゾーンの概要](../../../docs/standard/datetime/time-zone-overview.md)」の「タイム ゾーンの用語」の節を参照してください。  
  
> [!IMPORTANT]
>  <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> メソッドを呼び出すことで作成されるカスタム タイム ゾーンは、レジストリには追加されません。  カスタム タイム ゾーンには、<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> メソッドの呼び出しによって返されるオブジェクト参照を通してのみアクセスできます。  
  
 このトピックでは、調整規則のあるタイム ゾーンを作成する方法について説明します。  夏時間調整規則をサポートしないタイム ゾーンを作成する方法については、「[方法 : 調整規則のないタイム ゾーンを作成する](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)」を参照してください。  
  
### 浮動調整規則のあるタイム ゾーンを作成するには  
  
1.  調整ごとに \(つまり、特定の期間における標準時間からの切り替えと標準時間への切り替えのそれぞれについて\)、次の操作を行います。  
  
    1.  タイム ゾーン調整の切り替え開始時刻を定義します。  
  
         <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=fullName> メソッドを呼び出して、切り替えの時刻を定義する <xref:System.DateTime> 値、切り替えの月を定義する整数値、切り替えを行う週を定義する整数値、および切り替えを行う曜日を定義する <xref:System.DayOfWeek> 値を渡します。  このメソッド呼び出しにより、<xref:System.TimeZoneInfo.TransitionTime> オブジェクトがインスタンス化されます。  
  
    2.  タイム ゾーン調整の切り替え終了時刻を定義します。  これには、<xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=fullName> メソッドをもう一度呼び出す必要があります。  このメソッド呼び出しでは、2 番目の <xref:System.TimeZoneInfo.TransitionTime> オブジェクトがインスタンス化されます。  
  
    3.  <xref:System.TimeZoneInfo.AdjustmentRule.CreateAdjustmentRule%2A> メソッドを呼び出して、その調整が有効になる開始日と終了日、切り替えによって変動する時間数を定義する <xref:System.TimeSpan> オブジェクト、および夏時間への切り替えと夏時間からの切り替えが行われる日時を定義する 2 つの <xref:System.TimeZoneInfo.TransitionTime> オブジェクトを渡します。  このメソッド呼び出しにより、<xref:System.TimeZoneInfo.AdjustmentRule> オブジェクトがインスタンス化されます。  
  
    4.  <xref:System.TimeZoneInfo.AdjustmentRule> オブジェクトを、<xref:System.TimeZoneInfo.AdjustmentRule> オブジェクトの配列に割り当てます。  
  
2.  タイム ゾーンの表示名を指定します。  表示名は、世界協定時刻 \(UTC: Coordinated Universal Time\) からのタイム ゾーンのオフセットをかっこで囲み、その後にタイム ゾーン、タイム ゾーン内の 1 つ以上の都市、またはタイム ゾーン内の 1 つ以上の国や地域を表す文字列が続く標準形式に従います。  
  
3.  タイム ゾーンの標準時間の名前を指定します。  通常は、この文字列がタイム ゾーンの ID としても使用されます。  
  
4.  タイム ゾーンの夏時間の名前を指定します。  
  
5.  タイム ゾーンの標準名とは異なる ID を使用する場合は、タイム ゾーン ID を指定します。  
  
6.  UTC からのタイム ゾーンのオフセットを定義する <xref:System.TimeSpan> オブジェクトをインスタンス化します。  UTC より後の時刻のタイム ゾーンでは正のオフセットになります。  UTC より前の時刻のタイム ゾーンでは負のオフセットになります。  
  
7.  [TimeZoneInfo.CreateCustomTimeZone\(String, TimeSpan, String, String, String, TimeZoneInfo.AdjustmentRule\<xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=fullName> メソッドを呼び出して、新しいタイム ゾーンをインスタンス化します。  
  
## 使用例  
 次の例では、1918 年から現在までのさまざまな期間に対する調整規則が含まれる、米国の中部標準時ゾーンを定義します。  
  
 [!code-csharp[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#5)]
 [!code-vb[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#5)]  
  
 この例で作成されるタイム ゾーンには、複数の調整規則があります。  ある調整規則の有効期間の開始日と終了日が、別の調整規則の期間と重ならないように注意する必要があります。  重なる期間があると、<xref:System.InvalidTimeZoneException> がスローされます。  
  
 浮動調整規則の場合、特定の月の最終週に切り替えを行うことを示すには、<xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> メソッドの `week` パラメーターに値 5 を渡します。  
  
 [TimeZoneInfo.CreateCustomTimeZone\(String, TimeSpan, String, String, String, TimeZoneInfo.AdjustmentRule\<xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=fullName> メソッドの呼び出しで使用する <xref:System.TimeZoneInfo.AdjustmentRule> オブジェクトの配列を作成するときは、タイム ゾーンに対して作成する調整の数に合わせて配列のサイズを初期化してもかまいません。  このコード例では、代わりに、<xref:System.Collections.Generic.List%601.Add%2A> メソッドを呼び出して、各調整規則を <xref:System.TimeZoneInfo.AdjustmentRule> オブジェクトのジェネリック <xref:System.Collections.Generic.List%601> コレクションに追加しています。  その後、<xref:System.Collections.Generic.List%601.CopyTo%2A> メソッドを呼び出して、このコレクションのメンバーを配列にコピーします。  
  
 この例では、<xref:System.TimeZoneInfo.TransitionTime.CreateFixedDateRule%2A> メソッドを使用して、固定日付の調整も定義しています。  これは <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> メソッドの呼び出しと似ていますが、切り替えパラメーターの時刻、月、および日以外は必要とされない点が異なります。  
  
 この例は、次のようなコードを使用してテストできます。  
  
 [!code-csharp[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#7)]
 [!code-vb[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#7)]  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   System.Core.dll への参照をプロジェクトに追加する。  
  
-   次の名前空間をインポートする。  
  
     [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
     [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]  
  
## 参照  
 [日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)   
 [タイム ゾーンの概要](../../../docs/standard/datetime/time-zone-overview.md)   
 [方法 : 調整規則のないタイム ゾーンを作成する](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)