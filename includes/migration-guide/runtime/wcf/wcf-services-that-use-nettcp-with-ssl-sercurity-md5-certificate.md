### <a name="wcf-services-that-use-nettcp-with-ssl-sercurity-and-md5-certificate-authentication"></a>SSL セキュリティと MD5 証明書認証で NETTCP を使用する WCF サービス

|   |   |
|---|---|
|説明|.NET Framework 4.6 では、WCF SSL の既定のプロトコル一覧に TLS 1.1 および TLS 1.2 が追加されます。 クライアントとサーバーの両方のコンピューターに .NET Framework 4.6 以降がインストールされている場合は、TLS 1.2 がネゴシエーションに使用されます。TLS 1.2 では MD5 証明書認証がサポートされません。 このため、顧客が MD5 証明書を使用する場合、WCF クライアントでは WCF サービスへ接続できません。<ul><li>[ ] 後方互換 // メカニズムを使用して、この機能をオン/オフにします。通常はランタイムの設定、AppContext または構成ファイルを使用します。 状況によっては自動的にオンにする必要があります。</li><li>[ ] ビルド時の中断 // 再コンパイルしようとした場合、中断されます</li></ul>|
|提案される解決策|次のいずれかの操作を実行することで、この問題を回避して、WCF クライアントを WCF サーバーに接続できるようになります。<ul><li>MD5 アルゴリズムを使用しないように証明書を更新します。 この解決策をお勧めします。</li><li>バインドがソース コードで動的に構成されていない場合は、アプリケーションの構成ファイルを TLS 1.1 以前のバージョンのプロトコルを使用するように更新します。 これにより、引き続き MD5 ハッシュ アルゴリズムによる証明書を使用することができます。</li></ul>
<blockquote>
[!WARNING] MD5 ハッシュ アルゴリズムによる証明書は安全でないと見なされるため、この回避策はお勧めできません。</blockquote>
次の構成ファイルでこれを行います。<pre><code>&lt;configuration&gt;&#13;&#10;&lt;system.serviceModel&gt;&#13;&#10;&lt;bindings&gt;&#13;&#10;&lt;netTcpBinding&gt;&#13;&#10;&lt;binding&gt;&#13;&#10;&lt;security mode= &quot;None|Transport|Message|TransportWithMessageCredential&quot; &gt;&#13;&#10;&lt;transport clientCredentialType=&quot;None|Windows|Certificate&quot;&#13;&#10;protectionLevel=&quot;None|Sign|EncryptAndSign&quot;&#13;&#10;sslProtocols=&quot;Ssl3|Tls1|Tls11&quot;&gt;&#13;&#10;&lt;/transport&gt;&#13;&#10;&lt;/security&gt;&#13;&#10;&lt;/binding&gt;&#13;&#10;&lt;/netTcpBinding&gt;&#13;&#10;&lt;/bindings&gt;&#13;&#10;&lt;/system.ServiceModel&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre><ul><li>バインドがソース コードで動的に構成されている場合は、ソース コード内で TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) または以前のバージョンのプロトコルを使用するように <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType> プロパティを更新します。</li></ul>
<blockquote>
[!WARNING] MD5 ハッシュ アルゴリズムによる証明書は安全でないと見なされるため、この回避策はお勧めできません。</blockquote>| |スコープ|不明| |バージョン|4.6| |型|ランタイム|

