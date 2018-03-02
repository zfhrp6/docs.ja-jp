---
title: ".NET Framework における日付と時刻文字列の解析の解析"
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
- parsing strings, date and time strings
- date and time strings
- ParseExact method
- enumerations [.NET Framework], parsing strings
- base types, parsing strings
- DateTime object
- time strings
ms.assetid: 43bae51e-9b1d-41a6-a187-772c0d096d90
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6e3ef01abdb615b2850b5a9d07e1208ee22eda95
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="parsing-date-and-time-strings-in-net"></a>.NET での日付と時刻文字列の解析
解析メソッドは、日付と時刻の文字列形式を等価の <xref:System.DateTime> オブジェクトに変換します。 <xref:System.DateTime.Parse%2A> メソッドと <xref:System.DateTime.TryParse%2A> メソッドでは、日付と時刻のいくつかの共通表現のいずれかを変換します。 <xref:System.DateTime.ParseExact%2A> メソッドと <xref:System.DateTime.TryParseExact%2A> メソッドでは、日付と時刻の書式指定文字列で指定されたパターンに適合する文字列形式を変換します。 ([標準の日付と時刻の書式指定文字列](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)と[カスタムの日付と時刻の書式指定文字列](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)に関するトピックをご覧ください)。  
  
 解析は、日付と時刻の区切り記号、および月、日、および年号の名前に使用される文字列などの情報を提供する書式プロバイダーのプロパティの影響を受けます。 書式プロバイダーは、現在の <xref:System.Globalization.DateTimeFormatInfo> オブジェクトです。このオブジェクトは、現在のスレッド カルチャによって暗黙的に指定されるか、または解析するメソッドの <xref:System.IFormatProvider> パラメーターによって明示的に指定されます。 <xref:System.IFormatProvider> パラメーターには、カルチャを表す <xref:System.Globalization.CultureInfo> オブジェクト、または <xref:System.Globalization.DateTimeFormatInfo> オブジェクトを指定します。  
  
 解析される日付の文字列形式には、月と、少なくとも日付または年を含める必要があります。 時刻の文字列形式は、時間と、少なくとも分または AM/PM 指定子を含める必要があります。 ただし、可能な場合は、解析により省略されたコンポーネントに既定値が指定されます。 欠落している日付には現在の日付が規定で設定され、欠落している年には現在の年が規定で設定され、欠落している月の日付には月の最初の日が規定で設定され、欠落している時刻には午前 0 時が規定で設定されます。  
  
 文字列形式で時刻のみを指定する場合、解析は、<xref:System.DateTime.Today%2A> プロパティの対応する値に、その <xref:System.DateTime.Year%2A>、<xref:System.DateTime.Month%2A>、<xref:System.DateTime.Day%2A> プロパティを設定した <xref:System.DateTime> オブジェクトを返します。 ただし、<xref:System.Globalization.DateTimeStyles.NoCurrentDateDefault> 定数が解析メソッドで指定されている場合、結果の年、月、日付のプロパティの値は `1` に設定されます。  
  
 日付と時刻のコンポーネントだけでなく、日付と時刻の文字列形式には、世界協定時刻 (UTC) と何時間異なるかを示すオフセットを含めることができます。 たとえば、文字列 "2/14/2007 5:32:00 -7:00" は、UTC より 7 時間早い時刻を定義します。 オフセットが時刻の文字列形式から省略される場合、解析では、その <xref:System.DateTime.Kind%2A> プロパティに <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType> を設定して、<xref:System.DateTime> オブジェクトを返します。 オフセットが指定されている場合、解析では、その <xref:System.DateTime.Kind%2A> プロパティに <xref:System.DateTimeKind.Local> を設定した <xref:System.DateTime> オブジェクトと、使用しているマシンのローカル タイム ゾーンに調整された値を返します。 解析メソッドで <xref:System.Globalization.DateTimeStyles> 定数を使用して、この動作を変更できます。  
  
 書式プロバイダーは、あいまいな数値の日付を解釈するためにも使用されます。 たとえば、文字列 "02/03/04" で示された日付は、どのコンポーネントが月、日、年であるのかが明確ではありません。 この場合、コンポーネントは、書式プロバイダーの日付形式と同様の順序で解釈されます。  
  
