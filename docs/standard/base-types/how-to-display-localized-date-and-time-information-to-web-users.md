---
title: "方法 : ローカライズされた日付/時刻情報を Web ユーザーに表示する | Microsoft Docs"
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
  - "表示 (日付と時刻のデータを)"
  - "書式指定 [.NET Framework], 日付"
  - "書式指定 [.NET Framework], ローカライズされたデータ"
  - "ローカリゼーション [.NET Framework], 日付と時刻の表示"
  - "ローカライズされた日付の表示 [.NET Framework]"
  - "解析 (文字列を) [.NET Framework], 日付と時刻文字列"
ms.assetid: 377fe93c-32be-421a-a30a-be639a46ede8
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : ローカライズされた日付/時刻情報を Web ユーザーに表示する
Web ページは世界中どこでも表示可能なため、日付\/時刻値を解析して書式設定する操作では、ユーザーと対話する際に既定の書式 \(ほとんどの場合、Web サーバーのローカル カルチャの書式\) に依存するのは不適切です。  ユーザー入力された日付\/時刻文字列を扱う Web フォームは、ユーザーの選んだカルチャを使用して文字列を解析する必要があります。  同様に、ユーザーのカルチャに適合した書式で、日付\/時刻データをユーザーに表示する必要があります。  このトピックでは、これらを行う方法について示します。  
  
### ユーザー入力による日付\/時刻文字列を解析するには  
  
1.  <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=fullName> プロパティによって返された文字列配列にデータが含まれているかどうかを判別します。  含まれない場合は、手順 6. に進みます。  
  
2.  <xref:System.Web.HttpRequest.UserLanguages%2A> プロパティによって返された文字列配列にデータが含まれる場合は、その最初の要素を取得します。  最初の要素は、ユーザーの既定の言語と地域、または優先される言語と地域を表します。  
  
3.  <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=fullName> コンストラクターを呼び出すことにより、ユーザーが選択したカルチャを表す <xref:System.Globalization.CultureInfo> オブジェクトをインスタンス化します。  
  
4.  <xref:System.DateTime> 型または <xref:System.DateTimeOffset> 型の `TryParse` メソッドまたは `Parse` メソッドを呼び出して、変換を試みます。  `TryParse` メソッドまたは `Parse` メソッドの `provider` パラメーターを指定するオーバーロードを使用して、次のいずれかを渡します。  
  
    -   手順 3. で作成した <xref:System.Globalization.CultureInfo> オブジェクト。  
  
    -   手順 3. で作成した <xref:System.Globalization.CultureInfo> オブジェクトの <xref:System.Globalization.CultureInfo.DateTimeFormat%2A> プロパティによって返される <xref:System.Globalization.DateTimeFormatInfo> オブジェクト。  
  
5.  変換が失敗した場合、<xref:System.Web.HttpRequest.UserLanguages%2A> プロパティによって返される文字列配列内の他の要素ごとに手順 2. から 4. を繰り返します。  
  
6.  変換が引き続き失敗する場合、または <xref:System.Web.HttpRequest.UserLanguages%2A> プロパティによって返された文字列配列が空の場合には、<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName> プロパティによって返されるインバリアント カルチャを使って文字列を解析します。  
  
### ユーザーが要求したローカル日付\/時刻を解析するには  
  
1.  <xref:System.Web.UI.WebControls.HiddenField> コントロールを Web フォームに追加します。  
  
2.  現在の日付\/時刻、および世界協定時刻 \(UTC\) からのローカル タイム ゾーンのオフセットを <xref:System.Web.UI.WebControls.HiddenField.Value%2A> プロパティに書き込むことによって、`Submit` ボタンの `onClick` イベントを処理する JavaScript 関数を作成します。  文字列の 2 つの構成要素を分けるために、区切り記号 \(たとえばセミコロン\) を使用します。  
  
3.  スクリプトのテキストを <xref:System.Web.UI.ClientScriptManager.RegisterClientScriptBlock%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Boolean%29?displayProperty=fullName> メソッドに渡すことにより、Web フォームの <xref:System.Web.UI.Control.PreRender> イベントを使用して HTML 出力ストリームの中に関数を挿入します。  
  
4.  JavaScript 関数の名前を `Submit` ボタンの `OnClientClick` 属性に渡すことにより、イベント ハンドラーを `Submit` ボタンの `onClick` イベントに接続します。  
  
5.  `Submit` ボタンの <xref:System.Web.UI.WebControls.Button.Click> イベントのハンドラーを作成します。  
  
6.  イベント ハンドラー内で、<xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=fullName> プロパティによって返される文字列配列にデータが入っているかどうかを判別します。  入っていない場合は、手順 14. に進みます。  
  
