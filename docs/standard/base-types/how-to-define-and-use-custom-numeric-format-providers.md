---
title: "方法 : カスタム数値書式プロバイダーを定義して使用する"
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
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- number formatting [.NET Framework]
- custom numeric format strings
- numbers [.NET Framework], custom numeric format strings
- displaying date and time data
- format providers [.NET Framework]
- custom format strings
ms.assetid: a281bfbf-6596-45ed-a2d6-3782d535ada2
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0e44a909eb92f0d9dfa21980a918a2d370dcf427
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-define-and-use-custom-numeric-format-providers"></a>方法 : カスタム数値書式プロバイダーを定義して使用する
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]に制御する広範な数値の文字列形式。 数値の書式をカスタマイズするため、次の機能をサポートしています。  
  
-   標準の数値書式指定文字列: 数値をその文字列形式に変換するための定義済みの書式セットを提供します。 それらをなど、書式指定メソッド、任意の数値で使用できます<xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType>を持つ、`format`パラメーター。 詳細については、「[標準の数値書式指定文字列](../../../docs/standard/base-types/standard-numeric-format-strings.md)です。  
  
-   カスタム数値書式指定文字列: カスタム数値書式指定子を定義するために結合できる記号のセットを提供します。 などの書式設定メソッド、任意の数値で使用することもできます<xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType>を持つ、`format`パラメーター。 詳細については、「[カスタム数値書式指定文字列](../../../docs/standard/base-types/custom-numeric-format-strings.md)です。  
  
-   カスタム<xref:System.Globalization.CultureInfo>または<xref:System.Globalization.NumberFormatInfo>シンボルを定義し、数値の文字列形式を表示するために使用されるパターンの書式を設定するオブジェクト。 それらをなど、書式指定メソッド、任意の数値で使用できます<xref:System.Int32.ToString%2A>を持つ、`provider`パラメーター。 通常、`provider`パラメーターを使用して、カルチャ固有の書式設定を指定します。  
  
 一部の例には (アプリケーションで書式設定されたアカウント番号や ID 番号、郵便番号を表示する必要がある場合など)、これら 3 つの方法は適していません。 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]どちらである書式設定オブジェクトを定義することもできます、<xref:System.Globalization.CultureInfo>も<xref:System.Globalization.NumberFormatInfo>数値を書式設定する方法を決定するオブジェクト。 このトピックでは、このようなオブジェクトを実装するため、詳細な手順を説明し、電話番号の書式を設定する例について説明します。  
  
### <a name="to-define-a-custom-format-provider"></a>カスタム書式プロバイダーを定義するには  
  
1.  実装するクラスを定義、<xref:System.IFormatProvider>と<xref:System.ICustomFormatter>インターフェイスです。  
  
2.  <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> メソッドを実装します。 <xref:System.IFormatProvider.GetFormat%2A>コールバック メソッドを書式設定メソッド (など、<xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>メソッド) を実際にはカスタム書式設定を行うオブジェクトを取得するために呼び出します。 一般的な実装<xref:System.IFormatProvider.GetFormat%2A>は次の実行します。  
  
    1.  決定するかどうか、<xref:System.Type>オブジェクト メソッドとして渡されるパラメーターを表します、<xref:System.ICustomFormatter>インターフェイスです。  
  
    2.  パラメーターが表している場合、<xref:System.ICustomFormatter>インターフェイス、<xref:System.IFormatProvider.GetFormat%2A>を実装するオブジェクトを返します、<xref:System.ICustomFormatter>カスタム書式設定を提供するインターフェイスです。 通常、カスタム書式指定オブジェクトは、それ自体を返します。  
  
    3.  パラメーターを表していない場合、<xref:System.ICustomFormatter>インターフェイス、<xref:System.IFormatProvider.GetFormat%2A>返します`null`です。  
  
3.  <xref:System.ICustomFormatter.Format%2A> メソッドを実装します。 このメソッドは、<xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>メソッド、数値の文字列形式を返すことを行います。 メソッドの実装には通常、次の作業を行います。  
  
    1.  必要に応じて、メソッドが確認するには書式指定サービスを提供する正当なものであることを確認、`provider`パラメーター。 両方を実装するオブジェクトを書式設定の<xref:System.IFormatProvider>と<xref:System.ICustomFormatter>、テストが必要、`provider`現在の書式設定オブジェクトと等しいかどうかのパラメーターです。  
  
    2.  書式指定オブジェクトが、カスタム書式指定子をサポートするかどうかを決定します  (たとえば、"N" 書式指定子は、米国の電話番号を NANP 形式で出力することを示し、"I" はITU-T 推奨 E.123 形式での出力を示すことができます)。書式指定子を使用している場合、メソッドが特定の書式指定子を処理する必要があります。 内のメソッドに渡されます、`format`パラメーター。 指定子にも存在する場合の値、`format`パラメーターは<xref:System.String.Empty?displayProperty=nameWithType>します。  
  
    3.  としてメソッドに渡される数値の値を取得、`arg`パラメーター。 文字列形式に変換するために必要な操作を実行します。  
  
    4.  文字列表現を返します、`arg`パラメーター。  
  
