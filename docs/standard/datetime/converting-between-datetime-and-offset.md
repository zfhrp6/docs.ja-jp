---
title: "DateTime と DateTimeOffset 間の変換 | Microsoft Docs"
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
  - "変換 (DateTimeOffset 値と DateTime 値を)"
  - "変換 (時間を)"
  - "Date データ型, 変換"
  - "日付 [.NET Framework], 変換"
  - "DateTime 構造体, 変換"
  - "DateTimeOffset 構造体, 変換"
  - "ローカル タイムの変換"
  - "タイム ゾーン [.NET Framework], 変換"
  - "UTC 時刻, 変換"
ms.assetid: b605ff97-0c45-4c24-833f-4c6a3e8be64c
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# DateTime と DateTimeOffset 間の変換
<xref:System.DateTimeOffset> 構造体は <xref:System.DateTime> 構造体と比較してタイム ゾーンへの対応の程度が高くなっていますが、メソッドの呼び出しでは <xref:System.DateTime> パラメーターを使用するのが一般的です。  このため、<xref:System.DateTimeOffset> と <xref:System.DateTime> との間で値を変換する機能は、特に重要になります。  ここでは、タイム ゾーン情報を可能な限り保持しながら、これらの変換を実行する方法について説明します。  
  
> [!NOTE]
>  <xref:System.DateTime> 型と <xref:System.DateTimeOffset> 型には、タイム ゾーンで時刻を表すときにいくつかの制限事項があります。  <xref:System.DateTime.Kind%2A> プロパティを使用すると、<xref:System.DateTime> は世界協定時刻 \(UTC: Coordinated Universal Time\) とシステムのローカル タイム ゾーンのみを反映できます。  <xref:System.DateTimeOffset> は、UTC からの時刻のオフセットを反映しますが、そのオフセットが属する実際のタイム ゾーンは反映しません。  時刻の値とタイム ゾーンのサポートの詳細については、「[DateTime、DateTimeOffset、TimeSpan、および TimeZoneInfo の使い分け](../../../docs/standard/datetime/choosing-between-datetime.md)」を参照してください。  
  
## DateTime から DateTimeOffset への変換  
 <xref:System.DateTimeOffset> 構造体は、大部分の変換処理に適する、<xref:System.DateTime> から <xref:System.DateTimeOffset> への変換を実行するための方法を 2 つ提供します。これらはどちらも同等の効果があります。  
  
-   <xref:System.DateTimeOffset.%23ctor%2A> コンストラクター。<xref:System.DateTime> 値に基づいて、新しい <xref:System.DateTimeOffset> オブジェクトを作成します。  
  
