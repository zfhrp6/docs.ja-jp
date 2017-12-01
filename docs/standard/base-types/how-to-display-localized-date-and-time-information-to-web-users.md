---
title: "方法 : ローカライズされた日付/時刻情報を Web ユーザーに表示する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- formatting [.NET Framework], dates
- parsing strings [.NET Framework], date and time strings
- localization [.NET Framework], date and time displays
- formatting [.NET Framework], localized data
- displaying date and time data
- localized date displays [.NET Framework]
ms.assetid: 377fe93c-32be-421a-a30a-be639a46ede8
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 21493e0e0c9e42cf5efc42d86c8f126fbae9b392
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-localized-date-and-time-information-to-web-users"></a>方法 : ローカライズされた日付/時刻情報を Web ユーザーに表示する
(これは、Web サーバーのローカル カルチャの形式はほとんどの場合) 既定の形式に依存しないように解析して、日付と時刻の値を書式設定する操作、Web ページは、世界中のどこでも表示できます、ため、ユーザーと対話するときにします。 代わりに、Web フォームには、日付を処理し、ユーザーが入力した文字列を時間では、ユーザーの優先カルチャを使用して文字列を解析する必要があります。 同様に、日付と時刻のデータは、ユーザーのカルチャに準拠した形式でユーザーに表示する必要があります。 このトピックでは、その方法について説明します。  
  
### <a name="to-parse-date-and-time-strings-input-by-the-user"></a>日付と時刻を解析するには、文字列をユーザー入力  
  
1.  文字列の配列がによって返されるかどうかを判断、<xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType>プロパティが設定されます。 そうでない場合は、手順 6 に進みます。  
  
2.  文字列の配列がによって返される場合、<xref:System.Web.HttpRequest.UserLanguages%2A>プロパティが設定されると、その最初の要素を取得します。 最初の要素は、ユーザーの既定値または優先する言語と地域を示します。  
  
3.  インスタンスを作成、 <xref:System.Globalization.CultureInfo> 、ユーザーを表すオブジェクトを呼び出してのカルチャの優先、<xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType>コンス トラクターです。  
  
4.  いずれかを呼び出す、`TryParse`または`Parse`のメソッド、<xref:System.DateTime>または<xref:System.DateTimeOffset>型変換を試みます。 オーバー ロードを使用して、`TryParse`または`Parse`メソッドを`provider`パラメーター、させ、次のいずれか。  
  
    -   <xref:System.Globalization.CultureInfo>手順 3. で作成されたオブジェクト。  
  
    -   <xref:System.Globalization.DateTimeFormatInfo>によって返されるオブジェクト、<xref:System.Globalization.CultureInfo.DateTimeFormat%2A>のプロパティ、<xref:System.Globalization.CultureInfo>手順 3. で作成されたオブジェクト。  
  
5.  変換が失敗した場合、手順 2. ~ 4. string 配列に残った各要素によって返される、<xref:System.Web.HttpRequest.UserLanguages%2A>プロパティです。  
  
6.  変換がまだ失敗する場合、または文字列の配列がによって返される場合、<xref:System.Web.HttpRequest.UserLanguages%2A>プロパティが空、によって返されるインバリアント カルチャを使用して、文字列の解析、<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>プロパティです。  
  
### <a name="to-parse-the-local-date-and-time-of-the-users-request"></a>ローカルの日付と時刻がユーザーの要求の解析  
  
1.  追加、<xref:System.Web.UI.WebControls.HiddenField>コントロールを Web フォームです。  
  
2.  処理する JavaScript 関数を作成、`onClick`のイベント、`Submit`ボタンから世界協定時刻 (UTC) に、現在の日付と時刻のローカル タイム ゾーンのオフセットを記述して、<xref:System.Web.UI.WebControls.HiddenField.Value%2A>プロパティです。 (セミコロン) などの区切り記号を使用して、文字列の 2 つのコンポーネントを区切ります。  
  
3.  Web フォームを使用して<xref:System.Web.UI.Control.PreRender>HTML に関数を挿入するイベントを出力ストリームを使用するスクリプトのテキストを渡すことによって、<xref:System.Web.UI.ClientScriptManager.RegisterClientScriptBlock%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Boolean%29?displayProperty=nameWithType>メソッドです。  
  
4.  イベント ハンドラーへの接続、`Submit`ボタンの`onClick`イベントを JavaScript 関数の名前を提供することによって、`OnClientClick`の属性、`Submit`ボタンをクリックします。  
  
5.  ハンドラーを作成、`Submit`ボタンの<xref:System.Web.UI.WebControls.Button.Click>イベント。  
  
