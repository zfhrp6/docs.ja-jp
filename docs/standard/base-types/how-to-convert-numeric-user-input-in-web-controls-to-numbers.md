---
title: "方法 : Web コントロールでの数値のユーザー入力を数値に変換する | Microsoft Docs"
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
  - "変換 (数字のユーザー入力を数値に)"
  - "書式指定 [.NET Framework], 数"
  - "数値の書式指定 [.NET Framework]"
  - "数値 [.NET Framework], 変換 (数字のユーザー入力を数値に)"
  - "数値書式指定文字列 [.NET Framework]"
  - "解析 (文字列を) [.NET Framework], 数値文字列"
ms.assetid: f27ddfb8-7479-4b79-8879-02a3bd8402d4
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : Web コントロールでの数値のユーザー入力を数値に変換する
Web ページは世界中どこでも表示可能なため、ユーザーは <xref:System.Web.UI.WebControls.TextBox> コントロールの中に多種多様な形式で数値データを入力する可能性があります。  このため、Web ページのユーザーのロケールとカルチャを判別することは非常に重要です。  ユーザー入力を解析するとき、ユーザーのロケールとカルチャによって定義された書式指定規則を適用できます。  
  
### Web TextBox コントロールでの数値入力を数値に変換するには  
  
1.  <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=fullName> プロパティによって返された文字列配列にデータが含まれているかどうかを判別します。  含まれない場合は、手順 6. に進みます。  
  
2.  <xref:System.Web.HttpRequest.UserLanguages%2A> プロパティによって返された文字列配列にデータが含まれる場合は、その最初の要素を取得します。  最初の要素は、ユーザーの既定の言語と地域、または優先される言語と地域を表します。  
  
3.  <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=fullName> コンストラクターを呼び出すことにより、ユーザーが選択したカルチャを表す <xref:System.Globalization.CultureInfo> オブジェクトをインスタンス化します。  
  
4.  ユーザー入力の変換先となる数値型の `TryParse` メソッドまたは `Parse` メソッドを呼び出します。  `TryParse` メソッドまたは `Parse` メソッドの `provider` パラメーターを指定するオーバーロードを使用して、次のいずれかを渡します。  
  
    -   手順 3. で作成した <xref:System.Globalization.CultureInfo> オブジェクト。  
  
    -   手順 3. で作成した <xref:System.Globalization.CultureInfo> オブジェクトの <xref:System.Globalization.CultureInfo.NumberFormat%2A> プロパティによって返される <xref:System.Globalization.NumberFormatInfo> オブジェクト。  
  
5.  変換が失敗した場合、<xref:System.Web.HttpRequest.UserLanguages%2A> プロパティによって返される文字列配列内の他の要素ごとに手順 2. から 4. を繰り返します。  
  
6.  変換が引き続き失敗する場合、または <xref:System.Web.HttpRequest.UserLanguages%2A> プロパティによって返された文字列配列が空の場合には、<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName> プロパティによって返されるインバリアント カルチャを使って文字列を解析します。  
  
