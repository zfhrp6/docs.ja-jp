### <a name="httputilityjavascriptstringencode-escapes-ampersand"></a>HttpUtility.JavaScriptStringEncode でアンパサンドがエスケープされる

|   |   |
|---|---|
|説明|.NET Framework 4.5 以降では、<xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=name> でアンパサンド (&amp;) 文字がエスケープされます。|
|提案される解決策|アプリがこのメソッドの以前の動作に依存している場合、構成ファイルの [ASP.NET appSettings 要素](https://msdn.microsoft.com/library/hh975440.aspx) に aspnet:JavaScriptDoNotEncodeAmpersand 設定を追加できます。|
|スコープ|マイナー|
|Version|4.5|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String,System.Boolean)?displayProperty=nameWithType></li></ul>|

