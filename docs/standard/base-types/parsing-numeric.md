---
title: ".NET の数値文字列の解析"
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
- parsing strings, numeric strings
- numeric strings
- enumerations [.NET Framework], parsing strings
- base types, parsing strings
ms.assetid: e39324ee-72e5-42d4-a80d-bf3ee7fc6c59
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3c9bb58b0d7b45ca197653742844be01ac3bbe41
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="parsing-numeric-strings-in-net"></a>NET における数値文字列の解析
すべての数値型には、2 つの静的解析メソッド (`Parse` と `TryParse`) があり、数字の文字列形式を数値型に変換するために使用できます。 これらのメソッドでは、[標準の数値書式指定文字列](../../../docs/standard/base-types/standard-numeric-format-strings.md)と[カスタム数値書式指定文字列](../../../docs/standard/base-types/custom-numeric-format-strings.md)で記述されている書式指定文字列を使用して、生成された文字列を解析できます。 既定では、`Parse` と `TryParse` メソッドは、10 進数の整数を含む文字列を整数値のみに正常に変換することができます。 これらのメソッドは、整数部と小数部、グループ区切り、および小数点記号を含む文字列を浮動小数点値に正常に変換できます。 `TryParse` メソッドが `false` を返すのに対して、`Parse` メソッドは操作が失敗した場合に例外をスローします。  
  
## <a name="parsing-and-format-providers"></a>解析と書式プロバイダー  
 通常、数値の文字列形式はカルチャによって異なります。 通貨記号、グループ (または千単位) 区切り、および小数点記号などの数値文字列の要素は、カルチャによって大きく異なります。 暗黙的または明示的のいずれかの解析メソッドでは、これらのカルチャ固有のバリエーションを認識する書式プロバイダーを使用します。 呼び出しに書式設定プロバイダーが指定されていないかどうか、`Parse`または`TryParse`メソッドは、現在のスレッド カルチャに関連付けられている書式プロバイダー (、<xref:System.Globalization.NumberFormatInfo>によって返されるオブジェクト、<xref:System.Globalization.NumberFormatInfo.CurrentInfo%2A?displayProperty=nameWithType>プロパティ) を使用します。  
  
 書式設定プロバイダーがによって表される、<xref:System.IFormatProvider>実装します。 このインターフェイスが 1 つのメンバーには、<xref:System.IFormatProvider.GetFormat%2A>単一パラメーターを持つが、メソッド、<xref:System.Type>書式設定する型を表すオブジェクト。 このメソッドは、書式情報を示すオブジェクトを返します。 .NET には、次の 2 つがサポートしている<xref:System.IFormatProvider>数値文字列を解析するための実装。  
  
-   A<xref:System.Globalization.CultureInfo>オブジェクト<xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType>メソッドを返します、<xref:System.Globalization.NumberFormatInfo>カルチャに固有の書式情報を提供するオブジェクト。  
  
