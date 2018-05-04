### <a name="non-pooled-sql-connections-will-leak-memory-if-not-explicitly-disposed"></a>明示的に破棄されない場合に、非プールの SQL 接続でメモリがリークする

|   |   |
|---|---|
|説明|.NET Framework 4.5 で、明示的に破棄されない非プールの SQL 接続 (Dispose、Close、または using を使用) ではメモリがリークします。|
|提案される解決策|この問題は、.NET Framework 4.5 サービス更新プログラムで修正されます。 この問題を修正するには、.NET Framework 4.5 を .NET Framework 4.5.1 以降に更新してください。 または、&#39;using&#39; パターンで <xref:System.Data.SqlClient.SqlConnection?displayProperty=name> を使用するか (ベスト プラクティス)、接続が不要になったときは Dispose または Close を明示的に呼び出して、この問題を回避できる場合があります。|
|スコープ|エッジ|
|Version|4.5|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String)?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String%2CSystem.Data.SqlClient.SqlCredential)?displayProperty=nameWithType></li></ul>|

