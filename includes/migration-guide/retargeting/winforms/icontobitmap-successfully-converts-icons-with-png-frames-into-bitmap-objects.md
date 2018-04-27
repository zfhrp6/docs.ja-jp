### <a name="icontobitmap-successfully-converts-icons-with-png-frames-into-bitmap-objects"></a>PNG フレームを含んだアイコンが Icon.ToBitmap によって、Bitmap オブジェクトに正常に変換されます

|   |   |
|---|---|
|説明|以降、.NET Framework 4.6 を対象とするアプリで、<xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType>メソッドがビットマップ オブジェクトに PNG フレームを含んだアイコンを正常に変換します。 .NET Framework 4.5.2 および以前のバージョンを対象とするアプリで、<xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType>メソッドがスローされます、<xref:System.ArgumentOutOfRangeException>アイコン オブジェクトに PNG フレームがある場合は例外です。この変更はアプリを .NET Framework 4.6 を対象として再コンパイルして、特別な処理を実装している、<xref:System.ArgumentOutOfRangeException>アイコン オブジェクトに PNG フレームがある場合にスローされます。 .NET Framework 4.6 で実行している場合は、正常に変換が行われ、 <xref:System.ArgumentOutOfRangeException> がスローされることはないため、例外ハンドラーは呼び出されません。|
|提案される解決策|この動作に不都合がある場合は、次に示す要素を app.config ファイルの <code>&lt;runtime&gt;</code> セクションに追加することで、以前の動作を維持できます。<pre><code class="language-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true&quot; /&gt;&#13;&#10;</code></pre>app.config ファイルに既に <code>AppContextSwitchOverrides</code> 要素が含まれている場合は、次に示すように新しい値を value 属性にマージする必要があります。<pre><code class="language-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true;&lt;previous key&gt;=&lt;previous value&gt;&quot; /&gt;&#13;&#10;</code></pre>|
|スコープ|マイナー|
|Version|4.6|
|型|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.Drawing.Icon.ToBitmap?displayProperty=nameWithType></li></ul>|

