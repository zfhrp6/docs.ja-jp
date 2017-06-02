---
title: ".NET Framework における数値文字列の解析 | Microsoft Docs"
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
  - "解析 (文字列を)、数値文字列"
  - "数値文字列"
  - "列挙体 [.NET Framework]、解析 (文字列を)"
  - "基本型、解析 (文字列を)"
ms.assetid: e39324ee-72e5-42d4-a80d-bf3ee7fc6c59
caps.latest.revision: 20
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 20
---
# .NET Framework における数値文字列の解析
すべての数値型には、その数値の文字列形式を数値型に変換するための静的な解析メソッドとして、`Parse` および `TryParse` という 2 つのメソッドがあります。  これらのメソッドを使用すると、「[標準の数値書式指定文字列](../../../docs/standard/base-types/standard-numeric-format-strings.md)」および「[カスタム数値書式指定文字列](../../../docs/standard/base-types/custom-numeric-format-strings.md)」で説明する書式指定文字列を使用して作成した文字列を解析できます。  `Parse` メソッドと `TryParse` メソッドは、既定で、整数部のみを含む文字列を整数値に正しく変換できます。  また、整数部と小数部、桁区切り記号、および小数点記号を含む文字列を浮動小数点値に正しく変換できます。  操作が失敗すると、`Parse` メソッドからは例外がスローされ、`TryParse` メソッドからは `false` が返されます。  
  
## 解析と書式プロバイダー  
 通常、数値の文字列形式はカルチャごとに異なります。  通貨記号、桁区切り記号、および小数点記号すべてなどの数値文字列の要素はカルチャによって異なります。  解析メソッドは、明示的または暗黙的に、それらのカルチャによる違いを認識する書式プロバイダーを使用します。  `Parse` メソッドまたは `TryParse` メソッドの呼び出しで書式プロバイダーが指定されていない場合は、現在のスレッドのカルチャ \(<xref:System.Globalization.NumberFormatInfo.CurrentInfo%2A?displayProperty=fullName> プロパティによって返される <xref:System.Globalization.NumberFormatInfo> オブジェクト\) に関連付けられている書式プロバイダーが使用されます。  
  
 書式プロバイダーは <xref:System.IFormatProvider> の実装で表されます。  このインターフェイスには、<xref:System.IFormatProvider.GetFormat%2A> メソッドという単一のメンバーがあります。このメソッドの単一のパラメーターは、書式を指定する型を表す <xref:System.Type> オブジェクトです。  このメソッドが、書式情報を提供するオブジェクトを返します。  .NET Framework では、数値文字列を解析するために、次の 2 つの <xref:System.IFormatProvider> の実装がサポートされています。  
  
-   <xref:System.Globalization.CultureInfo> オブジェクト。このオブジェクトの <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=fullName> メソッドは、カルチャ固有の書式情報を提供する <xref:System.Globalization.NumberFormatInfo> オブジェクトを返します。  
  
