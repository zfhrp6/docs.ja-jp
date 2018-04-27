### <a name="default-value-of-servicepointmanagersecurityprotocol-is-securityprotocoltypesystemdefault"></a>ServicePointManager.SecurityProtocol の既定値は SecurityProtocolType.System.Default

|   |   |
|---|---|
|説明|.NET Framework 4.7 を対象とするアプリから、<xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> プロパティの既定値が <xref:System.Net.SecurityProtocolType.SystemDefault?displayProperty=nameWithType> になります。 この変更により、SslStream をベースとする NET Framework ネットワーク API (FTP、HTTPS、SMTP など) は、.NET Framework によって定義されるハード コーディングされた値を使用する代わりに、オペレーティング システムから既定のセキュリティ プロトコルを継承できます。 既定値はオペレーティング システムと、システム管理者が実行するカスタム構成によって異なります。 Windows オペレーティング システムの各バージョンの既定の SChannel プロトコルに関する詳細については、「[Protocols in TLS/SSL (Schannel SSP)](https://msdn.microsoft.com/library/windows/desktop/mt808159.aspx)」 (TLS/SSL のプロトコル (Schannel SSP)) を参照してください。以前のバージョンの .NET Framework を対象とするアプリケーションの場合、<xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> プロパティの既定値は、対象となる .NET Framework のバージョンに依存します。 詳細については、「.NET Framework 4.5.2 から 4.6 への移行に関する変更の再ターゲット」の「[ネットワーキング](~/docs/framework/migration-guide/retargeting/4.5.2-4.6.md#networking)」セクションを参照してください。|
|提案される解決策|この変更は、.NET Framework 4.7 以降のバージョンを対象とするアプリケーションに影響を与えます。システムの既定に依存せず、定義されているプロトコルを使用する場合、<xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> プロパティの値を明示的に設定できます。この変更が望ましくない場合、構成設定をアプリケーション構成ファイルの [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) セクションに追加し、変更を無効にできます。 次の例では、<code>&lt;runtime&gt;</code> セクションと無効に切り替える処理 <code>Switch.System.Net.DontEnableSystemDefaultTlsVersions</code> の両方を確認できます。<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Net.DontEnableSystemDefaultTlsVersions=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|スコープ|マイナー|
|Version|4.7|
|型|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType></li></ul>|