-   A<xref:System.Globalization.NumberFormatInfo>オブジェクト<xref:System.Globalization.NumberFormatInfo.GetFormat%2A?displayProperty=nameWithType>メソッドでは、それ自体を返します。  
  
 次の例の配列内の各文字列に変換しようとする、<xref:System.Double>値。 最初に、英語 (米国) カルチャの規則を反映する書式プロバイダーを使用して、文字列を解析しようとします。 この操作をスローした場合、 <xref:System.FormatException>、フランス語 (フランス) カルチャの規則を反映する書式プロバイダーを使用して文字列を解析しようとします。  
  
 [!code-csharp[Parsing.Numbers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/formatproviders1.cs#1)]
 [!code-vb[Parsing.Numbers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/formatproviders1.vb#1)]  
  
## <a name="parsing-and-numberstyles-values"></a>解析と NumberStyles 値  
 解析操作を処理できるスタイル要素 (空白、桁区切り記号、桁区切り記号など) が定義されている、<xref:System.Globalization.NumberStyles>列挙値。 既定では、整数値を表す文字列を解析してを使用して、<xref:System.Globalization.NumberStyles.Integer?displayProperty=nameWithType>値、数字、先頭および末尾の空白文字、および先頭の符号を可能にします。 浮動小数点値を表す文字列を解析の組み合わせを使用して、<xref:System.Globalization.NumberStyles.Float?displayProperty=nameWithType>と<xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType>値ですこの複合スタイルでは小数点以下桁数先頭と末尾の空白文字、先頭の符号、小数点区切り文字、グループと共に。区切り記号、および指数部です。 オーバー ロードを呼び出すことによって、`Parse`または`TryParse`型のパラメーターを含むメソッド<xref:System.Globalization.NumberStyles>と 1 つまたは複数設定<xref:System.Globalization.NumberStyles>フラグ、解析操作するため、文字列内に存在できるスタイル要素を制御することができます成功します。  
  
 桁区切り記号を表す文字列を変換できないなど、<xref:System.Int32>値を使用して、<xref:System.Int32.Parse%28System.String%29?displayProperty=nameWithType>メソッドです。 ただし、変換に使用する場合が成功すると、<xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType>フラグ、次の例に示すようにします。  
  
 [!code-csharp[Parsing.Numbers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/styles1.cs#2)]
 [!code-vb[Parsing.Numbers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/styles1.vb#2)]  
  
> [!WARNING]
>  解析操作は、常に特定のカルチャの書式規則を使用します。 渡すことによって、カルチャを指定しない場合、<xref:System.Globalization.CultureInfo>または<xref:System.Globalization.NumberFormatInfo>オブジェクトの現在のスレッドに関連付けられているカルチャが使用されます。  
  
 次の表のメンバー、<xref:System.Globalization.NumberStyles>列挙型、解析処理に与える影響について説明します。  
  
|NumberStyles 値|解析する文字列への影響|  
|------------------------|---------------------------------------|  
|<xref:System.Globalization.NumberStyles.None?displayProperty=nameWithType>|数字のみが許可されます。|  
|<xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>|小数点の記号と桁数が許可されます。 整数値の場合、0 のみが小数点の桁数として許可されます。 有効な 10 進区切り記号はによって決定されます、<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A?displayProperty=nameWithType>または<xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A?displayProperty=nameWithType>プロパティです。|  
|<xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType>|"e" または "E" の文字は、指数表記を示すために使用できます。 参照してください<xref:System.Globalization.NumberStyles>の詳細。|  
|<xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>|先頭の空白が許可されます。|  
|<xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>|末尾の空白が許可されます。|  
|<xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>|正または負の符号には、数字の先頭に追加できます。|  
|<xref:System.Globalization.NumberStyles.AllowTrailingSign?displayProperty=nameWithType>|正または負の符号は、数字の後に続けることができます。|  
|<xref:System.Globalization.NumberStyles.AllowParentheses?displayProperty=nameWithType>|かっこは、負の符号を示すために使用できます。|  
|<xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType>|グループ区切りが許可されます。 桁区切り記号の文字はによって決まります、<xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A?displayProperty=nameWithType>または<xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A?displayProperty=nameWithType>プロパティです。|  
|<xref:System.Globalization.NumberStyles.AllowCurrencySymbol?displayProperty=nameWithType>|通貨記号が許可されます。 通貨記号がによって定義された、<xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A?displayProperty=nameWithType>プロパティです。|  
|<xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>|解析する文字列は、16 進数として解釈されます。 これには、16 進数の値の 0 ～ 9、A ～ F、a ～ f を含めることができます。 このフラグは、整数値を解析するためにだけに使用できます。|  
  
 さらに、<xref:System.Globalization.NumberStyles>列挙型が複数を含む次の複合スタイルを示します。<xref:System.Globalization.NumberStyles>フラグ。  
  
|複合 NumberStyles 値|数値を含む|  
|----------------------------------|----------------------|  
|<xref:System.Globalization.NumberStyles.Integer?displayProperty=nameWithType>|含まれています、 <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>、 <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>、および<xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>スタイル。 これは、整数値を解析するために使用される既定のスタイルです。|  
|<xref:System.Globalization.NumberStyles.Number?displayProperty=nameWithType>|含まれています、 <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>、 <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>、 <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>、 <xref:System.Globalization.NumberStyles.AllowTrailingSign?displayProperty=nameWithType>、 <xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>、および<xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType>スタイル。|  
|<xref:System.Globalization.NumberStyles.Float?displayProperty=nameWithType>|含まれています、 <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>、 <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>、 <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>、 <xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>、および<xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType>スタイル。|  
|<xref:System.Globalization.NumberStyles.Currency?displayProperty=nameWithType>|除くすべてのスタイルが含まれています<xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType>と<xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>です。|  
|<xref:System.Globalization.NumberStyles.Any?displayProperty=nameWithType>|除くすべてのスタイルが含まれています<xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>です。|  
|<xref:System.Globalization.NumberStyles.HexNumber?displayProperty=nameWithType>|含まれています、 <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>、 <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>、および<xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>スタイル。|  
  
## <a name="parsing-and-unicode-digits"></a>解析と Unicode 数字  
 Unicode 標準では、さまざまな書記体系で数字のコード ポイントを定義します。 たとえば、U+0030 ～ U+0039 のコード ポイントは、0 ～ 9 の基本ラテンの数字を示し、U+09E6 ～ U+09EF のコード ポイントは、0 ～ 9 の数字のバングラ語の数字を示し、U+FF10 ～ U+FF19 のコード ポイントは、0 ～ 9 の全角の数字を示します。 ただし、解析メソッドで認識される数字は、U+0030 ～ U+0039 のコード ポイントの基本ラテンの数字 0 ～ 9 のみです。 [解析方法] の数値の文字列が渡された場合、その他の数字を格納している、メソッドをスロー、<xref:System.FormatException>です。  
  
 次の例では、<xref:System.Int32.Parse%2A?displayProperty=nameWithType>書記体系が異なるの桁の数字で構成される文字列を解析します。 例の出力に示されているように、基本ラテンの数字を解析する試行は成功しますが、全角、アラビア インド、バングラ語の数字を解析する試行は失敗します。  
  
 [!code-csharp[Parsing.Numbers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/unicode1.cs#3)]
 [!code-vb[Parsing.Numbers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/unicode1.vb#3)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Globalization.NumberStyles>  
 [文字列の解析](../../../docs/standard/base-types/parsing-strings.md)  
 [型の書式設定](../../../docs/standard/base-types/formatting-types.md)
