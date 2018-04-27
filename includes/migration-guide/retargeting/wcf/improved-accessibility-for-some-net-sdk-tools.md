### <a name="improved-accessibility-for-some-net-sdk-tools"></a>一部の .NET SDK ツールのアクセシビリティが強化されました

|   |   |
|---|---|
|説明|.NET Framework SDK 4.7.1 では、svcconfigedit.exe と svctraceviewer.exe のツールが改善され、さまざまなアクセシビリティの問題が修正されました。 その問題のほとんどは、名前の未定義や、特定の UI の自動化パターンが正しく実装されていないといった軽微なものです。 このような問題は、多くのユーザーが認識しないものですが、スクリーン リーダーのような支援技術を使用するお客様はこれらの SDK ツールのアクセシビリティの強化を実感されるでしょう。 実際に、この修正によって、キーボード フォーカスの順序のような以前の動作がいくつか変更されます。これらのツールのアクセシビリティの修正をすべて取得するには、app.config ファイルを次のようにします。<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|スコープ|エッジ|
|Version|4.7.1|
|型|再ターゲット中|

