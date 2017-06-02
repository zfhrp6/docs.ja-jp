---
title: ".NET Framework における日付と時刻文字列の解析の解析 | Microsoft Docs"
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
  - "基本型, 解析 (文字列を)"
  - "日付と時刻文字列"
  - "DateTime オブジェクト"
  - "列挙型 [.NET Framework], 解析 (文字列を)"
  - "ParseExact メソッド"
  - "解析 (文字列を), 日付と時刻文字列"
  - "時間の文字列"
ms.assetid: 43bae51e-9b1d-41a6-a187-772c0d096d90
caps.latest.revision: 24
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 24
---
# .NET Framework における日付と時刻文字列の解析の解析
解析メソッドは、日付と時刻の文字列形式を、等価の <xref:System.DateTime> オブジェクトに変換します。  <xref:System.DateTime.Parse%2A> メソッドと <xref:System.DateTime.TryParse%2A> メソッドは、複数ある日付と時刻の共通形式をどれでも変換します。  <xref:System.DateTime.ParseExact%2A> メソッドと <xref:System.DateTime.TryParseExact%2A> メソッドは、日時書式指定文字列で指定されるパターンに準拠する文字列形式を変換します \([標準の日時書式指定文字列](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)および[カスタム日時書式指定文字列](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)に関するトピックを参照してください\)。  
  
 解析は、日付と時刻の区切り記号に使用される文字列または月、日、年号の名前などの情報を提供する書式プロバイダーのプロパティに影響されます。  書式プロバイダーは、現在の <xref:System.Globalization.DateTimeFormatInfo> オブジェクトであり、現在のスレッド カルチャによって暗黙的に指定されるか、または解析メソッドの <xref:System.IFormatProvider> パラメーターによって明示的に指定されます。  <xref:System.IFormatProvider> パラメーターには、カルチャを表す <xref:System.Globalization.CultureInfo> オブジェクト、または <xref:System.Globalization.DateTimeFormatInfo> オブジェクトを指定します。  
  
 解析される日付の文字列形式には、月と、日または年の少なくともどちらかが含まれている必要があります。  時刻の文字列形式には、時間と、分または AM\/PM 指定子の少なくともどちらかが含まれている必要があります。  ただし可能であれば、省略された構成要素に対して解析が既定値を使用します。  日付がない場合は現在の日付、年がない場合は現在の年、月の日付がない場合はその月の初日、時刻がない場合は午前 0 時が、それぞれ既定で設定されます。  
  
 文字列形式が時刻のみを指定している場合は、解析が <xref:System.DateTime> オブジェクトの <xref:System.DateTime.Year%2A>、<xref:System.DateTime.Month%2A>、および <xref:System.DateTime.Day%2A> の各プロパティを <xref:System.DateTime.Today%2A> プロパティの対応する値に設定して、このオブジェクトを返します。  ただし、解析メソッドに <xref:System.Globalization.DateTimeStyles> 定数が指定された場合は、結果の年、月、および日の各プロパティが値 `1` に設定されます。  
  
 日付と時刻の文字列形式には、日付と時刻の構成要素に加えて、世界協定時刻 \(UTC: Coordinated Universal Time\) との時間の差を示すオフセットを含めることができます。  たとえば、"2\/14\/2007 5:32:00 \-7:00" という文字列は、UTC より 7 時間早い時刻を定義します。  時刻の文字列形式でオフセットが省略されている場合、解析は <xref:System.DateTime> オブジェクトの <xref:System.DateTime.Kind%2A> プロパティを <xref:System.DateTimeKind?displayProperty=fullName> に設定して返します。  オフセットが指定されている場合、解析は <xref:System.DateTime> オブジェクトの <xref:System.DateTime.Kind%2A> プロパティを <xref:System.DateTimeKind> に設定し、値をコンピューターのローカル タイム ゾーンに調整して返します。  この動作は、解析メソッドに <xref:System.Globalization.DateTimeStyles> 定数を使用することで変更できます。  
  
 書式プロバイダーは、あいまいな数値の日付を解釈する際にも使用されます。  たとえば、文字列 "02\/03\/04" で表された日付は、どの構成要素が月、日、年であるかが明確ではありません。  この場合は、書式プロバイダーの類似する日付形式の順序に従って構成要素が解釈されます。  
  
