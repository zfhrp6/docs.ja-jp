---
title: "方法 : カスタム数値書式プロバイダーを定義して使用する | Microsoft Docs"
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
  - "カスタム書式指定文字列"
  - "カスタム数値書式指定文字列"
  - "表示 (日付と時刻のデータを)"
  - "書式プロバイダー [.NET Framework]"
  - "書式指定 [.NET Framework], 数"
  - "数値の書式指定 [.NET Framework]"
  - "数値 [.NET Framework], カスタム数値書式指定文字列"
  - "数値書式指定文字列 [.NET Framework]"
ms.assetid: a281bfbf-6596-45ed-a2d6-3782d535ada2
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : カスタム数値書式プロバイダーを定義して使用する
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] では、数値の文字列表現を広範に制御することができます。  数値の書式をカスタマイズするための、次のような機能がサポートされています。  
  
-   標準の数値書式指定文字列。これは、数値を文字列形式に変換するための定義済み形式のセットです。  `format` パラメーターを持つ、<xref:System.Decimal.ToString%28System.String%29?displayProperty=fullName> などの任意の数値書式指定メソッドでこれらを使用できます。  詳細については、「[標準の数値書式指定文字列](../../../docs/standard/base-types/standard-numeric-format-strings.md)」を参照してください。  
  
-   カスタム数値書式指定文字列。これはシンボルのセットで、これらのシンボルを組み合わせてカスタム数値書式指定子を定義できます。  これらもまた、<xref:System.Decimal.ToString%28System.String%29?displayProperty=fullName> などの、`format` パラメーターを持つ任意の数値書式指定メソッドで使用できます。  詳細については、「[カスタム数値書式指定文字列](../../../docs/standard/base-types/custom-numeric-format-strings.md)」を参照してください。  
  
-   カスタム <xref:System.Globalization.CultureInfo> または <xref:System.Globalization.NumberFormatInfo> オブジェクト。これらは、数値の文字列表現の表示で使用されるシンボルと書式パターンを定義します。  `provider` パラメーターを持つ、<xref:System.Int32.ToString%2A> などの任意の数値書式指定メソッドでこれらを使用できます。  通常は、カルチャ固有の書式設定を指定するために `provider` パラメーターを使用します。  
  
 これら 3 つの技法が不適切な場合もあります。書式設定されたアカウント番号、識別番号、または郵便番号をアプリケーションで表示する必要がある場合などです。  [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] では、数値の書式を決定するために、<xref:System.Globalization.CultureInfo> オブジェクトでも <xref:System.Globalization.NumberFormatInfo> オブジェクトでもない書式設定オブジェクトを定義することもできます。  ここでは、そのようなオブジェクトの実装方法を手順を追って説明し、電話番号の書式を設定する例を示します。  
  
### カスタム書式プロバイダーを定義するには  
  
1.  <xref:System.IFormatProvider> インターフェイスと <xref:System.ICustomFormatter> インターフェイスを実装するクラスを定義します。  
  
