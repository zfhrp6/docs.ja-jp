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
caps.latest.revision: "24"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1beceb2b2d32c500e73cd7786c480fcd84c3001c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="parsing-date-and-time-strings-in-net"></a>日付と時刻の文字列を .NET での解析
解析メソッドを等価の日付と時刻の文字列形式の変換<xref:System.DateTime>オブジェクト。 <xref:System.DateTime.Parse%2A>と<xref:System.DateTime.TryParse%2A>メソッドは、日付と時刻のいくつかの一般的な形式のいずれかを変換します。 <xref:System.DateTime.ParseExact%2A>と<xref:System.DateTime.TryParseExact%2A>メソッドは、日付と時刻の書式指定文字列で指定されたパターンに準拠した文字列形式を変換します。 ([標準の日付と時刻の書式指定文字列](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)と[カスタムの日付と時刻の書式指定文字列](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)に関するトピックをご覧ください)。  
  
 解析は、日付と時刻の区切り記号、および月、日、および年号の名前に使用される文字列などの情報を提供する書式プロバイダーのプロパティの影響を受けます。 書式設定プロバイダーが現在<xref:System.Globalization.DateTimeFormatInfo>またはによって明示的に現在のスレッド カルチャによって暗黙的に提供されているオブジェクト、<xref:System.IFormatProvider>解析メソッドのパラメーターです。 <xref:System.IFormatProvider>パラメーターを指定、<xref:System.Globalization.CultureInfo>カルチャを表す、オブジェクトまたは<xref:System.Globalization.DateTimeFormatInfo>オブジェクト。  
  
 解析される日付の文字列形式には、月と、少なくとも日付または年を含める必要があります。 時刻の文字列形式は、時間と、少なくとも分または AM/PM 指定子を含める必要があります。 ただし、可能な場合は、解析により省略されたコンポーネントに既定値が指定されます。 欠落している日付には現在の日付が規定で設定され、欠落している年には現在の年が規定で設定され、欠落している月の日付には月の最初の日が規定で設定され、欠落している時刻には午前 0 時が規定で設定されます。  
  
 文字列形式を時刻のみを指定する場合の解析を返します、<xref:System.DateTime>オブジェクトをその<xref:System.DateTime.Year%2A>、 <xref:System.DateTime.Month%2A>、および<xref:System.DateTime.Day%2A>の対応する値に設定されたプロパティ、<xref:System.DateTime.Today%2A>プロパティです。 ただし場合、<xref:System.Globalization.DateTimeStyles.NoCurrentDateDefault>解析方法、結果の年、月、定数が指定されており、1 日プロパティの値に設定されます`1`です。  
  
 日付と時刻のコンポーネントだけでなく、日付と時刻の文字列形式には、世界協定時刻 (UTC) と何時間異なるかを示すオフセットを含めることができます。 たとえば、文字列 "2/14/2007 5:32:00 -7:00" は、UTC より 7 時間早い時刻を定義します。 時刻の文字列表現からのオフセットを省略すると、解析、<xref:System.DateTime>オブジェクトをその<xref:System.DateTime.Kind%2A>プロパティに設定<xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>です。 場合のオフセットを指定すると、解析、<xref:System.DateTime>オブジェクトをその<xref:System.DateTime.Kind%2A>プロパティに設定<xref:System.DateTimeKind.Local>し、その値は、コンピューターのローカル タイム ゾーンに調整します。 使用してこの動作を変更することができます、<xref:System.Globalization.DateTimeStyles>解析メソッドを使用して定数。  
  
 書式プロバイダーは、あいまいな数値の日付を解釈するためにも使用されます。 たとえば、文字列 "02/03/04" で示された日付は、どのコンポーネントが月、日、年であるのかが明確ではありません。 この場合、コンポーネントは、書式プロバイダーの日付形式と同様の順序で解釈されます。  
  
