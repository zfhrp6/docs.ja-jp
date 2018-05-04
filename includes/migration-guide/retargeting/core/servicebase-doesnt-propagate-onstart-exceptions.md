### <a name="servicebase-doesnt-propagate-onstart-exceptions"></a>ServiceBase で OnStart 例外を伝達させない

|   |   |
|---|---|
|説明|.NET Framework 4.7 以前のバージョンでは、サービスの起動時にスローされた例外は、<xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> の呼び出し元に伝達されません。 .NET Framework 4.7.1 を対象とするアプリケーションから、起動できなかったサービスに関して、ランタイムによって例外が <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> に伝達されます。|
|提案される解決策|サービスの起動時、例外が存在する場合、その例外は伝達されます。 この情報は、サービスが起動できないエラーの診断に役立ちます。この動作が望ましくない場合、アプリケーション構成ファイルの <runtime> セクションに次の <AppContextSwitchOverrides> 要素を追加することで無効にできます。<pre><code class="language-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceProcess.DontThrowExceptionsOnStart=true&quot; /&gt;&#13;&#10;</code></pre>4.7.1 より前のバージョンを対象とするアプリケーションでこの動作を望む場合、アプリケーション構成ファイルの <runtime> セクションに次の <AppContextSwitchOverrides> 要素を追加してください。<pre><code class="language-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceProcess.DontThrowExceptionsOnStart=false&quot; /&gt;&#13;&#10;</code></pre>|
|スコープ|マイナー|
|Version|4.7.1|
|型|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase)?displayProperty=nameWithType></li><li><xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase[])?displayProperty=nameWithType></li></ul>|