7.  <xref:System.Web.HttpRequest.UserLanguages%2A> プロパティによって返された文字列配列にデータが含まれる場合は、その最初の要素を取得します。  最初の要素は、ユーザーの既定の言語と地域、または優先される言語と地域を表します。  
  
8.  <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=fullName> コンストラクターを呼び出すことにより、ユーザーが選択したカルチャを表す <xref:System.Globalization.CultureInfo> オブジェクトをインスタンス化します。  
  
9. ユーザーのローカル日付\/時刻の文字列表現、およびユーザーのローカル タイム ゾーン オフセットの文字列表現を別々の配列要素に保存するために、<xref:System.Web.UI.WebControls.HiddenField.Value%2A> プロパティに割り当てられた文字列を <xref:System.String.Split%2A> メソッドに渡します。  
  
10. ユーザー側の日付\/時刻を <xref:System.DateTime> 値に変換するために、<xref:System.DateTime.Parse%2A?displayProperty=fullName> メソッドまたは <xref:System.DateTime.TryParse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%2CSystem.DateTime%40%29?displayProperty=fullName> メソッドを呼び出します。  メソッドのオーバーロードを使用し、`provider` パラメーターを指定して、次のいずれかを渡します。  
  
    -   手順 8. で作成した <xref:System.Globalization.CultureInfo> オブジェクト。  
  
    -   手順 8. で作成した <xref:System.Globalization.CultureInfo> オブジェクトの <xref:System.Globalization.CultureInfo.DateTimeFormat%2A> プロパティによって返される <xref:System.Globalization.DateTimeFormatInfo> オブジェクト。  
  
11. 手順 10. の解析操作が失敗する場合は、手順 13. に進みます。  それ以外の場合は、ユーザーのタイム ゾーン オフセットの文字列形式を整数に変換するために、<xref:System.UInt32.Parse%28System.String%29?displayProperty=fullName> メソッドを呼び出します。  
  
12. <xref:System.DateTimeOffset.%23ctor%28System.DateTime%2CSystem.TimeSpan%29?displayProperty=fullName> コンストラクターを呼び出すことにより、ユーザーのローカル時間を表す <xref:System.DateTimeOffset> をインスタンス化します。  
  
13. 手順 10. の変換が失敗した場合、<xref:System.Web.HttpRequest.UserLanguages%2A> プロパティによって返される文字列配列内の他の要素ごとに手順 7. から 12. を繰り返します。  
  
14. 変換が引き続き失敗する場合、または <xref:System.Web.HttpRequest.UserLanguages%2A> プロパティによって返された文字列配列が空の場合には、<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName> プロパティによって返されるインバリアント カルチャを使って文字列を解析します。  その後、手順 7. から 12. を繰り返します。  
  
 結果として、Web ページのユーザー側のローカル時間を表す <xref:System.DateTimeOffset> オブジェクトが生成されます。  その後、<xref:System.DateTimeOffset.ToUniversalTime%2A> メソッドを呼び出すことで、対応する UTC を判別できます。  また、<xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=fullName> メソッドを呼び出し、時間の変換先のタイム ゾーンとして <xref:System.TimeZoneInfo.Local%2A?displayProperty=fullName> の値を渡すことによって、Web サーバー側の対応する日付\/時刻を判別することもできます。  
  
