---
title: "方法 : 日付と時刻の値をラウンドトリップさせる | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ラウンドトリップ (日付と時刻の値を)"
  - "日付 [.NET Framework]、ラウンドトリップ (値を)"
  - "タイム ゾーン [.NET Framework]、ラウンドトリップ (日付と時刻の値を)"
  - "時刻 [.NET Framework]、ラウンドトリップ (値を)"
  - "書式指定 (文字列の) [.NET Framework]、ラウンドトリップ (値を)"
ms.assetid: b609b277-edc6-4c74-b03e-ea73324ecbdb
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : 日付と時刻の値をラウンドトリップさせる
ある特定の時点を明確に表すように日付と時刻の値を保つことは、多くのアプリケーションに共通する要件です。  このトピックでは、<xref:System.DateTime> 値、<xref:System.DateTimeOffset> 値、およびタイム ゾーン情報を持った日時値を保存する方法、および、保存した日時とまったく同じ時点を表すように復元する方法について説明します。  
  
### DateTime 値をラウンドトリップさせるには  
  
1.  <xref:System.DateTime.ToString%28System.String%29?displayProperty=fullName> メソッドと "o" 書式指定子を使用して、<xref:System.DateTime> 値を対応する文字列形式に変換します。  
  
2.  <xref:System.DateTime> 値の文字列形式をファイルに保存するか、プロセス、アプリケーション ドメイン、またはマシン境界に渡します。  
  
3.  <xref:System.DateTime> 値を表す文字列を取得します。  
  
4.  <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=fullName> メソッドを呼び出し、`styles` パラメーターの値として <xref:System.Globalization.DateTimeStyles?displayProperty=fullName> を渡します。  
  
 <xref:System.DateTime> の値をラウンドトリップさせる方法を次の例に示します。  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
 [!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]  
  
 <xref:System.DateTime> の値をラウンドトリップさせる場合、この方法により、あらゆる現地時刻と協定世界時刻を適切に保存できます。  たとえば、<xref:System.DateTime> ローカル値は米国の太平洋標準時タイム ゾーンのシステムに格納され、米国の中部標準時ゾーンのシステムで保存した場合、元の時刻は 2 個のタイム ゾーン間の時差を反映し、元の時刻より後の 2 時間です。  ただし、タイム ゾーンが指定されていない時刻の場合、この方法では必ずしも正確な結果を得ることができません。  <xref:System.DateTime.Kind%2A> プロパティが <xref:System.DateTimeKind> である <xref:System.DateTime> 値はすべて現地時刻として扱われます。  現地時刻以外では、<xref:System.DateTime> が間違った時点を示すことになります。  この制限は、日付と時刻の値に、該当するタイム ゾーンを確実に関連付けた上で、保存操作と復元操作を行うことによって回避できます。  
  
### DateTimeOffset 値をラウンドトリップさせるには  
  
1.  <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=fullName> メソッドと "o" 書式指定子を使用して、<xref:System.DateTimeOffset> 値を対応する文字列形式に変換します。  
  
2.  <xref:System.DateTimeOffset> 値の文字列形式をファイルに保存するか、プロセス、アプリケーション ドメイン、またはマシン境界に渡します。  
  
3.  <xref:System.DateTimeOffset> 値を表す文字列を取得します。  
  
4.  <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=fullName> メソッドを呼び出し、`styles` パラメーターの値として <xref:System.Globalization.DateTimeStyles?displayProperty=fullName> を渡します。  
  
 <xref:System.DateTimeOffset> の値をラウンドトリップさせる方法を次の例に示します。  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
 [!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]  
  
 この方法により、<xref:System.DateTimeOffset> の値が、常にある特定の時点として明確に識別されます。  その後、<xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=fullName> メソッドを呼び出すことによって、この値を世界協定時刻 \(UTC\) に変換できます。また、<xref:System.DateTimeOffset.ToOffset%2A?displayProperty=fullName> メソッドまたは <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=fullName> メソッドを呼び出すことによって、特定のタイム ゾーンの時刻に変換することもできます。  この方法には、特定のタイム ゾーンの時刻を表す <xref:System.DateTimeOffset> の値に対して日付と時刻の演算を行った場合、そのタイム ゾーンにおける正確な結果を得ることができないという重要な制限があります。  これは、<xref:System.DateTimeOffset> の値をインスタンス化すると、対応するタイム ゾーンとの関連付けが解除されるためです。  したがって、日付と時刻の計算を実行した場合、タイム ゾーンの調整規則は適用されません。  この問題は、日付値と時刻値、および付随するタイム ゾーンを保持するカスタム型を定義することによって回避できます。  
  
### 対応するタイム ゾーンと共に日付と時刻の値をラウンドトリップさせるには  
  
1.  2 つのフィールドを持ったクラスまたは構造体を定義します。  1 つ目のフィールドは <xref:System.DateTime> オブジェクトまたは <xref:System.DateTimeOffset> オブジェクトに、2 つ目のフィールドは <xref:System.TimeZoneInfo> オブジェクトにします。  これを踏まえた単純な型の例を次に示します。  
  
     [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
     [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]  
  
2.  このクラスに <xref:System.SerializableAttribute> 属性を適用します。  
  
3.  <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=fullName> メソッドを使用してオブジェクトをシリアル化します。  
  
4.  <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> メソッドを使用してオブジェクトを復元します。  
  
5.  逆シリアル化したオブジェクトを適切な型のオブジェクトにキャスト \(C\# の場合\) または変換 \(Visual Basic の場合\) します。  
  
 日付値と時刻値およびタイム ゾーン情報が格納されたオブジェクトをラウンドトリップさせる方法を次の例に示します。  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
 [!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]  
  
 この方法では、日付、時刻、およびタイム ゾーンの組み合わせを保持するオブジェクトが、日付値とタイム ゾーン値を確実に同期するように実装されている場合、保存と復元の前後で正確な時点が常に明確に反映されます。  
  
## コードのコンパイル  
 これらの例では、次の項目が必要です。  
  
-   C\# の `using` ステートメントまたは [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] の `Imports` ステートメントで次の名前空間がインポートされていること。  
  
    -   <xref:System> \(C\# のみ\)。  
  
    -   <xref:System.Globalization?displayProperty=fullName>.  
  
    -   <xref:System.IO?displayProperty=fullName>.  
  
    -   <xref:System.Runtime.Serialization?displayProperty=fullName>.  
  
    -   <xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=fullName>.  
  
-   System.Core.dll が参照設定されていること。  
  
-   `DateInTimeZone` クラス以外のすべてのコード例は、クラスまたは Visual Basic のモジュールのメソッドとして記述し、`Main` メソッドから呼び出すこと。  
  
## 参照  
 [書式設定操作の実行](../../../docs/standard/base-types/performing-formatting-operations.md)   
 [DateTime、DateTimeOffset、TimeSpan、および TimeZoneInfo の使い分け](../../../ocs/standard/datetime/choosing-between-datetime.md)   
 [標準の日時書式指定文字列](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)