6.  イベント ハンドラーで文字列の配列がによって返されるかどうかを判断、<xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType>プロパティが設定されます。 そうでない場合は、手順 14. に進みます。  
  
7.  文字列の配列がによって返される場合、<xref:System.Web.HttpRequest.UserLanguages%2A>プロパティが設定されると、その最初の要素を取得します。 最初の要素は、ユーザーの既定値または優先する言語と地域を示します。  
  
8.  インスタンスを作成、 <xref:System.Globalization.CultureInfo> 、ユーザーを表すオブジェクトを呼び出してのカルチャの優先、<xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType>コンス トラクターです。  
  
9. 割り当てられている文字列を渡す、<xref:System.Web.UI.WebControls.HiddenField.Value%2A>プロパティを<xref:System.String.Split%2A>別の配列要素内のユーザーのローカルの日付と時刻の文字列形式をおよびユーザーのローカル タイム ゾーン オフセットの文字列形式を格納する方法です。  
  
10. いずれかを呼び出す、<xref:System.DateTime.Parse%2A?displayProperty=nameWithType>または<xref:System.DateTime.TryParse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%2CSystem.DateTime%40%29?displayProperty=nameWithType>の日付と時刻に、ユーザーの要求を変換する方法、<xref:System.DateTime>値。 使用してメソッドのオーバー ロードを使用して、`provider`パラメーター、させ、次のいずれか。  
  
    -   <xref:System.Globalization.CultureInfo>手順 8. で作成されたオブジェクト。  
  
    -   <xref:System.Globalization.DateTimeFormatInfo>によって返されるオブジェクト、<xref:System.Globalization.CultureInfo.DateTimeFormat%2A>のプロパティ、<xref:System.Globalization.CultureInfo>手順 8. で作成されたオブジェクト。  
  
11. 手順 10 では、解析操作に失敗した場合は、手順 13 に進みます。 それ以外の場合、呼び出し、<xref:System.UInt32.Parse%28System.String%29?displayProperty=nameWithType>ユーザーのタイム ゾーン オフセットの文字列形式を整数に変換します。  
  
12. インスタンスを作成、<xref:System.DateTimeOffset>を呼び出すことによって、ユーザーのローカル時刻を表す、<xref:System.DateTimeOffset.%23ctor%28System.DateTime%2CSystem.TimeSpan%29?displayProperty=nameWithType>コンス トラクターです。  
  
13. 手順 10 で、変換が失敗した場合、手順 7 ~ 12 が string 配列に残った各要素によって返される、<xref:System.Web.HttpRequest.UserLanguages%2A>プロパティです。  
  
14. 変換がまだ失敗する場合、または文字列の配列がによって返される場合、<xref:System.Web.HttpRequest.UserLanguages%2A>プロパティが空、によって返されるインバリアント カルチャを使用して、文字列の解析、<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>プロパティです。 手順 7 ~ 12 を繰り返します。  
  
 結果は、 <xref:System.DateTimeOffset> Web ページのユーザーのローカル時刻を表すオブジェクト。 同等の UTC を呼び出すことによって確認できます、<xref:System.DateTimeOffset.ToUniversalTime%2A>メソッドです。 確認することも、等価の日付と時刻、Web サーバーで呼び出すことによって、<xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType>メソッドと値を渡す<xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>にかかる時間を変換先タイム ゾーンとします。  
  