## <a name="parse"></a>Parse  
 次のコード例の使用を示しています、**解析**に文字列に変換するメソッド、 **DateTime**です。 この例では、現在のスレッドに関連付けられているカルチャを使用して、解析が実行されます。 場合、<xref:System.Globalization.CultureInfo>に現在関連付けられているカルチャは、入力文字列を解析できません、<xref:System.FormatException>がスローされます。  
  
 [!code-csharp[Parsing.DateAndTime#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example.cs#1)]
 [!code-vb[Parsing.DateAndTime#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example.vb#1)]  
  
 指定することも、 **CultureInfo** 、そのオブジェクトで定義されているカルチャのいずれかに設定または標準のいずれかを指定できます<xref:System.Globalization.DateTimeFormatInfo>によって返されるオブジェクト、<xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType>プロパティです。 次のコード例にドイツ語の文字列を解析する書式設定プロバイダーを使用して、 **DateTime**です。 A **CultureInfo** DE-DE カルチャを表す定義は、この特定の文字列の解析を成功したことを確認する解析される文字列で渡されます。 そのため、すべての設定は、 **CurrentCulture**の**呼び出せるようになって**です。  
  
 [!code-csharp[Parsing.DateAndTime#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example2.cs#2)]
 [!code-vb[Parsing.DateAndTime#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example2.vb#2)]  
  
 ただしのオーバー ロードを使用できますが、<xref:System.DateTime.Parse%2A>カスタム書式プロバイダーを指定するメソッド、メソッドは非標準の書式プロバイダーの使用をサポートしていません。 日付と時刻の標準形式で表現を解析するを使用して、<xref:System.DateTime.ParseExact%2A>メソッド代わりにします。  
  
 次のコード例では、<xref:System.Globalization.DateTimeStyles>に現在の日付と時刻の情報を追加されないことを指定する列挙体、 **DateTime**の文字列が定義されていないフィールドです。  
  
 [!code-csharp[Parsing.DateAndTime#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example3.cs#3)]
 [!code-vb[Parsing.DateAndTime#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example3.vb#3)]  
  
## <a name="parseexact"></a>ParseExact  
 <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>メソッドに指定した文字列のパターンに準拠している文字列を変換する、 **DateTime**オブジェクト。 このメソッドには、指定されたフォームのない文字列が渡されるときに、<xref:System.FormatException>がスローされます。 標準の日付と時刻の書式指定子のいずれか、またはカスタムの日付と時刻の書式指定子の制限された組み合わせを指定することができます。 カスタムの書式指定子を使用すると、カスタムの認識文字列を構成することができます。 (指定子の詳細については、[標準の日付と時刻の書式指定文字列](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)と[カスタムの日付と時刻の書式指定文字列](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)に関するトピックをご覧ください)。  
  
 各オーバー ロード、<xref:System.DateTime.ParseExact%2A>メソッドにもが、<xref:System.IFormatProvider>通常文字列の書式に関するカルチャ固有の情報を提供するパラメーターです。 通常、この<xref:System.IFormatProvider>オブジェクトが、<xref:System.Globalization.CultureInfo>標準カルチャを表すオブジェクト、または<xref:System.Globalization.DateTimeFormatInfo>によって返されるオブジェクト、<xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType>プロパティです。 ただしとは異なり、その他の日付と時刻の関数の解析中、このメソッドもサポート、<xref:System.IFormatProvider>非標準の日付と時刻の形式を定義します。  
  
 次のコード例では、 **ParseExact**メソッドに渡されます、文字列オブジェクトを解析するには、後に続く、書式指定子、 **CultureInfo**オブジェクト。 これは、 **ParseExact**メソッドは、EN-US カルチャで長い日付パターンを示す文字列を解析できるのみです。  
  
 [!code-csharp[Parsing.DateAndTime#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example4.cs#4)]
 [!code-vb[Parsing.DateAndTime#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example4.vb#4)]  
  
## <a name="see-also"></a>関連項目  
 [文字列の解析](../../../docs/standard/base-types/parsing-strings.md)  
 [型の書式設定](../../../docs/standard/base-types/formatting-types.md)  
 [.NET での型変換](../../../docs/standard/base-types/type-conversion.md)