## 使用例  
 次の例は、日付\/時刻値の入力をユーザーに求める ASP.NET Web フォームの HTML ソースとコードの両方を含んでいます。  また、クライアント側スクリプトは、ユーザー側のローカル日付\/時刻に関する情報、およびユーザーのタイム ゾーンと UTC とのオフセットに関する情報を隠しフィールドに書き込みます。  その後、この情報はサーバーによって解析され、ユーザー入力を表示する Web ページが返されます。  さらに、ユーザーのローカル時間、サーバーの時間、および UTC を使用して、ユーザー側の日付\/時刻も表示されます。  
  
 <!-- TODO: review snippet reference [!code-csharp[Formatting.HowTo.ParseDateInput#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.ParseDateInput/cs/GetDateInfo.aspx#1)]  -->
 <!-- TODO: review snippet reference [!code-vb[Formatting.HowTo.ParseDateInput#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.ParseDateInput/vb/GetDateInfo.aspx#1)]  -->  
  
 クライアント側スクリプトは、JavaScript `toLocaleString` メソッドを呼び出します。  これにより、サーバー上で正常に解析される可能性がより高い、ユーザー ロケールの書式指定規則に従う文字列が生成されます。  
  
 <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=fullName> プロパティには、HTTP 要求の `Accept-Language` ヘッダーに含まれるカルチャ名からデータが入ります。  ただし、すべてのブラウザーの要求に `Accept-Language` ヘッダーが含まれるとは限りません。ユーザーがヘッダーを完全に禁止する場合もあります。  このため、ユーザー入力を解析する際にはフォールバック カルチャが重要になります。  通常、フォールバック カルチャは、<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName> によって返されるインバリアント カルチャです。  また、テキスト ボックスへの入力によってユーザーがカルチャ名を Internet Explorer に提供する場合もありますが、無効なカルチャ名が指定される可能性があります。  このため、<xref:System.Globalization.CultureInfo> オブジェクトをインスタンス化する際には、例外処理が重要になります。  
  
 Internet Explorer によって送信された HTTP 要求から取得される <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=fullName> 配列には、ユーザー側の優先度設定の順序でデータが入ります。  配列の先頭の要素には、ユーザーの最優先カルチャ\/地域の名前が格納されます。  何らかの追加項目が配列に含まれる場合、Internet Explorer はそれらに任意のクオリティ識別子を割り当てます。この識別子はセミコロンによってカルチャから区切られます。  たとえば、fr\-FR カルチャの項目は `fr-FR;q=0.7` という形式になります。  
  
 この例では、`useUserOverride` パラメーターを `false` に設定して <xref:System.Globalization.CultureInfo.%23ctor%2A> コンストラクターを呼び出し、新しい <xref:System.Globalization.CultureInfo> オブジェクトを作成します。  これによって、カルチャ名がサーバー上の既定のカルチャ名である場合、クラス コンストラクターによって作成される新しい <xref:System.Globalization.CultureInfo> オブジェクトにはカルチャの既定の設定が含まれ、サーバーの **\[地域と言語のオプション\]** アプリケーションを使ってオーバーライドされた設定は反映されません。  通常、サーバーでオーバーライドされた設定値はユーザーのシステムに存在せず、ユーザー入力に反映されることもありません。  
  
 この例では 1 つの日付\/時刻の 2 つの文字列表現 \(1 つはユーザー入力、もう 1 つは隠しフィールドに格納されたもの\) を解析するため、必要になる可能性のある <xref:System.Globalization.CultureInfo> オブジェクトが事前に定義されます。  <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=fullName> プロパティによって返される要素数より 1 つ多い <xref:System.Globalization.CultureInfo> オブジェクトから成る配列が作成されます。  その後、それぞれの言語\/地域文字列ごとに 1 つの <xref:System.Globalization.CultureInfo> オブジェクトがインスタンス化され、<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName> を表す <xref:System.Globalization.CultureInfo> オブジェクトもインスタンス化されます。  
  
 ユーザーの日付\/時刻の文字列表現を <xref:System.DateTime> 値に変換するために、コードの中で <xref:System.DateTime.Parse%2A> メソッドまたは <xref:System.DateTime.TryParse%2A> メソッドのどちらでも呼び出すことができます。  1 つの解析操作で解析メソッドを繰り返し呼び出す必要が生じる場合があります。  このため、解析操作が失敗した場合に `false` を返す <xref:System.DateTime.TryParse%2A> メソッドを使用する方が適切です。  これに対して、<xref:System.DateTime.Parse%2A> メソッドによって繰り返しスローされる例外を Web アプリケーションで処理する場合、コストが非常に大きくなる可能性があります。  
  
## コードのコンパイル  
 コードをコンパイルするには、分離コードのない [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web ページを作成します。  その後、この例を Web ページ内にコピーして、既存のすべてのコードを置き換えます。  [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web ページには、次のコントロールを含める必要があります。  
  
-   コード内で参照されない <xref:System.Web.UI.WebControls.Label> コントロール。  その <xref:System.Web.UI.WebControls.TextBox.Text%2A> プロパティを "Enter a Number:" に設定します。  
  
-   `DateString` という名前の <xref:System.Web.UI.WebControls.TextBox> コントロール。  
  
-   `OKButton` という名前の <xref:System.Web.UI.WebControls.Button> コントロール。  その <xref:System.Web.UI.WebControls.Button.Text%2A> プロパティを "OK" に設定します。  
  
-   `DateInfo` という名前の <xref:System.Web.UI.WebControls.HiddenField> コントロール。  
  
## .NET Framework セキュリティ  
 ユーザーが HTML ストリーム内にスクリプトを挿入するのを防ぐために、サーバー応答の中でユーザー入力を直接エコー バックしないでください。  そうする代わりに、<xref:System.Web.HttpServerUtility.HtmlEncode%2A?displayProperty=fullName> メソッドを使ってこれをエンコードする必要があります。  
  
## 参照  
 [書式設定操作の実行](../../../docs/standard/base-types/performing-formatting-operations.md)   
 [標準の日時書式指定文字列](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)   
 [カスタム日時書式指定文字列](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)   
 [日付と時刻文字列の解析](../../../docs/standard/base-types/parsing-datetime.md)