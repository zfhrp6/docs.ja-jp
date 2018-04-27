### <a name="sqlconnection-can-no-longer-connect-to-sql-server-1997-or-databases-using-the-via-adapter"></a>SqlConnection は VIA アダプターを使用して SQL Server 1997 またはデータベースに接続できなくなりました

|   |   |
|---|---|
|説明|[仮想インターフェイス アダプター (VIA) プロトコル](https://technet.microsoft.com/library/ms191229%28v=sql.105%29.aspx)を使用した SQL Server データベースへの接続はサポートされなくなりました。 SQL Server データベースへの接続に使用されるプロトコルは、接続文字列で表示されます。 VIA 接続には via:&lt;servername&gt; が含まれます。 このアプリが VIA 以外のプロトコル (tcp: や np: など) を介して SQL に接続される場合、破壊的変更は検出されません。また、SQL Server 7 (1997) への接続がサポートされなくなります。|
|提案される解決策|VIA プロトコルは推奨されていないので、SQL データベースに接続するには別のプロトコルを使用する必要があります。 最も一般的に使用されるプロトコルは TCP/IP です。 TCP/IP プロトコルを有効にするための手順については、[こちら](https://msdn.microsoft.com/library/bb909712.aspx)を参照してください。 データベースへのアクセスがイントラネット内からに限定されていて、ネットワーク速度が遅い場合は、共有パイプ プロトコルがより優れたパフォーマンスを提供する可能性があります。|
|スコープ|エッジ|
|Version|4.5|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String)?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String,System.Data.SqlClient.SqlCredential)?displayProperty=nameWithType></li></ul>|