2.  <xref:System.IFormatProvider.GetFormat%2A?displayProperty=fullName> メソッドを実装します。  <xref:System.IFormatProvider.GetFormat%2A> はコールバック メソッドで、カスタム書式指定を実際に行うオブジェクトを取得するために \([String.Format\(IFormatProvider, String, Object\<xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=fullName> メソッドなどの\) 書式指定メソッドによって呼び出されます。  通常、<xref:System.IFormatProvider.GetFormat%2A> の実装は次のような操作を実行します。  
  
    1.  メソッド パラメーターとして渡される <xref:System.Type> オブジェクトが <xref:System.ICustomFormatter> インターフェイスを表すかどうかを判断します。  
  
    2.  パラメーターが <xref:System.ICustomFormatter> インターフェイスを表す場合、<xref:System.IFormatProvider.GetFormat%2A> は、カスタム書式指定を行う <xref:System.ICustomFormatter> インターフェイスを実装するオブジェクトを返します。  通常は、カスタム書式指定オブジェクト自身が返されます。  
  
    3.  パラメーターが <xref:System.ICustomFormatter> インターフェイスを表さない場合、<xref:System.IFormatProvider.GetFormat%2A> は `null` を返します。  
  
3.  <xref:System.ICustomFormatter.Format%2A> メソッドを実装します。  このメソッドは [String.Format\(IFormatProvider, String, Object\<xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=fullName> メソッドによって呼び出され、数値の文字列表現を返します。  このメソッドを実装する場合には、通常、次のような操作を行う必要があります。  
  
    1.  必要に応じて、`provider` パラメーターを検査することにより、このメソッドが適切な書式設定サービスを提供することを確認します。  <xref:System.IFormatProvider> と <xref:System.ICustomFormatter> の両方を実装する書式設定オブジェクトの場合、現在の書式設定オブジェクトと等しいかどうか `provider` パラメーターを検査する必要があります。  
  
    2.  書式設定オブジェクトがカスタム書式指定子をサポートするかどうかを判断します。\(たとえば、「N」書式指定子は ITU\-T の推奨 E.123 形式で出力を示す場合があります。"」米国の電話番号が NANP 形式で「出力する必要があることを示すことがあります。\) 書式指定子が使用される場合、メソッドで特定の書式指定子を処理する必要があります。  これは `format` パラメーターでメソッドに渡されます。  指定子が存在しない場合、`format` パラメーターの値は <xref:System.String.Empty?displayProperty=fullName> です。  
  
    3.  `arg` パラメーターとしてメソッドに渡される数値を取得します。  それを文字列形式に変換するために必要な操作をすべて実行します。  
  
    4.  `arg` パラメーターの文字列表現を返します。  
  
### カスタム数値書式設定オブジェクトを使用するには  
  
1.  カスタム書式設定クラスの新しいインスタンスを作成します。  
  
2.  書式指定メソッド [String.Format\(IFormatProvider, String, Object\<xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=fullName> を呼び出します。その際、カスタム書式設定オブジェクト、書式指定子 \(使用しない場合は <xref:System.String.Empty?displayProperty=fullName>\)、および書式設定の対象となる数値を渡します。  
  
## 使用例  
 次の例では `TelephoneFormatter` という NANP または E.123 形式に米国の電話番号を表す数値を変換するカスタム数値書式のプロバイダーを定義します。  このメソッドは、"N" \(NANP 形式を出力\) および "I" \(国際 E.123 形式を出力\) の 2 つの書式指定子を処理します。  
  
 [!code-csharp[Formatting.HowTo.NumericValue#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#1)]
 [!code-vb[Formatting.HowTo.NumericValue#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#1)]  
  
 このカスタム数値書式プロバイダーは、[String.Format\(IFormatProvider, String, Object\<xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=fullName> メソッドでのみ使用可能です。  <xref:System.IFormatProvider> 型のパラメーターを持つ数値書式指定メソッドの他のすべてのオーバーロード \(たとえば `ToString`\) は、<xref:System.Globalization.NumberFormatInfo> 型を表す <xref:System.Type> オブジェクトを <xref:System.IFormatProvider.GetFormat%2A?displayProperty=fullName> 実装に渡します。  これらは、メソッドから <xref:System.Globalization.NumberFormatInfo> オブジェクトが返されることを期待します。  これが返されない場合、カスタム数値書式プロバイダーは無視され、現在のカルチャの <xref:System.Globalization.NumberFormatInfo> オブジェクトが代わりに使用されます。  この例の `TelephoneFormatter.GetFormat` メソッドは、数値書式指定メソッドに渡されるものが適切でない場合に備えて、メソッド パラメーターを検査し、それが <xref:System.ICustomFormatter> 以外の型を表す場合には `null` を返します。  
  
 カスタム数値書式プロバイダーで書式指定子のセットをサポートする場合には、[String.Format\(IFormatProvider, String, Object\<xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=fullName> メソッド呼び出しの書式指定項目に書式指定子が含まれない場合の既定の動作を必ず実装してください。  この例では、"N" が既定の書式指定子です。  こうして書式指定子を明示的に指定することで、数値を書式設定された電話番号に変換できます。  次の例は、このようなメソッド呼び出しを示しています。  
  
 [!code-csharp[Formatting.HowTo.NumericValue#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#2)]
 [!code-vb[Formatting.HowTo.NumericValue#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#2)]  
  
 加えて、書式指定子が存在しない場合にも変換が可能です。  次の例は、このようなメソッド呼び出しを示しています。  
  
 [!code-csharp[Formatting.HowTo.NumericValue#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#3)]
 [!code-vb[Formatting.HowTo.NumericValue#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#3)]  
  
 既定の書式指定子が定義されない場合、コードがサポートしない書式設定を .NET Framework で提供できるように、<xref:System.ICustomFormatter.Format%2A?displayProperty=fullName> メソッドの実装に次のようなコードを含める必要があります。  
  
 [!code-csharp[System.ICustomFormatter.Format#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.ICustomFormatter.Format/cs/format.cs#1)]
 [!code-vb[System.ICustomFormatter.Format#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.ICustomFormatter.Format/vb/Format.vb#1)]  
  
 この例では、<xref:System.ICustomFormatter.Format%2A?displayProperty=fullName> を実装するメソッドが [String.Format\(IFormatProvider, String, Object\<xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=fullName> メソッドのコールバック メソッドとして機能するようになっています。  このため、このメソッドは `formatProvider` パラメーターを検査して、現在の `TelephoneFormatter` オブジェクトへの参照が含まれるかどうかを判別します。  また、コードからこのメソッドを直接呼び出すこともできます。  その場合には、カルチャ固有の書式設定情報を指定する <xref:System.Globalization.CultureInfo> オブジェクトまたは <xref:System.Globalization.NumberFormatInfo> オブジェクトを提供するために `formatProvider` パラメーターを使用できます。  
  
## コードのコンパイル  
 コマンド ラインで csc.exe または vb.exe を使用してコードをコンパイルします。  [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] でコードをコンパイルするには、コンソール アプリケーション プロジェクト テンプレートの中にコードを配置します。  
  
## 参照  
 [書式設定操作の実行](../../../docs/standard/base-types/performing-formatting-operations.md)