-   暗黙の変換演算子。<xref:System.DateTimeOffset> オブジェクトに対し、<xref:System.DateTime> 値を割り当てることができます。  
  
 UTC およびローカルの <xref:System.DateTime> 値では、結果として出力された <xref:System.DateTimeOffset> 値の <xref:System.DateTimeOffset.Offset%2A> プロパティに、UTC またはローカル タイム ゾーン オフセットが正確に反映されます。  たとえば、次に示すコードでは、UTC 時刻を同等の <xref:System.DateTimeOffset> 値に変換します。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#1)]
 [!code-vb[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#1)]  
  
 この場合、`utcTime2` 変数のオフセットは 00:00 です。  同様に、次に示すコードでは、ローカル タイムを同等の <xref:System.DateTimeOffset> 値に変換します。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#2)]
 [!code-vb[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#2)]  
  
 ただし、<xref:System.DateTime> 値 \(<xref:System.DateTime.Kind%2A> プロパティが <xref:System.DateTimeKind?displayProperty=fullName>\) である場合は、これらの 2 つの変換メソッドにより、オフセットにローカル タイム ゾーンが設定された <xref:System.DateTimeOffset> 値が生成されます。  これは米国の太平洋標準時タイム ゾーンで実行するには、次の例に示します。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#3)]
 [!code-vb[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#3)]  
  
 <xref:System.DateTime> 値がローカル タイム ゾーンでも UTC でもない日付と時刻を反映する場合は、その値を <xref:System.DateTimeOffset> 値に変換し、オーバーロードされた <xref:System.DateTimeOffset.%23ctor%2A> コンストラクターを呼び出すことによって、タイム ゾーン情報を保持できます。  たとえば、中部標準時を反映する <xref:System.DateTimeOffset> オブジェクトをインスタンス化する例を次に示します。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#4)]
 [!code-vb[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#4)]  
  
 時刻の対応するタイム ゾーンの <xref:System.TimeZoneInfo.GetUtcOffset%28System.DateTime%29?displayProperty=fullName> メソッドを呼び出して、コンストラクター オーバーロードに対する 2 番目のパラメーターである <xref:System.TimeSpan> オブジェクト \(UTC からの時刻のオフセットを表す\) を取得する必要があります。  このメソッドの唯一のパラメーターは、変換される日付と時刻を表す <xref:System.DateTime> 値です。  夏時間をサポートするタイム ゾーンである場合にこのパラメーターを使用すると、メソッドによって特定の日付と時刻に対する適切なオフセットを決定できます。  
  
## DateTimeOffset から DateTime への変換  
 <xref:System.DateTimeOffset.DateTime%2A> プロパティは、一般に <xref:System.DateTimeOffset> から <xref:System.DateTime> への変換を実行するときに使用されます。  ただし、次の例に示すように、<xref:System.DateTime.Kind%2A> プロパティが <xref:System.DateTimeKind> である <xref:System.DateTime> 値を返します。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#5)]
 [!code-vb[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#5)]  
  
 これは、<xref:System.DateTimeOffset.DateTime%2A> プロパティが設定された状態で変換を行うと、UTC に対する <xref:System.DateTimeOffset> 値の関係が削除されることを意味します。  これは、UTC 時刻またはシステムの現地時刻に対応する <xref:System.DateTimeOffset> 値に影響します。その理由は、<xref:System.DateTimeOffset.DateTime%2A> 構造体が反映するのは <xref:System.DateTime.Kind%2A> プロパティに設定されている 2 つのタイム ゾーンだけであるからです。  
  
 タイム ゾーン情報を可能な限り保持しながら <xref:System.DateTimeOffset> から <xref:System.DateTime> 値への変換を行うためには、<xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=fullName> プロパティと <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=fullName> プロパティを使用します。  
  
### UTC 時刻の変換  
 変換後の <xref:System.DateTimeOffset.DateTime%2A> 値が UTC 時刻であることを確認するには、<xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=fullName> プロパティの値を取得します。  これは、<xref:System.DateTimeOffset.DateTime%2A> プロパティと 2 つの点で異なります。  
  
-   <xref:System.DateTime> 値を返します。このとき、<xref:System.DateTime.Kind%2A> プロパティは <xref:System.DateTimeKind> に設定されています。  
  
-   <xref:System.DateTimeOffset.Offset%2A> プロパティの値が <xref:System.TimeSpan.Zero?displayProperty=fullName> ではない場合、時刻を UTC に変換します。  
  
> [!NOTE]
>  変換後の <xref:System.DateTime> 値が特定の時刻を明確に示すことが必要なアプリケーションでは、<xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=fullName> プロパティを使用してすべての <xref:System.DateTimeOffset> を <xref:System.DateTime> に変換する処理を行うことを検討してください。  
  
 次のコード例は、<xref:System.DateTimeOffset.UtcDateTime%2A> プロパティを使用して、<xref:System.DateTimeOffset> 値 \(オフセットは <xref:System.TimeSpan.Zero?displayProperty=fullName>\) を <xref:System.DateTime> 値に変換します。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#6)]
 [!code-vb[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#6)]  
  
 次のコード例は、<xref:System.DateTimeOffset.UtcDateTime%2A> プロパティを使用して、<xref:System.DateTimeOffset> 値に対してタイム ゾーン変換と型変換の両方を実行します。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#12)]
 [!code-vb[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#12)]  
  
### 現地時刻の変換  
 <xref:System.DateTimeOffset> 値が現地時刻を表していることを確認するには、<xref:System.DateTimeOffset.DateTime%2A?displayProperty=fullName> プロパティによって返される <xref:System.DateTime> 値を `static` \(Visual Basic では `Shared`\) <xref:System.DateTime.SpecifyKind%2A> メソッドに渡します。  このメソッドは、最初のパラメーターとして渡された日付と時刻を返しますが、<xref:System.DateTime.Kind%2A> プロパティは 2 番目のパラメーターで指定された値に設定されています。  次のコード例は、<xref:System.DateTime.SpecifyKind%2A> メソッドを使用して、<xref:System.DateTimeOffset> 値の変換を行います。この値のオフセットはローカル タイム ゾーンのオフセットに対応します。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#7)]
 [!code-vb[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#7)]  
  
 <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=fullName> プロパティを使用して、<xref:System.DateTimeOffset> 値をローカルな <xref:System.DateTime> 値に変換することもできます。  返される <xref:System.DateTime> 値の <xref:System.DateTime.Kind%2A> プロパティには、<xref:System.DateTimeKind> が設定されています。  次のコード例は、<xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=fullName> プロパティを使用して、<xref:System.DateTimeOffset> 値の変換を行います。この値のオフセットはローカル タイム ゾーンのオフセットに対応します。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#10)]
 [!code-vb[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#10)]  
  
 <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=fullName> プロパティを使用して <xref:System.DateTime> 値を取得すると、プロパティの `get` アクセサーは、まず <xref:System.DateTimeOffset> 値を UTC に変換し、次に <xref:System.DateTimeOffset.ToLocalTime%2A> メソッドを呼び出して現地時刻に変換します。  これは、<xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=fullName> プロパティの値を取得して、型変換の実行と同時にタイム ゾーンの変換も実行できることを意味します。  また、変換実行時にはローカル タイム ゾーンの調整規則が適用されることにもなります。  次のコード例は、<xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=fullName> プロパティを使用して、型変換とタイム ゾーン変換の両方を実行します。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#11)]
 [!code-vb[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#11)]  
  
### 汎用変換メソッド  
 次の例では、`ConvertFromDateTimeOffset` というメソッドを定義します。このメソッドは、<xref:System.DateTimeOffset> 値を <xref:System.DateTime> 値に変換します。  そのオフセットに基づいて、<xref:System.DateTimeOffset> 値が UTC 時刻、現地時刻、その他の時刻のいずれであるかを判断し、それに応じて、返される日付と時刻の値の <xref:System.DateTime.Kind%2A> プロパティを定義します。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#8)]
 [!code-vb[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#8)]  
  
 次の例では、米国の中部標準時ゾーンの UTC 時刻、現地時間と時刻を表す <xref:System.DateTimeOffset> 値を変換するに `ConvertFromDateTimeOffset` のメソッドを呼び出します。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#9)]
 [!code-vb[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#9)]  
  
 このコードでは、アプリケーションおよび日付と時刻の値のソースに応じて、必ずしも常に有効ではない 2 つの前提条件が想定されます。  
  
-   オフセットが <xref:System.TimeSpan.Zero?displayProperty=fullName> に設定されている日付と時刻の値は、UTC 時刻を表すことを前提とします。  実際には、UTC は特定のタイム ゾーンの時刻ではありませんが、この時刻を基準として世界のタイム ゾーンの時刻が標準化されます。  タイム ゾーンには、<xref:System.TimeSpan.Zero> のオフセットを設定することもできます。  
  
-   ローカル タイム ゾーンのオフセットに等しいオフセットが設定された日付と時刻は、ローカル タイム ゾーンを表すことを前提とします。  日付と時刻の値と元のタイム ゾーンとの関連付けが解除されていることが理由となって、この前提条件に該当しないことがあります。日付と時刻には、同じオフセットが設定された他のタイム ゾーンの日付と時刻を設定できます。  
  
## 参照  
 [日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)