## 使用例  
 次の例は、<xref:System.Web.UI.WebControls.TextBox> コントロールに数値を入力するようユーザーに要求して、それを数値に変換する Web フォームの完全な分離コード ページです。  その後、その数値を 2 倍にして、元の入力と同じ書式指定規則を使って表示します。  
  
 [!code-csharp[Formatting.HowTo.ParseNumericInput#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.ParseNumericInput/cs/NumericUserInput1.aspx.cs#1)]
 [!code-vb[Formatting.HowTo.ParseNumericInput#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.ParseNumericInput/vb/NumericUserInput1.aspx.vb#1)]  
  
 <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=fullName> プロパティには、HTTP 要求の `Accept-Language` ヘッダーに含まれるカルチャ名からデータが入ります。  ただし、すべてのブラウザーの要求に `Accept-Language` ヘッダーが含まれるとは限りません。ユーザーがヘッダーを完全に禁止する場合もあります。  このため、ユーザー入力を解析する際にはフォールバック カルチャが重要になります。  通常、フォールバック カルチャは、<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName> によって返されるインバリアント カルチャです。  また、テキスト ボックスへの入力によってユーザーがカルチャ名を Internet Explorer に提供する場合もありますが、無効なカルチャ名が指定される可能性があります。  このため、<xref:System.Globalization.CultureInfo> オブジェクトをインスタンス化する際には、例外処理が重要になります。  
  
 Internet Explorer によって送信された HTTP 要求から取得される <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=fullName> 配列には、ユーザー側の優先度設定の順序でデータが入ります。  配列の先頭の要素には、ユーザーの最優先カルチャ\/地域の名前が格納されます。  何らかの追加項目が配列に含まれる場合、Internet Explorer はそれらに任意のクオリティ識別子を割り当てます。この識別子はセミコロンによってカルチャから区切られます。  たとえば、fr\-FR カルチャの項目は `fr-FR;q=0.7` という形式になります。  
  
 この例では、`useUserOverride` パラメーターを `false` に設定して <xref:System.Globalization.CultureInfo.%23ctor%2A> コンストラクターを呼び出し、新しい <xref:System.Globalization.CultureInfo> オブジェクトを作成します。  これによって、カルチャ名がサーバー上の既定のカルチャ名である場合、クラス コンストラクターによって作成される新しい <xref:System.Globalization.CultureInfo> オブジェクトにはカルチャの既定の設定が含まれ、サーバーの **\[地域と言語のオプション\]** アプリケーションを使ってオーバーライドされた設定は反映されません。  通常、サーバーでオーバーライドされた設定値はユーザーのシステムに存在せず、ユーザー入力に反映されることもありません。  
  
 ユーザー入力の変換先となる数値型の `Parse` メソッドまたは `TryParse` メソッドをコードで呼び出すことができます。  1 つの解析操作で解析メソッドを繰り返し呼び出す必要が生じる場合があります。  したがって、解析操作が失敗した場合に `false` を返す `TryParse` メソッドの方が適切です。  これに対して、`Parse` メソッドによって繰り返しスローされる例外を Web アプリケーションで処理する場合、コストが非常に大きくなる可能性があります。  
  
## コードのコンパイル  
 コードをコンパイルするには、既存のすべてのコードに置き換える形で、このコードを [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 分離コード ページの中にコピーします。  [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web ページには、次のコントロールを含める必要があります。  
  
-   コード内で参照されない <xref:System.Web.UI.WebControls.Label> コントロール。  その <xref:System.Web.UI.WebControls.TextBox.Text%2A> プロパティを "Enter a Number:" に設定します。  
  
-   `NumericString` という名前の <xref:System.Web.UI.WebControls.TextBox> コントロール。  
  
-   `OKButton` という名前の <xref:System.Web.UI.WebControls.Button> コントロール。  その <xref:System.Web.UI.WebControls.Button.Text%2A> プロパティを "OK" に設定します。  
  
 クラスの名前を、`NumericUserInput` から、[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] ページの `Page` ディレクティブの `Inherits` 属性で定義されるクラス名に変更します。  `NumericInput` オブジェクト参照の名前を、[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] ページの `form` タグの `id` 属性で定義される名前に変更します。  
  
## .NET Framework セキュリティ  
 ユーザーが HTML ストリーム内にスクリプトを挿入するのを防ぐために、サーバー応答の中でユーザー入力を直接エコー バックしないでください。  そうする代わりに、<xref:System.Web.HttpServerUtility.HtmlEncode%2A?displayProperty=fullName> メソッドを使ってこれをエンコードする必要があります。  
  
## 参照  
 [書式設定操作の実行](../../../docs/standard/base-types/performing-formatting-operations.md)   
 [数値文字列の解析](../../../docs/standard/base-types/parsing-numeric.md)