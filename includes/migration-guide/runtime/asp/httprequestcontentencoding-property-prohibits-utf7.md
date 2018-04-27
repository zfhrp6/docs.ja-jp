### <a name="httprequestcontentencoding-property-prohibits-utf7"></a>HttpRequest.ContentEncoding プロパティで UTF7 が禁止される

|   |   |
|---|---|
|説明|.NET Framework 4.5 以降では、<xref:System.Web.HttpRequest?displayProperty=name> の本文では UTF-7 エンコードが禁止されます。 UTF-7 データの受信を必要とするアプリケーションのデータが、正しくデコードされない場合があります。|
|提案される解決策|理想的には、<xref:System.Web.HttpRequest?displayProperty=name> で UTF-7 エンコードを使用しないようにアプリケーションを更新する必要があります。 または、[<appSettings>](https://msdn.microsoft.com/library/hh975440(v=vs.110).aspx) 要素の <code>aspnet:AllowUtf7RequestContentEncoding</code> 属性を使用して、レガシ動作に戻すことができます。|
|スコープ|エッジ|
|Version|4.5|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|

