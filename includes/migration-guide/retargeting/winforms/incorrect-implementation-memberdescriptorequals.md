### <a name="incorrect-implementation-of-memberdescriptorequals"></a>MemberDescriptor.Equals の不適切な実装

|   |   |
|---|---|
|説明|&quot;Equals&quot; メソッドの元の実装では、比較対象のオブジェクトからの 2 種類の文字列プロパティを比較していました (カテゴリ名と説明文字列)。 この修正プログラムでは、最初のオブジェクトの &quot;category&quot; を 2 番目のオブジェクトの &quot;category&quot; と比較し、さらに &quot;description&quot; を &quot;description&quot; と比較します。 MemberDescriptorEqualsReturnsFalseIfEquivalent の構成値を true に設定すると、4.6.2 を対象としている場合に、新しい動作を無効にすることができます。この構成を false に設定すると、ターゲット フレームワークのバージョンが 4.6.2 よりも前の場合に、この修正プログラムを有効にするにすることができます。|
|提案される解決策|記述子が等しいときに false を返すことがある MemberDescriptor.Equals にアプリケーションが依存していて、.NET Framework のバージョン 4.6.2 を対象とするときは、いくつかのオプションがあります。<ol><li>Equals メソッドを実行することに加えて、&quot;category&quot; フィールドと &quot;description&quot; フィールドを手動で比較するようにコードを変更します。</li><li>この変更を無効にするには、app.config ファイルに次の値を追加します。</li></ol><pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>アプリケーションが .NET Framework 4.6.1 以前のバージョンを対象にしている場合、この変更を無効にするには、app.config ファイルに次の値を追加することで互換性スイッチを false に設定します。<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|スコープ|エッジ|
|Version|4.6.2|
|型|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.ComponentModel.MemberDescriptor.Equals(System.Object)?displayProperty=nameWithType></li></ul>|

