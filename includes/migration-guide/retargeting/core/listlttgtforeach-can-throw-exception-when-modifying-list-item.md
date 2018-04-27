### <a name="listlttgtforeach-can-throw-exception-when-modifying-list-item"></a>List&lt;T&gt;.ForEach は、リスト項目を変更すると、例外をスローすることがあります。

|   |   |
|---|---|
|説明|.NET 4.5 から、<xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})> 列挙子は、呼び出し元のコレクション内の要素が変更された場合、<xref:System.InvalidOperationException?displayProperty=name> 例外をスローします。 以前は、この様な場合、例外はスローされませんでしたが、競合状態になることがありました。|
|提案される解決策|理想的には、安全な操作ではないため、要素の列挙中にリストを変更しないようにコードを修正する必要があります。 ただし、以前の動作に戻すには、アプリを .NET 4.0 向けにできます。|
|スコープ|エッジ|
|Version|4.5|
|型|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})?displayProperty=nameWithType></li></ul>|

