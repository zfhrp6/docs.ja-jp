---
title: "方法 : 日付と時刻の値をラウンドトリップさせる"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- round-trip date and time values
- dates [.NET Framework], round-trip values
- time zones [.NET Framework], round-trip date and time values
- time [.NET Framework], round-trip values
- formatting strings [.NET Framework], round-trip values
ms.assetid: b609b277-edc6-4c74-b03e-ea73324ecbdb
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 515a29e279cfa8fc100e0612fc19df7abc6a3b36
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-round-trip-date-and-time-values"></a>方法 : 日付と時刻の値をラウンドトリップさせる
ある特定の時点を明確に表すように日付と時刻の値を保つことは、多くのアプリケーションに共通する要件です。 このトピックの内容を保存および復元する方法を示しています、<xref:System.DateTime>値、<xref:System.DateTimeOffset>復元された値が保存されている値と同じ時間を識別できるようにゾーンの情報の値、および時刻と日付と時刻の値。  
  
### <a name="to-round-trip-a-datetime-value"></a>DateTime 値をラウンドトリップさせるには  
  
1.  変換、<xref:System.DateTime>を呼び出すことによって、文字列形式の値、 <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> "o"書式指定子を持つメソッドです。  
  
2.  文字列形式を保存、<xref:System.DateTime>値をファイル、またはプロセス、アプリケーション ドメイン、またはコンピューターの境界を通過させます。  
  
3.  表す文字列を取得、<xref:System.DateTime>値。  
  
4.  呼び出す、<xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType>メソッド、およびパス<xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType>の値として、`styles`パラメーター。  
  
 次の例を示していますラウンドト リップする方法、<xref:System.DateTime>値。  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
 [!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]  
  
 場合にラウンド トリップ、<xref:System.DateTime>値、この手法は正常にすべてのローカルと協定世界時刻の時間保持します。 たとえば、ローカル<xref:System.DateTime>値は、米国内のシステムに保存米国中部標準時タイム ゾーンのシステムで復元された場合、復元された日付と時刻は 2 つのタイム ゾーンの時差を反映し、元の時刻より 2 時間後になります。 ただし、タイム ゾーンが指定されていない時刻の場合、この方法では必ずしも正確な結果を得られるわけではありません。 すべて<xref:System.DateTime>値を持つ<xref:System.DateTime.Kind%2A>プロパティは<xref:System.DateTimeKind.Unspecified>はローカル時刻として扱われます。 この場合、これがない場合、<xref:System.DateTime>は正常に、適切な時点を時間で識別できません。 この制限を回避するには、日付と時刻の値と該当するタイム ゾーンを確実に関連付けてから保存操作と復元操作を行います。  
  
### <a name="to-round-trip-a-datetimeoffset-value"></a>DateTimeOffset 値をラウンドトリップさせるには  
  
1.  変換、<xref:System.DateTimeOffset>を呼び出すことによって、文字列形式の値、 <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> "o"書式指定子を持つメソッドです。  
  
2.  文字列形式を保存、<xref:System.DateTimeOffset>値をファイル、またはプロセス、アプリケーション ドメイン、またはコンピューターの境界を通過させます。  
  
3.  表す文字列を取得、<xref:System.DateTimeOffset>値。  
  
4.  呼び出す、<xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType>メソッド、およびパス<xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType>の値として、`styles`パラメーター。  
  
 次の例を示していますラウンドト リップする方法、<xref:System.DateTimeOffset>値。  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
 [!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]  
  
 この手法を常に明確に識別、<xref:System.DateTimeOffset>時間内の単一ポイントとしての値。 値から変換できるを世界協定時刻 (UTC) を呼び出して、<xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType>メソッド、またはそのは呼び出すことでの特定のタイム ゾーンの時刻に変換できる、<xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType>または<xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType>メソッドです。 この手法の大きな限界は、その日付と時刻の算術演算子で実行されると、<xref:System.DateTimeOffset>を特定のタイム ゾーンの時刻を表す値ではそのタイム ゾーンの正確な結果が得られない可能性があります。 これは、ためと、<xref:System.DateTimeOffset>値がインスタンス化される、そのタイム ゾーンの関連付けが解除されします。 したがって、日付と時刻の計算を実行した場合、タイム ゾーンの調整規則は適用されなくなります。 この問題を回避するには、日付と時刻の値、および付随するタイム ゾーンの両方を保持するカスタム型を定義します。  
  
### <a name="to-round-trip-a-date-and-time-value-with-its-time-zone"></a>そのタイム ゾーンの日付と時刻の値をラウンドト リップさせる  
  
1.  クラスまたは 2 つのフィールドを持つ構造体を定義します。 いずれかの最初のフィールドは、<xref:System.DateTime>または<xref:System.DateTimeOffset>オブジェクト、および 2 つ目は、<xref:System.TimeZoneInfo>オブジェクト。 次の例は、このような型の簡易バージョンです。  
  
     [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
     [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]  
  
2.  クラスを宣言、<xref:System.SerializableAttribute>属性。  
  
3.  使用してオブジェクトをシリアル化、<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>メソッドです。  
  
4.  オブジェクトを使用して、復元、<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A>メソッドです。  
  
5.  キャスト (C# の場合) か、適切な型のオブジェクトに逆シリアル化されたオブジェクト (Visual Basic で) に変換します。  
  
 次の例では、日付と時刻とタイム ゾーン情報が格納されたオブジェクトをラウンドト リップさせる方法を示します。  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
 [!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]  
  
 この方法は、どちらも、保存し、復元、および前に待機する時間組み合わされた日付と時刻とタイム ゾーン オブジェクトの実装と同期するように日付値を許可されていないこと、適切な時点を反映常に明確にする必要があります、タイム ゾーンの値です。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 これらの例には次の項目が必要です。  
  
-   次の名前空間は、c# を使用してインポートする`using`ステートメントまたは[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]`Imports`ステートメント。  
  
    -   <xref:System>(C# の場合のみ)。  
  
    -   <xref:System.Globalization?displayProperty=nameWithType>。  
  
    -   <xref:System.IO?displayProperty=nameWithType>。  
  
    -   <xref:System.Runtime.Serialization?displayProperty=nameWithType>。  
  
    -   <xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>。  
  
-   System.Core.dll への参照。  
  
-   各のコード例では、以外の場合、 `DateInTimeZone` 、クラスのクラスまたは Visual Basic モジュールに含まれる、メソッドでは、ラップされたおよびから呼び出される必要がある、`Main`メソッドです。  
  
## <a name="see-also"></a>関連項目  
 [書式設定操作の実行](../../../docs/standard/base-types/performing-formatting-operations.md)  
 [DateTime、DateTimeOffset、TimeSpan、および TimeZoneInfo の使い分け](../../../docs/standard/datetime/choosing-between-datetime.md)  
 [Standard Date and Time Format Strings](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