### <a name="to-use-a-custom-numeric-formatting-object"></a>カスタム数値書式設定オブジェクトを使用するには  
  
1.  カスタム書式指定クラスの新しいインスタンスを作成します。  
  
2.  呼び出す、<xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>メソッドを書式設定、カスタム書式指定オブジェクトを書式指定子を渡すこと (または<xref:System.String.Empty?displayProperty=nameWithType>いずれかを使用しない場合、)、および書式設定する数値。  
  
## <a name="example"></a>例  
 次の例では、米国の電話番号を表す数値を NANP または E.123 形式に変換する、`TelephoneFormatter` という名前のカスタム数値書式プロバイダーを定義します。 このメソッドは、"N" (NANP 形式を出力) と "I" (国際 E.123 形式を出力) の 2 つの書式指定子を処理します。  
  
 [!code-csharp[Formatting.HowTo.NumericValue#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#1)]
 [!code-vb[Formatting.HowTo.NumericValue#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#1)]  
  
 カスタム数値書式プロバイダーでのみ使用することができます、<xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>メソッドです。 数値書式指定メソッドの他のオーバー ロード (など`ToString`) 型のパラメーターがある<xref:System.IFormatProvider>すべて合格、<xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType>実装、<xref:System.Type>を表すオブジェクト、<xref:System.Globalization.NumberFormatInfo>型です。 返すメソッドを代わりに、期待どおり、<xref:System.Globalization.NumberFormatInfo>オブジェクト。 そうでない場合は、カスタム数値書式プロバイダーは無視されます、および<xref:System.Globalization.NumberFormatInfo>オブジェクトの代わりに、現在のカルチャが使用されます。 例では、`TelephoneFormatter.GetFormat`メソッド型の数値書式指定メソッドのパラメーターを確認し、返すことでメソッドに不適切な渡すことのできる可能性は処理`null`以外の型を表す場合<xref:System.ICustomFormatter>です。  
  
 カスタム数値書式プロバイダーでは、書式指定子のセットをサポートする場合に使用される書式項目の書式指定子が指定されていない場合、既定の動作を指定することを確認、<xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>メソッドの呼び出しです。 例では、"N" が既定の書式指定子です。 これにより、明示的な書式指定子を提供することによって、数値を書式設定された電話番号に変換できます。 このようなメソッドの呼び出しの例を次に示します。  
  
 [!code-csharp[Formatting.HowTo.NumericValue#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#2)]
 [!code-vb[Formatting.HowTo.NumericValue#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#2)]  
  
 ただし、書式指定子が存在しない場合に、変換を行うようにすることもできます。 このようなメソッドの呼び出しの例を次に示します。  
  
 [!code-csharp[Formatting.HowTo.NumericValue#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#3)]
 [!code-vb[Formatting.HowTo.NumericValue#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#3)]  
  
 既定の書式指定子が定義されていない場合の実装、<xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType>その .NET 提供できるように書式設定コードがサポートされていないこと、メソッドは、次のようなコードを含める必要があります。  
  
 [!code-csharp[System.ICustomFormatter.Format#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.ICustomFormatter.Format/cs/format.cs#1)]
 [!code-vb[System.ICustomFormatter.Format#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.ICustomFormatter.Format/vb/Format.vb#1)]  
  
 この例の場合、メソッドを実装する<xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType>をコールバック メソッドとして機能するためのものでは、<xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>メソッドです。 そのため、それを調べ、`formatProvider`現在への参照が含まれているかどうかのパラメーター`TelephoneFormatter`オブジェクト。 ただし、メソッドはコードから直接呼び出すこともできます。 その場合は、使用することができます、`formatProvider`を提供するパラメーター、<xref:System.Globalization.CultureInfo>または<xref:System.Globalization.NumberFormatInfo>をカルチャに固有の書式情報を提供するオブジェクト。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 コマンド ラインで csc.exe または vb.exe を使用してコードをコンパイルします。 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] でコードをコンパイルするには、コンソール アプリケーション プロジェクト テンプレートの中にコードを配置します。  
  
## <a name="see-also"></a>関連項目  
 [書式設定操作の実行](../../../docs/standard/base-types/performing-formatting-operations.md)