## <a name="parse"></a>Parse  
 次のコード例では、文字列を **DateTime** に変換するために、**Parse** メソッドを使用する方法を示します。 この例では、現在のスレッドに関連付けられているカルチャを使用して、解析が実行されます。 現在のカルチャに関連付けられている <xref:System.Globalization.CultureInfo> で入力文字列を解析できない場合、<xref:System.FormatException> がスローされます。  
  
 [!code-csharp[Parsing.DateAndTime#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example.cs#1)]
 [!code-vb[Parsing.DateAndTime#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example.vb#1)]  
  
 また、そのオブジェクトで定義されているカルチャのいずれかに設定される **CultureInfo** を指定するか、または <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> プロパティによって返される標準の <xref:System.Globalization.DateTimeFormatInfo> オブジェクトのいずれかを指定することもできます。 次のコード例は、書式プロバイダーを使用して、ドイツ語の文字列を **DateTime** に解析します。 この特定の文字列を正常に解析できるように、de-DE カルチャを示す **CultureInfo** が定義され、解析されている文字列と共に渡されます。 これで、**CurrentThread** の **CurrentCulture** にある、あらゆる設定が排除されます。  
  
 [!code-csharp[Parsing.DateAndTime#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example2.cs#2)]
 [!code-vb[Parsing.DateAndTime#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example2.vb#2)]  
  
 ただし、<xref:System.DateTime.Parse%2A> メソッドのオーバーロードを使用して、カスタム書式プロバイダーを指定することができますが、このメソッドでは非標準の書式プロバイダーの使用をサポートしていません。 非標準の書式設定で示された日付と時刻を解析するには、代わりに <xref:System.DateTime.ParseExact%2A> メソッドを使用します。  
  
 次のコード例では、<xref:System.Globalization.DateTimeStyles> 列挙体を使用して、現在の日付と時刻の情報を、文字列で定義しないフィールドの **DateTime** に追加しないことを指定します。  
  
 [!code-csharp[Parsing.DateAndTime#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example3.cs#3)]
 [!code-vb[Parsing.DateAndTime#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example3.vb#3)]  
  
## <a name="parseexact"></a>ParseExact  
 <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> メソッドは、指定された文字列パターンに準拠する文字列を **DateTime** オブジェクトに変換します。 指定された形式ではない文字列がこのメソッドに渡された場合、<xref:System.FormatException> がスローされます。 標準の日付と時刻の書式指定子のいずれか、またはカスタムの日付と時刻の書式指定子の制限された組み合わせを指定することができます。 カスタムの書式指定子を使用すると、カスタムの認識文字列を構成することができます。 (指定子の詳細については、[標準の日付と時刻の書式指定文字列](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)と[カスタムの日付と時刻の書式指定文字列](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)に関するトピックをご覧ください)。  
  
 <xref:System.DateTime.ParseExact%2A> メソッドのオーバーロードごとに、通常は文字列の書式設定に関するカルチャ固有の情報を指定する <xref:System.IFormatProvider> パラメーターもあります。 通常、この <xref:System.IFormatProvider> オブジェクトは標準的なカルチャを表す <xref:System.Globalization.CultureInfo> オブジェクトか、<xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> プロパティによって返される <xref:System.Globalization.DateTimeFormatInfo> オブジェクトです。 ただし、その他の日付と時刻の解析関数とは異なり、このメソッドでは、非標準の日付と時刻の書式を定義する <xref:System.IFormatProvider> もサポートしています。  
  
 次のコード例では、**ParseExact** メソッドに解析する文字列オブジェクト、書式指定子、**CultureInfo** オブジェクトが順に渡されます。 この **ParseExact** メソッドでは、en-US カルチャで長い形式の日付パターンを示す文字列のみを解析できます。  
  
 [!code-csharp[Parsing.DateAndTime#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example4.cs#4)]
 [!code-vb[Parsing.DateAndTime#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example4.vb#4)]  
  
## <a name="see-also"></a>参照  
 [Parsing Strings](../../../docs/standard/base-types/parsing-strings.md)  
 [型の書式設定](../../../docs/standard/base-types/formatting-types.md)  
 [.NET での型変換](../../../docs/standard/base-types/type-conversion.md)