## Parse  
 **Parse** メソッドを使用して文字列を **DateTime** に変換するコード例を次に示します。  この例では、現在のスレッドに関連付けられているカルチャを使用して解析が実行されます。  現在のカルチャに関連付けられている <xref:System.Globalization.CultureInfo> で入力文字列を解析できない場合は、<xref:System.FormatException> がスローされます。  
  
 [!code-csharp[Parsing.DateAndTime#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example.cs#1)]
 [!code-vb[Parsing.DateAndTime#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example.vb#1)]  
  
 カルチャの 1 つを定義するように **CultureInfo** を設定して、そのオブジェクトを指定するか、<xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=fullName> プロパティによって返される標準の <xref:System.Globalization.DateTimeFormatInfo> オブジェクトの 1 つを指定することもできます。  書式プロバイダーを使用してドイツ語文字列を **DateTime** に変換するコード例を次に示します。  この文字列を正しく解析するには、de\-DE \(ドイツのドイツ語\) カルチャを表す **CultureInfo** を定義し、解析する文字列と共に渡します。  これにより、**CurrentThread** の **CurrentCulture** の設定が無視されます。  
  
 [!code-csharp[Parsing.DateAndTime#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example2.cs#2)]
 [!code-vb[Parsing.DateAndTime#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example2.vb#2)]  
  
 ただし、<xref:System.DateTime.Parse%2A> メソッドのオーバーロードを使用するとカスタム書式プロバイダーを指定できますが、このメソッド自体は標準以外の書式プロバイダーの使用をサポートしていません。  標準以外の形式で表された日付と時刻を解析するには、代わりに <xref:System.DateTime.ParseExact%2A> メソッドを使用します。  
  
 <xref:System.Globalization.DateTimeStyles> 列挙体を使用して、文字列で定義されていないフィールドについて、現在の日付と時刻の情報を **DateTime** に追加しないように指定するコード例を次に示します。  
  
 [!code-csharp[Parsing.DateAndTime#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example3.cs#3)]
 [!code-vb[Parsing.DateAndTime#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example3.vb#3)]  
  
## ParseExact  
 <xref:System.DateTime.ParseExact%2A?displayProperty=fullName> メソッドは、指定した文字列パターンに準拠する文字列を **DateTime** オブジェクトに変換します。  指定された書式に従っていない文字列をこのメソッドに渡すと、<xref:System.FormatException> がスローされます。  標準の日付と時刻書式指定子のいずれかを指定するか、またはカスタムの日付と時刻書式指定子の限定された組み合わせを指定できます。  カスタムの書式指定子を使用すると、カスタムの認識文字列を生成できます。  指定子の説明については、[標準の日時書式指定文字列](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)および[カスタム日時書式指定文字列](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)に関するトピックを参照してください。  
  
 <xref:System.DateTime.ParseExact%2A> メソッドの各オーバーロードは、<xref:System.IFormatProvider> パラメーターも受け取ります。このパラメーターは、通常、文字列の書式に関するカルチャ固有の情報を指定します。  多くの場合、この <xref:System.IFormatProvider> オブジェクトは、標準のカルチャを表す <xref:System.Globalization.CultureInfo> オブジェクトか、または <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=fullName> プロパティによって返される <xref:System.Globalization.DateTimeFormatInfo> オブジェクトです。  ただし、日付と時刻を解析する他の関数とは異なり、このメソッドは標準以外の日付と時刻の形式を定義する <xref:System.IFormatProvider> もサポートします。  
  
 次のコード例では、解析する文字列オブジェクト、書式指定子、および **CultureInfo** オブジェクトを **ParseExact** メソッドに渡しています。  この **ParseExact** メソッドは、en\-US カルチャの Long Date パターンを表す文字列だけを解析できます。  
  
 [!code-csharp[Parsing.DateAndTime#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example4.cs#4)]
 [!code-vb[Parsing.DateAndTime#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example4.vb#4)]  
  
## 参照  
 [文字列の解析](../../../docs/standard/base-types/parsing-strings.md)   
 [型の書式設定](../../../docs/standard/base-types/formatting-types.md)   
 [.NET Framework における型変換](../../../docs/standard/base-types/type-conversion.md)