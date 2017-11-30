---
title: "方法 : Web コントロールでの数値のユーザー入力を数値に変換する"
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
- parsing strings [.NET Framework], numeric strings
- converting numeric user input to number
- numbers [.NET Framework], converting numeric user input to number
ms.assetid: f27ddfb8-7479-4b79-8879-02a3bd8402d4
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 92e28e3b303a7523b9da69b7eb283e0261fc681c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-numeric-user-input-in-web-controls-to-numbers"></a>方法 : Web コントロールでの数値のユーザー入力を数値に変換する
ユーザーに数値データを入力できる Web ページは、世界中のどこでも表示できます、ため、<xref:System.Web.UI.WebControls.TextBox>ほぼ無制限の数の形式で制御します。 その結果、ロケールと、Web ページのユーザーのカルチャを判別することが重要です。 ユーザー入力を解析する場合、ユーザーのロケールとカルチャによって定義された書式指定規則を適用することができます。  
  
### <a name="to-convert-numeric-input-from-a-web-textbox-control-to-a-number"></a>Web のテキスト ボックス コントロールから数値の入力を数値に変換するには  
  
1.  文字列の配列がによって返されるかどうかを判断、<xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType>プロパティが設定されます。 そうでない場合は、手順 6 に進みます。  
  
2.  文字列の配列がによって返される場合、<xref:System.Web.HttpRequest.UserLanguages%2A>プロパティが設定されると、その最初の要素を取得します。 最初の要素は、ユーザーの既定値または優先する言語と地域を示します。  
  
3.  インスタンスを作成、 <xref:System.Globalization.CultureInfo> 、ユーザーを表すオブジェクトを呼び出してのカルチャの優先、<xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType>コンス トラクターです。  
  
4.  いずれかを呼び出す、`TryParse`または`Parse`にユーザーを変換する数値型のメソッドの入力します。 オーバー ロードを使用して、`TryParse`または`Parse`メソッドを`provider`パラメーター、させ、次のいずれか。  
  
    -   <xref:System.Globalization.CultureInfo>手順 3. で作成されたオブジェクト。  
  
    -   <xref:System.Globalization.NumberFormatInfo>によって返されるオブジェクト、<xref:System.Globalization.CultureInfo.NumberFormat%2A>のプロパティ、<xref:System.Globalization.CultureInfo>手順 3. で作成されたオブジェクト。  
  
5.  変換が失敗した場合、手順 2. ~ 4. string 配列に残った各要素によって返される、<xref:System.Web.HttpRequest.UserLanguages%2A>プロパティです。  
  
6.  変換がまだ失敗する場合、または文字列の配列がによって返される場合、<xref:System.Web.HttpRequest.UserLanguages%2A>プロパティが空、によって返されるインバリアント カルチャを使用して、文字列の解析、<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>プロパティです。  
  
## <a name="example"></a>例  
 次の例は数値で入力を求める Web フォームを完全な分離コード ページ、<xref:System.Web.UI.WebControls.TextBox>を制御し、数値に変換します。 その数が 2 倍になり、元の入力として同じ書式指定規則を使用して表示します。  
  
 [!code-csharp[Formatting.HowTo.ParseNumericInput#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.ParseNumericInput/cs/NumericUserInput1.aspx.cs#1)]
 [!code-vb[Formatting.HowTo.ParseNumericInput#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.ParseNumericInput/vb/NumericUserInput1.aspx.vb#1)]  
  
 <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType>プロパティに含まれているカルチャ名から取得されます`Accept-Language`HTTP 要求に含まれるヘッダー。 ただし、一部のブラウザーを含める`Accept-Language`ヘッダーを要求、およびユーザーでのヘッダーを完全に抑制もことができます。 これにより、ユーザー入力を解析するときに、フォールバック カルチャを理解しておくことができます。 通常、によって返されるインバリアント カルチャは、フォールバック カルチャ<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>です。 ユーザーも指定できます Internet Explorer のカルチャ名を作成する可能性があるカルチャ名が無効であるテキスト ボックスに入力します。 これにより、インスタンス化するときに、例外処理を使用する重要な<xref:System.Globalization.CultureInfo>オブジェクト。  
  
 Internet Explorer によって送信された HTTP 要求から取得されたときに、<xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType>のユーザーの優先順位に従って配列を作成します。 配列の最初の要素には、ユーザーのプライマリのカルチャまたは地域の名前が含まれています。 配列には、追加項目が含まれている場合、Internet Explorer 任意に割り当てます品質指定子は、カルチャ名をセミコロンで区切られます。 たとえば、FR-FR カルチャのエントリがフォームをかかる場合があります`fr-FR;q=0.7`です。  
  
 呼び出しの例、<xref:System.Globalization.CultureInfo.%23ctor%2A>を持つコンス トラクター、`useUserOverride`パラメーターに設定`false`新しい<xref:System.Globalization.CultureInfo>オブジェクト。 これにより、カルチャ名がサーバーで、既定のカルチャ名である場合、新しい<xref:System.Globalization.CultureInfo>クラスのコンス トラクターによって作成されたオブジェクトのカルチャの既定の設定が含まれています、サーバーを使用してオーバーライドされた設定が反映されない**地域と言語のオプション**アプリケーションです。 サーバーでオーバーライドされた設定値は、ユーザーのシステム上に存在するか、ユーザーの入力に反映させる可能性があります。  
  
 コードは、いずれかを呼び出すことができます、`Parse`または`TryParse`ユーザーの入力を数値型のメソッドに変換されます。 Parse メソッドを繰り返し呼び出す解析操作が 1 つ必要があります。 その結果、`TryParse`返すためにのメソッドもよく、`false`解析操作が失敗した場合。 これに対し、繰り返される例外を処理するによってスローされる可能性があります、`Parse`メソッドは、Web アプリケーションで非常にコストがかかる処理をすることができます。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 コードをコンパイルするをコピー、[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]分離コード ページのため、その既存のすべてのコードで置き換えます。 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web ページは、次のコントロールを含める必要があります。  
  
-   A<xref:System.Web.UI.WebControls.Label>コントロールで、コードで参照されていません。 設定の<xref:System.Web.UI.WebControls.TextBox.Text%2A>プロパティを"の数値を入力:"です。  
  
-   `NumericString` という名前の <xref:System.Web.UI.WebControls.TextBox> コントロール。  
  
-   `OKButton` という名前の <xref:System.Web.UI.WebControls.Button> コントロール。 設定の<xref:System.Web.UI.WebControls.Button.Text%2A>プロパティを"OK"です。  
  
 クラスの名前を変更`NumericUserInput`で定義されているクラスの名前に、`Inherits`の属性、[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]ページの`Page`ディレクティブです。 名前を変更、`NumericInput`オブジェクトによって定義された名前への参照、`id`の属性、[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]ページの`form`タグ。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 ユーザーが HTML ストリームにスクリプトを挿入することを防ぐためにユーザー入力する必要がありますしない直接をエコーするサーバーの応答でします。 代わりを使用してエンコードする必要がある、<xref:System.Web.HttpServerUtility.HtmlEncode%2A?displayProperty=nameWithType>メソッドです。  
  
## <a name="see-also"></a>関連項目  
 [書式設定操作の実行](../../../docs/standard/base-types/performing-formatting-operations.md)  
 [数値文字列の解析](../../../docs/standard/base-types/parsing-numeric.md)