-   <xref:System.Globalization.NumberFormatInfo> オブジェクト。このオブジェクトの <xref:System.Globalization.NumberFormatInfo.GetFormat%2A?displayProperty=fullName> メソッドは、このオブジェクト自体を返します。  
  
 次の例では、配列の各文字列を <xref:System.Double> 値に変換しようとしています。  まず、英語 \(米国\) カルチャの規則を反映する書式プロバイダーを使用して文字列の解析を試みます。  この操作で <xref:System.FormatException> がスローされると、フランス語 \(フランス\) カルチャの規則を反映する書式プロバイダーを使用して文字列の解析を試みます。  
  
 [!code-csharp[Parsing.Numbers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/formatproviders1.cs#1)]
 [!code-vb[Parsing.Numbers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/formatproviders1.vb#1)]  
  
## 解析と NumberStyles の値  
 解析操作で処理できるスタイル要素 \(空白文字、桁区切り記号、小数点記号など\) は、<xref:System.Globalization.NumberStyles> 列挙値で定義されます。  既定では、整数値を表す文字列は、<xref:System.Globalization.NumberStyles?displayProperty=fullName> 値を使用して解析されます。このスタイルでは、数字、先頭と末尾の空白文字、および先頭の符号だけを使用できます。  浮動小数点値を表す文字列は、<xref:System.Globalization.NumberStyles?displayProperty=fullName> 値と <xref:System.Globalization.NumberStyles?displayProperty=fullName> 値の組み合わせで解析されます。この複合スタイルでは、10 進数の数字に加え、先頭と末尾の空白文字、先頭の符号、小数点記号、桁区切り記号、および指数を使用できます。  <xref:System.Globalization.NumberStyles> 型のパラメーターを含む `Parse` メソッドまたは `TryParse` メソッドのオーバーロードを呼び出し、<xref:System.Globalization.NumberStyles> フラグを 1 つ以上設定することで、解析操作を成功させるために文字列で使用できるスタイル要素を制御することができます。  
  
 たとえば、桁区切り記号を含む文字列を <xref:System.Int32> 値に <xref:System.Int32.Parse%28System.String%29?displayProperty=fullName> のメソッドを使用して変換できません。  ただし、次の例に示すよう <xref:System.Globalization.NumberStyles?displayProperty=fullName> フラグを使用すると、呼び出しが成功します。  
  
 [!code-csharp[Parsing.Numbers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/styles1.cs#2)]
 [!code-vb[Parsing.Numbers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/styles1.vb#2)]  
  
> [!WARNING]
>  解析操作では、常に特定のカルチャの書式指定規則が使用されます。  <xref:System.Globalization.CultureInfo> オブジェクトまたは <xref:System.Globalization.NumberFormatInfo> オブジェクトを渡すことによってカルチャを指定していない場合は、現在のスレッドに関連付けられているカルチャが使用されます。  
  
 次の表に、<xref:System.Globalization.NumberStyles> 列挙体のメンバーと、それらによる解析操作への影響を示します。  
  
|NumberStyles の値|解析対象の文字列に対する影響|  
|---------------------|--------------------|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|数字だけを使用できます。|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|小数点記号と小数を使用できます。  整数値については、小数部の数値として 0 だけを使用できます。  有効な小数点記号は、<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A?displayProperty=fullName> プロパティまたは <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A?displayProperty=fullName> プロパティによって決まります。|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|"e" または "E" という文字を使用して指数表記を示すことができます。  詳細については、「<xref:System.Globalization.NumberStyles>」を参照してください。|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|先頭の空白文字を使用できます。|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|末尾の空白文字を使用できます。|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|数字の前に正または負の符号を使用できます。|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|数字の後に正または負の符号を使用できます。|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|かっこを使用して負の値を示すことができます。|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|桁区切り記号を使用できます。  桁区切り記号文字は、<xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A?displayProperty=fullName> プロパティまたは <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A?displayProperty=fullName> プロパティによって決まります。|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|通貨記号を使用できます。  通貨記号は <xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A?displayProperty=fullName> プロパティで定義されます。|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|解析対象の文字列が 16 進数と解釈されます。  16 進数の数字を表す 0 ～ 9、A ～ F、および a ～ f を使用できます。  このフラグは、整数値の解析でのみ使用できます。|  
  
 さらに、<xref:System.Globalization.NumberStyles> 列挙体には、複数の <xref:System.Globalization.NumberStyles> フラグで構成される次の複合スタイルも用意されています。  
  
|NumberStyles の複合値|含まれるメンバー|  
|-----------------------|--------------|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|<xref:System.Globalization.NumberStyles?displayProperty=fullName>、<xref:System.Globalization.NumberStyles?displayProperty=fullName>、および <xref:System.Globalization.NumberStyles?displayProperty=fullName> の各スタイルが含まれます。  整数値の解析には、既定ではこのスタイルが使用されます。|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|<xref:System.Globalization.NumberStyles?displayProperty=fullName>、<xref:System.Globalization.NumberStyles?displayProperty=fullName>、<xref:System.Globalization.NumberStyles?displayProperty=fullName>、<xref:System.Globalization.NumberStyles?displayProperty=fullName>、<xref:System.Globalization.NumberStyles?displayProperty=fullName>、および <xref:System.Globalization.NumberStyles?displayProperty=fullName> の各スタイルが含まれます。|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|<xref:System.Globalization.NumberStyles?displayProperty=fullName>、<xref:System.Globalization.NumberStyles?displayProperty=fullName>、<xref:System.Globalization.NumberStyles?displayProperty=fullName>、<xref:System.Globalization.NumberStyles?displayProperty=fullName>、および <xref:System.Globalization.NumberStyles?displayProperty=fullName> の各スタイルが含まれます。|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|<xref:System.Globalization.NumberStyles?displayProperty=fullName> と <xref:System.Globalization.NumberStyles?displayProperty=fullName> を除くすべてのスタイルが含まれます。|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|<xref:System.Globalization.NumberStyles?displayProperty=fullName> を除くすべてのスタイルが含まれます。|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|<xref:System.Globalization.NumberStyles?displayProperty=fullName>、<xref:System.Globalization.NumberStyles?displayProperty=fullName>、および <xref:System.Globalization.NumberStyles?displayProperty=fullName> の各スタイルが含まれます。|  
  
## 解析と Unicode の数字  
 Unicode 規格では、さまざまな書記体系での数字に対応するコード ポイントが定義されています。  たとえば、U\+0030 ~ U\+0039 のコード ポイントは基本ラテン数字の 0 ~ 9 を表し、U\+09E6 ~ U\+09EF のコード ポイントは Bangla の数字 0 ~ 9 を表し、U\+FF10 から U\+FF19 のコード ポイントはフル幅の数字 0 ~ 9.を表します。  ただし、解析メソッドで認識される数字は、コード ポイントが U\+0030 ～ U\+0039 の基本ラテン数字の 0 ～ 9 だけです。  それ以外の数字を含む文字列を数値解析メソッドに渡した場合、メソッドから <xref:System.FormatException> がスローされます。  
  
 <xref:System.Int32.Parse%2A?displayProperty=fullName> メソッドを使用して、複数の書記体系の数字で構成された文字列を解析する例を次に示します。  この例の出力結果が示すように、基本ラテン数字の解析は成功しますが、フル幅、アラブインド言語と Bangla 数字の解析は失敗します。  
  
 [!code-csharp[Parsing.Numbers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/unicode1.cs#3)]
 [!code-vb[Parsing.Numbers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/unicode1.vb#3)]  
  
## 参照  
 <xref:System.Globalization.NumberStyles>   
 [文字列の解析](../../../docs/standard/base-types/parsing-strings.md)   
 [型の書式設定](../../../docs/standard/base-types/formatting-types.md)