## <a name="example"></a>例  
 次の例には、HTML ソースと、日付と時刻の値を入力するユーザーを確認する ASP.NET Web フォームのコードの両方が含まれています。 クライアント側のスクリプトはまた、隠しフィールドを UTC からローカルの日付と、ユーザーの要求の時刻と、ユーザーのタイム ゾーンのオフセットの情報を書き込みます。 この情報は、ユーザーの入力を表示する Web ページを返すと、サーバーによって解析されます。 またの日付と時刻 (utc)、サーバーで、ユーザーのローカル時刻、期間を使用して、ユーザーの要求を表示します。  
  
 [!code-aspx-csharp[Formatting.HowTo.ParseDateInput#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.ParseDateInput/cs/GetDateInfo.aspx#1)]
 [!code-aspx-vb[Formatting.HowTo.ParseDateInput#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.ParseDateInput/vb/GetDateInfo.aspx#1)]
  
 クライアント側スクリプトを呼び出す JavaScript`toLocaleString`メソッドです。 これには、これは、サーバー上で正常に解析される可能性が高く、ユーザーのロケールの書式指定規則に従う文字列が生成されます。  
  
 <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType>プロパティに含まれているカルチャ名から取得されます`Accept-Language`HTTP 要求に含まれるヘッダー。 ただし、一部のブラウザーを含める`Accept-Language`ヘッダーを要求、およびユーザーでのヘッダーを完全に抑制もことができます。 これにより、ユーザー入力を解析するときに、フォールバック カルチャを理解しておくことができます。 によって返されるインバリアント カルチャをフォールバック カルチャが通常は<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>します。 ユーザーも指定できます Internet Explorer のカルチャ名を作成する可能性があるカルチャ名が無効であるテキスト ボックスに入力します。 これにより、インスタンス化するときに、例外処理を使用する重要な<xref:System.Globalization.CultureInfo>オブジェクト。  
  
 Internet Explorer によって送信された HTTP 要求から取得されたときに、<xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType>のユーザーの優先順位に従って配列を作成します。 配列の最初の要素には、ユーザーのプライマリのカルチャまたは地域の名前が含まれています。 配列には、追加項目が含まれている場合、Internet Explorer 任意に割り当てます品質指定子は、カルチャ名をセミコロンで区切られます。 たとえば、FR-FR カルチャのエントリがフォームをかかる場合があります`fr-FR;q=0.7`です。  
  
 呼び出しの例、<xref:System.Globalization.CultureInfo.%23ctor%2A>を持つコンス トラクター、`useUserOverride`パラメーターに設定`false`新しい<xref:System.Globalization.CultureInfo>オブジェクト。 これにより、カルチャ名がサーバーで、既定のカルチャ名である場合、新しい<xref:System.Globalization.CultureInfo>クラスのコンス トラクターによって作成されたオブジェクトのカルチャの既定の設定が含まれています、サーバーを使用してオーバーライドされた設定が反映されない**地域と言語のオプション**アプリケーションです。 サーバーでオーバーライドされた設定値は、ユーザーのシステム上に存在するか、ユーザーの入力に反映させる可能性があります。  
  
 考えられるを定義するため、この例では、日付と時刻 (隠しフィールドに格納されている他のユーザーが 1 つの入力) の 2 つの文字列形式を解析、<xref:System.Globalization.CultureInfo>オブジェクトを事前に必要な可能性があります。 配列を作成、<xref:System.Globalization.CultureInfo>オブジェクトによって返される要素の数より大きい値の 1 つである、<xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType>プロパティです。 インスタンス化し、<xref:System.Globalization.CultureInfo>の各言語/地域識別文字列、オブジェクトをインスタンス化も、<xref:System.Globalization.CultureInfo>を表すオブジェクト<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>です。  
  
 コードは、いずれかを呼び出すことができます、<xref:System.DateTime.Parse%2A>または<xref:System.DateTime.TryParse%2A>メソッドは、ユーザーの文字列形式の日付に変換する時間を<xref:System.DateTime>値。 Parse メソッドを繰り返し呼び出す解析操作が 1 つ必要があります。 その結果、<xref:System.DateTime.TryParse%2A>返すためにのメソッドもよく`false`解析操作が失敗した場合。 これに対し、繰り返される例外を処理するによってスローされる可能性があります、<xref:System.DateTime.Parse%2A>メソッドは、Web アプリケーションで非常にコストがかかる処理をすることができます。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 コードをコンパイルするには、作成、[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]分離コードなしの Web ページ。 コピーして例では、Web ページ、既存のすべてのコードを置き換えます。 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web ページは、次のコントロールを含める必要があります。  
  
-   A<xref:System.Web.UI.WebControls.Label>コントロールで、コードで参照されていません。 設定の<xref:System.Web.UI.WebControls.TextBox.Text%2A>プロパティを"の数値を入力:"です。  
  
-   `DateString` という名前の <xref:System.Web.UI.WebControls.TextBox> コントロール。  
  
-   `OKButton` という名前の <xref:System.Web.UI.WebControls.Button> コントロール。 設定の<xref:System.Web.UI.WebControls.Button.Text%2A>プロパティを"OK"です。  
  
-   `DateInfo` という名前の <xref:System.Web.UI.WebControls.HiddenField> コントロール。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 ユーザーが HTML ストリームにスクリプトを挿入することを防ぐためにユーザー入力する必要がありますしない直接をエコーするサーバーの応答でします。 代わりを使用してエンコードする必要がある、<xref:System.Web.HttpServerUtility.HtmlEncode%2A?displayProperty=nameWithType>メソッドです。  
  
## <a name="see-also"></a>関連項目  
 [書式設定操作の実行](../../../docs/standard/base-types/performing-formatting-operations.md)  
 [Standard Date and Time Format Strings](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)  
 [Custom Date and Time Format Strings](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)  
 [日付と時刻文字列の解析](../../../docs/standard/base-types/parsing-datetime.md)
