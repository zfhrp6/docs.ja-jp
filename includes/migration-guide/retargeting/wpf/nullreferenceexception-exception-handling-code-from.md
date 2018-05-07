### <a name="nullreferenceexception-in-exception-handling-code-from-imagesourceconverterconvertfrom"></a>ImageSourceConverter.ConvertFrom からの例外処理コード内の NullReferenceException

|   |   |
|---|---|
|説明|<xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)> の例外処理コードのエラーは、目的の例外 (<xref:System.IO.DirectoryNotFoundException?displayProperty=name> または <xref:System.IO.FileNotFoundException?displayProperty=name>) の代わりにスローされる誤った <xref:System.NullReferenceException?displayProperty=name> を発生させていました。 この変更によりエラーが修正されるため、このメソッドは正しい例外をスローするようになりました。 既定では、.NET Framework 4.6.2 以下を対象とするすべてのアプリケーションは、互換性のために引き続き <xref:System.NullReferenceException?displayProperty=name> をスローします。 .NET Framework 4.7 以上を対象とする開発者は、正しい例外を確認する必要があります。|
|提案される解決策|NET Framework 4.7 以降を対象とする場合に <xref:System.NullReferenceException?displayProperty=name> を取得する構成に戻したい開発者は、アプリケーションの App.config ファイルに次のコードを追加/マージします。<pre><code class="language-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Media.ImageSourceConverter.OverrideExceptionWithNullReferenceException=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|スコープ|エッジ|
|Version|4.7|
|型|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)?displayProperty=nameWithType></li></ul>|

