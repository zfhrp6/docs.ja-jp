### <a name="wcf-message-security-now-is-able-to-use-tls11-and-tls12"></a>WCF メッセージ セキュリティで TLS1.1 と TLS1.2 が使用可能に

|   |   |
|---|---|
|説明|.NET Framework 4.7 以降、顧客はアプリケーション構成設定を介し、SSL3.0 と TLS1.0 に加え、WCF メッセージ セキュリティで TLS1.1 または TLS1.2 を構成できます。|
|提案される解決策|.NET Framework 4.7 では、WCF メッセージ セキュリティの TLS1.1 と TLS1.2 のサポートは既定で無効になっています。 app.config または web.config ファイルの <code>&lt;runtime&gt;</code> セクションに次の行を追加することで有効にできます。<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|スコープ|エッジ|
|Version|4.7|
|型|再ターゲット中|

