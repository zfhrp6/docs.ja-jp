### <a name="eventlistener-truncates-strings-with-embedded-nulls"></a>EventListener は、null が埋め込まれた文字列を切り捨てる

|   |   |
|---|---|
|説明|<xref:System.Diagnostics.Tracing.EventListener?displayProperty=name> は、埋め込まれた null のある文字列を切り捨てます。 null 文字は <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> クラスでサポートされません。 変更は、プロセスの <xref:System.Diagnostics.Tracing.EventListener?displayProperty=name> データを読み取るために <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> を使用し、区切り記号として null 文字を使用するアプリにのみ影響します。|
|提案される解決策|可能な場合は、埋め込まれた null 文字を使用しないように <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> データを更新する必要があります。|
|スコープ|エッジ|
|Version|4.5.1|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Diagnostics.Tracing.EventListener.%23ctor?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords,System.Collections.Generic.IDictionary{System.String,System.String})?displayProperty=nameWithType></li></ul>|

